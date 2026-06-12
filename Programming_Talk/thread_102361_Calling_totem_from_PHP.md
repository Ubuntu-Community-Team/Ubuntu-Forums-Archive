---
title: "Calling totem from PHP"
date: 2005-12-11
forum: Programming Talk
---

### Post by pr0fess0r on 2005-12-11
Hi
I have a PHP page on Ubunutu 5.10 and I want it to call totem for me like this:
/usr/bin/totem --fullscreen /dev/dvd/MOVIE
This works fine from the shell, no sudo needed
From PHP I try to call it like:
$command=@exec("/usr/bin/totem --fullscreen /dev/dvd/MOVIE");
But nothing happens and no error is returned, safe_mode is off in php.ini

Can anyone suggest where to look to resolve the problem or what it might be?
cheers

---

### Post by pr0fess0r on 2005-12-12
Here's what the Apache error log says:

Xlib: connection to "unix:1000.0" refused by server

Xlib: No protocol specified

(totem:11508): Gtk-WARNING **: cannot open display:

---

### Post by pr0fess0r on 2005-12-12
So how do I allow www-data to open a display so that I can use php to start programs?

---

### Post by skirkpatrick on 2005-12-12
Are you trying to run totem on the server or on the client?  Client-side makes the only sense and you won't be able to arbitrarily launch any program you want on the client-side from a webpage.  If you are wanting to embed a video in a webpage, I haven't figured that one out although there are plenty of sites that do it.

---

### Post by pr0fess0r on 2005-12-12
Hi
I'm trying to run totem from the pc, ie not remotely. I'm logged in and I could just pop up a temrinal and type the commands, the reason I want to run it via PHP is I have a MySQL database of video files on my hard drive. I'm wiring the computer up to my tv and using a wireless keyboard so i can play movies fro the comfort of my sofa:) I want to be able to search for a movie then just click a link to start it playing fullscreen in Totem.
Where I'm at now is I have given www-data sudo right to /usr/bin/totem in sudoers: I added www-data to sudoers i.e. www-data ALL=/usr/bin/totem

My php file now calls xhost +, i.e.
$command1=@exec("xhost +");
$command2=@exec("sudo /usr/bin/totem --fullscreen /dev/dvd/MOVIE");

In the apache error log I get:
xhost: unable to open display **
(totem:8226): Gtk-WARNING **: cannot open display: 0.0

So it's not quite there yet... any ideas?

cheers

---

