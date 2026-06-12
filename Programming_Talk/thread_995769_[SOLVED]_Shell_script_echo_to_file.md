---
title: "[SOLVED] Shell script echo to file"
date: 2008-11-28
forum: Programming Talk
---

### Post by HandleWithCare on 2008-11-28
so I'd thought I'd create a shel script to install abcde (cd ripper) with all other things I need to make life easier (lots of friends who want exaclty the same setup). But it didn't became easier at all! I ran in to several problems but this one I realy can't solve. I tried to google for it, but that's simply impossible since words as shell, read, write etc. simple have to many results in the wrong area. So much for the introduction, here's my question:

The script sets up the program, all goes well. But then it must create a file ($HOME/.abcde.conf). When the file already exists it offers the user three options
[LIST=1]
[*]overwrite
[*]append to file
[*]keep old file
[/LIST]
The problem is that the string to write to the file is kinda big, and it must be create from questions raised by the script. So what I tried to do was to create a variable which holds the contents, like so:
```
abcdeconf="NOSUBMIT=y
MP3ENCODERSYNTAX=lame
CDROMREADERSYNTAX=cdparanoia
PADTRACKS=y
LAME=lame
ID3=id3
ID3V2=id3v2
CDPARANOIA=cdparanoia
CDDISCID=cd-discid
${eject_after_pre}EJECT=eject
NORMALIZE=normalize-audio
LAMEOPTS='-h -b 320'
ACTIONS=cddb,read,normalize,encode,tag,move,clean
OUTPUTDIR=\""$musicdir"\"
OUTPUTTYPE=mp3
OUTPUTFORMAT='\${ARTISTFILE}/[\${YEAR}] \${ALBUMFILE}/\${TRACKNUM} - \${TRACKFILE}'
VAOUTPUTFORMAT='Various - \${ALBUMFILE}/\${TRACKNUM} - \${ARTISTFILE} - \${TRACKFILE}'
ONETRACKOUTPUTFORMAT=\$OUTPUTFORMAT
VAONETRACKOUTPUTFORMAT=\$VAOUTPUTFORMAT
$maxprocsInConf
mungefilename ()
{
	echo \"\$@\" | sed s,:,\ -,g | tr / _ | tr -d \\\"\?\\[:cntrl:\\]
}
${eject_after_pre}EJECTCD=y
EXTRAVERBOSE=y"
```

the mungefilename() function should in the end like like this in the file:
[CODE}
mungefilename ()
{
	echo echo "$@" | sed s,:,\ -,g | tr / _ | tr -d \"\?\[:cntrl:\]
}
[/CODE]

Then The contents of this must be written to the file. I used 
```
echo $abcdeconf > $HOME/.abcde.conf
```
or (when append whas chosen):
```
echo $abcdeconf >> $HOME/.abcde.conf
```
This totaly screws up the code because backslashes simply disappear. It does work when I do ```
echo "the content..." > file
``` But that means that I have to repeat the same code several times which is not good coding. 

So basicly, what I wanna do is this:
Create a variable which holds the content to be written to the file.
Write this var to a file without losing backslashes.

