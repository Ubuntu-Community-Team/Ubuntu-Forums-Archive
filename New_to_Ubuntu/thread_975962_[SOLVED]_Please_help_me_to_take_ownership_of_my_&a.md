---
title: "[SOLVED] Please help me to take ownership of my &amp;quot;HOME&amp;quot; folder"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-11-08
I eventually upgraded from 7.04 to 8.04 last night. I made two partitions on a HD, 20GB for system files and the rest for my HOME.

When booting up I get this message ;

Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writeable by others.

I can't customize my main menu, neither can I reinstall my applications by using "dpkg --set-selections < installed-software" - all for the same reason I believe.

I really need things explaining in the simplest of manners. Thanks for the help.

---

### Post by taurus on 2008-11-08
Try

```
sudo chown -R *username*:*username* /home/*username*
sudo chmod -R 755 /home/*username*
sudo chmod 600 /home/*username*/.dmrc
```
Replace *username* with your actual login name.

---

### Post by tahitiwibble on 2008-11-08
> **taurus said:**
> Try

```
sudo chown -R *username*:*username* /home/*username*
sudo chmod -R 755 /home/*username*
sudo chmod 600 /home/*username*/.dmrc
```
Replace *username* with your actual login name.

result of command line 1 is;

dad@dad-desktop:~$ sudo chown -R dad:dad /home/dad
[sudo] password for dad: 
chown: cannot access `/home/dad/.gvfs': Permission denied

---

### Post by cariboo on 2008-11-08
> chown: cannot access `/home/dad/.gvfs': Permission denied 

Thats normal.

Jim

---

### Post by tahitiwibble on 2008-11-08
> **cariboo907 said:**
> Thats normal.

Jim

How can I change that?

---

### Post by tahitiwibble on 2008-11-08
> **taurus said:**
> Try

```
sudo chown -R *username*:*username* /home/*username*
sudo chmod -R 755 /home/*username*
sudo chmod 600 /home/*username*/.dmrc
```
Replace *username* with your actual login name.

Further results;

dad@dad-desktop:~$ sudo chmod -R /home/dad
chmod: missing operand after `/home/dad'
Try `chmod --help' for more information.

dad@dad-desktop:~$ sudo chmod 600 /home/dad/.dmrc
dad@dad-desktop:~$ 

I'm lost.

---

### Post by bettlebrox on 2008-11-08
> **taurus said:**
> Try

```
sudo chown -R *username*:*username* /home/*username*
sudo chmod -R 755 /home/*username*
sudo chmod 600 /home/*username*/.dmrc
```
Replace *username* with your actual login name.

>sudo chmod -R 755 /home/*username*
**Don't do that!** This will change permissions on every directory AND file in your home directory and most regular files shouldn't have the execute bit set.

>sudo chmod 600 /home/*username*/.dmrc[/code]
Nope to that too ... you want to do "chmod 644 /home/dad/.dmrc" as the warning says:

[INDENT]Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.* File should be owned by user and have 644 permissions*.[/INDENT]

Can you issue this command on the .dmrc file and post the output:

[INDENT]ls -l /home/dad/.dmrc[/INDENT]

It will show what the permissions and ownership of the file are.

---

### Post by tahitiwibble on 2008-11-08
> **bettlebrox said:**
> >sudo chmod -R 755 /home/*username*
**Don't do that!** This will change permissions on every directory AND file in your home directory and most regular files shouldn't have the execute bit set.

>sudo chmod 600 /home/*username*/.dmrc[/code]
Nope to that too ... you want to do "chmod 644 /home/dad/.dmrc" as the warning says:

[INDENT]Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.* File should be owned by user and have 644 permissions*.[/INDENT]

Can you issue this command on the .dmrc file and post the output:

[INDENT]ls -l /home/dad/.dmrc[/INDENT]

It will show what the permissions and ownership of the file are.

:shock: but I already did both!!

dad@dad-desktop:~$ ls -l /home/dad/.dmrc
-rw------- 1 dad dad 26 2007-11-21 12:43 /home/dad/.dmrc

---

### Post by m_l17 on 2008-11-09
> **tahitiwibble said:**
> 
dad@dad-desktop:~$ ls -l /home/dad/.dmrc
-rw------- 1 dad dad 26 2007-11-21 12:43 /home/dad/.dmrc

That's the correct permissions for that file.

[QUOTE=bettlebrox]>sudo chmod -R 755 /home/username
Don't do that! This will change permissions on every directory AND file in your home directory and most regular files shouldn't have the execute bit set.
[/QUOTE]

The above is correct. Always be careful with the -R option. I'm not 100% sure, but that should not affect much.

---

### Post by tahitiwibble on 2008-11-09
> **tahitiwibble said:**
> I eventually upgraded from 7.04 to 8.04 last night. I made two partitions on a HD, 20GB for system files and the rest for my HOME.

When booting up I get this message ;

Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writeable by others.

I can't customize my main menu, neither can I reinstall my applications by using "dpkg --set-selections < installed-software" - all for the same reason I believe.

I really need things explaining in the simplest of manners. Thanks for the help.

I wonder if there's anyone around at this time of day that may be able to help me out, so ............. bump :confused:

---

### Post by m_l17 on 2008-11-09
Post the output of:

```
ls -la /home/
```

should look like this:

> drwxr-xr-x  5 root root     4096 2008-10-31 06:38 .

drwxr-xr-x 22 root root     4096 2008-11-01 03:21 ..

