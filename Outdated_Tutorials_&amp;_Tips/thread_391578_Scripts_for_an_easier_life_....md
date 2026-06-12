---
title: "Scripts for an easier life ..."
date: 2007-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by sobira on 2007-03-23
I made some scripts that will install some stuff for edgy .. i havn't tested them yet.. but they SHOULD work ... 
I will constantly update this as new scripts are added ... 

1) to install fonts (all but ms fonts)
download
[http://download.gindis-world.org/font.tar.gz](http://download.gindis-world.org/font.tar.gz) to home folder
-click it-
extract files to home folder right click font > properties > permissions > check allow execution as program .
to run simply open a terminal and do 
```
sudo bash font

```

2)Multimedia Codecs and DVD playback :
[http://download.gindis-world.org/codec.tar.gz](http://download.gindis-world.org/codec.tar.gz)
-click it-
extract to home folder
right click codec > properties > permissions > check allow execution as program .
to run simply open a terminal and do 
```
sudo bash codec.txt

```

3) Game Pack 
will install the following games : 
Tuxracer Applications -> Games -> planetpenguin-racer
Scorched3D Applications -> Games -> Scorched 3D
Frozen-Bubble Applications -> Games -> Frozen-Bubble
netpanzer Applications-> Games -> NetPanzer   or run command 
```
netpanzer
```
[http://download.gindis-world.org/gpack.tar.gz]("http://download.gindis-world.org/gpack.tar.gz")
just click it
save in home folder ,extract it  right click gpack > properties > permissions >check allow executing file as program
and then type in terminal : 
```
sudo bash gpack
```

4) Automatix2 Install :
Note:This will replace your sources.list with the one contained in the package ... it will create a backup of your sources.list at /etc/apt/sources.list.backup , so if you want to restore your list simply do 
```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
```
Download this tar.gz to home folder [http://download.gindis-world.org/automatix-install.tar.gz](http://download.gindis-world.org/automatix-install.tar.gz)
press alt+f2 gksudo nautilus and click run , go to your home folder , copy the archive to /tmp/ and extract the files there (make sure the path to the two files contained in the package "sources.list" and "amx2" are in directory /tmp/
and then right click amx2 >properties>permission >check allow executing file as program 
the open a terminal do the code :
```
cd /tmp/
```
and then 
```
sudo bash amx2
```

automatix2 can be run with Menu -> System -> Automatix
or  command
```
automatix2
```


i hope someone finds this helpful :)

---

### Post by bruenig on 2007-03-23
1. It is probably best that you just have us run the scripts with sudo, instead of using sudo for all the commands inside the script because that way we don't have to interact with the script as it is running and put our password.

You could have the scripts check for root and then send a message to run it with sudo if it isn't there by putting this at the top of the script
```
if [ $UID -ne 0 ] ; then
     echo "you need sudo to run this"
     exit 1
fi
```

By putting that at the top of each script, you can take all the sudos out and we can just do
```
sudo bash font.txt
```
instead of
```
bash font.txt
```
and have to put our password in as the script is running.

2. The multimedia codec script won't work if the correct repositories aren't enabled. It also doesn't have w32codecs in there. You could add something at the top to at least temporarily change the sources.list.

Something like
```
SOURCES="/etc/apt/sources.list"

if [ -f $SOURCES ] ; then
    mv $SOURCES $SOURCES".backup"
fi   

#Creating new sources.list
echo \
"deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse" \
>> $SOURCES

#Updating new sources
apt-get update

#put the rest of your script here

# Moves backup sources back
if [ -f $SOURCES".backup" ] ; then
   rm $SOURCES
   mv $SOURCES".backup" $SOURCES
fi
```

---

### Post by sobira on 2007-03-23
Thanks for the tips  bruenig :) 
i edited all the scripts

---

