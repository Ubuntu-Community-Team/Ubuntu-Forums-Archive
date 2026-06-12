---
title: "Drivers not found for the printer HP PSC 1315s All-in-One"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Yuliya on 2008-09-30
I was given a HP PSC 1315s All-in-One and I can not find the drivers. On [www.hp.com/de](www.hp.com/de) I can find them (it was bought in germany) but not for Linux system. Its there any way I could get them or at least any way I could get to use the scanner?

Thank you!

---

### Post by shifty_powers on 2008-09-30
[http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1315](http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1315)

---

### Post by Yuliya on 2008-09-30
does it also work on the PSC 1315s? (note the s - they are different printers)

---

### Post by shifty_powers on 2008-09-30
should do, the hplip driver supports a lot of hp printers....

---

### Post by Yuliya on 2008-09-30
I cant get the file. IT appears as .RUN and my computer wont open it and I dont know with what program to open it either

---

### Post by shifty_powers on 2008-09-30
did you getv the hplip pakcage?

and

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

will help :D

edit: hplip is [here](http://hplipopensource.com/hplip-web/gethplip.html)

---

### Post by Yuliya on 2008-09-30
I cant get it to work and I looked on the help section, I looked IF I already had the driver installed and I typed on terminal what said the site and gfot this:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          2.8.2-0ubuntu8 HP Linux Printing and Imaging System (HPLIP)
attila@attila-desktop:~$ rpm -qa hplip
The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
bash: rpm: command not found
attila@attila-desktop:~$ sudo apt-get install rpm
[sudo] password for attila: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
attila@attila-desktop:~$ sudo dpkg
dpkg: need an action option
 

and I cant update anything, also from the automatic updater due to thus "run manually dpkg"

---

### Post by shifty_powers on 2008-09-30
```
sudo dpkg --configure -a
```

---

### Post by Yuliya on 2008-09-30
I got everything sorted out there and now I do what the page says (the link you sent me) and I get this:

attila@attila-desktop:~$ sh hplip-2.8.8.44.run
sh: Can't open hplip-2.8.8.44.run

---

### Post by shifty_powers on 2008-09-30
hang on, did you go to the right directory? did you download the hplip package to the desktop?

and i just noticed that the installation instructions are for a different version to that you download on the fornt page, which is a bit naughty.

can you post the output of

```
ls
```

for that directory...

---

### Post by Yuliya on 2008-09-30
attila@attila-desktop:~$ sh hplip-2.8.8.44.run
sh: Can't open hplip-2.8.8.44.run
attila@attila-desktop:~$ lp
lp: Error - no default destination available.
attila@attila-desktop:~$ ls
08 Romanian Folkdances - for small Orchestra_ V. Poarga Româneasca [BB  76].mp3
09 Romanian Folkdances - for small Orchestra_ VI Maruntel [BB  76].mp3
24 rapsodia macabra463.mp3
Desktop
Documents
Examples
Firefox_wallpaper.png
gnash-dbg.log
Music
Photos
Pictures
Public
Templates
Videos
attila@attila-desktop:~$ 

thats what I get

---

### Post by oldos2er on 2008-09-30
Yuliya, try this. Run the following commands one at a time:

 chmod a+x hplip-2.8.8.44.run

 sh ./hplip-2.8.8.44.run

---

### Post by shifty_powers on 2008-09-30
no point in him doing that in that directory surely.

when you downloaded it, where did you save it?

---

### Post by sydbat on 2008-09-30
I may have missed something, but does the hplip in the repositories not work for your printer?

---

### Post by shifty_powers on 2008-09-30
pfft, thats just being a smart ****....

i'm tired, that's my excuse and i'm sticking to it :P

```
sudo apt-get hplip
```

and then look in your programs menu, or possibly the admin/preferences menu..

---

