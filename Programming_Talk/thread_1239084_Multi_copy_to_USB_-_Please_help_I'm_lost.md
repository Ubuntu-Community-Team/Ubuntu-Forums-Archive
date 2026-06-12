---
title: "Multi copy to USB - Please help I'm lost"
date: 2009-08-13
forum: Programming Talk
---

### Post by KiwiTheSwede on 2009-08-13
Hello all so my first post becomes a cry for help 
I'm pretty new to ubuntu and not that common to the filestructure and libraries so please forgive me if this turns out to be a noob question. 

I'm working on a small bash script to copy files from one location to all removable drives attached to the computer. Originally I did a bat for Windows however since windows are limited to attach units above z without too much hassel on the system I decided to do this on Ubuntu instead. 
Here's the code that I got in bat:
[php]::COPY FILES 
@echo off & setlocal enabledelayedexpansion 
echo ************************************** 
echo ******* Initiating program *********** 
echo ************************************** 
echo This will copy all files from this directory to all removable drives 
pause 
 
for /f "tokens=1,2 delims=\" %%a in ('fsutil fsinfo drives^|more/e/t0') do ( 
    if "%%b"=="" (set drive=%%a) else (set drive=%%b) 
    fsutil fsinfo drivetype !drive!|find "Removable Drive">nul 2>&0 &&xcopy *.* !drive!\ /Y /EXCLUDE:myXcludes 
) 
echo ************************************** 
echo ******** Copying complete ************ 
echo ************************************** 
pause[/php]So far I've managed to find and loop through devices attached to the computer and filter out removable drives though I'm not able to access the drive/ find mounting point (read, write a.s.o) . 
Here's what I've got so far:
[php]
#!/bin/bash

for DRIVES in /sys/block/sd*
do
    if readlink $DRIVES | grep -q usb
    then
        NAME=`basename $DRIVES`
        echo Copying files to $NAME
        #copy code comes here

    fi
done


exit 0
[/php]I've tried looping through the devices listed in media but I haven't found a way to filter out the drives also it seems as I find ghost dirs from previously attached drives that Ubuntu forgot to delete. 
Can anyone point me in the right direction please?

---

### Post by prshah on 2009-08-13
> **KiwiTheSwede said:**
> I've tried looping through the devices listed in media but I haven't found a way to filter out the drives

You can find all currently attached USB drives by ```
ls -l /dev/disk/by-id/usb*
```

---

### Post by KiwiTheSwede on 2009-08-13
Thanks alot for answering prshah :)

But that only gives me yet another method to list removable drives though not the actual mounting point sorry for being unclear in my orginal question. 

Or am I missing something?

---

### Post by prshah on 2009-08-13
> **KiwiTheSwede said:**
> 
But that only gives me yet another method to list removable drives though not the actual mounting point

To get the actual mount points of the removable devices, try```
mount|grep hal
``` This works since hal handles the auto-mounting of usb devices. Unfortunately, this means that manually mounted devices will not show up with this command.

If you don't mind a little inconvenience, the earlier solution can be adapted to this. The by-id path is a symlink to the device in use (eg, sdb). Find the actual device (by dereferencing the symlink, or analysing the ls -l output), then grep mount to show the mountpoint for the given device.

Post back if you need clarifications.

---

### Post by KiwiTheSwede on 2009-08-13
Thanks again!!

So after playing around a little with this I'm getting this output 
[php]
$ mount|grep sdb1
/dev/sdb1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)[/php]Which means that with a little string manipulation I should be able to extract the path I need. Correct?

Or this there a better way?

---

### Post by KiwiTheSwede on 2009-08-15
So after playing around I've come up with this:
[PHP]
#!/bin/bash
echo "This will copy all files in directory to all removable drives attached to this computer"
read -n1 -r -p "Press any key to continue..." key 
echo
echo
for DRIVES in /sys/block/sd*
do
    if readlink $DRIVES | grep -q usb
    then
        NAME=`basename $DRIVES`
     DRIVE=`mount|grep $NAME`
    INFO=`expr "$DRIVE" : '.*\(/media/.*\).* type'`
    echo Copying files to $INFO
    DIR=`echo ${INFO/ /\\ }`
    cp *.pdf "$DIR"
    echo Done
    echo

    fi
done
echo "Copying complete"
read -n1 -r -p "Press any key to exit" key

exit 0 
[/PHP]
It still feels a little bit like a hack but it will work for me for now at least.
Thanks again prshah for pointing me in the right direction

---

