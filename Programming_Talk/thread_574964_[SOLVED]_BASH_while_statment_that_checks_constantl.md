---
title: "[SOLVED] BASH: while statment that checks constantly?..."
date: 2007-10-13
forum: Programming Talk
---

### Post by ryanVickers on 2007-10-13
I have a script and runs inside one big big while loop, and it is constantly popping up dialogs that ask a question.  The user then inputs data using it, and can click OK or Cancel.  That's the catch - the OK outputs "0" to the variable "$?", and Cancel outputs "1" to it.  The while loop checks to see if the variable is one or zero, and if 0, it continues, and if one, it *should* cancel, and it does for the first question, because the while statement comes right after it, but after that it doesn't seem to be checking anymore - it just keeps continuing! :mad:

So, short version, I need awhile loop that will check it's parameters constantly... :confused:

---

### Post by zero-9376 on 2007-10-13
you should probably post your script so as to let others assist you more effectively

---

### Post by cwaldbieser on 2007-10-13
> **ryanVickers said:**
> I have a script and runs inside one big big while loop, and it is constantly popping up dialogs that ask a question.  The user then inputs data using it, and can click OK or Cancel.  That's the catch - the OK outputs "0" to the variable "$?", and Cancel outputs "1" to it.  The while loop checks to see if the variable is one or zero, and if 0, it continues, and if one, it *should* cancel, and it does for the first question, because the while statement comes right after it, but after that it doesn't seem to be checking anymore - it just keeps continuing! :mad:

So, short version, I need awhile loop that will check it's parameters constantly... :confused:
You are probably running some other command in the loop that changes the value of $?.  You ought to capture the value in another variable immediately after running your dialog command.

---

### Post by slavik on 2007-10-13
this is what you prolly have ... (pardon my C)
```

dialog()
while ($? == 0) {
//do stuff
}
```

this is what you should have
```

dialog()
while ($? == 0) {
//do stuff
dialog() #<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
}
```

---

### Post by ryanVickers on 2007-10-13
well, here's the script if anyone can see a problem - you can check my "RAR Maker" page for the working one, but the thing is I want to clean it up using while rather than the tons of 'if's ;)

