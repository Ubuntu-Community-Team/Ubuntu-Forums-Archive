---
title: "Accidentally installed a keyless repository, where do I find it to delete it?"
date: 2024-07-25
forum: New to Ubuntu
---

### Post by jebus42 on 2024-07-25
Greetings. I was attempting to install grapefruit and Wine for the first time, as I am new to linux as a whole and wanted to play some roblox. However, I made the mistake of using an out of date guide (this one--> [https://devforum.roblox.com/t/roblox-on-linux-everything-summarized-in-1-post/2215991](https://devforum.roblox.com/t/roblox-on-linux-everything-summarized-in-1-post/2215991)), and I now have a repository on my device that is missing the public key, which is blocking all attempts at updating Wine or anything else on my PC. I am working with ubuntu 24.04. The code for this error is here:
sudo apt update
Hit:1 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) noble InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble InRelease                      
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease               
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-updates InRelease
Get:5 [https://brinkervii.gitlab.io/grapejuice/repositories/debian](https://brinkervii.gitlab.io/grapejuice/repositories/debian) universal InRelease [2,401 B]
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble-backports InRelease
Err:5 [https://brinkervii.gitlab.io/grapejuice/repositories/debian](https://brinkervii.gitlab.io/grapejuice/repositories/debian) universal InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C215E86647988DA
Reading package lists... Done
W: GPG error: [https://brinkervii.gitlab.io/grapejuice/repositories/debian](https://brinkervii.gitlab.io/grapejuice/repositories/debian) universal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C215E86647988DA
E: The repository 'https://brinkervii.gitlab.io/grapejuice/repositories/debian universal InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

So far, I have tried to access my sources.list file, to no avail. I have visited the new location for the ubuntu repository in nano, but it does not hold any 3rd party repositories, which is what I need to delete. I have also already tried to use the software updater and directly finding the faulty repository there, but it refuses to show up. 

Does anyone know what sources.list file 3rd party repositories are stored in? I can delete it from there, I just haven't been able to locate it in 3 hours of searching and forum browsing. Failing that, is there another way to delete the faulty repository? Thank you for any help with this issue, it is greatly appreciated.

---

### Post by Xian on 2024-07-26
Check the contents of [FONT=monospace][COLOR=#000000]/etc/apt/sources.list.d

$ ls [/COLOR][/FONT][FONT=monospace][COLOR=#000000]/etc/apt/sources.list.d/[/COLOR][/FONT][FONT=monospace][COLOR=#000000][/COLOR]
[/FONT]

---

### Post by grahammechanical on 2024-07-26
Alternatively, open Software & Updates>Other Software tab and uncheck the repository. Or, select the repository and click remove. Then run Software Updater.

Regards

---

### Post by jebus42 on 2024-07-26
Thank you for the suggestion grahammechanical, but it does not show up there, leading to my issue.

---

### Post by jebus42 on 2024-07-26
Thank you for the suggestion Xian, but that folder is just as empty as every other sources.list variant I have tried to find my repositories in.

---

### Post by TheFu on 2024-07-26
Well, reloading the OS takes just 15 minutes.  Do you have good backups?  If you've wasted more than an hour on this, it is time to move on, since that's all it should take, if that, to do a fresh install and restore your settings and data.

---

### Post by jebus42 on 2024-07-26
That's my issue, I don't have any good backups. I failed to have the foresight to produce any. I am only planning on reinstalling in the event that there is no other possible solutions, but thank you for your suggestion TheFu.

---

### Post by TheFu on 2024-07-27
> **jebus42 said:**
> That's my issue, I don't have any good backups. I failed to have the foresight to produce any. I am only planning on reinstalling in the event that there is no other possible solutions, but thank you for your suggestion TheFu.

There are 3 types of backups.  

Simple end-users often only need to backup their HOME directory and that's sufficient to capture their personal data and settings.

On a multi-user system, with shared storage either between users or with other computers, backups are a little more complicated.  Get all the HOME directories for all the users and get the locations of that shared storage.  Not really all that hard, just be certain to use sudo to make the backups, so the owner, groups, and permissions are maintained, along with the files.

The type of backup above doesn't maintain system settings nor does it create a list of already installed programs to be reinstalled. For many people, that isn't very important. They use the included programs from the installation.  By not backing up the OS files, backups are much smaller and easier to get good enough.  However, getting a list of the installed packages isn't hard.  **dpkg --get-selections** will do that. Save the output to a file and include it in your backup data.  Or you can use the **apt-mark showmanual** command.

For reference purposes, backing up /etc/ is helpful. Just don't expect to restore it blindly. It is fairly small, so not really a problem to always included in your backups.  What I do with files I've customized in /etc/ is to add a comment TAG whenever I touch them, so that I know it has been manually modified.  At restore time, I just search for the TAG in those files, so I know which lines I modified and can do the same in the restore.  A little thinking ahead makes for restores to be faster and more accurate.  I think fewer than 10 files get manually modified in /etc/, so it isn't a big deal.  

Of course, there are files and directories in /etc/ for manually installed tools too.  A fresh OS install wouldn't include those, so I know to copy them over BEFORE I tell APT to install the tool into the new install.  Things like OS alarming and performance data capture are that way.  Some LAN firewall rules, and definitely my MTA setup.  All my systems run an MTA for a number of reasons.  I also backup the crontabs for each user. Almost forgot to mention that.  cron is something I use extensively on almost every system. It handles 99% of the automation here ... including daily, automatic, versioned, backups.

The other backup methods become very strict in how a restore can be performed and on which hardware it can be placed.  But with a data+settings backup method, the restore starts with a fresh install of the OS.

Wish I knew where to look for your repo issue.  The places already listed is where I'd look. I didn't think there were any other locations, but recently the repo layout did change (first time in 20+ yrs!), so perhaps there are other places for the new repo layout files to go?  IDK.   I try to keep my PPA use to a minimum, always prefer to use the Canonical core repos and ONLY the Canonical core repos whenever possible.  It avoids all sorts of APT-Hell problems and makes for a more stable system, IME.

---

### Post by Xian on 2024-07-28
Terminal command to list installed repos:
$ [FONT=monospace][COLOR=#000000]apt-add-repository --list

[/COLOR][/FONT]Terminal command to remove a specific rep:
$ sudo apt-add-repository -r repo_name


In your case most likely:
[PHP]sudo apt-add-repository -r deb https://brinkervii.gitlab.io/grapejuice/repositories/debian universal InRelease[/PHP]

---

