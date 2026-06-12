---
title: "Have an issue with my bash script"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2012-07-09
Hi all,

Now my problem is with a bash script which I managed to cook up with the help of angry_jhonny. The script runs but says permission denied when I give the device path then after the second function it exits.

The bash file is listed below.

```
#!/bin/bash
device=$(zenity --entry --text "Enter USB Device Number?")

if $device
then
exit 0
fi

volname=$(zenity --entry --text "What is the volume name?")

if $voname
then
exit 0
fi

volid=$(zenity --entry --text "What is the volume id?")

if $volid
then
exit 0
fi

sourc=$(zenity --entry --text "Where are the files?")

if $source
then
exit 0
fi

if ! $(zenity --question --no-wrap --text "Are there More files .....")
then


sudo umount $device
sudo mkdosfs -F32 -n $volname -i $volid $device
mkdir /media/$volname
mount $device /media/$volname
cd TNavi/PND_Versions/CE-No-inet
cp -v -r $source /media/$volname
umount $device
rm -r /media/$volname

exit 0

else
source2=$(zenity --entry --text "Where are the extra files?")
if $source2
then
exit 0
fi

umount $device
rm -r /media/$name
umount /dev/$device
mkdosfs -F32 -n $volname -i $volid $device
mkdir /media/$volname
mount $device /media/$volname
cd TNavi/PND_Versions/CE-No-inet
cp -v -r $source $source2 /media/$volname
umount $device
rm -r /media/$volname

exit 0

fi

```

Can any one help with this. And also at the device parameter if I put it like this "/dev/$device" then it doesn't work it works only like this "$device". But even after taking that it stops working at the second command. Also it says permission denied please help me to get it working.

---

### Post by papibe on 2012-07-09
Hi sadaruwan12.

You have some lines that use 'sudo' and some that don't. 

My first guess is you are missing a sudo somewhere. 

If I were you, I would remove all sudos and call the script using sudo:
```
sudo myscript
```

Just a thought.
Regards.

---

### Post by sadaruwan12 on 2012-07-09
No luck tried it this is what I get,

```
./SDCreator.sh: line 4: /dev/sdb1: Permission denied

```

---

### Post by papibe on 2012-07-09
If you want to check if a variable is unset or empty use this syntax:
```
if [ -z "$device" ]
then
    exit 0
fi
```
Regards.

---

### Post by sadaruwan12 on 2012-07-09
Nope No luck

---

### Post by steeldriver on 2012-07-09
You have one obvious typo

> **sadaruwan12 said:**
> 
**volname**=$(zenity --entry --text "What is the volume name?")

if $**voname**
then
exit 0
fi
[/CODE]

Also as papibe mentioned your tests don't really make sense - what are you inputing here?

> **sadaruwan12 said:**
> 
```
#!/bin/bash
device=$(zenity --entry --text "Enter USB Device Number?")

if $device
then
exit 0
fi

```

If you are trying to test for the existance of block device /dev/sdb1 for example, you would want something like 

```
 if [ -b "$device" ]
```or if you are inputing just the 'sdb1' part,

```
 if [ -b "/dev/$device" ]
```

You would need to do something similar for the volume directory - see here for a full list of file test operators:

[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)

---

### Post by sadaruwan12 on 2012-07-10
> #!/bin/bash
device=$(zenity --entry --text "Enter USB Device Number?")

That to insert my USB port where my SD Card reader is at. But my problem is why it's not working even I'm running the script with sudo.

---

### Post by jlgp on 2012-07-10
on a terminal session do:

ls -l /dev/sdb1

---

