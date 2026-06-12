---
title: "sudo chmod 777 /etc"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by kqlyugondo on 2016-09-22
Hey guys, i have a very big problem. Unfortunately i write sudo chmod 777 /etc and couldn't do anything. So i tired first to reboot, after that i tried to install ubuntu server again. But now i have a bigger problem when im trying to boot any ubuntu system i get: ......... end kernel panic - not syncing: VFS: Unable to mount root on unknown-block (0,0)

I really need help!!

---

### Post by TheFu on 2016-09-22
Welcome to the forums.

Why would you do that anyway?
I don't think making /etc 775 would matter.  The owner and group are already root:root, so there wouldn't be any change effectively.  I suspect something else happened.

From the info provided, I can't see anything that would cause a kernel panic. There are other, unknown, issues - perhaps a failing HDD or bad cable?  Can't tell.  Look at the log files - you'll want to boot off the install media and try a "live boot" desktop version to see the log files on the HDD.
a) wipe the disk
b) reload the OS as you like
c) MAKE A BACKUP of everything you don't want to loose.  That includes permissions, owners, groups, and ACLs.

If you learn this on day 2 of your Unix learning, that would be a great saver of future frustration over the next 50+ yrs.  It took me about 8 yrs to learn this and 80% of my data was lost.  Please be smarter than I was.

---

### Post by kqlyugondo on 2016-09-22
my fault not 775 but 777. I will try that but i really dont think thats the problem because it worked just fine to i used that command... Can still access grub but have installed two other ubuntu os and none of them works and are giving me the same error and even though one of the other ubuntu os is actually on another hdd.

---

### Post by TheFu on 2016-09-22
Commands in Unix don't protect you from being stupid. Sorry to be so harsh.  Just because something is allowed, that doesn't mean it is a good idea.  The designers of Unix made a conscious decision NOT to limit what users could do because they knew they didn't know all the different situations where something could be useful.  If you'd like to shoot yourself in the head, Unix will let you.

There is **seldom** a good reason to use 777 ... at least until you have 10+ yrs of admin experience.  All those php webapps with instructions to set 777 directories just tells me the creator doesn't understand Unix permissions (or doesn't care if their program gets hacked).

I remember how frustrating Unix permissions were before I understood them.  Learn them ASAP. There's no way around it on a Unix system and not understanding is putting your system at risk. File and directory permissions are the cornerstone of all Unix security.  There are lots of tutorials for this stuff, but nothing teaches it like making a few userids, putting them into a few groups, mix and match a little, create a directory under /tmp/ somewhere and play around for 30 minutes.  See how you can prevent the owner from using a file, but allow everyone else in the same group to have complete access.  There are lots of subtle permissions that are useful like that.  Prevent the owner of that file from doing anything with it .... how might you accomplish that?

BTW, it is very important that you provide accurate information here to get useful help. We are volunteers.

Look at the log files.

---

### Post by Impavidus on 2016-09-22
For those who may think they have the same problem, the chmod 777 /etc problem is very easy to solve. Just run```
sudo chmod 755 /etc
```or, if you already have a root shell, drop sudo. I'm not sure you can do this from your normal terminal, as sudo may refuse when it detects the incorrect permissions, but then you can use recovery mode or a live disk.

It seems you introduced a new problem while trying to reinstall.

---

### Post by Habitual on 2016-09-23
> **Impavidus said:**
> chmod 777 /etc problem is very easy to solve.
"chmod 777"  never fixed anything. No problem.

---

