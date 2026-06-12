---
title: "HowTo: Use Barry to Sync and backup/restore your Blackberry with Jaunty"
date: 2009-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Darkwing-Duck on 2009-09-13
So what I’m going to try and do here is give you a simple tutorial on installing Barry and configuring it to sync your blackberry with Evolution and to use the backup/restore features.


 To save some time and running about I have made an install script for the first part. You can download it [here]("http://david.wonderly.com/files/blackberry.tar.gz").
 

Once you have it downloaded open your terminal and go to the folder where you downloaded the file. (I also have in the tar.gz file a copy of this tutorial.)
 Once you’re in the folder where you downloaded the file unzip the tar.gz
 

```
tar -xvfz blackberry.tar.gz
```
Okay open the folder and there will be 3 files in there. install, README and syncit.
 

Run the install script
 

```
./install
```
Once it is done installing the packages you are ready to backup and restore your blackberry. Plug it in and type barrybackup to launch the program!
 

Now, if you are like me and wanted to sync your blackberry with Evolution there is a little more work to do. First off you want to make sure you have all your information in Evolution backed up. With evolution open click File >> Backup Settings…
 Follow those directions and it will back everything up for ya.
 

Now, to the fun stuff. Configuring opensync to run with Evolution and your Blackberry.
 Run these commands one at a time.
 

```
msynctool --delgroup EvoBarry
 msynctool --addgroup EvoBarry
 msynctool --addmember EvoBarry evo2-sync
 msynctool --addmember EvoBarry barry-sync
 msynctool --configure EvoBarry 1

```Okay, at this point it will bring up a text editor to configure the file. While it may look like a GUI it really isn’t. To navigate you should use the arrow keys. This file is setup like a XML file. You should change the contents to reflect what I have below. The only thing you need to custom change is the XXXXX to whatever your home folder is (If your login is direct the the XXXXX will be direct).
 
 > <config>
     <address_path>file:///home/XXXXX/.evolution/addressbook/local/system</address_path>
     <calendar_path>file:///home/XXXXX/.evolution/calendar/local/system</calendar_path>
     <tasks_path>file:///home/XXXXX/.evolution/tasks/local/system</tasks_path>
</config> Press Ctrl+X to close and and press Y to save.
 

Now, your ready for the second configuration.
 

```
msynctool --configure EvoBarry 2
```
Here there are a couple of things you will need to change or update. You will need to update your device PIN and if you have a password for your device you will need to delete the # that is before Password and change the work secret to whatever your password is.

> 

#
# This is the default configuration file for the barry-sync opensync plugin.
# Comments are preceded by a '#' mark at the beginning of a line.
# The config format is a set of lines of  .
#
# Keywords available:
#
# DebugMode        - If present, verbose USB debug output will be enabled
#
# Device           - If present, it is followed by the following values:
#      PIN number    - PIN number of the device to sync with (in hex)
#      sync calendar - 1 to sync calendar, 0 to skip
#      sync contacts - 1 to sync contacts, 0 to skip
#
# Password secret  - If present, specifies the device's password in plaintext
#
#DebugMode
Device 3009efe3 1 1
#Password secret
Once again, press Ctrl+X to exit and Y to save.
 

Now for the last command.
 

```
msynctool --showgroup EvoBarry
```
Now that everything is good to go you can run the syncit file.
 

```
./syncit
```
If you have any problems or have any questions please feel free to email me.

---

### Post by Lybic on 2009-09-16
./syncit: No such file or directory


not sure where i messed up

thanx in advance
Nick

---

### Post by pvicc on 2009-09-17
hi, 
Pls help.
I am getting this when i tried to addmember barry-sync

~$ msynctool --addmember EvoBarry barry-sync
Unable to instance plugin with name barry-sync: Unable to find the plugin "barry-sync"

Thanks in Advance

Additional information
before this command

