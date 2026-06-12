---
title: "Low Disk Space"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by pjstock on 2012-03-24
I am reeeeeeallly sorry to return to an issue that so many unsophisticated users (like me) have struggled with. I have read the threads that purport to address this Low Disk Space issue but I cannot make heads or tails of the steps they suggest taking.

I appear to have run of of space on my "root" (I use terms very cautiously) partition even though I have some 32Gb free on the other Hard Drive.

One thread suggested trying a command df -h to see what my disk setup looked like. They then suggested some cleaning steps.

Below are the Before view, the steps I took and the After view (which looks basically the same as the Before.)

If I am reading this correctly my root is currently configured at 19G? 
and it is 100% chewed up?

and my other drive is 228G and it still has space.

What is gobbling up the 19G in my root and how do I figure out what I can delete without fouling things up.




I tried these steps but don't seem to have freed up any space. What am I doing wrong? results before and after and steps here:

/dev/sda1              19G   18G   64K 100% /
none                  750M  284K  750M   1% /dev
none                  754M  352K  754M   1% /dev/shm
none                  754M  332K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sdb1             228G  185G   32G  86% /media/e0275508-079c-4be0-84f0-3919816ce305

julie@julie-desktop:~$ sudo apt-get clean
[sudo] password for julie: 

julie@julie-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
julie@julie-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  acroread-common wine1.2-gecko
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
After this operation, 8,278kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 257041 files and directories currently installed.)
Removing acroread-common ...
Removing wine1.2-gecko ...
julie@julie-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   18G  7.9M 100% /
none                  750M  284K  750M   1% /dev
none                  754M  388K  754M   1% /dev/shm
none                  754M  332K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sdb1             228G  185G   32G  86% /media/e0275508-079c-4be0-84f0-3919816ce305
julie@julie-desktop:~$

---

### Post by ksa618 on 2012-03-24
To try and find where all the data eating your space is, you can look around with the following command:
```
du -sh <directory>{/CODE]
So to check the disk usage of everything in /tmp you would run
[CODE]du -sh /tmp
```
Just poke around the file system with the command. You may need to use sudo for some directories. Start with /tmp and /var/log.

---

### Post by pjstock on 2012-03-24
OK, did a little housekeeping and moved some personal files off the small partition to the big hard drive.

df -h now shows:

julie@julie-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   15G  2.8G  85% /
none                  750M  284K  750M   1% /dev
none                  754M  472K  754M   1% /dev/shm
none                  754M  332K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sdb1             228G  188G   29G  87% /media/e0275508-079c-4be0-84f0-3919816ce305
julie@julie-desktop:~$ ^C
julie@julie-desktop:~$ 

My question then is, is it normal to have 15G of a 19G partition used for just the basic installation of Ubuntu 10.04 LTS?

Or should I be searching around for more dead wood to clear out?

Just going one by one through my File System folders I see the big users are:
dev 832mb
home 861Mb
lib 636mb
media 2.4Gb++++ (but clicking through this seems to be the same as File System - bin, boot, cdrom, dev, etc....
opt 235 mb
proc 1016Mb
sys 300Mb
var 249Mb

So those only total about 4.1G

usr is still counting (2.2Gb and rising. 2.4Gb, )  but clearly there is something going on there.

Goodness I wish I was more linux/ubuntu savvy. A little bit of knowledge truly is a dangerous thing.

what is all this stuff under SRC under USR?
I see about 8 sets of folders:

linux-headers-2.6.32-28
linux-headers-2.6.32-28-generic
linux-headers-2.6.32-29
30
31
etc. 

can I delete some or all of these?

---

### Post by snowpine on 2012-03-24
Ubuntu includes a tool called **baobab disk usage anayzer** that you can use to figure out what's using up all that space.

Here is a terminal command to show usage by folder:

```
 du -h --max-depth=1 /
```

15gb is the recommended **minimum** hard drive for Ubuntu, so I do not think your usage is atypical.

**Whatever you do** do not delete files outside your /home folder. If you find a file or folder that you do not think belongs, check back with us before you do anything! :)

