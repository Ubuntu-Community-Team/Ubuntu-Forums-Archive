---
title: "Grub not showing latest kernel updates"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by DandyDon on 2012-11-17
Hi all, running 1204.1 LTS, w/ dual boot of Windows XP. Machine is AMD64, 1.6Ghz, with 2gigs RAM. Ubuntu is on seperate partition, with its own swapfile. System runs great, but Grub boot choices stop at 3.2.0-29-generic. 

I think the current version is 3.2.0-33, updated 11/16/12. Why doesn't this show in the boot menu as default?. :confused:

---

### Post by Paqman on 2012-11-17
Hmm. You can prod Grub to update itself with the command:
```
sudo update-grub
```
Part of the output of that will show what kernels it detects.

---

### Post by DandyDon on 2012-11-17
> **Paqman said:**
> Hmm. You can prod Grub to update itself with the command:
```
sudo update-grub
```
Part of the output of that will show what kernels it detects.
Thanks for the suggestion Paqman. I opened Terminal and ran the script, Grub list was updated to 33. I restarted, it's still only showing 29 on the boot screen. Any other ideas?.

---

### Post by Paqman on 2012-11-17
How complicated is your partitioning setup? Is it possible that the copy of Grub that's installed is set up to get it's config files from a different copy of Linux you've got on there?

You could try running [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), which you can use to reinstall Grub.

---

### Post by Vaphell on 2012-11-17
how many kernels do you have installed? try removing old ones.

---

### Post by DandyDon on 2012-12-02
Hi all, updated from 12.04 to 12.10, which fixed Grub issue. Thanks to all who posted.

---

### Post by 95kreaninw95 on 2013-10-21
This question might be a bit old. But it's very very hard to fix, at least, by an average user like me. 

It's when Ubuntu showed me that the **/boot** is full. Later, I found that there are numerous users who effected by this problem for so many years(why it hasn't been fixed yet?). It's plainly stupid for Ubuntu to kill itself by its updates. The users left with an old Linux Kernel because their **/boot** is full thus they can't update to new Linux Kernel anymore. And that's about **performance** and **security** update!!!

That aside, I found a way to remove unused linux-image files and cleared my **/boot** up again. But I found out later that I'm using an outdated linux-image version(3.5.0-23) by *uname -r* command line even though I updated to 3.5.0-42 today. Basically, when I boot my laptop, Grub2 didn't see/list 3.5.0-42 kernel at all. So, I spent 3 hours searched a way to fix this problem but without any luck so far. The main problem was because all of the threads I found provide command line solution with some computer-alien words. So, I fail to understand most of the threads. Then I found one thread talking about an application which uses to fix boot related problem. It's **"Boot Repair" **[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) **. **By using it,my problem was fixed with just one click!!!

Now, the method I used to fix this problem.

1. Download Boot Repair with (in Terminal) *sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update* and then [I]sudo apt-get install -y boot-repair && (boot-repair &).

[/I]2. Open the app, click recommended repair, when it finished operation then reboot.

This app is very useful. It also give back my lost Ubuntu waiting screen during boot too. However, you might found that you Grub screen changed to something strange now. You can revert it back to normal by *sudo apt-get purge desktop-base* and then *sudo update-initramfs -u* and *sudo update-grub*. (Anwar Shah - [http://askubuntu.com/questions/160244/how-can-i-reset-my-grub-background-to-default](http://askubuntu.com/questions/160244/how-can-i-reset-my-grub-background-to-default) )

I hope this help >...<

---

