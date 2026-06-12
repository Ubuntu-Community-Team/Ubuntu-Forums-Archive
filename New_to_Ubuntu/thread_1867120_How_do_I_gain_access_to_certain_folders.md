---
title: "How do I gain access to certain folders?"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by slayner117 on 2011-10-22
I am the administrator, and it says that I need Owner Access. All I am trying to do is extract a new mouse theme to the usr/share/icon folder. Please help

---

### Post by haqking on 2011-10-22
> **slayner117 said:**
> I am the administrator, and it says that I need Owner Access. All I am trying to do is extract a new mouse theme to the usr/share/icon folder. Please help

you need to use sudo see [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by masgeeks on 2011-10-22
You can use gksudo nautilus from the command line, this will open up file manager with root privs.  Then browse to your home folder (filesystem > home > yourhomefolder) and find where you saved the download, extract to same location, and then just copy can paste the extracted folder to /usr/share/icons.

---

### Post by slayner117 on 2011-10-22
thank you for your help it worked just fine.

---

