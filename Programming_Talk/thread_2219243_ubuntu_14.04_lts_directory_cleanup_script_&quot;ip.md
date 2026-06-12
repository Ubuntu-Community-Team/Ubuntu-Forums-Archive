---
title: "ubuntu 14.04 lts directory cleanup script &quot;ip cam&quot;"
date: 2014-04-23
forum: Programming Talk
---

### Post by shawn14 on 2014-04-23
[SIZE=2]I am used to windows and dos.  now its time i learn a few new things about other operating systems

I am very new to linux unix ubuntu what ever. i am running on an old: inspiron 530s, 991.5 MiB RAM, Intel® Pentium(R) Dual CPU E2160 @ 1.80GHz × 2, Intel® G33 x86/MMX/SSE2, 32-bit OS, disk 77.6 GB. 

I don't know the first thing about ubuntu and how to make a script auto start or what to expect from the native system.

I think I would need a step by step instruction on how to create a script. to maintain a directory. it can only get so full and old files can be deleted to maintain the directory. i am using 2 easyn ip cam's fs series and ftp into this machine stated above. i have it forwarding to the this ftp every second. 

my ftp is pureftp server -- pureadmin v0.4 for gui
i made a directory in my home directory that the ftp puts the files.
/dadscam
in that directory is.
/cam1
/cam2

unless there is a program already out there i think i need a script. 

thank you

i am still searching google. put don't see anything user friendly or step by step. sorry if i annoy you with this thread. i am very new to ubuntu.[/SIZE]
[SIZE=2]
the picture file names go something like this:

00A00107151A(IP\ Camera\ 2)_1_20140422200106_2852.jpg
file size are approximately  50.1kb
I am using approximately 8gb out of 66gb of hard drive  from 6gb in the last 12 hrs

i think it would be wise to think about the size of the hard drive and the hours i can keep. eg. keep 24hr 48hr or 72hr etc.

i think i have more of a ram problem then a hard drive issue. i found this out by trying to access the cam1 directory threw the GUI. wow it stalled or lagged. but it seemed a lot easier access threw the terminal.

thank you for reading this far.[/SIZE]

[SIZE=2]

#!/bin/bash
# ip-cam-ftp-cleanup.sh
#    _______    __    __    ________    _________
#   /  ___  \  |  |  |  |  |   __   |  /
#   \  \  \_/  |  |  |  |  |  |  |  |  |
#    \  \      |  | /   |  |  |  |  |  |
#     \  \     |  |/    |  |  |  |  |  |      snowcatman
#      \  \    |        |  |  |  |  |  |
#       \  \   |    /|  |  |  |  |  |  |
#    _   \  \  |   / |  |  |  |  |  |  |
#   / \__/  /  |  |  |  |  |  |__|  |  |
#   \______/   |__|  |__|  |________|  \_____________
#
# ====================================================================
# modified script

#log this to a the local BASH file directory
# logger -s "foo bar" 2>> ~/bin/ip-cam-ftp-cleanup-log1.txt
# >>$ip-cam-ftp-cleanup-log2.txt 2>&1
#ip-cam-ftp-cleanup.sh >> ~/bin/ip-cam-ftp-cleanup-log3.txt 2>&1

#------------
#write_log()
#{
#  while read text
#  do
#      LOGTIME=`date "+%Y-%m-%d %H:%M:%S"`
#      # If log file is not defined, just echo the output
#      if [ "$LOG_FILE" == "" ]; then
#    echo $LOGTIME": $text";
#      else
#        LOG=$LOG_FILE.`date +%Y%m%d`
#    touch $LOG
#        if [ ! -f $LOG ]; then echo "ERROR!! Cannot create log file $LOG. Exiting."; exit 1; fi
#    echo $LOGTIME": $text" | tee -a $LOG;
#      fi
#  done
#}
#------------

#need to add a indicator for how long the proccess might take.


# Show were trash can is.
TRASHCAN=~/.local/share/Trash/files

