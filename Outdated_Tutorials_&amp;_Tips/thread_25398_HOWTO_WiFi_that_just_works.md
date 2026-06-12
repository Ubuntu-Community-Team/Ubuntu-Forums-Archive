---
title: "HOWTO: WiFi that just works"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by bradg on 2005-04-10
Hey everyone.  NetworkManager doesn't seem to work well with the version of D-BUS in hoary.  And netapplet isn't exactly stable for me and requires too much user intervention.  So, I hacked up this little screen-scraping PHP script today that accomplishes what I need for my WiFi roaming needs (at least until NetworkManager matures and is integrated into Breezy).  I'm not too concerned about developing a more elegant solution, as this is working wonderfully for me.  I just thought I'd post it here in case it could be of help to anybody.  Cheers.

[http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2)

wicme - Wireless Internet Configuration Made Easy
By Brad Griffith.
Licensed under the GNU General Public License.
============================================================
This is a small PHP hack that allows for easy configuration
of a wireless card in Ubuntu Hoary.  It may work in other
distros/environments, but I haven't tested it.  I'm not
planning on improving this tool too much, but I hope it can
be of use to somebody while project like NetworkManager
mature.

When wicme is run, either from the commandline or from its
menu item in System >> Administration >> Wireless Networks
it will first look to see if any networks in range are in
your preferred networks list.  If so, it will automatically
connect to that network.  If not, it will present a list of
networks that you can connect to, allow you to enter a WEP
key if needed, connect to that new network, and add it to
your list of preferred networks.  If a connection is made
successfully an lightbulb icon will appear in the notifica-
tion area.  If the connection fails, an X will be displayed
there instead.

INSTRUCTIONS
============================================================
1) Change lines 4 and 5 of "wicme" to match your wireless
   device and home directory.
2) Run "sh install.sh" as root.
3) Setup sudo to require no password for the admin group:
    a. Run "sudo visudo"
    b. Change the line that begins with "%admin" to read:
        "%admin ALL=(ALL) NOPASSWD: ALL
4) Add wicme to your startup programs in GNOME by using the
   "Sessions" preference tool's "Startup Programs" tab.
   
TODO
============================================================
Currently an incorrect WEP key can only be determined by a
time out of dhclient.  This takes a long time.  It would be
nice to have a faster method of testing this.

---

### Post by slade_slater on 2005-04-10
This rocks, I can't wait to test it on my laptop!

---

### Post by bradg on 2005-04-11
Awesome.  Let me know how it works out for you.

---

### Post by Gandalf on 2005-04-11
nice script thx man!!

---

### Post by bradg on 2005-04-11
Glad it helped you out.  Thanks for commenting.

---

### Post by Gandalf on 2005-04-11
[QUOTE=bradg]Glad it helped you out.  Thanks for commenting.[/QUOTE]
 no problem :D

---

### Post by Gandalf on 2005-04-11
You have a bug (not a bug just a typo mistake) in the script,
open wicme file
search for
```

function scan()
{
    exec('sudo iwlist wlan0 scan', $output);

```

replace with
```

function scan()
{
    exec("sudo iwlist $device scan", $output);

``` note the changes, double quotes instead of single and $device instead of wlan0

---

### Post by bradg on 2005-04-11
Great!  Thanks for pointing it out.

