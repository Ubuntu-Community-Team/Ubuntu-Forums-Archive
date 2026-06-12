---
title: "HOWTO: NetworkManager with WPA 1&amp;2 Support"
date: 2006-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Jeff250 on 2006-02-03
**Further Clarification:**
There's some history that's been lost since the writing of this guide.  Originally, (say, back in February 2006), Dapper had NO native support for WPA + NetworkManager and had NO plans of including it before the Dapper release.  Fortunately, some time later, Dapper was delayed and WPA + NetworkManager support WAS included after all.  Especially now that Dapper, Ubuntu 6.06, has been released, you should ALWAYS try installing the *network-manager* and *network-manager-gnome* or *knetworkmanager* packages FIRST.  This can be done for Ubuntu by the following code:
```
sudo apt-get install network-manager-gnome
```
or for Kubuntu with the following:
```
sudo apt-get install knetworkmanager
```

ONLY in the event that this does not work should you try the below guide, using it as a base to either get WPA + NetworkManager working or at least get your foot in the ground.  This guide was originally written for getting ipw2100 and ipw2200 chipsets working, but nowadays these *already work in Dapper's NetworkManager* for most people!  However, the guide is slowing expanding to include other drivers, including the Atheros-based chipsets' Madwifi drivers, which have made active improvement since Dapper's version of them.

[SIZE=4]**Introduction**[/SIZE]

NetworkManager is a fancy-dancy service and gnome applet that allows you to browse and connect to wireless networks.  NetworkManager can also switch to a wired network, if available.  Unfortunately, previous versions of NetworkManager have been unable to manage or connect to WPA networks.  When you are done with this guide, you will have the latest version of NetworkManager and wpa_supplicant installed from CVS and have WPA1 and WPA2 support with both TKIP and AEP options working correctly.

This guide assumes that you already have an active Internet connection during setup.  This guide also installs, at best, some beta-quality software.  Although I haven't experienced any problems, some may exist, and you yourself are responsible for any problems that you get into as a result of this guide.  It may hose your system.  Probably not, but if we could predict when our systems get hosed, then why would we ever let that happen? ;)

Potential bad news:  This guide is *only for Ubuntu Dapper*.  Breezy and below users don't have a new enough kernel.

**Downloading required tools**
First thing's first, you need the Universe repository enabled.  If you haven't done this yet, see here:
[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages]("https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages")

This HOWTO also assumes that you've created a "wpa" directory in your home directory, i.e. that you type in at a console:
```
mkdir ~/wpa
``` 
Let's get some nice compiling tools and headers if we don't already have them.
Open up a console and type:
```
sudo apt-get install build-essential cvs subversion automake1.9 gcc-3.4
```
Also, let's grab the linux-headers so that we can compile drivers:
```
sudo apt-get install linux-headers-`uname -r | cut -d'-' -f3`
```
The above command installs a linux-headers-X metapackage.  Note:  If you switch kernel platforms from, say a 386 to a 686 kernel, you WILL need to run the above command again to install the headers for that kernel.

**[SIZE=4]Drivers[/SIZE]**

There are two things we're going to try here--updating to the latest drivers and then installing the latest NetworkManager plus its network-related dependencies.  First, let's take care of the drivers.

**ieee80211 Subsystem (for some drivers, see below)**
*Download the ieee80211 subsystem for the following drivers*:
ipw2100
ipw2200/2915
*You don't need to for the following*:
madwifi, since madwifi doesn't use it
*You really shouldn't install it with the following:*
ipw3945, since ipw3945 breaks with it

Your mileage will probably vary with other unlisted drivers.  If your own chipset's drivers are not on this list and you know enough about them, feel free to reply with the necessary info to enhance this list.

Download this file to your ~/wpa directory:
[http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.1.14.tgz?download](http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.1.14.tgz?download)
Start a console and enter:
```
cd ~/wpa tar -zxvf ieee80211-1.1.14.tgz
cd ieee80211-1.1.14
sudo sh remove-old
sudo rm -rf /lib/modules/$(uname -r)/kernel/net/ieee80211
sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/net/ieee80211*
sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/config/ieee80211*
make
sudo make install
```

**If you have an IPW2100 chipset**
This section is for those who want to have the latest and greatest IPW2100 drivers.
If you have an IPW2200 or IPW2915 chipset, keep scrolling down until you see the section for that.

Download this file to your ~/wpa directory:
[http://prdownloads.sourceforge.net/ipw2100/ipw2100-1.2.1.tgz?download]("http://prdownloads.sourceforge.net/ipw2100/ipw2100-1.2.1.tgz?download")
Start a console and enter:
```
cd ~/wpa
tar -zxvf ipw2100-1.2.1.tgz
cd ipw2100-1.2.1
sudo sh remove-old
make
sudo make install
``` 
Great, if there are no errors, you've got the newest drivers installed.

**If you have an IPW2200 or an IPW2915 chipset**
This section is for those who want the latest and greatest IPW2200/IPW2915 drivers.
Download this file to your ~/wpa directory:
[http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.1.3.tgz?download]("http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.1.3.tgz?download")

```
cd ~/wpa
tar -zxvf ipw2200-1.1.3.tgz
cd ipw2200-1.1.3
sudo sh remove-old
make
sudo make install
``` 
Great, if there are no errors, you've got the newest drivers installed.

**If you have an Atheros-based chipset (Madwifi drivers)**

```
cd ~/wpa
svn checkout http://svn.madwifi.org/trunk madwifi
cd madwifi
make
sudo make install
```

**Your Driver HowTo Here**
If installing a newer driver for your wireless chipset fixed WPA + NetworkManager when it otherwise didn't work, reply so it can be included here!

**A note about updating the drivers**
This is a good time to add that if you want up-to-date IPW drivers, you'll need to reinstall the latest ipw drivers *whenever you update kernels*, even for kernel security updates through apt-get!  A new kernel means that there are new drivers that must again be replaced with the newest ones.

**[SIZE=4][COLOR=black]NetworkManager and Dependencies[/COLOR][/SIZE]**

The second strategy is to update to the latest NetworkManager, beginning with some of its important dependencies.

**Installing latest libnl from svn**
In the console:
```
cd ~/wpa
svn co https://svn.suug.ch/repos/tgr/libnl
cd libnl
./configure
make
sudo make install
sudo mkdir -p /usr/local/lib/pkgconfig
sudo cp libnl-1.pc /usr/local/lib/pkgconfig/
``` 
**Installing lastest wpaupplicant from cvs**
Next thing we've got to install is the latest wpa_supplicant from cvs.  If you already have a version of wpa_supplicant installed via the package manager, uninstall it.  Although wpa_supplicant used to require a patch to work with NetworkManager, the patch is now included in the latest cvs version:

```
cd ~/wpa
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs co hostap
cd hostap/wpa_supplicant
cp defconfig .config
sudo apt-get install cdbs debhelper dpatch libssl-dev libreadline5-dev
make
sudo make install
``` *Careful*:  Did you receive this error?
```
for i in wpa_supplicant wpa_passphrase wpa_cli dynamic_eap_methods; do cp $i /usr/local/sbin/$i; done
cp: cannot stat `dynamic_eap_methods': No such file or directory
make: *** [install] Error 1
``` If so, if you want to use the CVS version for now, edit the Makefile line 12 from this:
```
ALL=wpa_supplicant wpa_passphrase wpa_cli dynamic_eap_methods
``` ...to this:
```
ALL=wpa_supplicant wpa_passphrase wpa_cli# dynamic_eap_methods
``` Then run "sudo make install" again!

**Installing latest NetworkManager from svn**
First thing's first.  Uninstall the network-manager package using apt-get or Synaptic if it's currently installed.  (I've recently edited this to reflect network-manager's switch from cvs to svn.  Let me know if anyone has any issues.)

Now let's download the latest NetworkManager from svn:
```
sudo apt-get install debhelper cdbs gnome-common intltool libgnome-keyring-dev libdbus-glib-1-dev libiw-dev libgnomeui-dev libpanel-applet2-dev libglade2-dev libgconf2-dev libhal-dev libnl-dev libnotify-dev docbook-to-man dhcdbd libnotify-dev
cd ~/wpa
svn co http://svn.gnome.org/svn/NetworkManager
cd NetworkManager/trunk
gedit configure.in
``` 
By default, the compiler is set to treat warnings as errors.  Unfortunately, there will probably be warnings, or at least there have been in the past, so we want to disable this setting.  Press ctrl+f and search for Werror to find the line that looks like this:
```
    CFLAGS="-Wall -Werror -std=gnu89 $CFLAGS"
``` ...and remove "-Werror " such that it looks like this:
```
    CFLAGS="-Wall -std=gnu89 $CFLAGS"
``` Save and close.

We have to edit another file:
```
gedit initscript/Debian/NetworkManager
``` 
And find where it (for some reason) says:
```
DAEMON=/usr/sbin/$NAME
``` And change it to read:
```
DAEMON=/usr/local/sbin/$NAME
``` 
Now we have to make just one more config change to get the applet to work properly:
```
gedit gnome/applet/nm-applet.conf
``` Add this in there (just below the <policy user="root">...</policy> block is a nice place):
```
<policy user="YOURUSERNAME">
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>
``` (Be sure to replace YOURUSERNAME with your actual user name.)
Save and close.  Now do the exact same thing to this file:
```
gedit src/NetworkManager.conf
``` Save and close.

If you don't do the above, then you'll probably get dbus security errors when you try to run nm-applet.

Now let's 
```
./autogen.sh
make
sudo make install
``` 
Now we have to do some system-specific stuff that the svn version doesn't install by default:
```
sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/
sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/
sudo cp initscript/Debian/NetworkManager /etc/init.d/
sudo update-rc.d -f NetworkManager remove
sudo update-rc.d NetworkManager start 30 2 3 4 5 . stop 70 0 1 6 .
``` 
Hopefully that went well.  Now there's a few dozen different services and drivers we could restart to get this working without rebooting, but let's just reboot instead.

[size="4"]**Conclusion**[/size]

When Ubuntu comes up, try running nm-applet from the console.  You will have an icon in the notification area, and you should be able to use it to see and connect to WPA networks!  If this is working properly, add it to the startup by going to the System menu on the gnome panel, Preferences, then Sessions.  Go to the Startup Programs tab, and add nm-applet.  Now the NetworkManager applet will start up automatically!

If it's not working properly and you want to further debug the problem, you can try this:
```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
``` ... as this will give you console output, for example, as to what's going on on the network side of things, since nm-applet will just return applet errors.

Phew!  It's over now!  Hopefully you're now enjoying your newfound WPA support and not reinstalling Ubuntu! ;)

[size="4"]**Uninstall**[/size]

**Network Manager:**
```
sudo rm /etc/dbus-1/system.d/NetworkManager.conf
sudo rm /etc/dbus-1/system.d/nm-applet.conf
sudo rm /etc/init.d/NetworkManager
sudo update-rc.d -f NetworkManager remove
cd ~/wpa/NetworkManager/trunk
sudo make uninstall
```**wpa_supplicant:**
```
sudo rm /usr/local/sbin/wpa_*
```**libnl:**
```
sudo rm /usr/local/lib/libnl*
sudo rm -r /usr/local/include/netlink
sudo rm /usr/local/lib/pkgconfig/libnl-1.pc
```**Drivers:**
Reinstall your kernel image from the Ubuntu repositories.
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo apt-get install --reinstall linux-restricted-modules-`uname -r`
```

---

### Post by robban on 2006-02-14
Hi!

Thanks for a great howto!
However, things are not working quite yet.

I am having trouble connecting to a network with wpa2-psk/TKIP.
The router does not broadcast its ESSID.
All non-encrypted networks work like a charm

From the debugout it looks like its timing out.
Found others who where struggeling with this at the networkmanager mailing-lists,
but no solution.

Have anyone else encountred this, and do anyone know of a solution?

This is the output from networkmanager:

NetworkManager: <information>   Activation (eth1) successful, device activated.
NetworkManager: <debug info>    [1139929332.754570] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'LEWlan01'
NetworkManager: <information>   User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / LEWlan01
NetworkManager: <information>   Deactivating device eth1.
CTRL-EVENT-TERMINATING - signal 15 received
NetworkManager: <information>   Device eth1 activation scheduled...
NetworkManager: <information>   Activation (eth1) started...
NetworkManager: <information>   Activation (eth1) Stage 1 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 (Device Prepare) started...
NetworkManager: <information>   Activation (eth1) Stage 2 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth1) Stage 2 (Device Configure) starting...
NetworkManager: <information>   Activation (eth1/wireless): access point 'LEWlan01' is unencrypted, no key needed.
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD eth1                wext    /var/run/wpa_supplicant '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 2'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ADD_NETWORK'
NetworkManager: <information>   SUP: response was '0'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 ssid 4c45576c616e3031'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 scan_ssid 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <information>   SUP: response was 'OK'
Trying to associate with SSID 'LEWlan01'
NetworkManager: <information>   Activation (eth1) Stage 2 (Device Configure) complete.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
NetworkManager: <information>   eth1: link timed out.
NetworkManager: <information>   Old device 'eth1' activating, won't change.
NetworkManager: <information>   Activation (eth1/wireless): association took too long (>20s), failing activation.
NetworkManager: <information>   Activation (eth1) failure scheduled...

---

