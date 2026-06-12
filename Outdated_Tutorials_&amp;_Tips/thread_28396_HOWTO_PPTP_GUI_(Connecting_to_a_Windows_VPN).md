---
title: "HOWTO: PPTP GUI (Connecting to a Windows VPN)"
date: 2005-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by ernestoongaro on 2005-04-20
[FONT=Tahoma]
This is my first attempt at a how-to, please let me know your results. :) 
My school, SHSU, uses a Windows based VPN to allow unrestricted access to the wireless network. I, like many others like a nice GUI to assist in such configurations. The client is a proggie written by [Quozl](http://quozl.netrek.org/),  called pptpconfig.

Here is how to go about getting it:

Open up a terminal and type:
```

sudo gedit /etc/apt/sources.list

```

Add the line 
```

deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

```
to the bottom of the list, save, close and go back to the terminal and type:

```

sudo apt-get update
sudo apt-get install pptpconfig
killall gnome-panel

``` 

 It creates some Gnome menus, but it is unorganized and not run as sudo. Edit your menus by following this simple tutorial - [Gnome Menu Editor](http://ubuntuguide.org/#menu-editor) 
Delete the entry it created and make a new one under Applications>Internet or wherever and using the command **gksudo pptpconfig**
Good Luck!
[/FONT]

---

### Post by tritium3 on 2006-03-03
The following explains both pptp-linux and pptpconfig, for Breezy (Ubuntu 5.10):
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml")

---

### Post by jim.guenzel on 2006-08-30
I followed the directions by ernestoongaro and it worked correctly the first time! Thank you!

---

### Post by fratiijderi on 2006-09-05
I have tried and it'w works perfectly.

05.09.2006

---

### Post by Geoff2077 on 2006-09-05
What works perfectly first time - presumeably the connection to your windows server.

Can you explain how you access the server after connection please. In my case, I connect perfectly too, but I am unable as yet to open the folders on the server.

I am interested to learn how you access the server after connection - maybe this will throw some light on my 4 week old problem,

Cheers
Geoff

---

### Post by Johnathon on 2006-09-21
Try clicking on Places, "Connect to server", Choose windows share, and enter the details. HTH..

---

### Post by Geoff2077 on 2006-09-21
Thanks for the follow up. yes I eventually worked it out.
To mount the folder on the remote server:
Places/Connect to Server
Service type: windows share
Server (url): 192.168.16.2   (no slashes etc - just the number address)
Folder: Company  (or whatever the shared folder is on the server)
Username: fnerk
DomainName: XXXX (not needed I think)
Name for Connection: XXXVPN (not important)
then click on Connect.

---

### Post by mgmiller on 2006-10-01
This was exactly what I was looking for!

One last tweak.  After you have opened your remote and are displaying it in nautilus, add it to the nautilus bookmarks.  This way, after you open the VPN with pptpconfig, all you have to do is go to Places and click on your bookmark.  You can edit the bookmark name to call it whatever you want after you save it by clicking in nautilus bookmarks, edit bookmarks.  Notice all this is in nautilus, not firefox.  Thanks again.  This was an annoyance for me for my work computer that is finally resolved.

---

### Post by etank on 2006-11-08
Has anyone got this working correctly on Edgy? I know that I had it working in Dapper but I have been trying for an hour or so on Edgy and it seems to be a no go.

---

### Post by johnnymac on 2006-11-08
The PPTPCONFIG utility will not work correctly on Edgy.

So, what you have to do is:

1.  Use the pptpconfig to create your initial pptp configuration and make sure you choose client-to-lan.
2.  Create an executable script in /etc/pptp/ip-up.d/ which contains the routing information you need.
3.  Use the commands sudo pon <vpn-name> and sudo poff <vpn-name> to get it working.

Here's an example of the script you'd want...
```

#!/bin/sh
if [ "${PPP_IPPARAM}" = "tunnelname" ]; then
   route add -net  192.168.100.0 netmask 255.255.255.0 dev ppp0
   # ...etc...
fi

```

It's irritating I know....

---

### Post by etank on 2006-11-09
I keep getting a message that says: 

```
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/3
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
```

Then a two popups are shown saying:
```

Unable to remove file /var/run/pprpconfig.tunnel.undo
```

and 

```
/var/run/pptpconfig.tunnel.undo not present,
though it was expected to have been written by this program earlier.
```

but then the display says that it is restoring old settings.

---

### Post by johnnymac on 2006-11-09
Yeah - don't use pptpconfig to run the connection.  Once you have your connection setup and you have Client-to-LAN selected for the routing then you'll need to make sure you have a script setting up your routes (as in my previous reply).  Once you've accomplished this, open a terminal and execute sudo pon <tunnelname>

This is a workaround for pptpconfig not working in edgy.

---

### Post by likebike on 2006-11-22
It's worth mentioning in step 2 the script should be the same as the tunnel name.  Anyone have an idea when pptpconfig will be fixed for Edgy?

---

### Post by BrendanM on 2006-11-26
Is there a good way to test whether this has worked or not? When I try "route" in the terminal, or "tracepath <target ip>" it doesn't appear that it's going over the tunnel.

---

### Post by marusfarkus on 2006-12-21
I am having some troubles with this.  I am using 6.06 lts.  I have configured this every way possible and it is still not working for me. I have a shortcut created and it does not open.  gksudo pptpconfig is not working either.  It acts as if it is going to load and then nothing happens.  Can any one help?

---

### Post by wifi on 2006-12-28
> **johnnymac said:**
> 
2.  Create an executable script in /etc/pptp/ip-up.d/ which contains the routing information you need.

Do you use the package pptp or pptp-linux?
I don't have that set of directories. Create them manually or have to install any package?

> **johnnymac said:**
> 
3.  Use the commands sudo pon <vpn-name> and sudo poff <vpn-name> to get it working.

Here's an example of the script you'd want...
```

#!/bin/sh
if [ "${PPP_IPPARAM}" = "tunnelname" ]; then
   route add -net  192.168.100.0 netmask 255.255.255.0 dev ppp0
   # ...etc...
fi

```

Can you be more specific and give a complete script?

When I invoke pon <vpnname>  it only prints the selected options in config file.

Thanks.

---

### Post by etank on 2006-12-28
I would like to see a complete example as well.

---

### Post by LanceM on 2006-12-29
The script does not seem to be running. I can add the routes manually and everything works. So I came up with this: 

```
#!/bin/sh
#connect to work
sudo pon FCTG
#wait for connection
sleep 10
#add routes
route add -net  10.1.1.0 netmask 255.255.255.0 dev ppp0
route add -net  10.1.128.0 netmask 255.255.255.0 dev ppp0
```

Maybe not the best way, but it appears to work.

---

### Post by wilko on 2006-12-29
I used pptpconfig with no problems on all versions of Ubuntu prior to Edgy but encountered the same issues with using it in Edgy.  I found this and it proved to be a much more elegant solution:

[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)

---

### Post by LanceM on 2006-12-29
> **wilko said:**
> I used pptpconfig with no problems on all versions of Ubuntu prior to Edgy but encountered the same issues with using it in Edgy.  I found this and it proved to be a much more elegant solution:

[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)

Excellent! I will try that when I get home.

---

### Post by etank on 2006-12-29
I will as well. I'll post my results.

---

### Post by etank on 2006-12-29
Absolutely awesome. I am using Edgy with a belkin wireless card. I installed network-manager-gnome and the pptp applet for it and it works great. I did have to edit the /etc/network/interfaces to comment out the essid and key entries so that network-manager would take care of it. Thank you so much for sharing this find.

---

### Post by Rocket1957 on 2006-12-30
Hi I am brand new to Ubuntu and am very impressed so far. I followed Ernst's excellent instructrions but I got the returned reply "Package Not found" . I am running Dapper on an IBM Laptop. Any Ideas why I should get this response . I followed the link and all the packages seem to be there
any help to this newbie  apprecciated
Steve

---

### Post by maxamillion on 2006-12-30
pastebin your file /etc/apt/sources.list and then post the link, we will work from there

---

### Post by jklappenbach on 2007-01-02
[INDENT]> Originally Posted by wilko
I used pptpconfig with no problems on all versions of Ubuntu prior to Edgy but encountered the same issues with using it in Edgy. I found this and it proved to be a much more elegant solution:

[http://www.dailytechnology.net/how_t...y_edgy_eft.php](http://www.dailytechnology.net/how_t...y_edgy_eft.php)[/INDENT]

I followed these instructions, rebooted, and found that a left click on my network manager icon did not feature a VPN menu option.  It does display entries for all detected wireless nodes, as well as radio button for a wired network and options to Connect to or Create another wireless network.

I just upgraded to Edgy two days ago, and am on an Inspiron 6000 laptop.  My wireless is working fine, and have found everything else to be running smoothly.  Any suggestions on how to diagnose?

I have modified my sources.list as follows:

[INDENT][SIZE="1"]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
[/SIZE][/INDENT]

------------------------

Update:

I checked dmesg for any reports of ill, and found that the OS complained about ipw2200.  I should have saved the message, but it was something about dbus.  So, I downloaded the latest 802.11 and ipw2200 drivers, used the remove-old scripts for both, and executed make; sudo make install on both.  Now, dmesg reports no issues, but still, no VPN option on network manager.  I did install the plugin and apt-get reports that the package is up to date.

One thing, and this I'll address on the network manager (Gnome) forums:

I fugured that the version of network manager and/or the VPN plugin might need an update to function correctly on my machine.  Turns out, the Ubuntu package, 0.6.4, is up to date, but I thought I might be able to build with debugging info, set breakpoints, or perhaps add additional logging to pinpoint the issue. I attempted to compile network manager, and all went well until the test code functions were executed.  The following was reported:

...
gcc -g -O2 -o .libs/libnm_glib_test libnm_glib_test.o -pthread  ../utils/.libs/libnmutils.a ../gnome/libnm_glib/.libs/libnm_glib.so -ldbus-glib-1 -ldbus-1 /usr/lib/libgthread-2.0.so -lpthread /usr/lib/libglib-2.0.so -lrt
../gnome/libnm_glib/.libs/libnm_glib.so: undefined reference to `dbus_connection_disconnect'
collect2: ld returned 1 exit status
make[3]: *** [libnm_glib_test] Error 1

The issue was not with libnm_glib_test.c, as I commented out the code.  Instead, it's with the referenced library in the make file.  I'll post back when I know more.

---

### Post by LanceM on 2007-01-03
I also followed the steps for network-manager. Everything seemed to work fine. The only problem is that I do not have the ability to start the vpn from the applet. Still trying to figure out why.

---

### Post by jklappenbach on 2007-01-08
A few more things worth noting.  I have not been able to get the vpn plug-in for networkmanager to work, and, of course, pptpconfig doesn't get me connected.  You can use pptpconfig to set up a tunnel descriptor. 

```
#!/bin/sh
#connect to work
sudo pon [name of your pptpconfigured tunnel]
#wait for connection
sleep 10
#add routes
route add -net  [remote network ip] netmask [netmask] dev ppp0
```

In my case, my company's internal network addresses are all virtual and based on 10.*.*.*.  Therefore, I set up my remote network ip as 10.0.0.0 and the netmask as 255.0.0.0.

Next, I checked /etc/resolv.conf after executing the previous lines.  I found that there was no "search" entry.  Some may not need this, but I needed to alter /etc/resolv.conf to include the line:

search [remote domain name]

As part of the configuration actions of pon (IIRC) resolv.conf will be modified to include the ip addresses for dns to use for name resolution on the tunnel.  In my case, these lines alone weren't enough to enable proper DNS names for protocols.  I had to type everything in as IP addresses, not names.  Adding the "search" line in resolv.conf ended up doing the trick.

Finally, I created a short shell script to automate all this, taking a command line arg of "on" or "off" to start or stop the vpn tunnel.  This could be placed in init.d to enable automatic startup of the tunnel if needed.  If anyone would like a copy of the script, let me know.

---

### Post by praisebob on 2007-01-13
I used pptpconfig to setup the tunnel and then pon <tunnelname> as johnnymac noted, and it worked fine.
I had a bit of trouble getting the NetworkManager pptp plugin to run, but now its working as well.

I found useful information on debugging my connection on the plugin authors blog here:
[http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/software/networkmanager/pptp-plugin/#installing](http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/software/networkmanager/pptp-plugin/#installing)

Essentially, kill all NetworkManager related programs and run four terminals with one of these commands in each and they will return some useful information that can assist tracking down the problem:

sudo NetworkManager --no-daemon
nm-applet
sudo nm-ppp-starter   (this one has to be restarted every time you retry the vpn)
sudo tail -f /var/log/messages

In my case, I had to check off 'Refuse EAP' and 'Refuse CHAP' before it would connect.  I was also trying to pass the domain, but it was not needed.

---

### Post by lcohen999 on 2007-02-15
> **LanceM said:**
> The script does not seem to be running. I can add the routes manually and everything works. So I came up with this: 

```
#!/bin/sh
#connect to work
sudo pon FCTG
#wait for connection
sleep 10
#add routes
route add -net  10.1.1.0 netmask 255.255.255.0 dev ppp0
route add -net  10.1.128.0 netmask 255.255.255.0 dev ppp0
```

Maybe not the best way, but it appears to work.

how can I create a route add to encompass everything from my laptop.  ie, no matter what data I send, it goes through the tunnel?

---

### Post by BrendanM on 2007-02-15
I can't get this to work in a script, but if I set it to "all to tunnel" in PPTPConfig, and start it with the GUI, and then I go to the terminal and do " sudo ip route replace default dev 'ppp0'  " that seems to work for making the tunnel the default device and routing everything through the tunnel. If anyone has a better way, I'm interested too.

---

### Post by lcohen999 on 2007-02-15
I get a:

 sudo ip route replace default dev 'ppp0'
Cannot find device "ppp0"

---

### Post by BrendanM on 2007-02-15
I'm uploading the debug output from when I start the tunnel using PPTPConfig. You can compare it to yours/post yours. The key (as far as I can see) is when it tries to replace the default route and then gets the "RTNETLINK answers: No such device" error. That's why I have to go enter that command in the terminal; after that, it works for me. I don't know why it fails initially. Anyone? This seems like the kind of thing that's just begging for a bugfix.

---

### Post by kevinsun on 2007-02-16
I have exactly the same situation. Anyone can help?

---

### Post by zarej on 2007-02-23
> **lcohen999 said:**
> I get a:

 sudo ip route replace default dev 'ppp0'
Cannot find device "ppp0"

You should first start a connection with pptpconfig and then go to terminal and do:
```
$sudo ip route replace default dev 'ppp0'
```

Thats work for me. Thanx BrandonM. Did you find a better way or some script to automate process?

---

### Post by lcohen999 on 2007-02-23
lcohen@lorne-laptop:~$ sudo ip route replace default dev 'ppp0'
Password:
Cannot find device "ppp0"
lcohen@lorne-laptop:~$

after its connected (I know it is connected because the ping button is activated)

---

### Post by ThomasNovin on 2007-03-08
I have the same problem. Anyone found out what the problem is?

---

### Post by rts on 2007-03-10
Unfortunately, eth0 is a static IP address for me, so I can't use the NetworkManager solution.

When I try to connect to SecureIX VPN using some of the suggestions here, the pppd daemon sends out A TON of network traffic to the VPN server (like, 1.2 GiB in a minute), and then it dies:

$ sudo pon SecureIX
... a few moments later ...
$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.2.1.2  P-t-P:66.150.105.8  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1404  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:746859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:112 (112.0 b)  TX bytes:264326102 (252.0 MiB)
... a few more moments later ...
$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.2.1.2  P-t-P:66.150.105.8  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1404  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3941431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:112 (112.0 b)  TX bytes:1394117477 (1.2 GiB)

$ ifconfig ppp0
ppp0: error fetching interface information: Device not found



So... what is being transmitted, why is so much of it being transmitted, and why does the connection terminate?

---

### Post by ingo on 2007-03-20
ok, I had no joy with the above repository - this one worked instead

deb [http://quozl.linux.org.au/pptp/pptpconfig](http://quozl.linux.org.au/pptp/pptpconfig) ./

---

### Post by karlhm76 on 2007-03-26
> **jklappenbach said:**
> [INDENT][/INDENT]

I followed these instructions, rebooted, and found that a left click on my network manager icon did not feature a VPN menu option.  It does display entries for all detected wireless nodes, as well as radio button for a wired network and options to Connect to or Create another wireless network.

I just upgraded to Edgy two days ago, and am on an Inspiron 6000 laptop.  My wireless is working fine, and have found everything else to be running smoothly.  Any suggestions on how to diagnose?

I have modified my sources.list as follows:

[INDENT][SIZE="1"]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
[/SIZE][/INDENT]

------------------------

Update:

I checked dmesg for any reports of ill, and found that the OS complained about ipw2200.  I should have saved the message, but it was something about dbus.  So, I downloaded the latest 802.11 and ipw2200 drivers, used the remove-old scripts for both, and executed make; sudo make install on both.  Now, dmesg reports no issues, but still, no VPN option on network manager.  I did install the plugin and apt-get reports that the package is up to date.

One thing, and this I'll address on the network manager (Gnome) forums:

I fugured that the version of network manager and/or the VPN plugin might need an update to function correctly on my machine.  Turns out, the Ubuntu package, 0.6.4, is up to date, but I thought I might be able to build with debugging info, set breakpoints, or perhaps add additional logging to pinpoint the issue. I attempted to compile network manager, and all went well until the test code functions were executed.  The following was reported:

...
gcc -g -O2 -o .libs/libnm_glib_test libnm_glib_test.o -pthread  ../utils/.libs/libnmutils.a ../gnome/libnm_glib/.libs/libnm_glib.so -ldbus-glib-1 -ldbus-1 /usr/lib/libgthread-2.0.so -lpthread /usr/lib/libglib-2.0.so -lrt
../gnome/libnm_glib/.libs/libnm_glib.so: undefined reference to `dbus_connection_disconnect'
collect2: ld returned 1 exit status
make[3]: *** [libnm_glib_test] Error 1

The issue was not with libnm_glib_test.c, as I commented out the code.  Instead, it's with the referenced library in the make file.  I'll post back when I know more.

I am also getting this problem when I try and make the latest version. Did you find anything wrong with the makefile?

---

### Post by kevinsun on 2007-04-21
> **zarej said:**
> You should first start a connection with pptpconfig and then go to terminal and do:
```
$sudo ip route replace default dev 'ppp0'
```

Thats work for me. Thanx BrandonM. Did you find a better way or some script to automate process?

For me, it didn't work quite well.  I have to add one more route about the target vpn site, then it works.  However, the pptpconfig will keep on starting state rather than connected state.  Anyway, I think we probably still need to wait until edgy fully support pptp-linux client.  Otherwise, performing some custom route add may be necessary.

---

### Post by spiceisland on 2007-05-04
> **jklappenbach said:**
> A few more things worth noting.  I have not been able to get the vpn plug-in for networkmanager to work, and, of course, pptpconfig doesn't get me connected.  You can use pptpconfig to set up a tunnel descriptor. 

```
#!/bin/sh
#connect to work
sudo pon [name of your pptpconfigured tunnel]
#wait for connection
sleep 10
#add routes
route add -net  [remote network ip] netmask [netmask] dev ppp0
```

In my case, my company's internal network addresses are all virtual and based on 10.*.*.*.  Therefore, I set up my remote network ip as 10.0.0.0 and the netmask as 255.0.0.0.

Next, I checked /etc/resolv.conf after executing the previous lines.  I found that there was no "search" entry.  Some may not need this, but I needed to alter /etc/resolv.conf to include the line:

search [remote domain name]

As part of the configuration actions of pon (IIRC) resolv.conf will be modified to include the ip addresses for dns to use for name resolution on the tunnel.  In my case, these lines alone weren't enough to enable proper DNS names for protocols.  I had to type everything in as IP addresses, not names.  Adding the "search" line in resolv.conf ended up doing the trick.

Finally, I created a short shell script to automate all this, taking a command line arg of "on" or "off" to start or stop the vpn tunnel.  This could be placed in init.d to enable automatic startup of the tunnel if needed.  If anyone would like a copy of the script, let me know.

I had the same problem. Although my resolv.conf was auto-editted (by the pptp-client scripts) to include my company's DNS address, I was missing the crucial:

[INDENT]domain foobar.local[/INDENT]

line. I had a hunt around in /etc/ppp and came across the *ip-up.d/0dns-up* script. On a hunch, I created a file (mode 644) in /etc/ppp/resolv called the same name as my tunnel (e.g. /etc/ppp/resolv/foobar) with any extra lines I wanted in my /etc/resolv.conf after the tunnel was established. So, /etc/ppp/resolv/foobar contains simply:

[INDENT]domain foobar.local[/INDENT]

and, after the tunnel is established, my /etc/resolv.conf contains:

[INDENT]domain foobar.local

nameserver 192.168.0.3
[/INDENT]

Hope this helps!

---

### Post by computerjunkie on 2007-05-07
How do I configure pptp-config to use my wireless card instad of ppp0? (wireless is ath0)

this is the output from pptpconfig 
"Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/0
Modem hangup
Connection terminated.
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1"

firestarter is recording hits out of my computer using protocol "GRE", but not specifying a port  so I dont know which port to allow.

When using permissive mode (only blacklist traffic is blocked) then this is the output:

"Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/0
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1"

Firestarter records hits coming in using "GRE", but since its already in permissive mode, there is no way to allow these communications from the server.

How do I fix this?

---

### Post by computerjunkie on 2007-05-07
ok well yea in retrospect that was a stupid question. duh allow the host on the outgoing and incoming list.....lol

ooook it connects yay...ok now time for another stupid question:
how do I route my traffic through the vpn?? I started it and went to [http://whatsmyip.org](http://whatsmyip.org) and it came up with my internal IP, so either the vpn doesn't act as a proxy (which I would think it should) or firefox wasnt going throught the vpn

---

### Post by nullvoid on 2007-05-10
Will adding that script get rid of the "Failed to open /etc/pptpconfig/lock information entered has not been saved"?

---

### Post by lsilver on 2007-05-19
I'm trying to use PPTPconfig to set up a VPN on Fiesty.  I've followed the instructuions above to install the additional repository but when I run sudo apt-get install pptconfig I get the following error message:

pptpconfig:
   Depends: php-pcntl (>=4.3.7) but it is not installable
   Depends: php-gtk-pcntl (>=1.0.0) but it is not installable

I can't find these pacakges anywhere.  

Is there an update or replacement for pptpconfig that doesn't have these dependancies and will run on Fiesty?

---

### Post by cursebg on 2007-06-23
Hi! i have a problem with this how to. I needed to install the PPTP so i can connect to Internet and i had to download all the packages and dependencies manually. Then,finally, after i had done everything I tried to connect but an error occured. It shows me this
```
 Connection terminated by peer. MPPE required, but MS-chap[v2] not performed.
```

What should I do?
Thanks.

---

### Post by ilantz on 2007-06-24
> **spiceisland said:**
> I had the same problem. Although my resolv.conf was auto-editted (by the pptp-client scripts) to include my company's DNS address, I was missing the crucial:

[INDENT]domain foobar.local[/INDENT]

line. I had a hunt around in /etc/ppp and came across the *ip-up.d/0dns-up* script. On a hunch, I created a file (mode 644) in /etc/ppp/resolv called the same name as my tunnel (e.g. /etc/ppp/resolv/foobar) with any extra lines I wanted in my /etc/resolv.conf after the tunnel was established. So, /etc/ppp/resolv/foobar contains simply:

[INDENT]domain foobar.local[/INDENT]

and, after the tunnel is established, my /etc/resolv.conf contains:

[INDENT]domain foobar.local

nameserver 192.168.0.3
[/INDENT]

Hope this helps!

works charmly good & better together with jklappenbach testing, including the tips for the scripts inside /etc/ppp which made the thing quite easy.

Thanks!

---

### Post by skudvision on 2007-07-03
> **lsilver said:**
> I'm trying to use PPTPconfig to set up a VPN on Fiesty.  I've followed the instructuions above to install the additional repository but when I run sudo apt-get install pptconfig I get the following error message:

pptpconfig:
   Depends: php-pcntl (>=4.3.7) but it is not installable
   Depends: php-gtk-pcntl (>=1.0.0) but it is not installable

I can't find these pacakges anywhere.  

Is there an update or replacement for pptpconfig that doesn't have these dependancies and will run on Fiesty?

I assume you added:
# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
(or something similar) to your 
/etc/apt/sources.list

If so, then I assume that you are using an AMD64 version of ubuntu.

Both php-pcntl and php-gtk-pcntl from Mr. Cameron's site are for 386 architecture.  As such, those of us who want to use pptpconfig on an AMD64 are out of luck.  One could always find the source for the php-* programs and compile them to AMD64, thus creating a usable 64 bit version.

---

### Post by Riel on 2007-07-03
IN between these posts, I can see there are people who do not have the ' VPN'  options available in the GUI.

I have had this problem too. Changing the wireless-settings to **Roaming** fixed this. When I set my network manually, I do not have VPN options.

Is this a BUG, worth to be mentioned? Can anyone check, if it's the case at their Ubuntu's?






An other issue: when connected to VPN, all works. I can get at my work-drives, and check my mail by the exchange-server. But** most** internetpages don't work! Closing the VPN makes it allright! I don't know how to fix that...

---

### Post by nyvalbanat on 2007-07-06
> **skudvision said:**
> I assume you added:
# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
(or something similar) to your 
/etc/apt/sources.list

If so, then I assume that you are using an AMD64 version of ubuntu.

Both php-pcntl and php-gtk-pcntl from Mr. Cameron's site are for 386 architecture.  As such, those of us who want to use pptpconfig on an AMD64 are out of luck.  One could always find the source for the php-* programs and compile them to AMD64, thus creating a usable 64 bit version.

Get the AMD64 rpm packages from [http://sourceforge.net/project/showfiles.php?group_id=33063&package_id=121786](http://sourceforge.net/project/showfiles.php?group_id=33063&package_id=121786)

Convert to deb files using 
   sudo alien <...>.rpm
Then install:
  sudo dpkg -i <...>.deb

---

### Post by gymsmoke on 2007-07-08
First, thanks for all of the great info!
Here's where I am...
(All commands done as sudo...)

added the repo for pptpconfig
installed pptpconfig
setup the vpn with these parms - 
Tunnel name: MyVpnTunnel
   Route Style: Client to Lan
   Encryption:
      Require MPPE
      Refuse EAP

mkdir /etc/pptp
mkdir /etc/pptp/ip-up.d

vi MyVpnTunnel
#!/bin/sh
if [ "${PPP_IPPARAM}" = "tunnelname" ]; then
   route add -net  10.1.25.0 netmask 255.255.25
5.0 dev ppp0
fi
(save,close)

pon MyVpnTunnel

tail /var/llog/messages
Jul  8 09:31:57 MyBox pppd[12002]: Connect: ppp0 <--> /dev/pts/2
Jul  8 09:31:58 MyBox pppd[12002]: Warning - secret file /etc/ppp/chap-secrets has world and/or group access
Jul  8 09:31:58 MyBox pppd[12002]: CHAP authentication succeeded
Jul  8 09:31:59 MyBox kernel: [63626.516000] PPP MPPE Compression module registered
Jul  8 09:31:59 MyBox pppd[12002]: MPPE 128-bit stateless compression enabled
Jul  8 09:32:00 MyBox pppd[12002]: local  IP address 10.1.25.176
Jul  8 09:32:00 MyBox pppd[12002]: remote IP address 10.1.25.107
Jul  8 09:32:00 MyBox pppd[12002]: primary   DNS address 10.1.3.25
Jul  8 09:32:00 MyBox pppd[12002]: secondary DNS address 10.1.3.20
Jul  8 09:51:52 MyBox -- MARK --

I was connected for about 20 minutes, during which I couldn't ping any of the systems on the net, nor could I ssh into any of them...

I then stopped the tunnel with
poff MyVpnTunnel

tail /var/log/messages
Jul  8 09:32:00 MyBox pppd[12002]: primary   DNS address 10.1.3.25
Jul  8 09:32:00 MyBox pppd[12002]: secondary DNS address 10.1.3.20
Jul  8 09:51:52 MyBox -- MARK --
Jul  8 09:55:23 MyBox pppd[12002]: Terminating on signal 15
Jul  8 09:55:23 MyBox pppd[12002]: Connect time 23.4 minutes.
Jul  8 09:55:23 MyBox pppd[12002]: Sent 336 bytes, received 732 bytes.
Jul  8 09:55:23 MyBox pppd[12002]: Child process pptp MyVpnTunnel --nolaunchpppd  (pid 12003) terminated with signal 15
Jul  8 09:55:23 MyBox pppd[12002]: Modem hangup
Jul  8 09:55:23 MyBox pppd[12002]: Connection terminated.
Jul  8 09:55:23 MyBox pppd[12002]: Exit.


Can anyone offer some insight (or am I missing something?)

---

### Post by Phiu-x on 2007-07-18
PPTP Gui and I suspect pptp-linux (other problems)  is broken since Edgy and hasn't been working for Feisty. 

For your PPTP Gui problem : It does not add routes automatically. Try : 


[http://pptpclient.sourceforge.net/routing.phtml#client-to-lan](http://pptpclient.sourceforge.net/routing.phtml#client-to-lan)

---

### Post by kpalania on 2007-11-13
Hi,
I just purchased a new Dell machine with Ubuntu installed and am trying to get setup. Need to be able to connect to work via VPN and have been trying to get pptpconfig working but in vain.

I keep getting the "Cannot determine ethernet address for proxy arp" error. Could someone please help me out..

If I need to create an executable script, what kind of information do I need? All that I have at this point is the typical VPN info, like hostname and my account information. That is it. Thanks.

-- krish

---

### Post by noremac on 2008-04-09
I am trying to install this and when I do from the command line, I keep getting a message asking me to insert my Xubuntu CD. Wouldnt be a problem, however I am installing this on my Eee which doesnt't have one. I dont know how to set it up, or if even possible, to recognize the USB flash drive as the cdrom, which was my "CD" for installing eeeXubuntu on this Eee.

Any suggestions on how to get it to work?

And if the Original Poster still see's this thread, I am actually attending SHSU as well, and trying to get it to work on their VPN...

-Cameron

---

