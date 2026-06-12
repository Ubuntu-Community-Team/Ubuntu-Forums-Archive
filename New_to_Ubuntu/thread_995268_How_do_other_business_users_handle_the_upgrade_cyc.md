---
title: "How do other business users handle the upgrade cycles?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by TreverT on 2008-11-27
I am (relatively) new to Ubuntu - I've been using it for just over a year, and am pretty happy with 7.1.  It's solid and it does what I need.  However, I am quickly running headlong into an annoying problem - new versions of various software packages do not offer rpms for 7.1 anymore, because it is "old".  

For a good recent example, there is Gimp 2.6, which I would love to have due to the interface improvements, but can't install!  The only version in the repositories is 2.4 for Gutsy, and they tell me this will never change.  Gimp's site only lists rpms for the latest Ubuntu, plus a tar.gz source code ball which utterly refuses to compile due to a mountain of dependency issues (I wasted a good two hours of working time fiddling with it and trying to track down the packages it wanted, but eventually had to give it up and actually go back to trying to make income).  

More and more, I am running into this - rpms that are only for Ibex and leave out everything prior.  My wife's XP laptop installation is seven years old and yet we were able to DL and install Gimp 2.6 on it with no trouble, and Windows doesn't expect users to re-install the entire OS every six months.  I got the upgrade notice for Hardy ages ago but have just been too busy to deal with it, and now we're one more version into the future again.  I just don't have the working time to reinstall the entire OS and then waste a week or two chasing down all the new problems, things that break, etc.  How on earth do other business users cope with this pace of upgrading?

---

### Post by bobnutfield on 2008-11-27
You should probably consider installing an LTS version (8.04 Hardy), which gets supported for three years on the desktop and five years on servers.  It actually is not that difficult to maintain a current version by keeping data and home partitions separate to the /root partition.  That way, reinstalls of a new version leave you data intact.

By the way, rpms are for Red Hat and Fedora systems.  Ubuntu is Debian based and uses .deb files.

---

### Post by sydbat on 2008-11-27
From the GIMP website> Ubuntu or Debian users can simply run apt-get install gimp to get the latest stable release of GIMP.

---

### Post by TreverT on 2008-11-27
> **sydbat said:**
> From the GIMP website

Yes, but that only produces Gimp 2.4, not 2.6.  I've been told that 2.6 will never be in the Gusty repositories.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
**gimp is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by TreverT on 2008-11-27
> **bobnutfield said:**
> You should probably consider installing an LTS version (8.04 Hardy), which gets supported for three years on the desktop and five years on servers.  It actually is not that difficult to maintain a current version by keeping data and home partitions separate to the /root partition.  That way, reinstalls of a new version leave you data intact.

By the way, rpms are for Red Hat and Fedora systems.  Ubuntu is Debian based and uses .deb files.

Ack, my bad.  I knew that, but my brain isn't firing fully tonight.

Regarding the LTS, I was VERY wary of 8.04 because I kept hearing complaints about problems with the NTFS read/write drivers (We have several shared drives with XP, all NTFS) and all the people who loathed PulseAudio.  I never really understood what LTS was all about, though - so when you say "support", you mean that *everything* that comes out will include an 8.04-compatible version for the next three years?  I'd always just assumed that LTS versions meant that Ubuntu people wouldn't chew your head off if you asked tech questions on it two years later.  

My /home directory is on the same partition as everything else.  I assume this means it will get wiped with any reinstall?  And do I correctly understand that if I could move it to a separate disk partition, I could reinstall the OS without losing all my personal settings (like Firefox bookmarks, desktop backgrounds, etc etc etc)?

---

### Post by bobnutfield on 2008-11-27
> **TreverT said:**
> Ack, my bad.  I knew that, but my brain isn't firing fully tonight.

Regarding the LTS, I was VERY wary of 8.04 because I kept hearing complaints about problems with the NTFS read/write drivers (We have several shared drives with XP, all NTFS) and all the people who loathed PulseAudio.  I never really understood what LTS was all about, though - so when you say "support", you mean that *everything* that comes out will include an 8.04-compatible version for the next three years?  I'd always just assumed that LTS versions meant that Ubuntu people wouldn't chew your head off if you asked tech questions on it two years later.  

