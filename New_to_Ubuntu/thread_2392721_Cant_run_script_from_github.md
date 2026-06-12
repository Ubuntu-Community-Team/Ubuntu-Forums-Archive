---
title: "Cant run script from github"
date: 2018-05-24
forum: New to Ubuntu
---

### Post by michaellstone123 on 2018-05-24
Hello, im totally new to Ubuntu, my server uses Ubuntu Ubuntu 16.04 64 Bit, just trying to use this script [https://github.com/dmorlan/Nginx-FTP](https://github.com/dmorlan/Nginx-FTP) and got 
```
NginxFTP.sh: line 7: syntax error near unexpected token `newline'
NginxFTP.sh: line 7: `<!DOCTYPE html>'

```
Im alredy downloaded this script with wget command. Any idea whats wrong? Script seems fine on line 7.

---

### Post by TheFu on 2018-05-24
I appears you didn't download just the script. From the errror, it seems to have HTML, which I don't see in the script on github.

BTW, you understand the security risks in using FTP, right?   Plain FTP should not be used since around 1995.  Use scp, sftp, or even an HTTPS upload instead.  To get sftp, just install openssh-server.  Normal user accounts will have sftp/scp/ssh access if you don't restrict it.  Normal file system permissions will apply.  All of those methods are considered secure enough for internet use, provided you use ssh-keys, never passwords.   Passwords alone on the internet are a security failure.

[https://news.ycombinator.com/item?id=245935](https://news.ycombinator.com/item?id=245935) from the Hacker New has some reasons.  Google has 1.8M results. A common complaint is transfer speed. You can select a less-secure, higher performing, cipher.

---

### Post by Holger_Gehrke on 2018-05-24
'wget' got you the HTML-page with the script on it, not just the script. The script is in there, embedded in lots of html-markup around line 450. You can hit the button 'Raw' on the page to get the script without all the html and use wget to download [that]("https://raw.githubusercontent.com/dmorlan/Nginx-FTP/master/NginxFTP.sh").

Holger

PS: @TheFu: if I don't misunderstand that script, it sets vsftpd with SSL, so it should be secure enough ...

---

### Post by michaellstone123 on 2018-05-24
But script doesnt have HTML in

---

### Post by Holger_Gehrke on 2018-05-24
> **michaellstone123 said:**
> But script doesnt have HTML in

Are you sure ? The error you got showed line 7 of the 'script', and that was a document type declaration for a html file. That shouldn't be in there unless you downloaded the wrong file with wget. Just open the file in an editor and check its contents. A link to the script without all the markup was in my first post.

Holger

---

### Post by michaellstone123 on 2018-05-24
Okay it works :) Thanks!

---

### Post by david1222 on 2018-05-30
Thanks for your help! :)

---

