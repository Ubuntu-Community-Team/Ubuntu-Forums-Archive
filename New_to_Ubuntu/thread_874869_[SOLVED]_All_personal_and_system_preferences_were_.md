---
title: "[SOLVED] All personal and system preferences were erased!"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by nathanscottdaniels on 2008-07-30
AHH!  Just as I was starting to forgive Ubuntu, I turn my computer on and BAM.  Everything was like a fresh install.  All of my panels were back to the awful defaults, my desktop background reverted to that bird thing, my network setting killed themselves, I lost my FF profile, and all my visual preferences reverted to default.  Basically every setting under System => Preferences and System => Administration were lost as well as every application's setting.

The only change I made to my system was install some XP and Vista fonts so web pages looked normal and then I ran this command:

```
sudo fc-cache -fv
```

because this site told me to: 
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/) 

Do you think this had anything to do with it?  If not, how can I prevent this from happening again?

On a similar note, how do I get that wireless network icon to appear on the panel?  You know, the one that shows four bars representing the signal strength and if you right click on it, you can choose the wireless ssid.  The Network Monitor app only shows two computer monitors flashing.

---

### Post by SunnyRabbiera on 2008-07-30
well usually its unwise to run commands you know nothing about, make sure to check your sources for such things.
Now how old is your current ubuntu installation?
This may be the telltale signs of a bad burn and a bad install, give us all the information you can so we can help.

---

### Post by nathanscottdaniels on 2008-07-30
> **SunnyRabbiera said:**
> well usually its unwise to run commands you know nothing about, make sure to check your sources for such things.
Now how old is your current ubuntu installation?
This may be the telltale signs of a bad burn and a bad install, give us all the information you can so we can help.

I am running Ubuntu 8.04.  I installed it a little more than a week ago (7.1 had been on there for almost year prior but I formatted that partition and started fresh with 8.04)  

My laptop is painfully lacking support from Ubuntu so a lot of my drivers are restricted (ATI chipset and Broadcom Wireless) or no-existent (mouse, printers, second monitor).  

There was an error as I logged in that said something like the gnome-panel could not be loaded and it asked me If I wanted to delete it and I said no.  I have had a problem with my panels reseting or vanishing a few days ago but I fixed that.

That is about all the info I have.

---

### Post by SunnyRabbiera on 2008-07-30
Yeh the ATI and broadcom issues are famous, they are not our fault mind you as most of those kind of companies hate linux.
I am sorry you had so many issues, its how things are sometimes though but we do our best to fix the issues given to us.
Remember ubuntu is community driven, not run by some big company with more cash then brain cells.
The release of hardy has caused many issues admittedly, thats why its best to try more then one linux flavor.

---

### Post by philinux on 2008-07-30
Try rebooting.

Once logged in have a look in your home folder. ctrl h to show hidden files. See if everything is still in tact.

Have you got home on its own partition or did you install to full disk?

---

### Post by nathanscottdaniels on 2008-07-30
I restarted and nothing bad happened. (YAY!)  And my Home folder, while mostly empty, is on the same partition as the rest of my Ubuntu stuff.  (I forgot to mention I am dual-booting XP and Ubuntu temporarily until I build my next PC and remove XP off this one)

Also, restarting gave me that network icon in the staus area that I was talking about in the original post.

---

### Post by philinux on 2008-07-30
> **nathanscottdaniels said:**
> I restarted and nothing bad happened. (YAY!)  And my Home folder, while mostly empty, is on the same partition as the rest of my Ubuntu stuff.  (I forgot to mention I am dual-booting XP and Ubuntu temporarily until I build my next PC and remove XP off this one)

Also, restarting gave me that network icon in the staus area that I was talking about in the original post.

Good stuff. It sounds like it logged you in as root or something failed.

A reboot sometimes sorts things out.

---

### Post by nathanscottdaniels on 2008-07-30
You misunderstand.  I had already fixed my preferences before posting to this forum.  So that restart just proved that whatever happened before, did not happen again.  At any rate, I don't think that should happen again as long as I am careful.

---

### Post by SunnyRabbiera on 2008-07-30
well tell us if it does happen again okay?

---

