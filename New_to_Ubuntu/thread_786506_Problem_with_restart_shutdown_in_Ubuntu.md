---
title: "Problem with restart/ shutdown in Ubuntu"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by dmarook on 2008-05-08
Hello everyone,

I am a Linux noob trying out Ubuntu (Hardy). I installed it in Vista through WUBI and so far I am enjoying the experience of exploring the world of ubuntu. I am totally unfamilier with various commands to use in the terminal but so far have managed to do a fair amount just by reading various posts in this forum. 

In the last 2 to 3 days I am noticing that when I try to restart or shutdown Ubuntu the process starts, the top and bottom menubars disappears then the  process seem to halt with the desktop wallpaper still showing. It does not continue untill I press Ctrl+Alt+Backspace, after which it proceeds quickly and restarts or shuts down which ever I had chosen initially. It looks like Ubuntu may be having some trouble stopping a process?? I don't know How I can check this. I have noticed this problem after I left Azureus running overnight. That had worked parfectly and I shut it down gracefully in the morning. Could it have anything to do with it? 

Another thing is my NTFS partitions seem to be randomly mounted or unmounted at startup. They are always present in Media but I see some of them on Desktop after some restarts while not after others. Should I manually unmount them before every shoutdown and remount them on startup? Could this be affecting my shoutdown problems?

Thanks in advance for any help or suggestions.

DM

---

### Post by jcwinnie on 2008-05-08
Control-alt-backspace, I will have to remember that because I have similar problems that would seem to be the result of upgrading from Gutsy Gibbon to Hardy Heron from within my wubi installation. (I saw a RTFM comment that an upgrade to Gutsy Gibbon was not possible from within wubi, so I would assume the same might be true for Hardy Heron.)

Right now, I have to shut the computer off to be able to use it again.

---

### Post by ubuntozack on 2008-05-08
wow

---

### Post by jcwinnie on 2008-05-08
Yep. Then I fially gave up trying to get the upgrade to work. I downloaded wubi-8.0.4. Of course, the install wipes anything previously done, files, configurations, other programs, etc. 

I figure it is the developers way of punishing you for keeping a dual boot system rather than switching 100% to their marvelous OS. Either that, or a way to punish you for using Ubuntu, not sure which.

---

### Post by kirios on 2008-05-08
Could it be a technical issue rather than a 'punishment'?

> **jcwinnie said:**
> I figure it is the developers way of punishing you for keeping a dual boot system rather than switching 100% to their marvelous OS. Either that, or a way to punish you for using Ubuntu, not sure which.

---

### Post by dmarook on 2008-05-09
Anyone has any solution for this trouble or should I start from scratch and reinstall?:(

---

### Post by logos34 on 2008-05-09
for mounting windows at boot try this:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

but there may be some problem because of wubi

---

### Post by kirios on 2008-05-09
I would reinstall on a separate ext3 partition instead of using Wubi.

> **dmarook said:**
> Anyone has any solution for this trouble or should I start from scratch and reinstall?:(

---

