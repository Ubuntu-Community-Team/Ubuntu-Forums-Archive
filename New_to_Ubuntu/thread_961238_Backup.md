---
title: "Backup"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-10-28
hello,

i wanted to backup my system but actually i dont know how...
could someone help me with this

i want to backup to an extern hard drive

greetz
D.Dadsgé

---

### Post by wizard10000 on 2008-10-28
> **Dadsgé said:**
> hello,

i wanted to backup my system but actually i dont know how...
could someone help me with this

i want to backup to an extern hard drive

I use rsync to back up directories on three machines (one of them is a Windows machine) to a 300gb external hard drive - it works great.

Pretty good readme here - 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by beercz on 2008-10-28
> **Dadsgé said:**
> hello,

i wanted to backup my system but actually i dont know how...
could someone help me with this

i want to backup to an extern hard drive

greetz
D.Dadsgé

You can use rsync to copy your data to a mounted external hard disk, it's in the repros.

For a more sophisticated approach for incremental backups you can use [rsnapshot]("http://ubuntuforums.org/http;//rsnapshot.org"), which uses rsync.

rsync just copies new and modified files, so after the first backup, it is very quick and efficient.

I use rsnapshot with cron to automate my incremental backups on a daily basis.

If you need help with either, just ask.

---

### Post by Elfy on 2008-10-28
This is quite a good overview - [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I would tell you how I backup, but I'm not very good at doing it ;)

---

### Post by Dadsgé on 2008-10-28
thanx for your responses

i tried rsync following the site wizard gave me, but it doesnt work
it gave me an error
> sent 289859 bytes  received 20 bytes  30513.58 bytes/sec
total size is 256510053  speedup is 884.89
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]


what should i do now?

---

### Post by wizard10000 on 2008-10-28
> **Dadsgé said:**
> thanx for your responses

i tried rsync following the site wizard gave me, but it doesnt work
it gave me an error


what should i do now?

This is usually a file permissions problem.  Run rsync with the -v option to see verbose output - maybe it'll tell you which files are causing problems.

---

### Post by Dadsgé on 2008-10-28
could you explane me a bit more, i'm just a little noob
what should i type in command line?

---

### Post by wizard10000 on 2008-10-28
> **Dadsgé said:**
> could you explane me a bit more, i'm just a little noob
what should i type in command line?

Can you give us the command line you used that caused the error?  Then maybe we can help you fix it.

cheers -

---

### Post by Dadsgé on 2008-10-28
i just did what they said on the site
> sudo rsync --delete -azvv -e ssh /home 

---

### Post by beercz on 2008-10-28
> **Dadsgé said:**
> i just did what they said on the site
OK, try something like:

> sudo rsync -avvvz /home/yourusername/ /opt/disk | tee /home/yourusername/Desktop/rsyncoutput.txt

Substitue your own user name for 'yourusername', and the mount point of your external hard disk for '/opt/disk' - note the trailing / after the first 'yourusername' (your actual user name) - it's important - it instructs rsync to include all sub directories.

The | tee bit outputs the results of the program to both the screen a file on your desktop called rsyncoutput.txt, which you can open in a text editor when the rsync command finishes.

Post that file here.

Good luck.

---

### Post by beercz on 2008-10-28
BTW - what exactly are you trying to back up?

---

### Post by Dadsgé on 2008-10-28
i suppose it is normal that this takes a long, really long time :P

---

### Post by Dadsgé on 2008-10-28
> **beercz said:**
> BTW - what exactly are you trying to back up?

um trying to backup home, because i already had a lot of trouble
like compiz that doesnt work anymore or awn that flips out :P
and all my settings that were gone...

---

### Post by beercz on 2008-10-28
> **Dadsgé said:**
> i suppose it is normal that this takes a long, really long time :P
Only for the first time - rsync has to copy every single file you have.

Subsequent executions of the command only copy new or changed files, leaving the unchanged ones intact.

Therefore it is very efficient.

You just have to be patient the first time I'm afraid!

BTW If you are just backing up your own home directory, you may not need to use sudo.

---

### Post by wizard10000 on 2008-10-28
> **Dadsgé said:**
> i just did what they said on the site

Okay, let's look at this.

```
sudo rsync --delete -azvv -e ssh /home
```

First, if you run rsync as root root will own the files on the target drive unless you use a -p switch to preserve permissions.  Might be a good idea to read the rsync man page  :)

Also, there's no reason to use the -z switch or ssh for a local file copy.  You don't need the -e switch because we're not executing a remote shell.

Okay - here we go.

```
sudo rsync --delete -aEmv /home /path/to/folder/on/removable/drive
```

Here's what we did -

