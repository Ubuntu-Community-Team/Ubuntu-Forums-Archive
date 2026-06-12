---
title: "Swap FIle (not swap partition) not being used"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by alpine_rover on 2008-11-28
Hey all,

I just dual booted ubuntu 8.1 on a macbook 4,1 today, and I'm a complete linux noob.  I've gotten most everything working, but I'm not sure if the swap file I created is working.  When I type the free command, it always shows that none of it is being used, even with gimp, openoffice, etc. all up at the same time.  I have 2gb of RAM on the machine.  Any tips?

Thanks

---

### Post by MrWES on 2008-11-28
> **alpine_rover said:**
> Hey all,

I just dual booted ubuntu 8.1 on a macbook 4,1 today, and I'm a complete linux noob.  I've gotten most everything working, but I'm not sure if the swap file I created is working.  When I type the free command, it always shows that none of it is being used, even with gimp, openoffice, etc. all up at the same time.  I have 2gb of RAM on the machine.  Any tips?

Thanks

yah...welcome to Linux! :)

Bill

---

### Post by louieb on 2008-11-28
What does the free command show?
to run open applications>accessories>terminal
```
free -m
``````

             total       used       free     shared    buffers     cached
Mem:          1010        726        284          0         37        397
-/+ buffers/cache:        291        719
[COLOR=Red]Swap:         1019          0       1019[/COLOR]


```

---

### Post by drs305 on 2008-11-28
You can run the following command just to make sure it is enabled:
```
sudo swapon -a
```
If you get an error, your fstab may not be correctly identifying your swap partition. If so, use the 'blkid' command below to compare the two and change the fstab entry to match the 'blkid' UUID or device identity.
```

cat /etc/fstab | grep "swap"
sudo blkid | grep "swap"

```


If there are errors, or for further checking, you can also make sure the UUID of the swap partition is correctly identified elsewhere by comparing these two entries:
```

sudo blkid | grep "swap"
cat /etc/initramfs-tools/conf.d/resume
*If different:*
gksu gedit /etc/initramfs-tools/conf.d/resume
*Then:*
sudo update-initramfs -u

```

---

### Post by Rolcol on 2008-11-28
Swap isn't used when there is no need.  2GB is enough on your machine for a lot of programs and it looks like there is no need for swap at that point.  Swap is an extension to RAM.  It's only used if you run out of space on RAM.  On my system, I don't usually use swap unless I begin running a Virtual Machine and I only have 1GB RAM.

---

### Post by a0u on 2008-11-28
> **alpine_rover said:**
> Hey all,

I just dual booted ubuntu 8.1 on a macbook 4,1 today, and I'm a complete linux noob.  I've gotten most everything working, but I'm not sure if the swap file I created is working.  When I type the free command, it always shows that none of it is being used, even with gimp, openoffice, etc. all up at the same time.  I have 2gb of RAM on the machine.  Any tips?

Thanks
Check the "swappiness" setting.
There's much detailed documentation to be found at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq).

---

### Post by alpine_rover on 2008-11-28
Hey Thanks for the quick responses... free -m gives me this:

total       used       free     shared    buffers     cached
Mem:          1974       1209        764          0         74        457
-/+ buffers/cache:        678       1296
Swap:         1023          0       1023

Using the swapon -a command comes up with nothing.

---

### Post by drs305 on 2008-11-28
> **alpine_rover said:**
> 
Using the swapon -a command comes up with nothing.

That is a good thing ... ;-)

---

### Post by alpine_rover on 2008-11-28
Swappiness is 60.  I guess I could set it at 100 and see what happens, but I think as long as ubuntu is running smoothly, I'll leave it how it is for the time being.

---

