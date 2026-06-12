---
title: "Setting up a client-server coding environment..."
date: 2005-09-07
forum: Programming Talk
---

### Post by Paul Bramscher on 2005-09-07
Here's my situation: I'm a professional LAMP coder, and just switched from Windows XP to Ubuntu as my development box and do work on a big Solaris server.  What's a good arrangement for coding PHP?

* My PHP programs are big (like 30,000+ lines).  vi is the stone age -- I need something more modern.
* I need a full GUI with cut-and-paste at the bare minimum.
* I need PHP syntax highlighting.
* I don't want to be goofing around with command-line sftp/scp to move things back and forth.
* I can't make changes to the Solaris config, and the sysadmin probably won't do anything to help me.

Here's what I've come up with:
You can go into Konqueror on KDE and type "sftp://xxx.xxx.xxx.xxx" to open a connection to a remote server.  Or you can use Kate and open a file by typing "sftp://xxx.xxx.xxx.xxx" to its location.

Anyone else have thoughts?  Remember my restrictions above.

-Paul Bramscher

---

### Post by vasdee on 2005-09-08
I recommend SCREEM as the IDE of choice, sounds like it will have everything you need. Maybe consider bluefish too, i've come across a few bugs with the current package of screem (version 0.12) and i think bluefish might be more stable. 

I personally mount my remote filesystems (with gnome)  and work directly to the remote server - saving the project files and everything to the server- Screem handles this very well. 

The other option is setup a local mysql-php setup and do all dev locally then when you are ready you can upload the files to the remote server - again screem does this well.

---

### Post by Paul Bramscher on 2005-09-08
[QUOTE=vasdee]I recommend SCREEM as the IDE of choice, sounds like it will have everything you need. Maybe consider bluefish too, i've come across a few bugs with the current package of screem (version 0.12) and i think bluefish might be more stable. 

I personally mount my remote filesystems (with gnome)  and work directly to the remote server - saving the project files and everything to the server- Screem handles this very well. 

The other option is setup a local mysql-php setup and do all dev locally then when you are ready you can upload the files to the remote server - again screem does this well.[/QUOTE]

How do you mount a remote file system (for example, a Red Hat box) with Ubuntu?  I try something in a format like this:

mkdir {some mount point}
mount xxx.xxx.xxx.xxx:/home/myaccount /{some mount point}

And get this complaint:
mount: RPC: Program not registered

---

### Post by Shen on 2005-09-08
> **Paul Bramscher]* My PHP programs are big (like 30,000+ lines).  vi is the stone age -- I need something more modern.
* I need a full GUI with cut-and-paste at the bare minimum.
[/QUOTE]
I don't know why you don't want a vi-like editor when vim does all you ask for said:**
> 
You can go into Konqueror on KDE and type "sftp://xxx.xxx.xxx.xxx" to open a connection to a remote server.  Or you can use Kate and open a file by typing "sftp://xxx.xxx.xxx.xxx" to its location.

Vim can do this: ":e sftp://xxx.xxx.xxx.xxx" and it will open up the connection and file for you.

---

### Post by LordHunter317 on 2005-09-08
[QUOTE=Paul Bramscher]How do you mount a remote file system (for example, a Red Hat box) with Ubuntu?  I try something in a format like this:

mkdir {some mount point}
mount xxx.xxx.xxx.xxx:/home/myaccount /{some mount point}

And get this complaint:
mount: RPC: Program not registered[/QUOTE]That means the remote system isn't running NFS.  What filesystem does it use to export shares?

---

### Post by Daniel G. Taylor on 2005-09-08
Your current solution doesn't seem to conflict with any of your listed restrictions...

What exactly don't you like about Konq + Kate? (or Nautilus + Gedit for GNOME users like me) Are you asking for a different editor? A better way to access the files on the server?

---

### Post by Paul Bramscher on 2005-09-09
[QUOTE=Daniel G. Taylor]Your current solution doesn't seem to conflict with any of your listed restrictions...

What exactly don't you like about Konq + Kate? (or Nautilus + Gedit for GNOME users like me) Are you asking for a different editor? A better way to access the files on the server?[/QUOTE]

For instance, KDevelop will complain if you try to open a non-local file with the method I explained above.  A regular mount should render that transparent, and all applications will be able to talk to it, command-line scripts, etc.

But I found something interesting with KDE just yesterday -- just add a "Network Folder" via Konqueror and the "fish" protocol.  I think KDevelop still complains when opening a distant file, but it seems to offer more functionality than just making a bookmark to an sftp location.

In Konqueror, type "remote:/" or else click the "System" icon in the taskbar, and then "Remote Places".  Kate is happy with it.  But if you're using Bluefish, the file-open dialog doesn't seem to allow for that protocol.  So, again, a mount would be superior.  To open a file with Bluefish, you need to first establish a network folder with Konqueror, then right-click it or set up the file extension so that Bluefish is happy with it, but you can't open distant files remotely with Bluefish's own file-open dialog -- at least not that I found.

---

