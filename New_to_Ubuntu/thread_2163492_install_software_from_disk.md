---
title: "install software from disk"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by darylangela on 2013-07-18
I need help installing wireless network adapter software onto a Ubuntu 12.04 32 bit system. readme notes are as follows:				Software Package - Component ===============================================================================
	1. readme.txt
	
	2. Release Notes Document
	
	3. driver source code


		3.1 Makefile - to build the modules	   


		3.2 Script and configuration for DHCP:
 	   "wlan0dhcp"
 	   "ifcfg-wlan0"
	   
		3.3 Example of supplicant configuration file:
			"wpa1.conf"


		3.4 Script to run wpa_supplicant
			"runwpa"


	4. wpa_supplicant-0.6.9.tar.gz - the tool help the wlan network to communicate under the 
			protection of WPAPSK mechanism (WPA/WPA2)
	
	5. wpa_supplicant-0.6.9_wps_patch.tar.gz - for wps patch
	
==============================================================================================
			User Guide(1) - connecting wireless networking using "Network Manager" GUI utility
========================================
I've tried <sudo apt-get install wpa_supplicant> to which I get the reply unable to find package. Please add meat to the bare bones of this readme so that even a newbie like me can implement. Step by step command line prompts please. Option 2 is command line install, another 3 1/2 pages of the readme, "network manager" is much more my speed.

Daryl

---

### Post by oldos2er on 2013-07-18
*sudo apt-get install whatever* looks for an internet connection, if possible use a wired connection for this. Could you tell us the make/model of your wireless device?

---

