---
title: "script to back up edited system configuration files"
date: 2013-03-05
forum: Programming Talk
---

### Post by Harp on 2013-03-05
I'm fairly new to Linux and I'm araid I don't know shell scripting well enough to know how to create the script that I want for this task, so I was hoping someone wiser than I could lend some advice.

So, I'm arranging my system in such a way that any time I change an important configuration file (/etc/fstab, for example), I create a backup of the original, untouched file as well as a symbolic link to it in the directory ~/.config/backups/*-ln, where * is the name of the original file and the .ln extension refers to it as a link. For example, if I were to edit /etc/fstab, I would create in ~/.config/backups/ the following entries:

$ls -l
fstab-ln -> /etc/fstab
fstab-ori

This is nice because in one location I can look at a given *-ln file to see the real file's current state and I also keep a record of what files I'm altering and their original states (with the *-ori).

What I want to do now is make it so that when I run a backup of my /home directory (with deja-dup, for example) the states of those *-ln files gets backed up as well, so that if I need to restore my system at some point, I'll have copies of all of the system files I've edited, ready to be restored should I deem it necessary. I'm pretty sure that with symlinks, as soon as I restore my /home folder, those files would be overwritten with the contents of the new links they point to, so my current setup wouldn't work for that entirely. But I'm thinking that I could possibly create a script called something like "update-backups" that would copy the contents of each of my ~/.config/backups/*-ln files into individual files then labeled *-bak.

So ~/.config/backups/ would then read:

$ls -l
fstab-bak
fstab-ln -> /etc/fstab
fstab-ori

Then I would have a single directory in which I keep an original of, a link to, and a backup of each system file I edit. I feel this would greatly improve the efficiency of backing up only a /home directory.

Any thoughts or help with writing such a script?

---

### Post by papibe on 2013-03-05
Hi Harp.

I would start by rethinking your backup strategy a little bit.

Instead of just keeping record of the current and last files, I would keep all historic copies. For instance:
```
smb.conf.2012.11.14
smb.conf.2012.11.30
smb.conf.2012.12.18
smb.conf.2013.01.20
smb.conf.2013.03.05
```
Where the last one is the current one.

Just a thought.
Regards.

---

### Post by Harp on 2013-03-06
> **papibe said:**
> Instead of just keeping record of the current and last files, I would keep all historic copies..

I agree, this would be more efficient for the backups. But I still like the idea of having a link to each file to check its current state and also to see the path to the file, which would make it easier to restore files if I've forgotten where exactly they belong.

Any ideas on how to create these historic backups via the links to the original files?

I was thinking something like:
```

cat ~/.config/backups/*.ln > ~/.config/backups/*.bak
```

but this creates a single file with all the contents in it. I don't know the correct arguments to separate this into individual copies and add in the date as you've indicated.

Thanks

---

### Post by papibe on 2013-03-06
Try something like this:
```
for f in ~/.config/backups/*.ln; do **[COLOR="#FF0000"]echo[/COLOR]** cp "$f" ~/.config/backups/"${f%*.ln}".$(date +%F) ; done
```
Note that this command DO NOT copy the files, but print the commands only. When you are sure it does what you want, remove the '[COLOR="#FF0000"]**echo**[/COLOR]' word.

Let us know how it goes.
Regards.

---

### Post by Harp on 2013-03-06
Thanks! That was exactly what I needed. 

I've tweaked your code a bit to be more effective in the environment in which I'll be using it. Your code would create a new backup of every link in the folder, which would eventually cause redundancies. Instead, I've altered it to be a command that I run on a file BEFORE I edit it, in order to create the symlink and backup.

```
#!/bin/bash
# /usr/local/bin/pre
#
# pre [file]
#
# When invoked, creates a link to, and a dated backup of, [file] in ~/.config/backups/

FILE=$1

for f in $FILE; 
	do 
		cp -bu "$f" ~/.config/backups/"`basename ${f}`".$(date +%F) ; 
		ln -sf "$f" ~/.config/backups/"`basename ${f}`" ;
	done
```

As you can see, I named it "pre" and put it in my /usr/local/bin/ folder. So from the command line, if I type:
```
$pre /etc/fstab
```
for example, it creates two files in my ~/.config/backups/ folder: fstab.YYYY.MM.DD, which is only created if the source file is newer than the existing file, and a symlink to the original file.

The only problem I'm having with this code at the moment is that it only seems to work for complete path names. Ie, it only works when I type "pre /etc/fstab" but when I am in the /etc/ folder and type only "pre fstab", it creates a broken link. Do you have any suggestions about how to fix this? I believe it also requires that the ~/.config/backups/ folder already be in existence. 

Thank again.

---

