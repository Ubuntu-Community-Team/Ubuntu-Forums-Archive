---
title: "Linux Commands?"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by dalestenberg on 2012-05-09
I recently did a fresh install of Ubuntu 12.04. I have been adding programs trying to get familiar with using the terminal. What I'm asking is if anyone has some code for the terminal that could either be essential, or neat! I'm just exploring so any program recommendations would be great! Thanks in advance

---

### Post by wilee-nilee on 2012-05-09
This might a good start it has info and links.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

You can also look up Linux commands as well, as well as languages I would think, none of which I know though.

---

### Post by HeroOfCanton on 2012-05-09
There are some command line games. Running and playing them should help ease into more cli tools.

Couple of articles with suggestions:
[Make Use Of]("http://www.makeuseof.com/tag/play-games-inside-your-linux-terminal/")
[Top 10 Games]("http://www.the-tech-tutorial.com/?p=577")

Also, there are a lot of useful scripts floating around in the signatures on the forums. Download some of them to see what they do and how they work.

---

### Post by dalestenberg on 2012-05-09
Thank you so much!

---

### Post by 3rdalbum on 2012-05-09
You may already know this, but most commands in the terminal have a manual.

For instance, you know the command 'apt-get'? You can bring up a manual about how to use the 'apt-get' command:

```
man apt-get
```

Man is short for Manual.

Press Q to exit the manual.

I'll give you a neat little piece of code that might be useful if you were making a Bash script. First, install the "libnotify-bin" package:

```
sudo apt-get install libnotify-bin
```

Whenever you want to cause a notification to appear on your desktop, you can send one using the 'notify-send' command:

```
notify-send "Hello, world!"
```

If you look at the manual for the notify-send command, you'll be able to figure out how to make more attractive notifications, such as this one:

```
notify-send -i "info" "Hello, world" "This was a test"
```

---

### Post by Shadius on 2012-05-09
> **3rdalbum said:**
> You may already know this, but most commands in the terminal have a manual.

For instance, you know the command 'apt-get'? You can bring up a manual about how to use the 'apt-get' command:

```
man apt-get
```

Man is short for Manual.

Press Q to exit the manual.

I'll give you a neat little piece of code that might be useful if you were making a Bash script. First, install the "libnotify-bin" package:

```
sudo apt-get install libnotify-bin
```

Whenever you want to cause a notification to appear on your desktop, you can send one using the 'notify-send' command:

```
notify-send "Hello, world!"
```

If you look at the manual for the notify-send command, you'll be able to figure out how to make more attractive notifications, such as this one:

```
notify-send -i "info" "Hello, world" "This was a test"
```

This is cool! This thread might help as well.