---

### Post by 23dornot23d on 2012-03-24
Computer Janitor  [URL="http://manpages.ubuntu.com/manpages/jaunty/man8/computer-janitor.8.html"][COLOR=Blue][U]**LINK**
[/U][/COLOR][/URL]
and

[[COLOR=Blue]_**Bleachbit**_[/COLOR]]("http://bleachbit.sourceforge.net/") this is installable through the software center or 

**sudo apt-get install bleachbit**

May help in the short term to solve your problem ..... but if you want we can increase
the root size ..... 20 Gig is ok usually but if you have a lot of programs installed this
can get eaten up .....

gparted and resizing the root partition may be a option here ..... but first try to clean
a little space using the tools above .....

Post screen shots - if you need to make decisions using Computer Janitor ...... as it will show the things it thinks needs removing ..... and sometimes I see things in that list that
are important to me ..... but as you will see - you can always untick them .....

---

### Post by wildmanne39 on 2012-03-24
Hi, computer janitor and even bleachbit to some extent deletes packages that you need sometimes and will most likely cause stability problems.

Your root partition is what gets filled up when you install applications, so I usually give myself 20 gigs for it but most people recommend smaller but I have ran out of space in root before and I never want to do that again.

The size all depends on how much you install applications.
Thanks

---

### Post by Zimmer on 2012-03-24
Accessories>Disk Usage Analyser... to see where it is all going wrong...

If your GRUB menu is overfull of old kernel entries then it is time to go to the Synaptic Package manager and mark the OLD ones for removal, including their associated headers .. check which version number you need to keep! (suggest you keep the two most up-to-date kernels).
You are looking for entries like ...
 linux-headers-2.62.32-x 
 linux-image-2.62.32-x   

where x is a version number...
 
    
 
Then run sudo update-grub from a terminal to update the grub menu.

---

### Post by westie457 on 2012-03-24
> **Zimmer said:**
> Accessories>Disk Usage Analyser... to see where it is all going wrong...

If your GRUB menu is overfull of old kernel entries then it is time to go to the Synaptic Package manager and mark the OLD ones for removal, including their associated headers .. check which version number you need to keep! (suggest you keep the two most up-to-date kernels).
You are looking for entries like ...
 linux-headers-2.62.32-x 
 linux-image-2.62.32-x   

where x is a version number...
 
    
 
Then run sudo update-grub from a terminal to update the grub menu.

+1 to the above.

Something else to do is force a file-system check on the partition.

One way is to boot into the Live Desktop from a LiveCD/USB in try mode. Then run Gparted, right-click the problem partition and select 'check' and then click 'Apply'.

It is possible to force the check using the command-line however I cannot remember or find what the command is.


One question for you. Is the 'Trash' empty?
Hope this helps.

---

### Post by snowpine on 2012-03-24
Agree with the above that you can get rid of all but the 2 newest kernels and their headers or source. (Use your package manager, don't just delete the files.)

After which, to reclaim the disk space, you may need to:

```
sudo apt-get clean
```

---

### Post by pjstock on 2012-03-24
OK, so my USR folder totals 2.5Gb of which the subfolders have:

bin 166 Mb
games 1.7 Mb
include 4.9Mb
lib 1 Gb
local 108
sbin 25Mb
share 1 Gb
src 321

that about adds up.

is it likely that there is unecessary stuff in Share or Lib which are the biggest of the bunch?

---

### Post by NikTh on 2012-03-24
[IMG]http://imagebin.ubuntu-gr.org/1332629198.png[/IMG]> **pjstock said:**
> 
I see about 8 sets of folders:

linux-headers-2.6.32-28
linux-headers-2.6.32-28-generic
linux-headers-2.6.32-29
30
31
etc. 

can I delete some or all of these?
For old kernels remove , there is also an automate tool from **[Ubuntu-Tweak]("https://launchpad.net/ubuntu-tweak")**


[IMG]http://imagebin.ubuntu-gr.org/1332629198.png[/IMG]

---

### Post by pjstock on 2012-03-24
> **snowpine said:**
> Ubuntu includes a tool called **baobab disk usage anayzer** that you can use to figure out what's using up all that space.

Here is a terminal command to show usage by folder:

```
 du -h --max-depth=1 /
```

15gb is the recommended **minimum** hard drive for Ubuntu, so I do not think your usage is atypical.

**Whatever you do** do not delete files outside your /home folder. If you find a file or folder that you do not think belongs, check back with us before you do anything! :)

