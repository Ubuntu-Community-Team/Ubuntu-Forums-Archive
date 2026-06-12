---
title: "HOWTO: get Podcasts without Ipodder"
date: 2005-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by mtron on 2005-06-11
[Podcasts](http://en.wikipedia.org/wiki/Podcasting)  are a nice way to get periodical mp3 downloads via RSS. ( Check out [Lugradio](http://www.lugradio.org/) , great show! )
I had some problems setting up [Ipodder](http://ipodder.sourceforge.net/index.php)  (and it seems that i'm not alone) but here is an easy & working alternative [Bashpodder](http://linc.homeunix.org:8080/scripts/bashpodder/ ) . The program consists of 3 scripts, one conf file and has even a gui

Requires:
wget (comes with every standard install)
bash (comes with every standard install)
sed (comes with every standard install)
xmms (or every other mp3 player)
xdialog 


open terminal & type

```
sudo apt-get install xdialog
```

now type:

```
mkdir bashpodder
cd bashpodder
```

dowload bashpodder files:

```
wget http://linc.homeunix.org:8080/scripts/bashpodder/user_contributed/brian_hefferan/bashpodder.shell
wget http://linc.homeunix.org:8080/scripts/bashpodder/bp.conf
wget http://linc.homeunix.org:8080/scripts/bashpodder/gui/bpgui.sh
wget http://linc.homeunix.org:8080/scripts/bashpodder/gui/convert.sh
```

now make the scripts executeable
```
chmod -R 744 bashpodder.shell
chmod -R 744 bpgui.sh
chmod -R 744 convert.sh
```

after that, open the configuration file
```
gedit bp.conf
```

just copy in here the links to the rss podcast feeds, or delete the example feeds you are not interrested in. Then close gedit.

run the script
```
./bpgui.sh
```

Usage: 
First thing to do is mark "Re-Import Podcast List", click ok and wait a bit, then "Launch BashPodder dowload client" and the script will use wget to download the mp3s, when it's done you can launch the podcasts with xmms with the menu entry "View/Launch downloaded podcasts", if you have another player just replace xmms in the script bpgui.sh in line 24 & 36 with you favourite media player. 


Readme & Pics: [here](http://linc.homeunix.org:8080/scripts/bashpodder/gui/docs.html ) 
Author: [Linc](http://linc.homeunix.org:8080/scripts/bashpodder/ )

---

### Post by az on 2005-06-11
If they released a six-hour DVD of lugradio-live!  I would buy it and watch it in one sitting.


Mark Shuttleworth will be there and take part in the mass-debate!

---

### Post by word_virus on 2005-06-12
Hey, yeah!  I've been using this for a couple of months... it's a nice fuss-free way to get podcasts.  Never knew there was a gui.  I've just been using the shell script and setting it up to run as a weekly cron job.

---

### Post by MikePB on 2005-06-15
Wow, great. I couldn;t get this installed before... thanks!

---

### Post by Jarz Corp on 2005-06-15
Maybee it would be a good idea to add lynx to the "needed before start" list, I know linux is about keeping user occupied for the missing bit but lets see if we can't cut down on that just a tad.

Sorry about  the negativity but I am on a 64bit system.

---

### Post by Jarz Corp on 2005-06-15
And just for the record. This totally solved my problem and BETA ipodder as it should be called on linux, is wiped from my system. Next step is to check out some of the really nice alternative bp.conf files out there.

---

### Post by Technoviking on 2005-06-15
I use one of the contrib bashpodder shells, this one can handle bittorrent, has first only (download only the last podcast on a rss feed), and catch up.

bashpodder.shell
```

#!/bin/bash
# By Linc 10/1/2004
# Find the latest script at http://linc.homeunix.org:8080/scripts/bashpodder
# If you use this and have made improvements or have comments
# drop me an email at linc dot fessenden at gmail dot com
# I'd appreciate it!
#
# This revision by Brian Hefferan 2004/02/06, adding configuration options.
# No warranty. It seems to work for me, I hope it works for you.
# Questions /corrections on the additions by Brian Hefferan can be sent to
# brian at heftone  dot  com

#default values can be set here. Command-line flags override theses.
verbose=
wget_quiet='-q'  #default is -q
wget_continue=
catchup_all=
first_only=
unix2dos=
usetorrents=
sync_disks=
fetchlist='bp.conf'

function usage
{
  echo "
Usage: $0 [OPTIONS]
Options are:
-v, --verbose          display verbose messages. Also enables wget's continue
                      option.
--catchup_all          write all urls to the log file without downloading the
                      actual podcasts. This is useful if you want to subscribe
                      to some podcasts but don't want to download all the back
                      issues. You can edit the podcast.log file afterwards to
                      delete any url you still wish to download next time
                      bashpodder is run.
--first_only           grab only the first new enclosed file found in each feed.
                      The --catchup_all flag won't work with this option. If
                      you want to download the first file and also permanently
                      ignore the other files, run bashpodder with this option,
                      and then run it again with --catchup_all.
-bt --bittorrent       launch bittorrent for any .torrent files downloaded.
                      Bittorrent must be installed for this to work. The
                      the script and bittorrent process will continue running
                      in the foreground indefinitely. You can use ctr-c to
                      kill it when you want to stop participating in the
                      torrent.
--sync_disks           run the "sync" command twice when finished. This helps
                      makes sure all data is written to disk. Recommended if
                      data is being written directly to a portable player or
                      other removable media.
-u, --url_list         ignore bp.conf, instead use url(s) provided on the
                      command line. The urls should point to rss feeds.
                      If used, this needs to be the last option on the
                      command line. This can be used to quickly download just
                      a favorite podcast, or to take a few new podcasts for a
                      trial spin.
-h, --help             display this help message

"
}

if [ -n "$verbose" ]; then wget_quiet='';wget_continue='-c';fi
if test -f urls.temp;then rm urls.temp;fi

# Make script crontab friendly:
cd $(dirname $0)

while [ "$1" != "" ];do
   case $1 in
             -v|--verbose ) verbose=1
                            wget_continue='-c'
                            wget_quiet=''
                         ;;
            -u|--url_list ) shift
                            while [ "$1" != "" ];do
                               echo "$1" >> urls.temp
                               shift
                            done
                            if test ! -f urls.temp
                               then
                                   echo "Error: -u or --url_list option specified, but no urls given on command line. quitting."
                                   exit 1;
                            fi
                            fetchlist='urls.temp'
                         ;;
            --catchup_all ) catchup_all=1
                         ;;
             --first_only ) first_only=1
                         ;;
             --bittorrent ) usetorrents=1
                         ;;
             --sync_disks ) sync_disks=1
                         ;;
                -h|--help ) usage
                            exit
                         ;;
   esac
   shift
done

# datadir is the directory you want podcasts saved to:
datadir=$(date +%Y-%m-%d)

# Check for and create datadir if necessary:
if test ! -d $datadir
      then
      mkdir $datadir
fi

if test ! -f bp.conf && test ! -f urls.temp;
then
   echo "Sorry no bp.conf found, and no urls in command line. Run $0 -h for usage."
   exit
fi

# Read the bp.conf file and wget any url not already in the podcast.log file:
while read podcast
      do
      seenfirst=
      if [ -n "$verbose" ]; then echo "fetching rss $podcast...";fi;
      for url in $(wget -q "$podcast" -O - | tr '\r' '\n' | tr \' \" | \
                   sed -n 's/.*url *= *"\([^"]*\)".*/\1/p' )
              do
          if [ -n "$first_only" ] && [ -n "$seenfirst" ]; then break;fi
          echo $url >> temp.log
          if [ -n "$catchup_all" ];
          then
              if [ -n "$verbose" ]; then echo " catching up $url...";fi
          elif   ! grep "$url" podcast.log > /dev/null ;
          then
             if [ -n "$verbose" ]; then echo "  downloading $url...";fi
             wget $wget_continue $wget_quiet -P $datadir "$url"
          fi
          seenfirst=1
      done
done < $fetchlist

if test ! -f temp.log && [ -n "$verbose" ];then echo "nothing to download.";fi

if test -f urls.temp; then rm urls.temp;fi

# Move dynamically created log file to permanent log file:
cat podcast.log >> temp.log
sort temp.log | uniq > podcast.log
rm temp.log

# Use bittorrent to download any files pointed from bittorrent files:
if [ "$usetorrents" ]
then
    if ls $datadir/*.torrent 2> /dev/null
    then
          btlaunchmany.py $datadir
    fi
fi

# Create an m3u playlist:
ls -1rc $datadir | grep -v m3u > $datadir/podcast${datadir}.m3u
if [ -n "$unix2dos" ];then unix2dos $datadir/podcast${datadir}.m3u;fi;

if [ -n "$sync_disks" ]
then
    if [ -n "$verbose" ]; then echo "running sync..";fi;
    sync
    if [ -n "$verbose" ]; then echo "running sync again..";fi;
    sync
fi

if [ -n "$verbose" ]; then echo "done.";fi;

```

---

### Post by Jarz Corp on 2005-06-16
Hey thanks man, it was something along those lines I was looking for, as SDR does use BT.

---

### Post by danimal87 on 2005-06-21
I keep getting an error: "grep: podcast.log: No such file or directory"
do i just creat a file called podcast.log? 
"vim podcast.log"

---

### Post by Jarz Corp on 2005-06-21
Well so did I, just create an empty file by that name and run again, I ran into the same problem with the new_mp3 file.

I have used one of the customized scripts from the bashpodder page for days now and it really works well.

---

### Post by danimal87 on 2005-06-21
Thanks, the error went :-)

---

### Post by Jarz Corp on 2005-06-21
No problem, I know it is a "stupid" way to solve it. But I am all for trying to make linux a simple system to use, quite a bit of way before we get there, and this works so what the heck, why spend hours trying to figure out where in the scripts, what goes wrong.

---

### Post by mtron on 2005-07-03
[QUOTE=Mike Basinger]I use one of the contrib bashpodder shells, this one can handle bittorrent, has first only (download only the last podcast on a rss feed), and catch up.[/QUOTE]

Thanks Mike! 

I totally forgot about this thread, but i edited it now.

Lugradio is now also as OGGCast available! The feed:
http://www.lugradio.org/episodes.ogg.rss

---

### Post by Brokenrgv on 2006-01-08
awesome thnx for the how to, one question though how do you make it download 1 ep instead of the lot

---

### Post by passonno on 2006-06-05
So I followed the instructions to the letter, and all I can get is the gui, and no matter what I click in the gui it quickly restarts without doing anything, even to the point of only being able to be stopped by ctrl-c in a terminal.

Any ideas?

---

### Post by dkitty on 2006-06-05
I don't bother with the gui at all. It's easy to just add a feed address in bp.conf. Instructions in bashpodder.shell are pretty well explained. I threw bashpodder.shell on a cron job and also put a shortcut (to run verbose, in a terminal, so I can check progress if I wish) in my Gnome menu under Internet. Everything works like a charm.

Don't fear the terminal. Really.

---

### Post by Zerocool10482 on 2006-06-05
I just use PenguinTV. It's really cool and It's not something you have to use the termial.

---

### Post by dkitty on 2006-06-05
Wait. Doesn't the latest Amarok and... er... the music player in Gnome Ubuntu that looks like iTunes. I'm drawing a blank on the name. Don't they both have podcast support? That should be hella easy.

---

### Post by Zerocool10482 on 2006-06-06
Rhythmbox. It's ok but it doesn't do video. PenguinTV plays in Totem, XMMS and VLC. Amarok is ok but I like to watch DL.TV, Diggnation, Cranky Geeks and Commandn.

Amarok will download it but it won't play it. Then you have to find the file and then open it.

But for audio Amarok goes a better job than Rhythmbox. But I just don't like the GUI on Amarok. I've gotten confused by it.

---

### Post by dkitty on 2006-06-06
Right, Rhythmbox. Thanks.

I agree about Amarok's GUI. I think I've installed every stable release hoping it will get better, then removed it a day or two later. It doesn't slow down my system like Rhythmbox though.

I think I'll look at PenguinTV. Thank you for the recommendation.

---

### Post by Zerocool10482 on 2006-06-09
When you install PenguinTV. Remember to put down the center bar. It look like it didn't work but you have to pull down this center little bar to show everything.

Email me if you have any problems.

---

### Post by Sarisar on 2006-07-04
OK so I went a little overboard... but I wanted to learn scripts / shell and so kinda rewrote the bashpodder one... well most of it.  I picked up a few other bits from some other enhancements and added some bits from a few websites.

So it seems to work ... pretty much although a few podcasts pick up the wrong files (Daily Sonic for example but got that from the bashpodder original list)

It has some more functionality, including a debug option if you're having problems and a catchup to simply update the file and not download the podcasts.  I've also renamed a few files and it should handle ctrl-c better (tidies up after itself).

Can someone let me know if this is OK or if I should read more shell scripts?

Thanks :)

```

#!/bin/bash

# By Iain 2006-07-04

# This is mine written almost from scratch but original idea
# Stolen^H^H^H^H^H^H Based upon bashpodder.shell
# By Linc 10/1/2004
# Find the latest script at http://linc.homeunix.org:8080/scripts/bashpodder
# Last revision 07/01/2005 - Many Contributers!
# If you use this and have made improvements or have comments
# drop me an email at linc dot fessenden at gmail dot com
# I'd appreciate it!
# Changes by Chess Griffin 12/09/2005

# Also used commands and function
# Based on http://linuxcommand.org/writing_shell_scripts.php
# Quite heavily (clean_up and command line handling from there for example)
# Hopefully my version is better, but if not I learnt how to do scripts
# (yes this is my first script, at least on linux!)


###########
#
#   To Do
#
###########
#
#   Download only MP3s
#   http://www.thelinuxlink.net/images/techshow-slackware1.png
#   Sort Daily Sonic out
#   Have note of what day it ran, so check each podcast once per day?
#   
#   
#
###########


# Make script crontab friendly:
cd $(dirname $0)


###########
#
#   Constants
#
###########

LASTUPDATE="2006-JUL-03"
TEMPDIR="1-Incoming"
PROGNAME=$(basename $0)
PODCASTLIST="podcastlist.txt"
DOWNLOADEDLIST='downloads.log'
DOWNLOADEDTEMP='temp.log'


###########
#
#   Variables Defaults
#
###########

DATADIR=$TEMPDIR
DEBUG=0
VERBOSE=0
CATCHUP=0
PODCASTURL=""
PODCASTDIR=$TEMPDIR
PODCASTFILES=""
PODCASTFILEURL=""
ACTUALURL=""
TEMPURL=""
FILENAME=""


# If run with -h or unknkown option, this function is run
function FUNC_USAGE {

	# Display usage message on standard error
	echo ""
	echo "Bash Podder, a script to download podcasts"
	echo "Original idea by Linc (http://linc.homeunix.org:8080/scripts/bashpodder)"
	echo "Updates done by Chess Griffin 12/09/2005"
	echo "Rewritten and (hopefully) improved Iain Leggate $LASTUPDATE"
	echo ""
	echo "Usage:"
	echo "     -h, --help               Shows this help file (duh)"
	echo "     -d, --debug              Debug mode shows everything that is going on.  Huge amounts of text"
	echo "     -v, --verbose            Runs WGET without quiet mode for more information."
	echo "     -c, --catchup            Marks all podcasts as 'read' only.  Ignores current list"
	echo ""
	echo "Note:  -d and -v do different things, -d will not show details on wget, only -v does that."
	echo "You can run both options if you want debug and a non-quiet wget."
	echo "Running catchup is useful if you have removed podcasts from your lists or added new ones in"
	echo "as you can tidy up your podcast list without downloading everything"
	echo ""

}


# This should be run when ctrl-c is pressed OR on successful completion
function FUNC_CLEAN_UP {
	# Perform program exit housekeeping
	# Optionally accepts an exit status
	echo ""
	echo "Running housekeeping..."
	echo "This shouldn't take very long at all!"

	# Look for the temp file and copy and sort if we find it
	if [ -e "$DOWNLOADEDTEMP" ]; then
		# Don't do anything as we need this file!
		echo "Amalgamate $DOWNLOADEDLIST and $DOWNLOADEDTEMP"
		cat $DOWNLOADEDLIST >> $DOWNLOADEDTEMP
		echo "Sort the combined file removing dupes"
		sort $DOWNLOADEDTEMP | uniq > $DOWNLOADEDLIST
		echo "Remove temporary log file"
		rm $DOWNLOADEDTEMP
	fi	

	echo "Done"
	exit $1
}


# Try to handle errors in a nice way
function FUNC_ERROR_EXIT {
	# Display error message and exit
	echo "${PROGNAME}: ${1:-"Unknown Error"}" 1>&2
	FUNC_CLEAN_UP 1
}


# Trap the main close commands
trap FUNC_CLEAN_UP SIGHUP SIGINT SIGTERM

clear

# First up, lets see what the user passed us in the command line
while [ "$1" != "" ]; do
	case $1 in
		-h | --help )		FUNC_USAGE
						exit
						;;
		-d | --debug )		DEBUG=1
						;;
		-v | --verbose )	VERBOSE=1
						;;
		-c | --catchup )	CATCHUP=1
						;;
		* )				FUNC_USAGE
						exit 1
	esac
	shift
done


# Check for root and don't allow it to run!
if [ "$(id -u)" = "0" ]; then
	echo "What the hell are you running this as root for?  Go away!"
	exit
fi


# If debug let people know what the CLPs where
if [ "$DEBUG" = "1" ]; then

	echo "-d selected"

	if [ "$VERBOSE" = "1" ]; then
		echo "-v selected"
	fi
	
	if [ "$QUIET" = "1" ]; then
		echo "-q selected"
	fi

	if [ "$STFU" = "1" ]; then
		echo "-stfu selected"
	fi

fi


if [ "$DEBUG" = "1" ]; then
	echo "Check for $DOWNLOADEDTEMP"
fi

# Copy temp log over if we quit shell before completion last time
# This shouldn't happen though, should have been done automatically on clean_up
if [ -e $DOWNLOADEDTEMP ]; then
	echo "Found $DOWNLOADEDTEMP file.  This is a bad sign as it should always remove this!"
	echo "Amalgamating with $DOWNLOADEDLIST file..."
	cat $DOWNLOADEDLIST >> $DOWNLOADEDTEMP
	sort $DOWNLOADEDTEMP | uniq > $DOWNLOADEDLIST
	rm $DOWNLOADEDTEMP
fi


# Check for podcast list file
if [ "$DEBUG" = "1" ]; then
	echo "Check for $PODCASTLIST"
fi

if [ -e "$PODCASTLIST" ]; then
	# Don't do anything as we need this file!
	echo "Found $PODCASTLIST"
else
	# If we can't find the file can just exit as haven't touched any other files
	echo "Failed to find $PODCASTLIST.  Exiting..."
	exit
fi


# Check for podcast log file
if [ "$DEBUG" = "1" ]; then
	echo "Check for $DOWNLOADEDLIST"
fi

if [ -e "$DOWNLOADEDLIST" ]; then
	# Don't do anything as we need this file!
	if [ "$DEBUG" = "1" ]; then
		echo "Found $DOWNLOADEDLIST"
	fi
else
	# If we can't find the file can just exit as haven't touched any other files
	echo "Failed to find $DOWNLOADEDLIST.  Creating..."
	touch DOWNLOADEDLIST
fi



# Check temp directory exists
if [ -d "$TEMPDIR" ]; then
	echo "Found temporary directory $TEMPDIR"
else
	echo "Creating temporary directory $TEMPDIR"
	mkdir $TEMPDIR
fi


# Read podcast list
if [ "$DEBUG" = "1" ]; then
	echo "Reading $PODCASTLIST files"
fi

while read PODCASTURL PODCASTDIR
do

	# Check for # at start
	if echo $PODCASTURL | grep '^#' > /dev/null
	then
		# If we have then ignore line
		if [ "$DEBUG" = "1" ]; then
			echo "Ignoring comment: $PODCASTURL"
		fi
	else
		# If not lets see if we can download it
		if [ "$DEBUG" = "1" ]; then
			echo "Read in line:$PODCASTURL"
		fi

		# Otherwise we want to check there is a directory for the podcast		
		if test ! $PODCASTDIR ; then
			# If it isn't there error
			echo "No directory listed for $PODCASTURL"
		else
			# We have found the directory name, lets see if it exists
			if [ -d $PODCASTDIR ] ; then
				# If it does we don't want to do anything
				if [ "$DEBUG" = "1" ]; then
					echo "Found directory: $PODCASTDIR"
				fi
			else
				# If it doesn't we need to make it
				echo "Creating $PODCASTDIR directory"
				mkdir $PODCASTDIR
			fi

			# Now we know we have a URL, a DIR and the DIR exists we can get the podcast list
			echo "Getting podcast list from $PODCASTDIR ($PODCASTURL)"

			# OK this is stolen from bashpodder.shell as I don't get it entirely :(
			PODCASTFILES=$(wget -q $PODCASTURL -O - | xsltproc parse_enclosure.xsl - 2> /dev/null) || PODCASTFILES=$(wget -q $PODCASTURL -O - | tr '\r' '\n' | tr \' \" | sed -n 's/.*url="\([^"]*\)".*/\1/p')

			if [ "$DEBUG" = "1" ]; then
				echo "Podcast Files are: $PODCASTFILES"
			fi

			# For each podcast
			for PODCASTFILEURL in $PODCASTFILES
			do

				# This is also from the bashpodder.shell
				#the realurl fix for dynamically generated feeds (from Huw Lynes and James Stone)
				ACTUALURL=`curl -s -I -L -w %{url_effective} --url $PODCASTFILEURL | tail -n 1`
				#short url (i.e. filename!) from James Stone
				TEMPURL=`echo $ACTUALURL|awk -F / '{print $NF}'`
				FILENAME=`echo $TEMPURL|awk -F ? '{print $1}'`

				if [ "$DEBUG" = "1" ]; then
					echo "Actual URL: $ACTUALURL"
					echo "Temp URL: $TEMPURL"
					echo "FileName: $FILENAME"
				fi


				# See if we have downloaded it already
				if grep "$FILENAME" $DOWNLOADEDLIST > /dev/null
				then
					# If we have tell user if debug mode
					if [ "$DEBUG" = "1" ]; then
						echo "Already downloaded $FILENAME"
					fi
				else
					# If we haven't then download it unless running catchup
					if [ "$CATCHUP" = "1" ]; then

						if [ "$DEBUG" = "1" ]; then
							echo "Running catchup, skipping download of $FILENAME"
						fi

					else
						echo "Downloading $ACTUALURL..."

						# If we have verbose then show the wgets
						if [ "$VERBOSE" = "1" ]; then
							wget -c -P $TEMPDIR "$ACTUALURL"
						else
							wget -q -c -P $TEMPDIR "$ACTUALURL"
						fi

						# Move it into the relevant directory when it's done
						mv $TEMPDIR/$FILENAME* $PODCASTDIR/$FILENAME

					fi

					# And add the filename onto the bottom of the temp download list
					echo $FILENAME >> $DOWNLOADEDTEMP

				fi
			
			done

		fi

	fi


done < $PODCASTLIST

FUNC_CLEAN_UP

```

---

### Post by bountonw on 2006-07-05
I have been six months without a podcast every since switching to Linux.  Finally grabbed a few minutes to try and get connected again.  Followed through the steps and got bashpodder installed.  I tried to reimport podcast list, and got the following error in the terminal

```
convert.sh: line 5: lynx: command not found
convert.sh: line 5: lynx: command not found
```

I looked in convert.sh and found line 5 and the word lynx and that is the limit of my ability.  What do I do now?

---

### Post by Sarisar on 2006-07-05
Someone mentions this further up, but you need to install lynx.  Strangely enough it's 'lynx' under synaptic package manager :)

---

### Post by Psy-Krow on 2008-05-09
update:  linc is hosting bash podder at a different site now.

[http://lincgeek.org/bashpodder/](http://lincgeek.org/bashpodder/)

---

### Post by minchina on 2009-11-14
I don't know if this is still a live tread, but I am having a problem with bashpodder.  Everything is install and works, and I even have it running in cron.  The problem is that bashpodder creates a daily folder (e.g. 2009-11-14), but in that folder there is only an empty file called "podcast.m3u" - no mp3.  I am trying to download the podcast from here: [http://feeds.kcrw.com/kcrw/tu](http://feeds.kcrw.com/kcrw/tu).  It works great for other feeds - any ideas?

---

