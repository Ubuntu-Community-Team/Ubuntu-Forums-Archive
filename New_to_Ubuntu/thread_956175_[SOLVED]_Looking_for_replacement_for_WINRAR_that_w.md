---
title: "[SOLVED] Looking for replacement for WINRAR that will extract partial files."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-10-22
I'm new to Ubuntu and am looking for software with a GUI that will enable me to do this: Let's say there's a one hour video file broken up into 30 parts (RAR). I want to be able to download just part #1, extract that piece (which would include just the first 2 minutes of the video), and watch that part of the video using VLC. After watching the first two minutes, I'd decide whether I want to download the rest, depending on video/sound quality, or whatever. In XP I use WINRAR for that. Is there anything for Ubuntu that will enable me to extract just the first part of a video? Thanks.

---

### Post by tCarls on 2008-10-23
You should just be able to right click on the file and select extract if you have rar and unrar installed (run "sudo apt-get install rar unrar" if you don't). However, there's a bug that keeps it from working if you don't have the complete archive ([http://bugzilla.gnome.org/show_bug.cgi?id=504584](http://bugzilla.gnome.org/show_bug.cgi?id=504584)). Hopefully it will be fixed soon. Until then you may need to use the command line (unrar e file.rar -kb), sorry.

---

### Post by Hexagoon on 2008-10-23
I'm pretty sure that rar dont magically take the first part of the movie and puts it in the first archive. That makes this slightly impossible i think :P

---

### Post by bobsmith2 on 2008-10-25
> **tCarls said:**
> You should just be able to right click on the file and select extract if you have rar and unrar installed (run "sudo apt-get install rar unrar" if you don't). However, there's a bug that keeps it from working if you don't have the complete archive ([http://bugzilla.gnome.org/show_bug.cgi?id=504584](http://bugzilla.gnome.org/show_bug.cgi?id=504584)). Hopefully it will be fixed soon. Until then you may need to use the command line (unrar e file.rar -kb), sorry.

Thank you tCarls! I used the command line and that does the job. I never would have figured out how to do that without your help - plus it forced me to learn how to change directory in the command line, which I haven't needed to do before. The days of using DOS, years ago, came in handy for that - it's very similar. Your help is appreciated.

---

### Post by powermonkey on 2009-01-27
I know this is way after the fact, however VLC is able to play movies which are compressed in RAR, it will do exactly what you want, which is decode the first file of the movie and let you watch it.  It only works on the first file (i.e. .rar), all remaining files (.r00, r01, etc.) will give you an error, since they do not contain the video header.

---

