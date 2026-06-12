---
title: "[SOLVED] How do I configure Grub to boot a certain dist. first?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by ranch hand on 2008-10-27
I have dual booted Hardy/Hardy so that I have one I can screw up.  Seeing how the play one was last installed, I guess, it is the default start.

I want to change that.

How on earth do I do it?
Thanks.

---

### Post by ranch hand on 2008-10-27
It appears that my new install works.  Am sending this through it.

---

### Post by phidia on 2008-10-27
Edit /boot/grub/menu.lst and make sure the 1st entry (after all the default bits)
is the one you want to boot by default.

---

### Post by scorchgeek on 2008-10-27
Just to clarify, you would probably need to switch the order of the two Hardy installations.

---

### Post by fooman on 2008-10-27
easiest way would probably be to install startupmanager.  it is in synaptic (system > administration > synaptic package manager), or in a terminal:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

under the boot options tab, click the down arrow in the "default operating system" box and choose which install to boot.  you can also change the timeout for the menu or whether or not to show the menu.

---

### Post by ranch hand on 2008-10-28
Wow.  You guys are good.  And fast.

I had to come into town after posting last evening.  I am at the dreaded mother in laws on her lovely Vista machine downloading Ubuntustudio on her dsl line.  25X our dialup speed.

I need to get home and separate 2 bulls at the home place and seven cow/calf pairs at the other and then I will look into these suggestions further.

To clarify, yes I want to move my origanal install to the top of the list so that it will boot with no action on the part of the user.

I need to to do this for convenience sake for me and, more importantly, my wife who is not as enthusiastic about the change.  She is enthusiastic about leaving Vista Home Premium behind.

Also, as I do have a 329gig HDD, I think I will load Ubuntustudio too, and will still want the origanal Hardy install to be primary.

The Studio distro could also go on the unplugged Vista HDD but I don't really want to use it at all.  Bad vibes, negative thoughts and Vista all on one HDD, I like it unplugged as and emergency back up.
Thanks

---

### Post by ranch hand on 2008-10-28
> **phidia said:**
> Edit /boot/grub/menu.lst and make sure the 1st entry (after all the default bits)
is the one you want to boot by default.

There is something I am not getting here and I can't even figure out what that is.  Frustrating.

I ran    sudo gedit /boot/grub/menu.lst  

Got the page up and could make no sense of the uncommented list at the bottom of the page.  It would probably be easier if I had different versions or distributions or, gods help me, winsomething.

But at the top of the page there was something that looked promising;

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		1

The default number was 0 I changed this to 1.

Below this was the time out setting which I changed from 3 to 10 seconds so that I have time to read it all.

This seems to have accompished unexpected things in that it never did boot until I indicated the install I wanted and hit enter.

Now, I see that fooman is recommending a gui solution.  I have nothing at all against this but it has been since dos that I did any command line stuff and I would really like to learn this.  This by the way is how I have, in one week recently, been able to break my installation 4 times.  This is why I need the second one to play with.

I may install startupmanager to deal with the next install which will probably end up booting me into Ubuntu Studion on the third partition.  I thought maybe I should learn to deal with this problem before installing that one.

---

### Post by ranch hand on 2008-10-29
I have rebooted into my playtime installation and find that perhaps I am booting from there.  I think I see my confusion over the entries at the bottom of the page.  Thsy were refering to the origanal install (hogwash).  The same page here in playtime has the same files and then an added feature as follows;

# This is a divider, added to separate the menu items below from the Debian

Below is the listing for hogwash and hogwash recovery mode;

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

I still don't know how to get it to boot how I want but now I am much more aware of my ignorance.  This is always good.

---

### Post by Xiong Chiamiov on 2008-10-29
You have savedefault specified for each option, which might be confusing grub.  As you saw in the comments at the top of the file, you can either choose a number or specify savedefault on an option.

---

### Post by macogw on 2008-10-29
In the top commented part, put the number of the one you want to have boot, then mark savedefault as true so when you get kernel updates, it knows to increase the number.

---

### Post by ranch hand on 2008-10-29
Thanks all.  Works like a charm.

---

