---
title: "sharing www web directory between ubuntu and windows 7"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by vancouverwill on 2011-12-09
I've been fiddling around on and off for the last few weeks with sharing my local www directory between ubuntu 11.10 and windows 7. It's taking me a fair old while to get the setup so far, sharing files, ubuntu running how I want it and having both setups running in unison.

I have my shared files on a NTFS partition and this works fine for most things except for my www directory On the shared partition I have wamp installed with my www directory.

I've tried using symlinks and Documentroot to point to my wamp www directory but can't get it to work. I always get a permission error, this seems a fairly common situation to be but I haven't been able to find anything about sharing a web directory anywhere on the internet. I know it's super common to share files and that isn't a problem but something seems to be different when it's a web directory

---

### Post by vancouverwill on 2011-12-13
any thoughts on this? I've been trying to figure this out for a while. currently I'm using GIT to push and pull files back and forth

---

### Post by vancouverwill on 2011-12-18
anyone got any ideas on this? I'm starting to think that it's not designed to work this way because of the security risks of not having full permission control on a NTFS partition but I can't find anything about it on google

---

### Post by astrognome on 2011-12-18
Are you talking about sharing your webroot (/var/www), or your apache userdir?  What are you hoping to do?

---

### Post by vancouverwill on 2012-01-09
sorry about the slow reply I didn't notice you had replied to my message. I want to store all my web files on the ntfs directory so I have just one partition to be backed up. This would mean no web files in either the /var/www or the home directory. Doesn't necessarily have to be none completely but I want the majority of my web files to be on the ntfs shared partition. When I say my web files I mean the php files for a site and if it was another directory on the linux partition I could easily use it with a symlink.

This would not only make backing up easier it would also mean when I am logged in from windows I would be able to edit, view and update the files too. I've been looking around the web for a while on this and can't see any examples and haven't managed to get this working myself either.

---

### Post by mastablasta on 2012-01-09
ntfs directory? no, no. NTFS partition. how this is shown in linux is not so much relevant. 
 
create partition and mount it at the place you desire it to be. the easiest way.

---

### Post by vancouverwill on 2012-01-11
> **mastablasta said:**
> ntfs directory? no, no. NTFS partition. how this is shown in linux is not so much relevant. 
 
create partition and mount it at the place you desire it to be. the easiest way.

thanks but I'm sorry I used the wrong term, NTFS directory instead of partition but still I'm asking is it possible to have linux web files on a NTFS partition? I've been looking around on and off for months on this topic

---

### Post by vancouverwill on 2012-01-24
no one know the answer?

---

### Post by Mark Phelps on 2012-01-26
You can copy files from Linux filesystems to NTFS partitions all day long -- but, NTFS does not use the same permissions scheme as Linux.  So, if file permissions are important, that will not work.

---

