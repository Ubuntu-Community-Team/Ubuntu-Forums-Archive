---
title: "Howto Resize the XP partition to get more space for Ubuntu"
date: 2005-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Grul on 2005-05-12
I've been running ubuntu dual-boot with windows xp for a couple of weeks. I like ubuntu so much that I very rarely boot into windows anymore. I gave Ubuntu well little disk space when I set up the partitions on install, though. So what I want to is basically to resize the XP partition and toss that space to ubuntu. Let's say that I resize the NTFS partition with for instance PartitionMagic. How do I format the new space and mount it into the file system? Perhaps I could mount /home in the new space since the / partition is quite small. How do I do that in that case, and how do I copy over the old data in /home? I'm a little confused with mounting, formatting and all that crap right now, so I would appreciate some help so that I don't screw the whole system up.

---

### Post by Xian on 2005-05-12
Basically you would just:

1. Defragment your XP partition 

2. Resize the XP partition with gparted or qtparted

3. Format the free space for Linux (ext3, reiserfs, etc.)

4. Mount the new partition
$ sudo mkdir /mnt/<some_name>
$ sudo mount /dev/hdax /mnt/<some_name>

x=your partition number (assuming you are on the hda drive)
<some_name> = the name you choose for folder

5. Copy over your /home directory
$ sudo cp -rpfd /home/* /mnt/<some_name>/

6. Edit your /etc/fstab to mount the new home directory on boot
$ sudo gedit /etc/fstab
<append the following>

/dev/hdax       /home           reiserfs   defaults         0      2

Note: change reiserfs if needed to the file system you formated

7. Verify the contents of /mnt/<some_name> match present /home contents
Empty the contents of the present /home directory

8. Mount the new /home partition in its new location
$ sudo mount -o remount /dev/hdax

---

### Post by GrumpySmurf on 2005-05-12
Congratulations on making the move to Linux.  You seem interested in using Ubuntu seriously and as such a user, you should become very familiar with technical details on how to do what you want.  It will be better in the long run :).

Here's some tools you'll want to know about:

parted ([http://www.gnu.org/software/parted/parted.html](http://www.gnu.org/software/parted/parted.html))
mkfs (man mke2fs; man mkreiserfs) 
LVM (tldp.org/HOWTO/LVM-HOWTO/)

parted is a text based partition management tool.  mkfs is a general name for the various programs used to format partitions as filesystems.  The above programs in ()'s are for the ext2 and reiser filesystems, both supported by Ubuntu.  The ext3 filesystem is simply ext2 with journaling capability added and can be created with an option to the mke2fs program. LVM is Linux Volume Management, which is a package that makes disk management much easier to deal with.  The link for LVM is the 'official' howto document.  Google searching for ubuntu and lvm will yield some other documents.

So you want to know how to do it?  Here's an overview of the steps you'll need to take.  Some are optional and will be noted as such.

- BACK UP YOUR DATA!!  When doing any complex disk partition operations, you should always back up your critical data before starting.  Personally, I like BRU ([http://www.tolisgroup.com/](http://www.tolisgroup.com/)) as it is extremely reliable and operates similar to tar.

- Use Partition Magic (since you have it) to reduce the Windows partition.  This will give you unpartitioned free space to use.

- Use parted (or another disk partitioning tool if you don't like parted) to create a partition or partitions out of the free space for use by Linux.  

- (optional - potentially dangerous) Encapsulate your root partition in LVM so it is easier to manage and you can resize it easily.  This can be an advanced task.

- (optional) Create the partition as an LVM device so managing the size is easier.  Refer to the LVM HOWTO for example procedures on how to do this.  

- Format the newly created partition (or LVM device) with your favorite filesystem type.  I like reiserfs.  Some people like ext3.  I would use whichever your other Linux partition(s) are.  

- If this filesystem is replacing an existing directory, mount it in a temporary location, such as /mnt/newhome or /mnt/newusr.  Copy the existing directory structure to the new location.  Here's a sample command using /home.
```
$ cd /home ; sudo tar -cPf - . | (cd /mnt/newhome && sudo tar -xPf -)
```
This will ensure the entire tree is copied and the permissions are preserved.  I found tar | tar like this works better than recursive cp.  
Optionally, use mv:
```
$ sudo mv /home/* /mnt/newhome
```

- Unmount the temporary filesystem and mount it in the new location, for example:
```
$ sudo umount /newhome; sudo mount /home
```
Note that the original contents of /home will still be there after you unmount the filesystem.  You may wish to use the optional mv command above, though I'd use the tar | tar and verify that the data is sane before removing the existing director(y|ies).  

The use of LVM is fairly advanced and should be done only if you feel comfortable with the risks involved.  In my not so humble (professional) opinion, the best thing to do, actually, is to back up all your data in Windows and Linux and reinstall Ubuntu, creating the partitions in Linux using LVM from the get-go.  Then you can restore your data and off you go.  This reduces risk of unexpected dataloss or incorrect configuration while doing it on a 'live' system.

Good luck.  Feel free to PM me if you have further questions.  I can provide more "step by step" details if necessary, but its best to dive into these things head first and really learn whats going on with your system :).

---

