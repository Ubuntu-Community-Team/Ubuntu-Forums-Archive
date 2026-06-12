---
title: "Basic scripting/cron jobs"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by sindre2 on 2013-10-02
Hi,

I'm trying to learn how to set up a cron jobs or scripts that automates some stuff for me. Does anyone know of a good site for learning more about how to create your own cron jobs and scripts? I've been googling quite a bit, but can only find ultra-specific howtos, like rsync stuff.

Cron job 1:
Video files converting:
1) Monitor /folder1 for videofiles
2) Using ffmpeg or mencoder to convert the files to stereo audio and 480p
3) Move the converted files to /folder2

Cron job 2:
Delete non-mp3 files
1) Monitor /folder3 for non-mp3 files
2) Delete them

Script
1) Let user select working folder
2) Let user write what should be removed from filename of all files within folder

---

### Post by sudodus on 2013-10-02
Welcome to the Ubuntu Forums :-)

Search the internet for cron tutorial or crontab tutorial

Shortcut: start checking these links

[http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/](http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/)

[http://www.pantz.org/software/cron/croninfo.html](http://www.pantz.org/software/cron/croninfo.html)

---

### Post by Lars Noodén on 2013-10-03
cron just runs whatever program(s) you point it at so you could really just look for basic shell scripting guides.  

[list]
[*] [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[*] [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[*] [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[*] [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)
[/list]

About script #1, you might consider using inotify and incron instead of cron.  inotify watches a specific directory or file and runs a script when the watched item changes rather than at a preset time. 

About script #2, that can also be done with incron.  But the action of the script can be done with [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html) -- if the MP3 files are all named in a  uniquely identifiable way, such as ending in .mp3

Get the scripts working manually then move them over to cron or incron.

---