Just in case, here's the complete script so far (and yes, it's my first shell script so it might not be perfect (or good)):
```

#!/bin/sh
# Script must run as root 
if [ $USER != "root" ]; 
then
	echo "You need to run this script as root."
	echo "Use 'sudo $0' then enter your password when prompted."
	exit 1
fi

BOLD=`tput 'smso'`
NORMAL=`tput 'rmso'`

# step 1: install abcde with all other needs:
echo "\nstep 1: installing A Better CD Encoder (ABCDE) and all other things we need"
#sudo apt-get -y install abcde lame cdparanoia cd-discid id3 id3v2 normalize-audio
# step 2: create a config file
echo "\nstep 2: creating a configuration file"
musicdir='$HOME/Music/'
echo "the mp3's will be written to $BOLD $HOME/Music $NORMAL by default.\n\rDo you want to change this folder?"
while true; do
echo -n "confirm (y or n) "
read confirm
case $confirm in
	y|Y|YES|yes|Yes) 
		pathok=1
		echo "enter the full path to the folder (if it doesn't exist it wil be created)"
		while true; do
			if [ $pathok -eq 0 ]
			then
				break
			fi
			read usermusicdir
			echo "selected path is now '$usermusicdir', is this ok?"
			while true; do
				echo -n "confirm (y or n) "
				read confirm
				case $confirm in
					y|Y|YES|yes|Yes) 
						if [ ! -d $usermusicdir ]
						then
							echo "folder does not yet exist"
							mkdir $usermusicdir							
							if [ $? -eq 0 ]
							then
								sudo chown $SUDO_USER:$SUDO_USER $usermusicdir
								if [ $? -eq 0 ]
								then
									sudo chmod 755 $usermusicdir
									musicdir=$usermusicdir
									echo "folder created and chowned as $SUDO_USER:$SUDO_USER"
									pathok=0 
								else
									echo "something went wrong, please choose a different folder"
								fi
							else
								echo "can't set permissions to given path, please retry"
							fi
						fi				
						break
					;;
					n|N|no|NO|No)												 
						echo "please enter a new path"									
						break
					;;
					*) echo "please enter only y or n"
				esac
			done
		done
		break
	;;
	n|N|no|NO|No)
		break 
	;;
	*) echo "please enter only y or n"
esac
done
echo "Using folder '$musicdir'"
echo "\ndo you want the cd-player to eject the cd after ripping is done?"
while true; do
echo -n "confirm (y or n) "
read confirm
case $confirm in
	y|Y|YES|yes|Yes) 
		eject_after_pre=""
		break
	;;
	n|N|no|NO|No)
		eject_after_pre="#"
		break 
	;;
	*) echo "please enter only y or n"
esac
done
echo "\nabcde can use multiple cores when encoding cd's.\nif you have a multicore processor, enter the number of cores you want abcde to use,\nor press enter if you don't have a multicore precessor or when you simply don't want to use this feature"
while true; do
echo -n "enter the number of cores "
read maxprocs
case $maxprocs in
	[1-9]) 
		maxprocsInConf="MAXPROCS=$maxprocs"
		break
	;;
	"")
		maxprocsInConf="#MAXPROCS=2"
		break 
	;;
	*) echo "please enter a positive integer"
esac
done
# create a variable that holds the contents of the configfile
abcdeconf="NOSUBMIT=y
\rMP3ENCODERSYNTAX=lame
\rCDROMREADERSYNTAX=cdparanoia
\rPADTRACKS=y
\rLAME=lame
\rID3=id3
\rID3V2=id3v2
\rCDPARANOIA=cdparanoia
\rCDDISCID=cd-discid
\r${eject_after_pre}EJECT=eject
\rNORMALIZE=normalize-audio
\rLAMEOPTS='-h -b 320'
\rACTIONS=cddb,read,normalize,encode,tag,move,clean
\rOUTPUTDIR=\""$musicdir"\"
\rOUTPUTTYPE=mp3
\rOUTPUTFORMAT='\${ARTISTFILE}/[\${YEAR}] \${ALBUMFILE}/\${TRACKNUM} - \${TRACKFILE}'
\rVAOUTPUTFORMAT='Various - \${ALBUMFILE}/\${TRACKNUM} - \${ARTISTFILE} - \${TRACKFILE}'
\rONETRACKOUTPUTFORMAT=\$OUTPUTFORMAT
\rVAONETRACKOUTPUTFORMAT=\$VAOUTPUTFORMAT
\r$maxprocsInConf
\rmungefilename ()
\r{
\r\techo \"\$@\" | sed s,:,\ -,g | tr / _ | tr -d \\\"\?\\[:cntrl:\\]
\r}
${eject_after_pre}EJECTCD=y
EXTRAVERBOSE=y"

# create an actionvar which can 3 options
# 1) overwrite the file
# 2) add configuration to the end of the file (might stop abcde from working correctly)
# 3) keep the file on the system 
#does the file already exist?
configPath="$HOME/.abcde.conf"
if [ -f $configPath ];
then
	echo "\nthe file .abcde.conf already exists in $HOME"
	echo "what would you like to do?"
	echo "1) overwrite the file RECOMENDED"
	echo "2) append configuration to the end of the script (WARNING: this might stop abcde from working correctly, only choose this option if you know what you're doing!"
	echo "3) keep the old file"
	echo -n "enter your choice and hit return ";
	while true; do	
	read action
	case $action in
		3)
			break
		;;
		2)
			echo $abcdeconf >> $configPath
			break
		;;
		1)
			echo $abcdeconf > $configPath
			break
		;;
		*) echo "please enter 1, 2 or 3"
	esac
	done
else
	echo $abcdeconf > $configPath
fi
sudo chown $SUDO_USER:$SUDO_USER $configPath
chmod 777 $configPath
echo "DONE!\n"
exit 0

```

