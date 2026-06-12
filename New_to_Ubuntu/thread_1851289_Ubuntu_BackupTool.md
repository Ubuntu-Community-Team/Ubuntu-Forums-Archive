---
title: "Ubuntu BackupTool"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by node2network on 2011-09-28
Hi, I'm looking for useful backup tool!
 
I installed remastersys to make a full system bakcup , but my customized ubuntu is too large to make custom.iso file.
 
Is there a backup tool which mlike a full system backup like remastersys?

---

### Post by hyper2hottie on 2011-09-28
I realize you said backup tool, but if your not against using the command line you could try what this thread says:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) 

I backed up my system like the above link said.  I haven't actually tested if it works for restoring though.

---

### Post by nmaster on 2011-09-28
> **hyper2hottie said:**
> I realize you said backup tool, but if your not against using the command line you could try what this thread says:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) 

I backed up my system like the above link said.  I haven't actually tested if it works for restoring though.

i used to do that too, but people on the forums (you can prob find various threads) claimed that it didn't quite work... not sure if it has to do with the stuff in /dev/ but i don't do that anymore. 

clonezilla is great.  take a look, its probably what you want 
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by agillator on 2011-09-28
I use rsnapshot and an external drive. That gives me precise control over what is and isn't saved and also saves space because it uses hard links. I have not tried clonezilla but have heard it is pretty good if that is what you want. My problem using it as a true backup is it saves and restores EVERYTHING, junk and all. If that is what you want, ok. But I don't - I find it simple enough to reinstall a system and then simply reinstall the files I want to reinstall, but then that's me.

---

### Post by HermanAB on 2011-09-28
Howdy,

The reality is that it only takes about 30 minutes to re-install Linux from scratch, so laboriously making a backup of the whole system is rather pointless.

So, old hands just backup their data with rsync or Deja Dup.

---

### Post by shubham1 on 2011-09-28
open system settings
in system section click on file backup manager

---

### Post by aeiah on 2011-09-28
i use clonezilla for occasional system backup, and use incremental rsync for daily important data backups.

---

### Post by NLinTKO on 2011-09-28
I am using luckyBackup for a daily replication/backup of some selected directories. It has a built-in scheduler which makes it handy.

---

