---
title: "Changed swap partition size"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by timace on 2008-05-14
Hey,

I have discovered I've made a bad move, as mentioned in the title, I increased the swap partition size (because it was ridiculously low), now Ubuntu 8.04 doesn't recognise it when I go to hibernate, etc

Is there a way I can assign the swap partition to ubuntu again, without reinstalling?

Thanks in advance :)

---

### Post by overdrank on 2008-05-14
> **timace said:**
> Hey,

I have discovered I've made a bad move, as mentioned in the title, I increased the swap partition size (because it was ridiculously low), now Ubuntu 8.04 doesn't recognise it when I go to hibernate, etc

Is there a way I can assign the swap partition to ubuntu again, without reinstalling?

Thanks in advance :)

HI and this link can help to activate your swap
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Oldsoldier2003 on 2008-05-14
> **timace said:**
> Hey,

I have discovered I've made a bad move, as mentioned in the title, I increased the swap partition size (because it was ridiculously low), now Ubuntu 8.04 doesn't recognise it when I go to hibernate, etc

Is there a way I can assign the swap partition to ubuntu again, without reinstalling?

Thanks in advance :)

change your fstab to match the current partition information. you can do this by changing the UUID to match the new uuid of the swap partition (the UUID changed when you resized it) or simply change the /etc/fstab to load the swap partition via /dev or label. (you need superuser priveledges to save the changes)

```
sudo nano /etc/fstab
```

for example example if your swap resided on sdb2 the line should look like this:
```
/dev/sdb2	 none            swap    sw              0       0
```

If you want to go the UUID route:

```
ls -alh /dev/disk/by-uuid
```
then modify the UUID for your swap partition in /etc/fstab


edit: additional information as prompted by overdrank's response above:

after doing the above:
```
sudo mount -a
swapon -a
```

to verify your swap file is mounted and working:
```
free -m
```
if you see any value for swap other than:
```
Swap:            0          0          0
```
you are good to go

---

### Post by louieb on 2008-05-14
Been there, done that. To fix hibernation the UUID for swap needs to be checked  in 2 places. 
/etc/fstab and **/etc/initramfs-tools/conf.d/resume**

If the UUID changed  then you need to run
```
sudo dpkg-reconfigure  initramfs-tools
```

[http://louboldt.com/ilinuxmisc.htm#uuidswap](http://louboldt.com/ilinuxmisc.htm#uuidswap)

---

### Post by timace on 2008-05-15
> **Oldsoldier2003 said:**
> change your fstab to match the current partition information. you can do this by changing the UUID to match the new uuid of the swap partition (the UUID changed when you resized it) or simply change the /etc/fstab to load the swap partition via /dev or label. (you need superuser priveledges to save the changes)...

This worked! I just had to run swapon -a as root

Thanks so much for all your help guys. :)

---

