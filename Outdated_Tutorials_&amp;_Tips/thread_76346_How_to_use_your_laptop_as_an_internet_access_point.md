---
title: "How to use your laptop as an internet access point for a desktop"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by matthew on 2005-10-15
**How to use your laptop as an internet access point for a desktop**
 
I have tested this thoroughly since its original creation. In the meanwhile I upgraded the OS on the laptop form Hoary to Breezy. Now that both the computers in question are running Breezy and this has been tested fully I am posting it here. The original thread where I posted about this topic in the Hoary section is [here]("http://www.ubuntuforums.org/showthread.php?t=73406") and it was based on [this]("http://ubuntuforums.org/showthread.php?p=395983") thread. Special thanks to mlomker for his kind and vital assistance.
 
The goal here is to use a crossover cable and a wireless laptop to connect to the internet from a desktop computer that is too far from the router to run a cable.
 
By the way, there are a lot of words here, but that is because I like to be complete, not because this is hard. Read the whole thing before you start and you will discover this isn't real technical or difficult.
 
 [B]Notes: 
[/B]I am running Ubuntu Breezy 5.10 on both the laptop and desktop.
 
 My laptop is an AOpen 1557gls, configuration listed [here]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsOthers") in the entry I made on the Ubuntu Wiki.
 
My desktop is made up of a bunch of old parts including an AMD Duron processor. It is nothing special except it has a working ethernet card that I pretested by plugging it directly into my router.
 
My router is a Linksys WRT54G with the latest official firmware. This will likely work with other hardware and setups, but I have only tested it with mine. I am using WPA, but since all that is needed here is a working wireless connection that is beyond the scope of this howto. I connect from the router to the high-speed modem using DHCP.
 [B]
Before you start:[/B]
 Make sure you have a working connection from your wireless laptop to your router and from there to the internet.
 
Make sure you know how to use and set up your router as well as how to find it's configuration. For me this is through a browser interface at 192.168.1.1 when connected directly to the router via an ethernet cable or wireless connection.
 
Find the following information from your router's configuration. I will list mine (where security permits) for comparison and so you can see it below as we continue. On the linksys wrt54g with firmware version 4.20.7 this is found under Status->Router in the configuration pages.
 
    IP address: 192.168.15.100
    Default gateway: 192.168.15.1
  Subnet mask: 255.255.255.0
 Domain name: your.netprovider.net
    DNS: xxx.xxx.xxx.xxx (there will likely be 2 or 3 assigned to you by your internet provider and DHCP)
 
 *for me to log into my router from any computer on the network the address is 192.168.1.1
 
 *the router assigns addresses to computers using it from 192.168.1.100 to 192.168.1.149
 
 **Things you will need:**
 A desktop computer with a working Ubuntu installation and a tested and known to work ethernet card. *(I will call this desktop)*
 A ethernet crossover cable...*NOT* a regular ethernet cable
 A wireless access point that is already configured properly and has access to the internet *(I will call this router)*
A laptop or other computer with a working Ubuntu installation and a wireless connection that is configured properly and already works *(I will call this laptop)*
 
 **Step 0: Plug in the cable**
Plug the crossover cable in to the ethernet ports on the desktop and the laptop. Make sure both computers are turned on before you continue. It will be easiest if the computers are right next to each other for this process.
 
 **Step 1: Firestarter on the laptop to configure access:**
a. If you have a firewall installed on the laptop, disable and uninstall it. We will use Firestarter as it is easy to configure. If you already know how to configure your firewall and want to continue using it, feel free to do so.
 
 b. Install Firestarter on your laptop, either using synaptic or apt-get install firestarter.
 
 c. Configure Firestarter:
 
 Preferences->Network Settings
 -select the laptop's wireless card (for me eth1) as your "Internet Connected Network Device"
 -select the laptop's ethernet card (for me eth0) as your "Local Network Connected Device"
 -select "Enable internet connection sharing"
 
 **Step 2: Configuring your network rules on the laptop**
 
 From the panel menu: System->Administration->Networking
 
Your wireless connection (for me eth1) should already be configured properly and working so I won't discuss that here. Your settings for that card/connection will not change at all.
 
 Highlight your Ethernet Connection (for me eth0) and select "Properties"
 
 Check "This device is configured"
 
 Configuration: Static IP address
 IP Address: 192.168.2.102 *see note just below
 Subnet mask: 255.255.255.0
 Gateway address: 192.168.15.100 +see note just below
 
 Choose your wireless connection as the "Default gateway device"
 
 Click "ok" because you are done here.
 
