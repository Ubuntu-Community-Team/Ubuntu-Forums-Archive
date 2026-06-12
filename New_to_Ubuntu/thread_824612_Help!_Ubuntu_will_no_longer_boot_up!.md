---
title: "Help! Ubuntu will no longer boot up!"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by weej on 2008-06-10
Hi, I'm a newbie to both Ubuntu and Linux generally.

Installed Ubuntu 8.04 Hardy 64-bit on new PC to dual boot with XP
Dell Vostro 200 2.2GHz Intel Dual Core
2GB RAM
250GB HDD (Partitioned)

Everything fine for a while, occasionally booting up Ubuntu to slowly get used to it and slowly configure it to suit my needs.

At the same time I have been installing programmes on the XP side including Firefox, Thunderbird, AVG, Zone Alarm, Open Office, Skype etc.

On Ubuntu installed ntfs-3g and wireless card (I think using ndiswrapper).

One day I booted up Ubuntu and the wireless was not working, permanently. Tried to reboot a few times, no change.

Left it a while, carried on working on/setting up XP. Then a few days later tried to boot Ubuntu, which failed to boot and has ever since!

I get a lot of (from what I can remember)
[---] ata1.00 blah blah... [errno=-5]
[---] ata1.00 blah blah...
[---] ata2.00 blah blah...
ending with
[---] This is not a Software problem!
[---] ....check mclog and refer to hardware vendor
[---] Kernel panic not syncing: Machine Check

then no response to any key presses.

Unfortunately I don't know how to save/copy all the lines of error messages in order to post them here to give you the full picture - can someone please tell me how to do it when Ubuntu doesn't succeed in booting up?

It boots from LiveCD (after a long time, and by the way the wireless works off of LiveCD) and I managed to reinstall from the CD, but when I tried to restart after install the same thing happens and I can't boot from hard drive.

Windows XP works fine though.

---

### Post by weej on 2008-06-10
Oh by the way I have 2 disc drives, a DVD+/-RW and DVD ROM, which I guess are among the things the system is trying to look at?

---

### Post by hyper_ch on 2008-06-10
got a digital camera? take a screenshot with it ;)

---

### Post by weej on 2008-06-10
Out-of-the-box thinking. I like it!

---

### Post by fidamehran on 2008-06-10
Dear People, I also like to know what happened to "Weej"'s Ubuntu? Can somebody shed some light?

---

### Post by weej on 2008-06-10
This evening I will take photos of the screen whilst attempting to boot up, so you can all see the exact problem I'm having...

---

### Post by hyper_ch on 2008-06-10
btw, also try to boot from the desktop cd... whether this works...

---

### Post by weej on 2008-06-10
I can boot from the Ubuntu 8.04 CD ok

---

### Post by ukripper on 2008-06-10
> **weej said:**
> Hi, I'm a newbie to both Ubuntu and Linux generally.

Installed Ubuntu 8.04 Hardy 64-bit on new PC to dual boot with XP
Dell Vostro 200 2.2GHz Intel Dual Core
2GB RAM
250GB HDD (Partitioned)

Everything fine for a while, occasionally booting up Ubuntu to slowly get used to it and slowly configure it to suit my needs.

At the same time I have been installing programmes on the XP side including Firefox, Thunderbird, AVG, Zone Alarm, Open Office, Skype etc.

On Ubuntu installed ntfs-3g and wireless card (I think using ndiswrapper).

One day I booted up Ubuntu and the wireless was not working, permanently. Tried to reboot a few times, no change.

Left it a while, carried on working on/setting up XP. Then a few days later tried to boot Ubuntu, which failed to boot and has ever since!

I get a lot of (from what I can remember)
[---] ata1.00 blah blah... [errno=-5]
[---] ata1.00 blah blah...
[---] ata2.00 blah blah...
ending with
[---] This is not a Software problem!
[---] ....check mclog and refer to hardware vendor
[---] Kernel panic not syncing: Machine Check

then no response to any key presses.

