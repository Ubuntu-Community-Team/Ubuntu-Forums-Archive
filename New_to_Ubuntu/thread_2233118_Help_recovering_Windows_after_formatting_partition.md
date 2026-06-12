---
title: "Help recovering Windows after formatting partition to ext4"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by axel12382 on 2014-07-06
Hi, I "tried" installing ubuntu through usb. Half way though the process I got to the partioning part. I tried to make my own partition. I changed some things where the windows partition was. But I decided not to go through with the install and hit "quit" I rebooted my computer and now I have no operating system at all. I have yet to install ubuntu and now my windows OS is gone. Before I rebooted my computer I was able to see the windows partition through the file viewer but now it says that the ssd is empty. Is that even how it works? I didn't even get to the next window of partitioning and it alters my whole ssd. I am still using the ubuntu usb boot to post from here.

Is there a way to get my windows OS back and/or files at least?

---

### Post by Vladlenin5000 on 2014-07-06
Hi, welcome.

I don't know exactly what you did when running the installer but this > I changed some things where the windows partition was. tells us you may have done something. You should never mess with the previous Windows partitions when creating new ones for Linux. Always use Windows tools to manage Windows partitions, namely to resize them.

So... Can you remember exactly what you did, ie, what "changes" have you attempted to do in the preexisting Windows partition(s)?

---

### Post by axel12382 on 2014-07-06
I believe that I changed the windows partition from ntfs to ext 4 file system. Then after that I pressed quit and rebooted. But I didn't go to the next screen of the installation process.

---

### Post by Vladlenin5000 on 2014-07-06
> **axel12382 said:**
> I believe that I changed the windows partition from ntfs to ext 4 file system.

Well, that should do it. I wonder why you did that?... What were you trying to achieve? Windows can't even recognize other EXT2,3,4 partitions let alone be installed in one of them.
Now *probably* you'll need some external tool to recover the data from the botched partition...

Again, whenever you need to install another OS and dual-boot it with Windows, you never ever change the Windows partitions. If resizing is needed - it often is - that should be done from Windows with Windows native tools.

(EDIT) Bottom line: Ubuntu didn't delete your Windows, you did that.

---

### Post by axel12382 on 2014-07-06
Well its not I call myself a computer enthusiast. But if this is how the linux crowd welcomes curious people then thats cool. /s

---

### Post by lisati on 2014-07-06
> **axel12382 said:**
> Well its not I call myself a computer enthusiast. But if this is how the linux crowd welcomes curious people then thats cool. /s

We appreciate your frustration. Please be patient with us while we try to get a clearer picture of what actually happened with your computer, so we can make suggestions that are better informed and more relevant to your situation.

---

### Post by kansasnoob on 2014-07-06
I've had very good luck recovering data with TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

But you'll have to reinstall Windows when you're done recovering data.

---

### Post by kansasnoob on 2014-07-06
> **Vladlenin5000 said:**
> Well, that should do it. I wonder why you did that?... What were you trying to achieve? Windows can't even recognize other EXT2,3,4 partitions let alone be installed in one of them.
Now *probably* you'll need some external tool to recover the data from the botched partition...

Again, whenever you need to install another OS and dual-boot it with Windows, you never ever change the Windows partitions. If resizing is needed - it often is - that should be done from Windows with Windows native tools.

(EDIT) **[COLOR="#FF0000"]Bottom line: Ubuntu didn't delete your Windows, you did that[/COLOR]**.

