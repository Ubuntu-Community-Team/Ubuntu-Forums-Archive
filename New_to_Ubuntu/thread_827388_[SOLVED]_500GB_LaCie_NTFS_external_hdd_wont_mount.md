---
title: "[SOLVED] 500GB LaCie NTFS external hdd wont mount"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Azeem1991 on 2008-06-12
it shows up, but it then says:
'Cannot Mount Volume
Unable to mount the volume 'LaCie'

[IMG]http://img.photobucket.com/albums/v210/Aztherock/Screenshot.png[/IMG]

look at that

thats the message i get, i have no bloody idea what to do

im using ubuntu 8.04 and really need to be able to use the 500gb drive!

i must not format it, its got backups on it :(

thanks

---

### Post by Azeem1991 on 2008-06-12
anyone..?

:(

---

### Post by moore.bryan on 2008-06-12
patience, grasshopper, patience. the error-log tells you it was not unmounted properly. it also assumes the cause of that problem is an inappropriate unmounting in windows. if you do in-fact dual-boot, then just boot into windows and unmount/eject the drive in there and then come-back to ubuntu. if you don't dual-boot, then you can use the -f option to try and force ubuntu to boot it.

---

### Post by mde123 on 2008-06-12
The thing abut NTFS (new tecnology file system) file systems is that, (created by Micrsoft) when they are shutdown unclean, (like pulling out power plug) the hard drive locks up all of its data, because it is a secureity feature that is supposed to prevent virus, and other Windows crap from installing onto it, or from an  non wanted OS modifying it. The only thing that you can do is acces it from an windows computer and then shut it down propprely.
But in the future, DO NOT format as NTFS. Try FAT32
Thre is nothing wrong in ubuntu. It is just your HDD


[the error says there was an unclean shutdown]

---

### Post by Azeem1991 on 2008-06-12
yeah i was thinking that might be the case, now to find that laptop!

i didnt do it as a dual boot because THE HARD DRIVE DIDNT HAVE an image of windows XP which i DIDNT burn to cd and lose.

thanks guys, ill get back to you in about 10 minutes

---

### Post by Azeem1991 on 2008-06-12
wow. i should really trust my intuition a bit more!

thanks you guys it worked!

much love, thanks


Azeem

[www.azeembeatbox.com](www.azeembeatbox.com)

PS. the ubuntu community really is helpful :) ill try and be here a bit more from now

---

### Post by moore.bryan on 2008-06-12
glad to hear of success... my external hd just died and the lacie 500gb is exactly what i'm looking at getting. overall, have you had good luck with it?

---

### Post by Azeem1991 on 2008-06-12
yeah ive had it for a fair few months and its been good so far, the only problem i have with the unit is that the usb connecting cable is bloody short, apart from that, its all good

also, make sure you unplug it when your not using it overnight or whatever, i just do it because it wastes power if left on, and could possibly wear the disk..

---

### Post by mde123 on 2008-06-12
please click the gold ribbon to thank

---

### Post by Azeem1991 on 2008-06-12
got it

---

### Post by moore.bryan on 2008-06-12
> **Azeem1991 said:**
> the usb connecting cable is bloody short
that's okay, for me; i'm only putting it on-top of my clunky desktop.
> also, make sure you unplug it when your not using it overnight or whatever, i just do it because it wastes power if left on, and could possibly wear the disk..
i've gotten into the habit of doing this with almost all my appliances... thank god for surge protector off/on switches.

---

### Post by Azeem1991 on 2008-06-12
> **moore.bryan said:**
> that's okay, for me; i'm only putting it on-top of my clunky desktop.

i've gotten into the habit of doing this with almost all my appliances... **thank god for surge protector off/on switches.**

my god, thanks again! you just reminded me that i need to get my bloody surge protector out and use it haha

its been in its box for like 4 months under my desk o.o

---

### Post by moore.bryan on 2008-06-12
no worries... the surge protector does indeed work better when used.
;-)

are there any major drawbacks you've found to the lacie?

---

### Post by Azeem1991 on 2008-06-12
it needs an on/off switch...

nah not really, nope :p

---

### Post by moore.bryan on 2008-06-12
it doesn't have an on/off switch? yeah, come to think of it, i didn't see one... didn't realize that.

---

### Post by Azeem1991 on 2008-06-12
ah dammit, another problem..

virtualbox this time:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by moore.bryan on 2008-06-12
sorry, i don't use virtualbox...

---

### Post by Azeem1991 on 2008-06-12
[https://edge.launchpad.net/ubuntu/hardy/+source/virtualbox-ose-modules]](https://edge.launchpad.net/ubuntu/hardy/+source/virtualbox-ose-modules])

i downloaded the latest one 'virtualbox-ose-modules_24.0.4.tar.gz  (5.1 KiB) '

where do i install it?

---

### Post by moore.bryan on 2008-06-12
after you untar it--i.e. ```
tar xvzf virtualbox-ose-modules_24.0.4.tar.gz
```--you want to cd into the directory it makes, followed by--usually--a simple 
```
./configure --prefix=/usr
make
sudo make install
```

---

### Post by wootah on 2008-06-12
> **Azeem1991 said:**
> ah dammit, another problem..

virtualbox this time:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Ahh congrats on getting things working :)

I would recommend marking this thread as solved (at the top theres thread tools -> mark as solved) and then creating a new thread to address this exact issue :popcorn:

---

### Post by Azeem1991 on 2008-06-12
O.o what do you mean by cd into the directory it makes..?

---

### Post by Azeem1991 on 2008-06-13
all solved! thanks

---

### Post by moore.bryan on 2008-06-13
glad to hear all is well...

---

