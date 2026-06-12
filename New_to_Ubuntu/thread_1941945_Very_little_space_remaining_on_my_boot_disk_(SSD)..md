---
title: "Very little space remaining on my boot disk (SSD)... Or is it?"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by motoroller on 2012-03-16
Hey everyone, I figured this is the appropriate place to ask since I'm still pretty new to linux. I realize this is probably a very basic question so please try to refrain from making too much fun of me ok? :P

Anyway, I'm running Ubuntu 11.10 and my boot disk is a mushkin chronos 64GB SSD. I also have a traditional hard drive I installed as file storage. Both drives work fine, and I'm really impressed by how fast my boot-up time is with this setup. 

One thing kind of disturbs me though: When I first installed Ubuntu (on my brand new system) about 5 days ago, The filesystem and home folder showed that there was something like 50GB free space remaining. I expected as much, owing to the system files and swap partition. Since then I have installed a few programs through the software centre (nothing big though, just things like gparted, VLC, nvidia drivers, and a couple others). Yesterday it said I had about 49 or 50 GB free (which I expected), but this morning I was shocked to learn it only has 6GB free!

I didn't believe it at first, so I went into gparted to confirm it, and it said the same thing. What happened? Is this normal?

Forgive me if this question has been asked before; I'm just used to the Mac OS X system so this phenomenon is a little new to me.

Any advice would be much appreciated!

---

### Post by Elfy on 2012-03-16
Try running baobab to see where these files are.

Disk usage analyzer or something like it might be called - search in the dash for it, then run it on File System.

Alternatively start it from a terminal

```
baobab
```

That said I would be inclined to look in /var/log in the file manager first.

Try and think of something you might have done in between times - a backup perhaps gone awry.

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by motoroller on 2012-03-16
Wow that was quick!

Anyway I ran the disk usage analyzer and here's what it said:

root had 23 items and 40.6 gb
home had 2 items and 36.2 gb
usr had 9 items and 3.6 gb

all the rest were pretty small.

The overwhelming majority of the used space in my home folder was the ".cache" file, using 33.5 GB!!!

Within the cache, the folder "checkbox" was the largest, taking up nearly all of that 33.5 GB.

What can I do about this? Is it ok to delete this folder (checkbox)? 

Also, how can I prevent this happening in the future?  I installed and ran bleachbit today... maybe that had something to do with it...

---

### Post by Elfy on 2012-03-16
Can you run this in a terminal - paste the output.

```
sudo dpkg -l checkbox
```

---

### Post by motoroller on 2012-03-16
here's the terminal output:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  checkbox       0.12.8         System testing application

I have no idea what all that means.... :o

---

### Post by Elfy on 2012-03-16
You installed checkbox. The two i's here 

ii checkbox 0.12.8 System testing application

tell me that

So if you want to remove it do so then you can remove the checkbox folder in your /home

Edit - then check your disk usage

```
df -h
```

or with baobab as before

---

### Post by Holdolin on 2012-03-16
On a somewhat side note, I'd move the swap from the SSD to the HDD.  Swap will hammer your SSD.

---

### Post by motoroller on 2012-03-16
> **Holdolin said:**
> On a somewhat side note, I'd move the swap from the SSD to the HDD.  Swap will hammer your SSD.

I was thinking about doing that... Actually I don't know if I even need a swap seeing as how I have 8gb of 1600 ddr3 ram... But assuming I still need a swap, is there a quick and easy way to move it to my HDD?

Also, thank you very much forestpiskie! You've been a big help. :)
I deleted the checkbox folder and my disk usage is back to normal.

---

### Post by motoroller on 2012-03-16
Ok I turned off the swap on my SSD and deleted the swap partition using Gparted. I then created a new swap partition on the HDD and activated it. So far, so good. I was then left with a 8 GB hole where my swap partition was, so I decided to get rid of it and simply increase the size of my primary partition. I needed to boot from the ubuntu install USB for this...

When I increased the size of my primary partition, Gparted gave me an error message (I can't recall exactly what it said) although it appeared to have changed the partition size successfully. What's confusing is that when I check gparted, my partition takes nearly the entire SSD, but my home folder says there's 16gb used. When I check the disk usage analyzer, it only shows 8gb being used. I'm confused again, and a little frustrated:confused:

Did I do something wrong?

---

### Post by motoroller on 2012-03-17
I figured it out! I booted from the install usb, ran gparted, had it check and repair the file system, and presto it worked! :guitar:

---

