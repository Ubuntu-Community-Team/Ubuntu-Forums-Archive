---
title: "Strange Kubuntu Behavior"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by sheepofandromeda on 2013-11-27
I have been using Linux off and on for a few years now, but I never really got that deep into it.

Perhaps it was a bad decision to get my grandparents a new computer that ran Ubuntu.  Not because of the OS itself, but due to the fact that there are problems already on day one.  I love Ubuntu, but it is frustrating to get a new computer and to have it need to be troubleshooted.

A few different things happened.  First off, the install of the initial Ubuntu OS (12.04) wen't smooth enough.  But there were problems immediately when it tried to update.  When it got to the part where it updates the Linux headers and such, the updater said it encountered a problem.  I ignored it and continued on, only to have the screen go all visually corrupted and stop sending signal upon the screen's auto-lock.

I thought, no problems.  I'll just install Kubuntu, KDE will be a bit more familiar to them anyway.

Upon my installation of Kubuntu, I immediately noticed something strange with the fan.  It keeps going at variable speeds, fast then slow, fast then slow...almost like a cycle.  It also keeps giving me something about trying to fix a 'recursive error' or some thing of the sort whenever logging off or shutting down.  Having to manually power off the comupter every time I want to log off is a bit of a hassle.

What should I do?  Is there any way to fix these things, or would it just be wise for me to return the computer. It is an Asus Eeebox, and the fact that it came with Ubuntu instead of Windows seemed attractive to me at first, but now I am wondering if I made the wrong call.

---

### Post by sbnwl on 2013-11-27
Do you have patience.. Don't panic. Everything will be alright.
Give one more try, but this time install Ubuntu/Kubuntu 13.10 instead of 12.04.
There won't be any problems, as the newest kernel version 3.11 has many power saving improvements. The fan will be quiet most of the times.
Report back.

---

### Post by oldos2er on 2013-11-27
> **sheepofandromeda said:**
>   But there were problems immediately when it tried to update.  When it got to the part where it updates the Linux headers and such, the updater said it encountered a problem. 

Can you post all the output from the following command? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by craig10x on 2013-11-27
Ubuntu 13.10 is really solid..and the power management improvements since 12.04 are very obvious...i'd give that a try if i were you...

---

### Post by sheepofandromeda on 2013-11-27
I apologize.  The owners of the computer were quite hasty last night and I was in a bit of a panic.

The version of Kubuntu I installed was 13.10.  Should I try just installing regular Ubuntu instead?

Also, I will post the output once I return home, I am on a different computer, so I can't at the moment.

---

### Post by oldos2er on 2013-11-27
No rush.

If the error you saw was a mergelist error, you can try the following commands to correct it. ```

sudo mv /var/lib/apt/lists /var/lib/apt/lists-old


sudo mkdir -p /var/lib/apt/lists/partial


sudo apt-get update

```

---

