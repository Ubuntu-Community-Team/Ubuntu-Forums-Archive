---
title: "downloads"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by Lorganz on 2013-01-17
Hi everyone. New to Ubuntu so please bear with me. My problem is downloading....anything. The download appears to be fully working then an "Archive" window opens which states there is a long error message and nothing shows.
This happens with all the downloads I have tried.

Thanks in advance, any help would be appreciated

---

### Post by audiomick on 2013-01-17
Which version of Ubuntu do you have installed?

---

### Post by Lorganz on 2013-01-17
On the disk it says 12.04 LTS

---

### Post by ibjsb4 on 2013-01-17
> **Lorganz said:**
> Hi everyone. New to Ubuntu so please bear with me. My problem is downloading....anything. The download appears to be fully working then an "Archive" window opens which states there is a long error message and nothing shows.
This happens with all the downloads I have tried.

Thanks in advance, any help would be appreciated

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update && sudo apt-get upgrade
```And try again.

---

### Post by mcduck on 2013-01-17
> **Lorganz said:**
> Hi everyone. New to Ubuntu so please bear with me. My problem is downloading....anything. The download appears to be fully working then an "Archive" window opens which states there is a long error message and nothing shows.
This happens with all the downloads I have tried.

Thanks in advance, any help would be appreciated

When you start downloading a file, your web browser asks you if you want to open the file (with a suggested program depending on type of file you are downloading) or save it. Choose the option to save it. You can always open/extract the file yourself *after* it has downloaded.

---

### Post by d4m1r on 2013-01-17
What is the FULL name of the file?

Can you post a screenshot of the error message?

---

### Post by mad2-814 on 2013-01-17
Ubuntu always opens downloads with archive manager by default.  Find the file with the file type you want and right click and change default program that opens it.

---

