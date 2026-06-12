---
title: "Hello, I'm new here."
date: 2012-04-04
forum: New to Ubuntu
---

### Post by DNRDustin on 2012-04-04
Mostly this post is just to make my presence known on the forum, hello all. I have a few questions that I'm sure I will find the answers to before anyone responds. I am entirely new to the whole Ubuntu/Linux thing, and am a little nervous coming from being a lifelong windows user. Just decided to build a new pc out of old parts i had, and figured Ubuntu would run better on this p.o.s. than windows would. Gigabyte GA-7n400 pro2 MB, AMD Athlon xp CPU, 128mb ATI radeon something or rather GFX, 2Gb ddr400 RAM,  and a 160Gb Western Digital IDE HD. 

1. Takes 3 hours to boot from live cd, 1 1/2 from live usb. So its a little frustrating to decide its not going to boot past the "Begin Loading" screen after 5 or so. This is normal? I doubt it.

2. So i finally get to do a fresh format and install, go to boot and it doesnt see the os. just hangs at "Boot from" BIOS screen. After some reading i figure that having Windows on the HD before could cause problems, so I get Restatux to fix grub and file system.

3. Reboots fine. I see my grub screen and it boots right up when selecting my most current kernel. Now it gets irritating.

4. Reboot again and either A- I get no grub screen, it goes straight to boot but it wont because
                                                of various problems. network launch fails, PulseAudio issue, drive does
                                                not have root, files are corrupt or missing.
                                           B- I get grub screen, and neither the current or previous kernel will boot. Same 
                                                reasons as "A" pretty much.
                                           C- I grub screen and run restore to fix disk or remount drive or whatever, 
                                                pretty much anything in the restore menu will allow me to boot right up after.

Any thoughts? Keep in mind I have limited terminal knowledge, and am uber noob about getting around inside a linux file system. I am reading up on it, but it doesnt seem that commands are universal ie "type this, and that will always happen".

Sincerely, a frustrated Noobuntu user.):P

---

### Post by mastablasta on 2012-04-04
obviously something went very wrong during install. first sign -  booting so long from live CD is not normal. sure it take s a bit longer than from HDD but that's maybe like a minute or 3 instead of 20 seconds.

1. Did you check the iso image upon download with md5sum check? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. Did you burn the Image to the cd propperly - as in burn image not extract it and burn it on cd?
3. Did you check the CD that it burned data correctly? what programme di you use to create the USB?
4. Finnaly how did you install it? did you follow some tutorial? like this [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
did you use default settings on install? or did you customize it? what file format did you use when you formated the hard disk during install?

something is definatelly very wrong. you shouldn't even see grub after instalation unless you have windows (or other OS) installed on same hardware.

also may i suggets since it seem like you have older ATi graphics card if all is a bit slow (after porpper install) tht you try Xubuntu instead or use Unity 2D on login. but if it works ok then just leave it. some older ATI card don't have such a good 3D acceleration support. and Ubuntu default interface uses 3D hardware acceleration.

---

### Post by DNRDustin on 2012-04-07
I DL'd a new 11.10 .iso and md5 check was fine. Logging in with 2d doesnt seem to make a difference. Still having the same boot issues, even though I did a default install from boot disk creator using the new .iso. Also, flash is giving me problems. I can watch some YouTube videos, but the ones that will play dont work well(I cant move the mouse without video skipping). Install with flash aid seemed to be successful, and firefox doesnt say there are any flash errors. I have restricted content installed also.

---

