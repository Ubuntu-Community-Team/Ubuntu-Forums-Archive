---
title: "ndiswrapper problems"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by stoneofshadow on 2008-06-11
i have been trying to get my wireless internet working with these instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

that was working until step 3 i think when it says to put in some code about the ndiswrapper
i did a search in the home folder/file system for ndiswrapper and it only had two .ko files there. i also dont think i have a path

---

### Post by Otto-C on 2008-06-11
> **stoneofshadow said:**
> i have been trying to get my wireless internet working with these instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

that was working until step 3 i think when it says to put in some code about the ndiswrapper
i did a search in the home folder/file system for ndiswrapper and it only had two .ko files there. i also dont think i have a path

Suggest you provide the information suggested in the Testamonials section
of the website.

hth
Otto-c

---

### Post by issih on 2008-06-11
Ndiswrapper should be installed by default, and in linux, the locations of normally installed applications are in the users path variable by default. Because of this, you can just type the code exactly as shown, and the system will find ndiswrapper all on its own, you don't need to worry about where it actually is right now. Same goes for most applications, e.g. opening a terminal and typing firefox will launch firefox even though you are not in the executable files directory.

The reason you didn't find anything when searching your home directory is that it isn't in your home directory, the file browser nautilus hides most of the linux directory tree from you by default, hit ctrl-h to see the hidden files.

Just try entering the code they suggest, hopefully it will work

If ndiswrapper really isn't installed (check by opening a terminal and typing ndisw,then hit the tab key, if it completes the word, then the program is installed).

Then, assuming you can get an internet connection, install it by typing :

```
sudo apt-get install ndiswrapper
```

---

### Post by stoneofshadow on 2008-06-12
i put in ndisw and pressed tab and it did nothing
then i put in that sudo apt-get code below that and it said:
[sudo] password for frontend:
reading package lists...done
building dependency tree
reading state information...done
E: couldn't find package ndiswrapper

so im not sure what to do next
anyone ever seen this before?

---

### Post by stoneofshadow on 2008-06-12
what does it mean that it couldn't find the package?

---

### Post by stoneofshadow on 2008-06-12
should i try and download it from somewhere else or something?

---

### Post by issih on 2008-06-12
It means you have no internet connection basically, I had assumed you were using a wired connection to get online whist things were ironed out. You can either do that and retry the apt-get bit, or you can pull the files off the install cd.

Boot into ubuntu as normal, then put the cd you used to install ubuntu into the drive.

Now open System->Administration->Software Sources, and enter your login password when prompted.

Now tick the box under Installable from cd rom and then hit close. 

Once that is done open a terminal and try the apt-get line again, this time it will try to read from the cd to grab the software.

Hope that helps

---

### Post by stoneofshadow on 2008-06-13
ok 
ill try that and then ill come back here
thanks

---

### Post by stoneofshadow on 2008-06-13
i cant seem to find the place to plug in the cord for the internet.
i dont have an install disc, i did have it working before i upgraded to hardy on the wireless internet and that is how i downloaded the upgrade for hardy. and now it dosent work. so im not sure if i should look closer for the cable plugin or what. do all computers have them by default?

---

### Post by anewguy on 2008-06-13
There are a few very distinct things you must do before you will have any success:

(1) try this:

sudo ndiswrapper -l <-- that's a lower case "L" for list

if it just returns nothing, you already have ndiswrapper.  If it says ndiswrapper not found, then you need to install ndiswrapper.  Without an internet connection, you can do this from the LiveCD used for install as follows:

- put the install CD in the drive (do NOT start up any package manager)
- a File Browser window should open for the CD
- double-click on "pool"
- double-click on "main"
- double-click on "n"
- double-click on "ndiswrapper"

You should now see the deb packages for common and possibly the utils (I don't have the disk in front of me right now).  Double-click on each of these to install them.

Once you have done the above, ndiswrapper should be installed.  Verify this via:

sudo ndiswrapper -l <-- lower case "L" for List

it should just return nothing - no error message, nothing.  If not, post the results back here.

Now you need the Windows drivers for you wireless card.  This should include at minimum a .inf and a .sys file.  People vary as to where they want to place these - it's just a temp thing so I normally just copy them to the desktop.

Once you have the driver files, do the following:

change your default directory to the directory the Windows driver files are in.  If you put them on your desktop, just do the following:

cd ~/Desktop


Next you need to tell ndiswrapper to install those drivers:

sudo ndiswrapper -i xxxxxx.inf (where xxxxxx.inf is the name of your windows driver .inf file)

Now, check to see if the driver is loaded:

sudo ndiswrapper -l <--lower case "L" -> should show your device

Next, set up the dependencies and load the kernel module:

sudo depmod -a

sudo modprobe ndiswrapper

The next 2 steps are to make ndiswrapper start automatically at boot:

sudo ndiswrapper -m

sudo gedit /etc/modules

Add the following to the end of that file:

ndiswrapper

then save the file and exit.

Finally, certain adapters require that the "default" driver in Ubuntu not be started so that the driver loaded by ndiswrapper can be used instead.  One such series of adapters are the BCM 43xx series.  To stop the default driver from loading, it must be "blacklisted".  To do this:

sudo gedit /etc/modprobe.d/blacklist

Add the following to the end of that file:

blacklist bcm43xx

then save the file and exit.

Now, REBOOT.


I think I remembered everything here.  If you have a problem just post back.  :)

