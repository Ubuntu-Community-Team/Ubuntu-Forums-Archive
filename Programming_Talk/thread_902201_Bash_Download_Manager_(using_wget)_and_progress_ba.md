---
title: "Bash Download Manager (using wget) and progress bar"
date: 2008-08-27
forum: Programming Talk
---

### Post by RastaCre on 2008-08-27
Hi All,

I'm wrote a download manager script in bash using wget (my 1st bash script ever...).

The script works and does what it is supposed to do, so now I'm working on the UI (if we can call it this way).

So I'm stuck now trying to figure out a way to disable the wget output (connection info etc) but still be able to see a progress bar.

so this is what the output looks like while downloading:

```
downloading: DSCF0599.JPG ...
--09:30:42--  http://xxx.xxx/DSCF0599.JPG
           => `/home/rastacre/Downloads/DSCF0599.JPG'
Resolving xxx.xxx... xxx.xxx.xxx.xxx.
Connecting to xxx.xxx|xxx.xxx.xxx.xxx|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,614,820 (1.5M) [image/jpeg]

19% [======>                              ] 614,424      173.62K/s    ETA 00:14
```


and here's what I would like to see:

```
downloading: DSCF0599.JPG ...
19% [======>                              ] 614,424      173.62K/s    ETA 00:14
```

or something similar anyway...

Any ideas?

By the way, the script is meant to download stuff from RapidShare with a premium account. It allows to generate an RS cookie and maintains a log of downloaded files.

here's the code if you want to give it a try, also if anyone has ideas or suggestion I would much appreciate. Please bear in mind this really is my first script ever :) :



```
#!/bin/bash
#    RapidGet.sh
# 
#    A program that download files from RapidShare with a Premium user account,
#    by either direct URL input or from a file conatining a list of links
#    It also generate RapidShare cookies and maintaina log of downloaded files.
#
#    #######################################################################
#    #######################################################################
#
#    Copyright (C) 2008 RastaCre
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
#    #######################################################################
#    #######################################################################
#    
#    Guidelines for list file
#    
#    The list file can be structured to allow download of gorups of file
#    into separate paths:
#    
#    adding:
#    
#    	[path]<ABSOLUTE_PATH> 
#    
#    before a group of files will be used as path for such group. 
#    A new line in the list containing:
#    
#   	[path]<ABSOLUTE_PATH2>
#    
#    will determine the path of the second group and so on:
#    
#    [path]/home/user/Downloads/Pictures
#    link1
#    link2
#    link3
#    [path]/home/user/Downloads/Movies
#    link4
#    link5
#    link6
#    
#    This will download link 1, 2, 3 to "/home/user/Downloads/Pictures"
#    link 4, 5, 6 will be downloaded to "/home/user/Downloads/Movies"
#    Adding a line with any single character above a link (ie. "-") 
#    will cause the program to use the default download path for the following files:
#    
#    [path]/home/user/Downloads/Pictures
#    link1
#    link2
#    link3
#    -
#    link4
#    link5
#    link6
#    
#    This will download link 1, 2, 3 to "/home/user/Downloads/Pictures" 
#    link 4, 5, 6 will be downloaded to the default download path
#    
#    When downloading compressed files protected by password, it is possible to
#    add a line containing ["pass]<password>" above a link.
#    This will add a password entry to the logfile for the downloaded link.
#    Subsequent links won't have a password entry.
#

#################################################
#################################################
##               IMPORTANT!!!!!!               ##
#################################################
#################################################
######### DO NOT MODIFY THE NEXT LINES ##########
###### SETTINGS START 2008-08-21 15:46:32 #######
SCRIPTPATH=""
LOGPATH="s"
COOKIEPATH=""
DEFAULTPATH=""
################# SETTINGS END ##################
#FROM HERE ON YOU CAN MODIFY EVERYTHING YOU WANT#
#################################################
#################################################

VER="0.80"
#Log files and cookie
LOGFILE="$LOGPATH/.downloads_log"
CACHEFILE="$LOGPATH/.downloads_cache"
TEMPLOG="$LOGPATH/.downloads_templog"
COOKIE="$COOKIEPATH/.rapidcookie"

#Colour setttings
RED='\e[1;31m'
CYAN='\e[1;36m'
NC='\e[0m'
BL='\e[1;34m'
GR='\e[0;32m'
YEL='\e[1;33m'
DG='\e[1;30m'

#
# BEGINNING OF FUNCTIONS DECLARATION
#
######

