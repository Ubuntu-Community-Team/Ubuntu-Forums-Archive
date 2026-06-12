---
title: "Help cant log in to desktop"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by asf08005 on 2013-02-10
Hi,
  I changed something with my log in settings and now when i boot my computer it goes into a terminal box. I have no clue how to get to my desktop. The box says.
"To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bash: /home/andrew/.bashrc: Permission denied
andrew@Andrew-Linux:/$


What is the command to let me back into my computer?
   Thanks

---

### Post by cariboo on 2013-02-11
It would help, if you told us what you did, or what you were trying to do.

---

### Post by lordievader on 2013-02-11
Seems to me that you or something else changed the permissions to your home dir.
It is indeed a good idea to let us know what you were trying to do, or what you have done before the problem occurred.

---

### Post by asf08005 on 2013-02-20
hi,
 I believe it was a setting for log in options. forgive my vagueness, this was awhile back, I gave up but decided to give it a 2nd shot. I must of changed how I wished to log in, from automatic to admin. Before I changed it, the login on reboot would be similar to Windows. My name would pop up and I just put in my password. Now a terminal shows up, and I don't know how to get back into my desktop. 
   Thanks all!

---

### Post by lordievader on 2013-02-21
What is the output of:
```
ls -l /home/andrew
```

Or if this throws a permission error make it:
```
sudo ls -l /home/andrew
```

I'm assuming you still have sudo rights.
-lordievader.

---

