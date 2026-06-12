---
title: "Boot Partition Resizing"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by manikinxvx on 2014-08-23
I feel the need to ask this, as I apparently made a grevious error in a past reformatting and only allocated 220MB to the boot partition(sda1) and I failed to even notice it until Software Updater recently began notifying me that there was not enough room on that partition for new updates. 

Now, my question is, since I've never attempted this process, if I... using GParted... reduce the size of the partion not allocated  to boot(sda5 in this instance) and apply that change, could I *possibly* be able to then increase the size of the boot partition without reformatting and doing a total reinstallation?

Thanks in advance and for taking the time to read.

---

### Post by yancek on 2014-08-23
Another thing you can do is remove some of the kernel and initrd files from the boot partition.  First, determine which kernel you are currently using so you don't remove that.  This is explained at the link below.  I have seen a number of posts here which go into detail on potential problems with deleting kernels so you might use the search function here at the forums.

[http://askubuntu.com/questions/473217/i-cant-delete-old-kernel-ubuntu-14-04](http://askubuntu.com/questions/473217/i-cant-delete-old-kernel-ubuntu-14-04)

---

### Post by ajgreeny on 2014-08-23
Run command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-85
```which will show all the kernels installed in your system that appear in the grub menu, even if you don't see that menu.

The output will look a bit like:-
```
menuentry 'Xubuntu-12.04-amd64 Precise, with Linux 3.13.0-34-generic' --class xubuntu-12.04-amd64 --
menuentry 'Xubuntu-12.04-amd64 Precise, with Linux 3.13.0-34-generic (recovery mode)' --class xubunt
menuentry 'Xubuntu-12.04-amd64 Precise, with Linux 3.13.0-33-generic' --class xubuntu-12.04-amd64 --
menuentry 'Xubuntu-12.04-amd64 Precise, with Linux 3.13.0-33-generic (recovery mode)' --class xubunt
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

```
You can then use synaptic (install it if you haven't got it; it's the best package manager available) to search by name only, not name and description, for the old versions of kernel that you don't need any more and remove them along with their header packages, to leave just the two most recent.

Just out of interest, why have you got a separate /boot partition?  It is not needed in a desktop system and often causes the exact problem you are seeing here.

---

### Post by rbmawby on 2014-08-23
Folks, it would be really nice to know how to increase the /boot partition on a very big hard drive.

As explained, new folks go with the defaults and get things as described.

If possible, a filter entry would help a lot with Synaptic Package Manager?

It seems both of us are hung at the same spot!

Burke

P.S. also, not owning the files makes deletion difficult.

---

### Post by SuperFreak on 2014-08-23
Removing old kernels can also be done though [Ubuntu Tweak]("http://ubuntu-tweak.com/") without much fuss . You are probably saving old kernels that you don't need to run your system. Just make sure there are two kernels left on the PC

---

### Post by JKyleOKC on 2014-08-23
+10

**Ubuntu Tweak** is an excellent tool for maintaining a system. Its "janitor" function will tell you all the superfluous files that you can erase without killing the system, but you have to check them off to actually get them done away with. It has a number of other capabilities as well. Search for [http://ppa.launchpad.net/tualatrix/ppa](http://ppa.launchpad.net/tualatrix/ppa) to find out how to obtain and install it.

PPAs are "Private Personal Accounts" which are **unofficial** repositories that are not vetted by official sources, but the "launchpad" site **is** official and any PPA set up there is watched pretty closely by the community. I believe that anything there is safe from malware, but some PPAs are for software that's still not fully tested and can introduce problems.

The Ubuntu Tweak PPA, however, hasn't caused any problems for me in the two years I've been using it.

---

### Post by Elfy on 2014-08-23
> **rbmawby said:**
> Folks, it would be really nice to know how to increase the /boot partition on a very big hard drive.

As explained, new folks go with the defaults and get things as described.

If possible, a filter entry would help a lot with Synaptic Package Manager?

It seems both of us are hung at the same spot!

Burke

Open synaptic - select the installed status, put the number of the kernel in the filter box, click on Latest Version so it sorts - select the ones you wish to remove.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=255779&d=1408826524[/IMG]

---

### Post by Elfy on 2014-08-23
> **ajgreeny said:**
> ...
Just out of interest, why have you got a separate /boot partition?  It is not needed in a desktop system and often causes the exact problem you are seeing here.
Possibly a LVM install - you get no option if you use the standard installer on /boot size. 

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

If you are affected you can mark it as affects you with [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093/+affectsmetoo)

---

### Post by rbmawby on 2014-08-23
[Ubuntu Tweak]("http://ubuntu-tweak.com/"), as stated, cannot install until space is available.

---

### Post by rbmawby on 2014-08-23
This is so very good and of course it worked. You ROCK!

---

### Post by rbmawby on 2014-08-23
This was my install to verify the [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar610428_162.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=610428") 				 				 					 						 	[**[COLOR=#990303][B]Elfy**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=610428") Synaptic fix below. Thank you. I did the non-system items to do a quick cleaning. Out of curiosity why is there no review of **Ubuntu Tweak? Thanks again.**

---

### Post by manikinxvx on 2014-08-23
ajgreeny, as for why I have a separate /boot partition, 
this was another part of the error when reformatting.

---

### Post by manikinxvx on 2014-08-24
The tips and tricks for working around this issue in the short-term are great and very much appreciated. However, the answer to my specific question of resizing the partition seems to simply be, "No, that can't be done." Thank you to all who contributed... time to backup the very few things that get saved/stored on my internal drive and start the reformatting process. Hopefully I'll be able to clear this up with a new install and paying more attention this time.

---

### Post by JKyleOKC on 2014-08-24
I believe the main point for many if not most of us is that your 220 MB /boot partition is more than large enough as it stands, once it has been cleared of all leftover garbage.

My own /boot directory is using less than 62 MB; your partition could hold three copies of it with room left over.

That's with two sets of kernel files stored in it, which is all one ever needs. Any time you have more than two sets, you need to clean out the older ones. The only reason to keep more than one is that sometimes kernel updates introduce very subtle bugs that don't show up immediately, so it's wise to keep the previous version of the files after an update appears. However anything older will probably never be used again. Why waste space keeping it?

Almost all the other stuff you install will go into the "/" partition; only those files absolutely required for the first stages of powering up live in "/boot" so when you install a new kernel, it won't double in size. Many of the files, such as memtest, don't change from one kernel version to the next.

Thus there's no need to reformat and reinstall, unless you simply want to take advantage of all that you've learned since the first time around.

Actually, there's a way to change the size of partitions without totally reformatting, but it's quite tedious and if you happen to get a power failure midway through, then you have to reformat anyway...

---

### Post by rbmawby on 2014-08-24
Folks, THANK YOU SO MUCH! 

The quickness (especially on a weekend), 
clarity (even with steps for Synaptic Package Manager and with a screen capture including a filter), and 
accuracy of your responses is GREATLY APPRECIATED!

---

