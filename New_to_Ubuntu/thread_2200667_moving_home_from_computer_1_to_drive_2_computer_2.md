---
title: "moving home from computer 1 to drive 2 computer 2"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-20
I have a dual boot with 12.04 system on SSD and Win 8 system on HDD on a newish HP computer.

Yesterday I  put a tarball of /home/user (minus hidden files) from another, older 12.04 computer onto the new computer, but:

Places/Home shows it as a 14.6Gb tarball file dated Jan 19 with a last mod time of 08:43, plus

in Places/FileSystem/ mnt/newhome, I see a file of the exact same name, but it shows as a 4.0Gb file with same date but a last mod time of 07:12. Whether I tried to make a tarball earlier (i.e. at 7:12) and it failed to complete, I cannot remember.

Both are uncompressed.

Unfortunately yesterday was a long day of trying to solve some network problems and my memory of exactly what I did early in the day is scrambled eggs. I think what I did was to assign/mount sda6 (on the HDD of newcomputer) to mnt/newhome (which I can now see in gparted).  I trust it is safe to assume that these two tarballs are different files, but please correct me if not.

Anyway my plan today is to move the larger tarball to newhome (replacing the smaller file) and unzip it as there is insufficient room on the 20GB system home partition on the SSD for the long term.

The sda6 is over 400Gb and that is where I plan to mount /home for this computer, but I am having a very difficult time getting my head around exactly what mount points are and how to place the tarball so that it unzips into /home/user correctly.

If I have it correctly, and I will appreciate confirmation or correction:

1) /mnt/newhome is simply the pointer that system uses to find sda6
and that it (i.e., the mount point) takes up negligible space on the system partition

