---
title: "Busy box."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Xafira on 2008-05-04
Hi, I'm brand new when it comes to Ubuntu, and earlier today when I tried to boot up ubuntu, something called busybox came up. I have no idea why it did, or how I can get past it. I tried some of the commands, but nothing seemed to do anything, at all. So do any of you guys know what I can do with this?

---

### Post by superprash2003 on 2008-05-04
are you booting via live cd? if not then doesnt rebooting fix the problem/

---

### Post by iSplicer on 2008-05-04
Thats wierd. Exactly which ISO did you use to install?

---

### Post by Aearenda on 2008-05-04
There are several threads on problems of this sort in the forums, and several causes. They usually revolve around being unable to find the root partition during boot, because something has changed or moved. You might like to use the forum search to find them - look for 'hardy busybox'. 

The first question is, is this a Dell 530 (because the fix there is easy)?

---

### Post by gibberish on 2008-05-04
I have this problem on Dell 530s. I have an HL-DT-ST DVD +-rw GSA-H31N ATA drive which doesn't seem to be recognized (same with PCLOS also--all flavors). I tried the all-generic-ide thing, but it didn't work. I also tried making a live USB (pendrivelinux method) which works for PCLOS but not for Hardy. Then even if I get PCLOS running ndiswrapper doesn't work for my DWA-140 usb NIC. I haven't changed to RAID in the BIOS, 'cause I don't know what this will do to my system (I have Vista on, and don't want to lose it)
I'm starting to feel I've spent too much time on this, and will just need to wait until Linux is more mature.

---

### Post by Xafira on 2008-05-04
Thanks for the replies, and no, this is not a dell, I don't boot from a live cd, and I used the windows based installer inside the ubuntu folder to install it, not any ISO as far as I know. But anyways, the OS booted up now, so the issue may be solved:)

---

### Post by Danish989 on 2008-05-04
I'm having the same exact problem, but only difference is I used ubuntu for 2 days after installing (hardy heron) and then I restarted from xp to boot into ubuntu and got BusyBox out of nowhere .. I'm still stuck at it.

---

### Post by Aearenda on 2008-05-04
EDIT: Sorry, reread the thread and realised you've tried this. Pls ignore - but note that you can flip RAID to IDE modes in the BIOS during testing, and so long as you start the appropriate OS for the setting chosen, Windows will not care.

gibberish: You don't have to switch to RAID mode, using all_generic_ide as a kernel boot parameter will work. See post 15 in [http://ubuntuforums.org/showthread.php?p=4799028](http://ubuntuforums.org/showthread.php?p=4799028) for details.

---

### Post by Aearenda on 2008-05-04
Danish989: what happens if you turn the machine off, and then back on (not immediately - wait for the power to settle and drives to stop, switching off and on again instantly can cause damage)? 

Maybe you have tried that already. My thinking is that Windows may have left things in a different state to a cold power-on.

---

### Post by gibberish on 2008-05-19
Thanks Aearenda. I was busy for a while and couldn't mess with Ubuntu. I searched around, and found that if I used "linux all-generic-ide irqpoll" instead, everything worked just fine. Probably not the place for it, but got my DWA-140 usb wireless NIC working with ndiswrapper using an older XP driver. Now just have to get suspend/hibernate working consistently.

---

### Post by |{urse on 2008-05-19
> I have this problem on Dell 530s. I have an HL-DT-ST DVD +-rw GSA-H31N ATA drive which doesn't seem to be recognized (same with PCLOS also--all flavors). I tried the all-generic-ide thing, but it didn't work. I also tried making a live USB (pendrivelinux method) which works for PCLOS but not for Hardy. Then even if I get PCLOS running ndiswrapper doesn't work for my DWA-140 usb NIC. I haven't changed to RAID in the BIOS, 'cause I don't know what this will do to my system (I have Vista on, and don't want to lose it)
I'm starting to feel I've spent too much time on this, and will just need to wait until Linux is more mature.

Okay, rtfm to eliminate pebcak, Linux will never be mature because it doesn't have a life expectancy, It will always be growing and improving and have growing pains along the way. If you want a fully compatible system try designing one, use well known linux compatible parts. Don't expect your 100% vista compatible machine to be 100% linux happy.

---

### Post by gibberish on 2008-05-19
Thanks. What does "rtfm to eliminate pebcak" mean? I assume this is something helpful to assist with my problem.

---

### Post by |{urse on 2008-05-19
No not really helpful. lol but true. However, If you give me the output of

dmesg | tail


i might be able to help with your suspend/resume trouble

---

### Post by |{urse on 2008-05-19
or not :lolflag:
I'm guessing acpi is buggy for you
try this post using APM rather than acpi

[http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)

---

### Post by gibberish on 2008-05-20
thanks. I will give it a try when I have a chance. Hopefully in next couple of days. I will post the output then.

---

### Post by gibberish on 2008-05-26
tried the no acpi trick. Didn't work: box is Dell 530s, pretty new. I'm not sure it fully supports APM. 
dmesg | list output
:~$ dmesg | tail
[   53.865719] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   53.865804] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.139205] set status page addr 0x00033000
[   71.759651] NET: Registered protocol family 10
[   71.759887] lo: Disabled Privacy Extensions
[   71.760302] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   71.760505] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.108350] NET: Registered protocol family 17
[   84.244140] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.413558] wlan0: no IPv6 routers present
 
wasn't anything about this in the manual. Or near my chair. No question there's an ID ten T type of problem.

---

