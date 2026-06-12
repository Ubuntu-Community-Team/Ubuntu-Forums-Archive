---
title: "help"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by blake7 on 2008-06-13
hi this tex below is tryijng to help me get lost data back

question  how do i enter bios and ensure cd drive is set to boot ahead of hard drive.?????



below is the advice iam folling:-
the process goes something like this:

1) insert ubuntu live cd into cd drive.
2) reboot computer.
3) enter bios and ensure cd drive is set to boot ahead of hard drive.

Now let the computer boot from the cd, and select the option to try ubuntu without changing your system,

Eventually you will get an ubuntu desktop (it will take a while) which is running entirely from the cd drive.

You will then need to 'mount' the hard drive you want to rescue data from. I noticed that you said you are using wubi, so this guide will be handy, it tells you how to mount the wubi hard drive.

[https://wiki.ubuntu.com/WubiGuide#he...cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#he...cef9e81cd675b7)

At this point you can copy the data from the mounted wubi drive. You could paste it onto a usb key, or you could probably just drop it into a folder in the mounted windows drive somewhere. You should then be able to get at the files from within windows.

Hope thats useful
issih is offline Report Post   	Reply With Quote

---

### Post by forestpixie on 2008-06-13
Usually when you boot you will get a message - del toenter setup, esc to enter setup or an F kewy to use.

That should get you into the bios then find the boot order and set it to boot from cd first. Save changes - F10 for me

PC will reboot and if you have cd in tray it will boot it first

---

### Post by hyper_ch on 2008-06-13
you should use a descriptive thread title that reflects the content of your problem and not a generic "noob here" or "need help".

---

### Post by Voland on 2008-06-13
You can use F2 or Del key to reach BIOS setup. There you can get Boot menu option. Use it to change boot media order. Another one variant is to use F8 key. It is a qute new option to select boot media instead to setup BIOS.

---

### Post by blake7 on 2008-06-13
iam loading from a live cd 

it give me nothing that you said, i get a menue but not any ing you wrighten

---

### Post by forestpixie on 2008-06-13
This is all way before that - it's when you first turn the pc on

---

### Post by blake7 on 2008-06-13
got it i have ibm x60 and for some reson its the blue vantage button

ok
right

---

### Post by blake7 on 2008-06-13
thanks everone

now i got to mount the hard drive how do i do that i load up the os and it gone stright into the desk top

what next

thanks for your time

---

### Post by Bradtek on 2008-06-13
IBM Thinkpad Bios

While the "To interrupt normal startup, press the blue ThinkVantage button" message is displayed at the lower-left of the screen, press the F1 key.

Edit:  I guess I'm too late ;P

---

### Post by forestpixie on 2008-06-13
> **blake7 said:**
> thanks everone

now i got to mount the hard drive how do i do that i load up the os and it gone stright into the desk top

what next

thanks for your time

Follow the link you were originally given to get the drive to mount the virtual disk - [https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

> Now the content of the virtual disk will be visible under /vdisk. 

Other than that I can't help - never used wubi at all

---

### Post by blake7 on 2008-06-13
does any one live in london?
 i can come around and go thought all this 
its all to deep for me

help

---

### Post by blake7 on 2008-06-13
iam just trying to safe some lost documaents

thats all

what is my best option

---

### Post by forestpixie on 2008-06-13
Have you tried the commands it gives - also it could be that your win partition isn't sda1 so open a terminla in the buntu livecd and run this command

```
sudo fdisk -l
```

---

### Post by blake7 on 2008-06-13
hi been try ing to save documants after accidently deliting wubi
i try doing all that the great helper here offer, but i just can get my head around it all. 
can i meet someone who can simlpe just do it 
its ubuntu 8.4 i have a ibm x60

help or do you no any one who could help

cheers

---

### Post by forestpixie on 2008-06-13
You have already been asked to use sensible thread titles in your other help thread. I understand that you might be getting frustrated but what exactly can't you get your head round - the link you have is quite simple to run.

If you need help with getting it to run then ask questions and say what's going wrong if it is.

---

### Post by PmDematagoda on 2008-06-13
The two threads on the same main issue have been merged.

---

### Post by forestpixie on 2008-06-13
If this is the same data that you first started trying to recover in your thread from 3 weeks ago and if in the meantime you have been using windows then I would expect that the original wubi installation you deleted is probably unrecoverable by now.

---

### Post by blake7 on 2008-06-14
no i have not touched my laptop since this happened
i wish i could just go so where and some one help me

---

### Post by forestpixie on 2008-06-14
Have you actually followed the instructions in the link that you have been given.

Post the output of 

```
sudo fdisk -l
```


Edit - boot the livecd to do this, then you will be in the right environment to run the remaining commands and be in a position to find out whether the data is there or not.

---

### Post by blake7 on 2008-06-14
ok i so that just feel the desprate right at the moment

---

### Post by forestpixie on 2008-06-14
You have been given the information you need, no-one else going to come and rescue you. Once you've run the fdisk -l command you can then do the commands in the wubi page, then you'll be able to see if it is actually there.

---

### Post by blake7 on 2008-06-17
what does that all mean
where do i put in that command

---

### Post by forestpixie on 2008-06-17
Once you have the livecd booted - open a terminal it is in accessories menu,

the command you need are here

[https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7](https://wiki.ubuntu.com/WubiGuide#head-d08dd29d8d72682732b0bdb835cef9e81cd675b7)

If there are any errors paste the whole error and what you did here

---

### Post by blake7 on 2008-06-18
thank you 
i try that

---

