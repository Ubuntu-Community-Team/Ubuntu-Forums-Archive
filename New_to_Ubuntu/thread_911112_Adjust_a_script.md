---
title: "Adjust a script?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by sdim on 2008-09-05
> #!/bin/bash

##########################################################################
# Send To
##########################################################################
#                                                                        #
# Created by Mattia Galati (Adaron)                                      #
# first improvement and translation by Christopher Bratusek (Chrispy)    #
#                                                                        #
##########################################################################
# Language Settings ---------------------------------------------------- #
destination='Choose Destination'
title_destination='Send files to:'

copy='Copying'
title_copy='Please wait...'

success='Files successfully copied'
title_success='Success'

errors='Something went wrong'
title_errors='Error'

no_writable='Destination is either not existant or writable'
title_no_writable='Error'
# End of language settings ----------------------------------------------#
##########################################################################

devices=`ls -m /media/`
vv=${devices//cdrom?, /}
vd=${vv//cdrom, /}
options=${vd//, / FALSE /media/}
destinazione=`zenity --list --title "$title_destination" --text "$destination" --radiolist --column " " --column "Device" FALSE /media/$options`

if [[ "$destinazione" = "" ]]; then
    exit
fi

if [[ -w $destinazione ]]; then
	cp -R $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS $destinazione | zenity --progress --pulsate --auto-close --title="$title_copy" --text="$copy"
	if (( $? == 0 )); then
		zenity --info --text="$success" --title "$title_success";
	else	zenity --info --text="$errors" --title "$title_errors";
	fi
else	zenity --info --text="$no_writable" --title "$title_no_writable";
fi
This is a script Isomeone suggested for Moving things To other media (probably,removable media).
I'm interested in a script that Moves sth To other directories.
Does anyone know how to change/adjust the script above so as to accomplish just that?
Thank you.

---

### Post by anotherdisciple on 2008-09-05
Is there anywhere in particular that you would want to move files? ex) In your removable media in a folder called "Media"?

If you just want to be able to move it anywhere... I think it would be easier to just right-click the file(s), choose "Cut", and "Paste" it wherever you want it to go.

---

### Post by anotherdisciple on 2008-09-05
This stuff is super fun to learn if you are a geek like me. I'm just now learning it, so I can break it down a little for you...

```
#!/bin/bash
```
This is a shebang line. It says "I'm a BASH SHELL script, so interpret what I'm writing from BASH"

```
################################################## ########################
# Send To
################################################## ########################
# #
# Created by Mattia Galati (Adaron) #
# first improvement and translation by Christopher Bratusek (Chrispy) #
# #
################################################## ########################

```
This part has a "#" before every line... that means it is commented out. Lines that are commented out don't perform a task, they are just there for information usually. The creator is telling you who he is and what the name of the script is.


```
# Language Settings ---------------------------------------------------- #
destination='Choose Destination'
title_destination='Send files to:'

copy='Copying'
title_copy='Please wait...'

success='Files successfully copied'
title_success='Success'

errors='Something went wrong'
title_errors='Error'

no_writable='Destination is either not existant or writable'
title_no_writable='Error'
# End of language settings ----------------------------------------------#
################################################## ########################
```
If you know that you are going to use a sentence or something many times in a script, you can set a variable for it. Like above.  Instead of having to say "Something went wrong" he can just put a "$" in front of that variable... so now he only has to say "$errors". Does that make sense?

```
devices=`ls -m /media/`
vv=${devices//cdrom?, /}
vd=${vv//cdrom, /}
options=${vd//, / FALSE /media/}
destinazione=`zenity --list --title "$title_destination" --text "$destination" --radiolist --column " " --column "Device" FALSE /media/$options`
```
This is the same idea... he is saying... if I say $vv, I mean devices//cdrom?, /


I'll explain the if part and the zenity part if you are interested.

---

### Post by sdim on 2008-09-05
Referring to your previous question:Yes,I know that,but sometimes a Move To command would be useful,in that,I wouldn't have to open the target file to paste it in.You might say that it's a remnant of my Windows experience...:rolleyes:

---

### Post by sdim on 2008-09-05
Superb!
Yes,please,I would be very interested in learning,if it's no trouble for you.
Could we possibly adjust some *_media_* entries and change them to sth else,so as to achieve our goal?

---

### Post by anotherdisciple on 2008-09-05
Yep,  What would you like to change them to?

Also, if you know EXACTLY where you want the files to go... we could make a dialog box that asks "Where would you like to put this?"

and all you would have to type is something like /home/yourusername/Music or wherever you would like to put it... but that may be too complicated... I'll see if there is an easier way. I may have to work on it later tonight though... I can help you with all the simple parts of learning BASH tonight also. Is that good for you, or do you need the help pretty quick?

---

### Post by gvartser on 2008-09-05
This is a little example on how to move and copy files using a script.
/g

```
#!/bin/bash
#
# ScriptInfo:
# -----------
#    This script moves or copies all files from source to target dir.
#

#######################
# Functions:
#----------------------

Menu(){
        Options="copy move"
        PS3="Choose from the list above: "
        select selection in $(echo ${Options})
        do
                if [ "${selection}" ]
                then
                case ${selection} in
                copy)
                        echo "Copying contets of ${srcP} to ${trgP}"
                        cp -v ${srcP}/* ${trgP}/
                        ;;
                move)
                        echo "Moving contets of ${srcP} to ${trgP}"
                        mv -v ${srcP}/* ${trgP}/
                        ;;
                *)
                        echo "Invalid option!"
                        ;;
                esac
                break
                else
                        echo "Invalid option"
                fi
done
}

#######################
# Script Starts here:
#----------------------
printf "Enter Source path: ";read srcP
printf "Enter Target path: ";read trgP
if [ -d "${srcP}" ]
then
       export srcP
else
       echo "SRC Directory: ${srcP} does not exist!"
       exit 100
fi

if [ -d "${trgP}" ]
then
       export trgP
else
       echo "TARGET Directory: ${trgP} does not exist!"
       exit 100
fi

if [ "${srcP}" = "${trgP}" ]
then
       echo "SRC and TARGET directories can not be the same!"
       exit 100
fi
Menu

```

---

### Post by anotherdisciple on 2008-09-05
In the mean time... definitely read "Terminal For Beginners" here.... [http://ubuntuforums.org/showthread.php?t=73885]("http://ubuntuforums.org/showthread.php?t=73885")

Kyral does a GREAT job of explaining the basics of the terminal, and that will be a good head start to learning what you can do in BASH scripts.

---

### Post by gvartser on 2008-09-05
Another example but this time using some gui to it.

/g

```
#!/bin/bash
#
#

srcP=$(zenity --file-selection --directory --title "Select source directory")
if [ "${?}" = "0" ];then
        export srcP="${srcP}"
else
        exit 100
fi

trgP=$(zenity --file-selection --directory --title "Select target directory")
if [ "${?}" = "0" ];then
        export srcP="${srcP}"
else
        exit 100
fi

if [ "${srcP}" = "${trgP}" ];then
        zenity --error --text="Oops! you are not allowed to copy stuff into the same folder!" --title="Copy files script!"
        exit 100
fi

TASK="$(zenity --list --text="Select task:" --radiolist --column "Select:" --column "Task" cp "Copy" mv "Move")"
if [ "${?}" = "0" ];then
        case ${TASK} in
                Copy)
                        Ohh="copy"
                        cp -v ${srcP}/* ${trgP}/* | zenity --progress --title="File Copy Progress" --text="Copying all files: ${srcP} to ${trgP}" --auto-kill
                        ;;
                Move)
                        Ohh="move"
                        mv -v ${srcP}/* ${trgP}/* | zenity --progress --title="Moving file in Progress" --text="Moving all files: ${srcP} to ${trgP}" --auto-kill
                        ;;
        esac
fi

zenity --info --text="File ${Ohh} complete!" --title="File ${Ohh} script"

```

---

### Post by anotherdisciple on 2008-09-05
Gvartser's second example is probably closer to what you want... I'll test it out tonight.

---

### Post by sdim on 2008-09-05
I can't thank you enough,guys...
Your help and the time you devoted to answering me is appreciated.
_*To  anotherdisciple*_: I'll be away for 2-3 days,so we'll talk on Tuesday.
Whatever you can educate me with,is more than welcome.Many thanks.
_*To gvartser*_: Many thanks for your invaluable help.I tried the first script you suggested,but nothing happened.
I probably didn't do sth right (I made it executable).
As regards the second one,the GUI came on and made the choices,but again nothing happened.

---

### Post by elmoosecapitan on 2008-09-05
Very helpful: [http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)

---

