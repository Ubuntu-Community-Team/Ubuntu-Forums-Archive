---
title: "HowTo use DiskDrake for Partitioning"
date: 2006-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2006-01-07
You may partition with Partition Magic.
You may partition with GParted or QTParted.

Here's another alternative, and I recommend it for two reasons: 1. It's cost-free (unlike Partition Magic) and 2. I've never known it to fail.

For some strange reason, sometimes GParted and QTParted leave certain options greyed out, even if the partition isn't mounted.

DiskDrake has always worked flawlessly for me. If you want to use it, here's what you do:

1. Go to [the PCLinuxOS download page](http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/) and download PCLinuxOS

2. Burn the ISO as a disk image

3. Reboot your computer from the CD

4. Sign in as guest (password *guest*)

5. Click on **Install PCLinuxOS**

6. Type in the root password (*root*)

7. Select **Disk Partitioner (for advanced users)**

8. DiskDrake will pop up. Use it. Then select **Done**.

9. Instead of installing PCLinuxOS, select **cancel**.

10. Reboot and install Ubuntu.

---

### Post by -Rick- on 2006-03-12
Thanks for this tip :) This DiskDrake seems indeed like a very nice partition manager, atleast as good as PM. I didn't do step 10 though...I just installed it instead, very nice distro ;)

---

### Post by Maniak on 2006-03-13
Hang on a minute......isn't this an Ubuntu forum???

---

### Post by aysiu on 2006-03-13
[QUOTE=Maniak]Hang on a minute......isn't this an Ubuntu forum???[/QUOTE] Yes. And when people ask how they can resize partitions when GParted or QTParted has greyed out options that should not be greyed out, a third-party solution is sometimes a good one... in this case, DiskDrake.

---

### Post by barbarian on 2006-03-13
Hello,
looks very nice.. 
One question: can I safely resize(reduce) swap space?

---

### Post by shof2k on 2006-03-13
Nice tip...will diskdrake allow you to resize partitions after they've been created.  I have an annoying xp partition that I want to remove ;)

---

### Post by aysiu on 2006-03-13
[quote=barbarian]Hello,
looks very nice..
One question: can I safely resize(reduce) swap space?[/quote] As far as I know, yes.

[QUOTE=shof2k]Nice tip...will diskdrake allow you to resize partitions after they've been created.  I have an annoying xp partition that I want to remove ;)[/QUOTE] You can resize existing partitions, and you can delete unwanted partitions, yes.

---

### Post by az on 2006-03-13
The Dapper live cd is kisk-***.  The espresso installer has a similar partitioner and you can also run the standalone gparted with all the neccessary (ntfs) tools included.  If it is buggy for you at the moment, I'm sure it will be fixed before release.  A lot of talented people are working on it.

It is a smaller download, by about 50 megs, too...

...and it's ubuntu.

---

### Post by aysiu on 2006-03-13
Azz, the whole point of this tutorial is to propose an alternative just in case GParted doesn't work out for some people. I've seen numerous times people posting "greyed out" options that should not be greyed out in GParted and QTParted. I've experienced these problems myself, too.

I'm just proposing an alternative. If GParted and QTParted work out for people, I'm not going to stop them from using those tools.

---

### Post by az on 2006-03-13
Yes, but with Espresso being the installer that is planned on being shipped out by shipit, the issues that you describe with gparted will be addressed, if they haven't already been addresssed...

The partitionner on the breezy installer can do anything.  It just has a curses interface.  The gparted package that ships with the breezy live cd does not have all the suggested packages installed, nor does it unmount your swap.  It is not fully-functional out-of-the-box because it is not the prime-time partitioning tool that you need to install with.  Espresso is.

---

### Post by aysiu on 2006-03-13
When I see how reliable Espresso's partitioner is in a couple of months (isn't Dapper delayed?), then I may stop recommending DiskDrake (as it does require an entirely new ISO download). In the meantime, I continue to see issues with GParted and QTParted.

---

### Post by az on 2006-03-13
If espresso and the Dapper live cd fall on their ***, I'll send you a bottle of Canadian Club...

---

### Post by cls1chuck on 2006-03-28
I've seen multiple references to items being 'greyed out' in gparted; however I have a different issue when trying to shrink my (X) ntfs partition  using gparted (5.10 BB on the live CD downloaded earlier this month).  gparted goes through the motions of shrinking my XP part, but then when it 'comes back' (the progress dialog disappears), the partition info shows the same as before.  Has anyone heard of THIS problem?  Also, where can I access QTparted?  Is it part of 5.10?

