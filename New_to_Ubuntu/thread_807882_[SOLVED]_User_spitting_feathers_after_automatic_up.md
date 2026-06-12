---
title: "[SOLVED] User spitting feathers after automatic updates..."
date: 2008-05-26
forum: New to Ubuntu
---

### Post by usernamed on 2008-05-26
Firstly, this is all my own fault.  I skimmed the list of updates prior to hitting install, but didn't stop to think of the consequences.

My problem is (as ever) with wireless.  Having gone through days of pain trying to get my original USB dongle to work, I gave up and bought one that I knew had a ralink chipset, I had continued problems with that until I was pointed in the right direction by a friendly forum user, and for a whole week I had wireless.  Yay!

Today I downloaded these *blessed* updates and of course it's gone and built a new kernel and lost the rt73 module that I'd built and installed.  I have no wireless again.

Worst of all, my attempts to build a new module are failing because although the module builds fine, any attempt to load it gives me the following error:

```
mw@dt1:/usr/src/rt73-cvs-2008050213/Module$ sudo modprobe -i rt73
FATAL: Error inserting rt73 (/lib/modules/2.6.24-17-generic/extra/rt73.ko): Invalid module format
mw@dt1:/usr/src/rt73-cvs-2008050213/Module$ 

```

I'm running in Hardy 64-bit and would dearly love to get wireless working again as each time it fails I have to go getting the wireless router down, draping cables across the middle of the living room floor and basically make the room uninhabitable for everybody else.

I'd also like to have a brief moan (just to let off steam) about putting kernel updates in with general application updates.  If Microsoft placed an automatic update into Windows Update that broke wireless for users they'd be fighting loss of earnings lawsuits for the next 10 years.  I'd beg those in charge of releases to reconsider how kernel updates are deployed.  At the very least have a big "INSTALLING THIS UPDATE WILL CAUSE ALL THIRD-PARTY MODULES TO BE REMOVED - PLEASE ENSURE YOU HAVE THE CODE AND TOOLS NECESSARY TO REBUILD AND REINSTALL THESE MODULES BEFORE PROCEEDING" message.

To let sleepyheaded users like myself walk into it without so much as a warning dialog seems a little unfair...

Yours (tripping over network cables) 

Mark

---

### Post by shifty_powers on 2008-05-26
so you had a kernel update, yes?

if so, just enable to timeout for your grub menu, press esc when you boot up and then choose the lst kernel.

btw, you'll find startup-manager very useful for this.

```
sudo apt-get install startup-manager
```

and then look in system>admin

also you can edit your /etc/grub/menu.list so that ti only inculdes the previous kernel and not the one juts updated. there is nothing keeping you to the new kernel. I've had to do this myself with kernel updates and wireless before ;)

---

### Post by usernamed on 2008-05-26
Thanks Shifty,

I'll do this, but just for my own education, do you know why 'make clean' then rebuilding (and re-installing) the kernel module doesn't work?

---

### Post by shifty_powers on 2008-05-26
heh not as simple as that.

did you do make menuconfig and make sure you are using your prexisting kernel config?

also, most drivers, including the wireless drivers are part of the actual kernel, which is different from windows. so if you rebuild the kernel, you need to ensure that your wirelss drivers are included and enabled ;)

tbh, kernel compilation is something i've steered well away from, as it is more hassle than it is worth ;)

stick with old kernel for now, i tend to find that this is fine until the next version of ubuntu comes out, by which point they usually upagrade the kernel again and the problem has been solved ;)

---

### Post by usernamed on 2008-05-26
This is done and working, thanks again.

I didn't look at menuconfig, I had no intention of doing a manual kernel build (I didn't even want to do an automatic one)

I just clicked on install updates because Ubuntu seemed to be recommending these updates were downloaded and applied.  I wanted the finished LTS build precisely because I didn't want to have things breaking on me or mysteriously changing.  (But nor do I want my machine to have security issues through being out of date)

So you're saying that I'd need to do a manual config/build of the kernel before I'd be able to load modules into the updated kernel?

That does not seem in keeping with the Ubuntu philosophy somehow!

No matter, this kernel is working just fine and I'll happily let it see me through the next 3 years.  Thanks for all your help.

Mark

---

### Post by andrew.46 on 2008-05-27
Hi,

I usually change a few small options in /boot/grub/menu.lst to make selection of kernels a little easier. Press Alt-F2 and type:

```
gksudo gedit /boot/grub/menu.lst
```

and perhaps uncomment / comment these options as I have done routinely:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
color cyan/blue white/blue
```

The option that I have commented out is the "hiddenmenu" one, this allows the menu to be seen for the 10 seconds that "timeout" allows, in glorious blue and white :-). Plenty of other options to play with in this well-commented file. Just be a little cautious here or your machine will not boot.

     Andrew

---

### Post by dwp0980 on 2008-05-27
Hi,

I'm glad I'm not the only one who did this!

However, after calming back down again, and trying to remember how I did it the first time, I think I've got it working in the most recent kernel.  I don't know if it will help, but I used the RT73 tutorial from [_here_]("http://ubuntuforums.org/showthread.php?t=400236").

I didn't do the make clean, but followed all the steps through to 14.  You obviously don't need to blacklist etc again, but it worked after a reboot.

Hope this helps

---

