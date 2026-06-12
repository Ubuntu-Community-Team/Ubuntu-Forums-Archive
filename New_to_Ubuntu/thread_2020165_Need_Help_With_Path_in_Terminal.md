---
title: "Need Help With Path in Terminal"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by onaridge on 2012-07-07
I am not exactly a beginner but it's been awhile since I tried to anything technical in Ubuntu and I am forced to use a Windoze computer at work. I have forgotten how to write paths properly and Googling hasn't been any help. I need to install subsonic again and the directions on the site said do this: 

[LIST]
[*][Download]("http://www.subsonic.org/pages/download.jsp") the Subsonic .deb package and install it: sudo dpkg -i subsonic-x.x.deb
[/LIST]
 I wrote to the app developer for help when I typed the above into the terminal and got this:

$ sudo dpkg -i subsonic-x.x.deb
dpkg: error processing subsonic-x.x.deb (--install):
  cannot access archive: No such file or directory
Errors were encountered while processing:
 subsonic-x.x.deb

He said Please replace "[FONT=monospace]subsonic-x.x.deb" [/FONT]with the full path of the file you downloaded.

The file is here: 

/home/windyridge/Desktop/Downloads/subsonic-4.6.deb

What_ exactly_ should I type because what I typed didn't work. I know I have typed the path/command wrong somehow.

---

### Post by mgmiller on 2012-07-07
```
sudo dpkg -i /home/windyridge/Desktop/Downloads/subsonic-4.6.deb
``` 

When the dev said subsonic-x.x.deb the "x's" refer to the version number of file.  In this case 4.6.

When you literally put in the command:
sudo dpkg -i subsonic-x.x.deb
It could not find the file because no file of that name exits.

As a shortcut, you can substitute the tilde key"~" for the /home/windyridge part so another way to type the command would be:

```
sudo dpkg -i ~/Desktop/Downloads/subsonic-4.6.deb
```

Hope this helps  :popcorn:

Edit:

You realize you can also just double click the subsonic-4.6.deb file and it will run the installer for you graphically.  It will prompt you for your sudo password before installing anything.

---

### Post by onaridge on 2012-07-07
Yes it worked, thansk so much! And thanks for the very quick response!):P

---

### Post by mgmiller on 2012-07-07
You're welcome....

---

### Post by onaridge on 2012-07-10
Well eveything worked and then stopped. All of a sudden my Subsonic server stopped working and wouldn't even load. The router port and IP's all are fine. I changed nothing. I decided to reinstall the server and then got this error.

 java.lang.OutOfMemoryError

is this the program or Ubuntu? Basically subsonic streams all my music to my android phone. The server stopped working and now nothing. :(

---

### Post by onaridge on 2012-07-10
Better error printout:



eption         java.lang.OutOfMemoryError     Message         Java heap space     Java version         Sun Microsystems Inc. 1.6.0_24     Operating system         Linux 3.2.0-26-generic-pae     Server         jetty-6.1.x     Memory         Used 96 of 96 MB     Stack trace         java.lang.OutOfMemoryError: Java heap space

---

### Post by onaridge on 2012-07-10
How do I uninstall this program? I think that's what I need to do.

---

### Post by azmyth on 2012-07-10
sudo dpkg -r subsonic

or

sudo dpkg -r subsonic-4.6

---

### Post by onaridge on 2012-07-10
Thanks. I think a Java update may have broken it. Is there a way to roll back to a previous Java? I have 12.04 LTS.

---

### Post by mgmiller on 2012-07-11
This is apparently a known issue.  Take a look here for clues to add memory to java:
[http://forum.subsonic.org/forum/viewtopic.php?t=6291%29](http://forum.subsonic.org/forum/viewtopic.php?t=6291%29)

---

