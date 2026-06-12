---
title: "Sync folder on a different partition with Ubuntu one"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-03-08
Hi, I have a shared partition between windows and ubuntu, I want to sync it to ubuntu one but it wont work, I found this answer:



> [COLOR=#333333][FONT=UbuntuRegular]What you'll need to do is create a bind mount.
Here's some simplified steps assuming you know a little about mounting:

[LIST=1]
[*]Create a directory to mount in home: mkdir ~/Documents
[*]Create a directory as a mount point for the partition: sudo mkdir -p /mnt/SharedPartition
[*]Get the device id for your partition: sudo blkid
[*]Edit your fstab (By device id is used in UUID (also use your home directory):
[/LIST]
UUID=4B38-4ED2                  /mnt/SharedPartition  vfat auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  2
/mnt/SharedPartition/Documents  /home/john/Documents  none bind 0 0

[LIST=1]
[*]sudo mount -a
[*]You can now sync ~/Documents with Ubuntu One
[/LIST]
[/FONT][/COLOR]


full thread avaliable [here]("http://askubuntu.com/questions/104706/how-to-sync-folders-on-different-partitions-symlink"): 

But I am a beginner and I don't fully understand how to implement this could someone please explain in layman's terms how to do this?

Thanks in advance

---

### Post by TheFu on 2014-03-09
It may not be clear, but the commands are listed to run in each line. I would take those each as examples, that you should modify for your specific situation (mainly just the userid and paths), not the commands.  The UUID= line after #4 probably has errors, but I cannot tell, for certain.

```
mkdir ~/Documents
sudo mkdir -p /mnt/SharedPartition
blkid

```
 Edit the /etc/fstab and use the UUID found above as the deviceID. This is where you mount the storage to /mnt/SharedPartition. There are lots and of examples on the internet and there are a few inside the current fstab ON YOUR MACHINE.  The following lines are close - add them, to the bottom of the fstab and tweak it for your values. 
```
UUID=4B38-4ED2 /mnt/SharedPartition vfat auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 2
/mnt/SharedPartition/Documents /home/john/Documents none bind 0 0
```

Then run
```

    sudo mount -a

```
Which will mount those new places where they are specified.  At reboot, those same places will be mounted automatically, so make certain the drives are connected.  You can now sync ~/Documents with Ubuntu One

To learn about each command, use the **man** command. A bind mount is non-trivial, but those instructions are the best I've seen.
**man mount ** to learn about mount.
**man fstab** to learn about the fstab.  You get the idea.

---

### Post by LinuxVirgin2000 on 2014-03-11
Hi, thank you very much for the reply, I appreciate your help.

Ok I think I get most of it now but something is still not working. heres what I did:


Firstly I already have a documents folder in my home so running > [COLOR=#000000][FONT=Ubuntu Mono]mkdir ~/Documents[/FONT][/COLOR] didn't do anything
I ran: > [COLOR=#000000][FONT=Ubuntu Mono]sudo mkdir -p /mnt/SharedPartition[/FONT][/COLOR] and it worked, a folder called SharedPartition was made in /mnt (my partition has the same name as the example)
I ran: > [COLOR=#000000][FONT=Ubuntu Mono]blkid[/FONT][/COLOR] and nothing happened so I just took a random guess an ran  > [COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]blkid[/FONT][/COLOR] and it worked! (think i'm starting to finally understand how this terminal thing works!)

the next bit was where I started getting trouble

I ran:

> UUID=0BB932465B7C09DC /mnt/SharedPartition ntfs auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 2/mnt/SharedPartition/Documents /home/Deepak/Documents none bind 0 0

Note: all I changed from the example was the UUID, my username (Deepak) and I also changed "vFat" to "ntfs" everything else I left the same because I don't know what it means

the following message came up:
> bash: /mnt/SharedPartition: Is a directory

i did continue with the instructions just to see if it worked anyways and rebooted but it did not

please could you advise what I should do next to try and rectify this problem?

Thanks for all your help so far!

---

### Post by TheFu on 2014-03-11
Close ... but both those lines have errors.

> UUID=0BB932465B7C09DC /mnt/SharedPartition ntfs auto,users,uid=1000,gid=100,dmask=027,fmask=137,ut f8 0 2/mnt/SharedPartition/Documents /home/Deepak/Documents none bind 0 0 
looks incorrect to me.  There is a space "ut f8" ---> "utf8".  That single space MATTERS!!!!!!

The second line needs to refer to the mount point from the first line.  "/Documents" points nowhere.  It needs to be /mnt/SharedPartition. If you didn't break the lines correctly, neither line will work inside the fstab file.  It has a specific format and if that is NOT followed, it breaks.

Without seeing your passwd and groups files ... I cannot validate the uid/gid numbers. Those need to point to the matching numbers in those files for the userids and groupids setup.

Rebooting doesn't do anything different than "sudo mount -a".

BTW, I didn't need sudo on my system for blkid to work. Good job solving that.

---

