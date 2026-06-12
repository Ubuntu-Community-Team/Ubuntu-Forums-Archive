---
title: "reinstalling ubuntu with seperate home partition."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by donniezazen on 2008-10-25
Hi,

I have installed Ubuntu with separate home partition using following guide.

> **k3lt01 said:**
> If you do this you MUST back up your home folder and I would advise you to make a list of all your programs you have and use (even if they are not in your applications list. Step by step. I can't and wont take responsibility if you lose info or stuff the install.

1. Get your live cd and start your machine as you did when you installed Ubuntu last time.

2. Go through the processes as you did before until you get to partitioning the hard drive.

3. When you get to the partitioner you have few options chose the "manual partition option.

4. Click in the hard drive partition shown and then click edit partition.

5. Now you have to decide whether your willing to start again with total new install or whether your willing to risk resizing the / partition. f I were you I'd do a totally new install as you should have backed up your important info anyway. Now here you can click either delete this partition or edit this partition. If you click delete it WILL take you back to a totally clean install.

6a. Delete partition option chosen. Click on the blank partition (Free Space) and click new partition. This will bring a box up showing how big your hard drive is, adjust the number to 10000. Now go down to "Mount point" and click the down arrow to select "/" (this is your root partition), then click to format this partition and it will ask you what format to use chose ext 3 Journaling File System, now save these changes.

6b. Now you need to click on the "Free Space" again, "New Partition" again, make the size 2000 choose "SWAP" in the file format click to make the change.

6c. Same process again but use the remaining free space and choose "home" in the mount option.

7. Go through the rest of the install as you did before.

8. Make sure you put the files you backed up from your old /home partition back into your new one so you keep your old settings.

9. Re-install any programs you need that are not in the standard system which you had before.

10. Remember to let Ubuntu update itself after this is all done.

Last and most importantly enjoy your system and update your "/"partition when you want to want to upgrade to a new version.


Now i am wondering how to reinstall new upgrade. Suppose i am at manual partition part. When it asks me to where i want to install ubuntu i will chose 10 gb / partition(mount point / ).

1. Do i need also to chose /home and /swap partition? or just leave them as they are and just chose 10 gb already made / partition.
2. Should i back up before reinstall?

Thank You.

---

### Post by em4r1z on 2008-10-26
What's the version installed?, why do you need to reinstall the system? Reinstalling is the last resort to 'solve' a problem. If you want to upgrade your system from, say, 8.04 to 8.10, the system will tell you when the whole update is available and take care of it.

Following that 'guide', you'll need to tell the installer the location of the system and home partitions (the swap one will be automatically detected and formatted), the difference is that you'll ask it not to format the home one. Otherwise the installer will create a home folder within the system partition and the former home partition will be mounted as any other partition.

I wouldn't use all the remaining space for the home partition, though, for you might want to try a different operating system and/or make more partitions to, say, take advantage of different filesystems (a folder filled with hundrends of documents behaves different than one filled with movies, and different filesystems might be better for each.)

---

### Post by mikewhatever on 2008-10-26
> **soham_1207 said:**
> 
1. Do i need also to chose /home and /swap partition? or just leave them as they are and just chose 10 gb already made / partition.

You have to specify root (/) and swap (swap, [COLOR="Red"]not /swap[/COLOR]), as for the /home partition, it's up to you.

> 2. Should i back up before reinstall?

Yes, backup all personal files.

---

### Post by donniezazen on 2008-10-27
Thank You. Let me be more clear.

I have 8.04. I want to install 8.10 after its stable release in few days. To save myself from upgrade problems and i don't have a fast internet so i will download 8.10 using torrent and install it.

I have a separate /home partition. How to install 8.10 without formatting home partition and making new install use same previously created home partition? As i already have a separate home partition do you still suggest to backup all my data?(Oh! God moving/backing up music/movies worth 100 GB sucks up)

Sorry for not being so clear.:popcorn:

---

### Post by bumanie on 2008-10-27
Basically, you should only have to install intrepid to /, just make sure you don't format /home and everything should be fine. I have /home on a separate hard drive and never had an issue installing and formatting /

---

### Post by RavUn on 2008-10-27
What are the benefits of installing /home on a different partition?

---

### Post by em4r1z on 2008-10-27
> **soham_1207 said:**
> I have 8.04. I want to install 8.10 after its stable release in few days. To save myself from upgrade problems and i don't have a fast internet so i will download 8.10 using torrent and install it.Why would there be upgrade problems? Ubuntu releases aren't 'stable' as in 'error free', they're taken from the unstable branch of the system they're based on, Debian. I don't see how installing a newer system is easier than upgrading.
If your main concern is your Internet connection, you can upgrade using the Alternate CD.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by donniezazen on 2008-10-27
> **em4r1z said:**
> Why would there be upgrade problems? Ubuntu releases aren't 'stable' as in 'error free', they're taken from the unstable branch of the system they're based on, Debian. I don't see how installing a newer system is easier than upgrading.
If your main concern is your Internet connection, you can upgrade using the Alternate CD.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I have read many threads which suggest that it is better to reinstall then to upgrade. Upgrade will take whole day on my slow internet and new install will just take 30 mins. With the stable release i meant i do not want to install alpha or beta releases. Yes i can use Alternate CD.

---

### Post by tuxxy on 2008-10-27
If you upgrade rather than install you will not need to edit your fstab to remount your /home partition and also the update should be error free, I even did one last night :)

