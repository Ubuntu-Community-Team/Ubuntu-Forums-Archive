---
title: "kaiwan"
date: 2007-10-29
forum: Programming Talk
---

### Post by kaiwan on 2007-10-29
Hi! I am trying to write a script which can run java program called manager.jar
from my mp3 player. My player mounts in media/disk.
I wanna check if disk is mounted and if there is file called manager.jar
If a for example change manager.jar to manager2.jar I get this error:
Unable to access jarfile manager.jar
and I wanna to get my error output ...  echo "Error: Music Manager not found!"

The code:
#!/bin/sh

cd /media



if [ -d disk ]; then 
	if [ -f $manager ]; then
		cd /media/disk &&
		java -jar manager.jar &&
		echo "Program terminated by user!"
	else
		echo "Error: Music Manager not found!"
	fi
else 
	echo "Error: Disc not mounted!"
fi  

exit 0

---

### Post by kast on 2007-10-29
Sorry a little confused on what you need here. i get the check to see that your mp3 is mounted part but lost on the rest

---

### Post by kaiwan on 2007-10-30
What I wan is to check if mp3 is mounted, and then to check if
program manager.jar (music manager) is on my mp3 player.
mp3 is mounted on media/disk

# checking is disk is mounted
if [ -d disk ]; then
# checking if there is a file called "manager" on the disk
if [ -f $manager ]; then
# is file "manager" is on the disk to this:
cd /media/disk &&
java -jar manager.jar &&
echo "Program terminated by user!"
# is there is no file "manager
else
echo "Error: Music Manager not found!"
fi
#is disk is not mounted
else
echo "Error: Disc not mounted!"
fi

exit 0

---

### Post by dwhitney67 on 2007-10-30
I don't understand either (but that is because I am sleepy and on my 5th ESB),  but I think you should examine if whether the local variable "manager" has been initialized before this statement:

```
if [ -f $manager ]; then
```

It seems to me that you want to initialize "manager", then follow up with its usage using:

```
manager=manager.jar
...
java -jar $manager
```

P.S.  When shell scripting, IMO it is always best to define in UPPERCASE all variable names; that way they stand out from the rest of the code.

---

### Post by kast on 2007-10-30
ok so you need the

** if [ -d /media/disk ]** and the** if [ -f $manager ]** to succeed (return 0) ?? then move to the cd /media/disk part?

---