sudo rsync:  Ran rsync as root.  On a single user system where you're just backing up /home this isn't necessary but it won't hurt anything really.

--delete:

This deletes files on the target that no longer exist on the source.

-aEmv:

a:  Archive files
E:  Preserve executable flag
m:  Prune empty directories - this will delete any empty directories on the target
v:  Verbose output - you can get rid of this once it works the way you want.

Also, you need a target directory  :)

---

### Post by random turnip on 2008-10-28
If you want to do it without using any special software (i.e. manually) then you simple copy and paste everything you want to backup to your external HDD.

I personally find it just as easy to do it manually, takes a bit more time and you gotta remember to do it, but if you don't want it doing, and you want to add a couple of extra folders or somthing it's a lot more simple to do so.

---

### Post by Dadsgé on 2008-10-28
problem xD
file is bigger than the limits of thes forum...
i'm gonna try to put it in more files, but i still think that will be to big...

---

### Post by Dadsgé on 2008-10-28
> **wizard10000 said:**
> Okay, let's look at this.

```
sudo rsync --delete -azvv -e ssh /home
```

First, if you run rsync as root root will own the files on the target drive unless you use a -p switch to preserve permissions.  Might be a good idea to read the rsync man page  :)

Also, there's no reason to use the -z switch or ssh for a local file copy.  You don't need the -e switch because we're not executing a remote shell.

Okay - here we go.

```
sudo rsync --delete -aEmv /home /path/to/folder/on/removable/drive
```

Here's what we did -

sudo rsync:  Ran rsync as root.  On a single user system where you're just backing up /home this isn't necessary but it won't hurt anything really.

--delete:

This deletes files on the target that no longer exist on the source.

-aEmv:

a:  Archive files
E:  Preserve executable flag
m:  Prune empty directories - this will delete any empty directories on the target
v:  Verbose output - you can get rid of this once it works the way you want.

Also, you need a target directory  :)

ok, i did this, but still i get an error message...
a lot of files are already backed up

---

### Post by wizard10000 on 2008-10-28
> **Dadsgé said:**
> ok, i did this, but still i get an error message...
a lot of files are already backed up

If you don't share the error message we can't help you  :)

---

### Post by Dadsgé on 2008-10-28
well it was the same error as i gave you last time
i already closed the terminal, but ill give you a copy of the other one, so you guys don't need to search for it ;)

edit: here it is:
> sent 289859 bytes received 20 bytes 30513.58 bytes/sec
total size is 256510053 speedup is 884.89
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9] 

---

### Post by rtom on 2008-10-28
To save the system I make following:
```
dpkg --get-selections > installed-software

```then to restore ```
dpkg --set-selections < installed-software
dselect
```

Using this and GRUB to boot the ubuntu mini.iso I can make a fresh install, having all the packages needed. Since /home is a different partition, all the user settings remain unchanged. It takes on my old PIII about 20 minutes.

---

### Post by wizard10000 on 2008-10-28
> **Dadsgé said:**
> well it was the same error as i gave you last time
i already closed the terminal, but ill give you a copy of the other one, so you guys don't need to search for it ;)

edit: here it is:

You're trying to copy 25gb of data?

---

### Post by beercz on 2008-10-28
@Dadsgé

Did you manage to create the rsyncoutput.txt file?

If so, can you post it here?

Have you tried reading the file to look for the error message(s) - i.e. the files that cannot be copied?

When you find these, copy and paste the relevant text here.

---

### Post by Dadsgé on 2008-10-28
@ wizard: um i dont think i can possibly copy 25 GB of data when i just have an HD of 4GB :P
so there should be a little mistake...
maby it are 25000 files?

@ beercz: and still searching for the error message...

---

### Post by beercz on 2008-10-28
> **Dadsgé said:**
> @ wizard: um i dont think i can possibly copy 25 GB of data when i just have an HD of 4GB :P
so there should be a little mistake...
maby it are 25000 files?

@ beercz: and still searching for the error message...
Use the editor's find facility and search for "Error" or similar.

---

### Post by Dadsgé on 2008-10-28
ok, didn't found the error message in the file...
but when i did the sudo of you, i didn't got that message...

---

### Post by Dadsgé on 2008-10-28
when i look at the both backups (those of Wizard and beercz) then i see that in the one of Wizard i dont have all my files, not the normal ones, neater the hidden ones.. (in total: 43 of all 55 dir's)
in the one of beercz i do find all my files but none of my hidden ones... (in total: 13 of all 55 dir's)

---

### Post by Dadsgé on 2008-10-28
well its ok, i manually copied my files
but will it be enough to 'repair' the system when i replace my home folder?

---

