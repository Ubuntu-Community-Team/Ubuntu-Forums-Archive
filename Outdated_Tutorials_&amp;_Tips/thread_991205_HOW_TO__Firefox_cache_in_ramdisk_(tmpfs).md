---
title: "HOW TO:  Firefox cache in ramdisk (tmpfs)"
date: 2008-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by civilmonkey on 2008-11-23
I was trying to find a way to set up a ramdisk and have firefox store the cache there.  After a bit of reading this is what I found and did.

Reference Link:
[http://en.wikipedia.org/wiki/TMPFS]("http://en.wikipedia.org/wiki/TMPFS")

Step 1:  Make a place to mount the ramdisk.  In the terminal type:
```
sudo mkdir /media/ramdisk
```

Where /media/ramdisk is where you will mount the ramdisk.

Step 2:  Mount the ramdisk
```
sudo mount -t tmpfs -o size=64M,nr_inodes=10k,mode=0777 tmpfs /media/ramdisk
```

I set the permisions to 777 which allows anybody and everybody to access it.  Set these as you wish

Step 3 In firefox:  Set the cache location to you new ramdisk
Reference link: [http://www.infohole.com/blog/computing/firefox-cache-location/]("http://www.infohole.com/blog/computing/firefox-cache-location/")
Basically type ```
 about:config
``` in the URL address bar.  Search for ```
browser.cache.disk.parent_directory
``` or add a new string by right clicking and choosing new.  Then set the location to your ramdisk.  In my case I set it to ```
/media/ramdisk/
```

Optional:
Step 4:  If you wish to automount the ramdisk you need to edit your FSTAB file
Reference Link: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
```
gksudo gedit /etc/fstab
```
Add the line
```
tmpfs /media/ramdisk tmpfs size=64M,nr_inodes=10k,mode=777 0 0
```

Everything should be all set.  You can check the ramdisk to see if a folder 'Cache' is created when you load firefox.  Don't forget to close firefox or restart firefox before you set this up.

PS.  I don't know much about inodes but the above seems to work for me.

---

### Post by Cowchip7 on 2009-04-20
Now if I were to do this, how would I be able to restore the default settings if need be? :P

---

### Post by binbash on 2009-04-22
Thanks, works fine here

---

### Post by daverave999 on 2009-05-25
I have mine set to /dev/shm instead.

Though I think you could always just set browser.cache.disk.enable to false and it would use the RAM instead anyway.

---

### Post by aktiwers on 2009-05-25
Do you get any performance boost by doing this?

---

### Post by daverave999 on 2009-05-31
Clicking 'back' is pretty much instant now, and the momentary sluggishness when loading image-heavy pages seems to have gone. It certainly hasn't caused any problems.

---

### Post by Astinsan on 2009-06-01
> **Cowchip7 said:**
> Now if I were to do this, how would I be able to restore the default settings if need be? :P

Take out the key you added to firefox and take out the tempfs in the fstab will kill it.


It is a speedup for sure.

---

### Post by dcstar on 2009-06-03
> **daverave999 said:**
> I have mine set to /dev/shm instead.

Though I think you could always just set browser.cache.disk.enable to false and it would use the RAM instead anyway.

Why not just add this integer key and set it to the size you want?:

browser.cache.memory.capacity

[http://howto.helpero.com/howto/Speed-Up-Firefox_31.html](http://howto.helpero.com/howto/Speed-Up-Firefox_31.html)

---

### Post by graysky on 2009-08-19
You can do it following [this wiki](http://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs) page.

---

### Post by pluckypigeon on 2009-08-24
> **graysky said:**
> You can do it following [this wiki](http://wiki.archlinux.org/index.php/Speed-up_Firefox_using_tmpfs) page.

When am I supposed to run this script??

```
#!/bin/bash
# Change this to match your correct profile
PROFILE="y.default"

cd "${HOME}/.mozilla/firefox"

if test -z "$(mount | grep -F "${HOME}/.mozilla/firefox/${PROFILE}" )"
then
    mount "${HOME}/.mozilla/firefox/${PROFILE}"
fi

if test -f "${PROFILE}/.unpacked"
then
    rsync -av --delete --exclude .unpacked ./"$PROFILE"/ ./profile/
else
    rsync -av ./profile/ ./"$PROFILE"/
    touch "${PROFILE}/.unpacked"
fi

exit
```

I have tried running it after I close firefox, before I open it, after I've rebooted and I have tried not running it.... I can't seem to work out when I need to run it. Could someone help shed some light on this?? 

When I close the tmpfs mounted Firefox is it supposed to save back in to the main folder or does it not save at all?

What am I supposed to do to save changes?

I have tried following the wiki over and over.

Thanks for any responses.

---

### Post by pluckypigeon on 2009-08-25
> I have tried running it after I close firefox, before I open it, after I've rebooted and I have tried not running it.... I can't seem to work out when I need to run it. Could someone help shed some light on this?? 

When I close the tmpfs mounted Firefox is it supposed to save back in to the main folder or does it not save at all?

What am I supposed to do to save changes?

I have tried following the wiki over and over.

Thanks for any responses.

anyone?:(

---

### Post by supasoaker on 2011-01-22
take a rest pluckypigeon, forget everything and re-read the archlinux article - it should tell you!

one question  - how do I check that the tmpfs is running, I can't see anything in the mnt folder................

edit: I think I found out how - in the terminal type:

```
 dan@dan-desktop:~$ df 
```and a list should appear along the lines of:

```
 Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            949725292 218316212 683165780  25% /
none                   2025640       300   2025340   1% /dev
none                   2030148       196   2029952   1% /dev/shm
none                   2030148        84   2030064   1% /var/run
none                   2030148         0   2030148   0% /var/lock
none                   2030148         0   2030148   0% /lib/init/rw
tmpfs                  2097152     48388   2048764   3% /media/firefox_ramdisk
/dev/sr0                194658    194658         0 100% /media/RescueRemix1010

```

as you can see my tmpfs looks to be running nicely :)

---

### Post by pluckypigeon on 2011-01-22
> **supasoaker said:**
> take a rest pluckypigeon

That post was a year and a half ago, I've found plenty of time to rest.

---

