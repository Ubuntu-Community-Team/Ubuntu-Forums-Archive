---
title: "vlc/system error/lid"
date: 2016-08-13
forum: New to Ubuntu
---

### Post by xedoc on 2016-08-13
Hi,

I have a Razer blade stealth with Ubuntu Gnome. 

1) When i start ubuntu, i have a message exactly like this: [http://www.binarytides.com/blog/wp-content/uploads/2014/04/system-program-problem-detected.png](http://www.binarytides.com/blog/wp-content/uploads/2014/04/system-program-problem-detected.png)
   No clue of what could be, if it was windows i would think it was a bad installation or maybe a driver issue. Installation i don't think it is as it does the same with ubuntu-mate. I'm suing 3 partitions ext4( / ), Swap(8gigas), EFI(512mb). 

2) I installed VLC, the other software that comes by default works fine but when i play videos with vlc, the video becomes very littlle. even if i maximize vlc or if i fullscreen the video, very little even with different video extensions.

3) When i close the lid of my razer, the laptop suspend as it should, however when i open the lid it starts but after a few seconds the laptop suspend again without doing nothing, the only way i have to fix this is by restarting the laptop. It becomes very annoying as you can imagine.

With thanks and regards,

---

### Post by xedoc on 2016-08-13
Also, i justrestarted my laptop and now no more wifi. The icone even disappeared from the up right corner. :\

---

### Post by howefield on 2016-08-13
> **xedoc said:**
> 1) When i start ubuntu, i have a message exactly like this: [http://www.binarytides.com/blog/wp-content/uploads/2014/04/system-program-problem-detected.png](http://www.binarytides.com/blog/wp-content/uploads/2014/04/system-program-problem-detected.png)

For point 1.. anything in /var/crash/ ?

```
ls -al /var/crash/
```

---

### Post by xedoc on 2016-08-14
Hello Howefield, thank you for the help.

Here it is:

total 1452
drwxrwsrwt  2 root whoopsie    4096 Aug  6 00:05 .
drwxr-xr-x 14 root root        4096 Jul 20 21:08 ..
-rwxrwxrwx  1 root whoopsie       0 Aug  6 00:05 .lock
-rw-r-----  1 root whoopsie 1475373 Aug  6 00:05 _sbin_plymouthd.0.crash


And regarding the Wifi, i just turned on the laptop and the wifi is there. I don't what happened.

Regards,

---

### Post by howefield on 2016-08-14
> **xedoc said:**
> -rw-r-----  1 root whoopsie 1475373 Aug  6 00:05 _sbin_plymouthd.0.crash

Glad to hear that you have wifi back, so the crash problem looks like being down to plymouthd then.. you can have a look at it for more info but in all honesty I usually just report the system errors, most times they won't offer to report again, imhe anyway.

If you want to look at the info in the above crash report, try

```
cat /var/crash/__sbin_plymouthd.0.crash | less
```

It is likely to be a long report that scrolls quite some distance, so piping into "less" allows you to press the spacebar to view a page at a time and quit at your convenience. 

Also, make sure that you are fully updated to ensure any available fixes for system problems are applied.

---

### Post by xedoc on 2016-08-14
Hi,

I've lost wifi again, i did restart the laptop 2 times and  still no wifi. I turned off the laptop and then i turned on again. The  wifi came back. It's a little frustrating. It doesn't seem very logical  to me. It's like if the adapter couldn't turn on sometimes. Any idea  what could be ? 

I did report the problem as you said, no more notification regarding this. 

Any  idea concerning the other issues i'm facing ? I thought it could be the  graphical interface gnome but it happens exactly the samething with  ubuntu-mate.

---

### Post by howefield on 2016-08-15
> **xedoc said:**
> Any  idea concerning the other issues i'm facing ? I thought it could be the  graphical interface gnome but it happens exactly the samething with  ubuntu-mate.

Sorry I don't, except for to say it's usually better to have one thread per topic. 

In terms of vlc I can't reproduce or even guess what the issue might be but fwiw, I'd enable logging in VLC preferences with the verbosity set to 2. The resultant log *might* give you a clue. 

The suspend issues could be a number of things and really does warrant it's own thread with much more detail, such as complete hardware list. Just out of interest does suspend work if chosen from the menu before closing the lid. 

From the Arch wiki for the razor...
> 
Suspend Loop
Suspending (Close laptop lid) does not seem to work with a basic installation. You can suspend but once the system resumes it suffers from random suspends or the screen going blank for no apparent reason.
A temporary fix is to disable the automatic systemd suspend action by chaning the HandleLidSwitch value in the /etc/systemd/logind.conf file:
HandleLidSwitch=ignore

---

### Post by xedoc on 2016-08-17
Hi howefield,

Thanks again for your help. I'm going to create new topics for each problem. I did a research but i couldn't find any permanent solution for my issue with the lid. Maybe in the future, until then i disable the supense.

You may close the thread.

Kind regards,

---

