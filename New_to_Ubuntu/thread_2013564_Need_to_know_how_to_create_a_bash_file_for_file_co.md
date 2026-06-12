---
title: "Need to know how to create a bash file for file copying"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2012-07-01
Hello all !

My work requires me to format SD cards with specific number to the volume name and then copy some files in to it.

So what I currently do is run these command on the terminal one by one.

First of all get in to a the file location folder by using the "cd" command and the path is "/home/TNavi/Nointernet/".

After that I plug the SD card in and run this command.

```
$ sudo umount /dev/sdb1
```

after that I use "mkdosfs" to format and this is the command I use for that.

```
$ sudo mkdosfs -F32 -n<The Number I give> -i<My Volume ID> /dev/sdb1
```

after that I don't know how to mount the volume in to a temp location like the nautilus does it when I select the volume name from the list on to the left hand side.

All the guides have listed to create a directory then mount the volume on that but I want to do is similar to what nautilus does 'cos I dont want to keep that directory in my HDD.

Once the copying is done I use nautilus to unmount the volume and it also deletes the folder it has created I want to do that from the command line.

Now I copy the directories I want using this command,

```
$ sudo cp -v -r /<directory 1> /<directory 2> /dev/<SD card name>
```

ok thats my normal proses this is very hard when you have to select the commands one by one.

I want to put these in to a bash script so I can run them in termnal like a program until I terminate it.

Can some help me to do this I'm familiar with the terminal but not with bash scripting know little bit of programing.

Also I need to tell you that the "Volume Name", "Volume-id", "Source Folders" and the "Destination SD name" changes I need to be able to change them using the bash script. I also want to mount and dismount the volume like what nautilus does I don't want to keep the mount folder.

Can some one help me, TANKS IN ADVANCE.

---

### Post by angry_johnnie on 2012-07-01
as far as creating the directory for mounting is concerned, you could just create the directory in /tmp so it won't stay there permanently.

nautilus creates this temporary directory in /media, i think.

so, if you've given your device a name, and if you create a directory with that name, it should appear, once mounted, in /media/device.

as far as scripting goes, it's something along these lines:

```

#!/bin/bash

mkdir /media/<SD card name>
cd /home/you/directory/with/files
umount /dev/sdb1
mkdosfs -F32 -n<The Number I give> -i<My Volume ID> /dev/sdb1
mount /dev/sdb1 /media/<SD card name>
cp -v -r /<directory 1> /<directory 2> /media/<SD card name>
umount /dev/sdb1
rm -r /media/<SD card name>
```

once you have this, all you need to do is chmod a+x this script and then run it with sudo so it'll do all the things it needs to do.


now that's just a general idea.  if some of these values aren't always the same, than you can't have them hard coded in the script.  you could use variables instead.  for instance, suppose it's not always /dev/sdb1, but something else.  this can be achieved in various ways.

for example, using zenity:

```
#!/bin/bash

device=$(zenity --entry --text "where is the device located?")

if $device
then
exit 0
fi

mkdir /media/<SD card name>
cd /home/you/directory/with/files
**umount $device**
```

or, from the command line, using the 'read' command:

```
#!/bin/bash

read -p "Where is your device located?"
parameter="$REPLY"

mkdir /media/<SD card name>
cd /home/you/directory/with/files
**umount $parameter**
```

this way you can tell your script where to go each time.  it's still just a general idea, but it can be adjusted to your needs.

---

### Post by sadaruwan12 on 2012-07-01
Thank you very much for your reply angry_jhony it shed some light on what I should do.

And as changing values yes my script has changing values the volume name, volume ID, sdcard name and the source directories. the sdcard name is equal to the volume name the volume name look something like this "CGSLKxxxx". the ls three digits will change.

I just need to know how to enter a value for the volume name and for volume ID then from the volume name to create a folder in /media then select the sources like if no 1 then the sources are a and b if number 2 then a only like that. after selecting the source directories the copying will start then unmount the sd card then remove the folder in /media.

I know this is little too much but please can some one help me.

P.S: Like to know is there any way to automatically locate the SD card.

---

### Post by angry_johnnie on 2012-07-01
well, it's a bit far fetched and off the top of my head, but it would be something like the following code.  using zenity makes things a bit messy, but i like it.  it feels friendly.  there's a cancel option after every question.  other than that, it's pretty straight forward.



```
#!/bin/bash

device=$(zenity --entry --text "where is the device located?")

if $device
then
exit 0
fi

name=$(zenity --entry --text "what is the volume name?")

if $name
then
exit 0
fi

volid=$(zenity --entry --text "what is the volume id?")

if $volid
then
exit 0
fi


number=$(zenity --entry --text "what's the number?")
if $number
then
exit 0
fi


files=$(zenity --entry --text "where are the files?")

if $files
then
exit 0
fi

if ! $(zenity --question --no-wrap --text "more files?")
then

mkdir /media/$name
cd $files
umount $device
mkdosfs -F32 -n $number -i $volid $device
mount $device /media/$name
cp -v -r $files /media/$name
umount $device
rm -r /media/$name

exit 0

else
files2=$(zenity --entry --text "where are the extra files?")
if $files2
then
exit 0
fi

mkdir /media/$name
cd $files
umount $device
mkdosfs -F32 -n $number -i $volid $device
mount $device /media/$name
cp -v -r $files $files2  /media/$name
umount $device
rm -r /media/$name

exit 0

fi
```

---

### Post by sadaruwan12 on 2012-07-02
THX brother nice one this I can work with I also checked out zanity it's nice rather than going with just text thx a lot.

---

