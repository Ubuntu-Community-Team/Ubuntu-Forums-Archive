---
title: "Bash scripting question"
date: 2008-06-27
forum: Programming Talk
---

### Post by danhm on 2008-06-27
Hey, I'm trying to write a bash script to automate the creation of IRC stats using [pisg](http://pisg.sourceforge.net/) as the stats script. I want there to be two stat pages -- the last 24 hours and an all-time stats page. I've got the 24 hour stats page down just fine.
```

#!/bin/bash

ftp="/usr/bin/ncftpput -u user -p password server /public/logbook/"
DIR="/home/dan/.xchat2/xchatlogs/Gamesurge"
PISG="/home/dan/.xchat2/pisg-0.72/pisg"
iFILE="#channel.log"
oFILE="stats.html"

DATE=$(/bin/date +%F)
cd $DIR
$PISG -l $DATE/$iFILE -o $oFILE
$ftp $oFILE
exit 0

```

What I would like to do is to also have this script create an all-time file. Pisg can take many -l arguments (-l today.log -l yesterday.log -l two_days_ago.log etc) so I figured I could just have something that cycles through the dated directories until it reaches the beginning, but I don't know how to do that in bash or if it is possible. Can someone help?

---

### Post by geirha on 2008-06-27
Requiring -l in front of each input-file is a bit non-unix-friendly, so it requires some extra scripting. I believe this should do the trick. The echo I've marked in red will make it just print the command, not execute it. Remove the red echo if the command looks correct, and it will be executed.
```

cd "$DIR"
for file in */$iFILE; do echo -en "-l\0$file\0"; done | xargs -0 [color=red]echo[/color] $PISG -o $oFILE

```

---

### Post by danhm on 2008-06-27
Ok, I changed my script to:

```

#!/bin/bash

ftp="/usr/bin/ncftpput -u user -p password server /public/logbook/"
DIR="/home/dan/.xchat2/xchatlogs/Gamesurge"
PISG="/home/dan/.xchat2/pisg-0.72/pisg"
iFILE="#channel.log"
oFILE="stats.html"
oFILE_all="stats_all.html"

DATE=$(/bin/date +%F)
cd $DIR
$PISG -s -o $oFILE -l $DATE/$iFILE
for file in */$iFILE; do echo -en "-l $file\0"; done | xargs -0 $PISG -o $oFILE_all -s
$ftp $oFILE $oFILE_all
echo "done!"
exit 0

```

If I keep that second echo in there, it outputs:
```

dan@linux-0sua:~> ./stats.sh
/home/dan/.xchat2/pisg/pisg -o stats_all.html -s -l 2008-06-26/#channel.log -l 2008-06-27/#channel.log
```

That works fine if I copy and paste it (afer CDing to $DIR, of course).

However, as soon remove the second echo, it doesn't work.
```

dan@linux-0sua:~> ./stats.sh
Unknown option: l 2008-06-26/#channel.log
Unknown option: l 2008-06-27/#channel.log
Usage: pisg [-ch channel] [-l logfile] [-o outputfile] [-ma maintainer]
[-f format] [-ne network] [-d logdir] [-mo moduledir] [-s] [-v] [-h]

-ch --channel=xxx      : Set channel name
-cc --cchannels=xxx    : Only do this channel from cfg file, give multiple
                         times to do multiple channels
-l  --logfile=xxx      : Log file to parse, give multiple times to use
                         multiple log files.
-o  --outfile=xxx      : Name of HTML file to create
-t  --tag=xxx          : Replace %t in --outfile by xxx
-ma --maintainer=xxx   : Channel/statistics maintainer
-f  --format=xxx       : Logfile format [see FORMATS file]
-ne --network=xxx      : IRC network for the channel
-d  --dir=xxx          : Analyze all files in this dir. Ignores logfile.
                         Give multiple times to use multiple directories.
-nf --nfiles=xxx       : Analyze the last xxx files if used with --dir
-p  --prefix=xxx       : Analyze only files prefixed by xxx in dir
                         Only works with --dir
-cf --cfg opt=value    : Specify configuration options, eg. -cf ShowWpl=1
-co --configfile=xxx   : Configuration file
-mo --moduledir=xxx    : Directory containing pisg modules
-s  --silent           : Suppress output (except error messages)
-v  --version          : Show version
-h  --help             : Output this message and exit.

Example:

 $ pisg -ne IRCnet -f xchat -o suid.html -ch \#channel -l logfile.log

All options may also be defined by editing the configuration file and
calling pisg without arguments.
xargs: /home/dan/.xchat2/pisg/pisg: exited with status 255; aborting
done!

```

The dashes seem to disappear, I think?

I changed **do echo -en "-l_\0_$file\0"** to **do echo -en "-l $file\0"** because that first \0 was producing funky characters.

---

### Post by geirha on 2008-06-27
> **danhm said:**
> 
I changed **do echo -en "-l_\0_$file\0"** to **do echo -en "-l $file\0"** because that first \0 was producing funky characters.

What funky characters? Anyway, removing that \0 explains the errors you got...

You can probably do without using \0 as delimiters though. As long as your files and directories does not contain whitespace, this should work:

```
for file in */$iFILE; do echo "-l $file"; done | xargs $PISG -o $oFILE_all -s
```

---

### Post by danhm on 2008-06-27
Thanks a lot!

---

