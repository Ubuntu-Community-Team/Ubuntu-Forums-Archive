---
title: "Ubuntu 12.04 duel screens, one screen white"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by Fails101 on 2012-08-01
I just got Ubuntu up and running (thanks to the help of people here), but I have two screens and one of them is white and when I move my cursor over to the white screen it turns into a black X. I've tried searching for a solution, and though the problem seems to be fairly common I haven't found a solution. Help? Thanks in advance!

[I'm fairly sure it's not relevant, but the screens are acers and my graphics card is the GeForce GTX560 Ti, so I know it can handle them both....]

---

### Post by levlaz on 2012-08-01
Did out install the proprietary driver? If so which one?

---

### Post by Fails101 on 2012-08-01
> **levlaz said:**
> Did out install the proprietary driver? If so which one?


I have the NVIDIA accelerated graphics driver (post-release updates) (version current-updates) installed. (I hope this is what you are talking about...)

---

### Post by levlaz on 2012-08-01
Did you try to mess with the settings? 

Sudo nvidia-settings

---

### Post by Fails101 on 2012-08-01
> **levlaz said:**
> Did you try to mess with the settings? 

Sudo nvidia-settings
  
Yes, I have. It doesn't change it. :(

---

### Post by levlaz on 2012-08-01
Looks like this is a [bug]("http:// http://askubuntu.com/questions/146908/nvidia-settings-makes-one-of-my-dual-monitors-grey-and-useless-disables-network")... 

I would try either selecting the "recommended" driver instead of the post release one or disabling the restricted drivers all together. What type of work do you do? You may be able to get away with the "free" driver until this bug is fixed.

---

### Post by Fails101 on 2012-08-01
> **levlaz said:**
> Looks like this is a [bug]("http://%20http://askubuntu.com/questions/146908/nvidia-settings-makes-one-of-my-dual-monitors-grey-and-useless-disables-network")... 

I would try either selecting the "recommended" driver instead of the post release one or disabling the restricted drivers all together. What type of work do you do? You may be able to get away with the "free" driver until this bug is fixed.

I have tried that and it didn't work. :(
I'm a programmer, so it's not vital that I have the other screen up and running, it would just be convenient....

Also, I'm not sure what you mean by "'free' driver" ?

Thanks for helping me. :)

---

### Post by levlaz on 2012-08-01
Lol what I meant to say was that this is a bug... so Im not sure there is much you can do at this point. 

Sorry I'm writing on a tablet and its hard to be descriptive on this thing lol. 

Since you're a prorammer maybe you can help fix the bug. :-) 

Either way what I am suggesting is that you disable all of the nvidia drivers. You should be able to simple deactivate them all in the restricted drivers menu. 

If no proprietary drivers are installed on your system the "free" ( as in free and open source) driver will take over and maybe it will work just fine.

Once you disable the nvidia drivers... reboot your computer.

---

### Post by Fails101 on 2012-08-01
> **levlaz said:**
> Lol what I meant to say was that this is a bug... so Im not sure there is much you can do at this point. 

Sorry I'm writing on a tablet and its hard to be descriptive on this thing lol. 

Since you're a prorammer maybe you can help fix the bug. :-) 

Either way what I am suggesting is that you disable all of the nvidia drivers. You should be able to simple deactivate them all in the restricted drivers menu. 

If no proprietary drivers are installed on your system the "free" ( as in free and open source) driver will take over and maybe it will work just fine.

Once you disable the nvidia drivers... reboot your computer.

Ohhh. :) Haha, I wonder if they let random programmers help them with bugs.... [I'm very new to Ubuntu; I'm used to terminal though, as odd as that seems].

I'm not sure exactly what fixed it [I've been messing around trying to see what would fix it], but it's fixed now. Thanks for all your help! :D

---

### Post by levlaz on 2012-08-01
I am glad its working! 

If you figure out what changed post it here so that in the future either people with similar issues can fix it easily. 

One of the best ways to support the community is to document your success ... and failure :-)  

Welcome to Ubunutu I am sure you will love it!

---

### Post by Zammmo on 2012-08-05
I just installed Ubuntu 12.04 and had a very similar problem to this.

Initially,  my second display was showing as disabled and it wouldn't let me enable it

The command "sudo nvidia-settings" was very useful, as I couldn't find a way to get into these setting via the GUI

I managed to enable the second screen but upon restarting the X server it totally crashed my PC. I shut the computer down, it restarted and both screens came on.

Now I had a new problem. The second display would not show the back ground image, it was just white and when I tried to open up the display settings window to change it, the window did not open properly. I was able to change the settings (although it had no effect) but I could not close the window, move it to the primary display or open up the display setting window on the primary display. Very annoying.

I got around this problem by removing both of the default nvidia drivers from my system. I restarted my computer and it worked perfectly.

Having the launcher bar showing on both screens is a bit annoying, still trying to figure that one out.

---

