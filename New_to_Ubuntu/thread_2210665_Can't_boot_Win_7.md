---
title: "Can't boot Win 7"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by tusharkoshti on 2014-03-12
I installed Ubuntu along with Win 7. While installing I changed position of Win 7 loader ( why I did , don't know ). But due to this I lost GRUB. 
So again I installed Ubuntu without doing any over smart thing. Didn't change the Win 7 loader position. This time I got GRUB with both Ubuntu and Win 7.
But when I choose Win 7 , I can't boot through Win 7. I remain on the same GRUB window. Ubuntu is working. But I can't load Win 7 despite I see both OS. 
Please help.

---

### Post by phidia on 2014-03-12
Maybe [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") can help you?

---

### Post by slooksterpsv on 2014-03-12
Just to make sure I understand, you go down and highlight Windows 7, press Enter, and it takes you back to the GRUB menu?

Try running boot-repair, as the user mentioned above, and use pastebin to give us the output/log file of Boot-Repair. That way we can see the partitions and help identify what's going on.

---

### Post by tusharkoshti on 2014-03-12
I tried but I think I didn't succeed in installing boot-repair. I didnt find Boot-repair in the Dash. 
Here is the o/p of the command. 


tushar@tushar-VPCEH3AEN:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
[sudo] password for tushar: 
You are about to add the following PPA to your system:
 Boot-Repair
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it


.
.
.
.
.
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Fetched 72 B in 3s (20 B/s)
Reading package lists... Done


tushar@tushar-VPCEH3AEN:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#0000cd]E: Unable to locate package boot-repair[/COLOR]
tushar@tushar-VPCEH3AEN:~$

---

### Post by phidia on 2014-03-12
Someone else has had a similar problem-see if the fix described [in this thread]("http://askubuntu.com/questions/165255/unable-to-install-boot-repair") will work.

---

### Post by Mark Phelps on 2014-03-12
IF you forced the installation of GRUB components into the same partition that contains the Win7 boot loader, that effectively "broke" Win7 and running boot-repair is most likely not going to fix that.

One way to tell if this is the problem is to boot into Ubuntu, mount the Windows boot partition and look at the folders in there.  If you have both "Boot" and "boot", then you HAVE to remove the "boot" folder -- as that is confusing the Win7 boot loader.

After that, boot-repair might work.

---

### Post by newb85 on 2014-03-12
Are you using 11.10?  That's no longer supported.

---

### Post by tusharkoshti on 2014-03-14
@ newb85 

Ya. I was using Ubuntu 11.10. 
But now I upgraded it to 12.04. And problem is solved. 
Thank you.

---

### Post by newb85 on 2014-03-14
Good to hear.

---

