---
title: "Extract Zip Files!!"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mde123 on 2008-06-07
Hi i have am having a really hard time extracting a zip file that i got, and file roller wont let me open it, and i really REALLY dont want to have to use  
a command line. Just please tell me the packages i need, or what i need to edit!

PLease and thank you.

---

### Post by Barriehie on 2008-06-08
> **mde123 said:**
> Hi i have am having a really hard time extracting a zip file that i got, and file roller wont let me open it, and i really REALLY dont want to have to use  
a command line. Just please tell me the packages i need, or what i need to edit!

PLease and thank you.

I'm using Gutsy 7.10 and **Applications** > **Accessories** > ***Archive Manager*** should do the trick.

Barrie

---

### Post by hopelessone on 2008-06-08
Can't you just right click the file and select "Extract Here"...?

---

### Post by forger on 2008-06-08
Either the zip file you found is broken (bad download?) or you can post the error it gives.


P.S. Barriehie: file-roller = Archive manager

---

### Post by ubunken on 2008-11-10
Hi i have extracted the files using right click > extract here.. however i have to move the file to another location but whenever i try moving it, i will receive an Error moving file : Permission denied, is there anyway that i can move the files? Thanks in advance

---

### Post by handydan918 on 2008-11-10
If you are getting a permissions error, then you are probably trying to copy the file to a location outside of /home/your_username.

Try (in a terminal) ```
gksudo nautilus
```

---

### Post by redseventyseven on 2008-11-10
> **ubunken said:**
> Hi i have extracted the files using right click > extract here.. however i have to move the file to another location but whenever i try moving it, i will receive an Error moving file : Permission denied, is there anyway that i can move the files? Thanks in advance

If you're getting permission errors when moving the file, then it sounds like you're trying to move it to a place where it isn't a good idea to move it to. I would strongly advise against using "sudo" or "gksudo" (the commands you use to run programs as the administrator) willy-nilly.

Could you post where you intend to move the file to? Thanks.

---

### Post by ubunken on 2008-11-11
I am planning to move the file from desktop to /var/www and another file to /tmp

---

### Post by handydan918 on 2008-11-11
> **ubunken said:**
> I am planning to move the file from desktop to /var/www and another file to /tmp

Or you could just delete them.

You DO know that's what happens to everything in /tmp at reboot, right?

---

