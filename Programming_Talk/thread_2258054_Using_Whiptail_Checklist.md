---
title: "Using Whiptail Checklist"
date: 2014-12-24
forum: Programming Talk
---

### Post by shubhamjindal-1994 on 2014-12-24
I use Ubuntu 14.04.01, and I wanted to build an interactive program for mounting and unmounting my other hard drive partitions. The checklist option of whiptail will provided options for the available partions to be mounted, like /dev/sda6. and using a switch case the mount and unmount command can be executed. Also a guage option in whiptail will show the progress(0-100%). How can this be done? From googling, I could come up with this code only.

#!/bin/bash


function firstroutine {
 echo "running johns function"
}


function secondroutine {
 echo "running glens function"
}




function thirdroutine {
 echo "running adams function"
}


whiptail --title "Test" --checklist --separate-output "Choose:" 20 78 15 \
"John" "" on \
"Glen" "" off \
"Adam" "" off 2>results


while read choice
do
        case $choice in
                John) firstroutine
                ;;
                Glen) secondroutine
                ;;
                Adam) thirdroutine
                ;;
                *)
                ;;
        esac
done < results

---

### Post by grahammechanical on 2014-12-24
Whiptail is default installed in Ubuntu because it is used to draw the Recovery mode menu and react to user input and run scripts that have commands in the scripts. For example, if when at the recovery menu we select Clean, a script will run that in turn will run the apt-get commands of "clean" and "autoremove."

You can find these recovery mode scripts at /lib/recovery-mode/. You may be able to re-used parts of those scripts to get your script calling whiptail. More than this I cannot add. Except,

[http://en.wikibooks.org/wiki/Bash_Shell_Scripting/Whiptail](http://en.wikibooks.org/wiki/Bash_Shell_Scripting/Whiptail)

[http://www.techrepublic.com/blog/linux-and-open-source/how-to-use-whiptail-to-write-interactive-shell-scripts/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-use-whiptail-to-write-interactive-shell-scripts/)

Regards.

---

### Post by shubhamjindal-1994 on 2014-12-24
Thanx grahammechanical, 
I have done most of the work already. I was working on the scripts and i made some changes to it. Here is the full script. THESE WILL NOT WORK. You need to change the corresponding folders and partitions

#!/bin/bash


function mounting {
	sudo mkdir /media/jindal/Jindal
	sudo mkdir /media/jindal/Cdrive
	sudo mount -o ro /dev/sda6 /media/jindal/Jindal
	sudo mount -o ro /dev/sda4 /media/jindal/Cdrive
}


function unmounting {
	sudo umount /dev/sda6
	sudo umount /dev/sda4
	sudo rmdir /media/jindal/Jindal
	sudo rmdir /media/jindal/Cdrive
}


function gauge {
	{
    for ((i = 0 ; i <= 100 ; i+=1)) do
        sleep 0.02
        echo $i
    done
} | whiptail --gauge "Please wait while mounting..." 6 50 0
}




whiptail --title "Mount/Unmount partitions" --checklist --separate-output "Choose:" 20 78 15 \
"Mount" "Jindal and C-Drive will be mounted" on \
"Unmount" "Jindal and C-Drive will be unmounted  " off \
"Gauge" "100% gauge" off 2>results


while read choice
do
        case $choice in
                Mount) mounting
                ;;
                Unmount) unmounting
                ;;
                Gauge) gauge
                ;;
                *) echo "Default case"
                ;;
        esac
done < results

---

### Post by oldos2er on 2014-12-24
Moved to Programming Talk.

---

### Post by schragge on 2014-12-24
> THESE WILL NOT WORK
The code you posted works just fine. You probably want to say it does not work the way you intended it to work. What's your problem? How to get the  list of available partitions? There are many ways, some examples:
```
lsblk -lnoname,state
``````
findmnt -lnosource,target  -tvfat,ntfs
``````
blkid -odevice
``````
sudo parted -lm|awk  -F: '/^\//{print$1}'
``` There's also  [partx]("http://manpages.ubuntu.com/manpages/trusty/en/man8/partx.8.html"),   [findfs]("http://manpages.ubuntu.com/manpages/trusty/en/man8/findfs.8.html"),  and so on. Compare the options and choose the tool that fits your needs  best. Some of them allow filtering on labels/UUIDs, or on filesystem  type.

You probably should have used radiolist instead of checkbox, as selecting "Mount" and "Unmount" simultaneously makes no sense. Although selecting "Mount"/"Unmount" through radiolist makes little sense, too. It could be just a button as well.

Or you should present the choices in completely different way, where each item corresponds to a partition that has to be mounted/unmounted.

 And in my experience, mounting/unmounting operations are nearly instant, so I do not see the need for them to be gauged. Besides, your gauge function doesn't really gauge these operations. It gets invoked **after** the mounting/unmounting already done if user chooses to check the corresponding item "Gauge". As is, this function has no sense whatsoever.

---

### Post by shubhamjindal-1994 on 2014-12-24
Thanx schragge,
1. I know how to list available partitions. I just wanted the process to be in a flow...
2. I know, and I am using whiptail for the first time, I was going to change it to radiobuttons and with separate partitions...
3. I also know the operations are instant and don't needed to be gauged...i just wanted to see how can i embed it in a script for other uses later...
What I don't know,
1. How can I put the gauge function so that it works with mounting operation...or any function which takes time...
2.when a user runs the script, i wanted this to happen...first, the user clicks on mount or unmount radio button...then user selects the available partiotions...and then while the operation proceeds the gauge should be shown...and then a message box that its completed....
3. the mounting and unmounting of multiple partitions can take place...so a checklist is better....yes, first user has to choose between mount and unmount...
I wanted the syntax of commands..i am new to scripting

---

