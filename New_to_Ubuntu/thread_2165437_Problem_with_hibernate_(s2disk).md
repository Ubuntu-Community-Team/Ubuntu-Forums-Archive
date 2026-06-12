---
title: "Problem with hibernate (s2disk)"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by DesertEagle on 2013-08-04
Helo, folks

Sorry to reopen a dying thread, but I can't find help anywhere(i.e:Google, askubuntu, #ubuntu, even Arch linux forums)

My s2disk stopped working 2-3 days ago, when it used to work fine. It first complained when trying to resume, that /dev/sdc5 wasn't a swap partition. Now, it will say "Starting Snapshoot" but never completes it, doesn't show the percentage completed, doesn't show anything at all past that. Ctrl+Alt+Del does nothing, so I have to hard-boot it.

Here is my pm-powersave.log
[http://pastebin.com/pBZPBtFW](http://pastebin.com/pBZPBtFW)

And here is my pm-suspend.log
[http://pastebin.com/zM5SABRh](http://pastebin.com/zM5SABRh)

For what it's worth, I've always hibernated my PC using "sudo s2disk" and the swap partition is on my SSD, which also holds / and boot

Thanks for any help!

---

### Post by Toz on 2013-08-04
*Moved post to its own thread since its a slightly different issue than the [original thread]("http://ubuntuforums.org/showthread.php?t=2134259").*

According to your pm-suspend.log file, hibernate/thaw is working. What happens when you try to resume? Do the keyboard keys/laptop keys flash at all? Is there drive activity? If you go to the first tty (Ctrl+Alt+F1), do you get a text console?

What is the make/model of your computer?
Do you recall which updates were made 2-3 days ago?

What does the following command return:
```
swapon -s
```

Can you post the results of this command:
```
cat /var/log/syslog | grep PM:
```

---

### Post by DesertEagle on 2013-08-05
Thank you for taking the time, Toz! 

My keyboard and mouse become completely useless, and I can see the HDD activity LEDs blinking, albeit slowly. The fans do sound slower, but the whole system is still on. There's been quite a few updates from update-manager, so I wouldn't be able to tell you if anything's changed, other than uswsusp is the latest in the repositories (from 2011, iirc)

PC is a custom rig: Asus 990FX, AMD Athlon FX 8 core, 4G DDR3 128GB SSD for swap, root and boot, and 2x NVIDIA 9800 GT

Swapon returns:

Filename				Type		Size	Used	Priority
/dev/sdc5                               partition	4048892	0	-1

Here's the syslog:
[http://pastebin.com/cxDh8a72](http://pastebin.com/cxDh8a72)

Thanks again for your help!

---

### Post by Toz on 2013-08-05
> Aug  4 17:30:57 deaglepc kernel: [83315.443761] PM: Device 12:0:0:0 failed to freeze async: error -5
> Aug  4 17:30:57 deaglepc kernel: [83318.588264] PM: Device 16:0:0:0 failed to restore async: error 131072
Using lspci, can you look up and identify which devices are at those addresses?

> Aug  4 18:10:00 deaglepc kernel: [    2.725999] PM: Checking hibernation image partition /dev/sdc5
Aug  4 18:10:00 deaglepc kernel: [    2.726008] PM: Hibernation image partition 8:37 present
Aug  4 18:10:00 deaglepc kernel: [    2.726009] PM: Looking for hibernation image.
Aug  4 18:10:00 deaglepc kernel: [    2.726315] PM: Image not found (code -22)
Aug  4 18:10:00 deaglepc kernel: [    2.726317] PM: Hibernation image not present or could not be loaded.
Here is the message you are talking about. Can you try booting once with the "noresume" kernel parameter to see if it clears out that message (see the "Kernel Boot Parameters" link in my signature for info on how to temporarily boot with a kernel parameter)? Post back the same syslog entries after you have done that.

---

### Post by DesertEagle on 2013-08-05
I rebooted with noresume, but I'm not familiar with looking up an address lspci, so here's what I figure will help:

lspci -vb | grep 16
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])

lspci -vb | grep 12
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])