If you want to fresh install from the CD at installation/partitioning menu you should select your /root partition to install to, do not use the option "use whole disk" or install to your /home partition, there should be a graphical image of your disk anyway so you can keep your /home partition safe.

So for example if your sda 1 is /root sda2 is swap sda3 is /home then install to sda 1

---

### Post by donniezazen on 2008-10-27
> **RavUn said:**
> What are the benefits of installing /home on a different partition?

Having a separate /home partition makes it easier for you to reinstall Ubuntu while preserving your personal files and settings. This is a matter of convenience but is not foolproof. You should still regularly back up your data.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by donniezazen on 2008-10-27
> **bumanie said:**
> Basically, you should only have to install intrepid to /, just make sure you don't format /home and everything should be fine. I have /home on a separate hard drive and never had an issue installing and formatting /

> **tuxxy said:**
> If you upgrade rather than install you will not need to edit your fstab to remount your /home partition and also the update should be error free, I even did one last night :)

If you want to fresh install from the CD at installation/partitioning menu you should select your /root partition to install to, do not use the option "use whole disk" or install to your /home partition, there should be a graphical image of your disk anyway so you can keep your /home partition safe.

So for example if your sda 1 is /root sda2 is swap sda3 is /home then install to sda 1

If i chose to install new release in / partition will it not install everything(/,/swap,/home) in that small 10 gb partition instead of using old /home partition.

---

### Post by mikewhatever on 2008-10-27
> **soham_1207 said:**
> If i chose to install new release in / partition will it not install everything(/,/swap,/home) in that small 10 gb partition instead of using old /home partition.

Yes, it will put /home there. If you already have a home partition, you'd have to specify it as a separate partition too, and make sure not to format it.

---

### Post by SteveNorman on 2008-10-27
sorry this is not meant as a hijack,I am doing the same as OP. The answer to my question may benefit OP so forgive me if this redundant or a hijack.


So after installing the new release to /, and leaving the original (old release) home on its partition, it seems like we will have 2 separate home files. One home file on / that is created with the new install,, and also the old home on its partition left over from the old install. If this is the case is it simply a matter of removing the new home file from /? Are we fine at this point or is there a mounting procedure necessary to get the new install to recognize the old home after the new one is removed?

I am assuming the procedure goes like this:
1. backup old home
2. install new release to /
3. remove new home from /
4. mount old home using```
$sudo mount -t ext3 /dev/sda3 /home
```
where ext3 and sda3 are whatever filetype and partition old home is on.

Can someone verify this?

---

### Post by mikewhatever on 2008-10-27
No Steve, to avoid having two homes, you should point the installer to the partition you want to use as home. It's done exactly the same way as with root and swap, just be careful and don't format it.

---

### Post by em4r1z on 2008-10-27
> **soham_1207 said:**
> I have read many threads which suggest that it is better to reinstall then to upgrade.Bad advices inherited from their experience in Windows. Operating systems shouldn't be reinstalled every now and then.
I still fail to see your point for an upgrade downloads less files than a complete image. One shouldn't waste server resources just because it's freely given to him.

---

### Post by SteveNorman on 2008-10-28
em4r1z...

I am going to reinstall because I have screwed around with ubuntu to the point that I cant remember half of what I have done to it over the years. I want a fresh install so I can format and configure it with the knowledge I have gained as a result of experimentation with linux to the point that I dont want to do the work required to fix the current install. In short,, because I want to. Please dont assume I or anyone else here is doing anything because of a windows brainwashing. I have done as much experimenting on my OS as I could have. 90% of it is FAIL, but I have learned an enormous amount. My reward? Fresh install. Properly this time I hope thank you very much.

---

### Post by donniezazen on 2008-10-28
Thank You Guys

---

