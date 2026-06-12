---
title: "Can't find any info: How to partition harddrive zeroed with ubuntu."
date: 2013-09-09
forum: New to Ubuntu
---

### Post by miz-chelle on 2013-09-09
Howdy doodily.. I'm a squeaky clean newbie Linux user. I was assaulted by the zero day virus (or so they think...I'm still a skeptic) while running Windows 7... I was advised to zero out my hard drive using Ubuntu 12.04 and have been experiencing Ubuntu 12.04 ever since my destruction of Windows.. 

Well, I decided that I want to dip my foot back into the Windows pool but embarrassingly enough, I can't figure out how to partition my hard drive so I can still have my savior OS Ubuntu, and all the awesome benefits of said system. I already have the windows iso downloaded but now I don't know what to do, all my tech buddies are busy...:(


Oh god my brain.. I need a friend.

Can I just use Disk Utility and partition my 640 gig hard drive that is currently in Ext4 file type...?  it says device: /dev/sda1 and the mount point is / ...

That's what I"m confused about..Do I have to go into the boot menu instead? I'm so confused and flabbergasted I could cry @.@..  I don't even know if I"m explaining myself correctly...


If anyone has a clue as to what I'm babbling on about please be a sweetie and give a dog a bone...:(


I'll be right over here --------->  'm'@.@'m'

Banging my head on my desk.

---

### Post by carl4926 on 2013-09-09
Really you need to start again. Backup and format, then partition your drive. You would then install windows first, later follow with ubuntu.
Or, could you consider running windows on a second HD? Or on in Virtual Machine?

You see, windows needs a primary partition of type (fat or ntfs) for it's boot code. So you'd basically have to hack up your existing partitions and because that will completely change the table, you would have some considerable editing of system files to put that right. And there is a risk of data loss during partition shrinking etc...

A VM would be my choice if I couldn't start from scratch.

If you do start from scratch, expect at least a full 24hrs to install and fully update windows 7, be sure to do that before installing Ubuntu.

Your partition layout would be something like:
```
/dev/sda1              63   122093999    61046968+   7  HPFS/NTFS/exFAT
/dev/sda2       122094000   128230829     3068415   82  Linux swap / Solaris
/dev/sda3   *   128230891   488392064   180080587    5  Extended
[COLOR=#006400]/dev/sda5       128230893   169196579    20482843+  83  Linux
/dev/sda6       169196643   312560639    71681998+  83  Linux[/COLOR]
[COLOR=#ff8c00]/dev/sda7       312560703   354763456    21101377   83  Linux
/dev/sda8       354763458   488392064    66814303+  83  Linux[/COLOR]
```
That's my HD but I have 2 linux installs side by side

---

### Post by miz-chelle on 2013-09-10
Oh cheese and rice... :'( .. The pain of it all.

What a nauseating process...

I can start over...I guess. Wouldn't be losing any more than I've already lost..

I don't even know how to partition my drive!!!!!! AAAAAAHHHHHHHHHHHHH!!! 



....Need more wine.

---

### Post by miz-chelle on 2013-09-10
Okay okay okay... So basically.... um ...  uhuhuhuhuhuhhhhh.... My harddrive is in linux format..?  That means I need to use Disk Utility to format it....? into the windows file system?

---

### Post by carl4926 on 2013-09-10
I use gparted from a parted magic cd to create all my partitions FIRST
[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

Decide how big you want windows, create it and then the partitions for Linux
ATM you likely have just one ext4 and swap
Personally I use 2 x ext4 partitions in any one system
Usually 
ext4 20GB for /
ext4 70GB for /home (is what you see in my earlier quoted partitions) But you can make /home bigger. It's where all your files are kept.
The system is in / the smaller partition.

Once you have them in place
Install windows to the partition you created. I usually, deliberately use the windows installer to format the ntfs partition again

---

### Post by miz-chelle on 2013-09-10
The partitions from Linux?

Didn't know I'd need ...two..for linux
..........

So I can partition it from my current ubuntu..and set up both of the partitions ...format..etc..while my computers still running, right?! I don't have to go to the boot menu or do any painstaking tasks like that?


Don't I need one ext4 partition and one ntfs partition?...


Partition into 2 sections..then install windows on one, the ntfs..then go back to the other partition ext4..and ...partition that one into 2?

---

### Post by miz-chelle on 2013-09-10
Forgive my ignorance @.@.. I am a partition newbie..

---

### Post by carl4926 on 2013-09-10
> **miz-chelle said:**
> The partitions from Linux?

Didn't know I'd need ...two..for linux
..........

So I can partition it from my current ubuntu..and set up both of the partitions ...format..etc..while my computers still running, right?! I don't have to go to the boot menu or do any painstaking tasks like that?


Don't I need one ext4 partition and one ntfs partition?...


Partition into 2 sections..then install windows on one, the ntfs..then go back to the other partition ext4..and ...partition that one into 2?

No you cannot do it from your existing install
You need to get Parted Magic .iso and burn it to a CD to boot from, just like you burn a Ubuntu .iso to boot from
Parted Magic will by default run from your system RAM, which lets you manage your HD.

You don't need 2 partitions for Ubuntu, it's just my recommendation
1. for root or /
2. for home or /home

So your HD might go like this

sda1 NTFS 100GB Primary for win7
sda3 Extended Primary using all the space
sda5 ext4 20GB Logical for root 
sda6 swap Logical (swap sould be 2 x RAM) so if RAM is 4GB - swap = 8GB
sda7 ext4 Logical using all  the remaining space will be for /home

---

### Post by miz-chelle on 2013-09-10
Sigh.. Well that's all wonderful but it seems I've ran into another issue.. The windows iso I downloaded isn't burning. 

Of all the rotten luck... >=/ ..


If it isn't one thing it's another @.@..

---

### Post by PopsTheSailor on 2013-09-10
Well, here is what I would recommend. Most of this stuff I have done with my current config. All of it I have done before for one reason or another and it has helped.

1. Run DBAN if you really think you need to zero out hour hard drive. I wouldn't bother though.
2. Use your windows restore disks to set windows back up
3. Boot on a 13.04 live CD
4. Open a terminal and run gparted and partition 2 more partitions off of what windows sets up (1 physical drive with 3 logical partitions)
5. Leave Windows on one (I use 50GB of my 320)
6. Create a second 50GB partition and put your favorite version of Ubuntu on it. I'm using 13.04
7. Make the rest of your HDD a data drive. I'm not sure I would use /home as recommended above but the concept is there.
8. I put all my data on the 3rd partition. I then set up programs like Thunderbird to access my folders off of the data drive. It works great and I can use and have access to all my email from either windows or ubuntu. I've got directions somewhere if you want to do this and need help.
9. I then peel off additional 10GB chunks for other versions. Right now I have 12.04, 13.04 and xUbuntu all along with Windoze (snore) 7.

Hope this helps

---

### Post by SeijiSensei on 2013-09-10
If you have a valid Windows ISO and a valid product key, I suggest that rather than futzing with your hard drive, you install VirtualBox and create a Windows virtual machine.  I find this much more convenient than dual booting for running the occasional Windows program.  If, however, you want to play graphically-demanding games in Windows, you'll be better off repartitioning and setting up a Windows partition that talks to the bare hardware.

If you decide to go the VirtualBox route, follow the instructions for "Debian-based" distributions part way down [this page at the VB site]("https://www.virtualbox.org/wiki/Linux_Downloads").  Use the top line in the list of deb: sources, the one with "precise" in its name.

If you need to repartition, you can do this from the Ubuntu installation CD.  Just pick the "Try Ubuntu" option rather than installing.  After you reach the desktop, you should see an entry for the gparted partition manager in the menus.  Back up anything you want to save to another device, of course, since once you repartition, your data will be lost.

One attraction of using a virtual machine is the ability to clobber it if it gets infected.  After you've installed Windows into a VM, look in the "VirtualBox VMs" directory under your $HOME, and you'll see a directory that corresponds to the name of the virtual machine you created.  Copy that directory to another storage device.  Then if Windows goes haywire, you can replace the virtual machine with the pristine version you saved.

---

