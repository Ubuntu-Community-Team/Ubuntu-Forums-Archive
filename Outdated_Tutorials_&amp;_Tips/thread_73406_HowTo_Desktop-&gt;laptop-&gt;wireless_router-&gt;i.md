---
title: "HowTo: Desktop-&gt;laptop-&gt;wireless router-&gt;internet"
date: 2005-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by matthew on 2005-10-09
**HowTo: Desktop->laptop->wireless router->internet**

This is my first HowTo . I got this working today and I think I can make this clear. Hopefully it will work for you as well. The original thread where I asked about this topic and got help is [here.]("http://ubuntuforums.org/showthread.php?p=395983") Special thanks to mlomker for his kind and vital assistance.

The goal here is to connect to the internet from a desktop computer that is too far from the router to run a cable using a crossover cable and a wireless laptop.

By the way, there are a lot of words here, but that is because I like to be complete, not because this is hard. Read the whole thing before you start and you will discover this isn't real technical or difficult.

[B]Notes: 
[/B]I am running Ubuntu Hoary 5.04 on my laptop and Ubuntu Breezy 5.10 on my desktop.

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
```
search your.netprovider.net
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
``` Keep this information handy.

Go to the desktop and put the exact information in the file /etc/resolv.conf on the desktop using your favorite editor.
```
sudo gedit /etc/resolv.conf
``` It is probable that this file is currently blank. In any case, completely erase the contents if there are any and type in exactly what is shown in the same file on your laptop then save.

Okay. Time to test. Open firefox and type something simple in the address bar like "www.google.com"

If we did everything right it will work, but we are not quite done.

The resolv.conf file will be regenerated on the desktop every time you reboot. Unless you enjoy recreating the file each time, there is one more step remaining.

While the current internet connection is working, with all the [extra repositories enabled]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), fire up synaptic or apt-get install **resolvconf**

Once that is installed
```
cp /etc/network/interfaces /etc/network/interfaces_backup
gedit /etc/network/interfaces
``` and add the following to that file under the heading shown using the information from your current, working /etc/resolv.conf:
```
 iface eth0 inet static
  dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
  dns-search your.netprovider.net  
``` This will automatically create your (correct) /etc/resolv.conf file every time you reboot.

EDIT: This is really old now, so I'm officially deprecating it and releasing it into the wild. If anyone is interested in submitting an updated version (that you have the time and ability to support), please feel free to do so. I am not using this setup at the moment, and don't have the hardware available to play around with at the moment, so I can't write an update or give good support.

---

### Post by thorosius on 2007-03-28
I have a problem with connection sharing. I have a desktop PC with WinXP SP2 updated uptill december 2006. This PC is able to access the internet. I want to share this internet connection with my Laptop which has ubuntu edgy. My questions: 

1. Is the configuration you mentioned for your desktop alright if I use it in my Laptop.
2. Is any other configuration necessary for windows or ubuntu.

---

### Post by matthew on 2007-03-28
> **thorosius said:**
> I have a problem with connection sharing. I have a desktop PC with WinXP SP2 updated uptill december 2006. This PC is able to access the internet. I want to share this internet connection with my Laptop which has ubuntu edgy. My questions: 

1. Is the configuration you mentioned for your desktop alright if I use it in my Laptop.
2. Is any other configuration necessary for windows or ubuntu.I haven't used Windows in over two years so I am woefully unqualified to help with that side of things.

I can say that this should work whether a person is using a laptop or desktop in either role. I just named them as I did for convenience.

---

### Post by thorosius on 2007-03-28
No windows for 2 years? Amaizing!
Any way I'll try this. Thanks!

---

### Post by matthew on 2008-01-18
I am afraid I don't have the time to support this thread anymore, so I'm closing it. The info is pretty straightforward though, and a person should be able to adapt it for newer Ubuntu releases than I used when I wrote it, as well as in different configurations.

If anyone that has the knowledge and time to answer questions and wants to rewrite/update this and submit it as a new How To, you have my blessing.

---

