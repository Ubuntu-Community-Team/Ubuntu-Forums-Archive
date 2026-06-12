---
title: "Why is my / partition full w/ 10 gigs again?!"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by t-molli on 2008-05-14
Ok, what the hell !? This is the second time I've installed 8.04 using two partitions; / and /home. I give / 10 gigs and the rest to /home.

When I'm done installing, I'm around 2.5-3.0 gigs for /. Then, sometime between then and now (just double checked the size again) I end up with a full / partition that says it's 100% full.

I'm not a noob at this, but can't figure out where the extra files are. I install a few applications, but nothing large. Then I copy/paste all my folders to the /home partition. That should not be affecting my / partition.

Has this happened to anyone else?

I've looked in the trash and nothing is there anymore.

Man, I don't want to install this OS for a third time in 12 hours....

anyone got any ideas what's going on?

---

### Post by mkoehler on 2008-05-14
My best guess is that you aren't getting all of the files when you install items.  For example, if you install something under synaptic, items get tossed in various locations on your / partition.  In order to see where all of the files went, you can right click on the package in synaptic, click properties, then click on the "Installed Files" tab.  Additionally, various programs (synaptic, firefox, etc) download files into the /tmp directory which, of course, gets emptied when you log out, but the files remain until that point in time.  If I had to guess, these would be the reasons that your hard drive partition is filling up.  If you don't think this is the case, then you can run the "find" command with the "-newer" option to find files that are newer than a given file.

---

### Post by mr-Kirch on 2008-05-14
I actually install a lot of stuff just to get more memory and there packages i don't even use.

---

### Post by t-molli on 2008-05-14
> **mr-Kirch said:**
> I actually install a lot of stuff just to get more memory and there packages i don't even use.

what?

---

### Post by anjilslaire on 2008-05-14
Clean your update debs and then remove any orphaned packages:
```

sudo apt-get clean
sudo apt-get autoremove

```

---

### Post by t-molli on 2008-05-14
> **mkoehler said:**
> My best guess is that you aren't getting all of the files when you install items.  For example, if you install something under synaptic, items get tossed in various locations on your / partition.  In order to see where all of the files went, you can right click on the package in synaptic, click properties, then click on the "Installed Files" tab.  Additionally, various programs (synaptic, firefox, etc) download files into the /tmp directory which, of course, gets emptied when you log out, but the files remain until that point in time.  If I had to guess, these would be the reasons that your hard drive partition is filling up.  If you don't think this is the case, then you can run the "find" command with the "-newer" option to find files that are newer than a given file.

/tmp has almost nothing in it and I only install at the very beginning of installation. After that install of all programs, I was only at 2.5 gigs for my / partition. Where the other 7 gigs is at I can't find it. It's almost like it's seeing my /home partition in the / partition, but the are separate partitions; one being sda2 and the other sda3.

Never had this problem with 7.10 :confused:

---

### Post by wirelessmonkey on 2008-05-14
post the output of:
 df

and 

cat /etc/fstab

---

### Post by t-molli on 2008-05-14
> **wirelessmonkey said:**
> post the output of:
 df

and 

cat /etc/fstab


The output of df is that / is full, 100%, nada left.

The out put of fstab is it's sda2 like I mentioned above.

Like I said above guys; I'm not a complete newb. I've installed and setup 7.10 probably 50+ times on different machines. Something weird is going on here when I install 8.04. The only connection I can make is that it's filling up somewhere right around the time I start copying/pasting folders/files from my back-up drive to sda3 (/home). But, as I mentioned before - sda3 (/home) is a separate partition and therefore doesn't have anything to do with the capacity of /, which is also shown correctly using 'df -h'

Now here's where I might be a newb. I remember copying a folder from back-up drive to sda3 (/home), but forgot that the 3 large files required sudo to move. So, it came up with an error and I simply clicked on cancel. I would think those three large files would simply not have copied at all, but is it possible they've been put in some folder I'm not aware of???? I looked in all the trash cans I could find...

Any other ideas? Thanks again.

