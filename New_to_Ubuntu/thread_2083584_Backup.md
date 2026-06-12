---
title: "Backup"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by lizandeen on 2012-11-13
How do I run Deja-dup Backup as root (put as simply as possible please) ? Thanks to all in advance

---

### Post by NikTh on 2012-11-13
Hi , 
Open a terminal (CTRL+ALT+T)  and write ```
man deja-dup
```deja-dup has also a command line utility , so I assume you can start an immediately backup as root with sudo prefix in this command ```
deja-dup --backup
```**But I never tested. **

You have to be a little more specific about what you want to achieve. I guessed you want to backup something from root (/) folder. (but I'm not sure)

Thanks

---

### Post by newb85 on 2012-11-13
> **NikTh said:**
> 
You have to be a little more specific about what you want to achieve. I guessed you want to backup something from root (/) folder. (but I'm not sure)

Indeed.  If you're trying to back up your entire system, I'm afraid you'll run into some trouble.  I don't know that it's impossible, but Deja Dup was designed for easily backing up a user's /home folder.

I've found a great way to pseudo-back-up my system is to use Deja Dup to back up my /home and then use the "Sync between computers..." option in the Software Center to keep track of what packages I have installed.  If something happens, I can do a fresh install, install the packages I had before, and extract my /home directory, and presto!  (Exception: manually installed packages take a little more work.)

---

### Post by mastablasta on 2012-11-13
uless you plan file syncing then creating bit-by-bit image is probably best.
 
have a lok at Clonezilla or Redo backup (more friendly interface)

---

