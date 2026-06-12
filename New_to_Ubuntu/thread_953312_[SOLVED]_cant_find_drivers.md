---
title: "[SOLVED] cant find drivers"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Arthur Millar on 2008-10-20
realtek RTL8101E ethernet drivers

Foxconn onboard LAN problem
DMBIT after reboot no network!??!?!!

hell YEAH BABY {problem solved}  Coming to you LIVE from HARDY 8.04
just needed the right driver from realtek
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false) 
<readme>

<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8101E and RTL8102E(L), the Fast Ethernet controller with PCI-Express interface.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports linux kernel 2.4.20 and latter.
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8101-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8101-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8101.ko	(or r8101.o for kernel 2.4.x)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8101
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX

		,where X=0,1,2,...

  
<Set the network related information>
	1. Set manually
		a. Set the IP address of your machine.

			# ifconfig ethX "the IP address of your machine" 

		b. Set the IP address of DNS.

		   Insert the following configuration in /etc/resolv.conf.
		
			nameserver "the IP address of DNS"

		c. Set the IP address of gateway.

			# route add default gw "the IP address of gateway"

	2. Set by doing configurations in /etc/sysconfig/network-scripts
	   /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
	   /ifcfg-ethX for SuSE. There are two examples to set network 
	   configurations.

		a. Fixed IP address:
			DEVICE=eth0
			BOOTPROTO=static
			ONBOOT=yes
			TYPE=ethernet
			NETMASK=255.255.255.0
			IPADDR=192.168.1.1
			GATEWAY=192.168.1.254
			BROADCAST=192.168.1.255

		b. DHCP:
			DEVICE=eth0
			BOOTPROTO=dhcp
			ONBOOT=yes	

<Modify the MAC address>
	There are two ways to modify the MAC address of the NIC.
	1. Use ifconfig:

		# ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

	2. Use ip:

		# ip link set ethX address YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

	1. Force the link status when insert the driver.

	   If the user is in the path ~/r8101, the link status can be forced 
	   to one of the 4 modes as following command.

		# insmod ./src/r8101.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8101.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	RTL8101E and RTL8102E do not support Jumbo Frame.

---

### Post by eternalnewbee on 2008-10-20
> **Arthur Millar said:**
> realtek RTL8101E ethernet drivers

What do you exactly need?

---

### Post by Arthur Millar on 2008-10-20
i just installed 8.04 on my system 
every thing seems ok except i have no internet access 
i have tried to setup my network with no luck 
Hardware testing shows my eth0, but network tools only shows loopback 
i suspect its the driver

---

### Post by Arthur Millar on 2008-10-20
I tried another NIC 
same problem 
What am i doing wrong?>

---

### Post by eternalnewbee on 2008-10-20
> **Arthur Millar said:**
> i just installed 8.04 on my system 
every thing seems ok except i have no internet access 
i have tried to setup my network with no luck 
Hardware testing shows my eth0, but network tools only shows loopback 
i suspect its the driver

OK. Normally Ubuntu automatically detects your internet connection.
There should be an icon in your panel.
Also, check if if your hardware is properly connected.
Good luck.
( let me know how it goes ).

---

### Post by Bucky Ball on 2008-10-20
If you mean realtek RTL8101LE ethernet drivers? Could you run:

**lspci**

... in a terminal and identify what it says the card is there, please? Should be near the bottom.

Also, try this:

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

You need to have a driver installed for the card. You may need to stick in an ethernet cable from your router, reboot and see if you can get online that way to perform the instructions. You need to get the driver if it isn't there already. You could try:

**locate rtl8187**

... in a terminal and see if it is there. If so, skip down the page a bit.

---

### Post by Arthur Millar on 2008-10-20
lspci shows my NIC is there RTL8101E(rev 01)
still nothing 
the lights on my router and my nic are on
i have set everything to roaming for now

---

### Post by Bucky Ball on 2008-10-20
Okay, open:

System->Admin->Network

Unlock and choose your wireless connection then properties. In there, untick 'Enable Roaming' and set 'Configuration' to 'Auto Configuration (DHCP). This may work straight away or you may have to try restarting or just logging in again. Also, set an ESSID and security on the router and make sure they match in on the computer in the 'Network' window also. Let us know how you go.

