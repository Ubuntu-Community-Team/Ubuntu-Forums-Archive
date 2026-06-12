---
title: "64bit vs32bit install"
date: 2012-07-18
forum: Recurring Discussions
---

### Post by pgmer6809 on 2012-07-18
Bought a new computer with intel i3-2120 chip. 
Want to install Ubuntu 12.04.
Is there any reason to install 64bit version rather than 32bit version?
Are there 64 bit apps that will run? (FFox, Libre office,Wine etc.)
Thanks,
pgmer6809

---

### Post by efflandt on 2012-07-18
If you have more than 3 GB then it would be best to install 64-bit, because 32-bit cannot address more than around 3 GB (unless you use a special pae kernel).  If you install 64-bit all the usual applications are 64-bit, except maybe 32-bit flash with a 64-bit wrapper.  Real 64-bit flash is available, although, Adobe is not going to come out with any new flash versions for Linux other than security updates for current version.

64-bit Linux is not something new.  I used 64-bit SuSE back when I first got an early Athlon64 3200+ (2 GHz) in 2004.  Although, at that time they automatically included libs for both 32 and 64-bit.

So unless you use special 3rd party apps that are not available in 64-bit from Ubuntu or other Debian packages, you probably would not miss 32-bit.

---

### Post by oldfred on 2012-07-18
Moved to recurring discussions as it is asked every day.

Most of us with 64bit hardware (my system is 6 years old) run 64 bit. I only upgraded 3 years ago from 32 bit as back then there were some issues. I have not had any.

Some have reported issues with Skype and Oracle databases as  they are more 32bit. Wine runs as 32bit in your 64 bit system. I use the Windows version of Picasa in .wine without any issues. Some configuration required.

If you have less than 3GB of RAM then 32 bit may still be better. I am running the 64bit in 1.5GB of RAM on my laptop just for compatibility with my Desktop, but that is sub-optimal. Laptop occasionally has to use swap and gets slow if I try to load too much at once.

Note from 2008
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Many of the old arguments on 64 vs. 32 recommended
[https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)
Why Ubuntu officially suggests 32bit (25% have 32bit systems)
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html)

Benchmarks for 2009 show 64 bit better:
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by pgmer6809 on 2012-07-18
Thanks all for the update.
BTW My system has 6GB.
pgmer6809

---

