---
title: "want to install various distros side by side, but ultimately keep only one"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by triciasurfer on 2012-10-17
Dear popular community of Ubuntu,

Hello. I plan on installing several Linux distributions on my computer that has Windows 7. But I don't plan on keeping all Linux distros forever. I plan on keeping just one Linux distro (and keep the Windows 7 OS). I'm leaning towards Ubuntu, but I'll have to see whether problems arise or not.

What's the best, newbie-friendly way of doing this?

Here's what Gparted on a Live USB shows:
[http://ubuntuforums.org/attachment.php?attachmentid=225647&stc=1&d=1350447634](http://ubuntuforums.org/attachment.php?attachmentid=225647&stc=1&d=1350447634)

/dev/sda1 and /dev/sda2 are Windows7
sda3 is Windows Recovery Environment
sda5 is a Linux distro that's incompatible with me


I'd like to install the following:
Ubuntu 12.04
Ubuntu 12.10 (on Oct. 16 2012)
Fedora
Lubuntu
Xubuntu
OpenSuse
Thanks.

---

### Post by NikTh on 2012-10-17
Hi , 

I will suggest to install all those distributions to a VirtualBox machine. You can test them from there and without risks. (to corrupt your real system). 

About VirtualBox
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Newest VirtualBox version by Oracle
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

The only thing you have to do is to install the VM VirtualBox and download the .iso images you want . This time we speak I have 6 different Distributions in my VB machine. 
Think about it. 

Thanks

---

### Post by triciasurfer on 2012-10-17
NikTh, 
Thanks for your reply. But I think I'd like a real (and not virtual) install of the distros.

The page you linked to says:
> VirtualBox can run a "guest" operating system in a window of the host operating system without giving it direct access to your computer's hardware. 
 

In my various linux distros, I need to be able to access computer's hardware. Playing around with software is not good enough for my purpose.

---

### Post by NikTh on 2012-10-17
> **triciasurfer said:**
> NikTh, 
Thanks for your reply. But I think I'd like a real (and not virtual) install of the distros. Because if I face a problem, how will I know if the problem/bug is caused because of the virtualness or if it's a real problem with the ISO?

OK. You decide what to do. 

As you are now (gparted picture) you can start to cut space from /dev/sda5/ . 

/dev/sda5 is a logical partition and you can create (if I remember correctly) up to 32 logical partitions inside /dev/sda4 (extended partition), but you want only 5-6 . So start to cut space (always from the END of the /dev/sda5 partition) and create logical partitions with ext4 file-system. 

You can install the Distributions you want then. 

Be aware that you have 78GB free space to /dev/sda5. Leave some space for /dev/sda5 , at least 15GB (at my opinion) OR  if you can delete some files (or transfer them) so the free space will grow up. 

A suggestion would be to create logical partitions of 10-12GB each. 

Thanks

---

### Post by HermanAB on 2012-10-17
Virtualbox is the way to go.

---

### Post by triciasurfer on 2012-10-17
HermanAB,
VirtualBox is the way to go test software. But I'm not just testing the distro software, but see whether they work with hardware devices I use.

VirtualBox is not the way for me to go.

---

### Post by audiomick on 2012-10-17
Hi. Nik's advice was good. You can chop up the logical partition into several smaller ones to allow you to install several OS's. You will only need one swap partition. Each Linux install should find the existing swap, or be able to have the swap assigned to itself during the install. 

A word to the wise: I can recalling reading about people having trouble with installing OpenSuse after other OS's, or maybe Fedora. I can't remember too well. The trouble was that the bootloader was overwritten such that the previously installed OS's couldn't be found. Whatever; I personally would install those two first, then the Ubuntu flavours, and not worry too much about whether they boot until I get them all on and give GRUB, the bootloader, a chance to find them all during the last install.

You might want to leave a Data partition on there as well, so you have got somewhere central to store stuff to. If you want it to be accessible from the windows install, you should make it a ntfs partition.

---

### Post by triciasurfer on 2012-10-17
audiomick,
thanks for the tip on installin Fedora and OpenSUSE first and installing the Ubuntu flavors last.


----
To all:
How should I set up the partitions on GParted? What's clear to me is that all the Linux distros should be under /dev/sda 4 (extended). But what's the next step?

And when should I make new partitions? Should I create the 5-6 partitions at the outset, or should I make one new partition when I'm done installing the last Linux distro?  

How big should I make each?

How do I create the /data/ folder that will be shared among the various Linux distros?

---

### Post by triciasurfer on 2012-10-17
I have another question.

Let's say I have divvied up the 100 GB free space to 4 Linux distros, giving each distro partition 25 GB each. Let's say that my original plan was just to install 4 Linux distros and no more. 

But let's say that later, I find another Linux distro that I want to install. What are the steps to make space for the fifth? How easy is it to change from
 4Distros x 25GB
to
5 Distros x 20 GB


How do I do that?

Or must I know how many distros I want to install, before I start installing any of them?

---

### Post by JKyleOKC on 2012-10-17
> **triciasurfer said:**
> How easy is it to change from
 4Distros x 25GB
to
5 Distros x 20 GB


How do I do that?

Or must I know how many distros I want to install, before I start installing any of them?Not very easy at all, since to get the space for the fifth partition you would have to shrink each of the first four to 20 GB each, then move the upper three of them down to put all of the free space together. Moving a partition is an excellent opportunity for Murphy's Law to strike and wipe out that partition completely.

If you don't know in advance just how many distros you want to try out, I would recommend creating as many partitions as you can, giving each the minimum size (which ought to be at least 15 GB and more would be better, depending on how many bells and whistles you want to install later). Then, as you rule out each one you don't want, re-use its partition for the next one you want to add.

You mentioned that the one already there is already ruled out, so you can delete it right at the start and add it to your free space.

---

### Post by audiomick on 2012-10-17
Yes, what Jim said.

I would use gparted to do the partitioning. It is on the ubuntu live CD/ USB, or can be had as a stand alone bootable application. As Jim said, shuffling partitions around is a tiresome chore which carries a certain risk of losing data. I did some today. Reduced one approximately 45 GB partition by 4GB on the left hand end and gave the 4GB to the partition to left of it. That took nearly 2 hours. That was an oldish computer with not all that much RAM, but you get the idea.

I think the suggestion is good to set up several partitions of around 15GB each. That should be enough for the bulk of Linux distributions if the install is only for the purposes of testing. Do consider setting up a Data partition, or perhaps even a second (external?) drive for data. I reckon you can't really test a system without actually doing useful stuff with it, so you will need somewhere central to keep your files.

As I said, set up a few partitions (logical partitions inside the extended partition) and get your first installs on there. If you later want to add one, use the next partition or add a new one. If there is some empty space, leave it there for now. It wont hurt anything, and will make it easier to add another partition later if you need to.

---

### Post by triciasurfer on 2012-10-18
How do I create a "/home/" or "/MyDocuments/" sort of folder/partition that is easily accessible to all Linux distros?

---

### Post by NikTh on 2012-10-18
You can create a common /home partition where all Linux Distributions can have access to it. The only thing you must be aware of is that you have to set the same name (not username) during install. 
During install you have the option to set the name of the user (this must be the same) and the username (this can be different). 

You have to use the "something else" option during install and mount under /home the partition you already have created. 

You must be careful of 2 things. 
1) Use the same name 
2) Do not use the same username. 

