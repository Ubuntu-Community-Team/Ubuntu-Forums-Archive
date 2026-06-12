---
title: "HOWTO: Access Motorola phones through USB on Hoary using Moto4Lin"
date: 2005-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by gorkhal on 2005-08-11
[B]This howto's for installing and running moto4lin on ubuntu hoary. 
[/B]
Most of the information reproduced here, for convenience's sake , can be found at the **moto4lin's** wikipage [HERE](http://moto4lin.sourceforge.net/wiki/Main_Page)

moto4lin allows you to access your cell phone's file system under linux. Upload/Download pictures, ringtones, etc. . Its still in alpha, so be careful, but I have been running it without any problems whatsoever. Tried kmobiletools before, but could not get it to install (I'M ON GNOME :) ).  

**[COLOR=Red]***Update 1***[/COLOR]**

There's lots more supported now, I would definitely recommend checking out the [Supported Models](http://moto4lin.sourceforge.net/wiki/Supported_models) section at the motor4lin wiki.

Here is the list of 'officially' supported models (moto phones not listed here may also work, try it out):
C350, C350l, C380, C650, V180, V220, V300, V500, V547, V600, E398, E1000 
 
**[COLOR=Red]*Update*[/COLOR]**
List of other models that have been confirmed to work:
V400 
 
**If your moto phone works with this app, but its not in the official list, add it to the moto4lin wiki, [Supported Models](http://moto4lin.sourceforge.net/wiki/Supported_models) and fill in the USB ID as well. That way everyone gets it.**

Moto4lin supports AT and P2K modes on these phones. I have not tested the AT mode as of yet, but it's basically for Modem functionality and GPRS (me thinks), but its the P2K mode that I was interested in, since it lets you access your cell phone's file system. 

**#Requirements**
Install the following...
```

~$sudo apt-get install cvs
~$sudo apt-get install libqt3-mt-dev
~$sudo apt-get install zlib1g-dev
~$sudo apt-get install libusb-dev

```

**#Installing moto4lin **
We are going to get the moto4lin source  from a cvs repository. You might get an error from cvs at this stage, ignore and proceed. Asked for password? Just press Enter.
```

~$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
~$cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin

```
This should download the source into a directory named moto4lin. Now compile the source.
```

~$cd moto4lin
~/moto4lin$qmake
~/moto4lin$make
~/moto4lin$sudo make install 

```
Should you receive any compilation errors, you most likely do not have the required libraries, try looking through the error messages to figure out what you are missing. If everything goes ok, you have installed moto4lin successfully.

**#Configure moto4lin**
Connect YOUR phone to YOUR computer using YOUR usb cable. Thats right YOURs not mine, I am not sharing mine.

Now run moto4lin...
```
 ~$sudo moto4lin 
```
You need to run it under root, to access the P2K mode on your phone, at least until its fixed, or someone figures out how to run it as normal user.

In the bottom status bar of the moto4lin window it should say, at least the first time: '[info] Phone pluged as AT'

GoTo: Settings -> Preferences...
Set 'ACM Device' = '/dev/ttyACM0'
Then we need to figure out the following,
'AT Vendor ID', 
'AT Product ID', 
'P2K Vendor ID', 
'P2K Product ID'.

Click 'Update List' -> retrieves a list of the 'AT Vendor ID' and 'AT Product ID' of all your USB devices. Find your cell phone's AT IDs from the list.
(Once you have found it write it down, because an ODD thing is when moto4lin is run under root, it does not save any changes to settings)
Select 'Switch to P2K' -> if it is successful, it should say '[info] Phone pluged as P2K' in the status bar of the main window. 
Clicking 'Update List' again will now retrieve the 'P2K Vendor ID' and 'P2K Product ID' of all your USB devices. Write your cell phone's P2K IDs down.

Alternatively you can search  [HERE](http://moto4lin.sourceforge.net/wiki/Supported_models) for the AT and P2K IDs of your cellphone. 

Now quit moto4lin, and run as normal user 
```
~$moto4lin
```
Goto Settings -> Preferences and fill in the AT IDs and the P2K IDs.
 
Quit moto4lin, and the settings will be saved.
So run under root for execution and run as normal user for configuration.

**#Running moto4lin**
Now run moto4lin as root...
```
 ~$sudo moto4lin 
```

Check the current mode: 
If its already in P2K mode, click 'Connect' to load up your Motorola file system

If its in AT mode, Goto Settings -> Preferences...Select 'Switch to P2K' then try connecting.

I have attached a screenshot of how it looks like at this stage. If anyone figures how to run moto4lin without root privileges and still be able to access in P2K, do share.

Lots of kudos to the moto4lin guys for coming up with this wonderful application.

Happy experimenting  :)

---

### Post by foxy123 on 2005-08-13
Hi Gorkhal! Thanks a lot for the excellent HOWTO. I tried moto4lin before but failed. Now it works for me!

A couple of points you may want to make clearer in the HOWTO:

[QUOTE=gorkhal]
**#Configure moto4lin**
Now run moto4lin...
```
 ~$sudo moto4lin 
```
You need to run it under root, to access the P2K mode on your phone, at least until its fixed, or someone figures out how to run it as normal user.

In the bottom status bar of the moto4lin window it should say, at least the first time: '[info] Phone pluged as AT'

GoTo: Settings -> Preferences...
We need to figure out the following,
'AT Vendor ID', 
'AT Product ID', 
'P2K Vendor ID', 
'P2K Product ID'.

Click 'Update List' -> retrieves a list of the 'AT Vendor ID' and 'AT Product ID' of all your USB devices. Find your cell phone's AT IDs from the list.
(Once you have found it write it down, because an ODD thing is when moto4lin is run under root, it does not save any changes to settings)[/QUOTE]

you should also change  'ACM Device' to '/dev/ttyACM0', as it is said below. 

> **#Running moto4lin**
Now run moto4lin as root...
```
 ~$sudo moto4lin 
```
Goto Settings -> Preferences...Select 'Switch to P2K', only if it is not already in P2K mode. Goto Main Window and click 'Connect/Disconnect'. 

To see my files I had to click on Update List button.

Thanks again for your HOWTO!

---

### Post by az on 2005-08-13
You should request that this be packages for Ubuntu.  You can ask on the developmental mailing list,

---

### Post by void_false on 2005-08-13
WOW that just rox!
Now I need to buy miniusb datacable for my c350. Hell, official CD costs something like 30$  \\:D/

---

### Post by foxy123 on 2005-08-13
Has anyone heard anything about C975? It is not listed in the supported models...

---

### Post by gorkhal on 2005-08-13
Good to see it worked for someone too. Thanks for the suggestions foxy123.

[QUOTE=foxy123]Has anyone heard anything about C975? It is not listed in the supported models...[/QUOTE]

You could still try it out....it may work. Since the P2K mode used is supposed to be prevalent in a lot of the motorola phones.

---

### Post by tlaloczint on 2005-08-17
this is so cool I just add couple of songs that as ring ones and this rocks thanks (the songs I have to cut in order to make it fit I have a v180)

---

### Post by gorkhal on 2005-08-17
[QUOTE=tlaloczint] (the songs I have to cut in order to make it fit I have a v180)[/QUOTE]

I have a v180 too, trouble is, has only 1.9 MB of space, not only you have to cut, but also  encode the mp3s at like 64 kbps.

I am not sure if anything less than or greater than 64 kbps works.

---

### Post by manrobj on 2005-08-19
Also works for a V400.
Thanks!!

---

### Post by gorkhal on 2005-08-19
[QUOTE=manrobj]Also works for a V400.
Thanks!![/QUOTE]

Neat....I will start up a list of 'Unofficially' Supported models in the howto.

You could also add in your motorola phone number to the moto4lin wiki,
[HERE](http://moto4lin.sourceforge.net/wiki/Supported_models) and fill in the USB ID as well.

---

### Post by tlaloczint on 2005-08-22
[QUOTE=gorkhal]I have a v180 too, trouble is, has only 1.9 MB of space, not only you have to cut, but also  encode the mp3s at like 64 kbps.

I am not sure if anything less than or greater than 64 kbps works.[/QUOTE]
 I can encode it to 128 kbps still will play it, it will make it a bigger file do 
you can try it and let me kow

---

### Post by gorkhal on 2005-08-23
yes 128 kbps works now...weird dont know why it wasnt working before... :smile:

---

### Post by Lupine on 2005-09-15
Does anyone know where to go to request info on if a phone is supported or not?  I just got the popular E815 and I can't seem to get moto4lin to connect to it.  p2ktest comes back with "No phone found", however it is showing up under **lsusb** :
```
 
Bus 005 Device 003: ID 22b8:2a61 Motorola PCS

``` 

The moto4lin mailing list seems dead, and I don't see any forum for the project.  Anyone got their E815 working, or have a suggestion of where I should go to get help on that project?  

Sorry if this is a little OT....GREAT HOWTO....thx!

---

### Post by Seth on 2005-09-26
Good tutorial, worked great for me.

1) I would suggest using "checkinstall" instead of "make install" so you have a deb that is easy to remove. I hate compiling from source since it breaks apt; this is the way around that.
2) If you transfer an mp3 ringtone to your phone but you can't get it to play it:
- Navigate to your Audio SubFolder (/a/mobile/audio).
- BACKUP MyToneDB.db and TempToneDB.db to your computer!
- Delete MyToneDB.db and TempToneDB.db. 
- Upload new ringtone.
- Power cycle phone

This will rebuild your Audio database and is needed when using moto4lin to upload things.

---

### Post by Lupine on 2005-09-26
Great....what phone model?

---

### Post by gorkhal on 2005-09-26
hey anyone know...how to retrieve the addressbook (phone book) from your motorola phones?? using moto4lin. More specifically which file stores all that information ??

appreciate it...thanks.

---

### Post by Seth on 2005-09-26
[QUOTE=gorkhal]hey anyone know...how to retrieve the addressbook (phone book) from your motorola phones?? using moto4lin. More specifically which file stores all that information ??

appreciate it...thanks.[/QUOTE]
Much easier to use KMobileTools. I'm working on debs but they won't make it into Breezy methinks.

---

### Post by galder on 2005-10-12
Thanks for the howto.

I have a Motorola v1050, and it seems that the phone is recognized, because I can get the Vendor ID 22b8 and the product ID 3002, but when I switch to P2k i get this error:

[error] Unable to open device
[error] Check preferences
[error] Unable to connect

Could anyone help me? Any hint?

Thanks in advance!

---

### Post by chunk on 2005-10-24
It's not working for me. I have a Motorola v265 phone.

Vendor ID: 22b8
Product ID: 2a22

Sometimes Product ID also shows as 2a21.

I get the following messages in the main window of moto4lin after trying "switch to P2K":
```

[info] Phone is unpluged. Please connect it
[info] Phone pluged as P2K
[info] Phone pluged as AT
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] Phone is unpluged

```

Any advice"

---

### Post by ubuntu4everyone on 2005-11-27
i managed to start it and get my p2k and at numbers and save it, but now as soom as i connect my phone in the terminal it says

Form1
PhoneMan
New mode: 2
Killed


any ideas ?

---

### Post by geniium on 2005-11-27
Im having trouble to make it work with the RAZOR V3 phone under Breezy. Anyone has done it ?
Thanks for any info.

---

### Post by Brewtal on 2005-12-20
I've grabbed all the dependencies, and moto4lin from the cvs repository but when I go to "make" the file I'm getting a error.

```
~/moto4lin$ make
bash: make: command not found
```

Am I missing some other dependency or am I just lucky?

---

### Post by foxy123 on 2005-12-20
[QUOTE=Brewtal]I've grabbed all the dependencies, and moto4lin from the cvs repository but when I go to "make" the file I'm getting a error.

```
~/moto4lin$ make
bash: make: command not found
```

Am I missing some other dependency or am I just lucky?[/QUOTE]
it is wierd... have you got automake installed?

---

### Post by Brewtal on 2005-12-20
> foxy123 had this to say:

**it is wierd... have you got automake installed?**

Yep, automake is installed.

---

### Post by redgilda on 2005-12-20
[QUOTE=Brewtal]Yep, automake is installed.[/QUOTE]
ive got the same problem... i have never used this command before so i cant say 'it used to work before' ;-) when i check for automake in synaptic it does tell me it is installed.... any ideas what i could do?

i DO prefer installing the software from "Add Application" menu :D but I wanna  connect my moto... im using ubuntu breezy btw....

---

### Post by redgilda on 2005-12-20
ok i hate replying to my own messages... but i gotta say it worked so maybe itll help another newbie someday - turned out i DIDNT have 'make' installed... then i had to install also a C++ compiler (whatever that is) - i searched for c++ in synaptic and installed sth that looked like such a compiler.. then ran 'make' again and it worked.. 

so then when I ran moto4lin, i configured the settings under sudo, then when i ran moto4lin under normal user - the settings were still there but i was not able to recognize the phone, even though it said 'connected' and all the settings were correct... then in the terminal i saw some weird permission errors so i ran the program again as sudo and then i was able to connect/recognize/download things... :) 

so im happy with the 1st step. next - freeing up some free space on my v3, editing seems etc - never done that before either ;-) but now.. g'night!

and thanks for that HOW-TO, really!! much appreciated.

---

### Post by Brewtal on 2005-12-21
Thanks Redgilda. I installed gcc and make, now it works perfectly.

---

### Post by biketrials on 2005-12-28
I am having problems connecting to my razor v3.  

Vendor ID - 22b8
Product ID - 4901

when i run *sudo p2ktest*, and it views all my files on the phone and can see it's there. 

but if i run *sudo moto4lin* I get the following output.
```

[info] Phone pluged as P2K
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Check preferences
[error] Unable to connect

```

and this is from my prompt...
```

~$ sudo moto4lin
Form1
PhoneMan
New mode: 2
New mode: 1
P2kProc::doConnect()
doActConnect
doActConnect
P2kProc::doConnect()

```
Any help or suggestions would be much appreciated.  thanks for your time.

---

### Post by biketrials on 2005-12-28
Nevermind I solved my problem, the settings sould have been.

AT Vendor ID - 22b8
AT Product ID - 4902


P2K Vendor ID - 22b8
P2K Product ID - 4901

---

### Post by alvonsius on 2006-01-05
Anybody knows how to connect motorola E398 as a modem and use it woth KPPP??

