---
title: "Kubuntu boots to grey screen"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by QuantumCaffeine on 2012-09-25
My system was working fine, and then suddenly today when I booted up it presented me with just a grey screen. I could hear the welcome chime playing, so I'm pretty sure it booted up and logged me in properly, but in place of the desktop all I get is a blank grey screen.

Now, I haven't done anything terribly adventurous with my system, and didn't install anything new yesterday, so what could have gone wrong? Has a graphics driver update gone wrong or something? It's an AMD Llano A8-3850, using the integrated graphics via the radeon driver, and I'm running kubuntu precise.

Any help would be greatly appreciated; I'm stuck in Windows now and want to get back home. :)

P.S. Should probably have said that: I dual boot with Windows, and Windows is still working fine (or as well as it ever does :p) so I doubt it's a hardware issue.

---

### Post by bra|10n on 2012-09-25
Could be a kernel issue. If you have any older kernels installed you can try booting with an older version (hold down shift key on start). If so grub will show a choice of kernel versions, select a different one (any but the one highlighted).

If not, and as you say nothing is indeed new or updated since your last successful login then this points to a kdm error. Search for the latest threads in google accordingly.
HTH

---

### Post by cortman on 2012-09-25
If you can select "Recovery mode" from the Grub menu you can remove/reinstall KDM.

---

### Post by QuantumCaffeine on 2012-09-25
> **bra|10n said:**
> Could be a kernel issue. If you have any older kernels installed you can try booting with an older version (hold down shift key on start). If so grub will show a choice of kernel versions, select a different one (any but the one highlighted).

If not, and as you say nothing is indeed new or updated since your last successful login then this points to a kdm error. Search for the latest threads in google accordingly.
HTH

Switching back to the previous kernel seems to have fixed things, mostly. I was on 3.2.0-31-generic, and reverting back to 3.2.0-30 has brought the screen back. The failed boots had caused KDE to disable OpenGL, but the odd thing now is that when I re-enable it, I have to disable shaders and vsync to get decent performance (otherwise everything stutters when e.g. moving windows). Since I had them enabled before with no issues, I'm assuming there's also some kind of graphics driver issue here.

Anyway, the main thing is that I've got my desktop back, so thanks! Is it now just a case of waiting for the next kernel and/or driver update to fix some bug that's crept in, or is there something else I should do to stop the problem coming back?

---

### Post by QuantumCaffeine on 2012-09-25
> **cortman said:**
> If you can select "Recovery mode" from the Grub menu you can remove/reinstall KDM.

Thanks, but since reverting to a previous kernel version has fixed the problem (see previous post), I'm guessing it's not a KDM issue?

---

### Post by bra|10n on 2012-09-25
@QuantumCaffeine,
Good news and no, not *likely* a kdm problem. 
But it would be wise to read up on the issues of both kernel versions, the one that caused you the problem and the one you are now relying on. Note the changes from the earlier to the newer version keeping in mind your hardware and observations as you *tentatively* use your Kubuntu install.
Back up important data of course, even if it is for ease of access purposes only should such issues arise again.

#kubuntu irc is also a good idea, even if you only read through the logs...
Best wishes

Edit
You might read up on the experiences of those with kubuntu-backports ppa enabled, not sure what versions of kde and kernel it contains though.
Running kernel 3.4.6-1 and kde4.9.1-1 here on Intel but not on Kubuntu.

---

### Post by james_xxx on 2012-10-19
I am experiencing some kind of similar problem, as of today, in 12.04. The only difference is that a black screen comes up, after entering my password in KDM.

I do get a pointer in the middle of the screen, but everything else is black, and I have no network (wired or wireless).

This is using onboard Intel graphics.

I've tried booting into 3.2.0-31 & -30, but neither responded any differently.

---

### Post by buckyaustin on 2012-10-19
This is just a precautionary measure. But boot up your computer and edit your bios that network boot is at the top of your boot order. This seems to stabilize Ubuntu. It has fixed kernel errors for me in the past. So often that I do it now just out of superstition.

---

### Post by james_xxx on 2012-10-19
buckyaustin,

Interesting, I had never heard of that.

I'm not sure what happened, but I suspect strongly that an update broke things.

I have network going again, and though this is probably a backwards way of going about things, I going to go ahead and dist-upgrade to Quantal, and see if things are not fixed there. :)

---

### Post by bra|10n on 2012-10-19
@james_xxx,

Did you happen to apply recent updates using Muon (via either of it's 3 personalities)?

I confirmed this method as a fail a few days ago. Using the CLI after a fresh install worked flawlessly...

EDIT:
Reading your last post the upgrade will likely be larger than downloading a 12.10 iso.
Of course the choice is yours, but if the upgrade fails, or fails to rectify your current issue, then what...

---

### Post by james_xxx on 2012-10-19
Well, I did the upgrade, and it did not fix things.

However, installing the kubuntu-desktop meta-package did. :)

I should have thought of that early on.

I have a habit of getting rid of a lot of things in Kubuntu that I don't want, which of course does away with kubuntu-desktop.

Most of the time, this does not matter, but every once in a while it begins to matter a lot.

All is well that ends well!

---