---

### Post by dwhitney67 on 2008-11-28
I'm not 100% sure what your issue is.  Is it that you are concerned about duplicating code, or is it that you are having trouble writing text to a file that contains back-slashes (\)?

Here's a simple example demonstrating how to write data (that contains back-slashes) to a file, depending on whether the user wants to replace or append to the file:
```

#!/bin/sh

FILE="abcd.conf"
VAR="\\foo\\fubar"
ANS='r'

if [ -f $FILE ]
then
        echo -n "File '$FILE' exists; should I replace it, append to it, or cancel operation (r/a/c)? "
        read ANS
fi

case "$ANS" in
        'r') echo $VAR  > $FILE;;
        'a') echo $VAR >> $FILE;;
          *) exit 0;;
esac

echo "Contents of $FILE are:"
cat $FILE

exit 0

```

In as far as duplicating code, you did not indicate how many of lines are of issue; if it is only a few, I would not worry about it.  Alternatively though, you can consider creating a function, even one that expects parameters (e.g. $0, $1, etc).

For example:
```

#!/bin/sh

function shazam()
{
  echo $0     # echos program name
  echo $1     # echos first parameter
  echo $2     # echos second parameter
}

# main portion of script
# ...
shazam "\\First-Arg" "\\Second-Arg"

```

---

### Post by HandleWithCare on 2008-11-28
Thanks for your reply. My biggest concern was (and still is) how to echo backslashes to a file. Your solution doesn't work either. In stead of a backslash the file contains some unreadable character afterwards. It's weird... You'd think It would work.

---

### Post by dwhitney67 on 2008-11-28
> **HandleWithCare said:**
> Thanks for your reply. My biggest concern was (and still is) how to echo backslashes to a file. Your solution doesn't work either. In stead of a backslash the file contains some unreadable character afterwards. It's weird... You'd think It would work.

The example script I provided in the earlier post works fine on my system.  Try testing with it, because at this point all I can think of is that your script has a problem that is unrelated to writing back-slashes to a file.

---

### Post by HandleWithCare on 2008-11-28
Strange. But the problem is different than in my script. If I do the follwowing:
```

abcdeconf="some text
\rmungefilename ()
\r{
\r\techo \"\$@\" | sed s,:,-,g | tr / _ | tr -d \\'\\\"\\?\\[:cntrl:\\]
\r}"
echo abcdeconf > ./abcde.conf

```
the content of the file becomes this:
```

some text
mungefilename () 
{ 
	echo "$@" | sed s,:,-,g | tr / _ | tr -d '"?[:cntrl:] 
}

``` 
instead of what it should be, which is:
```

some text
mungefilename () 
{
        echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

```

I just can't find out what's going wrong here.

---

### Post by dwhitney67 on 2008-11-28
Lose the \r and \t characters.  If you want a tab, then hit the tab key.

Then when you echo abcdeconf, do it like this:
```

echo "$abcdeconf" > ./abcde.conf

```

---

### Post by HandleWithCare on 2008-11-28
I love you...

works like a charm now!

---

