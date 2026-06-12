---
title: "Where do I put scripts to make them work?"
date: 2021-09-30
forum: New to Ubuntu
---

### Post by GhX6GZMB on 2021-09-30
I'm a total noob to scripts and looking for your help, please.

I've written my first script, which looks like this:
```
#! /bin/bash
sudo apt update && sudo apt upgrade && sudo apt autoremove

```

The script file is right now:
```
/home/macro/upgrade
```

Permissions are OK (bits set to -rwxr-x--x)

But where should I place the script file?
At this point it doesn't work, as the shell can't find it.
Should I move it to somewhere else?
Or do I need to set an environment variable?

I'm lost.

---

### Post by Holger_Gehrke on 2021-09-30
If you enter just the name of a program into the shell it searches for the program file in the directories listed in the variable PATH. Enter 'echo $PATH' into a shell to see what directories are in PATH. 

If you give the shell a path and a file name, then it will execute a program even if it's not in a directory that's part of PATH. So if you enter '/home/macro/upgrade' into the shell (or './upgrade' if /home/macro/ is your current working directory) it will call your script.

Alternatively there are two directories which - if they exist - are automatically added to PATH: '~/bin/' (which AFAIK is not created by default for a user, so you'd have to create it and possibly restart at the very least your shell so it picks up on the existence of the directory) and '~/.local/bin/' (which I think does exist by default ...).  So if you move your script into one of these directories you should be able to call it without explicitly giving a path to it.

And of course you could change PATH to include a directory of your choice (entering 'PATH=${PATH}:${HOME}/myscripts' into the shell would add the directory ~/myscripts at the end of the PATH for the duration of your current session, so it would become the last directory to search for programs; to change the PATH permanently edit ~/.profile and add that command or change a command setting the PATH to include your changes).

Holger

---

### Post by Bashing-om on 2021-09-30
ml9104; Hello 

I expect that your need has been foreseen by our developers :)

Does the directory 'bin' already exist in your /home ?
> 
ls -al /home/sysop/ >> drwxrwxr-x  3 sysop sysop   4096 Aug 11  2020 [color=red]bin[/color]

where my username on my system is "sysop"

[INDENT]no new wheel here
[/INDENT]

---

### Post by GhX6GZMB on 2021-09-30
@Holger_Gehrke:
Thanks for your insight, running the 'echo $PATH' was really helpful.
I've now placed my script in /usr/local/sbin, seeing that it needs a sudo password to work. It runs wonderfully. I've also changed the permissions to -rwx------ and ownership to "root".

The references to a "bin" directory in $HOME I don't understand
.
PS: edited to correct a couple of mistakes.

---

### Post by The Cog on 2021-10-01
If you create a bin directory in your home directory (e.g. /home/macro/bin) then that directory will automatically be added to your PATH next time you log in. But of course, only your PATH will include that, not any other user's PATHs. I keep lots of utility scripts in my personal bin folder.

---

### Post by ActionParsnip on 2021-10-01
You can put the file in any folder that is in your path variable. I lie to make a folder to hold all my scripts (personally).

---

### Post by GhX6GZMB on 2021-10-01
> **The Cog said:**
> If you create a bin directory in your home directory (e.g. /home/macro/bin) then that directory will automatically be added to your PATH next time you log in. But of course, only your PATH will include that, not any other user's PATHs. I keep lots of utility scripts in my personal bin folder.

VERY interesting, Thank You. I'll try that as well.

---

### Post by Dennis N on 2021-10-01
There's possibly already someplace for your scripts in your home folder among the locations in PATH for executable files. My current OS has ~/.local/bin by default. ~/.local/share is also searched for themes and icons and these are priority locations over themes and icons in /usr/share.

---

### Post by Tadaen_Sylvermane on 2021-10-01
If I may. Something I didn't figure out till after awhile. You can run the entire script with a single sudo.

```
#!/bin/bash

apt update
apt upgrade
apt --purge autoremove
```

Execute via ```
sudo /path/to/script
```

---

### Post by GhX6GZMB on 2021-10-01
> **Tadaen_Sylvermane said:**
> If I may. Something I didn't figure out till after awhile. You can run the entire script with a single sudo.

Yes, of course. That's the whole point.

---

### Post by GhX6GZMB on 2021-10-01
OK, I put on my thinking hat.

I'll leave this script in /usr/local/sbin for several reasons:
1: it's a script for the main/sudo user only, and all other settings for this user are also in /usr/share. "Normal" users have their settings in $HOME subdirs.
2: it's a sudo script, which tells me that sbin, not bin is the right place.
3: there must be a reason that /usr/local/sbin exists (a bit weak, but...)

Other scripts that are for all/other users and do not need sudo rights I'll have to think about.

Thanks for your help everybody.

---

### Post by vanadium on 2021-10-02
Put your personal scripts in either `~/.local/share/bin` or `~/bin`.

Put scripts that need to be available to any user in the system in `/usr/local/bin`. `/usr/local/sbin` indeed is a suited location for your custom administrative scripts.

---

