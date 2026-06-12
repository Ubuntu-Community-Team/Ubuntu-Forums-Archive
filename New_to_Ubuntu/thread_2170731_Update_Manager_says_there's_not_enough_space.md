---
title: "Update Manager says there's not enough space"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by craigpwagner on 2013-08-27
Hi,

I installed the LTS Ubuntu 12.04 quite a while ago following recommendations for partition size and things like that.  Now I can't update anything because the Update Manager says I do not have enough space on the '/' drive.  I have used the terminal to run "sudo apt-get clean" and "sudo apt-get autoclean" but there still isn't enough space - the available space doesn't seem to increase after using those.  The recycle bin is empty.

GParted shows my partitions as:

1) "/" 9.31 GB with 631MB free
2) Linux Swap 3.73GB
3) "/home" 450 GB with 380GB free

How can I sort this out without losing any data or other programs installed on "/" or "/home"?

Many thanks for your help.

Cheers

Craig

---

### Post by TheFu on 2013-08-27
Please post the output for **df -i** and **df -k** - thanks. Please use the "code" tag when posting so the columns line up when we read it. See the "Adv Reply" options for that.

Looks like you'll want to use **gparted** to do some partition re-arranging and resizing.  Be certain that you absolutely backup anything you cannot afford to lose.  With all that free space under /home - this will be relatively easy.

Are you a developer?   Java, python, perl, ruby?  Languages tend to make lots and lots of tiny files which eat up i-nodes.

---

### Post by craigpwagner on 2013-08-27
df -i:

```
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sdb1        610800 472898   137902   78% /
udev             501015    592   500423    1% /dev
tmpfs            503218    508   502710    1% /run
none             503218      3   503215    1% /run/lock
none             503218     11   503207    1% /run/shm
/dev/sdb3      29671424  38837 29632587    1% /home
```

df -k

```
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdb1        9611492  8964344    158908  99% /
udev             2004060        4   2004056   1% /dev
tmpfs             805152      960    804192   1% /run
none                5120        0      5120   0% /run/lock
none             2012872      152   2012720   1% /run/shm
/dev/sdb3      467264096 64176728 379351716  15% /home
```

I'm not a programmer so Java etc not an issue.

Is there any way to see what files/programs have been installed on "/"?

Thanks for looking at all this.

---

### Post by Pako Pako on 2013-08-27
A stock Ubuntu install comes with a Disk Usage Analyzer (Home -> Accessories) if you want to see how much space goes to each directory and sub-directory.
There's also Software Center, then click on the Installed tab and go through each sub-category to see the programs you have installed.

---

### Post by Dennis N on 2013-08-27
Since you say you have been using 12.04 quite a while, you may have lots of old kernels in there. There have been many since the original release, and unless you remove them, they are still there. They take up considerable space. Clean and autoclean won't do it.

---

### Post by TheFu on 2013-08-27
> **Dennis N said:**
> Since you say you have been using 12.04 quite a while, you may have lots of old kernels in there. There have been many since the original release, and unless you remove them, they are still there. They take up considerable space. Clean and autoclean won't do it.

10G is fine if you keep the OS "clean" - don't install lots of GUI apps, clean up old programs, files, kernels, etc.

You asked if there is a way to see all the programs installed under /?  Well, if you use a package manager **every** program gets installed there.  All-of-them.  That is the point of having /usr and /bin and /sbin .... to load programs.

You can get a list of installed packages using **dpkg -l** or running synaptic (if you prefer a GUI).
You can see the amount of storage used by using **du -sh /usr /sbin /bin** - but that won't really help you decide which packages you can remove.

I can't see your original message now, but I thought you had a huge /home partition. If you like, you can shave off 10G from that, create a new partition ... let's call it /usr - temporarily mount it under /mnt/ while running a boot-live CD and move everything from /usr over to the /mnt/ storage, then modify /etc/fstab with the new partition and reboot.  Bam, you've just doubled the available storage for /usr, freed up all the old stuff previously stored under /usr on / and none of the programs will notice anything different.  I've done this many, many, many times myself.  BTW, on my desktop, 3.3G of storage is under /usr, so you can probably free about that much yourself.

Clear as mud?

It would probably be easier to just make 10G more storage available immediately next to the partition holding / then resize that partition into the newly available 10G space with gparted (running off a live-CD).

---

### Post by Dennis N on 2013-08-27
> **TheFu said:**
> 10G is fine 
.

He will have to check and see what his situation is. I have removed 4.5gB of old kernels and headers in 12.04 so that is not insignificant.

---

### Post by TheFu on 2013-08-27
> **Dennis N said:**
> He will have to check and see what his situation is. I have removed 4.5gB of old kernels and headers in 12.04 so that is not insignificant.

I [created a script that will generate the command to remove old kernels.]("http://blog.jdpfu.com/files/kernel-cleanup.sh")

There are much easier ways ... you can use the shotgun approach 
```
sudo apt-get purge linux-image*
```
and trust the system NOT to remove the currently running kernel. Then just cleanup any no-longer-need-dependencies:
```
sudo apt-get autoclean
```

I like to keep a few recent kernels on each box and I don't want to have a tool make a bad decision by accident, hence why the script doesn't just remove kernels itself.

