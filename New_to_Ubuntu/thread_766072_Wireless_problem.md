---
title: "Wireless problem"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by jsdieorksw on 2008-04-25
I recently bought a new compaq presario A931NR with Vista, i downloaded ubuntu and made to a boot disk and was able to dual boot vista along with the new OS (ubuntu).  Everything appears fine except for the internet.  I use comcast highspeed wireless but the wireless network wont show up in my available networks when I'm in ubuntu.  the internet works fine when i'm in Vista but not when I'm in ubuntu. There were a few blips while i was installing ubuntu, a message appeared telling me that the security updates didn't install properly and another message about ubuntu running on a partition it's not meant to, i don't know if this has anything to do with it but it might.  Please help me get connected to the internet!

---

### Post by rouge568 on 2008-04-25
You will want to enable the drivers for your wireless card. Go to System>Administration>Hardware_Drivers (if you are using anything other than 8.04, this will be Restricted_Drivers_Manager). Select all the tick boxes and see if it works. You may have to reboot.

Let us know how it goes!

---

### Post by Khalis7 on 2008-04-25
> **jsdieorksw said:**
> I recently bought a new compaq presario A931NR with Vista, i downloaded ubuntu and made to a boot disk and was able to dual boot vista along with the new OS (ubuntu).  Everything appears fine except for the internet.  I use comcast highspeed wireless but the wireless network wont show up in my available networks when I'm in ubuntu.  the internet works fine when i'm in Vista but not when I'm in ubuntu. There were a few blips while i was installing ubuntu, a message appeared telling me that the security updates didn't install properly and another message about ubuntu running on a partition it's not meant to, i don't know if this has anything to do with it but it might.  Please help me get connected to the internet!

Hi..I'll try help you out but first, I need to know what kind of wireless internet adapter and Ubuntu are you using. 
Run this code in terminal:
```
lshw -C network
```
You may access terminal from Application > Accessories > Terminal
Please indicate what is your wireless internet adapter.

---

### Post by jsdieorksw on 2008-04-25
I went into the restriced_drivers_manager and checked the boxes, actually there was only one box to check and it was already checked, it said it was already enabled and in use. I guess I'm gonna have to check the wireless internet adapter later.

---

### Post by jsdieorksw on 2008-04-25
Am I supposed to have more than one box to check? If so, why don't I?

---

### Post by jsdieorksw on 2008-04-25
I have a AR5006EG  802.11 b/g Wireless PCI Express Adapter

---

### Post by jsdieorksw on 2008-04-25
with Ubuntu 7.10

---

### Post by CPImmanuel on 2008-04-25
I have a similar problem with Ubuntu 8.04. I have a Thinkpad T60p which, I believe, has the atheros wireless. However, the system never appears to recognize the existence of the wireless interface. I have put in my windows hard drive, and so I know the wireless card is working and is set to be on in the BIOS. But when I replace the hard windows hard drive with the Ubuntu drive, it does not appear to see anything. I tried the  lshw -C network command, I don;t get anything except paul@paul-laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


I have used the synaptic package manager and let it do its thing of downloading and installing the madwifi driver. But the wireless is not recognized. 
Any ideas?

Thanks., 
Paul

---

### Post by rouge568 on 2008-04-27
Before you continue, update to 8.04. Wireless support is much better, and it may just work. (be sure to re-enable the restricted drivers afterwards)

If you are experiencing slow download, please see my post [here]("http://ubuntuforums.org/showthread.php?p=4793405#post4793405").

---

### Post by jsdieorksw on 2008-04-27
Well I installed 7.10 last week and I don't really want to have to deal with the hassle of upgrading to 8.4. I'm fine with 7.10 for now, as long as I can get my internet up and running. Plus from what I've heard in the ubuntu forums there are still a lot of bugs that have yet to fixed in the new release of Ubuntu.

---

### Post by arvevans on 2008-04-28
jsdieorksw

A number of wireless interface manufacturers have refused to provide technical (i.e. programmer level) information about their products to anybody other than Microsoft.  This makes it nearly impossible for their equipment to be used with other operating systems.  However, for Linux we do have the option of using "ndiswrapper" to run the Microsoft driver.  Installing and configuring ndiswrapper does require that you slow down and  take time to do a bit of research and to learn how to configure this interface tool.  Others can tell you in very general terms how ndiswrapper works, but you need to learn specifically how it works on your particular PC.  Once you have installed and verified ndiswrapper, you can then install the microsoft driver for your WiFi interface hardware.

Start your research by determining if "ndiswrapper" is installed on your Linux computer.  Open a terminal screen and type "ndiswrapper" followed by ENTER.  The text returned may indicate that you need to install ndiswrapper.  If that is the case then it will also tell you how to do that using the "apt-get" command.

Once ndiswrapper is properly installed, you can go to a terminal screen and type "man ndiswrapper" to see the user manual page for this tool.  From reading that you will see how to install the Microsoft type driver for your particular WiFi hardware.  This driver can usually be obtained from the WiFi equipment manufacturer's web page.

Now...before you go to all that trouble...I would like to re-state the suggestion made earlier by **rouge568**, that you upgrade or install the new version 8.04 of Ubuntu Linux.  His advise is sound thinking, and might very well solve your problem.

You seem to have opened multiple threads (complaints) about this on the Ubuntu forum.  That usually has a negative effect on the level of help you might receive.  People on the forum who are willing to help are usually browsing the whole list of active threads, and your adding multiples of the same problem just eats up an unnecessary amount of their valuable time (remember that these are mostly volunteers who are trying to help).  Some threads stop receiving help because the problem has already been solved, the initiator refuses to perform suggested actions, or the user demonstrates an attitude that drives others away from helping him/her.  

[LIST=1]
[*]Before you posted your problem, did you perform a search for that problem using the Ubuntu Forum search engine, to see if this has already been solved? And, did you read any old posts about your particular hardware and your particular problem.
[*]Did you do an Internet search to see of others have already solved this problem with your particular hardware?
[*]Did you look at the list of Linux compatible WiFi hardware to see if your equipment is directly supported?
[*]Have you read the instructions for "ndiswrapper" and understand it in case you have to use the Microsoft type WiFi hardware driver?
[*]Have you installed ndiswrapper and the Microsoft type driver to see if that solves your problem?
[/LIST]

Point to be made here is that you have the responsibility to do some work yourself to resolve your problem.   Linux is a more complex and more capable operating system than what you may have previously been using.  With this capability, it becomes your responsibility to learn how to use it. 

_._

---

### Post by jsdieorksw on 2008-04-28
Well I'd really rather not uninstall 7.10 and re-install 8.4 because it seems like it requires the windows set-up cd and the ubuntu installation cd, neither of which are currently in my possession.  any other solutions would be great

---

### Post by jsdieorksw on 2008-04-28
I've had a couple people mention that ndiswrapper would work but I've been busy trying out the other stuff people said would work so I guess that will be my next stop

---

### Post by jsdieorksw on 2008-04-28
I used the synaptics package manager to install ndiswrapper. after entering: man ndiswrapper i don't know exactly how to read or what to do with the information given, it seems to only product info/description/author. what should i do?

---

### Post by CleverJake on 2009-02-20
I know this is old, but I have this laptop and for posterity, I wanted to say that this issue was solved by updating to the svn trunk of madwifi after September of 2008, and now the main madwifi tree seems to work, though I am running arch linux and not ubuntu right now.

---

