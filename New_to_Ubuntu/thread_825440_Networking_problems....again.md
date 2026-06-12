---
title: "Networking problems....again"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Whik on 2008-06-11
ok once again thank you everybody for being such a great help so far but it apears ive stumbled onto a fairly common problem with hardy heron

After everyone helped me get my internet working on my linux computer the first thing i did was update it.
Now the internet doesnt work and when i did the config it came back  Network UNCLAIMED after doing some research that seems to be a fairly common problem for Hardy heron 
So my question is, Can i fix this for a linksys wireless card?

---

### Post by sam_delta on 2008-06-11
what method you used before the update? ndiswrapper?, if so, since there where some kernel updates, i believe you just need to type few commands to get the module running again

so, what method/drivers you where using before the update?
sam

---

### Post by Whik on 2008-06-11
I had ndiswrapper on there but i dont think thats how it accesed since the driver i had were labled as invalid by it so im pretty sure it was just linux running it

---

### Post by sam_delta on 2008-06-11
ah alright, whats your wireless card? you can find it out with the command ```
lspci
```

---

### Post by Whik on 2008-06-11
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843440&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4344040888B08&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843440&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4344040888B08&displaypage=download#versiondetail)

theres the link to the adapter i have version 1.0

---

### Post by sam_delta on 2008-06-11
i believe that that linksys card uses a broadcom chipset, i can confirm that if you post the ouput of the command ```
lspci
```

in the meantime, can you go WITH a wired connection plugged in into system>administration>hardware drivers, and check if there are some wireless drivers listed there? if there are, try to right click em and then enable them

sam

---

### Post by Whik on 2008-06-11
it does use a broadcam chip set at im sorry but i cant post it im having to run from the family computer to mine computer to work on mine and then make the post. Also i pulled up the drivers and theres nothing listed it just says No propiatery drivers

---

