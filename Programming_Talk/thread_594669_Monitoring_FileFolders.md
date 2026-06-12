---
title: "Monitoring File/Folders"
date: 2007-10-28
forum: Programming Talk
---

### Post by ThomThom on 2007-10-28
Hi.
I'm pretty fresh with Ubuntu and Linux.

My background is with PHP, VB, (Some basic C#), JS and Windows Scripting.

I want to create an application or script that will monitor a folder (and it's subfolders) for activity, then perform some actions and store some data in a database.

On Windows there's WMI that let you set up the system to call back functions in your WScript whenever a file or folder is changed.

I'm looking for something similar on Ubuntu.

I know that FileSystemWatcher in .NET and that it exists in Mono. I've installed MonoDevelop and I'm looking into it.

But is there some script like languages in Ubuntu that I can do this with? So that I don't have to compile the application or invoke such a large framework?

I plan to make an PHP application frontend for the data stored in the database so connectivity with MySQL in some way is required as well.

---

### Post by ilautar on 2007-10-28
Use inotify kernel interface.

en.wikipedia.org/wiki/Inotify
[http://www-128.ibm.com/developerworks/linux/library/l-inotify.html](http://www-128.ibm.com/developerworks/linux/library/l-inotify.html)

---

### Post by ghostdog74 on 2007-10-28
you can
1) design your own shell scripts
2) turn on auditd
3) use tools like tripwire.

---

### Post by ThomThom on 2007-10-28
> **ilautar said:**
> Use inotify kernel interface.

en.wikipedia.org/wiki/Inotify
[http://www-128.ibm.com/developerworks/linux/library/l-inotify.html](http://www-128.ibm.com/developerworks/linux/library/l-inotify.html)

And what can I use to interact with Inotify? Shell script? Phyton? Or does it have to be C or some other programming language?

---

### Post by wolfbone on 2007-10-28
Have you searched for inotify in the available packages? I expect pyinotify and inotify-tools are probably there - maybe others.

---

### Post by ThomThom on 2007-10-28
Yea, I've looked at Inotify and I've installed pyinotify. Seem to be a usable solution. I just need to quickly make myself familiar with Python.

Thanks for the suggestions folks. Keep them coming if you got more.

---

### Post by pmasiar on 2007-10-29
wiki in my sig will get you all links to start with Python. Welcome aboard!

---

### Post by ThomThom on 2007-10-29
Thanks for that link. Looks interesting.
Now I'm back at getting my hands to not automatically drop in them curly brackets and semi-colons. :)

---

