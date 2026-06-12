---
title: "Please help--I broke Sudo"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by cranet on 2013-04-28
Hello everyone:

I am now 2 weeks into solely using Ubuntu 13.04 as only OS on my new System 76 Panp9.  I am very impressed with it so far and am extremely satisfied with Ubuntu.  Please help me because it seems I have broken sudo while trying to give permissions to Plex media server.  Currently when I'm trying to execute a sudo commond in terminal I recieve the following error:

dayspring@Dayspring:~$ sudo apt-get update
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

Please tell me what I did wrong and how could I fix this.  Advanced Thank you.

---

### Post by pqwoerituytrueiwoq on 2013-04-28
boot a live dvd/usb and mount your / partition (open the drive in the file viewer)
then do this 
```
sudo chown root:root /media/$USER/*/usr/lib/sudo/sudoers.so
sudo chmod 644 /media/$USER/*/usr/lib/sudo/sudoers.so
```

---

### Post by cranet on 2013-04-28
Thank you very much, **[COLOR=#000000][pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458")!!![/COLOR]**[COLOR=#000000] Your solution worked.[/COLOR]

---

### Post by cranet on 2013-04-28
Oh I forgot to ask:
Is there a good site where I can learn what I did wrong and how/why your solution worked?  I want to be able to fix these issues on my own in the future.
Again, thank you for taking the time to assist me.

---

### Post by pqwoerituytrueiwoq on 2013-04-28
i looked at the permissions on my system for that file: /usr/lib/sudo/sudoers.so
then a played with chmod till i found the right number, then i gave you the code i did

---

### Post by davidbaumann on 2013-04-29
I guess sudo checks the permission of the file, so you can't insert your own sudoers.o with LD_PRELOAD (what might allow you to use a changed file that always allows you to do a sudo without password...

And you changed the permissions, but nobody can tell you when, maybe you will find out by reading the guide again?

David.

---

### Post by audiomick on 2013-04-29
> **davidbaumann said:**
> And you changed the permissions, 

yes, this

> **cranet said:**
> sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner.

indicates that you somehow changed the write permission on that file.

---