### Post by sam_delta on 2008-06-11
try installing b43-fwcutter, youll need a internet connection to do this (plug your ethernet cable)
then type
```
 sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with 'yes' when prompted if want to fetch the firmware
restart your computer and check if it works/shows under system>admin>hardware drivers

a b43-fwcutter works with most broadcoms however i duno your exact broadcom chipset, i cannot guarantee that this will work, but its worth giving a try
if it does not work, we'll have to go to ndiswrapper

sam

---

### Post by Whik on 2008-06-11
is it possible to download that to this computer with xp then move it over to my linux computer via psp/flash drive cause its not possible for me to hook my computer up to the ethernet when theres like 6 computers running on the connection and my dad would skin me

---

### Post by sam_delta on 2008-06-11
alright, i wrote a guide some time ago to someone who didnt had internet connection and wanted to install b43-fwcutter
follow the instructions on post number #9 from
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)

any questions/errors on any command/s, post em here
sam

---

### Post by Whik on 2008-06-11
thanks for the guide im gonna go try it now

---

### Post by Whik on 2008-06-11
ok i tried running the b43-fwcutter and i got a error because it couldnt get to the internet to get the files

---

### Post by Whik on 2008-06-11
bump

---

### Post by wil313 on 2008-06-11
If you are still having problems, try taking a look at this:

[http://ubuntuforums.org/showthread.p...ess+work+hardy](http://ubuntuforums.org/showthread.p...ess+work+hardy)

---

### Post by Whik on 2008-06-11
all that link does is bring me to the main forum page

---

### Post by sam_delta on 2008-06-11
ight, which one you tryied?  in post # 8 on this same thread, you need ethernet cable plugged

IF you do not have internet , you need to follow the guide on post #9 on the following link
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)

which guide you where following? and exactly where (or which command) it told you that you need an internet connection, and failed?

sam

---

### Post by Whik on 2008-06-11
heres a way that will help you reinstall b43-fwcutter, but please note that this will be significally harder w/o connection, but since there is no other choice, lets go!!

download and copy the following files into a USB flashdrive

(build-essetials)
[http://archive.ubuntu.com/ubuntu/poo...untu1_i386.deb](http://archive.ubuntu.com/ubuntu/poo...untu1_i386.deb)

(f43-fwcutter)
[http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)

(Broadcom Firmware)
[http://downloads.openwrt.org/sources...0.53.0.tar.bz2](http://downloads.openwrt.org/sources...0.53.0.tar.bz2)

go back to your ubuntu 8.04 pc and copy build essential.deb and b43-fwcutter-011.tar.bz2 file into the desktop
[B]
just run the build essentials and let them install
[/B]
now lets get to fwcutter

open a terminal and type
Code:

 cd Desktop

then

to extract
Code:

 tar xjf b43-fwcutter-011.tar.bz2

to change directory
Code:

 cd b43-fwcutter-011

to compile
Code:

 make

to get back to desktop
Code:

 cd ..

then we must install b43 with the firmware together

copy the broadcom-wl-4.80.53.0.tar.bz2 archive into your desktop and extract it (right click, extract here), it shuld make a folder with the same name
then open a terminal and type

Code:

 cd Desktop

Now our working directory is desktop, same place where we unpacked broadcom firmware

then we change working directory
Code:

 cd broadcom-wl-4.80.53.0/kmod

then we copy/install the firmware by typing this

Code:

 export FIRMWARE_INSTALL_DIR=”/lib/firmware”

finally to install
Code:

 ../../b43-fwcutter-011/b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” wl_apsta.o

restart pc and try to enable hardware drivers through system>administration>hardware drivers and should work
let us know if you have any problems with any command, thx,


procedure taken from: (i made the necessary modifications to make it without internet connection
[http://penkin.wordpress.com/2008/03/...dcom-wireless/](http://penkin.wordpress.com/2008/03/...dcom-wireless/)






I click install on the runner and it comes up saying downloading additional package data*i have me live cd in the drive also* then when it gets to file 6 of 8 the error comes up saying could not not download files please check your internet connection or instillation medium

---

### Post by sam_delta on 2008-06-11
EDIT, wait, they are not broken, 

you sayd "I click install on the runner and it comes up saying downloading additional package data" 

which package are you trying to install, build essential or b43-fwcutter?

sam

---

### Post by Whik on 2008-06-11
it was the build essential

---

### Post by sam_delta on 2008-06-11
insert your ubuntu 8.04 hardy cd then open a terminal and type
```
sudo apt-add cdrom
sudo apt-get update
sudo apt-get install build-essential
```

youll get some errors on the second command 'sudo apt-get update' dont worry run it anyways,  but build-essential should install fine with the 3rd command, when installed, proceed with the rest of the procedure, just skip instlling build-essential from the package

sam

---

### Post by wil313 on 2008-06-11
Sorry, this one should work:

[http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy](http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy)

---

### Post by Whik on 2008-06-11
im getting the error
Sudo: apt-add command not found

---

### Post by Whik on 2008-06-11
bump

---

### Post by Unix_Slayer on 2008-06-12
When the kernel gets updates, it knocks out the video drivers, and network drivers. All you have to do is open ndiswrapper. See if there is a device installed. If not, add the device back in with the proper .inf file. If it's there, remove it. Reboot, and open ndiswrapper again, and install the driver back again.

---

### Post by sam_delta on 2008-06-12
> **Whik said:**
> im getting the error
Sudo: apt-add command not found
sorry, mis typed, its ```
sudo apt-cdrom add
``` sry bout that

Also, if you get permission denied in any step (specially in the last one, add sudo before the command, so itll look like "sudo _comand_"

sam

---

### Post by Whik on 2008-06-12
in the last step i didnt get permission denied it came back saying
bash: ../../b43-fwcutter-011/b43-fwcutter : no such file or directory

---

### Post by sam_delta on 2008-06-12
alright, your probably skipped one step, did you downloaded and compiled b43?

assuming that you alredy installed build essentials and downloaded Broadcom Firmware (the third file from the guide i told you) into your desktop, then continue with the following instructions
follow them carefully, 

download (f43-fwcutter) from and save it in your desktop
[http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)

then copy it to your desktop and extract/compile it with the following command
 ```
cd Desktop
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
```

after you extract and compile b43-fwcutter on the desktop, that directory should be there.

go back to your desktop and copy/put broadcom-wl-4.80.53.0.tar.bz2 archive into your desktop and extract it (right click, extract here), it shuld make a folder with the same name (this file is the third one you downloaded from the post #9 of the link i gave you


after we extract b43-fwcutter with the instructions above then we type 
```

cd Desktop/broadcom-wl-4.80.53.0/kmod
export FIRMWARE_INSTALL_DIR=&#8221;/lib/firmware&#8221;
../../b43-fwcutter-011/b43-fwcutter -w &#8220;$FIRMWARE_INSTALL_DIR&#8221; wl_apsta.o
```

they must be typed in consecutive order
again, if you get permission deny on the last command, add sudo

sam

---

### Post by Whik on 2008-06-12
When i type make i get a long string of errors i even redownloaded b43fwcutter its so long the terminal doesnt even show it all

---

### Post by Whik on 2008-06-12
bump

---

### Post by sam_delta on 2008-06-12
you installd build essential?
whose errors should dissapear if you have build essential

to install build-essential, insert your ubuntu cd, then type
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

to make sure it installed succesfully, post the output of the third command

sam

---

