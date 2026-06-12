---
title: "Completing a proper backup"
date: 2016-07-15
forum: New to Ubuntu
---

### Post by michael351 on 2016-07-15
I'm new to Ubuntu. Now that it's installed, would someone suggest a procedure to follow (tar command syntax?) so that I can backup my installation and then restore it if I need to.
Ideally this would be a disk image.

Thanks!

(I searched this forum, but what to do is not clear to create a solid backup).

---

### Post by wildmanne39 on 2016-07-15
I believe clonzilla is still one of the best ways  to do that.
[http://clonezilla.org/liveusb.php](http://clonezilla.org/liveusb.php)

---

### Post by rdb3 on 2016-07-15
I use "Backups" for backing up and restoring.  I installed it from Ubuntu Software and have it set up to do a backup once a week.

---

### Post by oldrocker99 on 2016-07-15
I use grsync to make using rsync easy. It's the /home folder you need to back up. You can always reinstall a system.

---

### Post by DuckHook on 2016-07-15
FWIW, I don't back up the system. I've found over the years that it's not worth the trouble trying to clone and then reinstall the operating system because the restore process is often brittle, will restore you to an indeterminate previous state, and sometimes drags in the cruft (or mess) that caused the system breakage in first place. Especially in light of the fact that:

[LIST=1]
[*]After many installs, I find that an install from scratch takes no more than 40 minutes, tops,
[*]I now know exactly what config files to backup/restore and
[*]I keep a simple log of all post-install apps,
[/LIST]
I prefer having a pristine system to start over again. It's the data that is important, and that I backup two independent ways, with both on-site and off-site storage.

---

### Post by HermanAB on 2016-07-15
Yup.  Backup your data only.  

There is no point in backing up the system.  Linux is stored on servers the world over.  You don't need to keep yet another copy of it.  When the system gets messed up, do a fresh install from scratch and restore your data.  

This much more efficient and less time consuming.

---

### Post by giga+bytes on 2016-07-17
I'm glad I found this thread, it'll save a lot of time and external drive space!

---

### Post by mikodo on 2016-07-18
Thank you, michael351 for your thread. I am always looking for  better ways to administer my installs. So, your thread is of interest to  me. I would  like to impose and ask DuckHook a question if I may.
> **DuckHook said:**
>  -Snippet - I now know exactly what config files to backup/restore


What process of backup and restore do you use DuckHook? Which utility?

Would it be a cli copy/sync of all the pertinent configs >  Fresh install the same .iso > Delete the new stock install's pertinent config files > Use the same utility to restore from backup. 

Something like that?

Thank you.

---

### Post by DuckHook on 2016-07-18
> **mikodo said:**
> What process of backup and restore do you use DuckHook?Hi mikodo. Trust you are keeping well? I don't think you are hijacking the OP's thread because your question is just an extension of his. So, at the risk of babbling on too long, here are my usual habits:

[LIST=1]
[*]For tools, I just use rsync. I believe that the simpler things are, the better.
[*]I set daily anacron jobs to backup all desktops and laptops to my main server. I backup only /home.
[*]I set a daily cron job to synchronize main server with backup server. But this syncs everything, so the backup server is a mirror image of the main server.
[*]Every week I manually backup main server to third server: a USB drive that is then taken off-site. I rotate among 4 USB drives.
[*]Because storage media is so cheap these days (and my needs relatively light), I don't bother with compression or incrementals. This has the huge advantage that my backups are basically clones of my main server and are ready to go without any need for restoration. I just change where my links point to and, presto, I'm running off of the backup server (or third server if necessary).
[*]I have a symlink on my desktop to a file that resides on my server. It's a simple text file that I update every time I make a system change. Essentially, it is a log of all my config changes. In the event that I toast my install, I just reinstall and then cut and past all of the config changes to each respective file. If you prefer, you can log which files are changed and then simply set rsync to backup those specific config files in addition to /home. However, that seems more fragile to me. I prefer to do a clean install and then actually review my logged config changes to decide if I really need them anymore. This has the additional advantage that when I install to a new machine (like a laptop), my preferred configs are also easy to implement, since I can just cut and paste whatever I want into the new machine. I hasten to say that at some point, it's just a matter of personal preference. There is nothing inherently wrong with simply tracking config files that have been customized and rsyncing them. rsync allows you to define an exceptions file, an inclusion file, etc. It is ridiculously powerful and versatile.
[*]As oldrocker99 has suggested, I used to use grsync. For people who are allergic to the command line, this graphical front end for rsync is quite user-friendly. However, after I became comfortable with rsync, I discovered that it was far more convenient to automate things with a script and run it with cron or anacron. Hence, I no longer use grsync (though I would still highly recommend it, especially for new users).
[*]I backup most things in /home except for the various caches, trash folders, etc. Since rsync only backs up files that have changed, only the first-time backup is time-consuming. I find my subsequent backups take no more than a few minutes.
[*]Because nothing is compressed, tarred, zipped, etc. restores are simplicity itself. You could just copy everything back into the new install. However, it's easier to reverse the rsync input/outputs and, using the same command, everything gets restored easy-peasy.
[/LIST]
Hope this helps.

---

### Post by mikodo on 2016-07-18
Hi!

 I am fine and appreciative of your efforts in sharing here. How are you?

I use rsync extensively too. I have a data partition that I back up to  different drives also. It would not be a bother to learn how to do that  with the configs I have in Xubuntu as an example. They are shown in [this link]("http://docs.xfce.org/xfce/xfconf/start")  to the Xfce site. I am pretty sure if I asked how to back up my  Xfconfigs in the Xfce forums, someone like ToZ would direct me to [this page]("http://docs.xfce.org/xfce/xfconf/xfconf-query") for that.

I do appreciate your advice. I need to read it more thoroughly.

Have a great day!

> **DuckHook said:**
>  - snippets -

[LIST=1]
[*]I have a symlink on my desktop to a file that resides on my server. It's a simple text file that I update every time I make a system change. Essentially, it is a log of all my config changes. In the event that I toast my install, I just reinstall and then cut and past all of the config changes to each respective file. If you prefer, you can log which files are changed and then simply set rsync to backup those specific config files in addition to /home. However, that seems more fragile to me. I prefer to do a clean install and then actually review my logged config changes to decide if I really need them anymore. This has the additional advantage that when I install to a new machine (like a laptop), my preferred configs are also easy to implement, since I can just cut and paste whatever I want into the new machine. I hasten to say that at some point, it's just a matter of personal preference. There is nothing inherently wrong with simply tracking config files that have been customized and rsyncing them. rsync allows you to define an exceptions file, an inclusion file, etc. It is ridiculously powerful and versatile. 
[*]Because nothing is compressed, tarred, zipped, etc. restores are simplicity itself. You could just copy everything back into the new install. However, it's easier to reverse the rsync input/outputs and, using the same command, everything gets restored easy-peasy. 
[/LIST]


---

### Post by DragonBoy on 2016-07-19
I agree with "HermanAB". Do a fresh install from a CD or USB drive.

If you have important personal files like documents, pictures, music, scripts, etc. Just make *.tar.gz backups and save them on a spare USB or FTP site.

If you install specific files using the "sudo apt-get install <file_name>". Suggest making a bash script to track all of your installs. Then *.tar.gz bash script file and save it on a USB or FTP site. Then if you have to do a clean install. Download this file, unroll, and run. Then your done!!!

---

