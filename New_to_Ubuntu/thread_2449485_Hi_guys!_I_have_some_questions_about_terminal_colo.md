---
title: "Hi guys! I have some questions about terminal colors and file permissions."
date: 2020-08-27
forum: New to Ubuntu
---

### Post by sigurdsk on 2020-08-27
When i select "access to create and modify files" on directories the colors are wierd in the terminal. What are the correct settings for folders for permissions??

---

### Post by TheFu on 2020-08-27
> **sigurdsk said:**
> When i select "access to create and modify files" on directories the colors are wierd in the terminal. What are the correct settings for folders for permissions??

Whatever you like. ```
$ man -k DIRCOLOR
dir_colors (5)       - configuration file for dircolors(1)
dircolors (1)        - color setup for ls

```The colors shown are completely up to your desires. They don't change anything, just the display.

The answer for what permissions are needed depends on the directory involved and how restrictive you want or need to be. 
[LIST]
[*]If you are the owner, do whatever you like. 
[*]If you aren't the owner, best to never touch those permissions, owners, or group settings.  People who change system directory permissions usually end up being forced to reinstall the OS.
[/LIST]

For Unix systems, the owner, group, permissions, ACLs are all part of what is needed for a good backup.  Just having the data isn't sufficient. If a directory or file has the wrong permissions, some programs will refuse to work. This is mainly for those programs tied to security of the system. 

If you don't really understand file and directory permissions, may I suggest a tutorial?  
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Since almost everything on every Unix system is controlled by file permissions, they are key to understanding all access controls.  Everything that isn't a running process, is a "file."  All devices are files. Directories are files.  Network connections are files. If it doesn't show up in the system process table, it is a file.  Users who don't learn these permissions will struggle.  Simple. Elegant. Effective.

BTW, all popular OSes today use this model, except 1. Unfortunately, it is the one most desktop users had to learn.

---

### Post by SeijiSensei on 2020-08-29
Konsole, the KDE terminal program, has half-a-dozen built-in appearance themes you can choose from, or you can set up your own.  DK about the terminal programs in other Ubuntu flavors.

---

