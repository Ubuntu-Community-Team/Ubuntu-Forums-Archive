---
title: "too many options at boot up"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by hfp on 2008-11-05
Hey.  When I turn on my computer the boot up screen shows me about 7 different versions of ubuntu and two versions of vista that I can choose to start up.  The screen then counts down from 7 and I have to make a choice fast or the first option (ubuntu) will automatically be choosen.  Is there any way to get all these duplicates of ubuntu off the screen?  I only really need 1 ubuntu and 1 vista.  Thanks.

---

### Post by boof1988 on 2008-11-05
> **hfp said:**
> Hey.  When I turn on my computer the boot up screen shows me about 7 different versions of ubuntu and two versions of vista that I can choose to start up.  The screen then counts down from 7 and I have to make a choice fast or the first option (ubuntu) will automatically be choosen.  Is there any way to get all these duplicates of ubuntu off the screen?  I only really need 1 ubuntu and 1 vista.  Thanks.

I can't tell you how to get rid of the extra lines.  But I figured out on my system (Ubuntu 8.04.1) that if I use the up or down arrows the counter stops so I don't have to rush to pick.

Also... thanks for asking this question.  I have seen it elsewhere but I'm not sure what to "search" for on the forums.

---

### Post by Tarvok on 2008-11-05
If you open Synaptic (System->Administration->Synaptic Package Manager), search by name for "linux", and scroll through the results, you'll find you have multiple versions of the following package installed: linux-image-[version number]-generic. This is because every time your kernel is updated, it keeps the previous versions.

This is a good thing. Sometimes you get a bad update, and while the new version won't work, you can still log in using the old version, and wait for the team to fix it.

However, once you're certain you've got a good kernel, you can safely remove the old kernels. Just mark all but the most recent for removal.

At least, this is the best way to do it I know about, and it works for me. Maybe someone else knows a more elegant way to go about it.

---

### Post by Paqman on 2008-11-05
Startupmanager is a good tool that (among other things) can limit the number of kernels displayed at boot. Set it to one (or two to be safe) and you won't have this problem.

Of course, this doesn't actually remove the old kernels. As Tarvok says, deleting the old linux-image packages automatically cleans up the Grub menu.

---

### Post by shifty_powers on 2008-11-05
two things you can do.

try something such as startup manager...

```
sudo apt-get install startupmanager
```

which can restrict the amount of past kernels you see in grub.

or, and this is to be used carefully, edit grub

```
gksudo gedit /boot/grub/menu.lst
```

and take out the lines you don't need.

be very careful doing it that way!

---

### Post by drs305 on 2008-11-05
StartUp-Manager is a great gui-based app that can manage how many kernels are displayed on the boot menu. StartUp-Manager can manage a great number of boot menu display options, all without manually editing /boot/grub/menu.lst

I've written a tutorial about it here:
[Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

To install StartUp-Manager:
```
sudo aptitude install startupmanager
```

To run:
System, Administration, StartUp-Manager

---

### Post by Eviltechie on 2008-11-05
I've found that the cruft remover helps.

---

### Post by hfp on 2008-11-06
Thanks, guys.  I guess I'll just leave it alone since it could potentially be a good thing to have so many options.  However, is there any way to get rid of the countdown?  I have discovered that it goes away once I press the up or down arrow, as boof kindly pointed out, but is there a way to make it never appear in the first place?

---

### Post by drarem on 2008-11-06
I think commenting out the timeout value should work by putting a # in front of the timeout line as such:

# timeout		10


In /boot/grub/menu.lst

---

