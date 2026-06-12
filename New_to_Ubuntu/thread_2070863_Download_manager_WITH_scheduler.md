---
title: "Download manager WITH scheduler"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by danneauxs on 2012-10-13
I've been reading threads for an hour and I can not find exactly what I want.

I've found suitable download managers except I cannot find one with a SCHEDULER.

I am using satellite internet and I have a monthly data allowance.  Between 12am and 5am we have a free time where I can download without it being counted against my monthly limit.

Acceleration isn't really that important. 
Resume is important.
Scheduling is a must.

Any suggestions.

Iv'e looked at things like Jdownloader, aria2, fatrat, kget and a few more (not sure about spelling of what I named).

Thanks in advance
Danneauxs

---

### Post by dniMretsaM on 2012-10-13
Off the top of my head, I can tell you that [wxDownload Fast]("http://dfast.sourceforge.net/index.html") has scheduling. There are probably others, but I don't use a download manager other that my torrent client (and it's only for downloading legal stuff, btw), so I'm not sure which ones.

EDIT: I found the uGet also has a scheduler. And, unlike wxDownload Fast, uGet is in the repositories (amd64 1.8.0-1 download size is 192 kb, if you're wondering). You can install it like this:
```
sudo apt-get install uget
```

---

### Post by sandyd on 2012-10-13
DownThemAll comes to mind

---

### Post by HermanAB on 2012-10-13
So, what is wrong with wget or curl and cron?

---

### Post by adnan-kamili on 2012-10-14
If you don't mind waiting for some weeks, you can opt for flareGet. It doesn't support scheduling yet, but next version will definitely have scheduler!

---

### Post by danneauxs on 2012-10-14
@dniMretsaM
uGet does indeed have scheduling. I went back to my searches and the page where I read the description did not list that as a feature. Got it and hope it works.
wxDownload Fast seem interesting. I did not come across this one in my search.
Thanks

@sandyd 
I looked at it, went to the feature page and couldn't find anyting about scheduling.  I prefer Chrome to Firefox anyway. But I'll look into it though I have a habit of closing my browser when I leave my desk so that might be a problem.

@HermanAB
Went to the GNU wget manual page, didn't read it, but searched for the word "schedule" and didn't find it so stopped right there.
Isn't curl CLI? I don't do CLI. Typing is a pain without all your fingers.
cron?  Wouldn't that be more typing?  Have no idea how to run it but it sounds like more work than clicking and selecting to download at scheduled time. BUT thanks I'll look into that for a few other things I need a task scheduler for!!

@adnan-kamili
I looked at this and thought it looked good but like you said no Scheduler.  Get it added and I'm there!

Just a thanks to everyone who replied.  I've been a Windows user since 2.0 but have been trying Linux on and off for the last 4 years.  It just never worked out since I always ran into some program I couldn't find a GOOD alternative for or at all.  Other problems too... The biggest I'm having now is FINDING programs. Ubuntu Software Center just sucks in it's setup. Linux program names seemed designed to hide what they do from "windowz" people LOL.  I just seems like more work to find something that I often just give up.

So again thanks for putting in the effort.
Danneauxs

---

### Post by dniMretsaM on 2012-10-14
> **danneauxs said:**
> @HermanAB
Went to the GNU wget manual page, didn't read it, but searched for the word "schedule" and didn't find it so stopped right there.
Isn't curl CLI? I don't do CLI. Typing is a pain without all your fingers.
cron?  Wouldn't that be more typing?  Have no idea how to run it but it sounds like more work than clicking and selecting to download at scheduled time. BUT thanks I'll look into that for a few other things I need a task scheduler for!!

Both wget and curl are CLI programs (though they both have GUI front ends). They don't havee schedulers themselves, but that's why HermanAB mentioned cron (which is a scheduler). If you combine them, you can get exactly what you want. However, since you don't want to type, just go with uGet.

---

### Post by danneauxs on 2012-10-14
Thanks!

The hardest part is knowing what's available.  I'm getting more familiar with Linux in general.  Anything is more difficult if you have to start from scratch.

I'm appreciative of all replies and each is an opportunity to learn something.

Thanks everyone.
Danneauxs

---

### Post by Mahdi D on 2013-02-24
Hey there, you can schedule your downloads in DownThemAll with a trick:

[http://ubuntuforums.org/showthread.php?p=12527737#post12527737](http://ubuntuforums.org/showthread.php?p=12527737#post12527737)

Hope it helps.

---

