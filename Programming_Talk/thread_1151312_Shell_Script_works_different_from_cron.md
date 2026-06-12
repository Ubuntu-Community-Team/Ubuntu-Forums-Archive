---
title: "Shell Script works different from cron"
date: 2009-05-06
forum: Programming Talk
---

### Post by necrolin on 2009-05-06
I wrote a simple shell script for backing up my home directory using the tar command. If I run the script from the command line then it backs up my files as required. Everything seems to work fine. However, when I run it from cron my results are different. It still creates a backup file however, all of the directories in the .tar file are empty. No actual files are backed up. :confused:

Here's the part of the script that actually does the backing up...

l1backup()
{

if test -f /home/necrolin/.homebackup/snapshots/l0snapshot
then
# Copy snapshot files to avoid errors
cp /home/necrolin/.homebackup/snapshots/l0snapshot /home/necrolin/.homebackup/l1snapshot

# Run backup
tar -cvf /home/backup/level1.tar \
--exclude=".*" \
--exclude="/home/necrolin/Videos" \
--exclude="/home/necrolin/Music" \
--exclude="/home/necrolin/examples.desktop" \
--label="Level 1 backup executed on: `date`" \
-g /home/necrolin/.homebackup/l1snapshot /home/necrolin

# Copy snapshot file for use with level 2 backups
cp /home/necrolin/.homebackup/l1snapshot /home/necrolin/.homebackup/snapshots/l1snapshot
else
echo "You must run a level 0 backup before you can run a level 1 backup"
errorMsg
fi
}


Any ideas?

---

### Post by Arndt on 2009-05-07
> **necrolin said:**
> I wrote a simple shell script for backing up my home directory using the tar command. If I run the script from the command line then it backs up my files as required. Everything seems to work fine. However, when I run it from cron my results are different. It still creates a backup file however, all of the directories in the .tar file are empty. No actual files are backed up. :confused:

Here's the part of the script that actually does the backing up...

l1backup()
{

if test -f /home/necrolin/.homebackup/snapshots/l0snapshot
then
# Copy snapshot files to avoid errors
cp /home/necrolin/.homebackup/snapshots/l0snapshot /home/necrolin/.homebackup/l1snapshot

# Run backup
tar -cvf /home/backup/level1.tar \
--exclude=".*" \
--exclude="/home/necrolin/Videos" \
--exclude="/home/necrolin/Music" \
--exclude="/home/necrolin/examples.desktop" \
--label="Level 1 backup executed on: `date`" \
-g /home/necrolin/.homebackup/l1snapshot /home/necrolin

# Copy snapshot file for use with level 2 backups
cp /home/necrolin/.homebackup/l1snapshot /home/necrolin/.homebackup/snapshots/l1snapshot
else
echo "You must run a level 0 backup before you can run a level 1 backup"
errorMsg
fi
}


Any ideas?

Not much of an idea, but I would add some trace output to the script, and output for example the result of "pwd" and "which tar" to a file which you can read later.

---

### Post by geirha on 2009-05-07
Install [bsd-mailx](apt:bsd-mailx), then have the script run from cron. If the script produces any output, it will be mailed to you. Run ```
mail
``` to read those mails.

---

### Post by amac777 on 2009-05-07
Cron uses sh (not bash). So if your script is supposed to use bash, this can cause a lot of issues if you don't specifically specify on the first line:

```
#!/bin/bash
```