I am sure I am not using this command correctly. I seem to get a bunch of Permission Denied errors like this:

```
du: cannot read directory `/proc/29/task/29/fdinfo': Permission denied
du: cannot read directory `/proc/29/fd': Permission denied
du: cannot read directory `/proc/29/fdinfo': Permission denied
du: cannot read directory `/proc/30/task/30/fd': Permission denied
du: cannot read directory `/proc/30/task/30/fdinfo': Permission denied
du: cannot read directory `/proc/30/fd': Permission denied
du: cannot read directory `/proc/30/fdinfo': Permission denied
du: cannot read directory `/proc/31/task/31/fd': Permission denied
du: cannot read directory `/proc/31/task/31/fdinfo': Permission denied
du: cannot read directory `/proc/31/fd': Permission denied
du: cannot read directory `/proc/31/fdinfo': Permission denied
du: cannot read directory `/proc/37/task/37/fd': Permission denied
du: cannot read directory `/proc/37/task/37/fdinfo': Permission denied
du: cannot read directory `/proc/37/fd': Permission denied
du: cannot read directory `/proc/37/fdinfo': Permission denied
du: cannot read directory `/proc/38/task/38/fd': Permission denied
du: cannot read directory `/proc/38/task/38/fdinfo': Permission denied
du: cannot read directory `/proc/38/fd': Permission denied
```

> **Zimmer said:**
> Accessories>Disk Usage Analyser... to see where it is all going wrong...
.

DU shows the attached.
there seems to be an Audacity (a sound recorder I use) folder hogging 4.5Gb.
I could happily get ride of or relocated that if I could figure out where it is located.

> **Zimmer said:**
> it is time to go to the Synaptic Package manager and mark the OLD ones for removal, 

Thank you.
But in Synaptic Package Manager, where would I find this setting or whatever to mark old kernel thingees for removal.

In SPM I see about 30 versions of ... everything.
linux-backport, linux-headers....

so, can I just mark for deletion anything but that latest couple of versions?

My goodness there is a lot of stuff in SPM. 
is there an automated way of not letting it get so out of control?

I am trying to delete the 4.5Gb of space tied up in the Audacity audio application.

can anyone tell me why these files and folders are Locked under both users on this system, Peter and Julie?

and how I unlock them or eliminate these space wasters?

(by the way, thank you all very very much for your patience, expertise and help.)

---

### Post by 23dornot23d on 2012-03-24
I just did a google search on the temp files for Audacity .....

dont use it myself - but there may be a answer in these links somewhere ...

