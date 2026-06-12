---
title: "Cloning and Partitions with Ubuntu"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by benbrockn on 2012-11-21
Hey, I was wanting to partition my Hard drive, but want to keep my data and ubuntu system separate, but I will have multiple users (3-4 users). I assume /home will house my data (which will be shared between all users, if this is not the case with /home, please correct me) but where will our user profiles be located? in /home or /usr or elsewhere?

I was asking so that I can clone my / directory but I also want the image file to include user profiles (but not my data).

This is in case of system corruption or if I just wanted to use the cloned image for a different computer system.

I would like to know where the user profiles are stored though, that way if I want to update my cloned image I could save the user profile data, wipe the partition, re-image it from the clone, and then update the older user profiles.
-----------------------------------------------
BONUS Question: If I encrypt the entire /home folder for better security, can my other users read from it? And can I easily move files between it and a external HD?

Thanks for your help!

---

### Post by Mr_JMM on 2012-11-21
user direcotories and their data such as Documents, Pictures and some application settings are stored in the /home directory (partition if separate).

For example, for a user jimmy and jenny:
jimmy = /home/jimmy
jenny = /home/jenny

Jimmy's /home directory and data is not shared (by default) with Jenny's, neither are any application settings including Unity desktop.

---

### Post by CharlesA on 2012-11-22
> **benbrockn said:**
> 
BONUS Question: If I encrypt the entire /home folder for better security, can my other users read from it? And can I easily move files between it and a external HD?

The only way they could read your data was if they knew the passphrase.

