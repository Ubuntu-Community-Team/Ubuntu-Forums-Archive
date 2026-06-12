---
title: "Zenity Progress Indicator Help"
date: 2006-05-27
forum: Programming Talk
---

### Post by OldSpiceAP on 2006-05-27
Hey all, for the last few months I've been working on and off on a script that downloads the source code of the MMORPG Game PlaneShift, as well as the source of its depencies and compiles them in order.  Its getting to be a fairly complex script, but so far all seems to be working ok.  A thread about it in their forums can be found here:

[http://hydlaa.com/smf/index.php?topic=23316.0](http://hydlaa.com/smf/index.php?topic=23316.0)

Basically its a graphical build script.  The problem I'm having is getting actual progress of things like source code downloads, and compiling.  I'm forced to use the zenity pulsating progress bar which totally sucks from an end user perspective.

The repository for the ubuntu package is found here:

deb [http://vaalnor.mine.nu/repositories/dapper/unstable](http://vaalnor.mine.nu/repositories/dapper/unstable) /

and the package is called gooeybuilder

Alternately, you can look here which is my sort of online updated source code (if you could call it that since its a script)

[http://vaalnor.mine.nu/PlaneShift%20Builder/](http://vaalnor.mine.nu/PlaneShift%20Builder/)

could someone take a look and give me some ideas on how to get real progress indication?  I could really use a hand here. The actual script is named dapper_buildscript  -   or at least thats where the magic happens.  [http://vaalnor.mine.nu/PlaneShift%20Builder/gooeybuilder.8.1_all/usr/local/GooeyBuild/dapper_buildscript](http://vaalnor.mine.nu/PlaneShift%20Builder/gooeybuilder.8.1_all/usr/local/GooeyBuild/dapper_buildscript)   <---- direct link to actual script

---

### Post by cilynx on 2006-06-06
Getting Zenity to actually use the progress bar is a PITA.  You basically have to pipe the whole freaking operation to Zenity...

```

(for x in 10 20 30 40 50 60 70 80 90 ; do echo $x ; sleep 1; done)|zenity --progress

```

That should be enough to get you started.  $x is the percentage.  The 'sleep' is just in there to make it slow enough that you can watch it.

Good Luck

---

### Post by SirMsquared on 2008-04-21
Here's a sample script I knocked up that demonstrates the progress bar - it uses SCP to copy some files to a server you designate.

You can call this script from a script or from the commandline, or you can pop this script into .gnome2/nautilus-scripts (with a name such as 'copy_to_server') to have nautilus show it as a custom script.  Nifty!

```

#!/bin/bash

REMOTE=server.yourdomain.com

# hack for items on the desktop (stupid stupid nautilus)
if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "x-nautilus-desktop:///" ] ; then
        cd ~/Desktop    # change this for your setup
fi

if [ "0" == "$#" ] ; then
        zenity --error --title="Copy files error" --text="Please select one or more files."
else
        (
                i=0
                for file in "$@" ; do
                        echo $(($i * 100 / $#))
                        i=$(($i+1))
                        scp -p "$file" $REMOTE: &>/dev/null
                done
                echo 100
        )|zenity --progress --title="Copy files progress" --text="Copying $# files to $USER@$REMOTE..." --auto-close
fi

```

---

### Post by Tapas Pain on 2008-11-01
I don't know if I should start a new thread on this, but I have a question about Zenity progress bar.  Is there a way to make it show the actual progress of a task?  I've just started learning how to program shell scripts, so I did a basic one to create a tarball, move it, and then copy another backup file.  I've seen various zenity progress scripts on the Web, and imported the ideas from them, but I can't figure out how to make Zenity show the true progress of the task.  Can anyone offer any suggesitons please?  Here is the script:

#!/bin/bash

echo "Do you want to run the backup script (y/n)?" 

read answer

if [ "$answer" = "y" -o "$answer" = "yes" -o "$answer" = "Y" -o "$answer" = "Yes" -o "$answer" = "YES" ]; then
	echo "Standby ... user files are backing up.  Finished product will be on //media/disk."

else exit

fi

(
echo "10" ; 
echo "# Compressing tarball ..." ;
cd //home/tapas
tar -czvf my_tarball.tar.gz *
echo "20" ; 
echo "# Tarball compression complete" ; 
echo "60" ; 
echo "# Moving tarball" ; 
echo "70" ; 
mv -v my_tarball.tar.gz -t //media/disk
echo "# Removing original tarball file" ; 
echo "85" ; sleep 1
echo "# Backing up personal log" ; 
echo "90" ; 
echo "# Standby ... backing up personal log."
cd //home/tapas/Documents
cp -v personal.log personal.backup
echo "# Script is finished."
echo "100" ; 
) |
zenity --width=400 --height=100 --progress --title="User Profile Backup" --text="Backing up your data now..." --percentage=0 --pulsate

        if [ "$?" = -1 ] ; then
                zenity --error \
                  --text="Update canceled."
        fi

---

