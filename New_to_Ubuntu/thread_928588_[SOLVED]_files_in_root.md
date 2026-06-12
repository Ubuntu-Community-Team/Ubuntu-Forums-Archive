---
title: "[SOLVED] files in root"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by pmeyer on 2008-09-24
i'm a newcomer with Ubuntu 8.04 Hardy Heron - dualboot with GRUB
Vista and Ubuntu.

I have this two shortcuts in the root (initrd.img and vmlinuz) 
and i wish to know why i can't delete them.
The target files are in /boot !

Sorry for my very bad english but it's not my mother-language !

Can someone please help me ?

---

### Post by Idefix82 on 2008-09-24
I hope you don't mind me asking why on earth you want to delete them?

---

### Post by muteXe on 2008-09-24
[http://www.linfo.org/vmlinuz.html](http://www.linfo.org/vmlinuz.html)

[http://kerneltrap.org/node/7019](http://kerneltrap.org/node/7019)

I'm with Idefix82 on this.  They're not offensive/bad files, they take up less than 10Mb of space.
Why the hell do you want to delete them?

---

### Post by pmeyer on 2008-09-24
> **muteXe said:**
> [http://www.linfo.org/vmlinuz.html](http://www.linfo.org/vmlinuz.html)

[http://kerneltrap.org/node/7019](http://kerneltrap.org/node/7019)

I'm with Idefix82 on this.  They're not offensive/bad files, they take up less than 10Mb of space.
Why the hell do you want to delete them?
thanks a lot for answer me 

the ls - command shows me that these two files are links to
the original files in the directory /boot

i am a newcomer with linux and i want to know if these two
links in the root-directory are normal or not.

all other files of the system are stored in directoris except
these two

---

### Post by jemate18 on 2008-09-24
PLease DONT DELETE THEM!

Or else, you will regret it.. they are files needed necessary for your ubuntu to work. 

Do you mind answering why you want to delete them?

Did somebody tell you to delete it?

---

### Post by pmeyer on 2008-09-24
> **muteXe said:**
> [http://www.linfo.org/vmlinuz.html](http://www.linfo.org/vmlinuz.html)

[http://kerneltrap.org/node/7019](http://kerneltrap.org/node/7019)

I'm with Idefix82 on this.  They're not offensive/bad files, they take up less than 10Mb of space.
Why the hell do you want to delete them?
thanks a lot for answer me

the ls - command shows me that these two files are links to
the original files in the directory /boot

i am a newcomer with linux and i want to know if these two
links in the root-directory are normal or not.

all other files of the system are stored in directoris except
these two

---

### Post by Tatty on 2008-09-24
> **pmeyer said:**
> i am a newcomer with linux and i want to know if these two
links in the root-directory are normal or not.

Dont worry, I have these files in my root too.

It is generally a good idea to not manually change anything which isnt in /home unless you know for certain what you are doing.

As to why you could not delete them, read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But dont delete those files! :)

---

