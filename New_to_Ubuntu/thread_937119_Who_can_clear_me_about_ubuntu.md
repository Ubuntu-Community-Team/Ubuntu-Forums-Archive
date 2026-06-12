---
title: "Who can clear me about ubuntu?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Paul Weinstock on 2008-10-03
Hello, I'm new user and do not have experience about ubuntu, so I wanna know if I can install it together with windows? and would it be possible that I see my files in my hard drive saved in windows from ubuntu?

Thanks
Paul Weinstock

---

### Post by melojo on 2008-10-03
> **Paul Weinstock said:**
> Hello, I'm new user and do not have experience about ubuntu, so I wanna know if I can install it together with windows? and would it be possible that I see my files in my hard drive saved in windows from ubuntu?

Thanks
Paul Weinstock

yes to the above.  you can use the live cd to test it without installing.

welcome to the forums

---

### Post by shifty_powers on 2008-10-03
yes and yes.

have a look at the psychocats link in my sig, lots of stuff there.

google wubi, it is a good way of starting. it will create a partition, but it is really just a file on your windows drive. it will be completely transparent to you when using ubuntu, i.e. you will just see it as a partition within ubuntu.

by default ubuntu  an read/write to ntfs partitions, but windows won't be able to see your ubuntu stuff...

good fun and good luck :D

---

### Post by shifty_powers on 2008-10-03
well of course the live cd. sorry, it is such an automatic thing, didn't even think to mention it!

---

### Post by howefield on 2008-10-03
Short answer is yes to both your your questions.,

There are several ways to do it, you can install Ubuntu inside windows using Wubi, which basically means that Ubuntu will be installed as a file that resides inside your windows installation, the benefit being that it is easily uninstalled should you wish. 

Another way would be to dual boot, whereby windows and Ubuntu reside on their own partitions.

Wow you got to be fast in here :)  just to add to shifty_powers point about windows not seeing ubuntu files, this is true out of the box but you can install some free software that will give windows that ability.

---

### Post by shifty_powers on 2008-10-03
yes you can, but there is some question how stable the drivers are, and i would hesitate to use them personally.

and yes, you have to be like bloody lightening here :D

---

### Post by Mehall on 2008-10-03
> **shifty_powers said:**
> by default ubuntu  an read/write to ntfs partitions, but windows won't be able to see your ubuntu stuff...

I can't remember how, but there is somewhere that has files to give XP/Vista ext2 and ext3 support.

---

### Post by shifty_powers on 2008-10-03
yup, we've already mentioned that, but as i mentioned in my last post, i question the stability of the ext2, (iirc ext3 isn't supported yet), drivers for windows...

---

### Post by Paqman on 2008-10-03
> **shifty_powers said:**
> (iirc ext3 isn't supported yet)

Yes it is. It just mounts the ext3 partitions as ext2, which is fine since backwards compatibility is part of the ext3 spec.

---

### Post by shifty_powers on 2008-10-03
well i did say iirc ;)

been a while since i checked it out...

---

### Post by Elfy on 2008-10-03
Hi - as you've no doubt gathered - there are 2 ways - a dual boot and wubi. Much of the time people assume that an installation is a 'normal' dual boot so if you do install the wubi please make sure that you say so - whil eit doesn't alwyas make a difference, in some cases it does.

There is a fairly detailed wiki available for wubi - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) 



Good luck

---

### Post by bellmarbob on 2008-10-03
> **Paul Weinstock said:**
> Hello, I'm new user and do not have experience about ubuntu, so I wanna know if I can install it together with windows? and would it be possible that I see my files in my hard drive saved in windows from ubuntu?

Thanks
Paul Weinstock
Paul
I am also new but I have done the following very successfully
and there is no impact on my windows system.

I found a very easy way to install Ubuntu rather than running it thru Windows. My first concern was I did not want to partition my windows drive and load Ubuntu on that because then a hard drive failure would take both systems down and any problems I had with the Ubuntu install might impact my windows system. That is something you have to be very careful of when installing Ubuntu. I had a USB hard drive (you can buy one for $50) which I dedicated solely to Ubuntu. Before starting any of this you should also download and make a GRUB repair disk like system rescue CD. This is in case the Grub boot loader becomes corrupted during the install process.  The exact process I used was as follows:
 1. I set my boot sequence to boot from a CDROM followed by boot from the USB connection. My On-board hard drive (the one with windows)is the 3rd boot option
 2. I disconnected my hard drives in the PC that had windows on them. This is easily done by opening the case and pulling the power connection to the windows hard drives. Do this with the power OFF
 3. I then loaded the Ubuntu CDROM in and turned the PC on
 4. From this point just follow the instructions as they come up on the screen. 
 5. This fully installs Ubuntu on the USB hard drive.
 6. Boot the system up and see if it boots into Ubuntu. If it does skip step 7
 7. Use the system rescue disk to correct any boot problems you may have in booting into Ubuntu. 
 8. Shut system down and reconnect the windows drives  

some additional comments
  The result of this is that both windows and Ubuntu are totally independent of one another. Since both the windows MBR and Ubuntu's Grub want to load their system first, each will change the other's boot configuration if you do not disconnect the windows hard drives. Once installed though that is not an issue. To run Ubuntu you simply turn the USB hard drive on before turning your PC on. If you want to run windows just make sure your USB hard drive is turned off before you start the PC. My PC is a DELL with XP and an Intel processor. I do not know if there would be problems with an AMD processor although I do not think so 
 To exchange files and folders between Ubuntu and windows I made a small partition on my windows hard drive of 10 GB. It is in FAT32. I can then copy files from either Ubuntu or windows and place them in that partition. They can then be accessed by either system. Hope this helps.
 Bob

---

