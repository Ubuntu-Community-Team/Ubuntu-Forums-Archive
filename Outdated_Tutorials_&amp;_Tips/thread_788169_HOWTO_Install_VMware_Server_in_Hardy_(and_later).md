---
title: "HOWTO: Install VMware Server in Hardy (and later)"
date: 2008-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by altonbr on 2008-05-09
[CENTER][SIZE=6][COLOR=DarkRed]**_VMWARE SERVER AND UBUNTU HARDY (8.04)_**[/COLOR][/SIZE]

[SIZE=2](by running a script)[/SIZE]
[/CENTER]
[SIZE=4][B][U]
PREAMBLE[/U][/B][/SIZE]
[SIZE=4]_Previous Tutorial (VMware Player)_[/SIZE]
[My previous tutorial for VMware Player]("http://ubuntuforums.org/showthread.php?t=342631") *(January 20th, 2007 to May 5th, 2007)*
Feel free to look at it as it has pretty screenshots. It was used for Dapper, Edgy and Feisty, but I stopped updating it (and people stopped using it) because I found VMware Server a far superior product (and much easier to configure).

[SIZE=4]_Why am a starting a new tutorial?_[/SIZE]
With every release of Ubuntu and VMware Server, something always changes (annoyingly). At one time, it was even included in the repositories but that is no longer the case. By compiling the program however, you have more control to customize every aspect of the install and disable any unneeded services (such as NAT and host-only drivers).

[SIZE=4]_What does this tutorial deal with?_[/SIZE]
This tutorial/script deals with installing [VMware Server]("http://en.wikipedia.org/wiki/VMware_Server") (1.0.5) in [Ubuntu Hardy]("http://releases.ubuntu.com/hardy/") (8.04).


[SIZE=4]**_WHAT IS VMWARE SERVER?_**[/SIZE]
VMware Server allows you to run multiple operating systems on one computer, for free.


[SIZE=4]_**WHY USE VMWARE SERVER?**_[/SIZE]
[SIZE=4]_Servers_[/SIZE]
I personally use it for separation between my desktop and my personal server. I don't want server services running on my desktop (mail, web, mysql, php, etc.) as it is a security vulnerability. This enables to me to separate them virtually with less of security risk. If someone was to hack into my server, they would be unaware of the host (my desktop).

[SIZE=4]_Test bed_[/SIZE]
In the past I have also used it to install Windows 2000, Windows XP, test future versions of Ubuntu and other operating systems. Use it to play around and have fun!


[SIZE=4][B][U]KNOWN LIMITATIONS OF VMWARE SERVER
[/U][/B][/SIZE]
[LIST]
[*][USB 2.0]("http://en.wikipedia.org/wiki/Universal_Serial_Bus") support (coming in VMware Server 2.0). This means your printer may or may not work on the guest/virtual operating system
[*][Firewire]("http://en.wikipedia.org/wiki/IEEE_1394_interface")
[*][Limited 3D acceleration]("http://en.wikipedia.org/wiki/3D_computer_graphics") (that means no graphically intense programs can run smoothly -- such as games)
[*]VMware Server is proprietary, but free. If you're looking for open-source alternatives, see [Xen]("http://en.wikipedia.org/wiki/Xen") or [VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox")
[/LIST]

[SIZE=4]**_INSTALLING VMWARE SERVER_**[/SIZE]
[SIZE=4]_VMware Serial Number_[/SIZE]
Get it from here: [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

[SIZE=4]_install_vmware.sh_[/SIZE] (the script)
**Updated:** *2008-06-08 (June 8th)*

[U]Quick Note
[/U]I have detection for the .tar.gz files required for VMware and the any-any update to install, so if you already have them downloaded, sit them in the same folder as this script and it will skip the unnecessary download.

_Saving_
Save the script below as *install_vmware.sh* in your home directory.

```
#!/bin/bash
#!/bin/sh


# Installs VMware server and applies the any-any patch for Ubuntu 8.04
# install_vmware.sh
# Copyright (C) 2008  Brett Alton

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.


# ----- THANKS -----
# Kokopelli (http://ubuntuforums.org/showpost.php?p=4357442&postcount=10)
#	base code
# tamoneya (http://ubuntuforums.org/showthread.php?t=788060)
#	x86_64 detection
# Illuvator (http://ubuntuforums.org/showthread.php?t=337040)
#	VMware install problems
# http://phaq.phunsites.net/2006/03/17/installing-vmware-server-on-debian-sarge/
#	VMware Server dependencies
# p388l3s (http://ubuntuforums.org/showpost.php?p=4989259&postcount=23)
#	bug reporting
# Kokopelli (http://ubuntuforums.org/showpost.php?p=4877845&postcount=16)
#	64-bit library fix


# ----- FEATURES -----
#	* Installs VMware Server 1.0.6
#	* Installs VMware any any update 116
#	* Fixes issues for: VMware libraries, 64-bit libraries and USB support
#	* Does not require the Internet if VMware server and any-any patch are already downloaded
#	* Cleans up any downloaded files
#	* The script can successfully install over an existing installation so the user doesn't have to go through any special procedures besides running this script


# ----- CHANGELOG -----
# 2008-06-08
#	* Removed output supression for wget
#	* Changed spaces to tabs (how was it even spaces in the first place?)
# 	* Reverted back to VMware-any-any-update-116 downloading from uruz.org
# 2008-06-02
#	* Updated VMware Server to 1.0.6
#	* Kept VMware-any-any-update at 116 until I read more about 117, 117(2) and 117a
#	* Now downloading VMware-any-any-update-116 from vmkernelnewbies.googlegroups.com
# 2008-05-18
#	* Bug fixes
# 2008-05-14
#	* Created a prompt to install GUI libraries when X isn't present (thanks kezarjg!)
#	* Created separate library install list for 64-bit users
#	* Added -y flag to aptitude (thanks oraldlight!) -- or should I remove "2>&1 > /dev/null" ???
# 2008-05-10
#	* Destroyed stdout (and removed verbosity on 'tar') for a cleaner looking script
#	* Added more exit status checks
#	* Added detection for files before downloading
#	* Removed installing shortcut to "Applications > System Tools > VMware Server"
# 2008-05-09
#	* Initial release


# ----- TODO -----
#	* Ubuntu 8.04 detection (?)
#	* Allow arguments (./install_vmware.sh $1 $2) to allow running just the any-any patch (such as after a kernel update)
#	* Create fall-back download paths in case the hard-coded ones fail
#	* Add support for VMware MUI (http://download3.vmware.com/software/vmserver/VMware-mui-1.0.5-80187.tar.gz)
#	* Add support for VMware Tools
#	* Create a log?
#	* Don't hard-code VMware and any-any version numbers (how?)
#	* Add md5/sha1 download support
#	* Add /etc/vmware/ssl/ fix (but where and how to implement?)


# ----- FUNCTIONS -----
function print_info()
{
	echo " -- $1, continuing..."
}

function print_warn()
{
	echo " ** $1, continuing..."
}

function force_exit()
{
	echo " !! $2, exiting..."
	cleanup
	exit $1
}

function safe_exit()
{
	echo " -- Safely exiting..."
	cleanup
	exit 0
}

function cleanup()
{
	cd $INIT_DIR
	print_info 'Removing downloaded and extracted files'

	# Delete VMware tarball?
	if [ $DELETE_VMWARE_TARBALL -eq 1 ]; then
		rm -f $VMWARE_TARBALL
	fi

	# Delete any-any tarball?
	if [ $DELETE_ANYANY_TARBALL -eq 1 ]; then
		rm -f $ANYANY_TARBALL
	fi

	# Delete extracted directories
	rm -rf $VMWARE_DIR $ANYANY_DIR
}


# ----- VARIABLES -----
VMWARE_URL='http://download3.vmware.com/software/vmserver/'
#VMWARE_TARBALL='VMware-server-1.0.5-80187.tar.gz'
VMWARE_TARBALL='VMware-server-1.0.6-91891.tar.gz'
VMWARE_DIR='vmware-server-distrib'
VMWARE_PATH=$VMWARE_URL$VMWARE_TARBALL

# want to upgrade to http://groups.google.com/group/vmkernelnewbies/files
ANYANY_URL='http://uruz.org/files/'
ANYANY_TARBALL='vmware-any-any-update-116.tgz'
ANYANY_DIR='vmware-any-any-update116'
ANYANY_PATH=$ANYANY_URL$ANYANY_TARBALL

ARCH=`uname -m` # x86_64 or i686
if [ "$ARCH" == "x86_64" ]; then
	IS_64=1 # 64-bit
else
	IS_64=0 # non 64-bit
fi

INIT_DIR=`pwd` # current directory

DELETE_VMWARE_TARBALL=1
DELETE_ANYANY_TARBALL=1


# ----- INIT -----
# Updating Ubuntu
print_info 'Updating Ubuntu'
sudo aptitude update 2>&1 > /dev/null

# Check if 'aptitude update' failed
if [ $? -ne 0 ]; then
	print_warn 'Could not update Ubuntu. The installation may not working'
fi

print_info 'Upgrading Ubuntu'
sudo aptitude safe-upgrade

# Check if 'aptitude upgrade' failed
if [ $? -ne 0 ]; then
	print_warn 'Could not upgrade Ubuntu. The installation may not work'
fi


# ----- LIBRARIES -----
# Installing essential libraries
if [ $IS_64 -eq 1 ]; then
	print_info 'Installing essential libraries for 64-bit architecture'
	ESS_LIBS="xinetd build-essential linux-headers-`uname -r` ia32-libs libc6-i386" # 64-bit
else
	print_info 'Installing essential libraries for 32-bit architecture'
	ESS_LIBS="xinetd build-essential linux-headers-`uname -r`" # non 64-bit
fi
sudo aptitude -y install $ESS_LIBS 2>&1 > /dev/null

# Check if 'aptitude -y install' failed
if [ $? -ne 0 ]; then
	force_exit 1 'Could not install essential libraries'
fi


# ----- GUI CHECK -----
print_info 'Checking for essential GUI libraries'
NEED_GUI_LIBS=0
GUI_LIBS="libx11-6
libxtst6
libxt6
libxrender1
libxi6"
GUI_LIBS_FLAT='libx11-6 libxtst6 libxt6 libxrender1 libxi6'
for F in $GUI_LIBS; do
	if [ $NEED_GUI_LIBS -eq 0 ]; then
		INSTALLED=`dpkg --get-selections | grep $F`
		if [ "$INSTALLED" == "" ]; then
			NEED_GUI_LIBS=1
		fi
	fi
done

if [ $NEED_GUI_LIBS -eq 1 ]; then
	echo ' ?? Essential GUI libraries need to be installed, is this OK? [y/n]'
	read -n1 RETURN
	if [ $RETURN == 'y' ] || [ $RETURN == 'Y' ]; then
		print_info 'Installing extra GUI libraries'
		sudo aptitude -y install $GUI_LIBS_FLAT 2>&1 > /dev/null
	else
		force_exit 1 'Refused to install extra GUI libraries'
	fi
else
	print_info 'Essential GUI libraries already installed'
fi


# ----- VMWARE SERVER -----
# Download VMware server
if [ -f $VMWARE_TARBALL ]; then
	print_info 'VMware already present. Skipping download'
	DELETE_VMWARE_TARBALL=0 # do not delete if the user put it there
else
	print_info 'Downloading VMware server. This may take some time'
	wget $VMWARE_PATH
fi

# Check if wget failed
if [ $? -ne 0 ]; then
	force_exit 1 "Could not download $VMWARE_TARBALL"
fi

# Extract VMware server
if [ -e $VMWARE_DIR ]; then # if the name has already been taken (either file, directory, symbolic link, etc.)
	print_info 'Extracted directory detected. Deleting for the sake of security'
	rm -rf $VMWARE_DIR
fi
print_info 'Extracting VMware server'
tar -xzf $VMWARE_TARBALL

# Check if tar failed
if [ $? -ne 0 ]; then
	force_exit 1 "Could not extract $VMWARE_TARBALL. Does it exist or is it corrupt?"
fi

# Change directory
if [ -d $VMWARE_DIR ]; then
	cd $VMWARE_DIR
else
	force_exit 1 "Could not find $VMWARE_DIR"
fi

# Install VMware Server
if [ -f vmware-install.pl ]; then
	print_info 'Installing VMware server'
	sudo ./vmware-install.pl
else
	force_exit 1 'vmware-install.pl does not exist. VMware server is possibly broken'
fi


# ----- ANY ANY UPDATE -----
# Change to initial directory
cd $INIT_DIR

# Download vmware-any-any-update
if [ -f $ANYANY_TARBALL ]; then
	print_info 'any-any update already present. Skipping download'
	DELETE_ANYANY_TARBALL=0 # do not delete if the user put it their
else
	print_info 'Downloading the any-any update. This may take some time'
	wget $ANYANY_PATH
fi

# Check if wget failed
if [ $? -ne 0 ]; then
	force_exit 1 "Could not download $ANYANY_TARBALL"
fi

# Extract vmware-any-any-update
if [ -e $ANYANY_DIR ]; then # if the name has already been taken (either file, directory, symbolic link, etc.)
	print_info 'Extracted directory detected. Deleting for the sake of security'
	rm -rf $ANYANY_DIR
fi
print_info 'Extracting the any-any update'
tar -xzf $ANYANY_TARBALL

# Check if tar failed
if [ $? -ne 0 ]; then
	force_exit 1 "Could not extract $VMWARE_TARBALL. Does it exist or is it corrupt?"
fi

# Change directory
if [ -d $ANYANY_DIR ]; then
	cd $ANYANY_DIR
else
	force_exit 1 "Could not find $ANYANY_DIR"
fi

# Run vmware-any-any-update
if [ -f runme.pl ]; then
	print_info 'Running the any-any update'
	sudo ./runme.pl	
else
	force_exit 1 'runme.pl does not exist. any-any update is possibly broken'
fi


# ----- LIBRARY FIX -----
print_info 'Fixing library issues'
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0


# ----- 64-BIT FIX -----
# see: http://ubuntuforums.org/showpost.php?p=4877845&postcount=16
if [ $IS_64 -eq 1 ]; then
	print_info '64-bit computer detected. Running 64-bit VMware library fix'
	sudo ln -s /usr/lib32 /usr/l32
	sudo sed -i -e 's:usr/lib/:usr/l32/:g'  /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
	sudo sed -i -e 's:usr/lib/:usr/l32/:g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9
fi


# ----- USB FIX -----
USB_FIX_PRESENT=`grep '/proc/bus/usb' /etc/fstab`
if [ "$USB_FIX_PRESENT" == "" ]; then
	print_info 'Adding USB support to /etc/fstab'
	echo 'none /proc/bus/usb usbfs devgid=46,devmode=664 0 0' | sudo tee --append /etc/fstab
else
	print_info 'USB fix already present'
fi


# ----- EXIT -----
# Everything ran fine, exit safely
safe_exit
```_Running_
```
chmod a+x ./install_vmware.sh && ./install_vmware.sh
```[SIZE=4]_Notes:_[/SIZE]
You can hit 'enter' for almost all VMware server paths as the defaults work just fine. However, there are some exceptions:

_"/usr/bin/vmware-config.pl" question:_
When you see this for the first time
> Before running VMware Server for the first time, you need to configure it by invoking the following command: "/usr/bin/vmware-config.pl". Do you want this program to invoke the command for you now? [yes]Type **[COLOR=Red]no[/COLOR]**. When it appears the second time -- from running the any-any script -- type [COLOR=Green]**yes**[/COLOR]

_Networking_
I usually like to have my virtual machines run on the same network as my host so they get IP addresses like (192.168.1.100). If you want that, enable networking but disable NAT and host-only like so:
> Do you want networking for your virtual machines? (yes/no/help) [yes] [COLOR=Green]**yes**[/COLOR]

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] **[COLOR=Red]no[/COLOR]**

