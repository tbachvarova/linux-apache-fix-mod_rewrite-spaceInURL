# FIX linux (Ubuntu) Apache mod_rewrite space In URL

After the last Apache Upgrade, I've had some issues with "spaces in URL" in mod_rewrite.
2023-04-25 - upgrade apache2:amd64 2.4.38-3+deb10u9 2.4.38-3+deb10u10

The URLs that contain "space" and have been replaced with **%20** start to return error 403 by Apache.

I found that the update was actually to fix this:
https://security-tracker.debian.org/tracker/CVE-2023-25690

After the last Apache upgrade under Ubuntu, I solve the problem of returning 403 by adding `[NC,L,B,BNP]` at the end of the domain conf file, adn it works for me.

>RewriteEngine On
> 
>RewriteBase /
> 
>RewriteRule ^([^/])/([^/])$ /index.php?lang=$1&page=$2 [NC,L,**B,BNP**]


![fix Apache space in URL - mod_rewrite](img.jpg)


I hope that this fix should be helpful to somebody :-)