---

### Post by aysiu on 2006-03-28
> **cls1chuck]I've seen multiple references to items being 'greyed out' in gparted said:**
>  Sure. Maybe you haven't installed *ntfsprogs*? [quote] Also, where can I access QTparted?  Is it part of 5.10?  It's in the Universe repositories. Have you [enabled extra repositories](http://www.psychocats.net/ubuntu/sources)?

---

### Post by cls1chuck on 2006-03-28
[I thought I replied but see no reply, so I'm 're'-replying]
Aysiu, Thanks for the quick response - I'll try it.  [COLOR=Red]**Can I install ntfsprogs if I boot from the Live CD**[/COLOR]?  Also, is there a place that I could have found that I need to install ntfsprogs without posting?  While I **REALLY appreciate** the help I've received here in the forums, if I could help myself by going to a reference, I'm sure it would free up yours (and others') valuable time for helping others or making other valuable contributions.  FYI, I already reviewed 'how to help yourself', and found your PDF guide (great job btw!).
Anyway, it seems like my challenge isn't that there are no help references out there; rather it's that there is SO MUCH help and reference out there - but not (from my point of view) very organized.  Not a complaint - just wanting to know if there is a place you could point a Linux newbie for a 'silver bullet' for this stuff.

---

### Post by aysiu on 2006-03-28
> **cls1chuck][I thought I replied but see no reply, so I'm 're'-replying]
Aysiu, Thanks for the quick response - I'll try it.  [COLOR=Red]**Can I install ntfsprogs if I boot from the Live CD**[/COLOR]?[/quote] Yes! Boot up the live CD. Go to Applications > Accessories > Terminal and type ```
sudo nano /etc/apt/sources.list
``` Remove the # sign from in front of the Universe repositories. Then type ```
sudo apt-get update
sudo apt-get install ntfsprogs qtparted
``` > Also, is there a place that I could have found that I need to install ntfsprogs without posting? Probably, but it wouldn't have been easy to find if you didn't know exactly what you were looking for.  > While I **REALLY appreciate** the help I've received here in the forums, if I could help myself by going to a reference, I'm sure it would free up yours (and others') valuable time for helping others or making other valuable contributions. One of the valuable contributions Ubuntu users can make is giving online forum help. I don't consider this a waste of my valuable time at all. > FYI, I already reviewed 'how to help yourself', and found your PDF guide (great job btw!). Thanks. When Dapper comes out in June, I'll update it. [quote]Anyway, it seems like my challenge isn't that there are no help references out there said:**
>  The problem is really that no one person is in charge of the Ubuntu documentation. There are various semi-centralized locations for documentation.

For example, the Wiki:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

And the Documentation Storage Facility:
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

I find the best "documentation" is Google and the Ubuntu Forums, though.

If I have a problem or question, the first thing I do is go to Google and type [quote]site:ubuntuforums.org *name of problem or question* **Note**: this will almost invariably give you better results than using the search box built into the forums.

---

### Post by cls1chuck on 2006-03-29
well, QTparted did the trick; not sure why gparted did not, but oh well.  It would be nice to know why the one worked and the other did not, but at least I now have space to put a Linux partion on my hard drive!
Thanks again for all the help!

---

### Post by plors on 2006-03-29
[QUOTE=cls1chuck]well, QTparted did the trick; not sure why gparted did not, but oh well.  It would be nice to know why the one worked and the other did not, but at least I now have space to put a Linux partion on my hard drive!
Thanks again for all the help![/QUOTE]

that's most likely because you used an obsolete gparted. The newer versions deal just fine with ntfs.

About the 'greyed out options' in gparted.. i am quite sure these options are only greyed out when there's a good reason for it. If someone feels otherwise, please file a bug so the developers can have a look at it.

---

### Post by cls1chuck on 2006-03-29
Plors - I did make sure I had the latest updates (using the update manager and the package manager); is this the proper way to make sure I have the most current version?  (FYI this is the one that comes on the Ubuntu Live CD).

---

### Post by plors on 2006-03-29
i'm not sure (i don't use Ubuntu myself) but i don't think it has the latest gparted. IMHO the best way to use gparted is to run it from it's own [livecd]("http://gparted.sourceforge.net/livecd.php"). That way there are no issues with mounted partition and/or active swap and you are always sure you have the latest software.

---

### Post by towsonu2003 on 2006-03-29
Wouldn't it be easier to install this (as a program) in Ubuntu and partition from there? It is GPl'd from Mandrake Linux so they should be giving a link to get it (although I couldn't find it).

---

### Post by aysiu on 2006-03-29
[QUOTE=towsonu2003]Wouldn't it be easier to install this (as a program) in Ubuntu and partition from there? It is GPl'd from Mandrake Linux so they should be giving a link to get it (although I couldn't find it).[/QUOTE] Here it is:

[http://rpmfind.net/linux/rpm2html/search.php?query=drakxtools](http://rpmfind.net/linux/rpm2html/search.php?query=drakxtools)

I think I tried to *alien* install drakxtools once, and it didn't work for some reason.

---

### Post by towsonu2003 on 2006-03-29
[QUOTE=aysiu]
I think I tried to *alien* install drakxtools once, and it didn't work for some reason.[/QUOTE]
Possibly due to dependencies? [http://rpmfind.net//linux/RPM/mandriva/devel/cooker/cooker/media/main/drakxtools-10.4.16-1mdk.i586.html](http://rpmfind.net//linux/RPM/mandriva/devel/cooker/cooker/media/main/drakxtools-10.4.16-1mdk.i586.html)

Too advanced for my level...

Could we request this for Dapper?

---

### Post by rayburn on 2006-04-17
Thanks for this howto, I've just used it on a pc that I have been struggling to partition correctly with other tools, and it worked a treat. I already had PClinuxOS on a cd anyway, I just hadn't spotted the useful Diskdrake tool.

Many thanks once again.

---

### Post by aysiu on 2006-04-17
[QUOTE=towsonu2003]
Too advanced for my level...[/quote] Mine, too. It's also only useful from a live CD, unless you're resizing a non-Ubuntu partition that's unmounted.

> 
Could we request this for Dapper? I doubt they'd go for it. Space on the live CD is tight, and putting DiskDrake on seems weird, since that's really a Mandriva application.

It seems excessive, but I encourage Ubuntu users to download PCLinuxOS. First of all, it's far more impressive to ex-Windows users if you're introducing them to Linux via a live CD, as it has all the proprietary codecs Windows users tend to love. Secondly, it has this great partitioning tool on it.

Yeah... PCLinuxOS doesn't recognize my sound card or my USB mouse, but it's a great distro for people who have PCLinuxOS-compatible hardware.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=aysiu]
It seems excessive, but I encourage Ubuntu users to download PCLinuxOS. First of all, it's far more impressive to ex-Windows users if you're introducing them to Linux via a live CD, as it has all the proprietary codecs Windows users tend to love. Secondly, it has this great partitioning tool on it.[/QUOTE]
well, while we're there, check out this one [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) a liveCD for partitioning only. I've never used it but I'm gonna try from vmware after I go home (well, if I can download 30mb from my dial up).

---

### Post by imhdd on 2006-07-15
For anyone who has partitioning problems installing Dapper:

I received my free Dapper CD this week (thanks to Canonical). Want to dual boot with Win98SE. Have 80Gb drive, divided into C,D,E,F fat32 for Win98 and  partition G, 46Gb fat32 empty for Dapper.

Install stopped at partitioner. I worked over 6 hours trying to change the existing G, 46Gb to ext3 partitions for Dapper. Tried everything in my tool box including Partition Magic (older version), Maxtor and Western Digital tools, and nothing worked.

Then I remembered an old Mandrake 9.1 Install CD. I used it to partition and format my 46Gb as I wanted it, then shut down computer and installed Dapper with no more problems. I assume Mandrake 9.1 comes with the DiskDrake partitioner.

Now it all works great. I have all my Win98 partitions and Dapper working together just fine.

I should mention that I installed Dapper alone on a 40Gb drive and the partitioner worked fine in that environment.

---

### Post by aysiu on 2006-07-16
Mandrake and Mandriva do, in fact, come with the DiskDrake partitioner.

PCLinuxOS is a Mandriva-based Linux distro.

I've never heard any complaints about DiskDrake, and I constantly recommend it to people on these forums, even though certain forum members insist it's essentially the same program as GParted.

---

### Post by fatsheep on 2006-07-19
I burned the .iso file onto a CD-RW of mine and booted up with it.  I saw the initial PCLinuxOS screen, pressed enter and it started loading.  However it stopped loading and dropped me to a shell:

> ERROR: Unable to mount loop filesystem 
Commands were:
losetup /dev/loop/ 0 initrd/cdrom/livecd.sqfs
mount -r -t squashfs /dev/loop/0 initrd/loopfs

Dropping you to a limited shell

Any ideas?

---

### Post by aysiu on 2006-07-19
Maybe [this](http://www.linuxforums.org/forum/mandriva-linux-help/61197-pls-help-booting-mandriva-2006-free.html) might help you?

---

### Post by fatsheep on 2006-07-20
Thanks for the link.  I guess I'll just try burning the disk again.

---

### Post by fatsheep on 2006-07-20
Hmmm same, I'll try redownloading.  It's the "pclinuxos-p92.iso" one right?

---

### Post by aysiu on 2006-07-20
Yeah. Make sure you do a checksum on the image before you burn it.

---

### Post by fatsheep on 2006-07-20
Well K3B has a checksum thing it runs before it burns the CD but I'm not sure what if that's what you're talking about.  Anyways, I delete my original .iso, redownloaded it, reburned it at 4x speeds and it still fails K3B's checksum thingie.  ](*,)

---

### Post by aysiu on 2006-07-20
Maybe you should download PCLinuxOS with BitTorrent:
[http://www.pclinuxonline.com/wiki/TorrentFiles](http://www.pclinuxonline.com/wiki/TorrentFiles)

---

### Post by fatsheep on 2006-07-21
Alright, bittorent sounds like a good idea.  Downloaded the .torrent, saved it to my desktop, and I tried downloading it in both bittornado and bittorent client but I still get this error message:

> ERROR 
bad data from the tracker - bad bencoded data.


I've even tried turning off my firewall during the downloading of the .iso and the bittorent download, still doesn't work. :-k

---

### Post by kasper.damgaard on 2006-08-26
[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

Try this Freeware program to burn your .iso files

And mind, that it´s not an executable program but once you install it, right click on your iso file and there should be a "copy image to CD"

Easy and smart - works for me flawless. - also with the PSLinuxOS.iso

Regards
Kasper

---

### Post by wcfields on 2007-01-03
LOVELY! I had somehow created an excess partition when trying to load Ubuntu 6.1 while it was still a beta release. Nothing else I tried would let me get rid of that partiton!
     I would like to expand my UBUNTU partition (I'm striving to abandon "windwoes". I have UBUNTU on my second hard drive. It and the swap partition are on the last 10% of this drive.
Can I do this with DiskDrake?
     An off-topic query: my first hard drive seems to have permissions set to root, or something. Half the time I can write to it while running UBUNTU, half the time I can't. Any way to fix this?
:mrgreen:

---

### Post by FlailingJedi on 2007-02-12
Hi all,
Is there any way to get DiskDrake on a live-CD without downloading the entire operating system with it? I've tried GParted already, but it didn't work for me and someone said that DiskDrake was more reliable.

---

### Post by shane2peru on 2008-02-05
Ok, when DiskDrake fails, then we are to assume that the hdd does have bad clusters?  That is the error I got with GParted (which I am partial too), and with DiskDrake.  I really like DiskDrake too, used it loooong time ago, when installing Mandrake to partition my hdd, great tool, has been rock solid for years.

Shane

---

### Post by stinger30au on 2009-10-09
works well, get it from mandriva 2009

[http://www2.mandriva.com/](http://www2.mandriva.com/)

---

### Post by frank cox on 2011-07-14
> **aysiu said:**
> Azz, the whole point of this tutorial is to propose an alternative just in case GParted doesn't work out for some people. I've seen numerous times people posting "greyed out" options that should not be greyed out in GParted and QTParted. I've experienced these problems myself, too.

I'm just proposing an alternative. If GParted and QTParted work out for people, I'm not going to stop them from using those tools.

Good thing you are not an op on the irc channel, to suggest a non-Ubuntu answer there is tantamount to attempted murder.

BTW I have has some times that a Gparted live cd or the gparted in Parted Magic on UBDCD or God forbid a Puppy Linux disk would work when the one in Ubuntu would not. I realize that is blasphemy to some .

---