---

### Post by redgilda on 2006-01-19
[QUOTE=gorkhal]hey anyone know...how to retrieve the addressbook (phone book) from your motorola phones?? using moto4lin. More specifically which file stores all that information ??[/QUOTE]
hey, id appreciate that info too... i have no idea how to install Kmobile tools, so Id like to back up the phonebook using moto4lin (i have a black RAZR v3) -  could anyone help? :)

---

### Post by steevc on 2006-01-29
Thanks to this HOWTO I have the software installed. I'm just having trouble connecting to my V220. I set up the AT and P2K values given on the [V220 page]("http://moto4lin.sourceforge.net/wiki/V220"), but I can't connect. I get

```
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to connect
[info] Phone is unpluged
```

If it's an AT phone then should it be switching to P2K?

I initially set up the ACM device as /dev/sda, but got the same result. This is when running as root. When running as a normal user I get even more errors as it cannot retrieve the phone details.

EDIT: I've got it working now. I edited the settings file manually. Now when I run as root it works. I can extract pictures etc. Pretty cool considering Motorola would charge for that facility. The cable for my Canon camera fitted.

---

### Post by Stelmate on 2006-02-07
I'm getting a wierd error when I try to save my settings (under root and user)
QSettings::sync: filename is null/empty
Is there anyway to go in and edit these settings manually?

---