The following NEW packages will be installed:
  barry-util libboost-serialization1.34.1 libopensync0 multisync-tools
  opensync-plugin-barry opensync-plugin-evolution
The following packages will be upgraded:
  barrybackup-gui
1 upgraded, 6 newly installed, 0 to remove and 1 not upgraded.
Need to get 1085kB of archives.
After this operation, 3604kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  barry-util barrybackup-gui opensync-plugin-barry
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libboost-serialization1.34.1 1.34.1-15ubuntu3 [398kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main barry-util 0.16-0git2009083047 [275kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libopensync0 0.22-2build1 [233kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main barrybackup-gui 0.16-0git2009083047 [76.6kB]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main opensync-plugin-barry 0.16-0git2009083047 [67.8kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe multisync-tools 0.92.0~svn355-1 [21.6kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe opensync-plugin-evolution 0.22-2ubuntu2 [14.1kB]
Fetched 1085kB in 29s (36.8kB/s)                                               
Selecting previously deselected package libboost-serialization1.34.1.
(Reading database ... 173303 files and directories currently installed.)
Unpacking libboost-serialization1.34.1 (from .../libboost-serialization1.34.1_1.34.1-15ubuntu3_i386.deb) ...
Selecting previously deselected package barry-util.
Unpacking barry-util (from .../barry-util_0.16-0git2009083047_i386.deb) ...
Preparing to replace barrybackup-gui 0.14-2ubuntu2 (using .../barrybackup-gui_0.16-0git2009083047_i386.deb) ...
Unpacking replacement barrybackup-gui ...
Selecting previously deselected package libopensync0.
Unpacking libopensync0 (from .../libopensync0_0.22-2build1_i386.deb) ...
Selecting previously deselected package multisync-tools.
Unpacking multisync-tools (from .../multisync-tools_0.92.0~svn355-1_i386.deb) ...
Selecting previously deselected package opensync-plugin-barry.
Unpacking opensync-plugin-barry (from .../opensync-plugin-barry_0.16-0git2009083047_i386.deb) ...
Selecting previously deselected package opensync-plugin-evolution.
Unpacking opensync-plugin-evolution (from .../opensync-plugin-evolution_0.22-2ubuntu2_i386.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Processing triggers for man-db ...
Setting up libboost-serialization1.34.1 (1.34.1-15ubuntu3) ...

Setting up barry-util (0.16-0git2009083047) ...

Setting up barrybackup-gui (0.16-0git2009083047) ...

Setting up libopensync0 (0.22-2build1) ...

Setting up multisync-tools (0.92.0~svn355-1) ...
Setting up opensync-plugin-barry (0.16-0git2009083047) ...
Setting up opensync-plugin-evolution (0.22-2ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by pvicc on 2009-09-17
Thanks. After installing the package once again, i am able to sync my BB8900 with evolution contacts. But Calendar sync error. I could not sync calendar.

Is there any gui or everytime i have to go to the directory and type ./syncit.

Thanks in advance

PV

---

### Post by Larissa on 2009-12-05
Hi Darkwing,


Do you happen to know how it's possible to sync with korganizer // kaddressbook in karmic?

If i use barry-sync and kdepim-sync together I get the errors below, though the file is in place and writable.

The error even shows when I disable address-syncing.

```

$ msynctool --addgroup BBKDE
$ msynctool --addmember BBKDE barry-sync
$ msynctool --addmember BBKDE kdepim-sync
$ msynctool --configure BBKDE 2
This plugin has no options and does not need to be configured
$ msynctool --configure BBKDE 1
$ msynctool --sync BBKDE
Synchronizing group "BBKDE"
Member 1 of type barry-sync just connected
Member 2 of type kdepim-sync had an error while connecting: Unable to lock addressbook for writing.
Member 1 of type barry-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

```

Maybe if that doesn't work ... is there any workaround using Akonadi? Or some way to sync online without the need to set up a server oneself?
(but not Google Calendar please)


Thank you,
Larissa

---

