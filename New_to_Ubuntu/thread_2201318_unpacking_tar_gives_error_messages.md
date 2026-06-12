---
title: "unpacking tar gives error messages"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-23
I am trying to unpack a tarball created on a different computer and copied to the subject computer.

each line outputs error messages. Here is a sample:

```
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/Mount a device, including locating the device.txt: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/ChangeComputerName
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/ChangeComputerName: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/Grub Repair-Reinstall
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/Grub Repair-Reinstall: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup: Cannot mkdir: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/CopyHomeToDifferentHDD
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/CopyHomeToDifferentHDD: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/Unison-2.27.157-manual.pdf
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/Unison-2.27.157-manual.pdf: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/HowToMoveAppData&Prefs.txt
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/FileTransfer&Backup/HowToMoveAppData&Prefs.txt: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/Mount devices~
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/Mount devices~: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/BIOS & MOBO Profiler
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/BIOS & MOBO Profiler: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/Win-linux file sharing
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/Win-linux file sharing: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/Find USB Devices
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/Find USB Devices: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/HardwareProfiler4Linux
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/HardwareProfiler4Linux: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/HowTo's/Move "forward slash home" to it’s own partition
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/HowTo's/Move "forward slash home" to it’s own partition: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/Linux Stuff.tar.gz
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/Linux Stuff.tar.gz: Cannot open: No such file or directory
home/robert/Desktop/Linux Stuff/ Grub Loading......Error 18.txt~
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Linux Stuff/ Grub Loading......Error 18.txt~: Cannot open: No such file or directory
home/robert/Desktop/Rebuild Icons.bat
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Desktop/Rebuild Icons.bat: Cannot open: No such file or directory
home/robert/Band Vista Q's
tar: home: Cannot mkdir: Permission denied
tar: home/robert/Band Vista Q's: Cannot open: No such file or directory
tar: Exiting with failure status due to previous errors
robert@robert-HP:/media/Data$ ls

```

Robert installed both computers with the name robert, so /home/robert is my home directory on both. Is this a permission issue, or do I need to make the directories betore unpacking (surely not?)?

Or what is the issue?

---

### Post by gudrade on 2014-01-23
Hi!

What command did you use?
You can try **sudo** before this command, but check it first.

---

### Post by Odyssey1942 on 2014-01-23
Thanks for the suggestion. The reason I did not use sudo is that I have it in mind that if you are in your own home and use sudo, you assign the permissions of the super user.

Now this happens to be me and the passwords are the same, but I don't want to get everything unpacked and then denied access to my own data.

Please comment/clarify

---

### Post by gudrade on 2014-01-23
Use **chown robert:robert name_of_package **and **chown -R robert:robert destination**. See if it will return some error message.
But, what command did you use to unpack?

---

### Post by Odyssey1942 on 2014-01-23
Sorry, I must have skipped over that. The command was:

```
tar -xpvf 140118susiehome.tg
```

In terminal, entering either:

```
sudo chown robert:robert 140118susiehome.tg
```

or

```
chown robert:robert 140118susiehome.tg
```

brings me back to the prompt, i.e., ignores the commands.

Would it be helpful to have the tar creation command as well? I can retrieve it if so.

---

### Post by gudrade on 2014-01-23
I think that you don't have permission in **/media/Data.**
Try **ls -l **and see yours permissions.
The permissions of the package is valid to **/home/robert**.

