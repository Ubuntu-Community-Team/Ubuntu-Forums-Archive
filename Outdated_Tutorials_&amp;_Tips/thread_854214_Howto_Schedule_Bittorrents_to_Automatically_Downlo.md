---
title: "Howto: Schedule Bittorrents to Automatically Download"
date: 2008-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by simon_ives on 2008-07-09
**Howto:** Schedule Bittorrents to Automatically Download

Ever wondered if you could schedule your torrent downloads to occur in those times when you are not using you computer, when you know that there will be more people online sharing the file your downloading, or perhaps during the off-peak times of your Internet plan?  Well this tutorial is for you.  I will explain how to install all of the relevant software and configure your system to do all this in a few easy to follow steps.

**1.** We need to make sure that the relevant software is installed on our system.  To do this we start up Synaptic Package Manager

[INDENT]System &#8594; Administration &#8594; Synaptic Package Manager[/INDENT]

and search for 'bittorrent'.  Select 'bittorrent' from the options and click 'Apply' to install it with all of its dependencies.  If you've already got bittorrent installed then it will already be selected in the list and you won't need to perform this step.

**2.** Next we need to create the directory that we will download our torrents into.  You can use any directory that you have permission to use for this this but a sub-directory in your home directory will often make things easier.  For this tutorial I will be using a sub-directory in the user's home directory called 'torrents'.  To create this directory simply navigate to your home directory

[INDENT]Places &#8594; Home Folder[/INDENT]

right click on some empty space and select 'Create Folder'.  Name this folder 'torrents'.

**3.** To automate the task of downloading torrents, and stopping the downloads at an appropriate time, we are going to create some very simple bash scripts (For more on bash scripts see [[COLOR="Cyan"]here[/COLOR]]("http://en.wikipedia.org/wiki/Bash_script")).  We will use the familiar graphical text editor gedit for this task.

In your home folder right click some empty space and select

[INDENT]'Create Document' &#8594; 'Empty File'[/INDENT]

Name this file 'bittorrentstart.sh'.  Perform this task again to create another file and call this one 'bittorrentstop.sh'.  You can place these files anywhere you like, perhaps in a directory called 'scripts', but this tutorial will assume they are in your Home directory.
Right click the file 'bittorrentstart.sh' and open it with your text editor.  Paste in the following information:

```
[INDENT]#!/bin/sh
# Start Downloading Torrent Files!
# Written by Simon Ives - http://www.simonives.info
#
echo "Starting the Download Torrents Script"
#
echo "Checking for Torrent files"
#
if [ -f /home/Your_User_Name/torrents/*.torrent ]; then
	echo "Executing Bittorrent Application and saving progress to torrent.log"
	nohup btlaunchmany /home/Your_User_Name/torrents > /home/Your_User_Name/torrents/torrent.log &
else echo "No Torrent files found"
fi[/INDENT]
```

Make sure you change the 'Your_User_Name' to your user-name.  Save this file.  This script will search your torrents directory for *.torrent files and if it finds one or more it will execute the Bittorrent application.

Open 'bittorrentstop.sh' and paste in the following information:

```
[INDENT]#!/bin/bash
# Stop Downloading ALL Torrent Files!
# Written by Simon Ives - http://www.simonives.info
echo "Stopping all bittorrent downloads"
killall btlaunchmany[/INDENT]
```


**4.** The second part of automating the downloading of torrents is to tell our computer when to execute the start script and execute the stop script.  To do this we use a tool called cron (for more on cron see [[COLOR="Cyan"]here[/COLOR]]("http://en.wikipedia.org/wiki/Cron")).  To make the editing of cron entries simple we are going to create a text file that we will edit in gedit (like the bash scripts above) and then append it to our cron entries.

While in your Home directory right click on some empty space and select

[INDENT]'Create Document' &#8594; 'Empty File'[/INDENT]

Name this file 'cron.txt'.  Double click this file to open it and enter in the following information

```
[INDENT]# Start BitTorrent Download Script
05 02 * * * sh /home/Your_User_Name/bash_scripts/bittorrentstart.sh

# Stop ALL BitTorrent Downloads Script
55 11 * * * sh /home/Your_User_Name/bash_scripts/bittorrentstop.sh[/INDENT]
```

Be sure to enter your user-name in the required fields. This setup will start the download start script at 2:05am and start the download stop script at 11:55am.  These values will likely not suit you so you need to alter them.  To understand the format of cron entries picture five asterisks at the start followed by your command.  Something like the following

[INDENT]* * * * * sh /home/Your_User_Name/bash_scripts/bittorrentstart.sh[/INDENT]

The first asterisk represents minutes, the second hours, the third days of the month, the fourth is the month, and the fifth the day of the week.  The allowed syntax is

[INDENT]minute 0-59
hour 0-23
day of month 1-31
month 1-12 (or the month names)
day of week 0-7 (0 or 7 is Sun, or use the weekday names)[/INDENT]

Save this file and start up your terminal emulator

[INDENT]Applications &#8594; Accessories &#8594; Terminal[/INDENT]

Enter in the following command

[INDENT]```
user-name@computer-name:~$ crontab cron.txt[/INDENT]
```

To verify that this was entered into your cron entries properly enter in the following command

[INDENT]```
user-name@computer-name:~$ crontab -l[/INDENT]
```

**5.** Now that we've installed the relevant applications and told the computer to execute the appropriate tasks at the appropriate times all we need to do is save our *.torrent files into the torrent directory we created earlier and wait.  At the appropriate times they will be downloaded into their own sub-directory without you even being aware.

**6.** In the bittorrentstart.sh script we created earlier there is a command to create a log file.  This file records the activity of the torrent downloads.  This file, called 'torrent.log', will be found in the torrent directory.  You can simply open this file to check on the status of your downloads.  A sample line from this log file is

[INDENT]/home/Your_User_Name/torrents/torrent_name: Spd: 34.0  K/s:18.2  K/s Tot: 171.2  M:61.1  M [18:10:07 76%]
All: Spd: 34.0  K/s:18.2  K/s Tot: 171.2  M:61.1  M[/INDENT]

What all of these entries mean is beyond the scope of this tutorial but you can easily recognise your connection speed and the percentage finished of your torrent downloads.

Enjoy your automated torrent downloading!

[COLOR="Red"](edited on November 18 2008)[/COLOR]

---

