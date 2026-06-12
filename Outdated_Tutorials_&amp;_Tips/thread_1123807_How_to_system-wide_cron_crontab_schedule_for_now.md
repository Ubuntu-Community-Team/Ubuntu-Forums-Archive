---
title: "How to system-wide cron crontab schedule for now"
date: 2009-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by directcharitycontribution on 2009-04-12
Most important anything is to set correct for you 'environment variables' -- so edit system crontab to read this below as follows;

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

# SHELL=/bin/sh
# PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

SHELL=/bin/bash
# PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/username/bin
# MAILTO=username
# HOME=/home/username
DISPLAY=:0.0
#EDITOR=editoruchose

(basically u have add line 'DISPLAY=:0.0')

[http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)
[http://ubuntuforums.org/tags.php?tag=crontab](http://ubuntuforums.org/tags.php?tag=crontab) better read marked as [SOLVED]!

===========================

============================

============================

like [[COLOR="Pink"]cask-schedulers calendar[/COLOR]]("http://www.google.com/search?hl=en&q=+gcalcron+evolution+outlook") for people of micro-$orts this work for some useful rubbish rubbish rubbish computers box.

it is the crontab for system (CRON TABLE is simpled table schedule formats) working via "sudo gedit /etc/crontab" While editing this is going on, quite absorbing,  optional convenience   may find you put "sudo gedit /etc/crontab" launcher some place and duing regular editing setting up temporarily set nopasswd for "sudo gedit /etc/crontab" in sudoers file. (nopasswd may also be necessary to some commands you want with crontab).

so the first thing i did wanted to set up switched media-streaming. while partially working with streams can optimise OTHER lifes, housework, baths, snoozing or other non-puter multi-tasking , and time-shifting playbacks and off-peak contentions and rates. as most broadcasts end hourly i set some stop (killall/pkill) on periodically, good also if fails, and restarts after like news/intros. don't wanna listen such over again and sometimes just want summies not more if they doesn't really anything.

( you should want create userdumbs, not with any permissions or content and instant screenlocks, that can runs mode ummonitored or autoboots from alarm without any security compromise.)
(you for such convenience CAN instead to REDESIGN crontab just duplicate schedules lines for any attended usersname (other than root) modes, everybody mode (like player) unattended usersname can same then you remove some! but less IS more!!)

these may not be chics solution, but start works now is easy copy-paste develop when any other crontabs/scripts process comes along makes more ideals
putting # begin line disables *ANY* cron entry line action MINNIE:DMOUSE or description. very useful eg. leave commands setup for various contingencies, oneoffs, short-notice varying schedules decisions or testing is description. (Make some copy for such different periods)

[COLOR="Blue"]and it looks this. (YOU KEEP YOUR EXISTING ROOT COMMANDS AND REPLACE OTHER COMMANDS WITH YOUR CHOICES AND USERSNAME[/COLOR])

-------------------------------------------------------------------------------------
[COLOR="Blue"]system-wide crontab is as BETWEEN lines below[/COLOR]
-------------------------------------------------------------------------------------
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

# SHELL=/bin/sh
# PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

SHELL=/bin/bash
# PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/username/bin
# MAILTO=username
# HOME=/home/username
DISPLAY=:0.0
#EDITOR=gedit

# m h dom mon dow user command
17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
# D A I L I E S
* * * * * username exec command/scriptaddress
1 0 * * * username exec /usr/bin/abc123player --volume 250 stream/file-url
2 19,20,22 * * 1-5 username exec /usr/bin/abc123player --volume 15 --zoom 0.5 stream/file-url
12 19 * * 1-5 username exec killall abc123player
31 0,19 * * 1-5 username exec /usr/bin/abc123player --volume 15 --zoom 0.5 stream/file-url
13 19 * * 1-5 username exec /usr/bin/abc123player --volume 150 stream/file-url
50 19 * * 1,2,4,5 username exec /usr/bin/abc123player --volume 150 stream/file-url
50 19 * * 1,2,4,5 username exec /usr/bin/vlc --zoom 0.5 --video-x=1000 --video-y=507 stream/file-url
2 20 * * 1 username exec mplayer -dumpstream stream-url -dumpfile your_dumped_stream.mp4
2 19 * * 1 username exec mplayer -dumpstream -dumpfile "yourfile" -playlist "URL"
# S Y S T E M
3 3 * * * root exec /sbin/shutdown -P now
@hourly festival '(SayText "tea, no milk, sugar")'
@hourly padsp espeak "Hey there computeer. Eliminate idiots."
@hourly festival '(SayText "Hey there computeer. Eliminate even worse idiots.")' 
@hourly username festival '(SayText "Hey there. Give it a break!")'
# event.sh ; notify-send "message"
# xmessage -file /path/of/file/name/message.txt
#* * * *	root	UNCOMMENT LINE BEGINNING TO SUSPEND CRONTAB 
#* * * *	anyuser	UNCOMMENT LINE BEGINNING TO SUSPEND CRONTAB 
0 9-23,0-3 * * * username exec killall abc123player STREAMURL/alternative
15 9-23,0-3 * * * username exec killall abc123player STREAMURL/alternative
30 9-23,0-3 * * * username exec killall abc123player STREAMURL/alternative
45 9-23,0-3 * * * username exec killall abc123player STREAMURL/alternative
# O C C A S I O N A L
#3 6 18 4 * username exec /usr/bin/abc123player --volume 300 --novideo stream/file-url
#15 14 * * 6 username exec /usr/bin/abc123player --volume 300 stream/file-url
# P R O J E C T
# * * * * * username scriptForDay
#*/15 * * * * /sbin/ifconfig | mail [email]myname@mydomain.com[/email]
#15 0* * * /usr/local/scripts/run_webstats.script
# E X P E R I M E N T A L
@reboot exec amixer -c 0 cset numid=2 70%
@reboot exec amixer -c 0 sset PCM,0 75%,0%
30 19 * * * amixer -c 0 set PCM 2dB+
 * * * * * username exec data && process
# * * * * * username exec download && play
# * * * * * username exec download && save 
# * * * * * username exec download && save && play
# * * * * * username exec instruction x && sleep X/Xm/Xh && instruction y
#(processes only if preceding complete)
#* * * * * username exec instruction x, sleep X/Xm/Xh, instruction y
#(process all regardless)
#* * * * * username exec script
# SPECIFIC CRONTABS CAN BE USED FOR WEEK, MONTH, SEASON, WEATHER, LOCATION etc. YOU USE cp COMMANDS NECESSARY FOR INSTALLATION

#
-------------------------------------------------------------------------------------
[COLOR="Blue"]system-wide crontab is as BETWEEN lines above[/COLOR]
-------------------------------------------------------------------------------------


------------------------------------------------------------------------
_**TROUBLESHOUTING:**_

          Activity is indicated in /usr/var/syslog. To view go ***[COLOR="Pink"]Terminal > grep CRON /var/log/syslog[/COLOR]*** or ***[COLOR="Pink"]System > Administration > Log File Viewer[/COLOR]***

          ***Simple Method*** comment (put # at beginning) one active line and resave at a time until error messaging dissapears. that last commented line is then error line.

          **bad minute/hour/username** -- For message like "Error: bad minute; while reading /etc/crontab" open editor window at max one entry per line to check wrongs lines spacing, number numbers etc. syntax.

- Put **> /tmp/script.log** at the end of the cron entry for this script and debug it.
- Put **2> /tmp/error-script.log** at the end of the cron entry for this script to see whether it writes any error message to the log file.

_*RE: GNOME-SCHEDULE*_
syslog output shows 2nd which doesn't work was programmed thru gnome-scheduler 3rd does work thru basic system crontab
date time (none) /USR/SBIN/CRON[7737]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
date time (none) /USR/SBIN/CRON[7738]: (username) CMD (/usr/bin/vlc URL >/dev/null 2>&1 #JOB_ID_14)
date time (none) /USR/SBIN/CRON[7738]: (username) CMD (   /usr/bin/vlc URL )

[COLOR="Pink"]env | grep DISPLAY[/COLOR]

[COLOR="Pink"]grep CRON /var/log/syslog[/COLOR]

------------------------------------------------------------------------
_**NOTES:**_

          /usr/bin/totem switches consecutive media files from command line without stop required.

          /usr/bin/rhythmbox switches consecutive audia files from command line without stop required.

          /usr/bin/vlc can play concurrent or consecutive media files from command line, tho not Really Media choppy audio and NOT any video, and for good playlist. (Can play betters, video file audio, if called with added arguments by command line, eg 'exec /usr/bin/vlc --zoom 0.5 --video-x=1000 --video-y=507 stream/file-url', then no skipping audio?!)
         


          /usr/bin/mplayer variants use very no cpu can play all media files concurrent and consecutive from command line (, but some control is bad erratic, playlist not for good, and player's volume is not big).   [http://forums.debian.net/viewtopic.php?f=16&t=17783](http://forums.debian.net/viewtopic.php?f=16&t=17783)

          [http://manpages.ubuntu.com/manpages/intrepid/man1/fapg.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/fapg.1.html) multi-format playlist generator

------------------------------------------------------------------------
_**COMMANDS:**_

          [[COLOR="Pink"]http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html?S_TACT=105AGX03&S_CMP=ART[/COLOR]]("http://http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html?S_TACT=105AGX03&S_CMP=ART")
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

          [http://team.macnn.com/drafts/crontab_defs.html](http://team.macnn.com/drafts/crontab_defs.html)

          [http://users.bigpond.net.au/hermanzone/p8.html](http://users.bigpond.net.au/hermanzone/p8.html)

          [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) for script development

          [http://www.commandlinefu.com/commands/matching/vlc/dmxj/sort-by-votes](http://www.commandlinefu.com/commands/matching/vlc/dmxj/sort-by-votes)

[COLOR="Pink"]env | grep DISPLAY[/COLOR]

------------------------------------------------------------------------

backgroun info see post here 

          [http://ubuntuforums.org/showthread.php?t=943621](http://ubuntuforums.org/showthread.php?t=943621)  

          [http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

          my projects page [http://ubuntuforums.org/member.php?u=211533](http://ubuntuforums.org/member.php?u=211533)

------------------------------------------------------------------------
Readings:
[http://ubuntuforums.org/showthread.php?t=1155961&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=1155961&highlight=mplayer)

[http://search.techrepublic.com.com/search/crontab.html](http://search.techrepublic.com.com/search/crontab.html)


[URL="http://ubuntuforums.org/tags.php?tag=crontab"][COLOR="Pink"]http://ubuntuforums.org/tags.php?tag=crontab[/COLOR]
[/URL]
[[COLOR="Pink"]http://ubuntuforums.org/tags.php?tag=schedule[/COLOR]]("http://ubuntuforums.org/tags.php?tag=schedule")

[lifehacker.com incron - feature]("http://lifehacker.com/5041897/incron-creates-automated-jobs-from-file-actions")
[linux.com CLI Magic: Bring in podcasts with BashPodder]("http://www.linux.com/archive/feature/114219")
------------------------------------------------------------------------

this how to may be lock vesion, so if evolutioning vesion is [http://ubuntuforums.org/showthread.php?t=1121767](http://ubuntuforums.org/showthread.php?t=1121767)

---

### Post by directcharitycontribution on 2009-05-25
following unformation of [http://ubuntuforums.org/showthread.php?t=1169478#taglist](http://ubuntuforums.org/showthread.php?t=1169478#taglist) I have now had some task work through also crontab user and can write user for howto.

FOR PROGRAMMES WITH GRAPH INTERFACE YOU TYP, DISPLAY=:0 or env DISPLAY=:0.0 BEFORE THE COMMANDS USE IN CRONTAB OR 

Code:

#!/bin/sh
export DISPLAY=:0
my command

FOR A CALLED SCRIPT.

---

