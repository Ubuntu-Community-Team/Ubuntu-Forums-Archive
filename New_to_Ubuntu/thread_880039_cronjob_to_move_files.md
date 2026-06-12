---
title: "cronjob to move files"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by AnLGP on 2008-08-04
Hello,

I'd like to move mp3's from one place to another (basically backing them up to another HD) daily.  I know there's a way to setup a cron job to do this and I'd like to accomplish that.

How often would you recommend that I do this?  Daily?  I mean what's realistic here?

Also, this is my first time setting one up so if

/home/steve/music (is the trailing slash necessary?)

is the place that the music is coming from (directory A) and

/media/mediabackup/home/tux/music/

is the place it's going to (directory B), what exactly would I put in if say, I wanted the cron to have it move the files from directory A to directory B every day at 6pm?

This place [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm) seems to have a pretty good example of what's going on exactly but I'm not sure of the commands.  Is it a simple "mv" command?

---

### Post by tamoneya on 2008-08-04
I would use cp instead.  That way you keep the originals where they are. The command would be :```
cp -a /home/steve/music/* /media/mediabackup/home/tux/music/
```

Daily is definitely realistic.  I could even see every couple of hours.  It really depends how often things get updated.

---

### Post by AnLGP on 2008-08-04
Thanks!

That would go after the time increments, correct?

---

### Post by AnLGP on 2008-08-04
Also,

if the files exist already do they get copied over as well?  I don't want duplicates of files that have already been copied.

---

### Post by northern lights on 2008-08-04
> **AnLGP said:**
> I'd like to move mp3's from one place to another (basically backing them up to another HD) daily.  I know there's a way to setup a cron job to do this and I'd like to accomplish that.
Yes you can.

> **AnLGP said:**
> How often would you recommend that I do this?  Daily?  I mean what's realistic here?
Couldn't say. Highly depends on how valuable/unrecoverable the music is and how often you break your system. Weekly?!

> **AnLGP said:**
> I wanted the cron to have it move the files from directory A to directory B every day at 6pm?
Okay.

Whether moving/copying suffices depends on whether you want to have two folders with the same files (you're terming it a back-up makes me think that) or move files from i.e. the download folder to a music one (the idea of using 'mv' leads me to believe this is the case).

In the latter case the job should look like this:```
0 18 * * * mv /home/steve/music/*.mp3 /media/mediabackup/home/tux/music/
```

As an aside: 'mediabackup' is a valid mountpoint?

Should you want them synchronized and only one folder changes:```
0 18 * * * cp /home/steve/music/*.mp3 /media/mediabackup/home/tux/music/
```

If both chang, I'd recommend unison:

Make sure you have the universe repositories enabled. Run```
sudo apt-get update && sudo apt-get install unison unison-gtk
```

Now the cronjob should be:```
0 18 * * * unison /home/steve/music/ /media/mediabackup/home/tux/music/ -auto -ui text
```

For a weekly process: "0 18  * * 6" - every Saturday, 6 p.m.

---

### Post by AnLGP on 2008-08-04
Copying them from one HD to the other is what I want to do.  Yes that is a valid mountpoint.

```
30 * * * * * cp -a /home/steve/music/* /media/mediabackup/home/tux/music/
```

this is what I have.  If I understand it correctly it will take everything from the "/home/steve/music/" folder and put it into the "/media/mediabackup/home/tux/music/" folder every half an hour of every hour of every day, etc?

---

### Post by northern lights on 2008-08-04
> **AnLGP said:**
> 30 * * * * - every half an hour of every hour of every day
Everything correct but this.
This is every hour at half past full. I.e. 00:30, 01:30, 02:30, ...

```
/30 * * * *
```or```
0,30 * * * *
```will do every half an hour.

---

### Post by AnLGP on 2008-08-04
Thanks.  Was the issue the trailing slash in the cron job?  Just trying to clarify for future jobs.

---

### Post by northern lights on 2008-08-04
/X - every value divisible by X

---

