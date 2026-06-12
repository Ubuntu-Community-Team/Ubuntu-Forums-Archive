---
title: "Cannot boot"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-11-14
Hi friends,

Iam and my friend using ubuntu os.
My friend come accrossed  a problem.
While working, suddenly all the files and folder in desktop become locked and systems also dead slow.
we slowly closed all the applications which we opened and reboot the system.
After rebooting i can't go to gui mode, its standing in command mode. like this
[B]"mark login:"
[/B]I logined as root and tried "fsck" to mount all filesystem.
I tried to install "gdm" but i can't install, it shows /var/lib/dpkg/lock is read only.

Kindly help me to solve this problem.

---

### Post by jtarin on 2011-11-14
First thing you need to check Synaptic Package Manager open at the same time

or

That happens when synaptic or another package update / installation application is already running. Close any other package managers (including Add/Remove application, language pack installer, etc.) and retry.

---

### Post by jtarin on 2011-11-14
If not helpful,look at this [entry]("http://ubuntuforums.org/archive/index.php/t-1571977.html").

---

### Post by pmohankumar on 2012-01-06
Thanks friends.

---