#
# the function download requires a URL 
# the URL presence is checked from the download cache (CACHEFILE) and if present the user
# is prompted to either skip the file (already downloaded) or to download it again.
#
# when the download is completed the URL is added to the download cache (permanent file) and to
# a temporary log (TEMPLOG) that is deleted at the end of the script
#
# a log file (LOGFILE) stores start and end date for each download and also if a URL has been
# skipped
#

function download
{ 
	local URL="$1"
		
	DATETIME=`date '+%d-%m-%Y %H:%M:%S'`
	#extract the filename from the link provided
	FILENAME=`basename $URL`
	
	#check if the file is present in the CACHEFILE log, if so the file has been already downloaded
	if [ -f "$CACHEFILE" -a $(grep -i -c "$FILENAME" "$CACHEFILE") != "0" ]; 
	then
		echo -e -n "${NC}The file:\n${RED}$FILENAME ${NC}\nhas been already downloaded.Do you want to download it again?[ \033[4mY\033[0mes | \033[4mn\033[0mo | ye\033[4ms\033[0m to all | no to \033[4ma\033[0mll ] "
		if [ "$ALL" == "y" ]
		then
			ANSWER="y"
			echo -e "\nAutomatically downloading again all previously downloaded files."			
		else
			if [ "$ALL" == "n" ]
			then
				ANSWER="n"
				echo -e "\nAutomatically skipping the download of all previously downloaded files."
			else
				read -n 1 ANS
				ANSWER=`echo $ANS | tr "[:upper:]" "[:lower:]"`
			fi
		fi
		echo ""
	fi

	#skip the file if user answer n
	if [ "$ANSWER" == "n" ];
	then
		echo -e "$DATETIME|File: $FILENAME already downloaded|Skipping: $URL" >> $LOGFILE	
		echo -e "\nSkipping: ${RED}$FILENAME${NC}"
	#skipp all the file from now on
	elif [ "$ANSWER" == "a" ]
	then
		echo -e "$DATETIME|File: $FILENAME already downloaded|Skipping: $URL" >> $LOGFILE
		echo -e "\nSkipping: ${RED}$FILENAME${NC}\nAutomatically skipping the next files."
		ALL="n"
	else
		#automaticaly download all files if user answer s
		if [ "$ANSWER" == "s" ]
		then
			echo -e "\nAutomatically downloading the next files."
			ALL="y"
		fi
		
		#check if the destination path exist
		checkDir
		
		#update the logfile with the start time of download
		echo -e "$DATETIME|Start downloading: $FILENAME|From: $URL" >> $LOGFILE

		#download the file
		echo -e "${CYAN}downloading: ${BL}$FILENAME${NC} ..." 
		wget  -c --load-cookies=$COOKIE $URL -O $DPATH/$FILENAME --no-check-certificate

		#if the download complete without problem update the logfile
		#with the time of finished download
		if [ $? == 0 ] 
		then 
			DATETIME="`date '+%d.%m.%Y %H:%M:%S'`"		
			#update logfile
			echo -e "$DATETIME|Finished downloading: $FILENAME|Password: $PASSWORD|Saved in: $DPATH/$FILENAME" >> $LOGFILE
			#update cachefile
			echo $URL >> $CACHEFILE
			echo $DPATH/$FILENAME >> $TEMPLOG	
			echo -e "File: ${RED}$FILENAME${NC}\nDownloaded.                            ${BL}[${GR} OK ${BL}]${NC}" >&2

		else 
			#display an error if wget did not complete
			echo -e "Wget did not complete. downloading failed!  ${BL}[ ${RED}!! ${BL}]${NC}"  >&2; tput sgr0 ; exit 1 
		fi
	fi	
	echo -e "${NC}"	
}

#
# givemecookie generate a rapidshare cookie. It prompt the user for a user name and password
#
function givemecookie
{
	#ask for user name and password
	echo -e -n "${NC}Downloading the RapidShare cookie.\nPlease enter the user name of your RapidShare account: "
	read USER
	PSW="0"
	while [ "$PSW" == "0" ]
	do
		echo -n "Please enter the Password: " 
		read -s PASSWORD1
		echo -n -e "\nNow enter the Password again: "
		read -s PASSWORD2
		echo ""
		if [ "$PASSWORD1" == "$PASSWORD2" ]
		then
			PSW="1"
			echo -e "\nPassword Accepted.                          ${BL}[${GR} OK ${BL}]${NC}"
		else
			echo -e "The passwords provided do not match.        ${BL}[ ${RED}!! ${BL}]${NC}"
		fi	
	done
	
	#save the cookie to the default location
	wget --save-cookies=$COOKIE -q --post-data="login=$USER&password=$PASSWORD1" -O - https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi --no-check-certificate >> /dev/null
	echo -e "The cookies has been Set.                   ${BL}[${GR} OK ${BL}]${NC}"
}

