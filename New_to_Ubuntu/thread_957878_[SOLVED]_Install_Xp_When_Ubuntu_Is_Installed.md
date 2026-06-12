---
title: "[SOLVED] Install Xp When Ubuntu Is Installed?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by cairnzi on 2008-10-24
hey people, i would like to install xp(dual boot) just so i can play WH40K Dawn Of War as it is not supported via wine,would install with 30GB partition just so windows has room to play with,but all the tutorials i have seen are install ubuntu when xp is already installed,dos anone no how to install xp when ubuntu is my OS? many thanks.:confused:

---

### Post by paul101 on 2008-10-24
is there any particular why you cant install xp first? (its a whole load easier)

---

### Post by SunnyRabbiera on 2008-10-24
Its possible to install XP after ubuntu, but fair warning it will get rid of GRUB and it will want to wipe the whole drive for itself.

---

### Post by cairnzi on 2008-10-24
@ paul and sunny, yup just checked good old giggle and yup will just re-install xp back up me files,then install ubuntu, many thanks.

---

### Post by em4r1z on 2008-10-24
There's no need to reinstall your GNU/Linux system.

1. Use a LiveCD with Gparted to set up your hard drive the way you want (the Ubuntu installation CD is fine.)
2. Install Windows XP in the desired partition.
3. Use a LiveCD to restore Grub.
In a terminal:
```
sudo grub
find /boot/grub/stage1
(Take note of where's the system you want to have control
over the bootloader and use it in the next command.)
root (hdx,y)
setup (hd0)
quit
```

---

### Post by Squish on 2008-10-24
You could also try dawn of war with winetricks. I was able to get fable running off of that.

---

### Post by cairnzi on 2008-10-24
@ em4r1z,thanks mate,didnt no i could do it that way,cheers.

@ Squish, what do you meen "winetricks" ? sorry for my ignorance.

---

### Post by louieb on 2008-10-24
Here ya go:  [apcmag HowTo dual boot]("http://apcmag.com/howto_category.htm?cid=198")  all kinds of how to dual boot with this or that installed 1st.

---

### Post by cairnzi on 2008-10-24
@ louieb,cheers mate :)

---

### Post by Squish on 2008-10-25
Winetricks is a dirty script that will replace the dll files made by wine, with actual native files from windows.
So no backwards engineered stuff, just the original windows.

Of course it wont replace every file, but it will get directx9 on there, among a ton of others you can choose. I went in and did a bit of replacing of my own, getting the native windows kernel (I think...?) and a bunch of other files.

theres a few drawbacks to it, is that you cant ask for support for it, seeing as it is not officially wine, but thats alright. Check it out:
[http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")

---

### Post by cairnzi on 2008-10-26
@ Squish, cheers mate :guitar:

---

### Post by Squish on 2008-10-27
Did you have any luck with it?

---

### Post by cairnzi on 2008-10-27
yup, seems to be working ok, had a little trouble with the installation but seems to be ok, many thanks again :)

---

