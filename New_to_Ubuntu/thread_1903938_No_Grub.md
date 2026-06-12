---
title: "No Grub"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by morhin on 2012-01-03
10.04 on an Acer Aspire 5250
I was having some trouble with Pulse Audio so I took out everything that had it. Stuff quit working so I put in the live cd and wrote down everything that was originally installed with plans to re-install what was there.
Now I can't get back in. The Ubuntu lead page comes up then disappears and I'm left with a sign in for my laptop. A window comes up. 
After several tries I typed in grub and was informed that no grub was installed. I tried to install and get the following:

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main grub 
0.97-29ubuntu60.10.04.2
Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu60.10.04.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu60.10.04.2_i386.deb)
Could not resolve 'us.acrhive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I ran apt-get udpate and then sudo apt-get install grub and it does the same thing.

I'm new to this so I don't have a clue what went wrong but unless someone can guide me through this all I know to do is put the live cd back in and start all over.

---

### Post by oldos2er on 2012-01-03
Moved to Absolute Beginner Talk

---

### Post by oldfred on 2012-01-03
Was one of the default packages you ended up removing python?

If python is uninstalled it causes major breakage. Newer versions of Ubuntu can get to command line and onto Internet, but older versions did not work at all.

You may be able to chroot into your system and in effect rebuild it.

Several examples of chroot. Not sure if you need the reinstall of grub or not.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

After you chroot into your system and make sure you have Internet:
Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop 
apt-get install ubuntu-desktop python 
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

---

### Post by morhin on 2012-01-04
I type in
$ python 

I get
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56)
[GCC 4.4.3] on linux2

Seems like python is still there.

I'm a casual user and the rest of what you suggest is like..... way over my head.

My wife knows dos so we got to some of my files and I've retyped them onto a different computer. I'll move them back onto my computer after I've re-installed Ubuntu from the live cd. 

Thanks for you help. 

Thought his isn't a resolution I guess we'll call it closed.

I'll try to do that now.

---

### Post by morhin on 2012-01-04
I'm trying to find out how to close this thread and it's gotta be really easy..... if you know how.

If you know how, could you explain it to me..... real slow.

thx

morhin

---

### Post by westie457 on 2012-01-04
> **morhin said:**
> I'm trying to find out how to close this thread and it's gotta be really easy..... if you know how.

If you know how, could you explain it to me..... real slow.

thx

morhin

Thread Tools at the top of your original post will have the option to 'Mark as Solved'.

---

### Post by audiomick on 2012-01-04
> **morhin said:**
> ...
My wife knows dos so we got to some of my files and I've retyped them onto a different computer. ...

You know you should be able to copy your files to an external drive, if you have one, from the Live environment, i.e. booted into the live CD? 

If you haven't already re-installed, you might want to consider doing the new install with a separate /home partition. Look here

[]("http://www.google.com/url?q=https://help.ubuntu.com/community/HowtoPartition&sa=U&ei=1IMET6S9Couh-QaJ_tDRAQ&ved=0CAQQFjAA&client=internal-uds-cse&usg=AFQjCNEa3bqxb5DoxI06coOutXG8fJg7pQ")[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

The advantage is, in your current situation you could simply re-instal the OS and retain the existing /home. If all goes well, you are back where you started before the system broke, and your files are all still there.

If that is all too complicated, don't sweat about it, but it really isn't hard. I find it easier to remember where I am up to if I set up the partitions with gparted on the live CD, then point the installer at the partitions I have created.

My computer currently has four drives, about 10 partitions, I think, and two installs on it. (no windows!) ;)

---

### Post by oldfred on 2012-01-04
Also if you have not installed, have you tried rescue mode? Can you login to a command line.

You also do not want to install grub as all the new versions use grub2. If you install grub it confuses things and the package name for grub2 is grub-pc not grub2.

---

