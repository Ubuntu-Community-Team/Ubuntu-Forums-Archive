---
title: "Problems extracting tar.gz file"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by pgslmatias on 2014-07-04
Hello guys. I started reading a Byte of Python which recommended Light Table as a text editor for beginners. So i download it and it comes in a compressed tar.gz file. I right click on the icon and press extract here. But it doesn't work right. Is there a command that i can use to extract tar.gz files?

---

### Post by ian-weisser on 2014-07-04
> **pgslmatias said:**
> But it doesn't work right.
What does that mean?
Exactly what happened?

There are *many *fine text editors already in the Ubuntu Repositories...including one that was probably installed with Ubuntu.

For example, gedit is a fine text editor, quite suitable for beginners (I learned on it), and already included with the default install of Ubuntu.

---

### Post by pgslmatias on 2014-07-04
When I say it doesn't work right I mean that apparently everything is ok, a new folder apart from the compressed one appears in my desktop but nothing is decompressed. The actual application of the decompressed text editor looks like this (a picture I took from google images):[ATTACH=CONFIG]254471[/ATTACH]However, my decompressed application looks like this[ATTACH=CONFIG]254472[/ATTACH]. Btw, I downloaded Light Table for windows (my computer has dual boot windows 8.1 and ubuntu 14.04 64 bit), decompressed it and it worked the way it should, being that it looked like the first picture. However, I prefer using ubuntu and I only use windows when necessary so I'd like to be able to use Light Table in ubuntu.
Thanks for your help :)

---

### Post by yancek on 2014-07-04
The site below explains how to extract a tar.gz file from a command line, also has some examples.  There are lots of sites like this if you do an online search.

[http://www.cyberciti.biz/faq/linux-unix-bsd-extract-targz-file/](http://www.cyberciti.biz/faq/linux-unix-bsd-extract-targz-file/)

---

### Post by pgslmatias on 2014-07-04
It didn't work this is the output[ATTACH=CONFIG]254473[/ATTACH]. Thanks again for your help. I'm also thinking, if this doesn't work, about using gedit as my text editor. Does it include syntax highlighting for python?

---

### Post by slickymaster on 2014-07-04
> **pgslmatias said:**
> <...snip...> Thanks again for your help. I'm also thinking, if this doesn't work, about using gedit as my text editor. Does it include syntax highlighting for python?

Yes, Gedit supports syntax highlighting for python. It doesn't have many features out of the box, but is very simple to use. It can be extended with plugins. There is a set of plugins that can be installed from the [gedit-plugins]("https://live.gnome.org/Gedit/Plugins") package.

---

### Post by ian-weisser on 2014-07-04
The error message seems pretty clear to me.
> Cannot open: No such file or directory
You downloaded the tarball to a different directory than you perhaps expected.
You can easily move it to the directory you wish, and try again.

---

### Post by pgslmatias on 2014-07-04
Does geddit support indentation of the text?

---

### Post by slickymaster on 2014-07-04
I don't know if it has automatic indentation, I use Geany myself, but yeah it does support indentation.

---

### Post by yancek on 2014-07-04
Did you get the files extracted?  Your image in post 5 clearly shows you are running from your user home directory while the default directory for downloads is coincidentally enough, Downloads.

---