cat /var/log/syslog | grep PM
[http://pastebin.com/yFHQknm0](http://pastebin.com/yFHQknm0)

pastebinit /var/log/pm-powersave.log
[http://pastebin.com/0TBUXq53](http://pastebin.com/0TBUXq53)

pastebinit /var/log/pm-suspend.log
[http://pastebin.com/bJWPCatr](http://pastebin.com/bJWPCatr)

Thanks once more

---

### Post by Toz on 2013-08-05
> lspci -vb | grep 16
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])

lspci -vb | grep 12
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
Which USB devices do you have plugged in? Can you provide:
```
lsusb -t
```
Any firewire devices plugged in?

If you look in /var/log/apt, you will see some apt log files. Can you review them and see what was installed 2-3 days ago? If it was a kernel update, have you tried booting into the previous kernel to see if still works?

And one more thing. What are you using s2disk? Did pm-hibernate not work? Can you give pm-hibernate a try? Post back logs again.

---

### Post by DesertEagle on 2013-08-05
I do have one firewire device plugged in, however it's always been there even when s2disk used to work. The reason I used s2disk directly, quite frankly, is because I didn't know about pm-hibernate. However, when I try using pm-hibernate, the hibernating screen shows s2disk, so I figured it was just a script for s2disk (Also didn't work. It just stalled).

By the way, immediately after it complained about the swap partition, I poked around the uswsusp.conf file, checking to make sure the resume line points to the right partition. I even used dpkg-reconfigure on uswsusp to make sure the config file was done right. I've even forced an uninstall of the package, and then reinstalled it to see if it would work.

Anyhow, here's the lsusb -t
[http://pastebin.com/z85fJr25](http://pastebin.com/z85fJr25)

Here's the apt logs
[http://pastebin.com/Dz20XTTr](http://pastebin.com/Dz20XTTr)

I searched for "kernel", "linux", and "image" but found nothing on them, so I don't think it was a kernel update. For what it's worth, I have 3.2.0-36.57 installed, but now that I just checked, the dummy package (linux-image-generic with no version on the package name) says the latest version is 3.2.0.51.61 while the installed version is 3.2.36.43.

I have no clue, so here's a screenshot in case it makes sense to you.
[http://i.imgur.com/hnlCz2m.png](http://i.imgur.com/hnlCz2m.png)

---

### Post by Toz on 2013-08-05
> **DesertEagle said:**
> I do have one firewire device plugged in, however it's always been there even when s2disk used to work. The reason I used s2disk directly, quite frankly, is because I didn't know about pm-hibernate. However, when I try using pm-hibernate, the hibernating screen shows s2disk, so I figured it was just a script for s2disk (Also didn't work. It just stalled).
Try this. As root, create the file **/etc/pm/config.d/config** with the following contents:
```
SLEEP_MODULE="kernel"
```
...and try pm-hibernate again. This will use the default kernel method instead of uswsusp. If it doesn't work, you can just delete the file to return back to uswsusp.

> By the way, immediately after it complained about the swap partition, I poked around the uswsusp.conf file, checking to make sure the resume line points to the right partition. I even used dpkg-reconfigure on uswsusp to make sure the config file was done right. I've even forced an uninstall of the package, and then reinstalled it to see if it would work.
Sometimes using the **resume=/dev/<swap_partition>** kernel parameter works (replace <swap_partition> with the actual name of the swap partition.

> Anyhow, here's the lsusb -t
[http://pastebin.com/z85fJr25](http://pastebin.com/z85fJr25)

Here's the apt logs
[http://pastebin.com/Dz20XTTr](http://pastebin.com/Dz20XTTr)

I searched for "kernel", "linux", and "image" but found nothing on them, so I don't think it was a kernel update. For what it's worth, I have 3.2.0-36.57 installed, but now that I just checked, the dummy package (linux-image-generic with no version on the package name) says the latest version is 3.2.0.51.61 while the installed version is 3.2.36.43.
You could try installing the latest kernel (3.2.0.51.61) to see if it works better.

However, since this was all working 2-3 days ago and now doesn't, I'd be more inclined to believe that an updated/installed package is the cause. But there is nothing in your apt logs that sticks out as being a cause.

---

### Post by DesertEagle on 2013-08-05
> **Toz said:**
> Sometimes using the **resume=/dev/<swap_partition>** kernel parameter works (replace <swap_partition> with the actual name of the swap partition.


My /etc/uswsusp.conf says:

resume device = /dev/sdc5

should "device" not be there?

---

### Post by Toz on 2013-08-06
> **DesertEagle said:**
> My /etc/uswsusp.conf says:

resume device = /dev/sdc5

should "device" not be there?

I meant as a kernel parameter. Edit /etc/default/grub and change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="resume=/dev/sdc5"
```
...then run:
```
sudo update-grub
```
...and reboot.

Can you post back the following:
```
swapon -s
```
```
sudo blkid
```
```
cat /etc/default/grub | grep -v ^# | sed '/^$/d'
```

---

### Post by DesertEagle on 2013-08-06
> **Toz said:**
>  
```
GRUB_CMDLINE_LINUX="resume=/dev/sdc5"
```

I had already added it, however I don't know if the ACPI part should be there. I believe I also added it. Could it be causing an issue?
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force resume=/dev/sdc5"
```

swapon -s
```
Filename				Type		Size	Used	Priority
/dev/sdc5                               partition	4048892	0	-1
```

sudo blkid
```
/dev/sda1: LABEL="149GB" UUID="1607301a-a5e0-4d68-89e9-5b61d2cd8363" TYPE="reiserfs" 
/dev/sdb1: LABEL="Home" UUID="61b5c3ce-c178-44a3-a086-7fd5056859ee" TYPE="reiserfs" 
/dev/sdc1: UUID="b3241960-8f06-4d7d-90bf-6b1b8128f135" TYPE="ext4" 
/dev/sdc5: UUID="bf637647-1b1c-42e5-ab84-d3d3f9a74375" TYPE="swap" 
/dev/sdc6: UUID="12b67925-2f8a-4cfc-9fed-0ef220894a30" TYPE="reiserfs" 
/dev/sdd1: LABEL="150GB" UUID="7C7C-3868" TYPE="vfat" 
/dev/sdi1: LABEL="Win7" UUID="B2B81051B8101687" TYPE="ntfs" 
```

cat /etc/default/grub | grep -v ^# | sed '/^$/d'
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force resume=/dev/sdc5"
GRUB_CMDLINE_LINUX=""
```

---

### Post by Toz on 2013-08-06
When did you add acpi=force? That might interfere. Try removing it:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
...re-running:
```
sudo update-grub
```
...rebooting and testing.

When rebooted, post back:
```
cat /proc/cmdline
```

---

### Post by DesertEagle on 2013-08-06
It works! Thank you so much, Toz!! =D>

cat /proc/cmdline
```
BOOT_IMAGE=/vmlinuz-3.2.0-36-generic root=UUID=12b67925-2f8a-4cfc-9fed-0ef220894a30 ro quiet splash vt.handoff=7
```

---

### Post by Toz on 2013-08-06
Which begs the question: why did you use acpi=force? Was it solve another problem you were having? If so, you may find that problem has returned.

---

### Post by DesertEagle on 2013-08-06
You know, I have no clue.

I just put back the line, removed the /etc/pm/config.d/config file, and even tried using s2disk again, and both it and pm-hibernate work now.

So yeah, no clue :-?

---

