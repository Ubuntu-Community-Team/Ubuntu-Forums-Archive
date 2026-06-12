---
title: "Striata-Reader"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by sampioen on 2008-06-27
Hello all.

i installed the .rpm of the above mentioned reader for encrypt files like invoices. then i converted it with alien to a .deb (i looked on the internet how to do this)

now when i want to open my encrypted .emc files, it opens a gui window that apparently needs a username and password (i guess, because i dont see anything, just 2 open tabs to write something in)

???

Please assist this Kubuntu-newbee-just-saved-from-windows person..
;-)

---

### Post by rules on 2008-07-24
I had the same problem ... but have a look here [http://ubuntuforums.org/showthread.php?t=511759](http://ubuntuforums.org/showthread.php?t=511759)

kookieforyou suggest installing libstdc++5

I did this and now it only asks for the password.

Problem is, it still does not open the "page". It just gives me the pop-up that says I must click OK when I'm finished so that it will clear the temp folder.

Anyone know why?

Cheers

---

### Post by infoseeker on 2008-08-02
I get that message too and its there to flush out the temporary files created when the reader opens up the *.emc file.  You are only meant to click the 'OK' that AFTER reading the contents of the *.emc file.  It should open in the background somewhere, maybe in another window?

---

### Post by infoseeker on 2008-11-07
```
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
```
Anyone tried installing the reader in 64bit Ubuntu (8.10)?
[http://www.striata.com/_global/downloads.php](http://www.striata.com/_global/downloads.php)
There seems no option to select 64-bit reader.

---

### Post by Grootvis on 2008-11-17
Hi 

Also had a problem with striata reader & Ubuntu dapper drake.
I followed the instructions on [http://ubuntuforums.org/showpost.php?p=4347612](http://ubuntuforums.org/showpost.php?p=4347612)
& it worked.
I use evolution mail reader & when i receive my statements i can view them.
The statement opens up in firefox although you get the pop up in front. 
Ignore the pop up until you viewed the statement then click ok.
 
Many thanks to infoseeker & the others for the write up

---

### Post by stephanvaningen on 2008-11-17
Is it also not possible to use the folder-encryption tool provided in 8.10?

---

