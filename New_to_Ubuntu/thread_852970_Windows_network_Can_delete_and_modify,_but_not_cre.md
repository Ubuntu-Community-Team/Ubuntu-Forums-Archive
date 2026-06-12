---
title: "Windows network: Can delete and modify, but not create files or folders"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-08
I (finally) managed to create a network link between my Ubuntu and Windows machine using Samba. It's easy ... when you know how!

From Windows, I can access my Ubuntu shared folder perfectly.

From Ubuntu, I can access my Windows share perfectly... except for one problem. Although I can delete and modify files on the Windows share (from Ubuntu), I cannot create new files or folders.

[LIST]
[*]In nautilus, when I right-click in the folder, the options *Create Folder* and *Create Document* are both greyed out.
[*]In terminal, I don't even know how to access the Windows shared folder. (I tried "cd smb://win-pc/public/", which is how nautilus finds it, but it didn't work.)
[/LIST]
I have, of course, granted full control permissions on the Windows folder to "Everyone" and "Guest". The folder is fully accessible from my other Windows computers on the network.

How do I get Windows to allow me to create files or folders from Ubuntu?

More info:

[LIST]
[*]Ubuntu machine: version 8.04 (hardy), Kernel Linux 2.6.24-19-generic
[*]Windows machine: Vista Home Premium
[/LIST]
Edit: I take it from the answers that no one knows how  to grant create-access to Ubuntu from Windows? Does no one have create-access to Windows shares from Ubuntu?

---

### Post by renzokuken on 2008-07-08
if i remember correctly, from inside ubuntu window folders will be mounted in your /media folder. so for example, if your windows share is mounted at say /media/win-share, you could change the permissions on this folder to allow full read write access (or whatever you require)

---

### Post by Paddy Landau on 2008-07-08
> **renzokuken said:**
> if i remember correctly, from inside ubuntu window folders will be mounted in your /media folder. so for example, if your windows share is mounted at say /media/win-share, you could change the permissions on this folder to allow full read write access (or whatever you require)
No, I  checked, and it's not in the media folder.

When I open it in nautilus, the address bar shows
smb://win-pc/public/

Terminal doesn't recognise that as a folder.
> ls smb://win-pc/public/
ls: cannot access smb\://win-pc/public/: No such file or directoryBut, I still cannot create files or folders on the Windows share from Ubuntu. Any ideas how to allow this? I presume that Windows, not Ubuntu, is preventing this.

---

### Post by Krydahl on 2008-07-08
Do you know the path that you used to mount the share? If so, you should be able to access it via that.

---

### Post by Bucky Ball on 2008-07-08
Could be off the money, but nothing to do with Windows partitions being NTFS, if they are? This might be the problem creating folders on windows partitions while in Ubuntu OS. 

Good luck ...

---

### Post by Paddy Landau on 2008-07-08
> **Krydahl said:**
> Do you know the path that you used to mount the share? If so, you should be able to access it via that.
I used nautilus to find the Windows share (Places -> Network).

nautilus automatically mounts it.

That's not my problem, though; the problem is getting Ubuntu to be allowed to create files and folders on the Windows share (it can already modify and delete them).

---

### Post by Paddy Landau on 2008-07-08
> **Bucky Ball said:**
> Could be off the money, but nothing to do with Windows partitions being NTFS, if they are? This might be the problem creating folders on windows partitions while in Ubuntu OS. 

Good luck ...
No, I don't think so. Hardy has NTFS support built in; I have full create-read-write-delete access to the files in my Windows partition on the same computer as Hardy (it's a dual-boot) without any problems.

Accessing the files on a share over the LAN, as I understand it (correct me if wrong), means that the host computer handles the file structure, not Ubuntu.

---

### Post by Paddy Landau on 2008-07-09
I take it from the answers that no one knows how to grant create-access to Ubuntu from Windows?

Does no one have create-access to Windows shares from Ubuntu?

---

### Post by cariboo on 2008-07-09
No, windows share permissions are setup in Windows.

Have you made sure that everybody has permission to change files on your windows share. This is done in windows. Right click on your windows share in XP and there should be a check box that needs a check mark. I'm not close to a windows computer at the moment, thats why the instructions are a little vague.

Jim

---

### Post by Paddy Landau on 2008-07-10
> **cariboo907 said:**
> Have you made sure that everybody has permission to change files on your windows share.
Thanks for your suggestion.

It's Windows Vista box.

I've gone through every permission setting that I can find, including Advanced, and ensured that everyone has full permission. Note that another Windows computer can create files on the share; it seems to be just Ubuntu that can't.

---