drwxr-xr-x  2 ftp  nogroup  4096 2008-10-31 06:38 ftp

drwx------  2 root root    16384 2008-10-31 03:13 lost+found

drwxr-xr-x 35 ml   ml       4096 2008-11-09 04:07 ml


---

### Post by tahitiwibble on 2008-11-09
> **m_l17 said:**
> Post the output of:

```
ls -la /home/
```

dad@dad-desktop:~$ ls -la /home/
total 28
drwxr-xr-x  4 root root  4096 2008-11-07 21:22 .
drwxr-xr-x 21 root root  4096 2008-11-08 20:38 ..
drwxrwxrwx 96 dad  dad   4096 2008-11-09 10:30 dad
drwx------  2 root root 16384 2008-11-07 21:14 lost+found

Can anyone help me out here? I'm desperate to get my system up and running again.

---

### Post by tahitiwibble on 2008-11-09
Perhaps I should go through the whole formatting, re-installation, copy HOME backup etc etc again and hope for better luck next time around??

---

### Post by drs305 on 2008-11-09
What exactly do you need help with at present? Although running the chmod -R 755 command is not the best way to go, it probably hasn't done irreparable 'damage' to the way your system operates. 

If it is the customizing menus we can deal with that next.

Please feel free to PM me if you prefer that method.

---

### Post by tahitiwibble on 2008-11-09
> **drs305 said:**
> What exactly do you need help with at present? Although running the chmod 755 command is not the best way to go, it probably hasn't done irreparable 'damage' to the way your system operates.

Please feel free to PM me if you prefer that method.

I still have exactly the same problem as in my original post. Although now I'm even more worried about having possibly made the situation worse by doing stuff that I was advised to do in this thread.

---

### Post by drs305 on 2008-11-09
I just posted a tutorial on your situation over in the Tutorials section. Here is the link:
[ Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610")

If that doesn't cover it post back or PM me.

---

### Post by mapes12 on 2008-11-09
I hate to ask such a stupid question but: Did you backup /home before embarking on the upgrade.............Ouch!:shock:

---

### Post by tahitiwibble on 2008-11-09
> **drs305 said:**
> I just posted a tutorial on your situation over in the Tutorials section. Here is the link:
[ Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610")

If that doesn't cover it post back or PM me.

That has solved the error message while logging in. I'm going to try to reinstall my programs now.

---

### Post by tahitiwibble on 2008-11-09
> **mapes12 said:**
> I hate to ask such a stupid question but: Did you backup /home before embarking on the upgrade.............Ouch!:shock:

Yes I did, thank heavens :) I even had a backup of the HOME backup (very fortunately because somehow or other I destroyed my backup HD - and there went all my photos and music from the past few years :( )

---

### Post by tahitiwibble on 2008-11-09
> **drs305 said:**
> I just posted a tutorial on your situation over in the Tutorials section. Here is the link:
[ Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610")

If that doesn't cover it post back or PM me.

Your error fix worked perfectly. Heartfelt thanks to you.

I tried to reinstall my programs using "dpkg --set-selections < installed-software" in the terminal. The response was "dpkg: operation requires read/write access to dpkg status area". Would you be able to help?

---

### Post by drs305 on 2008-11-09
Importing the selections from a file requires administrative powers. Run the command preceded with "sudo". (Also make sure you are in the folder with the selections file or provide the full path.)

---

### Post by tahitiwibble on 2008-11-09
> **drs305 said:**
> Importing the selections from a file requires administrative powers. Run the command preceded with "sudo". (Also make sure you are in the folder with the selections file or provide the full path.)

I used this procedure [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) to create the file "installed-software"

This is a history of my actions from the past few minutes;

dad@dad-desktop:~$ sudo dpkg --set-selections < installed-software
[sudo] password for dad: 
dad@dad-desktop:~$ cd home
bash: cd: home: No such file or directory
dad@dad-desktop:~$ cd /home
dad@dad-desktop:/home$ sudo dpkg --set-selections < installed-software
bash: installed-software: No such file or directory

Why would the file not be recognized?

---

### Post by drs305 on 2008-11-09
To get to your home folder, use "cd $HOME". If the file is on your desktop, the command would be "cd $HOME/Desktop".

If you run the "ls" command in terminal right before you run the command do you see a listing for "installed-software"? If not, you are not in the correct directory - i.e. you may or may not be in your Home or Home/Desktop folder, but you aren't in the same directory as the file you are trying to use (installed-software).  

If you don't know where 'installed-software' is, run:
```
sudo find / -type f -iname 'installed-software'
```

Added: Also, note that to change into *your* home the traditional command would be " cd /home/*yourusername*". Under /home, there could be lots of users (/home/bob, /home/jane, etc) and even if there are not the /home area is owned by root.

---

### Post by tahitiwibble on 2008-11-09
> **drs305 said:**
> To get to your home folder, use "cd $HOME". If the file is on your desktop, the command would be "cd $HOME/Desktop".

If you run the "ls" command in terminal right before you run the command do you see a listing for "installed-software"? If not, you are not in the correct directory - i.e. you may or may not be in your Home or Home/Desktop folder, but you aren't in the same directory as the file you are trying to use (installed-software).  

If you don't know where 'installed-software' is, run:
```
sudo find / -type f -iname 'installed-software'
```

Added: Also, note that to change into *your* home the traditional command would be " cd /home/*yourusername*". Under /home, there could be lots of users (/home/bob, /home/jane, etc) and even if there are not the /home area is owned by root.

You solved my problems! **Thank you!**

---