[https://www.google.com/search?client=ubuntu&channel=fs&q=removing+audacity+temp+files&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=removing+audacity+temp+files&ie=utf-8&oe=utf-8)

---

### Post by JKyleOKC on 2012-03-24
> **pjstock said:**
> My goodness there is a lot of stuff in SPM. 
is there an automated way of not letting it get so out of control?Not any safe one, but there IS a way to make the task less tedious. In Synaptic, select "Status" from the list of options in the lower left corner of the dialog. The choices in the upper left corner will change; select "Installed" from there. At this point you'll only see those packages that are installed on your system.

Next, type "2.6.32" in the "Search" window at top right of the dialog. This should reduce the listing to only those packages that contain the version number 2.6.32. Click the green checkbox on each of those packages EXCEPT the two most recent ones, and select "Remove completely" from the pop-up option window. This means that you should have two copies of each of the different packages; there should be at least four packages left with green checkboxes rather than red.

When finished, click the "Apply" button, and examine the list of things that will be removed completely to make sure that nothing for the two most recent kernel versions is listed. Then turn it loose, and you may gain more than a gigabyte of disk space. That's how much I got back when I cleaned out the -32 through -38 versions earlier today.

If your kernel version is not 2.6.32, replace that with the actual version number in all the steps above, but do not include the final number that distinguishes one update from the next.

Hope this helps!

---

### Post by NikTh on 2012-03-24
> **pjstock said:**
> 
My goodness there is a lot of stuff in SPM. 
i**s there an automated way of not letting it get so out of control?**

> **NikTh said:**
> [IMG]http://imagebin.ubuntu-gr.org/1332629198.png[/IMG]
For old kernels remove , there is also an automate tool from **[Ubuntu-Tweak]("https://launchpad.net/ubuntu-tweak")**


Look post #11  and the attached .

If you want to proceed with the installation of ubuntu-tweak do 
```
sudo add-apt-repository [B]ppa:tualatrix/ppa
[/B]sudo apt-get update
sudo apt-get install ubuntu-tweak
```

---

### Post by pjstock on 2012-03-25
making progress. thank you all very much.

My thunderbird profile was taking 3.5Gb of space.

Question: what does a "dot" in front of a folder mean?
My Audacity (sound editing) software is taking 4.5Gb and is listed in a .audacity.... folder.

---

### Post by centaurusa on 2012-03-25
> **pjstock said:**
> Question: what does a "dot" in front of a folder mean?
My Audacity (sound editing) software is taking 4.5Gb and is listed in a .audacity.... folder.

.folder just means that the folder is hidden unless you specifically indicate that all folders are to be displayed (e.g. in Nautilus - Ctrl-H).

It sounds like you have some user-created files that you may be able to delete.  Otherwise, why not just resize some of your disk partitions to use some of the unallocated space to make the Ubuntu partition larger.  As noted earlier, you could install GParted (Gnome partition editor) and use this tool.

GParted Manual
[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)
 

GParted partitioning software – Full tutorial
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
 

Modify Your Partitions With GParted Without Losing Data
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by pjstock on 2012-03-25
That GParted full Tutorial is the clearest thing I have read so far on Partitioning. Thanks

I just opened Gparted to see what my set up currently looks like. Screenshots are attached.

if memory serves though that I think I might have two physical drives, one only 20Gb and the other something like 250Gb.
(this was a cobbled together system and so I might well have just used a spare 20Gb HDD to install Ubuntu on.)

Would this seem correct based on the screenshots? 

if that is the case, I presume I cannot resize the "sda"? 
To get more space for Ubuntu I would have to reinstall on the other HDD or another one?

Again, many thanks. This has been a very helpful exercise. I don't feel as useless and helpless as I did 2 days ago.

Peter

---

### Post by JKyleOKC on 2012-03-25
> **pjstock said:**
> if that is the case, I presume I cannot resize the "sda"? 
To get more space for Ubuntu I would have to reinstall on the other HDD or another one?Not at all; you can have the larger one automounted and store data on it while the system files stay on the smaller one. It's a bit complicated to explain but quite straightforward to actually do. The starting point is to create an empty partition on the large drive, and a (temporary) mount point in your system, then mount that empty partition at the new mount point. Next, copy all the content of your home directory to that new mount point and verify that it's there. Finally, add a line to the /etc/fstab file to mount that new partition to /home/yourname (with "yourname" replaced by your actual user name) at boot time, and reboot the system. Your home directory will now be on the large drive rather than on the small one and all new files you create there will be on the large drive as well.

Verify these instructions with others, though, before trying to follow them. I've given you the "executive summary" but there may be critical points that I've overlooked, and if there are, you could make your system difficult to boot (although I don't think I've suggested anything that could cause permanent damage)...

---

### Post by snowpine on 2012-03-25
> **pjstock said:**
> DU shows the attached.
there seems to be an Audacity (a sound recorder I use) folder hogging 4.5Gb.
I could happily get ride of or relocated that if I could figure out where it is located.

Do you see where it says "Scan Home" near the top left of the screen? One of the icons just to the right of that is "Scan Filesystem" and that's the one you want to click to analyse the full disk (not just your /home folder).

Based on the screenshots I don't see any problem really, it's just that your 20gb drive is not much bigger than the recommended minimum of 15gb, so you will have to be very careful installing applications, downloading files, etc. :)

