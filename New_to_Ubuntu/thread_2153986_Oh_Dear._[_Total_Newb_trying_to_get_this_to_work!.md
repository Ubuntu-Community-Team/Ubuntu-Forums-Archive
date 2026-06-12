---
title: "Oh Dear. :[ Total Newb trying to get this to work!"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by 12onthebox on 2013-06-13
I just installed Ubuntu 12.04 LTS 32bit onto my Acer Aspire One and so far I am having several issues that I have no idea how to fix. :[ I'm getting messages that say I'm experiencing internal errors. My screen is super dark and I can't fix the brightness level. I'm pretty sure that my installation wasn't a very good one, lol. I struggled for hours trying to figure out how to install it and now that I have it seems that everything is going wrong. :[ At first I tried booting from a USB with 0 success so then I used a CD with Unetbootin I believe and it worked (seemingly). A red icon at the top of the screen is telling me to run the Package Manager with an error message of: Opening the cache (E.Read error -read (5: Input/output error), E:The Package lists or status file could not be parsed or opened.)'. 

Help! :'[

---

### Post by cub on 2013-06-13
The red icon indicates there are updates available. Some update might solved your screen issue. If you open a terminal and run:
```
 sudo apt-get update && sudo apt-get upgrade
```
what is the result?

---

### Post by byStanderone on 2013-06-13
...since it's a fresh install and brewing problems...would suggest return to step one....prepare your disk for a new install...something would have been overlooked.

---

### Post by _0R10N on 2013-06-13
I'd suggest what @cub recommends... it's not unusual that fresh installs experience some stability issues. If after upgrading the problems remain, then you should start asking for help on each one of them separately.

---

### Post by 12onthebox on 2013-06-13
Ok my first task was trying to figure out how to open a terminal, lol, I'm not sure if I was doing it right, I did Ctrl-alt-f1 and it asked me to login. I'm not sure what my login ID would be so I just typed in my user name on the computer and the password but it keeps telling me the login is inocorrect. I have no idea what I'm doing. ](*,)

---

### Post by 12onthebox on 2013-06-13
Also, I don't know if this makes a difference but there is nothing on my screen except the bar at the top... aren't there supposed to be icons on the left? :-s

---

### Post by cub on 2013-06-13
Oh, if you don't know your user name and password it might get tricky. Didn't you need to provide it on the login page when you boot the system?

ctrl + alt + t should open a terminal. ctrl + alt +F1 open a virtual console. It will work too, but you need to login again. However to do the sudo command you would need your password again anyhow.

---

### Post by cub on 2013-06-13
[http://ubuntu-manual.org/](http://ubuntu-manual.org/) might come in handy.

Sorry, it is of course updated for 13.04.

---

### Post by mastablasta on 2013-06-13
ctrl-atl-t is the terminal. 

what you did is access virtual console.  which should have still worked. yeah it's your username and then username's password (assuming the user is first user, as that one will have sudo privileges).

---

### Post by 12onthebox on 2013-06-13
Ok I think I figured out the username/password issue. I typed in that code and it ran for a minute, when it stopped it said:

Errors were encountered while processing:
/var/cache/apt/archives/libreoffice-writer_1%3a3.5.7-0ubuntu4_i386.deb
/var/cache/apt/archives/libreoffice-calc_1%3a3.5.7-0ubuntu4_i386.deb
/var/cache/apt/archives/libreoffice-impress_1%3a3.5.7-0ubuntu4_i386.deb
/var/cache/apt/archives/libreoffice-draw_1%3a3.5.7-0ubuntu4_i386.deb
/var/cache/apt/archives/libreoffice-common_1%3a3.5.7-0ubuntu4_i386.deb
/var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I don't know where to go from there.

---

### Post by 12onthebox on 2013-06-13
And thanks for the information from everyone so far. You're really helping me during this learning process. ;)

---

### Post by 12onthebox on 2013-06-13
After restarting now it won't even load. It gets to the purple screen with the ubuntu logo and the loading dots and that's it. I tried powering off and trying again but it does the same thing - stuck at the loading screen. :[

---

### Post by mastablasta on 2013-06-13
can you press esc at that screen? if so then it should spill out a bunch of words. the lats one could give an idea as to what error stopped it.

---

### Post by cub on 2013-06-14
Could you try out doing a
```
sudo apt-get clean
```
and then run the update + upgrade again?

[edit]Seems I didn't see all the latest post when I replied. Never mind this one.

---

### Post by 3rdalbum on 2013-06-14
The message "Input/Output Error" gives us a clue: The spot on your disk where the package cache resides, is damaged.

Disk damage can spread across a disk, so this is maybe why you can't boot now. If you hit Control Alt F1 during boot you will probably see lots of Input Output errors. Reinstalling or formatting wont help as the disk will still be damaged.

I might be wrong and your system may not be booting for a different reason.

---

### Post by byStanderone on 2013-06-14
...perhaps this link can help
[http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/)

---

### Post by byStanderone on 2013-06-14
...hope this helps,

[http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/)

---

### Post by 12onthebox on 2013-06-16
What exactly does that mean if the disk is damaged? Can it be fixed? :[

---

### Post by 18echo on 2013-06-16
> **12onthebox said:**
> What exactly does that mean if the disk is damaged? Can it be fixed? :[

If the disk is physically damaged, no it cannot be fixed. You can recover data from it so you have it available when you replace the damaged disk.

But you still do not know if your disk is damaged or not.

If you set up your Acer for dual boot, and if you can boot to the Windows partition, you can scan the hard drive there.

Otherwise you can boot live from the DVD or thumb drive that you used to install 12.04, and scan it from there:
[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

If this is a fairly new Acer, and you haven't dropped it, chances are there is no damage.
If it is damaged, hopefully it's still under warranty.
Good luck.

---

### Post by Vormeph on 2013-06-16
I concur with the previous responses aforementioned; if your disk is physically damaged then you will not to purchase a new hard disk and add that to your laptop instead. However, the term 'damage' could also refer to the fact Linux isn't recognising the file format on your hard drive, in which case this might be Windows attempting to intervene with Linux with pride: that is, if you're dual booting. I think very little info is being given as to how you've partitioned your hard drive as to dual-booting, or lack thereof.

---

