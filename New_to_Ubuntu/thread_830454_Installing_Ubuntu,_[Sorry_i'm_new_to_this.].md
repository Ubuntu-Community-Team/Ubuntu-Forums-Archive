---
title: "Installing Ubuntu, [Sorry i'm new to this.]"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Nate1337 on 2008-06-15
Hey, I am installing ubuntu to dual boot with xp.
I am good so far, but now im stuck.
before I installed xp, I partitioned the 40gb hd with 10gb set aside for linux.
It says this:
 I need to specify a partition for the root file system (mount point "/") with a minimum of 2 GB, and a swap partition of at least 256MB. This isn't a problem... But I don't know what to put in the mount point box. When creating a partition, and I am assuming I format in the default ext3?

Please help...


Thanks in advance

---

### Post by powerpleb on 2008-06-15
The larger partition where Ubuntu is uses the '/' mount point. Swap partitions don't have a mount point.
Put '/' in the mount point box and format it to ext3 and you should be good to go.:smile:

---

### Post by JoshuaRL on 2008-06-15
On the partition you want Ubuntu installed on, put the /.  It's called root, and it has all the filesystem for the OS.  The swap partition is like the page file in Windows, but doesn't fragment the drive because it's its own partition.  And yes, format in ext3.  It's the filesystem for Linux and it works great.

And welcome to Ubuntu!

---

### Post by Nate1337 on 2008-06-15
Nice it worked!
Thanks,
Also it seems really slow when starting up...
Is there any script to speed up startup?
My friend told me there was a script or something you put in to speed up startup.

---

### Post by kool_kat_os on 2008-06-15
how long does it take?

---

### Post by Nate1337 on 2008-06-15
Like 2-3 Minutes =/
I am running Ubuntu 7.1 if that means anything to anyone...

---

### Post by powerpleb on 2008-06-15
How old is your system? What are the specs?

---

### Post by kool_kat_os on 2008-06-15
When your computer boots up does it show the ubuntu logo with the loading bar?

---

### Post by Nate1337 on 2008-06-15
Its a nice computer, Intel AMD athlon xp 1600+
482mb ram
Radeon 320m video card.

It starts xp in a matter of seconds.

And The ubuntu splash screen does not show up... Its just a black screen for a while :confused:

---

### Post by kool_kat_os on 2008-06-15
Try this...it worked for me...used to be 2 mins...now 35 seconds:

go to the terminal and type in ```
sudo gedit /boot/grub/menu.lst
```

then in the file look for this part:

here is something what it should look like:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70 [COLOR="Red"]ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]
```

now make it this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic
```

simply remove "ro quiet splash" and "quiet"


and save it and reboot...

---

### Post by Nate1337 on 2008-06-15
Yeah thats what it was, thanks Kat

---

### Post by JoshuaRL on 2008-06-15
You can also check your usplash settings, that may be the underlying issue.  Quieting splash just takes the problem out of necessity.  By fixing usplash you can get the Ubuntu loading splash page back.  It will boot a lot quicker too.

Check /etc/usplash.conf

xres=1024
yres=768

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it you need to update the theme with
```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by kool_kat_os on 2008-06-15
i havent tried that yet....

---

### Post by JoshuaRL on 2008-06-15
Yeah, that's the underlying issue.  For some reason with Gutsy usplash automagically gets the wrong settings during install sometimes.  It then takes a ton longer to boot up, and takes away the splash screen.  I had that problem on my Inspiron 5100, and that fixed it.

---

### Post by Nate1337 on 2008-06-15
Well 1 problem... Menu.1st just shows up as blank in gedit...
Its just a black screen... Help?

---

### Post by stalkier on 2008-06-15
> **kool_kat_os said:**
> Try this...it worked for me...used to be 2 mins...now 35 seconds:

go to the terminal and type in ```
sudo gedit /boot/grub/menu.lst
```

then in the file look for this part:

here is something what it should look like:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70 [COLOR="Red"]ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]
```

now make it this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70
initrd		/boot/initrd.img-2.6.22-14-generic
```

simply remove "ro quiet splash" and "quiet"


and save it and reboot...

Nice. Thanks a lot. Boots in about 45 secs. (guessing)

---

### Post by JoshuaRL on 2008-06-15
> **Nate1337 said:**
> Well 1 problem... Menu.1st just shows up as blank in gedit...
Its just a black screen... Help?

That's actually:
```

menu.lst

```
It's a lower-case "L", not a 1 (one).  If you open a config file in Linux and it's empty, usually that means you typed the path wrong.  Go ahead and close without saving.

Another thing, make sure you use "gksu" or "gksudo" instead of "sudo" when altering config files in gedit.  Use gksu for graphical apps and commands, sudo for CLI.

---

### Post by Nate1337 on 2008-06-15
10x speed up thank you very much!

---

### Post by JoshuaRL on 2008-06-15
No problem.  Welcome to Ubuntu!

---