---

### Post by 23dornot23d on 2012-03-25
> 
Based on the screenshots I don't see any problem really, it's just that  your 20gb drive is not much bigger than the recommended minimum of 15gb,  so you will have to be very careful installing applications,  downloading files, etc. :smile:
I agree too .... the gparted screenshots look good ..... you should be ok now for some time ....

The thing I would consider for the future .....

The 20 Gig drive ...... * ( if this in a Desktop machine ..... )

At some point I would consider upgrading the drive ( possibly a matching 250 Gig internal and clone the 20 Gig to it .... )

another option that I recommend if its a laptop .... is to add a external USB hard drive
my favourite is the 500 Gig Seagate .... for speed and ease of setting up. 
( each computer is different - but upto now I have had no problems and run them on 4 different computers .... )

As I say looking at what you have now - you should be ok for some time .... unless you intend installing loads of massive games ..... if the applications that you install are small
you should be able to go for a good six months .... maybe when the new 12.10 comes out ...... consider new options ..... my 2 cents anyway .... ;)

---

### Post by pjstock on 2012-03-26
> **23dornot23d said:**
> if this in a Desktop machine ..... )



Indeed this diagnosis was for a desktop.

But speaking of laptops..... my next cleanup project is on a laptop sporting Ubuntu but which only has only a single 35Gb HDD total.

the DF-h command shows the following:

peter@peterx300:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.5G  5.7G  408M  94% /
none                  300M  652K  300M   1% /dev
none                  307M  1.2M  306M   1% /dev/shm
none                  307M  420K  306M   1% /var/run
none                  307M     0  307M   0% /var/lock
/dev/sda6              29G   23G  5.2G  82% /media/28a27f7c-83ff-4415-b9c5-7734f03be244


I expect that like my desktop, I have inadvertantly saved user generated files to the boot area.
How can I use Disk Usage Analyzer to show me usage on just the boot partition folders? (Or at least to have it analzye each partition independently). That is I expect where the constriction is most occurring.

---

### Post by 23dornot23d on 2012-03-27
> 
/dev/sda1             6.5G  5.7G  408M  94% /
You are cutting it close for root in my mind here ..... 6.5 Gig .... you may be constantly
having to tidy this up ......

My option was to add a external USB hard drive ....

I have a Acer Aspire 1350 laptop with a 40 Gig drive in it .... and have it set up for
basic things like browsing the Web and a couple of 3D programs for design work 
but all the Data goes to a external 500 Gig USB drive ....

Root I rarely have below 20 Gig on any of my installs ...

Yours is
6.5 Gig with 408 meg free .....

Even after tidying it up completely you are not going to get any lower than 5 Gig ....
and that may not run many things ......

But its a good puzzle .... to work on ..... 

My idea would be to increase that partition size and make life easier for yourself ......
and add a external USB hard drive .....

I used to mess about reducing and reducing things ..... 
but with updates and upgrades being as they are ..... 
the best way is add more storage space IMHO ....

Especially with the Total Drive only being 35 Gig here ......

---

### Post by wildmanne39 on 2012-03-27
Hi, also if your root get's completely full your system will not boot.
Thanks

---

