---
title: "How to backup files from live DVD"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by dipper2 on 2014-07-23
I am currently running Ubuntu 12.04.4 (Linux 3.13.0-32-generic).

The recent HWE update caused my computer to give low graphic mode warnings and I have been unable to sort this out. See [here]("http://ubuntuforums.org/showthread.php?t=2234830&") if you are interested.

I have a live DVD for Ubuntu 14.04 and have been able to copy my documents and pictures to an external hard drive using copy/paste. I can't copy .Thunderbird (to save my emails and addresses) and using backup doesn't seem to do anything. I think (as a complete novice) that it is just looking at files in the DVD as the backup process only lasts a second and nothing appears on my external hard drive. I'm not worried about backing up my Firefox settings.

In simple terms (I am an absolute beginner) please would someone advise how I can save my emails and email addresses from Thunderbird before I carry out a factory reset. I have tried searching these forums but haven't found anything I understand! The computer is an HP Compaq that came preloaded with Ubuntu.

Many thanks.

---

### Post by SeijiSensei on 2014-07-23
If you copy your entire home directory (/home/username) to the external drive, you'll back up your mail and pretty much everything else associated with your account.

Thunderbird stores everything in /home/username/.thunderbird.  Firefox settings are in /home/username/.mozilla/firefox.  Note the dot at the beginning of each directory name.  Files and directories with a leading dot are "hidden" and not normally visible in directory listings. From the command prompt you can use "ls -a" to list hidden files; file managers like Nautilus and Dolphin usually have a menu entry and keystroke combination to turn the display of hidden files on or off.  In Dolphin it is Alt+period.

If you are going to install 14.04 and repartition the hard drive, you might consider allocating a separate partition for /home.  Then you can replace the OS and leave all your files untouched.  Use "manual partitioning" during installation.

---

### Post by Bucky Ball on 2014-07-23
I save the thunderbird and firefox profiles and just drop them in to the appropriate folders on the new install. Don't bother with the whole .Thunderbird or .Firefox folder. Just mentioning. ;)

---

### Post by dipper2 on 2014-07-23
Thanks for those comments. First of all, there are two 'Homes'. Presumably it's the one under 'Devices' that I need to copy.

If I highlight that 'Home', I don't get a copy option either with right click or from 'Edit'.

There are two users. If I highlight my account I can copy and paste but a lot of the folders won't copy/paste including .thunderbird, .mozilla-thunderbird and .dropbox. I get this message:

> The folder &#8220;.thunderbird&#8221; cannot be handled because you do not have permissions to read it.

Pictures, documents, desktop and a few others do get copied.

---

### Post by Bucky Ball on 2014-07-23
You could open a file manager as root and copy what you like, but be careful. Only do what you need to do then close the file manager. You can severely break your system as root.

gksudo nautilus

... will open Nautilus file manager as root and you should be able to copy what you like where you like. Do that then quit the file manager.

---

### Post by dipper2 on 2014-07-23
How do I copy and paste what I want when in root? What do I want? I'm learning but I'm still a novice!

---

### Post by dipper2 on 2014-07-23
Just had a little peek at that and got:

```
ubuntu@ubuntu:~$ gksudo nautilus
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ 
```

---

### Post by Bucky Ball on 2014-07-23
The 3.13.0-32 kernel is 14.04 as far as I know, not 12.04. ;)

You can install gksudo with the command provided by the terminal, but it is unusual if you haven't got the universe repository installed and open, which the terminal insinuates you haven't. Something would be wrong if that was the case.

---

### Post by dipper2 on 2014-07-23
This computer's got it in for me. Tried to install gksudo and got this:

```
ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksu
ubuntu@ubuntu:~$ 


```

---

### Post by Bucky Ball on 2014-07-23
Try ' sudo apt-get install gksudo'.

---

### Post by dipper2 on 2014-07-23
No change.

```
ubuntu@ubuntu:~$ sudo apt-get install gksudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksudo
ubuntu@ubuntu:~$ 

```

---

### Post by SeijiSensei on 2014-07-24
Open a command prompt and try this:
```

cd /
sudo rsync -av home /path/to/your/backup/

```
That will copy all of /home to /path/to/your/backup/home.  I recommend using "rsync -avn" first which will show you a list of the files that will be transferred so you can make sure everything is fine.  Remove the "n" to copy the files.

---

### Post by dipper2 on 2014-07-24
Thanks for that. My neighbour's a software engineer and he has managed to copy my files but I don't know what he did. I have now installed 14.04 LTS and it looks like all my old files are still there anyway.

Thanks for all the help.

---

### Post by kansasnoob on 2014-07-24
> **dipper2 said:**
> Thanks for that. My neighbour's a software engineer and he has managed to copy my files but I don't know what he did. I have now installed 14.04 LTS and it looks like all my old files are still there anyway.

Thanks for all the help.

Glad to see you got that sorted out :D

---

### Post by Bucky Ball on 2014-07-24
Excellent news. ;)

Please mark the thread as solved by following the second link in my signature. Good luck and enjoy.

---

### Post by Bucky Ball on 2014-07-24
Excellent news. ;)

Please mark the thread as solved by following the second link in my signature. Good luck and enjoy.

---

