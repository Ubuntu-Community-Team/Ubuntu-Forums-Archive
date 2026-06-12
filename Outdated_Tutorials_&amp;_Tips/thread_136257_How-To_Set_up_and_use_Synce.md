---
title: "How-To: Set up and use Synce"
date: 2006-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Trab on 2006-02-25
_**READ THIS FIRST**_
* Edited on 1/28/09*
I still do not use SynCE, due to the fact that most of my data is stored online, and I use a SD card to transfer files from my computer to my PocketPC. I know this guide is terribly outdated, so I am going to update it. Hopefully it works for those of you who need it.

I still strongly suggest using a SD card to transfer music, books, documents, videos, and even CAB installer files to your pocketPC. even when I had SynCE working, it was notoriously SLOW. 


Update 2/09/09: A German Translation for this guide can be found [here]("http://www.erbenux.com/allgemein/synchronisierung-von-windows-mobile-6.0-und-ubuntu.html") Thanks wucherpfennig! 

[B]
Here is the Guide for using SynCE with Ubuntu 8.10[/B]
(Thanks to TomTheWombat and his post [here]("http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/") almost all information is taken straight from him, with some reorganization and fixes I've noticed around the forums).

Firstly, you need to add the repository to get the packages. 

In a terminal, type:
```

sudo gedit /etc/apt/sources.list

```

add these lines to the bottom of that file
```

deb http://ppa.launchpad.net/synce/ubuntu intrepid main
deb-src http://ppa.launchpad.net/synce/ubuntu intrepid main 

```

Save and close the file. In the termial type:
```

sudo apt-get update
sudo apt-get install synce-hal librra0-tools librapi2-tools 

```
This updates your repository list, then installs the needed packages.

Next, attach your device to the computer. wait a few seconds, then in a terminal type:
```

synce-pls 

```

This will give you a list of files on your device.


**NOTE:** If your device is password protected, you will receive the following error.
```

. WARNING **: synce_info_from_odccm: Failed to get a connection for <device_name>: Not authenticated, you need to call !ProvidePassword with the correct password. pls: Could not find configuration at path '(Default)'

```
TomTheWombat suggests
> 
You will need to install synce-trayicon or synce-kpm.

This will allow you to then input your device password and access your files.


By default gnome is using the Network-Manager. SynCE will interrupt this. Here's how you can fix that:

in a terminal run:
```

/sbin/ifconfig -a | grep 80:00:60:0f:e8:00 | cut -d " " -f 1 

```
which should give you the interface of your device (you will need this below)


then run:
```

sudo gedit /etc/network/interfaces

```

at the bottom of the file add
```

iface <interface of your device> inet dhcp 

``` 

Now Network-Manager will ignore your device (note: firewalls will cause issues with this! either disable them, or configure them to allow the ports). run the following command to reset your network:
```

sudo /etc/init.d/networking restart 

```

Now you will install SynCE, Multisync/OpenSync frontend, and all needed libraries. run (again in a terminal)
```

sudo apt-get install multisync-tools opensync-plugin-evolution opensync-plugin-synce 

```


This next part is copied directly from TomTheWombat's post
(formatting, spacing, and minor fixes mine).

> 
Now we are going to need to setup synce and opensync. The synce-sync-engine starts up automatically if you use the ppa repository. The synce-engine should work without a config file, but you may want to download the config file and edit it (it is no longer called config.xml):

```

mkdir ~/.synce
wget -O ~/.synce/syncengine.conf.xml http://synce.svn.sf.net/svnroot/sync...fig/config.xml
gedit ~/.synce/syncengine.conf.xml

```

You may to disconnect and reconnect your device before the changes are loaded. Now you need to setup a sync profile on the device. Windows Mobile can only handle up to two profiles, so you may need to delete a profile first using synce-delete-partnership. To create a partnership use the following command. (You can tell it to sync "Contacts,Calendar,Tasks,Files". Delete the ones you don't want.)

```

synce-create-partnership "Linux desktop" "Contacts,Calendar,Tasks,Files"

```

Now we need to setup an opensync. You can use the `multisync0.90' program to setup, or you can create the group and add components via commandline:

```

msynctool --addgroup synce-sync
msynctool --addmember synce-sync synce-opensync-plugin
msynctol --addmember synce-sync evo2-sync

```

You can edit the settings with multisync0.90. To sync, press the button in multisync0.90 or do:

```

msynctool --sync synce-sync

```

You can also press the sync button within activesync on the device. By using the custom config, you can change it to popup a terminal on your computer when activesync asks for a sync instead of doing it in the background.


You can use the transport synce:/// in gnome by installing these packages via terminal:
```

sudo apt-get install synce-trayicon synce-gvfs

```
(Thanks Ehol for this tip!)







[b] BELOW IS THE OLD GUIDE! IT ALMOST CERTAIN NO LONGER WORKS, AND IS KEPT SIMPLY FOR ARCHIVE PURPOSES[b]

*edited on 4/7/08*
I have not used, or gotten Synce to work since 6.06 (Dapper Drake). We are just about to see the release of 8.04, its been 2 years. If this doesn't work, its because its outdated! I removed the ANCIENT packages that went along with this how to, it would have been a terrible idea to try them on a new ubuntu (For which it wasn't built).

My personal recommendation is, unless you are DYING to sync things with  evolution, get yourself a CF or SD card, and put files on that to then use on your PocketPC. That what I've been doing for the past 2 years.
If someone would like to rewrite/fix this how-to, please PM me, I will copy and paste your changes (along with credit to the writer) so that the instructions can be easily found here.



it has been requested quite a few times around the forum, i know i wish i could have found one a while ago, so here we go, the wonderful world of Synce...

*NOTE/DISCLAIMER:*
Synce is NOT my project, i do NOT promise it will work, and should your machine explode, i take no responsibility (ok, fine, i take the responsibility to laugh :-P)
be careful with synce, it can erase your entire PocketPC.... i would suggest using the builtin backup tool and saving the backup somewhere safe!
credit to:
Synce site
Storm of UbuntuForums (i used his howto for some of the linking stuff...)


alright onward and upward....

first we need to find out where your pocketpc is in dev...thanks again to storm for this part...

with your device unpluged type
```

ls /dev > /tmp/before

```
then plugin your device and type
```

ls /dev > /tmp/after
diff /tmp/before /tmp/after

```

hopefully it shows 
ttyUSB0 (just remember wat this is!)



then, you need a bunch of packages that are in the repository...
you can use synaptic, but im gonna write for apt-get

```

sudo apt-get install synce-dccm
sudo apt-get install synce-kde
sudo apt-get install synce-serial 

```
(note: this guide is written for Gnome, but uses the synce-kde package... it works fine for me)
you need all the librarys that come with them...
also, this is an optional step if you wanna try and synce your PIM data with evolution (i have yet to be able to do this...partially from lack of trying tho...)
```

sudo apt-get install multisync
sudo apt-get install synce-multisync-plugin

```

there is a howto on wat to do with multisync [here]("http://synce.sourceforge.net/synce/multisync_guide.php")

while installing synce-serial a config window will pop-up, check the options, default usually works fine...put in wat we found out earlier here (ttyUSB0 for me)


next you need to download and install these debs...
```

REMOVED

```

then
```

sudo dpkg -i synce-gnomevfs_0.9.0-2_i386.deb
sudo dpkg -i synce-software-manager_0.9.0-2_i386.deb
sudo dpkg -i synce-trayicon_0.9.0-2_i386.deb

```

we need a link here just to get it all to work...
```

sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2

```

run these commands
```

synce-trayicon
dccm
sudo synce-serial-config ttyUSB0 (REMEMBER TO PUT IN WAT YOU NEED HERE)
sudo synce-serial-start

```

now in your tray icon, u should see a synce icon... right click/explorer

tada! all done!

(you can now remove the debs u got from wget...)


questions, comments, patches, etc etc etc.... lemme know!

-Trab

EDIT: Updated the Howto 04/01/06 just a few fixes to errors and such....

---

### Post by dJnEvS on 2006-03-06
i think this is able to help me...
but i have got 1 problem:
```
root@ubuntu:~ # apt-get install synce-dccm
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
E: Kon pakket synce-dccm niet vinden
```
translation:
```
root@ubuntu:~ # apt-get install synce-dccm
Packet being reeds... Klaar (or something)
Tree of neccecery thing is builded... Klaar
E: Cant find packet synce-dccm
```

---

### Post by grgill on 2006-03-06
does this work with dapper? at one point i had it working with brezzy but have had no luck after upgrade. thanks

---

### Post by Trab on 2006-03-07
i dunno about dapper yet, i would assume so if all the librarys and other files are in the repo...

i really have no clue dJnEvS, could u try retranslating that for me? it doesnt make any sense in english...the one posability i can think of is you dont have the universe repositories enabled, which means the synce files cant be found...

let me know!

---

### Post by dJnEvS on 2006-03-07
what i still remember of the last time i used ubuntu, i need to add the list file of sources where u can download stuff from with apt-get... there is some file..that contains URL's... not sure what that file is, maybe u know it now... if so, could you post your list here?

---

### Post by Trab on 2006-03-26
sorry, took too long to get back to you!
its called the Repository
[code]
sudo cp /etc/apt/sources.list /etc/apt/sources.list2
sudo gedit /etc/apt/sources.list
[code]

uncomment the universe lines...
also, it might have some sort of dependancy error with that other program...

if anyone can test this on Dapper, i would aprecate it...
it SHOULD work (unless there is a dependancy error for some lib that is forced to be updated in dapper, that synce requires... there are ways around that though...)
latz
-Trab

---

### Post by slazh on 2006-03-29
Thanks! This works like a charm on with my T-Mobile SDA :D

Verry nice howto!

---

### Post by scav on 2006-04-05
i get the following error when trying synce-serial-start

everything else goes great, untill the last step


Apr  5 12:49:09 RINGJOL synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr  5 12:49:09 RINGJOL pppd[5731]: pppd 2.4.4b1 started by root, uid 0
Apr  5 12:49:09 RINGJOL pppd[5731]: Exit.

---

### Post by Trab on 2006-04-05
were u sure to use the commands with SUDO (where i told you too?)
do you have anytning else that uses PPPd (are u on dial-up?)
thanks
-TJ

---

### Post by trapangle on 2006-04-08
Tryed this with a Qtek 9090 (HTC Blue Angel), WM2003, and got some problems.

```
alain@Earth:~$ sudo synce-serial-config ttyUSB0

ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help.
```

```

alain@Earth:~$ sudo synce-serial-start
/usr/sbin/pppd: In file /etc/ppp/peers/synce-device: unrecognized option '/dev/ttyUSB0'

synce-serial-start was unable to start the PPP daemon!
```

Solution to both problems : removing the PDA and putting it back on its craddle.

But then :

```
alain@Earth:~$ sudo synce-serial-start

synce-serial-start is now waiting for your device to connect
```

I see the PDA tries to connect, but nothing happens and no icon appears nowhere. 

Do you know any command so I could check if it's connected ?

---

### Post by Trab on 2006-04-08
hmmm
wat this issue is is the ttyUSB0 is where the computer trys to find your pocketpc (at the 1st usb port). this is what the first part of the howto is about, you need to make sure u have the right port.....
if it was able to detect it the second time (When you removed and reattached it to the cradle) then its a different error, actually quite common...)
you have to make sure u ran all those commands before u try to get it up...(did u run synce-trayicon??)
then, remove and soft restart your pocketpc (make sure u know wat ur doing, otherwise u'll erase everything...)
let it boot up, then after running all those commands, put it in your cradle...

understand, synce-trayicon only needs to be running once,
dccm needs to be running once (tho if something goes wrong, a good idea is to killall dccm and restart it)
sudo synce-serial-start needs to be run EVERY TIME you want the pocketpc to connect (After its been removed)
cheers
good luck
lemme know how it goes
-Trab

---

### Post by amgadpasha on 2006-04-09
ok, its not working for me.. :(

i use ppoa adsl to access internet with my speed touch 330 usb modem, i use this script [http://steve-parker.org/speedtouchconf/](http://steve-parker.org/speedtouchconf/)
to configure the driver and set the connection..
now when i tried to set up my qtek 9090 it gives me this error when i run synce-serial-start
"
amgad@home:~$ sudo synce-serial-start

synce-serial-start encountered a problem with your /etc/ppp/options file:

The 'usepeerdns' option is not compatible with SynCE.  Please edit
/etc/ppp/options and remove this option before running this script again.
"

these are the contents of my /etc/ppp/options file: 
"
#------------------ /etc/ppp/options Beginning -------------
noauth
usepeerdns
lock
noipdefault
#------------------ /etc/ppp/options End ------------------
"

so what should i do now??

---

### Post by Trab on 2006-04-09
remove usepeerdns from your ppp/options file...

i dunno wat this will do to ur DSL modem, i think it should still work fine...
if not, then u can always put it back in...
cheers
-Trab

---

### Post by trapangle on 2006-04-10
[QUOTE=Trab]
understand, synce-trayicon only needs to be running once,
dccm needs to be running once (tho if something goes wrong, a good idea is to killall dccm and restart it)
sudo synce-serial-start needs to be run EVERY TIME you want the pocketpc to connect (After its been removed)
cheers
good luck
lemme know how it goes
-Trab[/QUOTE]

Thanks, it works now. No idea what happened at the first time, but the icon didn't appear when I typed synce-trayicon. Now it does. Meanwhile I just rebooted my ubuntu, nothing else. 
Thanks for the howto, now let's see the connection with evolution...

This for the ones who'll be searching this later : Connection between QTek 9090 (HTC blueangel) and Ubuntu works.

---

### Post by Trab on 2006-04-10
glad to hear it.
sometimes all it takes is a restart!
the connection to evolution is via a plugin called multisync, google for it. there are how-tos, i just never really got into it... it didnt work for me, and it wasnt something i really cared about.
cheers
-Trab

---

### Post by JNik on 2006-04-24
Although the icon on my Acer n50 shows established connection, the synce-tray says (No Device Connected) and after a while I get a Communications Error on my PDA.

I'm on Dapper by the way. Any ideas?

Edit: I just tried synce-pstatus and I get the "Unable to initialize RAPI: An unspecified failure has occurred" message.

---

### Post by cypresstwist on 2006-04-24
Exactly the same problem on my Dapper Beta. Yakumo Delta 400 shows up as a "Mobile Device" in "Places", the tray icon is started, but shows "No Device Connected". Same with raki. But I got this far and that is SOMETHING :)

---

### Post by Trab on 2006-04-24
im sorry i havent worked on it for dapper at all...
sorry :-/ this is beyond me... try checking the synce forum, and/or google...
cheers
-Trab

---

### Post by kai_schroeder on 2006-04-28
synce works on my dapper system. i guess the important step to make it work was to follow the advise in this bugreport [https://launchpad.net/distros/ubuntu/+source/synce-kde/+bug/37658](https://launchpad.net/distros/ubuntu/+source/synce-kde/+bug/37658)

Quote from it:

I've also found in Internet this file for UDEV that enables the serial connection when the PDA is connected to my PC. It must be called '60-ipaq.rules' and must be located at '/etc/udev/rules.d'. The only thing I can say is that it runs fine for me :)

# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
LABEL="synce_rules_end"

---

### Post by Trab on 2006-05-18
just because it says no device connected in the Synce-Tray icon, doesnt mean its not. even on breezy, ive had this issue, it is still connected.
cheers
-Trab

---

### Post by ghozali on 2006-05-22
[QUOTE=Trab]it has been requested quite a few times around the forum, i know i wish i could have found one a while ago, so here we go, the wonderful world of Synce...

*NOTE/DISCLAIMER:*
Synce is NOT my project, i do NOT promise it will work, and should your machine explode, i take no responsibility (ok, fine, i take the responsibility to laugh :-P)
be careful with synce, it can erase your entire PocketPC.... i would suggest using the builtin backup tool and saving the backup somewhere safe!
credit to:
Synce site
Storm of UbuntuForums (i used his howto for some of the linking stuff...)


alright onward and upward....

first we need to find out where your pocketpc is in dev...thanks again to storm for this part...

with your device unpluged type
```

ls /dev > /tmp/before

```
then plugin your device and type
```

ls /dev > /tmp/after
diff /tmp/before /tmp/after

```

hopefully it shows 
ttyUSB0 (just remember wat this is!)



then, you need a bunch of packages that are in the repository...
you can use synaptic, but im gonna write for apt-get

```

sudo apt-get install synce-dccm
sudo apt-get install synce-kde
sudo apt-get install synce-serial 

```
(note: this guide is written for Gnome, but uses the synce-kde package... it works fine for me)
you need all the librarys that come with them...
also, this is an optional step if you wanna try and synce your PIM data with evolution (i have yet to be able to do this...partially from lack of trying tho...)
```

sudo apt-get install multisync
sudo apt-get install synce-multisync-plugin

```

there is a howto on wat to do with multisync [here]("http://synce.sourceforge.net/synce/multisync_guide.php")

while installing synce-serial a config window will pop-up, check the options, default usually works fine...put in wat we found out earlier here (ttyUSB0 for me)


next you need to download and install these debs...
```

wget http://kuci.org/~teddy/ubuntu/synce-gnomevfs_0.9.0-2_i386.deb
wget http://kuci.org/~teddy/ubuntu/synce-software-manager_0.9.0-2_i386.deb
wget http://kuci.org/~teddy/ubuntu/synce-trayicon_0.9.0-2_i386.deb

```

then
```

sudo dpkg -i synce-gnomevfs_0.9.0-2_i386.deb
sudo dpkg -i synce-software-manager_0.9.0-2_i386.deb
sudo dpkg -i synce-trayicon_0.9.0-2_i386.deb

```

we need a link here just to get it all to work...
```

sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2

```

run these commands
[code]
synce-trayicon

I got this error when i got up to this 

synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory

I have flight 7 dapper ubuntu, and a HP HX4700 if anyone can help I would appreciate it ...

---

### Post by CnorthMSU on 2006-05-23
[QUOTE=ghozali][QUOTE=Trab]

run these commands
```

synce-trayicon

I got this error when i got up to this 

synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory

I have flight 7 dapper ubuntu, and a HP HX4700 if anyone can help I would appreciate it ...[/QUOTE]

I was having the same problem until just now. I just got this to work with Dapper Flight7 a few minutes ago and I'm sooo glad (I was on Breezy until today and upgraded to try to get my PocketPC working). Try a different symlink:
[CODE]sudo ln -s /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2
```

---

### Post by Whoopie on 2006-05-28
Although these packages are only for DAPPER, I attach them.

1. synce-gnomevfs
also shows the icon in the nautilus pathbar. Thanks to nsh at IRC #gnome-love for helping me.
You have to execute "sudo gtk-update-icon-cache /usr/share/icons/gnome/ -f" after installing this package.

2. synce-trayicon
supports icon transparency

3. synce-software-manager

4. syncefs
for mounting the WinCE filesystem (see [http://article.gmane.org/gmane.comp.handhelds.ipaq.synce.devel/293](http://article.gmane.org/gmane.comp.handhelds.ipaq.synce.devel/293))

---

### Post by peter rus on 2006-05-29
yay, i dont know why, but i have tried many hours desperately connecting that stupid em-500, but i followed this tutorial and it just worked, tnx dude :D

---

### Post by peter rus on 2006-05-29
hmm not really working though, if i use passwords it doesnt work. i enter the password using that tray icon property thing and i guess it stores it (dont know where though so i cant check it...) if i turn off the passwords it all works fine.

anyone can help me with this?

---

### Post by peter rus on 2006-06-04
solved it, i used RAKI and entered the password, that was it

---

### Post by xe1ufo on 2006-06-15
I am running Dapper.

I downloaded and installed everything according to your VERY excellent and detailed instructions.  THANKS A MILLION!  

I place my Jornada 568 (PocketPC 2002) on the dock and the two machines connect to each other. (PDA makes the toodle-doo "synked" sound.)  But I cannot get the tray Icon to load:

drsteve@drsteve-laptop:~$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory

I do have libgtop2-7 (2.14.1-Oubuntu1) installed.

HELP!!

Thanks in advance!

Dr. Steve, central old Mexico

---

### Post by dave.goodfellow on 2006-06-16
Try this in Dapper:

sudo ln -si /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2

Say y to replace

---

### Post by tom1502 on 2006-06-20
Hi,
can anyone assist me with creating a udev rule which automatically starts multisync when PDA is being connected?
And  it should run synce-serial-abort when i disconnect PDA, and if possible quit multisync. Can anyone help me with this?

ive tried the following:
```

# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_add_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start && su thomas -c DISPLAY=:0.0 /usr/bin/multisync"
LABEL="synce_add_end"
# all above is current
# -------------------------
# this is my idea, but not workin
BUS!="usb", ACTION!="remove", KERNEL!="ttyUSB*", GOTO="synce_remove_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-abort" # DUNNO HOW TO QUIT MULTISYNC
LABEL="synce_remove_end" 

```
But this does not work. synce-serial-start is starts if i just leave in the rule till the "-----".

But i'd love to get this workin automatically!

tom

---

### Post by binjured on 2006-06-21
Okay, maybe I am a complete idiot, but I can't even get past the first step here.  It says to use diff to find out where the device is, except mine shows nothing.  In fact I have no ttyUSB* entries in /dev/ at all!  I sure as hell know I have USB devices on the machine (my external hdd works just fine) and when using "cat /proc/bus/usb/devices" I get:
```

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#= 14 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS=16 #Cfgs=  1
P:  Vendor=413c ProdID=4011 Rev= 0.00
S:  Manufacturer=Dell Inc.
S:  Product=Dell Axim X51v
S:  SerialNumber=*********************
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```
So... it's there then right?  What's going on here?

---

### Post by Dromio on 2006-06-21
[quote=binjured]Okay, maybe I am a complete idiot, but I can't even get past the first step here.  It says to use diff to find out where the device is, except mine shows nothing.  In fact I have no ttyUSB* entries in /dev/ at all!  I sure as hell know I have USB devices on the machine (my external hdd works just fine) and when using "cat /proc/bus/usb/devices" I get:
*snip* So... it's there then right?  What's going on here?[/quote]

I'm having the same problem.  My pocketpc shows in the devices list, but I have no ttyUSB devs.

---

### Post by bohboh on 2006-06-22
I cant connect. Followed the guide, no errors. Connected the device and nothing.

Erm, not sure where to even begin.

What can i do to try and narrow it down?

---

### Post by Amon_Re on 2006-07-11
Followed this thing, and everything went fine untill i tried to actually connect.

Seems on my system that synce-serial-start dies before the connection is actually established, some timing problem i guess, the udev rule mentioned earlier however, seems to work arround that small problem

PS: My pocketpc seems unable to connect to the internet while connected to the PC.
I'm suspecting this to be a routing/dns/ppp issue, if anyone has some pointers, they're welcome ;)

---

### Post by mogulike on 2006-07-19
I tried to follow you tutorial and fell at the first hurdle. I've got a 02 XDA Mini (HTC Wizard), which is running MS Win PPC 5. 

When trying to find the pocket PC as a /dev/ I drew a blank. I know I must have missed something basic. I carefuly followed the instructions to get the ls of /dev before and after I switch my phone on. 

I did a dmesg to check the system picked up on me plugging it into the usb port. I found this line near the bottom, and it's the only one relating to the new usb device.

usb 2-2: new full speed USB device using uhci_hcd and address 2

I haven't installed anything for the phone on ubuntu upto this point, any help is welcome. Cheers

---

### Post by teejcee on 2006-08-21
> **mogulike said:**
> I tried to follow you tutorial and fell at the first hurdle. I've got a 02 XDA Mini (HTC Wizard), which is running MS Win PPC 5. 

I haven't installed anything for the phone on ubuntu upto this point, any help is welcome. Cheers


This may be your problem....

News

2006-01-04 If you are interested in Windows Mobile 5 support in SynCE, please join the SynCE-WindowsMobile5 mailing list.

2005-11-24 Important Windows Mobile 5 devices do not work with SynCE! This is currently being investigated but no SynCE developer has access such a device, so don't expect them to be supported very soon.


This information ( and more ) can be found here....

[http://synce.sourceforge.net/synce/](http://synce.sourceforge.net/synce/)

Hmmmm..I've just re-read your orignal post.  That device is a Pocket PC if I'm not mistaken, so my info re Win Mobile 5 is probably not applicable..:-#

---

### Post by gansinho on 2006-09-27
I have a dell axim x51 and I get nothing in the very begining =/// 
> with your device unpluged type
Code:

ls /dev > /tmp/before

then plugin your device and type
Code:

ls /dev > /tmp/after diff /tmp/before /tmp/after

hopefully it shows
ttyUSB0 (just remember wat this is!)

it doesn't shows anything =/// please someone help me, I'm trying really hard to make synce works...

---

### Post by Trab on 2006-09-28
alas, thanks to all those who helped, im sorry i let this thread die. its outdated a bit, as edgy is on its way, and WM5 is here.
i too have a dell axim x51 and dont believe it will work.
i suggest getting a sd or CF card and card reader and transfering stuff that way, its its a million times easier.
i will however be creating a new/updated howto (with updated packages hopefully) soon.
until then, cheers!

---

### Post by gansinho on 2006-09-28
Hey trab thanks for worring about me (sorry bad eglish)! I need to sync the calendar and tasks, so I couldn't figure out how transfering stuff via CF and SD will help me this way... if there's any share with me.
thanks!

---

### Post by madtweety on 2006-09-29
Hi guys thank 4 info :D 

well i need help on this 
now in your tray icon, u should see a synce icon... right click/explorer

right i done all what you said all cods, but i dont have anything in mt trat icon ??
this is what i done 

markie@markie-ubuntu:~$ synce-trayicon
markie@markie-ubuntu:~$ dccm
markie@markie-ubuntu:~$ sudo synce-serial-config ttyUSB0
Password:
You can now run synce-serial-start to start a serial connection.
markie@markie-ubuntu:~$ sudo synce-serial-start
synce-serial-start is now waiting for your device to connect
markie@markie-ubuntu:~$

can you help please im using a PDA

markie

---

### Post by brucevangeorge on 2006-10-10
Yeah. I'm getting a problem with the tray icon too:

```


synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory


```

followed the guide to the letter.

I'm running kde if it makes a difference.

---

### Post by wiresquire on 2006-10-10
> **brucevangeorge said:**
> Yeah. I'm getting a problem with the tray icon too:

```


synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory


```

followed the guide to the letter.

I'm running kde if it makes a difference.


I think you missed:
> 
we need a link here just to get it all to work...
Code:
```

sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2

```

/usr/lib/libgtop-2.0.so.5 should be /usr/lib/libgtop-2.0.so.7 on Dapper (6.06)

---

### Post by brucevangeorge on 2006-10-10
I don't think that's it:

```


ln: creating symbolic link `/usr/lib/libgtop-2.0.so.2' to `/usr/lib/libgtop-2.0.so.7': File exists


```

---

### Post by kseise on 2006-10-10
I am trying to get the Avantgo portion to work.  I am able to sync with Evolution OK.  In reading the how-to stuff, I know i have to enable ipforwarding ont he desktop.  I can't figure out how to do that.  Can anyone help me please?

---

### Post by kseise on 2006-10-31
I have now installed Edgy (6.10) and found that Firestarter does not open the correct ports for some reason.  When Firestarter is running, I get the RAPI errors that everyone seems to complain about.  By clicking "Stop Firewall", the ports get opened up and all syncing is possible.  If it helps anybody, try turning off the firewall to get Synce to connect.

I know it is user error and would love to see a how-to.

---

### Post by Robert.Zapata on 2006-12-08
Thanks for the great How-to..!!

It worked for me with just the following diference:

> 
sudo ln -si /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2

Say y to replace


I'm using **6.10** and a WindowsMobile phone *(Motorola MPx220)*

I create the following script to avoid manually typing all the commands after starting the machine, but is not working. :( 

#!/bin/bash
#Activate SynCE tray
synce-trayicon
dccm
sudo synce-serial-config ttyUSB0
sudo synce-serial-start

I keep getting this:
> 
rob@Thinkpad:~$ mpx220
bash: /usr/bin/mpx220: Permission denied


Then I try using "sudo" but no luck...

> 
rob@Thinkpad:~$ sudo mpx220
Password:
sudo: mpx220: command not found


Any ideas...??

Thank you very much.

---

### Post by DaCrayZeeOne on 2006-12-14
> **kseise said:**
> I have now installed Edgy (6.10) and found that Firestarter does not open the correct ports for some reason.  When Firestarter is running, I get the RAPI errors that everyone seems to complain about.  By clicking "Stop Firewall", the ports get opened up and all syncing is possible.  If it helps anybody, try turning off the firewall to get Synce to connect.

I know it is user error and would love to see a how-to.

Solution: add the following text to /etc/firestarter/user-post :
```
iptables -A INPUT -j ACCEPT -i ppp0
iptables -A FORWARD  -j ACCEPT -i ppp0 -o eth0
iptables -A FORWARD  -j ACCEPT -o ppp0 -i eth0
iptables -A OUTPUT -j ACCEPT -o ppp0

```

Only do this if you use ppp0 to talk to iPaq. You may need to use ppp1 or something else if you use a different interface.

This allows the iPaq to connect to/from the computer without having to disable firestarter firewall.

To allow the iPaq to connect to the net, I think you need to add this line also:

```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```

It's something like that, anyway. Unfortunately, this last command is unchecked by me, as I use a custom kernel and have not installed the correct modules for ipt_MASQUERADE yet.

Regards,

BenG.

---

### Post by DaCrayZeeOne on 2006-12-14
> **Robert.Zapata said:**
> Thanks for the great How-to..!!

It worked for me with just the following diference:



I'm using **6.10** and a WindowsMobile phone *(Motorola MPx220)*

I create the following script to avoid manually typing all the commands after starting the machine, but is not working. :( 

#!/bin/bash
#Activate SynCE tray
synce-trayicon
dccm
sudo synce-serial-config ttyUSB0
sudo synce-serial-start

I keep getting this:


Then I try using "sudo" but no luck...



Any ideas...??

Thank you very much.

Your script is non-executable. You need to run this:

```
chmod u+x mpx220
```

Then you call it like this:

```
./mpx220
or
/home/me/mpx220
```

Alternatively, call it like this:

```
sh mpx220
```

Good luck :)

BenG

PS: I think you do not need to have this line in your script:
```
sudo synce-serial-config ttyUSB0
```

Running it once sets up a configuration file. After this you only need to run synce-serial-start, though you need to do this as root. However, if you don't want to do this as root, and you trust all people who have access to your computer, you can create the file /etc/udev/rules.d/60-ipaq.rules with contents:
```
# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
LABEL="synce_rules_end"

```

(as root). Now run

```
sudo /etc/init.d/udev reload
```

And next time you plug your PocketPC in, **_it should automagically dial up the computer_**. ENSURE you have dccm running if you choose to do this.

Regards,

BenG.

---

### Post by kseise on 2007-02-03
> **DaCrayZeeOne said:**
> Solution: add the following text to /etc/firestarter/user-post :
```
iptables -A INPUT -j ACCEPT -i ppp0
iptables -A FORWARD  -j ACCEPT -i ppp0 -o eth0
iptables -A FORWARD  -j ACCEPT -o ppp0 -i eth0
iptables -A OUTPUT -j ACCEPT -o ppp0

```

Only do this if you use ppp0 to talk to iPaq. You may need to use ppp1 or something else if you use a different interface.

This allows the iPaq to connect to/from the computer without having to disable firestarter firewall.


That worked fine, but I had to enter it in /etc/firestarter/user-pre.  I got that tip from somewhere else.  When I put the two ideas together, it works great.



> **DaCrayZeeOne said:**
> 
To allow the iPaq to connect to the net, I think you need to add this line also:

```
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```

It's something like that, anyway. Unfortunately, this last command is unchecked by me, as I use a custom kernel and have not installed the correct modules for ipt_MASQUERADE yet.


It didnt' work.  I am using a vanilla Edgy kernel.  I have not given up yet.  Thank you for your help with this.

You Rock :guitar:

---

### Post by ryan76 on 2007-02-06
I'm getting this error too:

```
ryan@ubuntu:~$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
ryan@ubuntu:~$ 
```

I have tried everything suggested in this thread about setting up the links (although id on't udnerstand it). My iPAQ shows it's connected but I can't get to it without the tray icon.

---

### Post by LennartS on 2007-03-13
I had that problem too.
You probably have another version of libgtop. Go to /usr/lib/ and have a look. The one marked "shared library" is the relevant one. In my case it was "libgtop-2.0.so.7.0.0" which seems to come with ubuntu 6.10.

Delete the wrong link you created with

"sudo rm /usr/lib/libgtop-2.0.so.2".

Then

"sudo ln -s /usr/lib/<your lib version> /usr/lib/libgtop-2.0.so.2".

Afterwards continue like Trab taught us (thank you trab :) ). There it is, good luck.

---

### Post by GavinSpearhead on 2007-04-26
I try to connect my HP Travel companion to Feisty Fawn, but with little to no success. I've tried the sequence described above, but after "sudo synce-serial-start" I see that it connects on my PDA and then quickly disconnect. 

/var/log/messages shows this:

Apr 26 17:38:28 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Apr 26 17:38:28 localhost pppd[6924]: pppd 2.4.4 started by root, uid 0
Apr 26 17:38:28 localhost pppd[6924]: Serial connection established.
Apr 26 17:38:28 localhost pppd[6924]: Using interface ppp0
Apr 26 17:38:28 localhost pppd[6924]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 26 17:38:29 localhost pppd[6924]: local  IP address 192.168.131.102
Apr 26 17:38:29 localhost pppd[6924]: remote IP address 192.168.131.201
Apr 26 17:38:32 localhost pppd[6924]: LCP terminated by peer
Apr 26 17:38:32 localhost pppd[6924]: Connect time 0.1 minutes.
Apr 26 17:38:32 localhost pppd[6924]: Sent 400 bytes, received 1370 bytes.
Apr 26 17:38:35 localhost pppd[6924]: Connection terminated.
Apr 26 17:38:35 localhost pppd[6924]: Modem hangup
Apr 26 17:38:35 localhost pppd[6924]: Exit.

And ideas on how to resolve this?

---

### Post by Steve H on 2007-05-17
This thread worked a treat, tray icon is working well and now I can swap files. 

Brilliant, thanks.

:)

---

### Post by codeslicer on 2007-06-05
Thanks for the guide! Note, if you get and error saying shared libraries weren't found or something, you need to install a -dev package. So if let's say it says libgtop2.0 (just an example) is missing, you will need to install libgtop2.0-dev. HTH! Cheers!

---

### Post by gamecat on 2007-06-13
I hope someone can help me with this as I got a confusing answer to the difference test

```
ben@gamecat:~$ diff /tmp/before /tmp/after
664a665,668
> usbdev2.3_ep00
> usbdev2.3_ep03
> usbdev2.3_ep81
> usbdev2.3_ep82

```

any ideas which one of these I should use? I've tried running it with each but nothing happens.

```
ERROR:

synce-serial-config was unable to find a character device named "usbdev2.3_ep82"

Run "synce-serial-config --help" to get help.

```

---

### Post by plinydogg on 2007-06-14
Does anyone know if the packages names have changed? I typed:

sudo apt-get install synce-dccm

but got an error: package not found. Nor could I find any synce applications in the Synaptic Package Manager. 

Any help would be much appreciated. Thank you!

---

### Post by mnisecky on 2007-07-01
> **DaCrayZeeOne said:**
> Your script is non-executable. You need to run this:

```
chmod u+x mpx220
```

Then you call it like this:

```
./mpx220
or
/home/me/mpx220
```

Alternatively, call it like this:

```
sh mpx220
```

Good luck :)

BenG

PS: I think you do not need to have this line in your script:
```
sudo synce-serial-config ttyUSB0
```

Running it once sets up a configuration file. After this you only need to run synce-serial-start, though you need to do this as root. However, if you don't want to do this as root, and you trust all people who have access to your computer, you can create the file /etc/udev/rules.d/60-ipaq.rules with contents:
```
# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
LABEL="synce_rules_end"

```

(as root). Now run

```
sudo /etc/init.d/udev reload
```

And next time you plug your PocketPC in, **_it should automagically dial up the computer_**. ENSURE you have dccm running if you choose to do this.

Regards,

BenG.


I am using Motorola MPX220

Many thanks for this !!! But I have problem concerning synchronization with Evolution. Connection is OK, but synchonization doesn t working.

Can you help me ?

---

### Post by mnisecky on 2007-07-01
> **Robert.Zapata said:**
> Thanks for the great How-to..!!

It worked for me with just the following diference:



I'm using **6.10** and a WindowsMobile phone *(Motorola MPx220)*

I create the following script to avoid manually typing all the commands after starting the machine, but is not working. :( 

#!/bin/bash
#Activate SynCE tray
synce-trayicon
dccm
sudo synce-serial-config ttyUSB0
sudo synce-serial-start

I keep getting this:


Then I try using "sudo" but no luck...



Any ideas...??

Thank you very much.



I am using also Motorola MPX220

But I have problem concerning synchronization with Evolution. Connection is OK, but synchonization doesn t working. Did you solve this problem ?   And solution ....?

Can you help me ?

---

### Post by Trab on 2007-07-01
hey guys, I havent bothered to connect my new Dell Axim x51 to Ubuntu Feisty, or at all. within the next 2 weeks, I hope to reanalyze the new synce for windows mobile 5.0 and rewrite this guide, and also build new packages. any help/information would be apprecated, please PM me rather than posting ot this thread.

---

### Post by GnarusLeo on 2007-07-08
I get the same as Gamecat. 

```
gnaleo@tryodin:~$ diff /tmp/before /tmp/after
661a662,665gnaleo@tryodin:~$ diff /tmp/before /tmp/after
661a662,665
> usbdev3.3_ep00
> usbdev3.3_ep03
> usbdev3.3_ep81
> usbdev3.3_ep82
gnaleo@tryodin:~$   
```

Did anyone solve this?

I am trying to connect the brand new HTC S710 with Windows Mobile 6. Strangely, it does not output a ttyUSB :(

Help will be appriciated

---

### Post by kjaggu on 2007-07-23
> **GnarusLeo said:**
> I get the same as Gamecat. 

```
gnaleo@tryodin:~$ diff /tmp/before /tmp/after
661a662,665gnaleo@tryodin:~$ diff /tmp/before /tmp/after
661a662,665
> usbdev3.3_ep00
> usbdev3.3_ep03
> usbdev3.3_ep81
> usbdev3.3_ep82
gnaleo@tryodin:~$   
```

Did anyone solve this?

I am trying to connect the brand new HTC S710 with Windows Mobile 6. Strangely, it does not output a ttyUSB :(

Help will be appriciated


Hi guys,

I too am getting a similar error. I use an i-mate JAMA. Please help

---

### Post by ~~Tito~~ on 2007-07-30
Same here with my blackjack.

---

### Post by BoardDWorld on 2007-08-20
I'm getting the same problem as everyone else as well on my dopod C500, which is the same as GnarusLeo's HTC S710. I actually went to the extent of unplugging all USB devices and restarting the PC. The output was still much the same. 

> matthew@matthew-laptop:~$ ls /dev > /tmp/before
matthew@matthew-laptop:~$ ls /dev > /tmp/after
matthew@matthew-laptop:~$ diff /tmp/before /tmp/after
679a680,683
> usbdev5.2_ep00
> usbdev5.2_ep03
> usbdev5.2_ep81
> usbdev5.2_ep82
matthew@matthew-laptop:~$ 

Please note it was actually this that has put me back to using Vista and Office 2007 for work, I would much prefer to have this resolved and continue using Ubuntu, I miss it:( Thanks in advance!

---

### Post by parvinder on 2007-09-01
First of all thanks for the article. It was really very easy to install synce for a person like me who has hardly worked on linux. I installed Ubuntu today only and it was amazing.

But, now I am in a situation as with some other users, after I connect my AT&T 8525 and issue the command 
 -->"sudo sync-serial-start" 
--->I get a message that it is waiting for the device to connect. 
--->device shows user authenticated but then disconnects within less than a min.
---> here is the log...
Sep  1 20:49:55 sonyviao kernel: [  848.640000] usb 1-2: USB disconnect, address 2
Sep  1 20:49:55 sonyviao kernel: [  848.640000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Sep  1 20:49:55 sonyviao kernel: [  848.640000] ipaq 1-2:1.0: device disconnected
Sep  1 20:50:03 sonyviao kernel: [  856.704000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Sep  1 20:50:04 sonyviao kernel: [  856.952000] usb 1-2: configuration #1 chosen from 1 choice
Sep  1 20:50:04 sonyviao kernel: [  856.956000] ipaq 1-2:1.0: PocketPC PDA converter detected
Sep  1 20:50:04 sonyviao kernel: [  856.960000] usb 1-2: PocketPC PDA converter now attached to ttyUSB0
Sep  1 20:50:13 sonyviao synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Sep  1 20:50:13 sonyviao pppd[6404]: pppd 2.4.4 started by root, uid 0
Sep  1 20:50:13 sonyviao pppd[6404]: Serial connection established.
Sep  1 20:50:13 sonyviao pppd[6404]: Using interface ppp0
Sep  1 20:50:13 sonyviao pppd[6404]: Connect: ppp0 <--> /dev/ttyUSB0
Sep  1 20:50:16 sonyviao pppd[6404]: local  IP address 192.168.131.102
Sep  1 20:50:16 sonyviao pppd[6404]: remote IP address 192.168.131.201
Sep  1 20:50:22 sonyviao pppd[6404]: LCP terminated by peer
Sep  1 20:50:22 sonyviao pppd[6404]: Connect time 0.1 minutes.
Sep  1 20:50:22 sonyviao pppd[6404]: Sent 404 bytes, received 1406 bytes.
Sep  1 20:50:25 sonyviao pppd[6404]: Connection terminated.
Sep  1 20:50:25 sonyviao pppd[6404]: Modem hangup
Sep  1 20:50:25 sonyviao pppd[6404]: Exit.
Sep  1 20:50:26 sonyviao kernel: [  879.148000] usb 1-2: USB disconnect, address 3
Sep  1 20:50:26 sonyviao kernel: [  879.148000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Sep  1 20:50:26 sonyviao kernel: [  879.148000] ipaq 1-2:1.0: device disconnected
Sep  1 20:50:29 sonyviao kernel: [  882.476000] usb 1-2: new full speed USB device using uhci_hcd and address 4
Sep  1 20:50:29 sonyviao kernel: [  882.724000] usb 1-2: configuration #1 chosen from 1 choice
Sep  1 20:50:30 sonyviao kernel: [  882.728000] ipaq 1-2:1.0: PocketPC PDA converter detected
Sep  1 20:50:30 sonyviao kernel: [  882.732000] usb 1-2: PocketPC PDA converter now attached to ttyUSB0


Any help how to proceed further????

Thank you.

---

### Post by lensteruk on 2007-10-07
I have got as far as getting synce-serial-start to iniitiate and as seen below subsequent restarts shows that all is ok behind the scenes. but mulitsync just sits there and does no more. cant get anything into evolution at all. It this a probllem with ubuntu amd64 environ or have i missed somethin >??

You can now run synce-serial-start to start a serial connection.

mark@mark-desktop:~$ sudo synce-serial-start

synce-serial-start detected that a SynCE serial connection was already 
started with PID 8864.

To be able to start a new connection, you may use synce-serial-abort to
force the already active connection to close.

mark@mark-desktop:~$

---

### Post by king756 on 2007-10-20
I have just brought a T-Mobile Vario III (rebranded HTC Kaiser) and am trying to get it to sync with evolution.

I have come across the same errors as some of the others with the following devices being created.

```

679a680,683
> usbdev5.2_ep00
> usbdev5.2_ep03
> usbdev5.2_ep81
> usbdev5.2_ep82

```

I found the solution to solve this problem. Goto Settings -> Connections -> USB to PC and disable advanced network functionality on your pda. After doing this when you plug the pda in it creates '/dev/ttyUSB0' .

Heres a copy of the dmesg after doing the above
```

[ 3879.598029] ipaq 1-2:1.0: PocketPC PDA converter detected
[ 3879.600620] usb 1-2: PocketPC PDA converter now attached to ttyUSB0
[ 3879.600783] usbcore: registered new interface driver ipaq

```

From here i do:
dccm
sudo syce-serial-config /dev/ttyUSB0
sudo synce-serial-start

So far so good, it pops up on my phone, connecting... user authenticated, shows the sync icon at the bottom, then it disconnects, exactly like happens with parvinder.
```

Oct 20 23:35:17 adam-desktop kernel: [ 3879.333318] usb 1-2: new full speed USB device using uhci_hcd and address 2
Oct 20 23:35:18 adam-desktop kernel: [ 3879.510156] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 23:35:18 adam-desktop kernel: [ 3879.590256] usbcore: registered new interface driver usbserial
Oct 20 23:35:18 adam-desktop kernel: [ 3879.590552] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Oct 20 23:35:18 adam-desktop kernel: [ 3879.590876] usbcore: registered new interface driver usbserial_generic
Oct 20 23:35:18 adam-desktop kernel: [ 3879.590881] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Oct 20 23:35:18 adam-desktop kernel: [ 3879.597307] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
Oct 20 23:35:18 adam-desktop kernel: [ 3879.597312] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
Oct 20 23:35:18 adam-desktop kernel: [ 3879.598029] ipaq 1-2:1.0: PocketPC PDA converter detected
Oct 20 23:35:18 adam-desktop kernel: [ 3879.600620] usb 1-2: PocketPC PDA converter now attached to ttyUSB0
Oct 20 23:35:18 adam-desktop kernel: [ 3879.600783] usbcore: registered new interface driver ipaq
Oct 20 23:37:03 adam-desktop kernel: [ 3984.758569] PPP generic driver version 2.4.2
Oct 20 23:37:03 adam-desktop kernel: [ 3984.825005] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 20 23:37:03 adam-desktop synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Oct 20 23:37:03 adam-desktop pppd[7221]: pppd 2.4.4 started by root, uid 0
Oct 20 23:37:04 adam-desktop pppd[7221]: Serial connection established.
Oct 20 23:37:04 adam-desktop pppd[7221]: Using interface ppp0
Oct 20 23:37:04 adam-desktop pppd[7221]: Connect: ppp0 <--> /dev/ttyUSB0
Oct 20 23:37:05 adam-desktop kernel: [ 3986.329265] PPP BSD Compression module registered
Oct 20 23:37:05 adam-desktop kernel: [ 3986.370578] PPP Deflate Compression module registered
Oct 20 23:37:05 adam-desktop pppd[7221]: local  IP address 192.168.131.102
Oct 20 23:37:05 adam-desktop pppd[7221]: remote IP address 192.168.131.201
Oct 20 23:37:11 adam-desktop pppd[7221]: LCP terminated by peer
Oct 20 23:37:11 adam-desktop pppd[7221]: Connect time 0.1 minutes.
Oct 20 23:37:11 adam-desktop pppd[7221]: Sent 400 bytes, received 1018 bytes.
Oct 20 23:37:14 adam-desktop pppd[7221]: Connection terminated.
Oct 20 23:37:14 adam-desktop pppd[7221]: Modem hangup
Oct 20 23:37:14 adam-desktop pppd[7221]: Exit.

```

Any ideas?

---

### Post by king756 on 2007-10-21
Got a bit further.

It turns out as I am running Windows Mobile 6 I need to take a different approach. If you are using WM2005 or WM6 dont disable the advanced network settings to get ttyUSB0 if you originaly got something similar to below from dmesg 

```

679a680,683
> usbdev5.2_ep00
> usbdev5.2_ep03
> usbdev5.2_ep81
> usbdev5.2_ep82

```

Now follow the instructions from this tutorial [http://ubuntuforums.org/showthread.php?t=345176&highlight=odccm](http://ubuntuforums.org/showthread.php?t=345176&highlight=odccm) . Note ignore the bit about compiling the kernel if you are using the latest ubuntu, do this instead [http://ubuntuforums.org/showthread.php?t=345176&highlight=odccm](http://ubuntuforums.org/showthread.php?t=345176&highlight=odccm) .

I also noticed in the tutorial when i run the following i got no output:
```

sudo lshw -businfo | grep usb

```

And when i run the below i got a error and no ip assigned:
```
sudo dhclient3 rndis0
```

However when i run 'sudo odccm -f' and plug my phone in it is detected and typing 'pls' list the directorys and running plstatus shows the status. pls/plstatus are from the svn checkout in the tutorial (not the wrong urls, should be [https://synce.subversion](https://synce.subversion).... ). If I run the synce-pls installed by apt-get I get errors.

Now according to that tutorial I should be able to type 'synce:///' into the filebrowser and the pda files pop up, so far I have not managed to get that to work.

Also I have not got syncing with evolution using a datacable fixed yet. However I have got it to work using syncevolution and scheduleworld and installing funombol on my phone. I'd rather not use schedual world as I don't like the idea of storing my contacts etc on a external server i don't own.

---

### Post by toneman77 on 2007-11-02
So far everything went fine using this guide with Gutsy Gibbon and a XDA Neo (HTC Prophet)
When Connecting i get:
```
Nov  2 10:48:46 tones kernel: [ 5951.785569] usb 3-1: new full speed USB device using uhci_hcd and address 10
Nov  2 10:48:46 tones kernel: [ 5951.957409] usb 3-1: configuration #1 chosen from 1 choice
Nov  2 10:48:46 tones kernel: [ 5951.960360] ipaq 3-1:1.0: PocketPC PDA converter detected
Nov  2 10:48:46 tones kernel: [ 5951.962580] usb 3-1: PocketPC PDA converter now attached to ttyUSB1
Nov  2 10:48:46 tones kernel: [ 5951.962689] ipaq 3-1:1.1: PocketPC PDA converter detected
Nov  2 10:48:46 tones kernel: [ 5951.963647] usb 3-1: PocketPC PDA converter now attached to ttyUSB3

```
i then start:
```
tone@tones:~$ synce-trayicon  
tone@tones:~$ dccm 
tone@tones:~$ sudo synce-serial-config ttyUSB1

You can now run synce-serial-start to start a serial connection.

tone@tones:~$ sudo synce-serial-start 
kill: 15: No such process


synce-serial-start is now waiting for your device to connect

tone@tones:~$ 

```
Which gives me the following in /var/log/messages :
```
 Nov  2 10:51:09 tones synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Nov  2 10:51:09 tones pppd[12911]: pppd 2.4.4 started by root, uid 0
Nov  2 10:51:09 tones kernel: [ 6095.445807] f8d3cba4
Nov  2 10:51:10 tones kernel: [ 6095.445817] Modules linked in: iptable_filter ip_tables x_tables ppp_async ppp_generic slhc crc_ccitt rndis_host cdc_ether usbnet mii ipaq usbserial nls_cp437 nls_utf8 cifs binfmt_misc af_packet ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video container sbs button dock ac battery w83627ehf i2c_isa lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device sn9c102 compat_ioctl32 snd gspca soundcore videodev v4l2_common v4l1_compat usblp parport_pc parport pcspkr snd_page_alloc nvidia(P) i2c_core psmouse serio_raw iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev reiserfs sg usbhid hid sd_mod sr_mod cdrom ata_piix floppy e1000 ehci_hcd ata_generic libata scsi_mod uhci_hcd usbcore thermal processor fan fuse apparmor commoncap

```

But when i now try to connect to my device with the tray icon i get "no device connected"

Is there anything I am missing? What do I have to do do get this connection working.

Thanks in advance

Tone

---

### Post by intruderukr on 2007-11-06
Hi, I'm really new at this, am trying to synch my iPAQ 2495 running Windows mobile-5 to Gutsy Gibbon, I went through the whole tutorial which went well until  I ran the tray icon command and got this:
Unpacking synce-trayicon (from synce-trayicon_0.9.0-2_i386.deb) ...
Setting up synce-trayicon (0.9.0-2) ...
trude@ubuntu:~$ sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2
trude@ubuntu:~$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
trude@ubuntu:~$ sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2
ln: creating symbolic link `/usr/lib/libgtop-2.0.so.2' to `/usr/lib/libgtop-2.0.so.5': File exists
trude@ubuntu:~$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
trude@ubuntu:~$ dccm
trude@ubuntu:~$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
trude@ubuntu:~$ dccm
trude@ubuntu:~$ sudo synce-serial-config ttyUSB0

You can now run synce-serial-start to start a serial connection.

trude@ubuntu:~$ sudo synce-serial-start

synce-serial-start is now waiting for your device to connect

trude@ubuntu:~$ sudo synce-serial-start 

synce-serial-start is now waiting for your device to connect

trude@ubuntu:~$ 

As you see I tried a few different things, to no avail.  I'll appreciate your input.
Thanks!

---

### Post by toneman77 on 2007-11-10
> **intruderukr said:**
> Hi, I'm really new at this, am trying to synch my iPAQ 2495 running Windows mobile-5 to Gutsy Gibbon, I went through the whole tutorial which went well until  I ran the tray icon command and got this:
Unpacking synce-trayicon (from synce-trayicon_0.9.0-2_i386.deb) ...
Setting up synce-trayicon (0.9.0-2) ...
trude@ubuntu:~$ sudo ln -s /usr/lib/libgtop-2.0.so.5 /usr/lib/libgtop-2.0.so.2
trude@ubuntu:~$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: cannot open shared object file: No such file or directory
...

It seems you linked to a file you dont have. so first remove your link with
```
sudo rm /usr/lib/libgtop-2.0.so.2
```
then check what version of libgtop you have installed with
```
ls /usr/lib | grep libgtop
```
I had 2.0.so.7
so the command must be:
```
sudo ln -s /usr/lib/libgtop-2.0.so.7 /usr/lib/libgtop-2.0.so.2
```

---

### Post by thetimekeeper on 2007-11-12
You. Are. Amazing! I tried without success to get synce to work before, but after your guide, it worked flawlessly, except for the link with the libgtop which I got working.

I can browse and install programs on my PPC! Now there is truly nothing my Ubuntu can't do that Windows can. (Except Dreamweaver and Photoshop...:P) Thank you very much!

---

### Post by wild_oscar on 2007-11-14
[QUOTE=parvinder;3294676
But, now I am in a situation as with some other users, after I connect my AT&T 8525 and issue the command 
 -->"sudo sync-serial-start" 
--->I get a message that it is waiting for the device to connect. 
--->device shows user authenticated but then disconnects within less than a min.[/QUOTE]

I have the exact same problem. 
My /var/log/messages file shows:

```

Nov 14 17:25:48 localhost kernel: [26245.020074] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Nov 14 17:25:52 localhost kernel: [26248.548705] usb 2-2: new full speed USB device using ohci_hcd and address 8
Nov 14 17:25:52 localhost kernel: [26248.772926] usb 2-2: configuration #1 chosen from 1 choice
Nov 14 17:25:52 localhost kernel: [26248.775901] ipaq 2-2:1.0: PocketPC PDA converter detected
Nov 14 17:25:52 localhost kernel: [26248.779145] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
Nov 14 17:29:30 localhost kernel: [26467.039528] usb 2-2: USB disconnect, address 8
Nov 14 17:29:30 localhost kernel: [26467.041249] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Nov 14 17:29:30 localhost kernel: [26467.041707] ipaq 2-2:1.0: device disconnected
Nov 14 17:30:28 localhost kernel: [26524.782675] usb 2-2: new full speed USB device using ohci_hcd and address 9
Nov 14 17:30:29 localhost kernel: [26525.006721] usb 2-2: configuration #1 chosen from 1 choice
Nov 14 17:30:29 localhost kernel: [26525.009691] ipaq 2-2:1.0: PocketPC PDA converter detected
Nov 14 17:30:29 localhost kernel: [26525.012935] usb 2-2: PocketPC PDA converter now attached to ttyUSB0
Nov 14 17:30:36 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Nov 14 17:30:36 localhost pppd[4473]: pppd 2.4.4 started by root, uid 0
Nov 14 17:30:37 localhost pppd[4473]: Serial connection established.
Nov 14 17:30:37 localhost pppd[4473]: Using interface ppp0
Nov 14 17:30:37 localhost pppd[4473]: Connect: ppp0 <--> /dev/ttyUSB0
Nov 14 17:30:37 localhost pppd[4473]: local  IP address 192.168.131.102
Nov 14 17:30:37 localhost pppd[4473]: remote IP address 192.168.131.201
Nov 14 17:30:43 localhost pppd[4473]: LCP terminated by peer
Nov 14 17:30:43 localhost pppd[4473]: Connect time 0.1 minutes.
Nov 14 17:30:43 localhost pppd[4473]: Sent 400 bytes, received 1293 bytes.
Nov 14 17:30:46 localhost pppd[4473]: Connection terminated.
Nov 14 17:30:46 localhost pppd[4473]: Modem hangup
Nov 14 17:30:46 localhost pppd[4473]: Exit.


```

Any idea?

---

### Post by windigofer on 2007-11-16
> **toneman77 said:**
> So far everything went fine using this guide with Gutsy Gibbon and a XDA Neo (HTC Prophet)
When Connecting i get:
```
Nov  2 10:48:46 tones kernel: [ 5951.785569] usb 3-1: new full speed USB device using uhci_hcd and address 10
Nov  2 10:48:46 tones kernel: [ 5951.957409] usb 3-1: configuration #1 chosen from 1 choice
Nov  2 10:48:46 tones kernel: [ 5951.960360] ipaq 3-1:1.0: PocketPC PDA converter detected
Nov  2 10:48:46 tones kernel: [ 5951.962580] usb 3-1: PocketPC PDA converter now attached to ttyUSB1
Nov  2 10:48:46 tones kernel: [ 5951.962689] ipaq 3-1:1.1: PocketPC PDA converter detected
Nov  2 10:48:46 tones kernel: [ 5951.963647] usb 3-1: PocketPC PDA converter now attached to ttyUSB3

```
i then start:
```
tone@tones:~$ synce-trayicon  
tone@tones:~$ dccm 
tone@tones:~$ sudo synce-serial-config ttyUSB1

You can now run synce-serial-start to start a serial connection.

tone@tones:~$ sudo synce-serial-start 
kill: 15: No such process


synce-serial-start is now waiting for your device to connect

tone@tones:~$ 

```
Which gives me the following in /var/log/messages :
```
 Nov  2 10:51:09 tones synce-serial-start: Executing '/usr/sbin/pppd call synce-device'
Nov  2 10:51:09 tones pppd[12911]: pppd 2.4.4 started by root, uid 0
Nov  2 10:51:09 tones kernel: [ 6095.445807] f8d3cba4
Nov  2 10:51:10 tones kernel: [ 6095.445817] Modules linked in: iptable_filter ip_tables x_tables ppp_async ppp_generic slhc crc_ccitt rndis_host cdc_ether usbnet mii ipaq usbserial nls_cp437 nls_utf8 cifs binfmt_misc af_packet ppdev acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video container sbs button dock ac battery w83627ehf i2c_isa lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device sn9c102 compat_ioctl32 snd gspca soundcore videodev v4l2_common v4l1_compat usblp parport_pc parport pcspkr snd_page_alloc nvidia(P) i2c_core psmouse serio_raw iTCO_wdt iTCO_vendor_support intel_agp agpgart shpchp pci_hotplug evdev reiserfs sg usbhid hid sd_mod sr_mod cdrom ata_piix floppy e1000 ehci_hcd ata_generic libata scsi_mod uhci_hcd usbcore thermal processor fan fuse apparmor commoncap

```

But when i now try to connect to my device with the tray icon i get "no device connected"

Is there anything I am missing? What do I have to do do get this connection working.

Thanks in advance

Tone

Running Gutsy myself (and for the record, this is probably the *first* release of Ubuntu Linux that has actually had synce Behave As Advertised for me :3).

As noted, you do have to manually restart synce-serial-start with each connection--or, what you can do is try the [UDEV hack described earlier in the thread]("http://ubuntuforums.org/showpost.php?p=1886534&postcount=47") (this involves adding a specific ruleset in /etc/udev prompting synce-serial-start to autostart when it detects a Pocket PC connection; needless to say, this does have some security issues and should probably not be used on multiuser systems).

I have confirmed, at least on my end, that the instructions work perfectly on Gutsy (aside from the obvious issue with the libraries for synce-trayicon needing to be symlinked to /usr/lib/libgtop-2.0.so.7 rather than /usr/lib/libgtop-2.0.so.5).

(As a somewhat related aside, Gutsy has been quite well behaved on this old frankenlaptop (HP ZE4500 using Compaq Presario 2190US motherboard--yes, they do use the exact same motherboard, so such hardware chimaeras are quite possible :D).  I understand that Gutsy has given owners of new HP laptops fits, but at least us owners of "ain't no way it'll run Vista" lappies seem to be quite happy so far :D  (Dare I say it, even Compiz Fusion works out of the box with one single tweak to xorg.conf :D  Yes, even on this ATI Radeon 200M Hunk-O-Crap (tm) internal videocard :D  The *only* piece of hardware that required anything really special was the modem, and that's because it's one of those bloody annoying Linuxant modems that requires the proprietary driver to work correctly. :P)

---

### Post by toneman77 on 2007-11-18
Thanks for the reply, but i got it working some days ago.

Thats what i did (many thanks to jc2k)

- blacklisted the ipaq module
- installed rndis:
> **Jc2k said:**
> ```
svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```
- installed odccm and synce-gnomevfs from jc2k's repositories
- connected my phone

...and all went good (browsable with pls or synce://)

Thanks jc2k, you were very helpful

> **Jc2k said:**
> The best people to help you with SynCE are the SynCE team, so i look forward to seeing you in [IRC]("http://www.synce.org/index.php/IRC") or the [mailing list]("https://lists.sourceforge.net/lists/listinfo/synce-users").

Last but not least:
> **Jc2k said:**
> In Ubuntu, i strongly suggest against recompiling the kernel just for usb-rndis-lite. It just isn't needed!

---

### Post by Jc2k on 2007-11-19
Gutsy users:

You need these repositories... Add them to your /etc/sources.list however you normally do it.
```
deb http://ppa.launchpad.net/synce/ubuntu gutsy main
deb-src http://ppa.launchpad.net/synce/ubuntu gutsy main
```

Then install odccm and some support libraries
```
sudo apt-get update
sudo apt-get install odccm python-rapi2 python-rra python-rtfcomp libwbxml2-dev synce-gnomevfs subversion build-essential linux-kernel-headers
```

The following will install the driver you need to connect your device:
```
svn co http://synce.svn.sf.net/svnroot/synce/trunk/usb-rndis-lite/
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```

Now start odccm and connect your device:
```
sudo odccm -f
```

If you want to sync your device, you are up to here in the wiki instructions now.
[http://www.synce.org/index.php/SyncEngine#pywbxml](http://www.synce.org/index.php/SyncEngine#pywbxml)

There is more to follow. Note that this method will mean you get a transparent upgrade to 0.11 when it is released...

---

### Post by collegedude10 on 2007-12-02
> **Trab said:**
> 

first we need to find out where your pocketpc is in dev...thanks again to storm for this part...

with your device unpluged type
```

ls /dev > /tmp/before

```
then plugin your device and type
```

ls /dev > /tmp/after
diff /tmp/before /tmp/after

```

hopefully it shows 
ttyUSB0 (just remember wat this is!)



when i ran this, this is what i got in return. so where is my device located?
> 
edgar@edgar-laptop:~$ ls /dev > /tmp/before
edgar@edgar-laptop:~$ ls /dev > /tmp/after
edgar@edgar-laptop:~$ diff /tmp/before /tmp/after
0a1
> 3-2
668a670,673
> usbdev3.5_ep00
> usbdev3.5_ep03
> usbdev3.5_ep81
> usbdev3.5_ep82
edgar@edgar-laptop:~$ 

---

### Post by Iurie on 2007-12-03
> **Jc2k said:**
> Gutsy users:

The following will install the driver you need to connect your device:
```
svn co http://synce.svn.sf.net/svnroot/synce/trunk/usb-rndis-lite/
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```


How can I uninstal **usb-rndis-lite** installed from CVS?

---

### Post by corwinckler on 2008-01-22
Hi

Im on Gutsy, trying to get a new TytnII from htc to talk via Synce.

I *think* that Im close. Ive been reading forums for days trying just about everything.

The closest I have come is, to disable 'advance networking' in 'USB to PC' settings. Then dmesg show ttyUSB being recognised:
[  683.664000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  683.840000] usb 2-1: configuration #1 chosen from 1 choice
[  684.124000] usbcore: registered new interface driver usbserial
[  684.124000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  684.124000] usbcore: registered new interface driver usbserial_generic
[  684.124000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  684.144000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[  684.144000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[  684.144000] ipaq 2-1:1.0: PocketPC PDA converter detected
[  684.144000] usb 2-1: PocketPC PDA converter now attached to ttyUSB0
[  684.144000] usbcore: registered new interface driver ipaq
[  713.728000] PPP generic driver version 2.4.2
[  713.812000] ip_tables: (C) 2000-2006 Netfilter Core Team
[  715.232000] PPP BSD Compression module registered
[  715.276000] PPP Deflate Compression module registered

When I plug the sudo odccm -f

** (process:7031): DEBUG: _odccm_interface_address: waiting for IP address on ppp0
** (process:7031): DEBUG: _odccm_interface_address: waiting for IP address on ppp0
** (process:7031): DEBUG: _odccm_interface_address: waiting for IP address on ppp0
** (process:7031): DEBUG: _odccm_interface_address: waiting for IP address on ppp0
** (process:7031): DEBUG: _odccm_interface_address: waiting for IP address on ppp0
** (process:7031): DEBUG: device_info_received
** (process:7031): DEBUG: 94 e4 62 9b 2c 11 db a6 39 e4 73 9a 34 55 91 00 05 00 00 00 02 00 00 00 0b 00 00 00 48 00 54 00 43 00 5f 00 54 00 79 00 54 00 4e 00 5f 00 49 00 49 00 00 00 05 02 54 06 11 0a 00 00 05 00 00 00 d3 77 79 79 00 00 00 00 0f 00 00 00 50 6f 63 6b 65 74 50 43 00 53 53 44 4b 00 00 06 00 00 00 4b 61 69 73 65 72 00 02 00 00 00 05 00 00 00 02 00 00 00 05 00 00 00 02 00 00 00 00 00 00 00 10 00 00 00 0c 00 00 00 5d 00 00 00 01 00 00 00
** (process:7031): DEBUG: extradata:
** (process:7031): DEBUG: 10 00 00 00 0c 00 00 00 5d 00 00 00 01 00 00 00
** (process:7031): DEBUG: device_info_received: registering object path '/org/synce/odccm/Device/_9B62E494_112C_A6DB_39E4_739A34559100_'
device in I also get good feedback from odcm:

These I get when I do the synce-serial-start

I run synce-trayicon, BUT then get 'no device connected'

I try synce-pls and get:
cor@cor-laptop:~$ synce-pls
synce-pls: Could not find configuration at path '(Default)'


The synce-pls manual page says nothing about a configuration. Neither does the synce wiki. Im at a loss. I have no PIN on my device, (the only reference I could get to it was that you may have security on the device). 

Any ideas?

Regards
--Cor

---

### Post by max_dev on 2008-02-08
```
$ synce-trayicon
synce-trayicon: error while loading shared libraries: libgtop-2.0.so.2: wrong ELF class: ELFCLASS64
```

I'm using a Ubuntu's 64-bit version.

```
getlibs /usr/bin/synce-trayicon
No match for libgtop-2.0.so.2
```

:confused:

---

### Post by luispa on 2008-02-08
Hi,

This is an excellent guide. The problem is I can't connect my HTC Wizard to my computer. There's two situations.

WITH FIRESTARTER RUNNING: 
After entering "sudo synce-serial-start" nothing happens for a few minutes and then I receive this message:
"Warning!

You have firewall rules that may prevent SynCE from working properly!

synce-serial-start was unable to start the PPP daemon!"

I already opened ports 990, 5678 and 5679

WITHOUT FIRESTARTER RUNNING (By pressing the GUI STOP button):
After entering "sudo synce-serial-start" I get these messages on the HTC Wizard:
...
Connecting to Host
Authenticating User
Authenticated User
Disconnect
...

A few seconds after that the USB Connection icon disappear from the Wizard screen. 
...
I get these messages on terminal:
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.131.1
remote IP address 192.168.131.129

synce-serial-start is now waiting for your device to connect
...

The strange thing is at this moment Firestarter start working by itself without pressing the GUI "Start" button.

The syslog says:
Feb  8 21:41:32 luispa-desktop pppd[21716]: pppd 2.4.4 started by luispa, uid 0
Feb  8 21:41:33 luispa-desktop pppd[21716]: Serial connection established.
Feb  8 21:41:33 luispa-desktop pppd[21716]: Using interface ppp0
Feb  8 21:41:33 luispa-desktop pppd[21716]: Connect: ppp0 <--> /dev/ttyUSB0
Feb  8 21:41:33 luispa-desktop pppd[21716]: Cannot deter]: local  IP address 192.168.131.1
Feb  8 21:41:33 luispa-desktop pppd[21716]: remote IP address 192.168.131.129
Feb  8 21:41:41 luispa-desktop pppd[21722]: LCP terminated by peer
Feb  8 21:41:41 luispa-desktop pppd[21722]: Connect time 0.2 minutes.
Feb  8 21:41:41 luispa-desktop pppd[21722]: Sent 360 bytes, received 1265 bytes.
Feb  8 21:41:44 luispa-desktop pppd[21722]: Connection terminated.
Feb  8 21:41:44 luispa-desktop pppd[21722]: Modem hangup
Feb  8 21:41:44 luispa-desktop pppd[21722]: Exit.
Feb  8 21:41:48 luispa-desktop kernel: [ 7049.516000] Inbound IN=eth1 OUT= MAC=00:e0:7d:f7:57:32:00:30:b8:c7:e7:a1:08:00 SRC=24.86.103.143 DST=200.125.120.152 LEN=52 TOS=0x00 PREC=0x00 TTL=232 ID=0 DF PROTO=TCP SPT=31883 DPT=3128 WINDOW=37234 RES=0x00 SYN URGP=0 
Feb  8 21:42:33 luispa-desktop kernel: [ 7094.492000] usb 1-2: USB disconnect, address 32
Feb  8 21:42:33 luispa-desktop kernel: [ 7094.500000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
Feb  8 21:42:33 luispa-desktop kernel: [ 7094.500000] ipaq 1-2:1.0: device disconnected
...

Analizing both situations my guess is something is going wrong with FIRESTARTER but I don't know what. Any help will be really appreciated.

---

### Post by luispa on 2008-02-08
I forgot to set the notification type.

---

### Post by luispa on 2008-02-10
Good News!!! I partially solved this issue. Now I can connect my HTC Wizard and browse its files using Nautilus (synce:///). 

I was using dccm instead odccm. I'm using odccm now and works in this way:
- I need to STOP Firestarter
- After connection is established Firestarter starts again
- The HTC Wizard remains connected. This is the GOOD NEW.

I opened ports 990, 5678 and 5679. Firestarter allows connections from 192.168.131.1/24 and I still can't to run synce-serial-start without stopping Firestarter. i really appreciate some help on this.

Thank you very much in advance.

---

### Post by prostar on 2008-03-03
I am also up to this point with my HTC Hermes.  I can browse files/applications and get the mount/unmount notifications, but I can not get it to sync anything.  I keep getting "Broken Pipe" errors.  This points to a "synce engine" problem according to some sources.  It seems that "synce engine" used to be a separate component, but is now built into one of the other binaries?  How do I make sure the engine is started?  

I can even sync my Evolution calandar with Google calendar, but this is getting ridiculous.

*** UPDATE ***

This thread contains old/misleading info.  I put some tips on how I got mine working [here]("http://ubuntuforums.org/showthread.php?p=4470878#post4470878").

Basically the "synce" package I got from the repository didn't have a working sync-engine.  I had to download the one from svn (no building required).

---

### Post by nking00 on 2008-03-15
i get this: synce-trayicon: error while loading shared libraries: libgnutls.so.12: cannot open shared object file: No such file or directory ... anyone has any ideas? thanks!

---

### Post by excogitation on 2008-03-18
May I ask where I can find "synce-trayicon, synce-gnomevfs und synce-software-manager" now that the links in the first post return 404?

And - has anybody tried that on Hardy?

---

### Post by nking00 on 2008-03-18
hello, i got mine from [[COLOR="Blue"]here[/COLOR]]("http://distro.ibiblio.org/pub/linux/distributions/startcom/ML-5.0.5/os/i386/repodata/repoview/synce-0-0.9.1-7.ML5.html") but rpm so you need alien (synaptic has that..) or ```
sudo apt-get update
sudo apt-get install alien
``` the command: ```
 sudo alien -k name-of-rpm-file.rpm 
``` that convert to a deb..
-n

---

### Post by excogitation on 2008-03-19
Thanks, nking00.

What explorer do I use? MC?

Nautilus says:
"Couldn't display "synce:///".
Nautilus cannot handle synce: locations."

If I now want to sync my contacts with Evolution ... (->multisync)?

---

### Post by goodtimetribe on 2008-04-05
Ok, that's it. I've spent a couple of hours a few different times and I say this is totally bogus. Nothing works. I've tried it all. Anyone that says it works can VNC into my box and do it for me. I'll even pay up for it. I've wasted too many hours, and I've seen nothing new. For anyone willing to take a whack at it, it's a cingular 3125 on gutsy.

---

### Post by VeeDubb on 2008-04-06
> **goodtimetribe said:**
> Ok, that's it. I've spent a couple of hours a few different times and I say this is totally bogus. Nothing works. I've tried it all. Anyone that says it works can VNC into my box and do it for me. I'll even pay up for it. I've wasted too many hours, and I've seen nothing new. For anyone willing to take a whack at it, it's a cingular 3125 on gutsy.

Well, first of all, if you look at the first post you'll see that this was originally posted in '06.  Before 7.10 was released, so there are MANY different packages available.

The only bright spot is that the upcoming Spring 2008 release of mandriva linux (2008.1) will have a meta package that will install and configure everything for you in a couple of clicks.  It's not available in the current release (2008.0) but it should be out soon.

Best of luck.

---

### Post by kseise on 2008-04-21
Does anyone know where to find the .debs for synce-trayicon, synce-gnomevfs and  synce-software-manager for a 64 bit system?  I can't install the 32 bit .debs because dpkg doesn't like the 32 bit files.

---

### Post by TasKiNG on 2008-04-22
I'm using Hardy Heron 8.04 RC 64 Bit

Not found debs but just managed to install them using rpms as follows:-

sudo apt-get install alien

download the following from [ftp://ftp.uib.no/pub/Linux/Distributions/fedora/linux/extras/6/x86_64/repoview/synce-trayicon.html](ftp://ftp.uib.no/pub/Linux/Distributions/fedora/linux/extras/6/x86_64/repoview/synce-trayicon.html)

synce-gnomevfs-0.9.0-5.fc6.x86_64.rpm
synce-software-manager-0.9.0-7.fc6.x86_64.rpm
synce-trayicon-0.9.0-8.fc6.x86_64.rpm

install with :-

sudo alien -i ./synce-gnomevfs-0.9.0-5.fc6.x86_64.rpm
sudo alien -i ./synce-software-manager-0.9.0-7.fc6.x86_64.rpm
sudo alien -i ./synce-trayicon-0.9.0-8.fc6.x86_64.rpm

I've got my Ipaq 3715 connecting when its placed on the cradle and the synce-trayicon illuminates.

From the tray-icon I can add/remove programs but nautilus seems to have a problem opening up the location synce:/// 

Install and run gpe-filemanager as this still works with gnomevfs.  Just type synce:/// into the address bar. Does not seem to want to copy files though :(

Hope this helps

Cheers

Dave

---

### Post by nutpants on 2008-04-26
i have been battling synce and my windows mobile 6 device forever.. and its the same battle when i had my WM5 device and my WM2003 device..

i dont understand why,
  if you can add software to make your pocket pc or smart phone to make it act like a usb drive, they dont just work with the files in the smartphone or pocket pc and bypass active sync on the device.
just put the WM device in usb mode and then work out how to read the files on it.

nutz

---

### Post by mj-barton on 2008-04-26
The main thing holding me back from a complete switch is my Motorola Q.  Regardless of opinions of Windows Mobile, it serves my needs perfectly and I will be using this phone for long while.  I would like to switch over to Ubuntu.  

Has anybody else had luck with Sync CE?

---

### Post by nutpants on 2008-04-28
im getting there with help from the guy on this thread..

[http://ubuntuforums.org/showthread.php?t=761199](http://ubuntuforums.org/showthread.php?t=761199)

i can now communicate with my device..

still working on syncing it.

nutz

---

### Post by boot_sectorz on 2008-05-01
I love my HTC TyTN and its the reason I dual boot too. I don't mind using Outlook for contacts and all as I do this after a while. I want to use my laptop internet access to update a few things of my PDA. Its bad enough paying for 3G data packets when I'm connected on a home network. Can this be done in the new Ubuntu?

---

### Post by abhilashkumar on 2008-05-01
> **Trab said:**
> **READ THIS FIRST**
*edited on 4/7/08*
first we need to find out where your pocketpc is in dev...thanks again to storm for this part...

with your device unpluged type
```

ls /dev > /tmp/before

```
then plugin your device and type
```

ls /dev > /tmp/after
diff /tmp/before /tmp/after

```

hopefully it shows 
ttyUSB0 (just remember wat this is!)


Hi, I just found this post.
I hvae been trying to get this to work for quite some time now. When I tried the above section all I got was this.

> 15d14
< hidraw0
654a654,657
> usbdev1.10_ep00
> usbdev1.10_ep03
> usbdev1.10_ep81
> usbdev1.10_ep82
657,658d659
< usbdev1.4_ep00
< usbdev1.4_ep81

I dont see any ttyUSB0

My Specs:
. Acer Aspire 4520
. HTC Wizard (Imate KJAM) 
. Windows Mobile 5
. Hardy Heron 32bit

Further instructions would be appreciated!

Thanks.

---

### Post by TasKiNG on 2008-05-11
Just came across this [http://www.nabble.com/synce-gvfs-status-td16872791.html]("http://www.nabble.com/synce-gvfs-status-td16872791.html")

Not tried it yet but hoping it will allow Nautilus to connect to synce:///
via gvfs instead of gnomevfs

---

### Post by TasKiNG on 2008-05-11
> **TasKiNG said:**
> Just came across this [http://www.nabble.com/synce-gvfs-status-td16872791.html]("http://www.nabble.com/synce-gvfs-status-td16872791.html")

Not tried it yet but hoping it will allow Nautilus to connect to synce:///
via gvfs instead of gnomevfs

Note: I am using Ubuntu 8.04 64 Bit and have managed to get my IPAQ working with nautilus via gvfs i.e. I can now connect to synce:/// via nautilus.

Right. I followed the instructions here [http://www.mpellis.org.uk/]("http://www.mpellis.org.uk/") to add the repositories.
did a sudo apt-get update
then used synaptic package manager to install synce-gvfs

I also allowed all new updates found except synce-serial as I could not make this version work with udev to automount when the device is put on the cradle.

I then installed vdccm using sudo apt-get install vdccm
to get vdccm to work I then had to type sudo chmod a+s /usr/bin/vdccm then you can run vdccm as a normal user.

I then rebooted and set vdccm in the synce-trayicon preferences.

I can now browse / add and delete files on my ipaq from nautilus.

hope some of this helps someone.

Cheers

---

### Post by AdamWill on 2008-05-12
For transferring files I'd honestly just use wm5torage (the app that makes your device act as a USB mass storage device) because it's just so much simpler. I only worry about synce / opensync for actually *synchronizing*.

---

### Post by Klayy on 2008-05-31
I've managed to get sync working on Ubuntu 8.04 x86 with my HTC Kaiser using simply the tutorial on the SynCE site and then downloading some python header files (some blog suggested this, although I'm not sure whether this has actually helped me and I can't find the blog :/)
I've installed everything and did like a million reboots and then it simply worked, i got a nice popup saying that KlayyHTC is connected, I ran sync in the terminal and it synced everything to evolution, no problems. 

THEN I installed updates, including a kernel update (*-16 to *-17) and nothing works now. I feel like smashing my head against a wall. What could be the problem?
This is basically a clean install so I might just reinstall with my *-16 cd and try to make it work again...


EDIT: 
forgot to mention that it still works when I boot into *-16, although there is some trouble since I've reinstalled the whole thing in *-17 and for example the sync-engine command is not recognized (no idea why)
I'll try reinstalling

---

### Post by JoshuaRL on 2008-06-01
> **Klayy said:**
> I've managed to get sync working on Ubuntu 8.04 x86 with my HTC Kaiser using simply the tutorial on the SynCE site and then downloading some python header files (some blog suggested this, although I'm not sure whether this has actually helped me and I can't find the blog :/)
I've installed everything and did like a million reboots and then it simply worked, i got a nice popup saying that KlayyHTC is connected, I ran sync in the terminal and it synced everything to evolution, no problems. 

THEN I installed updates, including a kernel update (*-16 to *-17) and nothing works now. I feel like smashing my head against a wall. What could be the problem?
This is basically a clean install so I might just reinstall with my *-16 cd and try to make it work again...


EDIT: 
forgot to mention that it still works when I boot into *-16, although there is some trouble since I've reinstalled the whole thing in *-17 and for example the sync-engine command is not recognized (no idea why)
I'll try reinstalling

Sounds like a driver issue with SynCE.  If it still works with the .16 kernal and not the .17 then that's probably the issue.  Reinstalling SynCE and going through the same steps to get it working might fix it for you.

---

### Post by medvet on 2008-06-10
> **Klayy said:**
> I've managed to get sync working on Ubuntu 8.04 x86 with my HTC Kaiser using simply the tutorial on the SynCE site and then downloading some python header files (some blog suggested this, although I'm not sure whether this has actually helped me and I can't find the blog :/)
I've installed everything and did like a million reboots and then it simply worked, i got a nice popup saying that KlayyHTC is connected, I ran sync in the terminal and it synced everything to evolution, no problems. 

THEN I installed updates, including a kernel update (*-16 to *-17) and nothing works now. I feel like smashing my head against a wall. What could be the problem?
This is basically a clean install so I might just reinstall with my *-16 cd and try to make it work again...


EDIT: 
forgot to mention that it still works when I boot into *-16, although there is some trouble since I've reinstalled the whole thing in *-17 and for example the sync-engine command is not recognized (no idea why)
I'll try reinstalling
The procedure for installing synce in hardy includes replacing some kernel drivers. You have to repeat the first part of the installation procedure every time you update the kernel to new version ;)

I pasted the necessary steps from synce wiki below for reference...

> Kernel module

Get the USB driver *YOU MUST DO THIS* - there are critical fixes here not yet in the kernel.

Unload the current modules:

sudo rmmod rndis_host cdc_ether usbnet

Now we have to delete the old drivers, such that the kernel will not reload them next time:

sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko

Now we have to get and compile the new drivers:

sudo apt-get install usb-rndis-source cdbs
sudo module-assistant auto-install usb-rndis


I hope this helps... It worked for me and now I finally got internet on my qtek over usb... Going to try the gvfs module now.

---

### Post by Klayy on 2008-06-13
> **medvet said:**
> The procedure for installing synce in hardy includes replacing some kernel drivers. You have to repeat the first part of the installation procedure every time you update the kernel to new version ;)

I pasted the necessary steps from synce wiki below for reference...



I hope this helps... It worked for me and now I finally got internet on my qtek over usb... Going to try the gvfs module now.



but i did that with *.17 and it didn't work
the drivers installed and all, no errors, but it simply doesn't work
maybe I'm missing something, I'll try with *.18


EDIT:
well, it works, but it's strange - it's creating duplicates, but not with all entries
some things in the calendar get duplicated and some don't and it's driving me crazy


EDIT2: looks like it's ok now, although I haven't changed anything... too bad that I have to confirm what to do with conflicts for all contacts (luckily there's only 140 of them) during each sync, but I don't sync so much
anyway... *sigh* when will all everyday apps have a nice gui in linux? i like the terminal, but cmon...

---

### Post by sureshvv on 2008-06-18
Worked perfectly on my Motorola Mpx220 (Windows Mobile 2003) and Feisty Fawn.

EXCEPT:

1. I needed usbview. The device was not recognized by "lsusb" until I ran "usbview".

2. I got the deb packages from:
 [http://elmanytas.is-a-geek.net/filesblog/apt-ce/sw/PC/](http://elmanytas.is-a-geek.net/filesblog/apt-ce/sw/PC/) 

Thanks elmanytas!

But I still can't get opensync to work because the package opensync-plugin-synce-legacy does not exist for Feisty Fawn. Can I build this from source? Any help appreciated.

---

### Post by thejames on 2008-07-12
> **abhilashkumar said:**
> Hi, I just found this post.
I hvae been trying to get this to work for quite some time now. When I tried the above section all I got was this.


I dont see any ttyUSB0

Further instructions would be appreciated!

Thanks.

Same Problem. 


_My Specs:_
Intel Core 2 Duo 2.33GHz
Asus P5N-MX
2GB DDR2
Nvidia Geforce 8600GT

Using Hardy Heron kernel version 2.6.24-19

---

### Post by Mouth on 2008-07-19
Here's how to get it working ...

1. Make sure you have Hardy 8.04.1 (or Intrepid) (it includes the necessary upstream kernel patch for 2.6.24-19

2. Follow [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)  (and it's final step of kicking you then further onto [http://www.synce.org/moin/SynceSetup](http://www.synce.org/moin/SynceSetup))


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192411](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192411) has background.

---

### Post by Osiah on 2008-07-21
I got the below

707a708,711
> usbdev2.6_ep00
> usbdev2.6_ep03
> usbdev2.6_ep81
> usbdev2.6_ep82

...instead of ttyUSB0...

Did I do something wrong?

---

### Post by BoneZZZ on 2008-07-29
I connect my HTC Polaris with my Ubuntu 8.04.1 box with no problem. I can use mWM5storage, Internet Sharing, but if I install gnomevfs-0.11 or 0.12 to use Nautilus to see my HTC filesystem (via synce:///), it does not work. I'm using synce-hal instead of oddcm, because it is needed by synce-KPM, much better application than synce-GNOME + synce-TRAYICON.

Any ideas?

PS: with synce-oddcm, it did not work either!!!
PS2: gvfs-0.1 does not work either!!!

---

### Post by ^[H3ad-Tr1p]^ on 2008-08-07
hi friends

I'm trying to syncing my ipaq hx4700 and I've a problem that I'm sure many people had had :(

I had upgraded my ipaq from WM2003 to WM 6 and in a little while I'll upgrade to WM6.1

I'd followed this howto [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) until I've entered synce-pls such as send back 

** (process:8866): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00

** (process:8866): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'



as I saw more above the how to this :


The scheme described below is essentially an rndis connection via odccm. This is why you will be asked to blacklist the ipaq driver and to turn Enable enhanced network functionality on. The serial connection via odccm will be hopefully documented some time later and synce-hal when it gets more stable.


and as I didn't blacklisted ipaq driver becouse if I enter in consolle lsmod | grep ipaq I get:

ipaq                   42264  1 
usbserial              41840  3 ipaq
usbcore               169904  13 rndis_host,cdc_ether,usbnet,ipaq,usbserial,snd_usb_audio,uvcvideo,rtl8187,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd


It's that who can be cause of my error?

can You say to me how I can blacklist ipaq driver on hardy? So I can try again synce my ipaq?

thanks a lot

p.s.

If you know that it is possible that I've skipped something it should be great to give me the solution

thanks a lot

---

### Post by keteflips on 2008-09-06
I have the same problem:


> keteflips@moya:~$ msynctool --addmember ipaq evo2-sync 
keteflips@moya:~$ msynctool --addmember ipaq synce-plugin 
keteflips@moya:~$ msynctool --configure ipaq 2 
keteflips@moya:~$ msynctool --sync ipaq 
Synchronizing group "ipaq" 

** (process:10329): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00_0: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00_0

** (process:10329): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
[synce_info_from_file:69] unable to open file: /home/keteflips/.synce/active_connection
[rapi_context_connect:173] Failed to get connection info
Error while initializing syncengine: (null)
keteflips@moya:~$ 


I can see the PDA dates and files with synce-trayicon, the HTC Diamond its perfecte detected.

But I cant synchronize it with Evolution.

---

### Post by gishaust on 2008-11-07
I have had the same problem with my ipaq 112. I followed this howto 

[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)


When I get to  synce-pls i get the following does anyone know how to fix this?

```

** Message: Hal reports no devices connected

** (process:9821): WARNING **: No devices connected to odccm
synce-pls: Could not find configuration at path '(Default)'


```

I have tried my camera on the cable and it works fine I am using ubuntu 8.04. The ipaq is running os ce 5.0

---

### Post by legolas_w on 2008-11-20
Hi
Thank you for reading my post
I followed some steps in synce wiki and I also installed every synce package available in the ubuntu repository to get Nautilus working with synce.

I could get synce-pls to work but I can not see anything when I type synce:/// in the nautilus and instead it return an error like:

```


Nautilus cannot handle "synce" locations

```
I managed to install the try icon and it works fine when I select HAL as the communication daemon.

Thanks

---

### Post by legolas_w on 2008-11-24
Any comment?
Thanks.

---

### Post by nutpants on 2008-11-27
i know that nautilus changed the way they did things in the last 8 months
and that broke the tray icon and synce:/// in the nautilus
but i believe the tray icon was fixed sometime in the last 3 months or so and i did have it working..

how i did it or if it still does work, i dont know...
its hard to keep track of what works and what dose not for a noob like me.
i reinstalled with the new 8.10 on x64 and have not got to the point of trying my mobile device yet, or i was sidetracked trying to get conduit to work with my smartphone..

i forget..
not much help i know..

nutz

---

### Post by Nachoo on 2008-12-16
> **legolas_w said:**
> Hi
Thank you for reading my post
I followed some steps in synce wiki and I also installed every synce package available in the ubuntu repository to get Nautilus working with synce.

I could get synce-pls to work but I can not see anything when I type synce:/// in the nautilus and instead it return an error like:

```


Nautilus cannot handle "synce" locations

```
I managed to install the try icon and it works fine when I select HAL as the communication daemon.

Thanks
Yeah, same problem here. If you search in Synaptic you do find a package called syncevfs or something like does and if you look at the description you'll see it says it is just for that, to be able to browse the pda from Nautilus.... but it doesn't work. Anyway I'll keep trying and I'll let you know.

I'm trying to install trayicon. Can you help me on how to install it? If you don't install it the only way to sync is via the terminal, right?

---

### Post by forrestcupp on 2008-12-24
> **Nachoo said:**
> Yeah, same problem here. If you search in Synaptic you do find a package called syncevfs or something like does and if you look at the description you'll see it says it is just for that, to be able to browse the pda from Nautilus.... but it doesn't work. Anyway I'll keep trying and I'll let you know.

I'm trying to install trayicon. Can you help me on how to install it? If you don't install it the only way to sync is via the terminal, right?

It's called **synce-gvfs** and it does work.  You just need to restart your computer after installing it.  I've been beating myself over the head trying to get this to work, and I finally did it.

I love it.  Synce works so much better than it did a couple of years ago.

---

### Post by clarkkentjt on 2009-01-05
I'm very close, but can't get any PIM info to sync over to my Samsung SCH-i910 with WM6.1.  I'm only trying to get my contacts onto my cell phone, which I have 270 contacts in evolution. I'm running Ubuntu 8.10 Intrepid AMD.   Here's where I'm at:

1. I've followed TomtheWombat's guide from [http://ubuntuforums.org/showthread.php?t=954103](http://ubuntuforums.org/showthread.php?t=954103)   (thanks Tom)
2. I'm using the svm repos, which forces the uninstall of odccm btw.
3. I can see my windows mobile directories via terminal synce-pls and with GUI utility gpe-filemanager (found that suggestion on another forum entry). I can transfer files using gpe-filemanager.
4. Gnome Nautilus never displayed synce:/// (even with synce-gnomevfs plugin and after a reboot).  
5. synce-trayicon only appears if I launch as sudo for the terminal. 
6. I can create/delete partnerships using synce in the terminal, or via the synce-trayicon GUI.  I can successfully delete software addons (ie. google search or google maps)  Deleting a partnership has now removed all of my SCH-i910 initial default Verizon contacts.  No big deal.
7. My mobile phone displays the correct partnership in activesync.  I can initiate a sync and it says successful, but no contacts.
8. I've tried msynctool and multisync0.90, which will attempt to send the data (I see the debug of all the data), but it sits there waiting for opensync to connect to my mobile phone, but never does.
9. synce-kpm GUI shows correctly, but nothing happens when I click the sync Icon.  It also can delete software addons.
10. Also FWIW: on my mobile phone, in the settings, connections, usb connection mode, I have 2 options:  ActiveSync or Mass Storage/MyStorage.  Interesting when I select 'mass storage' my mobile phone's memory card auto-mounts in Ubuntu as a storage device, but synce doesn't see the mobile phone.  synce only sees my mobile phone device when set to 'activesync'.

Suggestions?  Maybe it's a synce config.xml setting?
Any help is appreciated.
-Clark

---

### Post by nutpants on 2009-01-10
i need to unload or stop the  rndis module in ubuntu 8.10 x64
i need to stop it so that vmware can access my wm 6.1 smartphone

i tried rmmod but that did not work.

nutz

---

### Post by kaefert66014235 on 2009-01-11
I have got some parts of synce to work. I've posted my progress here: [http://ubuntuforums.org/showthread.php?t=1034410](http://ubuntuforums.org/showthread.php?t=1034410)

---

### Post by Ehol on 2009-01-12
Does anyone have problems with rndis modules after the upgrade to the new version of Intrepid generic Kernel (2.6.27-11.23) ?

To me is a failure, because rndis fails to register the interface of the PDA and I can't connect anymore with synce (until 2.6.27-11.22 it all worked good)...

---

### Post by Ehol on 2009-01-15
Ok, it was a fault on my side.
Just dled the usb-rndis-lite from Synce SVN, compiled and installed.
After rebooting, all worked well as before.

---

### Post by PhilCash on 2009-01-21
G'day all,

Still banging my head on the desk after reading web page after web page and post after post and wondering if anyone has really ever gotten Synce and multisync and opensync configured to do anything actually useful under the Irritating Ibex with WM6.0...

I've gotten as far as the SynCe tray recognising my HTC Touch Diamond, and starting Multisync in a terminal indicates that its reading some of my calender (probably from Evolution) but fails with:

(multisync:7737): GLib-CRITICAL **: g_hash_table_size: assertion `hash_table != NULL' failed
Segmentation fault

Further investigation uncovers the possible root cause with SynCe:

$ synce-create-partnership "phil-laptop" "Contacts,Calendar,Tasks,Files"
Creating partnership...

error: failed to create partnership
error: org.synce.SyncEngine.Error.NoFreeSlots

ok, so lets see what we have:

$ synce-matchmaker status
Current partner index: 2
Partner 1 id:    0x698121d0
Partner 1 name:  "IOCOMM1"
Partner 2 id:    0x22d94da4
Partner 2 name:  "phil-laptop"

Ok...The sage advice from the SynCe web site is:...delete a partnership on your device to create room for a new one. But they give no indication of how to delete a partnership. synce-matchmaker has no 'delete' option, but it does have a 'clear' option, so lets try that:

sudo synce-matchmaker clear 2
[rra_matchmaker_clear_partnership:330] Failed to erase file: /root/.synce/rra/partner-77bb14b6
Partnership cleaning succeeded.

No joy...It still doesn't leave a vacant slot. Possibly due to the 'Failed to erase file...' notification? 

I don't know. How do you delete a partner?

Can anyone offer any enlightenment on this please?

Cheers,
Phil

---

### Post by Ehol on 2009-01-21
synce-delete-partnership ?
I don't remember for sure, but there is a command like the one I mentioned (or maybe exactly that one).
Try to search for it ...

---

### Post by PhilCash on 2009-01-21
Thanks Ehol. Dunno where you pulled that command from, I still haven't been able to find it (and yes, I've been looking), but it worked as far as it goes... I've got this far:

philcash@phil-laptop:~$ synce-delete-partnership

            AVAILABLE DEVICE PARTNERSHIPS
Index     Name         Device      Host         SyncItems
-----     ----         ------      ----         ---------

0	Windows PC	Touch_Diamond	IOCOMM1	[]
1	Linux desktop	Touch_Diamond	phil-laptop	[Files Calendar Tasks Contacts ]
Select index of partnership to delete, or empty to exit -1
Selected  1
Deleting partnership...
error: org.freedesktop.DBus.Error.NoReply
      ( I wonder what the error implies...did it fail to delete?)
philcash@phil-laptop:~$ 
philcash@phil-laptop:~$ synce-matchmaker status
Current partner index: 0
Partner 1 id:    0x698121d0
Partner 1 name:  "IOCOMM1"
philcash@phil-laptop:~$ 
      (well partner 2 is deleted, but what did the error mean?)
      (lets try multisynch now)
philcash@phil-laptop:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
[synce_connect:324] No partnership on the device matches this synchronization pair.
always_connected
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/phil/.multisync/6/remotesettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
[synce_join_thread:260] synce_join_thread called when no thread is running
sync_disconnect
[evo2-sync] INFORMATION: start: disconnect
philcash@phil-laptop:~$ 
     ("No partnership on the device matches this synchronization pair."
     (seems to be a problem...But when I had a partnership, multisync
     (reported: 
[rra_matchmaker_create_partnership:420] Partnership not found and there are no empty partner slots on device.
[synce_connect:336] Failed to create or select a partnership. Use the synce-matchmaker tool!
      
I'm going round in circles... If I use
"synce-create-partnership "phil-laptop" "Contacts,Calendar,Tasks,Files"
I create a partnership, but am back to "Partnership not found and there are no empty partner slots on device." from multisync.

So now what? If I've got a partnership, it complains its not found and there are no empty slots, and if I don't have one it complains it doesn't match. I'm sure its trying to tell me something, but I wish it would tell me in English. I know I'm close, but somewhere in the syntax is something I'm missing.

(Oh how I wish Palm had kept their hardware up with the times. I plugged my TX in and it all just seemed to work. Still, If Ubuntu is ever to appeal to the masses native support for PPC devices needs to improve.)

Any guidance would be greatly appreciated.

Cheers,
Phil

---

### Post by PhilCash on 2009-01-23
Closer and closer...must be nearly there...

G'day Again,

I have followed the instructions at 
[http://www.edadfutura.com/en/sincron...-ubuntu-macos/](http://www.edadfutura.com/en/sincron...-ubuntu-macos/)
and am closer than ever before, but still not quite there.
After completing the instructions I am able to browse my HTC and see files and status information.
But after attempting to sync, I was greeted with the message "Error Syncing. Unable to read from one of the members."
There did not appear to be a partnership. I started synch-kpm to investigate, and found that there was no partnership, so I setup a new partnership in synce-kpm (thats SynCE KDE PDA Manager...I'm using Ubuntu and don't know if running a KDE application is problematic or not)
So with a new partnership setup, I ran multisync and attempted to sync with the following results:

The initial response from Multisync was "The previous sync was unclean. Slow Syncing."
Then it carried on and stopped, indicating:

synche-opensync-plugin  Connected
evo2-sync               Sent all Changes
759 entries received
All clients connected or in error

But it seems to have halted at this point as the 'Remove", "Edit", and "Refresh" buttons remain grayed out and the updates have not been passed between Evolution and HTC.

Reboot.

After rebooting and trying to synch again with multisynch, the sync process counted through the 759 entries as before, but reported:
Error synchronising: Unable to read from one of the members.
and
synche-opensync-plugin  Disconnected
evo2-sync               Disconnected
All conflicts have been reported

    hmmm...suspect partnership has failed in some way...so, start terminal and:

philcash@phil-laptop:~$ synce-kpm
Running dataserver
running the GUI Part
Initialising DataServer
odccm is NOT running!!
Finished with init
Using new partnership api of sync-engine
checking for active partnerships, querying dataserver

The Synce gui starts and lists the partner as before, but the popup stating "No active partnerships found" comes up.

I can still browse the HTC, so I feel its really coming down to these blasted partnerships, but I just don't know how they work or how to diagnose problems with them.

As always, any help would be appreciated.

Cheers,
Phil

---

### Post by Ehol on 2009-01-26
If you have only the windows partnership you shouldn't be able to sync.
So you definitely need to create at least one partnership with synce.
The problem is I can't understand, after you deleted and then recreated the partnership, what kind of error you receive.
Is synce-sync-engine running ?

I have the doubt that you didn't install the synce suite from synce repository but from ubuntu ones. This is not the right thing to do, because the packages in ubuntu are too old (and a bit screwed I dare to say).

In any case, you should not use synce-kpm, because for Gnome there is the synce-trayicon (and synce-gvfs) that works far better.

The only suggestion I am willing to give you, is to delete all partnership, remove all the packages and start reinstalling all over again.
Maybe with a fresh install of synce suite (use the synce.org wiki to direction in order to install and search for  more updated threads in this forum) you could solve your problems

---

### Post by Trab on 2009-01-28
Ehol, thank you for your help on these problems, I'm sure those who are still trying to get SynCE appreciate it.

I have updated the guide based upon some other guides and wiki's I've found. hopefully this is helpful to someone. 

Please feel free to send me a Message if you have something to add to the guide. 

thanks,
Trab

---

### Post by melodyoutside on 2009-02-14
Hi all, 

I'm a complete newbie at all of this. I have a Axim X5 and would like to sync it with 8.04 (Hardy? or Gutsy? can't remember). From what I've seen on this thread, it appears to be the closest to what I need (I've been looking online for hours and have even tried a few things to no avail), but I see this is for Ubuntu 8.10.  Is there any possible way that you can show me, tell me, email me, whatever, any of the changes in what you wrote so that I can configure it for my axim? It would be a shame to watch it gather dust...forever....

Thanks!

---

### Post by gdiepen on 2009-03-03
> **Ehol said:**
> If you have only the windows partnership you shouldn't be able to sync.
So you definitely need to create at least one partnership with synce.
The problem is I can't understand, after you deleted and then recreated the partnership, what kind of error you receive.
Is synce-sync-engine running ?

I have the doubt that you didn't install the synce suite from synce repository but from ubuntu ones. This is not the right thing to do, because the packages in ubuntu are too old (and a bit screwed I dare to say).

In any case, you should not use synce-kpm, because for Gnome there is the synce-trayicon (and synce-gvfs) that works far better.

The only suggestion I am willing to give you, is to delete all partnership, remove all the packages and start reinstalling all over again.
Maybe with a fresh install of synce suite (use the synce.org wiki to direction in order to install and search for  more updated threads in this forum) you could solve your problems

I think that the majoriy of your problems were caused by using synce-matchmaker, which actually is meant for wm2003 and older devices and not for wm5/6/6.1 devices. 


> **Trab said:**
> Ehol, thank you for your help on these problems, I'm sure those who are still trying to get SynCE appreciate it.

I have updated the guide based upon some other guides and wiki's I've found. hopefully this is helpful to someone. 

Please feel free to send me a Message if you have something to add to the guide. 

thanks,
Trab

I was wondering whether you could add some link in the opening post to our own wiki on [http://www.synce.org](http://www.synce.org). The reason is that there is a large number of different instructions on the web. Unfortunately, not all of them are always updated after we update the instructions on our own Wiki. The best would be to have one central set of instructions instead of multiple copies that are all different.

Kind regards,

Guido Diepen

---

### Post by mike310z on 2009-03-07
How do we get the Ubuntu repository updated to the latest version from 0.11  ?

/frustrated gripe/
And ;-)  is there any way to actually make this work. I have beaten this 7 ways from hades(hell) and I cannot get a sync with WM6.1 phone.
/frustrated gripe off/

keep up the good work, if I can help debug wm6.1 with verizon phone let me know.

---

### Post by markofealing on 2009-03-17
> **forrestcupp said:**
> It's called **synce-gvfs** and it does work.  You just need to restart your computer after installing it.  I've been beating myself over the head trying to get this to work, and I finally did it.

I love it.  Synce works so much better than it did a couple of years ago.

synce-gvfs does not exist in Ubuntu 8.10 although there is a synce-gnomevfs. Selecting Explore with Filemanager just gives me the "Could not display "" Nautilus could not handle "synce" locations.

---

### Post by markofealing on 2009-03-17
Okay, a bit more Googling and found [https://launchpad.net/~synce/+archive/ppa](https://launchpad.net/~synce/+archive/ppa) and it now works.

---

### Post by kaefert66014235 on 2009-03-18
> **markofealing said:**
> synce-gvfs does not exist in Ubuntu 8.10 although there is a synce-gnomevfs. Selecting Explore with Filemanager just gives me the "Could not display "" Nautilus could not handle "synce" locations.

-) synce-gnomevfs is included in ubuntu, but doesn't work.
-) synce-gvfs does work great under 8.10, and it is not included in the ubuntu repositories.
-) you will need to use "http://ppa.launchpad.net/synce/ubuntu interpid main" if you want any functunality of synce

---

### Post by JoshuaRL on 2009-03-19
> **kaefert66014235 said:**
> -) synce-gnomevfs is included in ubuntu, but doesn't work.
-) synce-gvfs does work great under 8.10, and it is not included in the ubuntu repositories.
-) you will need to use "http://ppa.launchpad.net/synce/ubuntu interpid main" if you want any functunality of synce

I agree. I use synce just fine.  But I went to the synce wiki and installed using that, and the PPA.  For now that seems to be the answer.

---

### Post by Izobalax on 2009-04-10
I've followed the steps in this guide by fail at this point:

I type:

```
synce-pls
```

and the terminal gives me back:

```
synce-pls: error while loading shared libraries: libsynce.so.0: cannot open shared object file: No such file or directory
```

I use the PPA Jaunty repositories (running Jaunty beta), my device is an O2 XDA Orbit (first version). 

HALP.

/izo\

---

### Post by beansdad on 2009-04-17
Similar to above but I get the following response to synce-pls:

synce-pls: symbol lookup error: /usr/lib/librapi.so.2: undefined symbol: synce_info_get_transport

have tried all the options in connection problems to no avail. Can anyone help please.:(

---

### Post by Ehol on 2009-04-18
Try to give
```
ls -la /usr/lib/librapi*
```
and post here the results

---

### Post by kseise on 2009-05-07
$ ls -la /usr/lib/librapi*
lrwxrwxrwx 1 root root    16 2009-04-01 07:42 /usr/lib/librapi.so.2 -> librapi.so.2.0.0
-rw-r--r-- 1 root root 87992 2009-03-31 10:00 /usr/lib/librapi.so.2.0.0
$

---

### Post by mac0502 on 2009-05-20
when Im trying to install librra0-tools im getting this:

[FONT=Georgia]Package librra0-tools is a virtual package provided by:
  librra-tools 0.13-0ubuntu0~ppa1~intrepid1
You should explicitly select one to install.
E: Package librra0-tools has no installation candidate
[/FONT]

So i was trying to install it in synaptic but it still doesnt work

synce-pls give this error:

** Message: Hal reports no devices connected
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'


Im runing eeebuntu standard on eee901

---

### Post by killabee44 on 2009-05-22
> **JoshuaRL said:**
> I agree. I use synce just fine.  But I went to the synce wiki and installed using that, and the PPA.  For now that seems to be the answer.

Thanks. BTW... in case anyone wants a link to the wiki, here it is: 

[Synce Wiki]("http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice")

I successfully installed the synce and can see my files listed when I type in synce-pls at a terminal, but how do I browse my files in order to add and delete them? That's all I really want to do for now. 

btw.. 

```
sudo apt-get install opensync-plugin-kdepim
```

did not work. I got an error: "Couldn't find package opensync-plugin-kdepim"


Thanks.

---

### Post by Cyclops_ on 2009-05-23
I get the following error when trying synce-pls:

```

user@desktop:/etc/apache2/sites-available$ synce-pls 
** Message: Device /org/freedesktop/Hal/devices/usb_device_bb4_a04_noserial_if0_serial_usb_0 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

```

Any help would be great!!!

---

### Post by Cyclops_ on 2009-05-23
I guess I should have given my specs:

Laptop, Jaunty
(2.0 GHz, 800 MHz FSB, 2 MB L2 Cache, 4 Gig DDR2)

The Pocket-PC is a HTC PPC6601KIT with Windows Mobile 2003

---

### Post by joseangelusa on 2009-06-04
Hi,

I'm trying to set up synce to **browse the files in my mobile device**. I followed the steps in [http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice) but after running synce-pls I get the following error:

** Message: Device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

Additionally I installed synce-gfvs plus SynCE Tray Icon. Tray Icon shows as "not connected" even though my device is hooked up to the usb.

I have enabled "faster data synchronization" in the usb configuration in the mobile device. (If I disable it, the OS does not see the device).
The OS detects my device, I can see it under eth1. 
And I was succesful in doing internet-sharing/tethering. I'm using wicd.

I'm not so much interested for now in sync'ing the device, only browsing and tethering.

Additional info:
Mobile device: HTC Touch Cruise with Windows Mobile 6.5
OS: Ubuntu 8.10 (intrepid)
Laptop: Thinkpad T61P

Any help is truly appreciated.
Thanks.
= J =

---

### Post by Digitallad on 2009-06-06
If you have any problems with duplicate contacts after sync go to this Thread [http://ubuntuforums.org/showthread.php?t=1178304](http://ubuntuforums.org/showthread.php?t=1178304)  is quite useful

---

### Post by FAJALOU on 2009-06-06
Hi I am trying to get SynCE to work on my wm2003-SE HP IPAQ.
So Far I am very very close.  I have it set up so the computer will connect to my laptop but...

When I try to run this command:
```
lrc-laptop:~$ synce-matchmaker create** Message: Device /org/freedesktop/Hal/devices/usb_device_3f0_1016_noserial_if0_serial_usb_0 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
[rapi_context_connect:173] Failed to get connection info
[main:66] Failed to initialize RAPI
```

The above happens.  Then after a while, my two devices will disconnect.  Any help will be appreciated, I am really looking for any advice.  Thanks!

---

### Post by ledzepjes on 2009-06-15
TO: joseangelusa and anyone else

[PHP]Hi,

I'm trying to set up synce to browse the files in my mobile device. I followed the steps in [http://www.synce.org/moin/SynceInsta...u/ModernDevice](http://www.synce.org/moin/SynceInsta...u/ModernDevice) but after running synce-pls I get the following error:

** Message: Device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

Additionally I installed synce-gfvs plus SynCE Tray Icon. Tray Icon shows as "not connected" even though my device is hooked up to the usb.

I have enabled "faster data synchronization" in the usb configuration in the mobile device. (If I disable it, the OS does not see the device).
The OS detects my device, I can see it under eth1. 
And I was succesful in doing internet-sharing/tethering. I'm using wicd.

I'm not so much interested for now in sync'ing the device, only browsing and tethering.

Additional info:
Mobile device: HTC Touch Cruise with Windows Mobile 6.5
OS: Ubuntu 8.10 (intrepid)
Laptop: Thinkpad T61P

Any help is truly appreciated.
Thanks.
= J =[/PHP]

I to had the same error when connecting my HERA11000 (Tmobile Wing, or HTC P4300). Not due to the error, but for those interested about my phone setup and for me to make sure I have the latest operating system, I upgraded the mobile phone from WM5 to WM6 using the official Tmobile upgrage program. I went to the Synce website:
[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)

I tried synce-pls, and got an error similar to this:

[PHP]** Message: Device /org/freedesktop/Hal... {bla bla bla}... Hal, skipping
** Message: Odccm is not running...
synce-pls: Could not find configuration at path '(Default)'[/PHP]

For me, and I don't know if this is for everyone, but I had to make sure, before connecting the usb, that the program "ActiveSync" would be running in the task manager of the phone, if not I had to restart the phone to make sure, (psShutxp is a good mobile app to restart the phone). Then, after "ActiveSync" was running on the phone, in terminal:
[PHP]owner@ubuntu-pc:~$ synce-pls
Directory               2008-04-22 12:00:18  My Pictures/
Directory               2008-04-22 12:00:18  Templates/
Directory               2008-04-22 12:00:18  Personal/
Directory               2008-04-22 12:00:18  Business/
Directory               2008-04-22 12:00:18  My Music/
Directory               2008-04-22 12:00:18  My Ringtones/
Directory               2008-04-22 12:00:20  My Videos/
Directory               2008-07-30 14:04:24  Calls/
Directory               2008-08-06 23:33:14  Bluetooth Share/
Directory               2008-04-22 12:00:22  UAContents/
Directory               2008-04-22 12:00:24  My Voices/
Directory               2008-04-22 12:00:24  My Icons/
Archive           8551  2008-09-13 14:19:12  Doc1.docx
Directory               2008-10-28 17:00:36  Data/
Directory               2009-01-01 09:52:46  My Documents/
Directory               2009-03-04 16:40:50  Dictionaries/[/PHP]


I must first say, I didn't setup a partnership as of yet, but this is a guide showing from the beginning how I got my phone to sync with ubuntu 9.04 jaunty. As I just wanted to view the contents of my phone to copy/cut/edit files. I went to synce website: [http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)
In terminal:[PHP]owner@ubuntu-pc:~$ sudo gedit /etc/apt/sources.list[/PHP]
This opens up the repositories sources.list, scroll to the bottom, create two blank lines at the bottom of the list and paste these two codes into the blank lines:[PHP]deb http://ppa.launchpad.net/synce/ubuntu jaunty main
deb-src http://ppa.launchpad.net/synce/ubuntu jaunty main[/PHP]
**Note, my version of ubuntu is 9.04 jaunty, hence the reference to jaunty in the code. Logically, you'll need to replace "jaunty" with "intrepid" if you are using ubuntu 8.10 intrepid.
Save the list and close it and type:[PHP]owner@ubuntu-pc:~$ sudo apt-get update[/PHP]
Next:[PHP]owner@ubuntu-pc:~$ sudo apt-get install synce-hal librra-tools librapi2-tools[/PHP]
Then I connected my phone to the usb to my computer, first restarting my phone to make sure "ActiveSync" was indeed running, and then typing in terminal:[PHP]owner@ubuntu-pc:~$ synce-pls[/PHP]and got:[PHP]owner@ubuntu-pc:~$ synce-pls
Directory               2008-04-22 12:00:18  My Pictures/
Directory               2008-04-22 12:00:18  Templates/
Directory               2008-04-22 12:00:18  Personal/
Directory               2008-04-22 12:00:18  Business/
Directory               2008-04-22 12:00:18  My Music/
Directory               2008-04-22 12:00:18  My Ringtones/
Directory               2008-04-22 12:00:20  My Videos/
Directory               2008-07-30 14:04:24  Calls/
Directory               2008-08-06 23:33:14  Bluetooth Share/
Directory               2008-04-22 12:00:22  UAContents/
Directory               2008-04-22 12:00:24  My Voices/
Directory               2008-04-22 12:00:24  My Icons/
Archive           8551  2008-09-13 14:19:12  Doc1.docx
Directory               2008-10-28 17:00:36  Data/
Directory               2009-01-01 09:52:46  My Documents/
Directory               2009-03-04 16:40:50  Dictionaries/[/PHP]
Since it is listing the contents of the phone directories, I know that it was connecting correctly and I can move on. Otherwise, if you get something similar to joseangelusa's error messages[PHP]** Message: Device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00 not fully set in Hal, skipping
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'[/PHP] first restart the phone and make sure "ActiveSync" is running in the task list, also, in the phone go to start/settings/connections/usb to pc and make sure to UNcheck "Enable advanced network functionality".
At this point, I disconnected the phone, in terminal:[PHP]owner@ubuntu-pc:~$ sudo apt-get synce-trayicon[/PHP]to install the trayicon, it shows the icon of a phone up by the clock and by right clicking the icon, you can "explore with file manager" the contents of the phone, but you can't actually do this without synce-gvfs  installed (**NOTE:synce-gvfs supercedes synce-gnomevfs, install gvfs instead of gnomevfs), if you don't have synce-gvfs installed you will get this error in a popup window: [PHP]"Could not display "synce://"your phone name here"/"
Nautilus cannot handle "synce" locations.[/PHP]
So to get synce-gvfs, [PHP]owner@ubuntu-pc:~$ sudo apt-get synce-gvfs[/PHP]
then
1. restart the computer
2. restart the phone
3. and connect the phone with the usb cable
4. right click the synce-trayicon and 
5. click on "explore with file manager"
And now you should be browsing your phone ;)

Hope this helps, I will try to condence this later and post to a new thread and edit to show the link later just to simplify things.

---

### Post by Naegling23 on 2009-06-18
so, I have synce-trayicon set up, everything works.  The problem is that if I unmount my device, I cannot reconnect it without restarting my whole computer.  Is there a proper way to disconnect the phone from the computer to prevent this?

---

### Post by ToastyMallows on 2009-07-04
Hi everyone!

This tutorial works great for me.  I set up my Blackjack 2 SGH-i617 to work with Synce and the Synce Trayicon, I can browse my files and it gives me no errors what-so-ever.  I have synced my contacts to Evolution.  However, I have a question.

If my phone has to be reset at some point, would this synce help me to put all of my contacts back onto my phone?  And what steps would I need to take to make a partnership with my phone to get it back in it's original state so that I lose no contacts.


Thanks.

---

### Post by Circa Lucid on 2009-07-06
> **ToastyMallows said:**
> If my phone has to be reset at some point, would this synce help me to put all of my contacts back onto my phone?

Yupper. I just upgraded from an ATT 3125 to a Pantech Duo and SynCe worked perfect. Only drawback is that if you ever delete and re-create a partnership, you have to negotiate all the entry conflicts (you get alot of duplicate entries and multisync asks you which to keep).

HTH

---

### Post by kaefert66014235 on 2009-07-08
Its not really well suited in this topic, but its the imho better (and also free) alternative to synce:

[http://www.google.com/mobile/products/sync.html](http://www.google.com/mobile/products/sync.html)

Google acts to your mobile device as an exchange server, and syncs both calendar entries with your google calendar and contacts with your google mail contacts. Its especially interesting for people with internet on their windows mobile devices, since with this technique you can sync on the go.

---

### Post by wewantutopia on 2009-07-08
so I'm running Jaunty and when I enter [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get synce[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]gvfs  I get:

E: Invalid operation synce-gvfs

Any ideas?
[/COLOR][/COLOR]

---

### Post by kaefert66014235 on 2009-07-09
i would try sudo apt-get install synce-gvfs

---

### Post by Lemuel111 on 2009-07-10
[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]I have a Dell Axim 30 which I have been trying to sync but with no success. I am using Ubuntu 9. I type sync-pls in terminal & get the following:-
** Message: Hal reports no devices connected
** Message: No devices connected to odccm
synce-pls: Could not find configuration at path '(Default)'

I've also added the 2 lines as suggested:-
[/COLOR][/COLOR][COLOR=#000000][COLOR=#0000BB]deb http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//ppa.launchpad.net/synce/ubuntu jaunty main 
[/COLOR][COLOR=#0000BB]deb[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]src http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//ppa.launchpad.net/synce/ubuntu jaunty main  [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#0000BB]
I then type:-
sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get update 

and the following then comes up:-
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB       
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [7406B]
Get: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [2897B]
Fetched 63.5kB in 0s (82.9kB/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can anyone help?

Thanks in advance. 
[/COLOR][/COLOR]

---

### Post by mbeenham on 2009-07-11
> **Lemuel111 said:**
> [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR][/COLOR]

Have you got Synaptic running at the same time? Only one app can lock the database at a time.

As luck would have it I just this morning connected up my Axim X30 to my PC running Xubuntu Jaunty and following this excellent tutorial have it working.
Auto connects,Multisync window pops up when plugged in etc. I can synce-pls etc and synce-pstatus shows:
Version
=======
Version:    4.21.1088 (Microsoft Windows Mobile 2003 Pocket PC Phone Edition)
Platform:   3 (Windows CE)
Details:    ""

System
======
Processor architecture: 5 (ARM)
Processor type:         2577 (StrongARM)
Page size:              0x10000

Power
=====
ACLineStatus: 01 (Online)

Status for main battery
=========================
Flag:          12 (Unknown)
LifePercent:   100%
LifeTime:      Unknown
FullLifeTime:  Unknown

Status for backup battery
=========================
Flag:          1 (High)
LifePercent:   100%
LifeTime:      Unknown
FullLifeTime:  Unknown

Store
=====
Store size: 34082816 bytes (32 megabytes)
Free space: 9968284 bytes (9 megabytes)

Memory for storage: 34234368 bytes (32 megabytes)
Memory for RAM:     32251904 bytes (30 megabytes)

I have installed:
opensync-plugin-synce
synce-sync-engine
libopensync0
synce-multisync-plugin
libsynce0
librra0
librra-tools
multisync-tools
synce-hal
python-opensync
opensync-plugin-evolution
Some of these may be unnecessary as I did a fair bit of experimentation before I found this thread...

HTH

Please ignore above - following is accurate list of installed modules from my history listing:
libebackend1.2-0	(2.26.1-0ubuntu2)
libedata-book1.2-2	(2.26.1-0ubuntu2)
libedata-cal1.2-6	(2.26.1-0ubuntu2)
libgnet2.0-0	(2.0.8-1)
libmimedir0	(0.4-4)
libmultisync-plugin-backup	(0.82-8.1ubuntu2)
libmultisync-plugin-evolution	(0.82-8.1ubuntu2)
libmultisync-plugin-irmc	(0.82-8.1ubuntu2)
libopensync0	(0.22-2build1)
librapi2	(0.13-0ubuntu0~ppa1~jaunty2)
librapi2-tools	(0.13-0ubuntu0~ppa1~jaunty2)
librra0	(0.13-0ubuntu0~ppa1~jaunty1)
librra-tools	(0.13-0ubuntu0~ppa1~jaunty1)
librtfcomp0	(1.1-4)
libsynce0	(0.13-0ubuntu0~ppa1~jaunty1)
multisync	(0.82-8.1ubuntu2)
multisync-tools	(0.92.0~svn355-1)
opensync-module-python	(0.22-2build1)
opensync-plugin-evolution	(0.22-2ubuntu2)
opensync-plugin-synce	(0.11.1-2)
python-dateutil	(1.4.1-2)
python-rapi2	(0.13-0ubuntu0~ppa1~jaunty2)
python-rra	(0.13-0ubuntu0~ppa1~jaunty1)
synce-hal	(0.13-0ubuntu0~ppa1~jaunty2)
synce-multisync-plugin	(0.9.0-4.1)
synce-sync-engine	(0.13-0ubuntu0~ppa1~jaunty1)

---

### Post by Lemuel111 on 2009-07-12
I have gone through that list and added the ones which were missing but still nothing. I tried typing sync-pls in terminal & this is the read out:-
** (process:3901): CRITICAL **: synce_info_from_hal: Failed to get a connection for /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0: Pocket_PC: Not authenticated, you need to call ProvidePassword with the correct password.
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

Any suggestions?

---

### Post by diggedy on 2009-07-13
In case anyone is having trouble, im finding S2U2 is affecting the link, I have to ensure it is unlocked or sync-pls will not work

---

### Post by Lemuel111 on 2009-07-20
I have tried doing the tutorial again and double checking everything & I can get to "sync-pls" and this is the read out in terminal:-
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_2 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_1 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_0 not fully set in Hal, skipping
Unable to get the "My Documents" path.

Consequently I cannot read any files on my PDA & move onto the next stage. I am unable to find any similar read out on google. Can anyone help?
Thanks.

---

### Post by wucherpfennig on 2009-07-21
same problem here

---

### Post by Lemuel111 on 2009-07-29
I found this site [http://www.handhelds.org/moin/moin.cgi/AximX30Downloads](http://www.handhelds.org/moin/moin.cgi/AximX30Downloads)

but being new to Linux I can't understand what exactly to do. I have downloaded the first to items but after double clicking on them nothing happens. Can anyone help?

Thanks.

---

### Post by Ehol on 2009-08-01
Lemuel, that files are needed to install and boot linux ON the Axim30.
This thread is to help in using Synce to synchronize your windows mobile device with a Linux box (Ubuntu in this case).

If you really want to boot linux on the Axim, you better need to open a new thread in a more appropriate forum .

---

### Post by Ehol on 2009-08-01
> **Lemuel111 said:**
> I have tried doing the tutorial again and double checking everything & I can get to "sync-pls" and this is the read out in terminal:-
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_2 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_1 not fully set in Hal, skipping
** Message: Device /org/freedesktop/Hal/devices/usb_device_413c_4003_noserial_if0_serial_usb_0_0 not fully set in Hal, skipping
Unable to get the "My Documents" path.

Consequently I cannot read any files on my PDA & move onto the next stage. I am unable to find any similar read out on google. Can anyone help?
Thanks.

Do you have a firewall ? Try to disable it and retry.
If it works, you have to open port 5678 and 5679 in your firewall in order for synce to work.

Otherwise I have no clues, sorry.

---

### Post by alpha1echo on 2009-08-01
hi, can anyone help when i 

sudo /etc/init.d/networking restart

i get the following error. 

 * Reconfiguring network interfaces...                                          /etc/network/interfaces:7: too many parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:7: too many parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

Can anyone help.

---

### Post by JoshuaRL on 2009-08-02
> **alpha1echo said:**
> hi, can anyone help when i 

sudo /etc/init.d/networking restart

i get the following error. 

 * Reconfiguring network interfaces...                                          /etc/network/interfaces:7: too many parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:7: too many parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

Can anyone help.

What is in that file?
```
gedit /etc/network/interfaces
```

---

### Post by Lemuel111 on 2009-08-03
I disabled the firewall and typed sync -pls in terminal & this is the reading (PDA is connected):-

** Message: Hal reports no devices connected
** Message: No devices connected to odccm
synce-pls: Could not find configuration at path '(Default)'

---

### Post by Lemuel111 on 2009-08-06
At last I have a connection! I got it from this link

[http://ubuntuforums.org/showthread.php?p=6808083#post6808083](http://ubuntuforums.org/showthread.php?p=6808083#post6808083)

and followed the first item.

---

### Post by havoc783 on 2009-08-25
I'm having some problems getting this working on 9.04 (Jaunty).  What I'm  inevitability trying to achieve here is a update for my Samsung Omnia. The step where you add the lines to the text file, ( like the second or third step), I replaced the intrepid with jaunty and no luck finding packages.  Secondly, I went ahead and did the $sudo apt-get install synce-hal librapi2-tools, which worked, then connected the device and typed synce-pls and it gives me this:

$ sudo synce-pls
** Message: Hal reports no devices connected
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'


What's going on? Can you please point me in the right direction?
Thanks

---

### Post by kseise on 2009-08-26
HAVOC783 - You need to open the ports in your firewall.  If you are using Firestarter, try disabling the firewall and retrying the connection just the way you posted.  If it works with the firewall disabled, you need to open the ports when you reactivate the firewall.  I think it's port 5900, but check Google.  I am on a Windows machine right now.

---

### Post by havoc783 on 2009-08-26
> **kseise said:**
> HAVOC783 - You need to open the ports in your firewall.  If you are using Firestarter, try disabling the firewall and retrying the connection just the way you posted.  If it works with the firewall disabled, you need to open the ports when you reactivate the firewall.  I think it's port 5900, but check Google.  I am on a Windows machine right now.
Well, I tried this after a fresh boot and didn't have the firewall started yet. Are you sure it's a port issue?  Any thoughts?

---

### Post by shimoda on 2009-09-06
Thanks Ehol & Kseise...

I had the same problem and was the firewall... :)

---

### Post by bernt_ on 2009-09-07
> **legolas_w said:**
> 
I can not see anything when I type synce:/// in the nautilus and instead it return an error like:

```


Nautilus cannot handle "synce" locations

```


> **forrestcupp said:**
> 
It's called **synce-gvfs** and it does work.  You just need to restart your computer after installing it.  


You can do it also without reboot.
First look for the nautilus process:
ps -ax|grep nautilus
and kill them.
Then look for gvfs and gvfsd:
ps -ax|grep gvfs
and kill them.
They will be restarted but then they understand synce.
Now I can use the trayicon to browse my mobile phone.
(at this time the icons on the desktop reappears)

---

### Post by Mickafromparis on 2009-10-03
Hi!
It's basically working for me as long as i reboot everytime i want synce to work... Any idea? The FW issue is not fixed also, have to stop it everytime for synce-pls to work. Any help appreciated. Thanks

---

### Post by FAJALOU on 2009-10-06
Hey having an issue of my own.  When I type in synce-pls I get the following:

> louie@up2:~$ sudo ufw disable
Firewall stopped and disabled on system startup
louie@up2:~$ synce-pls

** (process:8101): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.name for device /org/freedesktop/Hal/devices/usb_device_3f0_1016_noserial_if0_serial_usb_0: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.name on device with id /org/freedesktop/Hal/devices/usb_device_3f0_1016_noserial_if0_serial_usb_0

** (process:8101): WARNING **: synce_info_from_odccm: Failed to get devices: The name org.synce.odccm was not provided by any .service files
synce-pls: Could not find configuration at path '(Default)'

Any thoughts would be appreciated!  thanks!

---

### Post by gotokhaleel on 2009-11-12
> **beansdad said:**
> Similar to above but I get the following response to synce-pls:

synce-pls: symbol lookup error: /usr/lib/librapi.so.2: undefined symbol: synce_info_get_transport

have tried all the options in connection problems to no avail. Can anyone help please.:(

Were you able to solve the problem? I too get the same error as below:

synce-pls: symbol lookup error: /usr/lib/librapi.so.2: undefined symbol: synce_info_get_transport

Pls help on this error.

---

### Post by dadoc on 2009-11-30
Same problem here:

[dadoc@dadoc-laptop:~] $sudo synce-pls
synce-pls: symbol lookup error: /usr/lib/librapi.so.2: undefined symbol: synce_info_get_transport

[dadoc@dadoc-laptop:~] $ls -la /usr/lib/librapi*
lrwxrwxrwx 1 root root    16 2009-12-01 08:20 /usr/lib/librapi.so.2 -> librapi.so.2.0.0
-rw-r--r-- 1 root root 97752 2009-11-12 11:05 /usr/lib/librapi.so.2.0.0

---

### Post by dadoc on 2009-11-30
apparently i've solved this issue by:

```
sudo apt-get install librapi2-dev
```

not sure why it helped

---

### Post by Tirish Anau on 2010-01-20
I don't know if anyone has tried this but it seems that if you add the packages from the following walkthrough([http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevic]("http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevic")e). If you add the packages before you add the source list you can force the install of synce and get the source add to the source list later. I have been pouring over code for hours and It has been a ***** to install. It does work.... kinda. I am still working on getting a positive sink but both the device (motorolla Q running WM 6.1) run recognize each others existence. My only problem at this point is it seems that Nautilus cannot handle "synce" locations. Which makes it irritably hard, further more the device can't successfully sync. The Q can recognize the network it just can't connect. ANY suggestions at this point would be HUGELY helpful. The source still doesn't update but synce kind of works. I am Running 9.10 Intrepid on an triple core amd Phenom and a 64 bit system with the Ubuntu studio.

---

### Post by Tirish Anau on 2010-01-21
I have gotten Synce to work I just can't get the sources to sink up. here is my problem.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

---

### Post by martah26 on 2010-01-22
Hi Thanks a million for the help you have provided - but I wonder if I may further trouble you for a moment. I am trying to connect Thunderbird with my IPAQ but am unsure what specifically I need to link it too - in the below line of your instructions it links to Evolution - but the actual wording for Thunderbird has me confused. All that I have followed works great - upto my identifying this partnership.

tmsynctol --addmember synce-sync evo2-sync

Many thanks .

---

### Post by kseise on 2010-02-09
> **martah26 said:**
> 

tmsynctol --addmember synce-sync evo2-sync


Martah26- Try making that 
```

msynctool --addmember synce-sync evo2-sync

```

I see typos in your post and if you are making the same errors at the commandline, that might be the problem.

---

### Post by NOTmick on 2010-03-15
Ok, one more time.

I've tried many approaches to this issue of syncing my HP iPAC pocketPC with Ubuntu, with no real success.  I've installed and uninstalled lots of files.  I have the icon in the tray when the PocketPC is attached, so I know it exists and Ubuntu knows about it.

Most tutorials and helps are for older versions of Ubuntu, though.
_**How about for 9.10?**_

What changes are needed and how do I do this?!

I'm fairly new to Ubuntu, but not a complete novice.

All help welcome.

Thanks!

---

### Post by Ehol on 2010-03-17
> **NOTmick said:**
> Ok, one more time.

I've tried many approaches to this issue of syncing my HP iPAC pocketPC with Ubuntu, with no real success.  I've installed and uninstalled lots of files.  I have the icon in the tray when the PocketPC is attached, so I know it exists and Ubuntu knows about it.

Most tutorials and helps are for older versions of Ubuntu, though.
_**How about for 9.10?**_

What changes are needed and how do I do this?!

It depends on what version of WM you have on your PPC.
If >= 5.0, then if you follow a walkthrough for 8.10 or 9.04, it applies well even to 9.10 (i.e. [http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice](http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice)). You just have to change the repo packages for karmic (i.e. deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) karmic main)


If older than 5.0 (i.e. wm2003), try [http://www.synce.org/moin/LegacyDevices/Ubuntu](http://www.synce.org/moin/LegacyDevices/Ubuntu). It should work with evry version of Ubuntu.

Hope this will help
Regards,
Ehol

---

### Post by samMD on 2010-03-20
ok so now how do you uninstall all of this , cause there is app called Microsoft My Phone

---

### Post by RealG187 on 2010-03-22
My device is password connected and I cannot connect until I enter my password on my phone. I have Synce tray installed, but I don't see anywhere to enter my password on my computer...

---

### Post by Ehol on 2010-03-23
> **RealG187 said:**
> My device is password connected and I cannot connect until I enter my password on my phone. I have Synce tray installed, but I don't see anywhere to enter my password on my computer...

My device too is password-protected and, as far as I know, there's no other way to unlock it than from the device itself ... I don't see the point in your statement ...

---

### Post by RealG187 on 2010-03-23
I heard you can use Synce Tray for password protected devices. I hate having to enter my password all the time, even on Windows. With ActiveSync and my old iPaq on XP I could enter the password on my computer.

It would be nice to save the password on my computer, that way I have convienient accesss to my phone but other people don't.

---

### Post by brandjamie on 2010-03-24
Finally got my phone syncing the calender and contacts but the tasks won't sync. Anyone know what I'm doing wrong?

Sorry, forgot to mention I'm syncing with Evolution.

---

### Post by RealG187 on 2010-03-24
Also, is there a way I can open PWI (Note) files I made on my phone in Ubuntu?

---

### Post by brandjamie on 2010-03-26
Well I fixed my problem with the tasks not syncing by installing some dodgy software that bricked my phone. Works fine after a hard reset! There are probably better methods though. 

I don't think it's possible to sync the notes (it's not listed in the evo-sync plug in settings).

---

### Post by RealG187 on 2010-03-26
I don't wanna sync the notes, I just want to view the PWI files by opening them like a normal file.

---

### Post by [CS]LaBrute on 2010-05-27
I have a problem with synce-sync-engine ... I cannot install it because it depends on packages that depend on python 2.4. 

Now, the actual problem that is annoying me for a while but managed to get around it until now is the fact that I have installed both python 2.4 and 2.6, but the packages synce-sync-engine depends on still say that they cannot be installed because they require python 2.4. On the other hand I cannot remove python 2.6 so that I can have only 2.4 because half of my system will be uninstalled.

How can I get around this annoying python problem?

Here is what I get:

```

n00b@darkstar:~/.synce$ sudo apt-get install synce-sync-engine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  synce-sync-engine: Depends: python-rra (>= 0.14) but it is not going to be installed
                     Depends: python-rapi2 (>= 0.14) but it is not going to be installed
                     Depends: python-rtfcomp but it is not going to be installed
E: Broken packages
n00b@darkstar:~/.synce$ 

```And next:

```
n00b@darkstar:~/.synce$ sudo apt-get install python-rra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-rra: Depends: python (< 2.6) but 2.6.4-0ubuntu1 is to be installed
E: Broken packages
n00b@darkstar:~/.synce$ 

```

This is awfully disturbing so if anyone has a solution it would be more than welcomed :)

Thanks!

---

### Post by fc90 on 2010-08-25
Hi @all,
sorry for reanimating this thread, but I also have a problem with sync.

I must connect two windows mobile phones to one PC (for a project in the uni).
There is an option "-o" for sync-engine that should be for only connecting one device to it. So in the normal mode (without -o) multiple devices should be no problem.

But it don't work for me.
When I connect the first device, than everything works perfectly. But when I connect the secound device it is ignored...

I hope anyone can help me.

Best Regards,
fc90

---

### Post by paul.drover on 2011-02-24
Running Maverick. I blithely followed the howto to install synce 'cause I'd kinda like to have my Ubuntu machine talk to my phone (htc). There was an indication that dccm was needed as well, so I apt-got synce-dccm. Now my machine fails to boot - black screen no disk activity after the grub2 os selection. How do I go about undoing what I've done? I'm guessing that it starts with booting from a CD, but what then?

Help... please.

Paul.

---

