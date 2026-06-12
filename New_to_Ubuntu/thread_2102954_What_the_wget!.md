---
title: "What the wget!"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by W0jtek on 2013-01-08
Hello! 
I`m using ubuntu 10.04, ubuntu 11.04LTS and lubuntu 11.10 on three different machines.

I`ve wrote a simple bash script using a wget command to downolad multiple files from multiple ftp servers.

And the problem is that the same script is working perfectly on both ubuntu machines and it`s not working on lubuntu.

command is (for active-only ftp server):
```
wget ftp://user:pass@server.com/*.* --directory-prefix=/directory/ --no-passive-ftp -a /directory/log
```
On lubutu wget hangs just before downloading .listing , i don`t know why, i don`t have idea where to check what`s going on.
 
And why both ubuntu`s don`t have any problem with wget`ing to the same server using the same login&pass.

I will be very grateful for any help.

command :
[IMG]http://galeriabutelek.pl/cmd.jpg[/IMG]
log
[IMG]http://galeriabutelek.pl/log.jpg[/IMG]

---

### Post by Impavidus on 2013-01-09
Lubuntu 11.10, being more recent than both of your ubuntu versions, may use a different version of wget, with a slightly different way of passing options to it.

You can use ```
wget -V
``` to get the exact version numbers of wget on your different machines. Use ```
wget -h
``` to get a description of the correct way to pass options to your particular versions.

By the way, 10.04 is the LTS release, not 11.04, which is out of support.

---

### Post by mastablasta on 2013-01-09
Turtle power!  :lolflag:
 
sorry can't resit. 
 
but yeah different versions of os may work differently. which is why users shouldn't just scower the net for scripts and run them blindly.

---

### Post by Cheesemill on 2013-01-09
Do you have write permissions for the local folder you are downloading to on your machine? Wget might be hanging at the start of the download as it can't write the files.

---

