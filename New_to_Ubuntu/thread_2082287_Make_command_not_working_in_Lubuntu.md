---
title: "Make command not working in Lubuntu"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by cforput on 2012-11-08
I'm trying to update my wireless driver in lubuntu and I'm following some directions blindly because I have no idea what they are doing but after I download and unzip the wireless driver file the next step is to run Make (after switching to the location where all the drivers files unzipped). 

I first do sudo su then I run Make and get the following errors

Entering directory '/usr/src/linux-headers-3.5.0-17-generic' /usr/src/linux-headers-3.5.0-17-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support. 

gcc: Command not found

I then get an Error 127 and an Error 2. 

Sorry I can't cut and paste the exact same error message because I'm using a different computer to write my post - wireless is not working on the other computer. Hence the need to try and update the driver files.

Any help would be greatly appreciated and please know that I'm a newbie so any real technical jargon will go right over my head

---

### Post by mikewhatever on 2012-11-09
> **cforput said:**
> I'm trying to update my wireless driver in lubuntu and I'm following some directions blindly because I have no idea what they are doing but after I download and unzip the wireless driver file the next step is to run Make (after switching to the location where all the drivers files unzipped). 


That's usually a bad idea. Anyway, can you, at least, provide the link to the howto you are trying to follow, and also the wireless hardware specs.

---

### Post by cforput on 2012-11-09
Hardware specs are a realtek RTL8188ce which when I started researching my problem it looks like I'm not alone. There are several folks saying the same thing. Their wireless is flaky so I thought I would try the latest drivers. My laptop is almost 2 years old and I was hoping that by updating the drivers my problem would go away. The directions I'm trying to follow are in the readme file that comes with the driver. Here is a copy / paste of it.

I'm using the steps in section II

**************************************************************
Release Date: 2012-05-09, ver 0006
Realtek Linux mac80211 based driver:
   --This driver supports follwing RealTek PCIE Wireless LAN NICs:
	RTL8188CE/RTL8192CE
	RTL8191SE/RTL8192SE
	RTL8192DE
	RTL8723AE

   --This driver supports follwing Linux OS:
 	Fedora Core
	Debian
	Mandriva
	Open SUSE
	Gentoo
	MeeGo
	android 2.2 (froyo-x86), etc.

   --This driver supports follwing kernel versions:
	1) kernel version >=2.6.35
	   you can build & install drvier use II. 


	2) kernel version [2.6.24, 2.6.34]
	   you can build & install drvier use III. 


========================================================================================
		I. Component 
