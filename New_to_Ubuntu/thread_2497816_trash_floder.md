---
title: "trash floder"
date: 2024-05-19
forum: New to Ubuntu
---

### Post by dimi67 on 2024-05-19
Hello. I am new to ubuntu I have a vps server with 22.04. with software Virtualmin I'm looking and I can't find where the trash floder can is??? Please a help.

---

### Post by TheFu on 2024-05-19
Virtualmin documentation [https://www.virtualmin.com/docs/getting-started/how-to-use-file-manager/#file-manager-keyboard-shortcuts](https://www.virtualmin.com/docs/getting-started/how-to-use-file-manager/#file-manager-keyboard-shortcuts) doesn't mention trash at all.
Servers don't have any Trash/ directories.  If you seek to restore deleted files, use backups and restore them that way.

Trash is something that Linux DEs, desktop environments, added. It is part of the XDG standard, I suppose, which is a GUI/Desktop thing, not for servers. The trash is only used when a GUI program is used to delete a file that is part of the DE being used.  They are not system-wide.  The typical location for Trash is on every mounted file system, at the root of that file system in a directory at the same level as the lost+found/ directory.

When I say "GUI", I don't mean "WebGUI".  I mean something from Gnome or XFCE or KDE or ... from the 10 other DEs.  I use a window manager without any DE, so my "desktop" doesn't have any Trash.

So, for a file system mounted to /TV/, then the Trash would be in  /TV/Trash/.  File systems where the users'HOME directories are placed have their Trash inside the HOME directory, probably in ~/.cache/Trash/ .   Why is there a different location for trash for each file system?  Because files are moved, not copied, into the Trash location.  A move on the same file system has nearly zero overhead, while a copy could take 2+ minutes for very large files.

Most file managers have a setting/preference for whether Trash will be used or not for the individual.

There are lots of CLI wrappers for **rm** that used to implement something like Trash for CLI users.  I never liked them.  When a file is deleted, I expect it to be gone, gone, gone.  If I need it back and it was a file that was on the file system overnight, then I can get it back from the backups.  Otherwise, I know it is gone and needs to be recreated if I want it THAT badly.

Best to assume there isn't any Trash, since that is the default.

---

### Post by dimi67 on 2024-05-19
I have deleted a 2gb .zip file, but I see that the space on the server's hard disk is the same. I can't find this file to delete it completely?
From ssh via command can I find this file, where is it?

---

### Post by TheFu on 2024-05-19
Look for "Empty Trash" in the GUI.
If you use **rm** to delete it from an ssh CLI shell, it is gone.

---

### Post by dimi67 on 2024-05-20
I deleted the file from the virtualmin file manager.

---

### Post by TheFu on 2024-05-20
> **dimi67 said:**
> I deleted the file from the virtualmin file manager.

I didn't see any mention of "trash" in the virtualmin documentation, so I doubt it exists.  It certainly wouldn't be standard on any server.  However, I've never used virtualmin.

---

### Post by dimi67 on 2024-05-21
If I delete it via ftp, will it be permanently deleted?

---

### Post by TheFu on 2024-05-21
> **dimi67 said:**
> If I delete it via ftp, will it be permanently deleted?

You shouldn't use plain FTP and nobody should since around 2002 when it was replaced by sftp.  sftp is built-into openssh-server. You probably already have it installed. It uses the same credentials as ssh and the same ports.  Most Linux file managers support sftp.  Check the manpage for your file manager to see if it goes by sftp:// or ssh:// URLs.

You can delete files, regardless of protocol, only if the current userid has permissions to do that.  Understanding file and directory permissions is a basic skill for all Linux/Unix systems.  They all work exactly the same.

---

### Post by ActionParsnip on 2024-05-21
I found this
[https://forum.virtualmin.com/t/deleted-data-how-to-restore-files-from-file-manager/113250](https://forum.virtualmin.com/t/deleted-data-how-to-restore-files-from-file-manager/113250)

Instead of some web UI, i suggest you use SSH and use command line. You'll learn more and get to grips with the OS. You could even use something like WinSCP/FileZilla but these don't have a recyclebin feature.

FTP is awful too. Nobody should use FTP. It is trash.
[https://whydoesitsuck.com/why-does-ftp-suck/](https://whydoesitsuck.com/why-does-ftp-suck/)

---

