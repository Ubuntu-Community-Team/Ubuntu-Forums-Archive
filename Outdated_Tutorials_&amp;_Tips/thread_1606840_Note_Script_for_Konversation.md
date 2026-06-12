---
title: "Note Script for Konversation"
date: 2010-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by vis.15 on 2010-10-27
This is a script that I created for Konversation. This script allows you to select a Nick and then write some notes about that User. Here is the full list of commands for the script: (I call my script nn, because it is very easy to type in. So I will be calling the script with /nn)

/nn - Opens up Notes file for selected Nick and Inserts date and Time at the end of the notes file. 

/nn c - Checks to see if there is a notes file for the selected nick.

/nn t - Opens up the notes file for selected nick, but does NOT insert the date and time.

/nn l - List last user note's opened.

/nn n NICK - When in a PM or no nick is selected, allows you to manual open a users/nick notes.

/nn d - Delete Last Nick user's notes.

/nn tc - Creates only a notes file. Does not open the notes.

/nn nc NICK- Manually checks if a User Note Exist.

/nn nt NICK - Manually open up User note and do not insert date.

/nn v - View Script Name, Author and Version.

/nn vs - Show the current channel /nn v.


Here is the code:
```

#!/bin/bash
Version="3.4"
Author="Dis"
Name="Konversation User Notes Script"
#note: $1=Server, $2=Channel, $3=File, $4=t/c/tc/n/d, $5=Nick,
#note: t=No Date/Time, c=check, d=delete last nick opened
#feature: /nn n Nick on PM's or No Nick Selected; Done.
#feature: /nn l; list what's in LN Done.
#feature: /nn v/vs; version/version show in IRC; Done.
# /nn nc Manually check if Note Exist.
#/nn nd broken.

File=$3 #this is so, b/c positional parameters are very hard to change
BB= #Turns Text Bold in IRC #0x02 = Bold

if [[ "$4" == *v* ]]; then
	if [ "$4" == "vs"  ]; then
		qdbus org.kde.konversation /irc say $1 "$2" "/me is using $BB $Name $BB By: $BB $Author $BB v:$Version"
	else	
		qdbus org.kde.konversation /irc info "Is $BB $Name $BB By: $Author $BB v:$Version"
	fi
	exit;
fi

LN=`echo ${3##*/}` #LN=Last nick; ##=last last part; *=*; /=split char
Dir=`echo ${3%/*}` #Dir = Working Directory; %=first part;

if [[ "$4" != *d* ]] && [[ "$4" != *l* ]]; then
	echo "$5$LN" > $Dir/LN; #saves file/nick into current working dir
	
	if [[ "$4" == *n* ]]; then # && [[ "$5" != "" ]]
		File="$Dir/$5$LN"
		LN=`echo ${File##*/}`
		Dir=`echo ${File%/*}`
	fi
elif [[ "$4" == *d* ]] || [[ "$4" == *l* ]]; then
	File=$Dir/`cat $Dir/LN` #File = file/Last Nick Used
	if [[ "$4" == *l* ]]; then
		LN=`echo ${File##*/}`
		Dir=`echo ${File%/*}`
		qdbus org.kde.konversation /irc info "Last Nick: $Dir/$BB $LN $BB"
		exit;
	fi
fi

if [ -e $File ]; then
	ex="t" #if exist (ex) then True
	NL='\n'
elif [ ! -e $File ]; then
	ex="f" #if not exist (ex) then False
	CF="$BB Created $BB File: $Dir/$BB $LN" 
else
	qdbus org.kde.konversation /irc error "An Unknown Error has Occurred."
	exit;
fi

if [[ "$4" == *t*  ]]; then #spaces matter! Just like regular commands!
	UU=`echo $4 | tr '[a-z]' '[A-Z]'`; #lower to upper case
	KonInfo="In Mode: $BB $UU"
	
	if [[ "$4" == *tc* ]]; then
		touch $File
	fi
else #&&=to make new file, e.g. /nn n dis; || b/c check fails, /nn c
	if [ "$ex" == "t" ] && [[ "$4" == *c* ]]; then
		qdbus org.kde.konversation /irc info "File: $Dir/$BB$LN exist"
		exit;
	elif [ "$ex" == "t" ] || [[ "$4" != *c* ]]; then
		if [[ "$4" != *d* ]]; then
			echo -e $NL`date +"%a, %b %d %r %Y %Z"`'\n' >> $File
		fi
	fi
	if [ "$ex" == "f" ] && [ "$5" == "" ]; then
		if [[ "$4" == *c* ]]; then
			ERR='info'
		else
			ERR="$BB error $BB"
		fi
		qdbus org.kde.konversation /irc $ERR "File: $Dir/$BB $LN does not exist"
		exit;
	fi
fi

if [[ "$4" != *d* ]]; then
	if [ "$ex" == "f" ]; then
		qdbus org.kde.konversation /irc info "$CF"
	fi
	
	qdbus org.kde.konversation /irc info "$BB Opened $BB up: $Dir/$BB $LN $BB from $2 $KonInfo";
	gedit $File;
	qdbus org.kde.konversation /irc info "$BB Closed: $BB $Dir/$BB $LN $BB from $2 $KonInfo";
elif [[ "$4" == *d* ]]; then
	rm $File
	qdbus org.kde.konversation /irc info "File $Dir/$BB$LN was deleted."
else
	qdbus org.kde.konversation /irc error "Unknown Command."
fi


```

---

