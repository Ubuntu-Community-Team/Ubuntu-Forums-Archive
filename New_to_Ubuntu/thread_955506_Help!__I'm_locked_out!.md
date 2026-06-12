---
title: "Help!  I'm locked out!"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Sister Irene on 2008-10-22
Greetings!  Last night I installed Ubuntu and set the user name and password.  When I restarted the computer, it did not accept the user name and password.  What do I do now?  Thank you for your help.

---

### Post by Sarmacid on 2008-10-22
Wouldn't be the only option, but you can just reinstall. Seems easier since it was a fresh install, or do you really need to use the system as it is?

---

### Post by Sister Irene on 2008-10-22
Will I be able to reinstall simply by reinserting the disc?  I can't get anywhere on the computer.

---

### Post by perlluver on 2008-10-22
Yes insert the disc, and choose to install Ubuntu.

---

### Post by Sarmacid on 2008-10-22
Just reboot the computer with the cd in the tray and you should be able to install again.

---

### Post by Sister Irene on 2008-10-22
> **perlluver said:**
> Yes insert the disc, and choose to install Ubuntu.

I don't get any choices.

---

### Post by Sister Irene on 2008-10-22
> **Sarmacid said:**
> Just reboot the computer with the cd in the tray and you should be able to install again.

Same thing, I don't get any choices.  I'm stuck at the Username screen.

Is there anything I can do at startup with the F keys?

---

### Post by perlluver on 2008-10-22
> **Sister Irene said:**
> I don't get any choices.

You have to boot from the CD, in the BIOS, check to make sure it set to boot from a CD.  Otherwise not sure what you mean.

---

### Post by TyTiger on 2008-10-22
IVE HAD THIS PROBLEM!

I just rebooted the PC and it logged me in the 2nd time. 

if youve done that already then yea re-install ububntu.

---

### Post by Sister Irene on 2008-10-22
> **perlluver said:**
> You have to boot from the CD, in the BIOS, check to make sure it set to boot from a CD.  Otherwise not sure what you mean.

I rebooted from the CD, but ended up at the username screen again!

---

### Post by Sister Irene on 2008-10-22
> **TyTiger said:**
> IVE HAD THIS PROBLEM!

I just rebooted the PC and it logged me in the 2nd time. 

if youve done that already then yea re-install ububntu.

How do I reinstall?  I don't get any screens with choices.

---

### Post by Sarmacid on 2008-10-22
There are 2 ways to get to the options. When you boot your pc, you should see some messages telling you that if you press some key you'll go to bios and maybe another telling you to select boot order. Press the one for boot order and select CD. If you don't see that option, go into bios, and search around for the boot order options. There put CD at top of your list followed by hard drive. Should get the options next time you boot with the cd in the tray.

---

### Post by OldGrey on 2008-10-22
What you describe is not what happens when you boot from a live CD. It does not ask for a username, it does not require one, because there is no way of storing one. Can I check a couple of waht may seem obvious things:

1. When you input your username and password are you using the right case? e.g. the user name is _always_ lower case.

2. If you stll cannot get in and wish to reinstall, double check that your BIOS is set to boot from the CD first.

I hope that one of these works.

---

### Post by redseventyseven on 2008-10-22
> **Sister Irene said:**
> How do I reinstall?  I don't get any screens with choices.

Hmmm. Well, if you actually booted from the CD, you wouldn't have arrived at the usual login screen. First thing is to not panic, take a deep breath and slow down.

Just because the CD is in the CD-ROM drive when you turn your computer on, it doesn't automatically mean that your computer will attempt to boot from the CD. Your BIOS (which stands for "Basic Input/Output System") settings may be set so that the computer checks the Hard Drive to see if it can boot from there before it looks at the CD-ROM drive. Obviously this means that the CD drive never gets a look-in because the computer will always find that the hard drive is "bootable" and won't go on to any further options.

Fortunately you can change the order in which your computer looks at different drives to check for bootable disks. When you switch your computer on, you should briefly see a screen with the manufacturers logo on it and some basic information about your computer, before the computer starts loading the operating system (e.g. Ubuntu or Windows). On this screen, there should be a message along the lines of "Press <DEL> to enter setup". This will take you to the BIOS settings where you should be able to change the order in which your computer checks the drives for bootable disks.

Note: the actual key you have to press to get to the BIOS settings depends on the manufacturer. It's often <DEL> or F2 or F12. If the computer is booting from the CD then it should take a lot longer than usual, and you will hear the CD spinning round and the CD light on the front of the drive flashing every now and then.

Hope this helps! Enjoy Ubuntu, and remember, don't panic!

---

### Post by northern lights on 2008-10-22
You don't necessarily have to reinstall if you forgot your username and pass - it might just be the easiest, depending on how tough the following would be for you to follow:

Instead of booting the regular Ubuntu, boot into Recovery Mode. This should be the second option in the GRUB menu.
Should the GRUB menu not appear automatically during boot-up, hit the 'ESC' key when "GRUB loading - stage 1.5" appears on the screen.

In Recovery Mode, drop to a root shell and run```
useradd USER
```
and subsequently```
passwd USER
```
where USER should be replaced by your desired username (make sure you don't choose the same you picked yesterday). Reboot and log-in with newly created name & pass...

---

### Post by Duck2006 on 2008-10-22
Can you start-up in recovery mode?

---

### Post by Sister Irene on 2008-10-22
You guys are all so great!  But I've run out of time.  I'll have to try again much later today or tomorrow.  Thank you!

---

### Post by Sarmacid on 2008-10-22
> **northern lights said:**
> You don't necessarily have to reinstall if you forgot your username and pass - it might just be the easiest, depending on how tough the following would be for you to follow:

Instead of booting the regular Ubuntu, boot into Recovery Mode. This should be the second option in the GRUB menu.
Should the GRUB menu not appear automatically during boot-up, hit the 'ESC' key when "GRUB loading - stage 1.5" appears on the screen.

In Recovery Mode, drop to a root shell and run```
useradd USER
```
and subsequently```
passwd USER
```
where USER should be replaced by your desired username (make sure you don't choose the same you picked yesterday). Reboot and log-in with newly created name & pass...

Hmm, didn't think of recovery mode, but you could just change your pass instead of creating a new user :P

---

### Post by Duck2006 on 2008-10-22
At the prompt in recovery mode type.

startx

when it starts go to places, home, and see what name is used.
Open the terminal type.

passwd (user name)
type in the pass-word
retype in the pass-word

Close of the terminal, Log out and at the promp type

reboot

and it should be able to log in with your user name and pass-word.

---

### Post by northern lights on 2008-10-22
> **Sarmacid said:**
> Hmm, didn't think of recovery mode, but you could just change your pass instead of creating a new user :P
Too true - *that* did not cross my mind. Collaboration's got great benefits, doens't it...

---

