---
title: "Plex media server not seeing media files"
date: 2018-05-05
forum: New to Ubuntu
---

### Post by elliottthomas on 2018-05-05
OK I have all my media files on an internal hard drive. I can see the hard drive in plex but no folders or anything.  I am new to linux.  I am lost LOL  I just want my plex to work like it did in windows.  I refuse to use windows anymore.  Any and all help would be greatly appreciated.

---

### Post by TheFu on 2018-05-05
First, welcome to the forums.

2nd, Linux is a multi-user OS from the ground up.  That means you have to understand file and directory permissions.  Learning them sooner than later will save you days, weeks, months of frustration.

On Unix systems, which Linux is, there are 2 basic types of things. Files and processes.  Everything that isn't a process is a file. Period.  Files have permissions, owners, group membership. This is the core for all Unix system security.  The keyboard is a file.  The screen is a file.  Directories are actually files. All devices are files as far as the OS is concerned. Get where I'm going?  So everything that isn't a process is actually a file. ;)  It makes for an elegant security model and one that is easy to grasp.

Plex usually runs with "plex" as the owner of the process and, as such, it can access files and directories that the "plex" userid can access.  Your personal userid isn't "plex", (let's assume elliot) so if you expect files created by your userid to be available to the plex userid, then you'll need to set the file / directory permissions to allow that.

So there are lots of questions I'd have to ask before providing a direct answer to help you, but it all comes back to file and directory permissions.  I'm assuming you already told the plex system (via a web interface) where the Movies, TV, Music, and Photos were on your HDD.  
Next question is what is the file system being used to store all the media? If it is Linux, then you can just use chmod to allow the plex userid 'read' access to the files. If it is NTFS or one of the other non-Linux file systems, the answer is different. Chmod doesn't work on those.

So, if you can say what the file system is, where the files are located (top level only) and exactly which userid owns all the media files, we can tell you what to type.

BTW, don't expect plex to work the same on Linux as it does on other OSes. There are definitely differences.

---

