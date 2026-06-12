---
title: "Where do I install a new application ?"
date: 2005-09-23
forum: Packaging and Compiling Programs
---

### Post by Michele Moglia on 2005-09-23
I wrote a gnome application made by one executable file,
some text files, some pixmaps and some wave files.
I have now to decide where to install the application
I read the document FHS Filesystem Hierarchy Standard 
([http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) ) but I have not understood 
where to put my files:

/opt/myapp/bin
/opt/myapp/pixmaps
/opt/myapp/data
/opt/myapp/audio

or 
/usr/share/myapp/pixmaps
/usr/share/myapp/data
/usr/share/myapp/audio

or
/usr/local/usr/

or ???

Can someone resolve my doubts ?  :? 
Thanks for any help.

---

### Post by bsussman on 2005-09-23
According to [http://www.pathname.com/fhs/]("http://www.pathname.com/fhs/")

I think /usr/local is the appropriate place.

but whether it belongs in a tree that includes share (/usr/local/share) depends on the nature of the code - architecture independent or not...

---

### Post by Michele Moglia on 2005-09-23
Ok : /usr/local

[B]Option 1
[/B]
but if I want to keep different parts of application together so:
Have I to make a subdirectory under /usr/local ?
/usr/local/myapp
and under this  ?
/usr/local/myapp/pixmap
/usr/local/myapp/data
/usr/local/myapp/audio

but under /usr/local there are not any subdir like myapp !

**Option 2**

So I have to put the executable in /usr/local/bin

and the other file which are platform indipendent in
/usr/local/share/myapp/pixmap
/usr/local/share/myapp/data
/usr/local/share/myapp/audio

Is this last one the right option ?


Thanks!


Michele

---

### Post by bsussman on 2005-09-23
First glance, your conclusion seems right.

If this app is for distribution, this matters. 


If it is your own tool or toy, just for yourself, consistency is more important than actual name.

---

