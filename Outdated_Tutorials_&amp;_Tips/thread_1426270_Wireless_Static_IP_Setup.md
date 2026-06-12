---
title: "Wireless Static IP Setup"
date: 2010-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by clint0n on 2010-03-10
[U]Change log
[/U]1. Guide created. 03/10/10
2. Changed the rc.local config so that the computer won't hang on start up if your router is down. Also added the change log and test subjects. 03/10/10
3. Added support for WPA. 03/12/10
4. Added command under Preparation to find available (wireless) interfaces. 03/14/10

_Tested on_
Ubuntu 9.10
Linux Mint 8
using WEP 128-bit hex keys and WPA(TKIP)


**--------------------------------------------------------------------------------Wireless Static IP Setup Guide-------------------------------------------------------------------------------------------**

Hello all, my name is Clinton. Today I want to show you how to make a "static ip" for your wireless connection(without using DHCP) so you can use your computer as a server or to host games, etc. behind a router.

**-------------------------------------------------------------------------------------Who Is This Guide For?-----------------------------------------------------------------------------------------------**

For people who were not able to get satisfactory performance and results from the standard network managers. You should already have a working device and the correct drivers installed for your wireless device before using this guide. This guide will show you how to set up your wireless device at the lowest level, which means we won't be using any fancy GUI's such as the default network-manager, if you aren't comfortable with using the terminal or editing system files then perhaps this isn't the guide for you. The guide will also make your device connect automatically at start up without any user interaction. This guide is probably not ideal if you are using different routers all the time, such as if you are a using a laptop, taking it to work using the internet and then coming home to use the internet. 

**----------------------------------------------------------------------------------Why Am I Making This Guide?------------------------------------------------------------------------------------------**