Old kernels weren't an issue until the last few years. Guess they took something out? I think it will be added back again in 13.10 - that will be helpful to prevent all the people with limited storage from getting into APT-hell over too many old kernels.

---

### Post by monkeybrain20122 on 2013-08-27
In Fedora there is a way to configure how many kernels to keep automatically(say 2). Is there anything similar for Fedora/Debian?

---

### Post by craigpwagner on 2013-08-28
I just ran:

```
sudo apt-get purge linux-image*
```

And it says it removed 1.9GB of stuff.  GParted shows the drive at over 2GB free - still not loads but enough to download these updates at least!!

I'll be interested to see if 13.10 fixes this issue.  But that won't be LTS will it?  Hmmm....

Thanks for your help everyone.

---

### Post by craigpwagner on 2013-08-29
Well this morning I turned the computer on and it does not recognise my Linux installation.  I dual boot with Win 8.  I've used a live USB and redone Grub but that hasn't fixed the issue.

So I used:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge linux-image*[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

And can no longer boot into Ubuntu...

I'm wondering if a clean install giving myself a repartitioned larger "/" drive might be the way to go here rather than fixing this install and running the risk of the "/" drive filling up again in a few months.  Or is there another way to install a fresh Ubuntu without having the problem of the "/" filling up?  I thought it was supposed to put download files and install stuff on the "/home" drive?

I have a large external hard drive so can back up my files etc quite easily.[/FONT][/COLOR]

---

### Post by TheFu on 2013-08-29
Check my signature for links; try **boot repair**, but on a completely full HDD, you might not be able to boot. Having full partitions is bad under any UNIX system and really, really, really bad if the full partition contains /var or /boot or /tmp or ... you get the idea.

/home is NOT used for system updates, applications or patches. It is for user-data, not the OS.  On your system, if you install lots of GUI stuff, then you need more than 10G for / .  15G should be safe and 20G should hold anyone's system, apps and patches (for most values of "anyone").

You were really smart to split /home from / . In post #6, I explained what you could do to solve the issue. Should be fairly easy.

With the amount of storage that you have, for your next install ... please consider allocating 20G for /. Know that for smaller file systems, the default inode-to-storage-ratio is usually poor. At 20G and larger, it becomes crazy in other direction (way too many). i-nodes take hardly any storage, so don't worry about that aspect.

I've run my main Ubuntu desktop on a 14G partition - including /home - for 5 yrs - with complete ruby and perl development environments in this space and still have 2.9G free.  Media is located on the network, not this machine.  Email is left on the email server too.

If you install java stuff, you need more storage, since it will pull in all sorts of crap, different java releases, and you'll probably discover that you need the Oracle JVM too, since not all JREs work the same.  If I were a java or Android dev, I'd want 25G for / just for the dev tools. I've installed the Android SDK + dev environment - alone, it used 16G of storage.

---

### Post by craigpwagner on 2013-08-29
Boot repair worked a charm.  Thanks for your help.

The stuff from post 6 is a little confusing to me!  I think I'll stick as I am for now and then next time I get full up I'll think of installing the latest release and repartition the / to 20GB as you suggest.

I don't think I've installed much GUI stuff.  I have WINE and Kindle.  Also a few Steam (linux) games.  I've no idea where those have installed!

---

### Post by Dennis N on 2013-08-29
Just some information related to this:

Some 12.04 installations include two kernels. It happened to my system, so it almost certainly happened to others. If not corrected, this results in five packages every kernel upgrade:

linux-headers
linux-headers-generic
linux-headers-generic-pae
linux-image
linux-image-generic-pae

total space = 305mB

There have been about 21 kernel upgrades in 12.04 since first released. You can do the math and see how this would add up on the unsuspecting user who never cleaned these out. Especially, those without a separate home partiton may never notice.

---

### Post by TheFu on 2013-08-29
I have the linux-headers-generic-something metapackage installed to make virtualbox guest addition dependencies handled easier. Lots of instructions say to install the headers using a `uname -r` - which breaks the guest addition install after every kernel release. Boo.

I though the pae and non-pae packages were selectively installed based on the OS needs?

---

### Post by Dennis N on 2013-08-29
> **craigpwagner said:**
> I think I'll stick as I am for now and then next time I get full up I'll think of installing the latest release and repartition the / to 20GB as you suggest.


There are also graphical tools to take care of unwanted kernels and the related headers.

In fact, the Synaptic Package Manager can be used for this. See this tutorial:

[http://liam-on-linux.livejournal.com/20347.html](http://liam-on-linux.livejournal.com/20347.html)

Each time a new kernel and headers come up for installation, you would then remove the oldest kernel and headers you have installed. That way, you keep the space needed fairly constant and well within your 10gb. No need for drastic changes.

---

### Post by Pako Pako on 2013-08-30
> **craigpwagner said:**
> I don't think I've installed much GUI stuff.  I have WINE and Kindle.  Also a few Steam (linux) games.  I've no idea where those have installed!
They install in various places. (/bin) (/etc) ... and of course saved information would be in $home
It might be the games taking up 3 GB apiece? (If you installed them from the repositories, you can open up Software Center and see "installed" to get a rough estimate how much space they're taking up.)

What did Disk Usage Analyzer tell you?

---

### Post by craigpwagner on 2013-08-30
I've removed 13 kernels and freed up about a gigabyte.  Nice result.

Thanks everyone.

---