New version is at [http://www.thecardinal1978.com/ubuntu/wireless-config-0.2.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.2.tar.bz2)

---

### Post by Gandalf on 2005-04-11
[QUOTE=bradg]Great!  Thanks for pointing it out.

New version is at [http://www.thecardinal1978.com/ubuntu/wireless-config-0.2.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.2.tar.bz2)[/QUOTE]
 no problem :D

---

### Post by bradg on 2005-04-11
OK, another new version:
[http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2)

This version will eliminate any repeats in the list.  Without this, on my campus for instance, choosing one "TigerNet" network will then cause the program to ask for all the WEP keys one after the other which is annoying.  This would also mean that if you selected the third network on a list and the first had the same name that you would be logged into the first.

---

### Post by Gandalf on 2005-04-11
great thx man

---

### Post by Ty1er Leeds on 2005-04-11
As an alternative to not requiring a pass for root access to the admin group, you could just make iwlist, iwconfig and dhclient3 runnable by non-root.

Issue the following commands at the root prompt:

chmod a+x /sbin/iwlist
chmod a+x /sbin/iwconfig
chmod a+x /sbin/dhclient3

This may be better or worse security depending on your system. (I didn't really want to not require a pass.. The pass stops me from being an idiot)

Cheers
Ty

---

### Post by bradg on 2005-04-11
Good point.  I've updated the README for the next release.  I kind of did this as a learning project for php scripting on the command line.  I'm playing around with do this correctly in python now.  I'll try to post a version of it in the next few days - will get rid of the zenity hacks and maybe deamonize the thing.

---

### Post by agentgray on 2005-04-11
I tried this out with my 3Com w/xjack...my network is broadcasted and uses 128WEP. 

Didn't work.

How do I remove the script and the apps it installs?

---

### Post by bradg on 2005-04-11
Does your card support scanning?  If not, that is why you are having trouble.  You can check this by running "sudo iwlist scan".  If you do support scanning, I can probably help you figure out what the problem is.  If you want to remove the script, run the following:

sudo rm /usr/bin/wireless
sudo rm /usr/share/applications/wifi.desktop
sudo apt-get remove php4-cli

Hope that helps.

---

### Post by agentgray on 2005-04-12
This is a relatively new card.  It supports a, b, and g.  It scans on windows XP ok, but this scanning might be different, I assume

I can get it to work on a "b" Netgear access point (with no security), but I cannot get it to work at home on a "g" Netgear router with 128-bit WEP. 

I'll give this a try and see if it works.  Otherwise, I'll remove the script.

---

### Post by Gandalf on 2005-04-12
[QUOTE=agentgray]This is a relatively new card.  It supports a, b, and g.  It scans on windows XP ok, but this scanning might be different, I assume

I can get it to work on a "b" Netgear access point (with no security), but I cannot get it to work at home on a "g" Netgear router with 128-bit WEP. 

I'll give this a try and see if it works.  Otherwise, I'll remove the script.[/QUOTE]
 guys there's also whereami scrit which is very usefull if you go always to the same places either on wired or wireless, this one also very usefull in wireless areas

---

### Post by bradg on 2005-04-12
The type of router shouldn't make any difference.  What driver does your nic use?  If you try the scanning command I used, do you get a list of APs in the the area?  If not, the driver you are using for your wifi card does not support scanning.  Also, you can test to see if you support scanning by trying out another tool like netapplet.  
Also, I've written this exact script in python now.  I will probably make it the default in the next release because it will drop the need to install php4-cli.  Soon, I'll replace the zenity stuff with pygtk.

---

### Post by joplass on 2005-04-12
Guys,
Do I have to have my wireless card working or this alone should make it work.
I am hoping for the best.  ;-)

---

### Post by Gandalf on 2005-04-12
[QUOTE=joplass]Guys,
Do I have to have my wireless card working or this alone should make it work.
I am hoping for the best.  ;-)[/QUOTE]
 no you must have the wireless card working, this is just an applet that scans for available wifi routers

---

### Post by usererror on 2005-04-14
this is a great little program, thanks for writting it!

i have a question that i think you can help me answer...

once wicme is used to connect to an access point, where does it store the information regarding the access point?  :confused:  for some reason i was able to connect at my home to my own ap but here at work i cannot get an IP from any, an we have the exact same network setups...i have turned off our WEP settings... and now i want to try connecting to a different AP, if possible but i no longer get asked!

---

### Post by bradg on 2005-04-15
Glad you like the script.  Information is stored in ~/.wifi-preferred.  It's just a simple text file, so it should be easy to read.  When I get some free time next week, I'm going to release of the pygtk port that will make the auto-config part a daemon and the selection part a bit more robust - this will fix the type of problem you describe and eliminate the php dependency.  Hope that helps.  Cheers.

---

### Post by usererror on 2005-04-15
many thanks for the info.  I will checkout the text file today at work. :D

---

### Post by ifrflyer on 2005-04-27
Brad,
First, thank you so much for creating this script, addressing a serious and annoying problem. I'm grateful. 

Second, having been hosed by NetworkManager myself, I'd like to ask, *before * I start installing this script, how I might uninstall it should it - in the worst case, unlikeliest scenario and you understand this is asked with all possible respect - bork my whole setup! 

Can you offer any procedures I might use to remove it should it not be my cup of tea? 

Thanks!

---

### Post by bradg on 2005-04-28
If you need to uninstall, run these three commands:
sudo rm /usr/bin/wireless
sudo rm /usr/share/applications/wifi.desktop
sudo apt-get remove php4-cli

There is really no way this can mess up your system, as it doesn't touch the system configuration at all.  Hope it can be of some help to you.  I'll be sprucing it up a bit after finals.

---

### Post by stevenyu on 2005-04-28
if anyone need help with setting up wifi with ndiswrapper, I can post my procedure on how to set it up  :razz:

---

### Post by zagor on 2005-04-28
Yes, please!

I've lost  a few hours in getting ndiswrapper to work and its still not-always working.
I'm planning to reinstall Hoary (I'm using the preview as for now) and suggestions on ndiswrapper will be welcome.