========================================================================================
The driver is composed of several parts:
	1. Firmare to make nic work
           1.1 firmare/rtlwifi

	2. Module source code
	   2.1 ./*
	   2.2 rtl8192ce
	   2.2 rtl8192se
	   2.2 rtl8192de
	   2.2 rtl8723ae
	
	3. Script to build the modules
	   3.1 Makefile 

	4. compat-wireless
	   4.1 compat-wireless*.tar.bz2
	   4.2 compat

========================================================================================
		II. Compile & Installation & uninstall
========================================================================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. Compile driver from the source code 
	   make

	3. Install the driver to the kernel
	   make install
	   reboot

	4. uninstall driver
	   make uninstall

========================================================================================
		III. Compile & Installation & uninstall [2.6.24, 2.6.34]
========================================================================================
We don't support kernel 2.6.24-2.6.34 directly, Because there are
lots of issues in mac80211 from kernel 2.6.24-2.6.34,
So we suggest you to use the latest kernel >= 2.6.35.

but if you want to use our driver in an old kernel,
you can use compat-wireless. this methord can support all kernel
versions higher than 2.6.24, and you can use all functions
of our driver like you use it in the latest kernel version.

You can get more informations of compat-wireless from:
[http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)

you should use the following commands to Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. install compat-wireless driver
	   ./compat/script/compat-install.sh
		 
	3. reboot
	   reboot

	4. uninstall driver
	   ./compat/script/compat-uninstall.sh

	5. you can get more information form follwing webset for how to use compat-wireless:
	   [http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)
	   
NOTICE:
	1. Maybe you can not use other vendors wireless after you install compat wireless,
	   in this situation, you can uninstall compat-wireless use step 4 to recover it.

	2. This install methord can support all versions of kernel, not just 2.6.24-2.6.34,
	   you can also use it in the kernel higher than 2.6.35.
========================================================================================
				IV. Start Up Wireless
========================================================================================
You can use two methord to start up wireless:

	1. Install driver like II. and reboot OS, Wireless will be brought 
	   up by GUI, such as NetworkManager

	2. If Wireless is not brought up by GUI, you can use: 
	   ifconfig wlan0 up 

	   Note: some times when you have two wireless NICs on your computer,
		 interface "wlan0" may be changed to "wlan1" or "wlan2", etc. 
		 So before "ifconfig wlan0 up", you can use "iwconfig" to check
		 which interface our NIC is.

	   Note: Don't try to down driver by "ifconfig wlan0 down" when 
		 NetworkManager id opened, because NetworkManager will up
		 driver automatically. 

========================================================================================
				V. Wireless UI & NetworkManager 
========================================================================================
	1. All latest distributions have UI & NetworkManager to like with AP.
	   And it's more easy to link with AP than commandline,
	   So we suggest you use UI to link with AP.

	2. Don't try to like with AP use commandline with UI or NetworkManager opened.

	3. If you still used commandline to link with AP, Please check if
	   NetworkManager & wpa_supplicant is killed by follwing command:

		ps -x | grep NetworkManager
		ps -x | grep wpa_supplicant

	4. Follwing commandlines(V-VII) are all used under Linux without UI. 

========================================================================================
				VI. Set wireless lan MIBs  
========================================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

	1. Current driver supports "iwlist" to show the device status of nic

	   iwlist wlan0 [parameters]

	   you can use follwing parameters:

        	parameter explaination      	[parameters]    
       		-----------------------     	-------------   
        	Show available chan and freq	freq / channel  
        	Show and Scan BSS and IBSS 	scan[ning]          
        	Show supported bit-rate         rate / bit[rate]        

	   For example:
		iwlist wlan0 channel
		iwlist wlan0 scan
		iwlist wlan0 rate

	2. Driver also supports "iwconfig", manipulate driver private ioctls, 
	   to set MIBs.

	   iwconfig wlan0 [parameters] [val]

	   you can use follwing parameters:

	   parameter explaination      [parameters]        [val] constraints
        	-----------------------     -------------        ------------------
        	Connect to AP by address    ap              	[mac_addr]
        	Set the essid, join (I)BSS  essid             	[essid]
        	Set operation mode          mode                {Managed|Ad-hoc}
        	Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

	   For example:
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
		iwconfig wlan0 essid "ap_name"
		iwconfig wlan0 mode Ad-hoc
		iwconfig wlan0 essid "name" mode Ad-hoc
		iwconfig wlan0 key 0123456789 [2] open
		iwconfig wlan0 key off
		iwconfig wlan0 key restricted [3] 0123456789
        	iwconfig wlan0 key s:12345

	   Note: There are two types of key, "hex" code or "ascii" code. "hex" code
	        only contains hexadecimal characters, "ascii" code is consist of 
                "ascii" characters. Assume the "hex" code key is "0123456789", you 
                are suggested to use command like this "iwconfig wlan0 key 0123456789". 
                Assume the "ascii" code key is "12345", you should enter command 
                like this "iwconfig wlan0 key s:12345".

           Note: Better to set these MIBS without GUI such as NetworkManager and be 
	        sure that our nic has been brought up before these settings. WEP key
	        index 2-4 is not supportted by NetworkManager.

========================================================================================
				VII. Getting IP address (For OS without UI) 
========================================================================================
Before transmit/receive data, you should obtain an IP address use one of
the follwing method: 

	1. static IP address:

		ifconfig wlan0 IP_ADDRESS

	2. dynamic IP address using DHCP:
	   	
		dhclient wlan0
		

========================================================================================
				VIII. WPAPSK/WPA2PSK (For OS without UI) 
========================================================================================
Wpa_supplicant helps you to link with WPA/WPA2(include WPA Enterprise) AP, 
in Linux with NetworkManger & UI, UI will help you to link with AP, 
But if there is no UI & Networkmanger in your Linux, you can use 
follwing method to link with WPA/WPA2 AP. 
	
	1. we suppose that your Linux have installed wpa_supplicant & 
	   kernel build with WIRELESS_EXT, In fact, lots of distributions
	   have done like this.

	   But if some distribution not install wpa_supplicant,
	   please download wpa_supplicant from webset and install it.

	2. Edit wpa1.conf to set up SSID and its passphrase.
	   For example, the following setting in "wpa1.conf" 
	   means SSID to join is "BufAG54_Ch6" and its 
	   passphrase is "87654321".

	   network={
			ssid="BufAG54_Ch6"
			#scan_ssid=1 //see note 3
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		  }

	   You can download wpa_supplicant and read wpa_supplicant.conf 
	   for more examples.

	3. Execute WPA supplicant:

	   wpa_supplicant -D wext -c wpa1.conf -i wlan0 

	4. To see detailed description for driver interface and wpa_supplicant, 
	   please type: 

	   man wpa_supplicant

---

### Post by qyot27 on 2012-11-09
It's not finding gcc because you haven't installed gcc.
```
sudo apt-get install build-essential
```
will do it. You may need some other pieces that aren't immediately obvious (like some of the autotools-related things, or certain -dev packages), but those can be worked out later.



Alternately, and on the off chance, it may be running into problems because you're running this under su and there could be some issues with the user profile recognizing things.  But I wouldn't immediately jump to that conclusion.

---

### Post by squakie on 2012-11-09
+1 on build-essential.  It's a meta package so it installs many things needed to "make" in ubuntu - including the gcc compiler.

---

### Post by oldos2er on 2012-11-09
Which wireless device do you have? You're running the 3.5.0-17 kernel, but the instructions you posted are for 2.6x kernels.

---

### Post by cforput on 2012-11-10
I have the RTL8188ce on a Toshiba Satellite L655-s5150. I don't know anything about kernels. I just went to Realtek's website and downloaded the latest driver and tried to install it. 

I'll try installing gcc and try again. 

Thanks. I'll post what happens.

---

### Post by MG&amp;TL on 2012-11-10
> **cforput said:**
> I have the RTL8188ce on a Toshiba Satellite L655-s5150. I don't know anything about kernels. I just went to Realtek's website and downloaded the latest driver and tried to install it. 

I'll try installing gcc and try again. 

Thanks. I'll post what happens.

You might want to read around the topic a little. You don't have to be an expert, but a little knowledge is a substantial improvement on no knowledge.

---

### Post by oldos2er on 2012-11-10
> **cforput said:**
> I have the RTL8188ce on a Toshiba Satellite L655-s5150. I don't know anything about kernels. I just went to Realtek's website and downloaded the latest driver and tried to install it. 

I'll try installing gcc and try again. 

Thanks. I'll post what happens.

Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)

---

### Post by 0011235813 on 2012-11-10
Don't be surprised if it doesn't work - the instructions clearly state that it's for kernel 2.6 and is made for Fedora & SuSe.

That said, it might still work.

If it doesn't, I recommend you buy an external wifi and connect it via USB. They don't cost much (<£20 last I checked) though make sure you buy one that states its compatible with Linux.

---