---

### Post by stoneofshadow on 2008-06-13
i am close to getting the wire conection set up 
but is it possible that if i plug it into the wrong port that it will short circuit?

---

### Post by anewguy on 2008-06-13
It sounds as if you're not familiar with connecting your PC's ethernet.  If you are in question, and since you do have internet access in order to post here, please search the web for a user guide for your PC first and look in it for which port is which.  Normally, a network cable won't plug in to any other jack, but modem cables can be forced to and WILL mess up your PC.

Please, find a user guide for your PC first.

In addition, did you try what I said in my last post?  It does not require network access at all.

:)

---

### Post by stoneofshadow on 2008-06-13
it said command not found when i did the sudo ndiswrapper -l so i will just have to find a install disc somewhere
thanks though

---

### Post by cariboo on 2008-06-13
You have the files you need on the cd you used to install ubuntu. Just put the cdrom in your drive, when the icon pops up on your desktop double click on the icon and then navigate to pool/main/n double click on ndiswrapper and it will install automagically for you, then follow the instructions on the page you linked to.

Jim

---

### Post by anewguy on 2008-06-13
I can try to attach the files here for you if you want.  Just download them to some media you can take to your ubuntu box, open it and double-click the files.  Note the files are from 7.10, as I can't find my 8.04 disk for the life of me (looks like another download this afternoon).

If you need help finding your Windows (preferably XP, NOT Vista) drivers, let me know.
:)

---

### Post by stoneofshadow on 2008-06-13
that would be great if you could upload the files i need and some instructions about them.
this computer that i am using right now is a windows xp, so what drivers do i need for that?
i thought it had all the drivers already.

---

### Post by anewguy on 2008-06-13
You'll need to get the Windows drivers for your wireless - try going to the vendor support page and downloading them.  If they are in an exe, you may need to run it in Windows first to unpack it.  Most of the time the actual drivers will be in a "drivers" folder, and perhaps by OS within that.  Some people will have you attempt to rename the file so you can extract in it Linux, but as long as you had to download on a Windows PC you might as well unpack them there as well.

How did you install Ubuntu?  I'm confused as to why you you can't follow my previous instructions to install this.

---

### Post by stoneofshadow on 2008-06-13
i bought the computer with ubuntu already installed from a guy who runs a small linux buisness

---

### Post by anewguy on 2008-06-13
Let's see.....you bought it from a guy who has a small Linux business??  Tell HIM to get the wireless working for you, and anything else (sound, video drivers, etc.) that might not be working right.  If he has a business and sold it to you, he should stand behind it.

---

### Post by anewguy on 2008-06-14
> **cariboo907 said:**
> You have the files you need on the cd you used to install ubuntu. Just put the cdrom in your drive, when the icon pops up on your desktop double click on the icon and then navigate to pool/main/n double click on ndiswrapper and it will install automagically for you, then follow the instructions on the page you linked to.

Jim

this was already covered in a prior post and the user apparently won't do it.

---

### Post by stoneofshadow on 2008-06-14
im about to download those two files up above from you anewguy
im a little confused why i would need to look for any windows drivers though only my unbuntu wireless is not working, the windows is on a different computer and it is fine

---

### Post by stoneofshadow on 2008-06-14
ubuntu not unbuntu i mean

---

### Post by anewguy on 2008-06-14
You NEED the Windows drivers!  There are no "working" drivers for your wireless in Ubuntu, so using ndiswrapper allows Linux to use the Windows drivers.

I see the post you were following was indeed for the bcm43xx series, so if you are sure that is what you have, then installing the 2 files I attached, double-clicking them so they install, get the Windows drivers, then follow my post a few back with the details should work for you.

Please keep this in mind - you need the Windows drivers to get your wireless working in Linux.  There is a new way of doing it, but it has been hit and miss from what I've read.  Ndiswrapper is the way to go.

Post back if you have questions.  :)

---

### Post by stoneofshadow on 2008-06-14
i just downloaded a windows driver for the broadcom thing
the file i downloaded was called 
Broadcom_43xxwl_drv4100155.exe
i clicked on it and it extracted a ton of files onto my pc
which ones of these do i need?
was this even the right driver

---

### Post by wariskampar on 2008-06-14
sorry to interrupt this thread but i think i my problem is somehow related with this thread. how do we check our wireless card driver in ubuntu, whether it is already installed or not. i mean, i can connect to internet wirelessly while i was in XP therefore i assume that the driver was already installed than. so, do i have to re-installed the driver in ubuntu (hardy heron). btw this is my lspci | grep Wireless output
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by anewguy on 2008-06-14
Some wireless adapters are supported "out of the box" in Linux, some are not.  You can normally tell you need a driver when you can't see any wireless networks even though you know there should be.  If you scan this forum, and the archive, you'll find the 2 big things people have trouble with - drivers for their video adapter and drivers for their wireless adapter.

As far as the file you downloaded - did you download it from the vendor and under your PC model?  I would have no way to know if you downloaded the correct file.  Since you unpacked it in Windows, use Windows Explorer and post back the file list here so I can try to determine the files you need.

---

### Post by anewguy on 2008-06-16
Did you get any further with this?

---

