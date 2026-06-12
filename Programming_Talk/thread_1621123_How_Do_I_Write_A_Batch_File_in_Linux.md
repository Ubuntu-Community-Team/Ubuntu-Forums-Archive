---
title: "How Do I Write A Batch File in Linux?"
date: 2010-11-13
forum: Programming Talk
---

### Post by argedion on 2010-11-13
I do hope that this is the appropriate forum for this question. 

I have a few batch files I used in Microsoft Windows that helped me to do ordinary task such as disk checks / defrags and other maintenance issues but one of the big things was my back up batch files. I really like the fact that I could click and Icon and all my important files were backed up to a central location then zipped up for storing on an external drive or optical disc. I would appreciate any help in this matter. 

Currently Running:
Compaq V5000
250 gig EIDE internal Hard drive
320 Gig Portable Hard drive
150 Gig External Hard drive 
2.O Gig of Ram
Windows XP Media Center sp3 with Ubuntu 10.04 LTS

---

### Post by tgalati4 on 2010-11-13
In the upper right corner is a search box.  Try searching:

rsync backup scripts

You will get a lot of hits including:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup+scripts](http://ubuntuforums.org/showthread.php?t=35087&highlight=rsync+backup+scripts)

For more specific help, post one of your backup batch files and maybe someone will transcribe it for you as a backup script.

To create an icon the the desktop, simply right-click and "Create Launcher".  Fill in the details and point to the backup script you just wrote.

The basic steps:

nano my_personal_backup_script.sh

(Edit the script and save it, Control-O, Control-X)

Make it executable:

sudo chmod +x my_personal_backup_script.sh

Run it:

./my_personal_backup_script.sh

Run it automatically by placing it in a crontab, either systemwide or personal.

Make a launcher icon on the desktop.

---

### Post by argedion on 2010-11-14
tgalati4 thanks for the info. I did a search however I used Linux Batch and I got nothing of relevance I didn't think to search for backup scripts. 

here is one of the backups I used to use for windows.

@echo Off

@echo Author: Argedion

@REM Purpose of File: To Back up Setting Files to ReWritable CD

@REM File Name: CDSav.bat

@REM Origination Date: 1:57 PM 4/16/2003

@echo.

cls

@echo.

@echo.
@copy C:\windows\system32\drivers\etc\hosts D:\mydocu~1\mysett~1\hostsf~1 /y > NUL

@copy C:\docume~1\argedion\locals~1\applic~1\micros~1\outlook\*.* D:\MyDocu~1\Micros~1\outlook /y > NUL

@echo Files Ready for Copying to Compact Disk Please Place ReWritable CD into Burner

@xcopy D:\mydocu~1\mysett~1\*.* f:\Stored\ /s /y > NUL

@xcopy D:\Projects\VB\*.* f:\MyBasic\ /s /y > NUL

This was used for sending stuff to the cd burner. I no longer use cd's with thumbdrives being so much easier to store and carry around. 

I mainly wish to just have a simple script to backup the /home folder to one of my thumb drives. Mainly I just want to save my files and not a bunch of programming files that are only good for now and not necessarily later I also wish to compress everything with 7zip before sending it to the thumb drive.

---

### Post by Barrucadu on 2010-11-14
"Batch" files in GNU/Linux are shell scripts; if you can use a terminal you can write scripts. I would link you to my backup script, but ubuntuforums is censoring the URL for some reason: [https://gith*******/Barrucadu/home/blob/master/bin/backup](https://gith*******/Barrucadu/home/blob/master/bin/backup)

---

### Post by argedion on 2010-11-14
Barracuda I was able to find this one

home / bin / backup

It almost looked like a complex program I would need some help setting up something of this nature considering the basic's of my batch file. I'm an old man willing to learn though all I need is a Good Teacher with Great Patience :D

---

### Post by cgroza on 2010-11-14
Linux Bash scripts is the equivalent of WInodows batch files.

---

### Post by ziekfiguur on 2010-11-14
a simple script to backup your home folder to a thumb drive would be:
```
#!/bin/bash
today=`date +%Y%m%d`
tar cPf - /home | 7za a -si /media/MY_THUMB/backup_$today.tar.7z 

```this makes a tar file containing your home directory, passes it to 7zip and stores it as backup_20101114.tar.7z on a drive called MY_THUMB if you run it today

to restore your files back run ```
$7za x -so /media/MY_THUMB/backup_20101114.tar.7z | tar x 
```from your / folder

---

### Post by argedion on 2010-11-14
ok thanks for the info.

I see I am going to have to learn bash besides the link to programming is there any other places to learn the basics

---

### Post by oldfred on 2010-11-14
My first bash file was a list of history where I had run several commands to test that they did what I wanted and copied them into a script.

The tar will combine & compress you files for smaller space, but some like to be able to see all the files and easily recover just one. rsync then is a command for that.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

One of many places to learn about bash:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
Whiptail is a program that allows shell scripts to display dialog boxes
[http://en.wikibooks.org/wiki/Bash_Shell_Scripting#Using_whiptail](http://en.wikibooks.org/wiki/Bash_Shell_Scripting#Using_whiptail)

---

### Post by argedion on 2010-11-14
Thanks oldfred

I really just want to be able to write some simple bash files to do the task of backing up and other task I may find usefull to do as I continue to learn linux. I never bothered with backup programs for the other OS because most of them came at a cost and I found it more comforting to write a batch file to do the job. While I continue to use batchfiles in that other OS since its a pretty stupid system and cant read my ext4 file system it makes it hard for me to use a batch in that system to backup my linux system. One thing this has taught me is even though I've been messing with linux for a few years I havent yet really learned anything about it. I guess my first approach needs to be understanding what commands are available and how to use them like I did the other OS. I'm to used to stuff like dir /w and xcopy this that /s . As much as I would like to writing bash files I really need to understand the commands that are available and how to use those first. I've just started reading an intro to linux figuring that was probably the best place to start. I have allowed that other system to make me a GUI junkie and a Command line Flunkie. Now I have to learn real computing. Anyone wanting to help an old man learn new tricks can email me *L* The one thing I do know is that I really love the Linux community and the amazing willingness to help poor wanna be's like me :P

---

### Post by _Fordy on 2010-11-14
Mainly for the benefit of googlers:

If you actually want to **write a batch file in Linux**, ie. you understand you can't run it under Linux, but you're writing it to use later under Win, then it's very simple:

Open gedit, type your commands, save it as whatever.bat

Linux won't recognise it, Win should.

In order to run Linux commands, save as .sh (shell) and the opposite is true.

---

### Post by wmcbrine on 2010-11-14
> **cgroza said:**
> Linux Bash scripts is the equivalent of WInodows batch files.Windows batch files are a pale shadow of Linux/Unix shell scripts. Shell scripts (the generic term; "bash" is just the default shell) can be extremely powerful. And shell scripts are much more central to the Unix world than batch files are to Windows.

---

### Post by tgalati4 on 2010-11-14
There are lots of Bash tutorials on the webz.  There are also lots of backup tools in the repositories for you to play with.  Some are better than others:

apt-cache search backup

---

### Post by argedion on 2010-11-15
one of the main reasons I wish to do a bash backup instead of a program is the ability to restore things in both OS's. I have found some tutorials and am starting there. I'm probably going to spend a bit of time in the forums cleaning up my scripts :) Does anyone know if there is a more preferred forum or a help community for programming in bash? or is this forum good for that?

---

### Post by ziekfiguur on 2010-11-15
A forum dedicated to bash scripting can be found at [http://bashscripts.org/forum/](http://bashscripts.org/forum/)
However, i think the people here will be able to answer most of your questions as well.

While learning bash it is useful to remember that most commands are documented pretty well, just type `man command' in your terminal. for example, for more information on the tar command you would run `man tar.' To exit the manual press q. Arrows and pageup, pagedown, home and end keys can be used to navigate through the document and when you type a / you can enter a sequence to search in the document, press enter to do the search and n to find the next occurrence after that.

---

### Post by WitchCraft on 2010-11-15
You can also learn Python or Perl for that matter.

Perl is more commonly used, while Python language design is better (IMHO, *ducking now*).

---

### Post by ziekfiguur on 2010-11-15
> **WitchCraft said:**
> You can also learn Python or Perl for that matter.

Perl is more commonly used, while Python language design is better (IMHO, *ducking now*).
I agree about Python's language design being better. But, for the purposes argedion describes, I think Bash would be a better option than Python (or Perl).

---

### Post by WitchCraft on 2010-11-15
> **ziekfiguur said:**
> I agree about Python's language design being better. But, for the purposes argedion describes, I think Bash would be a better option than Python (or Perl).

On the short run certainly, but probably not on the long run.

---

### Post by worseisworser on 2010-11-15
It might perhaps already have been mentioned, but both Perl and Python are a part of the LSB now:

[http://refspecs.linux-foundation.org/LSB_4.0.0/LSB-Languages/LSB-Languages/book1.html](http://refspecs.linux-foundation.org/LSB_4.0.0/LSB-Languages/LSB-Languages/book1.html)

---

### Post by argedion on 2010-11-15
Well I think at the moment I'll stick to learning Linux Commands and Understanding Bash before I delve into a real programming Language. I just hope your all available when I start getting stooopid with my scripting *L*

---

