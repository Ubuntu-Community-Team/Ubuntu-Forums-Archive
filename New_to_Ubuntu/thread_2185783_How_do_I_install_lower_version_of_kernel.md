---
title: "How do I install lower version of kernel?"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by xyepblra on 2013-11-04
I followed the instructions from MTE on [how to speed up my Ubuntu]("http://www.maketecheasier.com/speed-up-linux-computer"), and the first thing I did was remove older kernel images as well as shorten the available kernel versions list.

What I did next was:
```
Start-Date: 2013-11-02  12:59:45
Commandline: aptdaemon role='role-remove-packages' sender=':1.108'
Remove: linux-headers-3.5.0-40-generic:i386 (3.5.0-40.62~precise1), linux-image-3.5.0-40-generic:i386 (3.5.0-40.62~precise1), linux-headers-3.5.0-40:i386 (3.5.0-40.62~precise1), linux-headers-3.5.0-41:i386 (3.5.0-41.64~precise1), linux-headers-3.5.0-39:i386 (3.5.0-39.60~precise1), linux-headers-3.5.0-41-generic:i386 (3.5.0-41.64~precise1), linux-image-3.5.0-41-generic:i386 (3.5.0-41.64~precise1), linux-headers-3.5.0-39-generic:i386 (3.5.0-39.60~precise1), linux-image-3.5.0-39-generic:i386 (3.5.0-39.60~precise1)
End-Date: 2013-11-02  13:01:40

```

I believe the kernels listed above were the versions I have had installed before I did the things listed in clause 4 of the MTE guide.
After the update my kernel version changed to:
```
uname -r
3.9.2-ck1

```
Well, the problem with 3.9.2-ck1 is that networking manager is acting really strange: it does not start up at system boot, and the networking indicator on the media control panel blinks constantly after I choose "Wireless network".

My question is, how do I revert to an older kernel version, say, 3.5.0-40.62~precise1, given that I don't have it present in my system?

---

### Post by BBQdave on 2013-11-04
> **xyepblra said:**
> My question is, how do I revert to an older kernel version...

Perhaps too simple of an approach...

I am running Ubuntu Unity 12.04LTS 64-bit with Kernel Linux 3.2.0-55 on a Lenovo Thinkpad T400, smooth and responsive :)

Hardware: Intel® Core™2 Duo CPU T9400 @ 2.53GHz × 2 with 2 gigs of RAM and a 7200 RPM HD.

The stock Kernel Linux with 12.04LTS performs great. And I was able to gain system speed by adjusting Dash logging.

System Settings > Privacy > Applications tab > Do not log activities from the following applications: *Firefox Web Browser*

Firefox has it's own search and history function, seemed redundant (and slowed my system) with the same function in Dash.

---

### Post by DuckHook on 2013-11-04
```
sudo apt-get update && sudo apt-get install linux-image-3.5.0-40-generic linux-headers-3.5.0-40-generic linux-headers-3.5.0-40
```
```
sudo update-grub
```
This will download the older kernel and its headers, and update GRUB to detect it at boot. You may have to hold down the shift key during boot to bring up GRUB menu and then choose your preferred kernel. Be aware that some of your programs/drivers may have already be recompiled for the new kernel and may not run well on the older one. This is unlikely to have happened, but kernel reversions do come with their own set of problems.

You may wish to edit /etc/default/grub to have it select your old kernel as the default to load at boot. Remember to run update-grub after you make any changes.

---

### Post by Dave_L on 2013-11-04
In 12.04 you have a choice of three kernel series: 3.2.x, 3.5.x and 3.8.x. The corresponding metapackage(s) are: linux-generic (for 3.2.x), linux-generic-lts-quantal (for 3.5.x) or linux-generic-lts-raring (for 3.8.x).

---

### Post by xyepblra on 2013-11-05
Thank you, DuckHook, but your command didn't work, unfortunately, due to response that in English must sound something like 'the candidate package was not found, it is either obsolete or has been removed, but it is listed in the dependencies list of another package'.

Dave_L, do you think the command advised by DuckHook can be applied in fuzzy mode, so that to install any kernel available in series 3.2?

---

### Post by Dave_L on 2013-11-05
I don't know what you mean by "fuzzy mode".

If you want to install the latest 3.2.x kernel on 12.04:

```
sudo apt-get -s install linux-generic
```

The -s option means "simulate". The command will tell you what it will do, without making any changes.

If the output looks reasonable, then you can use the command without the -s option:

```
sudo apt-get install linux-generic
```

Personally I prefer synaptic as a package manager, rather than using apt-get directly. With synaptic it's easier to see what packages are available, what their dependencies are, etc.

---

### Post by xyepblra on 2013-11-05
Thank you,  Dave_L, Synaptic did the thing for me perfectly.

---