### Post by Jeff250 on 2006-02-16
About all you can do is occassionally check this file for updates:
[http://cvs.gnome.org/viewcvs/NetworkManager/ChangeLog?view=log](http://cvs.gnome.org/viewcvs/NetworkManager/ChangeLog?view=log)
and update the source from CVS and reinstall if you suspect that it might be fixed.

If you're feeling brave, you can join the mailing list and report the bug too.

---

### Post by mrogers on 2006-02-18
Fantastic howto!!! I can't tell you how thrilled I am to finally see "WPA" listed as an option in Network Manager. However, I can't connect to my home WPA network! I've just got a Linksys WRT54G with regular WPA TKIP on, a Dell 700m with Intel ipw2200 and after I eneter my password for the network it sits there and tries to connect for awhile but ultimately gives up and presents me with the password dialog box once again. I followed every instruction to the letter in the How-to, and (for once) didn't experience a single problem -- everything went just as you said. I'm on Dapper nightly 20060217.2 (fresh install yesterday). 

Any ideas why it can't authenticate? I did have NM and wpasupplicant installed via respositories prior to this howto, but I removed them as you instructed. I don't know if that has anything to do with it, but I though I'd mention it. Thanks for anyone's help.

---

### Post by mrogers on 2006-02-18
Uh-oh it looks like I have a bigger problem. Ever since following this how-to, I can't seem to connect to non-secure networks either. I can't figure it out. Help! (EDIT: to be more accurate, it connects to the insecure networks but I can't get an IP. Manually running dhclient doesn't work.)

Also, does anyone know where Network Manager stores its list of preferred networks?

UPDATE: when I run NetworkManager --no-daemon and look at the output, the DHCP request times out on every network. And what I think is wierd is that for every network it tries to connect to it says the frequency is 0 MHz. ?

I'd really appreciate someone's help on this. At least before I could connect to non-WPA wireless networks; now I can't connect to anything.

---

### Post by Jeff250 on 2006-02-18
NM stores the preferred networks using gconf.
You can browse the settings by typing in gconf-editor at a terminal.  Then the networks will be stored in /system/networking/wireless/networks

I was recently at a friends place who has a Linksys WRT54G V5.  I have a WRT54G V4 with the latest firmware, and everything works fine.  However, with my friend's V5 and the stock firmware, I couldn't connect either manually with wpa_supplicant or using NM.  I finally convinced him to upgrade his firmware to the latest version, but then I could only connect with wpa_supplicant.  NM still wouldn't work.

The V5 is based on an entirely different (and actually technologically inferior) platform than the V4, so I'm not really surprised that there's a discrepancy.  But it goes to show that your mileage can vary, even from AP to AP.  I guess another thing that you could take from this is that if anyone is in the market for a wireless router, the Linksys WRT54G V4 (or WRT54GL--same model) seems to be a winner.

The IP issue that you're having though is strange.  If you plug in a network cable, is NM capable of getting an IP then?

---

### Post by mrogers on 2006-02-18
Thanks. I can see the keys in gconf, but I can't delete them. What if I want to clear out my preferred wifi networks?

I have a Linksys WRT54G v4. And I can't connect to other wireless routers (like my secondary Netgear one or a separate Linksys one) either, so the router isn't the issue.

NM has no problem getting an IP for the wired connection. Only wireless can't auto-configure an IP.

---

### Post by Jeff250 on 2006-02-19
You can right-click the values in the right display and unset them.  I've found in the past that if you unset all of the values in a directory, the directory will disappear the next time you run gconf-editor.

If you want to delete the keys, these are stored in the gnome keyring.  You can access and delete these using gnome-keyring-manager, which if you don't have, it is downloadable in the repositories.  You can run it using the same name.

---

### Post by mrogers on 2006-02-19
Well I went through the whole how-to again just to make sure I didn't miss anything, but I still can't get an IP from any wireless network now. I really don't know what to do at this point.

---

### Post by Whoopie on 2006-02-19
For ipw2200-1.0.12 and kernel 2.6.15, you need a patch to get DHCP working.

The bug is mentioned under [http://www.bughost.org/bugzilla/show_bug.cgi?id=919](http://www.bughost.org/bugzilla/show_bug.cgi?id=919).

The patch is available there.
Direct link: [http://www.bughost.org/bugzilla/attachment.cgi?id=674](http://www.bughost.org/bugzilla/attachment.cgi?id=674)

Best regards,
Whoopie

---

### Post by mrogers on 2006-02-19
Whoopie: YES! Thank you! You're awesome, I now have completely automatic wireless networking in linux (with WPA) for the first time.

---

### Post by Jeff250 on 2006-02-20
Nice, I'll add a note about this in the HOWTO.

---

### Post by Jeff250 on 2006-02-21
Yesterday, an update to dhcp3 broke my NM such that the applet would only make it as far as the first light being lit.  Fortunately, today, another dhcp3 update seems to have fixed that problem.  I don't know if anyone else experienced this, but it seems to be resolved.

P.S.
There's a new IPW2200 driver release to fix the DHCP bug.  I'm going to update the guide to accommodate.

---

### Post by godilleur on 2006-02-22
First of all, great guide, much appreciated.  I'm having a little bit of trouble however.  When I go to install NM, I type ./autogen.sh and I get this:
```
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.7...
  testing automake-1.7... not found.
  testing automake-1.8... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build NetworkManager.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.34.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
Checking for required M4 macros...
  glib-gettext.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build NetworkManager
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

Am I missing anything short of downloading glib-gettext, or is there some package I should have installed that would include that?

---

### Post by Jeff250 on 2006-02-23
Have you "sudo apt-get build-dep network-manager"?

---

### Post by oscar on 2006-02-23
Thanks for this excellent howto, I now have my wireless working perfectly on a nearly clean install of dapper flight 4.

I did have a few issues though:

Firstly you do not mention anywhere updating the wireless firmware. I downloaded mine from:
[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
I extracted the files and then installed using:
```
cp *.fw /lib/firmware/$(uname -r)/
```
I am not sure if this is necessary or even what the version of the firmware already installed by default is but other howtos I have read for WPA install it.

Secondly I didnt have the source universe repositories enabled, I did have the binary but got an error when trying to 
```
sudo apt-get build-dep wpasupplicant
```
Uncommenting the correct line in /etc/apt/sources.list solved it.

Finally i didnt have the dhcdbd package installed which caused an error doing the:
```
./autogen.sh
```
solved by apt-get

I also have an issue with network manager because it prompts me for my password to access the keyring every time I boot up, is there any way around this?

* Some of the steps listed here might not be 100% right, I did have a more detailed message composed but hit Shift+Backspace and crashed X, think I have solved that now.

---

### Post by Jeff250 on 2006-02-23
> I am not sure if this is necessary or even what the version of the firmware already installed by default is but other howtos I have read for WPA install it.

This is unnecessary because Dapper already includes the latest firmware for the IPW chips.  In the case of the IPW2200, this is v2.4

> Secondly I didnt have the source universe repositories enabled

I'll add a note about specifically enabling the source repositories.

> i didnt have the dhcdbd package

Hmm, I don't know how this one got left out, but you're right in that it's not installed by default by Ubuntu.  I'll add this to the NM install instructions.

> I also have an issue with network manager because it prompts me for my password to access the keyring every time I boot up, is there any way around this?

Not to my knowledge.  I know of no way of getting NM to not use the gnome keyring, so, unfortunately this is a side effect.*  If there's a solution, it might be in configuring the gnome keyring to somehow remember any password forever.  This doesn't seem immediately possible, but doing so would help this annoying side effect with all keyring applications.  Gnome keyring is anal about not accepting 0-length passwords too.

* Actually you can choose to not store your password in the keyring, but then you're in an even worse predicament, having to retype your WPA password every time you boot up.

---

### Post by godilleur on 2006-02-23
[QUOTE=Jeff250]Have you "sudo apt-get build-dep network-manager"?[/QUOTE]

Well, I thought I did, ha.

Installing now....

---

### Post by godilleur on 2006-02-23
Worked great!

Thanks for the help.

---

### Post by zachtib on 2006-02-23
does anyone know what the statis of this working with an atheros card is? I can connect to my pw anetwork fine with my card from the commandline, but would like it to integrate w/ network manager

---

### Post by JazzSax on 2006-02-26
Hello,

I just finished following the tut and it worked! I finally was able to connect to my WPA2 home network.....until the next reboot!. After the reboot I lost all connection with my AP. Network Manager doesn't even show it on the list anymore. It is also sketchy with other AP's that it previously saw before the reboot. Sometimes I see them, other times not. I am using an Intel 2915 with DHCP through a Linksys WRT54GS v1.1 with latest firmware. ipw220-1.1.0, and ieee80211-1.1.12. Any suggestions would be greatly appreciated. Thanks


Erik

P.S. All other PC's on my network are obtaining IP's and connect properly

---

### Post by Darrena on 2006-02-26
[QUOTE=zachtib]does anyone know what the statis of this working with an atheros card is? I can connect to my pw anetwork fine with my card from the commandline, but would like it to integrate w/ network manager[/QUOTE]

One of the Network Manager Devs (Robert Love) has it working but I have had no success.  Here are his posts on the NetworkManager Mailing list on the subject:
------------------------------------------
Works for me like a charm.  I bump the timeout to 90s and have Dan's
enc_capa patch.  Otherwise, everything just works.

Using NM CVS HEAD and madwifi-ng r1451 and wpa_supplicant 0.4.8 (not
even the latest of the latter two).

       Robert Love


On Fri, 2006-02-24 at 15:10 -0500, Darren Albers wrote:
>
> I will try those versions, where do I bump the timeout at?

NM_SUPPLICANT_TIMEOUT in src/nm-device-802-11-wireless.c.  Around line
2200.

> Thanks!

De nada.

--------------------------------------------------------------

The patch he is referencing that Dan Williams posted is:
--- ./net80211/ieee80211_wireless.c.enccapa     2006-01-24 09:45:12.000000000 -0500
+++ ./net80211/ieee80211_wireless.c     2006-01-24 09:46:16.000000000 -0500
@@ -976,6 +976,9 @@
       range->min_frag = 256;
       range->max_frag = 2346;

+       range->enc_capa = IW_ENC_CAPA_WPA | IW_ENC_CAPA_WPA2 |
+               IW_ENC_CAPA_CIPHER_TKIP | IW_ENC_CAPA_CIPHER_CCMP;
+
       return 0;
 }

--------------------------------------

I have an Atheros A/B/G card and have had no luck at all with it so if you happen to get it working I would love to hear about it.

---

### Post by zachtib on 2006-02-27
[QUOTE=Darrena]One of the Network Manager Devs (Robert Love) has it working but I have had no success.  Here are his posts on the NetworkManager Mailing list on the subject:
------------------------------------------
Works for me like a charm.  I bump the timeout to 90s and have Dan's
enc_capa patch.  Otherwise, everything just works.

Using NM CVS HEAD and madwifi-ng r1451 and wpa_supplicant 0.4.8 (not
even the latest of the latter two).

       Robert Love


On Fri, 2006-02-24 at 15:10 -0500, Darren Albers wrote:
>
> I will try those versions, where do I bump the timeout at?

NM_SUPPLICANT_TIMEOUT in src/nm-device-802-11-wireless.c.  Around line
2200.

> Thanks!

De nada.

--------------------------------------------------------------

The patch he is referencing that Dan Williams posted is:
--- ./net80211/ieee80211_wireless.c.enccapa     2006-01-24 09:45:12.000000000 -0500
+++ ./net80211/ieee80211_wireless.c     2006-01-24 09:46:16.000000000 -0500
@@ -976,6 +976,9 @@
       range->min_frag = 256;
       range->max_frag = 2346;

+       range->enc_capa = IW_ENC_CAPA_WPA | IW_ENC_CAPA_WPA2 |
+               IW_ENC_CAPA_CIPHER_TKIP | IW_ENC_CAPA_CIPHER_CCMP;
+
       return 0;
 }

--------------------------------------

I have an Atheros A/B/G card and have had no luck at all with it so if you happen to get it working I would love to hear about it.[/QUOTE]

I'll look into it, thanks

---

### Post by Brimmy on 2006-03-03
Great how-to!!!
I do have one problem, I get this error when I run ./autogen.sh

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.7...
  testing automake-1.7... not found.
  testing automake-1.8... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.10.0
checking for intltool >= 0.30...
  testing intltoolize... found 0.34.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `../..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
cp: cannot create regular file `po/Makefile.in.in': No such file or directory
intltoolize: cannot copy '/usr/share/intltool/Makefile.in.in' to 'po/Makefile.in.in'


Any help would be great.

Brimmy

---

### Post by Jeff250 on 2006-03-03
/usr/share/intltool/Makefile.in.in
is included in the package 'intltool'.  It should have been downloaded when you typed in ```
apt-get build-dep network-manager
```

---

### Post by Brimmy on 2006-03-03
Well I ran apt-get again this is what I got.

sudo apt-get build-dep network-manager
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Ran ./autogen.sh and got the same message?

---

### Post by Jeff250 on 2006-03-03
Does the file '/usr/share/intltool/Makefile.in.in' exist?
Is there a 'po' directory in your Network Manager source directory?

---

### Post by daimer77 on 2006-03-04
Hello there, I have followed every single step of the guide, but I keep getting an error when I do the autogen.sh.

Is there a detail I miss or could it be lack of packages on my Dapper. It is a pure new Dapper from yesterday, untouched and ready for WPA :)

Any suggestions highly appreciated, since I seems to be the only one without a working WPA at the moment ;=)

Best regards, and thanks for a nice guide anyway.

Br, Daniel Mersebak

Here comes the console ouput:


---------------------------------------

... checking for GTK... yes
checking for GDK_PIXBUF... yes
checking for GLADE... yes
checking for GCONF... yes
checking for GNOME_KEYRING... yes
checking for NOTIFY... yes
checking for LIBNL... configure: error: Package requirements (libnl-1) were not met:

No package 'libnl-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBNL_CFLAGS
and LIBNL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Jeff250 on 2006-03-04
Try repeating the section entitled "Installing latest libnl from svn" and check for any error messages.

---

### Post by daimer77 on 2006-03-04
I just installed the packages and reran the autogen.sh thing.

But now I have major trouble start networking with WPA. I get  following output from /var/log/syslog ->

-------------------

Mar  4 21:00:44 localhost anacron[4504]: Anacron 2.3 started on 2006-03-04
Mar  4 21:00:44 localhost anacron[4504]: Normal exit (0 jobs run)
Mar  4 21:00:44 localhost NetworkManager: <information>^Istarting... 
Mar  4 21:00:44 localhost NetworkManager: <WARNING>^I nm_dbus_init (): nm_dbus_init() could not acquire the NetworkManager service.   Message: 'Connection ":1.3" is not a
llowed to own the service "org.freedesktop.NetworkManager" due to security policies in the configuration file' 
Mar  4 21:00:44 localhost NetworkManager: <ERROR>^I[1141502444.149733] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus sec
urity policy was not loaded. 
Mar  4 21:00:44 localhost NetworkManager: traceback: 
Mar  4 21:00:44 localhost NetworkManager: ^I/usr/local/sbin/NetworkManager(main+0x3e4) [0x8066507] 
Mar  4 21:00:44 localhost NetworkManager: ^I/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0x77cb0ea2] 
Mar  4 21:00:44 localhost NetworkManager: ^I/usr/local/sbin/NetworkManager [0x8052c61] 
Mar  4 21:00:44 localhost /usr/sbin/cron[4530]: (CRON) INFO (pidfile fd = 3)
 Mar  4 21:00:44 localhost /usr/sbin/cron[4531]: (CRON) STARTUP (fork ok)
Mar  4 21:0

---

### Post by Jeff250 on 2006-03-04
Make sure you did this part without any errors:

> Now we have to make just one more config change to get the applet to work properly:
```
gedit gnome/applet/nm-applet.conf
```
Add this in there (just below the <policy user="root">...</policy> block is a nice place):
```
<policy user="YOURUSERNAME">
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>
```
(Be sure to replace YOURUSERNAME with your actual user name.)
Save and close.  Now do the exact same thing to this file:
```
gedit src/NetworkManager.conf
```
Save and close.

If you don't do the above, then you'll probably get dbus security errors when you try to run nm-applet.

. . .

Now we have to do some system-specific stuff that the CVS version doesn't install by default:
```
sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/
sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/
```

---

### Post by Brimmy on 2006-03-05
> Does the file '/usr/share/intltool/Makefile.in.in' exist?
Is there a 'po' directory in your Network Manager source directory?

Yes they both exist.  I guess this one is tough!!

I am running kernel 2.6.15-16, could that be the problem?

---

### Post by Brimmy on 2006-03-05
Where does autogen copy the Makefile.in.in from?  I thought it was from /usr/share/intltool/Makefile.in.in, but it's not coping it from there, I rename that file to Makefile.in.old and deleted the one from po/Makefile.in.in and ran autogen.sh again and it copied the Makefile.in.in file from somewhere else?.  I also notice that the Makefile.in.in is larger than the one from usr/share/intltool/Makefile.in.in

---

### Post by xrado on 2006-03-05
great howto! first time that i got wireless working on my laptop..thx!

but i have one problem, every time i connect via wireless i have to enter dsn to resolve.conf again. Looks like network manager is managing this file. i got it empty every time.  (im using statis ip, not dhcp)

where do i set dns?

---

### Post by MichaëlVD on 2006-03-05
I've found these bugs on WPA support:
[http://bugzilla.gnome.org/show_bug.cgi?id=161376](http://bugzilla.gnome.org/show_bug.cgi?id=161376)
[http://bugzilla.gnome.org/show_bug.cgi?id=301311](http://bugzilla.gnome.org/show_bug.cgi?id=301311)
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/24295](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/24295)

However, no indication of plans/progress...

I would be very grateful for easy to use WPA support in Ubuntu... I've tried following the Howto ([https://wiki.ubuntu.com/WPAHowto)](https://wiki.ubuntu.com/WPAHowto)), but I never got it to work...

Edit: WPA should be easier with the newly released NetworkManager 0.6, right? If only installing that from source would work for me...

---

### Post by xenoxaos on 2006-03-05
i'm having problems on breezy, 

I get an error 

checking for DBUS... configure: error: Package requirements (dbus-glib-1 >= 0.60) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

any help

---

### Post by Jeff250 on 2006-03-05
[QUOTE=Brimmy]Yes they both exist.  I guess this one is tough!!

I am running kernel 2.6.15-16, could that be the problem?[/QUOTE]

I've previously tested it under that kernel without any problems.

[QUOTE=Brimmy]Where does autogen copy the Makefile.in.in from?  I thought it was from /usr/share/intltool/Makefile.in.in, but it's not coping it from there, I rename that file to Makefile.in.old and deleted the one from po/Makefile.in.in and ran autogen.sh again and it copied the Makefile.in.in file from somewhere else?.  I also notice that the Makefile.in.in is larger than the one from usr/share/intltool/Makefile.in.in[/QUOTE]

Wow, I wish I could say what was going on there. :confused: 

[QUOTE=xrado]great howto! first time that i got wireless working on my laptop..thx!

but i have one problem, every time i connect via wireless i have to enter dsn to resolve.conf again. Looks like network manager is managing this file. i got it empty every time.  (im using statis ip, not dhcp)

where do i set dns?[/QUOTE]

Unfortunately, NM currently does not support static IP's.

[QUOTE=MichaëlVD]I've found these bugs on WPA support:
[http://bugzilla.gnome.org/show_bug.cgi?id=161376](http://bugzilla.gnome.org/show_bug.cgi?id=161376)
[http://bugzilla.gnome.org/show_bug.cgi?id=301311](http://bugzilla.gnome.org/show_bug.cgi?id=301311)
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/24295](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/24295)

However, no indication of plans/progress...

I would be very grateful for easy to use WPA support in Ubuntu... I've tried following the Howto ([https://wiki.ubuntu.com/WPAHowto)](https://wiki.ubuntu.com/WPAHowto)), but I never got it to work...

Edit: WPA should be easier with the newly released NetworkManager 0.6, right? If only installing that from source would work for me...[/QUOTE]

With the .6 release, I'm thinking about making packages, especially since the latest Dapper kernel, the -17 release, seems to already include the necessary WPA driver support for IPW (either that, or I'm going crazy.)  Unfortunately, I'm going to have to read up on how this is done.

[QUOTE=xenoxaos]i'm having problems on breezy, 

I get an error 

checking for DBUS... configure: error: Package requirements (dbus-glib-1 >= 0.60) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

any help[/QUOTE]

I can't really help you with Breezy except try following the thread that I link to at the top of the HOWTO where a Breezy user and I got it working.  Note that this involves installing a new kernel and lots of other things that would make dist-upgrading to Dapper probably a better idea.

---

### Post by Brimmy on 2006-03-06
Well I wiped my drive, reinstalled Breezy, upgraded to Dapper, went through all of the steps again and i still get hung up on the ./autogen.sh with the same error?


checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.7...
  testing automake-1.7... not found.
  testing automake-1.8... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.10.0
checking for intltool >= 0.30...
  testing intltoolize... found 0.34.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `../..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

[B]Running intltoolize...
cp: cannot create regular file `po/Makefile.in.in': No such file or directory
intltoolize: cannot copy '/usr/share/intltool/Makefile.in.in' to 'po/Makefile.in.in'
[/B]

Please any suggestions on this?

---

### Post by Brimmy on 2006-03-07
Well i went as far as downloading dapper cd 4 iso, installed it went through all the steps and i still get hung up on the ./autogen.sh, with the same error.  So i give up, if i need to use wireless i'll boot to Windows.

Thanks for the help
Brimmy

---

### Post by bugmenot on 2006-03-08
FYI:
[QUOTE=mailed by j from bootlab.org]i have some cvs packages sitting on my laptop, but did not find the time
to package 0.6 yet, after reading scotts final words on that right now,
i will look into putting some packages up. im traveling the next two
weeks, not sure if that includes waiting times that would allow me to do
that or just prevent me from looking into it all together. j
 
into that.

> Salve j,
>  
> during the breezy phase you did the u.-community an invaluable service in  
> packaging NM and having the repository on bootlab.org.
> Will you consider doing the same with version 0.6.0 for dapper?
> [https://lists.ubuntu.com/archives/ubuntu-devel/2006-March/016170.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-March/016170.html)
[/QUOTE]

---

### Post by Brimmy on 2006-03-08
well i was able to compile NetworkManager [COLOR="Red"]WOOOHOOOO[/COLOR].  I completed the how to successfully, rebooted and had the nm-applet running....sort of.  When i move my mouse over the applet it tell me "No network devices".  I can kill NM and run it manually, and it will connect to my wired (eth0) fine.  But when i try to connect at work using wireless (eth1) i can not connect.  Trying to connect using WPA2 Enterprise PEAP with domain\username as identity with no success.  The IAS server doesn't even see me connect for authenication?  Did i miss something?

Here is what i clipped from my console

NetworkManager: <debug info>    [1141849428.412154] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'dentald'
NetworkManager: <information>   User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / dentald
NetworkManager: <information>   Deactivating device eth1.
NetworkManager: <information>   Device eth1 activation scheduled...
NetworkManager: <information>   Deactivating device eth0.
NetworkManager: <information>   Activation (eth1) started...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (eth1/wireless): access point 'dentald' is encrypted, and a key exists.  No new key needed.
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD eth1                wext    /usr/local/var/run/wpa_supplicant        '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 2'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ADD_NETWORK'
NetworkManager: <information>   SUP: response was '0'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 ssid 64656e74616c64'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 scan_ssid 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 proto WPA2'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 eap PEAP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 identity "dentald\jeronim1"'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 password "cardfive"'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   wpa_supplicant(6500): Global control interface '/usr/local/var/run/wpa_supplicant-global'NetworkManager: <information>   wpa_supplicant(6500): RX global ctrl_iface - hexdump_ascii(len=59):
NetworkManager: <information>   wpa_supplicant(6500):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et
NetworkManager: <information>   wpa_supplicant(6500):      68 31 09 09 77 65 78 74 09 2f 75 73 72 2f 6c 6f   h1__wext_/usr/lo
NetworkManager: <information>   wpa_supplicant(6500):      63 61 6c 2f 76 61 72 2f 72 75 6e 2f 77 70 61 5f   cal/var/run/wpa_
NetworkManager: <information>   wpa_supplicant(6500):      73 75 70 70 6c 69 63 61 6e 74 09                  supplicant_ 
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1             wext    /usr/local/var/run/wpa_supplicant        '
NetworkManager: <information>   wpa_supplicant(6500): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/usr/local/var/run/wpa_supplicant' bridge 'N/A'
NetworkManager: <information>   wpa_supplicant(6500): Initializing interface (2) 'eth1'
NetworkManager: <information>   wpa_supplicant(6500): EAPOL: SUPP_PAE entering state DISCONNECTED
NetworkManager: <information>   wpa_supplicant(6500): EAPOL: KEY_RX entering state NO_KEY_RECEIVE
NetworkManager: <information>   wpa_supplicant(6500): EAPOL: SUPP_BE entering state INITIALIZE
NetworkManager: <information>   wpa_supplicant(6500): EAP: EAP entering state DISABLED
NetworkManager: <information>   wpa_supplicant(6500): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(6500): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(6500): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
NetworkManager: <information>   wpa_supplicant(6500):   capabilities: key_mgmt 0xf enc 0xf
NetworkManager: <information>   wpa_supplicant(6500): Own MAC address: 00:13:ce:51:08:3f
NetworkManager: <information>   wpa_supplicant(6500): r_wext_set_wpa
NetworkManager: <information>   wpa_supplicant(6500): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6500): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6500): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6500): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(6500): wpa_driver_wext_set_countermeasures
NetworkManager: <information>   wpa_supplicant(6500): wpa_driver_wext_set_drop_unencrypted
NetworkManager: <information>   wpa_supplicant(6500): Setting scan request: 0 sec 100000 usec
NetworkManager: <information>   wpa_supplicant(6500): Added interface eth1
NetworkManager: <information>   wpa_supplicant(6500): Wireless event: cmd=0x8b06 len=8
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=9):
NetworkManager: <information>   wpa_supplicant(6500):      41 50 5f 53 43 41 4e 20 32                        AP_SCAN 2 
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=11):
NetworkManager: <information>   wpa_supplicant(6500):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK 
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=33):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss
NetworkManager: <information>   wpa_supplicant(6500):      69 64 20 36 34 36 35 36 65 37 34 36 31 36 63 36   id 64656e74616c6
NetworkManager: <information>   wpa_supplicant(6500):      34                                                4 
NetworkManager: <information>   wpa_supplicant(6500): 4'
NetworkManager: <information>   wpa_supplicant(6500): ssid - hexdump_ascii(len=7):
NetworkManager: <information>   wpa_supplicant(6500):      64 65 6e 74 61 6c 64                              dentald 
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=25):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 63   SET_NETWORK 0 sc
NetworkManager: <information>   wpa_supplicant(6500):      61 6e 5f 73 73 69 64 20 31                        an_ssid 1 
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: SET_NETWORK id=0 name='scan_ssid' value='1'
NetworkManager: <information>   wpa_supplicant(6500): scan_ssid=1 (0x1)
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=24):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 72   SET_NETWORK 0 pr
NetworkManager: <information>   wpa_supplicant(6500):      6f 74 6f 20 57 50 41 32                           oto WPA2 
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: SET_NETWORK id=0 name='proto' value='WPA2'
NetworkManager: <information>   wpa_supplicant(6500): proto: 0x2
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=30):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke
NetworkManager: <information>   wpa_supplicant(6500):      79 5f 6d 67 6d 74 20 57 50 41 2d 45 41 50         y_mgmt WPA-EAP
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='WPA-EAP'
NetworkManager: <information>   wpa_supplicant(6500): key_mgmt: 0x1
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=22):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 65 61   SET_NETWORK 0 ea
NetworkManager: <information>   wpa_supplicant(6500):            p PEAP
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: SET_NETWORK id=0 name='eap' value='PEAP'
NetworkManager: <information>   wpa_supplicant(6500): eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=41):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 69 64   SET_NETWORK 0 id
NetworkManager: <information>   wpa_supplicant(6500):      65 6e 74 69 74 79 20 22 64 65 6e 74 61 6c 64 5c   entity "dentald\
NetworkManager: <information>   wpa_supplicant(6500):      6a 65 72 6f 6e 69 6d 31 22                        jeronim1" 
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: SET_NETWORK id=0 name='identity' value='"dentald\jeronim1"'
NetworkManager: <information>   wpa_supplicant(6500): identity - hexdump_ascii(len=16):
NetworkManager: <information>   wpa_supplicant(6500):      64 65 6e 74 61 6c 64 5c 6a 65 72 6f 6e 69 6d 31   dentald\jeronim1
NetworkManager: <information>   wpa_supplicant(6500): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(6500): RX ctrl_iface - hexdump_ascii(len=33):
NetworkManager: <information>   wpa_supplicant(6500):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 61   SET_NETWORK 0 pa
NetworkManager: <information>   wpa_supplicant(6500):      73 73 77 6f 72 64 20 22 63 61 72 64 66 69 76 65   ssword "cardfive
NetworkManager: <information>   wpa_supplicant(6500):      22                                                " 
NetworkManager: <information>   wpa_supplicant(6500): CTRL_IFACE: SET_NETWORK id=0 name='password' value='"cardfive"'
NetworkManager: <information>   wpa_supplicant(6500): password - hexdump_ascii(len=8): [REMOVED]
NetworkManager: <information>   eth1: link timed out.
NetworkManager: <information>   Activation (eth1/wireless): association took too long (>40s), failing activation.
NetworkManager: <information>   Activation (eth1) failure scheduled...
NetworkManager: <information>   Activation (eth1) failed for access point (dentald)
NetworkManager: <information>   Activation (eth1) failed.
NetworkManager: <information>   Deactivating device eth1.
sendmsg(CTRL_IFACE monitor): No such file or directory
NetworkManager: <information>   SWITCH: no current connection, found better connection 'eth0'.
NetworkManager: <information>   Will activate connection 'eth0'.

---

### Post by bb002 on 2006-03-09
I'm stuck at getting the cvs version of wpasupplicant.
i enter the command ```
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
``` and I get asked for a password. Being an anonymous login why am I getting asked for a password? I've never used cvs before. I normally use official releases, even if those releases are betas.

If I use a blank password i get ```
cvs login: warning: failed to open /home/bb002/.cvspass for reading: No such file or directory
```
If I enter something I get a plain jane access denied.

Could you explain to me what's going on exactly? Maybe even add a little cvs primer to your howto. Just enough for those of us that have never used cvs to have a half-baked idea of what is good, bad, and ugly.

Thanks.

---

### Post by Brimmy on 2006-03-09
bb002
it should create a .cvpass file in your home directory with this info in it.

/1 :pserver:anonymous@anoncvs.gnome.org:2401/cvs/gnome A
/1 :pserver:anonymous@hostap.epitest.fi:2401/cvs A

---

### Post by Brimmy on 2006-03-09
Ok I now know that 802.1x will not work in linux, thats fine.   But i noticed that NetworkManager will not start when my laptop is in the docking station.  Here is the message i get when i run NM manually

@991FZ81:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        nm_dbus_init (): nm_dbus_init() could not acquire the NetworkManager service as it is already taken (ret=3). Is the daemon already running?
NetworkManager: <ERROR> [1141919860.039725] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:         NetworkManager(main+0x452) [0x8066db1]
NetworkManager:         /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0x77d8dea2]
NetworkManager:         NetworkManager [0x8052de1]
Trace/breakpoint trap

I need to run

```
sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/
sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/
sudo cp initscript/Debian/NetworkManager /etc/init.d/
sudo update-rc.d -f NetworkManager remove
sudo update-rc.d NetworkManager start 30 2 3 4 5 . stop 70 0 1 6 .
```

to get to run while docked?


PS Jeff250 great work on this how to.

---

### Post by Jeff250 on 2006-03-10
[QUOTE=bb002]I'm stuck at getting the cvs version of wpasupplicant.
i enter the command ```
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
``` and I get asked for a password. Being an anonymous login why am I getting asked for a password? I've never used cvs before. I normally use official releases, even if those releases are betas.

If I use a blank password i get ```
cvs login: warning: failed to open /home/bb002/.cvspass for reading: No such file or directory
```
If I enter something I get a plain jane access denied.

Could you explain to me what's going on exactly? Maybe even add a little cvs primer to your howto. Just enough for those of us that have never used cvs to have a half-baked idea of what is good, bad, and ugly.

Thanks.[/QUOTE]

There is no password, and just hitting enter sould work.  I'm not sure why you're getting that error though.  Try:
```
rm /home/bb002/.cvspass
touch /home/bb002/.cvspass
```
and check for any error messages.

---

### Post by Jeff250 on 2006-03-10
[QUOTE=Brimmy]Ok I now know that 802.1x will not work in linux, thats fine.   But i noticed that NetworkManager will not start when my laptop is in the docking station.  Here is the message i get when i run NM manually

@991FZ81:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        nm_dbus_init (): nm_dbus_init() could not acquire the NetworkManager service as it is already taken (ret=3). Is the daemon already running?
NetworkManager: <ERROR> [1141919860.039725] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:         NetworkManager(main+0x452) [0x8066db1]
NetworkManager:         /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0x77d8dea2]
NetworkManager:         NetworkManager [0x8052de1]
Trace/breakpoint trap[/quote]

Did you run:
```
sudo killall NetworkManager
```
before running:
```
sudo NetworkManager --no-daemon
```
?

> I need to run

```
sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/
sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/
sudo cp initscript/Debian/NetworkManager /etc/init.d/
sudo update-rc.d -f NetworkManager remove
sudo update-rc.d NetworkManager start 30 2 3 4 5 . stop 70 0 1 6 .
```

to get to run while docked?

You need to run this only once when you install it.

---

### Post by DeeZiD on 2006-03-11
I can't compile the new network manager, because libnl refuses to compile :(

I got the following error:
```
/usr/include/asm-x86_64/types.h:24: Fehler: in Konflikt stehende Typen für »__u64«
../include/netlink-local.h:37: Fehler: vorherige Deklaration von »__u64« war hier
In Datei, eingefügt von addr.c:32:
/usr/include/linux/socket.h:7:2: Warnung: #warning "You should include <sys/socket.h>. This time I will do it for you."
addr.c: In Funktion »nl_addr2str«:
addr.c:805: Warnung: Zeigerziele bei Übergabe des Arguments 1 von »dnet_ntop« unterscheiden sich im Vorzeichenbesitz
make[2]: *** [addr.o] Fehler 1
make[1]: *** [all] Fehler 2
Entering include
/bin/sh: line 1: cd: include: Datei oder Verzeichnis nicht gefunden
Entering doc
/bin/sh: line 1: cd: doc: Datei oder Verzeichnis nicht gefunden
Entering src
/bin/sh: line 1: cd: src: Datei oder Verzeichnis nicht gefunden
make: *** [all] Fehler 1

```

sry, its german ;)
but here are some translations:
Fehler=error
vorherige Deklaration=previous declaration
Zeigerziele bei Übergabe des Arguments 1 von »dnet_ntop« unterscheiden sich im Vorzeichenbesitz=don't know :D


I'm using 64Bit Dapper on my acer Aspire 5024 WLMi notebook with Radeon X700 and Xgl which works really fine and is stable, ndiswrapper works, too (blacklisted bcm(blabla) before). 

EXCEPT wireless :(

I really have to use WPA. 
But all these howtos won't work for me.


regards Dennis

---

### Post by DeeZiD on 2006-03-12
Does nobody know, what is the problem on AMD64 Dapper? :(
If the how-to works for someone who has a AMD64 Dapper, Please, please provide packages :)


regards Dennis

---

### Post by wheelspin on 2006-03-13
**Great How To!**

A big THANKS goes out to Jeff250 for this Howto.

I have written up a script based on the first post for my own use to automate the installation process. It can get old tracking down a thread and manually copy-paste or retype every input should one need to reinstall thier drivers or OS. It works so well I thought i would share it with everyone. It gets all your files and edits them as needed then installs them. I made some changes since I only have the ipw2915 chipset I added the ipw2100 drivers also. It will also ask if you want to install needed libraries to compile properly. Basically a one click solution.

You should select EVERYTHING EXCEPT for the drivers that do not apply to you.

 i.e. either ipw2100 or ipw2200\2915 not both. Then everything else.

To install just save it to your home directory.
```

tar -zxvf wirelessinstall-0.2.tar.gz
```

```
sudo chmod 755 wirelessinstall-0.2
```

```
./wirelessinstall-0.2
```

Comments or suggestions are appreciated. Enjoy!

I updated the installer so there isn't any confusion in the driver installation and so it doesn't redownload the drivers.

---

### Post by Anders Kvist on 2006-03-13
I've been trying to get this thing to work, but didn't have any success :(

I tried a WPA-PEAP connection at my school, my own Linksys wrt54g with both WPA (TKIP) and WEP...none worked :(

I can only connect to unencrypted networks.

I have an up-to-date dapper install and i followed the howto step by step and everything compiled and installed fine. I even tried the newest driver for ipw2200 (1.1.1) and the automatic installscript wheelspin posted.

Hope anyone can help me :)

Logs from NetworkManager --no-daemon:
[http://lnxbx.dk/~akv/wpa/wpa-peap.txt](http://lnxbx.dk/~akv/wpa/wpa-peap.txt)
[http://lnxbx.dk/~akv/wpa/wpa-tkip.txt](http://lnxbx.dk/~akv/wpa/wpa-tkip.txt)

/Anders Kvist

---

### Post by Brimmy on 2006-03-13
Thanks for the script wheelspin.

---

### Post by pouns on 2006-03-13
thanks for this how-to. It just works !
Does anyone experience any problems with DNS ?
It seems that NetManager delete my dns config every time it activates a connexion.:confused:

---

### Post by wheelspin on 2006-03-13
[QUOTE=Anders Kvist]I've been trying to get this thing to work, but didn't have any success :(

I tried a WPA-PEAP connection at my school, my own Linksys wrt54g with both WPA (TKIP) and WEP...none worked :(

I can only connect to unencrypted networks.

I have an up-to-date dapper install and i followed the howto step by step and everything compiled and installed fine. I even tried the newest driver for ipw2200 (1.1.1) and the automatic installscript wheelspin posted.

Hope anyone can help me :)

Logs from NetworkManager --no-daemon:
[http://lnxbx.dk/~akv/wpa/wpa-peap.txt](http://lnxbx.dk/~akv/wpa/wpa-peap.txt)
[http://lnxbx.dk/~akv/wpa/wpa-tkip.txt](http://lnxbx.dk/~akv/wpa/wpa-tkip.txt)

/Anders Kvist[/QUOTE]


Have you tried usind a SSID? I also have trouble connecting with the "automatic" setting below where you enter your password in NetworkManager mine is set to "TKIP" I have a Motorola router with several levels of encryption if not set right it will not connect.

ESS Authentication=======Encryption Status 
   	 
Pre-Shared Key (psk)=====WEP64 or WEP128

WPA==================TKIP or AES

WPA-PSK============== TKIP or AES  

I use this one WPA_PSK====TKIP

The ipw2200-1.1.1 drivers require firmware version-3.0 to be installed; Dapper has version-2.4. I am using the ipw2200-1.1.1 driver just to try it out, seems to work fine. 
I didn't include them into my script since you need to agree to a lenghtly "License Agreement" to download the newer firmware. They can be found here.

[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

extract them and cd to folder

```
sudo cp *.fw /lib/firmware/$(uname -r)
```

Then restart.

---

### Post by Anders Kvist on 2006-03-13
> **wheelspin]Have you tried usind a SSID? I also have trouble connecting with the "automatic" setting below where you enter your password in NetworkManager mine is set to "TKIP" I have a Motorola router with several levels of encryption if not set right it will not connect.

ESS Authentication=======Encryption Status 
   	 
Pre-Shared Key (psk)=====WEP64 or WEP128

WPA==================TKIP or AES

WPA-PSK============== TKIP or AES  

I use this one WPA_PSK====TKIP

The ipw2200-1.1.1 drivers require firmware version-3.0 to be installed said:**
> http://ipw2200.sourceforge.net/firmware.php[/url]

extract them and cd to folder

```
sudo cp *.fw /lib/firmware/$(uname -r)
```

Then restart.

First i tried the ipw2200 1.1.0 driver with 2.4 firmware and i upgradet the firmware to 3.0 when i tried the 1.1.1 driver. The card works fine, i tried it with kismet and i was able to connect to unencrypted networks.

I'v tried setting up a network instead of just connecting to it (if that's what you mean) with same outcome...but i'm going to try some more now...

The accesspoint it setup with TKIP and my girlfriends laptop with XP connects fine... :(

/Anders

---

### Post by anders.ostling on 2006-03-14
I just tried to follow the Howto to the letter, and everything seem to work just fine. Except that WPA2 does not include EAP-LEAP, the Cisco WPA protocol used at our site. Too bad, I guess I have to wait for next iteration.
The cvs version also feels more polished, faster and with better feedback (popups). Thanks a lot for the instructions!

Anyone that know how VPN (vpnc) can be integrated?

[update] I found the sources in the subdirectory of NM. Compiled and installed according to instructions. VPN is now, after a reboot, indeed in the applet menu, and I have created a connction profile. When trying to active the vpnc connection, I get the following error message in the NetworkManager traceback

...
NetworkManager: <information>   Will activate VPN connection 'IKEA VPN', service 'org.freedesktop.NetworkManager.vpnc', user_name 'xonn', vpn_data 'IPSec gateway / 152.31.66.234 / IPSec ID / VPNSecGroup / Domain / acme', route ''.
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 1 of 4 (Connection Prepare) scheduled...
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.vpnc (PID 5344)
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 1 of 4 (Connection Prepare) complete.
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 2 of 4 (Connection Prepare Wait) scheduled...
NetworkManager: <information>   VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 1 -> 6.
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 2 of 4 (Connection Prepare Wait) waiting...
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 2 of 4 (Connection Prepare Wait) complete.
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 3 of 4 (Connect) scheduled...
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 3 of 4 (Connect) sending connect request.
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 3 of 4 (Connect) request sent, waiting for reply...
NetworkManager: <information>   VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 6 -> 3.
** Message: <information>       vpnc started with pid 5347

NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 3 of 4 (Connect) reply received.
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 4 of 4 (IP Config Get) timeout scheduled...
NetworkManager: <information>   VPN Activation (IKEA VPN) Stage 3 of 4 (Connect) complete, waiting for IP configuration...
VPNC started in foreground...
** Message: <information>       Terminated vpnc daemon with PID 5347.

NetworkManager: <WARNING>        nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.vpnc', signal 'ConnectFailed', with message 'The VPN login failed because the VPN program could not connect to the VPN server.'.
NetworkManager: <information>   VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 3 -> 5.
NetworkManager: <information>   VPN service 'org.freedesktop.NetworkManager.vpnc' signaled state change 5 -> 6.
NetworkManager: <WARNING>        nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.vpnc): could not stop connection 'ACME VPN' because service was 6.
NetworkManager: <debug info>    [1142372610.856238] nm_dbus_signal_filter (): NetworkManagerInfo triggered update of VPN connection 'ACME VPN'

And yes, vpnc works fine stand-alone, both using the config options and command line options. vpnc has version: 0.3.3+SVN20051028-2ubuntu1

[update 2]
whaddoyanow, I rebooted once more, and re-entered my credentials (password & group password). This time it worked, and I was presented with a nice popup containing the vpn banner text! 
And the best thing is that is is reproducable, works every time! It also remembers the passwords between sessions (not reboots though).

Anders

---

### Post by benkong2 on 2006-03-15
Ok I  installed by the docs on an IBM T40 thinkpad the wireless driver is an airo.cs. What happens is it does not associate with my home network or any wireless network even open ones. Heres the output of a tail on var/log/syslog what do you think?

Mar 15 01:28:39 localhost NetworkManager: <information>^I  nameserver 192.168.1.1 
Mar 15 01:28:39 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 15 01:28:39 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Mar 15 01:28:39 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Mar 15 01:28:39 localhost dhclient: bound to 192.168.1.41 -- renewal in 121090 seconds.
Mar 15 01:28:40 localhost NetworkManager: <information>^IActivation (eth1) successful, device activated. 
Mar 15 01:28:40 localhost NetworkManager: <information>^IActivation (eth1) Finish handler scheduled. 
Mar 15 01:28:40 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 15 01:28:51 localhost kernel: [4305459.691000] eth1: no IPv6 routers present
Mar 15 01:29:02 localhost kernel: [4305471.120000] eth0: no IPv6 routers present
Mar 15 01:35:40 localhost NetworkManager: <information>^ISWITCH: terminating current connection 'eth1' because it's no longer valid. 
Mar 15 01:35:40 localhost NetworkManager: <information>^IDeactivating device eth1. 
Mar 15 01:35:40 localhost dhclient: wifi0: unknown hardware address type 801
Mar 15 01:35:40 localhost dhclient: wifi0: unknown hardware address type 801
Mar 15 01:35:40 localhost kernel: [4305868.788000] e100: eth1: e100_watchdog: link down
Mar 15 01:35:40 localhost dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Mar 15 01:35:41 localhost NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Mar 15 01:35:41 localhost NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Mar 15 01:36:00 localhost NetworkManager: <information>^IWill activate wired connection 'eth1' because it now has a link. 
Mar 15 01:36:00 localhost NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
Mar 15 01:36:00 localhost NetworkManager: <information>^IWill activate connection 'eth1'. 
Mar 15 01:36:00 localhost NetworkManager: <information>^IDevice eth1 activation scheduled... 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) started... 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) successful. 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 15 01:36:00 localhost NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Mar 15 01:36:00 localhost kernel: [4305888.788000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
Mar 15 01:36:00 localhost kernel: [4305888.803000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Mar 15 01:36:01 localhost NetworkManager: <information>^IActivation (eth1) Beginning DHCP transaction. 
Mar 15 01:36:01 localhost dhclient: wifi0: unknown hardware address type 801
Mar 15 01:36:01 localhost NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Mar 15 01:36:01 localhost NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth1 
Mar 15 01:36:02 localhost NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1 
Mar 15 01:36:02 localhost dhclient: wifi0: unknown hardware address type 801
Mar 15 01:36:06 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Mar 15 01:36:06 localhost dhclient: DHCPOFFER from 192.168.1.1
Mar 15 01:36:06 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Mar 15 01:36:06 localhost dhclient: DHCPACK from 192.168.1.1
Mar 15 01:36:06 localhost NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth1 
Mar 15 01:36:06 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 15 01:36:06 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Mar 15 01:36:06 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Mar 15 01:36:06 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Mar 15 01:36:06 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Mar 15 01:36:06 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Mar 15 01:36:06 localhost NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Mar 15 01:36:06 localhost NetworkManager: <information>^I  address 192.168.1.41 
Mar 15 01:36:06 localhost NetworkManager: <information>^I  netmask 255.255.255.0 
Mar 15 01:36:06 localhost NetworkManager: <information>^I  broadcast 192.168.1.255 
Mar 15 01:36:06 localhost NetworkManager: <information>^I  gateway 192.168.1.1 
Mar 15 01:36:06 localhost NetworkManager: <information>^I  nameserver 192.168.1.1 
Mar 15 01:36:06 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 15 01:36:06 localhost NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Mar 15 01:36:06 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Mar 15 01:36:06 localhost dhclient: bound to 192.168.1.41 -- renewal in 103089 seconds.
Mar 15 01:36:07 localhost NetworkManager: <information>^IActivation (eth1) Finish handler scheduled. 
Mar 15 01:36:07 localhost NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 15 01:36:07 localhost NetworkManager: <information>^IActivation (eth1) successful, device activated.

---

### Post by benkong2 on 2006-03-15
OOps! wrong log file here is the correct one.
Mar 15 01:36:18 localhost kernel: [4305906.648000] eth1: no IPv6 routers present
Mar 15 01:40:34 localhost kernel: [4306162.788000] e100: eth1: e100_watchdog: link down
Mar 15 01:40:46 localhost NetworkManager: <debug info>^I[1142404846.217802] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'bentux' 
Mar 15 01:40:46 localhost NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth0 / bentux 
Mar 15 01:40:46 localhost NetworkManager: <information>^IDeactivating device eth0. 
Mar 15 01:40:48 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Mar 15 01:40:48 localhost NetworkManager: <information>^IDevice eth0 activation scheduled... 
Mar 15 01:40:48 localhost NetworkManager: <information>^IDeactivating device eth1. 
Mar 15 01:40:48 localhost dhclient: wifi0: unknown hardware address type 801
Mar 15 01:40:48 localhost dhclient: wifi0: unknown hardware address type 801
Mar 15 01:40:48 localhost dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) started... 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0/wireless): access point 'bentux' is encrypted, but NO valid key exists.  New key needed. 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) New wireless user key requested for network 'bentux'. 
Mar 15 01:40:49 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0) New wireless user key for network 'bentux' received. 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 15 01:41:50 localhost NetworkManager: <information>^IActivation (eth0/wireless): access point 'bentux' is encrypted, and a key exists.  No new key needed. 
Mar 15 01:41:51 localhost NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth0^I^Iwext^I/usr/local/var/run/wpa_supplicant^I' 
Mar 15 01:41:51 localhost kernel: [4306239.771000] Setting transmit key to 0
Mar 15 01:41:51 localhost kernel: [4306240.053000] Setting transmit key to 1
Mar 15 01:41:51 localhost kernel: [4306240.348000] Setting transmit key to 2
Mar 15 01:41:52 localhost kernel: [4306240.616000] Setting transmit key to 3
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'AP_SCAN 2' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was '0' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 62656e747578' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Mar 15 01:41:52 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Mar 15 01:41:52 localhost kernel: [4306240.904000] Setting key 0
Mar 15 01:41:52 localhost kernel: [4306241.172000] Setting transmit key to 0
Mar 15 01:41:53 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Global control interface '/usr/local/var/run/wpa_supplicant-global' 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): RX global ctrl_iface - hexdump_ascii(len=59): 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185):      68 30 09 09 77 65 78 74 09 2f 75 73 72 2f 6c 6f   h0__wext_/usr/lo 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185):      63 61 6c 2f 76 61 72 2f 72 75 6e 2f 77 70 61 5f   cal/var/run/wpa_ 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185):      73 75 70 70 6c 69 63 61 6e 74 09                  supplicant_      
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth0^I^Iwext^I/usr/local/var/run/wpa_supplicant^I' 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Initializing interface 'eth0' conf 'N/A' driver 'wext' ctrl_interface '/usr/local/var/run/wpa_supplicant' bridge 'N/A' 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Initializing interface (2) 'eth0' 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): EAPOL: SUPP_PAE entering state DISCONNECTED 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): EAPOL: SUPP_BE entering state INITIALIZE 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): EAP: EAP entering state DISABLED 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): EAPOL: External notification - portEnabled=0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): EAPOL: External notification - portValid=0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): SIOCGIWRANGE: WE(compiled)=19 WE(source)=12 enc_capa=0x0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185):   capabilities: key_mgmt 0x0 enc 0x3 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Own MAC address: 00:02:8a:a3:1a:29 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): r_wext_set_wpa 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Driver does not support WPA. 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): wpa_driver_wext_set_countermeasures 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): wpa_driver_wext_set_drop_unencrypted 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Setting scan request: 0 sec 100000 usec 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Added interface eth0 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): Wireless event: cmd=0x8b06 len=8 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185): RX ctrl_iface - hexdump_ascii(len=9): 
Mar 15 01:41:53 localhost NetworkManager: <information>^Iwpa_supplicant(16185):      41 50 5f 53 43 41 4e 20 32                        AP_SCAN 2

---

### Post by anders.ostling on 2006-03-15
you know that you can edit your own posts, dont you? No need to send out a new reply if you only wanted to update the content of an existing. Just an advice

Anders

---

### Post by naked on 2006-03-15
I am using Dapper (Flight 5) on a Dell 700m w/ ipw2200.  I needed to install the new ipw2200 driver for this to work properly.  I used wheelspins script to do this after trying on my own without them.  The script works like a charm!.

L

---

### Post by Anders Kvist on 2006-03-15
I thought that my old dapper had a problem, so i downloaded the dapper flight 5 iso and made a fresh install...ran wheelspin's script, but it didn't work :( I even installed the ipw2200 1.1.1 driver and firmware 3.0... :(

I simply cannot get why this shit ain't working  when everyone of you guys says it's just working like a charm :/

/Anders

---

### Post by naked on 2006-03-15
[QUOTE=Anders Kvist]I thought that my old dapper had a problem, so i downloaded the dapper flight 5 iso and made a fresh install...ran wheelspin's script, but it didn't work :( I even installed the ipw2200 1.1.1 driver and firmware 3.0... :(

I simply cannot get why this shit ain't working  when everyone of you guys says it's just working like a charm :/

/Anders[/QUOTE]

Well, what happens?  What happens when you run 'nm-applet' from terminal?  Do you get any errors during boot-up (Alt+F1 will get rid of the usplash to provide more info)?  Can you '/etc/init.d/NetworkManager restart' without errors?  In order for the community to help you, me need some more info.

I know it can be frustrating, it took me about a week of messing with it to get it to half-way work (but now it works after fresh D.F.5 install w/ wheelspins script.

L

---

### Post by benkong2 on 2006-03-15
I should probably add this. (1) Thanks Anders, I should have done that.
(2) Is there a reason why this would not work with a Cisco 350 pci built in wireless in a Thinkpad?

---

### Post by Anders Kvist on 2006-03-15
[QUOTE=naked]Well, what happens?  What happens when you run 'nm-applet' from terminal?  Do you get any errors during boot-up (Alt+F1 will get rid of the usplash to provide more info)?  Can you '/etc/init.d/NetworkManager restart' without errors?  In order for the community to help you, me need some more info.

I know it can be frustrating, it took me about a week of messing with it to get it to half-way work (but now it works after fresh D.F.5 install w/ wheelspins script.

L[/QUOTE]

The post was an "update" to [http://www.ubuntuforums.org/showpost.php?p=819643&postcount=50](http://www.ubuntuforums.org/showpost.php?p=819643&postcount=50) which was my previous attempts...and contains the same logfiles...that was why i didn't attach any logfiles...exaclty the same happens...

I don't get any errors...it just doesn't work :(

/Anders

---

### Post by Anders Kvist on 2006-03-15
I've been fooling a little around for the last couple of hours....still nothing works :(

```
eth1      unassociated  ESSID:"MySSID"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I tried EVERYTHING and it keeps saying unassociated/Not-Associated, with WEP and WPA...i was able to connect to encryption free networks...i'm out of guesses...

i'm gonna install the flight 5 on my girlfriends laptop which also has ipw2200....just to test again...


/Anders

---

### Post by Anders Kvist on 2006-03-17
And now it all works...by a mistake i had switched channel on my accesspoint to 14...dah! :)

/Anders

---

### Post by charleyramm on 2006-03-17
I am trying to setup my WPA wireless network, but all this stuff goes right over my head. Is there a package that contains the tools you talk about here? Could somebody produce one?

thanks.
charley

---

### Post by weizilla on 2006-03-20
[QUOTE=xenoxaos]i'm having problems on breezy, 

I get an error 

checking for DBUS... configure: error: Package requirements (dbus-glib-1 >= 0.60) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

any help[/QUOTE]

I have the same problem. apparently breezy badger only has .32 or something for dbus and dapper has the .60 which is needed. I'm using breezy but considered only upgrading dbus to .60. However I figured this probably isn't a good idea though.

---

### Post by Jeff250 on 2006-03-20
[QUOTE=charleyramm]I am trying to setup my WPA wireless network, but all this stuff goes right over my head. Is there a package that contains the tools you talk about here? Could somebody produce one?

thanks.
charley[/QUOTE]

As of very recently, there is here:
[http://www.ubuntuforums.org/showthread.php?t=147249](http://www.ubuntuforums.org/showthread.php?t=147249)

---

### Post by dinub1 on 2006-03-20
Thanks for the detailed instroctions. I an not sure but are these instructions only valid for a certain type of Ubuntu and not for all ? I am interrested in running WPA wireless encryption with my Ubuntu 5.10 OCE. Network manager shows only WEP encryption available. I am using WPA-PSK/AES encryption on my Windows system. All runs fine. Under Ubuntu I tried security disabled and browses like a charm. If instructions are valid for my Ububtu then I will go over the instruction and try upgrading my system. Pls. let me know. THX in advance.

---

### Post by dinub1 on 2006-03-20
Thanks Daper Drake. I will try to implement. Quick question. If your instructions refer to wirelessinstall.0-2.tar.gz only why would version 0-1.tar.gz.be needed  ?

---

### Post by wheelspin on 2006-03-21
[QUOTE=dinub1]Thanks Daper Drake. I will try to implement. Quick question. If your instructions refer to wirelessinstall.0-2.tar.gz only why would version 0-1.tar.gz.be needed  ?[/QUOTE]
You only need 0.2, it's an update version of 0.1

---

### Post by sherlock-holmes on 2006-03-22
Hi jeff

thanks for the howto...its nice that a package was made out of it by wheelspin and good work guys....

---

### Post by Sebby on 2006-03-27
A big thanks for this guide. I've been struggling to get WPA working since installing Dapper, but this guide makes it so simple. Thanks again. :D

One thing... I accidentally deleted the NetworkManager icon from the top panel (notification area). How can I get it back?

---

### Post by tore- on 2006-03-27
Well, this did in fact brake my system. For some reason it decided to remove grub entries. I just amuses me that it is so freakin' hard to get something as simple as WPA support to work.

---

### Post by dabear on 2006-03-27
[QUOTE=tore-] For some reason it decided to remove grub entries. [/QUOTE]
Sorry, this is a good example of PEBKAC, there's no chance in hell NM will touch your grub entries.

---

### Post by Jeff250 on 2006-03-27
[QUOTE=Sebby]A big thanks for this guide. I've been struggling to get WPA working since installing Dapper, but this guide makes it so simple. Thanks again. :D

One thing... I accidentally deleted the NetworkManager icon from the top panel (notification area). How can I get it back?[/QUOTE]

Run nm-applet, and to get it to do it automatically, on the top gnome panel, go to System -> Preferences -> Sessions -> Startup Programs, and then add nm-applet.

---

### Post by Sebby on 2006-03-28
[QUOTE=Jeff250]Run nm-applet, and to get it to do it automatically, on the top gnome panel, go to System -> Preferences -> Sessions -> Startup Programs, and then add nm-applet.[/QUOTE]
It's in start programs as *nm-applet --sm-disable*. When I login, the message pops up to say I am connected to the wireless network (stemming from the applications menu!), but there is no NetworkManager icon. :(

---

### Post by Sebby on 2006-03-31
Any ideas?

Also, my DNS settings are lost on every reboot.

---

### Post by Sianis on 2006-04-21
Jeff250! Thanks the HOWTO =D> 

I have some questions. 

1. How can I connect to not secured (not WEP and not WPA) networks? I try It, but I saw the NW try join the open networks with wpa_supplicant, but why?

2. How can I enable to the NW a free way to the WPA-Key ( don't ask the password for the key ) ?

Thanks again...and I wait for reply!

Sianis

---

### Post by foureight84 on 2006-04-21
[QUOTE=Whoopie]For ipw2200-1.0.12 and kernel 2.6.15, you need a patch to get DHCP working.

The bug is mentioned under [http://www.bughost.org/bugzilla/show_bug.cgi?id=919](http://www.bughost.org/bugzilla/show_bug.cgi?id=919).

The patch is available there.
Direct link: [http://www.bughost.org/bugzilla/attachment.cgi?id=674](http://www.bughost.org/bugzilla/attachment.cgi?id=674)

Best regards,
Whoopie[/QUOTE]

how do you use this patch?

---

### Post by era86 on 2006-04-21
Hi all..

I followed this tutorial, and now my wireless card isn't detected. I tried backtracking and removing all the files I used, but it still doesn't seem to find my wireless. I tried ifup eth1 and it doesn't exist. Does anyone know what the problem could be?

Thanks!

---

### Post by Jeff250 on 2006-04-22
[QUOTE=Sianis]1. How can I connect to not secured (not WEP and not WPA) networks? I try It, but I saw the NW try join the open networks with wpa_supplicant, but why?[/QUOTE]

If it's not working by default, then there are really only two things I can suggest:
Open gconf-editor and go to /system/networking/wireless/networks and if the network to which you are trying to connect is listed there, view it and "unset" all of the settings for it by right-clicking on the values on the right-hand part of the window.

Also, if it's not for some reason detecting it correctly, try left-clicking on the networkmanager applet and selecting "Connect to other network..." and type in its name and select none for security.

> 2. How can I enable to the NW a free way to the WPA-Key ( don't ask the password for the key ) ?

Unfortunately, this is a known problem.

---

### Post by Jeff250 on 2006-04-22
[QUOTE=foureight84]how do you use this patch?[/QUOTE]

You don't need it for versions of the drivers later than 1.0.12, but to answer your question:
You can apply any patch to source code by downloading the patch to the source code's directory.  Then in that directory type in:
```
patch -p0 < PATCHFILENAME
```
and replace PATCHFILENAME with the name of the actual patch that you downloaded.
If it cannot find the file(s) that it is supposed to patch, then try:
```
patch -p1 < PATCHFILENAME
```
or:
```
patch -p2 < PATCHFILENAME
```
Anything past p2 probably isn't going to work if it hasn't already, and you're probably dealing with a different problem.

---

### Post by Jeff250 on 2006-04-22
[QUOTE=era86]Hi all..

I followed this tutorial, and now my wireless card isn't detected. I tried backtracking and removing all the files I used, but it still doesn't seem to find my wireless. I tried ifup eth1 and it doesn't exist. Does anyone know what the problem could be?

Thanks![/QUOTE]

Type in:
```
lsmod | grep ipw
```
Any results?
If nothing comes up, try:
```
sudo modprobe ipw2200
```
(or ipw2100 if you have an ipw2100).  Any errors?

---

### Post by pax on 2006-04-25
I'm stuck at wpa_supplicant :( 
This is what I get after sudo make install :

```
mkdir -p /usr/local/sbin/
for i in wpa_supplicant wpa_passphrase wpa_cli dynamic_eap_methods; do cp $i /us r/local/sbin/$i; done
cp: cannot stat `dynamic_eap_methods': No such file or directory
make: *** [install] Error 1

```

---

### Post by sublime on 2006-04-25
im getting the same thing as above.

---

### Post by sublime on 2006-04-25
ok i fixed it.  the latest cvs build is not stable and is wont build correctly.  go to:  [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)
and download the latest stable build, 0.4.8  this will compile and install correctly.

---

### Post by Jeff250 on 2006-04-26
Ah, good.  If you want to use the CVS version for now, edit the Makefile line 12 from this:
```
ALL=wpa_supplicant wpa_passphrase wpa_cli dynamic_eap_methods
```
...to this:
```
ALL=wpa_supplicant wpa_passphrase wpa_cli# dynamic_eap_methods
```

---

### Post by MrMojoRising on 2006-04-30
You saved my life!
I've been trying get WPA working on my laptop for a month now.
After one try with your guide it worked.
I am eternally grateful.

Here's my specs:

Acer TravelMate 4400 Notebook
Broadcom AirForce chipset
ndiswrapper &  acer_acpi used to bring up wireless card

For my notebook though i do have to run this little script to get the card up and running (this is a problem with all Acer notebooks) :


    sudo rmmod bcm43xx
    sudo depmod -a
    sudo modprobe acer_acpi
    sudo ndiswrapper -e bcmwl5
    sudo ndiswrapper -i bcmwl5.inf
    sudo modprobe -r ndiswrapper
    sudo modprobe ndiswrapper
    sudo modprobe acer_acpi
    cd /proc/acpi/acer
    sudo chmod 777 ./wireless
    echo "enabled: 0">/proc/acpi/acer/wireless
    echo "enabled: 1">/proc/acpi/acer/wireless



.....you can tell from the commands (maybe?) what steps i had to go through to get the wireless card up and ready to be used by NetworkManager.

---

### Post by brettr on 2006-04-30
Hey, I tried to install from your guide, but i was getting DBUS errors of some sort so i gave the script that was posted in the thread a try and it is goin good now. I just hava 2 questions.

1. When i log on i get asked for the keyring password... Is this normal/any way to stop it

2. It always fails to connect the first time.... Not a huge problem but if anyone has any ideas would like to hear them

Thanks.. Brett

---

### Post by Regenkind on 2006-05-01
hi, i tried to follow the script and used the Installer on an Kubuntu Drake beta 2 but i always seem to be stuck at the final make command. :confused: 
This is what i get:

make[3]: Entering directory `/home/gduma/NetworkManager/test'
depbase=`echo nm-online.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`; \
        if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I../gnome/libnm_glib -I../utils -I../include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DDBUS_VERSION_MAJOR=0 -DDBUS_VERSION_MINOR=60 -DDBUS_VERSION_MICRO=0 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -DDBUS_API_SUBJECT_TO_CHANGE -DBINDIR=\"/usr/local/bin\" -DDATADIR=\"/usr/local/share\"   -Wall -std=gnu89 -g -O2 -Wshadow -Wmissing-declarations -Wmissing-prototypes -Wdeclaration-after-statement -Wstrict-prototypes -Wfloat-equal -Wno-unused-parameter -Wno-sign-compare -MT nm-online.o -MD -MP -MF "$depbase.Tpo" -c -o nm-online.o nm-online.c; \
        then mv -f "$depbase.Tpo" "$depbase.Po"; else rm -f "$depbase.Tpo"; exit 1; fi
nm-online.c:22:43: error: NetworkManager/NetworkManager.h: No such file or directory
nm-online.c: In function &#8216;dbus_filter&#8217;:
nm-online.c:28: error: &#8216;NM_DBUS_INTERFACE&#8217; undeclared (first use in this function)
nm-online.c:28: error: (Each undeclared identifier is reported only once
nm-online.c:28: error: for each function it appears in.)
nm-online.c: In function &#8216;check_online&#8217;:
nm-online.c:40: error: &#8216;NM_DBUS_SERVICE&#8217; undeclared (first use in this function)
nm-online.c:40: error: &#8216;NM_DBUS_PATH&#8217; undeclared (first use in this function)
nm-online.c:41: error: &#8216;NM_DBUS_INTERFACE&#8217; undeclared (first use in this function)
nm-online.c:56: error: &#8216;NM_STATE_CONNECTED&#8217; undeclared (first use in this function)
nm-online.c: In function &#8216;main&#8217;:
nm-online.c:96: error: syntax error before &#8216;NM_DBUS_INTERFACE&#8217;
make[3]: *** [nm-online.o] Error 1
make[3]: Leaving directory `/home/gduma/NetworkManager/test'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gduma/NetworkManager/test'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gduma/NetworkManager'
make: *** [all] Error 2

Any ideas?

---

### Post by brettr on 2006-05-02
Not that this means much, however i got this error, while trying to install by this howto, So i removed everything according to the howto and then tried the script. But yes i would also like to know what this error means

---

### Post by Maliskia on 2006-05-04
Thx for the great howto!!!

I have a ipw2200 and want to connect to a Linksys WRT54G v4 (SSID not free and WPA). The first time I tried this method didn't work, but then I discovered that I had many versions of firmware, even for the ipw2100. When I removed these, I tried again, but nothing. But a few days later I suddenly discovered that he found some networks. So I tried it and YES:-D  he asked for a password to save the WPA-key. Then every time I reboot, he asks automatically that password and I'm connected. Just Perfect!

But yesterday, after I updated the kernel, it didn't work any more. After some search, I discovered that my firmware was changed again to that of ipw2100 and an old version for ipw2200. I changed it again to the right version, but nothing. It looks like I have to do the whole installation again :evil: 

I don't like the idea that I have to do this every time I update my kernel :neutral:

---

### Post by NeoEcoS on 2006-05-07
Hi all, i got the same problem.

I'm working with the lastest driver for ipw3945 1.0.3 , with monitor mode supported, ieee80211 ver 1.1.13 and dapper beta 2 up-to-date 050506.

When doing this how-to i have make some extra things like install some lib to get the autogen.sh of NetwordManager works.

I think some out-of-date library it's generating this error.

---

### Post by ifrflyer on 2006-05-08
Thanks for a GREAT script which mostly works. I'm on the latest dapper and working with an ipw2200. I can get everything going except I can't save the keys - every time I log on to an AP I'm asked for the AP's password - not the gnome-key manager password. What can I do? 

Thanks,

---

### Post by Jeff250 on 2006-05-12
Sorry for the slow responses.

[QUOTE=Maliskia]Thx for the great howto!!!

I have a ipw2200 and want to connect to a Linksys WRT54G v4 (SSID not free and WPA). The first time I tried this method didn't work, but then I discovered that I had many versions of firmware, even for the ipw2100. When I removed these, I tried again, but nothing. But a few days later I suddenly discovered that he found some networks. So I tried it and YES:-D  he asked for a password to save the WPA-key. Then every time I reboot, he asks automatically that password and I'm connected. Just Perfect!

But yesterday, after I updated the kernel, it didn't work any more. After some search, I discovered that my firmware was changed again to that of ipw2100 and an old version for ipw2200. I changed it again to the right version, but nothing. It looks like I have to do the whole installation again :evil: 

I don't like the idea that I have to do this every time I update my kernel :neutral:[/QUOTE]

The only things you should have to reinstall for each kernel are the ieee80211 subsystem, ipw2200 drivers, and the firmware, that is, if the kernel doesn't already have a late enough version of them.

[QUOTE=brettr]Hey, I tried to install from your guide, but i was getting DBUS errors of some sort so i gave the script that was posted in the thread a try and it is goin good now. I just hava 2 questions.

1. When i log on i get asked for the keyring password... Is this normal/any way to stop it

2. It always fails to connect the first time.... Not a huge problem but if anyone has any ideas would like to hear them

Thanks.. Brett[/QUOTE]

#1 is normal.  To debug #2 and receive error output, you can run:
```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```
Of course, the error messages are usually cryptic, but it will give you some google material or something to report to the NM mailing list.

---

### Post by Jeff250 on 2006-05-12
[QUOTE=ifrflyer]Thanks for a GREAT script which mostly works. I'm on the latest dapper and working with an ipw2200. I can get everything going except I can't save the keys - every time I log on to an AP I'm asked for the AP's password - not the gnome-key manager password. What can I do? 

Thanks,[/QUOTE]

Try typing gconf-editor and go to /system/networking/wireless/networks.  Select your network, and then on the right, right click and unset all of the values.  This should reset everything.

edit:
Also, apt-get gnome-keyring-manager and then run gnome-keyring-manager.  Delete the key for your network, if one exists.

---

### Post by Jeff250 on 2006-05-12
[quote="Regenkind"]hi, i tried to follow the script and used the Installer on an Kubuntu Drake beta 2 but i always seem to be stuck at the final make command.
This is what i get:

```
. . .
nm-online.c:22:43: error: NetworkManager/NetworkManager.h: No such file or directory
. . .
```[/quote]

This is the error of consequence.  I checked, and this has been fixed in the latest CVS version:
[http://cvs.gnome.org/viewcvs/NetworkManager/test/nm-online.c?r1=1.1.2.3&r2=1.1.2.4](http://cvs.gnome.org/viewcvs/NetworkManager/test/nm-online.c?r1=1.1.2.3&r2=1.1.2.4)
so run these commands again:
```
cd ~/wpa
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome login
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co NetworkManager
```

---

### Post by MrNamjama on 2006-05-14
[QUOTE=era86]Hi all..

I followed this tutorial, and now my wireless card isn't detected. I tried backtracking and removing all the files I used, but it still doesn't seem to find my wireless. I tried ifup eth1 and it doesn't exist. Does anyone know what the problem could be?

Thanks![/QUOTE]

I did the exact same thing and have the exact same problem. After backtracking (ie running the 'uninstall' part of that script from the first post which gets the latest cvs versions of all the packages) I tried to install KNetworkManager from the Dapper repos (which also installed wpa_supplicant), and got the latest firmware for the ipw2200 card, but eth0 (my formerly working wireless device) is completely gone.

Now that I'm not at home and cannot try it out, I realise that I put the firmware files into the right folder, but I think there were some there already (from Breezy, I dist upgraded yesterday). Could it be that multiple versions of firmware are making the card not... be able to be discovered?

---

### Post by MrNamjama on 2006-05-15
[QUOTE=Jeff250]
**If you have an IPW2200 or an IPW2915 chipset (OPTIONAL)**
This section is for those who want the latest and greatest IPW2200/IPW2915 drivers.
Download this file to your ~/wpa directory:
[http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.1.0.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.1.0.tgz?download)

```
cd ~/wpa
tar -zxvf ipw2200-1.1.1.tgz
cd ipw2200-1.1.1
sudo sh remove-old
make
sudo make install
```
[/QUOTE]

I had a look at dmesg | grep ipw and there were messages about the firmware not being able to be loaded. The sourceforge page for firmware downloads lists several versions for different drivers, and sure enough, I got the latest firmware which would appear to not be supported by the 1.1.0 driver, but works well with 1.1.1.

Getting the 1.1.1 version and installing it solved the problem for me.

Notice that in the original post the link is to the 1.1.0 version, but the instructions are for 1.1.1

---

### Post by Jeff250 on 2006-05-16
What excitement--the link should be fixed now.

---

### Post by Phrostay on 2006-05-16
Hello all. I'm a big Ubuntu n00b but I recently downloaded Dapper Drake 6.06 beta and installed it onto my HP tc4200 tablet laptop and it works like a charm even the pen works with a bit of configuration :). I would like to report that the automated script mentioned in this thread to enable wpa2 wireless support worked flawlessly using version 0.6 of the script. I have wpa2 authentication at home and at the university I attend. I'd like to clear up a few things though. I did not uninstall NetworkManager when I ran the script, however upon rebot I get the error 

"Details: Icon 'software-properties' not found"

So I am wondering how do I get my icon back and also everytime I reboot I have to go into network settings to enable the card again every reboot. Also when I go to my university to use evolution mail client, bittorrent or a manual "sudo apt-get update" from terminal I cannot connect to anything. My university uses a proxy server with an automatic configuration script. Whenever I use windows XP with firefox it prompts me for my password before using the internet. 

Once I have entered my access details I can begin to download from bittorrent or any other source including mIRC and most programs that would be blocked by a firewall. I think this might be a linux thing where I have to authenticate all programs before they can begin to download otherwise I don't know what the problem could be right now? I have entered my automatic proxy configuration script into System -> Preferences -> Network Proxy but no positive results have been returned. 

Thankyou for that wonderful script & guide, it has restored my faith in linux and wireless technology. I hope other people with the same tablet PC will have the same success. If you need tips on setting up your tc4200 just PM, oh yeah my system is a dual-boot too, but only because I need Visual Basic .NET 2003.

NOTE: I will be upgrading to beta2 after I have downloaded the CD from my ISP.

---

### Post by HackNack on 2006-05-24
Very good job on the guide. I had my Lenovo R51 laptop running in 30 minutes. I followed the how-to and only had to resolve minor dependency issues and what not.

---

### Post by e-lizza on 2006-06-05
I tried to follow the procedure.
but when I tried to install wpasupplicant, I got an error:

> u@c:~/wpa/hostap/wpa_supplicant$ sudo make install
mkdir -p /usr/local/sbin/
for i in wpa_supplicant wpa_passphrase wpa_cli dynamic_eap_methods; do cp $i /usr/local/sbin/$i; done
cp: cannot stat `dynamic_eap_methods': No such file or directory
make: *** [install] Error 1

I use clean install of ubuntu 6.06 release.
Any ideas how to solve it?

---

### Post by nexus_6 on 2006-06-06
i got everything up and running in no time, but can't seem to connect to wireless networks with hidden essid. i'm trying to connect to a standard 128-bit wep network at my university (which happens to be quite unstable, maybe plays a role). the console output simply shows a >20sec timeout at getting a dhcp address. as i have no wpa network to test, i can only say it works flawlessly at wep with public essid. 

everything is fine with wifi-radar (but i prefer NM, as it is much more comfortable), so that would be an alternative and shows that modules are loaded correctly. this is a dell latitude d510 with an ipw2200.

---

### Post by ke3pup on 2006-06-07
hi and thanx very much for the tut (otherwise i would have no clue on even where to begin!). i followed the whole tutorial step by step , i've got the NetWorkManager icon on Ubuntu 6.06LTS next to the clock, and it's showing my Wireless Accesspoint in the list of avalible networks with High signal but i can't connect to my wireless network. it's WPA preshared key encrypted but when i put in the password it won't connect.  below  is what i get when i put in the debuging command mentioned in first page :

```
NetworkManager: <information>   Activation (eth1) New wireless user key for network 'NETGEAR' received.
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (eth1/wireless): access point 'NETGEAR' is encrypted, and a key exists.  No new key needed.
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD eth1                wext  /usr/local/var/run/wpa_supplicant        '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 1'
NetworkManager: <information>   SUP: response was 'UNKNOWN COMMAND'
NetworkManager: <WARNING>        nm_utils_supplicant_request_with_check (): supplicant_send_network_config: supplicant error for 'AP_SCAN 1'.  Response: 'UNKNOWN COMMAND'
NetworkManager: <WARNING>        real_act_stage2_config (): Activation (eth1/wireless): couldn't send wireless configuration to the supplicant.
NetworkManager: <information>   Activation (eth1) failure scheduled...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   Activation (eth1) failed for access point (NETGEAR)
NetworkManager: <information>   Activation (eth1) failed.
NetworkManager: <information>   Deactivating device eth1.

```

Please help me get thru this. thanx

---

### Post by Jeff250 on 2006-06-07
[QUOTE=e-lizza]I tried to follow the procedure.
but when I tried to install wpasupplicant, I got an error:



I use clean install of ubuntu 6.06 release.
Any ideas how to solve it?[/QUOTE]

If you want to use the CVS version for now, edit the Makefile line 12 from this:
```
ALL=wpa_supplicant wpa_passphrase wpa_cli dynamic_eap_methods
```
...to this:
```
ALL=wpa_supplicant wpa_passphrase wpa_cli# dynamic_eap_methods
```

[quote=ke3pup]hi and thanx very much for the tut (otherwise i would have no clue on even where to begin!). i followed the whole tutorial step by step , i've got the NetWorkManager icon on Ubuntu 6.06LTS next to the clock, and it's showing my Wireless Accesspoint in the list of avalible networks with High signal but i can't connect to my wireless network. it's WPA preshared key encrypted but when i put in the password it won't connect. below is what i get when i put in the debuging command mentioned in first page[/quote]

Your error looks like you don't have the latest version of wpasupplicant installed.  Did you get any errors during installation of it?

---

### Post by ke3pup on 2006-06-07
no i didn't come across any errors during the tut... the synaptic Manager says that i have the wpasupplicant v0.4.8.3 installed... can anyone tell me what should i do to get it working. thanx

---

### Post by ke3pup on 2006-06-07
ok i went into Synaptic Package Manager and removed the installed version of wpasupplicant0.4.8.3.... downloaded 0.4.9 and extracted it in wpa folder and did :
```
cp defconfig .config
sudo apt-get build-dep wpasupplicant
make
sudo make install
```
didn't get any errors. but im still not connected! is there anything else i should do. thanx

---

### Post by Snam on 2006-06-09
This howto is written on February 3rd, 2006. A lot has changed since then (for example Ubuntu Dapper Drake 6.06 LTS final is released).

Is this howto still the way to go? 
Or are there easier ways?

Please let me know,

Snam

P.S. I've got a Dell Inspiron 6400 with an ipw3945 wireless card and a D-Link AirPlus G DI-524 Wireless Router with WPA-PSK/TKIP security.

---

### Post by pssl220 on 2006-06-09
I still have problems with setting up WPA.  In openSuse 10.1 it was very easy to set this up. With Breazy this was a problem. I read in these forums that lots of people had a problem getting WPA to work. I thought, certainly by the Drapper release this would be fixed. What is a higher priority than secure wireless?  Its not like I have some rare wireless card. I have the ipw2200 intel chips. 

I guess I will stick with SUSE which had no problem with WPA right from the start. Even Knoppix had no problem with WPA and that was with an older version. 

Ubuntu works well with WEP, but who wants to use WEP?

I am disappointed because the Ubuntu communtity seems to be very active and working to  make this a great distrubution. But for now, if you want WPA, openSuse seems to be the better choice.

---

### Post by sublime on 2006-06-10
[QUOTE=pssl220]I still have problems with setting up WPA.  In openSuse 10.1 it was very easy to set this up. With Breazy this was a problem. I read in these forums that lots of people had a problem getting WPA to work. I thought, certainly by the Drapper release this would be fixed. What is a higher priority than secure wireless?  Its not like I have some rare wireless card. I have the ipw2200 intel chips. 

I guess I will stick with SUSE which had no problem with WPA right from the start. Even Knoppix had no problem with WPA and that was with an older version. 

Ubuntu works well with WEP, but who wants to use WEP?

I am disappointed because the Ubuntu communtity seems to be very active and working to  make this a great distrubution. But for now, if you want WPA, openSuse seems to be the better choice.[/QUOTE]

give automatix a try.  it installed network manager no problem on my laptop.  the only thing im having trouble with is getting ndiswrapper or the bcm43xx driver working.  it sucks too cause thats the only thing that is wrong with my laptop.  i got xgl/compiz working perfectly.  its jsut those stupid ******* drivers.

---

### Post by Jeff250 on 2006-06-10
Snam--ALWAYS try the Dapper repository way first.  Your card is fairly new, so I don't know offhand if it's supported in Dapper natively, but install the Network Manager package for gnome to see, and then you can always uninstall it if doesn't seem to work.

pssl220--That's strange, since ipw2200 + Network Manager is supposed to work right out of the Dapper repository.  If for some bizarre reason it isn't working and you can't get it working, you should definitely choose a distro that has better support for your scenario.

---

### Post by Snam on 2006-06-11
[QUOTE=Jeff250]Snam--ALWAYS try the Dapper repository way first.  Your card is fairly new, so I don't know offhand if it's supported in Dapper natively, but install the Network Manager package for gnome to see, and then you can always uninstall it if doesn't seem to work.
[/QUOTE]

Thanks for this advice!

I installed the NetworkManager (0.6.2-0ubuntu7) from the repository. And comment out everything but the lo stuff in /etc/network/interfaces, as mentioned in [http://www.ubuntuforums.org/showthread.php?t=187747](http://www.ubuntuforums.org/showthread.php?t=187747).

And it works!!! There is nothing more to it. Now I'm sitting in my garden with my laptop on my lap enjoying the freedom of being wireless ;-)

---

### Post by Topfs on 2006-06-12
I followed this tutorial on Dapper Drake 6.06 LTS and I got network manager to show the scanned network and to atleast try to connect to them, a big step forward for me as I tried to use the one in Synaptic but there it didn't even scan right.

Well for my question, I can't connect, Not in WPA atleast. I have tried to connect to the neighbors open network (heheh, I am naughty I know ;) ) because I didn't want to  fiddle with my router if it isn't necessary But I could connect to theirs either, they MAY have mac block but I do not think so.

I use a Dlink DWL-G520 and I know this guide is not suited for this card but it has worked quite good 'til now so I would like to ask someone if they know howto get my card to connect to an unsecure router and I should probably be able to connect to my WPA.

I use the MadWIFI that is supplied with the CD, i386 not the i686

---

### Post by Jeff250 on 2006-06-13
If you'd like, you can try the latest Madwifi drivers from svn by reading up on it here:
[http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)

It looks like the following should work:
```
svn checkout http://svn.madwifi.org/trunk madwifi
cd madwifi
make
sudo make install
```
But unfortunately I lack the hardware to test the drivers to see if they work properly.

---

### Post by Topfs on 2006-06-13
[QUOTE=Jeff250]If you'd like, you can try the latest Madwifi drivers from svn by reading up on it here:
[http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)

It looks like the following should work:
```
svn checkout http://svn.madwifi.org/trunk madwifi
cd madwifi
make
sudo make install
```
But unfortunately I lack the hardware to test the drivers to see if they work properly.[/QUOTE]

Uhm I got an error:
/bin/sh: line 0: cd: /lib/modules/2.6.15-23-686/build: No such
 file or directory
Makefile.inc:95: *** /lib/modules/2.6.15-23-686/build is missing, please set KER 

could this be because I have the i386 installed and removed the i386?
I got it downloaded with the svn checkout but the make did not complete.


edit: Uhm it was, I reverted back to i386 drivers and the make succeded. rebooting now to see if it works.
I am a bit new to linux :)

---

### Post by Topfs on 2006-06-13
Hey what do you know it worked!

This guide is a go with the Dapper Drake LTS i386 restricted drivers plus:

svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
cd madwifi
make
sudo make install

D-Link DWL-G520 I think it is revision B.
WPA-PSK is fully operational, posting on it as we speak!.

Thx a million! you saved my day!
Edit: Skipped the driver installation in the guide for obvious reasons, but updated the ieee80211 thingy. If anyone needs to try it out.

---

### Post by Jeff250 on 2006-06-13
Excellent, I've added this to the guide!  It looks like you were missing the linux-headers-686 package when you got that error, whereas it seems you had the linux-headers-386 package, so I'd guess that's why switching to the 386 kernel allowed it to compile.  If you want, you can switch back to a 686 kernel, install the linux-headers-686 package, and then make and sudo make install the madwifi drivers again, but then again, if it ain't broke, why fix it? ;)

---

### Post by ignavia on 2006-06-13
[QUOTE=Topfs]Uhm I got an error:
/bin/sh: line 0: cd: /lib/modules/2.6.15-23-686/build: No such
 file or directory
Makefile.inc:95: *** /lib/modules/2.6.15-23-686/build is missing, please set KER 

could this be because I have the i386 installed and removed the i386?
I got it downloaded with the svn checkout but the make did not complete.


edit: Uhm it was, I reverted back to i386 drivers and the make succeded. rebooting now to see if it works.
I am a bit new to linux :)[/QUOTE]

I'm getting the same error, but with 386. Any ideas?

---

### Post by Topfs on 2006-06-14
I am not that good with linux but I would have tried to install the i686 package and try again, and if it doesn't work revert it back and try it one more time?.

You must have had the i686 package installed earlier? or?

Good luck atleast!

---

### Post by Jeff250 on 2006-06-14
Ah crap.  The linux headers part of my guide seems to have disappeared!  That would explain why everyone has been having trouble with them the last couple of days.

I just added (back) to the guide the instruction to do this:
```
sudo apt-get install gcc-3.4 linux-headers-`uname -r | awk 'BEGIN { FS="-" } ; { print $3 }'`
```

That should fix the problem.
edit: I've updated it with an awk script to grab the linux-headers metapackage for your platform.  Don't worry if you don't know what this means yet. ;-)

---

### Post by decon on 2006-06-14
Great howto, just to bad that it doesnt work for me atm :( 

When i have to rebooted im not seeing applet/deamon or whatever in the Notification Area :( Then I tried to run nm-applet and I can see that the Notification Area is somehow getting expanded.

Meh I then try to do the kill commands that you say we should try if it doesnt work. Then i'm getting this:
```
^[[Adecon@decon-laptop:~$ sudo killall NetworkManager
NetworkManager: no process killed
decon@decon-laptop:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        nm_dbus_init (): nm_dbus_init() could not acquire the NetworkManager service.
  Message: 'Connection ":1.30" is not allowed to own the service "org.freedesktop.NetworkManager" due to security policies in the configuration file'
NetworkManager: <ERROR> [1150297458.255560] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:         NetworkManager(main+0x4b8) [0x8067185]
NetworkManager:         /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d5bea2]
NetworkManager:         NetworkManager [0x80530b1]
Trace/breakpoint trap
decon@decon-laptop:~$

```

Some help please :D

---

### Post by TwiceOver on 2006-06-14
Everything went great until I got to:

./autogen.sh

I received a bunch of errors and when complete I was unable to run the make command.

My errors can be found at [www.abigmailbox.com/error.txt](www.abigmailbox.com/error.txt)

So close, yet so far away...

---

### Post by Jeff250 on 2006-06-14
Decon--redo the part of the guide where it says to gedit gnome/applet/nm-applet.conf and gedit src/NetworkManager.conf and make sure that you've made the necessary changes to those files.
Then do this again:
```
sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/
sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/
```
... and give it another reboot.

TwiceOver--Are you running Breezy?  If so, you'll get this error because libiw-dev isn't new enough.  Otherwise, if you're running Dapper, did you forget to run:
```
sudo apt-get build-dep network-manager
```  Regardless, the problem is with the libiw-dev package being either missing or not new enough.  The rest of those warnings are ignorable.

---

### Post by TwiceOver on 2006-06-14
[QUOTE=Jeff250]TwiceOver--Are you running Breezy?  If so, you'll get this error because libiw-dev isn't new enough.  Otherwise, if you're running Dapper, did you forget to run:
```
sudo apt-get build-dep network-manager
```  Regardless, the problem is with the libiw-dev package being either missing or not new enough.  The rest of those warnings are ignorable.[/QUOTE]

Yup that was the problem.  After I installed that package I finished up the rest of the How-To and am now posting this reply from my couch via WPA Secured Wireless!

Thanks for the great tutorial and all the help.

---

### Post by decon on 2006-06-14
[QUOTE=Jeff250]Decon--redo the part of the guide where it says to gedit gnome/applet/nm-applet.conf and gedit src/NetworkManager.conf and make sure that you've made the necessary changes to those files.
Then do this again:
```
sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/
sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/
```
... and give it another reboot.[/QUOTE]
I'm still getting the same errors :(
The files looks like this:
Networkmanaget.conf
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
<policy user="decon">
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>
        <policy at_console="true">
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>
        </policy>
        <policy context="default">
                <deny own="org.freedesktop.NetworkManager"/>
                <deny send_destination="org.freedesktop.NetworkManager"/>
                <deny send_interface="org.freedesktop.NetworkManager"/>
        </policy>
</busconfig>


```
nm-applet
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
<policy user="decon">
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>
	<policy at_console="true">
		<allow own="org.freedesktop.NetworkManagerInfo"/>

		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManagerInfo"/>

		<deny send_destination="org.freedesktop.NetworkManagerInfo"/>
		<deny send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
</busconfig>


```

EDIT: Okay i have changed decon to root and it now shows the nm-applet :) BUT I only have "Wired Network" in the list :( Why arent my wifi there ?

This is my hardware:```
decon@decon-laptop:~$ lspci 0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:00.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 802a (rev 01)
0000:02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
decon@decon-laptop:~$

```

Soon getting there, just a lil' more help ;)

---

### Post by Jeff250 on 2006-06-15
Did your ipw2200 not work on a default Ubuntu 6.06 install?
Check ```
lsmod | grep ipw2200
``` to make sure that the driver is loaded.  Also, make sure that your wifi network isn't on a hidden ssid.  If it is, you'll have to "Connect to other wireless network..." and type it in before it will show up.

---

### Post by elamericano on 2006-06-15
sudo apt-get build-dep network-manager:

Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for network-manager could not be satisfied.

That's not helpful. Why doesn't it say at least one dependency that hasn't been satisfied? Everything was fine until that step. How do I progress?

---

### Post by Jeff250 on 2006-06-15
You can try:
```
apt-cache showsrc network-manager
```
and try to manually satisfy the dependencies under "Build-Depends:".

---

### Post by kpkeerthi on 2006-06-15
Guys.. is this complication really required for installing network manager.

I just searched for 'network manager' in synaptic package manager, selected 'network-manager-gnome', marked for installation and applied. Restart, open terminal and type nm-applet and done. It worked like a charm. I have intel 2200 chipset.

---

### Post by elamericano on 2006-06-15
[QUOTE=Jeff250]You can try:
```
apt-cache showsrc network-manager
```
and try to manually satisfy the dependencies under "Build-Depends:".[/QUOTE]
Thanks, the problem is this one:
```
libdbus-glib-1-dev:
  Depends: libdbus-glib-1-2 (=0.60-6ubuntu8) but 0.60-6ubuntu9 is to be installed
 Depends: libdbus-1-dev but it is not going to be installed
```
I guess it want's me to back rev libdbus-glib-1-2, but I can't uninstall it and force install the other, because tons of packages would be removed along with it.

---

### Post by elamericano on 2006-06-15
I was able to use aptitude to roll back to previous versions:
Use / to search for the package
Press enter when you are on the right package
Scroll down to see the available versions
Press + to select the version you want
Press g to summarize changes
and g again to execute them.

After downreving libdbus-glib-1 and libdbus-1, I was able to install all the dev packages that were dependent on them. sudo apt-get build-dep network-manager certainly beats selecting these one by one.

---

### Post by swordthrower on 2006-06-16
I performed the howto step-by-step, but ran into an interesting problem.

When I got to this part:

```
./autogen.sh
```

It complains that wpasupplicant is not installed.

I investigated, and it turns out that when I did:

```
cd ~/wpa
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs co hostap
cd hostap/wpa_supplicant
cp defconfig .config
sudo apt-get build-dep wpasupplicant
make
sudo make install
```


it didnt' actuall install! Why? I am a semi-noob, but have been using linux for a few years now, and can't figure out why "sudo make install" isn't actually working... (especially since I didn't get any errors).

Thanks in advance for any suggestions. Hopefully I'm just missing something simple here.

---

### Post by peteruta on 2006-06-16
WEP does not with with the madwifi for me.
I have Toshiba Tecra M2 and have tried the how to with no success.

I did find in my searching the following.
Kernel .config should have.
CONFIG_NET_RADIO=y
CONFIG_FW_LOADER=y
CONFIG_CRYPTO=y

These are not set in the 6.06 header file for Ubuntu...

I now need to learn how to compile the Ubuntu kernel or go back to SuSE 10.1 which has AWSOME wifi support now... Im getting tired of batteling this one.

---

### Post by InDenial on 2006-06-17
Hi everyone,

I am confused. I have a rt2500 wireless card in my laptop which supports wpa out of the box as far as I can tell. (I can get it working by just changing my /etc/network/interfaces file as metioned in the [Wiki]("https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo")

I installed network manager doing 
```

sudo apt-get network-manager-gnome
```

Now I have a new icon automaticly at boot on the top right which gives me the option to connect to a new wireless network. I do however not have the option of choosing wpa security.

I could ofcourse install the cvs version of network manager but I want to know if this solves my problem and if I maybe need to do something else to get network manager working with wpa..

thanks in advance.

---

### Post by elamericano on 2006-06-17
[QUOTE=swordthrower]I performed the howto step-by-step, but ran into an interesting problem.

When I got to this part:

```
./autogen.sh
```

It complains that wpasupplicant is not installed.

I investigated, and it turns out that when I did:

```
cd ~/wpa
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs co hostap
cd hostap/wpa_supplicant
cp defconfig .config
sudo apt-get build-dep wpasupplicant
make
sudo make install
```


it didnt' actuall install![/QUOTE]
Sometimes those make install scripts don't work in every distribution. Anyway, I think in the case of wpa_supplicant and Ubuntu, you only need to copy the binaries you just built, wpa_supplicant, wpa_cli, and wpa_passphrase to /sbin. For me the make install copied them to /usr/local/sbin and "which wpa_supplicant" correctly points to them, but the ubuntu package that's installed by default puts the binaries in /sbin - so that's what I usually use.

---

### Post by elamericano on 2006-06-17
[QUOTE=InDenial]
I could ofcourse install the cvs version of network manager but I want to know if this solves my problem and if I maybe need to do something else to get network manager working with wpa..

thanks in advance.[/QUOTE]
The 0.6.2 package supports WPA, you do not need the CVS version. I assume wpasupplicant is installed. If you select "Connect to Other Wireless Network..." and look in the Wireless Security drop-down-box, there's no WPA?

---

### Post by elamericano on 2006-06-17
[QUOTE=peteruta]WEP does not with with the madwifi for me.
I have Toshiba Tecra M2 and have tried the how to with no success.

I did find in my searching the following.
Kernel .config should have.
CONFIG_NET_RADIO=y
CONFIG_FW_LOADER=y
CONFIG_CRYPTO=y

These are not set in the 6.06 header file for Ubuntu...

I now need to learn how to compile the Ubuntu kernel or go back to SuSE 10.1 which has AWSOME wifi support now... Im getting tired of batteling this one.[/QUOTE]
Did the driver work? Did you depmod -a and reboot? when you try to set the wep key using ifconfig, what happens?

Don't bother about the kernel. You just need the headers for your current kernel to compile. WEP decryption takes place in wireless card chip once the wep key has been sent down. The kernel and the rest of your computer have nothing to do with it, as it will receive nothing but cleartext.

---

### Post by InDenial on 2006-06-17
[QUOTE=elamericano]The 0.6.2 package supports WPA, you do not need the CVS version. [/quote]
Okay.. I thought the same. So lets go on to the next one.
> I assume wpasupplicant is installed.
Yes. Checked it. It is installed.. on to the next one.

> If you select "Connect to Other Wireless Network..." and look in the Wireless Security drop-down-box, there's no WPA?

You are correct. No WPA in the dropdown.

---

### Post by nekr0z on 2006-06-18
Well I did > sudo apt-get install knetworkmanager
As I run it, it would try to connect, and finally connects. But as it connects, either wired or wireless, IP appears to be not as it should according to DHCP. Certainly, the network doesn't work at all.

But as I do
> sudo dhclient eth0 (or eth1)
the interface starts working with no problem, until the next reconnection.

What the hell?

---

### Post by elamericano on 2006-06-21
[QUOTE=InDenial]You are correct. No WPA in the dropdown.[/QUOTE]
wpa_supplicant does not appear to support your wireless card

[http://hostap.epitest.fi/wpa_supplicant/]("http://hostap.epitest.fi/wpa_supplicant/")

However, you should be able to get it working if you use ndiswrapper.

---

### Post by InDenial on 2006-06-22
[QUOTE=elamericano]wpa_supplicant does not appear to support your wireless card

[http://hostap.epitest.fi/wpa_supplicant/]("http://hostap.epitest.fi/wpa_supplicant/")

However, you should be able to get it working if you use ndiswrapper.[/QUOTE]

I know wpa_supplicant does not support my wireless card because my card is supported by linux AND supports wpa out of the box... 

Ok lets see if I understand this:

[LIST]
[*]I have a fully supported card for linux. 
[*]I do not need any applications to get wpa running under linux.
[*]I need an application which makes it possible to choose between wireless networks on the fly because I have more than one accespoint I have to be able to connect to
[*]network manager does not work because it uses wpa_supplicant
[*]if my card is not supported by wpa_supplicant I can not use this application
[*] If I still want to be able to use the application I would have to use ndiswrapper[/LIST]

Maybe it is just me.. but doesn't that sound weird?

Is there an application like this which WILL work with my wireless card? More specific: Is there an application which does what I want and does support cards which support wpa out of the box without needing wpa_supplicant?

---

### Post by kleeman on 2006-06-22
[QUOTE=InDenial]I know wpa_supplicant does not support my wireless card because my card is supported by linux AND supports wpa out of the box... 

Ok lets see if I understand this:

[LIST]
[*]I have a fully supported card for linux. 
[*]I do not need any applications to get wpa running under linux.
[*]I need an application which makes it possible to choose between wireless networks on the fly because I have more than one accespoint I have to be able to connect to
[*]network manager does not work because it uses wpa_supplicant
[*]if my card is not supported by wpa_supplicant I can not use this application
[*] If I still want to be able to use the application I would have to use ndiswrapper[/LIST]

Maybe it is just me.. but doesn't that sound weird?

Is there an application like this which WILL work with my wireless card? More specific: Is there an application which does what I want and does support cards which support wpa out of the box without needing wpa_supplicant?[/QUOTE]


Have a look at this thread:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/534126.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/534126.html)

In particular these instructions for your card:

"The problem with Linux wireless right now is that different drivers have different ways of configuring. Note there are two versions of WPA too: WPA1 and WPA2. WPA2 is supposed it be backwards compatible...

Anyway, for my RT2500 based wireless card, I had to run:

iwconfig ra0 essid blah
iwconfig ra0 mode managed
iwpriv ra0 set Channel=1
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK=blahblah
iwpriv ra0 set TxRate=0

How did I figure that out? A lot of documentation reading. :("

---

### Post by InDenial on 2006-06-22
[QUOTE=kleeman]Have a look at this thread:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/534126.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/534126.html)

In particular these instructions for your card:

"The problem with Linux wireless right now is that different drivers have different ways of configuring. Note there are two versions of WPA too: WPA1 and WPA2. WPA2 is supposed it be backwards compatible...

Anyway, for my RT2500 based wireless card, I had to run:

iwconfig ra0 essid blah
iwconfig ra0 mode managed
iwpriv ra0 set Channel=1
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK=blahblah
iwpriv ra0 set TxRate=0

How did I figure that out? A lot of documentation reading. :("[/QUOTE]

The problem was not to get wpa working. This is as easy as not missing the toilet when taking a piss sitting down. THe problem is the the support for different wireless ap's. Like I want to be able to connect at home as well as when I am at work or somewhere else without having to change my /etc/network/interfaces file all the time. for this I need a tool, but it seems that all tools rely on wpa_supplicant

---

### Post by Grigs on 2006-06-22
I want to thank you very much for this posting. I am new to linux, like yesterday, just downloaded ubuntu to install along with xp pro, and was shocked when it did not have support for WPA for my intel 2915. What!?!?!

I followed the directions to the "t", and it worked!!! I am in Networking but have zero experience changing program files and scripting in a linux console, since I have primarlly have been a Windows guy. My hands were sweating at the end of this. :D I know, I suck...

Anyways, it works now and I just wanted to say thanks.

---

### Post by nekr0z on 2006-06-22
The further I go the stranger it is...

After having troubles with DHCP in network-manager I uninstalled network-manager, dhcdbd and knetworkmanager. Everything was immediately working OK, and I lived a couple of days like that.

But really lacking on-the-go WiFi network switching I installed knetworkmanager back today. It doesn't spoil DHCP any longer, instead it plainly doesn't work at all! Knetworkmanager doesn't see any network, neither wireless nor even wired!

During these days between uninstalling and installing back I have not installed or tweaked anything to deal with networking. I actually only installed stellarium (that is an astronomy thing) and vym (a mindmapping thing)...

I just don't understand what's going on in my laptop.

---

### Post by Jeff250 on 2006-06-23
How are you installing knetworkmanager, since it isn't in the guide?  If it's through the Dapper repos, it depends on the network-manager package, which itself depends on wpasupplicant, etc., so by installing the knetworkmanager package, you would be reinstalling all of these old packages, which would cause conflicts.

---

### Post by nekr0z on 2006-06-23
That's right, I do it through repos, and network-manager and dhcdbd are reinstalled. But I never used any newer version, so there should not be any conflict out there.

---

### Post by Jeff250 on 2006-06-23
Oh, nevermind, I thought that you had followed the complete guide.  What driver does your card use?

---

### Post by nekr0z on 2006-06-23
ipw2100 or even ipw2200 I believe, since it's an Intel BG2200 WiFi card.

By the way, I have read on one of the forums that it's a good idea to have this driver start with a "-led" key to make the WiFi led on a laptop work, so I wonder how to do it...

---

### Post by nekr0z on 2006-06-24
Now this is getting funny: after 3 or 4 reboots today (I was testing some RAM modules from Kingston and rebooted to run MemTest) NetworkManager started to work, all of a sudden. With broken DHCP, again.

---

### Post by Grigs on 2006-06-25
I followed this how to and it worked perfect for me. 

Yesterday I went to change some icons around I guess lost the shortcut to Network Manager, or the supplicant, or whatever the program was that allowed me to change wireless networks, passwords and the configuration of them. Does anyone know which file I am looking for to make the shortcut too? 

Everything about NM works, I just cant get to the configuration panel to change the config.

---

### Post by Grigs on 2006-06-25
OK. I figured this out. After changing around my panels I realized that I had removed the Area Notification Panel. This is where the NM-Applet resides. 

Which by the way is really confusing. It is a good thing this is not an official fix for WPA, b/c it has little bit to go before it is robust enough. 

What if I just wanted to put the NM manager applet on the desktop or somewhere besides the notification area panel?

---

### Post by -Chi.0 on 2006-06-25
I can't get this to work out, when I run this part of the code ](*,) 

```
sudo apt-get build-dep wpasupplicant
```

i get this back as seen in console:
```
root@Lappy:~/wpa/hostap/wpa_supplicant# sudo apt-get build-dep wpasupplicant
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

it their a way to fix this so I can continue? Any Help would be grately appreciated :D 

note: (I do have [COLOR="Magenta"]ndswrapper[/COLOR] setup I don't know if it's casing problems & my goal w/ this is to have wpa1 supprort for my **Delink DWL-G650M pcmcia card**, I might be going down the worng path w/ this)

---

### Post by Grigs on 2006-06-26
Make sure that when you do it that you do not have synaptic manager open. Or any other ubuntu process open that pulls installs off the net. 

Like your web broswer is ok to be open, but I know having synaptic manager open while trying to execute that command will generate thar error.

---

### Post by nekr0z on 2006-06-28
I still have problems with DHCP when using NetworkManager. Now I seem to see where the problem lays... Here is the part of /var/log/syslog:
> Jun 29 04:14:28 localhost NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
Jun 29 04:14:28 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 29 04:14:28 localhost NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0
Jun 29 04:14:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 29 04:14:29 localhost dhclient: DHCPOFFER from 172.16.0.1
Jun 29 04:14:29 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jun 29 04:14:29 localhost dhclient: DHCPACK from 172.16.0.1
Jun 29 04:14:29 localhost dhclient: bound to 172.16.0.12 -- renewal in 265757 seconds.
Jun 29 04:14:37 localhost kernel: [17439882.524000] eth0: no IPv6 routers present
Jun 29 04:15:13 localhost NetworkManager: <information>^IDevice 'eth0' DHCP transaction took too long (>45s), stopping it.
Jun 29 04:15:13 localhost dhclient: DHCPRELEASE on eth0 to 172.16.0.1 port 67
Jun 29 04:15:14 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Jun 29 04:15:14 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0
Jun 29 04:15:14 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0
Jun 29 04:15:14 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
Jun 29 04:15:14 localhost NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf.
Jun 29 04:15:14 localhost NetworkManager: <information>^Iautoip: Sending probe #0 for IP address 169.254.108.117.
Jun 29 04:15:14 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jun 29 04:15:16 localhost NetworkManager: <information>^Iautoip: Sending probe #1 for IP address 169.254.108.117.
Jun 29 04:15:16 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jun 29 04:15:18 localhost NetworkManager: <information>^Iautoip: Sending probe #2 for IP address 169.254.108.117.
Jun 29 04:15:18 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jun 29 04:15:20 localhost NetworkManager: <information>^Iautoip: Sending announce #0 for IP address 169.254.108.117.
Jun 29 04:15:20 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jun 29 04:15:23 localhost NetworkManager: <information>^Iautoip: Sending announce #1 for IP address 169.254.108.117.
Jun 29 04:15:23 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jun 29 04:15:26 localhost NetworkManager: <information>^Iautoip: Sending announce #2 for IP address 169.254.108.117.
Jun 29 04:15:26 localhost NetworkManager: <information>^Iautoip: Waiting for reply...
Jun 29 04:15:29 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 29 04:15:29 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
Jun 29 04:15:29 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 29 04:15:30 localhost NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification!
Jun 29 04:15:30 localhost NetworkManager: <information>^IActivation (eth0) Finish handler scheduled.
Jun 29 04:15:30 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 29 04:15:30 localhost NetworkManager: <information>^IActivation (eth0) successful, device activated.
Jun 29 04:15:30 localhost NetworkManager: <information>^Imatch
Jun 29 04:15:30 localhost NetworkManager: <information>^Imatch
Jun 29 04:15:30 localhost ntpdate[17451]: can't find host ntp.ubuntu.com
Jun 29 04:15:30 localhost ntpdate[17451]: no servers can be used, exiting
Jun 29 04:15:41 localhost kernel: [17439946.700000] eth0: no IPv6 routers present

Looks like NetworkManager asks dhclient to get an IP, dhclient does this, but NetworkManager does not understand that IP is received...

Any ideas?

---

### Post by Agent86 on 2006-06-29
[QUOTE=Jeff250]I just added (back) to the guide the instruction to do this:
```
sudo apt-get install gcc-3.4 linux-headers-`uname -r | awk 'BEGIN { FS="-" } ; { print $3 }'`
```That should fix the problem.
edit: I've updated it with an awk script to grab the linux-headers metapackage for your platform.  Don't worry if you don't know what this means yet. ;-)[/QUOTE]
I dist-upgraded my kernel to 2.6.15-25 from my Dapper install, and removed the old kernel stuff. Now I'm following your guide, but the linux-headers metapackage currently available is version 2.6.15.23 (there is no newer version available yet that Synaptic has found). Can I go ahead and compile with this metapackage? Will I have to recompile if and when the metapackage upgrade is available?

---

### Post by jka/v on 2006-06-29
Hi, I get stuck at the section for make in ipw

I have an intel ipw3945 chipset, and so downloaded that to my ~/wpa dir.

I go in, and tar it, no problem.  But when I type in make, I get the following error:

make: *** No targets specified and no makefile found.  Stop.

When I type in sudo make install, I get this error:

make: *** No rule to make target `install'.  Stop.


When I untar ipw3945-1.1.0.pre2 I get the following files:
~/wpa# tar -zxvf ipw3945-1.1.0-pre2.tgz
ipw3945-1.1.0-pre2/
ipw3945-1.1.0-pre2/load
ipw3945-1.1.0-pre2/Makefile
ipw3945-1.1.0-pre2/ISSUES
ipw3945-1.1.0-pre2/FILES
ipw3945-1.1.0-pre2/LICENSE
ipw3945-1.1.0-pre2/dvals
ipw3945-1.1.0-pre2/ipw3945_daemon.h
ipw3945-1.1.0-pre2/LICENSE.BSD
ipw3945-1.1.0-pre2/LICENSE.GPL
ipw3945-1.1.0-pre2/GIT_SHA1
ipw3945-1.1.0-pre2/unload
ipw3945-1.1.0-pre2/INSTALL
ipw3945-1.1.0-pre2/CHANGES
ipw3945-1.1.0-pre2/snapshot/
ipw3945-1.1.0-pre2/snapshot/ISSUES
ipw3945-1.1.0-pre2/snapshot/check_kernel
ipw3945-1.1.0-pre2/snapshot/check_ieee80211_compat
ipw3945-1.1.0-pre2/snapshot/find_ieee80211
ipw3945-1.1.0-pre2/snapshot/remove_kconfig_entry
ipw3945-1.1.0-pre2/snapshot/INSTALL
ipw3945-1.1.0-pre2/snapshot/add_radiotap
ipw3945-1.1.0-pre2/snapshot/patch_kernel
ipw3945-1.1.0-pre2/snapshot/README.ipw3945
ipw3945-1.1.0-pre2/in-tree/
ipw3945-1.1.0-pre2/in-tree/Kconfig.ipw3945
ipw3945-1.1.0-pre2/ipw3945.c
ipw3945-1.1.0-pre2/ipw3945.h
ipw3945-1.1.0-pre2/README.ipw3945

What am I doing wrong?  I've followed everything else, and it all seems fine up to this point.

I'm running dapper release, with 686-smp kernel

Thanks!

---

### Post by kiwiboyus on 2006-06-29
Thank you wheelspin for the great script! I have been messing with this since Dapper came out and now after trying your script again my Acer 4200 is connecting to my wireless w/wpa :)

No more mooching off my neighbours open wifi LOL

---

### Post by amanda on 2006-06-30
In case you got this far and stopped because you have no idea which chip set your modem has, may I suggest reading this: [http://ubuntuguide.org/wiki/Dapper#How_to_identify_Modem_chipset]("http://ubuntuguide.org/wiki/Dapper#How_to_identify_Modem_chipset") article on How to Identify Modem Chipset in the Ubuntu Guide.

I was confused as heck. Now I'm not. (For what it is worth, I got Network Manager running without going through the above, but that is another story.)

---

### Post by jka/v on 2006-06-30
I got mine working without doing this as well.

Ubuntu 6.06 supports the intel 3945 chipset natively, just need to add a few lines of script to /etc/network/interfaces, connects like a champ!

---

### Post by Jeff250 on 2006-06-30
jka/v, did you cd to the directory that the tar extracted?  If you're not in the wpa directory already, first:
```
cd ~/wpa
```
then:
```
cd ipw3945-1.1.0-pre2
```
then try "make" since it looks like there is definitely a Makefile being extracted there.

[QUOTE=Agent86]I dist-upgraded my kernel to 2.6.15-25 from my Dapper install, and removed the old kernel stuff. Now I'm following your guide, but the linux-headers metapackage currently available is version 2.6.15.23 (there is no newer version available yet that Synaptic has found). Can I go ahead and compile with this metapackage? Will I have to recompile if and when the metapackage upgrade is available?[/QUOTE]

The versions of the actual image and headers packages should match each other, but the metapackage versions aren't really comparable with the versions of the actual packages.  For example, the version of linux-image-2.6.15-23-686 should match the version of linux-headers-2.6.15-23-686, but the versions for metapackages like linux-headers-686 don't really matter.  I don't think you have anything to worry about as long as you have the latest from the Dapper repositories.

---

### Post by siriusnova on 2006-07-03
This doesn't seem to work with Networkmanager and madwifi-ng, (i wanted to compile the patches for aircrack etc with the madwifi drivers, interestingly i can dhcp an ip from a terminal but not through ntetwork manager..

Any ideas on how to incorporate the aircrack patches into the madwifi driver so that it works with networkmanager ?

---

### Post by cwalte on 2006-07-08
Thanks for this howto, I'm now able to connect wirelessly without any problems, in XP I keep losing the connection but not with Ubuntu. Now if only  Icould get the usb ports and sound working...

Cheers again!

Chris

---

### Post by sbrinkmann on 2006-07-16
Hello,
   thank you for this good Howto. The Network manager works but i can't connect to a network. I got always this message in the shell:

```

NetworkManager: <information>   Activation (eth1) started...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (eth1/wireless): access point 'Bresoly' is encrypted, and a key exists.  No new key needed.
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD eth1                wext    /usr/local/var/run/wpa_supplicant  '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 1'
NetworkManager: <information>   SUP: response was 'UNKNOWN COMMAND'
NetworkManager: <WARNING>        nm_utils_supplicant_request_with_check (): supplicant_send_network_config: supplicant error for 'AP_SCAN 1'.  Response: 'UNKNOWN COMMAND'
NetworkManager: <WARNING>        real_act_stage2_config (): Activation (eth1/wireless): couldn't send wireless configuration to the supplicant.
NetworkManager: <information>   Activation (eth1) failure scheduled...
NetworkManager: <information>   Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   Activation (eth1) failed for access point (Bresoly)
NetworkManager: <information>   Activation (eth1) failed.
NetworkManager: <information>   Deactivating device eth1.

```

Can Somebody tell me how to solve this Problem?

---

### Post by 5h4rk on 2006-07-17
Is it normal having both NetworkManager Applet 0.6.2 and Network Monitor 2.12.0 running together?

:-?

---

### Post by nrayever on 2006-07-17
excelent guide!!! :D :D 

for howto's like this is why i love ubuntu!! thanks a lot jeff250!!

nrayever

---

### Post by kleeman on 2006-07-18
Upgraded the kernel this morning to 2.6.15-26 and NetworkManager stopped working. nm-applet started  spinning as usual in gnome but then just dissappeared from the panel. I checked and it was running as a process just not showing up on the panel. Reverted to 2.6.15-25 kernel and it starts working again.

Hope this helps someone....

---

### Post by MrChonks on 2006-07-19
First off, excellent guide.  This is exactly what I needed for my attempt at getting WPA working.  Unfortunately, I am having a rather big problem: I went from having eth1 as my wireless nic, to having no eth1 at all after rebooting.

I went through your step-by-step instructions without any errors at all.  I rebooted and found the aformentioned issue.  Here are some logs that might help illustrate the issue:

root@<name>t42:/home/<name># NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <information>   eth0: Device is fully-supported using driver 'e1000'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker thread to start
NetworkManager: <information>   nm_device_init(): device's worker thread started, continuing.
NetworkManager: <information>   Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <information>   Deactivating device eth0.
NetworkManager: <information>   Updating allowed wireless network lists.
NetworkManager: <information>   Will activate wired connection 'eth0' because it now has a link.
NetworkManager: <WARNING>        nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

dmesg:

[17179607.328000] bridge-eth1: peer interface eth1 not found, will wait for it to come up
[17179607.328000] bridge-eth1: attached


So, do you have any idea why I would be dropping the interface afer the install?

Thanks for any help you can provide.

Chonks

---

### Post by Jeff250 on 2006-07-20
[quote="MrChonks"]First off, excellent guide. This is exactly what I needed for my attempt at getting WPA working. Unfortunately, I am having a rather big problem: I went from having eth1 as my wireless nic, to having no eth1 at all after rebooting.[/quote]

What driver are you using?  If you have, for example, an ipw card, you should see if the driver is listed with lsmod, a la:
```
lsmod | grep ipw
```

[quote="kleeman"]Upgraded the kernel this morning to 2.6.15-26 and NetworkManager stopped working. nm-applet started spinning as usual in gnome but then just dissappeared from the panel. I checked and it was running as a process just not showing up on the panel. Reverted to 2.6.15-25 kernel and it starts working again.

Hope this helps someone....[/quote]

Have you tried reinstalling ieee80211 and the driver for your card?  You need to do this for any new kernel, since new kernel means new drivers.

[quote="5h4rk"]Is it normal having both NetworkManager Applet 0.6.2 and Network Monitor 2.12.0 running together?[/quote]

Yes.  In fact, I don't even use the Network Monitor applet anymore, although I can see why it might be useful if you want to see when your adapter is sending/receiving.

---

### Post by popie on 2006-07-20
After working perfectly (with WPA) for over a month my Network Manager doesn't even list "Wireless connection" at all now. I was configuring a new Access Point, going back and forth between wired and wireless connections. Everything worked fine on new and old AP. Now this...

I originally got WPA working by simply installing Network Manager. That's all it took. Easy...

I have an IBM Thinkpad with an Atheros based mini-pci wireless card. 

I've completely removed and reinstalled Network Manager, no change. Wireless shows as active in Network Settings, but doesn't appear in Network Connection applet or Network Manager. 

Can someone tell me how to get this working again?

---

### Post by kleeman on 2006-07-20
> **Jeff250 said:**
> 


Have you tried reinstalling ieee80211 and the driver for your card?  You need to do this for any new kernel, since new kernel means new drivers.



Are not these updated automatically in the new linux-restricted package for the latest Ubuntu kernel?

---

### Post by MrChonks on 2006-07-20
root@<name>t42:/home/<name># lsmod | grep ipw
ipw2100               135140  0
ieee80211              52072  1 ipw2100


Funny thing is that while looking through the device manager yesterday, I realized that I had the 2100 drivers and not the 2200.  So, I re-ran all of the steps and just did the 2100 drivers.  That worked to get my wireless working.  But, unfortunately, I am still having the problem where NetworkManager is only seeing the wired interface.  Any ideas?

Thanks

---

### Post by Jeff250 on 2006-07-20
[quote="kleeman"]Are not these updated automatically in the new linux-restricted package for the latest Ubuntu kernel?[/quote]

If you're talking about dapper-security kernel updates, these updates usually contain some security updates and a few driver updates to solve large bugs.  Also, I checked the changelog for the restricted kernel image, and there haven't been any updates to it since Dapper has been released.  They've just incremented the version number to match the free kernel so far.  I assume you're a madwifi user since you're asking about the restricted modules, but in case you or anyone else is interested, the ipw* drivers and ieee80211 subsystem is in the free kernel, but the madwifi drivers are in the restricted modules.

Now, if you're talking about new edgy kernels, I haven't been following edgy development, but it still isn't an automatic update to the latest version, especially in the case of the restricted modules.  As for the free kernel image, only the changes in major versions will guarantee updates, like 2.6.15 to 2.6.17, but the -##'s are completely at the Ubuntu developers' discretion.

[quote="MrChonks"]Funny thing is that while looking through the device manager yesterday, I realized that I had the 2100 drivers and not the 2200. So, I re-ran all of the steps and just did the 2100 drivers. That worked to get my wireless working. But, unfortunately, I am still having the problem where NetworkManager is only seeing the wired interface. Any ideas?[/quote]

You might want to try...
```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```... again now that your interface is working.

[quote="popie"]Can someone tell me how to get this working again?[/quote]

You can try the above too.  Of course, usually at this point, the output usually isn't very helpful for us mere users, and there's probably an issue with your driver's support of your specific chipset, but it is strange that it originally was working.  You might try looking through Synaptic's history to see if you updated anything relevant around the time it stopped working.

---

### Post by kleeman on 2006-07-20
> **Jeff250 said:**
> If you're talking about dapper-security kernel updates, these updates usually contain some security updates and a few driver updates to solve large bugs.  Also, I checked the changelog for the restricted kernel image, and there haven't been any updates to it since Dapper has been released.  They've just incremented the version number to match the free kernel so far.  I assume you're a madwifi user since you're asking about the restricted modules, 
Yeah sorry I wasn't clear I am using a madwifi driver from restricted and there was no sign that it had stopped working on upgrade (I looked in dmesg) just that NetworkManager crashed. Guess I'll just stick to the old kernel until this is sorted out. I did have the right version of the restricted package installed for the kernel.

---

### Post by Jeff250 on 2006-07-20
You still should try installing the madwifi drivers while booted up in the latest kernel, because unless those same drivers just happen to be updated in the kernel update (which is unlikely for the dapper-security repository), you're actually downgrading to the driver versions you had before this guide.

---

### Post by popie on 2006-07-21
> **Jeff250 said:**
> 
You can try the above too.  Of course, usually at this point, the output usually isn't very helpful for us mere users, and there's probably an issue with your driver's support of your specific chipset, but it is strange that it originally was working.  You might try looking through Synaptic's history to see if you updated anything relevant around the time it stopped working.

Thanks! I tried your suggestion of killing NetworkManager and restarting. The first time it didn't help, but then, after fussing around removing and reinstalling Network Manager, WPA supplicant, etc. I tried it again and voila! Wireless started working again!

I THINK the key change that helped was in System, Administration, Networking, Wireless, Properties, and unchecking enabled, (so the Wireless entry in Networking appeared as "Not configured", which is different from being un-activated), then after killing and restarting Network Manager, wireless appeared as an option in Network Manager again!

---

### Post by kleeman on 2006-07-21
> **Jeff250 said:**
> You still should try installing ieee80211 and the madwifi drivers while booted up in the latest kernel, because unless those same drivers just happen to be updated in the kernel update (which is unlikely for the dapper-security repository), you're actually downgrading to the driver versions you had before this guide.
I actually wasn't ever using the latest madwifi drivers. All along I have been using the standard Dapper restricted drivers. I followed the first option in your howto namely simply install the 0.6.2 NM packages in Dapper. Do you think the latest madwifi drivers would be more stable with NetworkManager or do you think this irrelevant? I am unclear about how important the details of the kernel drivers are to the operation of NetworkManager...

---

### Post by Jeff250 on 2006-07-21
Oh, that's strange then that the kernel update broke it.  Since it's not working with the latest kernel, it can't hurt to try, since you're not using it.  As long as you're booted up in that kernel, it won't affect any others, including your older kernel that already works with NM.

---

### Post by guriben on 2006-07-22
Hello. I just thought I would add a small something to this thread regarding getting Dapper working on my Lenovo C100 which comes with the Broadcom 43xx chipset.

To check for Broadcom WLAN Chipset use "lspci | grep Broadcom"

Network Manager and NDISWrapper were installed either as part of Dapper (6.06 LTS) or Automatix (it may be that NDISWrapper was already installed but I checked it in Automatix also).

Used Synaptic to install bcm43xx-fwcutter.

In a terminal:

sudo gedit /etc/modprobe.d/blacklist

Add:

blacklist bcm43xx

To the end of the file and save.

In the terminal:

sudo rmmod bcm43xx
sudo rmmod ndiswrapper

(I ignored the error)

sudo modprobe ndiswrapper

No need to reboot. Left-clicked NetworkManager icon, entered the details for my non-broadcast SSID and the WPA key.

Worked!

:)

[UPDATE:] Looks like I have to do this every boot?.....surely not.
[UPDATE:] Did something more permanent, all I have to do now is click the applet, choose a New Wireless Network...enter my SSID and TKIP'd WPA key...enter my keychain password (why?) and done...no more hassle than on my hideous work XP Laptop...more a problem with non-broadcast SSID and WPA than anything I think...

---

### Post by elamericano on 2006-07-25
Is installing ieee80211 a step that ought to be done, even if everything is working? I build the latest dev releases of madwifi modules and wpa_supplicant along with the latest CVS of NetworkManager. I've never built ieee80211, but It's never been a problem after many updates.

What could possibly go wrong? ;-)

---

### Post by Jeff250 on 2006-07-26
Actually, I don't think that the madwifi drivers even use the ieee80211 module, but I included it in the guide to err on the side of caution.  A 'lsmod | grep 80211' would probably solve this for sure.

---

### Post by MrChonks on 2006-07-26
Everything is working fine now in regard to the functionality of the new NetworkManager.  However, is anyone experiencing a higher amount of network latency since the change to the new NetworkManager.  With the old NetworkManager, browing http was quicker by a certain margin.  Now, I have had to utilize the fasterfox extension to get any sort of reasonable traffic speed.  Any ideas on this?  Anyone else running into this?  Let me know if you have any questions.

Thanks,
Chonks

---

### Post by elamericano on 2006-07-28
> **Jeff250 said:**
> Actually, I don't think that the madwifi drivers even use the ieee80211 module, but I included it in the guide to err on the side of caution.  A 'lsmod | grep 80211' would probably solve this for sure.

You are correct. The module is not loaded.

---

### Post by Jaymac on 2006-08-05
You absolute legend.. I love you!

I think this is my first post... I've been lurking for well over a year, and spend quite a lot of time active in IRC, but I just had to express my sincere gratitude to you for this fantastic guide :D

---

### Post by Explodinglemur on 2006-08-06
I've got NetworkManager working great with my wireless device and WPA.  However, it doesn't seem to know my wired ethernet interface exists.  Any thoughts on why that might be?  (sudo ifconfig eth0 up and sudo dhclient eth0 works, it'd be nice to have all my wireless setup in one place though)

---

### Post by 5-HT on 2006-08-06
> **Explodinglemur said:**
> I've got NetworkManager working great with my wireless device and WPA.  However, it doesn't seem to know my wired ethernet interface exists.  Any thoughts on why that might be?  (sudo ifconfig eth0 up and sudo dhclient eth0 works, it'd be nice to have all my wireless setup in one place though)

What about commenting (placing a # in front of) all lines in /etc/network/interfaces pertaining to eth0?

---

### Post by Explodinglemur on 2006-08-06
> **5-HT said:**
> What about commenting (placing a # in front of) all lines in /etc/network/interfaces pertaining to eth0?

Already did that when I commented out eth1 (my wireless card).

---

### Post by kleeman on 2006-08-11
This guide worked perfectly for me. Had to put in a new PMCIA madwifi wireless card after the builtin aerial (but not card) blew. This caused my standard install NetworkManager from Dapper to stop working perhaps because it could not handle two ath interfaces.

The new NetworkManager seems to work better with gnome as well.

---

### Post by justinc on 2006-08-14
Thank you, thank you, thank you.  This howto worked perfect for me.

---

### Post by misha680 on 2006-08-14
This is now a HOWTO:

[http://www.ubuntuforums.org/showthread.php?p=1375266#post1375266](http://www.ubuntuforums.org/showthread.php?p=1375266#post1375266)

Misha

---

### Post by wbastien on 2006-08-17
ok the installation went through smoothly and when I restarted i see the network manager in the top right corner. i see my wireless connection and try to click on it but the menu closes. i tried clicking the little circle beside the network name but same thing, it doesnt open a dialog to connect or anything. i restarted again and now it doesnt see any wireless connections, but when i type iwlist scan i can see my wireless network and others around me. i havnt changed anything since the installation. i dont know why the wireless networks have dissapeared from the nm-applet. any help is appreciated. thanks.

---

### Post by misha680 on 2006-08-17
> **wbastien said:**
> ok the installation went through smoothly and when I restarted i see the network manager in the top right corner. i see my wireless connection and try to click on it but the menu closes. i tried clicking the little circle beside the network name but same thing, it doesnt open a dialog to connect or anything. i restarted again and now it doesnt see any wireless connections, but when i type iwlist scan i can see my wireless network and others around me. i havnt changed anything since the installation. i dont know why the wireless networks have dissapeared from the nm-applet. any help is appreciated. thanks.

If you are trying to connect to a LEAP network you need to click on "Connect to other network..." in the pulldown and put in the information there. Otherwise, I'm not sure what is going on. Did you follow the steps in the HOWTO about installing the files into /etc/dbus-1/event.d? Do they have executable permissions set up (just do a Properties in Nautilus to check)?

Misha

---

### Post by FrankL on 2006-08-19
Thanks for the great guide! I almost worked...:) ](*,) 

I got a Toshiba Tecra M7 with a intel 3945 wireless chipset and ubuntu 2.6.15-26-686 (for dual core). The installation of the network manager worked flawlessly and also the intel 80211 version 14 seemed to install. And also ipw3945 1.0.0 works (with and without the great script mentioned earlier). But that version doesn't allow WPA, does it? So I'm trying to install a newer version, but both with version 1.1.0 and version 1.0.12 I get the following error:


----------
frank@frank-laptop:~/Downloads/ipw3945-1.1.0$ make

 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


 Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
frank@frank-laptop:~/Downloads/ipw3945-1.1.0$ uname -r
2.6.15-26-686
------------

Does anyone know what I need to do to correct this? I tried uninstalling and reinstalling the different drivers, but it didn't help.

Thanks in advance,

      Frank

---

### Post by Jeff250 on 2006-08-21
Hmm, it might want the ieee80211 that comes with the kernel.  You could try going to your untarred ieee80211 source directory and then doing a "sudo make uninstall" and then reinstall the linux-image-2.6.15-26-686, linux-headers-2.6.15-26, and linux-headers-2.6.15-26-686 packages in Synaptic.  Then try installing those ipw3945 drivers.

---

### Post by batal on 2006-08-21
Hi there. 

Grats to this excellent guide, it worked very well for me. However, i have still one problem at the moment, and i cant find anything on the net about it.

I am using aan AVM Fritz! USB WLAN Stick with ndiswrapper. Before i used this guide i was never really able to connect to my AP with the NetworkManager. But connecting via wpa_supplicant command line worked very well.

Now after i used this guide the situation is like this:

The NetworkManager is loaded at the runlevels 2, 3, 4 and 5. After login nm-applet is loaded and the gnome-key-thing asks for the password. Then the NM tries to connect to the AP, but it wont work. BUT, if i kill all NM processes (2) and start it manually via the init script it just works as intended.

My Problem is that i can't see why this happens. I think it could be because NM is loaded before something other thats essential for it to work is started. 

Any ideas?


thanks,
batal

---

### Post by ephraste on 2006-08-25
> **misha680 said:**
> This is now a HOWTO:

[http://www.ubuntuforums.org/showthread.php?p=1375266#post1375266](http://www.ubuntuforums.org/showthread.php?p=1375266#post1375266)

Misha

Thank you for this great howto !!!
just like to hug you :KS :KS :KS 

i'll give a try to the new leap debs

________
Keep the pressure

---

### Post by misha680 on 2006-08-25
No prob. Since it worked for me it was simple enough to share. Hope it works.

Misha

> **ephraste said:**
> Thank you for this great howto !!!
just like to hug you :KS :KS :KS 

i'll give a try to the new leap debs

________
Keep the pressure

---

### Post by briggella on 2006-08-29
I have been struggling with wpa and Dlink G650 cards using the atheros chip for about 3 years. I could not get it working with Mandrake or Suse 10 so I have tried Ubuntu Dapper on my IBM Thinkpad T23. I have used CVS versions of NM, madwifi and WPA_supplican and I must say that this guide has been excellent. It is one of the few howtos where everything does what the guide says it will do and indeed I can connect with WPA, but this only last for 15-30 seconds and then disconnects. I enclose a log of my communication, hopefully as an attachment. I have changed my ESSID in the log to my_essid

Thanks for your thoughts

---

### Post by kaido on 2006-08-29
[B]Hello.
I have a thinkpad x31 wchich has cisco aironet 802.11b wifi card.
I am running dapper6.06 and have been trying to get the wpa to work for some time.
I have followed your guide to the end, and the error i get is following:[/B]

kaido@loom:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        nm_dbus_init (): nm_dbus_init() could not acqui re the NetworkManager service.
  Message: 'Connection ":1.13" is not allowed to own the service "org.freedeskto p.NetworkManager" due to security policies in the configuration file'
NetworkManager: <ERROR> [1156866385.327214] main (): nm_dbus_init() failed, exit ing. Either dbus is not running, or the NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:         NetworkManager(main+0x4b8) [0x8067e3d]
NetworkManager:         /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0x b7cbcea2]
NetworkManager:         NetworkManager [0x8053bf1]
Trace/breakpoint trap
kaido@loom:~$

**I also re-did a part of the guide as you recommended in earlier posts:**

Decon--redo the part of the guide where it says to gedit gnome/applet/nm-applet.conf and gedit src/NetworkManager.conf and make sure that you've made the necessary changes to those files.
Then do this again:
Code:

sudo cp src/NetworkManager.conf /etc/dbus-1/system.d/ sudo cp gnome/applet/nm-applet.conf /etc/dbus-1/system.d/

... and give it another reboot.
 [B]
This doesn't help.
My nm-applet.conf looks like this:[/B]

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy user="kaido">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy at_console="true">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManagerInfo"/>
		<deny send_destination="org.freedesktop.NetworkManagerInfo"/>
		<deny send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
</busconfig>

[B]What am I doing wrong? What should I try next?
Regards,
Kaido[/B]

---

### Post by loopjeremyloop on 2006-08-29
okay, i am completely at a loss here.

i have an intel 3945, and I have followed every guide I can find - and not only has NOTHING gotten wpa to work, but this guide has now completely removed my wireless card from my system.

I run lsmod to make sure that it's not loading, and it's not.  It used to, but... well...

Yeah.

So I downloaded the drivers from [http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net) - great.  Unpacked them.  No problem.  Then, I run "make", and I get the following lovely error:

```

jeremy@jeremy-laptop:~/wpa/ipw3945-1.0.12$ make

 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


 Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
jeremy@jeremy-laptop:~/wpa/ipw3945-1.0.12$

```

So... I've gone from working wireless (albeit no WPA) to no wireless at all and now can't get the drivers to install.

I am on a Dell Lattitude D820 (core duo / smp kernel / ipw3945).

Any ideas?

---

### Post by Jeff250 on 2006-08-30
brigella--I'm afraid I can't figure out what's wrong from the log.

kaido--
It looks like you're missing the "root" block.  There are also some spots where your copy says "In fo" instead of "Info", but this may have just occurred in copying?

Try this:
```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy user="kaido">
		<allow own="org.freedesktop.NetworkManager"/>
		<allow send_destination="org.freedesktop.NetworkManager"/>
		<allow send_interface="org.freedesktop.NetworkManager"/>
	</policy>
	<policy user="root">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy at_console="true">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManagerInfo"/>
		<deny send_destination="org.freedesktop.NetworkManagerInfo"/>
		<deny send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
</busconfig>
```

loopjeremyloop--
Does this:
[http://www.ubuntuforums.org/showpost.php?p=1403704&postcount=196](http://www.ubuntuforums.org/showpost.php?p=1403704&postcount=196)
help?

---

### Post by flyingmonkey on 2006-08-30
Hello,
I am trying to convince my Atheros based WLAN card using the madwifi drivers to connect to a WPA1 based access point using KNetworkManager.

The used software is:
Kernel based on Ubuntu-Sources 2.6.15. Madwifi divers madwifi-ng-r1705-20060816 (This is the latest snapshot. But I also tried this whole procedure using the latest stable snapshot madwifi-0.9.2 with the same result), wpa_supplicant 0.5.5 (I also tried 0.5.4, 0.5.3, 0.5.2 with the same result) and networkmanager 0.6.4. All recompiled from geberic sources.

The .config file of wpa_supplicant is:

CFLAGS += -I/usr/src/modules/madwifi-ng-r1705-20060816
CONFIG_CTRL_IFACE=y
CONFIG_DRIVER_HOSTAP=y
CONFIG_DRIVER_MADWIFI=y
CONFIG_DRIVER_WEXT=y
CONFIG_WIRELESS_EXTENSION=y
CONFIG_EAP_PSK=y

When I try to connect to a WPA protected network, I receive an ioctl[SIOCSIWAUTH]: Invalid argument message from networkmanager (the output of KNetworkManager contains hardly any detail from my point of vies, so it is omitted) and the authentication fails:

NetworkManager: <information>   wpa_supplicant(7155): Trying to associate with 0
0:15:e9:0d:9f:16 (SSID='salat' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(7155): CTRL_IFACE monitor send -
hexdump(len=50): 2f 75 73 72 2f 6c 6f 63 61 6c 2f 76 61 72 2f 72 75 6e 2f 4e 65
74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 39 32 32 2d
 32 00
NetworkManager: <information>   wpa_supplicant(7155): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(7155): WPA: clearing own WPA/RSN
IE
NetworkManager: <information>   wpa_supplicant(7155): Automatic auth_alg selecti
on: 0x1
NetworkManager: <information>   wpa_supplicant(7155): WPA: using IEEE 802.11i/D3
.0
NetworkManager: <information>   wpa_supplicant(7155): WPA: Selected cipher suite
s: group 8 pairwise 8 key_mgmt 2 proto 1
NetworkManager: <information>   wpa_supplicant(7155): WPA: set AP WPA IE - hexdu
mp(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2
 02
NetworkManager: <information>   wpa_supplicant(7155): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(7155): WPA: using GTK TKIP
NetworkManager: <information>   wpa_supplicant(7155): WPA: using PTK TKIP
NetworkManager: <information>   wpa_supplicant(7155): WPA: using KEY_MGMT WPA-PS
K
NetworkManager: <information>   wpa_supplicant(7155): WPA: Set own WPA IE defaul
t - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00
 00 50 f2 02
NetworkManager: <information>   wpa_supplicant(7155): No keys have been configur
ed - skip key clearing
NetworkManager: <information>   wpa_supplicant(7155): wpa_driver_wext_set_drop_u
nencrypted
[B]ioctl[SIOCSIWAUTH]: Invalid argument
WEXT auth param 2 value 0x4 - [/B]
NetworkManager: <information>     wpa_supplicant(7
155):
NetworkManager: <information>   wpa_supplicant(7155): wpa_driver_wext_set_operst
ate: operstate 0->0 (DORMANT)



I am able to successful authenticate using wpa_supplicant istself with wext driver:

@sunfire:~$ sudo wpa_supplicant -i ath0 -D wext -c /etc/wpa_supplicant.conf
Trying to associate with 00:15:e9:0d:9f:16 (SSID='salat' freq=2437 MHz)
Associated with 00:15:e9:0d:9f:16
WPA: Key negotiation completed with 00:15:e9:0d:9f:16 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:15:e9:0d:9f:16 completed (auth) [id=0 id_str=]

using the following configuration:
network={
        ssid="salat"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=<something>
}

Since the association process is successful using the wpa_supplicant directly, I assume the problem is somewhere between networkmanager and wpa_supplicant.

Has anybody stumbed over this problem and maybe any suggestion how to address this issue?

Thanks.

---

### Post by ChuckNH on 2006-08-30
> **Explodinglemur said:**
> I've got NetworkManager working great with my wireless device and WPA.  However, it doesn't seem to know my wired ethernet interface exists.  Any thoughts on why that might be?  (sudo ifconfig eth0 up and sudo dhclient eth0 works, it'd be nice to have all my wireless setup in one place though)

I've got to step in on this one......with same problem.  I set up WPA on my gateway config yesterday, then couldn't access 'net from Dapper.  Removed WPA, (back to default with no encryption) yet I cannot us Firefox or Thunderbird, although can ping server and upgrade pkgs (so obviously have a connection.  Mysterious, no?

---

### Post by loopjeremyloop on 2006-08-30
> **Jeff250 said:**
> 
loopjeremyloop--
Does this:
[http://www.ubuntuforums.org/showpost.php?p=1403704&postcount=196](http://www.ubuntuforums.org/showpost.php?p=1403704&postcount=196)
help?

HI!

Well, it's helping.  It got me back to where I started, looks like.

in case you're interested, I started another thread last night in the wireless section about my troubleshooting efforts - 
[http://www.ubuntuforums.org/showthread.php?t=246655](http://www.ubuntuforums.org/showthread.php?t=246655)
going to try recompiling the ipw driver next.

---

### Post by loopjeremyloop on 2006-08-30
OKAY

well, looks like I now have WPA support.  I think.

See, I'd know if I did if my network actually worked.  :)  Network manager shows up in the system notification area, says I'm connnected to the wired network (though it gives me a 169.x.x.x address, which is not what our DHCP server is handing out), and the wireless network SHOWS UP in the dialogues and allows me to enter my WPA info - but....

nothing connects.  

my theory is that there's a configuration SOMEWHERE that I'm missing.  I'm going back through this thread and finding it.  It's gotta be there.

It almost seems like network manager is fighting with network-admin (from the original gnome tools i think).  any thoughts on this one?


edit:  I just got a new hard drive for my laptop.  Gonna just try reinstalling on that fresh, and seeing if the original instructions actually DO work.  :)
edit2: and of course, dell sent me a PATA drive rather than SATA- even though I ordered sata... so it's gonna be a bit longer than this to get the new drive in.  :)  maybe i'll reinstall anyway, since I'm here...

---

### Post by kaido on 2006-08-30
> **Jeff250 said:**
> 
kaido--
It looks like you're missing the "root" block.  There are also some spots where your copy says "In fo" instead of "Info", but this may have just occurred in copying?


I added the "root" block and now the network manager runs fine.
Full respect, Jeff.
But i still can't connect to my WPA PSK network (the AP doesnt do EAP).

It shows my network in network manager under "Wireless Networks".
If I click on it, nothing happens.

If I choose "Connect to Other Wireless Network..." it let's me choose between 4  different securities: 3 WEP's and one LEAP. The last one allows only IEEE 802.1X and WPA-EAP and these wont work. I'm not sure what to put in the "User Name" field?

The strange thing is that I don't get any error messages.
How to troubleshoot this issue?
Where can I learn more about Network Manager and it's problems?

Regards,
Kaido

---

### Post by briggella on 2006-08-31
Well I finally got mine working last night. In the end I abandoned network manager as it kept wiping my /etc/resolv.conf. I also used a different command for wpa_supplicant. So

/usr/local/sbin/wpa_supplicant -B -i ath0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf and it fired up.

(extra note, I put wpa_supplicant in /usr/local/sbin and wpa_supplicant.conf in /etc/wpa_suppplicant. This may be different on your box)

The crucial difference appears to be using wext rather than madwifi. After that I had to set bup my routing tables as follows.My laptop is 192.168.0.4 and the router/AP is 192.168.0.1. I abandoned DHCP.

ifconfig ath0 192.168.0.4

route add -net 192.168.0.0 netmask 255.255.255.0 dev ath0

route add default 192.168.0.1 gw

and /etc/resolv.conf add the line

nameserver 192.168.0.1

Finally it works. Now all I need to do is work out how to get it all happening automatically on boot and be able to switch to wired network occsaionally.:D

---

### Post by Jeff250 on 2006-08-31
kaido, you can try here:
[http://mail.gnome.org/mailman/listinfo/networkmanager-list](http://mail.gnome.org/mailman/listinfo/networkmanager-list)
for more troubleshooting info or help.

---

### Post by kaido on 2006-09-01
Thank you very much for your help, Jeff.
I'll dig into that link.
Regards,
Kaido

---

### Post by Flavian on 2006-09-01
Hi I got a problem!
I did everything according to your howto.
Network manager was running and doing well, but I did not want the annyoing keyring thing to pop up again, so I went down and wanted to compile the newest network manager from CVS.
I did all the dependencies, everything went fine, until

```

sudo apt-get build-dep network-manager 

```
I got this error message:

Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for network-manager could not be satisfied.

Well, I did successfully compile wpa_supplicant...
I looked into synaptic and it said that wpa_supplicant was the unfulfilled dependencie. strange.

So I am stuck here.
Can you help please?
Flo

---

### Post by SilasleCake on 2006-09-01
I installed Ubuntu Dapper Drake today, and this is my first experience with Linux. The first thing I tried to do was to get my wireless internet connected onto here, and having trouble doing it on my own, came across your guide. I have started doing everything detailed in it, but now that I am at the part where I install the drivers, I am having trouble.

The ieee80211 Subsystem doesn't seem to want to install... When I type "make" in the terminal, after having done everything that comes before it, and worked without a problem, the following text comes up:

[COLOR="Blue"]alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ make
Checking in /lib/modules/2.6.15-23-386 for ieee80211 components...
find: /lib/modules/2.6.15-23-386/build/: No such file or directory
grep: /lib/modules/2.6.15-23-386/build//.config: No such file or directory
grep: /lib/modules/2.6.15-23-386/build//include/linux/autoconf.h: No such file or directory
find: /lib/modules/2.6.15-23-386/build/: No such file or directory
make -C /lib/modules/2.6.15-23-386/build M=/home/alejandro/wpa/ieee80211-1.1.14 modules
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2[/COLOR]

Being quite inexperienced in this domain, I'm not sure what this means, but the "Error 2" at the end lead me to believe that something went wrong. I went ahead and tried the "sudo make install" command and came up with a similar result.

[COLOR="Blue"]alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo make install
make -C /lib/modules/2.6.15-23-386/build M=/home/alejandro/wpa/ieee80211-1.1.14 modules
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2[/COLOR]

I wasn't sure what was wrong, and after fiddling a bit and trying again, nothing changed, so I tried to install the next driver, for IPW2100, but when I attempted that, it said that I couldn't do that until I installed ieee80211.

Do you have any idea what is wrong, and how I can fix it? I hope someone can help, because I am completely at a loss.

---

### Post by Jeff250 on 2006-09-01
edit: @SilasleCake:

It looks like your linux kernel headers might not be installed.  Try copying and pasting this into the console again:
```
sudo apt-get install linux-headers-`uname -r | awk 'BEGIN { FS="-" } ; { print $3 }'`
```
or if that doesn't work, try this, which I've now upgraded the guide to say, since it's simpler:
```
sudo apt-get install linux-headers-`uname -r | cut -d'-' -f3`
```
If you don't copy and paste, you might miss that some of those are back quotes instead of single quotes, namely the one before uname and after f3.

---

### Post by Jeff250 on 2006-09-01
> **Flavian said:**
> Well, I did successfully compile wpa_supplicant...
I looked into synaptic and it said that wpa_supplicant was the unfulfilled dependencie. strange.

So I am stuck here.
Can you help please?
Flo

Successfully compiling and installing wpa_supplicant still won't make it show up in Synaptic.  It's not supposed to.

Try this:
```
apt-cache showsrc network-manager
```
And try to manually download everything it says under "Build-Depends", and if you have all of that, you are done with that step.

---

### Post by Jeff250 on 2006-09-01
You know, now that Dapper is out, the build-deps won't be changing anyways, so I might as well enumerate that myself in the guide to just have everyone sudo apt-get install everything that it lists instead of having to do have everyone to sudo apt-get build-dep.  This should be done in a little bit.

---

### Post by SilasleCake on 2006-09-02
> **Jeff250 said:**
> edit: @SilasleCake:

It looks like your linux kernel headers might not be installed.  Try copying and pasting this into the console again:
```
sudo apt-get install linux-headers-`uname -r | awk 'BEGIN { FS="-" } ; { print $3 }'`
```
or if that doesn't work, try this, which I've now upgraded the guide to say, since it's simpler:
```
sudo apt-get install linux-headers-`uname -r | cut -d'-' -f3`
```
If you don't copy and paste, you might miss that some of those are back quotes instead of single quotes, namely the one before uname and after f3.

Those headers were installed, here is what I got whenever I typed that:

```
linux-headers-386 is already the newest version.
```

Any other ideas?

---

### Post by Flavian on 2006-09-03
> **Jeff250 said:**
> 
Try this:
```
apt-cache showsrc network-manager
```
And try to manually download everything it says under "Build-Depends", and if you have all of that, you are done with that step.

That is far too weird... ](*,) I tried to download all dependencies, but at at certain point it just gives me the response: "unmet dependencies... is going to be downloaded but not installed" or something.
Than I try find the unmet thing and it gives me two other unmet dependencies, I try to find those ones and it says 2 more... on and on and on it goes...

Kinda frustrating actually :(
If that what you said in your last post would help anything, like meeting the dependencies, that would be REALLY really nice.
Cause by now nothing, not even the old version of network-manager works anymore.

Thanks
Flo

---

### Post by Jeff250 on 2006-09-03
> **SilasleCake said:**
> Those headers were installed, here is what I got whenever I typed that:

```
linux-headers-386 is already the newest version.
```

Any other ideas?

The build directory is supposed to just be a symlink, so let's try making it manually:
```
sudo ln -s /lib/modules/2.6.15-23-386 /usr/src/linux-headers-2.6.15-23-386
```

---

### Post by Jeff250 on 2006-09-03
> **Flavian said:**
> That is far too weird... ](*,) I tried to download all dependencies, but at at certain point it just gives me the response: "unmet dependencies... is going to be downloaded but not installed" or something.
Than I try find the unmet thing and it gives me two other unmet dependencies, I try to find those ones and it says 2 more... on and on and on it goes...

Kinda frustrating actually :(
If that what you said in your last post would help anything, like meeting the dependencies, that would be REALLY really nice.
Cause by now nothing, not even the old version of network-manager works anymore.

Thanks
Flo

It sounds like you've run into some dependency hell.  This usually happens when you upgrade a package from outside the Ubuntu dapper repositories, say from downloading a deb off the Internet, or something from Debian or Ubuntu Edgy.  If you track down the "unmet dependencies" packages long enough like you were doing, you should eventually get to the culprit, which I'm guessing will have an error about how it cannot be installed because it depends on X version of Y package but the version of Y package is too high.  You could run into some other dependency problem too, so keep your eye out, but that's just my guess.

Basically, all I was trying to say in that other post is that instead of apt-get build-dep, I would just write in the guide apt-get install [and here write in all of the packages under apt-cache showsrc].  So this isn't going to help your problem unfortunately.

---

### Post by Flavian on 2006-09-04
Thanks for your reply!
Well, I think I will just go back to the normal, old network-manager and wait until I can finally install the newer version an easier way or something...

Can you tell me though how to remove all the unused, recently added packages.
I fear it might take a lot of disk space if I just let them lie around without using them... you know what I mean?
Is there a way to list all the unused packages and a way to delete all of those??

Thanks!
Flo

---

### Post by SilasleCake on 2006-09-04
> **Jeff250 said:**
> The build directory is supposed to just be a symlink, so let's try making it manually:
```
sudo ln -s /lib/modules/2.6.15-23-386 /usr/src/linux-headers-2.6.15-23-386
```

Well, that worked, and now my headers are installed! Unfortunately, I came across another problem, which once again I am at a loss to solve.:-| 

Everything runs smoothly up until I type the command "sudo make install" (this is installing the ieee80211 driver). Here is the code I get:
```
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo make install
make -C /lib/modules/2.6.15-26-386/build M=/home/alejandro/wpa/ieee80211-1.1.14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
install -d /lib/modules/2.6.15-26-386/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.15-26-386/net/ieee80211/
install -d `echo /lib/modules/2.6.15-26-386/include | grep "/net\$" || echo /lib/modules/2.6.15-26-386/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.15-26-386/include | grep "/net\$" || echo /lib/modules/2.6.15-26-386/include/net`
mkdir -p /lib/modules/2.6.15-26-386/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.15-26-386/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.15-26-386
make: *** [install] Bus error

```

---

### Post by Flavian on 2006-09-05
Hi guys!
How do I get back to the last WORKING network-manager if I can't install the new network manager?
If I type, "nm-applet" the Terminal gives me back:

** (nm-applet:5626): WARNING **: <WARNING>       nma_dbus_init (): nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.11" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

I don't have the nm-applet icon in the taskbar, even though it is installed!
Please help, I need my wireless card back on working with WPA encr.
Thanks
Flo

---

### Post by Jeff250 on 2006-09-05
> **SilasleCake said:**
> Well, that worked, and now my headers are installed! Unfortunately, I came across another problem, which once again I am at a loss to solve.:-| 

:-k 

That's bizarre.  The only thing I can think of is did you start back at the "sudo sh remove-old" step after you symlinked the linux headers directory?  If not, you probably should,  since that removes all the old ieee80211 from the linux headers, which can cause make headaches.

---

### Post by Jeff250 on 2006-09-05
> **Flavian said:**
> 
Is there a way to list all the unused packages and a way to delete all of those??

Thanks!
Flo

Via Synaptic:
Install deborphan and then under the Settings menu, select Filters and create a filter with only "orphaned" checked.  Then close that dialogue and on the bottom left, select "Custom Filters" and then select your newly created filter.

Via bash:
```
sudo apt-get install deborphan
deborphan
```
...will list the same packages.

---

### Post by Jeff250 on 2006-09-05
> **Flavian said:**
> Hi guys!
How do I get back to the last WORKING network-manager if I can't install the new network manager?
If I type, "nm-applet" the Terminal gives me back:

** (nm-applet:5626): WARNING **: <WARNING>       nma_dbus_init (): nma_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.11" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

I don't have the nm-applet icon in the taskbar, even though it is installed!
Please help, I need my wireless card back on working with WPA encr.
Thanks
Flo

This is the default NetworkManager.conf for Ubuntu:
```
<!DOCTYPE busconfig PUBLIC
	"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
	"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
		<allow own="org.freedesktop.NetworkManager"/>

		<allow send_destination="org.freedesktop.NetworkManager"/>
		<allow send_interface="org.freedesktop.NetworkManager"/>
	</policy>
	<policy at_console="true">
		<allow send_destination="org.freedesktop.NetworkManager"/>
		<allow send_interface="org.freedesktop.NetworkManager"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManager"/>

		<deny send_destination="org.freedesktop.NetworkManager"/>
		<deny send_interface="org.freedesktop.NetworkManager"/>
	</policy>
</busconfig>

```

And this is the default nm-applet.conf:
```
<!DOCTYPE busconfig PUBLIC
	"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
	"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy user="root">
		<allow own="org.freedesktop.NetworkManagerInfo"/>

		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
		<allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy at_console="true">
		<allow own="org.freedesktop.NetworkManagerInfo"/>

		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
		<allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManagerInfo"/>

		<deny send_destination="org.freedesktop.NetworkManagerInfo"/>
		<deny send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
</busconfig>
```

These belong in /etc/dbus-1/system.d/.
If these don't work, you might want to try the modifications to these files included in the guide.

---

### Post by SilasleCake on 2006-09-06
> **Jeff250 said:**
> :-k 

That's bizarre.  The only thing I can think of is did you start back at the "sudo sh remove-old" step after you symlinked the linux headers directory?  If not, you probably should,  since that removes all the old ieee80211 from the linux headers, which can cause make headaches.


Well, I had already done that, but I tried again, and came across the same problem. ](*,) Here is all the code, in case you find something that will explain it in there. Thanks...

```
alejandro@ubuntu-laptop:~$ cd ~/wpa
alejandro@ubuntu-laptop:~/wpa$ cd ieee80211-1.1.14
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo sh remove-old
Password:
Checking in /lib/modules/2.6.15-26-386 for ieee80211 components...
/lib/modules/2.6.15-26-386/net/ieee80211/ieee80211.ko
/lib/modules/2.6.15-26-386/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.15-26-386/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.15-26-386/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.15-26-386/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.15-26-386/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.15-26-386/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.15-26-386/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.15-26-386/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.15-26-386/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.15-26-386/include/net/ieee80211.h
/lib/modules/2.6.15-26-386/include/net/ieee80211_crypt.h
/lib/modules/2.6.15-26-386/include/net/ieee80211_radiotap.h
Above files found.  Remove? [y],n y
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo rm -rf /lib/modules/$(uname -r)/kernel/net/ieee80211
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/net/ieee80211*
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/config/ieee80211*
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ make
Checking in /lib/modules/2.6.15-26-386 for ieee80211 components...
make -C /lib/modules/2.6.15-26-386/build M=/home/alejandro/wpa/ieee80211-1.1.14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
alejandro@ubuntu-laptop:~/wpa/ieee80211-1.1.14$ sudo make install
make -C /lib/modules/2.6.15-26-386/build M=/home/alejandro/wpa/ieee80211-1.1.14 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
install -d /lib/modules/2.6.15-26-386/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.15-26-386/net/ieee80211/
install -d `echo /lib/modules/2.6.15-26-386/include | grep "/net\$" || echo /lib/modules/2.6.15-26-386/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.15-26-386/include | grep "/net\$" || echo /lib/modules/2.6.15-26-386/include/net`
mkdir -p /lib/modules/2.6.15-26-386/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.15-26-386/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.15-26-386
make: *** [install] Bus error

```

---

### Post by veganmasochist on 2006-09-06
Before I tried following this howto, I had Network Manager working, but it only gave WEP encryption options.  Now, it still works, but it only added LEAP encryption options.  All i want is to connect to a WPA network... Is that so difficult? :(

My card is an Xterasys XN-2423G.

Hope someone can help me.

Thanks!

---

### Post by Darrena on 2006-09-07
> **veganmasochist said:**
> Before I tried following this howto, I had Network Manager working, but it only gave WEP encryption options.  Now, it still works, but it only added LEAP encryption options.  All i want is to connect to a WPA network... Is that so difficult? :(

My card is an Xterasys XN-2423G.

Hope someone can help me.

Thanks!

I /think/ that card uses a TI chipset and the TI chipset driver on Linux does not support WPA.  See:
[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

You might want to google and see if someone is working on an updated driver.

---

### Post by Flavian on 2006-09-09
Thanks Jeff!
It works again! Thank you very much :)

---

### Post by murder2 on 2006-09-09
Great howto so far. I got to the point where I'm supposed to download the latest wpasupplicant from cvs. 

but then....
```
root@jon2:/home/jon/wpa# cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
Logging in to :pserver:anonymous@hostap.epitest.fi:2401/cvs
CVS password:
Unknown host hostap.epitest.fi.
```

:(


Edit: of course I had no net.... ](*,)

---

### Post by DutchKid on 2006-09-18
Hello. Thanks for the tut. I did everything you said (except for the first part about the drivers... I don't know which driver I need. How can I tell?). Anyway, it's not working... When I click the networking icon it doesn't show any wifi networks. Please tell me what I should do next or which tests I should run...

EDIT: I just found out I need the linux_wlan_ng driver. However, I don't know what I should do with this information?

---

### Post by DutchKid on 2006-09-19
EDIT 2: I downloaded this driver through the synaptic package manager. It didn't help. Shouldn't I, somehow, tell Ubuntu to use this driver with my PCMCIA card? Please, anyone?

---

### Post by Jeff250 on 2006-09-19
I think it should just work.  Do you have linux-wlan-wg-firmware installed too?

What do you get when you type the following?
```
lsmod | grep prism
```

---

### Post by DutchKid on 2006-09-20
Hi, thanks for your reply. I have also downloaded the firmware through synaptic. When I type that sentence, nothing happens :-(
I can't see the wireless card through the network manager icon anymore, either. But when I go to the network panel it says 'Wireless Card eth0 - activated'. And the power LED on the card itself is on.

---

### Post by drew_t on 2006-10-05
Hoping someone can give me some advice to fix a problem with intermittent connectivity.]  (*,) 

I have two Ubuntu systems that both have the same Atheros chipset-based Airlink (Fry's) PCI wireless cards.  (I bought these particular cards because I read somewhere that they would "just work" - hah!)  One of the machines is a dual-boot system; on it, the wireless card works flawlessly under Windows XP, so I don't think there is a defect with the wireless card.  

On both machines, I have NetworkManager installed, and the restricted module that includes the Madwifi.  (I just have the stuff from Synaptic; haven't tried any of that "make install" business.)  My Airlink router is set up to run WPA-PSK security.  When I boot up either of the Ubuntu systems, the passphrase keyring thing pops up; I type in the WPA passphrase; the NetworkManager icon starts spinning; then connects to my network.  (I have not had any problem with the network being detected, and the machines seem to remember that my network is the one they are supposed to connect to, bewteen shut-downs.)  Usually, the connection drops immediately, and then is reconnected; this happens a few times.  After that, it will stay connected, at least for a short while, and I can surf the net, or download updates in Synaptic, but the connection speed slows down in 15-30 seconds, then stops entirely.  If I wait a while, it will sometimes briefly recover, and work briefly, but then come to a standstill again; other times, NetworkManager icon shows that it has actually disconnected from the network, and it then reconnects.  So, basically, it works like it's supposed to, but only for brief spurts.  Both machines behave this way.

I don't really know how to diagnose the problem.  My knowledge of Linux is shallow, and I'm not very comfortable working with command-line/terminal situations.  If I click on System --> Administration --> Network Tools and select "Unknown Interface (ath0)" in the Network Device box, I do see continuously mounting "reception errors" under the right-and column.  The "received packets" read-out is vastly smaller and slower to increment.  The "transmission errors" and "collisions" read-outs are both zero.  So, it appears that there is a problem on the reception side, but I have no idea what to do about this.

I've seen threads which suggest that the /etc/network/interfaces file should have only the "auto lo" and
"iface lo inet loopback" lines, with everything else commented out; I've tried that, but it hasn't seemed to affect the problem.

Any suggestions appreciated.  If you need more information that has to be retrieved from the systems, keep in mind that you're going to need to tell me exactly what to type in the terminal.

---

### Post by Jeff250 on 2006-10-06
My guess is that your madwifi drivers are buggy.  I'd suggest doing the section under the guide entitled:
"If you have an Atheros-based chipset (Madwifi drivers)"
if you'd think you'd be comfortable doing it.

---

### Post by drew_t on 2006-10-06
OK, Jeff, I tried that on one of the two machines.  When I got to the last step, I got a message stating something to the effect that it appeared that the madwifi drivers were already installed, and if what I was trying to do was instal them, I should type "r" to remove the old drivers first.  I did so; hopefully, this was the right choice.

Unfortunately, it seemed to cause a new problem: now, when I boot up, NetworkManager tries, but never succeeds, in connecting to my network.  When I click on System --> Administration --> Network Tools, I now have an additional interface, "Unknown Interface (wifi0)" in the Network Device box.  (Previously, I had three: Loopback Intface l0, Ethernet Interface (eth0), and Unknown Interface (ath0).)  When NetworkManager is attempting to connect to my network, activity is shown in the "Interface Statistics" column when the wifi0 interface is selected; _no_ activity is shown when the ath0 interface view is selected.  (Previously, everything was happening in the ath0 interface.)  The "IP Information" box is empty, and all parameters are shown as "not available," in the "Interface Information" column in the wifi0 view.

If, rather than looking at Network Tools, I click on System --> Administration --> Networking, I see the ath0 referred to under the "Wireless Connection" heading, and there is no reference to "wifi0"

So, how did "wifi0" creep into the picture, and is NetworkManager now mistakenly trying to use it rather than "ath0"?  Any idea what I should try next?  I tried reinstalling NetworkManager, but it's doing the same thing.

---

### Post by Jeff250 on 2006-10-07
I'm afraid I'm not familiar enough with Atheros cards to know if that is normal or not.  Hopefully someone else can help you out here.

If you ever want to revert to your old drivers, just reinstall the linux-restricted-modules-YOURKERNELVERSION in synaptic.

---

### Post by jonathanhowell on 2006-10-08
I'm stuck with a request for a CVS password. 

jonathan@Wizard:~/wpa$ cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
Logging in to :pserver:anonymous@hostap.epitest.fi:2401/cvs
CVS password:
cvs [login aborted]: connect to hostap.epitest.fi(194.100.116.233):2401 failed: Connection refused

What am I doing wrong?
- Jonathan

---

### Post by rebegin on 2006-10-11
hey,
i've got problem with my network maanger as well.
i've browsed the net/google for hours, but i couldn't get the solution.
i'm trying to connect to my router which has wpa-spk switched on, but the
```
sudo NetworkManager --no-daemon
```
sais this:
```
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD wlan0               ndiswrapper/var/run/wpa_supplicant '
NetworkManager: <information>   SUP: response was 'FAIL'
NetworkManager: <WARNING>        nm_utils_supplicant_request_with_check (): supplicant_interface_init: supplicant error for 'INTERFACE_ADD wlan0           ndiswrapper     /var/run/wpa_supplicant '.  Response: 'FAIL'
NetworkManager: <WARNING>        real_act_stage2_config (): Activation (wlan0/wireless): couldn't connect to the supplicant.
NetworkManager: <information>   Activation (wlan0) failure scheduled...
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   Activation (wlan0) failed for access point (BOMASHOME)
NetworkManager: <information>   Activation (wlan0) failed.
NetworkManager: <information>   Deactivating device wlan0.
NetworkManager: <information>   SWITCH: no current connection, found better connection 'eth0'.
NetworkManager: <information>   Will activate connection 'eth0'.

```
and than it connects to the router through cable (eth0)...
i'm using ndiswrapper 0.25 and prism win-drivers....i've checked, and i don't have any /var/run/wpa_supplicant file...but i think it should exist.
any suggestions?
sorry for my english...
thanks in advance.

---

### Post by nozdormu on 2006-10-11
> I'm stuck with a request for a CVS password.

jonathan@Wizard:~/wpa$ cvs -d server:anonymous@hostap.epitest.fi:/cvs login
Logging in to server:anonymous@hostap.epitest.fi:2401/cvs
CVS password:
cvs [login aborted]: connect to hostap.epitest.fi(194.100.116.233):2401 failed: Connection refused

What am I doing wrong?
- Jonathan

I got that too, so I just used a recent CVS snapshot and it worked fine.

---

### Post by xander848 on 2006-10-27
Nozdormu
How did you do that?

---

### Post by Jeff250 on 2006-10-29
You can go here:
[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/hostap/](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/hostap/)
and then click on the "download tarball" link at the bottom.  Then you'll probably want to save it to ~/wpa/ and extract it with tar -zxvf [filename].

---

### Post by nrayever on 2006-11-12
this look good, but my question is: if gnome network manager already detects my ipw2200 under dapper i still need to compile the wireless drivers?? or i may use it the actual installed drivers??

nrayever

---

### Post by n3Cre0 on 2006-11-12
I'm connecting now each time with wpa_supplicant but I thought "there must be a simpler way to do this."

Then I found this thread installed the gnome-network-manager but nothing changed (no new menu entries etc).

I reboot and I see an applet in my taskbar (NetworkManager Applet 0.6.3) but why I leftclick it, it says "No network devices have been found" :confused: 

I'm using an IPW2200B/G Pro so it should work I think...

What did I do wrong?

Regards
n3Cre0

---

### Post by Jeff250 on 2006-11-13
> **nrayever said:**
> this look good, but my question is: if gnome network manager already detects my ipw2200 under dapper i still need to compile the wireless drivers?? or i may use it the actual installed drivers??

nrayever

If it works, then I wouldn't bother. :)

---

### Post by Jeff250 on 2006-11-13
> **n3Cre0 said:**
> I'm connecting now each time with wpa_supplicant but I thought "there must be a simpler way to do this."

Then I found this thread installed the gnome-network-manager but nothing changed (no new menu entries etc).

I reboot and I see an applet in my taskbar (NetworkManager Applet 0.6.3) but why I leftclick it, it says "No network devices have been found" :confused: 

I'm using an IPW2200B/G Pro so it should work I think...

What did I do wrong?

Regards
n3Cre0

sudo gedit /etc/network/interfaces
and then try commenting out (by putting a # as the first character of the line) everything but the lo stuff, like "auto lo" and "iface lo inet loopback".  You should probably give it a reboot too, or at the very least restarting some obscure service.

---

### Post by misha680 on 2006-11-14
Btw, in case you guys are interested, I made some NetworkManager CVS debs (these are the version from 10/10/06, I like that one because it reconnects on suspend for me automatically) for edgy (these are real debs not checkinstalled). They can be found in this post:

[http://www.ubuntuforums.org/showpost.php?p=1669898&postcount=17](http://www.ubuntuforums.org/showpost.php?p=1669898&postcount=17)

Misha

---

### Post by n3Cre0 on 2006-11-14
> **Jeff250 said:**
> sudo gedit /etc/network/interfaces
and then try commenting out (by putting a # as the first character of the line) everything but the lo stuff, like "auto lo" and "iface lo inet loopback".  You should probably give it a reboot too, or at the very least restarting some obscure service.

Change

> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid <a network WEP secured>
wireless-key <key>

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhc

to

> #auto lo
#iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid <a network WEP secured>
wireless-key <key>

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhc
?

Iwconfig gives this: 
lo
eth0 = Ethernet card
eth1 = IPW2200
sit0

---

### Post by Jeff250 on 2006-11-16
You've got it backwards.  Comment out everything *except* the lo stuff, so:
```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wireless-essid <a network WEP secured>
#wireless-key <key>

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

---

### Post by n3Cre0 on 2006-11-17
Thank you. 

Works fabulous.

So I guess the "normal" wifi manager is now disabled because it thinks there are no interfaces?

---

### Post by Jeff250 on 2006-11-17
This may not be 100% correct, but I think that the best analogy is to say that the legacy tools still can see the interfaces (type in ifconfig or iwconfig for evidence) but now since they're commented out, they don't how to use or connect with them.  This makes them available for network-manager.  So, yes, this is the moral equivalent of the old wifi manager being disabled.

---

### Post by n3Cre0 on 2006-11-18
Thanks a lot Jeff250 for patiently helping me out with this :)

---

### Post by cyangecko on 2006-11-20
Jeff,

First off, very nice Howto.  So far I have everything setting up ok until I get to compiling the network manager.  I get this message:  

checking for HAL... configure: error: Package requirements (hal >= 0.5.0) were not met:

No package 'hal' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Now, I go into synaptic to look up hal, and there it is.  I tried looking all over these forums for an answer, but am at a loss of what to do.  I appreciate any help anyone could give me at this point.  

Thank you.

Update: I managed to get past this point by starting again at the beginning of the Network Manager instructions.  Completed the howto, but still don't have it working.  Going to mess around some more and see if I can get it working.  Will check back.  Thanks again!

---

### Post by scarolan on 2006-12-11
I found this thread while looking for a way to not have to enter a password every time I connect to my own wifi network.  As I see it, this is a huge shortcoming of Ubuntu, and is a basic feature that both Mac and Windows computers have had for years.

I use Ubuntu Edgy + XFCE on an Acer 3102WLmi laptop.  I followed the tutorial to a tee - it took over 1 hour to complete.  Jeff, I'm amazed you had the patience to put all that together.  

After all this trouble, I *still* was required to enter a password for the keyring, and it also broke my nm-applet so it no longer shows up in the system tray.

And to think all I wanted to do was not have to enter a password every time I got onto my wifi network.  Next time I upgrade, I'm getting a Macintosh!!!  Sorry folks, but this is just one more reason that the "average" user will never take Linux seriously.  If the end-user cannot accomplish these basic tasks, there's not much hope that Linux will get much market share on the desktop.

Now to try and repair my wifi connection so at least I can get online again . . .

---

### Post by murder2 on 2006-12-19
After upgrading to kernel 2.6.15-27 the other day, I had to re-install the drivers for my ipw2200 card. This has been no problem before, when upgrading kernel. This time however, it wouldn't be done so easy. After installing everything over, still I couldn't connect to my network. I then tried to re-install everything a couple of more times, no luck. Got so frustrated, I downgraded back to 2.6.15-26 kernel, but now I can't even get it to work here! Tried to remove and install everything several times...
Anybody help me?

here's a print of the debugging info:
```
$ sudo NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'.
NetworkManager: <info>  Deactivating device eth1.
NetworkManager: <info>  Updating allowed wireless network lists.
```

---

### Post by Jeff250 on 2006-12-21
That's interesting.  It doesn't look as if anything of interest was changed in the -27 kernel, even though the -26 is acting up for you now too.  I take it that you've already tried using the straight-up dapper kernel without updating the ipw2200 drivers?  (You can just reinstall the kernel image to overwrite the updated drivers.)  When you say that you downgraded back to -26, does this mean that you are booting back into your old install of it or did you uninstall it and have to reinstall it?  If you didn't uninstall and reinstall -26 before trying it, this would suggest that the problem lies outside of your kernel config.

---

### Post by murder2 on 2006-12-28
I did not reinstall 26, only booted 26 kernel and removed 27. But I reinstalled everything related to NetworkManager as described in post 1 of this topic. But now I tried reinstalling 27 and reinstalling NetworkManager again, still no luck... Same output as above..... :-k
And for the record, I know there's nothing wrong with the wireless network. If I try to manually connect by entering essid, I get this output:
```
NetworkManager: <debug> [1167324842.875240] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'jonnet'
NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / jonnet
NetworkManager: <info>  Deactivating device eth1.
NetworkManager: <info>  Device eth1 activation scheduled...
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  Activation (eth1) started...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  Activation (eth1/wireless): access point 'jonnet' is encrypted, and a key exists.  No new key needed.
NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1               wext     /usr/local/var/run/wpa_supplicant       '
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'AP_SCAN 2'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
NetworkManager: <info>  SUP: response was '0'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6a6f6e6e6574'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth1/wireless): association took too long (>20s), failing activation.
NetworkManager: <info>  Activation (eth1) failure scheduled...
NetworkManager: <info>  Activation (eth1) failed for access point (jonnet)
NetworkManager: <info>  Activation (eth1) failed.
NetworkManager: <info>  Deactivating device eth1.
sendmsg(CTRL_IFACE monitor): No such file or directory
NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
```

I really need to get wifi working again before school and work starts over newyears, any tips and help very much appreciated.

---

### Post by klip on 2006-12-31
Answer for hal package not found problem:

Use synaptic package manager or apt if u prefer and search for something like libhal-dev (development files to use with hal). Install it and: CCCHHA DA IT WORKS!!!

---

### Post by murder2 on 2007-01-03
OK, so I installed windows on a partition, just too see if I could get the wifi-card to work there. It did. So there's no faulty hardware, which I was starting to suspect...
Now I've reinstalled Ubuntu all over again, and are running 6.10 on 2.6.17-10-generic kernel. Still I cannot get NetworkManager to connect to wireless... ](*,) 

```
$ sudo NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw2200'.
NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'.
NetworkManager: <info>  Deactivating device eth1.
NetworkManager: <info>  Updating allowed wireless network lists.
NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
```


And when trying to force connection:
```
NetworkManager: <debug> [1167857016.413959] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'jonnet'
NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / jonnet
NetworkManager: <info>  Deactivating device eth1.
NetworkManager: <info>  Device eth1 activation scheduled...
NetworkManager: <info>  Activation (eth1) started...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  Activation (eth1/wireless): access point 'jonnet' is encrypted, and a key exists.  No new key needed.
(NetworkManager:5027): GLib-GObject-WARNING **: invalid (NULL) pointer instance
(NetworkManager:5027): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
NetworkManager: nm_supplicant_interface_set_config: assertion `self != NULL' failed
NetworkManager: <WARN>  real_act_stage2_config(): Activation (eth1/wireless): couldn't send wireless configuration to the supplicant.
NetworkManager: <info>  Activation (eth1) failure scheduled...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth1) failed for access point (jonnet)
NetworkManager: <info>  Activation (eth1) failed.
NetworkManager: <info>  Deactivating device eth1.
```

Please, somebody, tell how to fix this... :(

---

### Post by Hushpuppy on 2007-01-09
Can anyone tell me what is wrong with the wpa_supplicant in this instance?  I'll show the end of the log information.  It seems to be failing silently, and I can't get my network card to work.  It worked once.  ](*,)   Then I booted into windows. :-k   Now I'm back in Ubuntu and on the wired, but the 3945 is not working though it should work fine... it did once, after all...

Thanks.

I'm running Kubuntu Edgy on a Thinkpad T60.  Versions:
uname -a : Linux rodin 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
wpa_supplicant: 0.5.4
network-manager: 0.6.3-2ubuntu6

Network card is an Intel 3945abg.  I'm using WPA-PSK, TKIP algorithm.
Jan  9 10:55:40 rodin NetworkManager: <information>^Iwpa_supplicant(5430): EAPOL: External notification - EAP fail=0
Jan  9 10:55:40 rodin NetworkManager: <information>^Iwpa_supplicant(5430): EAPOL: External notification - portControl=Auto
Jan  9 10:55:40 rodin NetworkManager: <information>^Iwpa_supplicant(5430): Wireless event: cmd=0x8b06 len=8
Jan  9 10:55:40 rodin NetworkManager: <information>^Iwpa_supplicant(5430): Wireless event: cmd=0x8b1a len=20
Jan  9 10:55:40 rodin NetworkManager: <information>^Iwpa_supplicant(5430): CTRL_IFACE monitor attached - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 31 37 38 2d 35 00
Jan  9 10:55:40 rodin NetworkManager: <information>^Iwpa_supplicant(5430): Authentication with 00:00:00:00:00:00 timed out.
Jan  9 10:56:40 rodin NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>120s), failing activation.

---

### Post by kleeman on 2007-01-09
I had a similar weird experience with network manager recently using a regular wpa router. It turned out to have a very strange fix:
Turned out I was specifying the ip address for the router to hand out via dhcp. When I made that dynamic everything was cool again. I got similar errors to what you show but of course this doesn't guarantee your problem is the same.......

---

### Post by Hushpuppy on 2007-01-10
> **kleeman said:**
> ...It turned out to have a very strange fix:
Turned out I was specifying the ip address .......

Thanks for the reply.  I appreciate it, even though I found my fix \\:D/ which was different than yours.

My AP had the SSID disabled.  ](*,)  I enabled it, and now it works. :-k  I guess the wpa_supplicant guys need to fix a bug, and I'll bring it to their attention.  Although I won't be surprised to hear that disabling the SSID is just security by obscurity (meaning: not secure at all).  But I don't know why I need to let the world know who I am; ***I*** know my SSID, why does the world need to know?  :confused:

Anyway, at least my Wireless card is now working with Ubuntu!  :-D

---

### Post by philipa on 2007-01-30
*Wireless works without NetworkManager, but not with it*

Clean Edgy install, Dell D620, Intel 3945ABG.

Wireless works fine for me with eth1 in /etc/network/interfaces; but then Network Manager only detects my wired interface.

I'd like to use NM (for easy roaming; and hopefully it will be part of the solution to connect to my corporate VPN). Consequently, I remove eth1 from /etc/network/interfaces. NM then kicks in, but fails with:

Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Selecting BSS from priority group 0 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): 0: 00:09:5b:72:2e:98 ssid='XXXX' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618):    skip - no WPA/RSN IE 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Trying to associate with 00:09:5b:72:2e:98 (SSID='XXXX' freq=0 MHz) 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 39 35 36 33 2d 31 00
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Cancelling scan request 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): WPA: clearing own WPA/RSN IE 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Automatic auth_alg selection: 0x1 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): WPA: clearing AP WPA IE 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): WPA: clearing AP RSN IE 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): WPA: clearing own WPA/RSN IE 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): No keys have been configured - skip key clearing 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): wpa_driver_wext_set_drop_unencrypted 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): State: SCANNING -> ASSOCIATING 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): WEXT: Operstate: linkmode=-1, operstate=5 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): wpa_driver_wext_associate 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Setting authentication timeout: 10 sec 0 usec 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): EAPOL: External notification - portControl=ForceAuthorized 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Wireless event: cmd=0x8b06 len=8 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): Wireless event: cmd=0x8b1a len=13 
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): **Authentication with 00:00:00:00:00:00 timed out. **
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 39 35 36 33 2d 31 00
Jan 29 23:12:27 NetworkManager: wpa_supplicant(9618): BSSID 00:09:5b:72:2e:98 blacklist count incremented to 2 
Jan 29 23:12:32 NetworkManager: [1170112352.340511] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'XXXX' 
Jan 29 23:12:32 NetworkManager: User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / XXXX 
Jan 29 23:12:32 NetworkManager: Deactivating device eth1


The access point is open - there's no password or WPA configured. Do I need to mess with wpa_supplicant.conf?

Thanks,

- Phil

---

### Post by Jeff250 on 2007-01-30
Network manager doesn't use wpa_supplicant.conf, so don't worry about that.

There is some weirdness with the 3945 about needing the linux-restricted-modules-generic package, which is needed for some binary daemon.  Make sure that that is installed.

---

### Post by Jeff250 on 2007-02-01
Another thing that has worked for some people with 3945's is just installing all of the edgy updates.  (I realize that this can be a catch-22 if you already don't have Internet.)

---

### Post by philipa on 2007-02-03
Thanks Jeff.

I have linux-restricted modules-generic.

I can also have wireless network access (not via NetworkManager) by adding the details to /etc/network/interfaces; and wired access (via NetworkManager); so Internet access is no problem. With regard to the edgy updates - any particular packages in mind?

---

### Post by philipa on 2007-02-04
SUCCESS!

I updated the ipw3945 microcode as per one of the comments at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452) and things now work.

I believe these are the necessary steps to get ipw3945 running with NetworkManager on edgy:
[LIST]
[*]Check linux-restricted-modules-generic package is installed.
[*]Edit /etc/network/interfaces to remove existing lines referring to eth1.
[*]Update the driver microcode:
```

$ wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz
$ tar xzvf ipw3945-ucode-1.14.2.tgz
$ sudo cp ipw3945-ucode-1.14.2/ipw3945.ucode /lib/firmware/2.6.17-10-generic/ipw3945.ucode
```
[*]Reload the module ```

$modprobe -r ipw3945
$modprobe ipw3945
```
[/LIST]

---

### Post by Beefeater on 2007-02-17
When I run "sudo NetworkManager/trunk/./autogen.sh" I recieve this errormessage. There is no higher version than 0.60 for Dapper so how do I go around it?


checking for DBUS... configure: error: Package requirements (dbus-glib-1 >= 0.72) were not met:

Requested 'dbus-glib-1 >= 0.72' but version of dbus-glib is 0.60

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by steeef on 2007-03-23
I thought I'd add my experience:

I've got a Dell Inspiron 6000 with an Intel Pro Wireless 2200BG. Open wireless networks were fine, but I couldn't get it to connect to my own wireless network, using WPA2 with a hidden SSID.

I tried installing Intel's drivers, I tried a few guides that supposedly get NetworkManager to work with WPA. The only method I got to work was the one at the beginning of this thread, but even then it would disconnect within a minute.

I decided to try reducing the security of my router. After changing the configuration to broadcast my SSID, it finally worked, even with WPA2 and CCMP/AES. NetworkManager finally connects without a problem, too.

I'm not sure if it's the version of the drivers/firmware I'm using for my wireless card, but the script mentioned to restart networking at boot wasn't required. In fact, when I had it enabled, ipw2200/0 would use 100% of my CPU.

Jeff250, thanks for starting this thread. I ended up clearing out /etc/networking/interfaces and letting NetworkManager handle everything instead of following your instructions to the letter, but this thread helped me troubleshoot what was wrong.

---

### Post by neptho on 2007-06-05
With Feisty, at least, NetworkManager is too flaky if you ever put the system to sleep; it constantly reloads the ipw3945 driver before wpa_supplicant has had a chance to associate... and the prior version of ipw3945 is unloaded (due in part to the user-level daemon which is required.. thank you Intel..)

So, here's my lazy-but-functional workaround:

**/etc/network/interfaces**:
```
auto eth1
iface eth1 inet dhcp
pre-up     /etc/init.d/wifi_wpa.sh start
pre-down     /etc/init.d/wifi_wpa.sh stop
```

**/etc/init.d/wifi_wpa.sh**:
```
#!/bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
BIN=/sbin/wpa_supplicant
PIDFILE=/var/run/wpa_supplicant.pid

  . /lib/lsb/init-functions

case "$1" in
  start)
if [ -x /sbin/wpa_supplicant ]; then
  $BIN -ieth1 -c /etc/wpa_supplicant.conf -Dwext -w -P $PIDFILE 2>&1 &
fi
    ;;
  stop)
    killall wpa_supplicant
    ;;
  *)
    ;;
esac
exit 0

```

**/etc/wpa_supplicant.conf**:
```
network={
  ssid="MYSSID"
  scan_ssid=1
  psk="MYPSK"
}
```

**/etc/acpi/suspend.d/95-iface-down.sh**:
```
#!/bin/sh
PATH=/bin:/sbin:/usr/bin:/usr/sbin
/sbin/ifdown eth1
```

**/etc/acpi/resume.d/95-iface-up.sh**:
```
#!/bin/sh
PATH=/bin:/sbin:/usr/bin:/usr/sbin
#Just to be sure
/sbin/ifdown eth1
sleep 2
/sbin/ifup eth1
```

Yes, it takes an extra 4 seconds to startup, but *it works without fail*.  Anyone who's been dealing with this mess at all, I strongly suggest 'apt-get --purge remove network-manager\*' and be done with it.  ;)

Make sure you chmod 755 every ".sh" shell script, and set your wpa_supplicant.conf 600, all files owned by root - if you want to keep your WPA key safe (but then again, anybody on your machine probably has that, anyhow)

---

### Post by Ripfox on 2007-06-05
Gee...I just downloaded wicd, selected wpa1/2, and typed in my password and instantly connected. Huh.

---

### Post by compwiz18 on 2007-06-06
> **ripfox said:**
> Gee...I just downloaded wicd, selected wpa1/2, and typed in my password and instantly connected. Huh.
;)

---

### Post by matt1606 on 2007-09-06
Proper built ubuntu feisty nm-0.6.5 deb packages ready to download form:
[http://helios.et.put.poznan.pl/~mjasin/nm-0.6.5-feisty/](http://helios.et.put.poznan.pl/~mjasin/nm-0.6.5-feisty/)

Best wishes,
matt1606

---

