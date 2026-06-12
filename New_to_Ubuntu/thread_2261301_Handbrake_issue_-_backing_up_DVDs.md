---
title: "Handbrake issue - backing up DVDs"
date: 2015-01-17
forum: New to Ubuntu
---

### Post by noobtechninja on 2015-01-17
Hi all.

I want to rip, store and backup some of my DVD collection onto my NAS so that I can
watch them via my Ras Pi and XBMC.

Ideally I'd like to store the files in .MKV or .MP4 format.

I have been ripping my DVDs with mplayer. Then I convert them to .MKV format using handbrake.
(Well I was until two nights ago, then handbrake has decided to stop working).

However since then, handbrake keeps crashing and I cannot convert/transcode
any media with it. Handbrake will load. I will select a file to convert, set up my
desired options. Then whenever I hit the convert button, handbrake will crash and close
the app.

Incidently, I've always had issues with handbrake in the past. And apparently, so do a
lot of Ubuntu users.

I ran the following code in a terminal
```

ghb

```

When I load handbrake, and then try to either select a .MPG file to convert or if I select the source button
I then get the following response in the terminal =
```

Segmentation fault (core dumped)

```

I've just searched in the apport.log files and found the following
```

ERROR: apport (pid 3337) Fri Jan 16 22:53:16 2015: called for pid 3322, signal 11
ERROR: apport (pid 3337) Fri Jan 16 22:53:16 2015: executable: /usr/bin/ghb (command line "ghb")
ERROR:  apport (pid 3337) Fri Jan 16 22:53:16 2015: gdbus call error: Error:  GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name  org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 3337) Fri Jan 16 22:53:16 2015: debug: session gdbus call: 
ERROR:  apport (pid 3337) Fri Jan 16 22:53:16 2015: apport: report  /var/crash/_usr_bin_ghb.1000.crash already exists and unseen, doing  nothing to avoid disk usage DoS

```



Useful info

CPU = AMD-64, 3500+
Ubuntu 12.04
KDE 4.8.5
3 GB of RAM


Any help or advice would be greatfully appreciated.

TIA

---

### Post by TheFu on 2015-01-18
Can't help with the handbrake issue, but mkv and mp4 are not video formats, they are just containers. You can place almost any video codec or/and audio codec files **inside** those containers.  Actually, mkv can hold almost any sort of files inside - text, srt, sub, doc, xls, ... whatever.

Looking at the error messages, perhaps you are running low on storage where handbrake needs temporary space? I dunno.
I'd force a reload of handbrake using **aptitude** and see if that solves the issue. You've certainly already tried to reload it with other, less smart, tools. Perhaps this will help?

I don't think the apport or gdbus issues mean anything.

---

### Post by SeijiSensei on 2015-01-18
Remove the copy of Handbrake you have installed and use the one from John Stebbins's repository:

```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk

```

---

### Post by monkeybrain20122 on 2015-01-18
Maybe I misunderstood but it doesn't make a lot of sense. Why don't you just rip your dvd to mkv directly with handbrake instead of the convoluted way of ripping with mplayer and then transcode with handbrake?

---

### Post by TheFu on 2015-01-18
> **monkeybrain20122 said:**
> Maybe I misunderstood but it doesn't make a lot of sense. Why don't you just rip your dvd to mkv directly with handbrake instead of the convoluted way of ripping with mplayer and then transcode with handbrake?

If handbrake can't handle it, then it is unlikely that vobcopy will (another tool to rip).  I have used ddrescue to clone a troubling DVD first, then thrown handbrake at it with success, mostly.

---

