---
title: "[HOW-TO] Make a movie preview with frames from the movie"
date: 2007-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Tristan_F on 2007-04-27
I don't know if the title is explicit enough.

A friend of mine asked me if it was possible to do this under linux. He uses a software which can do the same under Windows...So, I made a small bash script to allow to extract frames from a movie and combine them into a single picture to make a preview of the movie. 
I hope this script could be useful to other people.

Usage is as follow framegrabber [-n number of frames to extract] [-s size of the frames] video_file

Here it is what it looks like on the first movie ever made by the Lumiere brothers

[IMG]http://tristan.ferroir.free.fr/tmp/Lumiere2.jpg[/IMG]


Script can be found on this page [[COLOR="Blue"]_here_[/COLOR]]("http://tristan.ferroir.free.fr/Linux.php")

---

### Post by derekguy on 2007-05-27
Many thanks for this great how to. This is a handy little script that works fine for me (2.6.20-15-generic on i686)

The How to is explicit enough for me ;)

---

### Post by Tristan_F on 2007-05-28
Thank you for the feedback. I'm glad someone find it useful.

This script is a litlle bit like imagegrabberII but for Linux or so is what my friend says

---

### Post by bobbocanfly on 2007-05-29
Thanks for this! Really useful for showing quality of downloads and stuff. Really easy to use too.

EDIT: Found a bug of sorts in the code, if you type 'framegrabber' into the terminal it should return an error (as there is no specified video file) but it attempts to grab frames from the non existant file

---

### Post by Tristan_F on 2007-05-30
Thank you for pointing this error.

This is now fixed. I am glad that you find this little script useful too. The first time, this post was a little bit ignored it seems

---

### Post by i M@N on 2007-05-30
Hello.

That roxX ! many thnxX !!

@+...

---

### Post by Tristan_F on 2007-06-01
Thanks.

If anyone is eager or have free time to make a graphical interface (just browsing to the file, choosing the number of stills and the stills width), it would be great

---

### Post by Tristan_F on 2007-06-11
Just to let you know I slightly modified the script to make it "without sound". The previous script was outputting the sound of the movie when used. This is now fixed.

Comments of users are still welcome

---

### Post by bobbocanfly on 2007-09-11
If anyone is interested i made a pseudo-gui version using Zenity called framegrabgtk

[Sourceforge Page]("http://www.sourceforge.net/projects/framegrabgtk")

---

### Post by protenniser on 2008-02-01
Thanks mate, been searching for this for a long time. Very good script....

---

### Post by back2arie on 2009-12-01
Thanks mate.
Really simple and easy to use.

---

### Post by mutrox on 2010-02-09
Thanks a lot :) this script is very handful :)

---

