---
title: "No disk space available"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by ishana.rl on 2013-10-25
I have a fresh installed ubuntu 13.04 (Right from the CD from about 1 week ago) and I have a 500GB HDD...
Now, I am getting an error saying that there is no disk space available and I think it is been messing up my boot (Failing to load Ubuntu at all or lagging A LOT).

I did some searches and I "think" it could be boot space, which I have no idea what that means... but how do I fix that anyways?

---

### Post by varunendra on 2013-10-26
Hi, Welcome to the forums ! :)

Space issue should not occur on a system so recent, unless you allocated too small space to root (/) or /boot. But let's check that anyway.

Assuming you are able to boot into it anyhow, please open a terminal (Ctrl-Alt-T), and post back the outputs of -
```
df -h
dpkg -l | grep linux-image
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by fantab on 2013-10-26
An aside suggestion: 13.04 will go out service in January as it is supported for only 9months. Since its a new install anyway, may I suggest that you install the latest Ubuntu 13.10?

But lets get that space issue resolved first. Post the information which varunendra has asked for.

---

### Post by ishana.rl on 2013-10-27
It fixed it self somehow... I am not sure but at that time I also got the "Fail safe graphics" and I searched until I got it fixed

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       451G  223G  205G  53% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           790M  948K  789M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  4.9M  3.9G   1% /run/shm
none            100M   20K  100M   1% /run/user

```

> **fantab said:**
> An aside suggestion: 13.04 will go out service in January as it is supported for only 9months. Since its a new install anyway, may I suggest that you install the latest Ubuntu 13.10?

But lets get that space issue resolved first. Post the information which varunendra has asked for.

How do I update to 13.10? and how big is the update?

---

### Post by varunendra on 2013-10-27
> **ishana.rl said:**
> It fixed it self somehow... I am not sure but at that time I also got the "Fail safe graphics" and I searched until I got it fixed

Whatever magic happened, congrats ! :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

> How do I update to 13.10? and how big is the update?
The size would be almost the same as the full installation ISO.

The best choice regarding this, in my opinion, is to -

download the ISO of 13.10 > burn a DVD or create a live USB with it > test it in Live mode first ("Test" option) > Do a fresh installation (overwriting the current one) if it plays nicely with the hardware and you are satisfied with its performance.

As fantab said, since it is a fresh install, you shouldn't have much to save from it anyway. Although since 13.10 has just come out, it may have some bugs that may cause issues with your hardware. So it is highly recommended to try it in live mode first before jumping the gun.

If you choose to download the ISO, it is also recommended to download it via torrent to ensure integrity of the download. Official torrents can be found here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)


**EDIT:**
Just noticed - you have given all of 451 GiB space to root (/), that is, the whole Ubuntu installation.

While there is nothing wrong with that, I personally recommend a separate "Data" partition for your user data.
Keep only 40-50 GiB for Ubuntu installation, and allocate the remaining space to the data partition (you can have more than one if you need). By doing this, you won't have to worry about saving or moving the data whenever you wish to do a fresh installation or anything like that.

You can use "Gparted" from the Live DVD/USB to shrink the current partition. We'd be glad to assist if you need help with that.

---

