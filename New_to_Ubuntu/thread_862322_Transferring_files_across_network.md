---
title: "Transferring files across network"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by phil81uk on 2008-07-17
I have a Vista laptop and an Ubuntu laptop on my home network. what's the easiest way of transferring files across from one to the other? I don't need to share files, just transfer them. Eg. I have a movie on Ubuntu which I want to send to Vista.

Thanks!

---

### Post by scorp123 on 2008-07-17
SSH. e.g. **apt-get install openssh-server** on Ubuntu, and then a compliant software such as **WinSCP** on Windows, and voila ... you login from Windows to your Ubuntu box using your normal username and password and then you get to see your Ubuntu system's files and can drag and drop them locally onto your Windows box.

---

### Post by markjensen on 2008-07-17
I would just set up a "shared" folder in Windows (I have done this with XP, but not Vista) and connect to it from Ubuntu.   Much less installing of software and such.  And for a simple local home network transfer of files, using Windows built in SMB is fine.

---

