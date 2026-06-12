---
title: "which folders are in which partition?"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by pjstock on 2012-03-28
I am trying to cleanup a little laptop here which only has only a single 35Gb HDD total.

I seem to have defined my boot partition (is that the correct terminology?) a little on the small size. 6.5G and not surprisingly some 94% of it is used.

But I think I can finesse it (until I can Live boot and increase the boot partition size) if I can just clean it up a bit. I expect some user generated files have probably drifted into that sda1 partition that I could move over to sda6 or onto an external drive as has been suggested. 

How though do I determine which folders (when I look at say COMPUTER or FILE SYSTEM) are sitting on the sda1 (these are the ones I would look through and cleanup manually) and which are on sda6 (the 23G data side that does at least have about 5Gb still free.)

The DF-h command shows the following:

peter@peterx300:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 6.5G 5.7G 408M 94% /
none 300M 652K 300M 1% /dev
none 307M 1.2M 306M 1% /dev/shm
none 307M 420K 306M 1% /var/run
none 307M 0 307M 0% /var/lock
/dev/sda6 29G 23G 5.2G 82% /media/28a27f7c-83ff-4415-b9c5-7734f03be244


Peter

---

### Post by Paqman on 2012-03-28
It looks like  /media/28a27f7c-83ff-4415-b9c5-7734f03be244 is located on sda6, and everything else is on sda1. Which leaves the question what are sda2-5 doing? One might be an extended partition and one will be swap, but that still leave s acouple unaccounted for. Any idea?

Some quick ways to free space on your root partition:

Remove all your old kernels. They're about 100MB each, so take up a lot of space. Then:
```
sudo apt-get autoremove
```
This removes all packages you no longer require to satsify dependencies. Then:
```
sudo apt-get clean
```
Which dumps the whole package cache. Obviously clear out you trash, and if you want to go further clearing out space, install [bleachbit]("apt:bleachbit") and let it clear out some of the caches (eg: browser, thumbnails, etc).

---

### Post by pjstock on 2012-03-28
Thank you. I'll do this.
But I still expect there are some user (me) generated files stuck on sda1 (like audio files or photos or the like) which are either duplicates and can be deleted or can be as well stored on the remaining 5Gb of sda6.

But I have no clue what happened to sda2-5. I expect I might see that when I run GParted from LIVE (though I guess I can run GParted now just to have a look.)

Here's what I see in Gparted.

see anything interesting? (it's mostly Greek to me.)

what I would like to know is how I examine the folders that make up sda1 the 6.53Gb so that I can search around for any of these user generated excess files.

---

### Post by solocommand on 2012-03-28
To me, it looks like /media/28a27f7c-83ff-4415-b9c5-7734f03be244 is the only folder located on /dev/sda2. That means everything except that location would be pointing to /dev/sda1.

---

### Post by Paqman on 2012-03-28
> **pjstock said:**
> Here's what I see in Gparted.

see anything interesting? (it's mostly Greek to me.)


Nope. Probably you used to sda3-4 but they were deleted.

> 
what I would like to know is how I examine the folders that make up sda1 the 6.53Gb so that I can search around for any of these user generated excess files.

Disk Usage Analyser will show you. Collapse everything in your  /media/28a27f7c-83ff-4415-b9c5-7734f03be244, and take a look in /home/username (which is on sda1). That's your home folder and it's where everything downloads to or is stored in by default. It also contains all your user-specific settings, caches, etc.

---

### Post by oldfred on 2012-03-28
Your media partition looks like it has a lot of typical files from /home including some of the hidden files & folders. Did you just copy all of /home to media? If so and data still in /home may be in your media folder. But if you have updated, the default save location is normally in /home so you should sync the folders again before deleting.

If system is running ok, you can delete old log files.
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz


Some tools to look for duplicates:
FSlint is a toolkit to clean filesystem lint, like duplicate files, badly named paths, and broken symlinks for example. It includes a GUI as well as a command line interface. 
 
Meld diff Viewer

---