#
# checks if the path provided from the command line or from the link list
# exist. If it doesn't prompt the user to either create the path or use the default one (DEFAULTPATH)
#
function checkDir
{
	if [ -d $DPATH ]
	then
		echo -e "Download path.                              ${BL}[${GR} OK ${BL}]${NC}"
	else
		echo -e -n "Path: ${RED}$DPATH${NC}\nThe destination path doesn't exist.\nDo you want to create it? [ \033[4mY\033[0mes | \033[4mn\033[0mo | ye\033[4ms\033[0m to all | no to \033[4ma\033[0mll ] "	
		if [ "$PALL" == "y" ]
		then
			echo -e "\nAutomatically creating new path."
			mkdir -p "$DPATH"	
			echo -e "New path created.                           ${BL}[${GR} OK ${BL}]${NC}"; tput sgr0
		elif [ "$PALL" == "n" ]
		then
			echo -e "\nAutomatically using default download path."
			DPATH=$DEFAULTPATH
		else
			read -n 1 PANS
			PANSWER=`echo $PANS | tr "[:upper:]" "[:lower:]"`
			
			if [ "$PANSWER" == "n" ];
			then
				DPATH=$DEFAULTPATH
			elif [ "$PANSWER" == "a" ];
			then
				DPATH=$DEFAULTPATH
				PALL="n"
				echo -e "\nAutomatically using default download path."
				
			else
				if [ "$PANSWER" == "s" ];
				then
					PALL="y"
					echo -e "\nAutomatically creating new dpaths."
				fi
				mkdir "$DPATH"	
				echo -e "\nPath: ${RED}$DPATH${NC} created ${BL}[${GR} OK ${BL}]${NC}\n"
			fi
		fi
	fi
}

#
# printlog checks if the completed download log ($TEMPLOG) has been created
# then prints the content of the file and delete the log.
#
function printtemplog
{
	if [ -a $TEMPLOG ]
	then
		echo "Downloaded Files:"
		awk '{print}' $TEMPLOG
		echo -e "${NC}"
		rm $TEMPLOG
	else
		echo "No files have been downloaded."
	fi	
}

#
# 
#
function printlog
{
	if [ -a $LOGFILE ]
	then
		awk 'BEGIN {FS="|"}
		{print $1 "\n\t" $2 "\n\t" $3 "\n"}' $LOGFILE
	else
		echo "No log file found."
	fi	
}

#
# usage prints the script usage on screen
#
function usage
{
	echo - e"/nUsage: $0 -f <FILE_PATH> -l <URL> -p <SAVE_PATH> [OPTION]...\nTry '$0 -h' for more information"
}
function uhelp
{
	echo ""
	echo "Usage: $0 -f <FILE_PATH> -l <URL> -p <SAVE_PATH> [OPTION]..."
	echo ""
	echo "  -f <FILE_PATH>	Sets the path to a file containing a list of" 
	echo "			links to download from."
	echo ""
	echo "  -l <URL>		URL for a single file download."
	echo ""
	echo "  -p <SAVE_PATH>	Specify the path where the files are" 
	echo "			going to be saved. If not specified the"
	echo "			default download path will be used:"
	echo "			home/rastacre/Downloads/"
	echo ""
	echo "  -c			Sets a new cookie. Can be used on it's own."
	echo ""
	echo "  -n			Automatically skips files that have been" 
	echo "			already downloaded according to the log."
	echo ""
	echo "  -y			Automatically download again files that"
	echo "			have been already downloaded according to the log."
	echo ""
	echo "  -N			Download to the default location if"
	echo "			the path in -p <SAEV_PATH> doesn't exist."
	echo ""
	echo "  -Y			Automatically create the <SAEV_PATH> directory"
	echo "			if it doesn't already exist."
	echo ""
	echo "  -w			Run the configuration wizard."
	echo ""	
}

