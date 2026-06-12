---
title: "Programmatically Create Popup"
date: 2007-09-12
forum: Programming Talk
---

### Post by SuperMike on 2007-09-12
My daughter is a very quiet teenager who likes to lock her door and work on her Ubuntu for a class project. Sometimes she asks me to fix something and, instead of bothering her, I hop on her system via SSH and control it remotely.

There's come a time, however, where I need to tell her something but she's got her MP3 player running on her headphones, her door is locked, and she's in her zone during her class work. Some may say I'm not being a good parent by letting her leave the door locked like that, but she makes A+ grades, wins Mock Trial awards, and is planning on becoming an attorney someday. She also does quite a bit of chores around the house and is very mature for her age. She's a delightful girl and so I reward her with privacy when she needs it.

Anyway, I need to pop open a dialog in her GUI remotely via SSH. What's the trick to do that, programmatically or via a Bash script or some extra application? She's running Ubuntu Feisty with GNOME desktop.

I know that I can use zenity and dialog, but I don't know how to pop it into her X session while she's using it.

Some may say, give her email or install Gaim, but her system has limited RAM (for now -- I'm getting her a laptop soon) and she has no need for those things and merely browses the web or does her homework. So I need some other way to pop open a dialog in her X Windows session.

---

### Post by dwhitney67 on 2007-09-12
The easiest way (and I think you already know this) is to pop up an xterm.  However, I recommend that you spawn a program within the xterm, otherwise your daughter would have access to the shell prompt of the user that is launching the xterm.

The trick to allow one user to display an xterm or any other X11 window is to get the user (who has a lock on the display) to issue this command:

[FONT="Courier New"]$ xhost +[/FONT]

Once this is done, then any user who sets up their DISPLAY environment variable to reference the main screen can pop up a window.

[FONT="Courier New"]$ export DISPLAY=:0.0
$ xterm &[/FONT]

If you require fancier pop-ups, then you could consider using GTK+ or something similar.

All this is moot unless you can get your daughter to enable xhost.

---

### Post by mridkash on 2007-09-12
If you can open her computer remotely then is it possible that you open up gedit on her pc and type message. 
I dont know about SSH but I use reverse VNC to do that.

---

### Post by fct on 2007-09-12
If you are connecting from a linux host too, then you can start with "ssh -X user@daughtercomputer" and remotely launch X programs that way in your own X server.

There might be some problem with permissions, in that case try "ssh -Y" or copying the .Xauthority from the home directory of the user that connected with SSH. That works when, for example, you are using sudo to start a graphic application as a different user.

---

### Post by pmasiar on 2007-09-12
wall == write all shell command?

[http://docsrv.sco.com/cgi-bin/man/man?wall+1M](http://docsrv.sco.com/cgi-bin/man/man?wall+1M)
[http://proquest.safaribooksonline.com/0130277010/ch22](http://proquest.safaribooksonline.com/0130277010/ch22)
[http://esofthub.blogspot.com/2007/07/send-message-to-users-with-write-all.html](http://esofthub.blogspot.com/2007/07/send-message-to-users-with-write-all.html)

---

