---
title: "Best way to develop and manage websites locally in ubuntu"
date: 2013-05-31
forum: Programming Talk
---

### Post by nayzo on 2013-05-31
[COLOR=#000000][FONT=Arial]I'm new in Ubuntu, I use Ubuntu 12.04 LTS, for my Desktop,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I want to develop websites locally, so I installed LAMP, and I found that my www folder is in '/var/www/' so when I try to add new project in it using Netbeans or modify files or what so ever, I face permission problem !! :([/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I would like to know the best way I could use to manage and develop websites with ease?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by imagecko on 2013-05-31
Look at this site: [https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](https://netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)

Scroll down to "Specifying the Document Root for the Apache2 HTTP Server".
Thats the way I usually do it.

---

### Post by nayzo on 2013-05-31
Thanks it worked with me :)  I added multi-virtual host to manage more sites with the same public_html folder.

---