#
# this function is a configuration wizard to set up the default paths of the script
# it is automatically run the 1st time the script is run or with the -w argument
#
function wizard
{
	echo -e "${NC}"
	echo ".------------------------------------------------."
	echo "|                                                |"
	if [ -z $SCRIPTPATH ]
	then
		echo "|  This is the first time you run this program!  |"
		echo "|                                                |"
	fi
	echo "|  The following wizard will help you to         |"
	echo "|  configure the script for better utilization.  |"
	echo "|                                                |"
	echo "|  Please follow the instruction on screen.      |"
	echo "|                                                |"
	echo "\`------------------------------------------------\`"
	echo ""
	
	if [ -n "$DEFAULTPATH" ]
	then
		echo -e "\nThe script is currently configured as follow:\n"
		echo -e "Script path: 		${RED}$SCRIPTPATH${NC}"
		echo -e "Log file: 		${RED}$LOGPATH/${BL}.downloads_log${NC}"
		echo -e "Cache file: 		${RED}$LOGPATH/${BL}.downloads_cache${NC}"
		echo -e "Temp log file: 		${RED}$LOGPATH/${BL}.downloads_templog${NC}"
		echo -e "Cookie: 		${RED}$COOKIEPATH/${BL}.rapidcookie${NC}"
		echo -e "Default download Path: 	${RED}$DEFAULTPATH${NC}"
		echo -e -n "\nDo you want to keep this configuration? [ \033[4mY\033[0mes | \033[4mn\033[0mo ] "
		
		read -n 1 KEEPC
		echo ""
	else
		KEEPC="n"
	fi
	
	if [ "$KEEPC" == "n" ]
	then
		DATETIME=`date '+%Y-%m-%d %H:%M:%S'`

		# determine the script name and path
		LSOF=$(lsof -p $$ | grep -E "/"$(basename $0)"$")
		SCRIPTFULL=$(echo $LSOF | sed -r s/'^([^\/]+)\/'/'\/'/1 2>/dev/null)
		if [ $? -ne 0 ]
		then
			SCRIPTFULL=$(echo $LSOF | sed -E s/'^([^\/]+)\/'/'\/'/1 2>/dev/null)
		fi

		SCRIPTPATH=$(dirname $SCRIPTFULL)
		SCRIPTNAME=$(basename $0)

		#determine the position of the settings inside the script
		SFL=`grep -n -x '######### DO NOT MODIFY THE NEXT LINES ##########' $0 | cut -f1 -d:`
		SFL=$[$SFL+1]

		C="0"
		while [ $C -lt 1 ]
		do
			echo -e "Path:\t${RED}$SCRIPTPATH${NC}"
			echo -e -n "Please confirm that this is the correct path to the script: [ \033[4mY\033[0mes | \033[4mn\033[0mo ]"
			read -n 1 ANW
			echo ""
			if [ "$ANW" != "n" ]
			then
				C=$[$C+1]
			else
				echo "Please enter the path to the script file:"
				read APATH
				SCRIPTPATH=$APATH
			fi
		done

		echo -e "\nPlease enter the absolute path for the log files:"
		echo -n "(enter \"default\" or press \"enter\" to use the script path"
		if [ -n "$LOGPATH" ]
		then
			echo " or"
			echo " enter \"old\" to use the path of the current configuration)"
		else
			echo ")"
		fi
		read LOGP

		if [ "$LOGP" == "default" -o -z "$LOGP" ]
		then
			LOGP=$SCRIPTPATH
		elif [ "$LOGP" == "old" ]
		then
			LOGP=$LOGPATH
		fi

		echo ""
		echo "Please enter the absolute path for the RapidShare cookie:"
		echo "(enter \"default\" or press \"enter\" to use the script path or"
		echo -n " enter \"log\" to use the log files' path"
		if [ -n "$COOKIEPATH" ]
		then
			echo " or"
			echo " enter \"old\" to use the path of the current configuration)"
		else
			echo ")"
		fi
		read COOKIEP

		if [ "$COOKIEP" == "default" -o -z "$COOKIEP" ]
		then
			COOKIEP=$SCRIPTPATH
		elif [ "$COOKIEP" == "log" ]
		then
			COOKIEP=$LOGP
		elif [ "$COOKIEP" == "old" ]
		then
			COOKIEP=$COOKIEPATH	
		fi

		echo ""
		echo "Please enter the absolute default download path:"
		echo "(enter \"default\" or press \"enter\" to use the script path or"
		echo " enter \"log\" to use the log files' path or"
		echo -n " enter \"cookie\" to use the cookie's path"
		if [ -n "$DEFAULTPATH" ]
		then
			echo " or"
			echo " enter \"old\" to use the path of the current configuration)"
		else
			echo ")"
		fi
		read DOWNP

		if [ "$DOWNP" == "default" -o -z "$DOWNP" ]
		then
			DOWNP=$SCRIPTPATH
		elif [ "$DOWNP" == "cookie" ]
		then
			DOWNP=$COOKIEP
		elif [ "$DOWNP" == "log" ]
		then
			DOWNP=$LOGP
		elif [ "$DOWNP" == "old" ]
		then
			DOWNP=$DEFAULTPATH
		fi

		echo "###### SETTINGS START $DATETIME #######" | tee tempvar.tmp >>/dev/null
		echo "SCRIPTPATH=\"$SCRIPTPATH\"" | tee -a tempvar.tmp >>/dev/null
		echo "LOGPATH=\"$LOGP\"" | tee -a tempvar.tmp >>/dev/null
		echo "COOKIEPATH=\"$COOKIEP\"" | tee -a tempvar.tmp >>/dev/null
		echo "DEFAULTPATH=\"$DOWNP\"" | tee -a tempvar.tmp >>/dev/null
		echo "################# SETTINGS END ##################" | tee -a tempvar.tmp >>/dev/null

		awk '
		    FNR==NR && NR>=1 && NR<=6 {
			buf = buf $0 ORS
		    }
		    FNR!=NR {
			if (FNR=="'$SFL'")
			    printf buf
			print
		    }
		    ' tempvar.tmp $0 > tempscript.tmp

		rm $SCRIPTNAME
		rm tempvar.tmp
		mv tempscript.tmp $SCRIPTNAME
		chmod +x $SCRIPTNAME

		if [ $(grep -c -x "################# SETTINGS END ##################" "$0") != "1" ]
		then
			sed -e "$[$SFL+6],$[$SFL+11]d" $SCRIPTNAME >tempscript.tmp
			mv tempscript.tmp $SCRIPTNAME
			chmod +x $SCRIPTNAME
		fi

		LOGFILE="$LOGP/.downloads_log"
		CACHEFILE="$LOGP/.downloads_cache" 
		COOKIE="$COOKIEP/.rapidcookie" 
		TEMPLOG="$LOGP/.downloads_templog" 
		DEFAULTPATH="$DOWNP" 

		echo -e "\nThe script is configured as follow:\n"
		echo -e "Script path: 		${RED}$SCRIPTPATH${NC}"
		echo -e "Log file: 		${RED}$LOGP/${BL}.downloads_log${NC}"
		echo -e "Cache file: 		${RED}$LOGP/${BL}.downloads_cache${NC}"
		echo -e "Temp log file: 		${RED}$LOGP/${BL}.downloads_templog${NC}"
		echo -e "Cookie: 		${RED}$COOKIEP/${BL}.rapidcookie${NC}"
		echo -e "Default download Path: 	${RED}$DOWNP${NC}\n"
		echo -e "Settings saved.                             ${BL}[${GR} OK ${BL}]${NC}"
		
		givemecookie
	else
		echo -e "The old configuration has been kept.        ${BL}[${GR} OK ${BL}]${NC}"
	fi
}