In this particular case it does sound like user error, but the live installer has a nasty bug too:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by Vladlenin5000 on 2014-07-06
> **kansasnoob said:**
> In this particular case it does sound like user error, but the live installer has a nasty bug too:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Indeed, really nasty. I should have add it to the edited part of my previous post :(. The intention all along was to inform the thread's title is quite misleading because this sounds like user error. Although I don't have a clear enough picture of what happened and whether or not recovery tools such as TestDisk and/or Windows boot recovery tools are needed, _meanwhile this shouldn't be confused with bug#1265192_.

I'm sorry this sounded rude but it wasn't and it isn't by any *etiquette* I'm aware of. It isn't of course any scripted formula you'd expect from an helpdesk -> Chapter 3a: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
There's a good chance for the worst scenario which is having to rely on data recovery tools therefore you thread's title should reflect that in order to attract the experts (or advanced user) with such tools.

---

### Post by kansasnoob on 2014-07-06
> **Vladlenin5000 said:**
> Indeed, really nasty. I should have add it to the edited part of my previous post :(. The intention all along was to inform the thread's title is quite misleading because this sounds like user error. Although I don't have a clear enough picture of what happened and whether or not recovery tools such as TestDisk and/or Windows boot recovery tools are needed, _meanwhile this shouldn't be confused with bug#1265192_.

I'm sorry this sounded rude but it wasn't and it isn't by any *etiquette* I'm aware of. It isn't of course any scripted formula you'd expect from an helpdesk -> Chapter 3a: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
There's a good chance for the worst scenario which is having to rely on data recovery tools therefore you thread's title should reflect that in order to attract the experts (or advanced user) with such tools.

I don't think you were rude or said anything wrong, I just try to share info on that bug whenever I can :)

But it must be part of Murphy's law; ***the data you don't have backed up is always the data you lose!*** I'm anal about back ups (and back ups of my back ups) because I've lost data due to fire, flood, and a malicious ex besides the normal puter problems.

---

### Post by yancek on 2014-07-06
I don't imagine the OP will be back, but there was no information in his posts about which windows version he was using and whether it was an OEM install.  It should then have had a Recovery partition and if he had the foresight to make the recovery CD, he would be good to go with his windows.  I bought an HP several years ago with windows 7 installed and used Parted Magic to shrink the windows partition.  Before doing that, I had created a Recovery CD.  After shrinking the windows partition, I rebooted or rather tried.  Could not boot so there I was the second day with the computer having to recover it.  I know a lot off people successfully use PMagic or GParted on windows partitions but my experience makes me paranoid about it so I agree with the suggestion above.

Given the incredible number of tutorials available online, especially for Ubuntu, it seems as though the OP did not make much effort before starting or he would have known not to reformat the windows partition.  Hopefully, there is a Recovery CD somewhere.

---

### Post by Vladlenin5000 on 2014-07-06
I'm still baffled about changing the Windows partition to EXT4 (why on Earth?...) but no less baffled by the partitioner actually making that change without proceeding with the wizard (the OP says he didn't).

---

### Post by coffeecat on 2014-07-07
I don't think anyone responding to the OP needs to be concerned about what they said in this thread. All comments appear to be relevant and constructive. I have changed the thread title to something more accurate and more helpful both to the OP and to those responding. 

> but no less baffled by the partitioner actually making that change without proceeding with the wizard (the OP says he didn't). 

My guess is that the OP chose the "something else" option at the partitioning stage where (I believe) you can commit a partition reformat and then abandon the wizard. Reformatting the Windows partition does seem an unfortunate choice to have made.

---

### Post by yancek on 2014-07-07
The OP specifically states he selected to format the windows partition to ext4, obviously misreading or misunderstanding some tutorial or a badly written tutorial.  After doing that and checking the format box, I don't beleive any changes are made until you click the Install button.  That's probably what happened but I guess it doesn't matter now, except to the OP I guess.

---

### Post by coffeecat on 2014-07-07
> **yancek said:**
>  After doing that and checking the format box, I don't beleive any changes are made until you click the Install button.

It is possible to reformat a partition without proceeding with the installation using the "Something Else" option. I've just confirmed this with the 14.04 installer. In brief:

1 - Preexisting sda7 NTFS partition.
2 - Start Ubiquity installer.
3 - At partitioning stage select "Something Else".
4 - Highlight sda7, click on change.
5 - Change the "do not use partition" dropdown to ext4 and tick "format the partition". OK that.
6 - Click continue button with the "write previous changes to disk?" prompt.
7 - Screen refreshes after a little while with sda7 now showing ext4.
8 - Quit Ubiquity with quit button.
9 - sudo parted -l confirms that sda7 is now ext4.

Which is probably similar to what the OP did, except they seem to have reformatted their Windows C: partition. If they provide more details we will know better.

---

### Post by yancek on 2014-07-07
> Click continue button with the "write previous changes to disk?" prompt.

That should do the job without clicking the Install Now.  I don't really expect users to know this information but there is not shortage of tutorials, particularly for Ubuntu so it's hard to empathize when someone doesn't appear to have made much effort before beginning the install.  On the other hand, there are a lot of really poor tutorials out there.

---

### Post by nadarockyraccoon on 2014-07-07
Something worth noting here is that the op seemingly only destroyed the functioning windows partition, thus the recovery partition likely is still intact. A little tidbit geek squad doesn't want you to know, you can use a live boot of ubuntu to turn that drive on and recover windows. Simply boot, open gparted and right click the recovery drive(usually a fat32) go to manage flags and check boot. Reboot and the recovery should start. This will reformat the hard drive and wipe linux out.

I've never had much trouble letting linux resize windows and automatically partition the disk, but when I did this fixed it(and still works in windows 8). On the other hand what do you need windows for, and please don't say itunes or netflix. There are better solutions to those things that don't force users to buy a specific os or software. Also please please please read through the text and diologues in the installer. It let you know what you were doing and that it might break stuff. Linux will let you do that, for all it knows that is what you wanted.

---

### Post by yancek on 2014-07-07
I have windows 7 on one of my computers and have an entry in the Grub boot menu for the Recovery partitions which is functional so in this particular case, no need for a LiveCD or GParted.  Might have been able to use that option also, but he hasn't been back so...

---