### Post by asmoore82 on 2012-07-10
Quotation marks (") are Bash scripts' best friends :D.

---

### Post by sadaruwan12 on 2012-07-12
Can some plese help me with this script.

---

### Post by steeldriver on 2012-07-12
Several of us have tried to help -  it is hard to give you more specific advice until you explain exactly what you are trying to do

How about you COMMENT your script  explaining what each block does and what inputs you expect? Then we can take a look - something like:

```

# get target USB device in the form 'sdXn'
device=$(zenity --entry --text "Enter USB Device Number?")  

# test if $device is present on the system (via /dev/sdX)
if [ -b "/dev/$device" ]
.
.
.

```

---

### Post by sadaruwan12 on 2012-07-19
> **steeldriver said:**
> Several of us have tried to help -  it is hard to give you more specific advice until you explain exactly what you are trying to do

How about you COMMENT your script  explaining what each block does and what inputs you expect? Then we can take a look - something like:

```

# get target USB device in the form 'sdXn'
device=$(zenity --entry --text "Enter USB Device Number?")  

# test if $device is present on the system (via /dev/sdX)
if [ -b "/dev/$device" ]
.
.
.

```

OK I'll do that

---

### Post by sadaruwan12 on 2012-07-19
```
#!/bin/bash

# To specify the device /dev/sdb1 or /dev/sdc1
device=$(zenity --entry --text "Enter USB Device Number?")

if [ -z "$device" ]
then
    exit 0
fi

#I use a number to name the SD card the number looks like this CGSLK0393 and this changes from
#Card to card 
volname=$(zenity --entry --text "What is the volume name?")

if $volname
then
exit 0
fi

#I use the final three numbers of the above name to give the SD cards Volume ID
volid=$(zenity --entry --text "What is the volume id?")

if $volid
then
exit 0
fi

#This is to give the files but this path
#/home/user/TNavi/PND_Versions/CE-No-inet hardly changes the last directory does
# Which comes after the /CE-No-inet
sourc=$(zenity --entry --text "Where are the files?")

if $source
then
exit 0
fi

#Ask if I have more files or folder to add
if ! $(zenity --question --no-wrap --text "Are there More files .....")
then

#this will be carried out only if on source folder is given
umount $device # unmount the device after gatting the path from above command
mkdosfs -F32 -n $volname -i $volid $device #Creats the file system
mkdir /media/$volname #Creat a new Dir in the /media folder
mount $device /media/$volname # mounts the formated SD
cd TNavi/PND_Versions/CE-No-inet #Goes in to the folder
cp -v -r $source /media/$volname # copy the folder
umount $device #unmount the device
rm -r /media/$volname #delete the folder in /media

exit 0

#This is to give another directory to the cp command
#So the command will be like cp -v -r source1 source2 Destination
#This will be used only if needed
else
source2=$(zenity --entry --text "Where are the extra files?")
if $source2
then
exit 0
fi

umount $device
rm -r /media/$name
umount /dev/$device
mkdosfs -F32 -n $volname -i $volid $device
mkdir /media/$volname
mount $device /media/$volname
cd TNavi/PND_Versions/CE-No-inet
cp -v -r $source $source2 /media/$volname
umount $device
rm -r /media/$volname

exit 0

fi

```

Here you go with comments what I want to by each command please help.

---

### Post by anewguy on 2012-07-19
I'm still looking through the script, but while I'm doing that you also have another typo you can fix in the meantime:

sourc=$(zenity --entry --text "Where are the files?")

---

### Post by anewguy on 2012-07-19
You first "if" checks on a null value, but your next 2 (volname and volid) don't - you might need to change that:

if $volname

perhaps should be 

if [-z "$volname"]

same on the if for volid....

seems that pretty much just says "exit here"

maybe you intended it the way it is, I don't know...


Have you run any kind of tracing with this to see where any of the problems start?  I would add echo statements before and after each section to a log file (remember > on first, >> thereafter) to see where the problems are coming in.

Still not to the super user things

---

### Post by sadaruwan12 on 2012-07-19
Thx anewguy my original script is like this,

```
#!/bin/bash

# To specify the device /dev/sdb1 or /dev/sdc1
device=$(zenity --entry --text "Enter USB Device Number?")

if $device
then
exit 0
fi

#I use a number to name the SD card the number looks like this CGSLK0393 and this changes from
#Card to card 
volname=$(zenity --entry --text "What is the volume name?")

if $volname
then
exit 0
fi

#I use the final three numbers of the above name to give the SD cards Volume ID
volid=$(zenity --entry --text "What is the volume id?")

if $volid
then
exit 0
fi

#This is to give the files but this path
#/home/user/TNavi/PND_Versions/CE-No-inet hardly changes the last directory does
# Which comes after the /CE-No-inet
source=$(zenity --entry --text "Where are the files?")

if $source
then
exit 0
fi

#Ask if I have more files or folder to add
if ! $(zenity --question --no-wrap --text "Are there More files .....")
then

#this will be carried out only if on source folder is given
umount $device # unmount the device after getting the path from above command
mkdosfs -F32 -n $volname -i $volid $device #Creats the file system
mkdir /media/$volname #Creat a new Dir in the /media folder
mount $device /media/$volname # mounts the formated SD
cd TNavi/PND_Versions/CE-No-inet #Goes in to the folder
cp -v -r $source /media/$volname # copy the folder
umount $device #unmount the device
rm -r /media/$volname #delete the folder in /media

exit 0

#This is to give another directory to the cp command
#So the command will be like cp -v -r source1 source2 Destination
#This will be used only if needed
else
source2=$(zenity --entry --text "Where are the extra files?")
if $source2
then
exit 0
fi

umount $device
rm -r /media/$name
umount /dev/$device
mkdosfs -F32 -n $volname -i $volid $device
mkdir /media/$volname
mount $device /media/$volname
cd TNavi/PND_Versions/CE-No-inet
cp -v -r $source $source2 /media/$volname
umount $device
rm -r /media/$volname

exit 0

fi
```

That was a mistake I was checking it but this is my my original script. My issues when it comes to the latter part it says "No Permission" even if I was running it with sudo.

---

### Post by anewguy on 2012-07-19
Do you know exactly where it fails?  If you don't know the exact statement, do like I mentioned and put in some echo statements to create a log file - I'd do this after each command starting at your first unmount.

Also, given that you know via terminal what these id's are, try the steps manually at the command line and see if it gives any additional information when it fails.

---

