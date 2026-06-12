---
title: "QDM - A New Download Manager"
date: 2009-04-26
forum: Programming Talk
---

### Post by montamer on 2009-04-26
Hi 
Just wanted to mention that i have been working on a Download Manager, 

I haven't found any good GUI download accelerator. And i frequently use axel(with gnome-terminal) along firefox ; and its pain to have many windows opened at a time. And i have to save the url somewhere if i want to pause and start the download later.
So i thought of making my own :KS

**QtDownloadManager**
-which is a frontend for many console download accelerators available for linux. like
1) axel
2) proz
3) wget etc ......

Its written in QT, The basic interface and functions are done.
It also works with FlashGot addon in firefox.
I only integrated axel so far. Others are yet to be done :guitar:

Im not at all good at programming, and you might face some problems using it.(so be careful :lolflag:). I have learned alot about Qt writing this :D,

Im uploading the source,binary and configfiles; You are welcome to try it. And please report any problem or bugs you face here or in my blog.

[B]_If you want to use it_
1)U have to install axel seperately and change its config file according to the settings u prefer.
2)Untar the QtDownloadManager_configfiles.tar.bz2  in home directory. (it contains a folder with "." so u might not see it)
3)edit this file "~/.QtDownloadManager/defaults" and keep your own download folder
4) compile the program with "qmake && make" (u need qt4 libraries to compile the program) and place the binary in PATH

[/B]U can modify the code and please mention any changes  , so i can improvise :popcorn: for next time.

[B]Any Comments are welcome.
[/B]
MyBlog : [http://montamer.blogspot.com](http://montamer.blogspot.com)

Here is a quick view of the gui. :P

[IMG]http://1.bp.blogspot.com/_HV1n4ZofRwQ/SfRjW5mD31I/AAAAAAAAAL0/J3ZgcwACZqU/s1600-h/qdm1.png[/IMG]
[IMG]http://1.bp.blogspot.com/_HV1n4ZofRwQ/SfRjia3lq1I/AAAAAAAAAL8/q1dlICe7j44/s1600-h/qdm2.png[/IMG]

---

