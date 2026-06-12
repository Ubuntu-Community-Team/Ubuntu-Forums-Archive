---
title: "Oneiric on Poulsbo Netbook"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fjgaude on 2011-07-15
Okay folks, especially Luca, how do you install OO into subject kind of box?

I've got a working iso, 32-bit thumb drive, that installs on my main box, an Intel i5 with GMA HD, which works just fine, Unity 3D and all. But the GMA 500 is so off the wall, the install gets so far and then drops into command line. Lightdm loads but with no GUI.

Any ideas?

---

### Post by lucazade on 2011-07-15
Hi!

Have you tried to follow the steps of this post?
[http://ubuntuforums.org/showpost.php?p=10991520&postcount=1](http://ubuntuforums.org/showpost.php?p=10991520&postcount=1)

Are all the necessary steps to start livecd, install on hd and install psb_gfx drivers.
If is there anything you don't understand ask me, I'll try to explain in a better way.

You could also use alternate iso image instead of livecd, this way you can avoid to unload modules "poulsbo" and "psb_gfx" and follow only the following steps. (I suppose, haven't tried here)

from what you write you haven't blacklisted modules at startup so gui cannot be loaded...
when you start livecd, at the first purple screen (where you can select language for installation) if you hit F6 you can add additional params to kernel.
in this case append to default kernel params:

```
poulsbo.dummy=1 psb_gfx.dummy=1

```

then press enter to startup livecd in vesa compatibility mode to install ubuntu.
try to follow the other steps and let me know if ok.

:)

---

### Post by fjgaude on 2011-07-15
Okay, thanks for the quick reply... I haven't done what you suggested at all... thinking I would get the OO loaded then take care of what needs help.

I can install NN with gnome-shell and that seems okay... but I don't think that is the way to go... I'll get some time later today to go your route... will ask if anything needs explaining.

Thanks again!

---

### Post by fjgaude on 2011-07-16
Hello Luca, and all else... installed your suggestions and everything is working as expected: good 2D speed,sound,1366x768 resolution, mouse quickness, all nice! OO rocks on this Dell 10" netbook! Will start updating daily, or more often. Hope no crashes. <smile>

Brightness keys not working but is no issue with me.

We await your and Tista's next advance.

Once again, thank you for your continued effort to keep Poulsbo alive.

---

### Post by lucazade on 2011-07-16
> **fjgaude said:**
> Hello Luca, and all else... installed your suggestions and everything is working as expected: good 2D speed,sound,1366x768 resolution, mouse quickness, all nice! OO rocks on this Dell 10" netbook! Will start updating daily, or more often. Hope no crashes. <smile>

Brightness keys not working but is no issue with me.

We await you and Tista's next advance.

Once again, thank you for your continued effort to keep Poulsbo alive.

Ahhh! Great!
Glad to know it worked for you.. unfortuantely at the moment is a bit tricky to install but when kernel 3.0 will be released and adopted by oneiric there will be probably no need to install drivers because already inside kernel.
Of course our ppa will provide update drivers for all the brave.

---

### Post by fjgaude on 2011-07-16
Well, after updating OO with over 300 packages and kernel 3.0.0.-5, or whatever the latest is, I've had troubles getting back to where the install was when it worked correctly.

Anyway... keep on truckin' and I'll update as the new stuff comes out.
###

I removed psb-dkms and then re-installed; still not working. I get the VBE driver. Any suggestions.

---

### Post by fjgaude on 2011-07-17
I've tried everything at hand but nothing gets the box back to where it was before updating/upgrading Alpha 2 to current.

I re-installed psb-dkms and have checked all the files that should be modified. They all are. Except I can't see that the command to sed the /etc/grub.d/10_linux is changed.

I've tried using the old kernel 3.0.-3 and it acts the same as the new 3.0.0-5. No joy! psb-dkms built for both the kernels.

Any suggestions.

---

### Post by lucazade on 2011-07-17
> **fjgaude said:**
> I've tried everything at hand but nothing gets the box back to where it was before updating/upgrading Alpha 2 to current.

I re-installed psb-dkms and have checked all the files that should be modified. They all are. Except I can't see that the command to sed the /etc/grub.d/10_linux is changed.

I've tried using the old kernel 3.0.-3 and it acts the same as the new 3.0.0-5. No joy! psb-dkms built for both the kernels.

Any suggestions.

hmmm... hard to say
here it continues to work also with latest kernel -5

have you tried to change virtual terminal when you get the black screen on boot?
you can do it with Ctrl-Alt-F1 
this way you can fix stuff from terminal, login and paste

sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disable
sudo sed -i 's/vt.handoff=7//g' /etc/grub.d/10_linux
lsmod | grep psb_gfx

paste here the result.

---

### Post by fjgaude on 2011-07-17
Oh wow! It's working as it should... Each time I booted continuing to put the dummy=1 items in the kernel line. Should not have had to do that. <smile>

That's it for now, waiting for the super new stuff after you and Tista fix it all... all working with psb-gfx! Thanks again!

---

### Post by lucazade on 2011-07-17
> **fjgaude said:**
> Oh wow! It's working as it should... Each time I booted continuing to put the dummy=1 items in the kernel line. Should not have had to do that. <smile>

That's it for now, waiting for the super new stuff after you and Tista fix it all... all working with psb-gfx! Thanks again!

You're welcome...
hope this info could help also the other poulsbo owners.

see you

---

### Post by fjgaude on 2011-07-17
Okay, Oneiric's grub 2.0 can't handle the GRUB_GFX=1366X768X32, etc, needed for my 10.04 boot with fbdev driver. Any suggestions?

---

### Post by lucazade on 2011-07-17
> **fjgaude said:**
> Okay, Oneiric's grub 2.0 can't handle the GRUB_GFX=1366X768X32, etc, needed for my 10.04 boot with fbdev driver. Any suggestions?

[https://wiki.edubuntu.org/HardwareSupportComponentsVideoCardsPoulsboAlternatives](https://wiki.edubuntu.org/HardwareSupportComponentsVideoCardsPoulsboAlternatives)

take a look at first part

---

### Post by fjgaude on 2011-07-17
Like I pointed to: grub 2.o or maybe it is 1.99 doesn't do GRUB_GFX=1366X768X32 and the like, as indicated needed in your link, which I've been using since using the fbdev X driver.

I don't think this resolution technique was ever used in 10.10 wherein, if memory serves, is the first time the new grub was used. !0.04 used the old grub. With my dual boot, with 11.04, which uses the new grub I'm in trouble with the hi-res.

Something to think about, eh?

---

### Post by lucazade on 2011-07-18
> **fjgaude said:**
> Like I pointed to: grub 2.o or maybe it is 1.99 doesn't do GRUB_GFX=1366X768X32 and the like, as indicated needed in your link, which I've been using since using the fbdev X driver.

I don't think this resolution technique was ever used in 10.10 wherein, if memory serves, is the first time the new grub was used. !0.04 used the old grub. With my dual boot, with 11.04, which uses the new grub I'm in trouble with the hi-res.

Something to think about, eh?

that guide is for grub2 and ubuntu 10.10 already uses grub2.
there are no major changes in grub also in recent ubuntu releases.

You should follow all the steps of the wiki because GRUB_GFX=1366X768X32 is not enough to get the correct resolution with fbdev.
You need also the 01_915resolution file and update-grub.

---

### Post by fjgaude on 2011-07-18
> **lucazade said:**
> that guide is for grub2 and ubuntu 10.10 already uses grub2.
there are no major changes in grub also in recent ubuntu releases.

You should follow all the steps of the wiki because GRUB_GFX=1366X768X32 is not enough to get the correct resolution with fbdev.
You need also the 01_915resolution file and update-grub.

Okay, Luca... remember I had 10.04 fully working with all the steps of the wiki, even that of suspend and resume, working for over a year. I made room on the drive to dual-boot with 11.10, and finally got psb-gfx driver working with your help.

Now, I reboot using the 10.04 install. An error msg shows that says to the effect "Can not store monitor configuration. X doesn't support size requested."

I've double checked and all the files are as they should be. That error msg indicates to me that grub has not handled: 

```
GRUB_GFXMODE=1366x768x32
GRUB_GFXPAYLOAD_LINUX=1366x768x32
```

that's in /etc/default/grub file in the 10.04 partition correctly. Should these items be placed somewhere else? in the grub.conf in the 11.10 partition?

All items from the Wiki are in place correctly. It used to work but stopped when I went dual boot.

---

### Post by lucazade on 2011-07-18
> **fjgaude said:**
> Okay, Luca... remember I had 10.04 fully working with all the steps of the wiki, even that of suspend and resume, working for over a year. I made room on the drive to dual-boot with 11.10, and finally got psb-gfx driver working with your help.

Now, I reboot using the 10.04 install. An error msg shows that says to the effect "Can not store monitor configuration. X doesn't support size requested."

I've double checked and all the files are as they should be. That error msg indicates to me that grub has not handled: 

```
GRUB_GFXMODE=1366x768x32
GRUB_GFXPAYLOAD_LINUX=1366x768x32
```

that's in /etc/default/grub file in the 10.04 partition correctly. Should these items be placed somewhere else? in the grub.conf in the 11.10 partition?

All items from the Wiki are in place correctly. It used to work but stopped when I went dual boot.

ok, i think i get your problem...
to use the i915 resolution hack grub must be installed in the 10.04 partition and
not in oneiric partition.

otherwise at boot grub takes config from oneiric and not from 10.04.
so boot in 10.04  and install grub:
sudo grub-install /dev/sda           (where sda is your hd)
sudo update-grub

reboot and you should see grub from 10.04 and tweaks now should work properly

---

### Post by fjgaude on 2011-07-18
Okay, Luca, you are the man!

All works in both boots as it should... so onward and upward with the 11.10 situation, and hopefully all will be well at release time in October. <smile>

Thanks again for being so helpful!

---

### Post by leorosa on 2011-09-11
Hi Luca,

How about upgrading from NN to OO? It's safe for moving from emgd driver to psb_gfx? Please light my way =]

---

### Post by lucazade on 2011-09-11
> **leorosa said:**
> ..
abour psbgfx it seems there are some issue with latest kernel.. it needs some investigation because the kernel module is no more employed at boot time. 
..


figured out what's wrong.. grub must be installed on oneiric active partition (i.e. with natty grub don't work) ^^
in the meanwhile a couple of weird bugs are fixed and some workarounds are no more required (vt.handoff=7 and plymouth)

this is the updated install script, now even shorter.. hoping to drop it when kernel 3.1 will be out and shipped by default in oneiric+1
```
#!/bin/bash
# psb_gfx installation script for oneiric


# add repository, install drivers
add-apt-repository ppa:gma500/psb-gfx-testing
apt-get update
apt-get install psb-dkms 


# blacklist other drivers
echo 'blacklist poulsbo
blacklist acer-wmi' | tee -a /etc/modprobe.d/blacklist.conf


# fix for backlight 
sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="acpi_backlight=vendor"/g' /etc/default/grub


# finalize installation 
update-grub
update-initramfs -u -k all
```

---

