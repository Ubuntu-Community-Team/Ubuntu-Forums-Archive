---
title: "which Amarok database?"
date: 2006-07-19
forum: Other OS Talk
---

### Post by colsinc on 2006-07-19
Hi everyone, I have used both SQL Lite and mySQL databases for Amarok.  they both seemed to be about the same speed.  what are the pros and cons of the different DB's offered?

---

### Post by asimon on 2006-07-20
MySQL should scale better then sqlite, i.e. you should see a performance advantage when the number of media is very very high.

With the MySQL backend it's also possible to share the same db between different computers.

The sqlite backend doesn't work with NFS.

Amarok's wiki also mentions that the MySQL backend is not as stable as the sqlite backend. Probably because sqlite is the default and the MySQL backend doesn't get tested as much.

---

### Post by colsinc on 2006-07-27
thanks.  I think Ill just use SQL Lite for now.  I have about 2000 songs- -what is considered a very high number?

---

### Post by asimon on 2006-07-27
> **colsinc said:**
> thanks.  I think Ill just use SQL Lite for now.  I have about 2000 songs- -what is considered a very high number?
Good question. People use the sqlite backend with 10000 songs and more and don't seem to have any problems with it.

---

### Post by hopstah on 2006-07-27
i have almost 20000 songs and have no complaints about sqlite.  rescanning my collection takes about 3 minutes to complete, so i have no motivation to use a different backend.

---

### Post by colsinc on 2006-07-29
thanks everyone, just a few more Q's

Is it normal for it to take several (about five) seconds for amarok to display when it's been minimised to the system tray?
-(edit)I'm using Ubuntu 6.06, GNOME, P4 3Ghz, 768Mb.  my system does not have to be under stress for this to happen, and it happens even when amarok has been minimised for only a short while (like 2 minutes).
and
Is it possible to somehow backup the scores for each song.  Amarok went weird a couple of weeks ago and I killed it, and it lost all my scores :sad: ?

---

### Post by hextor on 2006-09-02
thats the problem with keeping scores on a database as opposed to one the files themselves..

trick or workaround: use the BPM field. that way you can hardcode your scores onto the files every once in a while - i mean the star scores of course

---

### Post by bionnaki on 2006-09-05
> **colsinc said:**
> 
Is it normal for it to take several (about five) seconds for amarok to display when it's been minimised to the system tray?
-(edit)I'm using Ubuntu 6.06, GNOME, P4 3Ghz, 768Mb.  my system does not have to be under stress for this to happen, and it happens even when amarok has been minimised for only a short while (like 2 minutes).


running kde apps on gnome will usually suck. you should try kubuntu. amarok is well intergrated and loads instantly (for me at least, whereas it did not for me in gnome - I also had a lag).

in kde, amarok runs very smoothly.

---

### Post by kubilaycan on 2007-09-16
> **hextor said:**
> thats the problem with keeping scores on a database as opposed to one the files themselves..

trick or workaround: use the BPM field. that way you can hardcode your scores onto the files every once in a while - i mean the star scores of course

how do u do that bpm trick? is there an automated script, or do u do it one by one?

by the way, does this mean that if my amarok is screwed, i lose all my star ratings i so carefully manage?

---

### Post by arbulus on 2007-09-17
> **colsinc said:**
> thanks everyone, just a few more Q's

Is it normal for it to take several (about five) seconds for amarok to display when it's been minimised to the system tray?
-(edit)I'm using Ubuntu 6.06, GNOME, P4 3Ghz, 768Mb.  my system does not have to be under stress for this to happen, and it happens even when amarok has been minimised for only a short while (like 2 minutes).
and
Is it possible to somehow backup the scores for each song.  Amarok went weird a couple of weeks ago and I killed it, and it lost all my scores :sad: ?


I was having problems with Amarok when I first installed it (i.e. slow load times, crashing, etc.).  I posted a question in the forums here about it, and it turned out to be a Java issue.  You can see my thread here:
 [http://ubuntuforums.org/showthread.php?t=520482](http://ubuntuforums.org/showthread.php?t=520482)

Hope that helps.

---

### Post by afonic on 2007-09-17
If you already have the MySQL server setup for some other use, use for amaroK as well. If not stay with Lite.

---

