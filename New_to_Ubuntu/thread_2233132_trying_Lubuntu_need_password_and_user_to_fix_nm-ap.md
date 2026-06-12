---
title: "trying Lubuntu need password and user to fix nm-applet bug"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by taff2 on 2014-07-06
Hi! Newbee here. I want to try Lubuntu on my old Dell XP laptop but I need to make sure I can access wireless before I get rid of Windows XP. I tried Lubuntu on an old Toshiba A10 but could not resolve wifi issues (still working on it actually). I like Lubuntu so far, however. After i fix the nm-applet bug (so wireless networks show up for me to choose from) I have to log out. When you log out while trying, not a hard install/replacement it wants a user password, which you don't set up on trial. Can this be done - fix the nm-applet bug and try Lubuntu without a complete install? 

Thanks in advance.

---

### Post by grahammechanical on 2014-07-06
Just to be clear. You are on a Lubuntu live session and you log out and are then asked for a password to log in again. Try pressing enter.

Regards.

---

### Post by taff2 on 2014-07-06
Pretty sure I tried that but I'll try again. Give me a minute to reload.

---

### Post by mörgæs on 2014-07-06
Best you can do is to run **sudo lshw -sanitize > lshw.txt** and post lshw.txt in CODE tags for both computers using a wired connection.

---

### Post by taff2 on 2014-07-06
Nope. enter does nothing but keep asking for password. Maybe you can't fix any bugs with "live CD". Is there any Linux product that will automatically find wireless networks? Debian, Mint, Puppy, any? I've never had good results inputting all the network data from scratch - Mac address, ssid, etal.

---

### Post by Dennis N on 2014-07-06
From the live session, start the network applet from the terminal by typing **nm-applet** and then enter. It will then detect any networks and an icon will show on the panel. Click on the icon to select your network, and supply the network's pass phrase in the dialog that pops up to connect.

The nm-applet bug (where it does not display in the panel) will be fixed when you upgrade your packages. It was fixed a couple of days ago.

---

### Post by Vladlenin5000 on 2014-07-06
> **Dennis N said:**
> From the live session, start the network applet from the terminal by typing **nm-applet** and then enter.

I spotted this bug in 2 installations back with 13.10. If I remember correctly, it worked fine in the live session but not when installed and it automatically connected to the network used in the live session and installation. It wouldn't of course had I use Ethernet.

---

### Post by Dennis N on 2014-07-06
> If I remember correctly, it worked fine in the live session but not when installed

No, I tested the live session before posting to be sure - network manager applet did not show in the panel and it did not start.

---

### Post by taff2 on 2014-07-06
Hey thanks. It brought up the applet as long as dos window stays open but it doesn't show any networks. I think I had to update things on another computer i actually installed Lubuntu on (that's the one that won't take my password - i think because of some router issues and compatibility). Thanks anyway.

---

### Post by taff2 on 2014-07-06
I guess I could do a dual laod of Lubuntu along side my old windows XP and see if after updated, etal if it'll work then.

---

### Post by Dennis N on 2014-07-06
> **taff2 said:**
> Hey thanks. It brought up the applet as long as dos window stays open but it doesn't show any networks. I think I had to update things on another computer i actually installed Lubuntu on (that's the one that won't take my password - i think because of some router issues and compatibility). Thanks anyway.

You have to keep the terminal open during your session or the network manager will shut down. When you are ready to quit, you can also use Ctrl-C in the terminal to end. Not showing any networks when you know one is available is an problem with the network card that most likely can be fixed. There is a forum on networking here that should provide assistance.

---

### Post by taff2 on 2014-07-06
I'll have to check in to that later. Thanks for the info.

---

