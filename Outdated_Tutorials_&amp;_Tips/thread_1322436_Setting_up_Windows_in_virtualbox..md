---
title: "Setting up Windows in virtualbox."
date: 2009-11-10
forum: Outdated Tutorials &amp; Tips
---

### Post by kio_http on 2009-11-10
**Section 1: Getting it running**
1st Install the full version of virtual box. This is optional but its also free and has more options than the Opensource edition in the Ubuntu represitory.

Add one of the following lines according to your distribution to your /etc/apt/sources.list or if you prefer a GUI method use software sources tool in Ubuntu. Then go to the repositories tab and click add repositories. Do not forget to enter "deb" also

The software sources can be accesed in Synaptic, Kpackagekit and Adept.


[SIZE="4"][COLOR="#ff0000"]Virtualbox Debian based represitories[/COLOR][/SIZE]

```
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
deb http://download.virtualbox.org/virtualbox/debian gutsy non-free
deb http://download.virtualbox.org/virtualbox/debian dapper non-free
deb http://download.virtualbox.org/virtualbox/debian lenny non-free
deb http://download.virtualbox.org/virtualbox/debian etch non-free
deb http://download.virtualbox.org/virtualbox/debian sarge non-free
deb http://download.virtualbox.org/virtualbox/debian xandros4.0-xn non-free
```

Now open terminal. In Gnome and XFCE this is done with Menu > Accessories >Terminal.
In KDE simply search konsole in the menu.

Type in 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6DFBCBAE
```
This authenticates the virtual box repository

```
sudo apt-get update
```
This refreshes the list of software to include your newly added virtual box package.

When the process is over 

type in

```
sudo apt-get install virtualbox-3.0
```
This installs Virtualbox.

Now launch virtual box. This can be done via the menu.

Create a new machine.
[COLOR="#ff0000"]Note[/COLOR]:Windows XP will need around 256 mb RAM to run properly, Windows Vista and windows 7 will need arround 512 MB. (althought Microsoft states 1 Gb)

Create you hard disk also.

Now go in settings of the machine. Under cdrom. If you wish to use an iso image or yoor disk drive. [COLOR="#ff0000"]Iso installation is much faster than cdrom.[/COLOR]

Note: Windows may be slow if you have SWAP and more than 1 Gb Ram. Swap is unnecessary for machines with more than 1Gb RAM you can disable it with this in terminal

```
sudo swapoff &#8211;a
```

**Subsection: Making the USB function work in virtualbox** [COLOR="DarkRed"]Do this only if the USB function doesn't work![/COLOR]
Set up USB for Virtualbox

Note: Only the non-free version has USB support at present. 

For Jaunty/ Karmic

From a terminal run these commands: 
Add yourself to the vboxusers group if not already there: - 
```
 if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi
```
Enter a root shell, eg 
```
 sudo -i
```
In that shell, set up /etc/fstab 
```
 vGid="`grep vboxusers /etc/group|cut -d\: -f3`" # Determine the devgid for the vboxusers group
 if [ "$vGid" ] && [ "`grep usbfs /etc/fstab`" == "" ] ; then
        echo "none /proc/bus/usb usbfs devgid=${vGid},devmode=664 0 0" >>/etc/fstab
        mount -a
 fi
```

Pre-Jaunty

To get USB support, you need the PUEL (non-free) version. Via the GUI, there is an option to enable USB. 

Since Gutsy, /proc/bus/usb is not mounted by default. For Gutsy and Hardy you just need to edit /etc/init.d/mountdevsubfs.sh and uncomment the following lines: 
        #
        # Magic to make /proc/bus/usb work
        #
        ```
mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
```

In Intrepid the lines required to mount usbfs have been removed entirely, so you need to add the following lines to /etc/init.d/mountdevsubfs.sh at the end of the do_start() function. Note that this is subtly different than the lines required for Gutsy/Hardy. the arguments for the domount function are slightly different from previous versions. 

        #
        # Magic to make /proc/bus/usb work
        #
        ```
mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
```

Then run the script that you just edited: 

```
sudo /etc/init.d/mountdevsubfs.sh start
```

In order to give users in the vboxusers group write permissions to the devices in /proc/bus/usb, you'll need to edit some rules in /etc/udev/rules.d. 

Under Gutsy, edit /etc/udev/rules.d/40-permissions.rules to say the following: 
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Under Hardy and Intrepid, edit /etc/udev/rules.d/40-basic-permissions.rules to say the following: 
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

Then, restart the udev service: 
sudo /etc/init.d/udev restart

Now, if you haven't done it already, make sure your user is part of the group vboxusers using the following command: 
sudo usermod -G vboxusers -a `whoami`

Finally, log out and login again to apply these changes.

**Subsection: Installing Windows**
Install Windows and then once logged in click on the virtual box windows. Devices > Install Guest additions.

Although machines with Intel Virtualisation or AMD virtualisation can run 64 bit WIndows in Virtualbox. I recommend 32 bit as [COLOR="#ff0000"]64 bit will double the RAM usage[/COLOR].

In Windows a cdrom appears in "My computer/ Computer" I[COLOR="#ff0000"]f you are running Windows 7 run the setup in vista compatibility mode.[/COLOR]

Feel free to enable Direct X support. I've had no conflicts with it. :KS

Now reboot.

Section 2: Further speeding up.
In Windows press "the windows key" + R

Run dialog will appear.
Enter in 
```
services.msc
```

Disable all things that are useless.

[COLOR="#ff0000"]Windows 7 only![/COLOR]
In start menu search. uac

Open the program "Change user account control settings" and set it to the "DO not dim my desktop"

Sound driver
If your sound doesn't work then the driver is available in Windows update.

Step 3: Its yours, Install what you like.

Install whatever programs you need. It would be a good idea to install .Net and Direct X updates.

[SIZE="5"][COLOR="Red"]Note:[/COLOR][/SIZE] [FONT="Arial Black"]Your copy of Windows must be genuine to legally run it in virtualbox. You may not use the same key as a installed Windows on host. You will have to abide by the same laws that apply for installing on another PC[FONT="Comic Sans MS"][COLOR="Lime"][/COLOR][/FONT][/FONT]

---

### Post by kio_http on 2009-11-11
Other alternatives for virtualbox are

qemu
XEN
vmware
bochs pc

---

### Post by ninjapirate89 on 2009-11-11
Nice basic tutorial. Maybe could be expanded by adding how to use usb devices in the virtual machine.

Edit -> Could also add how to add the GPG key for after adding virtualbox to the sources list.
This is the terminal input to add it for virtualbox 'sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6DFBCBAE' without the quotes of course.

---

### Post by kio_http on 2009-11-11
> **ninjapirate89 said:**
> 
Edit -> Could also add how to add the GPG key for after adding virtualbox to the sources list.
This is the terminal input to add it for virtualbox 'sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6DFBCBAE' without the quotes of course.

GPG key instructions added thanks.

---

### Post by eltama on 2009-11-11
I don't know why but on the 2 machines I've installed VirtualBox, it does not appear on the Applications menus. I had to open System->Preferences->Main Menu and uncheck and check again System Tools->Sun VirtualBox.

---

### Post by kio_http on 2009-11-12
> **eltama said:**
> I don't know why but on the 2 machines I've installed VirtualBox, it does not appear on the Applications menus. I had to open System->Preferences->Main Menu and uncheck and check again System Tools->Sun VirtualBox.

In KDE this is under the the Application > System menu

---

### Post by kio_http on 2009-11-12
> **ninjapirate89 said:**
> Nice basic tutorial. Maybe could be expanded by adding how to use usb devices in the virtual machine.



USB tutorial added!

---

### Post by kio_http on 2009-11-12
Feel free too sugest improvements:KS

---

### Post by kio_http on 2009-11-12
Virtual box USB adapted from [here]("https://help.ubuntu.com/community/VirtualBox/USB")

---

### Post by AlanR8 on 2009-11-12
I install it slightly differently but am sure the results are the same. Seems my method is simpler, unless I'm missing something!

Go to:

> [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

and download and save the version to suit your system. File comes down as a .deb file.

Double click the .deb file to install.

This will put an icon in your start menu AND provide full USB support and sort out premissions for you.

Open VirtualBox and follow the install process for (in my case XP).

Job sorted.

---

### Post by kio_http on 2009-11-12
> **AlanR8 said:**
> I install it slightly differently but am sure the results are the same. Seems my method is simpler, unless I'm missing something!

Go to:



and download and save the version to suit your system. File comes down as a .deb file.

Double click the .deb file to install.

This will put an icon in your start menu AND provide full USB support and sort out premissions for you.



Open VirtualBox and follow the install process for (in my case XP).

Job sorted.
I would have put that in but updates aren't prompted by Ubuntu your way.

Also the permissions problems occur only rarely for some users.

Open VirtualBox and follow the install process for (in my case XP).

---

### Post by AlanR8 on 2009-11-12
Hi kio_htp!

Hear what you say but I DO get notifications when a new version is ready. All I do is repeat the VB install process and all is well!

---

### Post by kio_http on 2009-11-13
> **AlanR8 said:**
> Hi kio_htp!

Hear what you say but I DO get notifications when a new version is ready. All I do is repeat the VB install process and all is well!

Yes you will get alerts via Virtualbox not Ubuntu software update or Kubuntu kpackagekit notifications.

Also GPG is not essential. It just authenticates the repositories and is able to check is archive was wrongly downloaded and corrupt

---

### Post by kio_http on 2009-11-15
Added genuine Windows information

---

### Post by atleastzero on 2009-11-15
I haven't been able to find it in my menus either, but I have had lots of luck opening from Terminal, just do:
 
```
VirtualBox
```
 
Installed Windows XP with only 192MB of RAM, since I only have 512MB total to share with my host. It's worked well so far and even runs Diablo II LoD lag-free.
 
Is there a way to make the guest window stretch even if it's down at 800x600 resolution? Diablo only needs the small resolution but it's a pretty small window to enjoy playing in.
 
Thanks for the tutorial!

---

### Post by kio_http on 2009-11-15
> **atleastzero said:**
> I haven't been able to find it in my menus either, but I have had lots of luck opening from Terminal, just do:
 
```
VirtualBox
```
 
Installed Windows XP with only 192MB of RAM, since I only have 512MB total to share with my host. It's worked well so far and even runs Diablo II LoD lag-free.
 
Is there a way to make the guest window stretch even if it's down at 800x600 resolution? Diablo only needs the small resolution but it's a pretty small window to enjoy playing in.
 
Thanks for the tutorial!

After you install guest additions, you select this option as illustrated in the picture. If it doesn't work direct maximize then restore.

---

### Post by kio_http on 2010-05-11
Updated for Lucid.

---

