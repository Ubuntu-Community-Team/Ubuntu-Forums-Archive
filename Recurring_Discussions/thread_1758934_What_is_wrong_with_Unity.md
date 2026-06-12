---
title: "What is wrong with Unity?"
date: 2011-05-15
forum: Recurring Discussions
---

### Post by VOT Productions on 2011-05-15
I'm planning to do a "Fix Unity's problems" topic, but I need to know what's wrong with it.

---

### Post by NormanFLinux on 2011-05-15
Nothing. The problems with Unity can be attributed to a buggy kernel 11.04 was shipped with.

The latest version, 2.6.39.0 restores the desktop to the state it was in previous versions of Ubuntu. Every one who has experienced the freeze problem, especially with their wireless connection, should apply the new kernel and reboot.

I couldn't believe the difference when I reactivated my wireless connection! Before, it induced a kernel panic and would lock up the desktop. Now all that memory-hogging usage is gone!

---

### Post by VOT Productions on 2011-05-15
You mean my p54usb would work?

---

### Post by NormanFLinux on 2011-05-15
My Broadcom driver kept freezing and I had to shut it off in the BIOS just to get a working desktop. I realized the problem had to be either with the driver or with the kernel. I decided it was the kernel and my hunch proved correct.

You would think Canonical would have fixed the kernel before they shipped Natty out. My initial impression of it was it was unusable. Now I feel its pretty functional. Several hours later, no more lockups!

---

### Post by VOT Productions on 2011-05-15
Where do I get it? I'm having wireless problems too, and since I use a older kernel I miss out on the goodies :(

---

### Post by nrundy on 2011-05-15
> **NormanFLinux said:**
> Nothing. The problems with Unity can be attributed to a buggy kernel 11.04 was shipped with.

The latest version, 2.6.39.0 restores the desktop to the state it was in previous versions of Ubuntu. Every one who has experienced the freeze problem, especially with their wireless connection, should apply the new kernel and reboot.

I couldn't believe the difference when I reactivated my wireless connection! Before, it induced a kernel panic and would lock up the desktop. Now all that memory-hogging usage is gone!

Is this kernel update received through the regular Update Manager update process? or does the user have to do "extracurricular" stuff to get it?

---

### Post by NormanFLinux on 2011-05-15
You will have to install a PPA to get the update to install the new kernel.

sudo add-apt-repository ppa:kernel-ppa/ppa

sudo apt-get update

apt-cache showpkg linux-headers

sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

Run the above commands in terminal and once the upgrade is finished, reboot.

You should see the new kernel version in the main tab of System Monitor.

Since its not pushed out as part of the regular update, these instructions will let any one enjoy Natty the way it was meant to be enjoyed in the first place - as a brand new, trouble-free computing experience.

---