Also, do you get any networks available when you type:

```
sudo iwlist scan
```

... into a terminal?

---

### Post by Arthur Millar on 2008-10-20
thanks bucky ball 
but its a wired connection 
i have tried setting the network to dhcp with a reboot 
just says manual network settings but no connection

---

### Post by Bucky Ball on 2008-10-20
> **Arthur Millar said:**
> thanks bucky ball 
but its a wired connection 
i have tried setting the network to dhcp with a reboot 
just says manual network settings but no connection

Wired? Hmm. That has me a bit stumped. Your RTL8101E is a wireless card and we should be able to get that to work if you could get online on that machine. Catch22. I'll think about that. There is no firewall preventing connection?

---

### Post by Arthur Millar on 2008-10-20
looks like the driver installed on my 8.04 is for a wireless card ???
im using an onboard LAN on a foxconn a6vmx
the manual states its realtek 
checking driver disks

---

### Post by Arthur Millar on 2008-10-20
apon further investigating i found the drivers for vista to be 
realtek 8169
realtek 8168
and 8101E

---

### Post by Arthur Millar on 2008-10-20
PLease help i cant get my LAN to work GRRRR 
why why why 
[http://ubuntuforums.org/images/icons/icon9.gif](http://ubuntuforums.org/images/icons/icon9.gif)

---

### Post by Arthur Millar on 2008-10-20
> **Bucky Ball said:**
> Wired? Hmm. That has me a bit stumped. Your RTL8101E is a wireless card and we should be able to get that to work if you could get online on that machine. Catch22. I'll think about that. There is no firewall preventing connection?

[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&ProdID=19](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&ProdID=19) 

this page says its not wireless but PCI express

---

### Post by Arthur Millar on 2008-10-20
> **eternalnewbee said:**
> 
( let me know how it goes ).
i found the driver i need its r8101-1.009.00.tar.bz2 
i put it on a memory stick and transfered it to the desktop 
from there i extracted the tarball to the desktop 
im now sitting at makefile ahem hew do i use that?

---

### Post by galileon on 2008-10-20
u need to install the gcc toolchains...
<code>
sudo apt-get install build-essentials autoconf
</code>
edit:
then try:
<code>
make
</code>

---

### Post by Arthur Millar on 2008-10-20
> **galileon said:**
> u need to install the gcc toolchains...
<code>
sudo apt-get install build-essentials autoconf
</code>
edit:
then try:
<code>
make
</code>

thanks 
i got as far #insmod .src/etc....
im just not sure which kernel to install for, is it 2.6.x or 2.4.x ?
im using hardy 8.04

---

### Post by Arthur Millar on 2008-10-20
so i find the driver install it BINGO connection
then i reboot and -NOTHING- no network 
driver is installed but nada 
now it wont even boot just haning at the loading screen

---

### Post by Arthur Millar on 2008-10-20
> **Arthur Millar said:**
> realtek RTL8101E ethernet drivers

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.



how do keep that r8196 driver off my pc 
i have tried rmmod and it works until i reboot 
cant find the modprobe.conf file in ubuntu

---

### Post by galileon on 2008-10-20
> **Arthur Millar said:**
> how do keep that r8196 driver off my pc 
i have tried rmmod and it works until i reboot 
cant find the modprobe.conf file in ubuntu

sudo nano /etc/modprobe.d/blacklist

---

### Post by Arthur Millar on 2008-10-20
> **galileon said:**
> sudo nano /etc/modprobe.d/blacklist

thanks but what then i tried 
#disable r8169 driver
blacklist r8169
did a rmmod r8169 
reboot 
still there!!

---

### Post by galileon on 2008-10-20
> **Arthur Millar said:**
> thanks but what then i tried 
#disable r8169 driver
blacklist r8169
did a rmmod r8169 
reboot 
still there!!

wierd...you can try to locate r8169 then mv it into r8169.unused so that the system can't fint the driver?

---

### Post by Arthur Millar on 2008-10-20
> **galileon said:**
> wierd...you can try to locate r8169 then mv it into r8169.unused so that the system can't fint the driver?

how?> sorry

---

### Post by Arthur Millar on 2008-10-20
could i add blacklist r8169 to blacklist-oss?

---

### Post by Arthur Millar on 2008-10-20
i am trying to replace a default driver on hardy 8.04 using rmmod 
it seems to work fine until i reboot 
sudo rmmod r8169
when i try the second time 
ERROR: module does not exist in /proc/modules 
when i reboot the module is still there 
the documentation i was given says if rmmod does not work 
edit modprobes.conf(which does not exist)
i aslo tried the blacklist files in etc/modprobes.d
#i hate you r8169
blacklist r8169
save 
reboot
still there 
r8169 is like the thorn in my side 
i had the net up and running untill the reboot
so i know the r8101-1 is the driver i need
my net is up but i dare not reboot

---

### Post by Bucky Ball on 2008-10-20
```
#i hate you r8169
blacklist r8169
```

You have entered that in /etc/modprobe.d/blacklist? Make sure you are opening that file by typing:

```
sudo nano /etc/modprobe.d/blacklist
```

Without the sudo, the changes won't stick. :)

---

### Post by Arthur Millar on 2008-10-20
> **Bucky Ball said:**
> 
You have entered that in /etc/modprobe.d/blacklist? Make sure you are opening that file by typing:

```
sudo nano /etc/modprobe.d/blacklist
```

Without the sudo, the changes won't stick. :)
I am in root to avoid Password's for now.
i have the blacklist file in the terminal window, 
is there a difference if i open it with **gedit?** 
how do i save the changes i make to this file in terminal mode and what changes should i be making? 
is the
[code]#
blacklist r8169[code/] 
correct?

---

### Post by Bucky Ball on 2008-10-20
> **Arthur Millar said:**
> 
is there a difference if i open it with **gedit?** 

Nope.

> **Arthur Millar said:**
> how do i save the changes i make to this file in terminal mode and what changes should i be making? 
is the
```
#
blacklist r8169
```correct?

Yep, as long as that is the driver you are trying to blacklist. From memory it is, but I would have to recheck. If you hit ctl/x in nano in the terminal, that will ask if you want to save changes. Answer 'y' to both questions and the file will close. Reopen the file and make sure it is saved correctly. Another thing to do would be to run:

```
echo -e "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist
```That is a guess but might work. Also:
```
locate r8169
```... in a terminal and see where else it might be residing. Which guide did you end up using?

---

### Post by Arthur Millar on 2008-10-20
> **Bucky Ball said:**
>  Which guide did you end up using?

below is the readme that came with my driver download

im still sitting at the terminal window with GNU nano 
i have added 
# i hate you r8169
blacklist r8169 
at the end 
How do i save that and exit from terminal with those settings 
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

how??


<Linux device driver for Realtek Ethernet controllers>

	This is the Linux device driver released for RealTek RTL8101E and RTL8102E(L), the Fast Ethernet controller with PCI-Express interface.

<Requirements>

	- kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
	- For linux kernel 2.4.x, this driver supports linux kernel 2.4.20 and latter.
	- compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8101-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8101-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8101.ko	(or r8101.o for kernel 2.4.x)

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8101
		# ifconfig -a

	If there is a device name, ethX, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate 
	the ethX.

		# ifconfig ethX

		,where X=0,1,2,...

  
<Set the network related information>
	1. Set manually
		a. Set the IP address of your machine.

			# ifconfig ethX "the IP address of your machine" 

		b. Set the IP address of DNS.

		   Insert the following configuration in /etc/resolv.conf.
		
			nameserver "the IP address of DNS"

		c. Set the IP address of gateway.

			# route add default gw "the IP address of gateway"

	2. Set by doing configurations in /etc/sysconfig/network-scripts
	   /ifcfg-ethX for Redhat and Fedora, or /etc/sysconfig/network
	   /ifcfg-ethX for SuSE. There are two examples to set network 
	   configurations.

		a. Fixed IP address:
			DEVICE=eth0
			BOOTPROTO=static
			ONBOOT=yes
			TYPE=ethernet
			NETMASK=255.255.255.0
			IPADDR=192.168.1.1
			GATEWAY=192.168.1.254
			BROADCAST=192.168.1.255

		b. DHCP:
			DEVICE=eth0
			BOOTPROTO=dhcp
			ONBOOT=yes	

<Modify the MAC address>
	There are two ways to modify the MAC address of the NIC.
	1. Use ifconfig:

		# ifconfig ethX hw ether YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

	2. Use ip:

		# ip link set ethX address YY:YY:YY:YY:YY:YY

	   ,where X is the device number assigned by Linux kernel, and
		  YY:YY:YY:YY:YY:YY is the MAC address assigned by the user.

<Force Link Status>

	1. Force the link status when insert the driver.

	   If the user is in the path ~/r8101, the link status can be forced 
	   to one of the 4 modes as following command.

		# insmod ./src/r8101.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

		,where
			SPEED_MODE	= 100	for 100Mbps
					= 10	for 10Mbps
			DUPLEX_MODE	= 0	for half-duplex
					= 1	for full-duplex
			NWAY_OPTION	= 0	for auto-negotiation off (true force)
					= 1	for auto-negotiation on (nway force)
		For example:

			# insmod ./src/r8101.ko speed=100 duplex=0 autoneg=1

		will force PHY to operate in 100Mpbs Half-duplex(nway force).

	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off (true force)
						= on	for auto-negotiation on (nway force)

		For example:
		
			# ethtool -s eth0 speed 100 duplex full autoneg on

		will force PHY to operate in 100Mpbs Full-duplex(nway force).

<Jumbo Frame>
	RTL8101E and RTL8102E do not support Jumbo Frame.

---

### Post by Bucky Ball on 2008-10-20
Looks good. This part:

<Set the network related information>

... you can set up with System->Administration->Network. You are getting stuck on the rmmod part and it is not removing the driver? Have you done the steps in my last post?

---

### Post by Arthur Millar on 2008-10-20
> **Bucky Ball said:**
> Looks good. This part:

<Set the network related information>

... you can set up with System->Administration->Network. You are getting stuck on the rmmod part and it is not removing the driver? Have you done the steps in my last post?

ran nano 
added 
blacklist r8169 
saved rebooted now my system is offline again 
*sigh 
i suspect that r8101 has been black listed as removing r8169 and r8101 and reinstalling has no effect must prceed to reinstall 
ubuntu. :S 
im going to go and have a boxing session 
blacklist did not work 
r8169 is my undoing

---

### Post by Bucky Ball on 2008-10-20
Not quite but pretty close. Someone else might chime in with a fix and in the meantime I'll keep thinking. Have fun.

Hang on, what about this, from this page:

[http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy)


[]("http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy")

---

### Post by Arthur Millar on 2008-10-20
im back and feeling better 
now 
i have figured a way around all this crap for now i just rmmod r8169 
disable r8101 by system>admin>hardeware testing 
re enable it, and it works. 
at least i can get online if i need to for now  
but i still need to kill r8169 FOREVER to be able to boot online

---

### Post by galileon on 2008-10-20
> **Arthur Millar said:**
> im back and feeling better 
now 
i have figured a way around all this crap for now i just rmmod r8169 
disable r8101 by system>admin>hardeware testing 
re enable it, and it works. 
at least i can get online if i need to for now  
but i still need to kill r8169 FOREVER to be able to boot online

the dirtiest hack i've ever used for such things is to sudo nano /etc/init.d/gdm and stick rmmod stuff near the top...

i know its ugly, but it saves the time troubleshooting!

---

### Post by Arthur Millar on 2008-10-20
everything seems to work now that i installed all the updates
i uninstalled the r8101 driver in prep for reboot after updates finished 
when i came back r8169 was gone! :)
:guitar:
reinstalled r8101 
rebooted and presto 
and just for good measure I rebooted again to see if all was well 
thanks all 
peace

---

### Post by Bucky Ball on 2008-10-20
Your welcome. Excellent news! ... And now for some fun. \\:D/

---

