---
title: "Dual Boot Instal - Won't see NTFS Partition"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by TechieJustin on 2012-10-30
I have a 1TB drive, shrunk the Windows 7 (64 bit) so it only takes up part of the drive, the rest is free space.  When I entered the install for Ubuntu, I chose "something else" but the entire drive shows up as free space.
What happened?
I attached two screen shots showing my partition resize in Windows and the Ubuntu install.
Both OSes are the 64 bit versions.

---

### Post by oldfred on 2012-10-30
Was drive ever in a RAID configuration or was drive partitioned with gpt (and maybe UEFI) before.

RAID leaves meta-data on a drive and gparted will not formated RAID drives. You can remove meta-data.

If running RAID do not run these commands or you will destroy RAID configuration.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

If drive was gpt and you install Windows in BIOS mode, it reformats to MBR partitioning. But only deletes the primary gpt partition table. gpt has a backup table which Linux tools see and get confused if drive is gpt or MBR.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by TechieJustin on 2012-10-31
Yes at one time the drive was in a RAID-1 config.  Not anymore.
I only have sda.
 
If I had completely wiped the drive with something like DBAN before I installed WIndows, would this have been avoided?

---

### Post by oldfred on 2012-10-31
If you totally erased drive I think that would also prevent the issue, but you can just run the dmraid command now and fix it.

---

### Post by TechieJustin on 2012-10-31
I understand.  I just wanted to make sure I grasped what went wrong.  When I get home I'll try your suggestion.  Thanks!
 
J

---

### Post by TechieJustin on 2012-10-31
> **oldfred said:**
> If you totally erased drive I think that would also prevent the issue, but you can just run the dmraid command now and fix it.
 
 
the first command I tried, it said there are no RAID volumes with that name.
ThIs there a live CD that has fixparts installed?  I tried using apt-get to install fixparts but it said I needed to enable universe.  Not sure how to do that on the liveCD.

---

### Post by oldfred on 2012-10-31
Fixparts is not in the repository. You just go a standard error message when first not found.

Just download from the rodbooks site. Actually it links here:

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

You want the .deb for either 32 or 64 bit version that you have installed.

---

### Post by TechieJustin on 2012-10-31
thanks, once I boot into the Ubuntu live/install CD how do I install this deb file?

---

### Post by oldfred on 2012-10-31
Remember where you downloaded it. Double click on the .deb which should open Software Center & let you install. It did give me an error, but installed.

```
fred@fred-Precise:~$ sudo fixparts
[sudo] password for fred: 
FixParts 0.8.1
Type device filename, or press <Enter> to exit: /dev/sda

Loading MBR data from /dev/sda

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): 

```

---

### Post by TechieJustin on 2012-11-02
It worked!  thanks!
I used the "install Ubuntu alongside" rather than the 'create your own' option.  It seems to have done what I wanted anyway, put Ubuntu on the second partition.

Now I have to get rid of Unity and go back to a normal Gnome desktop...

---

### Post by oldfred on 2012-11-02
If you want gnome panel or fallback (samething in 12.04).

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) - kansasnoob
# for gnome2 prior to 12.04
sudo apt-get install gnome-session-fallback
# this is same as fallback but based on gnome3 for 12.04 or later
sudo apt-get install gnome-panel
sudo apt-get install gnome-tweak-tool
sudo apt-get install indicator-applet indicator-applet-session

---

