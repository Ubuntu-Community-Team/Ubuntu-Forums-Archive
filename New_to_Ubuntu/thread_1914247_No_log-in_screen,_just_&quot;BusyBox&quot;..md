---
title: "No log-in screen, just &quot;BusyBox&quot;."
date: 2012-01-24
forum: New to Ubuntu
---

### Post by nsamba on 2012-01-24
Hey guys! maybe you can help me with this.

Today, I tried to delete some files, but a pop-up message said that my disk was read-only (I didn't make any changes on my disk, so I was surprised by this msg).

I restarted the PC, and a purple screen saying that my disk had errors appeared. It said that it will fix it if I pressed F, wich I did.

It stayed on that screen for couple minutes, and then the log-in screen appeared. I used the PC for ten minutes, and everything stopped responding, and the PC restarted by itself.

Now, a menu with the following options appear:

[IMG]http://img849.imageshack.us/img849/5731/img00401201201240152.jpg[/IMG]

The first two, wich are supposed to start Ubuntu, lead to "BusyBox" (I have no idea what that is. It appears to be some kind of terminal). And all I get is this:

[IMG]http://img27.imageshack.us/img27/1732/img00397201201240151.jpg[/IMG]

It there a way to start Ubuntu normally from here?

---

### Post by androssofer on 2012-01-24
> **nsamba said:**
> Hey guys! maybe you can help me with this.

Today, I tried to delete some files, but a pop-up message said that my disk was read-only (I didn't make any changes on my disk, so I was surprised by this msg).

I restarted the PC, and a purple screen saying that my disk had errors appeared. It said that it will fix it if I pressed F, wich I did.

It stayed on that screen for couple minutes, and then the log-in screen appeared. I used the PC for ten minutes, and everything stopped responding, and the PC restarted by itself.

Now, a menu with the following options appear:

***image went here***

The first two, wich are supposed to start Ubuntu, lead to "BusyBox" (I have no idea what that is. It appears to be some kind of terminal). And all I get is this:

***image went here***

It there a way to start Ubuntu normally from here?

never seen this before myself, but did a bit of searching..

apparantly you can wait a while on the busybox screen then type

```
exit
```

and it should boot as normal..

will continue to look for a more permanent fix..

---

### Post by androssofer on 2012-01-24
Moar info for you here:

[http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html](http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html)

---

### Post by drs305 on 2012-01-24
You may still have errors on the drive. I suggest booting a LiveCD to the Desktop, open a terminal, and run an fsck check.

Change the drive/partition [COLOR="Red"]XY[/COLOR] designations to your Ubuntu partition (sda5, etc):
```
mount # Check that your real Ubuntu partition is not mounted.
sudo e2fsck -f -y -v /dev/sd[COLOR="Red"]XY[/COLOR]
```

If it still won't boot, I'd suggest installing/running the Boot Repair app. You can run it from the LiveCD after installing it.

If neither the fsck check nor Boot Repair fixes things, Boot Repair can run the boot info script and provide a link to the RESULTS.txt it generates. Post that so we can check the status of your boot files.

There is a link to Boot Repair in my signature line.

---

### Post by sandyd on 2012-01-24
> **nsamba said:**
> Hey guys! maybe you can help me with this.

Today, I tried to delete some files, but a pop-up message said that my disk was read-only (I didn't make any changes on my disk, so I was surprised by this msg).

I restarted the PC, and a purple screen saying that my disk had errors appeared. It said that it will fix it if I pressed F, wich I did.

It stayed on that screen for couple minutes, and then the log-in screen appeared. I used the PC for ten minutes, and everything stopped responding, and the PC restarted by itself.

Now, a menu with the following options appear:

[IMG]http://img849.imageshack.us/img849/5731/img00401201201240152.jpg[/IMG]

The first two, wich are supposed to start Ubuntu, lead to "BusyBox" (I have no idea what that is. It appears to be some kind of terminal). And all I get is this:

[IMG]http://img27.imageshack.us/img27/1732/img00397201201240151.jpg[/IMG]

It there a way to start Ubuntu normally from here?
You have a corrupted filesystem/disk journal.
Try to repair (fsck) from livecd. If you haven't crashed the disk recently, this could be a sign of hard disk failure, so you might want to check the SMART status, and check the disk on a livecd.

---

### Post by nsamba on 2012-01-25
Thank you guys for your help, but I'm stilla newbie at Ubuntu, and I'm not sure how to do all those things you told me. I opened the terminal, but I don't know how to do a fsck check, and I can't find the Boot Repair app.

---

### Post by WasMeHere on 2012-01-25
> **drs305 said:**
> You may still have errors on the drive. I suggest booting a LiveCD to the Desktop, open a terminal, and run an fsck check.

Change the drive/partition [COLOR="Red"]XY[/COLOR] designations to your Ubuntu partition (sda5, etc):
```
mount # Check that your real Ubuntu partition is not mounted.
sudo e2fsck -f -y -v /dev/sd[COLOR="Red"]XY[/COLOR]
```

If it still won't boot, I'd suggest installing/running the Boot Repair app. You can run it from the LiveCD after installing it.

If neither the fsck check nor Boot Repair fixes things, Boot Repair can run the boot info script and provide a link to the RESULTS.txt it generates. Post that so we can check the status of your boot files.

There is a link to Boot Repair in my signature line.

I suggest that you follow these instructions. You can run this command to find out the what to use for the [COLOR="Red"]XY[/COLOR]
```
sudo fdisk -lu
```
Good luck :-)

---

### Post by drs305 on 2012-01-25
> **nsamba said:**
> Thank you guys for your help, but I'm stilla newbie at Ubuntu, and I'm not sure how to do all those things you told me. I opened the terminal, but I don't know how to do a fsck check, and I can't find the Boot Repair app.

If you don't know your Linux partition, you can run the command suggested by *Olle Wiklund*. Your Ubuntu partition, when running "sudo fdisk -lu", should give you something like
> /dev/sd**a5**       205037658   836886527   315924435   83  **Linux**
Look for the partition with "Linux" (and not "Linux swap / Solaris").

Next, just make sure it is not mounted. You can run the "mount" command to see what partitions are mounted. You should NOT see your real Ubuntu partition listed in the results. 

You accomplish the fsck check with the 'e2fsck' command I provided. In the example above, the Linux partition is "sd**a5**", so the command would be:
```
sudo e2fsck -f -v -y /dev/sd**a5**
```

---

### Post by nsamba on 2012-01-25
I tried that, and this is what I got. 
[IMG]http://img440.imageshack.us/img440/2514/screenshotat20120125112.png[/IMG]

---

### Post by WasMeHere on 2012-01-25
It seems you got no output at all from
```
sudo fdisk -lu
``` This means that the live system cannot see your internal drive at all. So there is something wrong with it. Either it is not connected properly, or it has failed.

---

### Post by nsamba on 2012-01-25
I restarted my PC and ran the code ```
sudo fdisk -lu
```

This time, it worked, and I could follow the steps drs305 and Olle wrote.

My computer works again. Thank you guys so much! I still can't understand how you know all this haha

---

### Post by WasMeHere on 2012-01-25
I'm glad it worked after reboot. Please mark this thread SOLVED

... and if you get problems in the future, please start a new thread ;-)

---

### Post by drs305 on 2012-01-25
> **nsamba said:**
> 
This time, it worked, and I could follow the steps drs305 and Olle wrote.

My computer works again. Thank you guys so much! I still can't understand how you know all this haha

Glad it's working. :-)

We've all been where you are at one time.

Would you please mark the thread SOLVED via the Thread Tools link at the top right of the first post? 

Happy Ubuntu-ing !

---

