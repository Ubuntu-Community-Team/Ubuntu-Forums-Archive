---
title: "Dual Boot With WinXp on one HDD and Ubuntu 11.10 in another"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by ApNewbie on 2012-02-21
Hello,

First I must warn you all, I am a absolute newbie so please refrain from going in too deep into technicalities !!! 

**Okay Now my problem:**

I am using wine to run MS office (excel to be more specific) and the problem is the macros in the sheet are not being shown as they should. The sheet loads ok but there are few vital functions missing. So I want my WinXP back (just for the XL spreadsheets)

I like Ubuntu otherwise so now I want dual boot. I searched the internet and got many complex explanation on how to do it on a single HDD. Humnnn ... and m confused now....

**My Question:**

If I have 2 HDD's and install XP in one and Ubuntu in another will it detect both while booting? Please tell me if its possible else give a suitable solution...

Thanks in Advance:)

---

### Post by forrestcupp on 2012-02-21
It's possible to do that, but installing Windows XP will write over the bootloader, and you'll have to restore Grub to have your dual boot.

If that is the only thing you need Windows for, it would be a lot easier to just install XP in a virtual machine, and not have to reboot to get to it. Virtual machines are made to work great with things like Office.

---

### Post by QIII on 2012-02-21
The way fraught with the least danger if you want to dual boot is simply to install each OS independently and on different hdds by disconnecting the other drive.

Plug in the drive you want, install OS.  Unplug that drive, plug the other in and install the other OS.

Plug in the first drive so both are connected.

Next time you boot, have the boot order set to boot first to your Ubuntu drive.  Log into Ubuntu and run the following in the terminal:

```
sudo update-grub2
```

or

```
sudo update-grub
```



That will add Windows to the GRUB selection list.

---

### Post by BlueAZ on 2012-02-21
Hi -- I'm a newbie, & also am running W-XP + Ubuntu on 2 HDD's in my computer.  This is the first post I've seen about this situation.  I built a fast new 64-bit computer & installed Ubuntu 11.04 from a CD.  Still had XP, 32-bit,  on an old computer that was fading fast.  Finally I got up the courage to transplant the XP HDD into the new box.  The HDD running Ubuntu is SATA; the XP one is an IDE connection.  I thought I'd have to reregister XP, but a quick conversation with a MS tech got it solved.
Now I can boot into either.  XP runs slower, but it's acceptable.  The way I switch is to hold down the Delete key after pressing the On button.  That brings up the boot menu, where you have to use keyboard arrows & Enter key only.  Then under Advanced, I click Hard Drives, & it lets me select 1st boot device.  I've learned the numbers assigned to each HDD, so I choose which one, then F10, Enter, & it boots.  If there's an easier way, I'd like to know it!
When I tried to upgrade to 11.10, I just got a blank screen, & had to reinstall 11.04 over that hard drive.  How did you get it to work?

---

### Post by Mark Phelps on 2012-02-21
> **BlueAZ said:**
> ... When I tried to upgrade to 11.10, I just got a blank screen, & had to reinstall 11.04 over that hard drive.  How did you get it to work?

This is an upgrade question/issue -- not a dual boot question.

Please don't send this thread down a different path with a different issue.

Please start your own thread for your own issue.

---

### Post by ApNewbie on 2012-02-21
Thanks all of you for the replies:) 

Especially forrestcupp and QIII.
I will check it out today and let you guys know

Thanks again

---

### Post by ApNewbie on 2012-02-22
Okay I installed VirtualBox from the Ubuntu S/W center and installed Ms Office in my WinXP VM, it works like charm:p

I would suggest anyone who just wants to run a few applications on Win System then, go for VM (VirtualBox), **however** for games dual booting will perhaps be the best option as they get stuck when I tried to run them on VM. {prolly because of the low memory and limited graphics}

Thanks

---