#
# a simple splash screen
#
function splash
{
	echo -e "${NC}"
	echo -e "${BL}.------------------------------------------------."
	echo -e "${BL}|                                                |"
	echo -e "${BL}|   ${RED}RapidGet ${NC}v. ${RED}$VER                             ${BL}|"
	echo -e "${BL}|   Copyright (C) 2008 RastaCre                  ${BL}|"
	echo -e "${BL}|                                                ${BL}|"
	echo -e "${BL}|   ${NC}A simple program for RapidSahre downloads    ${BL}|"
	echo -e "${BL}|   ${NC}EnJoY...                                     ${BL}|"
	echo -e "${BL}|                                                |"
	echo -e "${BL}\`------------------------------------------------\`"
	echo -e "${NC}"
}

#
# END OF FUNCTIONS DECLARATION
#
######

#
# BEGINNING OF PROGRAM
#
######

#
# get the arguments from the command line
#
# possible arguments are:
# -f requires a file with a list of links to download
# -l requires a direct link to the file to download
# -c generate a RapidShare cookie
# -p specify the download path
# -n automatically skip all downloaded files
# -y automatically download again all files
# -N automatically download to the default path if the specified download paths don't exist
# -Y automatically create all the paths if the specified download paths don't exist
# -w run the configuration wizard
# -s show only the splash screen
# -h shows help
# -h print the cache log on screen
#