Do you want to be able to use host-only networking in your virtual machines? 
[no] **[COLOR=Red]no[/COLOR]**

---

### Post by TwiceOver on 2008-05-10
Thanks!  Worked great.  Now I can dump VirtualBox.

---

### Post by hlarsick on 2008-05-10
WOW what a awesome post. All I did was copy the script and ran it, and it got everything it needed and now my VMware is back

Thanks :guitar:

---

### Post by altonbr on 2008-05-10
Excellent!

Do either of you happen to be using 64-bit Ubuntu? I have a line in their to make a fix for 64-bit Ubuntu, but sadly, I can't test it.

Thank you again for trying my script :)

---

### Post by altonbr on 2008-05-10
**Updated.**

It now:
[LIST]
[*]Looks prettier
[*]Does more status checks to make sure everything is running smoothly
[*]Added detection for already downloaded tarballs (so the script doesn't download them for you)
[*]General bug fixes... wait, what bugs?
[/LIST]

---

### Post by kezarjg on 2008-05-12
For my configuration (minimalist server install), I needed some additional libraries;

libx11-6
libx11-dev
libxtst6
libxt6
libxrender1

You may want to consider updating the script to check for these files and add if necessary.

Thanks

---

### Post by altonbr on 2008-05-12
> **kezarjg said:**
> For my configuration (minimalist server install), I needed some additional libraries;

libx11-6
libx11-dev
libxtst6
libxt6
libxrender1

You may want to consider updating the script to check for these files and add if necessary.

Thanks

Thank you, I'll look into it. My script so far only automates the task of setting up VMware, the any-any update and a couple other fixes, its not (yet) meant to make sure VMware WILL install. It is a good idea though, so thank you again.

I'll setup a Ubuntu server in VMware and test my script there.

---

### Post by jharrop on 2008-05-12
> **altonbr said:**
> Excellent!

Do either of you happen to be using 64-bit Ubuntu? I have a line in their to make a fix for 64-bit Ubuntu, but sadly, I can't test it.

Thank you again for trying my script :)

Thanks for the script..

I've just run it (as normal user) on a freshly installed 64-bit Hardy. The script finishes with:

```
The configuration of VMware Server 1.0.5 build-80187 for Linux for this running
kernel completed successfully.

 -- Fixing library issues, continuing...
 -- 64-bit computer detected. Running 64-bit VMware library fix, continuing...
 -- Adding USB support to /etc/fstab, continuing...
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...
```

Vmware wasn't running properly, so i stopped it, then:

```
$ sudo /etc/init.d/vmware start
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.
```

After running vmware-config.pl again, the services start properly:

```
$ sudo /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                      done
   Virtual ethernet                                             done
   Bridged networking on /dev/vmnet0                            done

```

But VMware Server Console won't start.  There's nothing in the logs to indicate the problem.

I can't look into this more right now .. I'll have another look on the weekend and report back.  I have had VMware Server running on another Hardy before, so hopefully it'll be easy enough to get running.

---

### Post by altonbr on 2008-05-13
@ jharrop:

I found some threads that suggested a couple extra libraries for 64-bit users. I will update it today for you to test again. You should be able to run the script a second time with no problems.

---

### Post by oraldlight on 2008-05-14
Fresh 8.04 x86_64 Ubuntu install. All updates ran via Update manager. D/L'd VMware-server-1.0.5.80187.tgz, vmware-any-any-update-116.tgz, and created the isntall-vmware.sh script, in /home/jkein.

Open Terminal, type 
```
jklein@jk-laptop:~$ sudo /bin/bash install-vmware.sh 
[sudo] password for jklein: 
 -- Updating Ubuntu, continuing...
 -- Upgrading Ubuntu, continuing...
 -- Installing necessary programs, continuing...

```

and that's all it did. For better than 30 minutes...

I tried launching again and same results...just sits at installing.

Rebooted, tried with and without 'sudo', it's just not completing. I hesitate to go comment out parts of your script for fear of uncertainty (I don't program, but see the logic/flow of events)

Suggestions?
====================
Manually created the kernel and reran installer - finished installing. 
I ended up manually running VMware isntaller, any-any installer and got it working. DOn't understand why I manually had to, but working now.

---

### Post by altonbr on 2008-05-14
> **oraldlight said:**
> Fresh 8.04 x86_64 Ubuntu install. All updates ran via Update manager. D/L'd VMware-server-1.0.5.80187.tgz, vmware-any-any-update-116.tgz, and created the isntall-vmware.sh script, in /home/jkein.

Open Terminal, type 
```
jklein@jk-laptop:~$ sudo /bin/bash install-vmware.sh 
[sudo] password for jklein: 
 -- Updating Ubuntu, continuing...
 -- Upgrading Ubuntu, continuing...
 -- Installing necessary programs, continuing...

```

and that's all it did. For better than 30 minutes...

I tried launching again and same results...just sits at installing.

Rebooted, tried with and without 'sudo', it's just not completing. I hesitate to go comment out parts of your script for fear of uncertainty (I don't program, but see the logic/flow of events)

Suggestions?

All that line is doing is running
```
sudo aptitude install build-essential linux-headers-`uname -r` xinetd
```

and then hiding the output. Try running that without running the script and see what happens. It sounds like your country's Ubuntu server may be down (ie: ca.archive.ubuntu.com).

---

### Post by altonbr on 2008-05-14
**Updated.**
Features:
[LIST]
[*]Created a prompt to install GUI libraries when X isn't present (thanks kezarjg!)
[*]Created separate library install list for 64-bit users
[*]Added -y flag to aptitude (thanks oraldlight!)
[/LIST]

Should be pretty unbreakable now. Keep reporting any bugs :)

---

### Post by Kosmi4 on 2008-05-16
thanks a lot.. your help is the reason i love Ubuntu..
worked great..:)

---

### Post by MystaMax on 2008-05-16
Hello, I used your script to install vmware server on ubuntu 8.04 64-bit, and when I type "vmware" @ the command line, I get back:

vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command:

/usr/bin/vmware-config.pl.


I've ran that script three times now. After each time, I try "vmware" and get the same error. Any ideas? I'm probably missing a dependency.

---

### Post by altonbr on 2008-05-17
> **MystaMax said:**
> Hello, I used your script to install vmware server on ubuntu 8.04 64-bit, and when I type "vmware" @ the command line, I get back:

vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command:

/usr/bin/vmware-config.pl.


I've ran that script three times now. After each time, I try "vmware" and get the same error. Any ideas? I'm probably missing a dependency.

What's the output at the end of my script? 

Type 'no' the first time it asks you to run '/usr/bin/vmware-config.pl' (which is in the VMware install script) and then the second time it asks you to run '/usr/bin/vmware-config.pl' (which is in the VMware-any-any patch), type 'yes'. That should compile VMware Server properly.

---

### Post by p388l3s on 2008-05-18
> vmware is installed, but it has not been (correctly) configured for this system. To (re-)configure it, invoke the following command:

/usr/bin/vmware-config.pl.


I've ran that script three times now. After each time, I try "vmware" and get the same error. Any ideas? I'm probably missing a dependency.

I got the same error on 64bit ubuntu wheb running the script, the answer was to install xinetd and then run:

```
sudo /usr/bin/vmware-config.pl
```

the install ran smooth after installing xinetd, BUT I get this error now when running vmware from a shell:

```
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7c19076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

```

Any help or insight would be appreciated.

---

### Post by p388l3s on 2008-05-18
OK,

So my other issue was resolved using this command in a shell:

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

as soon as I had run this command the errors went away.

I now have a complete working install of vmware server, so my suggestion to **altonbr** is on 64bit installs if you could make sure xinetd and the above mentioned code are run in your script and it should work all the time, and thanks for such great work in the first place. It's very much appreciated.

---

### Post by altonbr on 2008-05-18
@p388l3s

There's a thread showing the exact same problem but no help has come about: [http://ubuntuforums.org/showthread.php?p=4976397](http://ubuntuforums.org/showthread.php?p=4976397)

What's your output of:
```
$ locate libgobject-2.0.so
```

Mine is:
> /usr/lib/libgobject-2.0.so.0
/usr/lib/libgobject-2.0.so.0.1600.3
/usr/lib/vmware/lib/libgobject-2.0.so.0
/usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0

---

### Post by altonbr on 2008-05-18
> **p388l3s said:**
> OK,

So my other issue was resolved using this command in a shell:

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

as soon as I had run this command the errors went away.

I now have a complete working install of vmware server, so my suggestion to **altonbr** is on 64bit installs if you could make sure xinetd and the above mentioned code are run in your script and it should work all the time, and thanks for such great work in the first place. It's very much appreciated.

Well the line ```
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
``` is already in the script. Why **l3232**?

That xinetd problem is completely my fault. It got lost in translation between my last script and my current so I've added it to my current script above.

I'll be issuing an update once I test your fix.

---

### Post by MystaMax on 2008-05-18
[quote=altonbr]What's the output at the end of my script? 

Type 'no' the first time it asks you to run '/usr/bin/vmware-config.pl' (which is in the VMware install script) and then the second time it asks you to run '/usr/bin/vmware-config.pl' (which is in the VMware-any-any patch), type 'yes'. That should compile VMware Server properly.[/quote]

Unfortunately, I was pressed for time and install vmware server manually. i hope to test your script sometime next week, to see if I can recreate the problem.

Thanks.

---

### Post by edwindgarcia on 2008-05-18
Great script but i have a problem, everything goes ok, still i try to run vmware console....

Here is the error

[http://pastebin.com/f1f9e361b](http://pastebin.com/f1f9e361b)

i dont know what to do... thanks for help

---

### Post by edwindgarcia on 2008-05-18
hmmm...

Using this line:

> sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders

I solved the problem... thanks to everyone

---

### Post by p388l3s on 2008-05-18
**l3232**?

I have no idea!!! ;-) sry, when I looked at the whole list of errors I was getting it showed l3232 which doesn't exist on my machine, so I did a search on this forum and found that particular fix mentioned tried it an et voila! working install of vmware.

As for xinetd no worries, I'm glad you knew to fix it, otherwise not a big deal to install manually.

Actually this might be useful reading for you:

[http://ubuntuforums.org/showthread.php?t=779934&highlight=l3232]("http://ubuntuforums.org/showthread.php?t=779934&highlight=l3232")

Seems the 2 lines you have in there for 64bit might be superfluous now.

>  Re: How to VMWare in Ubuntu 8.04
Quote:
Originally Posted by fjgaude View Post
For 64 bit users there is one additional step in order to allow vmware console to launch:

Code:

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.9

At least was necessary for my 64-bit installs.

Thanks for trying to put everything in one place, Bodhi.zazen!

frank
I would be cautious of running the sed commands in Hardy final. It was needed during the Betas, but the loader was fixed to point to lib32 instead of lib at or near the final release. If you run the sed commands on a properly updated libgtk2.0-0.loaders, the loader will point to "l3232" which is incorrect.

Thanks again.

---

### Post by p388l3s on 2008-05-18
> **altonbr said:**
> @p388l3s

There's a thread showing the exact same problem but no help has come about: [http://ubuntuforums.org/showthread.php?p=4976397](http://ubuntuforums.org/showthread.php?p=4976397)

What's your output of:
```
$ locate libgobject-2.0.so
```

in answer to your question:

```

locate libgobject-2.0.so

/usr/lib/libgobject-2.0.so.0
/usr/lib/libgobject-2.0.so.0.1600.3

```

---

### Post by altonbr on 2008-05-18
I implemented the xinetd problem and changed my 64-bit library fix over to Kokopelli's code ([http://ubuntuforums.org/showpost.php?p=4877845&postcount=16](http://ubuntuforums.org/showpost.php?p=4877845&postcount=16)).

Hope that fixes everyone's 64-bit problems :S

---

### Post by bitumen on 2008-05-19
Ubuntu 8.04 server with ubuntu-desktop install no top 

Script Worked out of the box 

(Manual attempt to install and configure FAILED due to downloading wrong files)
The script pickup where i failed 

EXECELENT WORK

---

### Post by jharrop on 2008-05-19
> **altonbr said:**
> I implemented the xinetd problem and changed my 64-bit library fix over to Kokopelli's code ([http://ubuntuforums.org/showpost.php?p=4877845&postcount=16](http://ubuntuforums.org/showpost.php?p=4877845&postcount=16)).

Hope that fixes everyone's 64-bit problems :S

Tried running the script again on my X86_64.

It seemed to freeze at 

```
 -- Upgrading Ubuntu, continuing...
```

so I killed it, and installed 38 updates using Update Manager (configuring openssh-server required user interaction).

Ran your script again, and VMware Server is now working.

Thanks!

---

### Post by smit0737 on 2008-05-19
Worked great first time on a fresh install of 64b Hardy. Thanks!

---

### Post by altonbr on 2008-05-20
@jharrop
Hmm, thanks for letting me know. I'll look into it!

@everyone
I'm glad it worked out for all of you! Thanks for trying my script!

---

### Post by shadowtroopers on 2008-05-21
hi i try to install vmware as instructed and here are the situation after i accept license and agreement:

Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:48:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config3/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

what should i do next?

---

### Post by altonbr on 2008-05-21
@shadowtroopers
You could try enabling "System > Administration > Software Sources > Updates > (hardy-proposed)" to get a slightly newer kernel and try again.

I wouldn't normally recommend doing so, but then again I've never seen VMware fail on a 2.6.24-16 kernel.

You're running Ubuntu Hardy will all of the upgrades I assume? Are you running 64-bit or 32-bit?

---

### Post by shadowtroopers on 2008-05-21
I'm running on 32bit..I'll try doing it one more time, hope this would work.
Thanks.

---

### Post by shadowtroopers on 2008-05-21
Yup still get the same thing. I do enable hardy-proposed on my software source, but still got the same.

---

### Post by kbow on 2008-05-21
Very Nice Tutorial, worked great !!


Thanks !

---

### Post by altonbr on 2008-05-21
> **shadowtroopers said:**
> Yup still get the same thing. I do enable hardy-proposed on my software source, but still got the same.

Make sure to run ```
sudo aptitude update && sudo aptitude -y upgrade
``` and then try my script again.

---

### Post by neltnerb on 2008-05-22
Thanks for the script. It seemed to work great for installing, the modules installed without complaint on my up to date Hardy system.

However, actually running the program fails with the following error.

--

/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


I installed the software in /usr/local/bin (I don't like putting self-compiled stuff in /usr/bin), but I don't see how this could be causing the problem.  All the files they reference seem to exist, so I'm not sure what to make of these errors.

Thanks!

---

### Post by altonbr on 2008-05-22
> **neltnerb said:**
> Thanks for the script. It seemed to work great for installing, the modules installed without complaint on my up to date Hardy system.

However, actually running the program fails with the following error.

--

/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/local/lib/vmware/bin/vmware: /usr/local/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


I installed the software in /usr/local/bin (I don't like putting self-compiled stuff in /usr/bin), but I don't see how this could be causing the problem.  All the files they reference seem to exist, so I'm not sure what to make of these errors.

Thanks!

On the Gentoo forums, they suggest simply deleting the file! ([http://bugs.gentoo.org/show_bug.cgi?id=217650](http://bugs.gentoo.org/show_bug.cgi?id=217650)). Make sure you back it up before you do however!

---

### Post by neltnerb on 2008-05-22
thanks, that did it.

weird issue.

---

### Post by maurizio.omissoni on 2008-05-25
Great, thank to your work i have finally a vmware-server on my hardy.

---

### Post by drifting on 2008-05-25
Typical, everyone else it works fine for, any ideas ?

Paul.


-- Upgrading Ubuntu, continuing...
 -- Installing essential libraries for 64-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
 -- Extracting VMware server, continuing...
 -- Installing VMware server, continuing...
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

 -- Downloading the any-any update. This may take some time, continuing...
 -- Extracting the any-any update, continuing...
 -- Running the any-any update, continuing...
Updating /usr/bin/vmware-config.pl ... corrupted
Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware-server/modules/source/vmmon.tar.

Execution aborted.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- 64-bit computer detected. Running 64-bit VMware library fix, continuing...
 -- Adding USB support to /etc/fstab, continuing...
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...
paul@vs:~$

---

### Post by graffiX on 2008-05-26
Hey Brett, your script looks like it's working really well for others.  I have not had success with it but would hope to soon.  I tried running it and all I got was stuck on Updating Ubuntu, despite having just updated before starting the script.  I have attached a screen of what's going on.  

My system is an upgrade from Gutsy, and has never had vmware on this install.

Any advice would be awesome.

Dave

---

### Post by graffiX on 2008-05-26
del

---

### Post by Ron@ld on 2008-05-27
I was looking for VMWare on Linux and found this topic.
Excellent, but is doesn't work for me.

I followed the steps mentioned in the first screen and run the script.

The following error occurs.

Does it sound familiar to anyone?

ronald@ronald-laptop:~$ chmod a+x ./install_vmware.sh && ./install_vmware.sh
 -- Updating Ubuntu, continuing...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: De volgende ondertekeningen konden niet geverifiëerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY 2EBC26B60C5A2783
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
 ** Could not update Ubuntu. The installation may not working, continuing...
 -- Upgrading Ubuntu, continuing...
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 ** Could not upgrade Ubuntu. The installation may not working, continuing...
 -- Installing essential libraries for 32-bit architecture, continuing...
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Kon vergrendeling /var/lib/dpkg/lock niet verkrijgen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 !! Could not install essential libraries, exiting...
 -- Removing downloaded and extracted files, continuing...


Cheers,

Ronald

---

### Post by Ron@ld on 2008-05-27
A reboot was the solution. :confused:

---

### Post by altonbr on 2008-05-27
> **graffiX said:**
> Hey Brett, your script looks like it's working really well for others.  I have not had success with it but would hope to soon.  I tried running it and all I got was stuck on Updating Ubuntu, despite having just updated before starting the script.  I have attached a screen of what's going on.  

My system is an upgrade from Gutsy, and has never had vmware on this install.

Any advice would be awesome.

Dave

I removed the line that hides the output for upgrading Ubuntu. If you want to copy the script above it should work.

The problem is, sometimes 'sudo aptitude upgrade' will ask for input, especially for unsigned repositories.

It should work now, but not look as 'pretty' as it will spew out the output.

> **Ron@ld said:**
> A reboot was the solution. :confused:

Yeah, those error messaging didn't look to good. Is it up and working now?

---

### Post by Ron@ld on 2008-05-27
Yes, vmware works fine.

The only thing I have to do is getting my images, created under windows, up and running.

I get a disk error, images runs from my /home dir.

---

### Post by altonbr on 2008-05-27
> **Ron@ld said:**
> Yes, vmware works fine.

The only thing I have to do is getting my images, created under windows, up and running.

I get a disk error, images runs from my /home dir.

Sorry, what do you mean images? Like .iso files? Or .jpg files?

Are you talking about mounting or transferring files between both operating systems?

---

### Post by Ron@ld on 2008-05-27
No, I meant the vmware images I already have created in a windows environment.

But, I working on it and the things I have had done today are running.
So, I think by the end of this week the problems are solved.

---

### Post by graffiX on 2008-05-28
altonbr, thank you so much!  It worked perfectly.  Turns out it wanted to remove an old kernel before continuing, and it was able to finish properly after that, and everthing works fine.  Runs my VMs just right.

What a great day!  Got MSOffice (grr) and VMWare to work on Ubuntu today!  Thanks a lot.

Dave

---

### Post by elbeano on 2008-05-28
This worked exactly as described and saved me a huge amount of work/time. Thanks for the script. I learned from following its logic and your instructions for use and will use this again.

---

### Post by Crash 0verride on 2008-05-28
Great Tutorial, I will test when I get home.

---

### Post by newstp812 on 2008-05-28
[QUOTE=drifting;5041735]Typical, everyone else it works fine for, any ideas ?

Paul.


-- Upgrading Ubuntu, continuing...
 -- Installing essential libraries for 64-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
 -- Extracting VMware server, continuing...
 -- Installing VMware server, continuing...
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Paul,

I also had this problem and decided to remove my previous VMWare version but you need to mark it for COMPLETE removal. Then run the script found here and follow the instructions. It should work now, at least it did for me.

Sue

---

### Post by BobCFC on 2008-05-28
Thanks it got it working on my 64bit host

---

### Post by mecatroid on 2008-05-29
altonbr, you are a master !

Thanks a lot for this script that was perfect for me.

I had already installed a VMWare server, but it wasn't running anymore due to recent changes (automatic update I guess ...).

I just ran the script, and it was back and running.

You are a Giant

BTW : Ubuntu 8.04 Desktop 32bits 2.6.24-17-generic #1 SMP i686 GNU/Linux running on AMD dual core

---

### Post by brianafischer on 2008-05-31
The script seemed to complete successfully without any errors, but when I click on the "VMWare Server Console" from the Applications menu, nothing appears.

When I try to run "vmware" or "sudo vmware" from a console I get the following:

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```


I am running x86 on Hardy (8.04) with kernel version 2..6.24-17-generic

Pastebin install log [here]("http://pastebin.com/f5c4538fc")

Please help!  I don't want to convert to using VirtualBox....

---

### Post by dether on 2008-05-31
> **newstp812 said:**
> 

I also had this problem and decided to remove my previous VMWare version but you need to mark it for COMPLETE removal. Then run the script found here and follow the instructions. It should work now, at least it did for me.



Sue,

thanks for pointing me in the right direction. Now I've got my VMWare Server back up and running on Hardy.

@altonbr:

Thank you for sharing this great script!

---

### Post by brianafischer on 2008-05-31
Well, I have solved my problem using [this]("http://ubuntuforums.org/showpost.php?p=4186741&postcount=7") thread.

1. Bridged networking on eth0 failed to start.
```

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Bridged networking on /dev/vmnet2                                   done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
```

```
sudo /etc/init.d/vmware restart
```


2. Config Prompt

Problem:
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```
Solution:
```
sudo mv /etc/vmware/not_configured /etc/vmware/not_configured_backup
```

---

### Post by altonbr on 2008-06-02
@everyone:
Thank you for all of your wonderful compliments!

@brianafischer:
I'll have to look into this issue, thank you. It seems to be the only issue that now comes up for people when running my script. I'll have to add some better detection in there, thank you.

---

### Post by altonbr on 2008-06-02
Just a note:

VMware Server 1.0.6
and,
VMware-any-any-patch-117a

are out, but I won't add them to my script until I've fully tested them.

---

### Post by Nikayah on 2008-06-03
I need a hand, your script worked BEAUTIFULLY except it wouldn't accept my serial number. So i just skipped that part. I went to enter it from the VMWare werver window and got an error (visible in the screenshot below) can you please give me a hand??

```
Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  9AH05-YDX6P-1E291-48Q15

The serial number 9AH05-YDX6P-1E291-48Q15 is invalid.

``` ^This is the error I get when running your helpful script

EDIT: Nevermind I fixed it! For anyone else who has this problem just go into terminal and type: ```
gksudo vmware
```then enter your serial number.
~Nikayah

---

### Post by Nxion on 2008-06-03
Best tutorial ever! Serious!. Thanks!

---

### Post by SuzuZaku on 2008-06-04
Mine keep saying >  -- Installing essential libraries for 32-bit architecture, continuing... And it just sits there doing nothing, what do I do/What's wrong?

---

### Post by dcstar on 2008-06-04
> **altonbr said:**
> Just a note:

VMware Server 1.0.6
and,
VMware-any-any-patch-117a

are out, but I won't add them to my script until I've fully tested them.

I have already used the 1.0.6 version with the existing any-any and it seems to work fine for me.

BTW, I removed the "-q" from the wget as I find it more valuable to see the big download running and know how long it has to go.

---

### Post by altonbr on 2008-06-04
> **SuzuZaku said:**
> Mine keep saying  And it just sits there doing nothing, what do I do/What's wrong?

Can you edit the script so that
```
sudo aptitude -y install $ESS_LIBS 2>&1 > /dev/null

```
looks like
```
sudo aptitude -y install $ESS_LIBS

```
and tell me what happens?

> **dcstar said:**
> I have already used the 1.0.6 version with the existing any-any and it seems to work fine for me.

BTW, I removed the "-q" from the wget as I find it more valuable to see the big download running and know how long it has to go.

I'll keep the wget info in mind. I destroyed a lot of output, maybe I should just keep it all in there?

What any-any update did you use? 117a creates a directory listing like this:
--vmware-any-any-update115
----vmware-any-any-update117
which I find very odd.

---

### Post by justifiedandancient on 2008-06-05
I had vmware-server running in 8.04 AMD 64 following the previous threads 337040 and 779934. However, the recent kernel upgrade invalidated that so I had to fix it. So when I checked again and found this thread and the enclosed script. I had one issue with it in that it failed (stopped completely) because it couldn't shutdown the vmware services. There was a vmware process that wasn't dying so I killed it manually and ran the script again and it then worked.

Thanks for a great script.

---

### Post by iltofa on 2008-06-05
Laptop Acer 6292 Centrino Dual core Duo: everything ok.

THANKS!

---

### Post by siongz on 2008-06-06
hi.. i've got a problem when running ur script.. everythin worked fine up till the serial nuber part.. den errors popped up.
this is what i got in the terminal near the end..

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Bridged networking on /dev/vmnet2                                   done

The configuration of VMware Server 1.0.5 build-80187 for Linux for this running
kernel completed successfully.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- Adding USB support to /etc/fstab, continuing...
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...

any idea?? please help.. thx

---

### Post by daxm on 2008-06-07
> **altonbr said:**
> Just a note:

VMware Server 1.0.6
and,
VMware-any-any-patch-117a

are out, but I won't add them to my script until I've fully tested them.

I've hacked your script to run the 1.0.6 install and the any-any-116 setup from the local dir (since I couldn't find any URL links that didn't involve random strings being attached to the URL or that didn't require you to login to get the files).  I've loaded the VMware console and it appears to work.

See Attached.

---

### Post by pmasereeuw on 2008-06-07
Thanks for your wonderful script - it seems to be doing the same things I did by
hand following other information sources, but with much less effort - great!

I had one slight, but understandable problem: the soft links to the library
files did not work, because I installed in /usr/local instead of the default. I
fixed that by hand on the command line.

However, I still don't get a virtual machine running. The console starts, but
when I open a virtual machine file from my previous computer, or when I try to open a
newly created one, I get a dialog with this error:

> Unable to change virtual machine power state: The process exited with an error: End of error message.

The log file /var/log/vmware/vmware-serverd.log ends with messages like the
following:
> 
Jun 07 22:52:46: app| Msg_Post: Version mismatch with vmmon module: expecting 138.0, got 137.0.
Jun 07 22:52:46: app| You have an incorrect version of the `vmmon' kernel module.
Jun 07 22:52:46: app| Try reinstalling VMware Server.
Jun 07 22:52:46: app|
Jun 07 22:52:46: app| Msg_Post: Error
Jun 07 22:52:46: app| [msg.vmmonPosix.initFailed] Failed to initialize monitor device.
Jun 07 22:52:46: app| [localized] Failed to initialize monitor device.
Jun 07 22:52:46: app| ----------------------------------------
Jun 07 22:52:46: app| Msg_Post: Failed to initialize monitor device.
Jun 07 22:52:46: app|
Jun 07 22:53:06: app| Msg_Post: Error
Jun 07 22:53:06: app| [msg.vmmonPosix.badVersion] Version mismatch with vmmon module: expecting 138.0, got 137.0.
Jun 07 22:53:06: app| [msg.vmmonPosix.badDriver] You have an incorrect version of the `vmmon' kernel module.
Jun 07 22:53:06: app| Try reinstalling VMware Server.
Jun 07 22:53:06: app| [localized] Version mismatch with vmmon module: expecting 138.0, got 137.0.
Jun 07 22:53:06: app| You have an incorrect version of the `vmmon' kernel module.
Jun 07 22:53:06: app| Try reinstalling VMware Server.
Jun 07 22:53:06: app| ----------------------------------------

I have seen past messages that let you edit header files in the file vmmon.tar. I have the impression that such a thing could be needed here, but I am reluctant to try.

I am running a freshly installed 32 bits Ubuntu 8.04 with kernel 2.6.24-18.
This is the directory listing from where I invoke your script:

> 
install-vmware.sh
vmware-any-any-update-116.tgz
VMware-server-1.0.5-80187.tar.gz


Any ideas?

Pieter

---

### Post by AldenIsZen on 2008-06-07
Boy I wish I read the whole thread first! lol. Since I have many "projects" I am wokring on and vmware seems to be running, I think I will wait until either altonbr gives his approval or someone else has tried it, at least for now. If I get around to it first, i will report back. Thanks!

---

### Post by altonbr on 2008-06-08
**Updated:**
_2008-06-08_
[LIST]
[*]Removed output supression for wget
[*]Changed spaces to tabs (how was it even spaces in the first place?)
[*]Reverted back to VMware-any-any-update-116 downloading from uruz.org
[/LIST]
_2008-06-02_
[LIST]
[*]Updated VMware Server to 1.0.6
[*]Kept VMware-any-any-update at 116 until I read more about 117, 117(2) and 117a
[*]Now downloading VMware-any-any-update-116 from vmkernelnewbies.googlegroups.com
[/LIST]

---

### Post by kryptonite--- on 2008-06-08
hey there,
i followed ur script and installed it like 5 times now, i keep getting hte same error , that "you need to run bla bla bla configure.pl" error.

im running the 32 bit version, so when i try to use that one line thing l3232 it says the files r not there.

can u help me please....
i need this for a university course....

---

### Post by altonbr on 2008-06-08
> **kryptonite--- said:**
> hey there,
i followed ur script and installed it like 5 times now, i keep getting hte same error , that "you need to run bla bla bla configure.pl" error.

im running the 32 bit version, so when i try to use that one line thing l3232 it says the files r not there.

can u help me please....
i need this for a university course....

Read the full instructions. When it FIRST asks you to run "/usr/bin/vmware-config.pl", select no. The SECOND time it askes you, select yes. Then run through the prompts as usual.

---

### Post by kryptonite--- on 2008-06-08
well, i did that like 5 times, each time i get the first prompt i type no, then i get the rest of the procedure and installing the patches, it only installs one patch the rest i get this reponse "no patch needed/ available" and then it patches everything up and then i get the second prompt and i type yes , then when its done and i type vmware in the prompt it gives me that error

what do i do ?

---

### Post by altonbr on 2008-06-08
> **kryptonite--- said:**
> well, i did that like 5 times, each time i get the first prompt i type no, then i get the rest of the procedure and installing the patches, it only installs one patch the rest i get this reponse "no patch needed/ available" and then it patches everything up and then i get the second prompt and i type yes , then when its done and i type vmware in the prompt it gives me that error

what do i do ?

Try downloading my script once more (as it recently changed), delete any files that may have been downloaded and run the script once more.

Then, if it doesn't work, please paste the output of the error plus a couple of lines above.

---

### Post by kryptonite--- on 2008-06-08
i downloaded ur script 6 hours ago, has it been changed since then ?

---

### Post by kryptonite--- on 2008-06-08
ok downloaded and installed everything from scratch again...still same error....
il copy and paste what i get in the terminal, if there is a log file, let me know where it is and il paste its contents here again....
"vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl."

---

### Post by ezramorris on 2008-06-09
Hi, I get the following errors:

```
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
 -- Installing essential libraries for 32-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
--12:17:07--  http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz
           => `VMware-server-1.0.6-91891.tar.gz'
Resolving download3.vmware.com... 213.248.112.163
Connecting to download3.vmware.com|213.248.112.163|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 106,985,820 (102M) [application/x-gzip]

100%[=================================================================================================================>] 106,985,820  636.04K/s    ETA 00:00

12:20:12 (567.97 KB/s) - `VMware-server-1.0.6-91891.tar.gz' saved [106985820/106985820]

 -- Extracting VMware server, continuing...
 -- Installing VMware server, continuing...
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

 -- Downloading the any-any update. This may take some time, continuing...
--12:20:26--  http://uruz.org/files/vmware-any-any-update-116.tgz
           => `vmware-any-any-update-116.tgz'
Resolving uruz.org... 83.246.120.75
Connecting to uruz.org|83.246.120.75|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 493,492 (482K) [application/x-gzip]

100%[=================================================================================================================>] 493,492      531.94K/s             

12:20:28 (530.87 KB/s) - `vmware-any-any-update-116.tgz' saved [493492/493492]

 -- Extracting the any-any update, continuing...
 -- Running the any-any update, continuing...
Updating /usr/bin/vmware-config.pl ... corrupted
Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware-server/modules/source/vmmon.tar.

Execution aborted.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- Adding USB support to /etc/fstab, continuing...
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...

```

It mentions something about having an old version of vmware installed? Should I get rid of this?/How?

Thanks!

---

### Post by altonbr on 2008-06-09
@kryptonite---:
I was getting those errors last night, so I slightly modified my script and got it running again.

What kernel do you have?

```
uname -r
```

Sorry for making this take so long. It shouldn't be this hard, I swear!

@ezramorris:
I think it is as easy as:
```
sudo rm -rf /etc/vmware
```
I thought VMware took care of this so I didn't program it into my script. Can you tell me if that works?

---

### Post by ezramorris on 2008-06-09
> **altonbr said:**
> I think it is as easy as:
```
sudo rm -rf /etc/vmware
```
I thought VMware took care of this so I didn't program it into my script. Can you tell me if that works?

Yep, that does the trick.
Thanks.

PS. Does it really need to upgrade everything before it installs?

---

### Post by gr4n1t3 on 2008-06-09
So easy to follow and whats more it worked! :)

---

### Post by altonbr on 2008-06-09
> **ezramorris said:**
> Yep, that does the trick.
Thanks.

PS. Does it really need to upgrade everything before it installs?

No, but you really should have the latest and greatest kernel (linux-image) because every single little upgrade breaks VMware. Its annoying, yes but they're working on fixing that for VMware Server 2.0.

@gr4n1t3:
You're welcome! :)

---

### Post by spoonernash on 2008-06-11
I am trying to set up a headless vmware server on 8.04 server version. I followed this thread (thanks again altonbr) with success. I can connect to the server from another Linux box that has vmware-server-console on it. Now I need to get vmware-server-console set up on the server so I can connect with a Mac. First I want to get it working from another Linux box that does not have vmware-server-console loaded. Then I will tackle the Mac.

I downloaded and installed vmware-server-console on the new server. I installed libpng12-0 as it seemed to be needed. I installed xterm so I would have an X app to test.

When I ssh to the server and enter:
xterm -display 192.168.1.206:0
where 192.168.1.206 is the Linux box without vmware-server-console, I get a terminal window for the server on that box. So I think the basics work.

When I then enter on the server:
vmware -display 192.168.1.206:0
I get this:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fcc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6fcc81e]
#2 /usr/lib/libX11.so.6 [0xb7e56518]
#3 /usr/lib/libX11.so.6(XAddExtension+0x2c) [0xb7e39c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xb7d3fed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d3e8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d3ed39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xb7d3eec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b8b9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b8dd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b5dc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b6a24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b5dc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b69b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a6e298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a6e586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7077e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c83459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c6b3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c6b076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

I'm at a lost looking at this and I don't know what to try. Can anyone help me out with this?

---

### Post by altonbr on 2008-06-11
@spoonernash
I'm terribly sorry, but I have no experience with connecting to VMware on the command line (never have needed to). I'll see what I dig up though...

---

### Post by matrooswolf on 2008-06-12
Thanks!
Worked great for me!

---

### Post by uljanow on 2008-06-12
There is also a vmware-package (at least in debian testing) which builds debian packages out of various proprietary vmware products. Installing and Removing works properly.
Maybe there are some Ubuntu-Ports of it.


[http://packages.debian.org/lenny/vmware-package](http://packages.debian.org/lenny/vmware-package)

---

### Post by kryptonite--- on 2008-06-13
@altonbar:

my kernel is: 2.6.24-18-generic
i still get the same error i posted before....this is crazy.....

---

### Post by dmizer on 2008-06-13
just an fyi.

i copied the script and pasted it into nano.  for some reason, the paste wrapped the longer lines, and made a supreme mess of the script.  i tried to clean it up but wound up just starting fresh and used gedit instead.

never had this problem pasting into nano before.  don't know why it did this time, but it did create quite a headache for me.

---

### Post by RayH on 2008-06-13
alton - just sending a personal thanks for this script.  I ran into the rui/license key issue and this worked like a charm!

---

### Post by altonbr on 2008-06-13
> **uljanow said:**
> There is also a vmware-package (at least in debian testing) which builds debian packages out of various proprietary vmware products. Installing and Removing works properly.
Maybe there are some Ubuntu-Ports of it.


[http://packages.debian.org/lenny/vmware-package](http://packages.debian.org/lenny/vmware-package)

Thanks, I'll look into it!

> **kryptonite--- said:**
> @altonbar:

my kernel is: 2.6.24-18-generic
i still get the same error i posted before....this is crazy.....

Can you tell me in greater detail what you did before and after running my script? I really want to help, but I can't do much without more information.

> **dmizer said:**
> just an fyi.

i copied the script and pasted it into nano.  for some reason, the paste wrapped the longer lines, and made a supreme mess of the script.  i tried to clean it up but wound up just starting fresh and used gedit instead.

never had this problem pasting into nano before.  don't know why it did this time, but it did create quite a headache for me.

That's really odd as I created it in gEdit so its using UTF-8 and standard Linux line breaks.

The only possible explanation is that vbulletin has changed the output of my script and/or nano can't read Windows line breaks. I doubt it however.

I'll try posting the script as an attachment as well, just for cases like this.

---

### Post by kryptonite--- on 2008-06-13
well i followed your tutorial and did nothing more nor less, i didn everything exactly the same way u described and got the same prompts....
i re-installed everything 3 times and still the same problem...

---

### Post by malath on 2008-06-14
Well, I have installed the script providen on the page 1

but giving me message that there is no operating system detected, 

i want this to boot my current installed windows xp media cented on drive C:

how can i do this?

---

### Post by ezramorris on 2008-06-14
> **malath said:**
> Well, I have installed the script providen on the page 1

but giving me message that there is no operating system detected, 
Is this in the installer or when running a virtual machine? If it is inside VMware when you run a virtual machine (VM), you need to (1) have a virtual hard disk set up and selected in the VM settings, and (2) have some sort of media to boot off (usually a CD), by selecting 'use host drive' in the VM's CD settings. Then boot the machine and make sure it boots from the CD.

> **malath said:**
> i want this to boot my current installed windows xp media cented on drive C:

how can i do this?
You can do this by adding a hard disk in the VM settings and choosing "use a physical disk". However, neither I or VMware recommend this since it could damage the data on the drive, possibly leaving you unable to boot or access files. But it's up to you!

The best thing to do would be to install Windows XP in a virtual hard disk. To be legal and in order for you to do Windows activation, you will need to purchase another license from Microsoft.

---

### Post by djg5211 on 2008-06-16
THANK YOU!!!!

Worked flawlessly for me!

I have a couple of questions.... seeing how you seem to be very saavy
regarding VM/UBUNTU etc.

1. If a person wanted to upgrade to the VM Server 2.0 BETA, how would
   one do so without destroying what you already have created with 1.0.6
   (or whatever version this was) and/or are they compatible?

2. So, what i am doing is running Ubuntu with the absolute lastest updates
   and upgrades (as of last night [see message date]) VM Server and 
   MagicJack (USB Internet Phone Device) and it works great.
   My QUESTION is regarding passing some parameters from Ubuntu to VM Server.

   If i must reboot my system (ie:Ubuntu)..... When i run VM Server and start
   my Virtual Machine (Windows XP Home Edition) i have to UNPLUG the USB
   device and plug it back in before VM/XP will initialize the MagicJack device.
   But, the screwy thing is that the MagicJack creates like a VIRTUAL CD/DVD
   and unless i unplug and replug MagicJack into the USB port that VIRTUAL
   CD/DVD does not appear and if it's not there MagicJack don't work.

   Is there.....
   some way to pass such a parameter to VM from Ubunta so XP will pick up
   on the parameters and not give me the UNKNOWN DEVICE balloon?

Thanks in advance!
Dave

---

### Post by jcup on 2008-06-16
Yeah! I've had problems trying to get this to work before... Thanks to your how to, it was a snap...

Thanks!

---

### Post by kryptonite--- on 2008-06-18
@altonbr
i just remembered, the only thing different from your tutorial i did was to bridge netowkring to ath0 (as i want it bridged on my wifi, i dont use the ethernet card at all) you think this might be the problem? if so, how do i fix it and make it bridge on the ath0 ?
thanks alot man for tryin to make this work.

---

### Post by grg3 on 2008-06-19
> **spoonernash said:**
> I am trying to set up a headless vmware server on 8.04 server version. I followed this thread (thanks again altonbr) with success. I can connect to the server from another Linux box that has vmware-server-console on it. Now I need to get vmware-server-console set up on the server so I can connect with a Mac. First I want to get it working from another Linux box that does not have vmware-server-console loaded. Then I will tackle the Mac.

I downloaded and installed vmware-server-console on the new server. I installed libpng12-0 as it seemed to be needed. I installed xterm so I would have an X app to test.

When I ssh to the server and enter:
xterm -display 192.168.1.206:0
where 192.168.1.206 is the Linux box without vmware-server-console, I get a terminal window for the server on that box. So I think the basics work.

When I then enter on the server:
vmware -display 192.168.1.206:0
I get this:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6fcc767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6fcc81e]
#2 /usr/lib/libX11.so.6 [0xb7e56518]
#3 /usr/lib/libX11.so.6(XAddExtension+0x2c) [0xb7e39c9c]
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xb7d3fed7]
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d3e8b1]
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xb7d3ed39]
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xb7d3eec0]
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b8b9b6]
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b8dd75]
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b5dc14]
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xb7b6a24f]
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xb7b5dc14]
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xb7b69b34]
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a6e298]
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a6e586]
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xb7a7077e]
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xb7c83459]
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xb7c6b3a1]
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xb7c6b076]
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.

I'm at a lost looking at this and I don't know what to try. Can anyone help me out with this?

I think this is the same bug that I have seen in Debian Sid.

See:[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486507](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=486507)

---

### Post by pacice on 2008-06-20
Thanks for the great tut.
Worked first time, with networking to a vista peer to peer network.
Just need to get the file sharing with the local host working

Regards

Pacice

---

### Post by NKane on 2008-06-25
First of all your script is awesome, but I did have some problems.

I'm running Ubuntu 8.04, 64bit server edition.

Your script ran without a hitch, except when I tried to run it right after the script finished I got the following: 

```



Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
Unable to load image-loading module: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/132/32/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory 
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: unexpected character `@', expected string constant 
Locking assertion failure.  Backtrace: 
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7040767] 
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xf70408b1] 
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xf7ebf1bd] 
#3 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderQueryFormats+0x109) [0xf7daf969] 
#4 /usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1(XRenderFindFormat+0x4c) [0xf7daff4c] 
#5 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf5180] 
#6 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf5d2c] 
#7 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc5c14] 
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bd224f] 
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc5c14] 
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bd1b34] 
#11 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad6298] 
#12 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad6586] 
#13 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad877e] 
#14 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ceb459] 
#15 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cd33a1] 
#16 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cd3076] 
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cea6eb] 
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit_valist+0x91e) [0xf7ce9d46] 
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_signal_emit+0x38) [0xf7cea0b8] 
Locking assertion failure.  Backtrace: 
#0 /usr/lib32/libxcb-xlib.so.0 [0xf7040767] 
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xf704081e] 
#2 /usr/lib32/libX11.so.6 [0xf7ebe518] 
#3 /usr/lib32/libX11.so.6(XAddExtension+0x2c) [0xf7ea1c9c] 
#4 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(_XftDisplayInfoGet+0x77) [0xf7da7ed7] 
#5 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7da68b1] 
#6 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2 [0xf7da6d39] 
#7 /usr/lib/vmware/lib/libXft.so.2/libXft.so.2(XftDrawPicture+0x10) [0xf7da6ec0] 
#8 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf39b6] 
#9 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bf5d75] 
#10 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc5c14] 
#11 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0 [0xf7bd224f] 
#12 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x270) [0xf7bc5c14] 
#13 /usr/lib/vmware/lib/libgdk-x11-2.0.so.0/libgdk-x11-2.0.so.0(gdk_pixbuf_render_pixmap_and_mask_for_colormap+0x255) [0xf7bd1b34] 
#14 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad6298] 
#15 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad6586] 
#16 /usr/lib/vmware/lib/libgtk-x11-2.0.so.0/libgtk-x11-2.0.so.0 [0xf7ad877e] 
#17 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0xd1) [0xf7ceb459] 
#18 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0 [0xf7cd33a1] 
#19 /usr/lib/vmware/lib/libgobject-2.0.so.0/libgobject-2.0.so.0(g_closure_invoke+0x1b1) [0xf7cd3076] 
vmware: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed. 


```


The "fix" i did was to merely create a sub 32 folder inside of /usr/132 (i.e - /usr/132/32) and copied the entire contents of /usr/132 to the new 32 sub folder and viola! it worked!

---

### Post by kcallison on 2008-06-28
Thank you very much for the post.  I had given up on 8.04 and went back to 7.10.  Now I have it the way I wanted it in the first place (running 64 bit version of 8.04).

K. Callison

---

### Post by Rasqual on 2008-07-03
From what I've seen, Server 2.0 does not support adding existing physical disks (in RC1). A compelling enough reason (as far as I'm concerned) to not migrate, even after it's gone gold. What's more, the Web interface is soooooooo sluggish and kinda locks to using firefox as a browser.

I'll just stick to Server 1.0.x, thanks :/

---

### Post by Brian96 on 2008-07-05
I originally installed Vmware in Hardy using this script when the kernel was still at 24-16. I had not used it since all the kernel updates over the past few weeks, but it wasn't working today.

The error message that came up told me to run the config script, but I kept getting an error message.

Anyway, to skip ahead, I found that the folder for the 24-19 kernel does not have the "build" subdirectory that the other, older kernel folders have. (Sorry for the lack of accurate technical terms.)

I got it working by rebooting into a 24-18 session and running the config script, but I'd like for it to work in the latest kernel.

Any ideas as to why there is no "build" folder in my 24-19 kernel folder?

(I am running 64-bit Hardy.)

Thanks in advance.

---

### Post by aikiwolfie on 2008-07-05
I ran the script and it failed to install anything. I upgraded directly from Gutsy and had VMware Server installed on that. The Hardy upgrade killed it but left behind some files. If I try to use Synaptic to completly remove them it tells me all sorts of stuff will also be removed. Like a huge list of seemingly important files. Here's the out put from the script.

```
 -- Updating Ubuntu, continuing...
 -- Upgrading Ubuntu, continuing...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
 -- Installing essential libraries for 32-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
--23:51:53--  http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz
           => `VMware-server-1.0.6-91891.tar.gz'
Resolving download3.vmware.com... 84.53.178.66, 84.53.178.67
Connecting to download3.vmware.com|84.53.178.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 106,985,820 (102M) [application/x-gzip]

100%[====================================>] 106,985,820  239.00K/s    ETA 00:00

23:59:13 (237.49 KB/s) - `VMware-server-1.0.6-91891.tar.gz' saved [106985820/106985820]

 -- Extracting VMware server, continuing...
 -- Installing VMware server, continuing...
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

 -- Downloading the any-any update. This may take some time, continuing...
--23:59:19--  http://uruz.org/files/vmware-any-any-update-116.tgz
           => `vmware-any-any-update-116.tgz'
Resolving uruz.org... 83.246.120.75
Connecting to uruz.org|83.246.120.75|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 493,492 (482K) [application/x-gzip]

100%[====================================>] 493,492      251.85K/s             

23:59:21 (251.13 KB/s) - `vmware-any-any-update-116.tgz' saved [493492/493492]

 -- Extracting the any-any update, continuing...
 -- Running the any-any update, continuing...
Updating /usr/bin/vmware-config.pl ... corrupted
Unable to copy the source file ./vmmon.tar to the destination file 
/usr/lib/vmware-server/modules/source/vmmon.tar.

Execution aborted.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- USB fix already present, continuing...
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...
lynchk@moonstone:~/Scripts/Shell$ 

```

---

### Post by altonbr on 2008-07-05
@brian96:
Does this folder exist: '/lib/modules/2.6.24-19-generic/build/include'?

It does for me with 2.6.24-19 and VMware needs that to compile vmmon.

Please let me know. If it does exist and VMware doesn't install, please post the log here.

@aikiwolfie:
Can you please run 'vmware-server-distrib/bin/vmware-uninstall.pl' manually once 1.0.6 is extracted. You may have to do this manually.

Then, upon success, try running my script again.

---

### Post by ckrul on 2008-07-06
Thanks for doing the hard work with this great script! I had VMware running in no time.

---

### Post by Brian96 on 2008-07-06
> **altonbr said:**
> @brian96:
Does this folder exist: '/lib/modules/2.6.24-19-generic/build/include'?

It does for me with 2.6.24-19 and VMware needs that to compile vmmon.

Please let me know. If it does exist and VMware doesn't install, please post the log here.

@aikiwolfie:
Can you please run 'vmware-server-distrib/bin/vmware-uninstall.pl' manually once 1.0.6 is extracted. You may have to do this manually.

Then, upon success, try running my script again.

No, that folder doesn't exist (although it does for all previous kernel upgrades since 24-16).

I originally used your script to install it back when the kernel was at 24-16 and hadn't used VMWare since. I can't reproduce it now, but the error message I got when running "vmware" in a terminal said something about it not being configured properly and instructed me to run some config command. I ran it, and got an error message about not finding the kernel or something. That's when I noticed that the "build" folder and its subdirectories did not exist in my /lib/******24-19 folder. However, the build folder WAS in my 24-18 folder, so I rebooted into a 24-18 session, got the same initial error message, ran the recommended command, and everything worked out.

So, I guess my issue is: why didn't that folder get created in my /lib/modules/2.6.24-19-generic/build/include directory when I let the Update Manager update my kernel?

Thanks for your help.

---

### Post by mdpalow on 2008-07-11
thanks altonbr...

Really good script. I decided to install VMware again after a long time and was having some difficulty getting it to work. Your script did the trick in no time.

Thanks... mdpalow

---

### Post by dmizer on 2008-07-18
script completed successfuly.  still get this message upon attempting to run vmware:
```
$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

---

### Post by ngms27 on 2008-07-18
No matter what I try I cannot get this to work in Heron. This is the diagnostics:

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-19-386/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-19-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
/tmp/vmware-config0/vmmon-only/linux/hostif.c: In function ‘HostIF_BrokenCPUHelper’:
/tmp/vmware-config0/vmmon-only/linux/hostif.c:3042: warning: passing argument 1 of ‘HostIFBrokenCPUHelper’ discards qualifiers from pointer target type
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Werror-implicit-function-declaration" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
In file included from /tmp/vmware-config0/vmmon-only/common/task.c:1194:
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::validEIP’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::cs’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rsp’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: note: ‘sysenterState.SysenterStateV45::rip’ was declared here
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialised in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialised in this function
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.71.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.71.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.37.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.37.0.

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.24-19-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] 

 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                  [ OK ] 
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Do you want this program to set up permissions for your registered virtual 
machines?  This will be done by setting new permissions on all files found in 
the "/etc/vmware/vm-list" file. [no] 

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

Do you want to enter a serial number now? (yes/no/help) [no] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
   Starting VMware virtual machines...                                 done

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

 -- Fixing library issues, continuing...
 -- USB fix already present, continuing...
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...
root@ngms27-desktop:/home/ngms27# 


When running vmware I get:

root@ngms27-desktop:/home/ngms27# vmware
process 10160: Attempt to remove filter function 0xb6affcd0 user data 0x88b8b40, but no such filter has been added

The no console displays

---

### Post by Brian96 on 2008-07-18
> **Brian96 said:**
> No, that folder doesn't exist (although it does for all previous kernel upgrades since 24-16).

I originally used your script to install it back when the kernel was at 24-16 and hadn't used VMWare since. I can't reproduce it now, but the error message I got when running "vmware" in a terminal said something about it not being configured properly and instructed me to run some config command. I ran it, and got an error message about not finding the kernel or something. That's when I noticed that the "build" folder and its subdirectories did not exist in my /lib/******24-19 folder. However, the build folder WAS in my 24-18 folder, so I rebooted into a 24-18 session, got the same initial error message, ran the recommended command, and everything worked out.

So, I guess my issue is: why didn't that folder get created in my /lib/modules/2.6.24-19-generic/build/include directory when I let the Update Manager update my kernel?

Thanks for your help.


Just wanted to revisit this. Can anyone help me figure out why the /build/include directory didn't get created in my /lib/modules/2.6.24-19-generic directory? Is that something the upgrade should have done, or is it something that is handled by the script?

I am confused, because the directory did exist in my /lib/modules/2.6.24-18-generic directory, although I don't ever remember running altonbr's script since the "16" kernel release.

Thanks in advance.

---

### Post by dmizer on 2008-07-18
> **dmizer said:**
> script completed successfuly.  still get this message upon attempting to run vmware:
```
$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

figured this one out.

my wireless card is an atheros chipset, and i was running the card with the native module which gave it an ath0 designator, and also makes use of a wifi0 designator.  according to this post: [http://www.mansfieldlug.org.uk/index.php?option=com_content&task=view&id=26&Itemid=51](http://www.mansfieldlug.org.uk/index.php?option=com_content&task=view&id=26&Itemid=51) the compiler can't create a bridge when using the native driver for this card.

i switched to ndiswrapper (which gave my wireless card a wlan0 designator) and all was well.

---

### Post by GabrielDunn on 2008-07-22
Just wanted to give you props...great guide.  Worked flawlessly.  I bookedmarked it for future use.

If we were in prison I would protect you in the shower.

---

### Post by Domain1 on 2008-07-24
Hello, after attempting to install vmware from your instructions I recieve the following error:

100%[====================================>] 493,492      270.90K/s             

18:59:18 (269.98 KB/s) - `vmware-any-any-update-116.tgz' saved [493492/493492]

 -- Extracting the any-any update, continuing...
 -- Running the any-any update, continuing...
Can't exec "/etc/vmware/installer.sh": No such file or directory at ./runme.pl
	line 819 (#1)
    (W exec) A system(), exec(), or piped open call could not execute the
    named program for the indicated reason.  Typical reasons include: the
    permissions were wrong on the file, the file wasn't found in
    $ENV{PATH}, the executable in question was compiled for another
    architecture, or the #! line in a script points to an interpreter that
    can't be run for similar reasons.  (Or maybe your system doesn't support
    #! at all.)
    
Unknown VMware version ? is installed. This installer supports only version 2 
and 3.

Execution aborted.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- USB fix already present, continuing...
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...

Then nothing happens I am back to the start. I am using the 2.6.24-19-generic kernal and I haven't installed vmware before so I really wanted to get this installed. any help would be appreciated.

---

### Post by stealth17 on 2008-07-24
^^ I've run into the same problem.

---

### Post by altonbr on 2008-07-25
> **GabrielDunn said:**
> Just wanted to give you props...great guide.  Worked flawlessly.  I bookedmarked it for future use.

If we were in prison I would protect you in the shower.

This literally made me laugh out loud. I'm not even going to think of your intentions after you protected me though :|

> **Domain1 said:**
> Hello, after attempting to install vmware from your instructions I recieve the following error:

100%[====================================>] 493,492      270.90K/s             

18:59:18 (269.98 KB/s) - `vmware-any-any-update-116.tgz' saved [493492/493492]

 -- Extracting the any-any update, continuing...
 -- Running the any-any update, continuing...
Can't exec "/etc/vmware/installer.sh": No such file or directory at ./runme.pl
	line 819 (#1)
    (W exec) A system(), exec(), or piped open call could not execute the
    named program for the indicated reason.  Typical reasons include: the
    permissions were wrong on the file, the file wasn't found in
    $ENV{PATH}, the executable in question was compiled for another
    architecture, or the #! line in a script points to an interpreter that
    can't be run for similar reasons.  (Or maybe your system doesn't support
    #! at all.)
    
Unknown VMware version ? is installed. This installer supports only version 2 
and 3.

Execution aborted.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- USB fix already present, continuing...
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...

Then nothing happens I am back to the start. I am using the 2.6.24-19-generic kernal and I haven't installed vmware before so I really wanted to get this installed. any help would be appreciated.

Let me take a look at this and see if the script needs updating. Thanks for the report!

---

### Post by OzzyFrank on 2008-07-27
Thanks for the script and the instructions. Never could get it all to compile and/or get that "any-any" patch to do anything but waste my time before this. At first I thought this didn't work either, as the end messages were more cryptic, and didn't have the usual "Enjoy!" message from the develpment team, not to mention the final little instructions on what command runs it. Actually, that's just stuff that might confuse more of a newbie, but what made me go through the install again was (1) there was no icon in Applications > System (even my previous failed installs put one there) and more importantly (b) the terminal command "vmware-server" didn't work. I then tried "vmserver" (since Player is "vmplayer") but after the 2nd try gave just plain old "**vmware**" a bash, and seems that's the command. (Correct me if I am wrong, since I never did run Server from a terminal, but it used to be "vmware-server", as I remember installing packages of that name).

So, while this could be another little nicety added to the script, ie an icon made for it, those that don't end up with one can use that command to make their own (or just open from the terminal or Run dialog). I haven't really seen much mention of a missing icon, so figure I must be one of the few. (I'm running Ubuntu Hardy 64-bit with latest updates to 27 July 2008).

---

### Post by OzzyFrank on 2008-07-27
For those who need to make their own launcher, copy and paste this path when specifying the icon:

**/usr/share/pixmaps/vmware-server.png**

As I said, the command in simply **vmware**.

And the forum robot wasn't supposed to replace the 8 and ) at the end of my last post with a smilie, hahaha!

---

### Post by totaldrk62 on 2008-07-28
> **altonbr said:**
> Let me take a look at this and see if the script needs updating. Thanks for the report!

I am having the same issue. Any updates?

Update: So I went ahead and grabbed the installer from the website. When I tried running it, it complained about a tar3 previous installation (which I had in 7.10). So I removed all the vmware directories I could find and tried the installer again. It ran fine this time. Once installed I tried vmware at a command prompt and started some GCC 3.4 errors. That led me to a blog where I found my fix. 

cd /usr/lib/vmware/lib
/usr/lib/vmware/lib$ sudo mkdir bak
/usr/lib/vmware/lib$ sudo mv libgcc_s.so.1/libgcc_s.so.1 bak/

Once I did that everything ran great. Installing XP now so I can use my stupid Windows Mobile phone. Hope this helps your script in some way.

---

### Post by SyBorg on 2008-07-28
Maybe this helps someone else:

this morning I was struggling to run vmware on a minimalistic server (installed as 'command-line system'): all the vmware services started, I could connect from my desktop PC to the virtual machine and enter all the details for the new virtual OS, but when starting it would bail-out with an error saying:

"End of error message"

The vmware UI dump from /tmp/ would not help much:

"Jul 28 09:44:20: vmui| Log for VMware Server pid=13897 version=1.0.6 build=build-91891 option=Release
lug 28 09:44:20: vmui| Using log file /tmp/vmware-stefano/ui-13897.log
lug 28 09:44:20: vmui| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
lug 28 09:44:20: vmui| HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
lug 28 09:44:20: vmui| HostDeviceInfoFindHostIDECDROMs: /proc/ide could not be explored. Unable to enumerate host IDE cdroms.
lug 28 09:44:21: vmui| SMBIOS: can't open /dev/mem
lug 28 09:44:21: vmui| VmhsHostInfoPopulateSystem:  Could not get information from smbios to populate VMDB.
lug 28 09:44:21: vmui| HOSTINFO: Seeing AMD CPU, numCoresPerCPU 2 numThreadsPerCore 1.
lug 28 09:44:21: vmui| HOSTINFO: This machine has 1 physical CPUS, 2 total cores, and 2 logical CPUs.
lug 28 09:44:21: vmui| Gtk: Refusing to add non-unique action 'ListNewTeamAction' to action group 'App Actions'
lug 28 09:44:22: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: _Ferma and F_erma
lug 28 09:44:22: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: A_vanza and _Avanti
lug 28 09:44:22: vmui| Dlg::GetButtonInfo(): Duplicate GTK icon/label pair: I_nformazioni and Informazioni
lug 28 09:44:25: vmui| VMNetCtlConstruct: no Network Names to list
lug 28 09:44:25: vmui| VMUIGtkVmdb_LoadDevice: unhandled device class scsiCtlr"

I was about to give up and reinstall everything when, in the homedir of the user I created to manage & run the VMs, a .vmware directory that had "root:root" permissions

Changed the permissions to the correct user, the VM started fine

---

### Post by lib99 on 2008-07-28
This new installation script is GREAT!! Thank you!!

I have Ubuntu Hardy Heron since May and used the guide here on the forums to get VMWare server (1.05) installed. At the time there was some struggle with getting the network to work (etho and more so wlan0). Eventually it worked.

Since then I had little use for booting Windows XP. This past weekend I tried and VM Server wouldn't start on Ubuntu. My hunch is that along the way, one of the Ubuntu software updates messed up the installation.

I used the installation script provided here by altonbr. The script really made the process very-very easy. Installed latest VMware server (1.06) Everything went perfect. Except I can't access the wireless connection again. Something to still figure out, but isn't the fault of the script.  Thanks again altonbr!!

---

### Post by dmizer on 2008-07-29
According to this thread/howto: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Vmware-server no longer needs a helper script for install.  Just install it as per instructed on the Vmware website.

---

### Post by altonbr on 2008-07-30
> **OzzyFrank said:**
> For those who need to make their own launcher, copy and paste this path when specifying the icon:

**/usr/share/pixmaps/vmware-server.png**

As I said, the command in simply **vmware**.

And the forum robot wasn't supposed to replace the 8 and ) at the end of my last post with a smilie, hahaha!

VMware makes a launcher for you. I had one in my script at the very beginning but noticed it only created a duplicate launcher.

Are you using Xubuntu or Kubuntu? I haven't tried it in those.

As for your post above, I do agree that a 'success' message is in order, thank you! Didn't even think of that.

> **dmizer said:**
> According to this thread/howto: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Vmware-server no longer needs a helper script for install.  Just install it as per instructed on the Vmware website.

About time :D.

Looks like I have lots of updates to do...

---

### Post by channa on 2008-08-06
Thank you so much for making my life a little easier! I'm a relative newbie to ubuntu and stuff like this really helps when I'm trying to get something setup fast!

---

### Post by sultanchughtai on 2008-08-07
**Thank you very much for this lovely script altonbr! It saved lots of time=P~ I am a new user of Ubuntu Hardy on 64 bit...so just bare with me as silly questions may arrise. I ran the script the first time and I got the error message so I ran the script again (hopefully no harm was done) so I pasted the error message ...any advice/criticism is welcomed...please let me know...thank you!** 


sultan@ubuntu:~$ chmod a+x ./install_vmware.sh && ./install_vmware.sh
 -- Updating Ubuntu, continuing...
[sudo] password for sultan: 
 -- Upgrading Ubuntu, continuing...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  bridge-utils libqt3-mt libxalan110 libxerces27 
  linux-backports-modules-2.6.24-16-generic localechooser-data oem-config 
  oem-config-gtk 
The following packages will be upgraded:
  avant-window-navigator awn-manager libawn0 tzdata tzdata-java 
5 packages upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 1105kB of archives. After unpacking 25.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe tzdata-java 2008e-1ubuntu0.8.04 [140kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main tzdata 2008e-1ubuntu0.8.04 [657kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe awn-manager 0.2.1-0ubuntu2.2 [29.2kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe libawn0 0.2.1-0ubuntu2.2 [51.4kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe avant-window-navigator 0.2.1-0ubuntu2.2 [226kB]
Fetched 1105kB in 2s (457kB/s)           
Preconfiguring packages ...
(Reading database ... 161284 files and directories currently installed.)
Removing bridge-utils ...
Removing libqt3-mt ...
Removing libxalan110 ...
Removing libxerces27 ...
Removing linux-backports-modules-2.6.24-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Removing oem-config-gtk ...
Removing oem-config ...
Removing localechooser-data ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 161105 files and directories currently installed.)
Preparing to replace tzdata-java 2008c-1ubuntu0.8.04 (using .../tzdata-java_2008e-1ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2008c-1ubuntu0.8.04 (using .../tzdata_2008e-1ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2008e-1ubuntu0.8.04) ...

Current default timezone: 'America/New_York'
Local time is now:      Wed Aug  6 23:46:46 EDT 2008.
Universal Time is now:  Thu Aug  7 03:46:46 UTC 2008.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 161109 files and directories currently installed.)
Preparing to replace awn-manager 0.2.1-0ubuntu2 (using .../awn-manager_0.2.1-0ubuntu2.2_all.deb) ...
Unpacking replacement awn-manager ...
Preparing to replace libawn0 0.2.1-0ubuntu2 (using .../libawn0_0.2.1-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libawn0 ...
Preparing to replace avant-window-navigator 0.2.1-0ubuntu2 (using .../avant-window-navigator_0.2.1-0ubuntu2.2_amd64.deb) ...
Unpacking replacement avant-window-navigator ...
Setting up tzdata-java (2008e-1ubuntu0.8.04) ...
Setting up libawn0 (0.2.1-0ubuntu2.2) ...

Setting up avant-window-navigator (0.2.1-0ubuntu2.2) ...
Setting up awn-manager (0.2.1-0ubuntu2.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
 -- Installing essential libraries for 64-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
 !! Could not download VMware-server-1.0.6-91891.tar.gz, exiting...
 -- Removing downloaded and extracted files, continuing...
sultan@ubuntu:~$ chmod a+x ./install_vmware.sh && ./install_vmware.sh
 -- Updating Ubuntu, continuing...
 -- Upgrading Ubuntu, continuing...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
 -- Installing essential libraries for 64-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
 !! Could not download VMware-server-1.0.6-91891.tar.gz, exiting...
 -- Removing downloaded and extracted files, continuing...

---

### Post by Shadow94 on 2008-08-15
Ok, so I'm new to the forum, and seeing as how out of all of your tutorials that I have tried, they all worked, I tried to install VMware server in hardy using one of your tutorials. However, I first searched it on google, and found this [http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04](http://www.howtoforge.com/installing-vmware-server-on-ubuntu-8.04) and the installation was going fine, until I accidentally pressed something and the installation was a failure. Then, when I tried reinstalling, I got this message:```
miguel@miguel-desktop:~$ sudo /home/miguel/Desktop/vmware-server-distrib/vmware-install.pl
[sudo] password for miguel: 
A previous installation of VMware software has been detected.

Failure

Execution aborted.


```

So then, I tried your installation, but I got a similar error: ```
miguel@miguel-desktop:~$ chmod a+x ./install_vmware.sh && ./install_vmware.sh
 -- Updating Ubuntu, continuing...
W: GPG error: http://ftp.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Duplicate sources.list entry http://ppa.launchpad.net hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_do-core_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://download.tuxfamily.org feisty/eyecandy Packages (/var/lib/apt/lists/download.tuxfamily.org_3v1deb_dists_feisty_eyecandy_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
 -- Upgrading Ubuntu, continuing...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  initramfs-tools initscripts 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
 -- Installing essential libraries for 32-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- Downloading VMware server. This may take some time, continuing...
--20:03:31--  http://download3.vmware.com/software/vmserver/VMware-server-1.0.6-91891.tar.gz
           => `VMware-server-1.0.6-91891.tar.gz'
Resolving download3.vmware.com... 24.29.138.75, 24.29.138.33
Connecting to download3.vmware.com|24.29.138.75|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 106,985,820 (102M) [application/x-gzip]

100%[====================================>] 106,985,820  506.91K/s    ETA 00:00

20:09:48 (277.03 KB/s) - `VMware-server-1.0.6-91891.tar.gz' saved [106985820/106985820]

 -- Extracting VMware server, continuing...
 -- Installing VMware server, continuing...
A previous installation of VMware software has been detected.

Failure

Execution aborted.

 -- Downloading the any-any update. This may take some time, continuing...
--20:09:53--  http://uruz.org/files/vmware-any-any-update-116.tgz
           => `vmware-any-any-update-116.tgz'
Resolving uruz.org... 83.246.120.75
Connecting to uruz.org|83.246.120.75|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 493,492 (482K) [application/x-gzip]

100%[====================================>] 493,492      190.70K/s             

20:09:56 (190.25 KB/s) - `vmware-any-any-update-116.tgz' saved [493492/493492]

 -- Extracting the any-any update, continuing...
 -- Running the any-any update, continuing...
Can't exec "/etc/vmware/installer.sh": No such file or directory at ./runme.pl
	line 819 (#1)
    (W exec) A system(), exec(), or piped open call could not execute the
    named program for the indicated reason.  Typical reasons include: the
    permissions were wrong on the file, the file wasn't found in
    $ENV{PATH}, the executable in question was compiled for another
    architecture, or the #! line in a script points to an interpreter that
    can't be run for similar reasons.  (Or maybe your system doesn't support
    #! at all.)
    
Unknown VMware version ? is installed. This installer supports only version 2 
and 3.

Execution aborted.

 -- Fixing library issues, continuing...
ln: creating symbolic link `/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0': No such file or directory
 -- USB fix already present, continuing...
 -- Safely exiting...
 -- Removing downloaded and extracted files, continuing...

```

so I was really hoping that one of you would help me because I am a total noob at ubuntu, and have only had it for a day. I already downloaded the VMware-server-1.0.6-91891.tar.gz and acquired a serial. Please, any help will be appreciated.

---

### Post by lib99 on 2008-08-15
This script is great. However, I'm unable to get the wireless adapter working with this specific installation. A few months ago, I used instructions here [http://ubuntuforums.org/showpost.php?p=5017931&postcount=5]("http://ubuntuforums.org/showpost.php?p=5017931&postcount=5") to get everything in order (vmware 1.05). The link to the patch referenced, is dead now. Would anyone have a suggestion or tip to point me in the right direction?? Thanks.

---

### Post by OzzyFrank on 2008-08-15
Shadow94, have you tried a complete removal of VMware before trying again? That should get rid of errors where it is finding an installed version. And mighty adventurous of you to be installing virtualisation on your first day of Linux! Personally, I would have just played with a few apps on my first day so I don't end up hating Linux by the end of it, hehehe. Anyway, try uninstalling VMware then reinstalling it again. Can't remember if the script has an uninstaller, and I know it probably won't be listed in Synaptic, so if need be **sudo apt-get remove vmware**.

---

### Post by lsteacke on 2008-09-16
I found this thread when I needed to install Vmware server on my new install of hardy.  However everything appeared to install correctly after running the script until I tried to launch vmware.  The following lines are spammed before the backtrace which I could post should anyone find it useful.


Unable to load image-loading module: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/l3232/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory


[COLOR="DeepSkyBlue"][B]
PROBLEM SOLVED[/B][/COLOR]

Okay I've figured this out, in case anyone else runs into the problem using this script with the final version of hardy.  The sed command that replaces lib32 or l32 with l3232 in libgtk2.0 loaders breaks vmware.  You will need to run this sed to fix it.

```
sudo sed -i -e 's/usr\/l3232/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
```

---

### Post by pie[3.14] on 2008-09-22
Hi i am posting this after doing hours of googling. My vmware install would keep saying vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
so i did a lil googling on it and found that vmware leaves a file called not_configured when u do not run the config. well aperently some how it doesn't get deleted so, if u get that error and have configured it simply remove or rename /etc/vmware/not_configured and all should work. :)

---

### Post by waldoppper on 2008-10-13
Success!
I'm on Hardyx64 and had no issues with the script.
Thanks a lot.

---

### Post by zeitler on 2008-10-14
Hi,
I'm trying to install vmware-server in my pc to run Windows XP. 
The vmare's installation works fine and windows installation also run's well.

I'm having a problem with network. I want bridge network, but when I login in windows, the connection is limitated and shows 10Mb/s. I've already tried with NAT controller and without, everthing that I have seen in posts I've tried and nothing. 

Can you please help me?

When I create the bridge it ask's what interface do I want to make the bridge (wlan0 or eth0). What do I choose? I've created both, one with vmnet0 and the other with vmnet2 and I tried to log in windows with both in custom mode or in bridge mode and it still doesn't work.

Thanks in advance and sorry for the bad english?

zeitler

---

### Post by altonbr on 2008-10-14
> **zeitler said:**
> Hi,
I'm trying to install vmware-server in my pc to run Windows XP. 
The vmare's installation works fine and windows installation also run's well.

I'm having a problem with network. I want bridge network, but when I login in windows, the connection is limitated and shows 10Mb/s. I've already tried with NAT controller and without, everthing that I have seen in posts I've tried and nothing. 

Can you please help me?

When I create the bridge it ask's what interface do I want to make the bridge (wlan0 or eth0). What do I choose? I've created both, one with vmnet0 and the other with vmnet2 and I tried to log in windows with both in custom mode or in bridge mode and it still doesn't work.

Thanks in advance and sorry for the bad english?

zeitler

I usually choose 'bridge' as it is the easiest to setup and maintain, and acts like any other node according to your router. As for wlan0 or eth0, that means 'wireless ethernet' and 'ethernet' where 'wireless ethernet' is of course your wireless connection and 'ethernet' is your plugged in connection.

For the best connection, you should use 'eth0' unless you are primarily on your wireless network.

I would try turning off your virtual Windows, blowing away all of the ethernet interfaces and start with only one (bridge, eth0, etc.).

Try that and tell me how it goes.

Maybe login to Windows and run 'ipconfig' in the command-prompt so I can see what connection it is trying to use.

Hope that helps!

---

### Post by pmasereeuw on 2008-10-15
I have been reading somewhere that on a wifi connection, most wifi routers refuse to speak with a network card that pretends to have two ip addresses. Therefore, I set up my vm to use nat, because in that case, all traffic uses the ip of the host.

Note that I am not an expert, it's just something that I once read and which helped me get things going.

Pieter

---

### Post by zeitler on 2008-10-15
Hi. Thanks for the reply.

I have vmnet0 connected to eth0 and vmnet2 to wlan0. When I choose Bridged in network connection, vmnet0 is used by default. I've tried that didn't worked, in custom I choose vmnet2 it didn't work also. 
When I log into windows and I do ipconfig the values of ip and sub-net mask are 0.0.0.0, the other are blank.

I did, in host:

vmnet-bridge -D /dev/vmnet0 wlan0
Turning on bridge to wlan0...
Bringing up interface (backward compatability)
Sleeping forever, bye bye.

it was obvious, it's not for that interface :)

But when I do this
vmnet-bridge -D /dev/vmnet2 wlan0
Turning on bridge to wlan0...
wlan0: Resource deadlock avoided

Is this ok? I always work in wireless mode, and about the router doesn't allow two ip's for the same machine it's not probably because when I worked with windows vmware worked fine. 

Thanks for your replys.
zeitler

---

### Post by altonbr on 2008-10-15
> **zeitler said:**
> Hi. Thanks for the reply.

I have vmnet0 connected to eth0 and vmnet2 to wlan0. When I choose Bridged in network connection, vmnet0 is used by default. I've tried that didn't worked, in custom I choose vmnet2 it didn't work also. 
When I log into windows and I do ipconfig the values of ip and sub-net mask are 0.0.0.0, the other are blank.

I did, in host:

vmnet-bridge -D /dev/vmnet0 wlan0
Turning on bridge to wlan0...
Bringing up interface (backward compatability)
Sleeping forever, bye bye.

it was obvious, it's not for that interface :)

But when I do this
vmnet-bridge -D /dev/vmnet2 wlan0
Turning on bridge to wlan0...
wlan0: Resource deadlock avoided

Is this ok? I always work in wireless mode, and about the router doesn't allow two ip's for the same machine it's not probably because when I worked with windows vmware worked fine. 

Thanks for your replys.
zeitler

I think pmasereeuw was correct when he said that wlan0 only allows one connection at a time. Seems like a good feature but it only a postulation on my part.

Try the VMware/Linux docs.

---

### Post by zeitler on 2008-10-16
Hi 

That's right. Wifi doesn't work but etherlan works fine.

Thanks for all the help.

zeitler

---

### Post by zeiz on 2008-10-20
> **zeitler said:**
> Hi,
I'm trying to install vmware-server in my pc to run Windows XP. 
The vmare's installation works fine and windows installation also run's well.

I'm just tried to install vmware-server-2.0.0.116503.i386 on Hardy according to this tutorial using install_vmware.sh. Obviously I changed tarball's name in the file to current version and I had to change also any-any updates to 200 from 116. Everything was good until the updates: after fetching repositories program printed 404Not found and aborted with deleting all downloaded and extracted files. If 200 is the point then what it should be there instead?
Please  share your successful experience with installation!

---

### Post by altonbr on 2008-10-21
> **zeiz said:**
> I'm just tried to install vmware-server-2.0.0.116503.i386 on Hardy according to this tutorial using install_vmware.sh. Obviously I changed tarball's name in the file to current version and I had to change also any-any updates to 200 from 116. Everything was good until the updates: after fetching repositories program printed 404Not found and aborted with deleting all downloaded and extracted files. If 200 is the point then what it should be there instead?
Please  share your successful experience with installation!

I haven't updated the script for VMware Server 2.0.0 yet, so I would wait for that, or compile it yourself. Messing with a script when you don't know what you're doing is potentially dangerous.

---

### Post by zeiz on 2008-10-21
First of all many thanks for creating of the script and the tutorial!
I installed vmware without using the script as explained in [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)
Thanks bodhi.zazen!
Everything was fine but there is no any icon for vmware in menu and after typing 'vmware' in console firefox opens with invalid certificate notice; after confirming an exception I can see only empty window where "loading..." is shown and "Done" in taskbar. In case of 'sudo vmware' Opera opens instead of Firefox and does show a login window but nothing could be typed in the window. How to start vmware console?

---

### Post by altonbr on 2008-10-21
> **zeiz said:**
> First of all many thanks for creating of the script and the tutorial!
I installed vmware without using the script as explained in [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)
Thanks bodhi.zazen!
Everything was fine but there is no any icon for vmware in menu and after typing 'vmware' in console firefox opens with invalid certificate notice; after confirming an exception I can see only empty window where "loading..." is shown and "Done" in taskbar. In case of 'sudo vmware' Opera opens instead of Firefox and does show a login window but nothing could be typed in the window. How to start vmware console?

I thought VMware added a shortcut? I had code in there at one point, but took it out as I thought it created a duplicate shortcut.

What's the output when you run 'vmware' in the terminal?

Example:
```
$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


```

---

### Post by zeiz on 2008-10-21
I didn't get a shortcut but I do got the console: it just took too long and I thought it's frozen :oops:. I tried several times and last time I forgot to close that tab and went to forums again. Then I was back and found working login box...to face another problem: WinXP CD didn't want to boot! I created VM (12GB/500MB-mem), checked and rechecked HD and CD settings, I inserted CD before power up...). Then I tried another VM for Suse and its DVD also didn't boot. Both medias are bootable and installable for sure...what I'm doing wrong? :confused:
Sorry if it's off topic.

---

### Post by Brian96 on 2008-10-23
Hi, I upgraded my kernel when it came up in the Update Manager, so I ran the script again to get VMWare up to date. The script terminated with this error:

> Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway?

Please advise. Thank you.

---

### Post by CadetD on 2008-10-23
> **Brian96 said:**
> Hi, I upgraded my kernel when it came up in the Update Manager, so I ran the script again to get VMWare up to date. The script terminated with this error:



Please advise. Thank you.

I am getting the same problem after upgrading last night. 
I have tried changing the symlink of gcc from the gcc-4.2. to the gcc-4.1 (the only two on my machine), it fails with different error. 

How can I downgrade to the 4.2.3? Where can the package be downloaded from? 

Thanks.

---

### Post by mongobongo on 2008-10-23
> **Brian96 said:**
> Hi, I upgraded my kernel when it came up in the Update Manager, so I ran the script again to get VMWare up to date. The script terminated with this error:



Please advise. Thank you.

> **CadetD said:**
> I am getting the same problem after upgrading last night. 
I have tried changing the symlink of gcc from the gcc-4.2. to the gcc-4.1 (the only two on my machine), it fails with different error. 

How can I downgrade to the 4.2.3? Where can the package be downloaded from? 

Thanks.

Compiling with the newer gcc 4.2.4 is working fine for me.  Just make sure you follow the Post-Install Configuration steps at [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) before running VMWare Server.

There are some additional steps for 64 bit users at the same link.

---

### Post by CadetD on 2008-10-23
Thanks mongobongo. 

I just realized that the discussion is for VMWARE "Server" I am running Workstation 6. 
Does that make a difference? 

This is 32bit on my laptop. (Didn't want to update my PC which is 64bit yet -- good idea) 

Here is the output of vmware-config.pl: 
> 
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Workstation may crash if you'll continue. Please try to use exactly same
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] yes

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-21-rt/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-21-rt/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-rt'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:83:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from /tmp/vmware-config3/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config3/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config3/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:84:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:65: error: previous declaration of &#8216;poll_initwait&#8217; was here
/tmp/vmware-config3/vmmon-only/linux/driver.c:198: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-rt'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


It ran the post installation steps, just in case. Makes no difference. 

Thanks.

---

### Post by mongobongo on 2008-10-23
> **CadetD said:**
> Thanks mongobongo. 

I just realized that the discussion is for VMWARE "Server" I am running Workstation 6. 
Does that make a difference? 

This is 32bit on my laptop. (Didn't want to update my PC which is 64bit yet -- good idea) 

Here is the output of vmware-config.pl: 


It ran the post installation steps, just in case. Makes no difference. 

Thanks.

Sorry for the delay CadetD.  You might want to check out the step by step at [https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)

Hope that helps.

---

### Post by CadetD on 2008-10-23
I downloaded the latest VMware Wokstation 6.5. 
The installation does not require running vmware-config.pl. Autoconfigured everything and all done. 

Nice improvement. GUI installer. 2 clicks done. They are really investing in Linux ... I hope. 

Thanks for the help.

---

### Post by dmizer on 2008-10-23
This script is not needed to install vmware server.

Install as normal, then perform these commands:
```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

That's it. No script. This process has worked for me for the past 3 or 4 vmware server versions in Hardy.

Fix found here: [http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

---

### Post by altonbr on 2008-10-23
> **Brian96 said:**
> Hi, I upgraded my kernel when it came up in the Update Manager, so I ran the script again to get VMWare up to date. The script terminated with this error:



Please advise. Thank you.

It should work, yes.

> **dmizer said:**
> This script is not needed to install vmware server.

Install as normal, then perform these commands:
```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

That's it. No script. This process has worked for me for the past 3 or 4 vmware server versions in Hardy.

Fix found here: [http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/)

The point of the script is to help people do less on the command-line, since, unfortunately, it is still required to install VMware Server.

---

### Post by dmizer on 2008-10-26
> **altonbr said:**
> The point of the script is to help people do less on the command-line, since, unfortunately, it is still required to install VMware Server.
While I understand this, there are two problems. First of all, your script is still using the any any update which is not needed (and breaks bridging on wireless). Second, your script requires command line work anyway.

You have combined two commands into one line (just as I could have done with my two commands), but really it's the same amount of work in the cli.

Though honestly, for the moment I'm stumped while trying to install VMware server 2 in 64 bit. Vmware is still looking in the wrong place for the gcc pointers and thinks my kernel was compiled against gcc version 4.2.3 instead of 4.2.4.

Ugh, this is always a pain every time a kernel update comes down the pike.

---

### Post by altonbr on 2008-10-26
> **dmizer said:**
> While I understand this, there are two problems. First of all, your script is still using the any any update which is not needed (and breaks bridging on wireless). Second, your script requires command line work anyway.

You have combined two commands into one line (just as I could have done with my two commands), but really it's the same amount of work in the cli.

Though honestly, for the moment I'm stumped while trying to install VMware server 2 in 64 bit. Vmware is still looking in the wrong place for the gcc pointers and thinks my kernel was compiled against gcc version 4.2.3 instead of 4.2.4.

Ugh, this is always a pain every time a kernel update comes down the pike.

I do agree that this script is not fully required anymore, but for the casual user that wants VMware up and running quick, there is no other way but to use the command line. Even for VMware Server 2.0, people are having troubles getting it started. If VMware decided to release fully working .debs that didn't need to be recompiled after every kernel update, then there would be no problem. Until that happens, people can use my script for the 1.0.x series.

If you'd like to update the script and send me your revisions, please feel free to do so.

---

### Post by earthforce_1 on 2008-11-08
Has this script been broken by the latest kernel?  (I am running stock i386 8.10 ubuntu)  It gets as far as attempting to build the server, then borks on the compile:

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:53:
/tmp/vmware-config2/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:16:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:84:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config2/vmmon-only/linux/driver.c:171: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:175: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function &#8216;__LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1781: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by kextyn on 2008-11-10
> **earthforce_1 said:**
> Has this script been broken by the latest kernel?  (I am running stock i386 8.10 ubuntu)  It gets as far as attempting to build the server, then borks on the compile:

...

make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

I've got the same problem.  I'm running 8.10 Server AMD64.

---

### Post by altonbr on 2008-11-10
You guys are using Intrepid and the script is only for Hardy. You shouldn't need my script in Intrepid...

Well, it doesn't need VMware-any-any, so I've heard.

Should I be updating it for Intrepid and remove VMware-any-any?

---

### Post by emulantie on 2008-11-13
> **kextyn said:**
> I've got the same problem.  I'm running 8.10 Server AMD64.

The same message here!
Well, I got the same problem as you guys, Running I386 Ubuntu 8.10. I thought it would actually work when I got the icons and everything. Now I dont have a glue what to do? Im actually impressed that I managed to open the tar.gz files and almost made a complete installation. Not bad for a beginner who doesnt know much about Ubuntu.

Would be grateful to the one who can help me(us) with this!

---

### Post by dmizer on 2008-11-13
> **emulantie said:**
> Would be grateful to the one who can help me(us) with this!
Build it without the script. It will complain about a gcc version conflict, but if you tell it to compile anyway, it will work.

---

### Post by technicallyhesright on 2008-11-23
Hey all, someone was kind enough to post their successful install of vmware server on 8.10 Intrepid Ibex here: [http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/](http://geekzine.org/2008/11/20/install-vmware-server-on-ubuntu-intrepid-810/)  :KS

---

### Post by Berethorn on 2008-12-17
The any-any file cannot be found at the URL in the tutorial!

[http://uruz.org/files/vmware-any-any-update-116.tgz](http://uruz.org/files/vmware-any-any-update-116.tgz)

Just thought I'd point that out. Otherwise the install worked great (after downloading the any-any from another location) thanks! :)

---

### Post by cartisdm on 2009-02-19
If I understood it correctly, I shouldn't have to download the tar file if it's already in the home directory.  I did that, and the script still downloaded it.

....then I messed up what I was doing before the install was complete and had to run the script again and it had to RE-download the file.  Takes over 30 minutes with my connection so it's time consuming...

---

### Post by altonbr on 2009-02-22
> **cartisdm said:**
> If I understood it correctly, I shouldn't have to download the tar file if it's already in the home directory.  I did that, and the script still downloaded it.

....then I messed up what I was doing before the install was complete and had to run the script again and it had to RE-download the file.  Takes over 30 minutes with my connection so it's time consuming...

If the filename is 'VMware-server-1.0.6-91891.tar.gz' and in the directory that the script is running in, then it should not download the file again. I did this just for dial-up and DSL users.

---

### Post by Praetor77 on 2009-08-20
[http://ubuntuforums.org/showpost.php?p=7122645&postcount=53](http://ubuntuforums.org/showpost.php?p=7122645&postcount=53)

This works on Jaunty 2.6.28-15 kernel.... with vmware-server 2

---

