---
title: "Need to fix ROOT issues"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by iamsamami on 2012-02-13
Two weeks to get back into town, to get online again.
I've got an HP netbook w/ ubuntu 10.10, and it's giving me ROOT issues.
Right now am trying to download a bootable usb version.
I can see USB in boot options, but can't use usb other than for the mouse.
Same goes for memory flash drive, and have no cd drive.
Cannot remember password for su, but will try to add new login acct.
Applications don't work that wants to work via root;
Gparted, MountManager, Synaptic, etc.
Also cannot connect online w/ wifi.
Am trying to get a network cable to try to access my desktop w/ win98;
at least hope to backup files.
 
Questions:
If I get a bootable usb version to open, will it create a whole fresh system?
or will it allow to re-install on top of existing?
 
Is there there away to use usb to maybe run gparted from and split hdd
for a different drive to install a new ubuntu and then transfer files
for backup before nuking everything and starting all over???
 
Probably, the backup is the biggest issue.
Over 12 gigs of audio I really don't want to have to re-download
at a rate of 150 kbs, if that!!!
 
Why am I having issues w/ using usb drives?
I mean, I can't even get a backup through usb!!???
 
Oh, whatabout through Bluetooth? Could that be a way to try?
When I try to open bluetooth, it shows only that I don't have devices hooked up.
 
OH, and I tried recovery mode; and it doesn't show up in boot options.
I saw some reference about that, also some log file showed something like a timeout of 0 (zero) seconds.
 
What could I look FOR through the log files that might be helpful?
 
Sure hope I can find a way through this mess.
Please help me with this nightmare.
Any quick-fixes or work-arounds or links to faqs or with any ideas.
 
Thanks,
IamSamAmI
(no matter how long it takes, it's going to TAKE something)

---

### Post by Ms. Daisy on 2012-02-14
There are a whole lot of issues in your post.  Let's tackle one at a time.

I recommend first replacing the password that you forgot.

Look at this thread for a solution:

[http://ubuntuforums.org/showthread.php?t=1887124](http://ubuntuforums.org/showthread.php?t=1887124)

---

### Post by iamsamami on 2012-02-22
> **Ms. Daisy said:**
> There are a whole lot of issues in your post. Let's tackle one at a time.
 
I recommend first replacing the password that you forgot.
 
Look at this thread for a solution:
 
[http://ubuntuforums.org/showthread.php?t=1887124](http://ubuntuforums.org/showthread.php?t=1887124)
 
Thanks for the reply Ms Daisy, but I mentioned that I cannot boot into Recovery mode from boot options.
I cannot setup a different user account w/o su or sudo or root.
I then proceeded to ask other questions I need some help understanding.
 
Most important is this:
If I get a bootable version of Ubuntu onto a flash drive that my HP Netbook will recognize in boot options and then proceed -->
Will it "Install" or "Re-Install" Ubuntu?
Will it allow me back up files first before it proceeds?
 
If not, what can I do first or what other way can I try to get a backup of my files first?
 
Please, I have very limitable resources available to work with. This Library is very limiting in files I can download. At home I have a desktop with win98 that does not cooperate with the Window's solutions to the files I need that will help. And as well, am also limited to even how often often I can even get back online again.
 
Please, I need help. I have tried everything I can understand. I am at this point.
 
Thanks very much, to you Ms Daisy, and to this forum and to those who look onto this post and can guide me forward.
 
IamSamAmI

---

### Post by Ms. Daisy on 2012-02-22
> **iamsamami said:**
> If I get a bootable version of Ubuntu onto a flash drive that my HP Netbook will recognize in boot options and then proceed -->
Will it "Install" or "Re-Install" Ubuntu?

No, it will not install Ubuntu as long as you do not choose to install it.  If you boot from the USB you will be running the pen drive as the operating system instead of from the hard drive.
> **iamsamami said:**
> Will it allow me back up files first before it proceeds?
 
If not, what can I do first or what other way can I try to get a backup of my files first 
Yes. You should be able to mount the hard drive and access its data while you are running the live USB. (I'm hoping that you didn't encrypt your home directory. If you did that will significantly complicate things.)  **It would be very wise to back up the data before proceeding with any possible fixes.**

After you have backed up, let's go back to this:
> **iamsamami said:**
> OH, and I tried recovery mode; and it doesn't show up in boot options.
I saw some reference about that, also some log file showed something like a timeout of 0 (zero) seconds. 

To access recovery, have you tried this from the [psychocats tutorial]("http://www.psychocats.net/ubuntu/resetpassword")?
[QUOTE=psychocats]If you have a single-boot (Ubuntu is the only operating system on your computer), to get the boot menu to show, you have to hold down the *Shift* key during bootup. [/QUOTE]

But the first thing you should do is backup your files.

---

### Post by iamsamami on 2012-03-18
Thanks again Ms. Daisy,
finally got a neighbor to help me load up an iso image onto a flashdrive; saw it work on his machine, took it home and it works on my netbook. I can now start backing up my files before doing anything else.
O.k., I brought the netbook with me this time hoping it might allow me to hook onto a wireless signal, but it states it is not yet ready. I assume it wants a full installation.
Yet when I tried to go to Terminal and login su, I still couldn't get past the same root issue; though I did see him logged in as root while on his machine.
Yes, I did try different ways of seeing recovery mode. It doesn't show up. That neighbor claims it won't show up because it will want to re-install the pre-existing WinXP that was nuked before linux got installed. Makes sense.
Will try to spend more time this evening at neighbor to pick his brain for how and what to get all these issues worked out. By the time I get another chance to get online the only other thing I'd like to ask for some direction is for some reliable Links to go to for info, faqs, docs, you name it, that will get me upto speed on linux, how-to-fix linux problems, how-to-prevent linux problems, etc.
 
Should be able to post resolved the next time I get online.
 
Thanks,
IamSamAmI

---