while getopts f:l:p:cnyNYwshCL OPT 
do 
	case "$OPT" in 
		f) FILEPATH="$OPTARG";; 
		l) URL="$OPTARG";; 
		c) givemecookie ; exit 1;;
		p) DPATH="$OPTARG";;
		n) ALL="n";;
		y) ALL="y";;
		N) PALL="n";;
		Y) PALL="y";;
		w) wizard; exit 1 ;;
		s) splash; exit 1;;
		h) uhelp; exit 1;;
		C) printlog; exit 1 ;;
		L) printlog; exit 1;;
		[?]) usage ; exit 1;; 
	esac 
done 

#if the scriptpath is not declared (first run) then run the config wizard
#also generate the cookie on first run
if [ -z "$SCRIPTPATH" ]
then
	splash
	wizard
	exit 1
fi

#Set the download path, default = "home/rastacre/Downloads"
if [ -z "$DPATH" ]
then
	DPATH=$DEFAULTPATH
fi

#Check if a URL or a list of file has been passed
if [ -z "$URL" -a -z "$FILEPATH" ]
then	
	echo "You have to specify a URL or the path to a file!"
	usage
	exit 1
fi

splash

#If a URL has been passed Download from it
if [ -n "$URL" ]
then
	download "$URL"
fi

#If a list of links has been passed download from the list
if [ -n "$FILEPATH" ]
then
	for LINE in `cat $FILEPATH` 
	do 
		TYPE=${LINE:0:6}
		
		#check if the current line of the list is a path
		if [ "$TYPE" == "[path]" ]
		then
			DPATH="${LINE:6}"
		#check if the current line of the list is a password
		elif [ "$TYPE" == "[pass]" ]
		then
			PASSWORD=${LINE:6}
			echo "Password:$PASSWORD"
			echo "Password:$PASSWORD" >> $TEMPLOG
		elif [ ${#LINE} == "1" ]
		then
			PASSWORD=""
			echo "Password:[no-password]" >> $TEMPLOG
			DPATH=$DEFAULTPATH
		else
			#download from the link of the current line
			download "$LINE"
		fi
	done 
fi

#print the list of downloaded file for the current run
printtemplog

#
# END OF PROGRAM
#
######

##############################################################################
```

Thanks in advance for your help!

RastaCre

---

### Post by Reiger on 2008-08-27
Pipe it:

wget [args] **[COLOR="RoyalBlue"]|[/COLOR]** my_filter_thing

My filter thing will then strip any STDIN from the unwanted stuff; and use the remainder for the UI/STDOUT.

---

### Post by RastaCre on 2008-08-27
Thanks Reiger,

I only managed so far to get something like this...
```
0% 67.89 KB/s
0% 96.46 KB/s
0% 154.03 KB/s
0% 151.64 KB/s

```

by using this code that I found on another post of this forum:

```

wget  -c  ... 2>&1 | sed -u -n 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1 \2' 

```

it there at least a way to update the same line instead of having a bunch of new lines?

Cheers

---

### Post by Reiger on 2008-08-27
Hmm I'm not an expert in bash (happen to know about the pipe ;)) so I suggest you search for a Tutorial out there which covers a Bash-like shell; or check out ghostdog or LaRoza's sig. IIRC one of them had a link to a Bash tutorial.

---

### Post by RastaCre on 2008-08-27
Hehe Thanks anyway Reiger, you set me on the right direction, at least now I know what to look for! :)

---

### Post by ghostdog74 on 2008-08-27
```

wget http://yoururl 2>&1 | awk '
/downloading/ {print}
/Length:/ {f=1;next}
f {print}'

```
not tested

---

### Post by zazuge on 2009-04-17
sorry maybe it's outdayted but i've written a downloadmanager script
[URL="http://ubuntuforums.org/showthread.php?t=679034"]A download manager daemon
[/URL]
your script download one url at a time
and it seems your code and script skills are better than mine
so i suggest you add those functionalities to your script
* a daemon script in init.d to start stop the daemon
* the daemon lunch one instance of the DM script per user
* the script read url form a url-list in the download directory in the home path
* use pid locks to start stop wget instances
* make it work with flashgot in firefox
i've already done much of work but my script is poorly written
and don't check for errors.
maybe if we cooperate will make somethin  ^^

---