Simply because none of the other guides I could find worked for me or were only for wired connections. Two guides however strongly influenced me and taught me how to think correctly about how my computer runs and connects to the internet at start up. One was the [Arch Linux Beginners guide]("http://wiki.archlinux.org/index.php/Beginners%27_Guide") and the other by a guy named Vivek Gite [here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html").

[B]
----------------------------------------------------------------------------------------------Preparation------------------------------------------------------------------------------------------------------[/B][B]

[COLOR=Red]BACKUP [/COLOR][/B][COLOR=Red][COLOR=Black]- seriously there is a chance that something could go wrong if you mess up the commands or for some strange reason this guide doesn't work and you are stuck with no internet. It happened to me several times where I would read a guide and then they told me to uninstall network manager(because it interferes with doing static ip and other stuff) and then I was stuck without internet. So be prepared there is a chance that this may not work. Use the guide at your own risk and then blame me for it not working, lol.

[COLOR=Red]**KNOWLEDGE OF NETWORK SETTINGS **[COLOR=Black]- this is crucial! If you don't know what an IP is used for or don't know what your DNS servers are then do not proceed! You must do your homework and figure out the following:

[/COLOR][/COLOR][/COLOR][/COLOR]
[LIST]
[*][COLOR=Red][COLOR=Black][COLOR=Red][COLOR=Black]What 'IP Address' do you want to use on the network? For instance my router will allow me to use any address starting at [/COLOR][/COLOR][/COLOR][/COLOR]192.168.1.100 to 149 so long as it isn't being used by another computer on the network. So if my laptop is using a DHCP IP 192.168.1.105 then that one is taken, I have to either manually delete that one from the router(or let it expire) first or pick another. By the way DHCP means the router is managing the IPs given to the local computers, using a Static IP(locally speaking) means we are just going to take the IP from the router ourselves. So another good idea (if you want to have your router use DHCP for some computers and then you manage the static ones for your servers) is to start the Static IP's at the top of the range since typically the router will hand out(DHCP) IP's in numerical order starting at 192.168.1.100 or whatever the range may be for your routers settings(you need to figure this out yourself so read up on your specific router if you don't know about your settings, I am using a Linksys). So if you chose a static IP of 192.168.1.100 and then someone else hopped on the network using regular DHCP settings then the router might take away your IP and give it to them. So just a good idea to start at the top of the range(149) for static IP's unless you are going to make every computer on the network use static. At least that is my experience.
[*]What is your Subnet Mask number? Again check your router settings. My router's default is 255.255.255.0 . My outside world Subnet Mask is different though(255.255.255.240) so make sure you know the one that your router is using for managing internal IP addresses.
[*]What are your DNS Server numbers? Generally speaking there is usually two of these. Know what they are. Again check your router's status or with your ISP if you aren't sure.
[*]What is your ISP's domain and search names? Mine are the same - satx.rr.com . These names are sometimes not required or needed.
[*]What interface do you need to use to control your wireless card? Use ```
iwconfig
``` to see a list of available wireless devices(wlan0, ath0, etc.).
[*]What is your Broadcast number? Mine is 192.168.1.255 or so I've been told. I've also been told that you just replace the last number of your IP address with the biggest number of your Subnet Mask but I'm not sure. I recently found out from a more credible source that this number is your router number but the last number represents the maximum computers the router will handle hence the 255 the end. Figure yours out or just use the one you currently have before changing to static IP - find it by using ```
ifconfig wlan0
``` Note: replace wlan0 with whatever interface you are using to connect to the internet. Some people use ath0, eth0, etc. Know your interface, make sure you have the proper drivers installed before continuing.
[*]What wireless security are you using? Unsecured, WEP, WPA, or WPA2? Know what you are using and know the pass codes for it. *****UNFORTUNATELY***** I haven't been able to make a guide for WPA2 *YET* because I haven't tried and tested it. However for WPA2 users this guide may still be very helpful at getting you started. You just need to do something extra with the wpa_passphrase command which I cannot offer support for since I don't use WPA2.
[/LIST]

[COLOR=Red][B]
SAVE A COPY OF THIS GUIDE BEFORE PROCEEDING! 

ALSO DO NOT PROCEED IF YOU HAVEN'T READ THE PREVIOUS SECTION 'PREPARATION'! [/B][/COLOR]
[COLOR=Red][COLOR=Black][COLOR=Red][COLOR=Black]
[COLOR=Red][B]TURN OFF TEXT WRAPPING IN GEDIT BEFORE PROCEEDING MENU>ACCESSORIES>GEDIT>EDIT>PREFERENCES>UNCHECK TEXT WRAPPING THEN CLOSE IT

WARNING! I DON'T HAVE A GUIDE FOR WPA/WPA2 YET SO DON'T USE THE GUIDE UNTIL THEN USE ONLY FOR WEP AND UNSECURED
[/B][/COLOR]
[B]

-------------------------------------------------------------------------------------------Get Down To Business------------------------------------------------------------------------------------------[/B][/COLOR][/COLOR][/COLOR][/COLOR]


1. Open a terminal. Remove the default network-manager.
```
sudo aptitude remove network-manager-gnome
```**Also **you might want to remove other network managers you may have installed yourself(wicd, knetwork-manager, etc.) as these may conflict with the following setup.

2. Modify your /etc/network/interfaces file. 
```
gksu gedit /etc/network/interfaces
```[INDENT]This is a sample of mine. Copy the second part as you see fit.

> 
auto lo
iface lo inet loopback

iface [COLOR=Red]wlan0[/COLOR] inet static
address [COLOR=Red]192.168.1.105[/COLOR]
netmask [COLOR=Red]255.255.255.0[/COLOR]
network [COLOR=Red]192.168.1.0[/COLOR]
broadcast [COLOR=Red]192.168.1.255[/COLOR]
gateway [COLOR=Red]192.168.1.1[/COLOR]
dns-nameservers [COLOR=Red]24.93.41.127 24.93.41.128[/COLOR]
dns-search [COLOR=Red]satx.rr.com
[/COLOR]Replace the entries in red so that they correspond with your setup. Read the following for more info on each part.
**wlan0** is the interface device that controls your wireless card, some computers use ath0 if they have an Atheros chip.
**address **is the IP address you want.
**netmask **is your Subnet Mask.
**network **is your Gateway BUT change the last number part to zero.
**broadcast **is your Broadcast number. Your IP number mixed with your Subnet Mask.
**gateway **is your Gateway or router address. Once we are connected to the internet you can type this number into a internet browser address bar to modify router settings.
**dns-nameservers **add your DNS servers to this line. Separate using a space.
**dns-search **this is your ISP search domain, add this if you have it otherwise don't add this entry.

[/INDENT]3. Modify your /etc/hosts file. This file will create network aliases for your computer. So that when you type your hostname or IP in a browser it will know what computer to go to. 
```
gksu gedit /etc/hosts
```[INDENT]This is a sample of mine. You should only have to add a third line for your new alias so don't copy mine or delete lines from yours. Just add the IP you want and then copy your computer's name which should be on the second line already.

> 
127.0.0.1    localhost
127.0.1.1    clinton-desktop
[COLOR=Red]192.168.1.105   clinton-desktop
[/COLOR]
 The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/INDENT]4. Modify your /etc/resolv.conf file. This file stores your DNS servers and your ISP's search and domain names.
```
gksu gedit /etc/resolv.conf
```[INDENT]This is a sample of mine. Replace the red entries as you see fit, nameserver = DNS server. Some people don't need a search or domain entry. Also you can delete the "Generated by network manager" comment if you have one.
> 
search [COLOR=Red]satx.rr.com[/COLOR]
domain [COLOR=Red]satx.rr.com[/COLOR]
nameserver [COLOR=Red]24.93.41.128[/COLOR]
nameserver [COLOR=Red]24.93.41.127[/COLOR]
[/INDENT]5. [COLOR=Red]Save a copy of this guide to disk or print it out [/COLOR]before running the next command! Restart the computer and then we will test the connection.
```
sudo reboot
```[INDENT]Once you are back up and running we will bring the interface up. Replace wlan0 with your interface if you need to. 
```
sudo ifconfig wlan0 up
```[/INDENT][INDENT]Now we will scan for your router.
```
sudo iwlist wlan0 scan
```Now remember and perhaps write down the ESSID and Address(the long MAC address(i.e. 00:00:00:00:00:00) of the router you want to connect to. ESSID is also known as the name of the network.

Now we will try connecting to the network using either WPA, WEP or Unsecure. Must use quotes around ESSID's.

[COLOR=Red]Replace the following ESSID's and MAC Addresses with your router's from the previous iwlist command.[/COLOR][INDENT]_Unsecure Connection_
```
sudo iwconfig wlan0 essid "youressidhereinquotes" 
``````
sudo iwconfig wlan0 ap 00:00:00:00:00:00
```[/INDENT][COLOR=Red]Again don't forget to change the ESSID, MAC Address and WEP hex key.[/COLOR][INDENT][U] WEP Connection
[/U]```
sudo iwconfig wlan0 essid "youressidhereinquotes" key whateveryourhexkeyishere
``````
sudo iwconfig wlan0 ap 00:00:00:00:00:00
```[/INDENT][/INDENT][INDENT][INDENT]_WPA Connection_

For WPA connections we have to use an additional tool kit called wpa_supplicant. First off we make a config file for it.
```
sudo touch /etc/wpa_supplicant.conf
```Next we change the ownership of it so we can modify it. [COLOR=Red][COLOR=black]Change[/COLOR] "yourusername" [COLOR=black]to your computer user name.[/COLOR][/COLOR]
```
sudo chown yourusername /root /etc/wpa_supplicant.conf
```Now we will set your WPA password, change it to hex so the router can read it and then automatically place the info into the wpa_supplicant.conf we made previously.[COLOR=Red] Again replace the ESSID with your own, also change the password to the one you setup in the router for WPA.[/COLOR]
```
sudo wpa_passphrase youressid "yourwpapassword" > /etc/wpa_supplicant.conf
```Now since your WPA password will be stored in plain text we should make it only readable by the root user.
```
sudo chmod 0600 /etc/wpa_supplicant.conf
```Now we will try to associate our wireless device with the router. [COLOR=Red]Replace [COLOR=Red]the[/COLOR] essid in [COLOR=Red]"quotes"[/COLOR] [COLOR=Red]with your own.[/COLOR][/COLOR]
```
sudo iwconfig essid "youressidhere"
```Now we will set up a secure WPA connection. [COLOR=Red]Replace wlan0 with your own interface if you need to.[/COLOR] 
```
sudo wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf
```Now wait about 5-10 seconds to let it authenticate and then continue with the guide.

[/INDENT]Okay we are almost connected now. Now we will assign the IP using ifconfig.

[COLOR=Red]Replace the interface and IP with the one you need.
[/COLOR]```
sudo ifconfig wlan0 192.168.1.105
```[COLOR=Red]

[COLOR=Black]Now test your connection by going to google.com in a browser. If everything works then skip to step # 6, if something fails later come back and try this step though.

Okay for those of you who couldn't access the internet yet we just need to do one more step. We will manually add our router/gateway to the routing table.

[COLOR=Red]Replace the gateway(router) address with your own.
[/COLOR][/COLOR][/COLOR]```
sudo route add default gw 192.168.1.1
```[COLOR=Red][COLOR=Black][COLOR=Red]

[COLOR=Black]Alright you should be able to use the internet now - Proceed to step 6. 

If you can't connect then retrace your steps and make sure you didn't type anything wrong, it's very easy to make a typo! If you are trying to connect using WPA you may want to restart and then try connecting again or just continue with the guide since the computer may need to reload the .conf file we made.  If you failed using WEP double check that you entered your hex key correctly they can be tricky to the eyes at times. Post if you have problems, I'll try my best to help, use pastebay.org or pastebin.com to copy your debug info into and then post the links and your situation.
[/COLOR][/COLOR][/COLOR][/COLOR][/INDENT]6. Okay now the last step - we will set up your computer so it automatically connects to the network every time your computer starts. To do this we will modify the /etc/rc.local file.
```
gksu gedit /etc/rc.local
```[INDENT]
[COLOR=Black]Here I've included two different set ups, one for WEP/Unsecure and one for WPA.[/COLOR][COLOR=Red]
[/COLOR][B][COLOR=Red]
[U]WARNING: DO NOT LEAVE OUT THE "exit 0" LINE; Also do not foget the semi colons, backward slashes (\'s) and ampersand(&) for the last command.


[/U] [/COLOR][/B][INDENT] [COLOR=Purple]_**FOR WEP/UNSECURE CONNECTIONS**_[/COLOR]

This is a sample of mine. [COLOR=Red]Replace the red entries as you see fit.[/COLOR]I am set up for using WEP, so if you are using Unsecured just remove part of the line starting with the word "key". [COLOR=Red][COLOR=Black]The second '**if**config' command will set your IP so don't forget to use the one you desire.[/COLOR][/COLOR] [COLOR=Red][COLOR=Black]The route command will add your gateway/router to the routing table.[/COLOR][/COLOR]
> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ifconfig [COLOR=Red]wlan0[/COLOR] up ; \
iwconfig [COLOR=Red]wlan0[/COLOR] essid "[COLOR=Red]yourESSIDhere[/COLOR]" key [COLOR=Red]yourhexkeyhere[/COLOR] ; \
iwconfig [COLOR=Red]wlan0[/COLOR] ap [COLOR=Red]00:00:00:00:00:00[/COLOR] ; \
ifconfig [COLOR=Red]wlan0[/COLOR] [COLOR=Red]192.168.1.105[/COLOR] ; \
route add default gw [COLOR=Red]192.168.1.1[/COLOR] &
exit 0
[COLOR=Purple][U][B]FOR WPA CONNECTION

[/B][/U][/COLOR]This is a sample of mine for WPA. [COLOR=Red]Replace the red entries as you see fit. [COLOR=Black]The route command will add your gateway/router to the routing table.[/COLOR] [/COLOR][COLOR=Red][COLOR=Black]The second '**if**config' command will set your IP so don't forget to use the one you desire.[/COLOR][/COLOR] If you have a really slow or prehistoric computer you may want to increase the value of the second sleep command to 10 (seconds).
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ifconfig [COLOR=Red]wlan0[/COLOR] up ; \
iwconfig [COLOR=Red]wlan0[/COLOR] essid "[COLOR=Red]youressid[/COLOR]" ; \
sleep 5; \
wpa_supplicant -B -Dwext -i [COLOR=Red]wlan0[/COLOR] -c /etc/wpa_supplicant.conf ; \
sleep 5; \
ifconfig [COLOR=Red]wlan0 192.168.1.105[/COLOR] ; \
route add default gw [COLOR=Red]192.168.1.1[/COLOR] &
exit 0[COLOR=Red]
[COLOR=Black]
[/COLOR][/COLOR][/INDENT]**[COLOR=Red]_ WARNING: DO NOT LEAVE OUT THE "exit 0" LINE_[/COLOR]**[B][COLOR=Red]_; Also do not foget the semi colons, backward slashes (\'s) and ampersand(&) for the last command._
[/COLOR][/B]

[/INDENT]Alright you should be done now and whenever your computer starts it will automatically connect to your network. I hope you enjoyed the guide. Let me know if it helped or not. 

Peace to the world.[INDENT][COLOR=Red]
[/COLOR][/INDENT]

---

### Post by Naggobot on 2010-03-11
Accurate and careful work on quide. Kudos on careful warnings. 

I my self am  no expert on this matter so can you comment if it is beneficial, recommendable or necessary to use DHCP reservation on the router to fix the ip on router if DHCP is used? 

I personally have 3 laptops and PS3 at home. Two of the laptops and PS3 have IP's defined through DHCP reservation and one minilaptop gets it's IP by DHCP. My (cheap Dlink DIR-300) router has section where ip adresses can be defined by mac adresses. 

So far I have experienced no problems with this setup. I originally configured the PS3 about a year ago and the laptops few a weeks ago. 

This is what the LAN settings page looks like 

[http://www.flickr.com/photos/47127461@N08/4424373857/](http://www.flickr.com/photos/47127461@N08/4424373857/)

Right now there is nothing in the DHCP client list since the minilaptop has not been active for a long time and DHCP has expired.

---

### Post by clint0n on 2010-03-11
> **Naggobot said:**
> Accurate and careful work on quide. Kudos on careful warnings. 

I my self am  no expert on this matter so can you comment if it is beneficial, recommendable or necessary to use DHCP reservation on the router to fix the ip on router if DHCP is used? 

I personally have 3 laptops and PS3 at home. Two of the laptops and PS3 have IP's defined through DHCP reservation and one minilaptop gets it's IP by DHCP. My (cheap Dlink DIR-300) router has section where ip adresses can be defined by mac adresses. 

So far I have experienced no problems with this setup. I originally configured the PS3 about a year ago and the laptops few a weeks ago. 

This is what the LAN settings page looks like 

[http://www.flickr.com/photos/47127461@N08/4424373857/](http://www.flickr.com/photos/47127461@N08/4424373857/)

Right now there is nothing in the DHCP client list since the minilaptop has not been active for a long time and DHCP has expired.

If you don't want to manually set up static IP's for any computers/ps3's that might want to use the network/router then yes you will need to have the DHCP turned ON in your router settings. If you are going to set up static IP's for all the computers and ps3's then you could turn the DHCP server off in your router. I leave the DHCP server on for mine though just so if people want to bring their computer over we won't have to do much configuring.

It is indeed beneficial to have the router remember which computer should get what IP through the DHCP. The main reason is so the computers don't step on each other's toes when trying to connect. However you don't need DHCP(from my experience) if you are setting up static IP's on all of the computers. But again not every computer is going to need active(non passive) connections, most people just want to use the computer to check email, read and buy stuff. So it is much more convenient to let the router handle it for most connections.

I also have a ps3 and I personally have mine set up as a DMZ or demilitarized zone. They call it that because it leaves the ps3 wide open. Now this may or may not be very wise but in my opinion it's worth saving me the trouble of having to forward ports for every game that I want to host with. Plus I don't know about you all but I myself don't know many people who can hack ps3's yet - the hardware for them is still pretty darn secure. Only recently in the past month has someone finally been able to half-*** crack one - see [http://geohotps3.blogspot.com/2010/01/heres-your-silver-platter.html](http://geohotps3.blogspot.com/2010/01/heres-your-silver-platter.html) and he actually had to physically break his hardware to do it, haha.    

As far as reserving your IP's by the MAC address of the wireless cards I couldn't tell you how to do it or give you support for that. But from my experience I could not get a connection by using a MAC filter which is probably a little different then what you are talking about. I didn't spend much time trying it though either, lol.

EDIT: You know after re-reading your post I must know - are you able to host servers by only configuring and allocating the IPs through the DHCP server on your router or do you still have to make them static on the actual computers? You see I don't have that option because my router is ancient, so perhaps my guide is irrelevant for some people since it might be easier to just do it through the newer routers?

EDIT2: I guess it is true that you can make static IPs just by assigning them through the routers DHCP server(that is - if your router has the capability) - [http://en.wikipedia.org/wiki/Static_IP#Method_of_assignment](http://en.wikipedia.org/wiki/Static_IP#Method_of_assignment) but this guide may still be helpful to bypass some bugs related to just getting a connection in general. But in order to use the DHCP server we would have to run dhcpcd or dhclient on the computers after connecting instead of assigning the IPs with ifconfig and the /etc/network/interfaces file. Well 'O well - I'll rename the topic then.

EDIT3: > I my self am no expert on this matter so can you comment if it is beneficial, recommendable or necessary to use DHCP reservation on the router to fix the ip on router if DHCP is used? So let me rephrase my answer to this question. My answer would be no it is not beneficial to do that for the computers you are going to follow this guide for since this guide does not use DHCP. However it would be very beneficial to use it if you had to have static IP's for say a whole company or a large network. But in order for this guide to help you with that you would have to ignore certain parts of this guide(namely the /etc/network/interfaces file and also the ifconfig "IP" command in the rc.local script) and also add a program such as dhclient or dhcpcd to run in the rc.local script so that your computer will use your router's DHCP server. Otherwise this guide totally bypasses all forms of the DHCP server on the router.

---

### Post by Naggobot on 2010-03-12
Thank you clint0n for clarification and taking the time to reply. If I am not mistaken you did answer all of your questions in the subsequent edits. I still comment a bit on 

> I must know - are you able to host servers by only configuring and allocating the IPs through the DHCP server on your router or do you still have to make them static on the actual computers?I am quite green with Ubuntu but the reason I have "fixed" the ip adresses from the router for the laptops is that I am running rsync daemon on one laptop and second laptop works as a rsync client. Now when the "secondary" machine boots up a start up script runs the rsync client and backs up the first "primary" laptop. 

I have also samba share so that all work is saved on primary computer. 

Hopefully I have time at some point to do what you did and write a post on the setup procedure. I spent a good two days working on it since I had to start from absolute zero and I must have surfed through 100 sites to get every snippet of information together. It would also enable me to thank relevant sites/threads I retrieved the information from. Also I would like to have a peer review on the setup so that it is correct.

So I hopefully this answers your question at least partially. Rsync uses ip adress to connect to daemon and so far it has worked (yes few weeks, knock knock). Now that I have info on how to define the host name (thanks to you) I think I will tinker with that next.

---

### Post by clint0n on 2010-03-13
You are more than welcome. And yes I understand how it works now. I just never knew about that router feature. My router is ancient hehe.

> **Naggobot said:**
> 
Hopefully I have time at some point to do what you did and write a post on the setup procedure. I spent a good two days working on it since I had to start from absolute zero and I must have surfed through 100 sites to get every snippet of information together. It would also enable me to thank relevant sites/threads I retrieved the information from. Also I would like to have a peer review on the setup so that it is correct.


Haha that's the exact reason why I wrote the guide, more or less anyway. I did it just for me at first so I didn't ever have to search for and then string together multiple incomplete guides from various places every time I format my computer and need a stable (and static) internet connection, haha. Plus since writing it I've memorized how to do it now. Good luck with the guide, PM me a link to it when you finish it. :)

---

### Post by clint0n on 2010-03-30
why is the top post so wide now?? can an admin fix it?

---

