---
title: "var is suddenly 48 gb!!"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by mystmaiden on 2012-06-13
I've been fiddling about with getting xscreensaver  and Ubuntu Precise today - I posted about it  

[http://ubuntuforums.org/showthread.php?t=2003039](http://ubuntuforums.org/showthread.php?t=2003039)  

Edit - the only other thing I have done today that might have caused this is plug in my usb wireless adapter, its made for linux though so I think thats probably not the culprit.

Now suddenly I'm out of disk space. /var is showing at 48 gb. The culprits seem to be syslog and kern.log - each about 23 gb.  I have 166 mb left on the hard drive :(

I know where the problem is but not how to safely solve it. How can I slim them back down? 

thanks -
mystmaiden

---

### Post by matt_symes on 2012-06-13
Hi

I would boot into a LiveCD/USB, mount your install and have a look in those files and see why they're so big before i do anything.

48G is just crazy. You're 100% sure they're that size :shock: ?

For comparison, here's mine..

```
matthew@matthew-Aspire-7540 ~ % ls -lh /var/log/{syslog,kern.log}
-rw-r----- 1 syslog adm 1.1M Jun 14 01:34 /var/log/kern.log
-rw-r--r-- 1 syslog adm  31K Jun 14 02:24 /var/log/syslog
matthew@matthew-Aspire-7540 ~ %
```

Kind regards

---

### Post by fuzzyworbles on 2012-06-13
holy smokes! if that happened to me i'd probably just delete the offending logs and only work on finding the cause if it ever happened again. 

However, flooding the logs with garbage is a tactic to obfuscate a hacker's records when they're unable to delete them. If you're paranoid, you could painstakingly grep the logs for tell-tale signs of chicanery.

.. woops. didn't see your edit. to delete them just open a terminal and sudo rm /var/log/syslog /var/log/kern.log

---

### Post by mystmaiden on 2012-06-14
Thanks for the replies matt_symes and Fuzzyworbles


I'm sure they're that big (see attached). I tried to look at syslog with gedit but it was too big and was taking forever to load.I finally had to give up. If its a hacking attempt, I wouldn't really know what I was looking for though. Since I'm so low on space now, I'll try deleting one and having a look at the other.

thanks again,

mystmaiden

---

### Post by alphacrucis2 on 2012-06-14
> **mystmaiden said:**
> Thanks for the replies matt_symes and Fuzzyworbles


I'm sure they're that big (see attached). I tried to look at syslog with gedit but it was too big and was taking forever to load.I finally had to give up. If its a hacking attempt, I wouldn't really know what I was looking for though. Since I'm so low on space now, I'll try deleting one and having a look at the other.

thanks again,

mystmaiden

Use vi or vim instead of gedit for files that big. It doesn't try and load the entire file into ram. If you aren't familiar with it this cheat sheet is useful:

[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

---

### Post by oldfred on 2012-06-14
You can list very large files with the terminal commands, cat, less or more. To see details use man

man more

less /var/log/dmesg

use q to exit less or more

---

### Post by alphacrucis2 on 2012-06-14
Another useful one is tail.

tail -n 20 filename

will list the last 20 lines in the file specified by filename

---

### Post by mystmaiden on 2012-06-14
> **alphacrucis2 said:**
> Another useful one is tail.

tail -n 20 filename

will list the last 20 lines in the file specified by filename

Thanks alphacrusis. 

That didn't seem to work with kern.log and syslog plugged in as filename but I did find the difficulty. I emptied the files then let the computer run for a bit, and sure enough it was filling up the log files quickly.  There were lots of these - 

```
[drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
```

I don't know if that is from the screensaver or something to do with classic no tweaks but I have read somewhere that drm had some issues. I believe there is an alternative to drm?

---

### Post by jtarin on 2012-06-14
[Temporary solution until a kernel fix.]("https://bbs.archlinux.org/viewtopic.php?id=114935")
Or........[Here.]("http://lists.debian.org/debian-kernel/2012/01/msg00715.html")

Seems like desktop effects and your chip might be a problem.

---

### Post by gnorb on 2012-06-14
While trying to study the logs, you can also manually run logrotate before the logfiles grow too big.

---

### Post by steeldriver on 2012-06-14
Funny, I was looking at this last night and wondering if it could be the same issue I had - looks like it is

The fix posted by jtarin worked for me, i.e.

```
$ cat /etc/drirc
<!--  2012-05-23 : added /etc/drirc file to prevent kern.log filling with -->
<!-- [drm:intel_prepare_page_flip] messages - see ubuntu Bug #765813 -->

<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813)

---

### Post by mystmaiden on 2012-06-14
thanks so much  for the replies, I read the post that shows those commands late last night, but was unsure if that was being caused by the same issue that I have.

Do I copy and paste all that into the terminal at once or one line at a time?

---

### Post by steeldriver on 2012-06-14
The whole thing (well the first 2 lines are optional - just comments to remind my why the file is there - you can include them as-is or write something else between the <!-- and -->) needs to go into a file called 'drirc' in the directory /etc, you can do that either in a graphical editor like gedit i.e.

```
gksudo gedit /etc/drirc
```or with a terminal based editor

```
sudo nano /etc/drirc
```then paste in 

```

<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>

```

and save the file. You will need to reboot for it to take effect (there *may* be another way e.g. reloading modules but I don't know it).

---

### Post by mystmaiden on 2012-06-14
Thanks so much. The problem has finally subsided. To check and make sure what was causing it I purged xscreensaver , unhooked my linux usb wireless adapter and rebooted - let the computer run awhile and it did not generate any more errors.  Then I plugged in the adapter, checked again - no errors. Reloaded xscreensaver - whammo! Lots of new errors.

I ran the script and it immediately stopped the generation of the error but, do I need to get rid of xscreensaver or can I continue to use it? Other than the fact it doesn't auto start it seems to be behaving normally (it shows on startup and I followed the instructions found at [http://www.thelinuxgeeks.info/how-to-install-xscreensaver-in-ubuntu-12-04/  ]("http://www.thelinuxgeeks.info/how-to-install-xscreensaver-in-ubuntu-12-04/")
to create the proper file...

mystmaiden
[]("http://www.thelinuxgeeks.info/how-to-install-xscreensaver-in-ubuntu-12-04/")

---

### Post by mystmaiden on 2012-06-16
Just giving this a little bump to see if its best to remove the screensaver. I'd like to keep it but don't want to crash ubuntu or damage my computer

---

### Post by sffvba[e0rt on 2012-06-16
> **mystmaiden said:**
> Just giving this a little bump to see if its best to remove the screensaver. I'd like to keep it but don't want to crash ubuntu or damage my computer

Well the error isn't filling your log anymore so I can't see why you can't keep the screen-saver.


404

---

### Post by mystmaiden on 2012-06-17
Thanks!! I was hoping that was the case.

Marking this one solved and being grateful for all the help :)

---

