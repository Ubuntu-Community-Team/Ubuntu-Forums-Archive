---
title: "ATI Hibernation/Suspend problem"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by UanarchyK on 2008-08-26
I decided a few days ago (with basically zero prior linux experience) to take the plunge and replaced XP with Hardy Heron 8.04. All went more or less swimmingly, a few headaches here and there, but nothing with which Google/ubuntuforums couldn't help.

I installed ubuntu on a Dell E1505 with an ATI Mobility Radeon x1400. When using the proprietary drivers (installed through Hardware Drivers in Gnome), I am unable to hibernate or suspend.

When I try to hibernate I get an error saying something along the lines of "Pat 2 entry is already configured" and something about swsusp not having enough memory.

A look through the forums revealed others with similar problems that were able to be resolved by disabling Compiz, however, I have the problem even when I have no desktop effects. I have to turn off the proprietary drivers to get suspend/hibernate to work -- at the cost of no video or anything working.

Help!

Also-- is it true that there's currently no way to get video/3D to work while Compiz/Desktop Effects are on? I'd be thrilled just to be able to get my system to hibernate AND show video without having to switch drivers, but it would be nice if someone could steer me in a direction to get video/3d playing friendly with desktop effects (and yes I've tried changing the video output).

Thanks!


**EDIT**
I just re-enabled the ATI drivers and tried to hibernate so I could copy down exactly what the error says, and while it still gave the following error, it successfully hibernated this time.

[   85.974383](fglrx:KCL_enable_pat) *ERROR* Pat 2 entry is already configured

Apparently hibernating works some of time (rarely).

**EDIT PART TWO**
I installed the latest ati drivers according to the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
Now suspend seems to be working consistently (tried it a few times to make certain -- isn't always pretty, but it works). Hibernate still doesn't work, displaying an ugly pinstriped grey screen and then loading the unlock screen when None desktop effects is toggled. With Normal Desktop Effects toggled hibernate does much the same thing it was doing prior to the update, except it no longer displays the Pat 2 entry error and instead only displays a message about swsusp and memory.

---

### Post by anewguy on 2008-08-26
Did you enable a swap partition when you installed?  What is it's size versus your virtual memory size?

The way things normally work on a hibernate is that all of physical memory is copied to swap - if you have no swap or if it is too small you would get an error.

You may also want to search the forums for waking up from hibernate - there have been some posts on things like networking and other things not "waking up".  I have seen posts in other Linux forums that supposedly get around that.  After searching these forums, always do a google or yahoo search with linux hibernation problems - you'll find more info, a lot of which is generic to Linux so you don't have to worry about it being distribution-specific.  There may be differences in syntax and file names, but it can usually be worked out to apply to Ubuntu.

---

### Post by thumper13 on 2008-08-26
"Also-- is it true that there's currently no way to get video/3D to work while Compiz/Desktop Effects are on? I'd be thrilled just to be able to get my system to hibernate AND show video without having to switch drivers, but it would be nice if someone could steer me in a direction to get video/3d playing friendly with desktop effects (and yes I've tried changing the video output)."

Video may be different, but I can attest that 3d programs (e.g. Games) don't play well with the Desktop Effects. But, Alas, there is a way to make it so the effects get disabled when you enter the game and re-enabled when you exit. Unfortunately, I'm not 100% sure how, but a search of the forums will reveal the answer. (I got my wow doing that.)

"I installed ubuntu on a Dell E1505 with an ATI Mobility Radeon x1400"

My experience thus far with Ubuntu and ATI cards is that ATI cards cause Ubuntu to puke. Not because of Linux, Ubuntu or anything of the like, but because ATI doesn't release up to date video drivers. The issue you're having may be related to your video drivers, and if this is the case there may be no work around.

HOWEVER. As the other poster said, it does sound to me in my (limited) wisdom, that it is either a) a memory problem or b) a swap file problem. If you allowed Ubuntu to make it's own partitioning when you installed, your swap file SHOULD be fine, and there. if you manually edited the partitioning, you may have forgotten to add it.

Hope it helps you.

---

### Post by UanarchyK on 2008-08-26
> **thumper13 said:**
> HOWEVER. As the other poster said, it does sound to me in my (limited) wisdom, that it is either a) a memory problem or b) a swap file problem. If you allowed Ubuntu to make it's own partitioning when you installed, your swap file SHOULD be fine, and there. if you manually edited the partitioning, you may have forgotten to add it.

Hope it helps you.

I let it do its own partitioning and it's showing a 2.89GB linux-swap partition.

---

### Post by anewguy on 2008-08-26
> **UanarchyK said:**
> I let it do its own partitioning and it's showing a 2.89GB linux-swap partition.

How much main memory do you have?

---

### Post by UanarchyK on 2008-08-27
Do you mean HDD or RAM?

I have ~90GB in my main memory partition, 1GB RAM

---

### Post by anewguy on 2008-08-27
I did some more searching on the net, and it looks like this is a driver issue.  This post:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

states up front that you need the actual ATI drivers to hibernate.  Perhaps that is what you have already done.

I think what I would try is Envy - it seems to install the correct driver for most people (for me, I went 1 release back to get things to work on an ATI 9250).  It will have an option for uninstalling your current drivers - you want to do ALL of that first.  I believe that for 8.04 you actually use Envyng.

Envyng is in the repositories and I would start by installing that and going from there.

Please note that for other versions of Linux there are bug reports filed for problems with hibernate/resume with some of the kernels and the ATI drivers.


EDIT:  BTW - when you followed the how-to, did you do the first have (restricted modules) or did you do the catalyst section?  This could make a difference on what may be needed to be done.  Either way, you want the actual ATI drivers.

---

