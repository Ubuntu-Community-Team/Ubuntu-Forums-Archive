---
title: "My computer won't boot"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by willneu97 on 2012-02-20
So I have a Dell Inspiron 1545 that runs on Ubuntu 11.10, after I uninstalled Windows 7. I tried to reinstall windows 7, but it wouldn't let me. I forget what the problem was, and now my computer won't boot from anything. I turn it on, I see the Dell logo and the loading bar, but when the loading bar reaches the end, it stops. I can't open my boot menu or BIOS. Can anyone help?

---

### Post by Penguin360 on 2012-02-20
For Dell computer, F2 will let you enter BIOS setup, F12 will let you enter your boot menu.

---

### Post by 2F4U on 2012-02-20
Which loading bar do you see, the one from Ubuntu or the one from Windows?

---

### Post by willneu97 on 2012-02-20
> **2F4U said:**
> Which loading bar do you see, the one from Ubuntu or the one from Windows?

The loading bar for Dell

---

### Post by willneu97 on 2012-02-20
> **CodingBeaver said:**
> For Dell computer, F2 will let you enter BIOS setup, F12 will let you enter your boot menu.

I know, but when I try to do that nothing happens.

---

### Post by Penguin360 on 2012-02-20
> **willneu97 said:**
> I know, but when I try to do that nothing happens.
Maybe you hit the key too late? You have to hit the key right after Dell log appears, otherwise, it will start loading your OS.

---

### Post by willneu97 on 2012-02-20
> **CodingBeaver said:**
> Maybe you hit the key too late? You have to hit the key right after Dell log appears, otherwise, it will start loading your OS.
Thanks, I got it to work.

---

### Post by Penguin360 on 2012-02-20
> **willneu97 said:**
> Thanks, I got it to work.

How did you do it? Would you mind sharing your experience?

---

### Post by willneu97 on 2012-02-20
I know what the problem is now when I install windows. It says that windows can't be installed to either of my discs, because they are not formatted as NTFS. I don't get it. Before I installed ubuntu windows worked. Do I have to uninstall ubuntu? How would I go about doing that?

---

### Post by 2F4U on 2012-02-20
You could boot into a liveCD and use the partitioning tool to delete the Ubuntu partitions.

---

### Post by willneu97 on 2012-02-20
> **2F4U said:**
> You could boot into a liveCD and use the partitioning tool to delete the Ubuntu partitions.

Is a liveCD what I used to install it?

---

### Post by HavarN on 2012-02-20
If it gave you the option to try Ubuntu before you installed it, then yes. It's a live cd.

---

### Post by HeroOfCanton on 2012-02-20
You need to select a partition and set it up for use with windows. You should be given that option when you run the windows setup/recovery. Are trying to setup a dual boot system, or just going back to windows completely?

---

### Post by willneu97 on 2012-02-22
> **HeroOfCanton said:**
> You need to select a partition and set it up for use with windows. You should be given that option when you run the windows setup/recovery. Are trying to setup a dual boot system, or just going back to windows completely?

I'm trying to go back to Windows completely. I don't know how to set it up for use with windows, and I am not given the option to do so (at least I can't see it)

---

### Post by willneu97 on 2012-02-22
> **HavarN said:**
> If it gave you the option to try Ubuntu before you installed it, then yes. It's a live cd.
I booted from the disc, it only gives me the option to install ubuntu or try it. What do I do?

EDIT: Never mind, I got to the tool. How do I delete the ubuntu partitions? Do I just delete everything I see there?
[[IMG]http://i.imgur.com/j4vj0.jpg[/IMG]](http://imgur.com/j4vj0)

---

### Post by HavarN on 2012-02-23
That's the installation program.

You need to go back to the initial screen and press Try Ubuntu.

Then you run gparted, Partition Editor in the menus. gparted is pretty easy and straight forward to use.

---

### Post by eriktheblu on 2012-02-23
> **willneu97 said:**
>  How do I delete the ubuntu partitions? Do I just delete everything I see there?
That should do the trick.

If you're wanting to dual boot (choose Windows or Ubuntu on startup) do the following:
1. Delete the larger partition (/dev/sda1) but leave the smaller swap partition (/dev/sda5)
2. Create a new ext4 partition in the free space aligned to the right side. Allocate at least 30 GB, but leave at least 50 or unformatted for Windows.
3. Install Windows
4. Install Ubuntu and select options to boot along side other OSs.

---

### Post by HavarN on 2012-02-23
Actually, the installation program won't apply the changes you make to the partition table before you start the actual installation process/copying files onto the harddrive. If you don't plan to reinstall Ubuntu, just delete the Ubuntu partitions, you will have to use gparted or another partition editor.

---

### Post by willneu97 on 2012-02-23
> **HavarN said:**
> Actually, the installation program won't apply the changes you make to the partition table before you start the actual installation process/copying files onto the harddrive. If you don't plan to reinstall Ubuntu, just delete the Ubuntu partitions, you will have to use gparted or another partition editor.

The second partition is locked. How do I unlock it? Should I?
[[IMG]http://i.imgur.com/R8u8K.jpg[/IMG]](http://imgur.com/R8u8K)

EDIT: Never mind, found a way. Thanks for all the help! I have Windows 7 up and running. You guys are great!

---

