---
title: "Root Partition Size..."
date: 2012-04-25
forum: New to Ubuntu
---

### Post by luangwa on 2012-04-25
When I installed Lucid I installed the operating files in a 10Gig partition with the idea that it would be easier to do a clean update. I thought the partition size would be large enough for the root. I have blindly installed all files that the update manager suggested. Now the update manager is telling me that I have less than 0.4 Gig of free space. I have remove every program that I haven't opened, games, etc., but this has had little impact on the free space in the root. Is 10 Gig large enough for the root partition or is there program which can clean programs or features that I haven't used the root? 

Thanks for your anticipated assistance.
:confused:

---

### Post by thatguruguy on 2012-04-25
> **luangwa said:**
> When I installed Lucid I installed the operating files in a 10Gig partition with the idea that it would be easier to do a clean update. I thought the partition size would be large enough for the root. I have blindly installed all files that the update manager suggested. Now the update manager is telling me that I have less than 0.4 Gig of free space. I have remove every program that I haven't opened, games, etc., but this has had little impact on the free space in the root. Is 10 Gig large enough for the root partition or is there program which can clean programs or features that I haven't used the root? 

Thanks for your anticipated assistance.
:confused:

Open a terminal and type the following:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
See if that frees up some space.

---

### Post by luangwa on 2012-04-25
> **thatguruguy said:**
> Open a terminal and type the following:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
See if that frees up some space.

Thanks for your suggestion.I tried it and it removed python.

Here are the results:
        Size      Used   Available
Before   9.2G     8.4G     314 M
After    9.2G     8.2G     584 M

I never thought the root would swallow up the space. How could I use Gparted to resize the partition. Right now I have:

Partition   File System  Mount Point   Size   Used  Unused  Flags
/dev/sda1      ext3         /         9.32G   8.28G  1.04G  boot
/dev/sda2      ext2        /home      45.63G  10.83G  34.80G
/dev/sda3      extended               988.37M  ---    ----
  /dev/sda5   linux-swap              988.34m  ---    -----

---

### Post by luangwa on 2012-04-25
Thanks for your suggestion. I tried it and it removed python.

Here are the results:
Size Used Available
Before 9.2G 8.4G 314 M
After 9.2G 8.2G 584 M

I never thought the root would swallow up the space. How could I use Gparted to resize the partition. Right now I have:

Partition File System Mount Point Size Used Unused Flags
/dev/sda1 ext3 / 9.32G 8.28G 1.04G boot
/dev/sda2 ext2 /home 45.63G 10.83G 34.80G
/dev/sda3 extended 988.37M --- ----
/dev/sda5 linux-swap 988.34m --- -----

---

### Post by oldfred on 2012-04-25
I normally suggest 10 to 25GB for root if you have separate /home. My root is 25GB but I have only used 7GB or so with my /home still in root, lots of programs installed, but most data in separate data partitions.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Did you run backups that were copied back into root? I lost a lot of space once when I forgot to mount my /backup partition and it just copied everything into root. 

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by ajgreeny on 2012-04-25
Have a look at the properties of /var/log from a right click of the folder in your filesystem.  It is possible that some problem in the OS somewhere is propagating huge log files, which are growing exponentially, taking all that space.

I have a root partition of 10GB and after 2 years of 10.04 it is still only 4.5GB filled, with 5.5 still available.  I find it hard to believe that you have installed so many packages that your root is full with those, and the figures you have given show that only 270MB was used by the apt cache.

You may also find the disk-usage-analyser is useful for showing which folder is taking all that space.

---

### Post by luangwa on 2012-04-25
Thanks for your responses. I will try your suggestions and let you know what I find. It is getting late. Time for me to hit the sack.

---

### Post by luangwa on 2012-04-26
Thanks for your help. I wasted a day trying to figure out why my root directory needs all that room. My synapses are fried. I decided to run gparted on a CD and shrink /home and expand my root directory. If that doesn't work then I will apply the Old Windows two step "Format and Reload".

Thanks again for your response and suggestions.

---

### Post by Primefalcon on 2012-04-26
What I personally have is 20gb root (only using 8.3) and the rest for /home

and that actualy does me great

---

### Post by paulbuk on 2012-08-03
> **ajgreeny said:**
> Have a look at the properties of /var/log from a right click of the folder in your filesystem.  It is possible that some problem in the OS somewhere is propagating huge log files, which are growing exponentially, taking all that space.

I have a root partition of 10GB and after 2 years of 10.04 it is still only 4.5GB filled, with 5.5 still available.  I find it hard to believe that you have installed so many packages that your root is full with those, and the figures you have given show that only 270MB was used by the apt cache.

You may also find the disk-usage-analyser is useful for showing which folder is taking all that space.

I this evening was working away on my webDev/LAMP box (Ubuntu 11.04) when up POPs the "low disk space.. ony 2Gb left" GASP!!, AMAZEMENT!!. My root is some 82GB I thought, CAN'T BE??!!

Taking the above advice, I looked in var/log only to see actual text logs total some 22GB.....HOLY MOLY!! LOL. I'm about to login as' Root' and delete the whole text offender.
A screenshot is attached.

**Post Script**
It appears that the file is a mail.log. However, I use my Ubuntu 11.04 box a pure LAMP webdev (ie a localhost Apache server for mySQL/Drupal dev etc). I do use it for normal email via Evolution. But at this moment in time, I'm not sure what influences the issue. A posting on Stackexchange has revealed it safe to delete the log (it serves no purpose to me at this moment in time).
Opening the text file for a moment, the data reads a lot about SMTP, so I presume this maybe the culprit (possibly due to my LAMP/Apache server setup!).

Worth bearing in mind folks. More *nix knowledge gained me thinks and now further away from old M$ tehe,

PB, Lancs.

---

### Post by paulbuk on 2012-08-03
I deleted all the old logs (by date) by logging in as "root", clearing the trash and then rebooting. I now have 60GB free in root where as before it was on 2Gb free.
(FYI, my "Root" is a partition on a 500Gb physical,; "Home" is a second partition, this stems from a physical HD upgrade earlier in the year by which I 'cloned' the old 82Gb drive).

Attached is an after screenshot (my other drives are not showing on this screenshot but they weren't affected by the issue).
Hope that helps.

PB

---

### Post by Cheesemill on 2012-08-04
For the last 2 posters, just deleting your log files isn't a solution. You're just going to have the same problem over and over until you figure out *why* your logs are becoming so large.

Log files are there for a reason, one of these is to warn you of any abnormal behaviour going on so that you can fix it. Log files of that size are a sure sign that there is something wrong with your setup.

---

