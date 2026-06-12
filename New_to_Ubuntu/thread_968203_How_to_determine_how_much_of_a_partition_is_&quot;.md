---
title: "How to determine how much of a partition is &quot;used&quot;"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-02
When I installed Gutsy onto a virgin hard drive, I let the partitions come as the Install wanted. Therefore, / (root) also had /home in it's (root) partition. Last week, I've put /home on it's own partition (see below it's called: sda3). I now have a / (sda1) partition of over 78 GIG. I want to shrink it to 15 gig and expand the /home to 63 gig **more** than it's current size of 231 gig.

I loaded GParted LiveCD and tried to shrink sda1, but as it currently has 75 of 78 gig "in use", it wouldn't shrink more than the 3 gig free there. So I stopped and didn't do the: re-size/move. 

I want to know how much of sda1 is in use, now that /home is moved to sda3. I am desperate to not harm / (root) or /home. I can backup /home to an external usb 80 gig drive. So it can be 'safe'. *Or - does GParted move the data/OS as it 'shrinks' the partition?*

I would do a rm -R /home, but that will delete /home and I'm not wanting that. 

mark@Lexington-19:~$ sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9711    78003576   83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda3            9712       38536   231536812+  83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

mark@Lexington-19:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G   70G  1.7G  98% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  240K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  632K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3             220G   30G  179G  15% /home


I did a search of UbuntuForum.org for keywords: **move, resize, shrink, enlarge**, trying to find a how-to to help. Then I searched the 'net for that, too. I found a very well written How-To at Sourceforge, but it's too technical and complicated, using command line stuff to do the shrinking, etc.

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

I am familiar with GParted and how to run the LiveCD. If you are still reading this and can point me to the best (correct) How-To, I would be grateful.

---

### Post by Elfy on 2008-11-02
Not sure if I'm reading this right but 

you have 75Gb in a 78Gb partition and you are trying to shrink it - if that is what you're trying to do then you have to get rid of data first, that's why it will only let you shrink 3Gb.

Gparted isn't going to actually 'shrink' data - if it does it's gone wrong ;)

You need to move the data from sda1 before you can shrink it.

Edit - if you open a terminal and run this it should tell you size of home 

```
du -sh  ~/
```

---

### Post by Mark_in_Hollywood on 2008-11-02
mark@Lexington-19:~$ du -sh  ~/
30G	/home/mark/

If /home/mark has 30G (gig?) in it, what is in the partition sda3? I guess I'm asking if I now have "duplicates" of /home. One would be in /home and another in some partition? (where it should be)

---

### Post by Elfy on 2008-11-02
Have you physically moved home then from sda1 if you have it's a case of finding what is in root that is taking up so much room.

I think I read your post as having 2 /homes - 1 in / still - you can out any path you like in and it will tell you 

du -sh /etc/ for instance

You're definitely mounting home from where you expect, but is there another home in 
/ - maybe check with baobab or even nautilus 

I'm a bit confused as to what you are trying to do - if I was looking to resize / I would be looking at what was taking up the space. I don't know how you moved home from sda1 to sda3 and whether it was just copied or actually moved.

Whatever you do I suggest that you make a backup of your current /home

---

### Post by Elfy on 2008-11-02
<snip>

---

### Post by Elfy on 2008-11-02
<snip>

---

### Post by Mark_in_Hollywood on 2008-11-02
mark@Lexington-19:~$ du -sh /home
du: cannot read directory `/home/lost+found': Permission denied
30G	/home
mark@Lexington-19:~$ sudo du -sh /home/mark
du: cannot access `/home/mark/.gvfs': Permission denied

Help!!!!!!!

I had installed the OS. It had set up / and /home was part of sda1. Using the Psychocats "Put /home on a separate partition",

Create a separate home partition in Ubuntu
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

GParted created sda3 for (what was to become) /home. Following the 'cats how-to, I believe I removed /home after the data was moved from sda1 to sda3. (sudo rm -rf /home_backup)

Why sda1 shows as 78 gig is beyond me. If I'm not communicating it's because I'm "beyond me". I'm guessing that the absolute max size of the sda1 **in use** is below 15 gig, the remainder is "unused" space.

---

### Post by Elfy on 2008-11-02
I suggest that you use baobab to get a better idea of what is going on - bear in mind that it's not the most accurate of file sizes I think, you should though be able to find what is taking up the space

What happened to the backup you made did yopu get rid of it or is it still kicking about, check your trash and roots to see if there is anything in there - not forgetting that a hidden folder/file in trash will still be hidden.

---

### Post by Mark_in_Hollywood on 2008-11-02
/home was first copied to an 80 gig external usb drive. When that was done, the usb cable was removed from the 'puter. Next, I under a LiveCD, and with the primary-master drive "UN-mounted", I ran the commands per Psychocats How-to.

I'm attaching a screenshot of what baobab showed, hoping it will help.

---

### Post by Elfy on 2008-11-03
If you run the livecd again then the possible 2 homes won't be mounted so you should be able to distinguish between them and see what's going on. You caould also post a screenshot of gparted please.

Did you check the trashs'?

You need to open /home in baobab and see what is there, it odes look ok though

---

### Post by Mark_in_Hollywood on 2008-11-03
How will seeing GParted's partitions help me know what to do with sda1? 

Yes, both my local trash and root's trash have been emptied.

When I 

gksudo nautilus

I see my 

home 

folder. It no longer has the icon attached to it. If it's the /home that remains in sda1, how do I find the /home in sda3?

---

### Post by Elfy on 2008-11-03
Your home is the one that you made on sda3

/dev/sda3 220G 30G 179G 15% /home

You need to be checking first that you got rid of the backup home you made as part of the psychocat tut - 

I'm not sure what is going on with the files - babobab only shows root taking 33.4Gb - which given a ~30Gb home is about right.

Did you check the trash for hidden files?

Not sure where to go tbh - have a look here, there are a ferw commands there you can use

[http://ohioloco.ubuntuforums.org/showthread.php?t=898573](http://ohioloco.ubuntuforums.org/showthread.php?t=898573)

---

### Post by Mark_in_Hollywood on 2008-11-03
> **forestpixie said:**
> Your home is the one that you made on sda3

/dev/sda3 220G 30G 179G 15% /home

You need to be checking first that you got rid of the backup home you made as part of the psychocat tut - 

I'm not sure what is going on with the files - babobab only shows root taking 33.4Gb - which given a ~30Gb home is about right.

Did you check the trash for hidden files?

Not sure where to go tbh - have a look here, there are a ferw commands there you can use

[http://ohioloco.ubuntuforums.org/showthread.php?t=898573](http://ohioloco.ubuntuforums.org/showthread.php?t=898573)

From my previous post, immediately prior to this one:


"Yes, both my local trash and root's trash have been emptied."

At this point in time, I feel as though I cannot communicate my problem. I guess I'm either too nerdy or not nerdy enough. Doesn't matter. The purpose of this post is to get some help in checking whether the "old" /home in my sda1 is still there or not. Whether the new /home is in (or 'on') sda3.

So for now, I'm quitting this post.

Thank you, community.

---

