---
title: "No sound! The sound device have dissapeared"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by DeliriousNor on 2008-07-10
It just happened somthing weird with my computer. I was about to turn up the volume, but it wouldn't respond. I clicked on the sound symbol up on the right taskbar, and it tells me that there is now device. I then go into the menu and navigate myself to "sound". Strangely there is now device here. The sound have worked perfectly out-of-the-box, until now.


Any suggestions on what to do?

---

### Post by chrisccoulson on 2008-07-10
First of all, is your user a member of the 'audio' group? To check, type the following in to a terminal:
```
groups
```
...and make sure 'admin' is listed. If not, then use the Users and Groups tool to correct this.

If your user is a member of the 'audio' group, then you might find these following pages useful:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

---

### Post by DeliriousNor on 2008-07-10
Thanks! I will take a look at it.

---