Yes, I would see the tar creation command.
You also can try this command to unpack: **tar -zxvf 140118susiehome.tg /home/robert/test/**

---

### Post by Odyssey1942 on 2014-01-23
I went back as far as pressing the up arrow key would take me, but apparently the exact command is lost from the history of the terminal. I was later updating the files in the tarball with this command:

```
tar cpf /home/robert/backup-robert/140118home.tg --exclude=/home/robert/music --exclude=/home/robert/.Trash --exclude=/home/robert/backup-robert --exclude=/home/robert/.thumbnails  --exclude=/home/robert/.* --exclude=/home/robert/downloads /home/robert
```

which I think other than the filename of the tarball is substantively similar to the earlier command.There might have been a change or two in the exclusions, but I don't think those would be significant.

```
robert@robert-HP:/media/Data$ sudo ls -l
total 14286392
-rwxr--r-- 1 robert robert 14629242880 Jan 19 08:53 140118susiehome.tg
drwx------ 2 root   root         16384 Jan 19 18:08 lost+found

```

Not sure I understand this:

> /The permissions of the package is valid to /home/robert.

Can I ask you to please elaborate on that?

Also, not sure if there is enough room in /home to unpack using

```
tar -zxvf 140118susiehome.tg /home/robert/test
```

If I go to /home in Nautilus, right click and choose properties, it says there is 17.6 GB free. This tarball is 14.6GB. Is this going to leave enough free space in a 20GB partition if it unpacks it there?

Also is " test " in "  /home/robert/test " a directory? If so, I will need to mkdir, no? Sorry for these basic questions, but I am a very primitive level of understanding of the terminal.

---

### Post by sandyd on 2014-01-23
```

sudo mkdir /media/Data/tmp
cd /media/Data
sudo mv 140118susiehome.tg /media/Data/tmp
sudo chown -R robert:robert /media/Data/tmp
cd /media/Data/tmp
tar xvf 140118susiehome.tg 
```
Try the above, will extract into /media/Data/tmp

---

### Post by Odyssey1942 on 2014-01-23
Thanks for the code. I have done all that except unpacking the tarball. Do I not need to include " p " in the tar command to preserve file permissions?

---

### Post by Odyssey1942 on 2014-01-24
If anyone could respond regarding the " p " parameter question, it would be appreciated. I am holding off on the unpacking to ensure that I don't have to do it all (i.e., remaking the tarball, getting it to this computer, etc.) again. Thanks.

Edit: Also I want to learn something from this exercise. I understand all of the commands except:

> sudo chown -R robert:robert /media/Data/tmp

If anyone could explain exactly what chown is doing, I would be much obliged as permissions are a total mystery to me.

And I remain hopeful of receiving guidance regarding

> tar xvf 140118susiehome.tg

partly because I do not understand chown (and don't want to use " p " and un-do what chown above has done), and partly because I do not want to recreate this entire exercise (and so don't want to not use " p " if it is needed.) Thanks.

---

### Post by varunendra on 2014-01-24
> **Odyssey1942 said:**
> If anyone could respond regarding the " p " parameter question, it would be appreciated. I am holding off on the unpacking to ensure that I don't have to do it all (i.e., remaking the tarball, getting it to this computer, etc.) again. Thanks.
Yes, the 'p' switch is necessary to preserve the 'Old' permissions. But do you really want to retain them?
If you are extracting this data so that the current user can use it, you better extract without the 'p' switch so that the extracted files are owned by the user who is extracting them. With sudo, this user would be root, without sudo, it would be the currently logged in user - you (or from whichever user's account you are doing this).

> If anyone could explain exactly what chown is doing, I would be much obliged as permissions are a total mystery to me.
The "chown" command is used to change the ownership of the target data to the user (or user:group) specified as its argument. The "-R" option makes this change of ownership recursive.

So.. the command -
```
sudo chown -R robert:robert /media/Data/tmp
```
..makes the user "robert" and his user-group the owner of the directory "tmp" and everything inside it.

Once you are owner of the directory, you automatically have read/write permissions inside it, so extracting the contents of the archive (which implies 'writing' the extracted contents) remains no more a problem.

Now an advice based on information from your [previous thread]("http://ubuntuforums.org/showthread.php?t=2200667") :

You seem to have mounted the ext4 partition in [s]/mnt/Data[/s] /media/Data that you created using Gparted. Since Gparted is run using root privileges, (I think..) the owner of the created partition is by default 'root'. I believe this is something you don't want. To change the ownership of the created partition, you can simply change the ownership of its mount-point. Which means almost the same command as sandyd suggested, only applied to the mount-point itself instead of a directory (temp) inside it -
```
sudo chown robert:robert /media/Data
```
..assuming the mounted partition is empty and the files/folders are copied to it 'After' taking its ownership. If the file/folder are already there and you don't want to start clean again, add the "-R" switch -
```
sudo chown -R robert:robert /media/Data
```
The only thing that I am slightly skeptical about this is that the above command (with -R switch) will also change the ownership of the "lost+found" directory which is not a problem, but usually it is better to leave its ownership to root. With the previous form of command (without the -R switch), that is achieved. Any new directories/files created or copied (not 'moved') after changing the ownership will automatically inherit the ownership of the parent directory, that is, the /media/Data directory, which by now you have changed to 'robert'.

Hope that helps clearing your doubts. :)

---

### Post by Odyssey1942 on 2014-01-24
Varun, Very helpful. Thank you.

Not necessarily for Varun, but also very welcome, I am wondering if the following impacts. When I boot the computer into Ubuntu, I sign is as robert. Would that not make me root?

I am also robert as user in /home/user. 

If I need sudo, my password is the same as when I turn on the computer (i.e., same as root).

Since both instances (i.e., root and user) are robert, does this make the issue go away, or does Ubuntu somehow know that robert as root is  different from robert as user?

Does anyone have a reference that discusses ownership and permission in simple terms? And groups, which is another total mystery. I have no idea what a group is.

I have read the man pages and am not much the wiser. Is there a man pages for those of us who cannot understand the language of the normal man pages?

---

### Post by Dave_L on 2014-01-24
> **Odyssey1942 said:**
> Does anyone have a reference that discusses ownership and permission in simple terms? And groups, which is another total mystery. I have no idea what a group is.

I have read the man pages and am not much the wiser. Is there a man pages for those of us who cannot understand the language of the normal man pages?

Does this help?

[https://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions](https://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions)

Note that some of the commands in that guide require sudo, although that's not shown there.

---

### Post by Odyssey1942 on 2014-01-24
Dave that looks promising and I will proceed to study. 

Any thoughts on the root/user question?

---

### Post by Dave_L on 2014-01-24
> **Odyssey1942 said:**
> Dave that looks promising and I will proceed to study. 

Any thoughts on the root/user question?

This article might be helpful to read, at least the first part of it: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Your user "Robert" has administrative privileges. That enables the user to temporarily "become" root by using sudo.

---

### Post by Odyssey1942 on 2014-01-24
Thanks all. Closing thread.

---

### Post by varunendra on 2014-01-24
> **Odyssey1942 said:**
> When I boot the computer into Ubuntu, I sign is as robert. Would that not make me root?
No. If you sign in as "robert" you are "robert", not root. Nobody can login '**as**' root, only root can and root account is disabled on Ubuntu by default (for good).

One can have '**almost same**' privileges as root, but never have all of them as that would effectively make them root itself. The 'root' account is the supreme authority on Unix/Linux based systems and no other user can have the same 'full' authority over the system in any case (or I don't know if that is possible).

> If I need sudo, my password is the same as when I turn on the computer (i.e., same as root).
What 'sudo' asks for is 'Your' password, not that of root. As the root account is disabled on Ubuntu, it has no password at all.

Supplying 'Your' passwords gives you root privileges (for 15 minutes by default, calculated from the last action done as root) because your account (the 'First' account on Ubuntu always is) is a member of the group 'sudo'. Any member of this group has the right to gain root privileges (temporarily) by supplying their own password.

> [COLOR="#FF0000"]Since both instances (i.e., root and user) are robert,[/COLOR] does this make the issue go away, or does Ubuntu somehow know that robert as root is  different from robert as user?
Since the part highlighted in Red above is a false assumption, the rest of the assumption is wrong as well. Ubuntu (or Linux) knows you are not root, unless you log in as 'root' (once again, not possible on Ubuntu until you manually enable the root account first, which is highly discouraged for Ubuntu. See the "..RootSudo" link given by Dave to know why).

Even when you have been granted root privileges by 'sudo', the system knows you are not root itself, just a user with root privileges. There are some very important implications of this.

When you are a user, and are performing some task with 'sudo', you are using your own home (/home/user) and your own configuration files, settings etc. If such an action involves writing/modifying files, they will become owned by root (which is why it is recommended to use 'gksu' - a different thing, instead of 'sudo' for running graphical applications which most often use the user's configuration files which may be modified during their operation).

On the other hand, if you actually become root (by logging in as root, or by "sudo su" command), or use '**gksu**' (not installed by default on 13.04 and later versions of Ubuntu) instead of 'sudo', you would be using the root's home (/root) and its configuration files, settings etc. Any program run in this mode will modify root's file (if it does involve creating/modifying files), not of any user's.

There are a few quick tricks to check/verify this when you are in confusion, like running "ls ~/" command in both modes (once "sudo ls ~/", then "sudo su" followed by "ls ~/"). With sudo, you will see your own files in your own home. But after becoming root with "sudo su", the same command will show you the contents of root's home (the "~/" expression expands to current user's home, also represented as "/home/$USER").

It is Very Important to note that if you run "sudo su" in terminal, you will become root and will stay root until you exit that mode by running 'exit' command. Normally the 'exit' command will close the terminal. But when in "su" (or root) mode, it will just return from root mode to normal user mode. The indication for normal user is a dollar sign ($) at the end of terminal prompt. The indication for root is a hash (#) at the terminal prompt. Running terminal as root can be dangerous (you may accidentally change the ownership of your configuration files to root, thus being locked out of your account). So one should use "sudo su" only when absolutely necessary and should immediately exit that mode as soon as the job is done.

There is much reading regarding these, but read only as much as interests you. Being prepared is a good idea, but practically one can never be fully prepared for everything. There are many things which most of us have learnt by "Trial & Error", and many things are easier to remember when you have practical examples of them.

Hope I explained only what was interesting for you, and sorry if I made it heavier with unnecessary details/examples.

One more thing - keep in mind that almost all of us are just users and most of things that you'd be told here are our own understanding/interpretation/assumption of them, and we may be wrong... even the developers themselves can be wrong sometimes with their own creations. So keep an open mind, be always ready for revelations and surprises. :)

---

### Post by Odyssey1942 on 2014-01-24
Varun, what a great reply, thorough and very clearly written. Thank you, for this clears up one of the several "black dogs on the mantle" that loom in the back of my mind, along with the earlier light you shed on ownership and permissions. Your "caution" is noted.

BTW, for anyone reading this and who may be interested I am starting another thread on linking, which follows on from this thread, and is the "next step" in my current odyssey. Title will be "Linking back to /home".

---

### Post by varunendra on 2014-01-24
Glad you liked it, usually I get scared myself with the length of my posts :P

> **Odyssey1942 said:**
> BTW, for anyone reading this and who may be interested I am starting another thread on linking, which follows on from this thread, and is the "next step" in my current odyssey. Title will be "Linking back to /home".

..and whose link is this : [http://ubuntuforums.org/showthread.php?t=2201514](http://ubuntuforums.org/showthread.php?t=2201514)

Although we already seem to have **oldfred** there, yet I believe we all 'crazy minds' can join the fun as long as we have clear ideas about the problem with clear instructions to implement them. :)

---

