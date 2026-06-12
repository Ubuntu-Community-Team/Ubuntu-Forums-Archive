---
title: "Can I change ownership of second internal HD from root so I can use it?"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by salsify2 on 2014-04-02
Now on my fourth day of trying to get 13:10 installed as an XP refugee, I'm still struggling with my second hard drive. Everything I could find in the forums by searching seemed to deal with other situations than mine...or perhaps I just don't have the expertise yet to understand.I have two 325 GB internal hard drives. In the course of installing and reinstalling and reinstalling, even though I am fairly well convinced I only chose to install on the first drive presented (assuming that was the correct one for my boot sequence), I ended up with one Xubuntu install on my second drive. That took me a long time to figure out since they had the same folders and I didn't understand that one whole drive appeared only as "home" and the other as a separate drive—I kept looking for another drive. Okay, sorted that. So now I'm running off of one drive and the other one is ext4 and root.Following some instructions here on the forum, I installed something in the terminal that allowed me to use thunar as root, which allowed me to delete those files. Now I have an empty drive, but it's owned by root so I cannot use it at all. I found some instructions to run a command to change ownership, but those presumed the drive was media/[drivename]. Mine is media/[my username]/[drivename] but when I ran the instructions with that, it gave me a not found.So I'm basically baffled now. Is it possible to change ownership of this drive so I can use it or is it permanently out of reach? Or can I reinstall (groan: I spent all day yesterday downloading software) in some way that will give me access to both drives again? And, finally, assuming I can regain use of that other drive, if I use a portable hard drive to restore my personal files (yes, I did back up before all of this began), do I have to use the terminal for that (I'm puzzled that you have to use the terminal for doing everything)? Can I trust that to be a copying move rather than just, I don't know, erasing that hard drive too (yes, I'm not feeling very trusting right now)?

---

### Post by nothingspecial on 2014-04-02
If you want to use that drive as a storage drive for yourself then it would be a good idea to change the owner to your user. When running commands you have "found" it is a good idea to know what it's going to do. Changing ownership of system files can break stuff. it sounds like you have the path wrong. Did you miss out the leading / ?

You should post the path to your other drive and the command you are trying to run.

---

### Post by salsify2 on 2014-04-02
No, I was trying to avoid pasting anything code-ish since I don't seem to have any formatting in this post box other than smilies (although I see I can write it in directly--phew). ```
sudo chown -R salsify:salsify /media/salsify/36c35993-a1e8-4115-9867-b587a02b3e59
```is what I tried to run, where "salsify" is replaced with my actual name.  And I got that path from the file manager, selecting properties for that drive.ETA: thanks for helping with this.

---

### Post by oldfred on 2014-04-02
I like to label partitions, so the automount is by my label.

But if using a partition regularly it is better to permanently mount it with an entry in fstab. Then everytime you reboot it is auto mounted. You still have to set ownership (chown) & permissions(chmod) if ext4.

This is a manual mount, you would have to unmount with Nautilus if you already have it default mounted.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo [COLOR=#ff0000]chmod[/COLOR] -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo [COLOR=#ff0000]chown [/COLOR]-R $USER:$USER /mnt/data

You can run above chmod & chown on your default mount if desired.

Shows details of editing fstab and adding an entry based on a templeate:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by salsify2 on 2014-04-02
Thank you for your quick response. Unfortunately, I am not yet familiar enough with the specialized vocabulary for this OS to understand everything you have told me.> so the automount is by my label. I have no idea what this means.> But if using a partition regularly it is better to permanently mount it with an entry in fstab. Are you saying that I have to create a partition to encompass that whole drive? Or that it already is one? > you would have to unmount with Nautilus if you already have it default mounted.Do I have to install this file manager or can I use the default one in 13:10? And by "unmount" do you mean right click on the drive and select "eject"? Will I still be able to find that drive after I do that? Apologies for these idiot-level questions, but I'm trying not to make further assumptions that would worsen the situation.> #if not known to list partitions, change sda5 to your data partition or create multiples with different mount pointsI have no real idea what this means. > #where sda5 needs to be your drive, partitionIs that this? ```
/media/salsify/36c35993-a1e8-4115-9867-b587a02b3e59
```> #All directories will be 775.#All files will be 664 Are these some sorts of permissions or sizes or something? I didn't find those on the file permissions page you linked below. I assume that they are the correct whatevers for me to copy all of my personal files in from the backup drive. Yes?> $USERIs that literally what I type or do I put my own username in there? Do I retain the $? Do I type it in all-caps?> Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.When I mounted this drive in the first place, I just right-clicked on it on the desktop and selected "mount" and it's been mounted ever since, even through restarts. Will that not work any longer once I do these things? Really, this makes me want to just lie on the floor and weep. I am terribly sorry to have wasted your time but I can make no sense of this at all. Nor the other links: they simply use syntax and assumptions that I don't have the meaning for and I don't understand whether I have to do each of those things on each of those pages or what. I really appreciate your trying to help, but this looks to me as though you're telling me that unless I understand all of these things, there's no way to get my hard drive back so I can use it or any of my old files.

---

### Post by oldfred on 2014-04-02
When you use Naulitus file manager to auto mount partition it assigns a name. You can for every partition you create give it a label in gparted or Disks (Disk Utility) and then it will use the label. You show it mounted by the UUID which is a unique ID for every partition you create. Applies to partitions on hard drive or a flash drive.

some terms with $ and caps are internal variable. So $USER is your name 
fred@fred-Precise:~$ echo $USER
fred

This shows labels & UUIDs for every partition. I only show some as I have many.
sudo blkid -c /dev/null -o list    

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
...
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
...
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    xubuntu  (not mounted)  6314d8a8-060e-4c02-ad8c-3a2f70e2798b
..
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4    saucy    (not mounted)  ed61920f-fa6a-45a2-bd7c-3ae5502beeb7
...
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    Quantal  (not mounted)  94e634d0-39fb-4994-a685-8ee34747a240
fred@fred-Precise:~$ 

```

YOu can see above some of my partitions are mounted like my shared NTFS data and my Linux data partitions, but other old installs are not currently mounted, but if I click in Nautilus I can mount under the label. I use that for those I may only occassionally want to mount.

I do not think it is preserveing mount.  But it will just keep mounting if you click on it so it may seem like it is already mounted.

---

### Post by salsify2 on 2014-04-02
Thank you so much for trying to help further. I'm still not clear on some points, however.> When you use Naulitus file manager to auto mount partition it assigns a name.  So you're saying I do need to install this program and cannot do it with Thunar, the default one? >  You can for every partition you create give it a label in gparted or Disks (Disk Utility) Are these more programs I need to install? And then use them to partition my HD before I can change the ownership/permissions? Will they work on a HD that's owned by root? Do I need both of them to do this?If it's any help, I ran what you had at the top of your code block and got: ```
/dev/sda1  ext4             /              c26e4bd5-e83c-4f6b-891c-17e33b4c879b/dev/sda5  swap                      a402b199-f3f2-4d7f-9474-8a09da4f176e/dev/sdb1  ext4             /media/salsify/36c35993-a1e8-4115-9867-b587a02b3e59 36c35993-a1e8-4115-9867-b587a02b3e59/dev/sdb5  swap             (not mounted)  00b9e154-cd49-4150-84dd-e3ff3564c0a4
```(Apologies for that all being in a run-on line: I don't know how to break the lines here.) Just to be clear: I'm not interested in multiple partitions (unless they're required) on sdb1; I just want one into which I can put my files.

---

### Post by oldfred on 2014-04-02
I am sorry. I keep discussing Ubuntu which has different default applications than the other flavors of Ubuntu. I am not as familar with Lubuntu or Xubuntu.

I do not understand run on line, that looks like it came from a Windows text editor. 

```
 /dev/sda1  ext4             /              c26e4bd5-e83c-4f6b-891c-17e33b4c879b
/dev/sda5  swap                      a402b199-f3f2-4d7f-9474-8a09da4f176e
/dev/sdb1  ext4             /media/salsify/36c35993-a1e8-4115-9867-b587a02b3e59   36c35993-a1e8-4115-9867-b587a02b3e59
/dev/sdb5  swap             (not mounted)  00b9e154-cd49-4150-84dd-e3ff3564c0a4


```

Because you are mounting by UUID, your sdb1 line shows UUID twice, should have space inbetween.
This is your mount:
/media/salsify/36c35993-a1e8-4115-9867-b587a02b3e59

I do not know if your version has Disks or Disk Utility, it may have something similar. If you have Disks, you the edit partition to add a label.

---

### Post by salsify2 on 2014-04-02
Um, yeah: NoteTab Light because I haven't yet found anything Ubuntu-based that pastes in snippets and I have all of my old snippet libraries set up for it. Will try to find something equivalent when I get the drives sorted. I'll try GParted and see if I can make sense out of what the Xubuntu docs ([http://docs.xubuntu.org/1310/hardware-devices.html#disks-partitions](http://docs.xubuntu.org/1310/hardware-devices.html#disks-partitions)) say about setting up a partition.  And then I'll just do what you pasted in above and hope it all works out despite my lack of understanding.

---

### Post by oldfred on 2014-04-02
I like to install gparted in my install, but you cannot use it on mounted partitions. If you want to edit drive your install is on, you have to use live installer.

But since your data partition is on another drive gparted should work. If already mounted you probably have to unmount it even though just a minor change.
You should be able to click on partition and maybe right click? to edit label.

---

### Post by salsify2 on 2014-04-02
Okay, with a few kerfluffles (I now have a tiny empty partition I can't seem to get rid of) and randomly entering different things when I wasn't really sure what you actually meant, I finally worked my way through your list and rebooted and was able to mount my drive and create a folder in it.  Huzzah! I don't think I really understand what all I did, but it did work and for that you have my deep gratitude.  Now I hope I can just use this OS and software and get back to work after four days lost to the install process. Onward!

---