The first will granted you with access to all /home folders , without a matter in what distribution you boot in. 

The second will ensure that you will not have problems with conflict of configuration files from each distribution.

Good luck.

---

### Post by triciasurfer on 2012-10-18
NikTh,
thanks for your reply.

So when I install OpenSuse, Fedora, Ubuntu, Kubuntu, etc, they'll all ask me for 
1) Name
2) Username
?

And I should have the same "Name" in all distros?

---

### Post by NikTh on 2012-10-18
> **triciasurfer said:**
> 

So when I install OpenSuse, Fedora, Ubuntu, Kubuntu, etc, they'll all ask me for 
1) Name
2) Username
?

And I should have the same "Name" in all distros?

Yes.
And the same Name will give you access in all /home folders of each distro , no matter in what Distro you are connected. eg : from Fedora you will have access to OpenSuse /home folder (the OpenSuse's home will appears inside the /home partition like a common folder with files.) 

The different username will avoid any conflicts with configuration files between the Distros.. Each Distro will use  its own user's(username) home. 

Thanks

---

### Post by triciasurfer on 2012-10-18
nikth,
but I just want one home folder, shared among all distros.

---

### Post by NikTh on 2012-10-18
> **triciasurfer said:**
> nikth,
but I just want one home folder, shared among all distros.

No , this is not going to work. Different Distros , different configuration files. It will conflict each other. 

You have to create a common space (partition) and mount all /home folders(of each Distro during install) under this partition. Each Distro (when the username is different) will make its own /home folder. 

This is the only way I know.

---

### Post by JKyleOKC on 2012-10-18
There's a related point that's not at all obvious until it bites you. Behind the scenes, the kernel and file systems identify users by UID number, not by actual name. And different distributions start the UID number at different values. This means that, as an actual example, files owned by "jim" on a Mandriva system were not accessible to "jim" on Xubuntu after I switched over several years ago!

Mandriva systems, and I believe other RedHat-derived distributions, assign UIDs starting at 500, while Xubuntu and most Debian-based systems start with UID=1000. After my switch, the files showed as being owned by user "500" and group "500" instead of "jim" and "jim."

When I did the permanent switch, it was easy enough to fix things on the very few critical files involved: I simply used "sudo chown" to change ownership of the files from "500" to "jim" and that put the new UID into place for them. However this doesn't work when you are trying to access a common "/data" partition from several different distros at the same time. I don't think there's a single, simple solution to the problem in this case; when you know it's there, though, you can deal with it when necessary by copying the files using "sudo" and fixing the copies.

---

### Post by buckyaustin on 2012-10-18
There are a numerous amount of solutions here. I would reccomend installing all ubuntu varations using the repositories. Just use ubuntu software center for that. Then install virtualbox to run non-compatible OS's that way. This will use the least amount of your computers resources. While keeping you on the one OS. You will have to log out to switch which ubuntu your using. Shouldn't take you too long to get used to that. Good luck with that.

---

### Post by audiomick on 2012-10-18
As has been said, don't try and share a /home partition across different distributions. I is likely to lead to trouble. 

It sounds to me like you just need to have a separate Data partition.

---

### Post by buckyaustin on 2012-10-19
Try a multi-boot usb. This can be done using YUMI on windows. Not sure about Linux. When all the OS's are on the usb boot each one of them one at a time. This way you can check if the OS works with the hardware. Keep in mind to check Additional Hardware each time, because some drivers are not installed automatically with Ubuntu for various reasons.

Is this what you were looking for?

---

### Post by newb85 on 2012-10-19
My suggestion for your Home folder:

Create a common partition that is *not* set as /home for any distro.  Add folders to it to mirror the non-hidden folders in your home directories.  Replace those folders in your home directories with symlinks to their respective folders on the common partition.

You could also do this with some hidden folders to share settings for specific applications.  However, there are some system configuration files which need to not be shared between systems.

---

