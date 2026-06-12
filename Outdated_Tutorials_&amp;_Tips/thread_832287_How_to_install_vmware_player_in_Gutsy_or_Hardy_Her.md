---
title: "How to install vmware player in Gutsy or Hardy Heron"
date: 2008-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxmaveric on 2008-06-17
Some of my friends have asked me many times how I install Vmware player for Ubuntu 7.10 or 8.04. So here's my basic tutorial. I hope this makes sense everyone. This tutorial will explain how to install VMware Player on Ubuntu Gutsy or Hardy Heron.

Download the most current tar.gz package (VMware-player-2.0.4-93057.i386.tar.gz) from the VMware website.
[http://www.vmware.com/download/player/download.html](http://www.vmware.com/download/player/download.html)

Before you do anything, there are some things you have to look up and download in your Ubuntu system.
First you have to see what linux kernel you are using on your Ubuntu Linux PC.
Bring up your bash shell from the "applications menu bar". Click on "terminal" which is under "accessories". Type in the following command at the bash command line:

uname -r

This command will return the following linux kernel results:

2.6.22-14-generic (Gutsy Gibbon)
or
2.6.24-19-generic (Hardy Heron)


I have 2.6.24-19-generic, so I have to install the linux headers files for my kernel version:
(if your using Ubuntu 7.10 Gutsy install headers for 2.6.22-14-generic kernel)

Enter the following command:

sudo apt-get install linux-headers-2.6.24-19-generic

You also need to make sure you have "build-essential" package installed in your system before you install vmware-player.

Enter the following command:

sudo apt-get install build-essential

Now download VMware Player tar.gz package from the VMware website. At this time the most recent package is: VMware-player-2.0.4-93057.i386.tar.gz.

untar the .tar.gz file using the following command:

tar -xzvf VMware-player-2.0.4-93057.i386.tar.gz

The tar.gz package is now extracted.

Now you need to change into the vmware directory with the following command:

cd vmware-player-distrib

Now it's time for the fun stuff: Installing with the following command:

sudo ./vmware-install.pl

During the installation you must answer some basic questions. For a standard installation enter the following:

In which directory do you want to install the binary files?
[/usr/bin]
What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]
What is the directory that contains the init scripts?
[/etc/init.d]
In which directory do you want to install the daemon files?
[/usr/sbin]
In which directory do you want to install the library files?
[/usr/lib/vmware]
The path &#8220;/usr/lib/vmware&#8221; does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]
In which directory do you want to install the documentation files?
[/usr/share/doc/vmware]
The path &#8220;/usr/share/doc/vmware&#8221; does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]
Before running VMware Player for the first time, you need to configure it by
invoking the following command: &#8220;/usr/bin/vmware-config.pl&#8221;. Do you want this
program to invoke the command for you now?
[yes]
In which directory do you want to install the theme icons?
[/usr/share/icons]
What directory contains your desktop menu entry files? These files have a
.desktop file extension.
[/usr/share/applications]
In which directory do you want to install the application&#8217;s icon?
[/usr/share/pixmaps]
None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel. Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?
[yes]
What is the location of the directory of C header files that match your running
kernel?
[/lib/modules/2.6.22-14-generic/build/include]
None of the pre-built vmblock modules for VMware Player is suitable for your
running kernel. Do you want this program to try to build the vmblock module
for your system (you need to have a C compiler installed on your system)?
[yes]
Do you want networking for your virtual machines? (yes/no/help)
[yes]
Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]
Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]
Do you wish to configure another NAT network? (yes/no)
[no]
Do you want to be able to use host-only networking in your virtual machines?
[yes]
Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]
Do you wish to configure another host-only network? (yes/no)
[no]

None of the pre-built vmnet modules for VMware Player is suitable for your
running kernel. Do you want this program to try to build the vmnet module for
your system (you need to have a C compiler installed on your system)?
[yes]


The installation process is now finished and you can start VMware Player from your Applications Menu under "system tools". (Gnome)

If for some reason you don't like VMware-player and you want to try something else use the following command in the command line to remove Vmware player:

sudo /usr/bin/vmware-uninstall.pl

Have fun!
P.S. if your are looking for vmware virtual images to play around with I suggest the following website:
[http://www.vmware.com/appliances/directory/cat/45](http://www.vmware.com/appliances/directory/cat/45)

If you are interested in making your very own virtual OS images try this website:
[http://www.easyvmx.com/](http://www.easyvmx.com/) (use the Easy-VMX ver 2.0)

Once again have fun!

---

### Post by karlatsaic on 2008-06-24
I am running 64-bit Hardy Heron and the above all works smoothly except I get the message:

The following libraries could not be found on your system:
libX11.so.6
libXtst.so.6
libXext.so.6
libXrender.so.1
libz.so.1
You will need to install these manually before running VMPlayer

I have searched these forums to no avail on this issue. I am pretty sure it's a 32-bit vs. 64-bit issue based on some other posts I saw regarding other applications missing the same libraries. Surely, they must be part of some X Windows package.

---

### Post by karlatsaic on 2008-07-03
> **karlatsaic said:**
> I am running 64-bit Hardy Heron and the above all works smoothly except I get the message:

The following libraries could not be found on your system:
libX11.so.6
libXtst.so.6
libXext.so.6
libXrender.so.1
libz.so.1
You will need to install these manually before running VMPlayer

I have searched these forums to no avail on this issue. I am pretty sure it's a 32-bit vs. 64-bit issue based on some other posts I saw regarding other applications missing the same libraries. Surely, they must be part of some X Windows package.
I accidentally solved this problem by installing the 32-bit firefox and java libraries as described in [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537) . Evidently, the 5 libraries the vmware-player noted as missing are now there after doing that install. vmware-player works perfectly now.

---

### Post by misterphreeze on 2008-07-05
Thank you so much! This thread helped me out alot! And the link with the virtual machines should be good too.

---

### Post by linuxmaveric on 2008-07-10
> **karlatsaic said:**
> I accidentally solved this problem by installing the 32-bit firefox and java libraries as described in [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537) . Evidently, the 5 libraries the vmware-player noted as missing are now there after doing that install. vmware-player works perfectly now.
Glad you got it working. :)
Sorry I never got a chance to help you out. Been busy being a new Daddy :)
I have had problems before getting 64bit Ubuntu to place nice with vmware, but the firefox solution you presented sounds like it did the trick. Have fun.

RR.

---

### Post by linuxmaveric on 2008-07-10
> **misterphreeze said:**
> Thank you so much! This thread helped me out alot! And the link with the virtual machines should be good too.
Your Welcome!
I use vmware alot at work and it is a rather clever piece of software. I'm glad you like the vmware images link. There are so many different flavors of linux, bsd, and solaris that one can play around with using your vmware player. Have fun!
RR.

---

