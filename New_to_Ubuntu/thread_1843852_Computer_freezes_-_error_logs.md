---
title: "Computer freezes - error logs"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by zcacogp on 2011-09-14
Chaps, 

I rebuilt my desktop machine a week or so ago (new HDD), and it seemed to be running OK. I used the instructions here: 

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

... to create a list of software installed on the old build and then used dselect to install everything on the list on the new build. 

However, it has frozen on me three times in the last three days, and never froze before re-building. I have looked into /var/log and discovered a long list of log files, but have a couple of questions:

1. Which log file should I look in to find out what happened? (a quick google suggested that /var/log/messages should be a good one to look at, but this one doesn't exist, I presume because no messages have been created to be written to file.)
2. What am I looking for and how should I interpret it? 
3. Some of the log files seem to have times in them when I know the computer was switched off. An example is this line in kern.log (I presume this is a kernel log)


```
Sep 14 02:02:08 desktop kernel: [   23.492190] EXT4-fs (sda6): re-mounted. Opts: commit=0
```

The computer was switched off at 02:02:08 this morning. (And the system clock is correct!) How can it produce a line in an error log for this time? 

All help appreciated - thanks. 


Oli.

---

### Post by LowSky on 2011-09-14
Open the box up and check all the wires, but Sometimes we get bad hard drives... you can also run a smart test on the drive.

But more importantly when is it freezing? I had an issue releated to flash and my nvidia card causing a system freeze. if its that the simple fix is to use flash-aid and disable gpu acceleration

---

### Post by zcacogp on 2011-09-15
LowSky, 

Thanks. Bad HDD? Alas - that is why I removed the old one! Having said that, the SMART data all looks very healthy and it seems to pass the self-tests. 

It has frozen three times; on each occasion when doing nothing more than web-surfing. The symptoms have been the same each time; the "IOWait" trace on System Monitor has done up dramatically and the computer has ceased to respond - but the pointer has continued to respond to mouse movements. Eventually the System Monitor graph has stopped scrolling and I have had to turn the machine off and on again. 

Thanks for your help. 


Oli.

---

### Post by zcacogp on 2011-09-16
Chaps, 

It's just frozen again, and I have had to re-start it. So there should be something pretty recent in the logs for this one. 

The symptoms were identical to last time; web browser and Amarok windows open, and the machine stopped responding to anything other than mouse movements. 

All help welcomed - thanks. 


Oli.

---

### Post by Lisiano on 2011-09-16
Well you could use gnome-system-log instead of opening the files manually.
Also a good place would be to look at dmesg, xorg and kernel. Also can you switch to a TTY with Ctrl+Alt+F1-F6?

---

### Post by zcacogp on 2011-09-16
Lisiano, 

Thanks. The system log viewer is helpful (I hadn't come across it before.) I can open the log files you mentioned, but don't know what I should be looking for in there. If I was to post them up here would they make any sense to you? 

I haven't tried the TTY access - I didn't know it existed! I'll try it next time it freezes up. 

Thanks for your help. 


Oli.

---

### Post by Lisiano on 2011-09-16
Post them, even if I find something that I can't understand, maybe someone who understands will see them. Due to the possible size, use [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) or attach as a attachment.

---

### Post by zcacogp on 2011-09-19
Lisiano, 

Thanks. It has done it a couple more times now, and each time the symptoms are as described above. I'm not sure whether it freezes irrevocably, or whether it would come back after a while. What may be relevant is that when it does appear to freeze, it sounds like there is a lot of HDD activity going on. Yes, I can access TTY (helpful hint - thanks. I didn't know you could do that) and run top, and it shows nothing amiss on the CPU usage. However the system monitor trace goes very high for the IOWait and System Load. 

I've copied the various log files into the Ubuntu Pastebin, but I'm not sure what has happened to them; should I then paste them into this thread? If so, how? (I assumed that 'kern.og' was 'kernel' - is this right?)

Thanks very much for your help. 


Oli.

---

### Post by zcacogp on 2011-09-21
Anyone? 

For what it's worth, I have used the computer a bit in the last couple of days and it hasn't frozen again ... but I still don't trust it!

Thanks, in advance, for any help. 


Oli.

---

### Post by Lisiano on 2011-09-21
Probably "kern.og" is "kernel.log" but who knows, just compare it to yours and you will know if it's it or not, and yes, post the links here.
Also there is a top for I/O, ```
iotop
``` should show you exactly what is doing those I/O blocking waiting.

---

### Post by zcacogp on 2011-09-29
Lisiano, 

Many thanks for your help to date. I haven't posted the logs, mainly 'cos I was stuck for time. But I think I have found the solution ... 

Firefox. It seems to be an error with firefox, and I was told on a couple of occasions over the last week that there were scripts on the page (presumably gMail) which had stopped responding. Since then I have gone to Chromium, and the problem hasn't re-occurred. 

I know this is a work-around and the problem hasn't been solved, just side-skirted. (It is doubly annoying as I left Chromium for firefox around 3 months ago as it has a lower CPU load.) However, it does mean I can use the machine again which is good. And I'll probably go to 11.10 in a month or so's time anyway, which will mean a re-build. 

So, many thanks for your help. I appreciate it. The problem is now solved. 


Oli.

---

