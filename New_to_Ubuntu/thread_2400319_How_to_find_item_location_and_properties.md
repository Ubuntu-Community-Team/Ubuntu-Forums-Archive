---
title: "How to find item location and properties"
date: 2018-09-04
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2018-09-04
Ubuntu 18.04 with Gnome 3 desktop in a virtualbox vm

Until I am more comfortable with the command line I am still living in the gui. Below is an image of my desktop which is pretty standard. In windows (from which I come) I can _right click_ on an icon or anything else and I get a _context_ menu with useful options such as *properties, rename, file location, etc*. about that object. But, in Gnome, if I  right click on (for example) "Applications" in the top bar it just starts the application. There is no difference between using the right or left mouse buttons. There has to be a Linux way to find out information about an item. Like **_which app started it_**? **_Where is it located_**? How can I **_configure it (its settings)_**. Etc.

How does one do those things in Ubuntu's gui?

Similar question: Right clicking on the desktop brings up a context menu with small group of options. In Windows I can **modify this context list** and add to it. How does one do that in Ubuntu?

Thank you.

---

### Post by sporksrule on 2018-09-05
See this tutorial to fix right click in ubuntu 18.04: [https://itsfoss.com/fix-right-click-touchpad-ubuntu/](https://itsfoss.com/fix-right-click-touchpad-ubuntu/)

---

### Post by lordfrikk on 2018-09-06
This is more of a general answer that doesn't specifically talk about the Gnome (or any other) GUI because I think it might be more useful for you. Why? Because right now you might be using Gnome, then later you'll decide you want to try something else and what you know will no longer apply.

In short, in Linux command line is king. If you learn in, the knowledge will never go to waste, no matter what distro you're using. You can always ask here or somewhere else but in most cases the information is already there at your fingertips. With that said...

The **ps** command is used to find out about process, including how it was started and who "owns" it (usually the user that launched the process). More information (this is just an online version of the man database I mention below, so you can read it only your computer, too): [http://man7.org/linux/man-pages/man1/ps.1.html](http://man7.org/linux/man-pages/man1/ps.1.html)


The aptly named **find** command can help you find any file in the system; it's very configurable and it allows you to only find files, only directories, only files of certain size or newer than a specified time etc. Example:

> find / -iname "sshd_config"

This will find the file named "sshd_config". It will start at root ("/") and doesn't care about case (-iname is case-insensitive, -name is case-sensitive). More info: [http://man7.org/linux/man-pages/man1/find.1p.html](http://man7.org/linux/man-pages/man1/find.1p.html)

If you want something easier, most systems have a **locate** command that is much simpler to use but not as powerful. To do the previous search with locate:

> locate sshd_config

If you're sure the file exists but locate cannot find it, it's possible its database needs to be updated (this also happens with newly created files, because the update is usually run only on startup). To update, do:

> sudo updatedb

More info: [http://man7.org/linux/man-pages/man1/locate.1.html](http://man7.org/linux/man-pages/man1/locate.1.html)

As to your third question, this varies quite a bit from program to program, but usually the config files are in **/etc/** or **/usr/share/**. Sometimes they can have user-specific settings in your home directory. The almost-guaranteed way to find out is the most useful command for anyone using Linux: **man**.

The **man** command will display a manual of a specific command or topic. If you want to know how to configure ssh on your system, you can just do "man ssh" and go from there. The information will probably be written in the section Configuration Files. If not, at the very bottom of the man output, you can see related files. Among them are usually links to other topics like configuration files.

Last but not least, if you're not even sure *what* command you're supposed to run, try searching with **man -k**. This searched the man database not only for names but also description. If you term is generic enough, you're bound to find something that will get your started.

[http://man7.org/linux/man-pages/man1/man.1.html](http://man7.org/linux/man-pages/man1/man.1.html)

I'm sorry if this is not exactly what you asked for but hope it helps in some way.

---

### Post by ubantunovice2 on 2018-09-07
Thank you lordfrikk. Actually that is exactly what I was looking for. The linux way of doing things. The linux equivalent to what I can do in windows. The various linux guis are obviously not as mature or complete as the windows GUI and it is frustrating to repeatedly rediscover that fact or pretend they can duplicate the windows GUI in all respects. They can't. 

Thank you for taking the time to point me in the right direction.

---

### Post by DuckHook on 2018-09-07
> **ubantunovice2 said:**
> Thank you lordfrikk. Actually that is exactly what I was looking for. The linux way of doing things. The linux equivalent to what I can do in windows. The various linux guis are obviously not as mature or complete as the windows GUI and it is frustrating to repeatedly rediscover that fact or pretend they can duplicate the windows GUI in all respects. They can't. 

Thank you for taking the time to point me in the right direction.
You may wish to have a look at the links in my sig. Start with "Linux is not Windows" which will provide important context to your complaint that Linux doesn't do things precisely the Windows way. The other link: "Resources for Newcomers" will provide you with more guides, manuals and references than you can shake a stick at. Some of those references will give you alternate ways of achieving what you have been habituated to do in Windows.

Those of us who have been power users in both the Windows and Linux world generally agree that Linux is far more powerful and versatile for the power user than Windows. Windows is very confining to users for a good reason: it cannot risk letting users run wild because, since it charged you money, it generally has to support your screw-ups. Linux was developed by geeks for geeks and as a result will let you do anything you want to your system. You have complete freedom to do as much tweaking, customizing or damage as you want. There are users on this forum who spin their own personalized custom desktop environments—something that is just not possible in the proprietary world. When it comes to sheer power and flexibility, there are few other OSes that can match Linux.

Much of that power and flexibility is in the command line. For a good command line reference, see: "A Great CLI Guide".

---

### Post by Geoffrey_Arndt on 2018-09-07
OK Ubuntu Novice . . . in Linux, "properties" are displayed based on the "file" . . . . everything is a "file".   That's where you can right click any file in Linux to discover the properties.   In other words, open the file manager (Nautilus for instance) and start looking at files that are different types (called "mime" types in Linux) and right click those files. 

    Further, if you load a menu-manager program like "alacarte" - that program will provide the gui screens indicating where the exec (bin) is located, how to set up a command to start the program etc.   You can also right-click on "Devices" (in XFCE, you will find many desktop icons auto loaded, and can then right click disks, printers, etc. to obtain additional info.   Ditto for Budgie DE). 

   Ubuntu Unity and Gnome3 DE's don't allow those kinds of icons on the desktop without major hacks.   I haven't run KDE in ages, but I'm pretty sure there are tons of files, devices, etc. that display on that desktop, all with gui "discoverable properties" displays. 

One really nice additional bit of info Linux provides (that Windows doesn't) are all the "Ownership" details of a file, indicating who can run the file, view and/or change the file  . . etc.)  **That stuff is invaluable to know (and Windows lacks this capability out-of-the-box!   That's one reason why malware writers love Windows.**

---

### Post by ubantunovice2 on 2018-09-11
Thank you all very much. I really appreciate the help.

---

