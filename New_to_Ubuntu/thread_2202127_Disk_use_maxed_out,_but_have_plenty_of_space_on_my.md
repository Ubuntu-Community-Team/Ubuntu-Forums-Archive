---
title: "Disk use maxed out, but have plenty of space on my harddrive"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by jsylvestermcd on 2014-01-27
I am trying to install version 12.10 of Ubuntu. I currently am using 12.04 and have an Intel® Atom™ CPU N450 @ 1.66GHz × 2 Processor with 2.0 GIB of memory. When I go to update, I am receieving an error message that says:

"The upgrade has aborted. The upgrade needs a total of ** M free   space on disk '/boot'. Please free at least an additional ** M of   disk space on '/boot'. Empty your trash and remove temporary packages   of former installations using 'sudo apt-get clean'."

I don't remember the exact numbers, but I have well beyond the amount needed on my harddrive. I have run 'sudo apt-get clean' after restarting on the terminal with no change. I ran disk use analyzer as well and it appears my folder is at 100% usage. I don't know how to free up the space needed, or why this is coming up. Please help. Thanks.

---

### Post by joey8 on 2014-01-27
Sounds like an old kernel problem and this has been discussed before try this thread for starters [http://askubuntu.com/questions/298487/not-enough-free-disk-space](http://askubuntu.com/questions/298487/not-enough-free-disk-space) and inlcude more information in your post next time. Like the contents of /boot.

---

### Post by jones quest on 2014-01-27
List the hard drive usage with:
df -h
If you have a separate /boot partition that is filled up with old kernel versions from previous updates then that should show up here.

List the installed kernels:
dpkg -l "linux-image*" | grep "^i"

Remove the ones you don't need:
sudo apt-get purge linux-headers-[old version here]

HOX! Do not remove the kernel your using now:
uname -r

---

### Post by Impavidus on 2014-01-27
Your /boot partition is full. You may have to uninstall some old kernels using your package manager.

Are you installing or upgrading to 12.10? Anyway, it will reach end of life in 3 months and its successor reaches end of life now. In most cases (although not necessarily all cases) it will be better to stay with 12.04 until 14.04 is released.

---

### Post by ibjsb4 on 2014-01-27
First off :)

Do you really want to upgrade to 12.10?  If you do, then you will have to upgrade to 13.04, then 13.10, Then in April to 14.04.

Your running a Lts version (12.04), the next Lts is 14.04.  In April you can upgrade direct from 12.04 to 14.04, skipping the other versions.

About /boot ..

Regardless of which way you go, you need to clean it out.  On this subject everyone has there pet way.

I use Synaptic Package Manager and manually do this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic&sa=Search&cof=FORID:9)

Others like the command line.  In this link (step#6) the whole process is done with one line.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

And welcome to the forums, the both of you :)

---

### Post by Bashing-om on 2014-01-27
@ jones quest;

Succinct - to the point. Great post.
The "dpkg -l 'linux-image*" | grep "^i' requires a closing quote mark. Please edit your post to make it so.


We are all
[INDENT][INDENT][INDENT]in this together
[/INDENT][/INDENT][/INDENT]

---

### Post by jsylvestermcd on 2014-01-28
Ok, so I removed old kernals that I did not need. My current kernel is 3.2.0-56-generic, which obviously I kept on when going through using 'sudo apt-clean purge linuximagex.x.x-generic' It did free up space, but not enough to update. 

When  give the command to view current kerel's I am shown this:

ii  linux-image-3.2.0-58-generic           3.2.0-58.88                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.58.69                             Generic Linux kernel image


As far as upgrading, I didn't realize 14.0 was on it's way and that I can just upgrade directly to that, which I will do for sure to save time. Still, I don't know why my hard drive is being bogged down with that much space, especially after cleaning out the old kernels. Now when I type in df -h I get this:

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       5.2G  3.9G  1.1G  79% /
udev            995M  4.0K  995M   1% /dev
tmpfs           401M  860K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M   80K 1002M   1% /run/shm

Under /dev/sda5 the usage has gone done about 10% but I still need to free some space. Have not run the command provided on the google search on the link above that is: 

dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut  -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo  apt-get -y purge

Wanted to get some advice before running this. Thanks for your help and look forward to hearing from everybody.

---

### Post by deadflowr on 2014-01-28
> **jsylvestermcd said:**
> 
Under /dev/sda5 the usage has gone done about 10% but I still need to free some space. Have not run the command provided on the google search on the link above that is: 

dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut  -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo  apt-get -y purge

Wanted to get some advice before running this. Thanks for your help and look forward to hearing from everybody.

Read a breakdown of the command here
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

The first part should give you info on how to see what kernels are installed.
The benefit of that would be, if you only have a couple, then running the full command might not be a necessity.

---

### Post by Bashing-om on 2014-01-28
jsylvestermcd; Hey;

Another thing to look at is the "inode" usage:
```

df -i

```
If the is no "reference" number available, not a thing the system can do with a file.

In the event that you have used up all the "inodes" all you can do to alleviate the situation is delete LOTS of files.
If this is true, there are means to address that issue, but it is painful and lengthy and we will not go there yet.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2014-01-28
DON'T DO UPGRADE. If you want to update to a new release just backup your data and do a fresh install. Much faster and a lot less problematic down the road (many problems reported on this forum can be attributed to "upgrade") 

Your problem is a non problem if you were to just wipe the whole thing and start fresh. Also as other said, don't bother with 12.10. If you want a new release go for 13.10.

---

### Post by Impavidus on 2014-01-28
> **jsylvestermcd said:**
> (...)
"The upgrade has aborted. The upgrade needs a total of ** M free   space on disk '**/boot**'. Please free at least an additional ** M of   disk space on '/boot'. Empty your trash and remove temporary packages   of former installations using 'sudo apt-get clean'."
(...)

> **jsylvestermcd said:**
> (...)
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       5.2G  3.9G  1.1G  79% /
udev            995M  4.0K  995M   1% /dev
tmpfs           401M  860K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M   80K 1002M   1% /run/shm
(...)
Suddenly I don't see your /boot partition any more. I don't see a /home partition either (which may not exist, so that's OK) and I have to add that 5.2GB for a root partition is really tiny, especially if you don't have a /home partition. Is this the whole output from df -h? If you want to move to a newer release of Ubuntu, best repartition your drive a bit.

---

