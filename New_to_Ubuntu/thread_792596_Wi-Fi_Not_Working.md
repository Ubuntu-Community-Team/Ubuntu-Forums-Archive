---
title: "Wi-Fi Not Working"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by mbarvian on 2008-05-13
Hi guys, I just reinstalled Ubuntu on my PC and loving every minute of it.  But the thing that's dragging me down is the fact that my wireless internet at my house is not listing in the connections option.  I already started another post about this, and I think it's because of my Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter.

Are there any fixes or drivers I need to install to get this working?

---

### Post by mbarvian on 2008-05-13
any?

---

### Post by Bubba64 on 2008-05-13
When you started using the usb originally didn´t you need a code to get it working. Also are you getting a signal with the network manager with manual configuration or roaming.

---

### Post by subzero316 on 2008-05-13
try modprobe,
```
modprobe r8187
```

---

### Post by mbarvian on 2008-05-13
> **Bubba64 said:**
> When you started using the usb originally didn´t you need a code to get it working. Also are you getting a signal with the network manager with manual configuration or roaming.
No, in the network manager, wireless internet did not even show up.
> **subzero316 said:**
> try modprobe,
```
modprobe 8187
```
what will this do?

---

### Post by nicedude on 2008-05-13
To get my home wifi working properly I removed the network manager & gnome network manager and replaced them with Wicd which you can just google "ubuntu wicd" and find links on how to add to your sources list and then install with synaptic. 

The WICD is working fine with my wired lan and with my wireless lan. It also had ability to set up multiple location setting profiles for if you use your wifi with multiple connection setups. While network manager supposedly does that as well it wouldn't work for me.

This solution will only work though if your wifi drivers are working already though.

---

### Post by subzero316 on 2008-05-13
modprobe will add that module to your kernal...

btw u get the drivers online for realtek at [<<Realtek Site>>]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true").......

---

### Post by mbarvian on 2008-05-13
ok, I'll try that. How do I install tar.gz files?

---

### Post by subzero316 on 2008-05-13
Itz compressed....to uncompress it use,
```
tar -xzf filename.tar.gz
```

It will have the instllation istructions in it.

---

### Post by mbarvian on 2008-05-13
> **subzero316 said:**
> Itz compressed....to uncompress it use,
```
tar -xzf filename.tar.gz
```

It will have the instllation istructions in it.

great, and do you think this will fix my problem by just installing these drivers?

---

### Post by subzero316 on 2008-05-13
> **mbarvian said:**
> great, and do you think this will fix my problem by just installing these drivers?
considering the fact that is the official driver site it will u must unzip then install it.


First did you try
```
modprobe r8187
```

That`ll mostly get it working........


only if that doesnt work try  d/l the driver

---

### Post by mapes12 on 2008-05-13
Hi

This post may also be of assistance:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by mbarvian on 2008-05-13
> **subzero316 said:**
> considering the fact that is the official driver site it will u must unzip then install it.


First did you try
```
modprobe r8187
```

That`ll mostly get it working........


only if that doesnt work try  d/l the driver

so first I jus type that in to the command prompt and see what happens?

---

### Post by mbarvian on 2008-05-13
> **subzero316 said:**
> considering the fact that is the official driver site it will u must unzip then install it.


First did you try
```
modprobe r8187
```

That`ll mostly get it working........


only if that doesnt work try  d/l the driver

OK, I tried the modprobe and it didn't work, but I have absolutely no clue how to install the drivers. anything else I can do?

---

### Post by mbarvian on 2008-05-13
anyone?

---

### Post by mbarvian on 2008-05-13
sorry for the multiple posts, but here was the outcome of the modprobe r8187:

FATAL ERROR:

Is there anything else I can try, because I really need the internet to work

---

### Post by mbarvian on 2008-05-13
> **subzero316 said:**
> considering the fact that is the official driver site it will u must unzip then install it.


First did you try
```
modprobe r8187
```

That`ll mostly get it working........


only if that doesnt work try  d/l the driver

How do I install the driver, I don't understand the directions.  Could someone help with this?

---

### Post by mbarvian on 2008-05-14
OK, I put these two things in the terminal, does that help at all?
```
cd /home/maxwell/rtlkdriversblahblahblah
ls
```

This is what it turned out as:
[IMG]http://i231.photobucket.com/albums/ee240/mbarvian/Screenshot-1.png[/IMG]

Now what?

---

### Post by tamoneya on 2008-05-14
in terminal
```
gedit ~/rtl8185_linux_26.1027.0823.2007/readme
```Copy that file into the forums.

---

### Post by mbarvian on 2008-05-15
Here's what it came up as:

```
RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
	rtl8185.tar.gz
	stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
	wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
	wpa_supplicant-0.4.9.tar.gz
    	
    (6)Example of supplicant configuration file
	wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.





< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]
where

        parameter explaination      	[parameters]    
        -----------------------     	-------------   
        Show available chan and freq	freq / channel  
        Show and Scan BSS and IBSS 	scan[ning]          
        Show supported bit-rate         rate / bit[rate]        
        Show Power Management mode      power             

For example:

	iwlist wlan0 channel
	iwlist wlan0 scan
	iwlist wlan0 rate
	iwlist wlan0 power


Driver also supports "iwconfig", manipulate driver private ioctls, to set MIBs.

        iwconfig wlan0 [parameters] [val]
where

        parameter explaination      [parameters]        	[val] constraints
        -----------------------     -------------       	------------------
        Connect to AP by address    ap              		[essid]
        Set the essid, join (I)BSS  essid             		[mac_addr]
        Set operation mode          mode          		{Managed|Ad-hoc}
        Set keys and security mode  key / enc[ryption]          {N|open|restricted|off}


For example:

	iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
	iwconfig wlan0 essid "ap_name"
	iwconfig wlan0 mode Ad-hoc
	iwconfig wlan0 mode essid "name" mode Ad-hoc
	iwconfig wlan0 key 0123456789 [2] open
	iwconfig wlan0 key off
	iwconfig wlan0 key restricted [3] 0123456789

< Getting IP address >
After start up the nic, the network needs to obtain an IP address before transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS" command, or using DHCP.

If using DHCP, setting steps is as below:
	
	(1)connect to an AP via "iwconfig" settings
		iwconfig wlan0 essid [name]	or
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

	(2)run the script which run the dhclient
		./wlan0dhcp
           or 
		dhcpcd wlan0
              	(Some network admins require that you use the
              	hostname and domainname provided by the DHCP server.
              	In that case, use 
		dhcpcd -HD wlan0)



< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK mechanism
	
	(1)Unpack source code of WPA supplicant:
		tar -zxvf wpa_supplicant-0.4.9.tar.gz
		cd wpa_supplicant-0.4.9
	
	(2)Create .config file:
		cp defconfig .config
		
	(3)Edit .config file, uncomment the following line:
		#CONFIG_DRIVER_IPW=y.
		
	(4)Build WPA supplicant:
		make
        
	If make error for lack of <include/md5.h>, install the openssl lib:
	 1. Install the openssl lib from corresponding installation disc:
	    Fedora Core 2/3/4/5/6/7(openssl-0.9.71x-xx),
	    Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
	    Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl),
	    Gentoo(dev-libs/openssl), etc.
	 2. Download the openssl open source package from www.openssl.org, build and install it.
	 
	(5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
	For example, the following setting in "wpa1.conf" means SSID to join is "BufAG54_Ch6" 
	and its passphrase is "87654321".

		network={
			ssid="BufAG54_Ch6"
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		}
	Note: 1. proto=WPA for WPA, proto=RSN for WPA2.
              2. If you want to connect an AP which works under WPA2 mixed mode, you'd better
                 use Realtek customed wpa_supplicant package.
	

	(6)Execute WPA supplicant (Assume 8185 and related modules had been loaded):
		./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &

```

---

### Post by tamoneya on 2008-05-15
the installation section is what you need to pay attention to.  First however install build-essential```
sudo apt-get install build-essential
```Then try this ```
./makedrv
./wlan0up
./wlan0rmv
./wlan0down
./wlan0up
```

---

### Post by mbarvian on 2008-05-15
> **tamoneya said:**
> the installation section is what you need to pay attention to.  First however install build-essential```
sudo apt-get install build-essential
```Then try this ```
./makedrv
./wlan0up
./wlan0rmv
./wlan0down
./wlan0up
```

what does the "./" stand for?

---

### Post by tamoneya on 2008-05-15
it makes it a relative file name:
./ =this directory

---

### Post by mbarvian on 2008-05-15
> **tamoneya said:**
> it makes it a relative file name:
./ =this directory

so should I cd into directory, and then do these commands after installing?

---

### Post by tamoneya on 2008-05-15
yes you should cd into the directory and run the commands to install the driver.

---

### Post by mbarvian on 2008-05-15
> **tamoneya said:**
> yes you should cd into the directory and run the commands to install the driver.

I tried that, but when I went to install get-essential, it said:

```
E: Not found
```

Any suggestions, because after that I tried doing everything else, but it mostly said that it wasn't there.

---

### Post by mbarvian on 2008-05-15
OK, I've found the correct drivers, I was downloading the ones for rtl8185l but i have rtl8187b, which is not listed. So i googled it and found some hacked results, now can anyone help me installing these?  This is what I have so far, I've cd'ed into the directory and ls'd:

[img]http://i231.photobucket.com/albums/ee240/mbarvian/Screenshot-2.png[/img]

---

### Post by mbarvian on 2008-05-16
hey guys, thanks for all the help.  I've started a new thread here:

[http://ubuntuforums.org/showthread.php?p=4973759#post4973759](http://ubuntuforums.org/showthread.php?p=4973759#post4973759)

That's about installing these drivers.

Thanks again

---

