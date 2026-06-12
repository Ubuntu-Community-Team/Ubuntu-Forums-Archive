---
title: "Hardy nvidia problem"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by satjat on 2008-04-25
I am having strange problems since upgrading to Hardy yesterday.

Every time I start up, X starts in low graphics mode.
My graphics card is an Nvidia 6800.
Using the nvidia driver in the setup dialog fails the test. Only the nv driver passes. But still it starts in low resolution.
After X has started and log in, I go through Screens & Graphics and choose the nv driver and correct monitor once more. Now with ctrl-alt-bckspace it starts with 1680x1050 resolution as it should. The restricted driver is enabled and in use. Yet I cannot enable compiz (Desktop effects could not be enabled), manually running compiz returns 

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
 
and there is still the restart issue. When I restart it goes back to low resolution.

I reinstalled nvidia-glx-new in case something got wrong.
I tried using EnvyNG which returned no errors but still didn't work.
There are two other things to mention, not directly related but might indicate that the upgrade process was not successful.
The Grub menu did not get updated (it still shows 7.10 with 2.6.22-14 kernel) and uname -r returns 2.6.22-14-generic.
Running update grub returns:

Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

but I don't see 2.6.24-16 in any menu entry of the grub menu on startup
I know I can edit menu.lst and it should be added, but not being there and update not adding it is some kind of problem indicator.

Thank you all in advance,
Jason

---

### Post by alienexplorers on 2008-04-25
Try using nvidia-glx instead of nvidia-glx-new and see if that works.

---

### Post by reyhan on 2008-04-25
try to reinstall your Graphic card Driver

---

### Post by joshsmith on 2008-04-25
compiz doesnt work with nv. nv is not the restricted driver.

what went wrong in the update? if you dont have the new kernel, something must hvae gone seriously wrong. try updating again?

you shouldnt have to go into any dialogue to select the nvidia or nv driver, just install the driver from system>admininstration>hardware drivers and it should do it itself 

the simplest thing is probably going to be to install hardy from scratch, and that would be very easy to do

---

### Post by satjat on 2008-04-25
I will try to reinstall the nvidia drivers. I did it once already and it didn't work.
But what's your opinion on the grub/kernel issue? Should I manually edit menu.lst and use the new kernel?
Installing hardy from scratch would cost me losing a bunch of installed apps. Pretty time consuming, if there is an alternative solution.
The weird thing is I have both kernel images. They are just not added in grub. How can it be possible? I thought grub update does exactly that.

---

### Post by PmDematagoda on 2008-04-25
> **satjat said:**
> I will try to reinstall. I did it once already and it didn't work.
But what's your opinion on the grub/kernel issue? Should I manually edit menu.lst and use the new kernel?

Yes, try editing the menu.lst file manually and then boot into the new kernel, once that is done, install the Nvidia driver from Hardware Drivers in System>Administration>Hardware Drivers.

---

### Post by satjat on 2008-04-25
I used the new kernel and everything works ok.
However I am still in doubt if everything is ok, since the image was not added to the grub menu.

Anyway, I am happy now. Enjoying the Heron.

btw I don't see the "solved" option to mark the thread. Is that changed somehow?

---

### Post by PmDematagoda on 2008-04-25
> **satjat said:**
> I used the new kernel and everything works ok.
However I am still in doubt if everything is ok, since the image was not added to the grub menu.

Anyway, I am happy now. Enjoying the Heron.

btw I don't see the "solved" option to mark the thread. Is that changed somehow?

The "Solved" option is still not there at the moment, but it will be back soon.

---

### Post by patientHeron on 2008-04-28
> **satjat said:**
> I used the new kernel and everything works ok.
However I am still in doubt if everything is ok, since the image was not added to the grub menu.

Anyway, I am happy now. Enjoying the Heron.

btw I don't see the "solved" option to mark the thread. Is that changed somehow?

I confirm that it was a kernel problem for me, during the automated upgrade, i chose not to refresh the grub menu.lst file.
Sad to lose 1 precious night of sleep for that, but thanks for the solution!!!
 :guitar:

---