*the important thing here is to choose a different subnet from what your router assigns to computers connected to it. Mine assigns addresses in the 192.168.1.xxx subnet so I chose to use here 192.168.2.xxx
 
 +This is from the Default Gateway listed in the router's setup page as shown above.
 
 **Step 3: Configuring your network rules on the desktop**
 
 From the panel menu: System->Administration->Networking
  
 Highlight your Ethernet Connection and select "Properties"
  
  Check "This device is configured"
  
  Configuration: Static IP address
  IP Address: 192.168.2.103 *see note just below
  Subnet mask: 255.255.255.0
  Gateway address: 192.168.2.102 +see note just below
  
  Choose your wireless connection as the "Default gateway device"
  
  Click "ok" because you are done here.
  
*the important thing here is to choose the same subnet as your laptop is using. Earlier we used 192.168.2.102 subnet so I chose to use here 192.168.2.103. Same subnet, different computer.
  
  +This ***has*** to be the same as the IP address for your laptop's ethernet connection (eth0).
 
 **Step 4: Configuring the Domain Name and servers properly**
This step insures that your desktop will have access to the internet the same way the laptop does and be able to use names for web sites and not just IP addresses...in other words, we are going to tell your desktop the some of the same information manually that your router is telling your laptop through DHCP.
 
 On your laptop, open the file /etc/resolv.conf
 In it you will find something like this:
      Code:
     [LEFT]search your.netprovider.net
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx[/LEFT]
       
  Keep this information handy.
 
 Go to the desktop and put the exact information in the file /etc/resolv.conf on the desktop using your favorite editor.
      Code:
     [LEFT]sudo gedit /etc/resolv.conf[/LEFT]
       
It is probable that this file is currently blank. In any case, completely erase the contents if there are any and type in exactly what is shown in the same file on your laptop then save.
 
 Okay. Time to test. Open firefox and type something simple in the address bar like "www.google.com"
 
 If we did everything right it will work, but we are not quite done.
 
The resolv.conf file will be regenerated on the desktop every time you reboot. Unless you enjoy recreating the file each time, there is one more step remaining.
 
 While the current internet connection is working on the desktop, with all the [extra repositories enabled]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), fire up synaptic or apt-get install **resolvconf **on the desktop.
 
 Once that is installed do this on the desktop

     [LEFT]```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup

sudo gedit /etc/network/interfaces
```[/LEFT]
       
  and add the following to that file under the heading shown using the information from your current, working /etc/resolv.conf:

     [LEFT]```
 iface eth0 inet static
  dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
  dns-search your.netprovider.net
```  [/LEFT]
       
  This will automatically create your (correct) /etc/resolv.conf file every time you reboot.
 
Please post any mistakes you find and I will correct them. I don't know how adept I can be at answering questions as I just learned this myself, but feel free to post those here as well and I will try or we can hope someone more knowledgable can assist as well.
 
Also, I plan to submit this to the wiki soon after a few other people have tested the how-to and confirmed it works.
EDIT: Done and in [CategoryCleanup]("https://wiki.ubuntu.com/CategoryCleanup") awaiting final inclusion. Temporary wiki address is [here.]("https://wiki.ubuntu.com/forum/hardware/UseWirelessLaptopAsAnInternetAccessPoint")

---

### Post by Rxke on 2005-10-17
Works for me.


I used to do it the quick and dirty way, as laid out on the Firestarter website : [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php) i.e.: w/o the resolv.conf tweak, because I never type in adresses in the adressbar anyway, but this is a nice addition :D

