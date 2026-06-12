---
title: "advise on making code snippet more efficient"
date: 2011-10-27
forum: Programming Talk
---

### Post by cj13579 on 2011-10-27
Hi all,

I am writing a little program to automatically manage some TV shows that I may or may-not download via torrent :)

I have a section of code which checks the file name of the downloaded file against a config file which looks like:

```
The.Big.Bang.Theory:/media/TV/The Big Bang Theory
Strike.Back:/media/TV/Strike Back
Game.Of.Thrones:/media/TV/Game of Thrones
etc...
```

I would like the code to be future proof creating new Season folders if needed up to infinity (or at least something higher than 8!). I currently have a Windoze pretty folder structure with spaces etc but I am happy to rename if needed as it doesn't matter too much as I am using XBMC to watch it all.

Currently the code also goes through all the possible options regardless of whether or not it has moved the file or not.

```
#Read in the list of defined TV shows line by line
cat $TVSHOWS | while read line1
do
#For each TV show (line1) create a number of variables

#The name of the TV show
SHOW=${line1%:*}

#The length of the show name - Used to find where the season number begins
SHOW_L=${#SHOW}
SHOW_L=$SHOW_L+2;

#After the delimiter, the location where we want this show to be stored.
LOC=${line1##*:}

   #Cycle through the downloaded files trying to match to a TV show we have defined.
   cat downloads.tmp | while read DOWNLOAD
   do
   if [[ $DOWNLOAD == $SHOW.S* ]] ; then
         season=${DOWNLOAD:$SHOW_L:2}
        if [ $season = 01 ] && [ -d "$LOC/Season 1" ] ; then
            mv $DOWNLOAD "$LOC/Season 1";
			elif [ $season = 01 ] && [ ! -d "$LOC/Season 1" ] ; then
				mkdir "$LOC/Season 1";
				mv $DOWNLOAD "$LOC/Season 1";
			fi
        fi
        if [ $season = 02 ] && [ -d "$LOC/Season 2" ] ; then
            mv $DOWNLOAD "$LOC/Season 2";
			elif [ $season = 02 ] && [ ! -d "$LOC/Season 2" ] ; then
				mkdir "$LOC/Season 2";
				mv $DOWNLOAD "$LOC/Season 2";
			fi	
        fi
        if [ $season = 03 ] && [ -d "$LOC/Season 3" ] ; then
            mv $DOWNLOAD "$LOC/Season 3";
			elif [ $season = 03 ] && [ ! -d "$LOC/Season 3" ] ; then
				mkdir "$LOC/Season 3";
				mv $DOWNLOAD "$LOC/Season 3";
			fi
		fi
        if [ $season = 04 ] && [ -d "$LOC/Season 4" ] ; then
            mv $DOWNLOAD "$LOC/Season 4";
			elif [ $season = 04 ] && [ ! -d "$LOC/Season 4" ] ; then
				mkdir "$LOC/Season 4";
				mv $DOWNLOAD "$LOC/Season 4";
			fi
		fi
        if [ $season = 05 ] && [ -d "$LOC/Season 5" ] ; then
            mv $DOWNLOAD "$LOC/Season 5";
			elif [ $season = 05 ] && [ ! -d "$LOC/Season 5" ] ; then
				mkdir "$LOC/Season 5";
				mv $DOWNLOAD "$LOC/Season 5";
			fi			
        fi
        if [ $season = 06 ] && [ -d "$LOC/Season 6" ] ; then
            mv $DOWNLOAD "$LOC/Season 6";
			elif [ $season = 06 ] && [ ! -d "$LOC/Season 6" ] ; then
				mkdir "$LOC/Season 6";
				mv $DOWNLOAD "$LOC/Season 6;"
			fi
        fi
        if [ $season = 07 ] && [ -d "$LOC/Season 7" ] ; then
            mv $DOWNLOAD "$LOC/Season 7";
			elif [ $season = 07 ] && [ ! -d "$LOC/Season 7" ] ; then
				mkdir "$LOC/Season 7";
				mv $DOWNLOAD "$LOC/Season 7";
			fi
        fi
        if [ $season = 08 ] && [ -d "$LOC/Season 8" ] ; then
            mv $DOWNLOAD "$LOC/Season 8";
			elif [ $season = 08 ] && [ ! -d "$LOC/Season 8" ] ; then
				mkdir "$LOC/Season 8";
				mv $DOWNLOAD "$LOC/Season 8";
			fi
        fi
    fi
    done
done
```

I am going to continue plugging away at this but wanted to start this thread so that I can sponge ideas of people much cleverer than I. I think that I know the answer to the "check if I've moved anything" but need to try it out a few times.


I would still love to hear any input as to how I can make this better though. Also more than happy to post the full thing should it be required or anyone else wants to use it.

Many thanks in advance for any advice.

---

### Post by cj13579 on 2011-10-27
OK, think I have got something better now. It only goes up to 29 seasons but I don't know any TV shows that got that high any ways so I think I'm good for now. I will be easy to expand anyway if needed.

```
		case $season in
		0[1-9])
		i = $(echo $season | cut -c 2)
				if [ -d "$LOC/Season $i" ]; then
			mv $DOWNLOAD "$LOC/Season $i";
		else 
			[ ! -d "$LOC/Season $i" ] && [ $i -eq 0 ] ; then
				mkdir "$LOC/Season $i";
				mv $DOWNLOAD "$LOC/Season $i";
        fi
		;;
		1[0-9])
		i = $season
				if [ -d "$LOC/Season $i" ]; then
			mv $DOWNLOAD "$LOC/Season $i";
		else 
			[ ! -d "$LOC/Season $i" ] && [ $i -eq 0 ] ; then
				mkdir "$LOC/Season $i";
				mv $DOWNLOAD "$LOC/Season $i";
        fi
		;;
		2[0-9])
		i = $season
				if [ -d "$LOC/Season $i" ]; then
			mv $DOWNLOAD "$LOC/Season $i";
		else 
			[ ! -d "$LOC/Season $i" ] && [ $i -eq 0 ] ; then
				mkdir "$LOC/Season $i";
				mv $DOWNLOAD "$LOC/Season $i";
        fi
		;;
		esac
```

Who would have thought it, replacing Evernote to think out loud on here!

I am sure that this isn't perfect (because I'm not very good) so if some one can think of an even better way I'd love to hear it!

---

