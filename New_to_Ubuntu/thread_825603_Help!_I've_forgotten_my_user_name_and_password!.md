---
title: "Help! I've forgotten my user name and password!"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by dandenbear on 2008-06-11
Hello all!
I just installed Ubuntu yesterday-my first experience with a non-windows environment.  Today I booted up my system and it asked me for my user name and password. I have no clue what I set up for myself!

Is there a way to retreive this info?  Or do I have to reinstall Ubuntu (which would not be that big of a deal, as I have not useed it enough to have anything worth saving.)

Thanks!

---

### Post by haldean on 2008-06-11
The easiest way would definitely be to reinstall. As far as I know, the only way to get the password off of the computer would be to use a liveCD and bruteforce the password, but that usually takes days/weeks, so if it's not an issue just wipe and start again would be my advice.

A second opinion might not be a bad idea, though ;D

---

### Post by aquavitae on 2008-06-11
Reinstall. That's part of linux security - if you don't have a password, you can't use it. There's quite a lot of things you'll need that password for (e.g. installing stuff), so when you reinstall set it to something you'll remember.

---

### Post by drascus on 2008-06-11
there is no way to retrieve it but there is a way to reset it. first generally when you go to the log-in screen your user name will be displayed in the bottom right hand corner of the screen. you will see something that say blahblahblah-desktop or blahblahblah-laptop that blahblahblah is your screenname. well it is if you are the root user anyway. so with that information (write it down and remember it is case sensative) restart your computer when you see the word GRUB press Esc key. Then select the recovery mode from the menu. 

the computer will boot and present you with a shell. this is what to enter

> passwd <your username>

then enter your new password

then type 

> reboot

that should do it your password is changed

---

### Post by dandenbear on 2008-06-11
:KS
Wow! That was quick!  Don't you guys have better things to do in the middle of the night???

Thank you so much!  I will try drascus' advice and if that doesn't work, I will reinstall.  

Now go to bed!  :)

---

### Post by adityakavoor on 2008-06-11
this will help

[http://www.downloadsquad.com/2008/05/12/stupid-ubuntu-tricks-5-steps-for-resetting-a-forgotten-password/](http://www.downloadsquad.com/2008/05/12/stupid-ubuntu-tricks-5-steps-for-resetting-a-forgotten-password/)

---

### Post by forestpixie on 2008-06-11
> first generally when you go to the log-in screen your user name will be displayed in the bottom right hand corner of the screen. you will see something that say blahblahblah-desktop or blahblahblah-laptop

You can get your username with

```
ls /home
```


> Wow! That was quick! Don't you guys have better things to do in the middle of the night???It's the middle of the day here :)

---

