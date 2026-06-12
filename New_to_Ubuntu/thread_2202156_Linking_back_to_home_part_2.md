---
title: "Linking back to /home part 2"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-27
Back during my earlier experimentation trying to do this, I mounted the sda6 partition on the hdd at /media/Data.

I am now trying to finalize my startup with the old desktop showing in /home on the SSD, and want to make the mount point at /mnt/data.

Firstly, somehow that earlier mount instruction seems to survive a restart or shutdown, but there is no entry in fstab. How is this happening?

In anticipation of this maybe being useful info, here is fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5c523eff-90ae-47f8-a810-aff90a07b0dd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=A403-1C37  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda2 during installation
UUID=428c5eb3-d21b-4bda-b50a-ab3755ff24a7 /home           ext4    defaults        0       2
```

The above to assist with the first question and also relevant to #2 below:

and here is gparted:


Maybe not. Tried to insert image but it wants a URL. How do I just insert the screenshot?

Anyway it shows that sda is the HDD, whereas the above fstab is showing the SSD as SDA1. I conclude from this that fstab considers the drive that it is booting from as sda, whereas gparted has started after the boot, can see both drives, and assigned different drive sequences to the two drives. Is this correct?

More to come but don't want to overreach with questions. Will build on answers to the two questions above.

---

### Post by oldfred on 2014-01-27
Post #4 shows it, but not updated to new forum. 
 Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)

With new forum you just go to Advanced editor and click on paperclip icon in edit panel at top. Then you can open an upload window to browse your system for a file. Must be small or screenshot or smaller amount of data. Some formats will not upload. And some do not work first time, but then do??

Generally Ubuntu uses the drive order that BIOS/UEFI reports. On my system it is port order plugged into motherboard. But I skipped one port and if I plug in a flash drive it is sde, but if I reboot it is sdb and every other drive changes. So I have to be careful not to erase wrong drive.

---

### Post by Odyssey1942 on 2014-01-27
Thanks. I had clicked on the paper clip, but when it said attachments, while I was thinking insertion, I moved on. Got it!

> Firstly, somehow that earlier mount instruction seems to survive a restart or shutdown, but there is no entry in fstab. How is this happening?

Anyone got any thoughts on the first question? I don't want to start editing fstab until I know how this is happening.

---

### Post by oldfred on 2014-01-28
If it is not in fstab, I do not see how it can automount? Possibly script in startup? Did you do something there?

Right after booting post this, it should be the same as fstab plus internal mounts.

mount

---

### Post by Odyssey1942 on 2014-01-28
OldFred, Did not see yours while I was writing the below.

Well, this is interesting. When I turned the computer on this morning, dev/sda6 was not mounted, so yesterday's #1 has gone away. Moving on:

Here are my proposed steps to make permanent the linking of Desktop in sda6 to Desktop in /home. I am posting these here because I still don't understand exactly what the chown command is doing here and don't want to screw things up too badly. it is a lot quicker to do this right the first time than to try to explain later what I did, and what the error codes were.

1) Are these commands correct, and in the right step order? If not how should they read?

```
sudo mount /dev/sda6 /mnt/data
sudo chown -R robert:robert /mnt/data/tmp
sudo bind /mnt/data/tmp/home/robert/Desktop  Desktop
```

*If  the above tests OK, then edit fstab as below. I have made a backup of fstab*

2) (does edit need to be with gksu or sudo gedit /etc/fstab ?)

```
# mount dev/sda6 at /mnt/data
UUID=428c5eb3-d21b-4bda-b50a-ab3755ff24a7      /mnt/data           ext4    defaults        0       0
# bind files in /dev/mnt/data/tmp/home/robert/Desktop
/mnt/data/tmp/home/robert/Desktop	/home/robert/Desktop	none	bind
```

From OldFred's post in another thread, there needs to be some chown lines as well:

chown -R robert:robert /mnt/data/tmp (and does this need the "-R" following "chown")
and
chmod -R a+rwX /mnt/data

3) I still find ownership and permission baffling and so am unsure if one or both of these lines is required, and if so where in the changed fstab? Any guidance, ideally with explanation as to what they are actually doing would be very much appreciated.

4) Any other lines that need to be in the fstab that I haven't included? 

5) One that I remember in which OldFred discussed order of action in fstab and a caution about ensuring that the above take place AFTER the current fstab lines have done all their execution, citing a post by morbius, and I am looking for that post now, but if anyone can comment on this or point me to the thread, that will be appreciated also.

Since there are so many parts to this, I have numbered my questions to facilitate referencing back to all those that aren't answered in the resulting replies.

---

### Post by oldfred on 2014-01-28
You need to create mount points like /mnt/data, so it exists when you run the update to fstab.

You use sudo with command line tools, but if a gui based tool like gedit or gparted then you should use gksu or gksudo.

Why /mnt/data/tmp for any commands or is that just a test. I would just use /mnt/data.
And you do not have to manually mount if adding to fstab, in fact that will conflict once you do add to fstab. If manually mounted for testing, us umount (note no n) to unmount. Or Disks or gparted or Nautilus to unmount.

-R is resursion or it runs command on all subfolders. Sometimes after copying a lot of data I find it easier just to rerun the command so all data has correct ownership & permissions.
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

My commands are really based on this. See Morbius1 post for more detail.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.


 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by Odyssey1942 on 2014-01-28
> You need to create mount points like /mnt/data, so it exists when you run the update to fstab....

....And you do not have to manually mount if adding to fstab, in fact that will conflict once you do add to fstab. 

I don't understand this. The first sentence says it is needed and the second says it would conflict. Did you mean that it IS NEEDED before editing fstab, and AFTER fstab is modified and run that there is no longer any need for manual mounting? Please clarify.

> Why /mnt/data/tmp for any commands or is that just a test. Was an error, and yes that was for testing.

I don't understand the referenced post re Morbius, and so am going back to code to see if I have it right now. Still don't know if order of the below is correct or if chmod is needed?

```
# mount  dev/sda6  /mnt/data
UUID=428c5eb3-d21b-4bda-b50a-ab3755ff24a7      /mnt/data           ext4    defaults        0       0
# bind files in /dev/mnt/data/tmp/home/robert/Desktop
/mnt/data/tmp/home/robert/Desktop	/home/robert/Desktop	none	bind
# Will edit this later to explain what the following command does as soon as I understand what it does
chown -R robert:robert /mnt/data/tmp
# Will edit this later to explain what the following command does as soon as I understand what it does IF IT IS NEEDED
chmod -R a+rwX /mnt/data
```

---

### Post by oldfred on 2014-01-28
There is a difference between creating a mount point which will persistence until you delete it, and using that mount point by mounting a partition to it either manually or with fstab. 
If manually mounted or mounted with Nautilus, then an entry in fstab may conflict.
I do not know bind but assume manual bind may conflict with a bind in fstab.

This creates a mount point. And then you can mount any device to that.
 sudo mkdir /mnt/data

This actually mounts a partition to that mount. But only defaults are specified. And on reboot the mount is lost, but the mount point exists so you do not have to recreate it.
      
 sudo mount /dev/sda5 /mnt/data

And an entry in fstab creates a permanent mount that will be reloaded on reboot. You also can set many parameters. If NTFS you also only create default ownership & permissions since NTFS does not support those at the file & folder level.

Link to Morbius1's post it to provide more detail. He often explains a lot of things.
some more info on ownership & permissions by Morbius1, see post #8
He also creates mounts for many folders, so you can use his preferred bind.
      
 [http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

---

### Post by Odyssey1942 on 2014-01-28
Delighted to report that I not only understood all of your comments, but did so beforehand. In fact I might edit one of your lines
> This actually mounts a partition to that mount.
 to read:
> This actually mounts a partition to that mount point.

Could I ask you, or another, to please answer my questions in the previous post (#7). I really would like to wrap this up.

Many thanks.

---

### Post by oldfred on 2014-01-28
You do not put chown or chmod in fstab. Those are just commands you run once configured. Should only have to run once.

And I think Morbius1 now uses scripts to bind after the mount in fstab. They have sped up boot process and now there may be issues of timing? Do not use nor know bind so not sure of details.

       User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

Not sure about Desktop as a mount point. When I use Music I have to delete the Music in /home first. And Desktop is the icons on the Desktop in my system, so you want everything showing on Desktop?

I used to do this:
 mv Music oldMusic
That way I could go back easily or confirm I had nothing in my Music folder.
Now I do it as soon as I install, so I know it is empty. But then no going back and saying I had info in it.
rm -rf Music/
ln -s /mnt/data/Music

Then I can link my folders into my /home. I think bind would be similar.

---

### Post by Odyssey1942 on 2014-01-28
Thank you for the specific guidance as well as other thought provoking comments.

> And I think Morbius1 now uses scripts to bind after the mount in fstab. They have sped up boot process and now there may be issues of timing? Do not use nor know bind so not sure of details. Scripts are yet an unexplored process for me. Will work on this on my own computer, now that I can get this one back to the Missus (and hope that all runs smoothly with the binds). Will report later.

Unsure about this:
> Not sure about Desktop as a mount point. When I use Music I have to delete the Music in /home first. And Desktop is the icons on the Desktop in my system, so you want everything showing on Desktop?

Unless I am still not understanding the terminology, I am only using /mnt/data as a mount point, and using the (old) Desktop as a mount bind (via that mount point) to the current Desktop. The good news is that it seems to be working exactly as I want it to. It allows me to retain the same desktop layout (with icons, folders, shortcuts, etc grouped by subject which correspond to each of my eight work spaces WITHOUT having to re-create it. When I switch workspaces, if I need anything, I just open that folder and under it are individual files and subfolders which are organized appropriately pertinent to the subject. This allows a fairly uncluttered desktop but just a click away from anything I need.

and:
> I used to do this:
mv Music oldMusic
That way I could go back easily or confirm I had nothing in my Music folder.
Now I do it as soon as I install, so I know it is empty. But then no going back and saying I had info in it.
rm -rf Music/
ln -s /mnt/data/Music Exactly when in the install process did you make the file transfer to oldMusic and what was your concern about not having an empty folder? Maybe I don't see the intent, the files are in either Music or oldMusic. Why does it matter?

From what I know of mounting /home in another partition, binding the way I am doing gives me most of the advantages, but few of the disadvantages. Still unsure about whether there is any advantage with respect to configuration files, but guess I will learn in due course.

Edit: Suddenly this popped into mind:
```
All these commands will need sudo, as I am copying from my script.
mkdir /mnt/data
chown $USER:$USER /mnt/data
#chmod 777 /mnt/data
#The big "X" will also not make files executable unless they were executable to begin with.Morbius1
chmod -R a+rwX /mnt/data
``` This from post #2 in:

[http://ubuntuforums.org/showthread.php?t=2201514](http://ubuntuforums.org/showthread.php?t=2201514)

Why were they needed there, if I do not need them here?

---

### Post by oldfred on 2014-01-28
I copied commands from a script. I do a lot of new installs and copied one set of commands from bash's history, type history in command line to see all the commands you have run. 
And then you do not use sudo on each line but just to run bash file.

Almost all system commands need sudo or gksudo if graphical. I still type some commands and system comes back, gives me the raspberries and tells me I do not know what I am doing. So I try again with sudo. But this has never worked for me:
 [http://xkcd.com/149/](http://xkcd.com/149/)


As soon as I install I used to copy Music to oldMusic so I did not delete the default folder created in /home. In beginning I was running from a working system not new install & I wanted to be sure things worked and nothing had been saved to original Music or oldMusic before deleting it. 
And if you leave the current Music the link will not work as it cannot have two places for data.

This converted your standard Desktop to the version in old install.
 /mnt/data/tmp/home/robert/Desktop	/home/robert/Desktop	none	bind
If that works that is good. Not sure if you have overwritten default Desktop with bind or not. 
With links the old Desktop would be gone and you would have to manually recreate it.

---

### Post by Odyssey1942 on 2014-01-28
Also: > [QUOTE]You need to create mount points like /mnt/data, so it exists when you run the update to fstab....

....And you do not have to manually mount if adding to fstab, in fact that will conflict once you do add to fstab.
I don't understand this. The first sentence says it is needed and the second says it would conflict. Did you mean that it IS NEEDED before editing fstab, and AFTER fstab is modified and run that there is no longer any need for manual mounting? Please clarify.[/QUOTE] I am still unclear about the apparent conflict here.

If you did clarify, I did not understand it. Is this the key sentence and is it correct? > Did you mean that it IS NEEDED before editing fstab, and AFTER fstab is modified and run that there is no longer any need for manual mounting? If so exactly when should it be deleted? Thanks.

---

### Post by oldfred on 2014-01-28
I thought we discussed the difference between having a mount point and using the mount point to mount a partition. 
The mount point must exist.
But then you can manually mount a device  to test or temporarily use it.
But an internal drive you often permanently mount a partition in fstab.

But you can only use a mount point once to mount it. Either manually or with fstab. Also if you just click on a partition in Nautilus it will auto mount it, so then you would not be able to manually mount it or use fstab to mount it.

But you do not have to unmount any manual mounts if you reboot as that unmounts everything. But I prefer to test mounts in fstab before rebooting to make sure I can reboot. So I use the 
sudo mount -a

See also from a terminal, q to exit.
man mount

This quickly shows each command also:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Odyssey1942 on 2014-01-28
We did indeed, and even though I understand the difference, I wasn't reading yours closely enough. I now see why I was confused, and  that there is no conflict. Thanks for your patience.

One other thing: > But you do not have to unmount any manual mounts if you reboot as that unmounts everything. But I prefer to test mounts in fstab before rebooting to make sure I can reboot. If not rebooting, should any manual mounts be manually unmounted before running sudo mount -a as there is no reboot to remove them, or does sudo mount -a also automatically remove them?

---

### Post by Odyssey1942 on 2014-01-28
In the link you included in post 14, I saw this: ```
Since we've made changes to the /etc/fstab file, we need to have Ubuntu acknowledge those changes:
sudo mount -a
Now I need to give it the proper permissions. Let's just assume, for this example, that my username is jessica.
sudo chown -R jessica:jessica /storage
sudo chmod -R 755 /storage
Now the partition is mounted in the /storage folder and is ready for use!
```

Here again are the chown / chmod lines which I had asked about earlier, and this makes me wonder if they should be included in the fstab edit? Or manually added after each boot? (Surely not?) Or not needed in my case? What think you and why?

---

### Post by oldfred on 2014-01-29
If you run the mount -a with a partition already mounted you get an error message, something like already mounted.

You use command line to set ownership & permissions and only run that once. 

As I mentioned before if I have copied a lot of data, say from NTFS where there are no ownership and permission, I might rerun it. The settings should make all files added with correct settings, but I have managed to get some files with wrong settings and it is often easier just to reset all than do it manually for each file.

See this for the style of fstab entries, anything else is an error so any command line entries would be errors. 

man fstab
man mount
use q to exit.

---

### Post by Odyssey1942 on 2014-01-29
Fred, really great reply. Understood it all first read! That should wrap up the "system side" of the installation. I still must add her files created or modified since the tarball, but your guidance on permissions in your last post ought to get me through it. Thanks again for your steady assistance.

In summary, resolution of this project has taken me 10 days, on and off, and either had I knew then what I know then, the solution would have only taken 30 mins or less, including testing, or had I been able to describe the entire project more successfully at the outset it probably would not have taken a whole lot longer.

But I learned a lot in the process, for which I am gratified. However, I could have been using most of that time for other productive pursuits too. So I will post a summary of the solution under the heading "Alternative to mounting partition as home, using mount bind" in the "Installation & Upgrades" Forums later today or tomorrow, depending on the file project above. That way there is a summary for anyone trying to do the same thing that they can either use to do their thing, or for other noobs to use as a tool to learn how to do it.

I will mark this solved

---

### Post by oldfred on 2014-01-29
Glad you got it working. :)

---