My /home directory is on the same partition as everything else.  I assume this means it will get wiped with any reinstall?  And do I correctly understand that if I could move it to a separate disk partition, I could reinstall the OS without losing all my personal settings (like Firefox bookmarks, desktop backgrounds, etc etc etc)?

Yes, it means that software updates for 8.04, including all security fixes, will continue for the full term of the LTS version.  This means all the software that comes stock from the official repos (that would include the Gimp.)  It would not apply to third party software offically, but they are supported with third party repo enabling (Medibuntu, etc.)

And yes, you do understand correctly.  If your home partition is on a separate partition, all of your config settings are kept intact on a new install.  You simply have to direct the installer to leave the /home partition alone during installation.  I have been doing this for a long time, and each release is simply a matter of installing the new version and assigning my home partition to the existing one, and directing the installer to not format it.

I can't comment on Pulse Audio, other than to say you can simply uninstall it if you don't like it and use the stock installed Alsa.

---

### Post by ugm6hr on 2008-11-27
> **TreverT said:**
> My /home directory is on the same partition as everything else.  I assume this means it will get wiped with any reinstall?  And do I correctly understand that if I could move it to a separate disk partition, I could reinstall the OS without losing all my personal settings (like Firefox bookmarks, desktop backgrounds, etc etc etc)?

Yes (all above statements are correct).

I would also suggest Hardy 8.04LTS.

Some of the more important applications tend to be "backported" - and I would anticipate that should continue for LTS until the subsequent LTS release.  Unfortunately, GIMP 2.6 hasn't yet made it to the backports list.

However, if you are a business user, the official "supported" versions may well be safer.

---

### Post by Locutus_of_Borg on 2008-11-27
you could always use a distro that employs a rolling release schedule rather than a cyclical one as long as you are comfortable moving away from ubantu

---

### Post by bodhi.zazen on 2008-11-27
I suggest you go with a stable version of Linux, Ubuntu 8.04 or say Centos (test with a live CD or if needed a testing box).

After everything is set up, do security only updates.

---

### Post by w4ett on 2008-11-27
Ditto on the preference for the 8.04 LTS release in the workplace.  I support several business customers and have steered them to use the LTS releases ONLY....the support cycle is longer and the releases tend to be a little more on the stable side.  I also recommend the use of a seperate home partition....it just makes life a heck of a lot easier.

---

### Post by theozzlives on 2008-11-27
I rather enjoy upgrading every 6 mos., and I follow the Alphas also. There is an improvement with each release, and I earn a living. Update Manager gave you the option to upgrade to 8.04, but you can still get it. Make sure /home is a different partition.

---

### Post by Paqman on 2008-11-27
> **TreverT said:**
> so when you say "support", you mean that *everything* that comes out will include an 8.04-compatible version for the next three years?

No, "support" means that the repos will remain open for that long. Availability of 8.04 compatible .deb of anything outside the repos is beyond Ubuntu's control. You may get one, you may not.

The main repos are pretty much set in stone. You'll have the same version of major software (like GIMP) for the whole cycle. Security updates will be continuous throughout this period, however. Your system will be maintained and stable, but won't be upgraded until the next LTS release.

The "backports" repo people mentioned is a way of getting around this. If you enable backports, you will get *some* updated versions of core software, but only if it introduces major new features or significant bugfixes.

---

### Post by Sidewinder1 on 2008-11-28
I have had this same question for sometime; thank you TreverT for asking it. As a follow up question to the separate /home partition issue; could I not have my /home directory (currently in the same partition as everything else /root, etc) backed up on an external hard drive; then update to Hardy through Synaptic and then copy all of the files and directories from /home on the external back to the internal? Are there any concerns, issues with this method? BTW after installing Gutsy (my first Linux exposure) almost exactly 1 year ago, I love it and haven't looked back! Thank you all in advanve and for all of the past help.

Side

---

### Post by bodhi.zazen on 2008-11-28
IMO, for a Business, I would advocate a separate /home and a separate /data partition.

Of course backups go without saying.

Part of the reason is to keep the OS seprate from user and data parititions, but you can also secure these partitions (set noexec , nosuid , and nodev in fstab) as well as set quotas on them if you wish.

See Section 3.2

[http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html)

[http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ap-checklist.en.html](http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ap-checklist.en.html)

---

