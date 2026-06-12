---
title: "After installing ubuntu LAMP server"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by Csofresh on 2013-03-25
I'm trying to learn more about linux and servers by playing around with them and I can't figure out how to change the default **It works!**

[COLOR=#000000][FONT=Times]This is the default web page for this server.[/FONT][/COLOR]
[FONT=Times][SIZE=3][COLOR=#000000]The web server software is running but no content has been added, yet.[/COLOR][/SIZE][/FONT]

[FONT=Times][SIZE=3][COLOR=#000000]when i visit my IP address or localhost[/COLOR][/SIZE][/FONT]

[FONT=Times][SIZE=3][COLOR=#000000]I am just looking to save an HTML file to be viewed as or instead of this default file when I visit my IP but I cant find the default file (I've read var/www but still cannot locate it)[/COLOR][/SIZE][/FONT]

[FONT=Times][SIZE=3][COLOR=#000000]I've tried to save a VIM edited document as var/www/index.php and var/www/index.html but neither works[/COLOR][/SIZE][/FONT]

[FONT=Times][SIZE=3][COLOR=#000000]any assistance will be greatly appreciated thank you in advance.
I'm not using the gui so I only have the terminal and remember I'm really new so be really clear [/COLOR][/SIZE][/FONT]:D

---

### Post by Cyril4133 on 2013-03-25
You need to put your php and html file in lampp/htdocs/

---

### Post by steeldriver on 2013-03-25
For the default lamp-server installation I believe it's **[COLOR=#ff0000]/[/COLOR]**var/www/index.html - looks like you're just missing the leading **[COLOR=#ff0000]/[/COLOR]** (which makes it begin the  path in your current directory, instead of from the filesystem root)

```
$ cat /var/www/index.html
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
```

---