---

### Post by anjilslaire on 2008-05-14
Did you do a clean & autoremove as I mentioned above?

Othwise, start at "/" and check the properties of each folder to see what is abnormally large. Be sure to turn on visibility for hidden folders. Tedious, but effective...

Update:
/usr/ is my largest non-/home/ directory

---

### Post by HotShotDJ on 2008-05-15
> **t-molli said:**
> When I'm done installing, I'm around 2.5-3.0 gigs for /. Then, sometime between then and now (just double checked the size again) I end up with a full / partition that says it's 100% fullIn my experience, with this type of thing, something in /var is the culprit -- and it is almost always /var/log/*  -- so that is where I would start looking.

---

### Post by teslarage on 2008-05-15
> **anjilslaire said:**
> Clean your update debs and then remove any orphaned packages:
```

sudo apt-get clean
sudo apt-get autoremove

```

This should work. Have you tried this?

---

### Post by wt8008 on 2008-05-15
Try using some utilities to help you track out the offending directories

You can try du [http://en.wikipedia.org/wiki/Du_(Unix](http://en.wikipedia.org/wiki/Du_(Unix))

I also have used a Java program called JDiskReport [http://www.jgoodies.com/freeware/jdiskreport/](http://www.jgoodies.com/freeware/jdiskreport/) Get the java version, extract the jar file out of the zip file and you can run it by

```
java -jar jdiskreport-1.3.0.jar
```

The program will tally up the size of each folder and display the results graphically.

---

### Post by t-molli on 2008-05-15
Thanks everyone... sorry for the late reply, but last night I was trying to find a connection in the .gvfs folder located in /home. I saw something about it being a problem, so was trying to remove it. Doing that somehow effected my network and I was done with the Internet.

I re-installed again today and have been monitoring the capacity of / with each upgrade, install, copy/paste, etc., etc. I now have my system fully updated, restricted drivers are in place, installed all my apps., and copied all my stuff from a back-up drive. With that all said, my / partition is 29% full at 2.6 gigs. This is good. However, I'm noticing a connection again between sda2 (/) and sda3 (/home) in that when I do a 'df' in terminal I can see the .gvfs in /home is the exact same size as above for /. 

What is the connection with .gvfs in /home and the / partition?

Try it for yourself. Do a 'df' command in terminal and see if you .gvfs is the exact same size as / in sda2.

---

### Post by Paqman on 2008-05-15
The disk usage analyser should point out what folders are at fault pretty quickly.

One thing to watch out for is backup programs like sbackup. By default they might be dropping multiple backups onto your /. I've run out of room from that before.

---

### Post by t-molli on 2008-05-15
> **Paqman said:**
> The disk usage analyser should point out what folders are at fault pretty quickly.

One thing to watch out for is backup programs like sbackup. By default they might be dropping multiple backups onto your /. I've run out of room from that before.

yes, I was using disk usage analyzer, but could not - for the life of me - find anything wrong.

I'm thinking now that I was looking in the wrong place perhaps. I was using it to look at /, but if .gvfs is located in /home, but directly tied to / then something could have been in there. The only mystery is that I'm pretty sure I looked there last night and even though it said it was full, I only saw some very small files in there.

---

### Post by t-molli on 2008-05-15
Ok, I think the problem is a published bug in launchpad. Apparently it has something to do with the .gvfs, which is a new update in 8.04 having to do with connecting to networked drives.

The only problem is that I don't know what it is that I'm doing that everyone else using 8.04 isn't doing. I mean, I'm just copy/pasting files from a backup drive to /home. However, I did do that immediately after installing the OS and I was Ok. It was only later when I needed to move and organize files again that the problem occurred again. 

Also, I was watching it and saw I was at 91% full and then I didn't do anything and a little later I was 100% full. The only thing I had going at that time was a crontab file/script that was sync'ing my /home to my USB backup drive.

I may have to go back to 7.10 if there isn't a temp. fix for this, so if anyone knows anything about this, can you please provide solution.

Thanks in advance again...

---