[http://ubuntuforums.org/showthread.php?t=1909108]("http://ubuntuforums.org/showthread.php?t=1909108")

---

### Post by daslinkard on 2012-05-10
This [link]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") will take you to the download for The Command Line by William Shotts, Jr.  Good stuff here.

---

### Post by mikodo on 2012-05-10
Link was posted already!

---

### Post by plant on 2012-05-10
$top

Top is a good command the show users what all programs are running in the background and how much memory the programs are using. It also displays the process id's of the programms.

If any program gets struck, you can find the pid using this command and then 
issue a kill command to end the struck program

$kill -9 <pid>

---

### Post by dalestenberg on 2012-05-10
This was AWESOME!!!!! Can you put a time delay on it. For example can I tell it to send the message at a particular time like notify-send "Check bank account"?

---

### Post by Niemand000 on 2012-05-10
Wow man, have I got something for you! I was in the exact same spot you're in now and this "crash course" has helped me out *tremendously*!! 
[http://cli.learncodethehardway.org/book/](http://cli.learncodethehardway.org/book/)
It's a free book, he walks you through all the basics.  The only other way you'll start to get pretty good with it is when you start encountering problems with your drivers. i.e. I'm having issues with my internet not working on my laptop requiring me to root around in terminal but teaching me a LOT of cool commands in the process i.e.
sudo lshw-class network
and 
dmesg 
dmesg | grepiwl


Another one I can tell you about is 
sudo apt-get install youtube-dl
which is a youtube downloader, from then on just type in youtube-dl and the web address for a youtube video and it'll start downloading!!! :D

---

### Post by 3rdalbum on 2012-05-11
> **dalestenberg said:**
> This was AWESOME!!!!! Can you put a time delay on it. For example can I tell it to send the message at a particular time like notify-send "Check bank account"?

You sure can. There's at least two different ways of doing it.

The first way is to use the "sleep" command to make the terminal wait for a specified number of seconds:

```
sleep 120
notify-send "Your cup-a-noodles are ready!"
```

Or you can set it for minutes or hours:

```
sleep 2m
notify-send "Your cup-a-noodles are ready!"
```

The disadvantage with using 'sleep' is that it requires the terminal to be open. If you close the terminal, your command does not get run. So I use the "at" command instead:

```
at midnight
at now + 3 hours
at 3:00pm tomorrow
```

Such a versatile command! After inputting the 'at' command such as one of the three examples above, you'll be given a little shell to input what commands you want to be run at this specified time. After putting in all the commands and pressing Enter, you need to press Control-D and then your work will be saved and the job will be queued up.

So, this is the contents of my terminal after queueing up your hypothetical "Check bank account" job:

```
chris@chris-desktop:~$ at now + 1 week
warning: commands will be executed using /bin/sh
at> notify-send "Check bank account"
at> <EOT>
job 13 at Fri May 18 18:22:00 2012
chris@chris-desktop:~$ 
```

The EOT bit is where I pressed Control-D.

The "at" jobs you set will run even if you had turned your computer off in the meanwhile; if your computer is off while the job was meant to run, it will be run the next time you turn the computer on. So, don't set "halt" as the command to run in two minutes, and then turn your computer off manually. The next time you start up your computer will run the 'at' job and then turn off by your command :-)

See "man at" for more information, including on how to delete 'at' jobs.

---

### Post by dalestenberg on 2012-05-11
What a tremendous help you have been... If there are any other suggestions feel free to share. I'm learning on how to build directories right now. The one thing that I can not figure out is how to import data from windows to ubuntu... I'm running both of them on my laptop.

---

### Post by ammofreak on 2012-05-11
Hi ):P
For a newbie, I would recommend the following link for command line: [http://linuxcommand.org/...Hope](http://linuxcommand.org/...Hope) this helps...:)

---

### Post by Shadius on 2012-05-11
> **ammofreak said:**
> Hi ):P
For a newbie, I would recommend the following link for command line: [http://linuxcommand.org/...Hope](http://linuxcommand.org/...Hope) this helps...:)

Fix the link. It should be [Linux Command]("linuxcommand.org") Well, I fixed it for you. Hope you don't mind. :)

---

### Post by ammofreak on 2012-05-11
Not a problem....I would rather have good direction than bad. 
Thanks again!!!:)

---

### Post by alphacrucis2 on 2012-05-11
> **dalestenberg said:**
> What a tremendous help you have been... If there are any other suggestions feel free to share. I'm learning on how to build directories right now. The one thing that I can not figure out is how to import data from windows to ubuntu... I'm running both of them on my laptop.

Ubuntu should be able to see the Windows partition. It should be listed under devices in Nautilus. If you click on it, Nautilus should mount it and you can access it as you do your linux files and directories. You can also mount it from the command line using the mount command. Nautilus mounts it as

/media/Windows7_OS

on my laptop. I think it just uses the partition label as the mount directory name.

---

### Post by codemaniac on 2012-05-11
> **dalestenberg said:**
> What a tremendous help you have been... If there are any other suggestions feel free to share. I'm learning on how to build directories right now. The one thing that I can not figure out is how to import data from windows to ubuntu... I'm running both of them on my laptop.

All you can do is mount your windows partitions if it is not automounted and copy the data from windows partition to Ubuntu .

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

