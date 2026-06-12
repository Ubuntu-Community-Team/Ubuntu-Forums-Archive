---
title: "Wireless disconnected ! Please help"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Slavi K on 2012-09-08
My network is visible and Ive typed my WPA password but when its trying to connect it says that the network is dissconected and ofline.

I have tried with :  

rfkill unblock wifi

sudo /sbin/modprobe ath9k

....but nothing helped...
My machine is PB easynote TJ 71rb

---

### Post by shadedpixel on 2012-09-08
It is possible that your adapter or PCI card is not 100% supported. What kind of card are you using? Also, you may want to try disabling the security on your wireless network and see if it connects. But dont keep it unsecured (even if it works) its dangerous especially if you live in a highly populated area.

---

### Post by anewguy on 2012-09-09
Depending on the age and type of wireless adapter, it may not support WPA encryption.  I forgot the link to the script, so I won't even attempt to remember everything, so please do the following in a terminal window:

echo -n "Begin lspci" > network.txt
lspci >> network.txt
echo -n "Begin lsusb" >> network.txt
lsusb >> network.txt
echo -n "Begin lsmod" >> network.txt
lsmod >> network.txt

A couple of notes:  only 1 ">" on the first line, but all the rest MUST be ">>".  The output is being redirected to a file (network.txt) and the first line ">" says to create new file (or overwrite).  The rest need to append to the file - that's what the ">>" does.

When you have finished, there will be a file called network.txt in the folder you were in when you opened the terminal window (normally ~ [home] for the user).  Reply back here and attach the file to the reply.

---

