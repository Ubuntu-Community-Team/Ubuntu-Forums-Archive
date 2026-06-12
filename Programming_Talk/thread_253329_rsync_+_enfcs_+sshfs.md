---
title: "rsync + enfcs +sshfs"
date: 2006-09-08
forum: Programming Talk
---

### Post by keithweddell on 2006-09-08
I'm trying to use rsync to back up some files that I want to store on my isp server where I have some spare free space.  As the server is obviously not secure I want to use encfs to encrypt the files.

1.  I can mount the remote directory using sshfs so that it appears in my local file system.  

2.  I can then mount the remote encrypted directory using enfs.

3.  I can use rsync to backup my home directory.

However, I want to back up other files for which I need root permisions.  If I use sudo rsync I can access the files but do not have permissions to save them in the encfs directory.  If I don't use sudo, I can save into the encfs directory but can't access the files.  I seem to be stuck between two conflicting permissions problems.  Can anyone suggest a way round this?


Keith

---

### Post by keithweddell on 2006-09-08
OK I think I've solved this.  Create a file called /etc/fuse.conf which contains "user_allow_other".  This allows you to pass allow_other or allow_root options to encfs.

The only problem is there seems to be a bug in encfs which changes the date modified of files.  This makes it useless for rsync incremental backups.  Guess I'll go back to tar and scp.

Keith

---

### Post by guruofquality on 2006-11-25
> **keithweddell said:**
> I'm trying to use rsync to back up some files that I want to store on my isp server where I have some spare free space.  As the server is obviously not secure I want to use encfs to encrypt the files.

1.  I can mount the remote directory using sshfs so that it appears in my local file system.  

2.  I can then mount the remote encrypted directory using enfs.

3.  I can use rsync to backup my home directory.

However, I want to back up other files for which I need root permisions.  If I use sudo rsync I can access the files but do not have permissions to save them in the encfs directory.  If I don't use sudo, I can save into the encfs directory but can't access the files.  I seem to be stuck between two conflicting permissions problems.  Can anyone suggest a way round this?


Keith

Can you edit the mount options for the encfs to force the UID to be your UID and not root?. Use uid=XXXX

---

### Post by jtc on 2007-01-16
> **keithweddell said:**
> OK I think I've solved this.  Create a file The only problem is there seems to be a bug in encfs which changes the date modified of files.  This makes it useless for rsync incremental backups.

I use rsync in combination with encfs without any timestamp problems. Althought I guess there are a few diffrent ways you can implement those two programs.

Anyway, have you tried using rsync with --checksum? Then it is supposed to skip files based on their checksum instead of mod-time and size.

---