# Send to TrashCan
# find ~/dadscam/* -mtime +2 -exec mv {} $TRASHCAN \;
find ~/dadscam/* -mmin +2880 -exec mv {} $TRASHCAN \;

# Send to Death
# find $TRASHCAN* -mtime +3 -exec rm {} \;
find $TRASHCAN* -mmin +4320 -exec rm {} \;

# ====================================================================
#
#                +-+-+-+-+-+-+-+
#                |c|r|e|d|i|t|s|
#                +-+-+-+-+-+-+-+
#    [http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/)

# My name is Shawn Quintal A.K.A. Online SnowCatMan
# [EMAIL="snowcatman@gmail.com"]snowcatman@gmail.com[/EMAIL]
# This is my first script.
# Using native to ubuntu 14.04
# This is a BASH script
# I got the examples from [http://gotbletu.blogspot.com/](http://gotbletu.blogspot.com/) | [http://www.youtube.com/user/gotbletu](http://www.youtube.com/user/gotbletu) timebomb.sh
# 
================================================================================
i am looking to get the -mtime to hours if possible i thought i saw some were with a like 24h or something??? ok found it. still would like a program that can maintain a directory.
idk why the post was moved but ok.

i edited several times...
[/SIZE]

---

### Post by ofnuts on 2014-04-24
[LIST]
[*]"find" takes a list of ***directories*** to search files in so find "[SIZE=2]~/dadscam/*" is trying to work from a list of files and that won't work. You can process all your directories in one call if needed:
[/SIZE]
[/LIST]
[SIZE=2] 
```

find ~/dadscam ~/cam1 ~/cam2 ...

```


[LIST]
[*]To specify a time of last modification you can either use -mtime (in days) or -mmin (in minutes). So to work in hours multiply by 60 and use minutes (-mmin +120 for two hours)
[*]"-cmin"/"-ctime" can also be used for this (slightly different semantics)
[*]I don't see much purpose in staging files in a trash directory since it won't recover disk space, and even less purpose in selecting stuff to erase in it. Trashcan directories are for humans, not for script. But if you insist in using a trashcan, at least do something like:
[/LIST]
```

#empty trashcan
rm $trashcan/*
#move live files to trashcan
[SIZE=2]find ~/dadscam -mmin +2880 -exec mv {} $TRASHCAN \;
[/SIZE]
```
[LIST]
[*]Note that in the "find" above "mv" is called once for each file. You can use a different syntax to move all files in one "mv" invokation:
[/LIST]
```

[SIZE=2][SIZE=2]find ~/dadscam -mmin +2880 -exec mv -t $TRASHCAN {} \+

```[/SIZE][/SIZE]
[INDENT][/INDENT]
[INDENT](in the find command "-exec *command* {} \;" executes *command* once for each file, while [SIZE=2]"-exec *command* {} \+" build a single command line with all the files as parameters. In some version of Linux you can hit the command[/SIZE] line length limit that way).
[/INDENT]

Otherwise yes, the GUI is a major user of RAM in modern systems. You can run a command-line Linux in 256M but the GUI needs a lot more.
[/SIZE]

---

### Post by shawn14 on 2014-04-24
Thank you for your very informative reply. 

sorry for the long read~

I don't have to have the use of the trash can, matter of fact you made a good, pointing out that redundancy.

i guess from were i got the script they were setting them selves up for a second place to look for encase they might actually want a file recovered. 
but in my case i am just trying to keep a drive from over filling. with pictures from a came so far i have used 10gb out of 60gb hard drive. 

i am supost to be doing this for a mounth or so. and i can only see holding on to just anough days for me to go back and for a look see. watching the house sitter and watching out for a good picture of a would be thief.
so.... hows this??
[SIZE=2]
**find ~/dadscam **[/SIZE]**~/cam1 ~/cam2[SIZE=2] -mmin +6000 -exec rm [/SIZE]**[SIZE=2]**{} \+**

would that work? afraid to try it and loose the last 3 days [/SIZE]of savings of my ipcam jpg's on this ftp.

also is there a way for a on again off again to call this script. I am using "**startup applications**" in the search feature of ubuntu.

**1. gksudo pureadmin**
**2. ip-cam-ftp-cleanup-auto-on.sh**
in number 2. is this script:
========================
[B]#!/bin/sh
while [ true ]
do
    sh ip-cam-ftp-cleanup.sh
    sleep 60
done[/B]
========================

 would not like to take up more resources than i already have been using. plus i can't tell what is going on. 
i don't know how to log a success or fail in a .sh bash file. not that i have not tried. you you can tell by looking at my first post.

i have this ftp on a 2hr battery backup. but am setting my self up for a failure anyway. so when the power comes back on this old pc just turns on.
in and so. i want to have it to were the ftp server is running and accepting files and the script is trimming out files as needed.
 to keep from filling up the drive and in turn finding out how many hours/days of jpg 50.1kb photo's i get to keep on hand.

again thank you  				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1382218_5.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1382218") 				 				 					 						 	[**[COLOR=#000000]ofnuts[/COLOR]**]("http://ubuntuforums.org/member.php?u=1382218")

---

### Post by ofnuts on 2014-04-25
"find ~/dadscam ~/cam1 ~/cam2 -mmin +6000 -exec rm {} \+" byt 6000 minutes is 100 hours or a bit over 4 days, maybe you want something shorter. You can test it by just adding an "echo" to make it display the command instead of executing it:

```

find ~/dadscam ~/cam1 ~/cam2 -mmin +6000 -exec echo rm {} \+

```

To run a command periodically you should use "cron"; See [http://www.debian-administration.org/articles/56](http://www.debian-administration.org/articles/56)

Periodicity should be related to the time span covered. If you remove files that are several days old, you can run the job once per day ("sleep 60" sleeps one minute....) 

To log  to file you just redirect the output of the echo or printf commands to file. I fyou want something with better looks I use this in my own scripts:

```

log='/var/tmp/connection-controller.log'  # /var/tmp for my "user" logs, stuff running for the system can log to /var/log

function log {
        echo $(date '+%F %H:%M:%S') $$: $@ >> $log
}

# when need in the code:
log "Gateway IP address=$gatewayIP"

```

produces:

```

2014-04-14 21:04:56 2056: Gateway IP address=192.168.0.254

```

---