---

### Post by stevenyu on 2005-04-28
Ok here I go, here are the procedure I took for my TI based Netgear WG311v2 NIC with ndiswrapper

0 - **What you need?**

The latest windows driver for your wifi card (for my Netgear WG311v2, I didn't use the latest as the new one have a 3rd party software based wpa driver, so i used - [WG311v2 Beta Software Version 1.2](http://http://kbserver.netgear.com/support_details.asp?dnldID=848) )

The latest source of Ndiswrapper - [NDISWRAPPER](http://ndiswrapper.sourceforge.net/) 
You can use the source that came with Hoary, but I prefer getting the latest source myself.

1 - **Install Ubuntu Hoary**

2 - **Install the GNU C Compiler**

Once you got in to the X-Window, fire up the Synaptic and install the following programs:

**gcc**
**g++**
**Kernal Header** (use uname -a to find out which kernal you are running)
**ndiswrapper source** (or you can use the one you downloaded from sourceforge, I prefer this method, )

3 - **Remove the god damn ACX Driver**

go to */lib/modules/**kernelversion**/kernel/drivers/net/wireless*

and *mv acx /root/* follow by *depmod -a*

NOTE: ***kernelversion*** will be difference as kernel version are different for everyone, depend on your CPU type.

4 - **Unpack the source and driver man**

Just right click on the files and extract to where you want it to, for me I just do extract to my home folder.

5 - **Installing ndiswrapper**

goto the directory holding your ndiswrapper, and

*sudo make install*

then goto the directory holidng your WiFi NIC driver, and

*sudo ndiswrapper -i YOURWIFI.INF*

and check the installation by *sudo ndiswrapper -l* ,and you should see something similar to this:

> Installed ndis drivers:
wg311v2 driver present, hardware present

6 - **Auto load Ndiswrapper when reboot**

*sudo ndiwrapper -m*

7 - **Edit the network interface file**

the file is located in */etc/network* and here is my configuration for static IP.

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet static
	# wireless-* options are implemented by the wireless-tools package
	wireless_keymode open
	wireless_key REPLACE WITH YOUR WEP KEY
	wireless_mode managed
	wireless_essid REPLACE WITH YOUR ESSID
	wireless_nick REPLACE WITH YOUR HOST NAME
	address 192.168.1.3
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.254

auto wlan0


8 - **That all**  \\:D/

---

### Post by ifrflyer on 2005-04-30
I've installed the script and made the changes you recommended re admin sudo. THe script runs and does show me available networks. 

However I am in **hell** because the worthless little network connections dialogue which comes with ubuntu borks my connection every time and nothing I have tried to date has helped. It works mainly fine if I stay connected to the same network. If I have the gall to try to change wifi networks it locks up on me, tells me I am connected when I m not, and most often requires a restart of the whole bloody machine to get things right again, sometimes two restarts. 

I am willing, nay, delighted to admit user error yet I  have posted repeatedly and gotten no further than:

I have tried

/etc/init.d/networking restart

Nothing

I have tried 

ifdwn eth0 && ifup eth0

Nichts

Only occassionally does removing all the properties such as the WEP key and all other configuration details and clicking OK then reopening network connection and re-entering them manually -- SOMETIMES this allows me to reconnect to a network I was ALREADY on. 

Can you offer any suggestions? Please oh please? 

Thanks

---

### Post by usererror on 2005-05-01
I have been having similar problems...

only *rarely* have i been able to connect to linksys powered wifi routers with success.  most of the time, my entire system locks up and i am forced to power off.

wifi points i have been able to connect to are netgears and belkins without problems...so far...

i have ditched all methods of GUI wifi managers.

i have more sucess doing the following:

iwlist wlan0 scanning  

   * displays available wifi points *

iwconfig wlan0 ESSID "SSID name goes here"

/sbin/dhclient wlan0

perhaps that would work for you?

---

### Post by Eproxus on 2005-05-02
First: Great script! Thanks!

But: I've tried making iwlist, iwconfig acd dhclient3 runnable by non-root, but executing wicme in a prompt still asks far a password. When I try to run it in the Alt+F2 launchbox or the mini command line in gnome (both uses no further input than the launch command, so password input is ignored) it don't choose my preferred networks and instead displays an empty available networks list (which I know is wrong because there is a network).

Is the 'sudo visudo' thing making all sudo actions password free? I don't want that.

If it is, is there any way to make iwconfig run without password?

---

### Post by jtsai256 on 2005-05-03
This is definitely a great program. It has helped me out tremendously, being in an area where there are a ton of connections. 

I think I may have found a bug though. Whenever I try to click on the lightbulb icon that appears, wicme exits and I have to start it up again. Also, if there's no network in the region, the program seems to keep running in the background until there is a connection. The problem with this is that I didn't know the program was running in the background, and so I kept clicking on wicme to start. Once the connection was established, about 5 lightbulbs suddenly popped up in the system tray.

These small issues aside, however, this program is great! Thanks!

---

### Post by duk on 2005-05-04
[QUOTE=jtsai256]This is definitely a great program. It has helped me out tremendously, being in an area where there are a ton of connections. 

I think I may have found a bug though. Whenever I try to click on the lightbulb icon that appears, wicme exits and I have to start it up again. Also, if there's no network in the region, the program seems to keep running in the background until there is a connection. The problem with this is that I didn't know the program was running in the background, and so I kept clicking on wicme to start. Once the connection was established, about 5 lightbulbs suddenly popped up in the system tray.

These small issues aside, however, this program is great! Thanks![/QUOTE]
 Thanks for this excellent script, you just made wifi a whole lot easier.

---

### Post by smacknrat on 2005-05-07
Hi all.  
  It should be noted that I don't use Ubuntu, but this seems like a rather nice general discussion.  I've got a wg311v2 here and got it working with ndiwsrapper and the latest 2.0.0.7 drivers from netgear.  But the bitrate is just miserable.  The card and router are about 5 feet from each other and I have a hard time getting anything above 600 kB/s.

I've been able to get to 1 MB/s at random situations but so far the 5 MB/s is far from achievable.

I'm wondering what kinda bandwith you folks have with your wg311v2's with ndiswrapper.

I can get the card working with acx100 drivers, but the situation is hit and miss.

The router is set to 'g only' (Netgear WGR614v2.. Had a v4 but it frequently drops network connections for no reason.).

'iwlist wlan0 scan' shows:
```

wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:86:47:32
                    ESSID:"TheOutpost"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-31 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

notice that it lists 802.11b instead of 802.11g.  'iwconfig wlan0' shows:

```

wlan0     IEEE 802.11g  ESSID:"TheOutpost"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:86:47:32
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:2347 B   Fragment thr:2312 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-35 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

'iwlist wlan0 rate' shows:

```

wlan0     4 available bit-rates :
          1 Mb/s
          2 Mb/s
          5.5 Mb/s
          11 Mb/s
          Current Bit Rate=54 Mb/s

```

I'd really like to get some better bandwith here.  I'm getting a bit envious of people who can stream video at higher bitrates without a stutter. =)

(I've tried video streaming with ethernet, eth0, and the bitrate never went above 800 kB/s so it's certainly within reason)

---

### Post by shizow on 2005-06-24
the url for the link to the script doesnt work anymore\[http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2)

---

### Post by traherom on 2005-06-28
[QUOTE=shizow]the url for the link to the script doesnt work anymore\[http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2)[/QUOTE]
Yep, get one of those "search" ad places.

Sounds great though!

---

### Post by charlieg on 2005-07-15
How does this differ from [GtkWifi](http://gtkwifi.sourceforge.net) (other than php/python)?

Latest release here:
[http://www.ubuntuforums.org/showthread.php?t=49148](http://www.ubuntuforums.org/showthread.php?t=49148)

---

### Post by pirast on 2005-08-01
I wanted to try your script but:

> wget [http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2)
--15:48:14--  [http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2](http://www.thecardinal1978.com/ubuntu/wireless-config-0.3.tar.bz2)
           => `wireless-config-0.3.tar.bz2'
Resolving [www.thecardinal1978.com](www.thecardinal1978.com)... failed: Host not found.
 

I can't get it   :-? 

Could you please fix it?

Thanks,
Martin

---

### Post by vonkinder on 2005-08-02
Yes, Please fix your site. Your script sounds very good but we can't download it.
thanks in advance!

---

### Post by desertViking on 2005-08-18
Hey,

The original poster of this script seems to be unavailable at their ftp sesrver.  Does anyone have a copy that they'd be willing to post.

Activating wireless on my desktop system is the one thing keeping me from jumping to ubuntu.  I have it working on Mepis.

Regards,

desertViking

---

### Post by AsburyPark on 2005-08-25
Is there anyone willing to post a how to on manually connecting to a wireless network.  

My card is working, I can see my network, but I just cant connect.

 ](*,)

---

### Post by andlinux on 2005-08-26
[QUOTE=AsburyPark]Is there anyone willing to post a how to on manually connecting to a wireless network.  

My card is working, I can see my network, but I just cant connect.

 ](*,)[/QUOTE]
I've got the same problem, can somebody post this little program ?

---

### Post by usererror on 2005-08-26
To connect manually (this worked for me at least)  wlan0 is my wifi card

as root/sudo:

> **iwconfig** wlan0 ESSID *networkid*
> **iwconfig** wlan0 KEY *enter wep key if needed*
> **dhclient** wlan0

hopefully that will work for you.

---

### Post by andlinux on 2005-08-27
[QUOTE=usererror]To connect manually (this worked for me at least)  wlan0 is my wifi card

as root/sudo:

> **iwconfig** wlan0 ESSID *networkid*
> **iwconfig** wlan0 KEY *enter wep key if needed*
> **dhclient** wlan0

hopefully that will work for you.[/QUOTE]
It doesn't know the KEY.

---

### Post by Bobby Shaftoe on 2005-08-27
can anyone repost that script please? the original website is down atm so i got no chance to d/l it  :| 
brad, if you need space for hosting, i can give you plenty, just drup a PM or reply here.

---

### Post by emotional1 on 2005-09-03
I have tried to copy this file but keep getting  [http://thecardinal1978.com/main_index.html](http://thecardinal1978.com/main_index.html)
even when typing in the whole address I get this above website.  Any ideas on where or how I can find this .tar file?

Eric

---

### Post by usererror on 2005-09-04
[QUOTE=andlinux]It doesn't know the KEY.[/QUOTE]

KEY or ENC will work to input the wep encrpytion.  do 'man iwconfig' for full instructions.

however, i am now using the gtkwifi manager that is link to somewhere in this thread and the latest version of it works great with encryption! :)

---

### Post by emotional1 on 2005-09-04
I have tried to find this package for use on my laptop with a dell truemobile 1300 wireless card and this link you have provided leads me to: [http://thecardinal1978.com/main_index.html](http://thecardinal1978.com/main_index.html)
I have been unable to reach this link you have posted, I have tried copying, typing, cut and pasting, and all I get is this [http://thecardinal1978.com/main_index.html](http://thecardinal1978.com/main_index.html) with the message related websites.  Is there any way I might procure this package from you?  By e-mail?

Thanks Eric

---

### Post by usererror on 2005-09-04
[QUOTE=emotional1]I have tried to find this package for use on my laptop with a dell truemobile 1300 wireless card and this link you have provided leads me to: [http://thecardinal1978.com/main_index.html](http://thecardinal1978.com/main_index.html)
I have been unable to reach this link you have posted, I have tried copying, typing, cut and pasting, and all I get is this [http://thecardinal1978.com/main_index.html](http://thecardinal1978.com/main_index.html) with the message related websites.  Is there any way I might procure this package from you?  By e-mail?

Thanks Eric[/QUOTE]


Eric,

try going to this site: [http://gtkwifi.sourceforge.net/](http://gtkwifi.sourceforge.net/)

if you need me to email you the package send me a PM.

---

