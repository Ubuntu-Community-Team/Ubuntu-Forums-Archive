---
title: "[Ubuntu] Trying to install 32 bit program in 64 bit Ubuntu"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by ReSoL603 on 2014-06-10
I am running Ubuntu 14.04 on a 64 bit machine. I am trying to install this program [http://www.ecmtuning.com/downloads/install/ecmlink_3_27_92_full.sh](http://www.ecmtuning.com/downloads/install/ecmlink_3_27_92_full.sh) which will not install on a 64 bit system. I have searched for tips on installing 32 bit programs on 64 bit Ubuntu, but I am not coming to a conclusion. This is what I am doing and how I got here:

```
synical@synical-LT41P:~$ sudo apt-get install j2sdk1.4
[sudo] password for synical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package j2sdk1.4
E: Couldn't find any package by regex 'j2sdk1.4'
synical@synical-LT41P:~$ '/home/synical/Downloads/ecmlink_3_27_92_full.sh' 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
*******************************************************************
You can also run this application in console mode without
access to an X server by passing the argument -c
*******************************************************************

```

I tried 

```
synical@synical-LT41P:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0

E: Package 'ia32-libs' has no installation candidate
synical@synical-LT41P:~$ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0Reading package lists... Done
Building dependency tree       
Reading state information... Done
lib32bz2-1.0 is already the newest version.
lib32ncurses5 is already the newest version.
lib32z1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.
```

Since I've already installed the packages.. 

When I try to install using -c argument, I get this:

```
synical@synical-LT41P:~$ '/home/synical/Downloads/ecmlink_3_27_92_full.sh'  -c
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
This will install ECMLink on your computer.
OK [o, Enter], Cancel [c]

Where should ECMLink be installed?
[/home/synical/ECMLink]

Create symlinks?
Yes [y, Enter], No [n]

Select the folder where you would like ECMLink to create symlinks, then click Next.
[/usr/local/bin]

Create a Quick Launch icon?
Yes [y, Enter], No [n]

Create a desktop icon?
Yes [y, Enter], No [n]

Clear preferences?
Yes [y], No [n, Enter]

Extracting files...
Downloading ...
Extracting files...
   /
   ecmlink/
   ecmlink/datalogs/
   ecmlink/datalogs/sample-pull-e316g-gm35-street.elg
   ecmlink/datalogs/sample-pull-e316g-sd-roadcourse.elg
   ecmlink/firmware/
   ecmlink/resources/
   ecmlink/resources/com/
   ecmlink/resources/com/ecmtuning/
   ecmlink/resources/com/ecmtuning/ecmlink/
   ecmlink/resources/com/ecmtuning/ecmlink/view/
   ecmlink/resources/com/ecmtuning/ecmlink/view/ecmlink/
   ecmlink/resources/com/ecmtuning/ecmlink/view/main/
   ecmlink/resources/com/ecmtuning/ecmlink/view/mitsu/
   ecmlink/resources/data/
   ecmlink/resources/records/
   ecmlink/settings/
   .install4j/
   .install4j/ecmlink.png
   .install4j/s_bd23kg.png
   .install4j/uninstall.png
   ecmlink
   ecmlink.jar
   ecmlinkhelp.jar
   libs/
   libs/animation.jar
   libs/apple-extensions.jar
   libs/binding.jar
   libs/forms.jar
   libs/foxtrot.jar
   libs/jhall.jar
   libs/jspWin.dll
   libs/l2fprod-common-fontchooser.jar
   libs/libjspLux86.so.4.7
   libs/libjspMacOSX.jnilib
   libs/librxtxSerial-osx10.4.jnilib
   libs/librxtxSerial-osx10.6.jnilib
   libs/librxtxSerial.so
   libs/looks.jar
   libs/RXTXcomm.jar
   libs/serialio.jar
   libs/uif-extras.jar
   libs/uif.jar
   libs/validation.jar
   logging.properties
   resources/
   resources/com/
   resources/com/ecmtuning/
   resources/com/ecmtuning/ecmlink/
   resources/com/ecmtuning/ecmlink/view/
   resources/com/ecmtuning/ecmlink/view/ecmlink/
   resources/com/ecmtuning/ecmlink/view/ecmlink/Action.properties
   resources/com/ecmtuning/ecmlink/view/ecmlink/Resource.properties
   resources/com/ecmtuning/ecmlink/view/main/
   resources/com/ecmtuning/ecmlink/view/main/Action.properties
   resources/com/ecmtuning/ecmlink/view/main/Resource.properties
   resources/com/ecmtuning/ecmlink/view/mitsu/
   resources/com/ecmtuning/ecmlink/view/mitsu/Action.properties
   resources/com/ecmtuning/ecmlink/view/mitsu/Resource.properties
   uninstall
Run ECMLink?
Yes [y, Enter], No [n]

Finishing installation...

```

Which seems like it installs, but when I try to open it, simply nothing happens. I am stuck and I need this application to run since I paid over $800 for the tuning hardware. There is absolutely no alternative, I need this to run. Any help in getting this running will be greatly appreciated.

---

### Post by mastablasta on 2014-06-10
do you have the necessary 32bit libraries installed?

---

### Post by ReSoL603 on 2014-06-10
I installed > lib32z1 lib32ncurses5 lib32bz2-1.0 I'm not sure what else I'd need.

---

### Post by mastablasta on 2014-06-10
have you checked these options? : [https://help.ubuntu.com/community/32bit_and_64bit#How_to_Make_32-bit_Applications_Work_on_a_64-bit_Operating_System](https://help.ubuntu.com/community/32bit_and_64bit#How_to_Make_32-bit_Applications_Work_on_a_64-bit_Operating_System)


sorry i don't know your applicaiton, but applications that have 32bit only verison and i tried on 64bit have caused me no issues.

i am not sure why that one 32bit package went out and was replaced with multiple ones but have a look here (apparently you need to install all that end with i386):
[http://askubuntu.com/questions/363878/how-to-install-32-bit-matlab-in-ubuntu-64-bit/363879#363879](http://askubuntu.com/questions/363878/how-to-install-32-bit-matlab-in-ubuntu-64-bit/363879#363879)

if oyu ask me they should make a meta package that pulls all you need (and maybe a bit more) in. let others know if it worked.

---