BTW, it is simple to rip open an existing patchcable and to the cable-twist in order to make it a crossover [http://www.makeitsimple.com/how-to/dyi_crossover.htm](http://www.makeitsimple.com/how-to/dyi_crossover.htm)

---

### Post by matthew on 2005-10-17
Rxke, thanks for trying it out and posting your experience. I am gratified to hear it worked for you. I also appreciate the links!

---

### Post by Rxke on 2005-10-17
You're welcome.
but come to think of it... i mainly followed the 'simple' approach posted on the Firestarter site, then checked your info when things didn't work directly.
BTW, this works cross-platform too, I use my laptop under Breezy to connect my desktop running OSX...

---

### Post by kroiz on 2005-10-28
do I need the firewall (firestarter) to make it work or just for security reasons?
'cause Im not running any now. and I prefer not to install it if it is not essential.

---

### Post by matthew on 2005-10-28
[quote=kroiz]do I need the firewall (firestarter) to make it work or just for security reasons?
'cause Im not running any now. and I prefer not to install it if it is not essential.[/quote]
It's not necessary if you can figure out another way to enable internet connection sharing. 

I have found Firestarter to be an easy way to manage port access to a computer. It is really just a graphic frontend for IP Tables, the linux kernel's powerful firewall. It's easy to use so I recommend it.

If you have a preferred method without using Firestarter you can use it.

---

### Post by kroiz on 2005-10-28
[QUOTE=matthew]It's not necessary if you can figure out another way to enable internet connection sharing. 
If you have a preferred method without using Firestarter you can use it.[/QUOTE]

got it, thanks.

I got another question. what will happen when I will connect my laptop at work thru the ethernet? it wont work now. right? because I change it to static ip.

any elegant solution except manualy changing from DHCP to static when I get home and then at work from static to DHCP.

-Edit: I see that there is something called location in the network dialog, so I guess I can configure a location for home and work and set them to static and DHCP. 
I wonder if there is a way to make linux start with the right location? so when I boot my laptop at work it will start with the right network profile.

---

### Post by matthew on 2005-10-28
[quote=kroiz]got it, thanks.

I got another question. what will happen when I will connect my laptop at work thru the ethernet? it wont work now. right? because I change it to static ip.

any elegant solution except manualy changing from DHCP to static when I get home and then at work from static to DHCP.[/quote]
I've never done it, but there is a way to make the go-through computer use DHCP, so your laptop then could use DHCP in both places. You would need to search on the wiki...pretty sure I saw something about this there. [http://www.ubuntulinux.org/wiki](http://www.ubuntulinux.org/wiki) If not there, try Google. I know this can be done, but never having done it I don't know what it would take. It might end up being pretty easy.

---

### Post by kroiz on 2005-10-29
I thought I could do this without the firewall untill I bumped into  this:
From the "Linux IP Masquerade HOWTO", Chapter 3. Setting Up IP Masquerade:
```
 Once you have IP MASQ functioning, it is HIGHLY recommended for the user to implement a STRONG IPFWADM/IPCHAINS firewall ruleset.
```

so I'm gonna try it as in this howto.
btw I still dont understand why the firewall is needed and still curious, so if anyone care to explaine...

---

### Post by matthew on 2005-10-29
[quote=kroiz]I thought I could do this without the firewall untill I bumped into  this:
From the "Linux IP Masquerade HOWTO", Chapter 3. Setting Up IP Masquerade:
```
 Once you have IP MASQ functioning, it is HIGHLY recommended for the user to implement a STRONG IPFWADM/IPCHAINS firewall ruleset.
``` 
so I'm gonna try it as in this howto.
btw I still dont understand why the firewall is needed and still curious, so if anyone care to explaine...[/quote]
Ubuntu is pre-configured with no ports open. It is as if a firewall already exists preventing any traffic from coming in to the computer unless explicitly requested by the user (ie though a web browser, synaptic, etc).

IP tables is the main linux firewall (using IPCHAINS as the rules), but it takes a lot of reading and work to learn to use it.

Most other firewall packages available for linux simply enable the user to configure IPtables easily. Firestarter is my favorite for that.

So, in essense you already have a sort of firewall working for you. Installing and using another program like Firestarter will let you configure it how you want/need quickly and easily.

---

### Post by ppxdpah on 2005-10-30
[QUOTE=kroiz]I thought I could do this without the firewall untill I bumped into  this:
From the "Linux IP Masquerade HOWTO", Chapter 3. Setting Up IP Masquerade:
```
 Once you have IP MASQ functioning, it is HIGHLY recommended for the user to implement a STRONG IPFWADM/IPCHAINS firewall ruleset.
```

so I'm gonna try it as in this howto.
btw I still dont understand why the firewall is needed and still curious, so if anyone care to explaine...[/QUOTE]

You've got to think of a firewall as more of a switchboard than a gate - so if your computer receives a signal it can either:

ACCEPT - send the signal on to the appropriate application or location,
DROP - throw the signal away
REJECT - send a message back saying it won't accept the signal.

But it can also redirect the signals or pass them through to another network card and then on to more machines which is what is happening in this case.  It can also do things like change the port numbers used and all kinds of fancy stuff such as  detecting whether an incoming signal is part of a two way communication originating with the local machine.

Network addess translation (NAT) is a good keyword to find out more.

---

### Post by Tunnelrat81 on 2005-11-20
This is a question to Rxke if you're still around.  I've been working on using firestarter to do the same cross platform internet sharing that you were able to do, but have run into problems.  My internal network IP for my "hub" ubuntu machine is 192.168.1.145, connecting to the wireless network via wlan0.  I set up my eth0 connection as per the instructions here with an IP address of 192.168.1.146, on the same subnetmask with 192.168.1.145 as my gateway address.  This is the correct way of setting up the connected computer as I understand from this post, but for my OSX computer that is connected to this one via a crossover cable, I haven't been able to setup correctly.  I would appreciate some help on this.  In Firestarter I have set up the wlan0 and eth0 appropriately and enabled internet sharing, so I imagine that part of the process is properly setup as well.  But I have yet to get connectivity, pinging or otherwise, so its not just a dns problem.  

I'm using Breezy on my desktop PC (the wireless connected computer) and OSX on my wired "hopefully soon to be online" Powerbook Pismo.  I know my eth0 card is working because I've done internet sharing through windows to it with the same card/cable setup.  Thanks.

-J

---

### Post by Rxke on 2005-11-21
Hi Tunnelrat,

Weird, I was *just* thinking about how long ago it was since I got something in my inbox from subscribed Ubuntu-topics, I open my browser and... HeeHee...

I slavishly followed the step-by-step setup guide on Firestarter's documentation pages, so my IP numbers are slightly different...
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

On my Mac I did Systempreferences/'internet and network'  and then select 'network' (the 'globe')
and then in network: select 'Built-in Ethernet' (second errr... rowselector that says: "Show"; then select TCP/IP (leftmost)

And there I set up: 
Configure IPv4: Manual
IP-adress: 192.168.0.3  (can be 2, 4, 5, 6....)
Subnetmask 255.255.255.0
Router: 192.168.0.1
DNS-servers: 192.168.1.1

Oh, and then maybe in 'show', select "configuration network ports" and select "Built-in  Ethernet"

Extra info (probably superfluous) In 'internet and network/sharing' my firewall is on, internet sharing is off (since my desktop is not sharing to another one down the line, it is the 'receiver' and the 'voorzieningen' (dunno for sure how to translate that in English, amenities, services?) are all non-selected.

Hope this helps, if not, let me (us) know, and... If it works too!

---

### Post by Tunnelrat81 on 2005-11-21
Hey thanks for your prompt reply.  With some more tweaking and prodding I was able to get my connection working.  I think I had it set up correctly but I was having problems because whenever I would open firestarter and then restart my network, I'd lose my internet connection on my wireless computer and gain connection between my two.  So I could ping one from the other, but no internet on either.  My ubuntu install is a bit wierd in that I have to chattr +i (make the file immutable)  my /etc/network/interfaces file to keep my WEP recorded there correctly.  And I'm sure Firestarter was having trouble with that file being immutable when/if it had to tweak with it.  Whatever the problem was its apparently fixed now as I have my "interfaces" file setup the right way and immutable again with those changes.  

I did have a question though about the resolvconf program that the howto specifies to install and use for recording information etc.  Was the howto refering to installing this program on the WIRED computer or the wireless computer?  If its the wired one (my mac) then I"m sure I do'nt have to worry about it, and it makes sense that thats what they're refering to.  But I'll need to know if its necessary to install it on my ubuntu computer. 

Again, thank you for your help.  Support here is amazing.=)

-J

---

### Post by matthew on 2005-11-21
[quote=Tunnelrat81]I did have a question though about the resolvconf program that the howto specifies to install and use for recording information etc. Was the howto refering to installing this program on the WIRED computer or the wireless computer? If its the wired one (my mac) then I"m sure I do'nt have to worry about it, and it makes sense that thats what they're refering to. But I'll need to know if its necessary to install it on my ubuntu computer.[/quote]
I intended for resolvconf to be installed on the wired computer that is using the wireless computer as its access point. I have reworded that sentence in the howto to be a bit more clear...sorry for the confusion and thanks for asking so I could refine the language.

---

### Post by Tunnelrat81 on 2005-11-22
I'm happy to inform you that I'm up and running on both computers.  This was a step in the right direction for me as that iptables howto had shakin' in my boots.  And when my girlfriend would come over to study and needed my mac laptop to be online I was forced to boot into windows =(.  I've set it up, configured it, and set it to open the gui on startup (its a home pc so local security isn't an issue) but I do have one last problem.  After a reboot of the wireless computer (while still wired to the running mac) there is no connectivity between the two and thus no access from the other computer.  All I have to do to fix this is to run "/etc/init.d/networking restart" but it doesn't make sense that this should be necessary after each reboot because my network pref's haven't changed.  Thanks again for your help.  Without you guys on this forum, Ubuntu would definitely have a smaller advantage over the others.  

-J

---

### Post by matthew on 2005-11-22
Yeah, it doesn't make sense to me that this should be necessary. It isn't on my setup. I'm not sure how to fix that. 

Anyone else??

---

### Post by Rxke on 2005-11-22
[QUOTE=Tunnelrat81]After a reboot of the wireless computer (while still wired to the running mac) there is no connectivity between the two and thus no access from the other computer.  All I have to do to fix this is to run "/etc/init.d/networking restart" [/QUOTE]

That's puzzling.... You have to run that on the wired one? 

I don't remember I have to do that, but it's been more than two weeks since I rebooted, though I sometimes close (put to sleep) my iBook at night... and it doesn't mess things up at all.

---

### Post by Tunnelrat81 on 2005-11-23
I have to run that command on my wireless ubuntu pc.  The computer acting as the bridge.  Otherwise it doesn't properly setup the bridge to the wired mac after a reboot.

-J

---

### Post by Rxke on 2005-11-23
Weird... It should do that automatically during startup... Coincidentally, I rebooted my wireless iBook, for the kernel-update, and while doing that, I checked how mine behaved... I had automatic (re-)connectivity before gnome started...

You could try going into your menu: system/preferences/sessions and there select 'programs startup' (or something silmilarly sounding, again, I'm on a 'Dutch-speaking' system so not 100% sure about the translation...)

and there add the command. Not sure this needs to be done under sudo; there's a thread or in the Wiki a howto how to do admin privileges in startup stuff...

---

### Post by just4fun on 2005-12-10
there is tricky ? 
(1.wan/_dhcp_/cable/router/modem) -> (2.wlan/laptop -> 3.lan/laptop)->(4.wan/_dhcp_/dsl/router) -> (5.server/etc.....):confused: ](*,) ](*,) ](*,)

---

### Post by matthew on 2005-12-10
I'm going do what I can to try to help just4fun here a little bit. Here are the contents of two emails he sent me that give a little bit more detail into his problem/desired goal. I asked him to post here because I wasn't too clear on what he was hoping to do nor really what has been done so far. Maybe someone else will understand it better and can help out.

First email:> really liked youre how-to, but i have a little problem with setup...[IMG]http://us.i1.yimg.com/us.yimg.com/i/mesg/tsmileys2/16.gif[/IMG]
 Internet<->wlan/laptop<->dlink router<->server/desktops
 can't configure , can you help me with any advise, plz...[IMG]http://us.i1.yimg.com/us.yimg.com/i/mesg/tsmileys2/06.gif[/IMG] second email:
> my problem is in subnets
laptop/wlan gets ip from DHCP wireless Linksys
ip 192.168.1.102 gw 192.168.1.1
laptop/lan 
ip 192.168.2.102 gw 192.168.1.102
dlink can be configured for static ip, but I don't know what next?
dlink has own DHCP 192.168.0.1 stop.....[IMG]http://us.i1.yimg.com/us.yimg.com/i/mesg/tsmileys2/06.gif[/IMG] 

---

### Post by racyrefinedraj on 2006-02-18
Worked like a charm for me. THANKS! this means I don't have to lug my desktop across campus to set up wifi!!!

Also, I think under "configuring the desktop", when you say

> 
Choose your wireless connection as the "Default gateway device"


You mean choose your WIRED connection as the default gateway device. If my wireless connection was working on my desktop, I wouldn't need your howto :D 

Anyway, thanks a bunch

---

### Post by matthew on 2006-02-18
[quote=racyrefinedraj]Worked like a charm for me. THANKS! this means I don't have to lug my desktop across campus to set up wifi!!![/quote]Yay!! I'm glad to hear it worked for you!![quote=racyrefinedraj] You mean choose your WIRED connection as the default gateway device. If my wireless connection was working on my desktop, I wouldn't need your howto :D [/quote]I meant wireless--on the laptop that is being used as the gateway for the desktop to have internet access. I was referring to telling the Laptop to look at the wireless connection first when trying to connect to the outside world. Not a big deal, though. It's more important that stuff works than it is to settle on terminology.[quote=racyrefinedraj] Anyway, thanks a bunch[/quote]You are very welcome!

---

### Post by sidestream84 on 2006-07-14
Your method looks pretty useful for some situations, but the title is a bit misleading (I'm guessing it can't be changed now though).

Your connection is something like this (~ denoting wireless and - denoting wired connections):
```

Modem -> AP(w/ NAT routing) ~>  Laptop (connected to AP as a client and NATing again to its own clients) -> Desktop

```
While if the laptop were actually acting as an access point, it would be more like:
```

(laptop taking the place of the linksys router/AP)

Modem -> Laptop(w/ configuration for serving as NAT router and AP) ~> [wireless clients: PDAs, other laptops, etc]

-- OR --

(laptop complimenting linksys router/AP, providing more wireless coverage/range for other wireless devices)

Modem -> AP(w/ NAT routing) ~> [wireless clients]
               ^
               |
               v
         Laptop(w/ configuration acting as an AP) ~> [wireless clients]

```
Where the laptop and AP are connected via a wire (in the second example), and the laptop is broadcasting the only SSID (in the first example), or the same SSID that the AP is (in the second example-- effectively giving you more of a wireless coverage range via two locations for wireless clients to connect) and allowing other wireless devices to associate with it and use its wired connection just like your Linksys WRT54G does.

I'm not trying to negate or dilute the solution you've come up with (on the contrary, your process would be useful and used for something different than I'm describing), just that the laptop is more of a wireless to wired bridge (as a client to your existing linksys AP) than an actual access point, and the title of the thread may mislead some people as to its contents.

That said, do you (or anyone else reading) happen to know how to configure an ubuntu computer to act as an access point (ex: use a computer with wired ethernet connected to the modem and a wireless PCI card or USB adapter configured to provide the same features as your Linksys WRT54G)? I only need more info regarding the access point features (ex: getting my laptop to see the ubuntu machine's SSID and be able to connect to it just as a laptop can connect to the WRT54G), I'm already set for the standard networking things (masquerading, dhcp, etc). I found a few leads for running an access point on a linux machine, but they all required hostap which only works with chipsets I don't have at my disposal (Atheros, Prism, etc). I guess I should rephrase the question to "do you know how to configure ubuntu to act as an access point without using hostap (assuming it's possible)?"

---

### Post by tempo500 on 2006-09-17
hey,

working well! thanks for this. just one problem. ubuntu edgy does not memorize the dns entry. is there another way, besides putting the lines into the interfaces line? my next try would be to uninstall resolvconf and see if resolv.conf memorizes the two dns lines... thanks, phil

---

### Post by matthew on 2006-09-17
[COLOR=Black]You should be able to force the use of a specific dns server if you put the following in /etc/dhcp3/dhclient.conf

```
## Added by me to try to force the use of this dns server
prepend domain-name-servers xxx.xxx.xxx.xxx;
```Replace xxx.xxx.xxx.xxx with the IP of the dns server you will use. If there are more than one it is okay to have more than one "prepend..." line.

Put this near the beginning of the file. Most of the file is commented out right now anyway, so right at the top should be fine.

For comparison, here is my original /etc/dhcp3/dhclient.conf with the addition in [/COLOR]   [COLOR=Red]red[/COLOR][COLOR=Black]. Change the file, save and reboot. Note: I'm not using Edgy yet, so I'm really taking an educated guess that this should work.[/COLOR][COLOR=black]
[/COLOR]```
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#


[COLOR=Red]## Added by matthew to try to force the use of OpenDNS
prepend domain-name-servers 208.67.222.222;
prepend domain-name-servers 208.67.220.220;[/COLOR]


#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, host-name,
    netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

---

### Post by tempo500 on 2006-09-18
mh, didn't work. its not a biggy. if its (for now)just opening network manager and loading my saved preferences, i don't mind. shouldn't there also be an entry for the search domain?

thanks for the prompt reply, phil

---

### Post by matthew on 2006-09-18
> **tempo500 said:**
> mh, didn't work. its not a biggy. if its (for now)just opening network manager and loading my saved preferences, i don't mind. shouldn't there also be an entry for the search domain?

thanks for the prompt reply, philHmm...I'm not sure what else to try. Maybe someone else will jump in with an idea (though this thread doesn't get a lot of traffic). I suppose if it becomes important to figure out then you could always start a more issue-specific thread in the networking forum. If you do, post a link here. I would love to learn how to fix this.

---

### Post by tempo500 on 2006-09-18
hi again,

i uninstalled resolvconf, and hey... it memorized my dns entry's! lucky me. but things take time... i am now having troubles to connect to the local shared folders on the computer that is sharing the internet. ubuntu asked me if it should install samba and nfs when i added a folders to share(on the laptop)what i did... so, any hints? phil

---

