---
title: "Bash script or automation to sort my &quot;documents&quot; folder?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by CJ Master on 2008-11-01
Hello,

I was wondering if there was any macro or such that would automatically create these folders in my "documents" folder, "Music, Movies, Torrents,  Pictures, Documents, Windows" and whenever I download something to the "documents" folder, (Not to be confused with the documents subfolder I just created) It'll automatically move the file to the correct location. For example if I download a .gif then it'll move it to the pictures folder, or If I download a .exe or a .com then it'll move it to the windows folder.

If its bash, please tell me how to install it, i've never used bash before. =[

Thanks kindly for your help!

---

### Post by deconectat on 2008-11-01
bash is a command line interface, not a script. You could write a script in bash to do what you want, but i don't know if you can triger it when you copy a file. You could make it a cron job (so it would run every 5 minutes for example.

The script would be really simple like:
```

cd ~
mv *.jpeg Pictures/
mv *.gif Pictures/
mv *.avi Videos/

```
You get the ideea. You must put this in a text file, make it executable by typing *chmod +x filename* in a terminal (replace filename with the actual name you gave the file), then type *./filename* to run the script.

After you have it working, study *man crontab* to get it to run at specific times.

---

### Post by CJ Master on 2008-11-01
Hey thanks for the help!

It doesn't seem to be working however. I double clicked it and told it to run but it would organize the files I told it too.

Plus I have no idea what crontab is :???:

---

### Post by CJ Master on 2008-11-01
Here, I ran it thru terminal. Here's the rude reply: :P

```
mv: cannot stat `*.jpeg': No such file or directory
mv: cannot stat `*.png': No such file or directory
mv: cannot stat `*.gif': No such file or directory
mv: cannot stat `*.avi': No such file or directory
mv: cannot stat `*.rm': No such file or directory
mv: cannot stat `*.mid': No such file or directory
mv: cannot stat `*.mp3': No such file or directory
mv: cannot stat `*.mp4': No such file or directory
mv: cannot stat `*.wav': No such file or directory
mv: cannot stat `*.doc': No such file or directory
mv: cannot stat `*.rtf': No such file or directory
mv: cannot stat `*.odt': No such file or directory
mv: cannot stat `*.txt': No such file or directory
mv: cannot stat `*.gm6': No such file or directory
mv: cannot stat `*.gmk': No such file or directory
mv: cannot stat `*.exe': No such file or directory
mv: cannot stat `*.com': No such file or directory
mv: cannot stat `*.bat': No such file or directory
mv: cannot stat `*.dll': No such file or directory
mv: cannot stat `*.cfg': No such file or directory

```

Edit: And yes, I have some files in ther (a couple of RTF's and ODT's). And I double-checked my spelling.

---

### Post by deconectat on 2008-11-01
That error means the script is running in the worng directory. I assumed your documents directory is your home directory. cd ~ goes to your home directory; you should replace ~ with the path to your documents directory (like /home/xxx/Desktop).

---

### Post by CJ Master on 2008-11-01
Err. All my files have now flown south for the winter. And there not in my folders...... >.,<

---

### Post by anotherdisciple on 2008-11-01
I think we need more info.... where is this "documents" folder? Is it in your home directory?

The mv syntax is like this:y
mv (options) /path/to/file /new/path/for/file

"~" is a variable that means "home folder"
"*" is a wildcard that means "anything" or "any combination of characters"

So, if you want to move your .jpg files from your home folder to the pictures folder that is in your home folder... it would look like this:

```
mv ~/*.jpg ~/pictures
```

That means "Move any file that is in my home directory that ends with .jpg to the pictures folder in the home directory"


If you want to learn more about this kind of thing... I have a link called "Terminal for Beginners (Updated)" in my signature. It's a thread that I rewrote because it was so helpful to me.


Hope that helps!

---

### Post by CJ Master on 2008-11-01
My documents folder is in the same place that it installs, I belive its home/cjmaster/Documents.

Here's my script:

```
cd ~/Documents/
mv *.jpeg Pictures/
mv *.png Pictures/
mv *.gif Pictures/
mv *.avi Videos/
mv *.rm Videos/
mv *.mid Music/
mv *.mp3 Music/
mv *.mp4 Music/
mv *.wav Music/
mv *.doc Documents/
mv *.rtf Documents/
mv *.odt Documents/
mv *.txt Documents/
mv *.gm6 Documents/
mv *.gmk Documents/
mv *.exe Windows/
mv *.com Windows/
mv *.bat Windows/
mv *.dll Windows/
mv *.cfg Windows/
```

---

### Post by ciscosurfer on 2008-11-01
CJ Master,

Take a look at these two threads; they may be what you're after.

[http://ubuntuforums.org/showthread.php?t=950939&highlight=inotify-tools](http://ubuntuforums.org/showthread.php?t=950939&highlight=inotify-tools)

[http://ubuntuforums.org/showthread.php?t=594669&highlight=inotify-tools](http://ubuntuforums.org/showthread.php?t=594669&highlight=inotify-tools)

An apt-cache search shows various other packages as well:```
incron - cron-like daemon which handles filesystem events
inotail - tail replacement using inotify
inoticoming - trigger actions when files hit an incoming directory
inotify-tools - command-line programs providing a simple interface to inotify
iwatch - realtime filesystem monitoring program using inotify

```

---

### Post by CJ Master on 2008-11-01
Edit: Sorry, for some reason it double posted.

---

### Post by CJ Master on 2008-11-01
cisco, that iNotify looks perfect for what I want, but it looks a bit above my head.

And we probably need to do first things first, 1) where the heck did my files go, and 2) How do i get this script working manually? >.<

---

### Post by CJ Master on 2008-11-01
Eh?! They just suddenly showed up in my home/cjmaster/Documents/Documents folder even though it said there were no items there... odd, but I'm not complaining.

Alright, anyone have any idea how to mod the script to use iNotify?

---

### Post by ciscosurfer on 2008-11-01
Posts 3 and 4 of the first thread-link I posted should get you started.

---

### Post by CJ Master on 2008-11-01
No offense, but that code he gives as an example looks like alien talk to me...

Also, forgive me if i'm mistaken, but it looked like python. Would that work with my bash script?

---

### Post by ciscosurfer on 2008-11-01
It's not python.  A python script will typically start like this (depends on where it's located): #!/usr/bin/python

[sh]("http://en.wikipedia.org/wiki/Bourne_shell") used to point to [bash]("http://en.wikipedia.org/wiki/Bourne_again_shell") in older versions of Ubuntu but now points to [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"), another variation.  You can change #!/bin/sh to #!/bin/bash to make it a bash script instead of a dash script.  I'm not a programmer, so I'm afraid I can't be of much more help here.  You could ask one of the moderators to move this thread over to the Development and Programming area of the forum though.

---

### Post by CJ Master on 2008-11-02
Bump.
Oddly enough I reported but no mods have come...

---

### Post by bapoumba on 2008-11-02
> **CJ Master said:**
> Bump.
Oddly enough I reported but no mods have come...

We have looked and agreed it was better off in ABT. If you really want to have it moved to PT, please send me a PM.

---

### Post by CJ Master on 2008-11-02
Well ok, I don't care, as long as I find some way to do this :P

---

### Post by CJ Master on 2008-11-05
[img]http://www.court-records.net/rips/bubble-objection.gif[/img]

This thread needs to be bumped!

---

### Post by CJ Master on 2008-11-09
Bump. :-)

---

### Post by CJ Master on 2008-11-16
Bump =]

---

