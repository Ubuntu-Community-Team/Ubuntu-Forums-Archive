---
title: "Boot disc problems"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Mitchlb on 2008-05-13
I'm trying to run a boot disc on my Ubuntu system. It's a cd that was burned from an ISO file. It should recognize in the system on startup... Instead, it lingers for 2 minutes and then loads the Ubuntu Start Up screen.... It's a new version of Ubuntu (Hardy Heron). Its recognized by my XP run system, but not my Ubuntu system. It gives me no error messages on my Ubuntu run system... It just gives me an error format. I checked the burning technique - the disc was finalized... I don't see the problem. Thanks!

---

### Post by zenwalker on 2008-05-13
I assume that u want to use this boot disk to restore some thing, then u can boot into run level 3 and do what ever u want. Just pass init 3 to the kernel image in grub. THen it wont boot u into any Graphical Systems.

---

### Post by aquavitae on 2008-05-13
Three obvious things to check - is your computer set up to boot from cd? Did the iso download correctly (you can check the md5sum for that) and did is burn correctly?  If it downloaded ok, maybe just try burning it again...

---

### Post by Mitchlb on 2008-05-13
I said that the disc works. It's been checked... And you said just press 3?

---

### Post by Xiong Chiamiov on 2008-05-13
> **Mitchlb said:**
> I said that the disc works. It's been checked... And you said just press 3?
What he actually said (though admittedly, not very clearly) was that you need to pass the argument "init 3" when booting.  You can do that by pressing whatever key it is to edit the boot options (it says on the bottom), then adding it there.  However, that is just to get into a prompt on your current Ubuntu system, rather than to boot into your CD, as far as I can tell.  If that's your problem, you'd be better off pressing alt+f2 before X starts up, which will get you to a prompt.

---

### Post by Mitchlb on 2008-05-13
Ok. I'll see if it works. Thanks.

---

### Post by Mitchlb on 2008-05-13
I'm just trying to update to hardy heron on my current gutsy gibbon. I'll test it out for a few weeks. When I pressed alt + f2, it just loaded me into PhoenixBIOS Setup Utility... It's just not reading the Ubuntu disc is all... And the disc works fine... In the  phoenix utilities, it doesn't let me do anything but enable and disable the CD-ROM drive... And since it's already enabled that would be pointless.

---

### Post by aquavitae on 2008-05-14
If you're just trying to update you shouldn't need to boot from the cd, it should recognise it as an upgrade if you put it in while running gutsy. But thats the prolem - its not, right? Alternately you could upgrade from the internet without the cd at all, unless you don't have access to the internet.

So am I right in saying that gutsy doesn't see the cd at all, but windows does?  Have you tried another cd to make sure its not a problem with the gutsy setup?

Hope I'm on the right track this time :)

EDIT: This still won't help with the booting problem, but it might get hardy on you computer, which is the aim, right?

---

### Post by Mitchlb on 2008-05-14
Yhea. That is the aim - and your right in saying that its not recognizing... Sry. I wasn't very clear in my post. How would I do it online? I have internet access.

---

### Post by aquavitae on 2008-05-15
I've only done it once (I don't have internet access) but as far as I remember there is an upgrade manager under the menus. It should be under the administration menu, but I can't remember exactly what its called, probably 'Upgrade Manager' (not at my pc right now). That should start a wizard. Alternately there is a command line - 'sudo apt-get upgrade' IIRC. It may also be possible to do it through synaptic, but I'm not sure.

If you don't find it post back and I'll check my pc.

---

