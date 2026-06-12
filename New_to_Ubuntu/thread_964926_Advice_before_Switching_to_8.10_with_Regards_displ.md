---
title: "Advice before Switching to 8.10 with Regards displayconfig-gtk &amp; Resolution Woes"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2008-10-31
Hello all,

I upgraded from Hardy to Ibex yesterday, and had the resolution problems I usually have. After installing the proprietary nVidia driver, my monitor for some reason doesn't auto-detect properly, and I only have a limited number of resolution options to choose from in "system/preferences>screen resolution" (800x600 being the largest).

The old fix was to invoke "displayconfig-gtk", choose your monitor type, and all was well. Unfortunately with Ibex, displayconfig-gtk isn't included, nor can it be downloaded. 

So if you're reading this, what I'd suggest you do to get round the problem is BEFORE upgrading to Ibex, make a backup of your /etc/X11/xorg.conf file (a backup of the xorg.conf file with the proprietary drivers installed in Hardy, and the monitor correctly chosen using displayconfig-gtk).

Then install Ibex, install your proprietary drivers, and then manually edit your new /etc/X11/xorg.cong file, replacing the "monitor" and "screen" parameters with the saved parameters from your saved xorg.conf from Hardy.

An easy fix if you haven't yet installed Ibex. For me however, after sussing out there was a problem, I had to reinstall Hardy again, lift a copy of my xorg.conf onto a memory stick and then re-install Ibex a second time, edit xorg.conf, and thankfully everything's now working fine.

I Googled this problem last night and a lot of people seemed to be getting cheesed off with the same problem. The solution is obviously easy. just edit xorg.conf. The harder question however is edit it to what? What values should I put in? 

If you don't know, then all I can suggest is either finding out from your old Hardy install before upgrading. Or worst case scenario, reinstalling Hardy, install your drivers and choose your monitor type, and then take those values from xorg.conf to transfer over to your Ibex installation.

I just posted this in the hope that it may help some of those frustrated by the omission of displayconfig-gtk.

Good luck.

---

### Post by philinux on 2008-10-31
Have you raised a bug at launchpad with your full specs. Then the autodetect can be fixed.

---

### Post by SpongeBob SquarePants on 2008-10-31
> **philinux said:**
> Have you raised a bug at launchpad with your full specs. Then the autodetect can be fixed.

Hi Phil,

Yes, I've done that. The above was just a solution for the meantime.

---

### Post by Abdullio on 2009-01-08
Thanks for the posting. As an Ubuntu newbie (I once installed 7.04 on to Virtual PC 2007, but that's as far as my experience goes until I downloaded 8.10 yesterday) I was trying to figure out how to restore display settings after an attempt to install the "recommended" nVidia v96 driver went all wobbly. I tried to follow the instructions to install and use displayconfig-gtk at the following link, but found that even though the site suggested this would be easier than breathing, I couldn't get it to work (was I really that dumb?).

[http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/)

Obviously your posting has shed some light in that the solution I thought I had found exists no longer, however, if a newbie (like myself) or anyone else is just wanting to restore settings so that they get to the original as-installed detected settings you can try:

sudo dpkg-reconfigure -phigh xserver-xorg

Yes, this instruction is right there in the xserver configuration file to be seen, but other postings I have read all suggested that the above line without the "-phigh" part was the solution, but that seemed to do not much useful for me. Not to mention as a newbie you need to know how to get in and edit that file to begin with. The above solution avoids even having to know that file exists. After you do this, reboot and you may have to re-select your desired display resolution again.

---

### Post by evilkastel on 2009-01-08
actually there are a few workarounds about that. I wrote here one myself on my upgrade.

---

