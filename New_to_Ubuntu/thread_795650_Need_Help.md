---
title: "Need Help"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-05-15
Ok in trying to learn and configure my system, I've caused a few major system problems that wont let my Ubuntu installation fire up

so I am using the live cd at to access this computer, and am trying to back up my files this way before I do a reinstall. I have a few backed up

however there are a couple of folders which had their permissions set as just for me, and now it's telling me I cant back up or access them because I am not the owner, is there a way around this from the livecd?

---

### Post by celticbhoy on 2008-05-15
What method are you using to backup

---

### Post by Primefalcon on 2008-05-15
I am just copying the files over to a usb drive I have, which is working fine except for the folders that I don't apparently have permissions to back up

---

### Post by celticbhoy on 2008-05-15
I am guessing that you are using the gui for this and that is what you preffer. If so try this, right click on your desktop and create a luancher, call it root gui, and set the command to 'gksudo nautilus' and save. double click to launch and use this to copy the last of your folders.

---

### Post by Primefalcon on 2008-05-15
PERFECT THANK YOU

I am learning the terminal atm, tbh until about a month or so ago I was a solid windows user, knew it back and forwards.

I actually deleted my windows to put ubuntu, tbh I'd never go back, for starters it's a lot more stable and customizable, the source, of my current problems lol, but I'm learning.

Thanks again for your help

---

### Post by Tyke91 on 2008-05-15
if you want a terminal way to do this, open a terminal and type

```
cd /media
```then 

```
ls
```it should show you a list of all the mounted media, one should be the hard drive you're getting data from, and one should be your USB stick. let's pretend you got

```
cdrom disk disk-1
```doing a cd into disk and then ls again will show you which drive it is (usb stick or hard drive)

then just cd into the one you know is a hard drive, cd to /home/<your user name>, then use this command 
```
sudo cp /media/<mount point of your hard disk>/home/<your user name>/<file you want to copy> /media/<mount point of your usb stick>/<file/you/want/to/copy/into>

```or if you want to copy the entire home folder, replace the file name with an asterisk ' * '

_______________________________

I know this looks compilcated at first, but if you understand these things it all becomes simple.

cd - change directory, used with syntax ```
cd /directory/you/want/to/change/to
```cp - copy, used with syntax ```
cp file/to/copy /destination
```ls - view current directory, used with syntax ```
ls
``` if you want to view hidden files, use ```
ls -a
```* - wildcard, used when you want anything to be in that slot. * alone means everything, a* means everything starting with a lowercase 'a', *a is everything that ends with an a, *a* is anything with an a in the middle, etc...



hope this helps :) 
for a better tutorial, look at the second link in my sig.

---

### Post by Primefalcon on 2008-05-15
I know some basic terminal skills such as


cd = location/to/file
cd = to go back to user home
pwd = where I am
ls = see files and fodlers where i am at
and to use a program with soemthing such as

gedit file.text
wine file.exe

and so forth and with sudo and such.

but really, that sums up all my terminal knowledge atm, I know prob not a lot to know for a month, but I've mostly been using the gui, since I've only used linux for about a month as said.

getting there though :-)

thx for your help everyone and Tyke91 that will help, in he future :-)

---