Unfortunately I don't know how to save/copy all the lines of error messages in order to post them here to give you the full picture - can someone please tell me how to do it when Ubuntu doesn't succeed in booting up?

It boots from LiveCD (after a long time, and by the way the wireless works off of LiveCD) and I managed to reinstall from the CD, but when I tried to restart after install the same thing happens and I can't boot from hard drive.

Windows XP works fine though.

Give 32bit live cd a try and install.

---

### Post by weej on 2008-06-10
Even though I have a 64 bit processor? Is that a good long term solution, if it does work, or would I do best to try and resolve the set up with 64 bit version?

---

### Post by ukripper on 2008-06-10
> **weej said:**
> Even though I have a 64 bit processor? Is that a good long term solution, if it does work, or would I do best to try and resolve the set up with 64 bit version?

32 bit will stay long term. But if you like to tinker around a lot then 64bit is a good choice. But if you want something which just works most of the time then give 32 bit a go. all of my processors in my machines are 64bit but i am using 32 bit version on them and only one machine i use 64 bit  as i like to experiment  on it quiet alot.

---

### Post by hyper_ch on 2008-06-10
64bit has advantages... if you have no specific reasons to stick to 32bit got 64bit...

---

### Post by weej on 2008-06-11
Ok, this is getting weird. Went to boot up the PC last night so I could take pictures of the screen - and it booted up perfectly! It did this a couple of times, and all seemed ok, even the wireless was working.

However I tried again just now, and the same problem happened, so here are the screenshots:

Please see the attachments.

---

### Post by hyper_ch on 2008-06-11
I have no clue what that means but IMHO it does not look good at all.

---

### Post by ukripper on 2008-06-11
> **weej said:**
> Ok, this is getting weird. Went to boot up the PC last night so I could take pictures of the screen - and it booted up perfectly! It did this a couple of times, and all seemed ok, even the wireless was working.

However I tried again just now, and the same problem happened, so here are the screenshots:

Please see the attachments.

Have you tried using the kernel - 2.6.24.16-generic shown in your grub bootloader? Try that, if that doesn't fix probably you need to try 32bit version.

---

### Post by NinjaDuck on 2008-06-11
Insert the Ubuntu CD and run the memory test.

---

### Post by weej on 2008-06-12
Yes, I'll try that.

Last night it booted ok from the 2.6.24.16-generic option, but because I had very little time I couldn't run a full test of trying several times on both the 2.6.24.16 and 2.6.24.18 to establish a reliable trend. So I will do that and get back to you with the results.

By the way, I have only had a second option on the boot screen since I installed extra video and audio codecs/drivers/lib... (inc.VLC player) following a guide on the forums. Anyone know why this would have happened? Do you know how I can remove one of the options, *IF* I find out that I can only boot successfully from one?

---

### Post by ukripper on 2008-06-12
> **weej said:**
> Yes, I'll try that.

Last night it booted ok from the 2.6.24.16-generic option, but because I had very little time I couldn't run a full test of trying several times on both the 2.6.24.16 and 2.6.24.18 to establish a reliable trend. So I will do that and get back to you with the results.

By the way, I have only had a second option on the boot screen since I installed extra video and audio codecs/drivers/lib... (inc.VLC player) following a guide on the forums. Anyone know why this would have happened? Do you know how I can remove one of the options, *IF* I find out that I can only boot successfully from one?

i personally think kernel revision 24-18 has something to do with kernel panic on your hardware. If it works fine on -16 stick to that until next revision of kernel is available through update-manager.

Or you can still update revision to 24-19 through proposed repo.

Go to system-->Administration-->Software sources-->find PROPOSED REPOSITORY and tick on it. and then close.

and then go to terminal type folloling:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

this will make your proposed kernel update available which is 24-19. after reboot it will be available in your grub menu. try that if that fixes your issues of kernel panic.

regards,
ukripper.

---

### Post by weej on 2008-06-12
Thanks, will try it tonight.

---

