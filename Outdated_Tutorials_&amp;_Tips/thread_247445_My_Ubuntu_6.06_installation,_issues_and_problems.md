---
title: "My Ubuntu 6.06 installation, issues and problems"
date: 2006-08-30
forum: Outdated Tutorials &amp; Tips
---

### Post by tuga on 2006-08-30
Hello

I have ubuntu running since several months and have compiled some of the installation issues and problems that I have faced.
Some of this information is just copied from the ubuntu forums, ubuntu documentation or are just links. Thanks to all on ubuntu forums who helped me.
Maybe you can find some information that is usefull...

UBUNTU 6.06 INSTALLATION

1.
Install from alternate CD.

2.
Enable all repositories.

3.
Install fglrx driver support:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Reboot.

An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc. 

4.
Share internet connection

Note: Type all the following commands in a root terminal, DO NOT use sudo.
#sudo -i

.1. Start by configuring the network card that interfaces to the other computers on you network:
# ifconfig ethX ip
where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

.2. Then configure the NAT as follows:
# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
where ethX is the network card that the Internet is coming from
# echo 1 > /proc/sys/net/ipv4/ip_forward

.3. Install dnsmasq and ipmasq using apt-get:
# apt-get install dnsmasq ipmasq

.4. Restart dnsmasq:
# /etc/init.d/dnsmasq restart

.5. Reconfigure ipmasq to start after networking has been started:
# dpkg-reconfigure ipmasq

.6. Repeat steps 1 and 2.

.7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf (may not be needed)
# gedit /etc/sysctl.conf

5.
Install flash

6.
Install Thunderbird

7.
Restricted formats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

.1. Sound
Install the following packages to play most proprietary formats using Totem and Rhythmbox, which both come with Ubuntu.
      gstreamer0.10-ffmpeg
      gstreamer0.10-pitfdll
      gstreamer0.10-plugins-bad
      gstreamer0.10-plugins-bad-multiverse
      gstreamer0.10-plugins-ugly
      gstreamer0.10-plugins-ugly-multiverse

Since the version of Totem that comes with Ubuntu doesn't yet play DVDs, the list below also includes packages for the GXine player, which does. For playing encrypted DVDs, refer to DVD section
      gxine
      libxine-main1
      libxine-extracodecs
      w32codecs
Note: to enable w32codecs, see the w32codecs section

.2. Playing encrypted DVDs
The movie players provided in Ubuntu can play back unencrypted DVDs. However, many commercial DVDs are encrypted with a weak algorithm called CSS (the [WikiPedia]Content Scrambling System). You can enable playback of encrypted DVDs with MPlayer, xine and Totem-xine by installing libdvdcss2.
      Installing libdvdcss2
            Applies to all architectures except AMD64
                  Install the libdvdread3 package.
                  Then download the libdvdcss2 library by typing in a terminal:
                  sudo  /usr/share/doc/libdvdread3/examples/install-css.sh

.3. Windows codecs
Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions. You can download the package from an unoffical repository and install it with dpkg:
      wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
      sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

.4. Playing Streaming Video from the Internet
Install the totem-gstreamer-firefox-plugin package

.5. Flash sound in firefox
Install libflash-mozplugin

.6. Fonts and flash
If you are viewing a Flash video and you do not see any text, install the gsfonts and gsfonts-x11 packages

8.
Java
install the sun-java5-bin
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

8.
To have internet after power up.
Add these lines to /etc/rc.local, before the line exit 0:
	ifdown eth1
	ifup eth1
	ipmasq

9.
RAR archives: install unrar
7z archives: install p7zip

10.
Display Microsoft fonts like on Windows:
[http://www.ubuntuforums.org/showthread.php?t=208396](http://www.ubuntuforums.org/showthread.php?t=208396)

11.
Take back the Firefox & Thunderbird icon:
[http://www.ubuntuforums.org/showthread.php?t=199193](http://www.ubuntuforums.org/showthread.php?t=199193)

---

