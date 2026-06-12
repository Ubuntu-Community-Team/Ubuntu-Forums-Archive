---
title: "Ubuntu stuck at start up"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by seeker.k3 on 2012-04-28
Hi Folks
I can't start Ubuntu. I installed 11.10 (32-bit) a few months ago alongside Win7. I've learnt some of the simple commands in the Terminal, and removed a couple of packages. There's no reason to think that caused a problem, but it 'feels' like it did. After that, I couldn't shut Ubuntu down or log off properly, so I finally turned it off with the power button. Now, at start up, I get the default 11.10 screen and the login box, which I wouldn't normally. When I enter my password, the screen goes blank for a few seconds, and then I'm back at the same default screen with login box. The screen that I get at start up doesn't allow me to choose between 2D/3D/Gnome. 

I'd appreciate any suggestions. Thank you.

---

### Post by androssofer on 2012-04-28
> **seeker.k3 said:**
> Hi Folks
I can't start Ubuntu. I installed 11.10 (32-bit) a few months ago alongside Win7. I've learnt some of the simple commands in the Terminal, and removed a couple of packages. There's no reason to think that caused a problem, but it 'feels' like it did. After that, I couldn't shut Ubuntu down or log off properly, so I finally turned it off with the power button. Now, at start up, I get the default 11.10 screen and the login box, which I wouldn't normally. When I enter my password, the screen goes blank for a few seconds, and then I'm back at the same default screen with login box. The screen that I get at start up doesn't allow me to choose between 2D/3D/Gnome. 

I'd appreciate any suggestions. Thank you.

okey dokey. Seems liek you removed a package to do with unity...

at the login screen hit:

```
ctrl alt F1
```

it will bring up a blank screen saying:

```
ComputerName: Login:
```

type your username, hit enter, then your password, hit enter

now your in! then do:

```
sudo apt-get update
```

then

```
sudo apt-get install --reinstall ubuntu-desktop
```

then

```
sudo apt-get install unity
```

and that should re-install unity for you.. then it SHOULD work..

---

### Post by seeker.k3 on 2012-04-29
[SIZE=2]Thanks very much for your reply. Unfortunately, it has worked for me. I got up to the bit about the blank screen. That's not to suggest it wouldn't work, but blank screens are a feature of my computer. I can't see the boot menu either, but I can still blindly use my arrow keys, and it works fine. (I've never actually seen the boot menu, but I use it all the time.) 
 
Is there any way I can execute your instructions from a Ubuntu CD? Is there someway I can add the path?[/SIZE]

Thank you once again.

---

### Post by Gone fishing on 2012-04-29
I think you might have miss understood.

When you get to the login screen don't login just ctrl alt F1 and follow the instructions.

---

### Post by seeker.k3 on 2012-04-29
When I get to the login screen, I can't go further. At that point, if I hit ctrl + alt + F1, the screen goes blank. The end.

Thanks for your comments.

---

### Post by androssofer on 2012-04-29
> **seeker.k3 said:**
> When I get to the login screen, I can't go further. At that point, if I hit ctrl + alt + F1, the screen goes blank. The end.

Thanks for your comments.

no prompt on the top left?

try just typing your username and password as if there was a prompt. Then hit enter a few times...

so if the screen is off the top it should come down into view...

aside from tht, i have no ideas...

---

### Post by codingman on 2012-04-29
Try pressing CTRL-ALT-F1 through F6 and see if any of those work.

---

### Post by codingman on 2012-04-29
Wait, wait, wait, if it shows the login screen but does not work if you press CTRL-ALT-F1,then you have got a broken Ubuntu!

---

### Post by seeker.k3 on 2012-04-30
Thanks for all your comments and helpful advice.
Ctl Alt F1 (or F2, F3....) just sends me to a blank screen. It's probably working, but I often can't see things like that on this computer. It's hard to image that Ubuntu broke so easily. I really just think it's something minor; something with Unity. I wouldn't mind trying a different install anyway, so I won't waste anymore time on this. I'm glad to have learnt the ctl alt F1 sequence, and I'll practice it so that I'm ready next time. 
Thank you.

---

