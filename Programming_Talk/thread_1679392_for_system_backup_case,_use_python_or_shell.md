---
title: "for system backup case, use python or shell?"
date: 2011-01-31
forum: Programming Talk
---

### Post by abhilashm86 on 2011-01-31
I wanted to write a script to backup some directories in ubuntu, there are few directories i need to make a backup. 
for system backup case, use python or shell? 

So is python os shell better?? I just want to run executable and backup my files. 

There will be two 500GB external usb, i've formatted one to ext4 and other ntfs, so whenever i plugin, i'll mention name of disk in arguements, so script should go and copy the files. 

So i had a doubt, which language to use, since i'm a new to both. Can i run these scripts as normal user or sudo??

---

### Post by lavinog on 2011-02-01
How are you wanting the backup done.
If you are planning to use rsync, then I would just use a simple bash script to call rsync.

---

### Post by gerowen on 2011-02-01
For something as straight-forward as copying files from one place to another, possibly archiving them, bash would be more than adequate.

---

### Post by wmcbrine on 2011-02-01
This is *exactly* what shell script is for. Python actually sucks for this kind of application, and I say that as a Python lover.

---

### Post by lavinog on 2011-02-01
> **wmcbrine said:**
> This is *exactly* what shell script is for. Python actually sucks for this kind of application, and I say that as a Python lover.

It depends on the complexity of the backup logic.  If it is something that does incremental backups, or hardlinks duplicated files, it may be easier to utilize python.

I wrote a backup script in bash that ran on a file server.  Other machines would use either rsync or robocopy(native rsync like program for windows) to backup to the file server.  Then the script ran daily to hardlink all of the files to a daily folder.  This allowed me to roll back to any day.  I didn't start learning python until after I made that script.  I am not sure if it would have made much difference, but it would have made the script much easier to modify years later.

---

### Post by abhilashm86 on 2011-02-01
The files i'm backing up are subversion, management docs and custom documents from ubuntu machine. As far as complexity is concerned, its not huge files which are backed up!! So good to hear from you people about rsync, i'll check it out!! 

I just started out with python, I'm having an issue, how do i tell in my script which external USB drive is now plugged in??

I want my script to tell which USB drive i'm plugged in.........please help.

```

d = datetime.datetime.now()

dateVar = d.strftime('%Y%m%d_%H%M')
print dateVar
#not good idea to use os.system(...)
#os.mkdir(dateVar)

#subprocess.call(['mkdir', '/home/abhilash/ %s' %dateVar])
# Copy recursively from child of the folder, make sure the destination directory should not exist!!
shutil.copytree('/home/abhilash/Documents', '/media/PENDRIVE/backup/ %s' %dateVar)
```

I'm roughly doing in the start, will add more features as it progress, i'm total newbie to python, so don't freak me out!!

---

### Post by abhilashm86 on 2011-02-01
I was just trying out rsync from command line, i should be very carefull while using it, whereas in python script, i can mention each and every file how it should be created and copied. 
Let it copy a bit slow in python script, i'm not looking at performance, just want to copy whole code and documents according to date and time!! 

```
abhilash@abhilash-G62:~/Programming$ rsync -au /home/abhilash/mac_files/ /media/PENDRIVE/
rsync: symlink "/media/PENDRIVE/Mac4Lin_Icons_v0.4/scalable/actions/document-open.png" -> "../places/gnome-fs-directory-accept.png" failed: Operation not permitted (1)
rsync: symlink "/media/PENDRIVE/Mac4Lin_Icons_v0.4/scalable/actions/error.svg" -> "dialog-error.svg" failed: Operation not permitted (1)
rsync: symlink "/media/PENDRIVE/Mac4Lin_Icons_v0.4/scalable/actions/fileopen.png" -> "../places/gnome-fs-directory-accept.png" failed: Operation not permitted (1)


```

---

### Post by lavinog on 2011-02-01
Those errors bring up an interesting point.
How is your python script dealing with symlinks?

Your pendrive likely uses a FAT filesystem that doesn't support symlinks.

---

### Post by abhilashm86 on 2011-02-01
> **lavinog said:**
> Those errors bring up an interesting point.
How is your python script dealing with symlinks?

Your pendrive likely uses a FAT filesystem that doesn't support symlinks.

So what filesystem will symlink support? This USB is vfat and just to test the python script. 

Untill now shutil is handling errors like permission problems, file not found, device under /media not found through exception.

for the question of symlinks, I created symlink in Documents folder, when i ran the script, symlink contents has been copied........```
abhilash@abhilash-G62:~/Documents$ ls -l
total 8
lrwxrwxrwx 1 abhilash abhilash    8 2011-02-01 17:28 abhi -> ../a.txt
drwxr-xr-x 3 abhilash abhilash 4096 2011-02-01 14:50 lrjert
-rw------- 1 abhilash abhilash   27 2010-11-19 07:22 softwares_info

```

---

