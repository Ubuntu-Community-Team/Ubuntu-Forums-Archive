---
title: "Howto: CDemu 0.8 for kernel 2.6.16+ (Edgy)"
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by HAARP on 2006-10-13
[COLOR="Red"]**ATTENTION: THIS HOWTO IS SEVERLY OUTDATED. SEE THIS [POST](http://ubuntuforums.org/showthread.php?p=5896032#post5896032)**[/COLOR]


old Howto follows:

Heya,

Basicly, CDemu is a software that allows you to mount CD-images. 0.7 supported cue/bin, while the new 0.8 has support for:

.cue   (CDRWin)
.iso   (ISO9660)
.mds   (Alchol 120%)
.ccd   (CloneCD)
.nrg   (Nero Burning ROM)

Sure, you can mount isos with a loop device and convert other images to iso, but that just sucks.
Sadly, the new version needs a kernel >=2.6.16, so it won't work with Dapper unless you compiled your own newer kernel!
Since you need Edgy or need to compile your own kernel, I'm assuming you have some basic knowledge of Linux. If not, feel free to post questions!
Also feel free to post improvements or errors I made!

We're going to set CDemu up. I also have some scripts to mount them from Nautilus with just a right-click. 

1. Get CDemu:
[http://prdownloads.sourceforge.net/cdemu/cdemu-0.8.tar.bz2](http://prdownloads.sourceforge.net/cdemu/cdemu-0.8.tar.bz2)

2. Extract it somewhere, open a console and **cd** to the directory you extracted it to

3. Type **make**, this should compile CDemu - or not.
If it complains about missing stuff, try searching Synaptic for packages that end with **-dev** and have parts of the name needed by **make**. Repeat 3.
I would provide a package that can easily be installed, but CDemu seems to be the only app not working with checkinstall :/

4. Type **make install**. This installs CDemu on your system. To uninstall it again, type **make uninstall** from this folder.

5. CDemu doesn't like udev and the device-creation script supplied screws everything up. Type **gksu gedit /usr/bin/create_cdemu_devs.sh** and replace everything in that file with this:
```

#!/bin/bash

#if [ -e /dev/.devfs ] ; then
#	echo "You have devfs, nodes will be created automagically"
#	exit 0
#fi
#if [ -e /dev/.udev ] || [ -e /dev/.udev.tdb ] ; then
#	echo "You have udev, nodes will be created automagically"
#	exit 0
#fi
#if [ ! -z "${DESTDIR}" ] ; then
#	echo "Creating a package, nodes should be created later"
#	exit 0
#fi

# find out cdemu device major number
if [ ! -r /proc/devices ]; then
	echo "Can't open /proc/devices, make sure /proc is mounted"
	exit 0
fi

modprobe cdemu
if [ -z "$(lsmod | grep ^cdemu)" ]; then
	echo "Can't load module"
	exit 0
fi
cdemumajor=$(grep "^[[:space:]]*[0-9]\+[[:space:]]\+cdemu$" /proc/devices | grep -o "[0-9]\+")
if [ -z "$cdemumajor" ]; then
	echo "Can't find cdemu device number in /proc/devices"
	exit 0
fi
#modprobe -r cdemu
#

if [ -e /dev/cdemu ]; then
	rm -rf /dev/cdemu
fi
if [ -b /dev/cdemu0 ]; then
	rm -f /dev/cdemu*
fi
mkdir /dev/cdemu
for drivenumber in `seq -w 0 7` ; do
	mknod /dev/cdemu/${drivenumber} b ${cdemumajor} ${drivenumber}
done

#echo "if no error did show up device files created ;-)"

```
Save the file and exit. **This step is important. If you don't edit this file, the CDEMU module will be unloaded every time the file gets executed!**

Now type **gksu gedit /etc/rc.local** and add this to the bottom of the file **but before any "exit 0" you may encounter**:
```
echo " Creating CDemu devices..."
create_cdemu_devs.sh
```
Save and exit. This will make your system create all the devices at startup.

6. Activate CDemu for a test run. Type **sudo create_cdemu_devs.sh** to create the devices and load the kernel module.
If no errors showed up, everything is fine.
You don't need to do this everytime you want to mount an image, just this time.
Get [this file](http://cdemu.sourceforge.net/cdemu_example.tar.bz2) and extract it somewhere.
then type **cdemu 0 /path/to/file/mini.cue** followed by a **sudo mkdir /media/cdemu0** and **sudo mount -t iso9660 -o ro /dev/cdemu/0 /media/cdemu0**
This should mount the test file to **/media/cdemu0**. If this works, move on.

Information about mounting images with CDemu in text mode will appear when typing **cdemu** in console. Basicly, it's **cdemu X /path/to/image** to load an image into cdemu-drive X, whereas X is 0-7. It will be loaded into the device **/dev/cdemu/X** ready to be mounted. To unload the image (after unmounting first), type **cdemu -u X**


7. If you want to be able to mount images without root rights, do this:
```
sudo mkdir /media/cdemu0
sudo mkdir /media/cdemu1
sudo mkdir /media/cdemu2
sudo mkdir /media/cdemu3
sudo mkdir /media/cdemu4
sudo mkdir /media/cdemu5
sudo mkdir /media/cdemu6
sudo mkdir /media/cdemu7
```
Then do **gksu gedit /etc/fstab** and add this to the end of the file:
```
/dev/cdemu/0	/media/cdemu0	iso9660		ro,user,noauto			0	0
/dev/cdemu/1	/media/cdemu1	iso9660		ro,user,noauto			0	0
/dev/cdemu/2	/media/cdemu2	iso9660		ro,user,noauto			0	0
/dev/cdemu/3	/media/cdemu3	iso9660		ro,user,noauto			0	0
/dev/cdemu/4	/media/cdemu4	iso9660		ro,user,noauto			0	0
/dev/cdemu/5	/media/cdemu5	iso9660		ro,user,noauto			0	0
/dev/cdemu/6	/media/cdemu6	iso9660		ro,user,noauto			0	0
/dev/cdemu/7	/media/cdemu7	iso9660		ro,user,noauto			0	0
```

Now, after loading the image into CDemu, you just need to do a **mount /media/cdemuX** to mount the corresponding drive.

8. If you want to be able to mount images in Gnome's Nautilus with just a few clicks, create 2 files in **/home/*USER*/.gnome2/nautilus-scripts**

**cd-mount**:
```
#!/bin/bash
# Mount CD images

# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`

# Main
if [ $EXT_LOW == "cue" -o $EXT_LOW == "iso" -o $EXT_LOW == "mds" -o $EXT_LOW == "ccd" -o $EXT_LOW == "nrg" ]; then
	
# Find a free DEV to mount
	DEV=$((`cdemu -s | cut -f 8 -d " " | grep 0 -n -m 1 | cut -c 1`-2))
	if [ $DEV -lt "0" ]; then
		zenity --info --text "You can not mount any more images."; exit 1
	fi

# Only allow mounting an image once
	MOUNTED="`cdemu -s | grep "$1" | cut -f11- -d " "`"
	DEVMOUNTED="`cdemu -s | grep "$1" | cut -f3 -d " " | sed -e 's@:@@'`"
	if [ "$MOUNTED" == "$1" ]; then
		zenity --info --text "Image already mounted on cdemu$DEVMOUNTED."; exit 1
	fi

# DEV needs to be between 0 and 7
	if [ $DEV -ge "0" -a $DEV -le "7" ]; then
		cdemu $DEV "$1" &&
		mount "/media/cdemu${DEV}" &&
		gnome-open "/media/cdemu${DEV}"
	fi

# If directory is empty, then release cdemu
	sleep 0.5
	if [ "$(ls -A /media/cdemu${DEV})" ]; then
		echo
		else umount "/media/cdemu${DEV}"
		cdemu -u $DEV
		zenity --info --text "Mount failed."; exit 1
	fi

else zenity --info --text "Selected file is no image."; exit 1
fi
```

**cd-unmount**:
```
#!/bin/bash
# Unmount CD images

# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`

# Main
if [ $EXT_LOW == "cue" -o $EXT_LOW == "iso" -o $EXT_LOW == "mds" -o $EXT_LOW == "ccd" -o $EXT_LOW == "nrg" ]; then
	
# Get the cdemu device-number and filename
	DEV="`cdemu -s | grep "$1" | cut -f3 -d " " | sed -e 's@:@@'`"
	MOUNTED="`cdemu -s | grep "$1" | cut -f11- -d " "`"

# Check if mounted
	if [ "$MOUNTED" == "$1" ]; then
		umount /media/"cdemu${DEV}"
		if [ $DEV -ge "0" -a $DEV -le "7" ]; then
			cdemu -u $DEV
		fi
		sleep 0.5
		if [ "$(ls -A /media/cdemu${DEV})" ]; then
			zenity --info --text "Unmount failed. Is device busy?"; exit 1
			else zenity --info --text "Image unmounted."; exit 0
		fi
	else zenity --info --text "Image does not appear to be mounted."; exit 1
	fi

else zenity --info --text "Selected file is no image."; exit 1
fi
```

And if you like to be able to create cue-sheets from files missing one:
**create-cuesheet**
```
#!/bin/bash
# Create CUE for BIN

# Isolate the filename without the extension.
BASE=`echo "$1" | sed 's/\.[^.]*$//'` 

cat << EOF > "${BASE}.cue"
FILE "$1" BINARY
  TRACK 01 MODE1/2352
    INDEX 01 00:00:00
EOF
```

Make all 2/3 files executable! Now right click onto a CD-image in Nautilus, select **Scripts** and select **cd-mount** or **cd-unmount**. Easier than Daemon Tools!

Credits for about half of the script and a few "templates" I worked from goes to [adamkane](http://www.ubuntuforums.org/member.php?u=76104). I wouldn't have been able to pull this off without using his scripts.

Bugs/Todo:
- [color=#FF0000]fixed[/color] -- Mounting the same image 2 times renders you unable to unmount them again with those scripts. I'm gonna fix this later. -- [color=#FF0000]fixed[/color]
- [color=#FF0000]fixed[/color] -- Unmount didn't work for files with spaces -- [color=#FF0000]fixed[/color]
- Make a working deb-package.
- .cue files that point to uppercase files which are lowercase in reality won't work and vice versa. You can just open the cuesheet in a text-editor to correct that.

Have fun! :D

---

### Post by janfsd on 2006-10-16
thanks for the howto, it's working here :-D

---

### Post by enki74 on 2006-10-20
Ooooh!!!  It's holy great info!!! thanks fot the tip!!

---

### Post by HAARP on 2006-10-20
Glad its working for you (:

---

### Post by CodyJarrett on 2006-10-23
Hi, I think I might have screwed things up. This is the error I get:

> morten@morten-desktop:~/source/cdemu-0.8$ cdemu 0 /home/morten/Desktop/cdemu_example/mini.cue
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in ?
    main()
  File "/usr/bin/cdemu", line 124, in main
    device = libcdemu.get_device_from_drive_number(args[0])
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 755, in get_device_from_drive_number
    raise CDEmu_Error, "Do you have cdemu module loaded? - could't find block device. If you've no devfs/udev make sure you created them."
libcdemu.CDEmu_Error: Do you have cdemu module loaded? - could't find block device. If you've no devfs/udev make sure you created them.



Any help greatly appreciated!!!

---

### Post by HAARP on 2006-10-23
Try executing **sudo create_cdemu_devs.sh**

---

### Post by CodyJarrett on 2006-10-23
thanks for your reply, but this doesn't help. The script executes fine, but I get the same errors afterwards. 

I think this might have something to do with an earlier version of cdemu that has been installed. 

Is there anyway to remove every trace of cdemu - including older versions?

thanks!!!

---

### Post by HAARP on 2006-10-23
Go to the cdemu directory and type **sudo make uninstall**

It seems the kernel moduel isn't being loaded, however it should load after you execute create-devs.
What does **sudo modprobe cdmeu** do?

---

### Post by CodyJarrett on 2006-10-23
thank you so much - that did the job.
and thanks so much for these wonderful scripts :mrgreen: :mrgreen: :mrgreen:

---

### Post by Somniis on 2006-10-23
[I]Hmm.. having a problem that I didn't have when on Dapper.

bash: make: command not found

When in the cdemu directory.  Any help with this? ](*,)[/I]

Edit:  Nevermind, just needed the build-essential package.
I do, however, get this error now when trying to make: 

```
Makefile:31: *** You'll need sources for your (at least 2.6.16) kernel.  Stop.
```

Not really sure what that means.  I have upgraded to Edgy, and from what I see, I don't have the 2.6.16 kernel.  Do I need to re-compile my kernel? :???:

---

### Post by qrm on 2006-10-24
> /bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'


any help would be greatly appreciated

---

### Post by HAARP on 2006-10-24
> **Somniis said:**
> [I]Hmm.. having a problem that I didn't have when on Dapper.

bash: make: command not found

When in the cdemu directory.  Any help with this? ](*,)[/I]

Edit:  Nevermind, just needed the build-essential package.
I do, however, get this error now when trying to make: 

```
Makefile:31: *** You'll need sources for your (at least 2.6.16) kernel.  Stop.
```

Not really sure what that means.  I have upgraded to Edgy, and from what I see, I don't have the 2.6.16 kernel.  Do I need to re-compile my kernel? :???:

You do have the kernel, but not the sources. Search Synaptic for linux-headers for your running kernel

> **qrm said:**
> 
[code}/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
/bin/sh: Syntax error: Bad fd number
Building modules, stage 2.
MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'[/code]
any help would be greatly appreciated

Hmm, I don't understand this. Try to continue with the next steps and see if it works anyway

---

### Post by MarkoSK on 2006-10-29
hm,,.,,i get this error too:

/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST
*** Warning: "__stack_chk_fail" [/home/marko/programi/cdemu-0.8/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'


....tryed going forward but no success...it didn't work....

any help?*

---

### Post by HAARP on 2006-10-29
> **MarkoSK said:**
> hm,,.,,i get this error too:

/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST
*** Warning: "__stack_chk_fail" [/home/marko/programi/cdemu-0.8/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'


....tryed going forward but no success...it didn't work....

any help?*

Your kernel needs to be at least 2.6.16. You have 2.6.15. Sorry, it won't work.

---

### Post by MarkoSK on 2006-10-29
hm...but I have edgy installed and kernell should be 2.6.17 ??? (that's what i chose at boot??)

---

### Post by HAARP on 2006-10-29
Strange...have you updated your kernel header files to the newest version? e.g. install **linux-headers** in snyaptic and update everything

---

### Post by MarkoSK on 2006-10-29
hm...i tryed this:

sudo apt-get install linux-headers-2.6.17-10-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.


??
(sorry i'm still quite a noob at linux so i don't quite understand all yet :D)

---

### Post by HAARP on 2006-10-29
make tries to access old headers that don't suit your running kernel, but I don't understand why. Try fiddling some more with the header files, but I don't have any better idea. Sorry :/

---

### Post by MarkoSK on 2006-10-29
heh...ok i managed to make it to look at the new headers....but it pops the same mistake...look:

/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `**/usr/src/linux-headers-2.6.17-10-386**'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/marko/programi/cdemu/cdemu/cdemu_core.o
  CC [M]  /home/marko/programi/cdemu/cdemu/cdemu_mod.o
  LD [M]  /home/marko/programi/cdemu/cdemu/cdemu.o
  Building modules, stage 2.
  MODPOST
  CC      /home/marko/programi/cdemu/cdemu/cdemu.mod.o
  LD [M]  /home/marko/programi/cdemu/cdemu/cdemu.ko
make[1]: Leaving directory `**/usr/src/linux-headers-2.6.17-10-386**'



i jsut don't get it

---

### Post by HAARP on 2006-10-29
What's the matter? Looks successful to me :)

---

### Post by MarkoSK on 2006-10-29
hehe :D it works :D :D
hehe...so all it had to do is to make it too look at new kernel headers...

tnx :D

---

### Post by Amnon82 on 2006-10-30
Hi Guys,

I did some schemas for Nautilus Actions. 
You can find them on the [Nautilus Actions Project Page](http://www.grumz.net/?q=node/281)

---

### Post by KillerBOB on 2006-11-04
Hi, thanks for the Howto! Works pretty well. I just wonder if it would be possible to utilise "pmount" instead of "mount" somehow? That way there would not be necessary to create all the /media/cdemuX folders statically

Just a thought, I think using pmount would be a good idea, but someone might have a better understanding and prove me wrong.

Take care

---

### Post by HAARP on 2006-11-04
I've never used pmount directly from the console. I think this would work, but I've got no experience with it. If anyone wants to try this: Go on, do it :)

---

### Post by loko on 2006-11-04
hm, i use edgy final version but i get an error with cdemu:

```
user@user-laptop:~/cdemu_example$ sudo create_cdemu_devs.sh
user@user-laptop:~/cdemu_example$ cdemu 1 mini.cue
user@user-laptop:~/cdemu_example$ sudo mount /dev/cdemu/1 /media/test/
mount: block device /dev/cdemu/1 is write-protected, mounting read-only
mount: you must specify the filesystem type
```

I changed create_cdemu_devs.sh like described and get no errors while creating the device.


What is the problem here?

---

### Post by HAARP on 2006-11-04
> **loko said:**
> hm, i use edgy final version but i get an error with cdemu:

```
user@user-laptop:~/cdemu_example$ sudo create_cdemu_devs.sh
user@user-laptop:~/cdemu_example$ cdemu 1 mini.cue
user@user-laptop:~/cdemu_example$ sudo mount /dev/cdemu/1 /media/test/
mount: block device /dev/cdemu/1 is write-protected, mounting read-only
mount: you must specify the filesystem type
```

I changed create_cdemu_devs.sh like described and get no errors while creating the device.


What is the problem here?
Try **sudo mount  -t iso9660 -o ro /dev/cdemu/1 /media/test/**

---

### Post by loko on 2006-11-04
mh, ok so it is like mounting an image the "normal" way.

i thought cdemu was made to do this automatically ( the -t iso9660).

so how and where should i put it in the scripts, because i assume they will also not work then....

---

### Post by HAARP on 2006-11-04
> **loko said:**
> mh, ok so it is like mounting an image the "normal" way.

i thought cdemu was made to do this automatically ( the -t iso9660).

so how and where should i put it in the scripts, because i assume they will also not work then....

You can continue in the Howto, the modification in fstab takes care of that anyway.

---

### Post by NESFreak on 2006-11-09
tnx for the howto. But my files get strangely screwed up. Binaries dont work. pieces of plain txt are missing or screwed up. and images(pictures / photo's ) look disturbed.

any help?
NESFreak

---

### Post by HAARP on 2006-11-09
What kind of image are you using? How are files missing/destroyed? Binaries probably won't work on the CD, since the execute bit is not set.

---

### Post by NESFreak on 2006-11-09
> **HAARP said:**
> What kind of image are you using? How are files missing/destroyed? Binaries probably won't work on the CD, since the execute bit is not set.

as in the data on the disk seems to be corrupted, tried all images i could find. Iso,mdf, ccd.

i've posted a screenshot of both the document viewer not reading a pdf (morowind dutch manual) as the setup logo of morowind showing a  weird distortion. btw it was from a ccd image.
[[img]http://xs208.xs.to/xs208/06454/Schermafdruk.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs208&d=06454&f=Schermafdruk.png)

NESFreak

btw also tested the 'test image' same result

---

### Post by HAARP on 2006-11-09
Very strange. Must be an error with CDemu itself. Sorry, I have no idea :/

---

### Post by HAARP on 2006-11-18
I've encountered this bug myself now. I'm pretty sure its a bug with CDemu, try telling them about it :)
A workaround is to get ccd2iso, mdf2iso, whatever2iso from Synaptic or the web, and use them to convert the files to iso. Disadvantage is that copy-protection won't work in ISOs.

----

I edited the scripts yet again. They should be half a second faster now and I've fixed a bug with unmounting files that contained spaces.

---

### Post by adamkane on 2006-11-20
Great job!

You have a **typo** in the cd-mount/cd-unmount scripts.

```

if [ $DEV -ge "0" -a $DEV -le 7 ]; then

```should be

```

if [ $DEV -ge "0" -a $DEV -le "7" ]; then

```**Neat trick**:

If you add
```

sudo modprobe cdemu

```to the cd-mount Nautilus script, cdemu will be auto-loaded each time you use the script. No need to edit rc.d.

---

### Post by HAARP on 2006-11-20
(:

I've fixed the typo.
I'd rather keep modprobe cdemu inside of create_devices.sh since this way, the module gets loaded and the devices are created with one step. Easier that way, imo.
On the other hand, if I edit both mount and unmount scripts, I could make it so the module only gets loaded when needed. It's possible, but the module doesn't take that much space in memory, so it's not worth the work imo.

---

### Post by adamkane on 2006-11-20
Do these scripts mount .iso .nrg and .mds? I thought that cdemu only mounted .bin/.cue. I'm only testing on Dapper and cdemu 0.8.

*EDIT*
I mean cdemu 0.7
*END*

---

### Post by HAARP on 2006-11-20
It's all in the How-To. Since 0.8, you can mount all those formats, but 0.8 won't work on Dapper. Needs kernel >=2.6.16

---

### Post by adamkane on 2006-11-20
You should create a nautilus-script-cd-mount .deb file. This way cdemu and cd-mount/cd-unmount can be auto-installed. Users won't have to mess with the command-line. I'm working on this for Dapper, but I am a poor programmer.

nautilus-script-audioconvert is packaged as a .deb file. It's incomplete, but it's an example of what I'm talking about. 

The cd-mount .deb should include cdemu.ko for each kernel, i386, i686, k7. This way users won't install the wrong linux-headers, and hose their setup. The .deb file should also have the option to remove cdemu, if the user would like.

It may be better to create a separate cdemu .deb file as a dependency, but I'm not sure yet.

After you have the control and data files created:
> 
/control
/debian
/DEBIAN/control
/usr/local/conf/nautilus-script-cd-mount
/usr/local/conf/cdemu.ko
/usr/bin/cdemu
/usr/bin/nautilus-script-cd-mount-install
/usr/bin/create_cdemu_devs.sh
etc...
Here is Simple example to create a nautilus-script .deb file:
```

dpkg -b /home/<user>/projects/nautilus-script-cd-mount-0.1 nautilus-script-cd-mount-0.1-0ubuntu1_all.deb

```Have you tried KCDemu for KDE? It even works on Gnome (sort of). It creates a daemon-tools panel applet for loading cd images, but it didn't work well for me on Ubuntu. It can't be difficult to create a panel applet for Gnome, but it'll take me a few months to get up to speed on panel applet creation.

---

### Post by HAARP on 2006-11-21
Sounds promising, however I never manages to properly create any package without resorting to checkinstall :|
How do I create modules for kernels I don't run? I'm not really interested in getting those kernels just to do that.
Where do I put the scripts so every user can use them? Right now, those get stored in every users home folder, but I don't know the position to enable them globally.

---

### Post by adamkane on 2006-11-21
It's a bit tedious. I have an Intel and an AMD PC, so it possible:
Install kernel, reboot, make, save cdemu.ko somewhere, repeat for each kernel. Create one universal installer or create separate installers for each kernel.

I also find the kiso application useful for converting cd images whenever possible. I then mount them as an iso. Most cd images are single track anyway.

There is also a kiso service menu for KDE, which could be rewritten as a Nautilus script. It mounts AND converts cd images.

I just wanted to throw out some suggestions, since a lot of people will be looking at your thread.

---

### Post by qrm on 2006-11-23
when i try to unmount or mount the example image from nautilus I get this error:

the selected file is no image

It is already mounted and it shows up on my desktop as another icon, but when I try to unmount it from rightclick-unmount rather than with the script i get this error:

umount: only root can unmount /dev/cdemu/0 from /media/cdemu0

If I try to unmount it with the unmount-script i Get the previously mentioned Selected file is no image error.

any help is greatly apprecited

---

### Post by HAARP on 2006-11-24
Did you modify your fstab?
btw, the scripts check for the file extension. If it's the wrong one, it'll tell you they're not supported.

---

### Post by qrm on 2006-11-24
I did add the line to fstab and the file is the example file that is shown in your howto

---

### Post by HAARP on 2006-11-25
Unmounting using the unmount-command Gnome has is a bad idea, anyway. Even if it works, CDemu will still have the image loaded -> You won't be able to mount this image again, and you'll have one less device to mount images. Always use the image-unmount script.

You have to unmount the image directly. If you try unmounting that little icon on the Desktop, it will fail.

---

### Post by HugoPalma on 2006-11-29
I followed the tutorial and found the following problems:

- With the example mini.cue i can mount it ok but get a scrambled image.

- I keep getting "Invalid header of the cue-file" with any other cue file i use when i execute "cdemu 0 <whatever>.cue.


Any ideas ?

---

### Post by HAARP on 2006-11-29
> **HugoPalma said:**
> I followed the tutorial and found the following problems:

- With the example mini.cue i can mount it ok but get a scrambled image.

- I keep getting "Invalid header of the cue-file" with any other cue file i use when i execute "cdemu 0 <whatever>.cue.


Any ideas ?

There seem to be more cases of mounted images being scrambled with CDemu 0.8.  But the mini.cue should work just fine...
Maybe report the bug to them? Sorry, I can't help you here :(

Could you show me the contents of one of those not-working cue-files?

---

### Post by HugoPalma on 2006-11-29
> **HAARP said:**
> There seem to be more cases of mounted images being scrambled with CDemu 0.8.  But the mini.cue should work just fine...
Maybe report the bug to them? Sorry, I can't help you here :(

Could you show me the contents of one of those not-working cue-files?

Sure. I'm attaching it.

---

### Post by HAARP on 2006-11-29
> **HugoPalma said:**
> Sure. I'm attaching it.

Try removing the first 3 lines. Maybe CDemu expects the header to contain the FILE line first

---

### Post by HugoPalma on 2006-11-29
> **HAARP said:**
> Try removing the first 3 lines. Maybe CDemu expects the header to contain the FILE line first

I've already tried it with no luck. I also tried changing "WAVE" to "BINARY" and it actually didn't report the same error. Although it did report a bunch of errors for each track, something like:

Couldn't match: <TITLE "Cinema">  (spaces striped)

---

### Post by HAARP on 2006-11-29
Uh huh. My second guess is to remove all non-English symbols. CDemu may have problems with those

---

### Post by HugoPalma on 2006-11-29
> **HAARP said:**
> Uh huh. My second guess is to remove all non-English symbols. CDemu may have problems with those

I did that. Same error.

---

### Post by HAARP on 2006-11-29
Aw crap. I'm out of ideas.
Sorry I couldn't be of any help :(

---

### Post by HugoPalma on 2006-11-29
> **HAARP said:**
> Aw crap. I'm out of ideas.
Sorry I couldn't be of any help :(

Thanks for your help. I've asked the cdemu community for help. I'll post back as soon as i have an answer.

---

### Post by HugoPalma on 2006-11-30
I've tried the nautilus integration but i'm also having trouble using it.
Using the given example cue i always get the message:

"Selected file is no image"

when i right click on mini.cue and select cd-mount.
But when i run from the terminal:

./cd-mount mini.cue

it get's mounted just fine.
It seems that if i run from Nautilus it doesn't detect the file that i've selected.

Any ideas ?

---

### Post by HAARP on 2006-11-30
I have no idea why it's doing that to you. Something's fishy with your system :|

---

### Post by HugoPalma on 2006-11-30
> **HAARP said:**
> I have no idea why it's doing that to you. Something's fishy with your system :|

Tell me about it. You can see how fishy from this [post]("http://ubuntuforums.org/showthread.php?t=288949").

I'm just having no luck with edgy :( 
Oh well...

---

### Post by rodgersan on 2006-12-08
Same problem here with corrupted files... I don't know what to do...:(

---

### Post by HugoPalma on 2006-12-09
> **HugoPalma said:**
> Thanks for your help. I've asked the cdemu community for help. I'll post back as soon as i have an answer.

Here's the [reply]("http://sourceforge.net/mailarchive/forum.php?thread_id=31134556&forum_id=36225") i got.

---

### Post by rodgersan on 2006-12-09
> **HugoPalma said:**
> Here's the [reply]("http://sourceforge.net/mailarchive/forum.php?thread_id=31134556&forum_id=36225") i got.

I'm always lost, he didn't answer at your question about the scrambled picture...

---

### Post by HAARP on 2006-12-10
This seems to be a major problem with this release of CDemu. I believe the only way to get it fixed is to bug the developers like hell :|

---

### Post by rodgersan on 2006-12-10
> **HAARP said:**
> This seems to be a major problem with this release of CDemu. I believe the only way to get it fixed is to bug the developers like hell :|

What can we do exactly?? I would like to help but I don't really know how....

---

### Post by HAARP on 2006-12-10
> **rodgersan said:**
> What can we do exactly?? I would like to help but I don't really know how....

[http://cdemu.sourceforge.net/#contact](http://cdemu.sourceforge.net/#contact)

Try contacting them, tell them about the bug, give information, flood their mailing list. Sadly they don't have a bug tracker...

---

### Post by rodgersan on 2006-12-10
I sent an email to them with a little description of the problem and I will keep you aware as soon as I get an answer....

---

### Post by noidear on 2006-12-10
Hi 

I have been having the same problems with bin cue files, basically that they mount fine when using the terminal commands, but when I try to read or run a file from the mounted bin cue files all the contents are scrambled. eg pdf file, swf file avi file etc. Also I cant mount the bin cue files from the nautilus scripts. Only works from the command line

mounting iso files work fine though when using the cdemu commands from the terminal but I keep getting the no image error when I try to mount from the nautilus scripts.

here's how I have been doing it so far

I have set up cdemu as per the instructions on page 1 of this thread and set fstab and folders, for example;
[B]
mkdir /media/cdemu0[/B]

etc. Then when I want to mount an iso file I go

**cdemu 0 /path/to/file/filename.iso**

you ca****n then check if cdemu has loaded the iso properly by using 

**cdemu -s**

then to mount the file to /media/cdemu0 folder type

**sudo mount -t iso9660 -o ro /dev/cdemu/0 /media/cdemu0**

to unmount the file you first type

**sudo umount /media/cdemu0**

and finally to remove the iso from the cdemu binding type

**cdemu -u 0**

My workaround for bin cue files for now is to use bchunk to convert them to iso and then mount the iso files

to install bchunk type

**sudo apt-get install bchunk**

then to convert a bin cue file to iso type

[B]bchunk filename.bin filename.cue filename
[/B]
bchunk then converts the bin cue files to an iso file and then you can mount it and run it. 

Hope that helps some for now

---

### Post by HAARP on 2006-12-10
Wait, you're saying my mount-scripts are faulty? I investigate.

---

### Post by noidear on 2006-12-11
Hi HAARP

unfortunately they didn't work on my pc
i kept getting the no image error, but I'll try setting it up on my other laptop and see if it does the same thing, as other people have stated on this thread that it has worked for them. but if you could have a look at the scripts thanks as they would be really handy :)

---

### Post by HAARP on 2006-12-11
The mount script will test the filename and its extension. If It can't find the file or if it has a wrong extension, you'll get the "no image" error. Working extensions are: cue, iso, mds, ccd, nrg.
If it still won't work,please try to execute it within a terminal.
```
/home/*USER*/.gnome2/nautilus-scripts/cd-mount /path/to/image
``` and tell me the output. This way, I can try to see what's wrong.

---

### Post by noidear on 2006-12-11
Hi

Thanks for the response and here is the output when I try to mount an iso file using the terminal

sudo /path/to/nautilus-scripts/cd-mount /path/to/iso

(nautilus:14668): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

I also tried setting up cdemu on my other pc using your first post on this thread and unfortunately the same problems occur. I can mount iso files and play & read the contents of that volume fine, but  although bin cue files mount ok I cannot read the contents of those volumes. All the files are scrambled. So it must be some way that cdemu handles bin cue files or could it be to do with the create_cdemu_devs.sh script. Anyway, thanks again for the feedback and if I find out anything else I will report back

---

### Post by HugoPalma on 2006-12-12
> **HAARP said:**
> This seems to be a major problem with this release of CDemu. I believe the only way to get it fixed is to bug the developers like hell :|

I'm trying......

---

### Post by HAARP on 2006-12-12
> **noidear said:**
> Hi

Thanks for the response and here is the output when I try to mount an iso file using the terminal

sudo /path/to/nautilus-scripts/cd-mount /path/to/iso

[code}(nautilus:14668): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.[/code]


That's strange. libgnomevfs is Gnome/Nautilus' virtual file system, and certainly seems related. However, I don't know how. Try searching synaptic for it and install the other libgnomevfs packages that are there. Maybe that'll fix it...
I can't reproduce the error. Do you think you could try executing the script by hand? Open in text editor, and copy'n'paste it into a terminal line-by-line until you get a error message. I'm sorry for the work this takes, but it's my only idea to localize the problem :/

---

### Post by HugoPalma on 2006-12-14
> **HAARP said:**
> That's strange. libgnomevfs is Gnome/Nautilus' virtual file system, and certainly seems related. However, I don't know how. Try searching synaptic for it and install the other libgnomevfs packages that are there. Maybe that'll fix it...
I can't reproduce the error. Do you think you could try executing the script by hand? Open in text editor, and copy'n'paste it into a terminal line-by-line until you get a error message. I'm sorry for the work this takes, but it's my only idea to localize the problem :/

I also have the "Selected file is no image" error when i run from nautilus. 
Here's what i found out. If i run "sudo /path/to/nautilus-scripts/cd-mount /path/to/cue" i get:

[: 38: ==: unexpected operator

If i run "/path/to/nautilus-scripts/cd-mount /path/to/cue" (without the sudo) the mount runs just fine.
So, from the terminal it only works if i'm executing with no root priveliges.
Don't know if this is related to the problem when running from nautilus but maybe it helps figure out the problem.

---

### Post by HAARP on 2006-12-14
You're supposed to execute it as a user.

So it works from terminal (non-user) but not from right-click, scripts?

---

### Post by HugoPalma on 2006-12-14
> **HAARP said:**
> You're supposed to execute it as a user.

So it works from terminal (non-user) but not from right-click, scripts?

That's right. I have no problem with the script when i run them from the terminal. I have no luck when running them from nautilus.

---

### Post by mrneo240 on 2006-12-16
Hey just saying that it is not extremely important to update your kernel (could it be ?)
i compiled this on 
Ubuntu/dapper  - 2.6.15-27
by doing everything exactly the same except for modifying the makefile 
i edited mine to look like this 


Makefile (removed the kernel checks)
```
# Makefile for cdemu ( http://cdemu.sf.net/ )
# $Header$

PREFIX = /usr
SRCS = cdemu_core.c cdemu_mod.c cdemu_proc.c
OBJS = $(patsubst %.c,%.o, $(SRCS))

#
# Kernel source detection
#  - default to /lib/modules/$(uname -r)/build/
#  - fall back to /usr/src/linux/
#
KERN_VER = $(shell uname -r)
KERN_MAJ = $(shell echo $(KERN_VER) | cut -d. -f1-2 -)
ifndef KERN_DIR
	KERN_DIR = /lib/modules/$(KERN_VER)/build
	ifeq ($(shell test -e $(KERN_DIR)/Makefile || echo yes),yes)
		KERN_DIR = /usr/src/linux
	endif
endif
ifndef KERN_SRC
	ifeq ($(shell test -s $(KERN_DIR)/Makefile && echo yes),yes)
		KERN_SRC = yes
	else
		KERN_SRC = no
	endif
endif
KERN_INC = $(KERN_DIR)/include

ifeq ($(KERN_SRC),no)
    $(error You'll need sources for your (at least 2.6.16) kernel)
endif


#
# Python detection routine
#  - try to find .py install path
#
ifndef PYTHON
	PYTHON = $(shell which python)
	ifeq ($(shell test -x $(PYTHON) && echo yes),yes)
		PYTHON_PRE = $(shell $(PYTHON) -c "import sys; print sys.prefix")
		PYTHON_VER = $(shell $(PYTHON) -c "import sys; print sys.version[0:3]")
		PYTHON_V1 = $(shell $(PYTHON) -c "import sys; print sys.version[0:1]")
		PYTHON_V2 = $(shell $(PYTHON) -c "import sys; print sys.version[2:3]")
	else
		PYTHON_V1 = 1
		PYTHON_V2 = 1
	endif
endif
PYTHON_DIR = $(PYTHON_PRE)/lib/python$(PYTHON_VER)/site-packages


#
# Break kernel-specific cruft into sub .mk files in order
# to keep this stuff readable
#
ifndef MK_INC
	MK_INC = $(PWD)
endif

ifeq ($(KERN_MAJ),2.6)
	KERN_MICRO = $(shell echo $(KERN_VER) | sed 's/2\.6\.\([0123456789]*\).*/\1/')
		MODVAR = M

	include $(MK_INC)/mk/linux-2.6
endif


#
# Shared make targets
#
.PHONY: mrproper clean docs extra-docs install install-docs check python-check vapier-test

mrproper: clean
	rm -f docs/cdemu.{info,txt,html}

clean:
	rm -f .cdemu*.{ko,mod.o,o}.cmd cdemu*.{ko,o,mod.{c,o}} *.pyc core *~
	rm -rf .tmp_versions Modules.symvers
	rm -f docs/cdemu.{dvi,pdf}

docs:
	cd docs; makeinfo cdemu.texi
	cd docs; makeinfo --plaintext -o cdemu.txt cdemu.texi
	cd docs; makeinfo --no-split --html cdemu.texi

extra-docs:
	cd docs; texi2dvi -c -q cdemu.texi
	cd docs; texi2pdf -c -q cdemu.texi

install:
	@if [ "`whoami`" != "root" ] ; then \
		echo "****" ; \
		echo "**** WARNING -- You might not be root." ; \
		echo "**** If the below install fails, try it as root!" ; \
		echo "****" ; \
		echo "" ; \
	fi
	@echo "**** Installing files ****"
	install -D -m 644 $(KOBJ) $(DESTDIR)/lib/modules/$(KERN_VER)/misc/$(KOBJ)
	install -D -m 644 libcdemu.py $(DESTDIR)$(PYTHON_DIR)/libcdemu.py
	install -D -m 755 cdemu $(DESTDIR)$(PREFIX)/bin/cdemu
	install -D -m 755 create_cdemu_devs.sh $(DESTDIR)$(PREFIX)/bin/create_cdemu_devs.sh
	@if [ "$(DESTDIR)" = "" ] ; then \
		/sbin/depmod -a ; \
	else \
		echo "**** Skipping depmod" ; \
	fi
	-sh create_cdemu_devs.sh

uninstall:
	-rmmod cdemu
	-rm -f /lib/modules/$(KERN_VER)/misc/$(KOBJ)
	-rm -f $(PYTHON_DIR)/libcdemu.py*
	-rm -f $(PREFIX)/bin/cdemu
	-rm -f $(PREFIX)/bin/create_cdemu_devs.sh

install-docs:
	@if [ "`whoami`" != "root" ] ; then \
		echo "****" ; \
		echo "**** WARNING -- You might not be root." ; \
		echo "**** If the below install fails, try it as root!" ; \
		echo "****" ; \
		echo "" ; \
	fi
	gzip docs/cdemu.1
	install -D -m 644 docs/cdemu.1.gz $(DESTDIR)$(PREFIX)/share/man/man1/cdemu.1.gz
	gunzip docs/cdemu.1
	gzip docs/cdemu.info
	install -D -m 644 docs/cdemu.info.gz $(DESTDIR)$(PREFIX)/share/info/cdemu.info.gz
	gunzip docs/cdemu.info

check:
	@modprobe -r cdemu
	@dmesg -c 2>&1 >/dev/null
	@echo -e "\n**** Loading and removing module ****"
	insmod ./$(KOBJ)
	dmesg -c
	rmmod cdemu

python-check:
	@if [ -z "$(PYTHON)" ]; then \
		echo; \
		echo "Error: Could not find your python installation."; \
		echo "Maybe this will help: make PYTHON=/path/to/python.bin install"; \
		echo; \
		exit 1; \
	fi
	@if [ $(PYTHON_V1) -lt 2 -o $(PYTHON_V2) -lt 2 ]; then \
		echo; \
		echo "Error: You need at least python-2.2.0 to use cdemu."; \
		echo "Aborting..."; \
		echo; \
		exit 1; \
	fi

vapier-test:
	@for v in 2.4.2{1,2,3,6,7} 2.6.{5,6,7,8.1,9,10,11,999} ; do \
		echo -e "\n\n------------- $$v -------------\n\n" ; \
		echo $(MAKE) KERN_DIR=/usr/src/includes/$$v KERN_VER=$$v clean all ; \
		$(MAKE) \
			KERN_SRC=no \
			KERN_INC=/usr/src/includes/linux-$$v/include \
			KERN_VER=$$v \
			clean all 2>&1 | head -n 30 ; \
			_pipestatus="$${PIPESTATUS[*]}"; \
			[[ "$${_pipestatus// /}" -eq 0 ]] || exit 1 ; \
	done
	$(MAKE) clean
	@echo -e "\n\n------------- done -------------\n\n"

```

i compiled and followed the rest of the instructions and everything is working great 
no problems here

---

### Post by rodgersan on 2006-12-19
Some news, I've got this file: 

[http://www.kabelkaos.net/cdemu/userspace-cdemu-20061213.tar.bz2](http://www.kabelkaos.net/cdemu/userspace-cdemu-20061213.tar.bz2)

I'm trying to figure what to do with... it changed a lot and I'm not really experienced with linux....

---

### Post by HAARP on 2006-12-20
This is an userspace CDemu, meaning it does not use a kernel module to provide its functionality. However, that's all I know about it.

---

### Post by rodgersan on 2006-12-20
> **HAARP said:**
> This is an userspace CDemu, meaning it does not use a kernel module to provide its functionality. However, that's all I know about it.

Is it bad or good? I'm a little lost...

---

### Post by HAARP on 2006-12-24
> **rodgersan said:**
> Is it bad or good? I'm a little lost...

Neither. It's just a different approach.
For now, I'd stay with the kernel-one

---

### Post by chocomoojuice on 2006-12-27
I keep getting the following error when attempting the **make** step:

```
/bin/sh: Syntax error: Bad fd number
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.17-10-generic/misc/cdemu.ko
install: cannot stat `cdemu.ko': No such file or directory
make: *** [install] Error 1

```

What's wrong and how do I solve this =(!!!

---

### Post by HAARP on 2006-12-27
Looks like you're trying **make install** before **make**. Do a **make** first.

---

### Post by saracen on 2006-12-28
Would someone like to get this (or an equivalent) into fiesty?  It would be a shame to have fiesty released without full CD mounting support installed by default when there really isn't that much to getting it configured.

And why isn't cdemu in the repos anyway?

---

### Post by theaverageidiot on 2007-01-09
I'm trying to unmount a CD because I need to switch discs (its a game) but since the installers open I get "Can't unmount. Device is busy" or something. I tried modifying the script a tad to add sudo before the "umount /media/"cdemu${DEV}"" but it didn't matter (I reverted it back to original, btw).

Help? :)

[EDIT]

I found a solution! In case anybody has my trouble, here's what to do:

Open your cd-unmount script. Find this:
```
		umount /media/"cdemu${DEV}"
```

Replace it with this:
```
		umount -l /media/"cdemu${DEV}"
```

It will now be forced to unmount no matter what! :)

[EDIT AGAIN]
**Scratch that. It doesn't work. It acts like it works but it doesn't.**

---

### Post by HAARP on 2007-01-09
Try umount -lf

---

### Post by zukakog on 2007-01-09
I'm having a weird problem.  I mount the image as instructed, but don't seem to have access to it.  Here's what I do, and what I get:
```
self@machine:~/Desktop$ cdemu -v 5 Studio_8_Disc_2.mds
Using /dev/cdemu/5
CD Image seems to be a 'Alcohol 120% (MDS/MDF)' file.
MDS/MDF version: 1.3
datablocks: 4, lead-in blocks: 3, track blocks: 1, sessions?: 1
numsectors: 159503, datablocks offset: 112, extrablocks offset: 432
binfile: Studio 8 - Disc 2.mdf
datablock:   0, track: a0, mode:  0, flags: 14, sector size: 0, MSF: 01:00.00, sector: 0, offset: 0, pregap: 0, sectors: 0
datablock:   1, track: a1, mode:  0, flags: 14, sector size: 0, MSF: 01:00.00, sector: 0, offset: 0, pregap: 0, sectors: 0
datablock:   2, track: a2, mode:  0, flags: 14, sector size: 0, MSF: 35:28.53, sector: 0, offset: 0, pregap: 0, sectors: 0
datablock:   3, track:  1, mode: aa, flags: 14, sector size: 2448, MSF: 00:02.00, sector: 0, offset: 0, pregap: 150, sectors: 159503
Trying to open </home/self/Desktop/Studio 8 - Disc 2.mdf>
real (existing) CD image file:  /home/self/Desktop/Studio 8 - Disc 2.mdf
reformated tracks:  [[20, 0L, 0L, 0L, 0L, 0L], [100, 35L, 26L, 53L, 159503L, 390463344L]]
self@machine:~/Desktop$
```
```
self@machine:~/Desktop$ mount /media/cdemu5
self@machine:~/Desktop$ 
```

```
self@machine:~/Desktop$ ls /media/cdemu5
additional content.app  autorun.exe  coldfusion mx 70  fireworks_8  homesite+ 55  navmac800qsfile
additional content.exe  autorun.inf  config            fscommand    license.htm
self@machine:~/Desktop$
```

```
self@machine:~/Desktop$ cp /media/cdemu5/autorun.inf ~
cp: cannot open `/media/cdemu5/autorun.inf' for reading: Permission denied
self@machine:~/Desktop$ 
```

```
self@machine:~/Desktop$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
...
# cdemu virtual devices
/dev/cdemu/0    /media/cdemu0   iso9660         ro,user,noauto                  0       0
/dev/cdemu/1    /media/cdemu1   iso9660         ro,user,noauto                  0       0
/dev/cdemu/2    /media/cdemu2   iso9660         ro,user,noauto                  0       0
/dev/cdemu/3    /media/cdemu3   iso9660         ro,user,noauto                  0       0
/dev/cdemu/4    /media/cdemu4   iso9660         ro,user,noauto                  0       0
/dev/cdemu/5    /media/cdemu5   iso9660         ro,user,noauto                  0       0
/dev/cdemu/6    /media/cdemu6   iso9660         ro,user,noauto                  0       0
/dev/cdemu/7    /media/cdemu7   iso9660         ro,user,noauto                  0       0
self@machine:~/Desktop$ 
```

Any Ideas?

---

### Post by HAARP on 2007-01-10
Sorry. I honestly don't have any idea :/

---

### Post by Exclamation on 2007-01-16
Heres a .deb I made for amd64 :)

---

### Post by bogolisk on 2007-01-17
[LIST=1]
[*] Why is the create_cdemu_devs.sh needed? I've downloaded and built cdemu (not using the steps of this howto) and udev create the devices just fine. They're /dev/cdemu{0-7} instead /dev/cdemu/{0-7}, is it a big issue?
[*] I use pmount (after I fixed pmount's device detection) and the image would be mounted under /media/cdemuX, an icon would be created on the Desktop. Why are ppl not using pmount? I try to get cdemu supported in hal but have no idea how hal work!
[*] I use the "Eject" menu of the Desktop's icon to umount. cdemu need a little fix to work properly but after the fix, it works beautifully.
[*] I only have one cue file on my disk and it doesn't work with cdemu. cdemu conplained: "Interleaved files not (yet) supported."
[/LIST]

---

### Post by HAARP on 2007-01-17
> **bogolisk said:**
> [*] Why is the create_cdemu_devs.sh needed? I've downloaded and built cdemu (not using the steps of this howto) and udev create the devices just fine. They're /dev/cdemu{0-7} instead /dev/cdemu/{0-7}, is it a big issue?
As a matter of fact, it is.


> [*] I use pmount (after I fixed pmount's device detection) and the image would be mounted under /media/cdemuX, an icon would be created on the Desktop. Why are ppl not using pmount? I try to get cdemu supported in hal but have no idea how hal work!
If pmount works for you, feel free to share how you did it. I will then try change my How-To to use pmount :)

> [*] I use the "Eject" menu of the Desktop's icon to umount. cdemu need a little fix to work properly but after the fix, it works beautifully.
Eject may unmount the image, but CDemu still has the file loaded into it's corresponding device. Do this more than 8 times, and you can't any more images.

> [*] I only have one cue file on my disk and it doesn't work with cdemu. cdemu conplained: "Interleaved files not (yet) supported."
Obviously, CDemu doesn't support your kind of cuesheet. Bug the authors :)

---

### Post by bogolisk on 2007-01-17
> **HAARP said:**
> As a matter of fact, it is.

Do you mind elaborate a bit more? I don't understand the issue with /dev/cdemuX vs /dev/cdemu/X.

> 
If pmount works for you, feel free to share how you did it. I will then try change my How-To to use pmount :)

Unfortunately you have to change the source code of pmount and rebuild it. How many ppl here are interested in doing that? Also, your cd-mount zenity script would still be needed to bind a file into a cdemu slot.

> 
Eject may unmount the image, but CDemu still has the file loaded into it's corresponding device. Do this more than 8 times, and you can't any more images.

It will disconnect the file, the bug I encountered was a kernel trap but easily fixable (in cdemu.) Eject send CDROMEJECT to cdemu which doesn't recognize it and forwared it to cdrom driver and cdrom driver crapped out when it try to eject a "cdemu disc". What I did was to make CDROMEJECT ioctl an alias to CDEMU_UNLOAD (rebuilding cdemu required.) Eject then would work beautifully: unmount the device, remove /media/cdemuX, eject/unload the image.

---

### Post by HAARP on 2007-01-17
> **bogolisk said:**
> Do you mind elaborate a bit more? I don't understand the issue with /dev/cdemuX vs /dev/cdemu/X.
Well, with /dev/cdemuX it just wouldn't work for me. I spent some time trying to find out what's wrong, but in the end, i just went with creating the right devices on my own. There's not much to it.

> Unfortunately you have to change the source code of pmount and rebuild it. How many ppl here are interested in doing that? Also, your cd-mount zenity script would still be needed to bind a file into a cdemu slot.
And you're asking why people don't use pmount? :P

> It will disconnect the file, the bug I encountered was a kernel trap but easily fixable (in cdemu.) Eject send CDROMEJECT to cdemu which doesn't recognize it and forwared it to cdrom driver and cdrom driver crapped out when it try to eject a "cdemu disc". What I did was to make CDROMEJECT ioctl an alias to CDEMU_UNLOAD (rebuilding cdemu required.) Eject then would work beautifully: unmount the device, remove /media/cdemuX, eject/unload the image.
Could you share this patch? Since we're building CDemu anyway, we may aswell do with it :)

---

### Post by bogolisk on 2007-01-17
> **HAARP said:**
> Well, with /dev/cdemuX it just wouldn't work for me. I spent some time trying to find out what's wrong, but in the end, i just went with creating the right devices on my own. There's not much to it.

I'm thinking about making cdemu a package. In fact I've built one for myself. However, it's kinda pointless since cdemu cannot handle cue/bin files.

> 
And you're asking why people don't use pmount? :P

I'm not sure ppl are willing to download all the *-dev packages (hal, dbus, etc) , patch pmount, then rebuild. Any way what I've changed in pmout was:

```

diff -NruwBb pmount-0.9.13.orig/src/policy.c pmount-0.9.13/src/policy.c
--- pmount-0.9.13.orig/src/policy.c     2006-08-15 17:00:37.000000000 -0400
+++ pmount-0.9.13/src/policy.c  2007-01-16 21:30:22.000000000 -0500
@@ -178,6 +178,8 @@

             snprintf( devfilename, sizeof( devfilename ), "%s/device", devdirname );

+           debug("%s: devfilename = [%s]\n", __func__, devfilename);
+
             /* read out the link */
             if( !sysfs_get_link( devfilename, linkfilename, 1024 ) )
                 sysdev = sysfs_open_device_path( linkfilename );
@@ -370,12 +372,11 @@
     int removable;
     char blockdevpath[PATH_MAX];

+    blockdevpath[0] = '\0';
     dev = find_sysfs_device( device, blockdevpath, sizeof( blockdevpath ) );
-    if( !dev ) {
-        debug( "device_removable: could not find a sysfs device for %s\n", device );
-        return 0;
-    }

+
+    if (dev) {
     debug( "device_removable: corresponding block device for %s is %s\n",
                 device, blockdevpath );

@@ -386,6 +387,15 @@
     if( !removable )
         removable = find_bus_ancestry( dev, hotplug_buses );
     sysfs_close_device( dev );
+    } else if (blockdevpath[0] != '\0') {
+      debug( "device_removable: corresponding block device for %s is %s\n",
+            device, blockdevpath );
+      removable = get_blockdev_attr( blockdevpath, "removable" );
+    } else {
+        debug( "device_removable: could not find a sysfs device for %s\n", device );
+       return 0;
+    }
+

     if( !removable )
         fprintf( stderr, _("Error: device %s is not removable\n"), device );


```




> 
Could you share this patch? Since we're building CDemu anyway, we may aswell do with it :)

```

 diff -uwBb  cdemu-0.8.orig/cdemu_core.c  cdemu-0.8/cdemu_core.c
--- cdemu-0.8.orig/cdemu_core.c 2006-08-04 22:38:56.000000000 -0400
+++ cdemu-0.8/cdemu_core.c      2007-01-17 01:04:01.000000000 -0500
@@ -540,6 +540,7 @@

                        return 0;

+               case CDROMEJECT:
                case CDEMU_UNLOADCD:
                        printk_cdemu(KERN_INFO, "unloaded cd on drive %s\n", cdi->name);
                        return unload_cd(vc);

```

---

### Post by HAARP on 2007-01-17
> **bogolisk said:**
> I'm thinking about making cdemu a package. In fact I've built one for myself. However, it's kinda pointless since cdemu cannot handle cue/bin files.


It can, just not your kind.

Anyway, thanks for sharing the patches.

---

### Post by tee2 on 2007-01-27
I get this error when I try to loadan image into cdemu:

```
tee@tee-laptop:/media/usbdisk$ cdemu 0 bking-ftd.mds
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in ?
    main()
  File "/usr/bin/cdemu", line 127, in main
    libcdemu.load_cd(device, args[-1],os.path.basename(args[-1]))
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 779, in load_cd
    tracks = image_track_data_extractor(raw_entries, bin_filename)
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 712, in extract_track_data_mds
    mode = get_mode_mds(raw_entries[i][1], raw_entries[i][2])
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 562, in get_mode_mds
    raise CDEmu_Error, "Unkown mode number:", mode
TypeError: raise: arg 3 must be a traceback or None

```

---

### Post by HAARP on 2007-01-27
> **tee2 said:**
> I get this error when I try to loadan image into cdemu:

```
tee@tee-laptop:/media/usbdisk$ cdemu 0 bking-ftd.mds
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in ?
    main()
  File "/usr/bin/cdemu", line 127, in main
    libcdemu.load_cd(device, args[-1],os.path.basename(args[-1]))
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 779, in load_cd
    tracks = image_track_data_extractor(raw_entries, bin_filename)
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 712, in extract_track_data_mds
    mode = get_mode_mds(raw_entries[i][1], raw_entries[i][2])
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 562, in get_mode_mds
    raise CDEmu_Error, "Unkown mode number:", mode
TypeError: raise: arg 3 must be a traceback or None

```

Do other images work?

---

### Post by BooVeMan on 2007-01-29
I've got a problem mounting an 4,4GB dvd iso. The error is:
```

user@computer:~/cdemu-0.8$ cdemu -v 0 ../large.dvd.iso
Using /dev/cdemu0
CD Image seems to be a 'ISO-9660 (ISO)' file.
ISO9660 file:  /home/user/large.dvd.iso
Trying to open </home/user/large.dvd.iso>
real (existing) CD image file:  /home/user/large.dvd.iso
reformated tracks:  [[40, 0, 0, 0, 0, 0], [100, 509L, 50L, 22L, 2294272L, 4698669056L]]
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in ?
    main()
  File "/usr/bin/cdemu", line 127, in main
    libcdemu.load_cd(device, args[-1],os.path.basename(args[-1]))
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 792, in load_cd
    c_struct = build_struct(tracks, file , len(tracks) - 1, comment)
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 733, in build_struct
    tracks+=struct.pack(track_struct,*entry)
OverflowError: long int too large to convert
```
any idea? this is cdemu 0.8 with the cdeject patch and yes smaller isos do work.
Thanks!

---

### Post by HAARP on 2007-01-29
> **BooVeMan said:**
> I've got a problem mounting an 4,4GB dvd iso. The error is:
```

user@computer:~/cdemu-0.8$ cdemu -v 0 ../large.dvd.iso
Using /dev/cdemu0
CD Image seems to be a 'ISO-9660 (ISO)' file.
ISO9660 file:  /home/user/large.dvd.iso
Trying to open </home/user/large.dvd.iso>
real (existing) CD image file:  /home/user/large.dvd.iso
reformated tracks:  [[40, 0, 0, 0, 0, 0], [100, 509L, 50L, 22L, 2294272L, 4698669056L]]
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in ?
    main()
  File "/usr/bin/cdemu", line 127, in main
    libcdemu.load_cd(device, args[-1],os.path.basename(args[-1]))
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 792, in load_cd
    c_struct = build_struct(tracks, file , len(tracks) - 1, comment)
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 733, in build_struct
    tracks+=struct.pack(track_struct,*entry)
OverflowError: long int too large to convert
```
any idea? this is cdemu 0.8 with the cdeject patch and yes smaller isos do work.
Thanks!

Looks like an error with CDemu. Bug the author till he turns blue :)

I'm sorry for you guys, but all those tracebacks you post here are useless for me. I can't really code C and am only responsible for the scripts

---

### Post by Tearlow on 2007-02-01
Hey,

First of Thanks for such a awesome Guide! It took me some time to go throu it all but now im finally there =)

There seems to be some problems with some bin files thought (the only thing I had time to test) out of 3 cds I only got 1 to work- and that one worked flawlessly! But while using thous scrips I recived that "Mount failed" is there a way to actualy see the error message?

---

### Post by HAARP on 2007-02-02
It's probably an issue with CDemu itself. Try opening the cue-files with a text editor, see if there are any upper-/lowercase differences to the filename.

No, I can't display the error. It just checks if the directory it gets mounted to contains anything. If there is nothing, it tells you mount failed.

---

### Post by Tearlow on 2007-02-02
> **HAARP said:**
> It's probably an issue with CDemu itself. Try opening the cue-files with a text editor, see if there are any upper-/lowercase differences to the filename.

No, I can't display the error. It just checks if the directory it gets mounted to contains anything. If there is nothing, it tells you mount failed.

Actualy the CUE-file was the first thing I checked.
After some Research (Looking at your Script) I belive I understand it, Nice work ^_^

Now then, All we can do (Well most of us) is to wait for a newer version of CDEMU then...

---

### Post by haani on 2007-02-03
when i type make i get this : any clue how to solve this...

> /bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

---

### Post by Daniel15 on 2007-02-04
> **haani said:**
> when i type make i get this : any clue how to solve this...

This is because Ubuntu Edgy symlinks /bin/sh to dash rather than bash. Dash runs scripts faster, but some features of bash aren't supported (I guess the script to compile CDEmu uses these features). Try this:
```

sudo ln -sf /bin/bash /bin/sh
make
sudo ln -sf /bin/dash /bin/sh

```

This will change /bin/sh to use bash instead, compile CDemu, and then change it back to dash.

---

### Post by haani on 2007-02-04
thanks that fixed it to some extent but then when i type make i get this,

> make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

after that when i type sudo make install i get this:

> Makefile:71: /mk/linux-2.6: No such file or directory
make: *** No rule to make target `/mk/linux-2.6'.  Stop.

---

### Post by patrick295767 on 2007-02-11
Patrick295767 made an howto for cdemu :popcorn:  :guitar: 

[http://forums.debian.net/viewtopic.php?t=12195](http://forums.debian.net/viewtopic.php?t=12195)

---

### Post by rakku-toki &amp; telkio-kuuni on 2007-02-14
hi!

newbie here! 

these scripts don't work for me, i think it's because i always need to type "sudo" for cdemu to load my images (i mean "sudo cdemu 0 /home/user/image.cue"; if i don't, i get this message:"ERROR: for loading a CD I need a drive number or a --device and a cd-image description file"). 

is it normal? what should i change in the scripts to get it to work?

thank you ;)

---

### Post by HAARP on 2007-02-15
> **rakku-toki & telkio-kuuni said:**
> hi!

newbie here! 

these scripts don't work for me, i think it's because i always need to type "sudo" for cdemu to load my images (i mean "sudo cdemu 0 /home/user/image.cue"; if i don't, i get this message:"ERROR: for loading a CD I need a drive number or a --device and a cd-image description file"). 

is it normal? what should i change in the scripts to get it to work?

thank you ;)

Are the access rights for that image set properly? You shouldn't need to do that.  If you launch cdemu directly, the scripts won't even get executed. They are not responsible for this.

---

### Post by darkmaster on 2007-02-16
Well, I'm trying to use cdemu to mount some DC games (Homebrew, legal, such as beats of rage). The problem is that this kinf of cds are mixed audio and data cd. It looks like Ubuntu is unable to mount this kind of media. If I insert a Dreamcast game like this into the cdrom, Ubuntu only asks me if I want to play its music tracks. I tryed to mount manually the CDs but the result was that data was visible and audio tracks maybe no more.... so the game didn't work aniway. 

I then found CDEmu. I must say it works flawlessly for common iso images. But if I try to mount an .nrg Dreamcast game CD, it fails. That's the outpoot:

```
darkmaster@localhost:~/cdi2iso$ cdemu 0 ./image.nrg
darkmaster@localhost:~/cdi2iso$ sudo mount -t iso9660 -o ro /dev/cdemu/0 /media/cdemu0
Password:
mount: wrong fs type, bad option, bad superblock on /dev/cdemu/0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

darkmaster@localhost:~/cdi2iso$ dmesg | tail
[17209552.432000] cdemu:257: cdemu_open: start cdemu0
[17209552.432000] cdemu:266: cdemu_open: end
[17209552.432000] cdemu:612: cdemu_block_media_changed: start cdemu0
[17209552.432000] cdemu:616: cdemu_block_media_changed: going into cdrom_media_changed()
[17209552.432000] cdemu:308: cdemu_media_changed: start cdemu0
[17209552.432000] cdemu:320: cdemu_media_changed: end
[17209552.432000] cdemu:572: cdemu_block_release: start
[17209552.432000] cdemu:349: cdemu_lock_door: start
[17209552.432000] cdemu:275: cdemu_release: start
[17209552.432000] cdemu:282: cdemu_release: end
```

I gave also the suggested command as you can notice. Well, looks like it is not able to mount those kind of games. I even tryed converting a cdi Dreamcast game image to iso using cdi2iso but the iso file, big as much as the cdi one, results unreadable by the package manager and unmountable by CDEmu or the normal mount command. 

Do you think I should ask to the CDEmu staff? Can you help me in any way? Thanks for the wonderfull scripts by the way!

---

### Post by HAARP on 2007-02-16
Are Dreamcast nrg's even normal ISO9660 images?

---

### Post by darkmaster on 2007-02-16
> **HAARP said:**
> Are Dreamcast nrg's even normal ISO9660 images?

Don't have a clue. Common Dreamcast games are in cdi format but nrg is used too. I don't know if they are ISO. What if they are not?

And in general, can Ubuntu or Linux in general mount a mixed content CD?

---

### Post by HAARP on 2007-02-16
> **darkmaster said:**
> Don't have a clue. Common Dreamcast games are in cdi format but nrg is used too. I don't know if they are ISO. What if they are not?


Then only a Dreamcast/Emulator can read them, not the Linux kernel

> And in general, can Ubuntu or Linux in general mount a mixed content CD?

Never tried that, but it should work

---

### Post by darkmaster on 2007-02-16
> **HAARP said:**
> Then only a Dreamcast/Emulator can read them, not the Linux kernel

In windows, daemon tools or alcohool can normally boot this games. We're talking about normal CDs, writted with normal CD burners, not original DC Games.

> **HAARP said:**
> Never tried that, but it should work

No, it doesn't. Insetting a mixed CD in the drive, Ubuntu will only ask you to play its music tracks! But if you manually mount the CD, then Ubuntu recognisez its data tracks and forgets about the audio ones. Adio OR Data, it looks like that.

Even inserting a correctly toasted CD with disc-juggler for windows, Ubuntu still has all of this troubles recognizing it, I guess since it is a mixed data.... dunno! :(

The point is that the .iso image is normally written by Nero, Alcohool, Disc Juggler and mounted by daemon tools, ecc.... all of this for windows! Windows also recognises this kind if burned CD correctly.... how is that that I cannot have Linux do the same thing??? :confused:

---

### Post by HAARP on 2007-02-16
> **darkmaster said:**
> In windows, daemon tools or alcohool can normally boot this games. We're talking about normal CDs, writted with normal CD burners, not original DC Games.


Uhh, I don't know what's the cause then. Bother the devs, it's their job to get it working :>

> No, it doesn't. Insetting a mixed CD in the drive, Ubuntu will only ask you to play its music tracks! But if you manually mount the CD, then Ubuntu recognisez its data tracks and forgets about the audio ones. Adio OR Data, it looks like that.

Even inserting a correctly toasted CD with disc-juggler for windows, Ubuntu still has all of this troubles recognizing it, I guess since it is a mixed data.... dunno! :(

The point is that the .iso image is normally written by Nero, Alcohool, Disc Juggler and mounted by daemon tools, ecc.... all of this for windows! Windows also recognises this kind if burned CD correctly.... how is that that I cannot have Linux do the same thing??? :confused:


Looks like pmount sees the audio tracks and mount sees the data track. Again, I don't know how to get that working.

---

### Post by rakku-toki telkio-kuuni on 2007-02-18
> **HAARP said:**
> Are the access rights for that image set properly?

huh :confused: ... I'll try to figure this out... just don't know how...

when I said "newbie", I really meant that :lolflag:

---

### Post by HAARP on 2007-02-18
> **rakku-toki telkio-kuuni said:**
> huh :confused: ... I'll try to figure this out... just don't know how...

when I said "newbie", I really meant that :lolflag:

OK, let's assume the images is in your home folder, and you are the owner of the file. The owner should have read rights on that file..

---

### Post by amano on 2007-02-19
Wow. This How-To is rather scary. Is there any chance that someone comes up with a .deb file that just works?

---

### Post by AstarothCY on 2007-02-21
So the bottom line is CDemu cannot handle bin/cue?

---

### Post by HAARP on 2007-02-21
> **amano said:**
> Wow. This How-To is rather scary. Is there any chance that someone comes up with a .deb file that just works?
Maybe. I'm not going to, tho

> **AstarothCY said:**
> So the bottom line is CDemu cannot handle bin/cue?

The whole point of CDemu is to handle those files. Where'd you get that idea?

---

### Post by AstarothCY on 2007-02-21
From the top of page 10:

> **bogolisk said:**
> I'm thinking about making cdemu a package. In fact I've built one for myself. However, it's kinda pointless since cdemu cannot handle cue/bin files.

I've tried repeatedly with various different cue/bin files and I just keep getting the "wrong filesystem" error. I've uninstalled and reinstalled cdemu.. still the same. Converting to .iso doesn't seem to work either, the conversion happens but the iso is unusable. Is there no alternative app to handle bin/cue files?

---

### Post by HAARP on 2007-02-21
Maybe there's a new kind of cue-sheets that CDemu can't handle or something. Works fine for me, so I can't really help you guys :/
There are bin2iso converters out there somewhere. You could try those.

---

### Post by AstarothCY on 2007-02-21
could you post an example of a "compatible" cuesheet so that i can compare the formatting?

---

### Post by HAARP on 2007-02-24
> **AstarothCY said:**
> could you post an example of a "compatible" cuesheet so that i can compare the formatting?

Only data track:
```
FILE "TEST.bin" BINARY

  TRACK 01 MODE1/2352

    INDEX 01 00:00:00

```

Mixed Mode:
```
FILE "MW2.BIN" BINARY

  TRACK 01 MODE1/2352

    INDEX 01 00:00:00

  TRACK 02 AUDIO

    FLAGS PRE

    PREGAP 00:02:00

    INDEX 01 12:29:12

  TRACK 03 AUDIO

    FLAGS PRE

    INDEX 00 14:44:73

    INDEX 01 14:46:73

  TRACK 04 AUDIO

    FLAGS PRE

    INDEX 00 17:08:01

    INDEX 01 17:10:01

  TRACK 05 AUDIO

    FLAGS PRE

    INDEX 00 19:03:03

    INDEX 01 19:05:03

  TRACK 06 AUDIO

    FLAGS PRE

    INDEX 00 20:46:44

    INDEX 01 20:48:44

  TRACK 07 AUDIO

    FLAGS PRE

    INDEX 00 23:07:48

    INDEX 01 23:09:48

  TRACK 08 AUDIO

    FLAGS PRE

    INDEX 00 24:57:38

    INDEX 01 24:59:38

  TRACK 09 AUDIO

    FLAGS PRE

    INDEX 00 27:11:50

    INDEX 01 27:13:50

  TRACK 10 AUDIO

    FLAGS PRE

    INDEX 00 28:56:51

    INDEX 01 28:58:51

  TRACK 11 AUDIO

    FLAGS PRE

    INDEX 00 31:13:09

    INDEX 01 31:15:09

  TRACK 12 AUDIO

    FLAGS PRE

    INDEX 00 33:40:09

    INDEX 01 33:42:09

  TRACK 13 AUDIO

    FLAGS PRE

    INDEX 00 35:55:47

    INDEX 01 35:57:47

  TRACK 14 AUDIO

    FLAGS PRE

    INDEX 00 38:11:45

    INDEX 01 38:13:45

  TRACK 15 AUDIO

    FLAGS PRE

    INDEX 00 40:39:23

    INDEX 01 40:41:23

  TRACK 16 AUDIO

    FLAGS PRE

    INDEX 00 42:59:13

    INDEX 01 43:01:13

  TRACK 17 AUDIO

    FLAGS PRE

    INDEX 00 45:05:61

    INDEX 01 45:07:61

  TRACK 18 AUDIO

    FLAGS PRE

    INDEX 00 48:16:01

    INDEX 01 48:18:01

  TRACK 19 AUDIO

    FLAGS PRE

    INDEX 00 50:17:66

    INDEX 01 50:19:66

  TRACK 20 AUDIO

    FLAGS PRE

    INDEX 00 52:58:02

    INDEX 01 53:00:02

  TRACK 21 AUDIO

    FLAGS PRE

    INDEX 00 55:18:26

    INDEX 01 55:20:26

  TRACK 22 AUDIO

    FLAGS PRE

    INDEX 00 57:27:41

    INDEX 01 57:29:41

  TRACK 23 AUDIO

    FLAGS PRE

    INDEX 00 59:34:72

    INDEX 01 59:36:72

  TRACK 24 AUDIO

    FLAGS PRE

    INDEX 00 61:33:60

    INDEX 01 61:35:60

  TRACK 25 AUDIO

    FLAGS PRE

    INDEX 00 64:37:06

    INDEX 01 64:39:06

  TRACK 26 AUDIO

    FLAGS PRE

    INDEX 00 66:46:18

    INDEX 01 66:48:18

  TRACK 27 AUDIO

    FLAGS PRE

    INDEX 00 68:46:16

    INDEX 01 68:48:16
```

---

### Post by AstarothCY on 2007-02-24
Identical to my cuesheet. No idea why it's not working.

```
mount: wrong fs type, bad option, bad superblock on /dev/cdemu/0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

bin file works perfectly under windows, and actually i can just rename the bin file to .mpg and watch it with VLC, but i cant mount it. I have the exact same problem with other .bin files with various kinds of content.

---

### Post by HAARP on 2007-02-25
Dang! People have problems with mounting stuff and I can't figure it out...
Does anyone have a small cue/bin image that doesn't work and can send it to me for testing?

---

### Post by patrick295767 on 2007-02-25
A good howto by patrick295767 for the frontend of cdemu there : 
[http://forums.debian.net/viewtopic.php?t=12195&highlight=cdemu](http://forums.debian.net/viewtopic.php?t=12195&highlight=cdemu)

Enjoy !!

---

### Post by SSamiK on 2007-02-25
Thanks for a great howto! :) 
Had a bit of a problem getting it to work with 2.6.20-8 (feisty). 
 ```
sudo create_cdemu_devs.sh
FATAL: Error inserting cdemu (/lib/modules/2.6.20-8-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg:
cdemu: Unknown symbol generic_file_read
```

Found a solution in [[COLOR="RoyalBlue"]the gentoo forums[/COLOR]]("http://forums.gentoo.org/viewtopic-t-519565.html?sid=b791467f487342ca3fe1dc887e30d3e9") witch solved my troubles. (second post. :-) )

---

### Post by Jengu on 2007-02-25
I haven't read through the thread but just in case nobody has suggested it yet: File a bug with the cdemu guys about the udev trouble so the hack to fix that isn't necessary, and submit your nautilus-actions script to them. It'd be nice to see it become part of the cdemu package, or have a separate package for installing them :)

---

### Post by HAARP on 2007-03-01
> **Jengu said:**
> or have a separate package for installing them :)

The problem with that is, users need to install the scripts. I don't know where a common all-users directory for nautilus scripts is (if it even exists) so I can't do that.

> and submit your nautilus-actions script to them. It'd be nice to see it become part of the cdemu package, 

I doubt they'd do that.

---

### Post by yabbadabbadont on 2007-03-03
> **AstarothCY said:**
> Identical to my cuesheet. No idea why it's not working.

```
mount: wrong fs type, bad option, bad superblock on /dev/cdemu/0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

bin file works perfectly under windows, and actually i can just rename the bin file to .mpg and watch it with VLC, but i cant mount it. I have the exact same problem with other .bin files with various kinds of content.

From your description it sounds like an image of a (s)vcd.  If so, this is from the cdemu FAQ:
> Q: I am trying to mount an [S]VCD but the mount command keeps failing!
A: Of course it does not work ! An [S]VCD contains no real filesystem. You need to read it in raw mode.
e.g. use MPlayer or xine to watch the movie. Just point the player to the virtual device (i.e. /dev/cdemu/0)
But Windows does you say !? Windows lies to you ;-) Windows has the problem that it can't read cds in raw mode, so the ATAPI driver creates a virtual file system, so Windows programs can read it. This layer is not needed in Linux since we can just handle the raw format with our media players. ;-)

---

### Post by quaestor on 2007-03-04
> 
>>or have a separate package for installing them

>The problem with that is, users need to install the scripts. I don't know where a
>common all-users directory for nautilus scripts is (if it even exists) so I can't do that.
/usr/share/nautilus-scripts - This should be system-wide on any .deb system...
Any user with '**sudo**' rights can just copy the scripts there (I think many people may not realize that
any folder full of scripts in this directory will show up as a sub-menu, so '**/usr/share/nautilus-scripts/cdemu**' with your scripts in it would create a 'cdemu' sub-menu
in the nautilus right-click menu)
Install scripts per-user with '**nautilus-script-manager**'
And if someone made a .deb, this could all be part of the install

> 
>>and submit your nautilus-actions script to them. It'd be nice to see it become part\
>>of the cdemu package,

>I doubt they'd do that.I really can't imagine why not...

q

---

### Post by AstarothCY on 2007-03-05
> **yabbadabbadont said:**
> From your description it sounds like an image of a (s)vcd.  If so, this is from the cdemu FAQ:

Thanks, it was an SVCD and that seems to make sense, yet it still doesn't work. It's an improvement in that I can open the disc using VLC but I get no image and the sound is just static. Xine and Totem won't even open it.

---

### Post by rakku-toki telkio-kuuni on 2007-03-06
> **HAARP said:**
> Are the access rights for that image set properly? You shouldn't need to do that.  If you launch cdemu directly, the scripts won't even get executed. They are not responsible for this.

uh. sorry. i've been away for a while.

if fact, i've found out that i can't even "make" without "sudo". maybe i have a too-restricted-access-rights issue here. i think i'll need to start a new thread. 

thank you for the support, HAARP!!

---

### Post by auraithx on 2007-03-11
I get this error when doing "make"

```
glasgowm@glasgowm-desktop:~/cdemu-0.8$ make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/glasgowm/cdemu-0.8/cdemu_core.o
  CC [M]  /home/glasgowm/cdemu-0.8/cdemu_mod.o
  CC [M]  /home/glasgowm/cdemu-0.8/cdemu_proc.o
  LD [M]  /home/glasgowm/cdemu-0.8/cdemu.o
  Building modules, stage 2.
  MODPOST
  CC      /home/glasgowm/cdemu-0.8/cdemu.mod.o
  LD [M]  /home/glasgowm/cdemu-0.8/cdemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic
```

---

### Post by karaluh on 2007-03-17
HAARP,
have you tried this:
[http://cdemu.kabelkaos.net]("http://cdemu.kabelkaos.net")

---

### Post by U5tabil on 2007-03-24
Iv done the instalation and the test image works.

But when i try to mount a .cue file of an .mp3 that i have im getting an error saying:

Mount failed.

Any sugestion on how to fix this?

---

### Post by shiversc on 2007-03-24
> **karaluh said:**
> HAARP,
have you tried this:
[http://cdemu.kabelkaos.net]("http://cdemu.kabelkaos.net")

What is that?
:confused:

---

### Post by karaluh on 2007-03-24
> **shiversc said:**
> What is that?
:confused:

Think of it as of a cdemu 0.9

---

### Post by U5tabil on 2007-03-24
> **U5tabil said:**
> Iv done the instalation and the test image works.

But when i try to mount a .cue file of an .mp3 that i have im getting an error saying:

Mount failed.

Any sugestion on how to fix this?

I tryed burning the .cue file to a cd but that failed to. But when i play the .cue file in amarok the list of songs comes up. 

But why cant i emu that .cue file? Mount failed.

---

### Post by bomanizer on 2007-03-28
> **MarkoSK said:**
> hehe :D it works :D :D
hehe...so all it had to do is to make it too look at new kernel headers...

tnx :D

What did you change? Something in the makefile?

---

### Post by modology on 2007-04-05
Hi, I'm using Fiesty and I have some problems with CDEMU 0.8.
After download and unpack. I sucessfully to do "make" and "make install"


 then I type in "modprobe cdemu
" then I have this error messages
> FATAL: Error inserting cdemu (/lib/modules/2.6.20-13-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)



then
> root@ubuntu:/home/modology/Desktop/cdemu-0.8# ./create_cdemu_devs.sh
You have udev, nodes will be created automagically


I dont know how to fix this error.
I attemp to mount MDS file then I have this problem. 
> root@ubuntu:/home/modology/Desktop/cdemu-0.8# cdemu 0 Warcraft\ III.mds
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in <module>
    main()
  File "/usr/bin/cdemu", line 124, in main
    device = libcdemu.get_device_from_drive_number(args[0])
  File "/usr/lib/python2.5/site-packages/libcdemu.py", line 755, in get_device_from_drive_number
    raise CDEmu_Error, "Do you have cdemu module loaded? - could't find block device. If you've no devfs/udev make sure you created them."
libcdemu.CDEmu_Error: Do you have cdemu module loaded? - could't find block device. If you've no devfs/udev make sure you created them.


I hope someone can help me out

---

### Post by slicers on 2007-04-10
apply this patch

> --- cdemu_core.c.orig   2007-04-11 10:24:03.000000000 +0900
+++ cdemu_core.c        2007-04-11 10:26:01.000000000 +0900
@@ -486,11 +486,11 @@
                        }

                        if (cmd == CDROMREADRAW) {
-                               tmp = generic_file_read(vc->backing_file, (void*)arg, CD_FRAMESIZE_RAW, &position);
+                               tmp = do_sync_read(vc->backing_file, (void*)arg, CD_FRAMESIZE_RAW, &position);
                                if (tmp != CD_FRAMESIZE_RAW)
                                        dprintk("only read %i bytes\n",tmp);
                        } else {        /*CDROMREADCOOKED*/
-                               tmp = generic_file_read(vc->backing_file, (void*)arg, CD_FRAMESIZE, &position);
+                               tmp = do_sync_read(vc->backing_file, (void*)arg, CD_FRAMESIZE, &position);
                                if (tmp != CD_FRAMESIZE)
                                        dprintk("only read %i bytes\n",tmp);
                        }


---

### Post by HAARP on 2007-04-11
Sorry for being absent for a while.

> HAARP,
have you tried this:
[http://cdemu.kabelkaos.net](http://cdemu.kabelkaos.net)

No. Where'd you get this?

---

### Post by rodgersan on 2007-04-11
> **HAARP said:**
> Sorry for being absent for a while.



No. Where'd you get this?


subscribing to the mailing list, I supposed as many here...

Somebody successed to make it working under feisty?

---

### Post by soomon on 2007-04-16
> **slicers said:**
> 
apply this patch

Quote:
--- cdemu_core.c.orig 2007-04-11 10:24:03.000000000 +0900
+++ cdemu_core.c 2007-04-11 10:26:01.000000000 +0900
@@ -486,11 +486,11 @@
}

if (cmd == CDROMREADRAW) {
- tmp = generic_file_read(vc->backing_file, (void*)arg, CD_FRAMESIZE_RAW, &position);
+ tmp = do_sync_read(vc->backing_file, (void*)arg, CD_FRAMESIZE_RAW, &position);
if (tmp != CD_FRAMESIZE_RAW)
dprintk("only read %i bytes\n",tmp);
} else { /*CDROMREADCOOKED*/
- tmp = generic_file_read(vc->backing_file, (void*)arg, CD_FRAMESIZE, &position);
+ tmp = do_sync_read(vc->backing_file, (void*)arg, CD_FRAMESIZE, &position);
if (tmp != CD_FRAMESIZE)
dprintk("only read %i bytes\n",tmp);
} 

hi, i also have this problem, i also tried to compile the cdemu 0.8 / cdemu module.

how do i have to apply this patch??
save it into an .sh file and execute ist?

thanks & greets,
soomon

---

### Post by Civean on 2007-04-21
Hi,
I have finally read through this entire thread.  The cdemu program and scripts work excellent on my new, shiny Feisty Fawn, however I have encountered the same bug as many others here. Both cue/bin and mds files show severe data corruption of the files on the mounted volume.

I used the install method described in the first post, except for the change outlined in this post needed get the make to work: (apparantly due to some changes in the kernel) [http://forums.gentoo.org/viewtopic-t-519565.html?sid=b791467f487342ca3fe1dc887e30d3e9]("http://forums.gentoo.org/viewtopic-t-519565.html?sid=b791467f487342ca3fe1dc887e30d3e9")

The strange thing is, I can't find any mention of this data corruption bug anywhere else on the internet, only here in this specific forum thread, with this specific install method. Users of gentoo, debian, etc doesn't seem to experience this bug, so I have a hard time believing there is something wrong with cdemu 0.8.

Since I have also not found any other way of installing cdemu on ubuntu, I'm therefore asking you all out there, can someone with more technical proficiency look into this issue? To not be able to load mds, cue/bin etc is a total deal breaker for me and many others who want or just has to migrated to ubuntu, unless there is some other method I have missed.

---

### Post by rodgersan on 2007-04-21
> **Civean said:**
> Hi,
I have finally read through this entire thread.  The cdemu program and scripts work excellent on my new, shiny Feisty Fawn, however I have encountered the same bug as many others here. Both cue/bin and mds files show severe data corruption of the files on the mounted volume.

I used the install method described in the first post, except for the change outlined in this post needed get the make to work: (apparantly due to some changes in the kernel) [http://forums.gentoo.org/viewtopic-t-519565.html?sid=b791467f487342ca3fe1dc887e30d3e9]("http://forums.gentoo.org/viewtopic-t-519565.html?sid=b791467f487342ca3fe1dc887e30d3e9")

The strange thing is, I can't find any mention of this data corruption bug anywhere else on the internet, only here in this specific forum thread, with this specific install method. Users of gentoo, debian, etc doesn't seem to experience this bug, so I have a hard time believing there is something wrong with cdemu 0.8.

Since I have also not found any other way of installing cdemu on ubuntu, I'm therefore asking you all out there, can someone with more technical proficiency look into this issue? To not be able to load mds, cue/bin etc is a total deal breaker for me and many others who want or just has to migrated to ubuntu, unless there is some other method I have missed.


I didn't get cdemu working on my edgy with the last cdemu stable and experimental version 3 monthes ago but you can try thoses tarballs: [http://kabelkaos.net/cdemu/experimental/](http://kabelkaos.net/cdemu/experimental/) (from the mailing-list, there are some special instructions for ubuntu)

I will install feisty in the next couple of days and I hope cdemu will work on it. Please inform us about your progress, I'm getting sick from not being able to mount cue/bin/nrg images.

---

### Post by Civean on 2007-04-22
As of now, CDemu 0.8 installed from the guide in this thread and with the modification from the link in my previous post "works", except it corrupts data loaded from cue/bin and mds images. (possibly more)

As I have understood it from reading around, CDemu 0.8 is sort of abandoned and the developers started working on another implementation, which so far has resulted in the files from [http://kabelkaos.net/cdemu/experimental/]("http://kabelkaos.net/cdemu/experimental/")

So far I have been able to ./configure and make, make install 3 of the 5 packages, by downloading a whole bunch of libraries. 2 however, fail at the make stage with similar error messages:

xxxx@nc6000:~/Program/cdemu-0.9/gcdemu$ sudo make
Making all in pixmaps
make[1]: Entering directory `/home/xxxx/Program/cdemu-0.9/gcdemu/pixmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/xxxx/Program/cdemu-0.9/gcdemu/pixmaps'
Making all in po
make[1]: Entering directory `/home/xxxx/Program/cdemu-0.9/gcdemu/po'
file=`echo sl | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file sl.po
/bin/sh: -o: not found
make[1]: *** [sl.gmo] Error 127
make[1]: Leaving directory `/home/xxxx/Program/cdemu-0.9/gcdemu/po'
make: *** [all-recursive] Error 1

I suspect this is something unrelated to the specific program, anyone have a solution for this? Would be greatly helpful!

---

### Post by olejorgen on 2007-04-22
I can't get this to work in feisty :(

```
ole@ole:~/download/software/cdemu-0.8$ make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/ole/download/software/cdemu-0.8/cdemu_core.o
/home/ole/download/software/cdemu-0.8/cdemu_core.c: In function &#8216;cdemu_ioctl&#8217;:
/home/ole/download/software/cdemu-0.8/cdemu_core.c:489: warning: implicit declaration of function &#8216;generic_file_read&#8217;
  CC [M]  /home/ole/download/software/cdemu-0.8/cdemu_mod.o
  CC [M]  /home/ole/download/software/cdemu-0.8/cdemu_proc.o
  LD [M]  /home/ole/download/software/cdemu-0.8/cdemu.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/home/ole/download/software/cdemu-0.8/cdemu.ko] undefined!
  CC      /home/ole/download/software/cdemu-0.8/cdemu.mod.o
  LD [M]  /home/ole/download/software/cdemu-0.8/cdemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
ole@ole:~/download/software/cdemu-0.8$ sudo make install > install_output
Password:
/bin/sh: Syntax error: Bad fd number
ole@ole:~/download/software/cdemu-0.8$ sudo modprobe cdemu 
FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ole@ole:~/download/software/cdemu-0.8$ dmesg | tail
[105650.842762] VFS: Can't find ext3 filesystem on dev loop0.
[105705.625942] attempt to access beyond end of device
[105705.625949] loop0: rw=0, want=154, limit=153
[105705.626131] isofs_fill_super: bread failed, dev=loop0, iso_blknum=38, block=76
[105714.980063] cramfs: wrong magic
[105714.980816] VFS: Can't find ext3 filesystem on dev loop0.
[105714.981530] attempt to access beyond end of device
[105714.981534] loop0: rw=0, want=154, limit=153
[105714.981689] isofs_fill_super: bread failed, dev=loop0, iso_blknum=38, block=76
[105997.295101] cdemu: Unknown symbol generic_file_read
ole@ole:~/download/software/cdemu-0.8$ cat install_output 
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.20-15-generic/misc/cdemu.ko
install -D -m 644 libcdemu.py /usr/lib/python2.5/site-packages/libcdemu.py
install -D -m 755 cdemu /usr/bin/cdemu
install -D -m 755 create_cdemu_devs.sh /usr/bin/create_cdemu_devs.sh
sh create_cdemu_devs.sh
You have udev, nodes will be created automagically

```

---

### Post by Civean on 2007-04-22
Don bother with cdemu 0.8, it gives corrupted files on the mounted volumes. (See examples in the middle of this thread) 

But if you want to proceed, you should try the tip from [http://forums.gentoo.org/viewtopic-t...e1dc887e30d3e9]("http://forums.gentoo.org/viewtopic-t...e1dc887e30d3e9")
(Second post)

I don know if this will help, but since you get some errors relating to the the generic_file_read, give it a try...

I have given up on cdemu 0.8, but I keep trying with the expermimental userland version mentioned earlier. I would greatly appreciate it if someone could take a look at my problem earlier, I really have no idea how to proceed.

---

### Post by Civean on 2007-04-25
Since CDEmu seems broken, I continued to search and found this:

[http://ubuntuforums.org/showthread.php?t=413015](http://ubuntuforums.org/showthread.php?t=413015)

Unfortunatly, it's a KDE application. It starts alright, and seems to work, but nothing happens when I try to mount the images. But for KDE users I think is this is the answer to the cd-image mounting dilemma!

//EDIT
Scratch that, AcetoneISO merely converts the other formats to ISO, then mounts them. So, it's not the solution we are looking for.

---

### Post by rodgersan on 2007-04-25
new experimental builds.... I will give it a try asap and I hope it will work...

[http://kabelkaos.net/cdemu/experimental/](http://kabelkaos.net/cdemu/experimental/)

---

### Post by karlhm76 on 2007-05-07
Not working for me.
It seems to compile ok, but when I try and load the module I get this error:

FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Can't load module

This only happened after I upgraded to fiesty. It worked great in edgy, but I did experience corruption on some bin/cue files, as mentioned elsewhere.

I'll list the output at different stages:

make:
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/home/karl/cdemu-0.8/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

sudo make install:
/bin/sh: Syntax error: Bad fd number
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.20-15-generic/misc/cdemu.ko
install -D -m 644 libcdemu.py /usr/lib/python2.5/site-packages/libcdemu.py
install -D -m 755 cdemu /usr/bin/cdemu
install -D -m 755 create_cdemu_devs.sh /usr/bin/create_cdemu_devs.sh
sh create_cdemu_devs.sh
You have udev, nodes will be created automagically

then sudo modprobe cdemu:
FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)


dmesg gives me this:
[237390.888782] cdemu: Unknown symbol generic_file_read

obviously looks like the problem is related to the generic_file_read symbol. I have to go to work now, but I may be able to do some quick searches on what this all means. In the meantime can anyone offer any assistance?

Thanks

---

### Post by rodgersan on 2007-05-07
> **karlhm76 said:**
> Not working for me.
It seems to compile ok, but when I try and load the module I get this error:

FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Can't load module

This only happened after I upgraded to fiesty. It worked great in edgy, but I did experience corruption on some bin/cue files, as mentioned elsewhere.

I'll list the output at different stages:

make:
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/home/karl/cdemu-0.8/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

sudo make install:
/bin/sh: Syntax error: Bad fd number
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.20-15-generic/misc/cdemu.ko
install -D -m 644 libcdemu.py /usr/lib/python2.5/site-packages/libcdemu.py
install -D -m 755 cdemu /usr/bin/cdemu
install -D -m 755 create_cdemu_devs.sh /usr/bin/create_cdemu_devs.sh
sh create_cdemu_devs.sh
You have udev, nodes will be created automagically

then sudo modprobe cdemu:
FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)


dmesg gives me this:
[237390.888782] cdemu: Unknown symbol generic_file_read

obviously looks like the problem is related to the generic_file_read symbol. I have to go to work now, but I may be able to do some quick searches on what this all means. In the meantime can anyone offer any assistance?

Thanks

dropping cdemu 0.8 for the last build would be a better choice...

---

### Post by anomalyconcept on 2007-05-15
Hi, just thought I'd weigh in on this since I had the same problem.

Apparently generic_file_read() is no longer in the kernel (not sure after which version), but a [helpful post]("http://forums.gentoo.org/viewtopic-p-3767131.html?sid=d5cfe4877e1aec54496fbf8169b121c7#3767131") at the Gentoo forums cleared this up.

To paraphrase:
replace generic_file_read() with do_sync_read() in cdemu_core.c to fix this issue.

Hope this helps.

---

### Post by celiothrkn on 2007-05-16
Slightly confused on this generic_file_read() error. I did check the link to the Gentoo forums.

But when I opened cdemu_core.c and I Found no
[INDENT]generic_file_read()[/INDENT]

So I Replaced all
[INDENT]generic_file_read[/INDENT]
with
[INDENT]do_sync_read[/INDENT]

Is that right? I'm still getting the error message
[INDENT]FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/INDENT]

**EDIT:** My bad. Afterwards, you need to re-"sudo make" and re-"sudo make install" with the newly edited cdemu_core.c

---

### Post by karlhm76 on 2007-05-18
thanks for all the help guys - invaluable.

I have now got cdemu working, the replacing of the function as outlined in the gentoo forum, did the trick.


Thanks again

---

### Post by Civean on 2007-05-19
Still, not using CDemu 0.8 and instead use the new 1.0 userspace builds would probably fix the data corruption problem. It seems other people around here have gotten this version to work, however it does not for me. I can't install CDemu 1.0, I have no idea what to do after I ./configure, make, make install the 5 different modules. How do I start the GUI program? How do I load images? Why does it say the daemon is not running? Etc...

If someone could write up a small manual on how to get CDemu 1.0 from tar.gz -> loaded cd image (all steps in between) I would be very, very grateful.

/C

---

### Post by sojyujai on 2007-05-23
Doing a bit of googling I came across this blog posting:  [http://mniess.googlepages.com/cdemuforubuntu7.04](http://mniess.googlepages.com/cdemuforubuntu7.04)
Where someone has made .deb files for userspace-cdemu 1.0.0 for feisty.

I tried it out - installation was a snap - but when put to use it I'm getting the following error when I try to load the cue file from a bin/cue image:

```
 Failed to load image /media/sda7/Movies/insomnia_2002_Kvcd/videocd.cue to device 0:
org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

Afterward the gCDEmu Applet becomes non-responsive and gets greyed out on my panel, so far the only way I've managed to get it working again is a reboot.

Any suggestions on how to fix the error would be appreciated.

---

### Post by asthro on 2007-05-25
> **qrm said:**
> any help would be greatly appreciated

for the "bad fd number" error : 

rm /usr/bin/sh
sudo ln -s /bin/bash sh

et voilou

---

### Post by muted on 2007-05-26
I have come so far in Feisty that I can mount the demo .cue. I have a problem though:

I try to use the mount script in nautilus, and get the error message "You can not mount any more images." allthough I have not mounted a single cdemu image anywhere (the demo .cue is already unmounted again;))

Any ideas as to why the script thinks i have all image slots mounted?

---

### Post by Goofee691 on 2007-06-08
hi all i am using feisty on my amd64 for awhile and cant seem to get cdemu to work
modprobe fails
here is what i have tried to do with the output of it

sean@num4:~/Desktop/cdemu-0.8$ make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/sean/Desktop/cdemu-0.8/cdemu_core.o
/home/sean/Desktop/cdemu-0.8/cdemu_core.c: In function ‘cdemu_transfer_bio’:
/home/sean/Desktop/cdemu-0.8/cdemu_core.c:179: warning: format ‘%i’ expects type ‘int’, but argument 3 has type ‘ssize_t’
/home/sean/Desktop/cdemu-0.8/cdemu_core.c: In function ‘cdemu_ioctl’:
/home/sean/Desktop/cdemu-0.8/cdemu_core.c:489: warning: implicit declaration of function ‘generic_file_read’
  CC [M]  /home/sean/Desktop/cdemu-0.8/cdemu_mod.o
  CC [M]  /home/sean/Desktop/cdemu-0.8/cdemu_proc.o
  LD [M]  /home/sean/Desktop/cdemu-0.8/cdemu.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/home/sean/Desktop/cdemu-0.8/cdemu.ko] undefined!
  CC      /home/sean/Desktop/cdemu-0.8/cdemu.mod.o
  LD [M]  /home/sean/Desktop/cdemu-0.8/cdemu.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
sean@num4:~/Desktop/cdemu-0.8$ sudo make install
/bin/sh: Syntax error: Bad fd number
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.20-16-generic/misc/cdemu.ko
install -D -m 644 libcdemu.py /usr/lib/python2.5/site-packages/libcdemu.py
install -D -m 755 cdemu /usr/bin/cdemu
install -D -m 755 create_cdemu_devs.sh /usr/bin/create_cdemu_devs.sh
sh create_cdemu_devs.sh
You have udev, nodes will be created automagically
sean@num4:~/Desktop/cdemu-0.8$ modprobe cdemu
FATAL: Error inserting cdemu (/lib/modules/2.6.20-16-generic/misc/cdemu.ko): Operation not permitted

any help would be apreciated

---

### Post by rodgersan on 2007-06-09
Try following this (devs instructions):

You build in order: libmirage, cdemu-daemon, cdemu-kernel, cdemu-client

For each directory:
Now since this is a snapshot there isn't any configure script, so we 
have to make that one first, so run ./autogen.sh
This should result in a working ./configure script among other things. I 
had to install some extra packages like autoconf, automake, docbook, 
glib, gobject, libsysfs etc.
./configure --prefix=/usr
(for cdemu-daemon use instead "./configure --prefix=/ --exec-prefix=/usr")
make
sudo make install

that should be it. now to get cdemu up and running, execute as root:
/etc/init.d/cdemu-daemon start
that works for fedora linux at least
for ubuntu linux there is another init script that can be used instead.
and now you should be able to use the "cdemu" program to load cd-images 
to devices.

---

### Post by Jokeaflorias on 2007-06-16
When I type sudo create_cdemu_devs.sh I get this:

FATAL: Error inserting cdemu (/lib/modules/2.6.20-16-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Can't load module

I've been working on getting a program like this working for days, and I would really appreciate some help. Thanks.

P.S. I'm running Feisty Fawn, but wouldn't that have it's own kernel if it was just an upgrade from Edgy?

---

### Post by mouseclone on 2007-06-17
Same error
```

mouseclone@mouseclone-desktop:~/cdemu-0.8$ sudo make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/home/mouseclone/cdemu-0.8/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
mouseclone@mouseclone-desktop:~/cdemu-0.8$ sudo make install
/bin/sh: Syntax error: Bad fd number
**** Installing files ****
install -D -m 644 cdemu.ko /lib/modules/2.6.20-16-generic/misc/cdemu.ko
install -D -m 644 libcdemu.py /usr/lib/python2.5/site-packages/libcdemu.py
install -D -m 755 cdemu /usr/bin/cdemu
install -D -m 755 create_cdemu_devs.sh /usr/bin/create_cdemu_devs.sh
sh create_cdemu_devs.sh
You have udev, nodes will be created automagically
mouseclone@mouseclone-desktop:~/cdemu-0.8$ sudo modprobe cdemu 
FATAL: Error inserting cdemu (/lib/modules/2.6.20-16-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Ubuntu 7.04.  Also, I have made sure that I have header files.

---

### Post by utopial on 2007-06-25
same error

---

### Post by gbesso on 2007-06-25
I had that too, I found the solution here
[http://www.vprajan.org/?p=76]("http://www.vprajan.org/?p=76")

---

### Post by JNik on 2007-07-05
I get the following error when I try to mount a DVD iso:

```
Traceback (most recent call last):
  File "/usr/bin/cdemu", line 132, in ?
    main()
  File "/usr/bin/cdemu", line 127, in main
    libcdemu.load_cd(device, args[-1],os.path.basename(args[-1]))
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 792, in load_cd
    c_struct = build_struct(tracks, file , len(tracks) - 1, comment)
  File "/usr/lib/python2.4/site-packages/libcdemu.py", line 733, in build_struct
    tracks+=struct.pack(track_struct,*entry)
OverflowError: long int too large to convert

```

Does CDemu work with DVD isos too?

---

### Post by francky_51 on 2007-07-11
**/bin/sh: Syntax error: Bad fd number**
Ubuntu uses dash instead of bash.
Change the /bin/sh symlink to point to the bash shell instead of the current dash shell.

---

### Post by yabbadabbadont on 2007-07-11
> **francky_51 said:**
> **/bin/sh: Syntax error: Bad fd number**
Ubuntu uses dash instead of bash.
Change the /bin/sh symlink to point to the bash shell instead of the current dash shell.

The proper way to do this is to run ```
sudo dpkg-reconfigure dash
``` and then select No when it asks if it should be the default /bin/sh.  :D

---

### Post by Pheodax on 2007-07-13
> **gbesso said:**
> I had that too, I found the solution here
[http://www.vprajan.org/?p=76]("http://www.vprajan.org/?p=76")
This fixed the problem here. It now works like a charm.

The scripts are awesome! :)

---

### Post by ElemonGW on 2007-07-13
Many many thanks for that. I have tried to install cdemu at the past bu with no luck. Now, thnx to this guide I managed to intsall them and make them work perfectly. Thnx!!!

---

### Post by madubuntuer on 2007-07-22
The instructions are for ebuild which isn't installed. I cant install it using apt-get 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ebuild

The script appearto use ebuild and emake which are both not obtainable via apt-get. Aren't they specific to gentoo. So what am I supposed to with that patch then?

I did try the replace the function name but I get this when I do a checkinstall
(Reading database ... 111640 files and directories currently installed.)
Unpacking cdemu (from .../cdemu_0.8-1_amd64.deb) ...
dpkg: error processing /home/steven/cdemu/cdemu-0.8/cdemu_0.8-1_amd64.deb (--install):
 trying to overwrite `/lib/modules/2.6.20-15-generic/modules.seriomap', which is also in package linux-image-2.6.20-1
5-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/steven/cdemu/cdemu-0.8/cdemu_0.8-1_amd64.deb

---

### Post by jbysmith on 2007-07-27
Brilliant, thanks for this :)

The one and only program I missed from Windows was Daemon-Tools for mounting image files, this comes pretty close.

---

### Post by vadania on 2007-08-25
Hello,

I'm trying to insstall CDemu 0.8 on my Ubuntu 7.04.
When I go to the extracted folder and try make, I get  the following error:

> [HTML][HTML]```
bogdan@bogdandt:/tmp/cdemu$ sudo make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/tmp/cdemu/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'

```[/HTML][/HTML]
:confused:

---

### Post by vadania on 2007-08-25
Hello,

I'm trying to insstall CDemu 0.8 on my Ubuntu 7.04.
When I go to the extracted folder and try make, I get  the following error:

> [HTML][HTML]```
bogdan@bogdandt:/tmp/cdemu$ sudo make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
/bin/sh: Syntax error: Bad fd number
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "generic_file_read" [/tmp/cdemu/cdemu.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'

```[/HTML][/HTML]
What could this be from? How can I repair it?
:confused:

---

### Post by Civean on 2007-08-25
vadania, this problem is described earlier in the thread. The problem is that the linux kernel no longer contains the command "generic_file_read". The solution is written earlier in the thread, see for example the second post at [this page]("http://ubuntuforums.org/showthread.php?t=276743&page=16"). 

However:** I strongly recommend against using CDEmu 0.8!** This version contains a bug that on some systems shows corrupt data from the loaded images, rendering th program useless. This bug is described in the beginning of this thread, and renders the program totally useless except for .iso files. The developers won't fix this bug since they have remade CDEmu from the ground up, the so called "userspace-cdemu" which can be found at 

[http://www.kabelkaos.net/cdemu/]("http://www.kabelkaos.net/cdemu/"). (Use the vhba one, this is the newest)
 
.deb files exist for 7.04 from this address:

 [http://mniess.googlepages.com/cdemuforubuntu7.04]("http://mniess.googlepages.com/cdemuforubuntu7.04")

So far I haven't been successful in making the new CDEmu work, but I know that others have. I have no idea why the developers haven't just edited the homepage to clarify the situation. Judging from the CDEmu mailing lists (found at "lists" from the CDEmu homepage) though the team are soon ready to release userspace-cdemu as CDEmu 1.0, and hopefully then end this confusion with CDEmu 0.8.

---

### Post by Beholder87 on 2008-02-06
can anyone help me??? i have an error message when i try to start cdmud about: "Failed to open control device."
i posted it in another topic: [http://ubuntuforums.org/showthread.php?p=4281068&posted=1#post4281068](http://ubuntuforums.org/showthread.php?p=4281068&posted=1#post4281068)
thanks

---

### Post by fermulator on 2008-09-06
Hey great post!  But unfortunately it doens't work with newer versions of CDemu.

I *believe* this does ...[http://www.grumz.net/?q=node/307&PHPSESSID=2a686cc22630a97288a36c4312068358](http://www.grumz.net/?q=node/307&PHPSESSID=2a686cc22630a97288a36c4312068358)

---

### Post by HAARP on 2008-10-02
Hello, original author here. This Howto is very old. I've since moved to another distro, but I have the newer CDemu working there. I wrote a new Howto with a new set of scripts for that distro, but I'm sure it can be adapted for Ubuntu. Get it here:
[http://forums.gentoo.org/viewtopic-t-695369-highlight-cdemu.html?sid=75e16b05fad7a496a57482a455bcd9db](http://forums.gentoo.org/viewtopic-t-695369-highlight-cdemu.html?sid=75e16b05fad7a496a57482a455bcd9db)

Have Fun!

---

