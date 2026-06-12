---
title: "Lost boot.disk file (dual boot 8.04 and XP)"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by kronprinz311 on 2008-09-03
I cant boot into Ubuntu anymore, I get kicked into BusyBox. I know the problem isn't because of a bad Windows shutdown. Thats happened before and it's easy to fix.

Before being kicked into BusyBox I get a message saying that my "root.disk" file cannot be found. And sure enough, if I "cd" (from BusyBox) to the directory where it usually is, its not there. Even If I browse to that directory from within XP.

The only thing I did before this problem started happening was to uninstall the .NET Framework from Windows as well as some minor programs and did a defrag.

I tried running chkdsk /r in windows to fix any dirty NTFS flags and disk errors, but it didn't help.

Please help! Is there any way to get my files that were in my "home" folder, they were important :(

---

### Post by halitech on 2008-09-03
worse comes to worse you can always use the Live CD to save the files to a thumb drive or from within XP if you can get to it.

---

### Post by kronprinz311 on 2008-09-03
I thought I could do that, but when I use the live cd, I run a search for some of the files and nothing comes back! Is there a better way to do this?

---

### Post by halitech on 2008-09-03
file names are case sensative so might be better to mount the drive and browse to the files you want to save

---

### Post by kronprinz311 on 2008-09-03
Ok I'll try that, I didn't it was possible to mount the drive if root.disk file was missing. What is the purpose of that file anyways?

---

### Post by halitech on 2008-09-03
it works the same as NTLR on windows

---