### Post by Stelmate on 2006-02-07
Okay I figured it out.
In your /home/username/.qt directory there is a moto4linrc config file, directly edit this to change your settings (if they won't change like mine was)
also there is one in the /etc/qt/ directory but that does not effect the settings for some strange reason, root will use the moto4linrc in the .qt directory instead.

---

### Post by happyponcho42 on 2006-02-08
To the people getting errors when executing the 'make' command, before you issue the 'make' command, you have to issue 'qmake' first, as per the tutorial.

---

### Post by swoon on 2006-02-11
[QUOTE=Stelmate]Okay I figured it out.
In your /home/username/.qt directory there is a moto4linrc config file, directly edit this to change your settings (if they won't change like mine was)
also there is one in the /etc/qt/ directory but that does not effect the settings for some strange reason, root will use the moto4linrc in the .qt directory instead.[/QUOTE]

what did you change to get rid of the "QSettings::sync: filename is null/empty" error?

---

### Post by Stelmate on 2006-02-11
I didn't get rid of the QSettings error, thats why I had to manually edit the file :).  It works great now that I edited the file directly though. (Thats all the error was saying, the program seemed to create a tmp file and than tried to write the tmp file to your actually settings file and it fails, or at least it was on mine)

Does anyone know how to install java apps using moto4lin? I can copy over the .jar to the kjava folder but the phone doesn't see it in the menu.  I tried one with a .jad and .jar file as well but it is still not showing up.

---

### Post by happyponcho42 on 2006-02-12
[QUOTE=Stelmate]I didn't get rid of the QSettings error, thats why I had to manually edit the file :).  It works great now that I edited the file directly though. (Thats all the error was saying, the program seemed to create a tmp file and than tried to write the tmp file to your actually settings file and it fails, or at least it was on mine)

Does anyone know how to install java apps using moto4lin? I can copy over the .jar to the kjava folder but the phone doesn't see it in the menu.  I tried one with a .jad and .jar file as well but it is still not showing up.[/QUOTE]

For java apps, you do not want to be the File Manager mode.  Click on the 'Kjava' button to switch modes, then 'Add' the files there.  After you upload each individual java app, 'Update List' and select it on the list and hit 'Set .pat file'.  If you do not see the new app on your phone, just turn it off and back on again and it should be there.

---

### Post by zero_ on 2006-02-20
Hi all

i've been crazy all this day

The problem was in the path of the device

here my cfg file of the preference ( in /home/myhome/.qt/moto4linrc )

cfgACMdevice=/dev/ttyACM0
cfgATproduct=3002
cfgATvendor=22b8
cfgAutoConnect=1
cfgP2Kproduct=3001
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0

see: no spaces and no ' ' in the device path.
ù
Hope to be usefoul for anyone.

Giorgio aka zero_ from italy

Ciao!!!

---

### Post by opticyclic on 2006-02-27
[QUOTE=Brewtal]I've grabbed all the dependencies, and moto4lin from the cvs repository but when I go to "make" the file I'm getting a error.

```
~/moto4lin$ make
bash: make: command not found
```

Am I missing some other dependency or am I just lucky?[/QUOTE]

I had this problem as well.
However, I don't believe the previous 'solutions' posted here are correct.
I failed with the previous suggestions but succceded with
sudo apt-get install build-essential

[http://www.ubuntuforums.org/showthread.php?t=137028&highlight=make](http://www.ubuntuforums.org/showthread.php?t=137028&highlight=make)

---

### Post by linuxNewb on 2006-03-08
Just wanted to say thanks for this thread. I uploaded wallpaper and songs from Breezy to my RAZR v3 with no problems using the instructions found here.

One question though: I uploaded an mp3 to the audio folder, and I can play it on the phone -- sounds great -- but how can I set it as my ring-tone, it's not in the ringer list? Thanks.

edit: After a quick google search, I found this forum thread stating that in order to set your mp3 files as ringtones you need to delete a couple of files from the phone (razr v3). [http://www.howardforums.com/archive/topic/839817-1.html](http://www.howardforums.com/archive/topic/839817-1.html)

Needless to say this makes me nervous. Can anyone here confirm this? Thanks.

update: I followed the instructions and it worked perfectly -- delete MyToneDB.db and TmpTneDB.db 
Now I can set my mp3s as ringtones.

---

### Post by seiyachan on 2006-03-11
I am able to connect my motorola v3x with moto4lin in P2K mode, but it cannot get the file list....

---

### Post by Stereotypical Rage on 2006-03-28
I can't connect my Black V3 RAZR to moto4lin.

However it connects via kmobiletools.
I'm at my job now and I was doing some googling and I came across this page.


[http://user.cs.tu-berlin.de/~sluo/linux/razr/en-razr.html](http://user.cs.tu-berlin.de/~sluo/linux/razr/en-razr.html)

It says for the V3 RAZR, one needs the p2kmoto files too.

I will install this package when I get home and post results.

---

### Post by acoster on 2006-04-24
For running moto4lin without being root, and without sudo, you can set the bitsuid of it (its a bit dangerous if you are on an untrusty enviroment. But I dont think its the case ;) )

```
sudo chmod u+s `which moto4lin`
```

---

### Post by Dax0r on 2006-05-11
[QUOTE=happyponcho42]For java apps, you do not want to be the File Manager mode.  Click on the 'Kjava' button to switch modes, then 'Add' the files there.  After you upload each individual java app, 'Update List' and select it on the list and hit 'Set .pat file'.  If you do not see the new app on your phone, just turn it off and back on again and it should be there.[/QUOTE]

I tried but I get this:

[info] Phone connected as P2K
Getting file list
[error] Phone is busy. Please try later

I tried many times...
It worked only 2-3 times and when I tried to upload the game I get:
Uploading 1 file(s)
Uploading: j2me6.pat (0 bytes)  <---- (is it normal?)
Uploading complete

When I click on Set path file I get every time : 

Uploading: j2me7.pat (0 bytes) <---
Uploading complete

I reboot the phone (v3) and when I start the game I get:
"application expired"..I tried many games!!

Someone experienced this problems??

---

### Post by Sponge34 on 2006-05-13
Hi,
just thought you ought to know that on Breezy, this took less time to get talking to the phone than p2kman (or the moto phone apps for that matter) does in Windoze XP... that included downloading cvs as well :)

Cool tutorial and with a RAZR V3r Black moto4lin works a treat. Getting the file list requires clicking the connect button then update list but that's only me getting used to the s/w I guess.

S.

---

### Post by Peepsalot on 2006-06-04
I just tried these instructions, but failed on the cvs steps:
```
peeps@ninja:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password:
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host

```

I'm not familiar with cvs so I don't really understand what this is about.  Any help?

---

### Post by Peepsalot on 2006-06-04
Nevermind.  I found the .deb packages for Ubuntu:
[http://moto4lin.sourceforge.net/wiki/Debian_Packages](http://moto4lin.sourceforge.net/wiki/Debian_Packages)

---

### Post by Peepsalot on 2006-06-04
Well i got it installed, but I can't get it to connect to my phone, it's a Razr V3c.  

When I start moto4lin I get this:
```
peeps@ninja:~$ sudo moto4lin Password:
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan

```

And in the GUI it says "[info] Phone is unpluged. Please connect it"

---

### Post by Glass_Onion on 2006-06-17
Hey all, I know my problem's with Dapper and not Hoary but I'm guessing I could try my luck here instead of starting another thread.

I'm having trouble setting up the ACM device. I've tried to follow the instructions [here](http://moto4lin.sourceforge.net/wiki/System_Configuration) on the moto4lin wiki but with no luck. It just says to plonk the following into a rules file without actually specifying one; 

```
KERNEL=="ttyACM[0-9]*"			NAME="ttyACM%n", GROUP="usb", MODE="0660"
```

First I tried it in 40-permissions.rules but with no luck. I then tried it in a couple of others deleting it if it didn't work. What am I doing wrong?

---

### Post by briguy on 2006-06-21
[quote=Sponge34]Hi,
just thought you ought to know that on Breezy, this took less time to get talking to the phone than p2kman (or the moto phone apps for that matter) does in Windoze XP... that included downloading cvs as well :)

Cool tutorial and with a RAZR V3r Black moto4lin works a treat. Getting the file list requires clicking the connect button then update list but that's only me getting used to the s/w I guess.

S.[/quote]

Could you post your settings under preferences?  I can connect via p2k, but it can't read file lists, drive letters, etc.

Thanks

---

### Post by crane on 2006-06-22
For some reason My razr V3 will not connect.
When I click connect I get this in the terminal: 
doActConnect
doActConnect
P2kProc::doConnect()
(E_drv_connect: no phone)

Any advice on what to try or where to look?

---

### Post by Roland22 on 2006-06-24
I have a RAZR V3X , and it works GREAT:D . time to delete the win partition:-D :-D

---

### Post by chungaroo on 2006-07-26
I'm able to connect my Motorola L6, but I can only see the /a directory.  I know there is a /c directory with the personal files (photos, etc).  How do I fix this?

---

### Post by alaaji on 2006-07-26
I just wanted to confirm that this works great with the Motorola V360 using the deb packages from [http://moto4lin.sourceforge.net/](http://moto4lin.sourceforge.net/).

---

### Post by shane2peru on 2006-07-27
Ok, I know this is an old thread, but there doesn't seem to be anything to it's equal that is up to date.  I had my phone connected to my computer following most of the instructions in this how to.  I installed via the deb, rather than compiling and cvs'ing.  That was yesterday.  Today I tried Kmobiletools and it worked, I just set the device to /dev/ttyACM0 and it connected.  Now when I bring up moto4lin, it shows my phone connected as an AT phone, and not P2K.  I have a Razr V3 Motorola phone.  I tried to set it up again as described in page one of this thread moto4lin as regular user, set the values, and set it as a p2k device.  Then run it as sudo moto4lin and it doesn't seem to work.  It just stares at me saying "Phone plugged as AT".  One more thing - when I run ```
moto4lin
``` it doesn't show my phone, it doesn't show very much honestly.  When I run ```
sudo moto4lin
``` it shows a lot of things and my phone.  Any ideas???  

Shane

---

### Post by shane2peru on 2006-07-27
Ok, I solved my own problems.  For some odd reason the numbers of the AT and P2K vendors keeps changing on me.  I had to go back and reset those numbers to the right numbers to get it to work.  So if it doesn't connect, go back to square one and start over with the setup of the program for the phone, and don't just assume the numbers are what they were before.

Shane

---

### Post by pek on 2006-07-30
no way i could make it work.


i do not have any device called /dev/ttyACM0 BUT lsmod says i have cdc-amc loaded. i tryed on google and i only found this -> [http://tinyurl.com/qjrcp](http://tinyurl.com/qjrcp)

the phone is a c835.

---

### Post by jackhawk28 on 2006-08-04
> **steevc said:**
> EDIT: I've got it working now. I edited the settings file manually. Now when I run as root it works. I can extract pictures etc. Pretty cool considering Motorola would charge for that facility. The cable for my Canon camera fitted.

Where'd you find the settings file?

---

### Post by N8MAN1068 on 2006-08-18
> **Glass_Onion said:**
> 
I'm having trouble setting up the ACM device. I've tried to follow the instructions [here](http://moto4lin.sourceforge.net/wiki/System_Configuration) on the moto4lin wiki but with no luck. It just says to plonk the following into a rules file without actually specifying one; 

```
KERNEL=="ttyACM[0-9]*"			NAME="ttyACM%n", GROUP="usb", MODE="0660"
```

First I tried it in 40-permissions.rules but with no luck. I then tried it in a couple of others deleting it if it didn't work. What am I doing wrong?
From a command line, run:
echo AT+MODE=8 > /dev/ttyACM0

However, I also saw that page in the configuration where it's supposed to automatically create the device. I was just about to post and ask which file to put that in...I see you beat me to it. I also can't figure out which file to plop this in so that the port is automatically created when the phone is plugged in.

Anyone?

---

### Post by ncappel1 on 2006-08-18
just like chungaroo, I am able to connect my phone (PEBL u6) using moto4lin but cannot seem to find any of my wallpapers, pictures, or other personal files. I can only see what appears to be system files in a/


is there a way to access a different directory?

---

### Post by Disclaimer on 2006-08-24
I've been having problems with my V191..

here the output

> 
[info] Phone pluged as AT
[info] Phone is unpluged
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] Phone pluged as AT
[info] Phone pluged as P2K
Getting file list
[error] Unable to get drive list
Complete
Searching for 
[error] Bad request or no files found



I have only got a Phone main directory, completely empty and I can't add files to it.

Any ideas are aprecieted. Thanks.

---

### Post by dawg on 2006-08-27
i've tried following the how-to step by step, but i still can't get it to work.  i get to the qmake part which works, then i go to the make part and nothing happens i get bash: make: command not found.  ive installed auto make and gcc.  any ideas?  btw im using dapper.

---

### Post by rasgward on 2006-08-29
Hey Y'all,
 Moto4lin looks great, but I don't think it supports my phone motorola v323. I have searched and haven't seen it listed. Anyway, if anyone has any thoughts...here is the output of the device file under proc/bus/usb/devices

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 20 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(comm.) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=22b8 ProdID=2a22 Rev= 0.01
S:  Manufacturer=Motorola, Inc.
S:  Product=Motorola A41x/V32x
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=32ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=8a(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=0b(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

Thanks. -Greg
Mainly it connects to the AT but won't even touch the p2k it seems.

---

### Post by bugardifieno on 2006-08-31
As of June 1, 2006 you need to add moto4lin in front of the > /cvsroot/moto4lin login and ```
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin
``` --see this url [http://haacked.com/archive/2005/05/12/3178.aspx](http://haacked.com/archive/2005/05/12/3178.aspx)
It should be:
```
[email]anonymous@cvs.sourceforge.net[/email]:moto4lin/cvsroot/moto4lin login
~$cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:moto4lin/cvsroot/moto4lin co -P moto4lin
```

---

### Post by Dr. Feelgood on 2006-09-04
I don't know if this works in Dapper.  It used to work great for me in Breezy but now I reinstalled it in Dapper it gives me this error

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 1

```

It still opens up the GUI and says the phone is plugged in as AT but thats it.  I can't switch to P2K or connect or anything else.  Anyone have any ideas as what the problem could be?

---

### Post by Dr. Feelgood on 2006-09-09
Anyone have a clue??  It used to work perfect for me in Breezy but ever since I did a fresh Dapper install I get this problem.

---

### Post by redgilda on 2006-09-17
hmm I've got a problem all of a sudden..
Yesterday I was able to connect my phone in moto4lin and download and upload stuff and today I'm getting this error:

```
[info] Phone is unpluged. Please connect it
```

Any idea what's wrong? I did notice that my phone is behaving weirdly too (V3).. I cant change Ring Styles settings all of a sudden (All I did before was upload and download pictures and sounds)

Does it mean that my phone is cooked? #-o
/edit/ - restarted ubuntu and all was fine, phone connected without any problems and then later I found a nice and easy solution to fix my ring styles too. yay.

---

### Post by solitoni on 2006-09-18
> **ncappel1 said:**
> just like chungaroo, I am able to connect my phone (PEBL u6) using moto4lin but cannot seem to find any of my wallpapers, pictures, or other personal files. I can only see what appears to be system files in a/


is there a way to access a different directory?

I have the same problem with a Motorola V235. Many people seem to have had success with V220, and V235 is superficially similar. Has anybody succeeded with V235 already?

Using the utility p2ktest that comes with moto4lin I was able to get the
following output:

# p2ktest 
P2k Test
Device list:
0000:0000: [Linux 2.6.15 ehci_hcd] [EHCI Host Controller]
0000:0000: [Linux 2.6.15 uhci_hcd] [UHCI Host Controller]
0000:0000: [Linux 2.6.15 uhci_hcd] [UHCI Host Controller]
22b8:4901: [Motorola Inc.] [Motorola Phone (V235)]
0000:0000: [Linux 2.6.15 uhci_hcd] [UHCI Host Controller]
P2k Phone found

(E_p2k_connect.-3: Unable to set configuration)
Phone Model: V235
Drive: /aþ/c
Free space: 1768415 bytes
File count: 267 bytes
   1    300  40   4 /a/ALARMCLOCK
   2   5392   2   0 /a/default_wml.css
   ......etc.

So in the Drive: field there is /aþ/c which looks like /a plus /c, but the file listing only has /a files. :confused:

:cool: **Update: Found solution to my problem myself**

I have been compiling moto4lin-0.3, but not the version from the CVS server, but simply from sourceforge. Only the CVS version appears to be able to handle multiple drives, and my V235 does have two drives.

I found this information finally in the moto4lin mailing list. A link to the latter as well as other valuable information can be found on the moto4lin wiki at [http://moto4lin.sourceforge.net/wiki/](http://moto4lin.sourceforge.net/wiki/)

Now moto4lin works for my V235 like a charm!

---

### Post by hecbuma on 2006-09-29
hi, I`d install the moto4lin, and i follow all the step, finally i get to work with my L7, but when I restart my pc and update my sistem, the the product id of my cell phone change, it use to be 4902 y I used teh combination 4901 and 4902, but when it change, and i try to change the values again with the new product id, it doesnt connect to the phone, help please

---

### Post by Edska on 2006-10-12
I am gettin error doing these lines:

```
~$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
~$cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin
```

Here it is

```
edska@edska-desktop:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password:
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host
edska@edska-desktop:~$ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin
cvs [checkout aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host
```

---

### Post by Edska on 2006-10-12
I installed that moto4lin but here is another error.

```
~/moto4lin$ make
bash: make: command not found
```

I have installerd automake, gcc and cpp. 
Can any one help me?

---

### Post by Edska on 2006-10-12
OK, guys I finished. It works perfect on E398

---

### Post by kalel on 2006-10-16
yeeeeeeeeeeeeeees

works!!!!!!!!!!!!


i love you man =) jajajajajaja


thanks

---

### Post by gez on 2006-10-23
> cvs [checkout aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host

I know the how to says there will be an error message, but is this the one?

It doesn't seeem to work beyond this point.

---

### Post by drobvice on 2006-11-13
The website says that cvs is obsolete and they are using svn now.  I tried the svn instruction but am having a problem with qmake and make.  I have to specify "qmake -project" then "qmake -makefile" then do "qmake".  The make gives errors and the make install (likewise for checkinstall) doesn't work.  I tried the package in edgy but my razr v3m will not connect at all.  It does show up in the usb list when you update in the settings menu.

---

### Post by Icarosaurus on 2006-11-13
Anyone knows how to access Motorola e365 through PL2303 USB-to-serial cable under Edgy?
Is it a mission impossible?
:)

---

### Post by Muty-bg on 2006-11-22
Hi everyone

thx for the great how-to :)

I too didn't managed to install it from the cvs, but I found out that there is a package for ubuntu here: [http://moto4lin.sourceforge.net/wiki/Debian_Packages]("http://moto4lin.sourceforge.net/wiki/Debian_Packages")

I installed it and everything works great :) 

I have a motorola razer v3

---

### Post by foxy123 on 2006-11-23
Does anyone know if it is possible to copy an address book from v220 to v3?

---

### Post by petit.padavoine on 2006-11-26
Well everything works fine, great HOWTO.

Just a small question though, which directory should I upload ringtones to?

---

### Post by Fintan on 2006-11-28
Okay i got everything working as well. Thankx all. Now for the stupid question: I am using a razr v3i it connects automaticaly and loads my files into the file manager.
But where is my phonebook, kalander and how do i sync it / them with lets say Kontact , evolution or thunderbird?
Oh yes am running kubuntu on edgy.

Thank you for the help
cheers
F

---

### Post by Footer on 2006-12-12
Has anyone gotten their V3m to work with Moto4Lin?  I can't for the life of me get it to connect (but as mentioned in an earlier post, it does show up in the usb list when doing update in the settings menu).  I see in the Moto4Lin wiki that it doesn't work <yet> nor does it's brother V3c ... I've gotten it to work with bitpim and kmobiletools but neither of those have all the features I'm looking for (uploading files, jpg & mp3 in particular).

Anyway, I've noticed that Windows machines (XP & Win2k) recognize it as a V3c so perhaps when Moto4Lin works with the V3c, it will recognize the V3m as well.  I DON'T want to go down the Windows road and have only briefly experimented with plugging it in to see what Windows says it is ... So not sure how well it works there or not.  :)

Thanks for listening!

---

### Post by drobvice on 2006-12-12
I have a Verizon V3m and it is not recognized.  For me, it will show up when you do the update in the settings screen for me, as well.

---

### Post by Tekovro on 2006-12-14
i have a razr v3t. it sees my phone but it wont let me change it to p2k. please help!

---

### Post by Footer on 2006-12-14
Try putting in a bogus number in the Settings --> Preferences --> AT Product ID like 1234.  That worked for me to get it to try connect as P2K.  But with my v3m, this is the output on the command line:

footer@kubuntu:~/Desktop/moto4lin-0.3$ ./moto4lin
Form1
PhoneMan
ScimInputContextPlugin()
New mode: 2
doActConnect
doActConnect
P2kProc::doConnect()
(E_openPhone: Unable to set configuration)

It doesn't matter if I start as root either:
```
sudo ./moto4lin
```
same results and NO JOY!!!

](*,)

---

### Post by train2335 on 2006-12-17
I am having problems with this. I am using Ubuntu 6.06 and using a Motorola Razr v3. I can't get into P2K mode. I got into it once and it worked, and I have tryed it using the same method that worked earlier and it won't work anymore. If you have any solutions for me let me know. I have tryed everything! When I press the Switch to P2K button, it doesn't do anything. Please help me!

---

### Post by Footer on 2006-12-18
Did you try putting a bogus number in the AT Product ID field as I suggested in my previous post?  That worked for me to get it to try connect as P2K ... and you're right, pushing the AT or P2K buttons doesn't seem to do anything.

But I still can't get my phone to connect regardless of what I try!

---

### Post by train2335 on 2006-12-18
> **Footer said:**
> Did you try putting a bogus number in the AT Product ID field as I suggested in my previous post?  That worked for me to get it to try connect as P2K ... and you're right, pushing the AT or P2K buttons doesn't seem to do anything.

But I still can't get my phone to connect regardless of what I try!

Wow. That actually worked. I am now connected and everything. Thanks man!:D

---

### Post by murlosad on 2006-12-20
> **Footer said:**
> Did you try putting a bogus number in the AT Product ID field as I suggested in my previous post?  That worked for me to get it to try connect as P2K ... and you're right, pushing the AT or P2K buttons doesn't seem to do anything.

But I still can't get my phone to connect regardless of what I try!

Worked for me with a V3m from Alltel, using your 1234 as the AT product ID.

I had to enter that while running moto4lin as a user, then exit and open it with sudo but it seems to connect just fine.  thanks for all the help everybody

---

### Post by Footer on 2006-12-21
> **murlosad said:**
> Worked for me with a V3m from Alltel, using your 1234 as the AT product ID.

I had to enter that while running moto4lin as a user, then exit and open it with sudo but it seems to connect just fine.  thanks for all the help everybody

What version of U(K)ubuntu are you using?  How did you install moto4lin (SVN, Deb packages, Ubuntu repositories, etc.)?  Does any of that matter???  All I want for Christmas is my V3m to connect via moto4lin!

Thanks!

---

### Post by gorilla_king on 2006-12-24
hey everybody. i've been messin with my razr v3m (but show up as v3c) and this thread for like a month now and it still doesn't freakin work.

It's always just said it can't connect when i try to switch to p2k.

so this morning i installed the svn version and have different errors. i guess that's good. can someone help with these

> [info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/usb/acm/0 to P2K mode...
[info] AT E0 answer: 
[debug] nread=0, errno=25
[error] Unable to connect

and here is the command line
> thomas@joey:~/Programs/moto4lin$ sudo moto4lin
Form1
PhoneMan
New mode: 1
P2kProc::doConnect()
Unable to connect: Inappropriate ioctl for device

thanks for the help/advice

ps changing the at product id's just makes my phone not even show up. so that doesn't work.

---

### Post by theaverageidiot on 2006-12-25
I followed everything and it works fine but there's nothing in KJava and I know I've got like, 4 games that came with my V3i on it.

I click KJava then Update List casue there's nothing there and this happens:

```
Getting file list
[info] Found drives: [ /a /c ]
[info] Search request: [/a/|*]
[info] Found 326 files
[info] Search request: [/c/|*]
[error] Phone is busy. Please try later
[info] Found 296 files
Complete
```

??? What's up?

---

### Post by murlosad on 2006-12-26
> **Footer said:**
> What version of U(K)ubuntu are you using?  How did you install moto4lin (SVN, Deb packages, Ubuntu repositories, etc.)?  Does any of that matter???  All I want for Christmas is my V3m to connect via moto4lin!

Thanks!

I'm using edgy eft, as far as installing moto4lin, I'm not sure what repo it was in but all I had to do was 
```
sudo apt-get install moto4lin
```

I can look up the repos later, I'm at work now.  and I'll post my moto4linrc file as well.

here's my moto4linrc file.  It goes in /home/username/.qt

> 
[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=1234
cfgATvendor=22b8
cfgAutoConnect=1
cfgP2Kproduct=2a61
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0
cfgLoadList=1


you should just be able to copy that into a text file and save it as /home/username/.qt/moto4linrc

you can also launch moto4lin as a regular user and make the config changes, then close it and launch as root 'sudo moto4lin' to use. 

You also have to click on preferences and click 'switch to p2k', then close the preferences dialog and click connect.  Obviously make sure your phone is on.

I usually have to click the update button at the bottom a few times to get it to display the file tree, but once it's up I've been able to download pictures.  I tried uploading an mp3 for a ringtone, but I only got 10 seconds, so I don't know if there is a size limit.

Good luck, I'll check back when I can and offer what assistance I'm able.

---

### Post by mrmailer on 2007-01-02
Please help me, I can't get to where any of you guys are.  I have always used cdc-acm, but I can't, despite even manually loading it, get a /dev/ttyACM0 or whatever with my sprint motoslvr l7.

Here's what dmesg says on plugging it in...

usb 5-5.4: new full speed USB device using ehci_hcd and address 55
usb 5-5.4: configuration #1 chosen from 1 choice


that's it.

lsusb
Bus 005 Device 056: ID 22b8:2a64 Motorola PCS 



and proc/bus/usb/devices

T:  Bus=05 Lev=02 Prnt=10 Port=03 Cnt=02 Dev#= 56 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=22b8 ProdID=2a64 Rev= 0.01
S:  Manufacturer=Motorola Inc.
S:  Product=Motorola L7c/K1m/V3m
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=128ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=84(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms


I saw this
[http://moto4lin.sourceforge.net/wiki/SLVR_L7](http://moto4lin.sourceforge.net/wiki/SLVR_L7)
"Seems to work fine. Can list all the files in the phone (remember to set the phone's USB connection to data first so it doesn't appear as a USB mass-storage device) and download things from it."

Where in the WORLD is this setting?


any help appreciated, thanks!

---

### Post by skipo on 2007-02-09
Hello there... I tried to install a program with Kjava, but something went terribly wrong. Now the the phone says that I don't have any MIDlet suites installed, but the programs are taking some of the drivespace.

What can I do? What can I safely remove? The phone is L6.

I attached the list of files in /a/mobile/kjava.
There is only one small file in /c/mobile/kjava, J2MEPCK.

Any help would be appreciated.

---

### Post by angelsneverdie on 2007-02-12
Hello all.

I'm running edgy eft and have a motorola razr v3t.
I can't get this thing to work.  I instilled all the stuff like the guide said, couldn't get into the cvs part but typing sudo apt-get install moto4lin worked.
I've tried doing all the settings like it says and always get this in the terminal

:~$ sudo moto4lin
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 2
P2kProc::doConnect()
doActConnect
(E_getPhoneName: E001)
(E_getDriveName: E001)
(E_fileCount: E002)
(E_getDriveName: E001)


It will say the phone is connected by then it will say it is unable to find phone model, etc, and i can't see a file list.

anyone know what is going on here?
and go easy on me, i'm a linux newbie.

---

### Post by TheBlueCow on 2007-02-12
For those of you having troubles with your phones, try to sudo chown username:username your ~/.qt/moto4linrc file. I couldn't change any settings or anything because it wasn't actually my file. Changing my product ID (AT) to 1234 worked for me, too.

---

### Post by angelsneverdie on 2007-02-12
> **TheBlueCow said:**
> For those of you having troubles with your phones, try to sudo chown username:username your ~/.qt/moto4linrc file. I couldn't change any settings or anything because it wasn't actually my file. Changing my product ID (AT) to 1234 worked for me, too.

i know that I may or may not be a complete f*cking idiot, but could you explain the chown thing for us newbies who have absolutely no idea what you mean?

thanks!

---

### Post by Footer on 2007-02-13
> **angelsneverdie said:**
> i know that I may or may not be a complete f*cking idiot, but could you explain the chown thing for us newbies who have absolutely no idea what you mean?

thanks!

You are not a complete f*cking idiot ... just a Linux newb.  :)

```
man chown
```

tells you all about the chown command.  Basically, what it does is changes ownership of the file to whomever you set.  So this command:

```
sudo chown username:group filename.ext
```

changes the ownership of filename.ext to username:group.  Of course, there is no such user as 'username' and probably no group such as 'group' but you get the drift.  Typically, on a Linux system, the username and group are one and the same (not always true on Unix systems).  Just do an ls -al at the console prompt and you will see who owns the files and what group they belong too.

Back to moto4lin:  I've finally got my v3m connected.  But here is the log of what happens after it connects:

Try to connect
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
Getting file list
[error] Unable to get drive list
Complete

What the???  Man, this is bizarre ...

:confused:

---

### Post by angelsneverdie on 2007-02-14
thanks for the explanation . . . i appreciate it.  One day i'll get the hang of this thing.

i tried this in the terminal window:

sudo chown mitchell:mitchell /usr/bin/moto4lin.exe
Password:
chown: cannot access `/usr/bin/moto4lin.exe': No such file or directory

mitchell being my username - am i pointing it to the right file?  i really don't understand how this file system is layed out, I need to do some reading about that.  in any case, thanks again!

-Mitchell

---

### Post by Footer on 2007-02-14
> **angelsneverdie said:**
> thanks for the explanation . . . i appreciate it.  One day i'll get the hang of this thing.

i tried this in the terminal window:

sudo chown mitchell:mitchell /usr/bin/moto4lin.exe
Password:
chown: cannot access `/usr/bin/moto4lin.exe': No such file or directory

mitchell being my username - am i pointing it to the right file?  i really don't understand how this file system is layed out, I need to do some reading about that.  in any case, thanks again!

-Mitchell

Please go back and read post #97.  The poster was referring to your moto4linrc file to chown but I'm sure it's already owned by mitchell:mitchell.

And by the way, Linux doesn't normally have .exe files.  :)  That's a Windoze thang.  :)  But that's OK.  We've all been where you are right now.  Just keep plugging along and welcome to the wonderful world of Linux.  Your computing experience will get better, trust me!

:)

---

### Post by nickispeaki on 2007-02-17
hi! thanks for this howto! i'm from ukraine, and this guys (creator of moto4lin) too! it's amazing! :guitar: 
but how to i read on this forum....  i use linuxmint 2.1 (ubuntu 6.10) . i need g++ ( sudo apt-get install g++ )

and moto4lin i downloaded from sourceforge.net  [http://sourceforge.net/projects/moto4lin/](http://sourceforge.net/projects/moto4lin/)

so.... moto4lin works! it's GREAT! but only from sudo moto4lin..... why?

thanks for comments!

slava Ukraini!
(long live Ukraine! :guitar: )

---

### Post by nickispeaki on 2007-02-17
and motorola c650 (mint linux)

---

### Post by nickispeaki on 2007-02-17
try to download from [http://sourceforge.net/projects/moto4lin/](http://sourceforge.net/projects/moto4lin/) for angelsneverdie

---

### Post by angelsneverdie on 2007-02-17
> **nickispeaki said:**
> try to download from [http://sourceforge.net/projects/moto4lin/](http://sourceforge.net/projects/moto4lin/) for angelsneverdie

the install text file says this:  
o To compile you need:
* QT Library 3.3.3 (c++ headers and binary lib)
* libusb-devel 0.8 (headers and binary lib)
* g++

Installing
========
1.  qmake
    make

2. Now you can run application.

can anyone tell me what that means?  well enough that if i see something like that in the future i'll know what to do?  again, sorry for all the questions...i'm trying.

---

### Post by r0bby1982 on 2007-02-21
> **Brewtal said:**
> I've grabbed all the dependencies, and moto4lin from the cvs repository but when I go to "make" the file I'm getting a error.

```
~/moto4lin$ make
bash: make: command not found
```

Am I missing some other dependency or am I just lucky?

try *sudo apt-get install make* that should fix your problem 

:) Hopefully.

-Rob

---

### Post by MikB on 2007-02-24
Or try using this HOWTO:

[http://www.computechgroup.com/?p=284]("http://www.computechgroup.com/?p=284")

---

### Post by anywebloco on 2007-03-04
HI - I'm trying to connect a V3i on Edgy. The connection seems to work (the phone gets recognised) in P2K mode but then I get the following errors:

[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
Getting file list
[info] Found drives: [ ?¨H· 1U· ]
[info] Search request: [?¨H·/|*]
[debug] Unable to execute search request
[info] Search request: [1U· /|*]
[debug] Unable to execute search request
Complete

Any suggestions?

---

### Post by mlenis on 2007-03-09
Hello Ubuntu family.  I was wondering if anyone has gotten moto4Lin to recognize the Motorola Slvr L7 to do some seem editing?  I need to enable the Java app loder on my phone so that I can install Blooover.  Any help will be greatl appreciated.

Thank you

---

### Post by marcw on 2007-03-09
Fwiw, I could not get moto4lin to work with my Razr using the package found in the Edgy repository no matter what I tried.  I read every post in this thread about 3 times and tried every solution I was able to Google for.  But I had not built it from svn as a couple of posters had suggested.  When I did that, EUREKA!, it worked straight away!

So what I would suggest for anyone who, like me, was having troubles getting the darn thing to work  to build it from scratch using the instructions found here:
[http://moto4lin.sourceforge.net/wiki/SVN_Installation](http://moto4lin.sourceforge.net/wiki/SVN_Installation)

---

### Post by mlenis on 2007-03-11
Ok I downloaded the svn version but I don't know where I downloaded it too.  Is there a default directory where all svn packages get put in?

Thanks

---

### Post by mlenis on 2007-03-11
Im installing it as I type.  I'll let you guys know how it goes.

Thanks

---

### Post by mlenis on 2007-03-11
[info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences

This is what im getting now.

Can anyone tell me why I cant connect to the phone?  

When I click on update lis in preferences my phone shows up with a Vendor ID, Product ID,  Manufact. and product.  So to some degree it is pulling information from th phone.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by LenzM on 2007-03-22
Thanks for the guide, I've got my Motorola L6 hooked up and working now.  I kind of used a hybrid of this guide and the one on the wiki.  This is exactly what I did

```

sudo aptitude install libqt3-mt-dev zlib1g-dev libusb-dev
svn co https://svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin moto4lin
cd moto4lin/
qmake
make
sudo make install
sudo chmod u+s /usr/bin/moto4lin

```

---

### Post by Shampyon on 2007-03-23
> **mlenis said:**
> [info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences

This is what im getting now.

Can anyone tell me why I cant connect to the phone?  

When I click on update lis in preferences my phone shows up with a Vendor ID, Product ID,  Manufact. and product.  So to some degree it is pulling information from th phone.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

I'm having the same problem. I installed everything according to the instructions, but it just refuses to connect.

I'm using a Moto Razr v3i
This is what I get when I open with the Terminal:

```
#sudo moto4lin
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 2
New mode: 1

```

I have no idea what any of that means, and I'm an optimistic fool, so I went ahead and tried everything as per the instructions anyway.

I try to switch the device to P2K, and get this problem:
```
[info] Phone pluged as P2K
[info] Phone pluged as AT
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
```
Doesn't look good. I try connecting anyway:
```
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
```

So now I'm stuck. :confused:

---

### Post by Seine on 2007-04-04
I have problems getting this working. Can anyone help?

Moto4lin version: No version number, built from SVN on 3 April 2007
Distro: Ubuntu Edgy
Phone: Motorola V360

Here's what happens when I follow the instructions.

Terminal:-
```
jem@fawkes:~/t/moto4lin$ sudo moto4lin 
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 2

```

Logging in moto4lin:-
```
Phone is unpluged. Please connect it
Phone pluged as P2K

```
*Already this has diverged from the instructions. Should be plugged as "AT"*

In Preferences I set ACM Device = /dev/ttyACM0

I click View List and find an entry for Motorola Phone (V360). Vendor ID = 22b8, Product ID = 4810.

I click Switch to P2K. Logging in moto4lin says:-
```
error unable to open device
error please check preferences

```

Then, at a guess, I try plugging in product and vendor IDs at random. Nothing makes a difference.

I hope someone can help me please!
Thanks
Jem

---

### Post by shane2peru on 2007-04-04
Ok, I have gotten my phone to connect.  I can add ringers, and pictures, but I can't seem to access my phone book.  Also how would I add a java program.  I have a Razr V3.  Any ideas?  I'm a little more interested in the phone book as I don' t have any java programs to add right now, but I'm sure there are some games out there I could add somewhere.  Thanks.

Shane

---

### Post by Erlander on 2007-04-16
I'm running Feisty beta fully updated and installed Moto4lin from Synapatic.

Phone is recognised correctly as RAZR V3x in the preferences usb list.

This is all I get in the information window:

```
[info] Phone pluged as P2K
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
```

and this in terminal:
```

rob@Ubuntu:~$ sudo moto4lin
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 2
New mode: 1
doActConnect
doActConnect
P2kProc::doConnect()

```

Does anyone have any suggestions (other than get a new phone)

Rob

---

### Post by kuriharu on 2007-04-18
Okay, I've followed that, but I can't get it to connect. It sees the phone in AT mode, but when it tries to switch to P2K mode, it never works. I've written down the vender ID info correctly -- what should i do next?:

---

### Post by simonept86 on 2007-04-23
if you have problem like

> [info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode…
[error] Unable to connect
[info] Phone is unpluged

try to see here:

[http://tuxinside.wordpress.com/2007/04/23/moto4lin-now-work-moto4lin-adesso-funziona/](http://tuxinside.wordpress.com/2007/04/23/moto4lin-now-work-moto4lin-adesso-funziona/)

---

### Post by kuriharu on 2007-04-23
Thanks! I'll try that tonight and post the results.

---

### Post by Erlander on 2007-04-23
Still no luck here.  Razr V3x and Feisty.

Rob

---

### Post by kuriharu on 2007-04-24
No luck. Okay, I give up.  Thanks anyway. I'll give up on moto4lin, but maybe the other one might work. Push comes to shove, I could always *sigh* use the Windows software. ugh.

---

### Post by Erlander on 2007-04-24
It would be nice to get it to work.

One more step to getting rid of Windows.

Rob

---

### Post by cheesepuff on 2007-04-30
Motorola Q, this is the best I got...

[info] Found drives: [ ?èM· ]
[info] Search request: [?èM·/|*]
[debug] Unable to execute search request
Complete
Getting file list

Seems to kind of find it...Considering it's windows mobile im not surprised really

---

### Post by noenter1 on 2007-05-08
Ok... Im wondering is there a way to completely purge the AT mode? First start the program it detects the phone and starts in P2K mode, then it switches over to AT mode and wont let me switch back to P2K.

Edit: This is on Feisty btw.

---

### Post by anjilslaire on 2007-05-19
I've gotten moto4lin to work fully on my l6 with Feisty using the SVN howto posted 
svn co [https://svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin](https://svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin) moto4lin
cd moto4lin/
qmake
make
sudo make install
sudo chmod u+s /usr/bin/moto4lin 

but also edit my moto4linrc to read as 

[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=**4902**
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=**4901**
cfgP2Kvendor=22b8

---

### Post by Mr.Linc on 2007-05-25
Hi,

I just wanted to say *thank you very much* to the guy who started this thread.
I got a v3black a couple weeks ago, tried moto4lin by myself but couldn't get it to work; but now, by following this *howto* it worked just fine.
I'm on Feisty.

:)

---

### Post by serj_alligator on 2007-05-26
For those of you that went over all sorts of manuals and it still didn't work like for me this solution should help...
I had to change some settings for moto4lin to work!
I have Motorola SLVR L7 and running on Fiesty (7.04).

In the phone go to Menu>Settings>Connection>USB Settings>Set=>Default Connection: Data/Fax Connection

Also I have went over steps that **anjilslaire** does, even dough regular package might work just as well...

I hope that it helps you! :D

---

### Post by anjilslaire on 2007-05-26
Your right about the regular version in the repo's. It also works.

The trick for my L6 was the bolded settings in my earlier post. The values were swapped by default.
cfgATproduct=**4902**
cfgP2Kproduct=[B]4901
[/B]
I'll have to check my phone settings too :)

EDIT:
My SLVR L6 has only has
Menu>Settings>Connection>Blutooth Link
or
Menu>Settings>Connection>Sync

Ah we,, it works fine for me as noted.

---

### Post by Tombo5150 on 2007-06-04
I just got a brand new phone. Apparently, this phone is a very brand new model too. Its the Motorola RIZR Z3. I have successfully downloaded moto4lin from synaptic (i'm on feisty 7.04). I'm getting nothing....is there any way to get around the fact that I have a brand new phone that hardly anyone out in the market has yet?

---

### Post by anjilslaire on 2007-06-05
Most motos have similar settings. Check my settings a couple posts up to see if changing things up a bit work

---

### Post by Tombo5150 on 2007-06-06
I don't understand where to put in anything. In the terminal? or in moto4lin?

---

### Post by nickispeaki on 2007-06-13
# sudo chown root /usr/bin/moto4lin
# sudo chmod u+s /usr/bin/moto4lin

The above gives possibility to use software without necessity of logging as root. You can also run the command with sudo command.


very usefull too lines!!!!!!

from here:
[http://moto4lin.sourceforge.net/wiki/SVN_Installation](http://moto4lin.sourceforge.net/wiki/SVN_Installation)

---

### Post by nickispeaki on 2007-06-13
just go to:
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmoto4lin%2Fmoto4lin_0.3%2Bsvn20060819-1_i386.deb&md5sum=c1cb53f849e85c2d3c46f82946945a52&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmoto4lin%2Fmoto4lin_0.3%2Bsvn20060819-1_i386.deb&md5sum=c1cb53f849e85c2d3c46f82946945a52&arch=i386&type=main)

(for moto4lin in .deb-file)

install it

type commands (in terminal, of course!):

# sudo chown root /usr/bin/moto4lin
# sudo chmod u+s /usr/bin/moto4lin

The above gives possibility to use software without necessity of logging as root. You can also run the command with sudo command.

GoTo: Settings -> Preferences...
Set 'ACM Device' = '/dev/ttyACM0'

Enjoy!

---

### Post by dj_flx on 2007-06-16
I've tried everything I could find for my RAZR V3m, even up to and including the SVN compile and install.

I get no further than:

```
[info] Phone pluged as P2K
Try to connect
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
Getting file list
[error] Unable to get drive list
Complete
```

Nothin'.

---

### Post by paulieman on 2007-06-16
I've got my Alltel V3M working perfectly...  However, I cannot see the microSD card that is installed in the file manager...  Anyone else have this problem?

kjava appears to be junk too...  get the following error:  [error] Unable to get J2MEST

Thanks to those that have figured this out!  Was a PITA, but gets me one more application away from Winblows!

~Paul

---

### Post by kcfoxie on 2007-06-23
Hey everyone,

I'm a n00b to the Linux world. I have Edgy Eft installed on an older Apple iBook (PowerPC). I managed to compile Moto4Lin to access my V235 under Mac OS X 10.4.9 w/ the latest dev tools at work, and my phone connected. Using Parallels on my Intel MacBook at home w/ the KMobilePhone Tools LiveCD, I can also access the phone from the i386/KDE Build. However, try as I might, using SVN and CVS, I cannot get the phone to connect on my Ubtuntu machine. I have Hoary installed on another iMac, but I can't find a repository that will let me install the needed files to attempt to compile it on that system.

Basically, the problem I have is that p2ktest fails to get the phone name, directories, etc. It is a A and C drive phone, and according to the wiki you just need to compile the moto4lin source from the cvs server. No dice for me, I've pvt'd the guy who posted w/ the same problem and asked if he had to reconfigure the makefile or anything to get it working. I did have issues under OS X to get it compiled, but I managed to get it working. 

If anyone can offer me any assistance on how to get the program compiled for PPC/Ubuntu 6.10 I'd be very greatful. I may attempt to upgrade to 7.04 again, the last time bonnaro (I think) failed to initialize, and it gendered the GNOME environment quite crippled. But that's a story for anothe day!

Thank you all so much

~kc

---

### Post by s1ightcrazed on 2007-07-01
> **paulieman said:**
> I've got my Alltel V3M working perfectly...  However, I cannot see the microSD card that is installed in the file manager...  Anyone else have this problem?

~Paul

Yup.... and SVN so far has not fixed it. 

dj_flx - look at the moto4lin wiki under supported models for SPECIFIC instructions on the V3M. These worked for me (mainly because I was the one who posted the wiki entry ;) ) and the should work for any v3m.

---

### Post by dj_flx on 2007-07-01
> **s1ightcrazed said:**
> Yup.... and SVN so far has not fixed it. 

dj_flx - look at the moto4lin wiki under supported models for SPECIFIC instructions on the V3M. These worked for me (mainly because I was the one who posted the wiki entry ;) ) and the should work for any v3m.

This page?

[http://moto4lin.sourceforge.net/wiki/Razr_V3m](http://moto4lin.sourceforge.net/wiki/Razr_V3m)


That's one place I've already been, I'm afraid. I'll have to try again from scratch later, I guess.

Maybe there's something about Verizon messing things up?

---

### Post by s1ightcrazed on 2007-07-02
Possible that your product ids are different. My phone is from verizon as well. Check your product IDs, the only real tricky thing is that the AT prod ID needs to be 1 higher then the P2K one.

---

### Post by starscalling on 2007-07-10
gah had to compile from svn - and to get that had to go to their page - seems to be a little different now on the exact command - so replace cvs with svn first
then i had to do sudo su
and fiddle with the darn thing
but i got it working with my l7
seems to see the mem card too :>

---

### Post by S.Peterman on 2007-07-10
Just wanted to say thanks for posting this great tut, and that this works for the slvr l2's.

---

### Post by sprice on 2007-07-12
I have a SLVR L71 and nothing seems to be working for me.

here's the output of p2ktest

```

22b8:4810: [Motorola Inc.] [Motorola Phone (L71)]
045e:0039: [Microsoft] [Microsoft IntelliMouse Optical]
03f0:3f11: [hp] [psc 1310 series ]
413c:2005: [DELL] [DELL USB Keyboard]
051d:0002: [American Power Conversion] [Smart-UPS 1500 FW:601.3.D USB FW:8.1]
0000:0000: [Linux 2.6.20-16-generic ohci_hcd] [OHCI Host Controller]
0644:0200: [TEAC] [CA-200]
0000:0000: [Linux 2.6.20-16-generic ehci_hcd] [EHCI Host Controller]
No phone found.

```

At the top it lists my L71 but then at the bottom it says no phone found!

---

### Post by neilq101 on 2007-07-12
I'm trying to get my sister's v235 to sync with Ubuntu Feisty to help her ditch windows, and while Wammu/Gammu syncs successfully, it is incapable of syncing pictures, multimedia and java apps, so i need this to work.  When i start the app and click Connect/Disconnect, it comes up with  

[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect

No random messing around with the numbers seems to work, does anybody have any ideas on how to make them interface properly?

---

### Post by FleetAdmiral74 on 2007-07-21
I am having trouble downloading the source from that repository, I get something about no route to host...can anyone give me a hand? Running Feisty...

---

### Post by nickispeaki on 2007-07-21
ALL, ALL, ALL!

so!

if NOthing can you help JUST CLICK Connect/Disconnect button on higher/left coner.  

It's help me!

andDDDDDDD


read FIRST (AGAIN) page -

i do this things/

waw! i setup this complex prog (moto4lin)  may be 5 time and every each time read manual. especilly on this forum....


how i want to just enjoy whithout this commands, terminals. just plag and just work

God save me from this HELL!:guitar:

---

### Post by nickispeaki on 2007-07-21
> **FleetAdmiral74 said:**
> I am having trouble downloading the source from that repository, I get something about no route to host...can anyone give me a hand? Running Feisty...

try this!

packages.debian.org/unstable/comm/moto4lin

---

### Post by FleetAdmiral74 on 2007-07-21
> **nickispeaki said:**
> try this!

packages.debian.org/unstable/comm/moto4lin

That worked great, thanks!

Now I just have to hope the rest of the instructions at [http://www.younevercall.com/Ubuntu-Ringtones.htm](http://www.younevercall.com/Ubuntu-Ringtones.htm) go nice and smoothly.

---

### Post by dj_flx on 2007-07-21
=sigh=

Tried everything, still nothing.

Works fine with Motorola Phone Tools on WinXP, so I know the phone and USB cable are good. Have all the SEEM hacks in place to enable everything the Verizon V3c can do (USB, multimedia recognized by phone tools).

It connects, but cannot get device, drive/file list, etc.

Is there anything I can look at to post that would help knocking this thing into shape? :confused:

---

### Post by FleetAdmiral74 on 2007-07-21
Well I created the file, but get an error when trying to dl it to the phone. 

[info] Phone is unpluged
Downloading 1 file(s)
Downloading: /a/mobile/audio/moto~~.mp3 (63287 bytes)
[error] Unable to download files

I don't hink its too bid...could it be the bitrate wrong? How do I change that in Audacity?

edit3: its on the phone, but when browing it just comes back to the audio menu if I scroll to the end...i'm so close, I can feel it! Do I need to convert the mp3 to imy, or what? I deleted the mp3, but it still falls back to the audio menu when I scroll to the end of the list.

---

### Post by greenwom on 2007-07-24
> **anjilslaire said:**
> I've gotten moto4lin to work fully on my l6 with Feisty using the SVN howto posted 
svn co [https://svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin](https://svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin) moto4lin
cd moto4lin/
qmake
make
sudo make install
sudo chmod u+s /usr/bin/moto4lin 

but also edit my moto4linrc to read as 

[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=**4902**
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=**4901**
cfgP2Kvendor=22b8



THIS SOLVED IT<<<<<< This should get placed in the wiki....

---

### Post by psyopper on 2007-07-29
I'm not sure why I'm posting this, everyone that posts that their phone doesn't connect properly is generally ignored it seems. But here goes anyway...

Phone AT&T RAZR V3xx
moto4lin installed by SVN [as outlined here]("http://moto4lin.sourceforge.net/wiki/SVN_Installation")
Phone is set for Data Connection in Settings | Connections | USB Settings | Default Connection on the phone.

My moto4linrc reads as follows:
[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=6402
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=6401
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=0
cfgGoLastFolder=0
cfgLoadList=0

When I launch moto4lin from the command line I get:
```

$ moto4lin
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 1
P2kProc::doConnect()
New mode: 2
doActConnect
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Broken pipe]
(E_getPhoneName: E001)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Broken pipe]
(E_getDriveName: E001)
sendControl Error:[error sending control message: Broken pipe]
(E_fileCount: E001)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Broken pipe]
(E_getDriveName: E001)


```

Moto4Lin shows:
[info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 OK 
[info] Phone answer: OK 
[info] Phone pluged as P2K
[info] Phone connected as P2K
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...
[error] Unable to get phone model
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...
[error] Unable to get drive name
[info] Sending control message failed.. Retry...
[error] Unable to get file count
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...
[error] Unable to get drive name

When I plug the phone in *before* launching moto4lin the little USB icon show up on the phone. When I launch moto4lin the icon goes away and the phone no longer shows "USB Connection" on the display, instead it just says "Charge Complete".

If I plug the phone in while moto4lin is running the USB icon shows up for a split second then goes away and "Charge Complete" appears on the display.

Seems to me there is something about the "Broken Pipe" error that could be the problem. Anyone know what the broken pipe message is about. I realize that the "pipe" is the data channel, but that's about all I know about pipes.

Any love out there?

---

### Post by ahchong on 2007-07-30
ive been trying to install the moto4lin.
but... ive encounter during the compile area. when the logging 
 "cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin" it wrote connection time out. ive try i many time but it seems same. and then cannot compile the moto4lin. ive use AMD 64-bit,  does this related?


Edit* from the link i cannot connect but when i try on other pages link. i can connect to the server... and got something problem...

ahchong@Emily:~$ cd moto4lin
ahchong@Emily:~/moto4lin$ make
cd moto_ui && make -f Makefile
make[1]: Entering directory `/home/ahchong/moto4lin/moto_ui'
g++ -c -pipe -Wall -W -g -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Iui/ -I. -Imoc/ -o obj/main.o main.cpp
make[1]: g++: Command not found
make[1]: *** [obj/main.o] Error 127
make[1]: Leaving directory `/home/ahchong/moto4lin/moto_ui'
make: *** [sub-moto_ui] Error 2


HELP!!!

---

### Post by ahchong on 2007-07-31
YO!!!...
ive follow the intrcution but something came up.
can u help me with this?

ahchong@Emily:~$ cd moto4lin
ahchong@Emily:~/moto4lin$ make
cd moto_ui && make -f Makefile
make[1]: Entering directory `/home/ahchong/moto4lin/moto_ui'
g++ -c -pipe -Wall -W -g -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Iui/ -I. -Imoc/ -o obj/main.o main.cpp
make[1]: g++: Command not found
make[1]: *** [obj/main.o] Error 127
make[1]: Leaving directory `/home/ahchong/moto4lin/moto_ui'
make: *** [sub-moto_ui] Error 2

tell me k...

---

### Post by tonikay on 2007-07-31
Hi guys,

I've had a r4ead through all the post and i can't seem to find anything that answers my question. Please forgive me if i've missed something.

Just trying to comment my v3 to feisty.

Initially moto4lin detects the phone and i get the messaage:

phone pluged as AT

but as soon as i hit connect i get:

[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 OK 
[info] Phone answer: OK 
[error] Unable to connect
[info] Phone is unpluged

and my phone stops charging. If i unplug the usb cable and try again i get the same error.

Any ideas?

---

### Post by ahchong on 2007-08-01
how to make the moto4lin change back to AT read V3X?
after swith to P2K mode?

---

### Post by ironmonkeygf on 2007-08-02
> **ahchong said:**
> how to make the moto4lin change back to AT read V3X?
after swith to P2K mode?

Click the reboot phone button and the phone should reboot and be in AT mode.

---

### Post by lownslow on 2007-08-02
Hi, I'm pretty new to linux so I hope I can get this across without too much confusion.
I followed the directions, and at the command cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
I get the error "no route to server". So then I went to the sourceforge web site and downloaded the moto4lin-0.3 and pk2 packages. They show up on my computer in my home directory. There is a link for "moto4lin", but it is broken...doesn't open the application. I'm also unable to run any of the commands such as....
~$cd moto4lin
~/moto4lin$qmake
~/moto4lin$make
~/moto4lin$sudo make install.
Thanks

edit: I saw the post about cvs being obsolete, I'll try try the svn and see what happens. Thanks.

---

### Post by belaflek on 2007-09-12
Well..Im seeing the RAZR v3xxx in the devices under the pref part. 

At first it was trying to connect to /dev/usb/acm/0 so I made a symbolic link before I relized how to change it in the ~/home/username/.qt folder (this seems to be where the settings for the program are kept) Currently

cfgACMdevice=/dev/ttyACM0
cfgATproduct=6410
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=6410
cfgP2Kvendor=22b8

Its still unable to connect with 
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: =8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 AT+MODE=8 
[debug] nread=0, errno=25
[error] Unable to connect

---

### Post by Bollinja on 2007-09-22
> **neilq101 said:**
> I'm trying to get my sister's v235 to sync with Ubuntu Feisty to help her ditch windows, and while Wammu/Gammu syncs successfully, it is incapable of syncing pictures, multimedia and java apps, so i need this to work.  When i start the app and click Connect/Disconnect, it comes up with  

[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect

No random messing around with the numbers seems to work, does anybody have any ideas on how to make them interface properly?

I had this error with my V220, this worked for me:

[I]A couple of tips

After reading the "Note to USB cable users" above and after some guessing I was able to make my V3 connect by:

   1. Setting the AT Vendor ID to 22b8
   2. Setting the AT Product ID to a random number (4164 in my case :P)
   3. Setting the P2K Vendor ID to 22b8
   4. Setting the P2K Product ID to 4901 (the auto detection set it to 4902, which wouldn't work)
   5. Clicking on "Switch to P2K"
   6. Connecting to the phone on the main window [/I]

from:

[http://moto4lin.sourceforge.net/wiki/Razr_V3-HELP](http://moto4lin.sourceforge.net/wiki/Razr_V3-HELP)

I also had to change the ACM Device under Preferences to /dev/ttyACM0

Hope that helps :)

---

### Post by Siph0n on 2007-10-03
I have a Motorola L7c from Verizon and am trying to use Moto4Lin to connect to it.... I plugged my phone into my computer using a usb cable, but the only devices that showed up are a bunch of /dev/usbdev1.17_ep* and also a /dev/bus/usb/001/017 device... I than run sudo moto4lin, and click Settings->Preferences. Under 
ACM Device : /dev/bus/usb/001/017
AT Vendor ID : 22b8
AT Product ID : 2a64
P2K Vendor ID : 22b8
P2K Product ID : 4901

I click on Update List and see two items:
UHC Host Controller
Motorola K1m/L7c - I see the Product ID of 2a64 here....

I click the Motorola one and click Switch to P2K and in the screen in the background it says "Please check preferences". I also click OK and than Connect, and it says it can't connect. Any idea what I am doing wrong???

---

### Post by gordwait on 2007-10-31
I spent the last hour trying to get this to work with a V3C Razr,
Here is what I learned (hopefully save someone else the hour)

1: Moto4lin or pk2test do not work with my phone

- moto4lin reports 22b8:2a61 for the P2K Id's

- One problem is that the linux kernel module cdc-acm was hogging the usb connection, so that moto4lin would fail to connect. 

This helped clear that out:
[http://moto4lin.sourceforge.net/wiki/User_talk:Dion](http://moto4lin.sourceforge.net/wiki/User_talk:Dion) 

(in a nutshell, try rmmod cdc-acm to kill off the offending linux kernel module)

Once I did the rmmod trick, the phone connected - yay? - nope, 
 I got this from moto4lin:

[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name

Seems like this phone has newer firmware. 

The p2ktest - it only checks for phones with the 4901/4902 ID, if you hack the source and put in 2a61, then it finds the phone, then prints the same errors as moto4lin (Unable to get ....)..

Ah well, good luck!

---

### Post by theophiles on 2007-11-04
after I put in

cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin

I get

cvs [checkout aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host

that might be why this whole thing is not working. for me

---

### Post by Mark_in_Hollywood on 2007-11-16
Yikes: is there a more recent How-to for Moto4Lin?

Just in case there really is a simple way to do this:

relevant lsusb:

mark@Lexington:~$ lsusb
Bus 001 Device 007: ID 22b8:4902 Motorola PCS E398 GSM Phone

and

mark@Lexington:~$ sudo moto4lin
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 1

As a non-programmer, I can't tell what this all means. Is there an easy way to get this working? Any way easy or not?

---

### Post by rexxxlo on 2007-11-18
its 2:45 in the morningi just readal the posts on this cant get it to connect completely 

it will connect for min but will not let me browse the files or change anything

i think it might have something to do with my 64bit system and os ??

if it mess with the product id and vendor id i get this

[info] Phone is unpluged. Please connect it
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: AT E0 
[info] Phone answer: OK 
[info] Phone pluged as AT
Getting file list
[error] Unable to get drive list
Complete


then it will not reconnect gain until i restart the program 

it shows the phone in the file manager but has no access to it 

i followed this wiki also  to no avail

im confused

---

### Post by dondad on 2007-11-22
When I do this:
```

cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login

```




I get this:
```

Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password: 
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host

```

I hit enter at the password prompt

---

### Post by Blake27 on 2007-11-23
There is an Ubuntu package available in Gutsy.  
```
sudo apt-get install moto4lin
```

---

### Post by thetimekeeper on 2007-12-06
> **nickispeaki said:**
> just go to:
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmoto4lin%2Fmoto4lin_0.3%2Bsvn20060819-1_i386.deb&md5sum=c1cb53f849e85c2d3c46f82946945a52&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmoto4lin%2Fmoto4lin_0.3%2Bsvn20060819-1_i386.deb&md5sum=c1cb53f849e85c2d3c46f82946945a52&arch=i386&type=main)

(for moto4lin in .deb-file)

install it

type commands (in terminal, of course!):

# sudo chown root /usr/bin/moto4lin
# sudo chmod u+s /usr/bin/moto4lin

The above gives possibility to use software without necessity of logging as root. You can also run the command with sudo command.

GoTo: Settings -> Preferences...
Set 'ACM Device' = '/dev/ttyACM0'

Enjoy!
Bahaha, worked for me! I changed permissions as above, and changed my AT product ID to 4902, one more then my P2K ID, restarted, and it connected and updated flawlessly, whereas before I had the could not open phone error. Give it a try :)

---

### Post by atomicpc on 2008-01-12
I think cvs in moto4lin is dead. Use svn instead.

I get errors. It appears that the phone is connected but it can't see the drive or whatever.

---

### Post by Skully on 2008-01-18
I'm getting this:

[info] Phone pluged as P2K
Try to connect
[info] Phone connected as P2K
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...
[error] Unable to get phone model
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...
[error] Unable to get drive name
[info] Sending control message failed.. Retry...
[error] Unable to get file count
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...
[error] Unable to get drive name
Getting file list
[info] Sending control message failed.. Retry...
[info] Sending control message failed.. Retry...[info] Phone pluged as P2K

And then my phone goes to an option screen: 

Would you like to view your personnel settings?
As if to taunt me.  

After a few times it gave my the option to not see the personnel settings screen any more.  But still no progress. 

This is really frustrating.  I know which phone company isn't getting any more of my money once my contract is up.

If anyone can help I'd be very grateful.

Oh  yeah, here's my terminal output if that helps any: 

yeti@ubuntu:~$ sudo moto4lin
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 2
P2kProc::doConnect()
doActConnect
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getPhoneName: E002)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getDriveName: E002)
sendControl Error:[error sending control message: Broken pipe]
(E_fileCount: E001)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getDriveName: E002)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getDriveName: E002)

Also, I can't cd into my .qt folder.  It says "Permission denied"  
I tried chmod, but can only change file permissions, not folders.  Am I missing something here? 

Thanks!

---

### Post by bharadwaj on 2008-01-28
the coolest one......man this rox
Perfect replacement for my emulated moto software

---

### Post by Matteran on 2008-03-17
So... I've been trying to get my V3 working, and nothing works. I do a p2ktest and this is the output:

```
Switching to P2K...
P2k Phone found

Phone Model: V3
Drive: /a
Free space: 5600684 bytes
File count: 492 bytes
{then proceeds to list all the files in the filesystem}

```

So... I can read the file system... but moto4lin will not for the life of me actually connect and read that info from p2k... any ideas?

---

### Post by midia on 2008-03-26
Hi,  Thanks for this but It doesn't work for my k1m krzr and I need your help.  Here's the output from moto4lin (run under 'sudo moto4lin'):

[info] Phone is unpluged. Please connect it
[info] Phone pluged as P2K
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
:
$lsusb = 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 22b8:2a64 Motorola PCS 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000 

So, we're hooked up.

/var/log/messages = 
 tail /var/log/messages
Mar 26 20:45:18 mks-sdb1 kernel: [ 1889.842537] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Mar 26 20:45:27 mks-sdb1 kernel: [ 1899.519878] usb 3-2: USB disconnect, address 3
Mar 26 20:45:40 mks-sdb1 kernel: [ 1913.340805] usb 3-2: new full speed USB device using ohci_hcd and address 4
Mar 26 20:45:41 mks-sdb1 kernel: [ 1913.554581] usb 3-2: configuration #1 chosen from 1 choice

No mention of which /dev/tty to connect to.

Any thoughts? :confused:

Thanks,
Midia

---

### Post by midia on 2008-03-26
CVS IS NO LONGER USED:

obtaining moto4lin source from Subversion

...the summary is:

svn co [https://moto4lin.svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin](https://moto4lin.svn.sourceforge.net/svnroot/moto4lin/trunk/moto4lin) moto4lin

See more here:  [http://moto4lin.sourceforge.net/wiki/SVN_Installation](http://moto4lin.sourceforge.net/wiki/SVN_Installation)

Take care,
Midia

---

### Post by keforex on 2008-05-07
Hello all

Following the tutorial steps on page 1 (in bold here) I get the folowing problems:

**Click 'Update List' -> retrieves a list of the 'AT Vendor ID' and 'AT Product ID' of all your USB devices. Find your cell phone's AT IDs from the list.**

--- Did that, ok.


**Select 'Switch to P2K' -> if it is successful, it should say '[info] Phone pluged as P2K' in the status bar of the main window.**

--- Did that, not ok. **[COLOR="Red"]error:Unable to open device[/COLOR]** and **[COLOR="Red"]error:Please check preferences.[/COLOR]**

Under preferences, the USB view shows my Razor there, AT vendor ID = 22b8 and Product ID = 2a64.

My phone is a sprint red motorola razor and I am using a regular digital camera USB cable.

What should I do to solve the above problem that happens when I click the button entitled "Switch to P2K"?

---

### Post by theophiles on 2008-05-07
I'm having the same problem with mine as keforex. Same phone, but US Cellular.

---

### Post by ventu on 2008-05-28
Hello Ubuntu forums, I havn'y yet to look through the whole thread but is there a way to 'start over' per-say with this, I've been trying to hook up a Razr v3 and a V555 with this.  I keep getting several errors such as:

[info] Phone pluged as P2K
[info] Phone pluged as AT
Try to connect
[error] Unable to connect

$ sudo moto4lin
Form1
PhoneMan
New mode: 2
New mode: 1
P2kProc::doConnect()


Like its doubling up for some reason, I would just like to start over and try it again.  I just didn't know how to go about this. Also I know this isn't the correct thread but how do I 'uninstall' a program like this, a complied one so that i can start over. *possible that was a dumb question* :P

Thanx guys

---

### Post by Chilongola on 2008-06-08
Been trying to use moto4lin with V3i to no avail.  I tried with an L6 and a V3r and bingo works perfect.  With V3i it cannot fine phone model.  Update list etc does not work with this phone but very well with other 2.

---

### Post by ~sHyLoCk~ on 2008-07-05
Not working in my Motorazr2 V8. Anyone has checked if this phone works?

---

### Post by richrock on 2008-07-09
I've had no luck so far with Hardy Heron 8.04 and Moto4lin.  

The initial setup said to set the ACM device to 
```
/dev/ttyACM0
``` yet everytime I restart or save any changes, I get ```
/dev/tty/ACM0
```
And when I switch to P2K I get :
```

[info] AT phone found
[info] Switching device /dev/tty/ACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
```
The status bar stays on Mode: AT

and the terminal output is :
```

Form1
PhoneMan
New mode: 1
P2kProc::doConnect()
doActConnect
doActConnect
P2kProc::doConnect()
```

Oh, and it's a V3i

I think it's soemthing to do with the ttyACM0 > tty/ACM0 but not sure how to fix this...

Rich

---

### Post by Road on 2008-07-21
> **richrock said:**
> I've had no luck so far with Hardy Heron 8.04 and Moto4lin.  

The initial setup said to set the ACM device to 
```
/dev/ttyACM0
``` yet everytime I restart or save any changes, I get ```
/dev/tty/ACM0
```
And when I switch to P2K I get :
```

[info] AT phone found
[info] Switching device /dev/tty/ACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
```
The status bar stays on Mode: AT

and the terminal output is :
```

Form1
PhoneMan
New mode: 1
P2kProc::doConnect()
doActConnect
doActConnect
P2kProc::doConnect()
```

Oh, and it's a V3i

I think it's soemthing to do with the ttyACM0 > tty/ACM0 but not sure how to fix this...

Rich

Look for ./qt/moto4lin  If your run it as user it can read it but cant change it.  You can also just sudo and change it by hand as it it has the exact same settings.

While I got around this problem mine throws and error

sendControl Error:[error sending control message: Broken pipe]

sendControl Error:[error sending control message: Invalid argument]
(E_getPhoneName: E002)

V3

---

### Post by serfcx on 2008-07-22
Tried everything to connect my L6 to Ubuntu Hardy, get connected as P2K but then error in terminal as follows 

P2kProc::doConnect()
doActConnect
(E_getPhoneName: E001)
(E_getDriveName: E001)
(E_fileCount: E002)
(E_getDriveName: E001)

Message in moto4lin unablr to get phone model,drive name and file count.

Any help on where to go from here ?

---

### Post by wnelson on 2008-07-25
I had to add this to the end of /etc/modprobe.d/alias to get my motorola w385 to work.

$ /sbin/lsusb | grep -i "motorola pcs"

Bus 004 Device 018: ID 22b8:2b24 Motorola PCS
                         |    |
                      Vendor:Product

Make sure you vendor= and product= are your phones id's.

Also change the usb:vVENDOR8pPRODUCT* to also reflect your id's.

alias usb:v22B8p2B24* usbserial
options usbserial vendor=0x22b8 product=0x2b24

dmesg will result in /dev/ttyUSB0 and 1

This site will help also.

[http://www.arachnoid.com/linux/linux_mobile_internet_access.html](http://www.arachnoid.com/linux/linux_mobile_internet_access.html)


Walt
Tacoma, WA

---

### Post by anjilslaire on 2008-07-26
check my post here for my L6 SLIVR. Still works gerat in Hardy:

[http://ubuntuforums.org/showpost.php?p=2686308&postcount=127]("http://ubuntuforums.org/showpost.php?p=2686308&postcount=127")

---

### Post by tman-ph on 2008-07-30
in hardy, install moto4lin and p2kmoto:

sudo apt-get install moto4lin p2kmoto

then run p2ktest. if you see the files in your phone then you should be able to connect to it using moto4lin.

remember to run it as root:

sudo moto4lin

thanks moto4lin! it think it's better than motorola phone tools for windows!

---

### Post by Fintan on 2008-07-31
Thank you for that but this is what I get:

> fintan@fintanws2:~$ p2ktest
P2k Test
Device list:
03f0:5c11: [HP] [Photosmart C4200 series]
0000:0000: [] []
0000:0000: [] []
055d:1060: [] []
0000:0000: [] []
22b8:4902: [] []
0000:0000: [] []
Switching to P2K...
P2k Phone found

(E_p2k_connect.-3: Unable to set configuration)
 Error:[error sending control message: Operation not permitted]
(E_p2k_getPhoneName.-14: E001)
Can not get phone model
 Error:[error sending control message: Operation not permitted]
(E_p2k_getDriveName.-14: E001)
Can not get drive name
 Error:[error sending control message: Operation not permitted]
(E_p2k_freeSpace.-14: E001)
Can not get free space Error:[error sending control message: Operation not permitted]
(E_p2k_fileCount.-14: E001)
Can not get file count Error:[error sending control message: Operation not permitted]
(E_p2k_fileCount.-14: E001)
(E_p2k_fileList.-14: E000)
fintan@fintanws2:~$

on all of my usb ports

Kubuntu Hardy kde3.5.9 / kde4.1 (upgraded to today)

Any ideas?

---

### Post by Endolith on 2008-08-27
> **Fintan said:**
> Thank you for that but this is what I get:

Error:[error sending control message: Operation not permitted]

on all of my usb ports

Any ideas?


Do you need to run this program as root?

[http://ubuntuforums.org/showthread.php?p=5671038#post5671038](http://ubuntuforums.org/showthread.php?p=5671038#post5671038)

---

### Post by cmtsailor on 2008-08-29
when I login to cvs I can't get past the password request by hitting enter.  I just time out...

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-05
ya so any update to this

---

### Post by upforthedownstroke on 2008-09-05
I'm having some problems with this one too. I can see my file list when I run ```
sudo p2ktest
```, and thus I've attempted to run ```
sudo moto4lin
``` but the terminal still spits this out when I attempt to connect to the phone:

```
will@GNUthought:~$ sudo moto4lin
Form1
PhoneMan
New mode: 1
New mode: 2
doActConnect
doActConnect
P2kProc::doConnect()
doActConnect
(E_getPhoneName: E001)
(E_getDriveName: E001)
(E_fileCount: E002)
(E_getDriveName: E001)
(E_getDriveName: E001)


```

moto4lin usually spits this out:

[info] Phone pluged as AT
[info] Phone pluged as P2K
Try to connect
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
Getting file list
[error] Unable to get drive list
Complete

HALP!

---

### Post by upforthedownstroke on 2008-09-05
Update:
I was able to get it working by editing my moto4linrc to read as follows:

```
[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=4902
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=4901
cfgP2Kvendor=22b8
```

---

### Post by Chilongola on 2008-09-05
where can I find that file?

---

### Post by upforthedownstroke on 2008-09-06
> **Chilongola said:**
> where can I find that file?

/home/user/.qt/moto4linrc

You must edit as root.

---

### Post by anjilslaire on 2008-09-06
Ah, just like I had it configured on the previous page ;)
[http://ubuntuforums.org/showpost.php?p=2686308&postcount=127](http://ubuntuforums.org/showpost.php?p=2686308&postcount=127)

It's located in /home/USERNAME/.qt/

---

### Post by LexRoss on 2008-09-09
> **upforthedownstroke said:**
> Update:
I was able to get it working by editing my moto4linrc to read as follows:

```
[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=4902
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=4901
cfgP2Kvendor=22b8
```

Still did not help with my Motorola SLVR L9. Here is what I get on Hardy 8.04 before and after editing the file.

Originally I had cfgAutoConnect=0 in my ~/.qt/moto4linrc file and the output of p2ktest was

```
$ sudo p2ktest
P2k Test
Device list:
0000:0000: [Linux 2.6.24-19-generic ehci_hcd] [EHCI Host Controller]
174f:6a31: [] []
0bda:0116: [] []
0000:0000: [Linux 2.6.24-19-generic ehci_hcd] [EHCI Host Controller]
22b8:4901: [] [?]
0000:0000: [Linux 2.6.24-19-generic ohci_hcd] [OHCI Host Controller]
0000:0000: [Linux 2.6.24-19-generic ohci_hcd] [OHCI Host Controller]
P2k Phone found

(E_p2k_connect.-4: Unable to claim the interface)
 Error:[error sending control message: Broken pipe]
(E_p2k_getPhoneName.-14: E001)
Can not get phone model
 Error:[error sending control message: Broken pipe]
(E_p2k_getDriveName.-14: E001)
Can not get drive name
 Error:[error sending control message: Broken pipe]
(E_p2k_fre$ sudo p2ktest
P2k Test
Device list:
0000:0000: [Linux 2.6.24-19-generic ehci_hcd] [EHCI Host Controller]
174f:6a31: [] []
0bda:0116: [] []
0000:0000: [Linux 2.6.24-19-generic ehci_hcd] [EHCI Host Controller]
22b8:4901: [] [?]
0000:0000: [Linux 2.6.24-19-generic ohci_hcd] [OHCI Host Controller]
0000:0000: [Linux 2.6.24-19-generic ohci_hcd] [OHCI Host Controller]
P2k Phone found

(E_p2k_connect.-4: Unable to claim the interface)
 Error:[error sending control message: Broken pipe]
(E_p2k_getPhoneName.-14: E001)
Can not get phone model
 Error:[error sending control message: Broken pipe]
(E_p2k_getDriveName.-14: E001)
Can not get drive name
 Error:[error sending control message: Broken pipe]
(E_p2k_freeSpace.-14: E001)
Can not get free space Error:[error sending control message: Broken pipe]
(E_p2k_fileCount.-14: E001)
Can not get file count Error:[error sending control message: Broken pipe]
(E_p2k_fileCount.-14: E001)
(E_p2k_fileList.-14: E000)
eSpace.-14: E001)
Can not get free space Error:[error sending control message: Broken pipe]
(E_p2k_fileCount.-14: E001)
Can not get file count Error:[error sending control message: Broken pipe]
(E_p2k_fileCount.-14: E001)
(E_p2k_fileList.-14: E000)

```

Then I've modified the file as suggested with cfgAutoConnect=1. What I have is this:

```
$sudo p2ktest
P2k Test
Device list:
0000:0000: [Linux 2.6.24-19-generic ehci_hcd] [EHCI Host Controller]
174f:6a31: [] []
0bda:0116: [] []
0000:0000: [Linux 2.6.24-19-generic ehci_hcd] [EHCI Host Controller]
22b8:4902: [Motorola Inc.] [Motorola Phone (L9)]
0000:0000: [Linux 2.6.24-19-generic ohci_hcd] [OHCI Host Controller]
0000:0000: [Linux 2.6.24-19-generic ohci_hcd] [OHCI Host Controller]
Switching to P2K...
P2k Phone found

(E_p2k_openPhone.-1: no p2k phone)
(E_p2k_sendControl.-6: no connection)
(E_p2k_getPhoneName.-14: E001)
Can not get phone model
(E_p2k_sendControl.-6: no connection)
(E_p2k_getDriveName.-14: E001)
Can not get drive name
(E_p2k_sendControl.-6: no connection)
(E_p2k_freeSpace.-14: E001)
Can not get free space(E_p2k_sendControl.-6: no connection)
(E_p2k_fileCount.-14: E001)
Can not get file count(E_p2k_sendControl.-6: no connection)
(E_p2k_fileCount.-14: E001)
(E_p2k_fileList.-14: E000)

```

Any ideas?

---

### Post by TwiceOver on 2008-09-09
```

Installing moto4lin

We are going to get the moto4lin source from a cvs repository. You might get an error from cvs at this stage, ignore and proceed. Asked for password? Just press Enter.
Code:

~$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login

```

At this point I receive a password prompt and hit "enter" and it just drops to the next line blank blinking cursor, does not continue.

EDIT:  After about 5 minutes:

```

dan@dan-laptop:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password: 
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: Connection timed out

```


Any ideas?

---

### Post by lernatix on 2008-09-26
Does this work with 'hardy' 8.04?

---

### Post by lernatix on 2008-09-26
> Initializing nautilus-share extension
seahorse nautilus module initialized
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:9783): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
^ ^ ^ ^ ^ 
error code from nautilus...

> [info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
Getting file list
[error] Unable to get drive list
Complete
[info] Switching device /dev/usb/acm/0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Phone is unpluged
[info] Phone pluged as AT
Getting file list
[error] Unable to get drive list
Complete
^ ^ ^ ^ 
Error from moto4lin...

15 pages to read... 8(

---

### Post by lernatix on 2008-09-26
> [device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=4902
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=4901
cfgP2Kvendor=22b8

THANKYOU THANKYOU THANKYOU

I had to create the moto4linrc file in the .qt folder!
(not sure why it didn't exist)

For the record, the .qt directory is a "hidden folder" ;)

---

### Post by AceOnline on 2008-09-28
> **lernatix said:**
> Does this work with 'hardy' 8.04?

I am running Hardy - 8.04 and I Installed the necessary packages as instructed on the first page and I ran moto4lin and it works fine with my Motorola L6.

If it supports your phone then it should work! I just got the software 2 hours back and had it up and running in no time!

all I need to figure out is how do I install my explicit collection of adult games on the phone! :D

---

### Post by Chilongola on 2008-09-28
Still cannot get it to work with my VRi.  It has been working fine with V3 and L6.

---

### Post by davesinger on 2008-09-30
I'm new at this...Usually I get stuff done by trial and error (and reading the entire thread) but I'm stumped on this one.
OS – Hardy Heron, Phone Motorola W385

I was not able to get the correct vendor and product codes to 'stick' usin moto4lin so I edited moto4linrc and retried to connect. It accepted the changes but gave me the following errors:  

Moto4lin opens, following messages:
Messages:
[info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/tty/USB0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect

btw: I got the same errors using device /dev/tty/USB1, /dev/tty/USB0, and /dev/ttyACM0 – I also tried the PK Product ID: 2b41 because [http://moto4lin.sourceforge.net/wiki/W385](http://moto4lin.sourceforge.net/wiki/W385)  shows that as the correct code (even though when I click 'Update List' 2b44 is pulled from the phone (?)

When I select 'Switch to P2K' the messages are the same...
[info] Switching device /dev/tty/USB0 to P2K mode...
[error] Unable to open device
[error] Please check preferences

The vendor codes (at least the AT ones and the device) are as edited; I don't know about the P2K's because it won't switch over.

This looks similar to post 179 and 182 may answer it (but I'm unclear on exactly where to edit the aliases file)  Any ideas?  Help would be greatly appreciated.

---

### Post by utopyr on 2008-09-30
Hit the same thing, checked for svn, sure enough, this page
[http://moto4lin.sourceforge.net/wiki/SVN_Installation]("http://moto4lin.sourceforge.net/wiki/SVN_Installation")
says >  Obtaining moto4lin source from CVS (obsolete!) 
> **TwiceOver said:**
> ```

Installing moto4lin

We are going to get the moto4lin source from a cvs repository. You might get an error from cvs at this stage, ignore and proceed. Asked for password? Just press Enter.
Code:

~$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login

```

At this point I receive a password prompt and hit "enter" and it just drops to the next line blank blinking cursor, does not continue.

EDIT:  After about 5 minutes:

```

dan@dan-laptop:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password: 
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: Connection timed out

```


Any ideas?

---

### Post by fab.fucci on 2008-10-04
hey there...I am hoping someone can help me.  After many failed attempts I found this article (excellent) and my hopes scaled new heights. Unfortunately I cant get rid of this (E_openPhone: Unable to set configuration) message and just cant connect my v3....although I get '[info] Phone pluged as P2K' - downhill from there though

I feel like I'm very close but obviously missing something.  I use 8.04 LTS an being relatively new, I'm maybe not using the right compiliers or libraries maybe?

---

### Post by fab.fucci on 2008-10-04
I still cannot sort my issues so I was hoping someone could post how I remove moto4lin completely, I'd like to try n start it all again.

I apologies for the vaugness (if such a word) I've been trying to sort it for a while and I'm close to over it.  I think I have tried every permutation and combination of varying installation instructions across many threads and websites...this is my last hope, if someone could advise how to blow the current install away please advise...I thought I had better things to do on a friday!!!  Its bloody saturday now!!!!

---

### Post by lingenfr on 2008-11-08
> **fab.fucci said:**
> I still cannot sort my issues so I was hoping someone could post how I remove moto4lin completely

Go to a command prompt and type

sudo apt-get remove moto4lin

and you should be good to go. Cheers.

---

### Post by oarion7 on 2008-11-13
This works great! Using Hardy Heron and Motorola V190.

Thanks!!

---

### Post by davesinger on 2008-12-28
Ok, I finally got the answer to my question.  Trial and error is a wonderful thing if you don't corrupt the files...
I had to edit the moto4lin preference files manually, moto4lin wouldn't accept the changes so it wouldn't connect.  The file to edit is /home/username/.qt/moto4linrc.  It is in the hidden directory ".qt" so you need to view hidden files to get to it.  The file should read as follows (everything between the - - - - - - - - - - - -'s):
- - - - - - - - - - - - 
[device]
cfgACMdevice=/dev/tty/USB0
cfgATproduct=2b44
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=2b41
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=0
cfgGoLastFolder=0
cfgLoadList=0
- - - - - - - - - - - - 

After saving the file (I'd recommend making a backup of the original file first, just in case) go into terminal and use the commands:

sudo modprobe usbserial vendor=0x22b8 product=0x2b44 
sudo moto4lin 

You can find details of the preferences at [http://moto4lin.sourceforge.net/wiki/W385](http://moto4lin.sourceforge.net/wiki/W385) but I think there is a typo in the P2K section (missing a slash)

---

### Post by Chilongola on 2008-12-28
which model phone is this for?
Tks

Got it w385, sorry

---

### Post by davesinger on 2008-12-30
> **davesinger said:**
> Ok, I finally got the answer to my question.  Trial and error is a wonderful thing if you don't corrupt the files...
I had to edit the moto4lin preference files manually, moto4lin wouldn't accept the changes so it wouldn't connect.  The file to edit is /home/username/.qt/moto4linrc.  It is in the hidden directory ".qt" so you need to view hidden files to get to it.  The file should read as follows (everything between the - - - - - - - - - - - -'s):
- - - - - - - - - - - - 
[device]
cfgACMdevice=/dev/tty/USB0
cfgATproduct=2b44
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=2b41
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=0
cfgGoLastFolder=0
cfgLoadList=0
- - - - - - - - - - - - 

After saving the file (I'd recommend making a backup of the original file first, just in case) go into terminal and use the commands:

sudo modprobe usbserial vendor=0x22b8 product=0x2b44 
sudo moto4lin 

You can find details of the preferences at [http://moto4lin.sourceforge.net/wiki/W385](http://moto4lin.sourceforge.net/wiki/W385) but I think there is a typo in the P2K section (missing a slash)
what I don't get is WHY DOESN'T IT WORK NOW!!!  Two days later.  I'm doing exactly the same things, typing the same commands.  And it won't switch to P2K.  It's getting to the point where I may go back to my old LG phone and Bitpim.

---

### Post by iconfixit on 2009-01-21
I was wondering if any on else has a Motorola L6 that they got to work. I have tried everything that I can find and think of but no luck with getting to work. I am brand new to Ubuntu though so thats not saying much. LOL. I would applicate any and all the help I can  get thank you very much.

---

### Post by Chilongola on 2009-01-22
Hi, welcome!  If you do a "look back" in this thread you will see that there has been a few successes with the L-6.  I did, with not much effort.  My V3-i though is a no, no.

---

### Post by iconfixit on 2009-01-22
I have looked at most of the post and over the internet and still can not get my L6 to connect.

---

### Post by DaveAK on 2009-01-22
I set this up by following the moto4lin wiki instructions for my KRZR and I can connect to the phone just fine.  I get a list of files and can download files, but when I go to upload, and select a file from my home directory in the Open File dialog box, it says file not found.  I ran moto4lin as sudo, and even chmod the file to 777, but still no luck.  What gives?

---

### Post by DaveAK on 2009-01-22
Well, after installing p2kmoto it now uploads files.  Don't know why, but at least it works. :)

---

### Post by iconfixit on 2009-01-25
I have tried to run moto4lin as sudo and installed p2kmoto but still nothing.

---

### Post by jbrid on 2009-02-19
I tried my darndest to get moto4lin to work with my w755. No luck. :icon_frown:

```


$ cat .qt/moto4linrc
[device]
cfgACMdevice=/dev/ttyUSB1
cfgATproduct=2b44
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=2b41
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=0
cfgGoLastFolder=0
cfgLoadList=0

$ uname -a
Linux CATALUX 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 22b8:2b44 Motorola PCS 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$ sudo p2ktest
P2k Test
Device list:
1d6b:0002: [Linux 2.6.27-11-generic ehci_hcd] [EHCI Host Controller]
045e:0040: [Microsoft] [Microsoft 3-Button Mouse with IntelliEye(TM)]
1d6b:0001: [Linux 2.6.27-11-generic uhci_hcd] [UHCI Host Controller]
1d6b:0001: [Linux 2.6.27-11-generic uhci_hcd] [UHCI Host Controller]
22b8:2b44: [Motorola Inc.] [Motorola W755]
1d6b:0001: [Linux 2.6.27-11-generic uhci_hcd] [UHCI Host Controller]
No phone found.
$ moto4lin
QSettings::sync: filename is null/empty
Form1
PhoneMan
New mode: 1
P2kProc::doConnect()
Unable to connect: Resource temporarily unavailable

Moto4lin Interface:
[info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyUSB1 to P2K mode...
[debug] nread=-1, errno=11
[error] Unable to connect


```

Incidentally, I could not get my phone to work with KMobileTools either. My suspicion is that Motorola's latest software is blocking access via these tools. I haven't tried the Windows tools yet.

---

### Post by Mark_in_Hollywood on 2009-03-02
I recently got a Moto V195s and moto4lin opens it up just great. Now, if someone can tell me how-to synch the instrucment's phonebook with a copy of the phonebook on my 'puter, I'ld be grateful.

---

### Post by Cuba71 on 2009-03-25
_Motorola RAZR V3_xx
After reading carefully all the posts in this thread, and some of the links, I'm as far as been able to establish the connection between MOTO4LIN and the phone. 
Then I get:
  ```
sendControl Error: [error sending control message: Broken pipe]

```

This is what my moto4linrc file looks like:

```
[INDENT][device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=6402
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=6401
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0
cfgLoadList=0[/INDENT]
```

Any help, anyone?  

Thank you

---

### Post by aidiazmin on 2009-04-19
Hi.

I,m new on using ubuntu.I,m using ubuntu 8.04 LTS. 
I,m wanted to use moto4lin on my old handphone Motorola E398.

I,m use all the "magic" words step by step without having problem on installing the moto4lin.

1.sudo apt-get install cvs
2.sudo apt-get install libqt3-mt-dev
3.sudo apt-get install zlib1g-dev
4.sudo apt-get install libusb-dev

Then Im having problem on the next step. But Im found other way.

5.sudo apt-get install moto4lin
6.Succes on Installing
7.sudo gedit /home/aidiazmin/.qt/moto4linrc
8.I adjust it by the number given on the wiki [http://moto4lin.sourceforge.net/wiki/Category:Models](http://moto4lin.sourceforge.net/wiki/Category:Models)

But then Im having other problems :

[info] Phone is unpluged. Please connect it
Try to connect
[error] No phone found. Check preferences for AT Vendor/Product ID
[error] Unable to connect

For the terminal it stated:
Form1
PhoneMan
doActConnect
doActConnect
P2kProc::doConnect()
(E_drv_connect: no phone)


About for some our in trial and errors I got this solution

I go for my phone settings---->connection----->usb setting
and change it to data/fax connection
I didnt know if all motorola  got this setting but It,s on my E398

so I ran back the program. Its work like charm. tahnks for moto4lin for this program. Its ease me.

Thanks for all the support here. I hope that this will help others that using same as my phone.
Thanks.:D

---

### Post by dBuster on 2009-05-01
Okay so I try to get my v3m to connect and it starts to connect, via usb cable that is, and then after about 30 seconds it disconnects and wait, give it 30 seconds it tries to connect again. 

It repeats this over and over again and I can not get it to connect via usb what so ever.  I am using Jaunty and have tried moto4lin, kmobiletools and neither one work... 

Any ideas??

---

### Post by wizard10000 on 2009-05-03
Spam (searched for bitpim threads) but I got mine working.

I purged the 1.0.6 installation from Jaunty and installed v1.05 from Soureforge and my phone connected first time on /dev/ttyACM0 - wouldn't connect at all with the version of bitpim that comes with Jaunty.

Link to sourceforge archive:

[http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636](http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636)

---

### Post by warpasylum on 2009-05-09
Just wanted to thank serj_alligator. I've been messin' with this all day with no luck. Turns out all I had to do was change usb settings to data/fax connection. good to go now. Just have to run as root.

---

### Post by newpublic on 2009-05-10
some infomation in the web:
[http://www.motoedy.cn/thread-53596-1-1.html](http://www.motoedy.cn/thread-53596-1-1.html)
you can have a try !:KS

---

### Post by whiteguy1104 on 2009-07-31
> **dj_flx said:**
> I've tried everything I could find for my RAZR V3m, even up to and including the SVN compile and install.

I get no further than:

```
[info] Phone pluged as P2K
Try to connect
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
Getting file list
[error] Unable to get drive list
Complete
```

Nothin'.

exactly my problem same phone everything

---

### Post by anotherone33 on 2009-09-29
motorola l6  usb  connect on ubuntu jaunty 9.04 ....
>extremely simply<
install from synaptic (gestore pacchetti)  (or sudo apt-get install ...)
  - kmobiletools
  - moto4lin
  - p2kmoto
remember for moto4lin the [configuration]("http://moto4lin.sourceforge.net/wiki/L6") ([http://moto4lin.sourceforge.net/wiki/L6](http://moto4lin.sourceforge.net/wiki/L6)) ! :

you can look in attached zipped images how is working fine !

you can backup and explore all files in l6 ... with **moto4lin**
you can see and backup all your sms and contacts and more ... with **kmobiletools** 

enjoy ! thanks folks before me... for this to be possible ....

other phones ... see right configuration in wiki sourcerge click [model]("http://moto4lin.sourceforge.net/wiki/Category:Models") ([http://moto4lin.sourceforge.net/wiki/Category:Models](http://moto4lin.sourceforge.net/wiki/Category:Models))

---

### Post by dudiao on 2009-12-09
So I have successfully loaded ringtones from my Linux box onto my w385 with moto4lin, but they don't play - you hear a little burp but that's all. The phone says they are there and are the correct size, the file attributes are correct, and all of the original verizon ringtones work. I have tried all different lengths up to 30 seconds, both mp3 and qcp, all different bit rates, used raw files or audacity modified or iwrt.com supplied. I have followed all the hints about deleting the data bases, restarting, and even removing the battery. Everything gives me a file in a/brew/mod/my_ringers that just burps at me. I'm frustrated because so many people here get through the upload process but once the [ringtone]("http://howardforums.com/showthread.php?p=13265891#") is on the phone  it just works. Any thoughts?

---

### Post by manolomanolo on 2010-01-27
Hi.

I am trying to connect my Motorola Razr V3i to my Ubuntu Karmic Koala.

I am trying to use Moto4lin but I am not able to browse my phone contact and file system.

Can anyone help me please?
Thank you.

---

### Post by manolomanolo on 2010-01-27
Ok, I managed to connect. Is there any way to access the phone book?

---

### Post by Aped on 2010-03-24
> **manolomanolo said:**
> Ok, I managed to connect. Is there any way to access the phone book?

How? I've been trying to get this to work, different combinations of numbers in fields, press this button before that one, for an age. I feel like I'm trying to figure out some ritual from scratch.

---

### Post by Chutler on 2010-06-20
> **Aped said:**
> How? I've been trying to get this to work, different combinations of numbers in fields, press this button before that one, for an age. I feel like I'm trying to figure out some ritual from scratch.

I'm having problems as well.  I'm trying to set up a razr V3 (at least that's what it says on the serial # label) and having no luck.

I'm running moto4lin as sudo...

ACM device: /dev/ttyACM0
AT Vendor: 22b8
AT Product: 4902
2PK Vendor: 22b8
2PK Product: 4901

And no dice...I keep seeing this in the terminal:
> 
craig@craig-desktop:~$ sudo moto4lin
Form1
PhoneMan
New mode: 2
doActConnect
doActConnect
P2kProc::doConnect()
doActConnect
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getPhoneName: E002)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getDriveName: E002)
sendControl Error:[error sending control message: Broken pipe]
(E_fileCount: E001)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getDriveName: E002)
sendControl Error:[error sending control message: Broken pipe]
sendControl Error:[error sending control message: Invalid argument]
(E_getDriveName: E002)
doActConnect

Any thoughts?    :confused:

---

### Post by anotherone33 on 2010-07-29
seen this list [http://moto4lin.sourceforge.net/wiki/to](http://moto4lin.sourceforge.net/wiki/to) reach your razor v3?

also for me again problems with l6 (loose instructions, frustrating) ...

again, with moto4lin  seem needs 
> sudo moto4lin

Preferences:  (this exactly)
ACM device: /dev/ttyACM0
AT Vendor: 22b8
AT Product: 4902
2PK Vendor: 22b8
2PK Product: 4901

Push  >Switch to p2k

then up .... push Connect

Update list ....

ok. running again, again all files. thanks.
l6 exact instruction (that above), here [http://moto4lin.sourceforge.net/wiki/L6](http://moto4lin.sourceforge.net/wiki/L6).

---

### Post by anotherone33 on 2010-07-29
I changed the title for google searchs. Thanks. Bye. 

not c650 but l6

---

### Post by CongoJim on 2010-07-31
> **anotherone33 said:**
> seen this list [http://moto4lin.sourceforge.net/wiki/to](http://moto4lin.sourceforge.net/wiki/to) reach your razor v3?

also for me again problems with l6 (loose instructions, frustrating) ...

again, with moto4lin  seem needs 
> sudo moto4lin

Preferences:  (this exactly)
ACM device: /dev/ttyACM0
AT Vendor: 22b8
AT Product: 4902
2PK Vendor: 22b8
2PK Product: 4901

Push  >Switch to p2k

then up .... push Connect

Update list ....

ok. running again, again all files. thanks.
l6 exact instruction (that above), here [http://moto4lin.sourceforge.net/wiki/L6](http://moto4lin.sourceforge.net/wiki/L6).

Do bear in mind that if during a session you unplug your phone and plug it back in it'll show up as ttyACM1 or 2 or 3 each time you unplug but at reboot back to ttyACM0. You can reboot or change it in the preferences as needed just look on the list, no connection on ttyACM0 but ttyACM1 exists, ding ding ding, there's your solution.

---

### Post by lockjaw$ on 2011-01-07
It also works superb for Motorola V1050 :)

---

### Post by Morpholinux on 2011-08-27
[http://moto4lin.sourceforge.net/wiki](http://moto4lin.sourceforge.net/wiki) the link to the english page does not work!
And I do not know german! 

got problems with motorola ve240

---

