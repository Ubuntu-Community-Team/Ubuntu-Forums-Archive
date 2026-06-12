---
title: "[SOLVED] Advice Requested on Battery Care for Laptop"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Andavane on 2008-11-17
Dear Members

I'm in the process of ordering a battery for my Sony Vaio laptop.

The vendor recommends:

> 
Caring for your Sony Vaio VGN-S3HP Hi-Capacity Battery
You can improve the life of your Sony Vaio VGN-S3HP Hi-Capacity Battery by doing the following:
When you first receive your laptop battery charge it fully for at least 6-8 hours and then discharge the battery fully by using your laptop unplugged from the mains until it runs down completely.

Repeat this 3 times to ensure your Sony Vaio VGN-S3HP Hi-Capacity Battery will give you the maximum performance.

If you regularly use your Sony Vaio VGN-S3HP Laptop on mains power for extended periods, removing the battery from your Laptop during these periods will extend the usable life of your laptop battery.


If I follow the advice of "letting my laptop battery run down completely"
3 times, what efect would this have on my Ubuntu installation?

I have recently installed Hardy, and it's working well.

PS: In the past I have run the battery down until I receive the low battery warning sign, and then I have switched on the mains.

Regards

John

---

### Post by ciscosurfer on 2008-11-17
Breaking in a laptop battery is a good idea.  It "primes the pump", as it were.  It allow the cells inside the battery to "flex their muscles".  It is not necessary to allow the battery to fully discharge before plugging back into the mains.  You *could* do this, and with a journaled file system you should be fine from data corruption if you were to allow the battery to fully discharge, i.e., to the point where your laptop turns itself off due to lack of power.  If you're going to go that route, I suggest not doing anything important during those times, but if you do, be sure to constantly save your work before and during the "low battery" warning.  To sum up: it's a good idea, and you will have successfully broken in your battery if you follow the same procedure that you outlined in your post script. :-)

---

### Post by bumanie on 2008-11-17
I guess you don't want to run the battery out when the OS is actively running - so run it down to 1-2% power left. But the idea sony is getting across is that if battery cells are repeatedly only discharged to say 75% of their charge, rather than near 100%, the batteries have a 'memory' and will only recharge to 75% of their potential. To reverse this or stop it from occurring, one should run any rechargeable battery down to zero (or nearly zero if it's a computer) before recharging, thus not creating a 'false memory'. To charge and discharge rapidly 3-4 times is known as deep cycling and can sometimes 'rejuvenate a battery's memory'. I guess they say to do this deep cycling to a new battery to ensure it operates at its full potential from the start.

---

### Post by Tony Flury on 2008-11-17
running the battery down to zero did nothing wrong to my linux installation.

Just turned off the power management, unplugged from the mains and then walked away.

If you are really nervous - take a back up - but I think you wil find that the file system is more than resilient enough to cope with a power failure.

---

### Post by beercz on 2008-11-17
> **Tony Flury said:**
> Just turned off the power management, unplugged from the mains and then walked away.

If you are really nervous - take a back up - but I think you wil find that the file system is more than resilient enough to cope with a power failure.
I periodically go into my laptop's BIOS, shut the laptop lid and leave it running on battery overnight.  When the battery runs down the laptop merely switches off.

My file system remains intact, although I do have a good backup of my data.  I am paranoid about backups.

---

### Post by lakersforce on 2008-11-17
Nothing - Ubuntu shuts itself down when critically low on battery

---

### Post by The Cog on 2008-11-17
If you hit Escape at the GRUB prompt and then leave it, then there will be no disk activity at all as it shuts down, so no risk to the filesystem.

---

### Post by Daveski on 2008-11-17
> **Andavane said:**
> 
If you regularly use your Sony Vaio VGN-S3HP Laptop on mains power for extended periods, removing the battery from your Laptop during these periods will extend the usable life of your laptop battery.

This advise is important also. Modern Lithium based batteries are pretty resistant to the old 'memory' problems. The life and capacity is shortened by temperature more than anything else, and considering how hot x86 laptops run these days, the battery is always at a fairly high temperature.

Remove your battery at about 40% charge and keep it at 20 degrees C or lower if you can when you aren't using it.

---

### Post by Andavane on 2008-11-18
Thanks for all the very useful replies.
I asked as I have ordered a new battery for the laptop;
the one that came with the machine is now over three years old and still able
to run the unit for 2 -- 3 hours. But I think it is on the way out.

I was interested in the idea of hitting escape at the GRUB prompt: something that doesn't use the OS seems a great idea. 

Also I reckon that with the new battery I could continue to swap between the two, and keep the spare in a cool place near the window.

Kind regards

John

---

