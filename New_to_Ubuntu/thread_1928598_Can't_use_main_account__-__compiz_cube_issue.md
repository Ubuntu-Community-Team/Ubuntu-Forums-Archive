---
title: "Can't use main account  -  compiz cube issue"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Essam EM on 2012-02-20
Hey guys, 

I just downloaded the latest version of Ubuntu yesterday.

I enabled the cube effect on my user account but since then all I can see on my screen is the purple wallpaper. The programs on the left are nowhere to be seen, neither is the bar that is usually at the top. When I type something, a small white bar appears in the bottom right corner of the screen with the text I entered.

I can still access the guest account, though.

Can someone please tell me the solution to this problem?

Thanks

Essam

---

### Post by rg4w on 2012-02-20
If you can open Terminal (try /usr/bin/) you can enter this command to restore Unity:

unity --reset

---

### Post by Essam EM on 2012-02-20
Hi rg4w,

Thanks for your help.

I tried typing in 'unity -- reset' in the white bar in the bottom right hand corner, but nothing happens.

I can't get the terminal up, there is nothing on the screen except for the wallpaper and my mouse pointer. Is there a keyboard shortcut to bring it up or something?

Thanks

Essam

---

### Post by rg4w on 2012-02-20
The white box won't do it. You'll need to use the menus to open a file system window, then navigate into /usr/bin to find Terminal.  

I hosed my own Unity once while playing around, so I've had the exact same problem. :)

---

### Post by Essam EM on 2012-02-21
Thanks a lot rg4w, everything's works with 'unity -- reset'. :D

---

### Post by rg4w on 2012-02-21
If you want to try enabling the cube, several articles (OMG Ubutun and elsewhere) suggest first disabling the Unity plugin in CCSM, then setting up the Cube stuff, then -- and this is the most important step, as you've discovered -- re-enabling the Unity plugin BEFORE closing CCSM.

With that recipe I've successfully set up the Cube in 11.10.

---