Assuming you have that line at the beginning of the script, another problem that is common is that there is no $PATH setup when things execute via cron. So you can't rely on ~/ or other short forms of filenames. I don't see anything in that part of the script you posted but maybe you should double check. (basically use absolute filenames everywhere even programs names that you normally don't need to specify the path for)

---

### Post by necrolin on 2009-05-07
> **geirha said:**
> Install [bsd-mailx](apt:bsd-mailx), then have the script run from cron. If the script produces any output, it will be mailed to you. Run ```
mail
``` to read those mails.

I'll look into this. I'm thinking that what I'll actually need to do is install posfix or sendmail and see what results I get. I believe that mailx is just a client.... correct me if I'm wrong. But your idea is good. I used to get all my cron related stuff mailed to me when I was using Fedora. It was a nice feature.

---

### Post by necrolin on 2009-05-07
> **amac777 said:**
> Cron uses sh (not bash). So if your script is supposed to use bash, this can cause a lot of issues if you don't specifically specify on the first line:

```
#!/bin/bash
```

Assuming you have that line at the beginning of the script, another problem that is common is that there is no $PATH setup when things execute via cron. So you can't rely on ~/ or other short forms of filenames. I don't see anything in that part of the script you posted but maybe you should double check. (basically use absolute filenames everywhere even programs names that you normally don't need to specify the path for)

Yes, I do have #!/bin/bash in the beginning of the script. No relative paths in the script. The above is actually almost the entire script. I use a "case" statement to select the level of backup I want to do and case calls on the correct function. Each function is the same, except that they use different "-g snapshot" in order to get different levels of incremental backups. I have 3 levels: 0 full backup, 1 weekly backup, 2 daily backup. That's about it.

This is probably something really small and easy... but it's making me go crazy.

---

### Post by geirha on 2009-05-07
> **necrolin said:**
> I'll look into this. I'm thinking that what I'll actually need to do is install posfix or sendmail and see what results I get. I believe that mailx is just a client.... correct me if I'm wrong. But your idea is good. I used to get all my cron related stuff mailed to me when I was using Fedora. It was a nice feature.

You don't need a mail server. Cron just writes the output of the command with an added mail-header to /var/mail/$USER, which is the mbox the mail command will read by default.

---

### Post by necrolin on 2009-05-07
> **geirha said:**
> You don't need a mail server. Cron just writes the output of the command with an added mail-header to /var/mail/$USER, which is the mbox the mail command will read by default.

/var/mail is empty... cron isn't outputting anything.

---

### Post by geirha on 2009-05-07
> **necrolin said:**
> /var/mail is empty... cron isn't outputting anything.

Yeah. It seems it checks whether there is a mail binary or something. If bsd-mailx (or just mailx on Hardy) is installed, cron will start mailing. When it isn't installed, it doesn't seem to send the output anywhere ... /dev/null maybe?

---

### Post by amac777 on 2009-05-07
Are you really sure that the script is doing what you think it is? 

I took another look at the part you posted and it is using the -g option of tar which is a listed incremental archive. Therefore, if no files have changed since the previous time you ran the script, the new archive it creates will only include the directories but no actual files. The reason is no files have changed so none are included in the newly created archive.

So perhaps you ran the script from the command line manually and it backed up all the files because it was the first time it was run, and then you tested running the script from cron and it made an archive with only the directories but no files because the files hadn't changed since the first run?

---

### Post by necrolin on 2009-05-07
> **amac777 said:**
> Are you really sure that the script is doing what you think it is? 

I took another look at the part you posted and it is using the -g option of tar which is a listed incremental archive. Therefore, if no files have changed since the previous time you ran the script, the new archive it creates will only include the directories but no actual files. The reason is no files have changed so none are included in the newly created archive.

So perhaps you ran the script from the command line manually and it backed up all the files because it was the first time it was run, and then you tested running the script from cron and it made an archive with only the directories but no files because the files hadn't changed since the first run?

I'm doing a few Uni courses in the evenings so there are files which are updated daily. So, there should never be an empty archive. This project is simply a review for the final exam for me. (unix admin class).

---

### Post by necrolin on 2009-05-07
I figured it out...

the secret was this:

tar -cvf

the v (verbose) option spits out exactly what it's doing. This crashes the cron job. You'll get the exact same thing if you throw some "echo"s in there. This is actually what tipped me off as to what the problem could be. Works perfect now running with the initial options of:

tar -cf

Thanks for everyone's help.

---