### Post by schragge on 2013-03-06
If the idea of keeping /etc in version control system appeals to you, please take a look at [etckeeper]("http://manpages.ubuntu.com/manpages/precise/en/man8/etckeeper.8.html"). I'm using it to track all changes to */etc*. Info on *etckeeper* in Ubuntu Server Guide: [uhelp]12.04/serverguide/etckeeper.html[/uhelp]. On Ubuntu, etckeeper comes preconfigured to use bzr. This prompted the upstream author to put following in the [README]("http://git.kitenet.net/?p=etckeeper.git;a=blob;f=README;h=b8b6d784c307812922061342b9e27987d91fa7e0;hb=e5577a7a5d7788290a861bf5283bfb116f62dfd4"):
> **"Joey Hess"]By default, etckeeper uses git. This choice has been carefully made said:**
> I'm using it with git as Joey suggests. (I'm on Debian, so I didn't have to make any changes to etckeeper's configuration.) There are many online howtos on etckeeper, too: [1]("http://linuxaria.com/recensioni/etckeeper-keep-under-control-your-configuration-files?lang=en"), [2]("http://evilrouters.net/2011/02/18/using-etckeeper-with-git-on-ubuntu/"), [3]("http://beginlinux.com/server/ubuntu/1598-how-to-use-etckeeper-"), [4]("http://www.serverwatch.com/server-tutorials/keep-configs-under-control-with-etckeeper.html").

---

### Post by Harp on 2013-03-06
> **schragge said:**
> If an idea of keeping /etc in version control system appeals to you, please take a look at [etckeeper]("http://manpages.ubuntu.com/manpages/precise/en/man8/etckeeper.8.html").

That looks like a decent solution as well. I'll have to check it out a little futher. The benefit of this "pre" script, though, is that one could quickly create a link and backup of any file at the drop of the command, not just the contents of /etc.

---

### Post by schragge on 2013-03-06
Joey Hess, the author of etckeeper, actually [keeps his whole home directory under version control]("http://joeyh.name/vcshome/"). He started with cvs, then changed to svn, then finally converted it to git. But there are other approaches, too. From the [vcs-home](http://vcs-home.branchable.com/) page linked by Joey:
> 
[list]
[*]Richard "RichiH" Hartmann's [vcsh](https://github.com/RichiH/vcsh) is a fully-fledged suite to manage everything about your configs. It fully integrates with [mr](http://kitenet.net/~joey/code/mr) allowing you to be *really* lazy.
...
[*]Adam Spiers uses mr together with a [plugin](https://github.com/aspiers/kitenet-mr/blob/master/lib/stow) for [GNU Stow](http://www.gnu.org/software/stow/) (a symlink farm manager). This approach is in some respects similar to vcsh but uses symlinks rather than detached git working trees.[/list]


---

### Post by Harp on 2013-03-10
As an update, I've been using my "pre" command for the last week or so with no problems. It's quite handy, I find, to be able to create such detailed backups with a quick command before I edit a file.

I've updated the "pre" script to accept the input of files from the current working directory (without full paths). 

```
#!/bin/bash
# /usr/local/bin/pre
# Author: Russell Pinkston
# March 10, 2013
# License: GPL
#
# pre [file]
#
# Creates a link to, and a dated backup of, [file] in ~/.config/backups/

FILE=$1

for f in "$( readlink -f "$( dirname "$FILE" )" )/$( basename "$FILE" )" ; 
	do 
		cp -bu "$f" ~/.config/backups/"`basename ${f}`".$(date +%F) ; 
		ln -sf "$f" ~/.config/backups/"`basename ${f}`.ln" ;
	done
```

I've also come to the realization that, though this script is handy for backing up a file before I edit it, it does not keep a backup of the linked file's current state. For example, if I were to run a deja-dup backup of my /home directory, the files in my ~/.config/backups/ folder would only be backups of the previous states (from running "pre"), and not their current states. This is what papibe's script would be useful for. So, I've taken what papibe gave me and edited it to work with the same parameters as "pre." I've named it "post" and have also put it in my /usr/local/bin folder. 

```
#!/bin/bash
# /usr/local/bin/post
# Author: Russell Pinkston
# March 10, 2013
# License: GPL
#
# Creates a copy of the current state of all links at ~/.config/backups/*.ln
# Renames each copy as basename.YYYY.MM.DD

for f in ~/.config/backups/*.ln; 
	do 
		cp -bu "$f" "${f%.*}".$(date +%F) ;
	done
	
```

So, now I can run "$ pre [file]" on the command line to back up a file before editing it. And I can run "$ post" at any other time to create backups of all the linked files after editing them.

Pretty snazzy. If anyone has any suggestions for the code of these scripts, let me know. I would also like to be able to add something to the "post" script where it will only create a new backup if the file has changed since the latest backup.

---

### Post by Bucky Ball on 2013-03-10
[I]Thread moved to **Programming Talk**
[/I]
Please note; ***The Cafe*** is not for technical support. ;)

---

### Post by Harp on 2013-03-10
> **Bucky Ball said:**
> [I]Thread moved to **Programming Talk**
[/I]
Please note; ***The Cafe*** is not for technical support. ;)

Okay, thanks.

---

