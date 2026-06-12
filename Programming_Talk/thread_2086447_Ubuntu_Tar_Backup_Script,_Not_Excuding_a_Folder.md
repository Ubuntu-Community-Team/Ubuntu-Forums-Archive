---
title: "Ubuntu Tar Backup Script, Not Excuding a Folder"
date: 2012-11-20
forum: Programming Talk
---

### Post by jlacroix on 2012-11-20
I am trying to create a tar backup script. I used the following article as my baseline:
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

And this is what I ended up creating:
```
#!/bin/bash
# init

DATE=$(date +20%y%m%d)

sudo tar -cvpzf /tmp/`hostname`_$DATE.tar.gz \
--exclude=/proc \
--exclude=/lost+found \
--exclude=/sys \
--exclude=/mnt \
--exclude=/media \
--exclude=/dev \
--exclude=/tmp \
--exclude=/home/jlacroix/Desktop \
--exclude=/home/jlacroix/Documents \
--exclude=/home/jlacroix/Music \
--exclude=/home/jlacroix/Pictures \
--exclude=/home/jlacroix/Projects \
--exclude=/home/jlacroix/Roms \
--exclude=/home/jlacroix/Videos \
--exclude="/home/jlacroix/.VirtualBox VMs" \
--exclude=/home/jlacroix/.SpiderOak \
/

scp /tmp/`hostname`_$DATE.tar.gz jlacroix@Pluto:/share/Recovery/Snapshots

sudo rm /tmp/`hostname`_$DATE.tar.gz
```

The problem is that as it runs, it tries to backup the tar backup file itself. I don't understand why, since the backup file lives inside /tmp. which is one of the directories I told it to exclude. 

My second question, is if my exclusion of the ".Virtualbox VMs" folder is correct. It was the only folder that has a space in it, so I wrapped it in double quotes. Was that the right thing to do, or should I put all paths in double quotes to make it consistent?

---

### Post by spjackson on 2012-11-21
That looks like it should work. Something similar works for me. Is it just the backup file that is picked up in error or is anything else picked up that should be excluded?

The only things I can think of are these.
[LIST=1]
[*]If --exclude=/tmp in your script includes non-printable characters (such as carriage-return etc.)
[*]If /tmp is a symbolic link to, for example, /var/tmp then your backup file would get picked up under its proper name.
[/LIST]

---

### Post by jlacroix on 2012-11-21
> **spjackson said:**
> That looks like it should work. Something similar works for me. Is it just the backup file that is picked up in error or is anything else picked up that should be excluded?

The only things I can think of are these.
[LIST=1]
[*]If --exclude=/tmp in your script includes non-printable characters (such as carriage-return etc.)
[*]If /tmp is a symbolic link to, for example, /var/tmp then your backup file would get picked up under its proper name.
[/LIST]
The permissions for /tmp is drwxrwxrwt, is that a link?

---

### Post by spjackson on 2012-11-21
> **jlacroix said:**
> The permissions for /tmp is drwxrwxrwt, is that a link?
No, it's not a link. That's normal for /tmp. So that rules out the second possibility.

Do any other files get included that should be excluded? What version of tar are you using? Did you check that there's nothing wrong with the way that you've written --exclude=/tmp ?

---

### Post by SlugSlug on 2012-11-21
should it not look like

```
#!/bin/bash
# init

DATE=$(date +20%y%m%d)

sudo tar -cvpzf /tmp/`hostname`_$DATE.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/tmp --exclude=/home/jlacroix/Desktop --exclude=/home/jlacroix/Documents --exclude=/home/jlacroix/Music --exclude=/home/jlacroix/Pictures --exclude=/home/jlacroix/Projects --exclude=/home/jlacroix/Roms --exclude=/home/jlacroix/Videos --exclude="/home/jlacroix/.VirtualBox VMs" --exclude=/home/jlacroix/.SpiderOak /
scp /tmp/`hostname`_$DATE.tar.gz jlacroix@Pluto:/share/Recovery/Snapshots
sudo rm /tmp/`hostname`_$DATE.tar.gz
```

---

### Post by jlacroix on 2012-11-21
> **SlugSlug said:**
> should it not look like

```
#!/bin/bash
# init

DATE=$(date +20%y%m%d)

sudo tar -cvpzf /tmp/`hostname`_$DATE.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/tmp --exclude=/home/jlacroix/Desktop --exclude=/home/jlacroix/Documents --exclude=/home/jlacroix/Music --exclude=/home/jlacroix/Pictures --exclude=/home/jlacroix/Projects --exclude=/home/jlacroix/Roms --exclude=/home/jlacroix/Videos --exclude="/home/jlacroix/.VirtualBox VMs" --exclude=/home/jlacroix/.SpiderOak /
scp /tmp/`hostname`_$DATE.tar.gz jlacroix@Pluto:/share/Recovery/Snapshots
sudo rm /tmp/`hostname`_$DATE.tar.gz
```
No, I put the trailing backslashes at the end to format the script line by line so it's not a jumbled up mess of a command.

---

