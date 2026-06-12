---
title: "Ubuntu is broken... any recommendations?"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by mikeebean on 2012-11-23
After testing Ubuntu 12.04 and Gnome 3 shell for two weeks on a USB key, I've been very pleased with both and decided to install Ubuntu on my Vista hard drive. I used PerfectDisk to defrag, prep, and edit my partitions. After a few initial problems, Vista was working fine in this new configuration for several days.

I've had a few major issues since installing Ubuntu. Just an FYI, I set up three accounts: an untouched Unity, a tweaked Unity, and a Gnome 3 Shell.

After installing Ubuntu, Vista would fail to boot from GRUB, and would only  boot from the "last known good configuration" option in the Windows recovery menu. I decided this wasn't an acceptable trade-off and repaired the MBR.

I then installed EasyBCD, which boots properly into Vista, but suddenly my main Ubuntu account with Gnome 3 shell would not open, throwing a "failed to load session gnome" error. My other accounts still work, but the screen is now stretched, and my monitor's resolution isn't shown in the Display settings. I tried repair procedures from the terminal but then lost access to that account entirely. I know I should have backed up my files and now I can't figure out how to access them.

At this point I just feel exhausted and I don't know what to do next. I want to recover my files if possible. I want to keep access to Vista for certain applications. I want to repair or reinstall Gnome 3 shell. I hate the idea of reinstalling and losing two nights of tweaking and updating.

**Here are some questions and thoughts I have in the aftermath of installation:**
- Should I just forget about dual booting and install Ubuntu on an external HD? Is there a significant performance drop using this method? I don't want to run from a USB stick; it's too slow.

- I read on someone's blog that they keep their Vista and Ubuntu files together in a separate partition, protecting them from system corruption and easily sharing them between the OSes. I think I might do this if I can get Ubuntu working again.

- I really like the stability and support of Ubuntu, as well as the Software Center and Update Manager, but Gnome3 seems somewhat crippled and many add-ons/features don't work properly. If I prefer Gnome 3 over Unity and will likely use it exclusively, should I stick with Ubuntu or go to another OS? 

Sorry for my rambling post, but it seems just when I've got it all figured out, the rules keep changing, and I'm losing my resolve. Thanks for any advice.

---

### Post by carl4926 on 2012-11-23
There should be absolutely no issue booting Vista and Linux together.
I only really use Gparted for partitioning, I never heard of the tool you used.

I understand there are some remix gnome images
[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#Download](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#Download)

Fedora and openSUSE do great Gnome 3 releases.

Personally, I'd not use EasyBCD. All I read is not good.

Recover Vista with the Vista DVD and re-install
Just make sure you set grub as sda here:
[https://docs.google.com/open?id=0B3e0lLG3OdqEXzhmUkZlWDFUak0](https://docs.google.com/open?id=0B3e0lLG3OdqEXzhmUkZlWDFUak0)

---

### Post by Steveo031986 on 2012-11-23
First, if you can't access your data a external hd dock or case will allow you to access your files. That being said, its always a good idea to have separate partitions if your going to dual boot operating systems especially will the ext file system so windows wont be able to access it natively.

I think your problem is that you didn't disable windows boot before you installed grub. Windows doesn't play well when you install another os after it, because it will try to access its booting sequence. If you still have the windows cd you can boot from that and click on repair and go from there.

---

### Post by mikeebean on 2012-11-26
Thanks for the advices. It seems I just needed to step away and rethink my strategy.

 I was able to access the main home folder and retrieve my files using my secondary accounts. (I just didn't know where to look at first.)

I checked the error log to see if I could try to recover my system, but instead I reinstalled and I use only Unity, I'll wait for a better Ubuntu Gnome3 experience. As soon as I had myself a setup I was happy with, I used Clonezilla to back up the partition. All personal files are saved in a separate partition.

I still prefer Gnome3, so I also created another partition and installed Fedora 17. (Triple-booting! To quote Tom Hulse in Amadeus; "They're both so beautiful, I                           can't decide. Why don't I have two                           heads?")  It's really surprisingly comparable, aside from the interface of course.

---

### Post by carl4926 on 2012-11-27
Fedora is a first class OS

---

### Post by Jonathan Precise on 2013-08-26
If your problem is solved, then go to thread tools and mark it as solved.

---

### Post by mikeebean on 2014-03-16
Jonathan- 

Sorry I never revisited this, it was never really 'solved' and I forgot about it. I ended up temporarily installing Fedora as a dual-boot and used it for maybe a year. Ultimately I came back to dual-booting Ubuntu 12.04 Unity because Fedora kept having big issues on every update, something related to my laptop's hardware. I also replaced Vista with Windows 7 and reinstalled EasyBCD which fixed my dual-booting issues.

This was all before Gnome 3 was an official supported flavor of Ubuntu. I may try Ubuntu GNOME when Ubuntu 14.04 comes out next month! 

-Michael

---

