---
title: "Code to quickly restore and backup disks..."
date: 2012-07-14
forum: New to Ubuntu
---

### Post by frenchn00b on 2012-07-14
Hi, 

it can help absolute beginners.

it is called clone-hdd.sh


Here it is:

```


#!/bin/sh

# init
rm /tmp/dialog.rep
rm /tmp/dialog.tmp
rm dialog.rep  
rm dialog.tmp 


LINES=$(tput lines)
COLUMNS=$(tput cols)


echo "Size console: $COLUMNS $LINES"
COL=$(( $COLUMNS -5 ))
LIG=$(( $LINES -3 ))


echo "Check your directory: "
pwd

if [ ! -f completed.wav ] ; then 
	echo "File completed.wav not found."
	echo "Please check your directory (pwd)"
	exit
fi




if [ "$1" != "--force"  ] ; then 
	if [ "$(whoami)" != "root" ]  ; then 
		echo "You are $(whoami) and not root."
		echo "Program exited."
		exit
	fi
fi



# clear
clear
echo "Current Path: $(pwd)"


# mode
rm /tmp/dialog.tmp
echo "Backup" > /tmp/dialog.tmp
echo "Restore" >> /tmp/dialog.tmp


	LISTOFFILES=` cat /tmp/dialog.tmp  `
	DIALOGLIST=` echo "${LISTOFFILES}" | sed 's/\ /_/g'   | awk -F ";" ' {  printf "\x22"NR"\x22"  " " "\x22"$0"\x22" " " }  '    `
	DIAG=$(dialog --menu "Choose one:" 60 800 80 ` echo "$DIALOGLIST" | head -n 1  `     2>&1 >/dev/tty  )
	if [ "$DIAG" = "" ] ; then
        	DIAG=""
	        exit
	fi
	CHOICE=`echo "${DIAG}" | sed 's/\"//g'`
	#[ "${CHOICE}" != ""  ] && echo "*$CHOICE*"
	echo "${LISTOFFILES}" | head -n "$CHOICE" | tail -n 1
	MODE=` echo "${LISTOFFILES}" | head -n "$CHOICE" | tail -n 1 `
	###MODE=`sh fvwmdialog.sh --sf dialog.tmp `



# mode restore
if [ "Restore" = "$MODE" ] ; then
	echo "Restore mode"
	aplay ding.wav

        # target now
        dialog --backtitle RESTORE  --fselect "$(pwd)/" 15 86  2>/tmp/dialog.rep
        SOURCEFILE=` cat /tmp/dialog.rep`
        echo "Source file: *$SOURCEFILE*"
        if [ ! -f "$SOURCEFILE" ]  ; then
                echo "You must enter a filename $SOURCEFILE that exists"
                exit
        fi

	# display info
	DESC=""

	IMGGZTEST=`echo "$SOURCEFILE"  | tail -c 8`
	IMGTEST=`echo "$SOURCEFILE"  | tail -c 5`
	[ "$IMGTEST" = ".img" ] && FORMATSRC="img"
	[ "$IMGGZTEST" = ".img.gz" ] && FORMATSRC="img.gz"


		[ "$IMGTEST" = ".img" ] &&  SOURCEFILEINFO=`echo "$SOURCEFILE" | awk ' {  gsub(".img",".info.txt") ; printf $0  }  '`
		[ "$IMGGZTEST" = ".img.gz" ] &&  SOURCEFILEINFO=`echo "$SOURCEFILE" | awk ' {  gsub(".img.gz",".info.txt") ; printf $0  }  '`

		if [  -f  "$SOURCEFILEINFO"    ] ; then 
			cat "$SOURCEFILEINFO" > /tmp/dialog.tmp
			dialog  --backtitle "RESTORE - Information file: ${SOURCEFILEINFO} "  --textbox /tmp/dialog.tmp 20 60
			DESC=` cat "$SOURCEFILEINFO"   `
			rm /tmp/dialog.tmp 
		fi
	echo "$SOURCEFILE"
	echo "$IMGTEST $IMGGZTEST : $SOURCEFILEINFO"
	echo "$FORMATSRC"


        ### select the disk
        if  [ "$(whoami)" != "root"  ] ; then
                sudo fdisk -l | grep "/dev/" | grep -v Disk > /tmp/dialog.tmp
                else
                fdisk -l | grep "/dev/" | grep -v Disk > /tmp/dialog.tmp
        fi
        file=`sh fvwmdialog.sh --sf /tmp/dialog.tmp `
        [ "$file" = "" ] && exit
        TARGETTMP=`echo "$file" | awk ' { print $1 } '`
        echo "Backup target: *$TARGETTMP*"

	# valid the disk with output
        dialog --backtitle RESTORE  --inputbox  output 20 60 "$TARGETTMP" 2>/tmp/dialog.rep
        TARGET=` cat /tmp/dialog.rep`
        echo "Target disk: *$TARGET*"
	echo "Src: $SOURCEFILE => $TARGET"



	# now cmdtd info
	if [ "$FORMATSRC" = "img.gz" ] ; then
		    CMDTDNFO="gunzip -c ${SOURCEFILE} | dd of=${TARGET}"
		echo "> $CMDTDNFO <$FORMATSRC> $CMDTDNFO "

	fi
	if [ "$FORMATSRC" = "img" ] ; then 
		 CMDTDNFO="dd  if=${SOURCEFILE} of=${TARGET}"
		echo "> $CMDTDNFO <$FORMATSRC> $CMDTDNFO "

	fi


        # confirm yes/no
        dialog  --backtitle RESTORE   --yesno "Command: \n $CMDTDNFO  \n \n Description:\n $DESC "  15 55  2>/tmp/dialog.rep


        # run it
        clear
        date
        echo " "
	echo " "
	echo "Disks: "
	fdisk -l | grep "${TARGET}"
	echo " " 
        echo "Command restore :  $CMDTDNFO  "
        echo "<Enter Return to start>"
        read enternowkey


        # run it
	echo "Start $(date)"
        if [  "$2" = "--debug"    ] || [ "$1" = "--debug" ] ; then
        	        echo "Debug"
                        else
				echo "	$FORMATSRC format: real mode - operation"
				# [ "FORMATSRC" = "img.gz" ] &&   gunzip -c ${SOURCEFILE} | dd of=${TARGET} 
				# [ "FORMATSRC" = "img" ] &&      dd  if="${SOURCEFILE}"  of="${TARGET}"

				echo "	source=${SOURCEFILE} - target=${TARGET}"

                                [ "$IMGTEST" = ".img" ]      &&  echo "	Operation img" 
                                [ "$IMGGZTEST" = ".img.gz" ] &&  echo "	Operation img.gz"
				# exit
				[ "$IMGTEST" = ".img" ]      &&  dd  if="${SOURCEFILE}"  of="${TARGET}"
			        [ "$IMGGZTEST" = ".img.gz" ] &&  gunzip -c ${SOURCEFILE} | dd of=${TARGET}

        fi
        echo "End $(date)"
        aplay completed.wav
fi





# mode backup
if [ "Backup" = "$MODE" ] ; then 
	aplay ding.wav
	echo "Backup mode"
	### select the disk
	if  [ "$(whoami)" != "root"  ] ; then 
		sudo fdisk -l | grep "/dev/" | grep -v Disk > /tmp/dialog.tmp
		else
		fdisk -l | grep "/dev/" | grep -v Disk > /tmp/dialog.tmp
	fi
	file=`sh fvwmdialog.sh --sf /tmp/dialog.tmp `
	[ "$file" = "" ] && exit
	SOURCETMP=`echo "$file" | awk ' { print $1 } '`
	echo "src: *$SOURCETMP*"


	# valid the disk with output
	dialog --backtitle BACKUP  --inputbox  output 20 60  "$SOURCETMP" 2>/tmp/dialog.rep
	SOURCE=` cat /tmp/dialog.rep`
	echo "Source disk: *$SOURCE*"


	# target now
	rm /tmp/dialog.rep
	dialog --backtitle BACKUP  --fselect "$(pwd)/"   16 85   2>/tmp/dialog.rep
	TARGETDSK=` cat /tmp/dialog.rep`
	echo "Targetdsk: *$TARGETDSK*"
	if [ -d "$TARGETDSK" ]  ; then 
		echo "You must enter a filename ex. test"
		exit
	fi

	# confirm yes/no 
	TARGETFILE="$TARGETDSK.img.gz"
	TARGETFILENFO="$TARGETDSK.info.txt"
	if [ -f "${TARGETFILE}" ]  ; then 
		echo "File exist"
		exit
	fi

	# editbox information
	DATENOW=`date +%Y%m%d-%H%M%S`
	echo "${DATENOW}" > /tmp/dialog2.tmp
	dialog  --backtitle "BACKUP - Edit Information file: ${TARGETFILE} "  --editbox /tmp/dialog2.tmp 20 60 2>/tmp/dialog.tmp
	INFODSK=`cat /tmp/dialog.tmp  ` 



	# yes / no
	dialog  --backtitle BACKUP   --yesno "Command:\n dd if=${SOURCE} | gzip -c9 > ${TARGETFILE} \n\n \n Information disk: \n${INFODSK} "  20 60 2>/tmp/dialog.rep


	# run it
	clear
	date
	echo " " 
	echo "Command:  dd if=${SOURCE} | gzip -c9 > ${TARGETFILE}"
	echo "<Enter Return to start>"
	read djksf
	# run it
	echo "Start $(date)"
	if [  "$2" = "--debug"    ] || [ "$1" = "--debug" ] ; then 
				echo "Debug - File: ${TARGETFILENFO} - DD : ${TARGETFILE}"
			else
				echo "$INFODSK" > ${TARGETFILENFO}
				[ "$1" != "--nodd" ] && [ "$2" != "--nodd" ]  && [ "$3" != "--nodd" ]    && dd if=${SOURCE} | gzip -c9 > ${TARGETFILE}
	fi
	echo "End $(date)"
	aplay completed.wav
fi




#end
rm /tmp/dialog.rep  
rm /tmp/dialog.tmp 




```

---

### Post by CharlesA on 2012-07-14
You might be better off adding a check that looks for these files before removing them to prevent unneeded errors:

rm /tmp/dialog.rep
rm /tmp/dialog.tmp
rm dialog.rep  
rm dialog.tmp

---

