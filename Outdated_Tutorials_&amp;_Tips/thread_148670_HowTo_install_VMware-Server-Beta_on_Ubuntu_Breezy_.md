---
title: "HowTo install VMware-Server-Beta on Ubuntu Breezy 5.10"
date: 2006-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-03-22
My Original is at:
[http://howtoforums.net/viewtopic.php?t=5](http://howtoforums.net/viewtopic.php?t=5)

------------------------

**Overview:**
I put together this script to automate the installation / pre-installation requirements for "vmhost" servers...
This script consists of 4 parts.
   1. A server install of Ubuntu 5.10 aka Breezy
   2. Running the first script aka Apt-Install-Breezy
   3. Running the second script aka POST-apt-installBREEZY
   4. Download / Install vmware-server-beta

**IMPORTANT: Pre-Installation considerations:**
   1. You downloaded Ubuntu 5.10 Breezy from [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
   2. Installed a fresh copy using the "server" option
   3. Chose the username "vmadmin" during install
   4. Connected to a network with dhcp / internet connection
   5. You must activate the root user using:
```
 sudo passwd root 
```

**Final Results:**
The final configuration, if everything went smooth should be: Ubuntu 5.10 Breezy, VMware-Server-Beta, VMware-Console, FluxBox window manager, VNCserver

Feel free to modify / customize the scripts below however I do recommend you know what you are doing and run this on a testing machine first.
USE AT YOUR OWN RISK!!!

[b][i]Switch user to root & change to the directory were you downloaded / created the files...and begin!
[/b][/i]

**Apt-Install-Breezy**
```

#!/bin/bash
# This Script will bring an Ubuntu 5.10 (breezy) base-server to a vmware host ready system
build="$0"

#Args
newhostname=`echo "$1" |tr '[:upper:]' '[:lower:]'`
newdomain=`echo "$2" |tr '[:upper:]' '[:lower:]'`
newip="$3"
newsubnet="$4"
newbroadcast="$5"
newgateway="$6"
newnameserver="$7"

newkernel="2.6.12-10-686-smp"

currenteth0=`ifconfig |grep Bcast`
currentip=`ifconfig |grep Bcast |cut -d ':' -f2 |cut -d ' ' -f1`
currentsubnet=`ifconfig |grep Bcast |cut -d ':' -f4`
currentbroadcast=`ifconfig |grep Bcast |cut -d ':' -f3 |cut -d ' ' -f1`
#currentgateway=
currentnameserver=`cat /etc/resolv.conf |grep nameserver`
currentkernel=`uname -a |cut -d ' ' -f3`

####################################################

if test $# -lt 7
then
        echo "USAGE: $0 <new hostname> <new domain name> <new ip address> <new subnet> <new broadcast address> <new default gateway> <new dns nameserver ip address>

        Your currnet network settings are:
$currenteth0

---------------------------------------------
MORE CURRENT SETTINGS TO BE CHANGED
Running Kernel:         $currentkernel
Hostname:               $HOSTNAME
IP Address:             $currentip
Subnet Mask:            $currentsubnet
Broadcast Address:      $currentbroadcast
DNS Nameservers:        $currentnameserver

---------------------------------------------

"
        exit 1
fi



clear
echo "
##################################################################
# This Script Will configure the system to be vmware ready       #
# it will change system settings and install the necessary      #
# packages from the internet.                                    #
##################################################################
"
#################### User confirmation before install #####################
echo "####### Final Confirmation Before Install   #######"
echo "####### There is no way back from here !!!! #######"
echo " "
echo "We have gathered all the information necessary to install"
echo "The installation parameters you defined are as follow:"
echo "
WARNING !!!
You are about to change the following system settings

---------------------------------------------
CURRENT         -->     NEW
$currentkernel  -->     $newkernel
$HOSTNAME       -->     $newhostname
$currentip      -->     $newip
$currentsubnet  -->     $newsubnet
$currentbroadcast       -->     $newbroadcast
$currentnameserver      -->     $newnameserver

---------------------------------------------

"
echo " "
echo " "
echo "ARE YOU SURE YOU WANT TO CONTINUE ?!?"
echo -n "YES/NO"; read aa;
test "YES" = "$aa" || (echo; echo "you must type in YES or NO (case matters)")
test "YES" = "$aa" || exit 1


########
echo "configure system locales"
dpkg-reconfigure locales
########

########
echo "changing hostname"
cp -vp /etc/hostname /etc/hostname.orig
echo $newhostname > /etc/hostname

echo "changing /etc/hosts"
cp -vp /etc/hosts /etc/hosts.orig
echo "
127.0.0.1       localhost.localdomain   localhost
$newip          $newhostname $newhostname.$newdomain

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
">/etc/hosts
########

########
echo "changing /etc/resolv.conf"
cp -vp /etc/resolv.conf /etc/resolv.conf.orig
echo "
search $newdomain
domain $newdomain
nameserver $newnameserver
">/etc/resolv.conf
########

########
echo "changing system ip"
cp -vp /etc/network/interfaces /etc/network/interfaces.orig
echo "
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
                   address $newip
                   netmask $newsubnet
                   broadcast $newbroadcast
                   gateway $newgateway
">/etc/network/interfaces
########

########
echo "restarting network..."
/etc/init.d/networking restart
########

########
echo "creating backup of sources.list "
cp -vpr /etc/apt/sources.list /etc/apt/sources.list.orig
echo "
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
" > /etc/apt/sources.list
########

########
# Update Apt and get Packages I install on VMhost's
apt-get update
apt-get dist-upgrade
apt-get install openssh-server x-window-system-core xterm build-essential g++-3.4 xinetd
########

########
#edit sources.list
echo "creating backup of sources.list before changing to universe"
cp -vpr /etc/apt/sources.list /etc/apt/sources.list.bkup
echo "changing sources.list now for installation of pkgs"
echo "
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
" > /etc/apt/sources.list
########

########
echo "installing required pkgs from universe"
apt-get update
apt-get install linux-headers-2.6.12-10 linux-headers-2.6.12-10-686-smp linux-image-2.6.12-10-686-smp fluxbox fluxconf sysstat tightvncserver xtightvncviewer htop iftop wdm
#not sure about these
#vncserver
#xdm

########
echo "restoring sources.list"
mv /etc/apt/sources.list.orig /etc/apt/sources.list
########

#old version 5.04
#apt-get install fluxbox sysstat tightvncserver xfonts-base xvncviewer xfonts-75dpi xfonts-scalable xfonts-100dpi build-essential linux-headers-2.6.10-5-386 fluxconf eterm xterm xfonts-cyrillic mozilla-firefox htop emelfm mc

########
#fix for font issue with vncserver
echo '
#font fix patch
$fontPath .= "/usr/share/X11/fonts/misc/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/100dpi/:unscaled,";
$fontPath .= "/usr/share/X11/fonts/Type1/,";
$fontPath .= "/usr/share/X11/fonts/Speedo/,";
$fontPath .= "/usr/share/X11/fonts/75dpi/,";
$fontPath .= "/usr/share/X11/fonts/100dpi/,";
$fontPath .= "/usr/share/X11/fonts/freefont/,";
$fontPath .= "/usr/share/X11/fonts/sharefont/";
'>>/etc/vnc.conf
########

########
#fix for fluxbox autostartup on startx
echo "exec /usr/bin/fluxbox" > ~/.xsession
su -c "echo 'exec /usr/bin/fluxbox' > ~/.xsession" - vmadmin
########

########
# then to start up vnc automatically create the following script in /etc/init.d/ and link it in rcS.d
echo "
#!/bin/bash
# This script will start VNCserver as the VMadmin user
# Don't forget to make it executable
su - vmadmin -c "vncserver :1"
" >/etc/init.d/vncserver
chmod 760 /etc/init.d/vncserver

# The link command
cd /etc/rcS.d/
ln -s ../init.d/vncserver S99vncserver
########

########
#start vncserver to initiate the password prompt
echo "please type the password for vnc access"
/etc/rcS.d/S99vncserver
########

########
#start xinetd
/etc/init.d/xinetd start
########

########
#start fluxbox automatically in the vnc session
su -c "echo 'exec /usr/bin/fluxbox' >> ~/.vnc/xstartup" - vmadmin
########

#######

echo "


---------------------------------------------
Installation Proccess completed successfully!

After reboot you can use any vncviewer to
login to:
$newip:1 or $newhostname:1
with the password you specified at the prompt.

---------------------------------------------
Summary
New Kernel Installed:   $newkernel
New Hostname:           $newhostname
New IP address:         $newip

---------------------------------------------

Please reboot the server
---------------------------------------------


"

```


**POST-apt-installBREEZY**
```

#!/bin/bash
# Run this script only after you have:
# 1.run Apt-Install-Breezy
# 2.rebooted
#######

#delete debs from apt archive
apt-get clean
echo "apt cache cleaned"

#add fluxbox menu item
su -c "cp -vp ~/.fluxbox/menu ~/.fluxbox/menu.orig" - vmadmin

echo "
[begin] (Fluxbox) {}
    [submenu] (Frequent) {}
        [exec] (VMware-Console) {/usr/bin/vmware-console}
        [exec] (xterm) {xterm}
        [exec] (xtightvncviewer) {/usr/bin/xtightvncviewer}
        [exec] (FluxConfig) {fluxbare}
    [end]
">/home/vmadmin/.fluxbox/menu
su -c "cat ~/.fluxbox/menu.orig |grep -v begin >> ~/.fluxbox/menu" - vmadmin

echo "Menu Items added Successfully"
#######


```


**VMware-Server-Beta install**
After Machine is Setup with Apt-Install-Breezy & POST-apt-installBREEZY
-----------------------------
   1. set the CC envirnment variable to gcc-3.4 before installing vmware
```

export CC=/usr/bin/gcc-3.4

```

   2. Download:
       VMware-server-e.x.p-20925.tar.gz
       VMware-console-e.x.p-20925.tar.gz
       VMware-VmPerlAPI-e.x.p-20925.tar.gz

[b]Note: the scripts are tested with the versions above, they
should work with newer vmware versions as well.[/b]

Browse to the directories were you saved the vmware downloads...
then run each moules intall seperatly...

**HowTo install VMware-server**
tar -xvzf VMware-server-e.x.p-20925.tar.gz
cd vmware-server-distrib
./vmware-install.pl

**HowTo install VMware-console**
```

tar -xvzf VMware-console-e.x.p-20925.tar.gz
cd vmware-console-distrib
./vmware-install.pl

```

**HowTo install the VMware-VmPerlAPI:**
```

tar -xvzf VMware-VmPerlAPI-e.x.p-20925.tar.gz
cd vmware-api-distrib/
./vmware-install.pl

```

----------------------
You should be able to connect / manage your server via:
1. vmware-console from any machine connected on the network.
2. vmware-console from the local machine.
3. vmware-console executed from the vnc session running on :1 ...e.g <vmhost01:1>


I'd like to hear your feedback...
Have Fun !!!  8)

---