2) by causing sda6 to become /home (see below) and then replacing the earlier tarball with the later, larger tarball, in /home/user and unzipping it, the files will be in the right place for the new computer to function the way  I expect (i.e., the way it does now, except with all of the files from oldcomputer added to the existing files now in /home/user. 

Finally I am quite inexperienced with the terminal and don't see to be able to find sda6. I can see sda1 and sda2 in /dev but not sda.

Using:
```
locate tarball
```

shows instances of the file at:
/home/user,  and another at:
/mnt/newhome

If my assumption about /newhome being a pointer, this makes sense. And projecting from that, to use the terminal I simply address the sda6 partition by referring to /mnt/newhome until such time as sda6 becomes /home.

Finally, looking at the locate output, it appears that at this stage Ubuntu doesn't know that sda6 should be /home, and I do not know how to make it /home, and when in the above process I should do so.

I hope this isn't as confusing as I am confused, but my familiarity with file structure and the shell is primitive. Any clarification/guidance will be much appreciated.

---

### Post by oldfred on 2014-01-20
This shows the steps to move /home. You have added the extra step of a tarball. 
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
But do you really want to create a new /home or perhaps a data partition may be better?
I actually leave /home inside / (root) and link folders from my data partition(s) into /home.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Jason_Gibson on 2014-01-20
> [COLOR=#000000]I actually leave /home inside / (root) and link folders from my data partition(s) into /home.[/COLOR]

I have been doing a separate home partition and just leaving it alone with reinstalls but this sounds like a much better idea. I will do this on my next rebuild for sure. Could you also do this with wine folder and virtual box folder? put them on other partition and just link to home?

---

### Post by Odyssey1942 on 2014-01-20
> But do you really want to create a new /home or perhaps a data partition may be better?
I actually leave /home inside / (root) and link folders from my data partition(s) into /home.

Sometimes a reply causes the penny to drop. Yours hit squarely on my confusion in all this, and also made me realize that I may have already past the point of doing what I intended to do.

When I installed 12.04 on the SSD, I made one 20Gb partition as system, one 20Gb partition as /home and left the other 20Gb partition unused, but formatted all as EXT4. My idea was to "move" /home to the hdd (which has a 400GB EXT4 partition for this intended purpose), but I am now unsure if I can do that. Would I have to have done that at the time of installing Ubuntu, or is this something that I can still do?

If not, it looks as though your preferred approach is the only option available to me now without going through the install again (which is simple, but the configuration that follows is very time-consuming)? And if your preferred approach is taken, how does one
> link folders from my data partition(s) into /home?

OTOH, if it is still something that I can do, my original plan, after moving /home to the HDD, was to have the two remaining EXT4 partitions on the SSD available for later versions of Ubuntu, or for trying out Mint or whatever, and having them all point to the same 400Gb /home so that if I actually use one of the trial installs and change any data, I will have it in the same place I would had I made the change in 12.04. I am assuming that by leaving /home inside of / root that I could not do this, but maybe this is incorrect?

Edit: I reread yours and realized that the four links at the bottom were in point. Now reading but have my answer already to my question above about linking.

Now look forward to your reply to the other questions.

---

### Post by oldfred on 2014-01-20
You can move system partitions around at will. Just a lot of technical issues like ownership & permissions. I learned a lot by doing ( and then undoing as I did not want it).

I moved /home to my new drive years ago, but I think I had it configured for only 20 minutes when I found the info on data partitions. Since I was doing multiple installs and already had a shared NTFS with Ubuntu and XP I wanted data shared but not settings from /home. A separate /home can work with one install and upgrading, as software is intended to use old settings and update. But once updated an older version software from another install may then not work. And while some may want similar configuration in the next install, I want to experiment or test something & want to reconfigure anyway.
 
I also moved a /boot once, but again undid it as that cannot be shared either and ended up with a grub only partition. Not now required with grub2, but back with grub legacy it was a good way to multi-boot.

I have not moved .wine from my /home and that is why it is about 2GB as we use the Windows versions of Picasa. I understand that linking .wine does not work very well, but have not reviewed that lately. 
I do also move to folders in my data partitions some normally hidden data files in /home like my Firefox & Thunderbird profiles. My now mostly hidden .files & .folders in /home are 300 to 500MB plus .wine.

If you move system partitions, you have to be very careful to preserve ownership & permissions. If those get messed up it is usually a reinstall. But data in a data partition can just be set to be owned by you or a group and you set permissions similar to /home.

Mounting and mount point is a bit of an issue. In the partition my data folders are at the top level. So from a live installer I have Music, Documents, Video, etc but I mount in /mnt/data and link from that mount into /home. Then my Music folder in /home really is the folder in my data partition. 

My SSD has two installs, and I have few more on my hard drive for tests. And all of them use the same data. With same Firefox & Thunderbird profiles I can use same bookmarks and read the same email, but do have to have every application installed in every install.

---

### Post by Odyssey1942 on 2014-01-20
Perhaps I said something that I did not intend to. I have not thought of moving system partitions at all. The very thought of it makes me tremble.

I am unsure of the extent of the relative advantages/disadvantages of a separate home partition vs linking data to /home. Here is the main benefit as I see it:

With linking, all of your configuration files are in the system in /home while your data files reside elsewhere. So as you might try various installs, each has a properly  configured system. 

Any of the installs can reach the data files and change them as desired without changing a hidden file belonging to another install.

The principal disadvantage that I can see is that each new install must be reconfigured to suit the user. (But this may be offset by not having to deal with issues in  a separate home partition which might result by different installs accessing it. Not very sure about this.)

Is all that correct, and if not, please clarify?

I would also welcome an expansion of the benefits and negatives of this approach vs a separate home partition if OldFred or any one else cares to contribute. I can see this being of interest to every Ubuntu user.

All of this thread is very helpful to me. Thanks.

---

### Post by oldfred on 2014-01-21
Some users have posted that they have shared a /home. But I believe at some point settings will overlap and cause issues. Perhaps if configurations are so different that no settings overlap it will work. For example is one install is Ubuntu and the other Kubuntu, it would expect few if any settings to overlap as GUI is so different.

You can copy all of /home to a new install and have the same settings. But of course then you may have to do double maintenance if you want to try to keep them the same or in sync. But we seem to be finding new versions are enough different that settings may not be the same anyway. 

Some other potential issues. All Debian based use same UID & GID. Fedora changed several versions ago to also be the same.
 Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

 User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

Moving /home is moving a system partition. :)

---

