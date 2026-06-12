---
title: "Rsync fails to create certain folders."
date: 2011-01-19
forum: Programming Talk
---

### Post by Trapper on 2011-01-19
I am having a curious problem with an rsync script. Although I could opt to just back up my complete home folder, I choose to be selective and only backup what I would actually need if a hard drive disaster occurred. I am having difficulty backing up properly when I back up files in a subfolder but no files from the base folder the subfolder is under. Rsync refuses to create the base folder in the backup target partition and therefore will not create the subfolder and files either.

Here's an example. It's my ".config" folder. There are a number of subfolders but I am only interested in backing up the "transmission" subfolder. My line for that in my script is this:

```
rsync -arv /home/trapper/.config/transmission/ /media/RSYNC-Backup/trapper/.config/transmission/
```When I run it I get this error message:

```
rsync: mkdir "/media/RSYNC-Backup/trapper/.config/transmission" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
```However, this works and creates the .mozilla folder and it's entire contents, including subfolders & all subfolder files, at the backup target.

```
rsync -arv /home/trapper/.mozilla/ /media/RSYNC-Backup/trapper/.mozilla/

```Just to test, I added this to my script just prior to the transmission backup line:

```
if [ ! -d /media/RSYNC-Backup/trapper/.config ]
         then
mkdir /media/RSYNC-Backup/trapper/.config
fi

```The function above created the .config folder at the target and then the transmission folder backed up properly.


I obviously have something wrong. What do I not know that I should know?

---

### Post by jondecker76 on 2011-01-20
I use rsync to backup the entire /home directory (including all users directories) - I'm no expert but I normally don't have problems.

The 2 most obvious things I can think of:
1) Permissions... cd into ~/.config and issue a ls -la and make sure the owner isn't root

2) Is Transmission running while you attempt the backup?  make sure it isn't by running killall transmission before trying to back up

---

### Post by Trapper on 2011-01-20
> **jondecker76 said:**
> I use rsync to backup the entire /home directory (including all users directories) - I'm no expert but I normally don't have problems.

The 2 most obvious things I can think of:
1) Permissions... cd into ~/.config and issue a ls -la and make sure the owner isn't root

2) Is Transmission running while you attempt the backup?  make sure it isn't by running killall transmission before trying to back up

Thanks for this but in this instance it's not my problem. Just a few minutes ago I figured out what it is with the help of someone at Linux Forum.

I need to use the  --relative flag. Rather than rysnc -arv I should be using [FONT=monospace]rysnc [/FONT]-arvR. That's going to give me:
[I][I][FONT=monospace]
[/FONT]/media/RSYNC-Backup/home/trapper/"Whatever I am backing up in the script."[/I][/I]

In the specific case of:

```
rsync -arvR */home/trapper/*.config/transmission/ */media/RSYNC-Backup/*

```I get:

/media/RSYNC-Backup/home/trapper/,config/transmission, with the transmission folder being the only subfolder backed up ... which is what I want.

---