```

#!/bin/bash
#version 1.9
clear
echo "========="
echo "This script was made by ryanVickers, under this license:"
echo "-You MAY download and do whatever you want to the script, under the terms below:"
echo "-You may NOT redistribute it in any way for any reason without my permission"
echo "-I reserve the right to deny support to anyone..."
echo "...running code older than the latest version!"
echo "========="

#creates command out of mkrar.sh
mkrarpath=`dirname ${0}`
if [ -f /bin/mkrar ]
then
echo "MKRAR is a command - continuing..."
else
echo "MKRAR does not appear to be installed as a command!"
echo -n "Please enter the root password to fix this: "
sudo cp $mkrarpath/mkrar.sh /bin/mkrar
sudo chmod a=rwx /bin/mkrar >/dev/null 2>&1
echo "Done!"
fi
echo "---------------------------------------------------"

#version notifier
echo "mkrar version 1.9 - up and running!"
echo "---------------------------------------------------"

#check to see if all required sub-apps are installed
echo "Please wait - Examining system..."

if [ -f /bin/bash ]
then
echo "BASH is installed - continuing..."
else
echo "BASH does not appear to be installed!  It is needed for this script to function."
echo -n "Install BASH now? (y/n): "
read install
    if [ $install == "y" ]
    then
    sudo apt-get install bash
    else
    echo "BASH was not installed - abandoning script..."
    sleep 2
    exit 0
    fi
fi

if [ -f /usr/bin/rar ]
then
echo "RAR is installed - continuing..."
else
echo "RAR does not appear to be installed!  It is needed for this script to function."
echo -n "Install RAR now? (y/n): "
read install
    if [ $install == "y" ]
    then
    sudo apt-get install rar
    else
    echo "RAR was not installed - abandoning script..."
    sleep 2
    exit 0
    fi
fi

if [ -f /usr/bin/unrar ]
then
echo "UNRAR is installed - continuing..."
else
echo "UNRAR does not appear to be installed!  It is not absolutely necessary,"
echo "but you will need it if you want to read the archives you make with RAR."
echo -n "Install UNRAR now? (y/n): "
read install
    if [ $install == "y" ]
    then
    sudo apt-get install unrar
    else
    echo "UNRAR was not installed - continuing..."
    sleep 1
    echo "It is not needed for now, but you will need it if you want to read the archives!"
    sleep 5
    fi
fi

if [ -f /usr/bin/zenity ]
then
echo "Zenity is installed - continuing..."
else
echo "Zenity does not appear to be installed!  It is needed for this script to function."
echo -n "Install zenity now? (y/n): "
read install
    if [ $install == "y" ]
    then
    sudo apt-get install zenity
    else
    echo "Zenity was not installed - abandoning script..."
    sleep 2
    exit 0
    fi
fi
echo "System meets requirements - starting script..."
echo

#actual script
echo "==============================================================================="
echo "=    If you notice any text appearing here before you're done configuring,    ="
echo "= Stop and try again.  There was an error - You managed to break it some how! ="
echo "==============================================================================="
zenity --info --title "Graphical RAR Maker Info:" --text "At anytime, or now, if you wish to exit, simply close the terminal, or click cancel on one of the dialogs.  Of course, if this is done in the middle of the archiving process, there is a chance that the already completed archives will be useless or corrupt.";

opt=$(zenity --list --title "Pick Some Options" --height 400 --width 400 --text "Please choose the desired options to use.  Note: Picking lowercase AND uppercase is dumb!" --checklist  --column "Pick" --column "Options" FALSE "Lock_Archive" FALSE "Test_Archive" FALSE "Delete_Original_Files_After_Archiving_is_Done" FALSE "Do_Not_Add_Empty_Directories" FALSE "Convert_Filenames_to_Lowercase" FALSE "Convert_Filenames_to_Uppercase" --separator=":");

while [ "$?" -eq "0" ]; do

opt=$opt"0"

if [[ $opt =~ "Lock_Archive" ]]
then
runopt=$runopt"-k "
else
runopt=$runopt
fi

if [[ $opt =~ "Test_Archive" ]]
then
runopt=$runopt"-t "
else
runopt=$runopt
fi

if [[ $opt =~ "Delete_Original_Files_After_Archiving_is_Done" ]]
then
runopt=$runopt"-df "
else
runopt=$runopt
fi

if [[ $opt =~ "Do_Not_Add_Empty_Directories" ]]
then
runopt=$runopt"-ed "
else
runopt=$runopt
fi

if [[ $opt =~ "Convert_Filenames_to_Lowercase" ]]
then
runopt=$runopt"-cl "
else
runopt=$runopt
fi

if [[ $opt =~ "Convert_Filenames_to_Uppercase" ]]
then
runopt=$runopt"-cu "
else
runopt=$runopt
fi

if [ $opt == "0" ]
then
runopt=""
else
runopt=$runopt
fi
    comp=$(zenity --scale --title "Set the Compression Level" --text "Please choose the compression level to use (0 = none, 3 = default, 5 = maximum)" --min-value=0 --max-value=5 --value=3 --step 1);

        pri=$(zenity --scale --title "Set the Priority" --text "Please choose the priority of the archiving script (0 = normal, higher # = lower priority)" --min-value=0 --max-value=19 --value=0 --step 1);

            typ=$(zenity --list --title "Set the Archive Size Units" --height 300 --text "Please choose the units that will be used (ex. 50 MB or 2 GB)" --radiolist  --column "Pick" --column "Units" FALSE "Gigabyte(s)" TRUE "Megabyte(s)" FALSE "Kilobyte(s)" FALSE "NO-Splitting");

                if [ $typ == "Gigabyte(s)" ]
                then
                size="4"

                elif [ $typ == "Megabyte(s)" ]
                then
                size="100"

                elif [ $typ == "Kilobyte(s)" ]
                then
                size="750"

                elif [ $typ == "NO-Splitting" ]
                then
                size=""

                else
                zenity --error --title "Failure" --text "Something went wrong!  Perhaps there was a script error...  Sorry for any inconvenience!"
                exit 1
                fi
if [ $typ == "NO-Splitting" ]
then
runsize="999999999999999999999999999"
else


                size=$(zenity --entry --title "Set the Archive Size" --text "Please enter the maximum size for the archive (in "$typ") (will split to this size if necessary):" --entry-text $size);
                    if [ $typ == "Gigabyte(s)" ]
                    then
                    runsize=$((size*1024*1024))
                    
                    elif [ $typ == "Megabyte(s)" ]
                    then
                    runsize=$((size*1024))

                    elif [ $typ == "Kilobyte(s)" ]
                    then
                    runsize=$((size*1))

                    else
                    zenity --error --title "Failure" --text "Something went wrong!  Perhaps there was a script error...  Sorry for any inconvenience!"
                    exit 1
                    fi
                    runsize=$(($runsize*1024/1000))
fi
wherelist=$HOME" "$HOME"/Desktop /home /"

                    where=$(zenity --entry --title "Pick the File/Folder Location" --width 400 --text "Where is the file/folder you wish to archive?" --entry-text $wherelist);
                checkA=5
                    while [ $checkA == 5 ]; do
                        if [ -d $where ]
                        then
                        zenity --info --text "Location exists - continuing..."
                    checkA=4
                        else
                        zenity --info --text "Location does not appear to exist, or is not a folder! - Please try again..."
                    where=$(zenity --entry --title "Pick the File/Folder Location again" --width 400 --text "Where is the file/folder you wish to archive?" --entry-text $where);
                            if [ "$?" -eq "1" ]
                            then
                            exit 0
                            fi
                        fi
                    done




cd $where
list=$(ls -w 1)


                        folder=$(zenity --entry --title "Pick the File/Folder to Archive" --width 400 --text "What is the folder/file you wish to archive called?" --entry-text $list);
                    checkB=5
                        while [ $checkB == 5 ]; do
                            if [ -e $where/$folder ]
                            then
                            zenity --info --text "Location exists - continuing..."
                        checkB=4
                            else
                            zenity --info --text "Location does not appear to exist! - Please try again..."
                        folder=$(zenity --entry --title "Pick the File/Folder to Archive again" --width 400 --text "What is the folder/file you wish to archive called?" --entry-text $folder);
                                if [ "$?" -eq "1" ]
                                then
                                exit 0
                                fi
                            fi
                            done

    

                            name=$(zenity --entry --title "Pick the Archive Name(s)" --width 600 --text "What should we call the archive(s)?" --entry-text $folder"-splitRAR-"$size$typ);

                                cd $where
                                zenity --info --title "Please Note:" --text "This may take several minutes depending on the selected compression level, quantity of, and size of, the files"

                                zenity --question --title "Archive Preferences Confirmation" --text "So, you want to make a RAR of the folder/file called '"$folder"', put it in "$where", call the archive(s) '"$name"', split them (if necessary) into "$size$typ" pieces, run the script with a nice value of "$pri" and compress the archive to a level of "$comp"?"

                                    nice -n $pri rar a $runopt-m$comp -v$runsize"K" $name.rar $folder
                                    zenity --info --title "Done!" --text "Archiving complete!  You can find the archive(s) "$name" in "$where"!";
                                    exit 0
done
zenity --error --title "Failure!" --text "Archiving canceled - Aborting mkrar..."
exit 0

```

I may think about changing the license, but for now, I still want to hold on to it ;)

---

### Post by cwaldbieser on 2007-10-13
It is somewhat hard to follow due to the indentation, but it seems like your last command before the main "done" of the while loop is a "zenity --error" dialog.  That always has an exit value of 0, so your while loop should loop indefinitely.

Forgive me if you already know this, but I think you may just be thiking that the "zenity --question" dialog sets the variable "$?".  This is actually a shell variable that always contains the exit status of the last command issued.  That is why you need to do something like:

```

LOOP_FLAG=0
while [ $LOOP_FLAG -eq 0 ]; do
    ...
    zenity --question "Loop again?"
    LOOP_FLAG=$?
    ...
done

```

---

### Post by ryanVickers on 2007-10-13
well, I just know that when the boxes exit, it gives that value a 1 or 0, and before, I had the whole script inside of if statements (one for every dialog) and a ton of else and exit 0 at the end, and it worked, but this is better (if I can get it working ;))

---

### Post by ryanVickers on 2007-10-13
what you've got there didn't quite make sense at first, but it gave me an idea that worked! :) :) :)

---

