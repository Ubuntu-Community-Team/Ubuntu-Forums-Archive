---
title: "bcm43xx followed instructions but nothing"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by KeithF40 on 2008-08-27
I am new to linux and so would like to get it set up so i can start exploring and learning.  Anyway this is what I did to my dv6000z without success.

1. installed latest ubuntu from live cd straight to hd

2. put in cd and went to synaptic and searched for ndiswrapper

3. checked all 3 ndiswrapper entries and applyed

4. terminal

a) sudo ndiswrapper -i $HOME/broadcom/bcmwl5.inf

b) sudo ndiswrapper -l

c) sudo modprobe ndiswrapper

d) sudo ndiswrapper -m

5. then it pops up that new drivers are available
i click the popup and it lists broadcom card and in use
i check the box for enable
then it comes up about firmware and that it can auto extract it so i check the box for it and click next
says i need to restart

6. restart

7. nothing
go back to where it lists the driver and says in use but not enabled so i check box again and restart and still nothing

---

### Post by nicedude on 2008-08-27
I am not sure but you might find a positive result with b43-fwcutter as it just tries to install the latest or best Broadcom wifi driver for you. This is outside of Ndiswrapper of course as it is a way to use a windows driver with Linux.

To use it try

sudo apt-get install b43-fwcutter


and in the install it should prompt you if you want to download a driver so say yes of course.


Hope this helps, feel free to PM me if you are lost and if I don't know I will try and find someone who does :-)

---

### Post by RequinB4 on 2008-08-27
For a full tutorial for installing ndiswrapper (faster than fwcutter):

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

EDIT: The problem with what you did in the OP is that you didn't blacklist all of the evil modules that take precedence over the one you want.

---

### Post by KeithF40 on 2008-08-27
if at this point i do all that will it work or is there more i have to do to make up for what i did?

---

### Post by aitjcize on 2008-08-27
see this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
I had the same problem too,
and worked!!
try it.

---

### Post by KeithF40 on 2008-08-27
Didnt work for me, im done with this unless someone who has done it on a dv6000z for 4311 rev 01 can help, im pooped.

---