As far as I know you can encrypt your home directory during installation, but I am not sure if you can do it post install (but I'm sure it is possible).

---

### Post by benbrockn on 2012-11-22
Hmm...

This is a tough decision. I know that if I separate /home from /, I would be able to keep my data (I should say our data since it is a combo of mine and my wife's) separate, but this would exclude user profiles from the main root partition.

If I leave /home in root, and store our data in a separate partition, I know she would just put her pics and videos, and music in her /home directory and defeat the purpose.

Is there any way at all to separate the user profiles from /home in a separate directory or Partition maybe? Or any way to disable the pictures/video/music/ etc folders from home or rather, make them shortcuts to a separate data partition?

I want to keep root as small as possible for quick cloning/upgrading (max 20 GB) and not clone our data (I have 1 TB of random junk that doesn't need to be cloned).

--------------

As for encryption, yes I was thinking of encrypting /home from a fresh install, but I may not now until I get the former issues resolved.

---

### Post by Paqman on 2012-11-22
> **benbrockn said:**
> this would exclude user profiles from the main root partition.

Is that a big problem? Many people deliberately set their system up to separate /home from /, so that they can reinstall over the top of / and leave the user profiles untouched.

> Or any way to disable the pictures/video/music/ etc folders from home or rather, make them shortcuts to a separate data partition?

Yep, you can easily link the various folder in a user's home to another location. When she clicks on "Pictures" in her home folder she would actually go to wherever you choose to link to. 

> 
I want to keep root as small as possible for quick cloning/upgrading (max 20 GB)

20GB is pretty big for a root partition. A clean install is under 5GB IIRC, and you'd need to install a *lot* of stuff to even get near 10GB (Linux is very efficient about sharing libraries between apps, so it doesn't bloat as much as Windows). The main advantage of having spare space in your root partition is so that the system can create big temp files in /tmp if you're doing something like authoring a DVD that creates GB-sized temp files.

---

### Post by benbrockn on 2012-11-22
@Paqman

> 20GB is pretty big for a root partition...The main advantage of having spare space in your root partition is so  that the system can create big temp files in /tmp if you're doing  something like authoring a DVD that creates GB-sized temp files. 

I would be encoding dvds, audio, etc. How big do you think I should go for root then? Between 10-20GB?

And as with your suggestions, I will probably set up my HD like this:


[LIST]
[*]root
[*]swap
[*]/home (with picture/music/vid/etc folders linked to Data)
[*]data (ext4)
[/LIST]

I think this is a good setup, what does everyone else think? If I do this, how big should I make the /home?

Also, I know there is the big debate on how big swap space should be and I've read several articles on each side. If I have 6GB RAM (laptop) and 4GB RAM (desktop) I was thinking 2GB of swap for both. (but I will NOT use hibernation on either).

Let's say I just have 600GB of hard-drive space for both, what would be good for root, swap, and /home with the remaining going on Data?

---

### Post by Paqman on 2012-11-22
> **benbrockn said:**
> 
I would be encoding dvds, audio, etc. How big do you think I should go for root then? Between 10-20GB?

20GB would be a good conservative amount, 15GB would almost undoubtedly be fine too.


> [LIST]
[*]root
[*]swap
[*]/home (with picture/music/vid/etc folders linked to Data)
[*]data (ext4)
[/LIST]

I think this is a good setup, what does everyone else think? If I do this, how big should I make the /home?

Looks fine. How big home is depends on how much data you'll have there. Besides config files you'll also have caches and such.

However, if you're looking to keep /home as minimalist as possible, is there much point in having it on a partition? If it's only config files and such then it would be really easy to back up if you needed to reinstall. You'd get it all onto a cheap USB stick that you've probably got kicking around in a drawer.

> Also, I know there is the big debate on how big swap space should be and I've read several articles on each side. If I have 6GB RAM (laptop) and 4GB RAM (desktop) I was thinking 2GB of swap for both. (but I will NOT use hibernation on either).

You have heaps of RAM, so your machines probably won't use swap much. Personally I use a 512MB swap file on my root partition. I don't think there's any need for you to have a swap bigger than 1GB, whether it's a file or a partition.

> 
Let's say I just have 600GB of hard-drive space for both, what would be good for root, swap, and /home with the remaining going on Data?

/ = 20GB
swap = 1GB
/home = 20GB (just in case someone or something puts data there)
/data = everything else

Don't sweat about getting it perfect. You can always change the sizes afterwards (although it can be very slow to change large partitions).

---

### Post by benbrockn on 2012-11-22
> Looks fine. How big home is depends on how much data you'll have there. Besides config files you'll also have caches and such.

Yeah, I do want /home to be minimalist but if cache files are/could be located there I want to play it safe.

I think this model looks good. And yeah I want to try to plan it out perfect, because I have done this before on windows and linux and it is such a pain formatting everything and customizing it, and when done find out that C: or root needs more space.

Thanks for your help!

---

### Post by benbrockn on 2012-11-22
Other than the user's config file, you also mentioned cache and other stuff. I do not currently have Ubuntu with me so I can't look at it myself. Define "other stuff".

Is there a way (and if so could you show me it) how to send the user's cache files and any other files of significant size to another location?

I would be set then! I really only want user config data in /Home (if this is even possible). **[I'm assuming that the entire user profile is only compromised of the user's config file, please correct me if I'm wrong, but this is what I gathered from earlier posts]**

This is what I'll do:


[LIST]
[*]/ (20GB ext4)
[*]swap (1 GB)
[*]/home (5-10GB ext4 with all docs/photos/music/vids/etc linked to Data, and all cache sent to /)
[*]Data (~5XXGB ext4)
[/LIST]
Or if cache/other files cannot be linked elsewhere (or if this is proving difficult) then I'll do this:


[LIST]
[*]/ (20GB ext4 with all docs/photos/music/vids/etc linked to Data)
[*]swap (1 GB)
[*]Data (~5XXGB ext4 with user profiles backed up here)
[/LIST]

---

### Post by Paqman on 2012-11-23
> **benbrockn said:**
> Other than the user's config file, you also mentioned cache and other stuff. I do not currently have Ubuntu with me so I can't look at it myself. Define "other stuff".

All sorts of bits and pieces. Settings for individual apps. The whole contents of their Ubuntu One (ie: files, music, etc). Plus databases. Essentially anything that's specific to a user rather than the system itself.

If they use Wine then their home folder will also contain an entire fake Windows directory structure (ie: C:\ drive) including the entirety of any Windows apps they install (but not including Windows system files, obviously). If they install a few chunky Windows apps this can get pretty massive.

> Is there a way (and if so could you show me it) how to send the user's cache files and any other files of significant size to another location?

That would start getting pretty fiddly, and would have to be done for every single app that has a cache. So a fair bit of work to set up and maintain. Essentially however in Linux is completely possible to link any location on a filesystem to any other location.

You can create a symlink in the file manager using Edit > Make link, or you can hold CTRL-SHIFT and drag it to the new location. Multiple tabs are handy for the latter.

> **[I'm assuming that the entire user profile is only compromised of the user's config file, please correct me if I'm wrong, but this is what I gathered from earlier posts]**


It's composed of heaps and heaps of little config files. Conceptually Linux isn't a single system, it's a highly modular collection of little programs all cooperating. So each wee component will have it's own config file.

---

### Post by oldfred on 2012-11-23
If you in Nautilus turn on show hidden files/folders you will see lots of the configurations, but most do not take much space. Some applications like Firefox & Thunderbird store all there data in the . or hidden folders.

I keep /home inside / (root) and link all my data back into /. I use 25B for most / partitions, but actually use about 9GB. My /home is 2GB (of the 9GB) and 75% of that is .wine as I install the Windows version of Picasa and wine is more difficult to move.

Having two different users and setting permissions for each and shared makes it a bit more complicated & I do not know details.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

I jsut use links, but some prefer bind or bindfs.
       HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472) 
       
 Advantages of bind post 16 - Morbius1
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

     I have two data partitions. One still is NTFS from when I dual booted XP and I have not moved that into my Linux partition, yet. I have my Firefox & Thunderbird profiles in the NTFS so I could have the same data in XP & all my Ubuntu installs. I also move some other hidden folders with data to my LInux formated data partition. 

You will probably need to plan partitions or folders ownership & permissions, so you can separate your accounts and share some.

Some posts from those that really understand ownership & permissions with multiple users.
       Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

---

### Post by newb85 on 2012-11-23
+1 to Paqman's suggestion of symlinks.  If your goal is to keep your users' profiles on the / partition and the data (documents, pictures, music, etc.) on a separate partition, you could do this:

Leave /home as part of the / partition.
Create a /data partition.  In /data, create two directories, one for you and one for your wife.  Change the ownership of those two directories to the corresponding users.  Within those two directories, create directories corresponding to each of the non-hidden directories in the user's home directory.
Replace the non-hidden directories within the users' home directories with symlinks to the corresponding directories on the /data partition.

Thus, it will look like your wife is saving things to her home directory, and in reality, it will be stored on the /data directory.

---

