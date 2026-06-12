---
title: "Internet access"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by sunilkumar on 2008-09-03
I have a pc with dual boot Win XP SP3 and Ubuntu Herdy (Latest). Ubuntu installed yesterday only and I am newbie. I was connecting to internet thru my Win XP SP3 with DSL connection. My router is Linksys WAG200G. Can I access internet with Ubuntu as well as Win XP SP3 from same mechine? If I can, how to set up? My computer motherboard is Gigabyte GSL945GCM-S2L. I have network card detected by Ubuntu ith0. But cant setup WAG200G or access to port 192.168.1.1. Why and how?

Please help me.

Regards,
-S-

---

### Post by gandaran on 2008-09-03
how is the connection set up for windows xp? does windows xp dial out/pppoe authentication or your modem router does this, if it's a windows xp setup then use the sudo pppoeconf tool (terminal/console), if it's your modem thats dial's out then it should work with both windows and ubuntu without any intervention.

---

### Post by Gone fishing on 2008-09-03
Yes

You can connect both PCs the Ubuntu and XP machine to the router either via a network cable (your router has 4 ports) or using the wireless. 

I would have thought the router uses dhcp and if you plug in the cable it you should be able to ping 192.168.1.1. If not check the XP machines properties of the network connection and if the XP machine is using 192.168.1.3 use another IP address say 192.168.1.2 (This is set in sysetm>administration>network)

---

### Post by halitech on 2008-09-03
open a terminal and post the output of```
ifconfig
```

---

### Post by sunilkumar on 2008-09-05
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:74:6e:5b   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:4294967284 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:221  
 
eth0:avahi Link encap:Ethernet  HWaddr 00:1d:7d:74:6e:5b   
          inet addr:169.254.5.243  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:221  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1362 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1362 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:68326 (66.7 KB)  TX bytes:68326 (66.7 KB) 
This is my ifconfig command output.
Please help me.

---

### Post by halitech on 2008-09-05
just to clarify, you have 1 machine which dual boots XP and Ubuntu?

---

### Post by HunterA3 on 2008-09-05
Both operating systems should be able to access the network since it's a dual boot machine and Ubuntu sees the NIC installed.

If your router is 192.168.1.1 and you can't see it, you may not have your network configured correctly in Ubuntu.  I thought I saw something about the IP of 169.254.5.243
You can try to get a new IP address, but I suspect that you have to edit your network settings manually to ensure you're getting a valid IP address from your DHCP server and the correct gateway.

---

### Post by sunilkumar on 2008-09-06
Ya, I am using same mechine with Dual boot Win XP and Ubuntu. With Win XP I can surf, but with Ubuntu, I have the above said problem. I am newbie.
> If your router is 192.168.1.1 and you can't see it, you may not have your network configured correctly in Ubuntu. I thought I saw something about the IP of 169.254.5.243
You can try to get a new IP address, but I suspect that you have to edit your network settings manually to ensure you're getting a valid IP address from your DHCP server and the correct gateway.

What shoud I do? How to configure manually? Please guide me step by step.

Thanks in advance.
-S-

---

### Post by Bucky Ball on 2008-09-06
Is your wireless light on? If not, open a terminal and copy and paste this:

**lspci**

Post the result. We need to know what wireless card you have.

Yes you can. The configurations in Ubuntu and Windoze are totally separate. If your card is not up (light on) don't worry about trying to configure anything at this point. (eg when your card is up you will be able to find available networks and you will find your network once you enter the correct SSID and security code, if you are using one). First things first.

---

### Post by sunilkumar on 2008-09-06
Hi I have ethernet network card built in motherbboard Gigabyte GSL945GCM-S2L. I tried sudo pppoeconf command and it scanned eth0, then gave error message "Sorry.. Access concentrator does not respond...Reason may be.." Sorry I dont remember exactly the message and I am away from my home now.

The DSL router is Linksys WAG200G. It connects through Win XP and no problem in surfing. Even I log in to UBUNTU the lights are on and I can browse with WIN XP3 laptop (wireless connection from same WAG200G. (Laptop Win XP and Desktop dual boot Win XP/UBUNTU. Desktop has connected to WAG200G with network code) 

Hope the picture is clear.

Regards,
-S-

---

### Post by Bucky Ball on 2008-09-06
Clearer. Try going to:

**System->Administration->Network**

... from the drop down menu on the top toolbar. Click Unlock and enter your password, click on your connection type (making sure your connection type has a tick next to it - if it isn't ticked, ticking it may just fix the problem simply) and hit properties. Make sure you have the correct details in there. SSID if you are using one (name of the network) and security key if you are using one.

As mentioned, your router should be serving you a DHCP address automatically (sounds like it as XP connects no problem without you fiddling). So make sure configuration is set to **Automatic Configuration (DHCP)** in your Ubuntu network settings.  Are you connecting via cable or dial up?

You need to try this stuff out while you are sitting in front of your computer so let us know how you go. :)

---

### Post by sunilkumar on 2008-09-06
Thanks, that I tried. The connection is DSL not dial-up. I tried with Automatic DHCP and static IP. Both failed. Pinging giving me 0% success rate. 
Do I have to share the internet connection from Win XP first?
I configuered the DSL router WAG200G using Win XP.

What does "Access Concentrato does not respond..." error message mean?

Regards,
-S-

---

### Post by Bucky Ball on 2008-09-06
No, like I said, your windoze install has absolutely nothing to do with this. :)

---

### Post by Bucky Ball on 2008-09-06
Try this. In a terminal, copy and paste:

**sudo pppoe-start**

You will then be asked for your password. See if that makes any difference. Also, your setup maybe timing out too quickly for your connection to be established with your isp.

If no go, the second post from 'mips' on this page has several possible solutions for your problem. Apparently it is a known problem but there are workarounds so don't panic. :)

[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by sunilkumar on 2008-09-06
My **lspci** command output is:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

and
**sudo pppoe -start** command output is:

sudo: unable to resolve host sunil-desktop
[sudo] password for sunil: 
sudo: pppoe: command not found


I am not panic, but.... the "why" question is troubling me.
Thanks for your support dears.


Now can you guide me? Please tell me in details what is the problem. Just for future reference.

Regards,
-S-

---

### Post by Bucky Ball on 2008-09-06
Exactly like this, just copy and paste it from here into your terminal, don't type it:
[B]
sudo pppoe-start

[/B]You shouldn't get output from this command. It should start your connection. If you still get the 'unable to resolve host' error, copy and paste this into your terminal:

**echo "127.0.1.1 sunil-desktop" | sudo tee -a /etc/hosts**

Your card, BTW, is this from the results of your lspci -l command:

Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

You will find a lot of info if you copy and paste that into a search engine and add ubuntu to the end. :)

* Update: Okay, I think we are getting somewhere and I am understanding your problem and setup a bit better. Try these in your terminal one by one if the above didn't work for you. Make sure they are exactly as I have put here - copy and paste them from here is the best option:

**sudo dhclient -r**

That releases your dhcp address. Then

[B]sudo dhclient

[/B]That renews it again. If that didn't work try:[B][FONT=Verdana]

sudo /[/FONT]etc/init.d/network restart

[/B]Any luck?

---

### Post by sunilkumar on 2008-09-06
> Your card, BTW, is this from the results of your lspci -l command:

Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

You will find a lot of info if you copy and paste that into a search engine and add ubuntu to the end.


Ya, it is the output of lspci command.

I will try as you said will ifnorm shortly.

I may succeed with your support.

---

### Post by halitech on 2008-09-06
I'm going to ask a dumb question here, with using a router, unless he's using it as a switch and not an actual router, would not the PPPoE connection be handled by the router and it should be just a standard ethernet connection to the router?

sunilkumar, when you are in windows, do you need to click on anything to get your connection working first before you can go online?

---

### Post by sunilkumar on 2008-09-06
> sunilkumar, when you are in windows, do you need to click on anything to get your connection working first before you can go online?

No Sir. Just open the brower and browse. That is all and simple.

I think your first question is correct. But dont know much since I am not a Techie and very new (2 days only) to Linux.

Regards,
-S-

---

### Post by Bucky Ball on 2008-09-06
Yup, that is the question and it seems windoze xp works fine. Which is why I am figuring just hasn't served a dhcp. What are you thinking, Halitech? After I re-read from the start, you may have noticed I have taken a different tac. Maybe restarting the network could be the simple answer. fire away. :)

---

### Post by halitech on 2008-09-06
> **sunilkumar said:**
> No Sir. Just open the brower and browse. That is all and simple.

I think your first question is correct. But dont know much since I am not a Techie and very new (2 days only) to Linux.

Regards,
-S-

we all started at the same place, just some started before others :)
I want to review some info first as things have gone on over 2 pages and I may have missed something.

1. you have DSL and a wired connection from the computer to the router
2. DHCP seems to be working in XP
3. the light for the connection is on when you are booted into Ubuntu

We have your ifconfig information, can you open a terminal and post the output of ```
cat /etc/network/interfaces
```
also, in the upper right, do you have an icon for network manager? If you do, left click on it and tell us if it says manual configuration or wired network?

> **Bucky Ball said:**
> Yup, that is the question and it seems windoze xp works fine. Which is why I am figuring just hasn't served a dhcp. What are you thinking, Halitech? After I re-read from the start, you may have noticed I have taken a different tac. Maybe restarting the network could be the simple answer. fire away. :)

I'm thinking one of 2 things, something went wonky in the network or the router for some reason doesn't like giving an IP address out to a linux request on some cards. (like my router does) I have 4 systems and 2 of them I have to manually assign addresses where the other 2 work fine. 2 are laptops so I can swap things around and the same devices in different machines will still fail to get an address but work fine on another router.

---

### Post by sunilkumar on 2008-09-06
Previous sudopppoe and other commands output is:

sunil@sunil-desktop:~$ sudo pppoe-start 
sudo: unable to resolve host sunil-desktop 
[sudo] password for sunil: 
sudo: pppoe-start: command not found 
sunil@sunil-desktop:~$ echo "127.0.1.1 sunil-desktop" | sudo tee -a /etc/hosts 

sudo: unable to resolve host sunil-desktop 
[sudo] password for sunil: 
127.0.1.1 sunil-desktop 
sunil@sunil-desktop:~$ sudo dhclient -r 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:1d:7d:74:6e:5b 
Sending on   LPF/eth0/00:1d:7d:74:6e:5b 
Sending on   Socket/fallback 
sunil@sunil-desktop:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:1d:7d:74:6e:5b 
Sending on   LPF/eth0/00:1d:7d:74:6e:5b 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
sunil@sunil-desktop:~$ sudo /etc/init.d/network restart 
sudo: /etc/init.d/network: command not found 
sunil@sunil-desktop:~$ 

Also I found the network  manager on the top right corner of the screen. It was showing a menu like: Automatic configuration (checked) and manual configuration etc. I just check marked on manual configuration. Then it displayed the Admin>Network Tools menu. I entered the ip adress etc that I got from Win XP then again tried to ping. Unfortunately it gave me 0% success (failed). Still tried with firefox for browsing and that also failed.

Expecting your further assistance.
Regards,
-S-

---

### Post by Bucky Ball on 2008-09-06
Sunil, before going any further, could you please open a terminal and paste this in:[B]

echo "127.0.1.1 sunil-desktop" | sudo tee -a /etc/hosts

[/B]That will fix the 'unable to resolve host' problem you keep getting. Then paste in:

**sudo /etc/init.d/networking re****start**

Sorry, my mistake.  :)

---

### Post by sunilkumar on 2008-09-06
Oho! I have done the first command and the below its output:

sunil@sunil-desktop:~$ echo "127.0.1.1 sunil-desktop" | sudo tee -a /etc/hosts
[sudo] password for sunil: 
127.0.1.1 sunil-desktop
sunil@sunil-desktop:~$ 

Now let me reboot to UBUNTU and will tell you the result. Actualy what is the problem? I cant figure out head and tail.

Anyway, I really appreciate you guys patience and cooperative attitude.

Thanks,
-S-

---

### Post by sunilkumar on 2008-09-06
The outputs:

sunil@sunil-desktop:~$ echo "127.0.1.1 sunil-desktop" | sudo tee -a /etc/hosts
[sudo] password for sunil: 
127.0.1.1 sunil-desktop
sunil@sunil-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ppp0: ERROR while getting interface flags: No such device

Plugin rp-pppoe.so loaded.
                                                                         [ OK ]

sunil@sunil-desktop:~$ 

Now what?

---

### Post by Bucky Ball on 2008-09-06
Please post the result of:

[B]sudo nano /etc/network/interfaces

[/B]Then reboot your machine into ubuntu and see if the connection is working. Something may have stuck. Very late here so I need to sleep but will see how you are going tomorrow.I am going to bump this thread as someone else may be able to help while I am sleeping (new ideas). This is unusual problem and doesn't seem to be obvious fix.But there will be a fix somehow![B] \\:D/

*[/B]bump[B] *
[/B]

---

### Post by sunilkumar on 2008-09-06
auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0

auto ppp0






iface eth0 inet ipv4ll

auto eth0



-----------
Basically what is happening? Can you please explain?

---

### Post by Bucky Ball on 2008-09-06
> Basically what is happening? Can you please explain?Trying to figure that out! :)

Ah!

Could you open that same file with:

**sudo gedit /etc/network/interfaces**

```
auto lo
iface lo inet loopback

# iface ppp0 inet ppp
# provider ppp0

# auto ppp0

iface eth0 inet dhcp

iface eth0 inet ipv4ll

auto eth0
```Could you make it look like that please, save it, and then:

                                       ```
sudo /etc/init.d/networking restart
```If nothing changes then, reboot to Ubuntu and let us know. What I think is happening is that your machine is trying to dial or make a connection to  your provider (or wanting to) but your router/modem has already done that, so there is some kind of conflict happening. Possibly trying to connect  on a line that is already in use or something strange. By putting the hash marks next to those lines makes them inactive. If you are running a named network with security, will may need to add those details to this file to0.

Could you possibly post the Windoze network configuration, copy and paste it here also (I just realised you may have been typing your results - should have mentioned to just copy and paste them here to save time, sorry). ;)

---

### Post by sunilkumar on 2008-09-07
No I was not typing. I was copying the output to a text file and pasting it here in the forum. Same your commands also I am copying and pasting there in ubuntu terminal.

Sure I will do this also after reaching home.

Regards,
-S-

---

### Post by sunilkumar on 2008-09-07
sunil@sunil-desktop:~$ sudo gedit /etc/network/interfaces
[sudo] password for sunil: 
sunil@sunil-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:11: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:11: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"                                                               [fail]
sunil@sunil-desktop:~$ 

This was the output.

Now my qeustion.
I tried Network tools>Device>Configure my eth0 before pinging. It says device does not exists or name incorrect.
Is it the problem of my network card driver? When I googled realtek network card (as in the previous output) in ubuntuforum I received information for downloading linux driver from realtek.com and downloaded the driver. So how can I delete the present driver and update the driver with this new downloaded linux driver? If that is the case, Please guide me step by step. 1) To delete the present driver 2) to untar and install this new driver from my flash drive.

Fro your ifnromation: When I gave the below command (searched the forums and got from one link, dont remember)

**sudo vi /etc/ppp/pap-secrets**

It shows my DSL router user ID and password. That means the network card is communicating with router WAG200G. Am I correct? Then what is the problem? Cant get head and tail. Mostly it is DNS problem or somehting like that. Network card (driver) or DSL configuration dont have any problem. Am I right?

As you said > Possibly trying to connect on a line that is already in use or something strange. 

Just giving my two cents.

Regards,
-S-

---

### Post by sunilkumar on 2008-09-07
Another question.

If I reomved completely present Ubuntu installation and re-installed UBUNTU, will it help?

Is it a UBUNTU bug? In that case it will not help me. If I tried the same in another Win XP mechine? If it is bug, it will not help me.

Correct?

---

### Post by germantechie on 2008-09-07
i too have the same problem.
Working fine in Vista but not able to configure in KUbuntu.
i am pasting some snapshots of the network settings that i have by default as an attachment.

i dont know how this ip address stuck by default. also even if edit details to some other ip address or remove it altogether, reopening the network settings lists the previous default settings.

---

### Post by Bucky Ball on 2008-09-07
[QUOTE=sunilkumar]If I reomved completely present Ubuntu installation and re-installed UBUNTU, will it help?[/QUOTE]

Don't think so. You are correct. You are communicating with your router. Sorry, have been busy today so ...

Give me a minute or two to have a think and read your last posts.
:)

---

### Post by Bucky Ball on 2008-09-07
´Device doesn´t exist´ refers to the fact the eth0 doesn´t actually physically exist! All hardware devices in Linx are treated as files. Thus, when you mount a hard drive, you are dealing with the file ´Ýourdrive´ rather than *physical* device /dev/sda (or your first drive - which is *mounted* at /media/Yourdrive  Get it?) If you have a look by opening a terminal and typing:

dir /media

You will see the mount point for all your partitions in there. :)

Same with the card. eth0 is just a name for the device, not the actual *physical* device. In other words, don´t worry, things are fine. Now, as I said, you are pinging your device so close. Try this and simple approach, reboot your machine and tell me how you go. Remember: to get to the file: **sudo gedit /etc/network/interfaces**

```
auto lo
iface lo inet loopback

# iface ppp0 inet ppp
# provider ppp0

# auto ppp0

# iface eth0 inet dhcp

# iface eth0 inet ipv4ll

auto eth0
```

---

### Post by sunilkumar on 2008-09-07
I did that also. Tried to ping and surf. Nothing happened. Then i rebooted the system. Again tried. No result.

I tried system>hardware test. Internet test was ok in it. It gave me a report in xml format. Is it helpfull to you? Then I will cut and paste it here.

Regards,
-S-

---

### Post by sunilkumar on 2008-09-07
<?xml version="1.0" ?>
<system version="1.0">
<hardware>
<hal version="0.5.11rc2">
<device id="10" udi="/org/freedesktop/Hal/devices/computer">
<property name="info.subsystem" type="str">
unknown
</property>
<property name="info.product" type="str">
Computer
</property>
<property name="info.addons" type="list">
<value type="str">
hald-addon-cpufreq
</value>
<value type="str">
hald-addon-acpi
</value>
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.SystemPowerManagement
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --remove-all
</value>
<value type="str">
hal-storage-cleanup-all-mountpoints
</value>
</property>
<property name="info.callouts.session_add" type="list">
<value type="str">
hal-acl-tool --reconfigure
</value>
</property>
<property name="info.callouts.session_inactive" type="list">
<value type="str">
hal-acl-tool --reconfigure
</value>
</property>
<property name="info.callouts.session_remove" type="list">
<value type="str">
hal-acl-tool --reconfigure
</value>
</property>
<property name="info.callouts.session_active" type="list">
<value type="str">
hal-acl-tool --reconfigure
</value>
</property>
<property name="org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures" type="list">
<value type="str">
i
</value>
<value type="str">
i
</value>
<value type="str">

</value>
<value type="str">

</value>
<value type="str">

</value>
<value type="str">
b
</value>
</property>
<property name="org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths" type="list">
<value type="str">
hal-system-power-suspend
</value>
<value type="str">
hal-system-power-suspend-hybrid
</value>
<value type="str">
hal-system-power-hibernate
</value>
<value type="str">
hal-system-power-shutdown
</value>
<value type="str">
hal-system-power-reboot
</value>
<value type="str">
hal-system-power-set-power-save
</value>
</property>
<property name="org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames" type="list">
<value type="str">
num_seconds_to_sleep
</value>
<value type="str">
num_seconds_to_sleep
</value>
<value type="str">

</value>
<value type="str">

</value>
<value type="str">

</value>
<value type="str">
enable_power_save
</value>
</property>
<property name="org.freedesktop.Hal.Device.SystemPowerManagement.method_names" type="list">
<value type="str">
Suspend
</value>
<value type="str">
SuspendHybrid
</value>
<value type="str">
Hibernate
</value>
<value type="str">
Shutdown
</value>
<value type="str">
Reboot
</value>
<value type="str">
SetPowerSave
</value>
</property>
<property name="power_management.is_powersave_set" type="bool">
False
</property>
<property name="power_management.can_suspend_to_disk" type="bool">
True
</property>
<property name="power_management.can_hibernate" type="bool">
True
</property>
<property name="power_management.can_suspend" type="bool">
False
</property>
<property name="power_management.can_suspend_hybrid" type="bool">
False
</property>
<property name="power_management.type" type="str">
acpi
</property>
<property name="power_management.acpi.linux.version" type="str">
20070126
</property>
<property name="power_management.can_suspend_to_ram" type="bool">
False
</property>
<property name="system.hardware.product" type="str">
945GCM-S2L
</property>
<property name="system.hardware.vendor" type="str">
Gigabyte Technology Co., Ltd.
</property>
<property name="system.hardware.uuid" type="str">
00000000-0000-0000-0000-001D7D746E5B
</property>
<property name="system.hardware.primary_video.product" type="int">
10098
</property>
<property name="system.hardware.primary_video.vendor" type="int">
32902
</property>
<property name="system.hardware.version" type="str">

</property>
<property name="system.hardware.serial" type="str">

</property>
<property name="system.formfactor" type="str">
desktop
</property>
<property name="system.chassis.type" type="str">
Desktop
</property>
<property name="system.chassis.manufacturer" type="str">
Gigabyte Technology Co., Ltd.
</property>
<property name="system.firmware.release_date" type="str">
12/27/2007
</property>
<property name="system.firmware.version" type="str">
F5
</property>
<property name="system.firmware.vendor" type="str">
Award Software International, Inc.
</property>
<property name="system.kernel.machine" type="str">
i686
</property>
<property name="system.kernel.version" type="str">
2.6.24-19-generic
</property>
<property name="system.kernel.name" type="str">
Linux
</property>
</device>
<device id="11" udi="/org/freedesktop/Hal/devices/platform_bluetooth">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (bluetooth)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_bluetooth
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="platform.id" type="str">
bluetooth
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/bluetooth
</property>
</device>
<device id="12" udi="/org/freedesktop/Hal/devices/acpi_CPU0">
<property name="info.category" type="str">
processor
</property>
<property name="info.product" type="str">
Intel(R) Pentium(R) D CPU 3.40GHz
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/acpi_CPU0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
processor
</value>
</property>
<property name="processor.can_throttle" type="bool">
True
</property>
<property name="processor.number" type="int">
0
</property>
<property name="linux.acpi_path" type="str">
/proc/acpi/processor/CPU0
</property>
<property name="linux.hotplug_type" type="int">
4
</property>
<property name="linux.acpi_type" type="int">
1
</property>
</device>
<device id="13" udi="/org/freedesktop/Hal/devices/acpi_CPU1">
<property name="info.category" type="str">
processor
</property>
<property name="info.product" type="str">
Intel(R) Pentium(R) D CPU 3.40GHz
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/acpi_CPU1
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
processor
</value>
</property>
<property name="processor.can_throttle" type="bool">
True
</property>
<property name="processor.number" type="int">
1
</property>
<property name="linux.acpi_path" type="str">
/proc/acpi/processor/CPU1
</property>
<property name="linux.hotplug_type" type="int">
4
</property>
<property name="linux.acpi_type" type="int">
1
</property>
</device>
<device id="14" udi="/org/freedesktop/Hal/devices/computer_alsa_timer">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
ALSA Timer Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_alsa_timer
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/timer
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/sound/timer
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/timer
</property>
<property name="alsa.device_file" type="str">
/dev/snd/timer
</property>
<property name="alsa.type" type="str">
timer
</property>
</device>
<device id="15" udi="/org/freedesktop/Hal/devices/computer_oss_sequencer_0">
<property name="info.category" type="str">
oss
</property>
<property name="info.product" type="str">
OSS Sequencer Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
oss
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_oss_sequencer_0
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="oss.device_file" type="str">
/dev/sequencer2
</property>
<property name="oss.type" type="str">
sequencer
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/sequencer2
</property>
<property name="linux.device_file" type="str">
/dev/sequencer2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/sound/sequencer2
</property>
</device>
<device id="16" udi="/org/freedesktop/Hal/devices/computer_oss_sequencer">
<property name="info.category" type="str">
oss
</property>
<property name="info.product" type="str">
OSS Sequencer Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
oss
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_oss_sequencer
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="oss.device_file" type="str">
/dev/sequencer
</property>
<property name="oss.type" type="str">
sequencer
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/sequencer
</property>
<property name="linux.device_file" type="str">
/dev/sequencer
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/sound/sequencer
</property>
</device>
<device id="17" udi="/org/freedesktop/Hal/devices/computer_alsa_sequencer">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
ALSA Sequencer Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_alsa_sequencer
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/seq
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/sound/seq
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/seq
</property>
<property name="alsa.device_file" type="str">
/dev/snd/seq
</property>
<property name="alsa.type" type="str">
sequencer
</property>
</device>
<device id="18" udi="/org/freedesktop/Hal/devices/computer_logicaldev_input_1">
<property name="info.category" type="str">
input
</property>
<property name="info.product" type="str">
Power Button (CM)
</property>
<property name="info.addons.singleton" type="list">
<value type="str">
hald-addon-input
</value>
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
input
</value>
<value type="str">
button
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_logicaldev_input_1
</property>
<property name="input.device" type="str">
/dev/input/event4
</property>
<property name="input.product" type="str">
Power Button (CM)
</property>
<property name="button.has_state" type="bool">
False
</property>
<property name="button.type" type="str">
power
</property>
<property name="linux.device_file" type="str">
/dev/input/event4
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
input
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/input/input4/event4
</property>
</device>
<device id="19" udi="/org/freedesktop/Hal/devices/computer_logicaldev_input_0">
<property name="info.category" type="str">
input
</property>
<property name="info.product" type="str">
Power Button (FF)
</property>
<property name="info.addons.singleton" type="list">
<value type="str">
hald-addon-input
</value>
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
input
</value>
<value type="str">
button
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_logicaldev_input_0
</property>
<property name="input.device" type="str">
/dev/input/event3
</property>
<property name="input.product" type="str">
Power Button (FF)
</property>
<property name="button.has_state" type="bool">
False
</property>
<property name="button.type" type="str">
power
</property>
<property name="linux.device_file" type="str">
/dev/input/event3
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
input
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/input/input3/event3
</property>
</device>
<device id="20" udi="/org/freedesktop/Hal/devices/computer_logicaldev_input">
<property name="info.category" type="str">
input
</property>
<property name="info.product" type="str">
Macintosh mouse button emulation
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/computer_logicaldev_input
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.capabilities" type="list">
<value type="str">
input
</value>
<value type="str">
input.mouse
</value>
</property>
<property name="input.device" type="str">
/dev/input/event0
</property>
<property name="input.product" type="str">
Macintosh mouse button emulation
</property>
<property name="linux.device_file" type="str">
/dev/input/event0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
input
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/virtual/input/input0/event0
</property>
</device>
<device id="21" udi="/org/freedesktop/Hal/devices/pnp_INT0800">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
PnP Device (INT0800)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_INT0800
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.id" type="str">
INT0800
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:0e
</property>
</device>
<device id="22" udi="/org/freedesktop/Hal/devices/pnp_PNP0c01">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
System Board
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0c01
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
system
</property>
<property name="pnp.description" type="str">
System Board
</property>
<property name="pnp.id" type="str">
PNP0c01
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:0d
</property>
</device>
<device id="23" udi="/org/freedesktop/Hal/devices/pnp_PNP0c02_1">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
General ID for reserving resources required by PnP motherboard registers. (Not device specific.)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0c02_1
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
system
</property>
<property name="pnp.description" type="str">
General ID for reserving resources required by PnP motherboard registers. (Not device specific.)
</property>
<property name="pnp.id" type="str">
PNP0c02
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:0c
</property>
</device>
<device id="24" udi="/org/freedesktop/Hal/devices/pnp_PNP0c02_0">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
General ID for reserving resources required by PnP motherboard registers. (Not device specific.)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0c02_0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
system
</property>
<property name="pnp.description" type="str">
General ID for reserving resources required by PnP motherboard registers. (Not device specific.)
</property>
<property name="pnp.id" type="str">
PNP0c02
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:0b
</property>
</device>
<device id="25" udi="/org/freedesktop/Hal/devices/pnp_PNP0303">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
IBM Enhanced (101/102-key, PS/2 mouse support)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0303
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
i8042 kbd
</property>
<property name="pnp.description" type="str">
IBM Enhanced (101/102-key, PS/2 mouse support)
</property>
<property name="pnp.id" type="str">
PNP0303
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:0a
</property>
</device>
<device id="26" udi="/org/freedesktop/Hal/devices/pnp_PNP0f13">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
PS/2 Port for PS/2-style Mice
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0f13
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
i8042 aux
</property>
<property name="pnp.description" type="str">
PS/2 Port for PS/2-style Mice
</property>
<property name="pnp.id" type="str">
PNP0f13
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:09
</property>
</device>
<device id="27" udi="/org/freedesktop/Hal/devices/pnp_PNP0400">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
Standard LPT printer port
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0400
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
parport_pc
</property>
<property name="pnp.description" type="str">
Standard LPT printer port
</property>
<property name="pnp.id" type="str">
PNP0400
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:08
</property>
</device>
<device id="28" udi="/org/freedesktop/Hal/devices/pnp_PNP0501">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
16550A-compatible COM port
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0501
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
serial
</property>
<property name="pnp.description" type="str">
16550A-compatible COM port
</property>
<property name="pnp.id" type="str">
PNP0501
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:07
</property>
</device>
<device id="29" udi="/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0">
<property name="info.category" type="str">
serial
</property>
<property name="info.product" type="str">
16550A-compatible COM port
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0501
</property>
<property name="info.capabilities" type="list">
<value type="str">
serial
</value>
</property>
<property name="serial.device" type="str">
/dev/ttyS0
</property>
<property name="serial.type" type="str">
platform
</property>
<property name="serial.port" type="int">
0
</property>
<property name="serial.originating_device" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0501
</property>
<property name="linux.device_file" type="str">
/dev/ttyS0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
tty
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:07/tty/ttyS0
</property>
</device>
<device id="30" udi="/org/freedesktop/Hal/devices/pnp_PNP0700">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
PC standard floppy disk controller
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0700
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.description" type="str">
PC standard floppy disk controller
</property>
<property name="pnp.id" type="str">
PNP0700
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:06
</property>
</device>
<device id="31" udi="/org/freedesktop/Hal/devices/pnp_PNP0c04">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
Math Coprocessor
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0c04
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.description" type="str">
Math Coprocessor
</property>
<property name="pnp.id" type="str">
PNP0c04
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:05
</property>
</device>
<device id="32" udi="/org/freedesktop/Hal/devices/pnp_PNP0800">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
AT-style speaker sound
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0800
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.description" type="str">
AT-style speaker sound
</property>
<property name="pnp.id" type="str">
PNP0800
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:04
</property>
</device>
<device id="33" udi="/org/freedesktop/Hal/devices/pnp_PNP0b00">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
AT Real-Time Clock
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0b00
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.description" type="str">
AT Real-Time Clock
</property>
<property name="pnp.id" type="str">
PNP0b00
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:03
</property>
</device>
<device id="34" udi="/org/freedesktop/Hal/devices/pnp_PNP0200">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
AT DMA Controller
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0200
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.description" type="str">
AT DMA Controller
</property>
<property name="pnp.id" type="str">
PNP0200
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:02
</property>
</device>
<device id="35" udi="/org/freedesktop/Hal/devices/pnp_PNP0c02">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
General ID for reserving resources required by PnP motherboard registers. (Not device specific.)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0c02
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
system
</property>
<property name="pnp.description" type="str">
General ID for reserving resources required by PnP motherboard registers. (Not device specific.)
</property>
<property name="pnp.id" type="str">
PNP0c02
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:01
</property>
</device>
<device id="36" udi="/org/freedesktop/Hal/devices/pnp_PNP0a03">
<property name="info.subsystem" type="str">
pnp
</property>
<property name="info.product" type="str">
PCI Bus
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pnp_PNP0a03
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pnp.description" type="str">
PCI Bus
</property>
<property name="pnp.id" type="str">
PNP0a03
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pnp
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pnp0/00:00
</property>
</device>
<device id="37" udi="/org/freedesktop/Hal/devices/platform_serial8250">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (serial8250)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_serial8250
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
serial8250
</property>
<property name="platform.id" type="str">
serial8250
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/serial8250
</property>
</device>
<device id="38" udi="/org/freedesktop/Hal/devices/platform_pcspkr">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (pcspkr)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_pcspkr
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
pcspkr
</property>
<property name="platform.id" type="str">
pcspkr
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/pcspkr
</property>
</device>
<device id="39" udi="/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input">
<property name="info.category" type="str">
input
</property>
<property name="info.product" type="str">
PC Speaker
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/platform_pcspkr
</property>
<property name="info.capabilities" type="list">
<value type="str">
input
</value>
</property>
<property name="input.device" type="str">
/dev/input/event2
</property>
<property name="input.product" type="str">
PC Speaker
</property>
<property name="input.originating_device" type="str">
/org/freedesktop/Hal/devices/platform_pcspkr
</property>
<property name="linux.device_file" type="str">
/dev/input/event2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
input
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/pcspkr/input/input2/event2
</property>
</device>
<device id="40" udi="/org/freedesktop/Hal/devices/platform_iTCO_wdt">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (iTCO_wdt)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_iTCO_wdt
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
iTCO_wdt
</property>
<property name="platform.id" type="str">
iTCO_wdt
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/iTCO_wdt
</property>
</device>
<device id="41" udi="/org/freedesktop/Hal/devices/platform_i8042">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (i8042)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_i8042
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
i8042
</property>
<property name="platform.id" type="str">
i8042
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/i8042
</property>
</device>
<device id="42" udi="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port">
<property name="info.subsystem" type="str">
serio
</property>
<property name="info.product" type="str">
i8042 AUX port
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/platform_i8042
</property>
<property name="info.linux.driver" type="str">
psmouse
</property>
<property name="serio.description" type="str">
i8042 AUX port
</property>
<property name="serio.id" type="str">
serio1
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
serio
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/i8042/serio1
</property>
</device>
<device id="43" udi="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input">
<property name="info.category" type="str">
input
</property>
<property name="info.product" type="str">
ImPS/2 Logitech Wheel Mouse
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port
</property>
<property name="info.capabilities" type="list">
<value type="str">
input
</value>
<value type="str">
input.mouse
</value>
</property>
<property name="input.device" type="str">
/dev/input/event5
</property>
<property name="input.product" type="str">
ImPS/2 Logitech Wheel Mouse
</property>
<property name="input.originating_device" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port
</property>
<property name="linux.device_file" type="str">
/dev/input/event5
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
input
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/i8042/serio1/input/input5/event5
</property>
</device>
<device id="44" udi="/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port">
<property name="info.subsystem" type="str">
serio
</property>
<property name="info.product" type="str">
i8042 KBD port
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/platform_i8042
</property>
<property name="info.linux.driver" type="str">
atkbd
</property>
<property name="serio.description" type="str">
i8042 KBD port
</property>
<property name="serio.id" type="str">
serio0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
serio
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/i8042/serio0
</property>
</device>
<device id="45" udi="/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input">
<property name="info.category" type="str">
input
</property>
<property name="info.product" type="str">
AT Translated Set 2 keyboard
</property>
<property name="info.addons.singleton" type="list">
<value type="str">
hald-addon-input
</value>
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port
</property>
<property name="info.capabilities" type="list">
<value type="str">
input
</value>
<value type="str">
input.keyboard
</value>
<value type="str">
input.keypad
</value>
<value type="str">
input.keys
</value>
<value type="str">
button
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
</property>
<property name="input.device" type="str">
/dev/input/event1
</property>
<property name="input.xkb.rules" type="str">
base
</property>
<property name="input.xkb.variant" type="str">

</property>
<property name="input.xkb.model" type="str">
evdev
</property>
<property name="input.xkb.layout" type="str">
us
</property>
<property name="input.product" type="str">
AT Translated Set 2 keyboard
</property>
<property name="input.originating_device" type="str">
/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port
</property>
<property name="linux.device_file" type="str">
/dev/input/event1
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
input
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/i8042/serio0/input/input1/event1
</property>
</device>
<device id="46" udi="/org/freedesktop/Hal/devices/platform_floppy_0">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (floppy.0)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_floppy_0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="platform.id" type="str">
floppy.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/floppy.0
</property>
</device>
<device id="47" udi="/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy">
<property name="info.category" type="str">
storage
</property>
<property name="info.product" type="str">
PC Floppy Drive
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy
</property>
<property name="info.vendor" type="str">

</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/platform_floppy_0
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.Volume
</value>
<value type="str">
org.freedesktop.Hal.Device.Storage.Removable
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
storage
</value>
<value type="str">
block
</value>
</property>
<property name="info.addons" type="list">
<value type="str">
hald-addon-storage
</value>
</property>
<property name="storage.no_partitions_hint" type="bool">
True
</property>
<property name="storage.media_check_enabled" type="bool">
False
</property>
<property name="storage.originating_device" type="str">
/org/freedesktop/Hal/devices/platform_floppy_0
</property>
<property name="storage.bus" type="str">
platform
</property>
<property name="storage.requires_eject" type="bool">
False
</property>
<property name="storage.hotpluggable" type="bool">
False
</property>
<property name="storage.drive_type" type="str">
floppy
</property>
<property name="storage.removable.media_available" type="bool">
False
</property>
<property name="storage.automount_enabled_hint" type="bool">
True
</property>
<property name="storage.vendor" type="str">
PC Floppy Drive
</property>
<property name="storage.model" type="str">

</property>
<property name="storage.size" type="int">
0
</property>
<property name="volume.mount.valid_options" type="list">
<value type="str">
ro
</value>
<value type="str">
sync
</value>
<value type="str">
dirsync
</value>
<value type="str">
noatime
</value>
<value type="str">
nodiratime
</value>
<value type="str">
noexec
</value>
<value type="str">
quiet
</value>
<value type="str">
remount
</value>
<value type="str">
exec
</value>
<value type="str">
utf8
</value>
<value type="str">
shortname=
</value>
<value type="str">
codepage=
</value>
<value type="str">
iocharset=
</value>
<value type="str">
umask=
</value>
<value type="str">
uid=
</value>
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/fd0
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_signatures" type="list">
<value type="str">
ssas
</value>
<value type="str">
as
</value>
<value type="str">
as
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_execpaths" type="list">
<value type="str">
hal-storage-mount
</value>
<value type="str">
hal-storage-unmount
</value>
<value type="str">
hal-storage-eject
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_argnames" type="list">
<value type="str">
mount_point fstype extra_options
</value>
<value type="str">
extra_options
</value>
<value type="str">
extra_options
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_names" type="list">
<value type="str">
Mount
</value>
<value type="str">
Unmount
</value>
<value type="str">
Eject
</value>
</property>
<property name="block.device" type="str">
/dev/fd0
</property>
<property name="block.major" type="int">
2
</property>
<property name="block.is_volume" type="bool">
False
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy
</property>
<property name="block.minor" type="int">
0
</property>
</device>
<device id="48" udi="/org/freedesktop/Hal/devices/platform_eisa_0">
<property name="info.subsystem" type="str">
platform
</property>
<property name="info.product" type="str">
Platform Device (eisa.0)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/platform_eisa_0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="platform.id" type="str">
eisa.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
platform
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/platform/eisa.0
</property>
</device>
<device id="49" udi="/org/freedesktop/Hal/devices/pci_8086_27da">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) SMBus Controller
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27da
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) SMBus Controller
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10202
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
5
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
12
</property>
<property name="pci.subsys_product_id" type="int">
20481
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.3
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.3
</property>
</device>
<device id="50" udi="/org/freedesktop/Hal/devices/pci_8086_27c0">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801GB/GR/GH (ICH7 Family) SATA IDE Controller
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
ata_piix
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0
</property>
<property name="pci.product" type="str">
82801GB/GR/GH (ICH7 Family) SATA IDE Controller
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10176
</property>
<property name="pci.device_protocol" type="int">
128
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
1
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
1
</property>
<property name="pci.subsys_product_id" type="int">
45058
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.2
</property>
</device>
<device id="51" udi="/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0">
<property name="info.category" type="str">
scsi_host
</property>
<property name="info.product" type="str">
SCSI Host Adapter
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0
</property>
<property name="info.capabilities" type="list">
<value type="str">
scsi_host
</value>
</property>
<property name="scsi_host.host" type="int">
1
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi_host
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.2/host1
</property>
</device>
<device id="52" udi="/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0">
<property name="info.subsystem" type="str">
scsi
</property>
<property name="info.product" type="str">
SCSI Device
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0
</property>
<property name="info.linux.driver" type="str">
sr
</property>
<property name="scsi.vendor" type="str">
HL-DT-ST
</property>
<property name="scsi.target" type="int">
0
</property>
<property name="scsi.bus" type="int">
0
</property>
<property name="scsi.host" type="int">
1
</property>
<property name="scsi.model" type="str">
DVD-RAM GSA-H55N
</property>
<property name="scsi.type" type="str">
cdrom
</property>
<property name="scsi.lun" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0
</property>
</device>
<device id="53" udi="/org/freedesktop/Hal/devices/storage_model_DVD_RAM_GSA_H55N">
<property name="info.category" type="str">
storage
</property>
<property name="info.product" type="str">
DVD-RAM GSA-H55N
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/storage_model_DVD_RAM_GSA_H55N
</property>
<property name="info.vendor" type="str">
HL-DT-ST
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.Storage
</value>
<value type="str">
org.freedesktop.Hal.Device.Storage
</value>
<value type="str">
org.freedesktop.Hal.Device.Storage.Removable
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
storage
</value>
<value type="str">
block
</value>
<value type="str">
storage.cdrom
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.addons" type="list">
<value type="str">
hald-addon-storage
</value>
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="access_control.type" type="str">
cdrom
</property>
<property name="access_control.file" type="str">
/dev/scd0
</property>
<property name="storage.no_partitions_hint" type="bool">
True
</property>
<property name="storage.media_check_enabled" type="bool">
True
</property>
<property name="storage.removable.media_available" type="bool">
False
</property>
<property name="storage.removable.support_async_notification" type="bool">
False
</property>
<property name="storage.originating_device" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="storage.partitioning_scheme" type="str">

</property>
<property name="storage.bus" type="str">
scsi
</property>
<property name="storage.requires_eject" type="bool">
True
</property>
<property name="storage.cdrom.cdr" type="bool">
True
</property>
<property name="storage.cdrom.mrw_w" type="bool">
True
</property>
<property name="storage.cdrom.cdrw" type="bool">
True
</property>
<property name="storage.cdrom.support_multisession" type="bool">
True
</property>
<property name="storage.cdrom.write_speed" type="int">
8468
</property>
<property name="storage.cdrom.hddvd" type="bool">
False
</property>
<property name="storage.cdrom.dvdrw" type="bool">
True
</property>
<property name="storage.cdrom.dvdram" type="bool">
True
</property>
<property name="storage.cdrom.support_media_changed" type="bool">
True
</property>
<property name="storage.cdrom.dvdplusrdl" type="bool">
True
</property>
<property name="storage.cdrom.hddvdr" type="bool">
False
</property>
<property name="storage.cdrom.bdr" type="bool">
False
</property>
<property name="storage.cdrom.bd" type="bool">
False
</property>
<property name="storage.cdrom.dvdplusrwdl" type="bool">
False
</property>
<property name="storage.cdrom.dvdr" type="bool">
True
</property>
<property name="storage.cdrom.dvdplusrw" type="bool">
True
</property>
<property name="storage.cdrom.hddvdrw" type="bool">
False
</property>
<property name="storage.cdrom.dvdplusr" type="bool">
True
</property>
<property name="storage.cdrom.dvd" type="bool">
True
</property>
<property name="storage.cdrom.mo" type="bool">
False
</property>
<property name="storage.cdrom.mrw" type="bool">
True
</property>
<property name="storage.cdrom.write_speeds" type="list">
<value type="str">
8468
</value>
<value type="str">
7056
</value>
<value type="str">
4234
</value>
<value type="str">
2822
</value>
</property>
<property name="storage.cdrom.bdre" type="bool">
False
</property>
<property name="storage.cdrom.read_speed" type="int">
8468
</property>
<property name="storage.drive_type" type="str">
cdrom
</property>
<property name="storage.hotpluggable" type="bool">
False
</property>
<property name="storage.automount_enabled_hint" type="bool">
True
</property>
<property name="storage.vendor" type="str">
HL-DT-ST
</property>
<property name="storage.firmware_version" type="str">
1.05
</property>
<property name="storage.model" type="str">
DVD-RAM GSA-H55N
</property>
<property name="storage.lun" type="int">
0
</property>
<property name="storage.size" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sr0
</property>
<property name="org.freedesktop.Hal.Device.Storage.method_signatures" type="list">
<value type="str">
as
</value>
<value type="str">
as
</value>
</property>
<property name="org.freedesktop.Hal.Device.Storage.method_execpaths" type="list">
<value type="str">
hal-storage-eject
</value>
<value type="str">
hal-storage-closetray
</value>
</property>
<property name="org.freedesktop.Hal.Device.Storage.method_argnames" type="list">
<value type="str">
extra_options
</value>
<value type="str">
extra_options
</value>
</property>
<property name="org.freedesktop.Hal.Device.Storage.method_names" type="list">
<value type="str">
Eject
</value>
<value type="str">
CloseTray
</value>
</property>
<property name="block.device" type="str">
/dev/scd0
</property>
<property name="block.major" type="int">
11
</property>
<property name="block.is_volume" type="bool">
False
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_model_DVD_RAM_GSA_H55N
</property>
<property name="block.minor" type="int">
0
</property>
</device>
<device id="54" udi="/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_scsi_generic">
<property name="info.category" type="str">
scsi_generic
</property>
<property name="info.product" type="str">
SCSI Generic Interface
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0_scsi_generic
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_0_scsi_device_lun0
</property>
<property name="info.capabilities" type="list">
<value type="str">
scsi_generic
</value>
</property>
<property name="scsi_generic.device" type="str">
/dev/sg1
</property>
<property name="linux.device_file" type="str">
/dev/sg1
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi_generic
</property>
<property name="linux.sysfs_path" type="str">
/sys/class/scsi_generic/sg1
</property>
</device>
<device id="55" udi="/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host">
<property name="info.category" type="str">
scsi_host
</property>
<property name="info.product" type="str">
SCSI Host Adapter
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0
</property>
<property name="info.capabilities" type="list">
<value type="str">
scsi_host
</value>
</property>
<property name="scsi_host.host" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi_host
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.2/host0
</property>
</device>
<device id="56" udi="/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0">
<property name="info.subsystem" type="str">
scsi
</property>
<property name="info.product" type="str">
SCSI Device
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host
</property>
<property name="info.linux.driver" type="str">
sd
</property>
<property name="scsi.vendor" type="str">
ATA
</property>
<property name="scsi.target" type="int">
0
</property>
<property name="scsi.bus" type="int">
0
</property>
<property name="scsi.host" type="int">
0
</property>
<property name="scsi.model" type="str">
WDC WD1600AAJS-6
</property>
<property name="scsi.type" type="str">
disk
</property>
<property name="scsi.lun" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
</property>
</device>
<device id="57" udi="/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424">
<property name="info.category" type="str">
storage
</property>
<property name="info.product" type="str">
WDC WD1600AAJS-6
</property>
<property name="info.vendor" type="str">
ATA
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0
</property>
<property name="info.capabilities" type="list">
<value type="str">
storage
</value>
<value type="str">
block
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="storage.no_partitions_hint" type="bool">
False
</property>
<property name="storage.media_check_enabled" type="bool">
False
</property>
<property name="storage.originating_device" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="storage.partitioning_scheme" type="str">
mbr
</property>
<property name="storage.bus" type="str">
scsi
</property>
<property name="storage.requires_eject" type="bool">
False
</property>
<property name="storage.hotpluggable" type="bool">
False
</property>
<property name="storage.drive_type" type="str">
disk
</property>
<property name="storage.removable.media_size" type="long">
160041885696
</property>
<property name="storage.removable.media_available" type="bool">
True
</property>
<property name="storage.serial" type="str">
1ATA_WDC_WD1600AAJS-65WAA0_WD-WCAS21782424
</property>
<property name="storage.automount_enabled_hint" type="bool">
False
</property>
<property name="storage.vendor" type="str">
ATA
</property>
<property name="storage.firmware_version" type="str">
58.0
</property>
<property name="storage.model" type="str">
WDC WD1600AAJS-6
</property>
<property name="storage.lun" type="int">
0
</property>
<property name="storage.size" type="long">
160041885696
</property>
<property name="block.device" type="str">
/dev/sda
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
False
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="block.minor" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sda
</property>
</device>
<device id="58" udi="/org/freedesktop/Hal/devices/volume_uuid_62dc29c9_c807_4a52_bc2f_75f259557f5d">
<property name="info.category" type="str">
volume
</property>
<property name="info.product" type="str">
Volume (swap)
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/volume_uuid_62dc29c9_c807_4a52_bc2f_75f259557f5d
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="info.capabilities" type="list">
<value type="str">
volume
</value>
<value type="str">
block
</value>
</property>
<property name="volume.is_mounted_read_only" type="bool">
False
</property>
<property name="volume.mount_point" type="str">

</property>
<property name="volume.uuid" type="str">
62dc29c9-c807-4a52-bc2f-75f259557f5d
</property>
<property name="volume.is_mounted" type="bool">
False
</property>
<property name="volume.is_partition" type="bool">
True
</property>
<property name="volume.partition.start" type="long">
157324962816
</property>
<property name="volume.partition.media_size" type="long">
160041885696
</property>
<property name="volume.partition.number" type="int">
6
</property>
<property name="volume.label" type="str">

</property>
<property name="volume.fstype" type="str">
swap
</property>
<property name="volume.fsusage" type="str">
other
</property>
<property name="volume.is_disc" type="bool">
False
</property>
<property name="volume.fsversion" type="str">
2
</property>
<property name="volume.linux.is_device_mapper" type="bool">
False
</property>
<property name="volume.block_size" type="int">
512
</property>
<property name="volume.num_blocks" type="int">
5301387
</property>
<property name="volume.size" type="long">
2714310144
</property>
<property name="storage.model" type="str">

</property>
<property name="block.device" type="str">
/dev/sda6
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
True
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="block.minor" type="int">
6
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sda/sda6
</property>
</device>
<device id="59" udi="/org/freedesktop/Hal/devices/volume_uuid_46fb014b_b31c_45bd_8f3b_e0a42c31714a">
<property name="info.category" type="str">
volume
</property>
<property name="info.product" type="str">
Volume (ext3)
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.Volume
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
volume
</value>
<value type="str">
block
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/volume_uuid_46fb014b_b31c_45bd_8f3b_e0a42c31714a
</property>
<property name="storage.model" type="str">

</property>
<property name="volume.is_mounted_read_only" type="bool">
False
</property>
<property name="volume.uuid" type="str">
46fb014b-b31c-45bd-8f3b-e0a42c31714a
</property>
<property name="volume.mount_point" type="str">
/
</property>
<property name="volume.unmount.valid_options" type="list">
<value type="str">
lazy
</value>
</property>
<property name="volume.is_mounted" type="bool">
True
</property>
<property name="volume.is_partition" type="bool">
True
</property>
<property name="volume.mount.valid_options" type="list">
<value type="str">
ro
</value>
<value type="str">
sync
</value>
<value type="str">
dirsync
</value>
<value type="str">
noatime
</value>
<value type="str">
nodiratime
</value>
<value type="str">
noexec
</value>
<value type="str">
quiet
</value>
<value type="str">
remount
</value>
<value type="str">
exec
</value>
<value type="str">
acl
</value>
<value type="str">
user_xattr
</value>
<value type="str">
data=
</value>
</property>
<property name="volume.partition.start" type="long">
94607202816
</property>
<property name="volume.partition.media_size" type="long">
160041885696
</property>
<property name="volume.partition.number" type="int">
5
</property>
<property name="volume.label" type="str">

</property>
<property name="volume.fstype" type="str">
ext3
</property>
<property name="volume.ignore" type="bool">
False
</property>
<property name="volume.fsusage" type="str">
filesystem
</property>
<property name="volume.is_disc" type="bool">
False
</property>
<property name="volume.fsversion" type="str">
1.0
</property>
<property name="volume.linux.is_device_mapper" type="bool">
False
</property>
<property name="volume.block_size" type="int">
512
</property>
<property name="volume.num_blocks" type="int">
122495562
</property>
<property name="volume.size" type="long">
62717727744
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sda/sda5
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_signatures" type="list">
<value type="str">
ssas
</value>
<value type="str">
as
</value>
<value type="str">
as
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_execpaths" type="list">
<value type="str">
hal-storage-mount
</value>
<value type="str">
hal-storage-unmount
</value>
<value type="str">
hal-storage-eject
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_argnames" type="list">
<value type="str">
mount_point fstype extra_options
</value>
<value type="str">
extra_options
</value>
<value type="str">
extra_options
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_names" type="list">
<value type="str">
Mount
</value>
<value type="str">
Unmount
</value>
<value type="str">
Eject
</value>
</property>
<property name="block.device" type="str">
/dev/sda5
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
True
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="block.minor" type="int">
5
</property>
</device>
<device id="60" udi="/org/freedesktop/Hal/devices/volume_part2_size_1024">
<property name="info.category" type="str">
volume
</property>
<property name="info.product" type="str">
Volume
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/volume_part2_size_1024
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="info.capabilities" type="list">
<value type="str">
volume
</value>
<value type="str">
block
</value>
</property>
<property name="volume.is_mounted_read_only" type="bool">
False
</property>
<property name="volume.mount_point" type="str">

</property>
<property name="volume.uuid" type="str">

</property>
<property name="volume.is_mounted" type="bool">
False
</property>
<property name="volume.is_partition" type="bool">
True
</property>
<property name="volume.partition.start" type="long">
94607170560
</property>
<property name="volume.partition.media_size" type="long">
160041885696
</property>
<property name="volume.partition.number" type="int">
2
</property>
<property name="volume.label" type="str">

</property>
<property name="volume.fstype" type="str">

</property>
<property name="volume.fsusage" type="str">

</property>
<property name="volume.is_disc" type="bool">
False
</property>
<property name="volume.fsversion" type="str">

</property>
<property name="volume.linux.is_device_mapper" type="bool">
False
</property>
<property name="volume.block_size" type="int">
512
</property>
<property name="volume.num_blocks" type="int">
2
</property>
<property name="volume.size" type="int">
1024
</property>
<property name="storage.model" type="str">

</property>
<property name="block.device" type="str">
/dev/sda2
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
True
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="block.minor" type="int">
2
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sda/sda2
</property>
</device>
<device id="61" udi="/org/freedesktop/Hal/devices/volume_uuid_D874829474827552">
<property name="info.category" type="str">
volume
</property>
<property name="info.product" type="str">
Volume (ntfs)
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.Volume
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
volume
</value>
<value type="str">
block
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/volume_uuid_D874829474827552
</property>
<property name="storage.model" type="str">

</property>
<property name="volume.is_mounted_read_only" type="bool">
False
</property>
<property name="volume.uuid" type="str">
D874829474827552
</property>
<property name="volume.mount_point" type="str">

</property>
<property name="volume.unmount.valid_options" type="list">
<value type="str">
lazy
</value>
</property>
<property name="volume.is_mounted" type="bool">
False
</property>
<property name="volume.is_partition" type="bool">
True
</property>
<property name="volume.mount.valid_options" type="list">
<value type="str">
ro
</value>
<value type="str">
sync
</value>
<value type="str">
dirsync
</value>
<value type="str">
noatime
</value>
<value type="str">
nodiratime
</value>
<value type="str">
noexec
</value>
<value type="str">
quiet
</value>
<value type="str">
remount
</value>
<value type="str">
exec
</value>
<value type="str">
uid=
</value>
<value type="str">
gid=
</value>
<value type="str">
umask=
</value>
<value type="str">
locale=
</value>
<value type="str">
utf8
</value>
</property>
<property name="volume.partition.uuid" type="str">

</property>
<property name="volume.partition.media_size" type="long">
160041885696
</property>
<property name="volume.partition.number" type="int">
1
</property>
<property name="volume.partition.label" type="str">

</property>
<property name="volume.partition.start" type="int">
32256
</property>
<property name="volume.partition.flags" type="list">
<value type="str">
boot
</value>
</property>
<property name="volume.partition.scheme" type="str">
mbr
</property>
<property name="volume.partition.type" type="str">
0x07
</property>
<property name="volume.label" type="str">

</property>
<property name="volume.fstype" type="str">
ntfs
</property>
<property name="volume.ignore" type="bool">
False
</property>
<property name="volume.fsusage" type="str">
filesystem
</property>
<property name="volume.is_disc" type="bool">
False
</property>
<property name="volume.fsversion" type="str">
3.1
</property>
<property name="volume.linux.is_device_mapper" type="bool">
False
</property>
<property name="volume.block_size" type="int">
512
</property>
<property name="volume.num_blocks" type="int">
184779567
</property>
<property name="volume.size" type="long">
94607138304
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sda/sda1
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_signatures" type="list">
<value type="str">
ssas
</value>
<value type="str">
as
</value>
<value type="str">
as
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_execpaths" type="list">
<value type="str">
hal-storage-mount
</value>
<value type="str">
hal-storage-unmount
</value>
<value type="str">
hal-storage-eject
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_argnames" type="list">
<value type="str">
mount_point fstype extra_options
</value>
<value type="str">
extra_options
</value>
<value type="str">
extra_options
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_names" type="list">
<value type="str">
Mount
</value>
<value type="str">
Unmount
</value>
<value type="str">
Eject
</value>
</property>
<property name="block.device" type="str">
/dev/sda1
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
True
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD1600AAJS_65WAA0_WD_WCAS21782424
</property>
<property name="block.minor" type="int">
1
</property>
</device>
<device id="62" udi="/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0_scsi_generic">
<property name="info.category" type="str">
scsi_generic
</property>
<property name="info.product" type="str">
SCSI Generic Interface
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0_scsi_generic
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c0_scsi_host_scsi_device_lun0
</property>
<property name="info.capabilities" type="list">
<value type="str">
scsi_generic
</value>
</property>
<property name="scsi_generic.device" type="str">
/dev/sg0
</property>
<property name="linux.device_file" type="str">
/dev/sg0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi_generic
</property>
<property name="linux.sysfs_path" type="str">
/sys/class/scsi_generic/sg0
</property>
</device>
<device id="63" udi="/org/freedesktop/Hal/devices/pci_8086_27b8">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801GB/GR (ICH7 Family) LPC Interface Bridge
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27b8
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pci.product" type="str">
82801GB/GR (ICH7 Family) LPC Interface Bridge
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10168
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
1
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
6
</property>
<property name="pci.subsys_product_id" type="int">
20481
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1f.0
</property>
</device>
<device id="64" udi="/org/freedesktop/Hal/devices/pci_8086_244e">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801 PCI Bridge
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_244e
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pci.product" type="str">
82801 PCI Bridge
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
9294
</property>
<property name="pci.device_protocol" type="int">
1
</property>
<property name="pci.device_subclass" type="int">
4
</property>
<property name="pci.subsys_vendor_id" type="int">
0
</property>
<property name="pci.device_class" type="int">
6
</property>
<property name="pci.subsys_product_id" type="int">
0
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1e.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1e.0
</property>
</device>
<device id="65" udi="/org/freedesktop/Hal/devices/pci_8086_27cc">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) USB2 EHCI Controller
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
ehci_hcd
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27cc
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) USB2 EHCI Controller
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10188
</property>
<property name="pci.device_protocol" type="int">
32
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
3
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
12
</property>
<property name="pci.subsys_product_id" type="int">
20486
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7
</property>
</device>
<device id="66" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
EHCI Host Controller
</property>
<property name="info.vendor" type="str">
Linux 2.6.24-19-generic ehci_hcd
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27cc
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7
</property>
<property name="usb_device.speed_bcd" type="int">
294912
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5
</property>
<property name="usb_device.linux.device_number" type="int">
1
</property>
<property name="usb_device.serial" type="str">
0000:00:1d.7
</property>
<property name="usb_device.speed" type="float">
480.0
</property>
<property name="usb_device.device_class" type="int">
9
</property>
<property name="usb_device.device_protocol" type="int">
1
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.device_revision_bcd" type="int">
518
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
2.0
</property>
<property name="usb_device.num_ports" type="int">
8
</property>
<property name="usb_device.product" type="str">
EHCI Host Controller
</property>
<property name="usb_device.vendor" type="str">
Linux 2.6.24-19-generic ehci_hcd
</property>
<property name="usb_device.is_self_powered" type="bool">
True
</property>
<property name="usb_device.version_bcd" type="int">
512
</property>
<property name="usb_device.vendor_id" type="int">
0
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="usb_device.can_wake_up" type="bool">
True
</property>
<property name="usb_device.product_id" type="int">
0
</property>
<property name="usb_device.bus_number" type="int">
5
</property>
<property name="usb_device.max_power" type="int">
0
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/005/001
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5
</property>
</device>
<device id="67" udi="/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
USB-2.0 4-Port HUB
</property>
<property name="info.vendor" type="str">
Genesys Logic, Inc.
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-8
</property>
<property name="usb_device.linux.device_number" type="int">
3
</property>
<property name="usb_device.is_self_powered" type="bool">
True
</property>
<property name="usb_device.vendor_id" type="int">
1507
</property>
<property name="usb_device.vendor" type="str">
Genesys Logic, Inc.
</property>
<property name="usb_device.product_id" type="int">
1544
</property>
<property name="usb_device.device_protocol" type="int">
1
</property>
<property name="usb_device.device_revision_bcd" type="int">
1794
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.speed" type="float">
480.0
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.bus_number" type="int">
5
</property>
<property name="usb_device.product" type="str">
USB-2.0 4-Port HUB
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
2.0
</property>
<property name="usb_device.num_ports" type="int">
4
</property>
<property name="usb_device.max_power" type="int">
100
</property>
<property name="usb_device.version_bcd" type="int">
512
</property>
<property name="usb_device.device_class" type="int">
9
</property>
<property name="usb_device.speed_bcd" type="int">
294912
</property>
<property name="usb_device.can_wake_up" type="bool">
True
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/005/003
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-8
</property>
</device>
<device id="68" udi="/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Hub Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
hub
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial_if0
</property>
<property name="usb.device_protocol" type="int">
1
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0
</property>
<property name="usb.linux.device_number" type="int">
3
</property>
<property name="usb.speed" type="float">
480.0
</property>
<property name="usb.device_class" type="int">
9
</property>
<property name="usb.speed_bcd" type="int">
294912
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
1794
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
2.0
</property>
<property name="usb.num_ports" type="int">
4
</property>
<property name="usb.product" type="str">
USB Hub Interface
</property>
<property name="usb.vendor" type="str">
Genesys Logic, Inc.
</property>
<property name="usb.is_self_powered" type="bool">
True
</property>
<property name="usb.version_bcd" type="int">
512
</property>
<property name="usb.vendor_id" type="int">
1507
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
0
</property>
<property name="usb.interface.class" type="int">
9
</property>
<property name="usb.interface.subclass" type="int">
0
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
True
</property>
<property name="usb.product_id" type="int">
1544
</property>
<property name="usb.bus_number" type="int">
5
</property>
<property name="usb.max_power" type="int">
100
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0
</property>
</device>
<device id="69" udi="/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
ImationFlashDriv
</property>
<property name="info.vendor" type="str">
Imation Corp.
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554
</property>
<property name="usb_device.speed_bcd" type="int">
294912
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5
</property>
<property name="usb_device.linux.device_number" type="int">
2
</property>
<property name="usb_device.serial" type="str">
07781C370554
</property>
<property name="usb_device.speed" type="float">
480.0
</property>
<property name="usb_device.device_class" type="int">
0
</property>
<property name="usb_device.device_protocol" type="int">
0
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.device_revision_bcd" type="int">
256
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
2.0
</property>
<property name="usb_device.num_ports" type="int">
0
</property>
<property name="usb_device.product" type="str">
ImationFlashDriv
</property>
<property name="usb_device.vendor" type="str">
Imation Corp.
</property>
<property name="usb_device.is_self_powered" type="bool">
False
</property>
<property name="usb_device.version_bcd" type="int">
512
</property>
<property name="usb_device.vendor_id" type="int">
1816
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="usb_device.can_wake_up" type="bool">
False
</property>
<property name="usb_device.product_id" type="int">
391
</property>
<property name="usb_device.bus_number" type="int">
5
</property>
<property name="usb_device.max_power" type="int">
200
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/005/002
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5
</property>
</device>
<device id="70" udi="/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Mass Storage Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
usb-storage
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0
</property>
<property name="usb.speed_bcd" type="int">
294912
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0
</property>
<property name="usb.linux.device_number" type="int">
2
</property>
<property name="usb.serial" type="str">
07781C370554
</property>
<property name="usb.speed" type="float">
480.0
</property>
<property name="usb.device_class" type="int">
0
</property>
<property name="usb.device_protocol" type="int">
0
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
256
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
2.0
</property>
<property name="usb.num_ports" type="int">
0
</property>
<property name="usb.product" type="str">
USB Mass Storage Interface
</property>
<property name="usb.vendor" type="str">
Imation Corp.
</property>
<property name="usb.is_self_powered" type="bool">
False
</property>
<property name="usb.version_bcd" type="int">
512
</property>
<property name="usb.vendor_id" type="int">
1816
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
80
</property>
<property name="usb.interface.class" type="int">
8
</property>
<property name="usb.interface.subclass" type="int">
6
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
False
</property>
<property name="usb.product_id" type="int">
391
</property>
<property name="usb.bus_number" type="int">
5
</property>
<property name="usb.max_power" type="int">
200
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0
</property>
</device>
<device id="71" udi="/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host">
<property name="info.category" type="str">
scsi_host
</property>
<property name="info.product" type="str">
SCSI Host Adapter
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0
</property>
<property name="info.capabilities" type="list">
<value type="str">
scsi_host
</value>
</property>
<property name="scsi_host.host" type="int">
2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi_host
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host2
</property>
</device>
<device id="72" udi="/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host_scsi_device_lun0">
<property name="info.subsystem" type="str">
scsi
</property>
<property name="info.product" type="str">
SCSI Device
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host_scsi_device_lun0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host
</property>
<property name="info.linux.driver" type="str">
sd
</property>
<property name="scsi.vendor" type="str">
Imation
</property>
<property name="scsi.target" type="int">
0
</property>
<property name="scsi.bus" type="int">
0
</property>
<property name="scsi.host" type="int">
2
</property>
<property name="scsi.model" type="str">
ImationFlashDriv
</property>
<property name="scsi.type" type="str">
disk
</property>
<property name="scsi.lun" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5:1.0/host2/target2:0:0/2:0:0:0
</property>
</device>
<device id="73" udi="/org/freedesktop/Hal/devices/storage_serial_Imation_ImationFlashDriv_07781C370554_0_0">
<property name="info.category" type="str">
storage
</property>
<property name="info.product" type="str">
ImationFlashDriv
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/storage_serial_Imation_ImationFlashDriv_07781C370554_0_0
</property>
<property name="info.vendor" type="str">
Imation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host_scsi_device_lun0
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.Storage.Removable
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
storage
</value>
<value type="str">
block
</value>
</property>
<property name="info.addons" type="list">
<value type="str">
hald-addon-storage
</value>
</property>
<property name="storage.no_partitions_hint" type="bool">
False
</property>
<property name="storage.media_check_enabled" type="bool">
True
</property>
<property name="storage.originating_device" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0
</property>
<property name="storage.partitioning_scheme" type="str">
mbr
</property>
<property name="storage.bus" type="str">
usb
</property>
<property name="storage.requires_eject" type="bool">
False
</property>
<property name="storage.hotpluggable" type="bool">
True
</property>
<property name="storage.drive_type" type="str">
disk
</property>
<property name="storage.removable.media_size" type="int">
2062548992
</property>
<property name="storage.removable.media_available" type="bool">
True
</property>
<property name="storage.removable.support_async_notification" type="bool">
False
</property>
<property name="storage.serial" type="str">
Imation_ImationFlashDriv_07781C370554-0:0
</property>
<property name="storage.automount_enabled_hint" type="bool">
True
</property>
<property name="storage.vendor" type="str">
Imation
</property>
<property name="storage.firmware_version" type="str">
PMAP
</property>
<property name="storage.model" type="str">
ImationFlashDriv
</property>
<property name="storage.lun" type="int">
0
</property>
<property name="storage.size" type="int">
0
</property>
<property name="block.device" type="str">
/dev/sdb
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
False
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_Imation_ImationFlashDriv_07781C370554_0_0
</property>
<property name="block.minor" type="int">
16
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sdb
</property>
</device>
<device id="74" udi="/org/freedesktop/Hal/devices/volume_uuid_B49F_189F">
<property name="info.category" type="str">
volume
</property>
<property name="info.product" type="str">
ALJAWAL
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/storage_serial_Imation_ImationFlashDriv_07781C370554_0_0
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.Volume
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
volume
</value>
<value type="str">
block
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/volume_uuid_B49F_189F
</property>
<property name="storage.model" type="str">

</property>
<property name="volume.is_mounted_read_only" type="bool">
False
</property>
<property name="volume.uuid" type="str">
B49F-189F
</property>
<property name="volume.mount_point" type="str">
/media/ALJAWAL
</property>
<property name="volume.unmount.valid_options" type="list">
<value type="str">
lazy
</value>
</property>
<property name="volume.is_mounted" type="bool">
True
</property>
<property name="volume.is_partition" type="bool">
True
</property>
<property name="volume.mount.valid_options" type="list">
<value type="str">
ro
</value>
<value type="str">
sync
</value>
<value type="str">
dirsync
</value>
<value type="str">
noatime
</value>
<value type="str">
nodiratime
</value>
<value type="str">
noexec
</value>
<value type="str">
quiet
</value>
<value type="str">
remount
</value>
<value type="str">
exec
</value>
<value type="str">
utf8
</value>
<value type="str">
shortname=
</value>
<value type="str">
codepage=
</value>
<value type="str">
iocharset=
</value>
<value type="str">
umask=
</value>
<value type="str">
dmask=
</value>
<value type="str">
fmask=
</value>
<value type="str">
uid=
</value>
<value type="str">
flush
</value>
</property>
<property name="volume.partition.uuid" type="str">

</property>
<property name="volume.partition.media_size" type="int">
2062548992
</property>
<property name="volume.partition.number" type="int">
1
</property>
<property name="volume.partition.label" type="str">

</property>
<property name="volume.partition.start" type="int">
16384
</property>
<property name="volume.partition.flags" type="list">
<value type="str">

</value>
</property>
<property name="volume.partition.scheme" type="str">
mbr
</property>
<property name="volume.partition.type" type="str">
0x0e
</property>
<property name="volume.label" type="str">
ALJAWAL
</property>
<property name="volume.fstype" type="str">
vfat
</property>
<property name="volume.ignore" type="bool">
False
</property>
<property name="volume.fsusage" type="str">
filesystem
</property>
<property name="volume.is_disc" type="bool">
False
</property>
<property name="volume.fsversion" type="str">
FAT16
</property>
<property name="volume.linux.is_device_mapper" type="bool">
False
</property>
<property name="volume.block_size" type="int">
512
</property>
<property name="volume.num_blocks" type="int">
4028384
</property>
<property name="volume.size" type="int">
2062532608
</property>
<property name="linux.hotplug_type" type="int">
3
</property>
<property name="linux.sysfs_path" type="str">
/sys/block/sdb/sdb1
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_signatures" type="list">
<value type="str">
ssas
</value>
<value type="str">
as
</value>
<value type="str">
as
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_execpaths" type="list">
<value type="str">
hal-storage-mount
</value>
<value type="str">
hal-storage-unmount
</value>
<value type="str">
hal-storage-eject
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_argnames" type="list">
<value type="str">
mount_point fstype extra_options
</value>
<value type="str">
extra_options
</value>
<value type="str">
extra_options
</value>
</property>
<property name="org.freedesktop.Hal.Device.Volume.method_names" type="list">
<value type="str">
Mount
</value>
<value type="str">
Unmount
</value>
<value type="str">
Eject
</value>
</property>
<property name="block.device" type="str">
/dev/sdb1
</property>
<property name="block.major" type="int">
8
</property>
<property name="block.is_volume" type="bool">
True
</property>
<property name="block.storage_device" type="str">
/org/freedesktop/Hal/devices/storage_serial_Imation_ImationFlashDriv_07781C370554_0_0
</property>
<property name="block.minor" type="int">
17
</property>
</device>
<device id="75" udi="/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host_scsi_device_lun0_scsi_generic">
<property name="info.category" type="str">
scsi_generic
</property>
<property name="info.product" type="str">
SCSI Generic Interface
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host_scsi_device_lun0_scsi_generic
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_718_187_07781C370554_if0_scsi_host_scsi_device_lun0
</property>
<property name="info.capabilities" type="list">
<value type="str">
scsi_generic
</value>
</property>
<property name="scsi_generic.device" type="str">
/dev/sg2
</property>
<property name="linux.device_file" type="str">
/dev/sg2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
scsi_generic
</property>
<property name="linux.sysfs_path" type="str">
/sys/class/scsi_generic/sg2
</property>
</device>
<device id="76" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Hub Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
hub
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0
</property>
<property name="usb.speed_bcd" type="int">
294912
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-0:1.0
</property>
<property name="usb.linux.device_number" type="int">
1
</property>
<property name="usb.serial" type="str">
0000:00:1d.7
</property>
<property name="usb.speed" type="float">
480.0
</property>
<property name="usb.device_class" type="int">
9
</property>
<property name="usb.device_protocol" type="int">
1
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
518
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
2.0
</property>
<property name="usb.num_ports" type="int">
8
</property>
<property name="usb.product" type="str">
USB Hub Interface
</property>
<property name="usb.vendor" type="str">
Linux 2.6.24-19-generic ehci_hcd
</property>
<property name="usb.is_self_powered" type="bool">
True
</property>
<property name="usb.version_bcd" type="int">
512
</property>
<property name="usb.vendor_id" type="int">
0
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
0
</property>
<property name="usb.interface.class" type="int">
9
</property>
<property name="usb.interface.subclass" type="int">
0
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
True
</property>
<property name="usb.product_id" type="int">
0
</property>
<property name="usb.bus_number" type="int">
5
</property>
<property name="usb.max_power" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-0:1.0
</property>
</device>
<device id="77" udi="/org/freedesktop/Hal/devices/pci_8086_27cb">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #4
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
uhci_hcd
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27cb
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #4
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10187
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
3
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
12
</property>
<property name="pci.subsys_product_id" type="int">
20484
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.3
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.3
</property>
</device>
<device id="78" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
UHCI Host Controller
</property>
<property name="info.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27cb
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3
</property>
<property name="usb_device.speed_bcd" type="int">
4608
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.3/usb4
</property>
<property name="usb_device.linux.device_number" type="int">
1
</property>
<property name="usb_device.serial" type="str">
0000:00:1d.3
</property>
<property name="usb_device.speed" type="float">
12.0
</property>
<property name="usb_device.device_class" type="int">
9
</property>
<property name="usb_device.device_protocol" type="int">
0
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.device_revision_bcd" type="int">
518
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
1.1
</property>
<property name="usb_device.num_ports" type="int">
2
</property>
<property name="usb_device.product" type="str">
UHCI Host Controller
</property>
<property name="usb_device.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb_device.is_self_powered" type="bool">
True
</property>
<property name="usb_device.version_bcd" type="int">
272
</property>
<property name="usb_device.vendor_id" type="int">
0
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="usb_device.can_wake_up" type="bool">
True
</property>
<property name="usb_device.product_id" type="int">
0
</property>
<property name="usb_device.bus_number" type="int">
4
</property>
<property name="usb_device.max_power" type="int">
0
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/004/001
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.3/usb4
</property>
</device>
<device id="79" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Hub Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
hub
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0
</property>
<property name="usb.speed_bcd" type="int">
4608
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-0:1.0
</property>
<property name="usb.linux.device_number" type="int">
1
</property>
<property name="usb.serial" type="str">
0000:00:1d.3
</property>
<property name="usb.speed" type="float">
12.0
</property>
<property name="usb.device_class" type="int">
9
</property>
<property name="usb.device_protocol" type="int">
0
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
518
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
1.1
</property>
<property name="usb.num_ports" type="int">
2
</property>
<property name="usb.product" type="str">
USB Hub Interface
</property>
<property name="usb.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb.is_self_powered" type="bool">
True
</property>
<property name="usb.version_bcd" type="int">
272
</property>
<property name="usb.vendor_id" type="int">
0
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
0
</property>
<property name="usb.interface.class" type="int">
9
</property>
<property name="usb.interface.subclass" type="int">
0
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
True
</property>
<property name="usb.product_id" type="int">
0
</property>
<property name="usb.bus_number" type="int">
4
</property>
<property name="usb.max_power" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.3/usb4/4-0:1.0
</property>
</device>
<device id="80" udi="/org/freedesktop/Hal/devices/pci_8086_27ca">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #3
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
uhci_hcd
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27ca
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #3
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10186
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
3
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
12
</property>
<property name="pci.subsys_product_id" type="int">
20484
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.2
</property>
</device>
<device id="81" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
UHCI Host Controller
</property>
<property name="info.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27ca
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2
</property>
<property name="usb_device.speed_bcd" type="int">
4608
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.2/usb3
</property>
<property name="usb_device.linux.device_number" type="int">
1
</property>
<property name="usb_device.serial" type="str">
0000:00:1d.2
</property>
<property name="usb_device.speed" type="float">
12.0
</property>
<property name="usb_device.device_class" type="int">
9
</property>
<property name="usb_device.device_protocol" type="int">
0
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.device_revision_bcd" type="int">
518
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
1.1
</property>
<property name="usb_device.num_ports" type="int">
2
</property>
<property name="usb_device.product" type="str">
UHCI Host Controller
</property>
<property name="usb_device.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb_device.is_self_powered" type="bool">
True
</property>
<property name="usb_device.version_bcd" type="int">
272
</property>
<property name="usb_device.vendor_id" type="int">
0
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="usb_device.can_wake_up" type="bool">
True
</property>
<property name="usb_device.product_id" type="int">
0
</property>
<property name="usb_device.bus_number" type="int">
3
</property>
<property name="usb_device.max_power" type="int">
0
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/003/001
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.2/usb3
</property>
</device>
<device id="82" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Hub Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
hub
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0
</property>
<property name="usb.speed_bcd" type="int">
4608
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-0:1.0
</property>
<property name="usb.linux.device_number" type="int">
1
</property>
<property name="usb.serial" type="str">
0000:00:1d.2
</property>
<property name="usb.speed" type="float">
12.0
</property>
<property name="usb.device_class" type="int">
9
</property>
<property name="usb.device_protocol" type="int">
0
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
518
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
1.1
</property>
<property name="usb.num_ports" type="int">
2
</property>
<property name="usb.product" type="str">
USB Hub Interface
</property>
<property name="usb.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb.is_self_powered" type="bool">
True
</property>
<property name="usb.version_bcd" type="int">
272
</property>
<property name="usb.vendor_id" type="int">
0
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
0
</property>
<property name="usb.interface.class" type="int">
9
</property>
<property name="usb.interface.subclass" type="int">
0
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
True
</property>
<property name="usb.product_id" type="int">
0
</property>
<property name="usb.bus_number" type="int">
3
</property>
<property name="usb.max_power" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-0:1.0
</property>
</device>
<device id="83" udi="/org/freedesktop/Hal/devices/pci_8086_27c9">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #2
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
uhci_hcd
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c9
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #2
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10185
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
3
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
12
</property>
<property name="pci.subsys_product_id" type="int">
20484
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.1
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.1
</property>
</device>
<device id="84" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
UHCI Host Controller
</property>
<property name="info.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c9
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1
</property>
<property name="usb_device.speed_bcd" type="int">
4608
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.1/usb2
</property>
<property name="usb_device.linux.device_number" type="int">
1
</property>
<property name="usb_device.serial" type="str">
0000:00:1d.1
</property>
<property name="usb_device.speed" type="float">
12.0
</property>
<property name="usb_device.device_class" type="int">
9
</property>
<property name="usb_device.device_protocol" type="int">
0
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.device_revision_bcd" type="int">
518
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
1.1
</property>
<property name="usb_device.num_ports" type="int">
2
</property>
<property name="usb_device.product" type="str">
UHCI Host Controller
</property>
<property name="usb_device.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb_device.is_self_powered" type="bool">
True
</property>
<property name="usb_device.version_bcd" type="int">
272
</property>
<property name="usb_device.vendor_id" type="int">
0
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="usb_device.can_wake_up" type="bool">
True
</property>
<property name="usb_device.product_id" type="int">
0
</property>
<property name="usb_device.bus_number" type="int">
2
</property>
<property name="usb_device.max_power" type="int">
0
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/002/001
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.1/usb2
</property>
</device>
<device id="85" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Hub Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
hub
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0
</property>
<property name="usb.speed_bcd" type="int">
4608
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-0:1.0
</property>
<property name="usb.linux.device_number" type="int">
1
</property>
<property name="usb.serial" type="str">
0000:00:1d.1
</property>
<property name="usb.speed" type="float">
12.0
</property>
<property name="usb.device_class" type="int">
9
</property>
<property name="usb.device_protocol" type="int">
0
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
518
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
1.1
</property>
<property name="usb.num_ports" type="int">
2
</property>
<property name="usb.product" type="str">
USB Hub Interface
</property>
<property name="usb.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb.is_self_powered" type="bool">
True
</property>
<property name="usb.version_bcd" type="int">
272
</property>
<property name="usb.vendor_id" type="int">
0
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
0
</property>
<property name="usb.interface.class" type="int">
9
</property>
<property name="usb.interface.subclass" type="int">
0
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
True
</property>
<property name="usb.product_id" type="int">
0
</property>
<property name="usb.bus_number" type="int">
2
</property>
<property name="usb.max_power" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-0:1.0
</property>
</device>
<device id="86" udi="/org/freedesktop/Hal/devices/pci_8086_27c8">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #1
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
uhci_hcd
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c8
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) USB UHCI Controller #1
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10184
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
3
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
12
</property>
<property name="pci.subsys_product_id" type="int">
20484
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.0
</property>
</device>
<device id="87" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0">
<property name="info.subsystem" type="str">
usb_device
</property>
<property name="info.product" type="str">
UHCI Host Controller
</property>
<property name="info.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27c8
</property>
<property name="info.bus" type="str">
usb_device
</property>
<property name="info.linux.driver" type="str">
usb
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0
</property>
<property name="usb_device.speed_bcd" type="int">
4608
</property>
<property name="usb_device.configuration_value" type="int">
1
</property>
<property name="usb_device.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.0/usb1
</property>
<property name="usb_device.linux.device_number" type="int">
1
</property>
<property name="usb_device.serial" type="str">
0000:00:1d.0
</property>
<property name="usb_device.speed" type="float">
12.0
</property>
<property name="usb_device.device_class" type="int">
9
</property>
<property name="usb_device.device_protocol" type="int">
0
</property>
<property name="usb_device.device_subclass" type="int">
0
</property>
<property name="usb_device.device_revision_bcd" type="int">
518
</property>
<property name="usb_device.num_configurations" type="int">
1
</property>
<property name="usb_device.version" type="float">
1.1
</property>
<property name="usb_device.num_ports" type="int">
2
</property>
<property name="usb_device.product" type="str">
UHCI Host Controller
</property>
<property name="usb_device.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb_device.is_self_powered" type="bool">
True
</property>
<property name="usb_device.version_bcd" type="int">
272
</property>
<property name="usb_device.vendor_id" type="int">
0
</property>
<property name="usb_device.num_interfaces" type="int">
1
</property>
<property name="usb_device.can_wake_up" type="bool">
True
</property>
<property name="usb_device.product_id" type="int">
0
</property>
<property name="usb_device.bus_number" type="int">
1
</property>
<property name="usb_device.max_power" type="int">
0
</property>
<property name="linux.device_file" type="str">
/dev/bus/usb/001/001
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.0/usb1
</property>
</device>
<device id="88" udi="/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0">
<property name="info.subsystem" type="str">
usb
</property>
<property name="info.product" type="str">
USB Hub Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0
</property>
<property name="info.bus" type="str">
usb
</property>
<property name="info.linux.driver" type="str">
hub
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0
</property>
<property name="usb.speed_bcd" type="int">
4608
</property>
<property name="usb.configuration_value" type="int">
1
</property>
<property name="usb.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-0:1.0
</property>
<property name="usb.linux.device_number" type="int">
1
</property>
<property name="usb.serial" type="str">
0000:00:1d.0
</property>
<property name="usb.speed" type="float">
12.0
</property>
<property name="usb.device_class" type="int">
9
</property>
<property name="usb.device_protocol" type="int">
0
</property>
<property name="usb.device_subclass" type="int">
0
</property>
<property name="usb.device_revision_bcd" type="int">
518
</property>
<property name="usb.num_configurations" type="int">
1
</property>
<property name="usb.version" type="float">
1.1
</property>
<property name="usb.num_ports" type="int">
2
</property>
<property name="usb.product" type="str">
USB Hub Interface
</property>
<property name="usb.vendor" type="str">
Linux 2.6.24-19-generic uhci_hcd
</property>
<property name="usb.is_self_powered" type="bool">
True
</property>
<property name="usb.version_bcd" type="int">
272
</property>
<property name="usb.vendor_id" type="int">
0
</property>
<property name="usb.num_interfaces" type="int">
1
</property>
<property name="usb.interface.protocol" type="int">
0
</property>
<property name="usb.interface.class" type="int">
9
</property>
<property name="usb.interface.subclass" type="int">
0
</property>
<property name="usb.interface.number" type="int">
0
</property>
<property name="usb.can_wake_up" type="bool">
True
</property>
<property name="usb.product_id" type="int">
0
</property>
<property name="usb.bus_number" type="int">
1
</property>
<property name="usb.max_power" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
usb
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-0:1.0
</property>
</device>
<device id="89" udi="/org/freedesktop/Hal/devices/pci_8086_27d2">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) PCI Express Port 2
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
pcieport-driver
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d2
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) PCI Express Port 2
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10194
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.device_subclass" type="int">
4
</property>
<property name="pci.subsys_vendor_id" type="int">
0
</property>
<property name="pci.device_class" type="int">
6
</property>
<property name="pci.subsys_product_id" type="int">
0
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.1
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.1
</property>
</device>
<device id="90" udi="/org/freedesktop/Hal/devices/pci_10ec_8168">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
RTL8111/8168B PCI Express Gigabit Ethernet controller
</property>
<property name="info.vendor" type="str">
Realtek Semiconductor Co., Ltd.
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d2
</property>
<property name="info.linux.driver" type="str">
r8169
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_10ec_8168
</property>
<property name="pci.product" type="str">
RTL8111/8168B PCI Express Gigabit Ethernet controller
</property>
<property name="pci.vendor_id" type="int">
4332
</property>
<property name="pci.vendor" type="str">
Realtek Semiconductor Co., Ltd.
</property>
<property name="pci.product_id" type="int">
33128
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
0
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
2
</property>
<property name="pci.subsys_product_id" type="int">
57344
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0
</property>
</device>
<device id="91" udi="/org/freedesktop/Hal/devices/net_00_1d_7d_74_6e_5b">
<property name="info.category" type="str">
net.80203
</property>
<property name="info.product" type="str">
Networking Interface
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_10ec_8168
</property>
<property name="info.interfaces" type="list">
<value type="str">
org.freedesktop.Hal.Device.WakeOnLan
</value>
</property>
<property name="info.capabilities" type="list">
<value type="str">
net
</value>
<value type="str">
net.80203
</value>
<value type="str">
wake_on_lan
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/net_00_1d_7d_74_6e_5b
</property>
<property name="org.freedesktop.Hal.Device.WakeOnLan.method_signatures" type="list">
<value type="str">

</value>
<value type="str">

</value>
<value type="str">
b
</value>
</property>
<property name="org.freedesktop.Hal.Device.WakeOnLan.method_execpaths" type="list">
<value type="str">
hal-system-wol-supported
</value>
<value type="str">
hal-system-wol-enabled
</value>
<value type="str">
hal-system-wol-enable
</value>
</property>
<property name="org.freedesktop.Hal.Device.WakeOnLan.method_argnames" type="list">
<value type="str">

</value>
<value type="str">

</value>
<value type="str">
enable
</value>
</property>
<property name="org.freedesktop.Hal.Device.WakeOnLan.method_names" type="list">
<value type="str">
GetSupported
</value>
<value type="str">
GetEnabled
</value>
<value type="str">
SetEnabled
</value>
</property>
<property name="net.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_10ec_8168
</property>
<property name="net.arp_proto_hw_id" type="int">
1
</property>
<property name="net.address" type="str">
00:1d:7d:74:6e:5b
</property>
<property name="net.80203.mac_address" type="long">
126658834011
</property>
<property name="net.physical_device" type="str">
/org/freedesktop/Hal/devices/pci_10ec_8168
</property>
<property name="net.linux.ifindex" type="int">
2
</property>
<property name="net.interface" type="str">
eth0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
net
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0
</property>
</device>
<device id="92" udi="/org/freedesktop/Hal/devices/pci_8086_27d0">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) PCI Express Port 1
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
pcieport-driver
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d0
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) PCI Express Port 1
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10192
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.device_subclass" type="int">
4
</property>
<property name="pci.subsys_vendor_id" type="int">
0
</property>
<property name="pci.device_class" type="int">
6
</property>
<property name="pci.subsys_product_id" type="int">
0
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1c.0
</property>
</device>
<device id="93" udi="/org/freedesktop/Hal/devices/pci_8086_27d8">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82801G (ICH7 Family) High Definition Audio Controller
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
HDA Intel
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8
</property>
<property name="pci.product" type="str">
82801G (ICH7 Family) High Definition Audio Controller
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10200
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
3
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
4
</property>
<property name="pci.subsys_product_id" type="int">
40962
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0
</property>
</device>
<device id="94" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0">
<property name="info.category" type="str">
sound
</property>
<property name="info.product" type="str">
HDA Intel Sound Card
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8
</property>
<property name="info.capabilities" type="list">
<value type="str">
sound
</value>
</property>
<property name="sound.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8
</property>
<property name="sound.card_id" type="str">
HDA Intel
</property>
<property name="sound.card" type="int">
0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0
</property>
</device>
<device id="95" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_1">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
ALC662 Digital ALSA Playback Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_1
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/pcmC0D1p
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D1p
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/pcmC0D1p
</property>
<property name="alsa.device_file" type="str">
/dev/snd/pcmC0D1p
</property>
<property name="alsa.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="alsa.card_id" type="str">
HDA Intel
</property>
<property name="alsa.pcm_class" type="str">
generic
</property>
<property name="alsa.device" type="int">
1
</property>
<property name="alsa.type" type="str">
playback
</property>
<property name="alsa.card" type="int">
0
</property>
<property name="alsa.device_id" type="str">
ALC662 Digital
</property>
</device>
<device id="96" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
ALC662 Analog ALSA Playback Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/pcmC0D0p
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/pcmC0D0p
</property>
<property name="alsa.device_file" type="str">
/dev/snd/pcmC0D0p
</property>
<property name="alsa.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="alsa.card_id" type="str">
HDA Intel
</property>
<property name="alsa.pcm_class" type="str">
generic
</property>
<property name="alsa.device" type="int">
0
</property>
<property name="alsa.type" type="str">
playback
</property>
<property name="alsa.card" type="int">
0
</property>
<property name="alsa.device_id" type="str">
ALC662 Analog
</property>
</device>
<device id="97" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
ALC662 Analog ALSA Capture Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/pcmC0D0c
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/pcmC0D0c
</property>
<property name="alsa.device_file" type="str">
/dev/snd/pcmC0D0c
</property>
<property name="alsa.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="alsa.card_id" type="str">
HDA Intel
</property>
<property name="alsa.pcm_class" type="str">
generic
</property>
<property name="alsa.device" type="int">
0
</property>
<property name="alsa.type" type="str">
capture
</property>
<property name="alsa.card" type="int">
0
</property>
<property name="alsa.device_id" type="str">
ALC662 Analog
</property>
</device>
<device id="98" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1">
<property name="info.category" type="str">
oss
</property>
<property name="info.product" type="str">
ALC662 Analog OSS Control Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
oss
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="oss.device_file" type="str">
/dev/mixer
</property>
<property name="oss.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="oss.card_id" type="str">
HDA Intel
</property>
<property name="oss.type" type="str">
mixer
</property>
<property name="oss.card" type="int">
0
</property>
<property name="oss.device_id" type="str">
ALC662 Analog
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/mixer
</property>
<property name="linux.device_file" type="str">
/dev/mixer
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer
</property>
</device>
<device id="99" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_hw_specific_2">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
HDA Intel ALSA hardware specific Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_hw_specific_2
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/hwC0D2
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D2
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/hwC0D2
</property>
<property name="alsa.device_file" type="str">
/dev/snd/hwC0D2
</property>
<property name="alsa.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="alsa.card_id" type="str">
HDA Intel
</property>
<property name="alsa.device" type="int">
2
</property>
<property name="alsa.type" type="str">
hw_specific
</property>
<property name="alsa.card" type="int">
0
</property>
</device>
<device id="100" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0">
<property name="info.category" type="str">
oss
</property>
<property name="info.product" type="str">
ALC662 Analog OSS PCM Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
oss
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="oss.device_file" type="str">
/dev/dsp
</property>
<property name="oss.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="oss.card_id" type="str">
HDA Intel
</property>
<property name="oss.device" type="int">
0
</property>
<property name="oss.type" type="str">
pcm
</property>
<property name="oss.card" type="int">
0
</property>
<property name="oss.device_id" type="str">
ALC662 Analog
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/dsp
</property>
<property name="linux.device_file" type="str">
/dev/dsp
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp
</property>
</device>
<device id="101" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1">
<property name="info.category" type="str">
alsa
</property>
<property name="info.product" type="str">
HDA Intel ALSA Control Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
alsa
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="linux.device_file" type="str">
/dev/snd/controlC0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/snd/controlC0
</property>
<property name="alsa.device_file" type="str">
/dev/snd/controlC0
</property>
<property name="alsa.type" type="str">
control
</property>
<property name="alsa.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="alsa.card_id" type="str">
HDA Intel
</property>
<property name="alsa.card" type="int">
0
</property>
</device>
<device id="102" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0">
<property name="info.category" type="str">
oss
</property>
<property name="info.product" type="str">
ALC662 Analog OSS PCM Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
oss
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="oss.device_file" type="str">
/dev/audio
</property>
<property name="oss.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="oss.card_id" type="str">
HDA Intel
</property>
<property name="oss.device" type="int">
0
</property>
<property name="oss.type" type="str">
pcm
</property>
<property name="oss.card" type="int">
0
</property>
<property name="oss.device_id" type="str">
ALC662 Analog
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/audio
</property>
<property name="linux.device_file" type="str">
/dev/audio
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio
</property>
</device>
<device id="103" udi="/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_1">
<property name="info.category" type="str">
oss
</property>
<property name="info.product" type="str">
ALC662 Analog OSS PCM Device
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="info.capabilities" type="list">
<value type="str">
oss
</value>
<value type="str">
access_control
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_1
</property>
<property name="info.callouts.add" type="list">
<value type="str">
hal-acl-tool --add-device
</value>
</property>
<property name="info.callouts.remove" type="list">
<value type="str">
hal-acl-tool --remove-device
</value>
</property>
<property name="oss.device_file" type="str">
/dev/adsp
</property>
<property name="oss.originating_device" type="str">
/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0
</property>
<property name="oss.card_id" type="str">
HDA Intel
</property>
<property name="oss.device" type="int">
1
</property>
<property name="oss.type" type="str">
pcm
</property>
<property name="oss.card" type="int">
0
</property>
<property name="oss.device_id" type="str">
ALC662 Analog
</property>
<property name="access_control.type" type="str">
sound
</property>
<property name="access_control.file" type="str">
/dev/adsp
</property>
<property name="linux.device_file" type="str">
/dev/adsp
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
sound
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/adsp
</property>
</device>
<device id="104" udi="/org/freedesktop/Hal/devices/pci_8086_2772">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82945G/GZ Integrated Graphics Controller
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_2772
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="pci.product" type="str">
82945G/GZ Integrated Graphics Controller
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10098
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
0
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
3
</property>
<property name="pci.subsys_product_id" type="int">
53248
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:02.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:02.0
</property>
</device>
<device id="105" udi="/org/freedesktop/Hal/devices/pci_8086_2772_drm_i915_card0">
<property name="info.category" type="str">
drm
</property>
<property name="info.product" type="str">
Direct Rendering Manager Device
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/pci_8086_2772
</property>
<property name="info.capabilities" type="list">
<value type="str">
drm
</value>
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_2772_drm_i915_card0
</property>
<property name="drm.dri_library" type="str">
i915
</property>
<property name="linux.device_file" type="str">

</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
drm
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:02.0/drm/card0
</property>
</device>
<device id="106" udi="/org/freedesktop/Hal/devices/pci_8086_2770">
<property name="info.subsystem" type="str">
pci
</property>
<property name="info.product" type="str">
82945G/GZ/P/PL Memory Controller Hub
</property>
<property name="info.vendor" type="str">
Intel Corporation
</property>
<property name="info.parent" type="str">
/org/freedesktop/Hal/devices/computer
</property>
<property name="info.linux.driver" type="str">
agpgart-intel
</property>
<property name="info.udi" type="str">
/org/freedesktop/Hal/devices/pci_8086_2770
</property>
<property name="pci.product" type="str">
82945G/GZ/P/PL Memory Controller Hub
</property>
<property name="pci.vendor_id" type="int">
32902
</property>
<property name="pci.vendor" type="str">
Intel Corporation
</property>
<property name="pci.product_id" type="int">
10096
</property>
<property name="pci.device_protocol" type="int">
0
</property>
<property name="pci.subsys_vendor" type="str">
Giga-byte Technology
</property>
<property name="pci.device_subclass" type="int">
0
</property>
<property name="pci.subsys_vendor_id" type="int">
5208
</property>
<property name="pci.device_class" type="int">
6
</property>
<property name="pci.subsys_product_id" type="int">
20480
</property>
<property name="pci.linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:00.0
</property>
<property name="linux.hotplug_type" type="int">
2
</property>
<property name="linux.subsystem" type="str">
pci
</property>
<property name="linux.sysfs_path" type="str">
/sys/devices/pci0000:00/0000:00:00.0
</property>
</device>
</hal>
<processors>
<processor id="6" name="0">
<property name="bogomips" type="float">
6806.06
</property>
<property name="cache_size" type="int">
2097152
</property>
<property name="clflush_size" type="int">
64
</property>
<property name="coma_bug" type="bool">
False
</property>
<property name="core_id" type="int">
0
</property>
<property name="cpu_cores" type="int">
2
</property>
<property name="cpu_family" type="int">
15
</property>
<property name="cpu_mhz" type="float">
3400.218
</property>
<property name="cpuid_level" type="int">
6
</property>
<property name="f00f_bug" type="bool">
False
</property>
<property name="fdiv_bug" type="bool">
False
</property>
<property name="flags" type="list">
<value type="str">
fpu
</value>
<value type="str">
vme
</value>
<value type="str">
de
</value>
<value type="str">
pse
</value>
<value type="str">
tsc
</value>
<value type="str">
msr
</value>
<value type="str">
pae
</value>
<value type="str">
mce
</value>
<value type="str">
cx8
</value>
<value type="str">
apic
</value>
<value type="str">
sep
</value>
<value type="str">
mtrr
</value>
<value type="str">
pge
</value>
<value type="str">
mca
</value>
<value type="str">
cmov
</value>
<value type="str">
pat
</value>
<value type="str">
pse36
</value>
<value type="str">
clflush
</value>
<value type="str">
dts
</value>
<value type="str">
acpi
</value>
<value type="str">
mmx
</value>
<value type="str">
fxsr
</value>
<value type="str">
sse
</value>
<value type="str">
sse2
</value>
<value type="str">
ss
</value>
<value type="str">
ht
</value>
<value type="str">
tm
</value>
<value type="str">
pbe
</value>
<value type="str">
nx
</value>
<value type="str">
lm
</value>
<value type="str">
constant_tsc
</value>
<value type="str">
pebs
</value>
<value type="str">
bts
</value>
<value type="str">
sync_rdtsc
</value>
<value type="str">
pni
</value>
<value type="str">
monitor
</value>
<value type="str">
ds_cpl
</value>
<value type="str">
est
</value>
<value type="str">
cid
</value>
<value type="str">
cx16
</value>
<value type="str">
xtpr
</value>
<value type="str">
lahf_lm
</value>
</property>
<property name="fpu" type="bool">
True
</property>
<property name="fpu_exception" type="bool">
True
</property>
<property name="hlt_bug" type="bool">
False
</property>
<property name="model" type="int">
6
</property>
<property name="model_name" type="str">
Intel(R) Pentium(R) D CPU 3.40GHz
</property>
<property name="physical_id" type="int">
0
</property>
<property name="siblings" type="int">
2
</property>
<property name="stepping" type="int">
4
</property>
<property name="vendor_id" type="str">
GenuineIntel
</property>
<property name="wp" type="bool">
True
</property>
</processor>
<processor id="7" name="1">
<property name="bogomips" type="float">
6800.31
</property>
<property name="cache_size" type="int">
2097152
</property>
<property name="clflush_size" type="int">
64
</property>
<property name="coma_bug" type="bool">
False
</property>
<property name="core_id" type="int">
1
</property>
<property name="cpu_cores" type="int">
2
</property>
<property name="cpu_family" type="int">
15
</property>
<property name="cpu_mhz" type="float">
3400.218
</property>
<property name="cpuid_level" type="int">
6
</property>
<property name="f00f_bug" type="bool">
False
</property>
<property name="fdiv_bug" type="bool">
False
</property>
<property name="flags" type="list">
<value type="str">
fpu
</value>
<value type="str">
vme
</value>
<value type="str">
de
</value>
<value type="str">
pse
</value>
<value type="str">
tsc
</value>
<value type="str">
msr
</value>
<value type="str">
pae
</value>
<value type="str">
mce
</value>
<value type="str">
cx8
</value>
<value type="str">
apic
</value>
<value type="str">
sep
</value>
<value type="str">
mtrr
</value>
<value type="str">
pge
</value>
<value type="str">
mca
</value>
<value type="str">
cmov
</value>
<value type="str">
pat
</value>
<value type="str">
pse36
</value>
<value type="str">
clflush
</value>
<value type="str">
dts
</value>
<value type="str">
acpi
</value>
<value type="str">
mmx
</value>
<value type="str">
fxsr
</value>
<value type="str">
sse
</value>
<value type="str">
sse2
</value>
<value type="str">
ss
</value>
<value type="str">
ht
</value>
<value type="str">
tm
</value>
<value type="str">
pbe
</value>
<value type="str">
nx
</value>
<value type="str">
lm
</value>
<value type="str">
constant_tsc
</value>
<value type="str">
pebs
</value>
<value type="str">
bts
</value>
<value type="str">
sync_rdtsc
</value>
<value type="str">
pni
</value>
<value type="str">
monitor
</value>
<value type="str">
ds_cpl
</value>
<value type="str">
est
</value>
<value type="str">
cid
</value>
<value type="str">
cx16
</value>
<value type="str">
xtpr
</value>
<value type="str">
lahf_lm
</value>
</property>
<property name="fpu" type="bool">
True
</property>
<property name="fpu_exception" type="bool">
True
</property>
<property name="hlt_bug" type="bool">
False
</property>
<property name="model" type="int">
6
</property>
<property name="model_name" type="str">
Intel(R) Pentium(R) D CPU 3.40GHz
</property>
<property name="physical_id" type="int">
0
</property>
<property name="siblings" type="int">
2
</property>
<property name="stepping" type="int">
4
</property>
<property name="vendor_id" type="str">
GenuineIntel
</property>
<property name="wp" type="bool">
True
</property>
</processor>
</processors>
</hardware>
<questions>
<question name="network">
<answer type="multiple_choice">
pass
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
<question name="resolution">
<answer type="multiple_choice">
skip
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
<question name="keyboard">
<answer type="multiple_choice">
skip
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
<question name="video">
<answer type="multiple_choice">
skip
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
<question name="internet">
<answer type="multiple_choice">
fail
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
<question name="audio">
<answer type="multiple_choice">
skip
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
<question name="mouse">
<answer type="multiple_choice">
skip
</answer>
<answer_choices>
<value type="str">
pass
</value>
<value type="str">
fail
</value>
<value type="str">
skip
</value>
</answer_choices>
<comment>

</comment>
</question>
</questions>
<software>
<lsbrelease>
<property name="release" type="str">
8.04
</property>
<property name="codename" type="str">
hardy
</property>
<property name="distributor_id" type="str">
Ubuntu
</property>
<property name="description" type="str">
Ubuntu 8.04.1
</property>
</lsbrelease>
<packages>
<package id="592" name="acl">
<property name="description" type="str">
Access control list utilities
</property>
<property name="version" type="str">
2.2.45-1
</property>
</package>
<package id="593" name="acpi">
<property name="description" type="str">
displays information on ACPI devices
</property>
<property name="version" type="str">
0.09-3ubuntu1
</property>
</package>
<package id="594" name="acpi-support">
<property name="description" type="str">
a collection of useful events for acpi
</property>
<property name="version" type="str">
0.109
</property>
</package>
<package id="595" name="acpid">
<property name="description" type="str">
Utilities for using ACPI power management
</property>
<property name="version" type="str">
1.0.4-5ubuntu9
</property>
</package>
<package id="596" name="adduser">
<property name="description" type="str">
add and remove users and groups
</property>
<property name="version" type="str">
3.105ubuntu1
</property>
</package>
<package id="597" name="alacarte">
<property name="description" type="str">
easy GNOME menu editing tool
</property>
<property name="version" type="str">
0.11.5-0ubuntu1
</property>
</package>
<package id="598" name="alsa-base">
<property name="description" type="str">
ALSA driver configuration files
</property>
<property name="version" type="str">
1.0.16-0ubuntu4
</property>
</package>
<package id="599" name="alsa-utils">
<property name="description" type="str">
ALSA utilities
</property>
<property name="version" type="str">
1.0.15-3ubuntu2
</property>
</package>
<package id="600" name="anacron">
<property name="description" type="str">
cron-like program that doesn't go by time
</property>
<property name="version" type="str">
2.3-13ubuntu2
</property>
</package>
<package id="601" name="apmd">
<property name="description" type="str">
Utilities for Advanced Power Management (APM)
</property>
<property name="version" type="str">
3.2.2-8.1ubuntu1
</property>
</package>
<package id="602" name="app-install-data">
<property name="description" type="str">
Ubuntu applications (data files)
</property>
<property name="version" type="str">
0.5.10.3
</property>
</package>
<package id="603" name="app-install-data-commercial">
<property name="description" type="str">
Application Installer (data files for commercial applications)
</property>
<property name="version" type="str">
9
</property>
</package>
<package id="604" name="apparmor">
<property name="description" type="str">
User-space parser utility for AppArmor
</property>
<property name="version" type="str">
2.1+1075-0ubuntu9.1
</property>
</package>
<package id="605" name="apparmor-utils">
<property name="description" type="str">
Utilities for controlling AppArmor
</property>
<property name="version" type="str">
2.1+1075-0ubuntu9.1
</property>
</package>
<package id="606" name="apport">
<property name="description" type="str">
automatically generate crash reports for debugging
</property>
<property name="version" type="str">
0.108.2
</property>
</package>
<package id="607" name="apport-gtk">
<property name="description" type="str">
GTK+ frontend for the apport crash report system
</property>
<property name="version" type="str">
0.108.2
</property>
</package>
<package id="608" name="apt">
<property name="description" type="str">
Advanced front-end for dpkg
</property>
<property name="version" type="str">
0.7.9ubuntu17
</property>
</package>
<package id="609" name="apt-utils">
<property name="description" type="str">
APT utility programs
</property>
<property name="version" type="str">
0.7.9ubuntu17
</property>
</package>
<package id="610" name="aptitude">
<property name="description" type="str">
terminal-based package manager
</property>
<property name="version" type="str">
0.4.9-2ubuntu5
</property>
</package>
<package id="611" name="apturl">
<property name="description" type="str">
Install package with the apt protocol
</property>
<property name="version" type="str">
0.2.2ubuntu1
</property>
</package>
<package id="612" name="aspell">
<property name="description" type="str">
GNU Aspell spell-checker
</property>
<property name="version" type="str">
0.60.5-1ubuntu2
</property>
</package>
<package id="613" name="aspell-en">
<property name="description" type="str">
English dictionary for GNU Aspell
</property>
<property name="version" type="str">
6.0-0-5.1
</property>
</package>
<package id="614" name="at">
<property name="description" type="str">
Delayed job execution and batch processing
</property>
<property name="version" type="str">
3.1.10ubuntu4
</property>
</package>
<package id="615" name="at-spi">
<property name="description" type="str">
Assistive Technology Service Provider Interface
</property>
<property name="version" type="str">
1.22.1-0ubuntu1
</property>
</package>
<package id="616" name="avahi-autoipd">
<property name="description" type="str">
Avahi IPv4LL network address configuration daemon
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="617" name="avahi-daemon">
<property name="description" type="str">
Avahi mDNS/DNS-SD daemon
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="618" name="base-files">
<property name="description" type="str">
Debian base system miscellaneous files
</property>
<property name="version" type="str">
4.0.1ubuntu5.8.04.2
</property>
</package>
<package id="619" name="base-passwd">
<property name="description" type="str">
Debian base system master password and group files
</property>
<property name="version" type="str">
3.5.16
</property>
</package>
<package id="620" name="bash">
<property name="description" type="str">
The GNU Bourne Again SHell
</property>
<property name="version" type="str">
3.2-0ubuntu18
</property>
</package>
<package id="621" name="bash-completion">
<property name="description" type="str">
programmable completion for the bash shell
</property>
<property name="version" type="str">
20060301-3ubuntu3
</property>
</package>
<package id="622" name="bc">
<property name="description" type="str">
The GNU bc arbitrary precision calculator language
</property>
<property name="version" type="str">
1.06.94-3ubuntu1
</property>
</package>
<package id="623" name="belocs-locales-bin">
<property name="description" type="str">
tools for compiling locale data files
</property>
<property name="version" type="str">
2.4-2.2ubuntu7
</property>
</package>
<package id="624" name="bind9-host">
<property name="description" type="str">
Version of 'host' bundled with BIND 9.X
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="625" name="binutils">
<property name="description" type="str">
The GNU assembler, linker and binary utilities
</property>
<property name="version" type="str">
2.18.1~cvs20080103-0ubuntu1
</property>
</package>
<package id="626" name="binutils-static">
<property name="description" type="str">
statically linked binutils tools
</property>
<property name="version" type="str">
2.18.1~cvs20080103-0ubuntu1
</property>
</package>
<package id="627" name="bluez-audio">
<property name="description" type="str">
Bluetooth audio support
</property>
<property name="version" type="str">
3.26-0ubuntu6
</property>
</package>
<package id="628" name="bluez-cups">
<property name="description" type="str">
Bluetooth printer driver for CUPS
</property>
<property name="version" type="str">
3.26-0ubuntu6
</property>
</package>
<package id="629" name="bluez-gnome">
<property name="description" type="str">
Bluetooth utilities for GNOME
</property>
<property name="version" type="str">
0.25-0ubuntu1
</property>
</package>
<package id="630" name="bluez-utils">
<property name="description" type="str">
Bluetooth tools and daemons
</property>
<property name="version" type="str">
3.26-0ubuntu6
</property>
</package>
<package id="631" name="bogofilter">
<property name="description" type="str">
a fast Bayesian spam filter (dummy package)
</property>
<property name="version" type="str">
1.1.5-2ubuntu5
</property>
</package>
<package id="632" name="bogofilter-bdb">
<property name="description" type="str">
a fast Bayesian spam filter (Berkeley DB)
</property>
<property name="version" type="str">
1.1.5-2ubuntu5
</property>
</package>
<package id="633" name="bogofilter-common">
<property name="description" type="str">
a fast Bayesian spam filter (common files)
</property>
<property name="version" type="str">
1.1.5-2ubuntu5
</property>
</package>
<package id="634" name="brasero">
<property name="description" type="str">
CD/DVD burning application for GNOME
</property>
<property name="version" type="str">
0.7.1-3ubuntu1
</property>
</package>
<package id="635" name="brltty">
<property name="description" type="str">
Access software for a blind person using a braille display
</property>
<property name="version" type="str">
3.9-6ubuntu1
</property>
</package>
<package id="636" name="brltty-x11">
<property name="description" type="str">
Access software for a blind person using a braille display
</property>
<property name="version" type="str">
3.9-6ubuntu1
</property>
</package>
<package id="637" name="bsdmainutils">
<property name="description" type="str">
collection of more utilities from FreeBSD
</property>
<property name="version" type="str">
6.1.10ubuntu2
</property>
</package>
<package id="638" name="bsdutils">
<property name="description" type="str">
Basic utilities from 4.4BSD-Lite
</property>
<property name="version" type="str">
1:2.13.1-5ubuntu2
</property>
</package>
<package id="639" name="bug-buddy">
<property name="description" type="str">
GNOME Desktop Environment bug reporting tool
</property>
<property name="version" type="str">
2.22.0+dfsg-2
</property>
</package>
<package id="640" name="busybox-initramfs">
<property name="description" type="str">
Standalone shell setup for initramfs
</property>
<property name="version" type="str">
1:1.1.3-5ubuntu12
</property>
</package>
<package id="641" name="bzip2">
<property name="description" type="str">
high-quality block-sorting file compressor - utilities
</property>
<property name="version" type="str">
1.0.4-2ubuntu4
</property>
</package>
<package id="642" name="ca-certificates">
<property name="description" type="str">
Common CA Certificates PEM files
</property>
<property name="version" type="str">
20070303-0ubuntu3
</property>
</package>
<package id="643" name="capplets-data">
<property name="description" type="str">
configuration applets for GNOME 2 - data files
</property>
<property name="version" type="str">
1:2.22.1-0ubuntu4.1
</property>
</package>
<package id="644" name="cdparanoia">
<property name="description" type="str">
audio extraction tool for sampling CDs
</property>
<property name="version" type="str">
3.10+debian~pre0-6
</property>
</package>
<package id="645" name="cdrdao">
<property name="description" type="str">
records CDs in Disk-At-Once (DAO) mode
</property>
<property name="version" type="str">
1:1.2.2-8ubuntu3
</property>
</package>
<package id="646" name="cli-common">
<property name="description" type="str">
common files between all CLI packages
</property>
<property name="version" type="str">
0.5.6
</property>
</package>
<package id="647" name="command-not-found">
<property name="description" type="str">
Suggest installation of packages in interactive bash sessions
</property>
<property name="version" type="str">
0.2.17ubuntu1
</property>
</package>
<package id="648" name="command-not-found-data">
<property name="description" type="str">
Set of data files for command-not-found.
</property>
<property name="version" type="str">
0.2.17ubuntu1
</property>
</package>
<package id="649" name="compiz">
<property name="description" type="str">
OpenGL window and compositing manager
</property>
<property name="version" type="str">
1:0.7.4-0ubuntu7
</property>
</package>
<package id="650" name="compiz-core">
<property name="description" type="str">
OpenGL window and compositing manager
</property>
<property name="version" type="str">
1:0.7.4-0ubuntu7
</property>
</package>
<package id="651" name="compiz-fusion-plugins-extra">
<property name="description" type="str">
Collection of extra plugins from OpenCompositing for Compiz
</property>
<property name="version" type="str">
0.7.4-0ubuntu1
</property>
</package>
<package id="652" name="compiz-fusion-plugins-main">
<property name="description" type="str">
Collection of plugins from OpenCompositing for Compiz
</property>
<property name="version" type="str">
0.7.4-0ubuntu5
</property>
</package>
<package id="653" name="compiz-gnome">
<property name="description" type="str">
OpenGL window and compositing manager - GNOME window decorator
</property>
<property name="version" type="str">
1:0.7.4-0ubuntu7
</property>
</package>
<package id="654" name="compiz-plugins">
<property name="description" type="str">
OpenGL window and compositing manager - plugins
</property>
<property name="version" type="str">
1:0.7.4-0ubuntu7
</property>
</package>
<package id="655" name="compizconfig-backend-gconf">
<property name="description" type="str">
Settings library for plugins - OpenCompositing Project
</property>
<property name="version" type="str">
0.7.4-0ubuntu1
</property>
</package>
<package id="656" name="console-setup">
<property name="description" type="str">
Set up the font and the keyboard on the console
</property>
<property name="version" type="str">
1.21ubuntu8
</property>
</package>
<package id="657" name="console-terminus">
<property name="description" type="str">
Fixed-width fonts for fast reading on the Linux console
</property>
<property name="version" type="str">
4.20-6
</property>
</package>
<package id="658" name="console-tools">
<property name="description" type="str">
Linux console and font utilities
</property>
<property name="version" type="str">
1:0.2.3dbs-65ubuntu7
</property>
</package>
<package id="659" name="consolekit">
<property name="description" type="str">
framework for defining and tracking users, sessions and seats
</property>
<property name="version" type="str">
0.2.3-3ubuntu5
</property>
</package>
<package id="660" name="contact-lookup-applet">
<property name="description" type="str">
contact lookup applet for GNOME
</property>
<property name="version" type="str">
0.16-1
</property>
</package>
<package id="661" name="coreutils">
<property name="description" type="str">
The GNU core utilities
</property>
<property name="version" type="str">
6.10-3ubuntu2
</property>
</package>
<package id="662" name="cpio">
<property name="description" type="str">
GNU cpio -- a program to manage archives of files
</property>
<property name="version" type="str">
2.9-6ubuntu1
</property>
</package>
<package id="663" name="cpp">
<property name="description" type="str">
The GNU C preprocessor (cpp)
</property>
<property name="version" type="str">
4:4.2.3-1ubuntu6
</property>
</package>
<package id="664" name="cpp-4.2">
<property name="description" type="str">
The GNU C preprocessor
</property>
<property name="version" type="str">
4.2.3-2ubuntu7
</property>
</package>
<package id="665" name="cron">
<property name="description" type="str">
management of regular background processing
</property>
<property name="version" type="str">
3.0pl1-100ubuntu2
</property>
</package>
<package id="666" name="cups-pdf">
<property name="description" type="str">
PDF printer for CUPS
</property>
<property name="version" type="str">
2.4.6-4ubuntu2
</property>
</package>
<package id="667" name="cupsddk">
<property name="description" type="str">
CUPS Driver Development Kit
</property>
<property name="version" type="str">
1.2.0-0ubuntu1
</property>
</package>
<package id="668" name="cupsddk-drivers">
<property name="description" type="str">
CUPS Driver Development Kit - Driver files
</property>
<property name="version" type="str">
1.2.0-0ubuntu1
</property>
</package>
<package id="669" name="cupsys">
<property name="description" type="str">
Common UNIX Printing System(tm) - server
</property>
<property name="version" type="str">
1.3.7-1ubuntu3
</property>
</package>
<package id="670" name="cupsys-bsd">
<property name="description" type="str">
Common UNIX Printing System(tm) - BSD commands
</property>
<property name="version" type="str">
1.3.7-1ubuntu3
</property>
</package>
<package id="671" name="cupsys-client">
<property name="description" type="str">
Common UNIX Printing System(tm) - client programs (SysV)
</property>
<property name="version" type="str">
1.3.7-1ubuntu3
</property>
</package>
<package id="672" name="cupsys-common">
<property name="description" type="str">
Common UNIX Printing System(tm) - common files
</property>
<property name="version" type="str">
1.3.7-1ubuntu3
</property>
</package>
<package id="673" name="cupsys-driver-gutenprint">
<property name="description" type="str">
printer drivers for CUPS
</property>
<property name="version" type="str">
5.0.2-2ubuntu1
</property>
</package>
<package id="674" name="dash">
<property name="description" type="str">
POSIX-compliant shell
</property>
<property name="version" type="str">
0.5.4-8ubuntu1
</property>
</package>
<package id="675" name="dbus">
<property name="description" type="str">
simple interprocess messaging system
</property>
<property name="version" type="str">
1.1.20-1ubuntu2
</property>
</package>
<package id="676" name="dbus-x11">
<property name="description" type="str">
simple interprocess messaging system (X11 deps)
</property>
<property name="version" type="str">
1.1.20-1ubuntu2
</property>
</package>
<package id="677" name="dc">
<property name="description" type="str">
The GNU dc arbitrary precision reverse-polish calculator
</property>
<property name="version" type="str">
1.06.94-3ubuntu1
</property>
</package>
<package id="678" name="dcraw">
<property name="description" type="str">
decode raw digital camera images
</property>
<property name="version" type="str">
8.80-1
</property>
</package>
<package id="679" name="debconf">
<property name="description" type="str">
Debian configuration management system
</property>
<property name="version" type="str">
1.5.20
</property>
</package>
<package id="680" name="debconf-i18n">
<property name="description" type="str">
full internationalization support for debconf
</property>
<property name="version" type="str">
1.5.20
</property>
</package>
<package id="681" name="debianutils">
<property name="description" type="str">
Miscellaneous utilities specific to Debian
</property>
<property name="version" type="str">
2.28.2-0ubuntu1
</property>
</package>
<package id="682" name="defoma">
<property name="description" type="str">
Debian Font Manager -- automatic font configuration framework
</property>
<property name="version" type="str">
0.11.10-0.2
</property>
</package>
<package id="683" name="deskbar-applet">
<property name="description" type="str">
universal search and navigation bar for GNOME
</property>
<property name="version" type="str">
2.22.2.1-0ubuntu1
</property>
</package>
<package id="684" name="desktop-file-utils">
<property name="description" type="str">
Utilities for .desktop files
</property>
<property name="version" type="str">
0.15-1ubuntu4
</property>
</package>
<package id="685" name="dhcdbd">
<property name="description" type="str">
D-Bus interface to the ISC DHCP client
</property>
<property name="version" type="str">
3.0-1ubuntu1
</property>
</package>
<package id="686" name="dhcp3-client">
<property name="description" type="str">
DHCP client
</property>
<property name="version" type="str">
3.0.6.dfsg-1ubuntu9
</property>
</package>
<package id="687" name="dhcp3-common">
<property name="description" type="str">
common files used by all the dhcp3* packages
</property>
<property name="version" type="str">
3.0.6.dfsg-1ubuntu9
</property>
</package>
<package id="688" name="dictionaries-common">
<property name="description" type="str">
Common utilities for spelling dictionary tools
</property>
<property name="version" type="str">
0.90.0ubuntu2
</property>
</package>
<package id="689" name="diff">
<property name="description" type="str">
File comparison utilities
</property>
<property name="version" type="str">
2.8.1-12ubuntu1
</property>
</package>
<package id="690" name="displayconfig-gtk">
<property name="description" type="str">
Simple tool to change xserver settings
</property>
<property name="version" type="str">
0.3.10
</property>
</package>
<package id="691" name="diveintopython">
<property name="description" type="str">
free Python book for experienced programmers
</property>
<property name="version" type="str">
5.4-2ubuntu2
</property>
</package>
<package id="692" name="dmidecode">
<property name="description" type="str">
Dump Desktop Management Interface data
</property>
<property name="version" type="str">
2.9-1ubuntu1
</property>
</package>
<package id="693" name="dmz-cursor-theme">
<property name="description" type="str">
Style neutral, scalable cursor theme
</property>
<property name="version" type="str">
0.4.1
</property>
</package>
<package id="694" name="dnsutils">
<property name="description" type="str">
Clients provided with BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="695" name="doc-base">
<property name="description" type="str">
utilities to manage online documentation
</property>
<property name="version" type="str">
0.8.7
</property>
</package>
<package id="696" name="docbook-xml">
<property name="description" type="str">
standard XML documentation system, for software and systems
</property>
<property name="version" type="str">
4.5-5
</property>
</package>
<package id="697" name="dosfstools">
<property name="description" type="str">
Utilities to create and check MS-DOS FAT filesystems
</property>
<property name="version" type="str">
2.11-2.3ubuntu1
</property>
</package>
<package id="698" name="dpkg">
<property name="description" type="str">
package maintenance system for Debian
</property>
<property name="version" type="str">
1.14.16.6ubuntu4
</property>
</package>
<package id="699" name="dvd+rw-tools">
<property name="description" type="str">
DVD+-RW/R tools
</property>
<property name="version" type="str">
7.0-9ubuntu1
</property>
</package>
<package id="700" name="e2fslibs">
<property name="description" type="str">
ext2 filesystem libraries
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="701" name="e2fsprogs">
<property name="description" type="str">
ext2 file system utilities and libraries
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="702" name="ed">
<property name="description" type="str">
The classic unix line editor
</property>
<property name="version" type="str">
0.7-1ubuntu1
</property>
</package>
<package id="703" name="eject">
<property name="description" type="str">
ejects CDs and operates CD-Changers under Linux
</property>
<property name="version" type="str">
2.1.5-6
</property>
</package>
<package id="704" name="ekiga">
<property name="description" type="str">
H.323 and SIP compatible VoIP client
</property>
<property name="version" type="str">
2.0.12-0ubuntu2
</property>
</package>
<package id="705" name="eog">
<property name="description" type="str">
Eye of GNOME graphics viewer program
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="706" name="esound-common">
<property name="description" type="str">
Enlightened Sound Daemon - Common files
</property>
<property name="version" type="str">
0.2.38-0ubuntu9
</property>
</package>
<package id="707" name="espeak">
<property name="description" type="str">
A multi-lingual software speech synthesizer
</property>
<property name="version" type="str">
1.36-0ubuntu1
</property>
</package>
<package id="708" name="espeak-data">
<property name="description" type="str">
A multi-lingual software speech synthesizer: speech data files
</property>
<property name="version" type="str">
1.36-0ubuntu1
</property>
</package>
<package id="709" name="ethtool">
<property name="description" type="str">
display or change ethernet card settings
</property>
<property name="version" type="str">
6-0
</property>
</package>
<package id="710" name="evince">
<property name="description" type="str">
Document (postscript, pdf) viewer
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="711" name="evolution">
<property name="description" type="str">
groupware suite with mail client and organizer
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="712" name="evolution-common">
<property name="description" type="str">
architecture independent files for Evolution
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="713" name="evolution-data-server">
<property name="description" type="str">
evolution database backend server
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="714" name="evolution-data-server-common">
<property name="description" type="str">
architecture independent files for Evolution Data Server
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="715" name="evolution-exchange">
<property name="description" type="str">
Exchange plugin for the Evolution groupware suite
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="716" name="evolution-plugins">
<property name="description" type="str">
standard plugins for Evolution
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="717" name="evolution-webcal">
<property name="description" type="str">
webcal: URL handler for GNOME and Evolution
</property>
<property name="version" type="str">
2.21.92-0ubuntu1
</property>
</package>
<package id="718" name="example-content">
<property name="description" type="str">
Ubuntu example content
</property>
<property name="version" type="str">
31
</property>
</package>
<package id="719" name="f-spot">
<property name="description" type="str">
personal photo management application
</property>
<property name="version" type="str">
0.4.3.1-0ubuntu1
</property>
</package>
<package id="720" name="fast-user-switch-applet">
<property name="description" type="str">
Applet for the GNOME panel providing a menu to switch between users
</property>
<property name="version" type="str">
2.22.0-0ubuntu2
</property>
</package>
<package id="721" name="fdutils">
<property name="description" type="str">
Linux floppy utilities
</property>
<property name="version" type="str">
5.5-20060227-1.1
</property>
</package>
<package id="722" name="file">
<property name="description" type="str">
Determines file type using &quot;magic&quot; numbers
</property>
<property name="version" type="str">
4.21-3ubuntu1
</property>
</package>
<package id="723" name="file-roller">
<property name="description" type="str">
an archive manager for GNOME
</property>
<property name="version" type="str">
2.22.3-0ubuntu1
</property>
</package>
<package id="724" name="findutils">
<property name="description" type="str">
utilities for finding files--find, xargs
</property>
<property name="version" type="str">
4.2.32-1ubuntu2
</property>
</package>
<package id="725" name="finger">
<property name="description" type="str">
user information lookup program
</property>
<property name="version" type="str">
0.17-11
</property>
</package>
<package id="726" name="firefox">
<property name="description" type="str">
meta package for the popular mozilla web browser
</property>
<property name="version" type="str">
3.0+nobinonly-0ubuntu0.8.04.1
</property>
</package>
<package id="727" name="firefox-3.0">
<property name="description" type="str">
safe and easy web browser from Mozilla
</property>
<property name="version" type="str">
3.0+nobinonly-0ubuntu0.8.04.1
</property>
</package>
<package id="728" name="firefox-3.0-gnome-support">
<property name="description" type="str">
Support for Gnome in Mozilla Firefox
</property>
<property name="version" type="str">
3.0+nobinonly-0ubuntu0.8.04.1
</property>
</package>
<package id="729" name="firefox-gnome-support">
<property name="description" type="str">
meta package pointing to the latest gnome-support package for firefox
</property>
<property name="version" type="str">
3.0+nobinonly-0ubuntu0.8.04.1
</property>
</package>
<package id="730" name="fontconfig">
<property name="description" type="str">
generic font configuration library - support binaries
</property>
<property name="version" type="str">
2.5.0-2ubuntu3
</property>
</package>
<package id="731" name="fontconfig-config">
<property name="description" type="str">
generic font configuration library - configuration
</property>
<property name="version" type="str">
2.5.0-2ubuntu3
</property>
</package>
<package id="732" name="foo2zjs">
<property name="description" type="str">
Support for printing to ZjStream-based printers
</property>
<property name="version" type="str">
20071205-0ubuntu3
</property>
</package>
<package id="733" name="foomatic-db">
<property name="description" type="str">
OpenPrinting printer support - database
</property>
<property name="version" type="str">
20080211-0ubuntu1
</property>
</package>
<package id="734" name="foomatic-db-engine">
<property name="description" type="str">
OpenPrinting printer support - programs
</property>
<property name="version" type="str">
3.0.2-20070719-0ubuntu4
</property>
</package>
<package id="735" name="foomatic-db-hpijs">
<property name="description" type="str">
OpenPrinting printer support - database for HPIJS driver
</property>
<property name="version" type="str">
20070813-0ubuntu2
</property>
</package>
<package id="736" name="foomatic-filters">
<property name="description" type="str">
OpenPrinting printer support - filters
</property>
<property name="version" type="str">
3.0.2-20071204-0ubuntu2.1
</property>
</package>
<package id="737" name="fortune-mod">
<property name="description" type="str">
provides fortune cookies on demand
</property>
<property name="version" type="str">
1:1.99.1-3ubuntu3
</property>
</package>
<package id="738" name="fortunes-min">
<property name="description" type="str">
Data files containing fortune cookies
</property>
<property name="version" type="str">
1:1.99.1-3ubuntu3
</property>
</package>
<package id="739" name="freeglut3">
<property name="description" type="str">
OpenGL Utility Toolkit
</property>
<property name="version" type="str">
2.4.0-6
</property>
</package>
<package id="740" name="friendly-recovery">
<property name="description" type="str">
Make recovery more user-friendly
</property>
<property name="version" type="str">
0.1.2
</property>
</package>
<package id="741" name="ftp">
<property name="description" type="str">
The FTP client
</property>
<property name="version" type="str">
0.17-16build1
</property>
</package>
<package id="742" name="fuse-utils">
<property name="description" type="str">
Filesystem in USErspace (utilities)
</property>
<property name="version" type="str">
2.7.2-1ubuntu2
</property>
</package>
<package id="743" name="gamin">
<property name="description" type="str">
File and directory monitoring system
</property>
<property name="version" type="str">
0.1.9-2ubuntu2
</property>
</package>
<package id="744" name="gcalctool">
<property name="description" type="str">
A GTK2 desktop calculator
</property>
<property name="version" type="str">
5.22.2-0ubuntu1
</property>
</package>
<package id="745" name="gcc">
<property name="description" type="str">
The GNU C compiler
</property>
<property name="version" type="str">
4:4.2.3-1ubuntu6
</property>
</package>
<package id="746" name="gcc-4.2">
<property name="description" type="str">
The GNU C compiler
</property>
<property name="version" type="str">
4.2.3-2ubuntu7
</property>
</package>
<package id="747" name="gcc-4.2-base">
<property name="description" type="str">
The GNU Compiler Collection (base package)
</property>
<property name="version" type="str">
4.2.3-2ubuntu7
</property>
</package>
<package id="748" name="gconf-editor">
<property name="description" type="str">
An editor for the GConf configuration system
</property>
<property name="version" type="str">
2.22.0-0ubuntu2
</property>
</package>
<package id="749" name="gconf2">
<property name="description" type="str">
GNOME configuration database system (support tools)
</property>
<property name="version" type="str">
2.22.0-0ubuntu3
</property>
</package>
<package id="750" name="gconf2-common">
<property name="description" type="str">
GNOME configuration database system (common files)
</property>
<property name="version" type="str">
2.22.0-0ubuntu3
</property>
</package>
<package id="751" name="gdb">
<property name="description" type="str">
The GNU Debugger
</property>
<property name="version" type="str">
6.8-1ubuntu2
</property>
</package>
<package id="752" name="gdebi">
<property name="description" type="str">
Simple tool to install deb files
</property>
<property name="version" type="str">
0.3.8
</property>
</package>
<package id="753" name="gdebi-core">
<property name="description" type="str">
Simple tool to install deb files
</property>
<property name="version" type="str">
0.3.8
</property>
</package>
<package id="754" name="gdm">
<property name="description" type="str">
GNOME Display Manager
</property>
<property name="version" type="str">
2.20.6-0ubuntu2
</property>
</package>
<package id="755" name="gedit">
<property name="description" type="str">
official text editor of the GNOME desktop environment
</property>
<property name="version" type="str">
2.22.3-0ubuntu1
</property>
</package>
<package id="756" name="gedit-common">
<property name="description" type="str">
official text editor of the GNOME desktop environment (support files)
</property>
<property name="version" type="str">
2.22.3-0ubuntu1
</property>
</package>
<package id="757" name="genisoimage">
<property name="description" type="str">
Creates ISO-9660 CD-ROM filesystem images
</property>
<property name="version" type="str">
9:1.1.6-1ubuntu6
</property>
</package>
<package id="758" name="gettext-base">
<property name="description" type="str">
GNU Internationalization utilities for the base system
</property>
<property name="version" type="str">
0.17-2ubuntu1
</property>
</package>
<package id="759" name="ghostscript">
<property name="description" type="str">
The GPL Ghostscript PostScript/PDF interpreter
</property>
<property name="version" type="str">
8.61.dfsg.1-1ubuntu3
</property>
</package>
<package id="760" name="ghostscript-x">
<property name="description" type="str">
The GPL Ghostscript PostScript/PDF interpreter - X Display support
</property>
<property name="version" type="str">
8.61.dfsg.1-1ubuntu3
</property>
</package>
<package id="761" name="gimp">
<property name="description" type="str">
The GNU Image Manipulation Program
</property>
<property name="version" type="str">
2.4.5-1ubuntu2
</property>
</package>
<package id="762" name="gimp-data">
<property name="description" type="str">
Data files for GIMP
</property>
<property name="version" type="str">
2.4.5-1ubuntu2
</property>
</package>
<package id="763" name="gimp-gnomevfs">
<property name="description" type="str">
GNOME-VFS URI plugin for GIMP
</property>
<property name="version" type="str">
2.4.5-1ubuntu2
</property>
</package>
<package id="764" name="gimp-help-common">
<property name="description" type="str">
Data files for the GIMP documentation
</property>
<property name="version" type="str">
2.4.0-2
</property>
</package>
<package id="765" name="gimp-help-en">
<property name="description" type="str">
Documentation for the GIMP (English)
</property>
<property name="version" type="str">
2.4.0-2
</property>
</package>
<package id="766" name="gimp-python">
<property name="description" type="str">
Python support and plugins for GIMP
</property>
<property name="version" type="str">
2.4.5-1ubuntu2
</property>
</package>
<package id="767" name="gksu">
<property name="description" type="str">
graphical frontend to su
</property>
<property name="version" type="str">
2.0.0-5ubuntu3
</property>
</package>
<package id="768" name="gnome-about">
<property name="description" type="str">
The GNOME about box
</property>
<property name="version" type="str">
1:2.22.2-0ubuntu3
</property>
</package>
<package id="769" name="gnome-accessibility-themes">
<property name="description" type="str">
accessibility themes for the GNOME 2 desktop
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="770" name="gnome-app-install">
<property name="description" type="str">
GNOME Application Installer
</property>
<property name="version" type="str">
0.5.2.8-0ubuntu1
</property>
</package>
<package id="771" name="gnome-applets">
<property name="description" type="str">
Various applets for GNOME 2 panel - binary files
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="772" name="gnome-applets-data">
<property name="description" type="str">
Various applets for GNOME 2 panel - data files
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="773" name="gnome-cards-data">
<property name="description" type="str">
data files for the GNOME card games
</property>
<property name="version" type="str">
1:2.22.2.1-0ubuntu1
</property>
</package>
<package id="774" name="gnome-control-center">
<property name="description" type="str">
utilities to configure the GNOME desktop
</property>
<property name="version" type="str">
1:2.22.1-0ubuntu4.1
</property>
</package>
<package id="775" name="gnome-desktop-data">
<property name="description" type="str">
Common files for GNOME 2 desktop apps
</property>
<property name="version" type="str">
1:2.22.2-0ubuntu3
</property>
</package>
<package id="776" name="gnome-doc-utils">
<property name="description" type="str">
a collection of documentation utilities for the Gnome project
</property>
<property name="version" type="str">
0.12.2-1ubuntu1
</property>
</package>
<package id="777" name="gnome-games">
<property name="description" type="str">
games for the GNOME desktop
</property>
<property name="version" type="str">
1:2.22.2.1-0ubuntu1
</property>
</package>
<package id="778" name="gnome-games-data">
<property name="description" type="str">
data files for the GNOME games
</property>
<property name="version" type="str">
1:2.22.2.1-0ubuntu1
</property>
</package>
<package id="779" name="gnome-icon-theme">
<property name="description" type="str">
GNOME Desktop icon theme
</property>
<property name="version" type="str">
2.22.0-1ubuntu2
</property>
</package>
<package id="780" name="gnome-keyring">
<property name="description" type="str">
GNOME keyring services (daemon and tools)
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="781" name="gnome-mag">
<property name="description" type="str">
a screen magnifier for the GNOME desktop
</property>
<property name="version" type="str">
1:0.15.0-0ubuntu1
</property>
</package>
<package id="782" name="gnome-media">
<property name="description" type="str">
GNOME media utilities
</property>
<property name="version" type="str">
2.22.0-0ubuntu3
</property>
</package>
<package id="783" name="gnome-media-common">
<property name="description" type="str">
GNOME media utilities - common files
</property>
<property name="version" type="str">
2.22.0-0ubuntu3
</property>
</package>
<package id="784" name="gnome-menus">
<property name="description" type="str">
an implementation of the freedesktop menu specification for GNOME
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="785" name="gnome-mime-data">
<property name="description" type="str">
base MIME and Application database for GNOME.
</property>
<property name="version" type="str">
2.18.0-1
</property>
</package>
<package id="786" name="gnome-mount">
<property name="description" type="str">
wrapper for (un)mounting and ejecting storage devices
</property>
<property name="version" type="str">
0.8~svn20080225-0ubuntu4
</property>
</package>
<package id="787" name="gnome-netstatus-applet">
<property name="description" type="str">
Network status applet for GNOME 2
</property>
<property name="version" type="str">
2.12.1-1ubuntu1
</property>
</package>
<package id="788" name="gnome-nettool">
<property name="description" type="str">
network information tool for GNOME
</property>
<property name="version" type="str">
2.22.0-0ubuntu2
</property>
</package>
<package id="789" name="gnome-orca">
<property name="description" type="str">
Scriptable screen reader
</property>
<property name="version" type="str">
2.22.1-0ubuntu1
</property>
</package>
<package id="790" name="gnome-panel">
<property name="description" type="str">
launcher and docking facility for GNOME
</property>
<property name="version" type="str">
1:2.22.2-0ubuntu1
</property>
</package>
<package id="791" name="gnome-panel-data">
<property name="description" type="str">
common files for the GNOME Panel
</property>
<property name="version" type="str">
1:2.22.2-0ubuntu1
</property>
</package>
<package id="792" name="gnome-pilot">
<property name="description" type="str">
A GNOME applet for management of your Palm PDA
</property>
<property name="version" type="str">
2.0.15-2ubuntu3
</property>
</package>
<package id="793" name="gnome-pilot-conduits">
<property name="description" type="str">
conduits for gnome-pilot
</property>
<property name="version" type="str">
2.0.15-1ubuntu2
</property>
</package>
<package id="794" name="gnome-power-manager">
<property name="description" type="str">
frontend for gnome-powermanager
</property>
<property name="version" type="str">
2.22.1-1ubuntu4
</property>
</package>
<package id="795" name="gnome-screensaver">
<property name="description" type="str">
GNOME screen saver and locker
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="796" name="gnome-session">
<property name="description" type="str">
The GNOME 2 Session Manager
</property>
<property name="version" type="str">
2.22.1.1-0ubuntu2
</property>
</package>
<package id="797" name="gnome-settings-daemon">
<property name="description" type="str">
GNOME settings daemon
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="798" name="gnome-spell">
<property name="description" type="str">
GNOME/Bonobo component for spell checking
</property>
<property name="version" type="str">
1.0.7-1ubuntu2
</property>
</package>
<package id="799" name="gnome-system-monitor">
<property name="description" type="str">
Process viewer and system resource monitor for GNOME 2
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="800" name="gnome-system-tools">
<property name="description" type="str">
Cross-platform configuration utilities for GNOME
</property>
<property name="version" type="str">
2.22.0-0ubuntu9
</property>
</package>
<package id="801" name="gnome-terminal">
<property name="description" type="str">
The GNOME 2 terminal emulator application
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="802" name="gnome-terminal-data">
<property name="description" type="str">
Data files for the GNOME terminal emulator
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="803" name="gnome-themes">
<property name="description" type="str">
official themes for the GNOME 2 desktop
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="804" name="gnome-user-guide">
<property name="description" type="str">
GNOME user's guide
</property>
<property name="version" type="str">
2.22.0+svn20080407ubuntu1
</property>
</package>
<package id="805" name="gnome-utils">
<property name="description" type="str">
GNOME desktop utilities
</property>
<property name="version" type="str">
2.20.0.1-1ubuntu5
</property>
</package>
<package id="806" name="gnome-volume-manager">
<property name="description" type="str">
GNOME daemon to auto-mount and manage media devices
</property>
<property name="version" type="str">
2.22.1-1ubuntu6
</property>
</package>
<package id="807" name="gnupg">
<property name="description" type="str">
GNU privacy guard - a free PGP replacement
</property>
<property name="version" type="str">
1.4.6-2ubuntu5
</property>
</package>
<package id="808" name="gpgv">
<property name="description" type="str">
GNU privacy guard - signature verification tool
</property>
<property name="version" type="str">
1.4.6-2ubuntu5
</property>
</package>
<package id="809" name="grep">
<property name="description" type="str">
GNU grep, egrep and fgrep
</property>
<property name="version" type="str">
2.5.3~dfsg-3
</property>
</package>
<package id="810" name="groff-base">
<property name="description" type="str">
GNU troff text-formatting system (base system components)
</property>
<property name="version" type="str">
1.18.1.1-16
</property>
</package>
<package id="811" name="grub">
<property name="description" type="str">
GRand Unified Bootloader
</property>
<property name="version" type="str">
0.97-29ubuntu21
</property>
</package>
<package id="812" name="gsfonts">
<property name="description" type="str">
Fonts for the Ghostscript interpreter(s)
</property>
<property name="version" type="str">
1:8.11+urwcyr1.0.7~pre43-1
</property>
</package>
<package id="813" name="gstreamer0.10-alsa">
<property name="description" type="str">
GStreamer plugin for ALSA
</property>
<property name="version" type="str">
0.10.18-3
</property>
</package>
<package id="814" name="gstreamer0.10-gnomevfs">
<property name="description" type="str">
GStreamer plugin for GnomeVFS
</property>
<property name="version" type="str">
0.10.18-3
</property>
</package>
<package id="815" name="gstreamer0.10-plugins-base">
<property name="description" type="str">
GStreamer plugins from the &quot;base&quot; set
</property>
<property name="version" type="str">
0.10.18-3
</property>
</package>
<package id="816" name="gstreamer0.10-plugins-base-apps">
<property name="description" type="str">
GStreamer helper programs from the &quot;base&quot; set
</property>
<property name="version" type="str">
0.10.18-3
</property>
</package>
<package id="817" name="gstreamer0.10-plugins-good">
<property name="description" type="str">
GStreamer plugins from the &quot;good&quot; set
</property>
<property name="version" type="str">
0.10.7-3ubuntu0.1
</property>
</package>
<package id="818" name="gstreamer0.10-pulseaudio">
<property name="description" type="str">
GStreamer plugin for PulseAudio
</property>
<property name="version" type="str">
0.9.7-2
</property>
</package>
<package id="819" name="gstreamer0.10-tools">
<property name="description" type="str">
Tools for use with GStreamer
</property>
<property name="version" type="str">
0.10.18-4ubuntu1
</property>
</package>
<package id="820" name="gstreamer0.10-x">
<property name="description" type="str">
GStreamer plugins for X11 and Pango
</property>
<property name="version" type="str">
0.10.18-3
</property>
</package>
<package id="821" name="gtk2-engines">
<property name="description" type="str">
theme engines for GTK+ 2.x
</property>
<property name="version" type="str">
1:2.14.1-0ubuntu1
</property>
</package>
<package id="822" name="gtk2-engines-murrine">
<property name="description" type="str">
cairo-based gtk+-2.0 theme engine
</property>
<property name="version" type="str">
0.53.1-1ubuntu1
</property>
</package>
<package id="823" name="gtk2-engines-pixbuf">
<property name="description" type="str">
Pixbuf-based theme for GTK+ 2.x
</property>
<property name="version" type="str">
2.12.9-3ubuntu4
</property>
</package>
<package id="824" name="gtk2-engines-ubuntulooks">
<property name="description" type="str">
'ubuntulooks' theme for GTK+ 2.x
</property>
<property name="version" type="str">
0.9.12-11
</property>
</package>
<package id="825" name="gtkhtml3.14">
<property name="description" type="str">
HTML rendering/editing library - bonobo component binary
</property>
<property name="version" type="str">
3.18.2-0ubuntu1
</property>
</package>
<package id="826" name="gucharmap">
<property name="description" type="str">
Unicode character picker and font browser
</property>
<property name="version" type="str">
1:2.22.1-0ubuntu2
</property>
</package>
<package id="827" name="guidance-backends">
<property name="description" type="str">
collection of system administration tools for GNU/Linux
</property>
<property name="version" type="str">
0.8.0svn20080103-0ubuntu16.1
</property>
</package>
<package id="828" name="guile-1.6-libs">
<property name="description" type="str">
Main Guile libraries
</property>
<property name="version" type="str">
1.6.8-6ubuntu1
</property>
</package>
<package id="829" name="gvfs">
<property name="description" type="str">
userspace virtual filesystem - server
</property>
<property name="version" type="str">
0.2.4-0ubuntu1
</property>
</package>
<package id="830" name="gvfs-backends">
<property name="description" type="str">
userspace virtual filesystem - backends
</property>
<property name="version" type="str">
0.2.4-0ubuntu1
</property>
</package>
<package id="831" name="gvfs-fuse">
<property name="description" type="str">
userspace virtual filesystem - fuse server
</property>
<property name="version" type="str">
0.2.4-0ubuntu1
</property>
</package>
<package id="832" name="gzip">
<property name="description" type="str">
The GNU compression utility
</property>
<property name="version" type="str">
1.3.12-3.2
</property>
</package>
<package id="833" name="hal">
<property name="description" type="str">
Hardware Abstraction Layer
</property>
<property name="version" type="str">
0.5.11~rc2-1ubuntu8.1
</property>
</package>
<package id="834" name="hal-cups-utils">
<property name="description" type="str">
CUPS integration with HAL
</property>
<property name="version" type="str">
0.6.13+svn86-0ubuntu4
</property>
</package>
<package id="835" name="hal-info">
<property name="description" type="str">
Hardware Abstraction Layer - fdi files
</property>
<property name="version" type="str">
20080508+git20080601-0ubuntu0.8.04
</property>
</package>
<package id="836" name="hdparm">
<property name="description" type="str">
tune hard disk parameters for high performance
</property>
<property name="version" type="str">
8.6-1ubuntu1
</property>
</package>
<package id="837" name="hicolor-icon-theme">
<property name="description" type="str">
default fallback theme for FreeDesktop.org icon themes
</property>
<property name="version" type="str">
0.10-1ubuntu1
</property>
</package>
<package id="838" name="hostname">
<property name="description" type="str">
utility to set/show the host name or domain name
</property>
<property name="version" type="str">
2.94
</property>
</package>
<package id="839" name="hotkey-setup">
<property name="description" type="str">
auto-configures laptop hotkeys
</property>
<property name="version" type="str">
0.1-17ubuntu21
</property>
</package>
<package id="840" name="hpijs">
<property name="description" type="str">
HP Linux Printing and Imaging - gs IJS driver (hpijs)
</property>
<property name="version" type="str">
2.8.2+2.8.2-0ubuntu8
</property>
</package>
<package id="841" name="hplip">
<property name="description" type="str">
HP Linux Printing and Imaging System (HPLIP)
</property>
<property name="version" type="str">
2.8.2-0ubuntu8
</property>
</package>
<package id="842" name="hplip-data">
<property name="description" type="str">
HP Linux Printing and Imaging - data files
</property>
<property name="version" type="str">
2.8.2-0ubuntu8
</property>
</package>
<package id="843" name="human-icon-theme">
<property name="description" type="str">
Human Icon theme
</property>
<property name="version" type="str">
0.28
</property>
</package>
<package id="844" name="human-theme">
<property name="description" type="str">
Human theme
</property>
<property name="version" type="str">
0.18
</property>
</package>
<package id="845" name="hwtest">
<property name="description" type="str">
Hardware Testing
</property>
<property name="version" type="str">
0.1-0ubuntu10
</property>
</package>
<package id="846" name="hwtest-gtk">
<property name="description" type="str">
GTK interface for the hwtest program
</property>
<property name="version" type="str">
0.1-0ubuntu10
</property>
</package>
<package id="847" name="iamerican">
<property name="description" type="str">
An American English dictionary for ispell
</property>
<property name="version" type="str">
3.1.20.0-4.4
</property>
</package>
<package id="848" name="ibritish">
<property name="description" type="str">
A British English dictionary for ispell
</property>
<property name="version" type="str">
3.1.20.0-4.4
</property>
</package>
<package id="849" name="ifupdown">
<property name="description" type="str">
high level tools to configure network interfaces
</property>
<property name="version" type="str">
0.6.8ubuntu8
</property>
</package>
<package id="850" name="im-switch">
<property name="description" type="str">
Input method switch framework
</property>
<property name="version" type="str">
1.16ubuntu1
</property>
</package>
<package id="851" name="info">
<property name="description" type="str">
Standalone GNU Info documentation browser
</property>
<property name="version" type="str">
4.11.dfsg.1-4
</property>
</package>
<package id="852" name="initramfs-tools">
<property name="description" type="str">
tools for generating an initramfs
</property>
<property name="version" type="str">
0.85eubuntu39.1
</property>
</package>
<package id="853" name="initscripts">
<property name="description" type="str">
Scripts for initializing and shutting down the system
</property>
<property name="version" type="str">
2.86.ds1-14.1ubuntu45
</property>
</package>
<package id="854" name="inputattach">
<property name="description" type="str">
utility to attach serial devices to the input subsystem
</property>
<property name="version" type="str">
1.23-0ubuntu2
</property>
</package>
<package id="855" name="iproute">
<property name="description" type="str">
Professional tools to control the networking in Linux kernels
</property>
<property name="version" type="str">
20071016-2ubuntu1
</property>
</package>
<package id="856" name="iptables">
<property name="description" type="str">
administration tools for packet filtering and NAT
</property>
<property name="version" type="str">
1.3.8.0debian1-1ubuntu2
</property>
</package>
<package id="857" name="iputils-arping">
<property name="description" type="str">
Tool to send ICMP echo requests to an ARP address
</property>
<property name="version" type="str">
3:20071127-1
</property>
</package>
<package id="858" name="iputils-ping">
<property name="description" type="str">
Tools to test the reachability of network hosts
</property>
<property name="version" type="str">
3:20071127-1
</property>
</package>
<package id="859" name="iputils-tracepath">
<property name="description" type="str">
Tools to trace the network path to a remote host
</property>
<property name="version" type="str">
3:20071127-1
</property>
</package>
<package id="860" name="iso-codes">
<property name="description" type="str">
ISO language, territory, currency, script codes and their translations
</property>
<property name="version" type="str">
1.7-1ubuntu1
</property>
</package>
<package id="861" name="ispell">
<property name="description" type="str">
International Ispell (an interactive spelling corrector)
</property>
<property name="version" type="str">
3.1.20.0-4.4
</property>
</package>
<package id="862" name="jockey-common">
<property name="description" type="str">
user interface and desktop integration for driver management
</property>
<property name="version" type="str">
0.3.3-0ubuntu8
</property>
</package>
<package id="863" name="jockey-gtk">
<property name="description" type="str">
GNOME user interface and desktop integration for driver management
</property>
<property name="version" type="str">
0.3.3-0ubuntu8
</property>
</package>
<package id="864" name="klibc-utils">
<property name="description" type="str">
small statically-linked utilities built with klibc
</property>
<property name="version" type="str">
1.5.7-4ubuntu4
</property>
</package>
<package id="865" name="klogd">
<property name="description" type="str">
Kernel Logging Daemon
</property>
<property name="version" type="str">
1.5-1ubuntu1
</property>
</package>
<package id="866" name="landscape-client">
<property name="description" type="str">
Placeholder for the Landscape client
</property>
<property name="version" type="str">
0.1
</property>
</package>
<package id="867" name="language-pack-en">
<property name="description" type="str">
translation updates for language English
</property>
<property name="version" type="str">
1:8.04+20080527
</property>
</package>
<package id="868" name="language-pack-en-base">
<property name="description" type="str">
translations for language English
</property>
<property name="version" type="str">
1:8.04+20080527
</property>
</package>
<package id="869" name="language-pack-gnome-en">
<property name="description" type="str">
GNOME translation updates for language English
</property>
<property name="version" type="str">
1:8.04+20080527
</property>
</package>
<package id="870" name="language-pack-gnome-en-base">
<property name="description" type="str">
GNOME translations for language English
</property>
<property name="version" type="str">
1:8.04+20080527
</property>
</package>
<package id="871" name="language-selector">
<property name="description" type="str">
Language selector for ubuntu linux
</property>
<property name="version" type="str">
0.3.4
</property>
</package>
<package id="872" name="language-selector-common">
<property name="description" type="str">
Language selector for ubuntu linux
</property>
<property name="version" type="str">
0.3.4
</property>
</package>
<package id="873" name="language-support-en">
<property name="description" type="str">
metapackage for English language support
</property>
<property name="version" type="str">
1:8.04+20080218
</property>
</package>
<package id="874" name="language-support-translations-en">
<property name="description" type="str">
Additional translations metapackage for English
</property>
<property name="version" type="str">
1:8.04+20080407
</property>
</package>
<package id="875" name="language-support-writing-en">
<property name="description" type="str">
Writing aids metapackage for English
</property>
<property name="version" type="str">
1:8.04+20080630
</property>
</package>
<package id="876" name="laptop-detect">
<property name="description" type="str">
attempt to detect a laptop
</property>
<property name="version" type="str">
0.13.2ubuntu1
</property>
</package>
<package id="877" name="laptop-mode-tools">
<property name="description" type="str">
Scripts to spin down hard drive and save power
</property>
<property name="version" type="str">
1.35-1ubuntu1
</property>
</package>
<package id="878" name="launchpad-integration">
<property name="description" type="str">
launchpad integration
</property>
<property name="version" type="str">
0.1.19
</property>
</package>
<package id="879" name="less">
<property name="description" type="str">
Pager program similar to more
</property>
<property name="version" type="str">
418-1
</property>
</package>
<package id="880" name="lftp">
<property name="description" type="str">
Sophisticated command-line FTP/HTTP client programs
</property>
<property name="version" type="str">
3.6.1-1
</property>
</package>
<package id="881" name="libaa1">
<property name="description" type="str">
ascii art library
</property>
<property name="version" type="str">
1.4p5-33ubuntu1
</property>
</package>
<package id="882" name="libacl1">
<property name="description" type="str">
Access control list shared library
</property>
<property name="version" type="str">
2.2.45-1
</property>
</package>
<package id="883" name="libalut0">
<property name="description" type="str">
OpenAL Utility Toolkit
</property>
<property name="version" type="str">
1.1.0-1
</property>
</package>
<package id="884" name="libao2">
<property name="description" type="str">
Cross Platform Audio Output Library
</property>
<property name="version" type="str">
0.8.8-3
</property>
</package>
<package id="885" name="libapm1">
<property name="description" type="str">
Library for interacting with APM driver in kernel
</property>
<property name="version" type="str">
3.2.2-8.1ubuntu1
</property>
</package>
<package id="886" name="libarchive1">
<property name="description" type="str">
Single library to read/write tar, cpio, pax, zip, iso9660, etc.
</property>
<property name="version" type="str">
2.2.4-1ubuntu1
</property>
</package>
<package id="887" name="libart-2.0-2">
<property name="description" type="str">
Library of functions for 2D graphics - runtime files
</property>
<property name="version" type="str">
2.3.20-1
</property>
</package>
<package id="888" name="libart2.0-cil">
<property name="description" type="str">
CLI binding for libart 2.3
</property>
<property name="version" type="str">
2.20.0-2ubuntu3
</property>
</package>
<package id="889" name="libasound2">
<property name="description" type="str">
ALSA library
</property>
<property name="version" type="str">
1.0.15-3ubuntu4
</property>
</package>
<package id="890" name="libaspell15">
<property name="description" type="str">
GNU Aspell spell-checker runtime library
</property>
<property name="version" type="str">
0.60.5-1ubuntu2
</property>
</package>
<package id="891" name="libatk1.0-0">
<property name="description" type="str">
The ATK accessibility toolkit
</property>
<property name="version" type="str">
1.22.0-0ubuntu1
</property>
</package>
<package id="892" name="libatm1">
<property name="description" type="str">
shared library for ATM (Asynchronous Transfer Mode)
</property>
<property name="version" type="str">
2.4.1-17.1build1
</property>
</package>
<package id="893" name="libatspi1.0-0">
<property name="description" type="str">
C binding libraries of at-spi for GNOME Accessibility
</property>
<property name="version" type="str">
1.22.1-0ubuntu1
</property>
</package>
<package id="894" name="libattr1">
<property name="description" type="str">
Extended attribute shared library
</property>
<property name="version" type="str">
1:2.4.39-1
</property>
</package>
<package id="895" name="libaudiofile0">
<property name="description" type="str">
Open-source version of SGI's audiofile library
</property>
<property name="version" type="str">
0.2.6-7ubuntu1
</property>
</package>
<package id="896" name="libavahi-client3">
<property name="description" type="str">
Avahi client library
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="897" name="libavahi-common-data">
<property name="description" type="str">
Avahi common data files
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="898" name="libavahi-common3">
<property name="description" type="str">
Avahi common library
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="899" name="libavahi-compat-libdnssd1">
<property name="description" type="str">
Avahi Apple Bonjour compatibility library
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="900" name="libavahi-core5">
<property name="description" type="str">
Avahi's embeddable mDNS/DNS-SD library
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="901" name="libavahi-glib1">
<property name="description" type="str">
Avahi glib integration library
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="902" name="libavahi-ui0">
<property name="description" type="str">
Avahi GTK User interface library
</property>
<property name="version" type="str">
0.6.22-2ubuntu4
</property>
</package>
<package id="903" name="libavc1394-0">
<property name="description" type="str">
control IEEE 1394 audio/video devices
</property>
<property name="version" type="str">
0.5.3-1build1
</property>
</package>
<package id="904" name="libbeagle1">
<property name="description" type="str">
library for accessing beagle using C
</property>
<property name="version" type="str">
0.3.0-2ubuntu1
</property>
</package>
<package id="905" name="libbind9-30">
<property name="description" type="str">
BIND9 Shared Library used by BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="906" name="libblkid1">
<property name="description" type="str">
block device id library
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="907" name="libbluetooth2">
<property name="description" type="str">
Library to use the BlueZ Linux Bluetooth stack
</property>
<property name="version" type="str">
3.29-0ubuntu1
</property>
</package>
<package id="908" name="libbonobo2-0">
<property name="description" type="str">
Bonobo CORBA interfaces library
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="909" name="libbonobo2-common">
<property name="description" type="str">
Bonobo CORBA interfaces library -- support files
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="910" name="libbonoboui2-0">
<property name="description" type="str">
The Bonobo UI library
</property>
<property name="version" type="str">
2.21.90-1
</property>
</package>
<package id="911" name="libbonoboui2-common">
<property name="description" type="str">
The Bonobo UI library -- common files
</property>
<property name="version" type="str">
2.21.90-1
</property>
</package>
<package id="912" name="libbrlapi0.5">
<property name="description" type="str">
braille display access via BRLTTY - shared library
</property>
<property name="version" type="str">
3.9-6ubuntu1
</property>
</package>
<package id="913" name="libbz2-1.0">
<property name="description" type="str">
high-quality block-sorting file compressor library - runtime
</property>
<property name="version" type="str">
1.0.4-2ubuntu4
</property>
</package>
<package id="914" name="libc6">
<property name="description" type="str">
GNU C Library: Shared libraries
</property>
<property name="version" type="str">
2.7-10ubuntu3
</property>
</package>
<package id="915" name="libc6-i686">
<property name="description" type="str">
GNU C Library: Shared libraries [i686 optimized]
</property>
<property name="version" type="str">
2.7-10ubuntu3
</property>
</package>
<package id="916" name="libcaca0">
<property name="description" type="str">
colour ASCII art library
</property>
<property name="version" type="str">
0.99.beta13b-4
</property>
</package>
<package id="917" name="libcairo-perl">
<property name="description" type="str">
Perl interface to the Cairo graphics library
</property>
<property name="version" type="str">
1.043-1
</property>
</package>
<package id="918" name="libcairo2">
<property name="description" type="str">
The Cairo 2D vector graphics library
</property>
<property name="version" type="str">
1.6.0-0ubuntu2
</property>
</package>
<package id="919" name="libcairomm-1.0-1">
<property name="description" type="str">
C++ wrappers for Cairo (shared libraries)
</property>
<property name="version" type="str">
1.4.2-1
</property>
</package>
<package id="920" name="libcamel1.2-11">
<property name="description" type="str">
The Evolution MIME message handling library
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="921" name="libcap1">
<property name="description" type="str">
support for getting/setting POSIX.1e capabilities
</property>
<property name="version" type="str">
1:1.10-14build1
</property>
</package>
<package id="922" name="libcdio-cdda0">
<property name="description" type="str">
library to read and control digital audio CDs
</property>
<property name="version" type="str">
0.78.2+dfsg1-2ubuntu1
</property>
</package>
<package id="923" name="libcdio-paranoia0">
<property name="description" type="str">
library to read digital audio CDs with error correction
</property>
<property name="version" type="str">
0.78.2+dfsg1-2ubuntu1
</property>
</package>
<package id="924" name="libcdio7">
<property name="description" type="str">
library to read and control CD-ROM
</property>
<property name="version" type="str">
0.78.2+dfsg1-2ubuntu1
</property>
</package>
<package id="925" name="libcdparanoia0">
<property name="description" type="str">
audio extraction tool for sampling CDs (library)
</property>
<property name="version" type="str">
3.10+debian~pre0-6
</property>
</package>
<package id="926" name="libchromexvmc1">
<property name="description" type="str">
XvMC Libraries used by the Openchrome VIA driver
</property>
<property name="version" type="str">
1:0.2.901-0ubuntu4
</property>
</package>
<package id="927" name="libchromexvmcpro1">
<property name="description" type="str">
XvMC Pro Libraries used by the Openchrome VIA driver
</property>
<property name="version" type="str">
1:0.2.901-0ubuntu4
</property>
</package>
<package id="928" name="libck-connector0">
<property name="description" type="str">
ConsoleKit libraries
</property>
<property name="version" type="str">
0.2.3-3ubuntu5
</property>
</package>
<package id="929" name="libcomerr2">
<property name="description" type="str">
common error description library
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="930" name="libcompizconfig0">
<property name="description" type="str">
Settings library for plugins - OpenCompositing Project
</property>
<property name="version" type="str">
0.7.4-0ubuntu1
</property>
</package>
<package id="931" name="libconsole">
<property name="description" type="str">
Shared libraries for Linux console and font manipulation
</property>
<property name="version" type="str">
1:0.2.3dbs-65ubuntu7
</property>
</package>
<package id="932" name="libcroco3">
<property name="description" type="str">
a generic Cascading Style Sheet (CSS) parsing and manipulation toolkit
</property>
<property name="version" type="str">
0.6.1-1build2
</property>
</package>
<package id="933" name="libcucul0">
<property name="description" type="str">
low-level Unicode character drawing library
</property>
<property name="version" type="str">
0.99.beta13b-4
</property>
</package>
<package id="934" name="libcupsimage2">
<property name="description" type="str">
Common UNIX Printing System(tm) - image libs
</property>
<property name="version" type="str">
1.3.7-1ubuntu3
</property>
</package>
<package id="935" name="libcupsys2">
<property name="description" type="str">
Common UNIX Printing System(tm) - libs
</property>
<property name="version" type="str">
1.3.7-1ubuntu3
</property>
</package>
<package id="936" name="libcurl3">
<property name="description" type="str">
Multi-protocol file transfer library (OpenSSL)
</property>
<property name="version" type="str">
7.18.0-1ubuntu2
</property>
</package>
<package id="937" name="libcurl3-gnutls">
<property name="description" type="str">
Multi-protocol file transfer library (GnuTLS)
</property>
<property name="version" type="str">
7.18.0-1ubuntu2
</property>
</package>
<package id="938" name="libcwidget3">
<property name="description" type="str">
high-level terminal interface library for C++ (runtime files)
</property>
<property name="version" type="str">
0.5.8-1ubuntu1
</property>
</package>
<package id="939" name="libdaemon0">
<property name="description" type="str">
lightweight C library for daemons
</property>
<property name="version" type="str">
0.12-0.1
</property>
</package>
<package id="940" name="libdatrie0">
<property name="description" type="str">
Double-array trie library
</property>
<property name="version" type="str">
0.1.2-2
</property>
</package>
<package id="941" name="libdb4.6">
<property name="description" type="str">
Berkeley v4.6 Database Libraries [runtime]
</property>
<property name="version" type="str">
4.6.21-6ubuntu1
</property>
</package>
<package id="942" name="libdbus-1-3">
<property name="description" type="str">
simple interprocess messaging system
</property>
<property name="version" type="str">
1.1.20-1ubuntu2
</property>
</package>
<package id="943" name="libdbus-glib-1-2">
<property name="description" type="str">
simple interprocess messaging system (GLib-based shared library)
</property>
<property name="version" type="str">
0.74-2
</property>
</package>
<package id="944" name="libdecoration0">
<property name="description" type="str">
Compiz window decoration library
</property>
<property name="version" type="str">
1:0.7.4-0ubuntu7
</property>
</package>
<package id="945" name="libdeskbar-tracker">
<property name="description" type="str">
metadata database, indexer and search tool - deskbar-applet plugin
</property>
<property name="version" type="str">
0.6.6-0ubuntu3.8.04.1
</property>
</package>
<package id="946" name="libdevmapper1.02.1">
<property name="description" type="str">
The Linux Kernel Device Mapper userspace library
</property>
<property name="version" type="str">
2:1.02.20-2ubuntu2
</property>
</package>
<package id="947" name="libdirectfb-1.0-0">
<property name="description" type="str">
direct frame buffer graphics - shared libraries
</property>
<property name="version" type="str">
1.0.1-7ubuntu3
</property>
</package>
<package id="948" name="libdjvulibre15">
<property name="description" type="str">
Runtime support for the DjVu image format
</property>
<property name="version" type="str">
3.5.20-2
</property>
</package>
<package id="949" name="libdmx1">
<property name="description" type="str">
X11 Distributed Multihead extension library
</property>
<property name="version" type="str">
1:1.0.2-2build1
</property>
</package>
<package id="950" name="libdns32">
<property name="description" type="str">
DNS Shared Library used by BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="951" name="libdrm2">
<property name="description" type="str">
Userspace interface to kernel DRM services -- runtime
</property>
<property name="version" type="str">
2.3.0-4ubuntu1
</property>
</package>
<package id="952" name="libdv4">
<property name="description" type="str">
software library for DV format digital video (runtime lib)
</property>
<property name="version" type="str">
1.0.0-1ubuntu1
</property>
</package>
<package id="953" name="libebook1.2-9">
<property name="description" type="str">
Client library for evolution address books
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="954" name="libecal1.2-7">
<property name="description" type="str">
Client library for evolution calendars
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="955" name="libedata-book1.2-2">
<property name="description" type="str">
Backend library for evolution address books
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="956" name="libedata-cal1.2-6">
<property name="description" type="str">
Backend library for evolution calendars
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="957" name="libedataserver1.2-9">
<property name="description" type="str">
Utility library for evolution data servers
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="958" name="libedataserverui1.2-8">
<property name="description" type="str">
GUI utility library for evolution data servers
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="959" name="libedit2">
<property name="description" type="str">
BSD editline and history libraries
</property>
<property name="version" type="str">
2.9.cvs.20050518-4
</property>
</package>
<package id="960" name="libeel2-2">
<property name="description" type="str">
Eazel Extensions Library (for GNOME2)
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="961" name="libeel2-data">
<property name="description" type="str">
Eazel Extensions Library - data files (for GNOME2)
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="962" name="libegroupwise1.2-13">
<property name="description" type="str">
Client library for accessing groupwise POA through SOAP interface
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="963" name="libelfg0">
<property name="description" type="str">
an ELF object file access library
</property>
<property name="version" type="str">
0.8.6-4
</property>
</package>
<package id="964" name="libenchant1c2a">
<property name="description" type="str">
a wrapper library for various spell checker engines
</property>
<property name="version" type="str">
1.3.0-5
</property>
</package>
<package id="965" name="libesd-alsa0">
<property name="description" type="str">
Enlightened Sound Daemon (ALSA) - Shared libraries
</property>
<property name="version" type="str">
0.2.38-0ubuntu9
</property>
</package>
<package id="966" name="libespeak1">
<property name="description" type="str">
A multi-lingual software speech synthesizer: shared library
</property>
<property name="version" type="str">
1.36-0ubuntu1
</property>
</package>
<package id="967" name="libexchange-storage1.2-3">
<property name="description" type="str">
Backend library for evolution calendars
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="968" name="libexempi3">
<property name="description" type="str">
library to parse XMP metadata (Library)
</property>
<property name="version" type="str">
1.99.9-1
</property>
</package>
<package id="969" name="libexif12">
<property name="description" type="str">
library to parse EXIF files
</property>
<property name="version" type="str">
0.6.16-2.1
</property>
</package>
<package id="970" name="libexpat1">
<property name="description" type="str">
XML parsing C library - runtime library
</property>
<property name="version" type="str">
2.0.1-0ubuntu1
</property>
</package>
<package id="971" name="libffi4">
<property name="description" type="str">
Foreign Function Interface library runtime
</property>
<property name="version" type="str">
4.2.3-2ubuntu7
</property>
</package>
<package id="972" name="libflac8">
<property name="description" type="str">
Free Lossless Audio Codec - runtime C library
</property>
<property name="version" type="str">
1.2.1-1ubuntu2
</property>
</package>
<package id="973" name="libflickrnet2.1.5-cil">
<property name="description" type="str">
Flickr.Net API Library
</property>
<property name="version" type="str">
25277-6build1
</property>
</package>
<package id="974" name="libfontconfig1">
<property name="description" type="str">
generic font configuration library - runtime
</property>
<property name="version" type="str">
2.5.0-2ubuntu3
</property>
</package>
<package id="975" name="libfontenc1">
<property name="description" type="str">
X11 font encoding library
</property>
<property name="version" type="str">
1:1.0.4-2
</property>
</package>
<package id="976" name="libfreetype6">
<property name="description" type="str">
FreeType 2 font engine, shared library files
</property>
<property name="version" type="str">
2.3.5-1ubuntu4
</property>
</package>
<package id="977" name="libfribidi0">
<property name="description" type="str">
Free Implementation of the Unicode BiDi algorithm
</property>
<property name="version" type="str">
0.10.9-1
</property>
</package>
<package id="978" name="libfs6">
<property name="description" type="str">
X11 Font Services library
</property>
<property name="version" type="str">
2:1.0.0-4ubuntu2
</property>
</package>
<package id="979" name="libfuse2">
<property name="description" type="str">
Filesystem in USErspace library
</property>
<property name="version" type="str">
2.7.2-1ubuntu2
</property>
</package>
<package id="980" name="libgadu3">
<property name="description" type="str">
Gadu-Gadu protocol library - runtime files
</property>
<property name="version" type="str">
1:1.7~rc2-2
</property>
</package>
<package id="981" name="libgail-common">
<property name="description" type="str">
GNOME Accessibility Implementation Library -- common modules
</property>
<property name="version" type="str">
1.22.1-0ubuntu1
</property>
</package>
<package id="982" name="libgail-gnome-module">
<property name="description" type="str">
GNOME Accessibility Implementation Module for GnomeUI/BonoboUI
</property>
<property name="version" type="str">
1.20.0-1
</property>
</package>
<package id="983" name="libgail18">
<property name="description" type="str">
GNOME Accessibility Implementation Library -- shared libraries
</property>
<property name="version" type="str">
1.22.1-0ubuntu1
</property>
</package>
<package id="984" name="libgamin0">
<property name="description" type="str">
Client library for the gamin file and directory monitoring system
</property>
<property name="version" type="str">
0.1.9-2ubuntu2
</property>
</package>
<package id="985" name="libgc1c2">
<property name="description" type="str">
conservative garbage collector for C and C++
</property>
<property name="version" type="str">
1:6.8-1.1
</property>
</package>
<package id="986" name="libgcc1">
<property name="description" type="str">
GCC support library
</property>
<property name="version" type="str">
1:4.2.3-2ubuntu7
</property>
</package>
<package id="987" name="libgconf2-4">
<property name="description" type="str">
GNOME configuration database system (shared libraries)
</property>
<property name="version" type="str">
2.22.0-0ubuntu3
</property>
</package>
<package id="988" name="libgconf2.0-cil">
<property name="description" type="str">
CLI binding for GConf 2.20
</property>
<property name="version" type="str">
2.20.0-2ubuntu3
</property>
</package>
<package id="989" name="libgcrypt11">
<property name="description" type="str">
LGPL Crypto library - runtime library
</property>
<property name="version" type="str">
1.2.4-2ubuntu7
</property>
</package>
<package id="990" name="libgd2-noxpm">
<property name="description" type="str">
GD Graphics Library version 2 (without XPM support)
</property>
<property name="version" type="str">
2.0.35.dfsg-3ubuntu2
</property>
</package>
<package id="991" name="libgdata-google1.2-1">
<property name="description" type="str">
Client library for accessing google POA through SOAP interface
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="992" name="libgdata1.2-1">
<property name="description" type="str">
Client library for accessing google POA through SOAP interface
</property>
<property name="version" type="str">
2.22.2-0ubuntu2
</property>
</package>
<package id="993" name="libgdbm3">
<property name="description" type="str">
GNU dbm database routines (runtime version)
</property>
<property name="version" type="str">
1.8.3-3
</property>
</package>
<package id="994" name="libggz2">
<property name="description" type="str">
GGZ Gaming Zone: common utilities library
</property>
<property name="version" type="str">
0.0.14-1
</property>
</package>
<package id="995" name="libggzcore9">
<property name="description" type="str">
GGZ Gaming Zone: core client frontend library
</property>
<property name="version" type="str">
0.0.14-2
</property>
</package>
<package id="996" name="libggzmod4">
<property name="description" type="str">
GGZ Gaming Zone: game frontend library
</property>
<property name="version" type="str">
0.0.14-2
</property>
</package>
<package id="997" name="libgimp2.0">
<property name="description" type="str">
Libraries for the GNU Image Manipulation Program
</property>
<property name="version" type="str">
2.4.5-1ubuntu2
</property>
</package>
<package id="998" name="libgksu2-0">
<property name="description" type="str">
library providing su and sudo functionality
</property>
<property name="version" type="str">
2.0.5-1ubuntu5.1
</property>
</package>
<package id="999" name="libgl1-mesa-dri">
<property name="description" type="str">
A free implementation of the OpenGL API -- DRI modules
</property>
<property name="version" type="str">
7.0.3~rc2-1ubuntu3
</property>
</package>
<package id="1000" name="libgl1-mesa-glx">
<property name="description" type="str">
A free implementation of the OpenGL API -- GLX runtime
</property>
<property name="version" type="str">
7.0.3~rc2-1ubuntu3
</property>
</package>
<package id="1001" name="libglade2-0">
<property name="description" type="str">
library to load .glade files at runtime
</property>
<property name="version" type="str">
1:2.6.2-1
</property>
</package>
<package id="1002" name="libglade2.0-cil">
<property name="description" type="str">
CLI binding for the Glade libraries 2.6
</property>
<property name="version" type="str">
2.12.0-2ubuntu3
</property>
</package>
<package id="1003" name="libglew1.5">
<property name="description" type="str">
The OpenGL Extension Wrangler - runtime environment
</property>
<property name="version" type="str">
1.5.0dfsg1-3ubuntu1
</property>
</package>
<package id="1004" name="libglib-perl">
<property name="description" type="str">
Perl interface to the GLib and GObject libraries
</property>
<property name="version" type="str">
1:1.161-1
</property>
</package>
<package id="1005" name="libglib2.0-0">
<property name="description" type="str">
The GLib library of C routines
</property>
<property name="version" type="str">
2.16.3-1ubuntu3
</property>
</package>
<package id="1006" name="libglib2.0-cil">
<property name="description" type="str">
CLI binding for the GLib utility library 2.12
</property>
<property name="version" type="str">
2.12.0-2ubuntu3
</property>
</package>
<package id="1007" name="libglibmm-2.4-1c2a">
<property name="description" type="str">
C++ wrapper for the GLib toolkit (shared libraries)
</property>
<property name="version" type="str">
2.16.0-1
</property>
</package>
<package id="1008" name="libglu1-mesa">
<property name="description" type="str">
The OpenGL utility library (GLU)
</property>
<property name="version" type="str">
7.0.3~rc2-1ubuntu3
</property>
</package>
<package id="1009" name="libglut3">
<property name="description" type="str">
the OpenGL Utility Toolkit
</property>
<property name="version" type="str">
3.7-25
</property>
</package>
<package id="1010" name="libgmime-2.0-2">
<property name="description" type="str">
MIME library
</property>
<property name="version" type="str">
2.2.11-2ubuntu1
</property>
</package>
<package id="1011" name="libgmime2.2-cil">
<property name="description" type="str">
CLI binding for the MIME library
</property>
<property name="version" type="str">
2.2.11-2ubuntu1
</property>
</package>
<package id="1012" name="libgnome-desktop-2">
<property name="description" type="str">
Utility library for loading .desktop files - runtime files
</property>
<property name="version" type="str">
1:2.22.2-0ubuntu3
</property>
</package>
<package id="1013" name="libgnome-keyring0">
<property name="description" type="str">
GNOME keyring services library
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="1014" name="libgnome-mag2">
<property name="description" type="str">
screen magnification library for the GNOME desktop (shared library)
</property>
<property name="version" type="str">
1:0.15.0-0ubuntu1
</property>
</package>
<package id="1015" name="libgnome-media0">
<property name="description" type="str">
runtime libraries for the GNOME media utilities
</property>
<property name="version" type="str">
2.22.0-0ubuntu3
</property>
</package>
<package id="1016" name="libgnome-menu2">
<property name="description" type="str">
an implementation of the freedesktop menu specification for GNOME
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="1017" name="libgnome-pilot2">
<property name="description" type="str">
Support libraries for gnome-pilot
</property>
<property name="version" type="str">
2.0.15-2ubuntu3
</property>
</package>
<package id="1018" name="libgnome-speech7">
<property name="description" type="str">
GNOME text-to-speech library
</property>
<property name="version" type="str">
1:0.4.18-0ubuntu2
</property>
</package>
<package id="1019" name="libgnome-vfs2.0-cil">
<property name="description" type="str">
CLI binding for GnomeVFS 2.20
</property>
<property name="version" type="str">
2.20.0-2ubuntu3
</property>
</package>
<package id="1020" name="libgnome-window-settings1">
<property name="description" type="str">
Utility library for getting window manager settings
</property>
<property name="version" type="str">
1:2.22.1-0ubuntu4.1
</property>
</package>
<package id="1021" name="libgnome2-0">
<property name="description" type="str">
The GNOME 2 library - runtime files
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1022" name="libgnome2-canvas-perl">
<property name="description" type="str">
Perl interface to the GNOME canvas library
</property>
<property name="version" type="str">
1.002-1+b1ubuntu1
</property>
</package>
<package id="1023" name="libgnome2-common">
<property name="description" type="str">
The GNOME 2 library - common files
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1024" name="libgnome2-perl">
<property name="description" type="str">
Perl interface to the GNOME libraries
</property>
<property name="version" type="str">
1.040-1
</property>
</package>
<package id="1025" name="libgnome2-vfs-perl">
<property name="description" type="str">
Perl interface to the 2.x series of the GNOME VFS library
</property>
<property name="version" type="str">
1.080-1
</property>
</package>
<package id="1026" name="libgnome2.0-cil">
<property name="description" type="str">
CLI binding for GNOME 2.20
</property>
<property name="version" type="str">
2.20.0-2ubuntu3
</property>
</package>
<package id="1027" name="libgnomecanvas2-0">
<property name="description" type="str">
A powerful object-oriented display - runtime files
</property>
<property name="version" type="str">
2.20.1.1-1
</property>
</package>
<package id="1028" name="libgnomecanvas2-common">
<property name="description" type="str">
A powerful object-oriented display - common files
</property>
<property name="version" type="str">
2.20.1.1-1
</property>
</package>
<package id="1029" name="libgnomecups1.0-1">
<property name="description" type="str">
GNOME library for CUPS interaction
</property>
<property name="version" type="str">
0.2.3-1ubuntu1
</property>
</package>
<package id="1030" name="libgnomekbd-common">
<property name="description" type="str">
GNOME library to manage keyboard configuration - common files
</property>
<property name="version" type="str">
2.22.0-1
</property>
</package>
<package id="1031" name="libgnomekbd2">
<property name="description" type="str">
GNOME library to manage keyboard configuration - shared library
</property>
<property name="version" type="str">
2.22.0-1
</property>
</package>
<package id="1032" name="libgnomekbdui2">
<property name="description" type="str">
User interface library for libgnomekbd - shared library
</property>
<property name="version" type="str">
2.22.0-1
</property>
</package>
<package id="1033" name="libgnomeprint2.2-0">
<property name="description" type="str">
The GNOME 2.2 print architecture - runtime files
</property>
<property name="version" type="str">
2.18.4-1
</property>
</package>
<package id="1034" name="libgnomeprint2.2-data">
<property name="description" type="str">
The GNOME 2.2 print architecture - data files
</property>
<property name="version" type="str">
2.18.4-1
</property>
</package>
<package id="1035" name="libgnomeprintui2.2-0">
<property name="description" type="str">
GNOME 2.2 print architecture User Interface - runtime files
</property>
<property name="version" type="str">
2.18.2-1
</property>
</package>
<package id="1036" name="libgnomeprintui2.2-common">
<property name="description" type="str">
GNOME 2.2 print architecture User Interface - common files
</property>
<property name="version" type="str">
2.18.2-1
</property>
</package>
<package id="1037" name="libgnomeui-0">
<property name="description" type="str">
The GNOME 2 libraries (User Interface) - runtime files
</property>
<property name="version" type="str">
2.22.1.0-0ubuntu2
</property>
</package>
<package id="1038" name="libgnomeui-common">
<property name="description" type="str">
The GNOME 2 libraries (User Interface) - common files
</property>
<property name="version" type="str">
2.22.1.0-0ubuntu2
</property>
</package>
<package id="1039" name="libgnomevfs2-0">
<property name="description" type="str">
GNOME Virtual File System (runtime libraries)
</property>
<property name="version" type="str">
1:2.22.0-2ubuntu1
</property>
</package>
<package id="1040" name="libgnomevfs2-bin">
<property name="description" type="str">
GNOME Virtual File System (support binaries)
</property>
<property name="version" type="str">
1:2.22.0-2ubuntu1
</property>
</package>
<package id="1041" name="libgnomevfs2-common">
<property name="description" type="str">
GNOME Virtual File System (common files)
</property>
<property name="version" type="str">
1:2.22.0-2ubuntu1
</property>
</package>
<package id="1042" name="libgnomevfs2-extra">
<property name="description" type="str">
GNOME Virtual File System (extra modules)
</property>
<property name="version" type="str">
1:2.22.0-2ubuntu1
</property>
</package>
<package id="1043" name="libgnutls13">
<property name="description" type="str">
the GNU TLS library - runtime library
</property>
<property name="version" type="str">
2.0.4-1ubuntu2.1
</property>
</package>
<package id="1044" name="libgomp1">
<property name="description" type="str">
GCC OpenMP (GOMP) support library
</property>
<property name="version" type="str">
4.2.3-2ubuntu7
</property>
</package>
<package id="1045" name="libgpg-error0">
<property name="description" type="str">
library for common error values and messages in GnuPG components
</property>
<property name="version" type="str">
1.4-2ubuntu7
</property>
</package>
<package id="1046" name="libgpgme11">
<property name="description" type="str">
GPGME - GnuPG Made Easy
</property>
<property name="version" type="str">
1.1.5-2ubuntu1
</property>
</package>
<package id="1047" name="libgphoto2-2">
<property name="description" type="str">
gphoto2 digital camera library
</property>
<property name="version" type="str">
2.4.0-8ubuntu7
</property>
</package>
<package id="1048" name="libgphoto2-port0">
<property name="description" type="str">
gphoto2 digital camera port library
</property>
<property name="version" type="str">
2.4.0-8ubuntu7
</property>
</package>
<package id="1049" name="libgpmg1">
<property name="description" type="str">
General Purpose Mouse - shared library
</property>
<property name="version" type="str">
1.19.6-25ubuntu1
</property>
</package>
<package id="1050" name="libgpod-common">
<property name="description" type="str">
a library to read and write songs and artwork to an iPod
</property>
<property name="version" type="str">
0.6.0-3ubuntu3
</property>
</package>
<package id="1051" name="libgpod3">
<property name="description" type="str">
a library to read and write songs and artwork to an iPod
</property>
<property name="version" type="str">
0.6.0-3ubuntu3
</property>
</package>
<package id="1052" name="libgraphviz4">
<property name="description" type="str">
rich set of graph drawing tools
</property>
<property name="version" type="str">
2.16-3ubuntu2
</property>
</package>
<package id="1053" name="libgs8">
<property name="description" type="str">
The Ghostscript PostScript/PDF interpreter Library
</property>
<property name="version" type="str">
8.61.dfsg.1-1ubuntu3
</property>
</package>
<package id="1054" name="libgsf-1-114">
<property name="description" type="str">
Structured File Library - runtime version
</property>
<property name="version" type="str">
1.14.7-2ubuntu1
</property>
</package>
<package id="1055" name="libgsf-1-common">
<property name="description" type="str">
Structured File Library - common files
</property>
<property name="version" type="str">
1.14.7-2ubuntu1
</property>
</package>
<package id="1056" name="libgsl0ldbl">
<property name="description" type="str">
GNU Scientific Library (GSL) -- library package
</property>
<property name="version" type="str">
1.10-4
</property>
</package>
<package id="1057" name="libgstreamer-plugins-base0.10-0">
<property name="description" type="str">
GStreamer libraries from the &quot;base&quot; set
</property>
<property name="version" type="str">
0.10.18-3
</property>
</package>
<package id="1058" name="libgstreamer0.10-0">
<property name="description" type="str">
Core GStreamer libraries and elements
</property>
<property name="version" type="str">
0.10.18-4ubuntu1
</property>
</package>
<package id="1059" name="libgtk-vnc-1.0-0">
<property name="description" type="str">
A VNC viewer widget for GTK+ (runtime libraries)
</property>
<property name="version" type="str">
0.3.4-0ubuntu2
</property>
</package>
<package id="1060" name="libgtk2-perl">
<property name="description" type="str">
Perl interface to the 2.x series of the Gimp Toolkit library
</property>
<property name="version" type="str">
1:1.161-1
</property>
</package>
<package id="1061" name="libgtk2.0-0">
<property name="description" type="str">
The GTK+ graphical user interface library
</property>
<property name="version" type="str">
2.12.9-3ubuntu4
</property>
</package>
<package id="1062" name="libgtk2.0-bin">
<property name="description" type="str">
The programs for the GTK+ graphical user interface library
</property>
<property name="version" type="str">
2.12.9-3ubuntu4
</property>
</package>
<package id="1063" name="libgtk2.0-cil">
<property name="description" type="str">
CLI binding for the GTK+ toolkit 2.12
</property>
<property name="version" type="str">
2.12.0-2ubuntu3
</property>
</package>
<package id="1064" name="libgtk2.0-common">
<property name="description" type="str">
Common files for the GTK+ graphical user interface library
</property>
<property name="version" type="str">
2.12.9-3ubuntu4
</property>
</package>
<package id="1065" name="libgtkhtml2-0">
<property name="description" type="str">
HTML rendering/editing library - runtime files. (for GNOME2)
</property>
<property name="version" type="str">
2.11.1-1
</property>
</package>
<package id="1066" name="libgtkhtml3.14-19">
<property name="description" type="str">
HTML rendering/editing library - runtime files
</property>
<property name="version" type="str">
3.18.2-0ubuntu1
</property>
</package>
<package id="1067" name="libgtkhtml3.16-cil">
<property name="description" type="str">
CLI binding for GtkHTML 3.16
</property>
<property name="version" type="str">
2.20.1-2ubuntu2
</property>
</package>
<package id="1068" name="libgtkmm-2.4-1c2a">
<property name="description" type="str">
C++ wrappers for GTK+ 2.4 (shared libraries)
</property>
<property name="version" type="str">
1:2.12.5-2
</property>
</package>
<package id="1069" name="libgtksourceview-common">
<property name="description" type="str">
common files for the GTK+ syntax highlighting widget
</property>
<property name="version" type="str">
1.8.5-1
</property>
</package>
<package id="1070" name="libgtksourceview1.0-0">
<property name="description" type="str">
shared libraries for the GTK+ syntax highlighting widget
</property>
<property name="version" type="str">
1.8.5-1
</property>
</package>
<package id="1071" name="libgtksourceview2.0-0">
<property name="description" type="str">
shared libraries for the GTK+ syntax highlighting widget
</property>
<property name="version" type="str">
2.2.1-1
</property>
</package>
<package id="1072" name="libgtksourceview2.0-common">
<property name="description" type="str">
common files for the GTK+ syntax highlighting widget
</property>
<property name="version" type="str">
2.2.1-1
</property>
</package>
<package id="1073" name="libgtkspell0">
<property name="description" type="str">
a spell-checking addon for GTK's TextView widget
</property>
<property name="version" type="str">
2.0.10-4
</property>
</package>
<package id="1074" name="libgtop2-7">
<property name="description" type="str">
gtop system monitoring library
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1075" name="libgtop2-common">
<property name="description" type="str">
common files for the gtop system monitoring library
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1076" name="libgucharmap6">
<property name="description" type="str">
Unicode browser widget library (shared library)
</property>
<property name="version" type="str">
1:2.22.1-0ubuntu2
</property>
</package>
<package id="1077" name="libguile-ltdl-1">
<property name="description" type="str">
Guile's patched version of libtool's libltdl
</property>
<property name="version" type="str">
1.6.8-6ubuntu1
</property>
</package>
<package id="1078" name="libgutenprint2">
<property name="description" type="str">
runtime for the Gutenprint printer driver library
</property>
<property name="version" type="str">
5.0.2-2ubuntu1
</property>
</package>
<package id="1079" name="libgvfscommon0">
<property name="description" type="str">
userspace virtual filesystem - library
</property>
<property name="version" type="str">
0.2.4-0ubuntu1
</property>
</package>
<package id="1080" name="libgweather-common">
<property name="description" type="str">
GWeather shared library
</property>
<property name="version" type="str">
2.22.1.1-0ubuntu2
</property>
</package>
<package id="1081" name="libgweather1">
<property name="description" type="str">
GWeather shared library
</property>
<property name="version" type="str">
2.22.1.1-0ubuntu2
</property>
</package>
<package id="1082" name="libhal-storage1">
<property name="description" type="str">
Hardware Abstraction Layer - shared library for storage devices
</property>
<property name="version" type="str">
0.5.11~rc2-1ubuntu8.1
</property>
</package>
<package id="1083" name="libhal1">
<property name="description" type="str">
Hardware Abstraction Layer - shared library
</property>
<property name="version" type="str">
0.5.11~rc2-1ubuntu8.1
</property>
</package>
<package id="1084" name="libhesiod0">
<property name="description" type="str">
Libraries for hesiod, a service name resolution protocol
</property>
<property name="version" type="str">
3.0.2-18.1
</property>
</package>
<package id="1085" name="libhtml-parser-perl">
<property name="description" type="str">
A collection of modules that parse HTML text documents
</property>
<property name="version" type="str">
3.56-1
</property>
</package>
<package id="1086" name="libhtml-tagset-perl">
<property name="description" type="str">
Data tables pertaining to HTML
</property>
<property name="version" type="str">
3.10-2
</property>
</package>
<package id="1087" name="libhtml-tree-perl">
<property name="description" type="str">
represent and create HTML syntax trees
</property>
<property name="version" type="str">
3.23-1
</property>
</package>
<package id="1088" name="libhunspell-1.1-0">
<property name="description" type="str">
spell checker and morphological analyzer (shared library)
</property>
<property name="version" type="str">
1.1.9-1
</property>
</package>
<package id="1089" name="libice6">
<property name="description" type="str">
X11 Inter-Client Exchange library
</property>
<property name="version" type="str">
2:1.0.4-1
</property>
</package>
<package id="1090" name="libicu38">
<property name="description" type="str">
International Components for Unicode
</property>
<property name="version" type="str">
3.8-6
</property>
</package>
<package id="1091" name="libidl0">
<property name="description" type="str">
library for parsing CORBA IDL files
</property>
<property name="version" type="str">
0.8.10-0.1
</property>
</package>
<package id="1092" name="libidn11">
<property name="description" type="str">
GNU libidn library, implementation of IETF IDN specifications
</property>
<property name="version" type="str">
1.1-1
</property>
</package>
<package id="1093" name="libiec61883-0">
<property name="description" type="str">
an partial implementation of IEC 61883
</property>
<property name="version" type="str">
1.1.0-2ubuntu2
</property>
</package>
<package id="1094" name="libieee1284-3">
<property name="description" type="str">
cross-platform library for parallel port access
</property>
<property name="version" type="str">
0.2.11-3
</property>
</package>
<package id="1095" name="libisc32">
<property name="description" type="str">
ISC Shared Library used by BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="1096" name="libisccc30">
<property name="description" type="str">
Command Channel Library used by BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="1097" name="libisccfg30">
<property name="description" type="str">
Config File Handling Library used by BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="1098" name="libiw29">
<property name="description" type="str">
Wireless tools - library
</property>
<property name="version" type="str">
29-1ubuntu2
</property>
</package>
<package id="1099" name="libjasper1">
<property name="description" type="str">
The JasPer JPEG-2000 runtime library
</property>
<property name="version" type="str">
1.900.1-3
</property>
</package>
<package id="1100" name="libjpeg62">
<property name="description" type="str">
The Independent JPEG Group's JPEG runtime library
</property>
<property name="version" type="str">
6b-14
</property>
</package>
<package id="1101" name="libkeyutils1">
<property name="description" type="str">
Linux Key Management Utilities (library)
</property>
<property name="version" type="str">
1.2-4
</property>
</package>
<package id="1102" name="libklibc">
<property name="description" type="str">
minimal libc subset for use with initramfs
</property>
<property name="version" type="str">
1.5.7-4ubuntu4
</property>
</package>
<package id="1103" name="libkpathsea4">
<property name="description" type="str">
TeX Live: path search library for TeX (runtime part)
</property>
<property name="version" type="str">
2007.dfsg.1-2
</property>
</package>
<package id="1104" name="libkrb53">
<property name="description" type="str">
MIT Kerberos runtime libraries
</property>
<property name="version" type="str">
1.6.dfsg.3~beta1-2ubuntu1
</property>
</package>
<package id="1105" name="liblaunchpad-integration1">
<property name="description" type="str">
library for launchpad integration
</property>
<property name="version" type="str">
0.1.19
</property>
</package>
<package id="1106" name="liblcms1">
<property name="description" type="str">
Color management library
</property>
<property name="version" type="str">
1.16-7ubuntu1
</property>
</package>
<package id="1107" name="libldap-2.4-2">
<property name="description" type="str">
OpenLDAP libraries
</property>
<property name="version" type="str">
2.4.9-0ubuntu0.8.04
</property>
</package>
<package id="1108" name="liblircclient0">
<property name="description" type="str">
LIRC client library
</property>
<property name="version" type="str">
0.8.3~pre1-0ubuntu7.1
</property>
</package>
<package id="1109" name="liblocale-gettext-perl">
<property name="description" type="str">
Using libc functions for internationalization in Perl
</property>
<property name="version" type="str">
1.05-2ubuntu1
</property>
</package>
<package id="1110" name="liblpint-bonobo0">
<property name="description" type="str">
library for launchpad integration
</property>
<property name="version" type="str">
0.1.19
</property>
</package>
<package id="1111" name="libltdl3">
<property name="description" type="str">
A system independent dlopen wrapper for GNU libtool
</property>
<property name="version" type="str">
1.5.26-1ubuntu1
</property>
</package>
<package id="1112" name="liblwres30">
<property name="description" type="str">
Lightweight Resolver Library used by BIND
</property>
<property name="version" type="str">
1:9.4.2-10
</property>
</package>
<package id="1113" name="liblzo2-2">
<property name="description" type="str">
data compression library
</property>
<property name="version" type="str">
2.02-3
</property>
</package>
<package id="1114" name="libmagic1">
<property name="description" type="str">
File type determination library using &quot;magic&quot; numbers
</property>
<property name="version" type="str">
4.21-3ubuntu1
</property>
</package>
<package id="1115" name="libmagick10">
<property name="description" type="str">
image manipulation library
</property>
<property name="version" type="str">
7:6.3.7.9.dfsg1-2ubuntu1
</property>
</package>
<package id="1116" name="libmeanwhile1">
<property name="description" type="str">
open implementation of the Lotus Sametime Community Client protocol
</property>
<property name="version" type="str">
1.0.2-3
</property>
</package>
<package id="1117" name="libmetacity0">
<property name="description" type="str">
library of lightweight GTK2 based Window Manager
</property>
<property name="version" type="str">
1:2.22.0-0ubuntu4
</property>
</package>
<package id="1118" name="libmng1">
<property name="description" type="str">
Multiple-image Network Graphics library
</property>
<property name="version" type="str">
1.0.9-1
</property>
</package>
<package id="1119" name="libmono-addins-gui0.2-cil">
<property name="description" type="str">
GTK# frontend library for Mono.Addins
</property>
<property name="version" type="str">
0.3.1-4
</property>
</package>
<package id="1120" name="libmono-addins0.2-cil">
<property name="description" type="str">
addin framework for extensible CLI applications/libraries
</property>
<property name="version" type="str">
0.3.1-4
</property>
</package>
<package id="1121" name="libmono-cairo1.0-cil">
<property name="description" type="str">
Mono Cairo library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1122" name="libmono-cairo2.0-cil">
<property name="description" type="str">
Mono Cairo library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1123" name="libmono-corlib1.0-cil">
<property name="description" type="str">
Mono core library (1.0)
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1124" name="libmono-corlib2.0-cil">
<property name="description" type="str">
Mono core library (2.0)
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1125" name="libmono-data-tds1.0-cil">
<property name="description" type="str">
Mono Data library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1126" name="libmono-data-tds2.0-cil">
<property name="description" type="str">
Mono Data Library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1127" name="libmono-security1.0-cil">
<property name="description" type="str">
Mono Security library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1128" name="libmono-security2.0-cil">
<property name="description" type="str">
Mono Security library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1129" name="libmono-sharpzip0.84-cil">
<property name="description" type="str">
Mono SharpZipLib library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1130" name="libmono-sharpzip2.84-cil">
<property name="description" type="str">
Mono SharpZipLib library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1131" name="libmono-sqlite2.0-cil">
<property name="description" type="str">
Mono Sqlite library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1132" name="libmono-system-data1.0-cil">
<property name="description" type="str">
Mono System.Data library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1133" name="libmono-system-data2.0-cil">
<property name="description" type="str">
Mono System.Data Library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1134" name="libmono-system-web1.0-cil">
<property name="description" type="str">
Mono System.Web library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1135" name="libmono-system-web2.0-cil">
<property name="description" type="str">
Mono System.Web Library
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1136" name="libmono-system1.0-cil">
<property name="description" type="str">
Mono System libraries (1.0)
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1137" name="libmono-system2.0-cil">
<property name="description" type="str">
Mono System libraries (2.0)
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1138" name="libmono0">
<property name="description" type="str">
libraries for the Mono JIT
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1139" name="libmono1.0-cil">
<property name="description" type="str">
Mono libraries (1.0)
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1140" name="libmono2.0-cil">
<property name="description" type="str">
Mono libraries (2.0)
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1141" name="libmtp7">
<property name="description" type="str">
Media Transfer Protocol (MTP) library
</property>
<property name="version" type="str">
0.2.6.1-2ubuntu1
</property>
</package>
<package id="1142" name="libmusicbrainz4c2a">
<property name="description" type="str">
Second generation incarnation of the CD Index - library
</property>
<property name="version" type="str">
2.1.5-1ubuntu2
</property>
</package>
<package id="1143" name="libnautilus-burn4">
<property name="description" type="str">
Nautilus Burn Library - runtime version
</property>
<property name="version" type="str">
2.22.1-0ubuntu1
</property>
</package>
<package id="1144" name="libnautilus-extension1">
<property name="description" type="str">
libraries for nautilus components - runtime version
</property>
<property name="version" type="str">
1:2.22.3-0ubuntu2
</property>
</package>
<package id="1145" name="libncurses5">
<property name="description" type="str">
Shared libraries for terminal handling
</property>
<property name="version" type="str">
5.6+20071124-1ubuntu2
</property>
</package>
<package id="1146" name="libncursesw5">
<property name="description" type="str">
Shared libraries for terminal handling (wide character support)
</property>
<property name="version" type="str">
5.6+20071124-1ubuntu2
</property>
</package>
<package id="1147" name="libndesk-dbus-glib1.0-cil">
<property name="description" type="str">
CLI implementation of D-Bus (GLib mainloop integration)
</property>
<property name="version" type="str">
0.4.1-1
</property>
</package>
<package id="1148" name="libndesk-dbus1.0-cil">
<property name="description" type="str">
CLI implementation of D-Bus
</property>
<property name="version" type="str">
0.6.0-1
</property>
</package>
<package id="1149" name="libneon27">
<property name="description" type="str">
An HTTP and WebDAV client library
</property>
<property name="version" type="str">
0.27.2-1
</property>
</package>
<package id="1150" name="libnet-dbus-perl">
<property name="description" type="str">
Perl extension for the DBus message system
</property>
<property name="version" type="str">
0.33.5-1
</property>
</package>
<package id="1151" name="libnewt0.52">
<property name="description" type="str">
Not Erik's Windowing Toolkit - text mode windowing with slang
</property>
<property name="version" type="str">
0.52.2-11.2ubuntu1
</property>
</package>
<package id="1152" name="libnl1">
<property name="description" type="str">
Library for dealing with netlink sockets
</property>
<property name="version" type="str">
1.1-1
</property>
</package>
<package id="1153" name="libnm-glib0">
<property name="description" type="str">
network management framework (GLib shared library)
</property>
<property name="version" type="str">
0.6.6-0ubuntu5
</property>
</package>
<package id="1154" name="libnm-util0">
<property name="description" type="str">
network management framework (shared library)
</property>
<property name="version" type="str">
0.6.6-0ubuntu5
</property>
</package>
<package id="1155" name="libnotify1">
<property name="description" type="str">
sends desktop notifications to a notification daemon
</property>
<property name="version" type="str">
0.4.4-3build1
</property>
</package>
<package id="1156" name="libnspr4-0d">
<property name="description" type="str">
NetScape Portable Runtime Library
</property>
<property name="version" type="str">
4.7.1+1.9-0ubuntu0.8.04.1
</property>
</package>
<package id="1157" name="libnss-mdns">
<property name="description" type="str">
NSS module for Multicast DNS name resolution
</property>
<property name="version" type="str">
0.10-3ubuntu2
</property>
</package>
<package id="1158" name="libnss3-1d">
<property name="description" type="str">
Network Security Service libraries
</property>
<property name="version" type="str">
3.12.0.2+1.9-0ubuntu0.8.04.1
</property>
</package>
<package id="1159" name="libntfs-3g23">
<property name="description" type="str">
ntfs-3g filesystem in userspace (FUSE) library
</property>
<property name="version" type="str">
1:1.2216-1ubuntu2
</property>
</package>
<package id="1160" name="libogg0">
<property name="description" type="str">
Ogg Bitstream Library
</property>
<property name="version" type="str">
1.1.3-3ubuntu1
</property>
</package>
<package id="1161" name="liboil0.3">
<property name="description" type="str">
Library of Optimized Inner Loops
</property>
<property name="version" type="str">
0.3.14-3
</property>
</package>
<package id="1162" name="liboobs-1-4">
<property name="description" type="str">
GObject based interface to system-tools-backends - shared library
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1163" name="libopal-2.2">
<property name="description" type="str">
Open Phone Abstraction Library - successor of OpenH323
</property>
<property name="version" type="str">
2.2.11~dfsg1-3ubuntu2
</property>
</package>
<package id="1164" name="libopenal0a">
<property name="description" type="str">
OpenAL is a portable library for 3D spatialized audio
</property>
<property name="version" type="str">
1:0.0.8-7
</property>
</package>
<package id="1165" name="libopencdk10">
<property name="description" type="str">
Open Crypto Development Kit (OpenCDK) (runtime)
</property>
<property name="version" type="str">
0.6.6-1ubuntu1
</property>
</package>
<package id="1166" name="libopenexr2ldbl">
<property name="description" type="str">
runtime files for the OpenEXR image library
</property>
<property name="version" type="str">
1.2.2-4.4ubuntu1
</property>
</package>
<package id="1167" name="libopenobex1">
<property name="description" type="str">
OBEX protocol library
</property>
<property name="version" type="str">
1.3-3ubuntu1
</property>
</package>
<package id="1168" name="liborbit2">
<property name="description" type="str">
libraries for ORBit2 - a CORBA ORB
</property>
<property name="version" type="str">
1:2.14.12-0.1
</property>
</package>
<package id="1169" name="libotr2">
<property name="description" type="str">
Off-the-Record Messaging library
</property>
<property name="version" type="str">
3.1.0-2
</property>
</package>
<package id="1170" name="libpam-gnome-keyring">
<property name="description" type="str">
PAM module to unlock the GNOME keyring upon login
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="1171" name="libpam-modules">
<property name="description" type="str">
Pluggable Authentication Modules for PAM
</property>
<property name="version" type="str">
0.99.7.1-5ubuntu6.1
</property>
</package>
<package id="1172" name="libpam-runtime">
<property name="description" type="str">
Runtime support for the PAM library
</property>
<property name="version" type="str">
0.99.7.1-5ubuntu6.1
</property>
</package>
<package id="1173" name="libpam0g">
<property name="description" type="str">
Pluggable Authentication Modules library
</property>
<property name="version" type="str">
0.99.7.1-5ubuntu6.1
</property>
</package>
<package id="1174" name="libpanel-applet2-0">
<property name="description" type="str">
library for GNOME Panel applets
</property>
<property name="version" type="str">
1:2.22.2-0ubuntu1
</property>
</package>
<package id="1175" name="libpango1.0-0">
<property name="description" type="str">
Layout and rendering of internationalized text
</property>
<property name="version" type="str">
1.20.1-1
</property>
</package>
<package id="1176" name="libpango1.0-common">
<property name="description" type="str">
Modules and configuration files for the Pango
</property>
<property name="version" type="str">
1.20.1-1
</property>
</package>
<package id="1177" name="libpaper-utils">
<property name="description" type="str">
library for handling paper characteristics (utilities)
</property>
<property name="version" type="str">
1.1.23
</property>
</package>
<package id="1178" name="libpaper1">
<property name="description" type="str">
library for handling paper characteristics
</property>
<property name="version" type="str">
1.1.23
</property>
</package>
<package id="1179" name="libparted1.7-1">
<property name="description" type="str">
The GNU Parted disk partitioning shared library
</property>
<property name="version" type="str">
1.7.1-5.1ubuntu9.1
</property>
</package>
<package id="1180" name="libpcap0.8">
<property name="description" type="str">
System interface for user-level packet capture
</property>
<property name="version" type="str">
0.9.8-2
</property>
</package>
<package id="1181" name="libpcre3">
<property name="description" type="str">
Perl 5 Compatible Regular Expression Library - runtime files
</property>
<property name="version" type="str">
7.4-1ubuntu2
</property>
</package>
<package id="1182" name="libperl5.8">
<property name="description" type="str">
Shared Perl library
</property>
<property name="version" type="str">
5.8.8-12
</property>
</package>
<package id="1183" name="libpisock9">
<property name="description" type="str">
library for communicating with a PalmOS PDA
</property>
<property name="version" type="str">
0.12.3-4ubuntu1
</property>
</package>
<package id="1184" name="libpisync1">
<property name="description" type="str">
synchronization library for PalmOS devices
</property>
<property name="version" type="str">
0.12.3-4ubuntu1
</property>
</package>
<package id="1185" name="libpixman-1-0">
<property name="description" type="str">
pixel-manipulation library for X and cairo
</property>
<property name="version" type="str">
0.10.0-0ubuntu1
</property>
</package>
<package id="1186" name="libpng12-0">
<property name="description" type="str">
PNG library - runtime
</property>
<property name="version" type="str">
1.2.15~beta5-3
</property>
</package>
<package id="1187" name="libpolkit-dbus2">
<property name="description" type="str">
library for accessing PolicyKit via D-Bus
</property>
<property name="version" type="str">
0.7-2ubuntu7
</property>
</package>
<package id="1188" name="libpolkit-gnome0">
<property name="description" type="str">
PolicyKit-gnome library
</property>
<property name="version" type="str">
0.7-2ubuntu1.1
</property>
</package>
<package id="1189" name="libpolkit-grant2">
<property name="description" type="str">
library for obtaining privileges via PolicyKit
</property>
<property name="version" type="str">
0.7-2ubuntu7
</property>
</package>
<package id="1190" name="libpolkit2">
<property name="description" type="str">
library for accessing PolicyKit
</property>
<property name="version" type="str">
0.7-2ubuntu7
</property>
</package>
<package id="1191" name="libpoppler-glib2">
<property name="description" type="str">
PDF rendering library (GLib-based shared library)
</property>
<property name="version" type="str">
0.6.4-1ubuntu2
</property>
</package>
<package id="1192" name="libpoppler2">
<property name="description" type="str">
PDF rendering library
</property>
<property name="version" type="str">
0.6.4-1ubuntu2
</property>
</package>
<package id="1193" name="libpopt0">
<property name="description" type="str">
lib for parsing cmdline parameters
</property>
<property name="version" type="str">
1.10-3build1
</property>
</package>
<package id="1194" name="libportaudio0">
<property name="description" type="str">
Portable audio I/O - shared library
</property>
<property name="version" type="str">
18.1-6
</property>
</package>
<package id="1195" name="libpt-1.10.10">
<property name="description" type="str">
Portable Windows Library
</property>
<property name="version" type="str">
1.10.10-1ubuntu6
</property>
</package>
<package id="1196" name="libpt-1.10.10-plugins-alsa">
<property name="description" type="str">
Portable Windows Library Audio Plugin for the ALSA Interface
</property>
<property name="version" type="str">
1.10.10-1ubuntu6
</property>
</package>
<package id="1197" name="libpt-1.10.10-plugins-v4l">
<property name="description" type="str">
Portable Windows Library Video Plugin for Video4Linux
</property>
<property name="version" type="str">
1.10.10-1ubuntu6
</property>
</package>
<package id="1198" name="libpt-1.10.10-plugins-v4l2">
<property name="description" type="str">
Portable Windows Library Video Plugin for Video4Linux v2
</property>
<property name="version" type="str">
1.10.10-1ubuntu6
</property>
</package>
<package id="1199" name="libpth20">
<property name="description" type="str">
The GNU Portable Threads
</property>
<property name="version" type="str">
2.0.7-8
</property>
</package>
<package id="1200" name="libpulse-browse0">
<property name="description" type="str">
PulseAudio client libraries (zeroconf support)
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1201" name="libpulse0">
<property name="description" type="str">
PulseAudio client libraries
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1202" name="libpulsecore5">
<property name="description" type="str">
PulseAudio sound server core
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1203" name="libpurple0">
<property name="description" type="str">
multi-protocol instant messaging library
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1204" name="libqthreads-12">
<property name="description" type="str">
QuickThreads library for Guile
</property>
<property name="version" type="str">
1.6.8-6ubuntu1
</property>
</package>
<package id="1205" name="librarian0">
<property name="description" type="str">
Rarian is a documentation meta-data library (library package)
</property>
<property name="version" type="str">
0.8.0-0ubuntu1
</property>
</package>
<package id="1206" name="libraw1394-8">
<property name="description" type="str">
library for direct access to IEEE 1394 bus (aka FireWire)
</property>
<property name="version" type="str">
1.3.0-2
</property>
</package>
<package id="1207" name="libreadline5">
<property name="description" type="str">
GNU readline and history libraries, run-time libraries
</property>
<property name="version" type="str">
5.2-3build1
</property>
</package>
<package id="1208" name="librecode0">
<property name="description" type="str">
Shared library on which recode is based
</property>
<property name="version" type="str">
3.6-14ubuntu1
</property>
</package>
<package id="1209" name="librpc-xml-perl">
<property name="description" type="str">
Perl module implementation of XML-RPC
</property>
<property name="version" type="str">
0.59-2
</property>
</package>
<package id="1210" name="librsvg2-2">
<property name="description" type="str">
SAX-based renderer library for SVG files (runtime)
</property>
<property name="version" type="str">
2.22.2-2
</property>
</package>
<package id="1211" name="librsvg2-common">
<property name="description" type="str">
SAX-based renderer library for SVG files (extra runtime)
</property>
<property name="version" type="str">
2.22.2-2
</property>
</package>
<package id="1212" name="libsamplerate0">
<property name="description" type="str">
audio rate conversion library
</property>
<property name="version" type="str">
0.1.2-5ubuntu1
</property>
</package>
<package id="1213" name="libsane">
<property name="description" type="str">
API library for scanners
</property>
<property name="version" type="str">
1.0.19-1ubuntu3
</property>
</package>
<package id="1214" name="libsasl2-2">
<property name="description" type="str">
Cyrus SASL - authentication abstraction library
</property>
<property name="version" type="str">
2.1.22.dfsg1-18ubuntu2
</property>
</package>
<package id="1215" name="libsasl2-modules">
<property name="description" type="str">
Cyrus SASL - pluggable authentication modules
</property>
<property name="version" type="str">
2.1.22.dfsg1-18ubuntu2
</property>
</package>
<package id="1216" name="libscim8c2a">
<property name="description" type="str">
library for SCIM platform
</property>
<property name="version" type="str">
1.4.7-3ubuntu8
</property>
</package>
<package id="1217" name="libscrollkeeper0">
<property name="description" type="str">
Library to load .omf files (runtime files)
</property>
<property name="version" type="str">
0.3.14-15ubuntu1
</property>
</package>
<package id="1218" name="libsdl1.2debian">
<property name="description" type="str">
Simple DirectMedia Layer
</property>
<property name="version" type="str">
1.2.13-1ubuntu1
</property>
</package>
<package id="1219" name="libsdl1.2debian-alsa">
<property name="description" type="str">
Simple DirectMedia Layer (with X11 and ALSA options)
</property>
<property name="version" type="str">
1.2.13-1ubuntu1
</property>
</package>
<package id="1220" name="libselinux1">
<property name="description" type="str">
SELinux policy enforcement, run-time libraries
</property>
<property name="version" type="str">
2.0.55-0ubuntu4
</property>
</package>
<package id="1221" name="libsensors3">
<property name="description" type="str">
library to read temperature/voltage/fan sensors
</property>
<property name="version" type="str">
1:2.10.5-3ubuntu1
</property>
</package>
<package id="1222" name="libsepol1">
<property name="description" type="str">
SELinux binary policy, run-time library
</property>
<property name="version" type="str">
2.0.20-0ubuntu3
</property>
</package>
<package id="1223" name="libsexy2">
<property name="description" type="str">
collection of additional GTK+ widgets - library
</property>
<property name="version" type="str">
0.1.11-2
</property>
</package>
<package id="1224" name="libsgutils1">
<property name="description" type="str">
Utilities for working with generic SCSI devices (shared libraries)
</property>
<property name="version" type="str">
1.24-1
</property>
</package>
<package id="1225" name="libshout3">
<property name="description" type="str">
MP3/Ogg Vorbis broadcast streaming library
</property>
<property name="version" type="str">
2.2.2-2
</property>
</package>
<package id="1226" name="libsigc++-2.0-0c2a">
<property name="description" type="str">
type-safe Signal Framework for C++ - runtime
</property>
<property name="version" type="str">
2.0.17-2ubuntu3
</property>
</package>
<package id="1227" name="libslang2">
<property name="description" type="str">
The S-Lang programming library - runtime version
</property>
<property name="version" type="str">
2.1.3-2
</property>
</package>
<package id="1228" name="libslp1">
<property name="description" type="str">
OpenSLP libraries
</property>
<property name="version" type="str">
1.2.1-7.1
</property>
</package>
<package id="1229" name="libsm6">
<property name="description" type="str">
X11 Session Management library
</property>
<property name="version" type="str">
2:1.0.3-1
</property>
</package>
<package id="1230" name="libsmbclient">
<property name="description" type="str">
shared library that allows applications to talk to SMB/CIFS servers
</property>
<property name="version" type="str">
3.0.28a-1ubuntu4.4
</property>
</package>
<package id="1231" name="libsmbios1">
<property name="description" type="str">
Provide access to (SM)BIOS information -- dynamic library
</property>
<property name="version" type="str">
0.13.10-1ubuntu1
</property>
</package>
<package id="1232" name="libsndfile1">
<property name="description" type="str">
Library for reading/writing audio files
</property>
<property name="version" type="str">
1.0.17-4
</property>
</package>
<package id="1233" name="libsnmp-base">
<property name="description" type="str">
SNMP (Simple Network Management Protocol) MIBs and documentation
</property>
<property name="version" type="str">
5.4.1~dfsg-4ubuntu4
</property>
</package>
<package id="1234" name="libsnmp15">
<property name="description" type="str">
SNMP (Simple Network Management Protocol) library
</property>
<property name="version" type="str">
5.4.1~dfsg-4ubuntu4
</property>
</package>
<package id="1235" name="libsoup2.4-1">
<property name="description" type="str">
an HTTP library implementation in C -- Shared library
</property>
<property name="version" type="str">
2.4.1-1
</property>
</package>
<package id="1236" name="libspeex1">
<property name="description" type="str">
The Speex Speech Codec
</property>
<property name="version" type="str">
1.1.12-3ubuntu0.8.04.1
</property>
</package>
<package id="1237" name="libsqlite0">
<property name="description" type="str">
SQLite shared library
</property>
<property name="version" type="str">
2.8.17-4build1
</property>
</package>
<package id="1238" name="libsqlite3-0">
<property name="description" type="str">
SQLite 3 shared library
</property>
<property name="version" type="str">
3.4.2-2
</property>
</package>
<package id="1239" name="libss2">
<property name="description" type="str">
command-line interface parsing library
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="1240" name="libssl0.9.8">
<property name="description" type="str">
SSL shared libraries
</property>
<property name="version" type="str">
0.9.8g-4ubuntu3.3
</property>
</package>
<package id="1241" name="libstartup-notification0">
<property name="description" type="str">
library for program launch feedback (shared library)
</property>
<property name="version" type="str">
0.9-1
</property>
</package>
<package id="1242" name="libstdc++6">
<property name="description" type="str">
The GNU Standard C++ Library v3
</property>
<property name="version" type="str">
4.2.3-2ubuntu7
</property>
</package>
<package id="1243" name="libsysfs2">
<property name="description" type="str">
interface library to sysfs
</property>
<property name="version" type="str">
2.1.0-4
</property>
</package>
<package id="1244" name="libtag1c2a">
<property name="description" type="str">
TagLib Audio Meta-Data Library
</property>
<property name="version" type="str">
1.4-8ubuntu1
</property>
</package>
<package id="1245" name="libtasn1-3">
<property name="description" type="str">
Manage ASN.1 structures (runtime)
</property>
<property name="version" type="str">
1.1-1
</property>
</package>
<package id="1246" name="libterm-readkey-perl">
<property name="description" type="str">
A perl module for simple terminal control
</property>
<property name="version" type="str">
2.30-3ubuntu1
</property>
</package>
<package id="1247" name="libtext-charwidth-perl">
<property name="description" type="str">
get display widths of characters on the terminal
</property>
<property name="version" type="str">
0.04-4build1
</property>
</package>
<package id="1248" name="libtext-iconv-perl">
<property name="description" type="str">
converts between character sets in Perl
</property>
<property name="version" type="str">
1.4-3
</property>
</package>
<package id="1249" name="libtext-wrapi18n-perl">
<property name="description" type="str">
internationalized substitute of Text::Wrap
</property>
<property name="version" type="str">
0.06-5
</property>
</package>
<package id="1250" name="libthai-data">
<property name="description" type="str">
Data files for Thai language support library
</property>
<property name="version" type="str">
0.1.9-1
</property>
</package>
<package id="1251" name="libthai0">
<property name="description" type="str">
Thai language support library
</property>
<property name="version" type="str">
0.1.9-1
</property>
</package>
<package id="1252" name="libtheora0">
<property name="description" type="str">
The Theora Video Compression Codec
</property>
<property name="version" type="str">
1.0~beta2-2
</property>
</package>
<package id="1253" name="libtiff4">
<property name="description" type="str">
Tag Image File Format (TIFF) library
</property>
<property name="version" type="str">
3.8.2-7ubuntu3
</property>
</package>
<package id="1254" name="libtotem-plparser10">
<property name="description" type="str">
Totem Playlist Parser library - runtime version
</property>
<property name="version" type="str">
2.22.3-0ubuntu2
</property>
</package>
<package id="1255" name="libtracker-gtk0">
<property name="description" type="str">
GTK+ widgets for apps that use tracker
</property>
<property name="version" type="str">
0.6.6-0ubuntu3.8.04.1
</property>
</package>
<package id="1256" name="libtrackerclient0">
<property name="description" type="str">
metadata database, indexer and search tool - library
</property>
<property name="version" type="str">
0.6.6-0ubuntu3.8.04.1
</property>
</package>
<package id="1257" name="libuniconf4.4">
<property name="description" type="str">
C++ network libraries for rapid application development
</property>
<property name="version" type="str">
4.4.1-0ubuntu2
</property>
</package>
<package id="1258" name="liburi-perl">
<property name="description" type="str">
Manipulates and accesses URI strings
</property>
<property name="version" type="str">
1.35.dfsg.1-1
</property>
</package>
<package id="1259" name="libusb-0.1-4">
<property name="description" type="str">
userspace USB programming library
</property>
<property name="version" type="str">
2:0.1.12-8
</property>
</package>
<package id="1260" name="libusplash0">
<property name="description" type="str">
userspace bootsplash library
</property>
<property name="version" type="str">
0.5.19
</property>
</package>
<package id="1261" name="libuuid1">
<property name="description" type="str">
universally unique id library
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="1262" name="libvisual-0.4-0">
<property name="description" type="str">
Audio visualization framework
</property>
<property name="version" type="str">
0.4.0-2
</property>
</package>
<package id="1263" name="libvolume-id0">
<property name="description" type="str">
volume identification library
</property>
<property name="version" type="str">
117-8
</property>
</package>
<package id="1264" name="libvorbis0a">
<property name="description" type="str">
The Vorbis General Audio Compression Codec
</property>
<property name="version" type="str">
1.2.0.dfsg-2
</property>
</package>
<package id="1265" name="libvorbisenc2">
<property name="description" type="str">
The Vorbis General Audio Compression Codec
</property>
<property name="version" type="str">
1.2.0.dfsg-2
</property>
</package>
<package id="1266" name="libvorbisfile3">
<property name="description" type="str">
The Vorbis General Audio Compression Codec
</property>
<property name="version" type="str">
1.2.0.dfsg-2
</property>
</package>
<package id="1267" name="libvte-common">
<property name="description" type="str">
Terminal emulator widget for GTK+ 2.0 - common files
</property>
<property name="version" type="str">
1:0.16.13-1ubuntu1
</property>
</package>
<package id="1268" name="libvte9">
<property name="description" type="str">
Terminal emulator widget for GTK+ 2.0 - runtime files
</property>
<property name="version" type="str">
1:0.16.13-1ubuntu1
</property>
</package>
<package id="1269" name="libwavpack1">
<property name="description" type="str">
an audio codec (lossy and lossless) - library
</property>
<property name="version" type="str">
4.41.0-1
</property>
</package>
<package id="1270" name="libwmf0.2-7">
<property name="description" type="str">
Windows metafile conversion library
</property>
<property name="version" type="str">
0.2.8.4-6
</property>
</package>
<package id="1271" name="libwnck-common">
<property name="description" type="str">
Window Navigator Construction Kit - common files
</property>
<property name="version" type="str">
2.22.1-0ubuntu1
</property>
</package>
<package id="1272" name="libwnck22">
<property name="description" type="str">
Window Navigator Construction Kit - runtime files
</property>
<property name="version" type="str">
2.22.1-0ubuntu1
</property>
</package>
<package id="1273" name="libwpd8c2a">
<property name="description" type="str">
Library for handling WordPerfect documents (shared library)
</property>
<property name="version" type="str">
0.8.12-1ubuntu1
</property>
</package>
<package id="1274" name="libwpg-0.1-1">
<property name="description" type="str">
WordPerfect graphics import/convert library (shared library)
</property>
<property name="version" type="str">
0.1.1-1
</property>
</package>
<package id="1275" name="libwps-0.1-1">
<property name="description" type="str">
Works text file format import filter library (shared library)
</property>
<property name="version" type="str">
0.1.1-1
</property>
</package>
<package id="1276" name="libwrap0">
<property name="description" type="str">
Wietse Venema's TCP wrappers library
</property>
<property name="version" type="str">
7.6.dbs-14
</property>
</package>
<package id="1277" name="libwvstreams4.4-base">
<property name="description" type="str">
C++ network libraries for rapid application development
</property>
<property name="version" type="str">
4.4.1-0ubuntu2
</property>
</package>
<package id="1278" name="libwvstreams4.4-extras">
<property name="description" type="str">
C++ network libraries for rapid application development
</property>
<property name="version" type="str">
4.4.1-0ubuntu2
</property>
</package>
<package id="1279" name="libwww-perl">
<property name="description" type="str">
WWW client/server library for Perl (aka LWP)
</property>
<property name="version" type="str">
5.808-1
</property>
</package>
<package id="1280" name="libx11-6">
<property name="description" type="str">
X11 client-side library
</property>
<property name="version" type="str">
2:1.1.3-1ubuntu2
</property>
</package>
<package id="1281" name="libx11-data">
<property name="description" type="str">
X11 client-side library
</property>
<property name="version" type="str">
2:1.1.3-1ubuntu2
</property>
</package>
<package id="1282" name="libx11-xcb1">
<property name="description" type="str">
Xlib/XCB interface library
</property>
<property name="version" type="str">
2:1.1.3-1ubuntu2
</property>
</package>
<package id="1283" name="libx86-1">
<property name="description" type="str">
x86 real-mode library
</property>
<property name="version" type="str">
0.99-1.2ubuntu4
</property>
</package>
<package id="1284" name="libxau6">
<property name="description" type="str">
X11 authorisation library
</property>
<property name="version" type="str">
1:1.0.3-2
</property>
</package>
<package id="1285" name="libxaw7">
<property name="description" type="str">
X11 Athena Widget library
</property>
<property name="version" type="str">
2:1.0.4-1
</property>
</package>
<package id="1286" name="libxcb-xlib0">
<property name="description" type="str">
X C Binding, Xlib/XCB interface library
</property>
<property name="version" type="str">
1.1-1ubuntu1
</property>
</package>
<package id="1287" name="libxcb1">
<property name="description" type="str">
X C Binding
</property>
<property name="version" type="str">
1.1-1ubuntu1
</property>
</package>
<package id="1288" name="libxcomposite1">
<property name="description" type="str">
X11 Composite extension library
</property>
<property name="version" type="str">
1:0.4.0-1
</property>
</package>
<package id="1289" name="libxcursor1">
<property name="description" type="str">
X cursor management library
</property>
<property name="version" type="str">
1:1.1.9-1
</property>
</package>
<package id="1290" name="libxdamage1">
<property name="description" type="str">
X11 damaged region extension library
</property>
<property name="version" type="str">
1:1.1.1-3
</property>
</package>
<package id="1291" name="libxdmcp6">
<property name="description" type="str">
X11 Display Manager Control Protocol library
</property>
<property name="version" type="str">
1:1.0.2-2
</property>
</package>
<package id="1292" name="libxevie1">
<property name="description" type="str">
X11 EvIE extension library
</property>
<property name="version" type="str">
1:1.0.2-2
</property>
</package>
<package id="1293" name="libxext6">
<property name="description" type="str">
X11 miscellaneous extension library
</property>
<property name="version" type="str">
2:1.0.3-2build1
</property>
</package>
<package id="1294" name="libxfixes3">
<property name="description" type="str">
X11 miscellaneous 'fixes' extension library
</property>
<property name="version" type="str">
1:4.0.3-2
</property>
</package>
<package id="1295" name="libxfont1">
<property name="description" type="str">
X11 font rasterisation library
</property>
<property name="version" type="str">
1:1.3.1-2
</property>
</package>
<package id="1296" name="libxft2">
<property name="description" type="str">
FreeType-based font drawing library for X
</property>
<property name="version" type="str">
2.1.12-2ubuntu5
</property>
</package>
<package id="1297" name="libxi6">
<property name="description" type="str">
X11 Input extension library
</property>
<property name="version" type="str">
2:1.1.3-1
</property>
</package>
<package id="1298" name="libxinerama1">
<property name="description" type="str">
X11 Xinerama extension library
</property>
<property name="version" type="str">
2:1.0.2-1build1
</property>
</package>
<package id="1299" name="libxkbfile1">
<property name="description" type="str">
X11 keyboard file manipulation library
</property>
<property name="version" type="str">
1:1.0.4-1
</property>
</package>
<package id="1300" name="libxklavier12">
<property name="description" type="str">
X Keyboard Extension high-level API
</property>
<property name="version" type="str">
3.5-1
</property>
</package>
<package id="1301" name="libxml-parser-perl">
<property name="description" type="str">
Perl module for parsing XML files
</property>
<property name="version" type="str">
2.34-4.3
</property>
</package>
<package id="1302" name="libxml-twig-perl">
<property name="description" type="str">
Perl module for processing huge XML documents in tree mode
</property>
<property name="version" type="str">
1:3.32-1
</property>
</package>
<package id="1303" name="libxml2">
<property name="description" type="str">
GNOME XML library
</property>
<property name="version" type="str">
2.6.31.dfsg-2ubuntu1
</property>
</package>
<package id="1304" name="libxml2-utils">
<property name="description" type="str">
XML utilities
</property>
<property name="version" type="str">
2.6.31.dfsg-2ubuntu1
</property>
</package>
<package id="1305" name="libxmu6">
<property name="description" type="str">
X11 miscellaneous utility library
</property>
<property name="version" type="str">
2:1.0.4-1
</property>
</package>
<package id="1306" name="libxmuu1">
<property name="description" type="str">
X11 miscellaneous micro-utility library
</property>
<property name="version" type="str">
2:1.0.4-1
</property>
</package>
<package id="1307" name="libxp6">
<property name="description" type="str">
X Printing Extension (Xprint) client library
</property>
<property name="version" type="str">
1:1.0.0.xsf1-1build1
</property>
</package>
<package id="1308" name="libxplc0.3.13">
<property name="description" type="str">
Light weight component system
</property>
<property name="version" type="str">
0.3.13-1build1
</property>
</package>
<package id="1309" name="libxpm4">
<property name="description" type="str">
X11 pixmap library
</property>
<property name="version" type="str">
1:3.5.7-1
</property>
</package>
<package id="1310" name="libxrandr2">
<property name="description" type="str">
X11 RandR extension library
</property>
<property name="version" type="str">
2:1.2.2-1
</property>
</package>
<package id="1311" name="libxrender1">
<property name="description" type="str">
X Rendering Extension client library
</property>
<property name="version" type="str">
1:0.9.4-1
</property>
</package>
<package id="1312" name="libxres1">
<property name="description" type="str">
X11 Resource extension library
</property>
<property name="version" type="str">
2:1.0.3-1
</property>
</package>
<package id="1313" name="libxslt1.1">
<property name="description" type="str">
XSLT processing library - runtime library
</property>
<property name="version" type="str">
1.1.22-1ubuntu1
</property>
</package>
<package id="1314" name="libxss1">
<property name="description" type="str">
X11 Screen Saver extension library
</property>
<property name="version" type="str">
1:1.1.2-1
</property>
</package>
<package id="1315" name="libxt6">
<property name="description" type="str">
X11 toolkit intrinsics library
</property>
<property name="version" type="str">
1:1.0.5-3
</property>
</package>
<package id="1316" name="libxtrap6">
<property name="description" type="str">
X11 event trapping extension library
</property>
<property name="version" type="str">
2:1.0.0-4build1
</property>
</package>
<package id="1317" name="libxtst6">
<property name="description" type="str">
X11 Testing -- Resource extension library
</property>
<property name="version" type="str">
2:1.0.3-1
</property>
</package>
<package id="1318" name="libxv1">
<property name="description" type="str">
X11 Video extension library
</property>
<property name="version" type="str">
2:1.0.3-1ubuntu1
</property>
</package>
<package id="1319" name="libxxf86dga1">
<property name="description" type="str">
X11 Direct Graphics Access extension library
</property>
<property name="version" type="str">
2:1.0.2-1
</property>
</package>
<package id="1320" name="libxxf86misc1">
<property name="description" type="str">
X11 XFree86 miscellaneous extension library
</property>
<property name="version" type="str">
1:1.0.1-2
</property>
</package>
<package id="1321" name="libxxf86vm1">
<property name="description" type="str">
X11 XFree86 video mode extension library
</property>
<property name="version" type="str">
1:1.0.1-2
</property>
</package>
<package id="1322" name="libzephyr3">
<property name="description" type="str">
The original &quot;Instant Message&quot; system libraries without Kerberos
</property>
<property name="version" type="str">
2.1.20070719.SNAPSHOT-1
</property>
</package>
<package id="1323" name="linux-generic">
<property name="description" type="str">
Complete Generic Linux kernel
</property>
<property name="version" type="str">
2.6.24.19.21
</property>
</package>
<package id="1324" name="linux-headers-2.6.24-19">
<property name="description" type="str">
Header files related to Linux kernel version 2.6.24
</property>
<property name="version" type="str">
2.6.24-19.34
</property>
</package>
<package id="1325" name="linux-headers-2.6.24-19-generic">
<property name="description" type="str">
Linux kernel headers for version 2.6.24 on x86/x86_64
</property>
<property name="version" type="str">
2.6.24-19.34
</property>
</package>
<package id="1326" name="linux-headers-generic">
<property name="description" type="str">
Generic Linux kernel headers
</property>
<property name="version" type="str">
2.6.24.19.21
</property>
</package>
<package id="1327" name="linux-image-2.6.24-19-generic">
<property name="description" type="str">
Linux kernel image for version 2.6.24 on x86/x86_64
</property>
<property name="version" type="str">
2.6.24-19.34
</property>
</package>
<package id="1328" name="linux-image-generic">
<property name="description" type="str">
Generic Linux kernel image
</property>
<property name="version" type="str">
2.6.24.19.21
</property>
</package>
<package id="1329" name="linux-restricted-modules-2.6.24-19-generic">
<property name="description" type="str">
Non-free Linux 2.6.24 modules on x86/x86_64
</property>
<property name="version" type="str">
2.6.24.13-19.44
</property>
</package>
<package id="1330" name="linux-restricted-modules-common">
<property name="description" type="str">
Non-free Linux 2.6.24 modules helper script
</property>
<property name="version" type="str">
2.6.24.13-19.44
</property>
</package>
<package id="1331" name="linux-restricted-modules-generic">
<property name="description" type="str">
Restricted Linux modules for generic kernels
</property>
<property name="version" type="str">
2.6.24.19.21
</property>
</package>
<package id="1332" name="linux-sound-base">
<property name="description" type="str">
base package for ALSA and OSS sound systems
</property>
<property name="version" type="str">
1.0.16-0ubuntu4
</property>
</package>
<package id="1333" name="linux-ubuntu-modules-2.6.24-19-generic">
<property name="description" type="str">
Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
</property>
<property name="version" type="str">
2.6.24-19.28
</property>
</package>
<package id="1334" name="locales">
<property name="description" type="str">
common files for locale support
</property>
<property name="version" type="str">
2.7.9-4
</property>
</package>
<package id="1335" name="login">
<property name="description" type="str">
system login tools
</property>
<property name="version" type="str">
1:4.0.18.2-1ubuntu2
</property>
</package>
<package id="1336" name="logrotate">
<property name="description" type="str">
Log rotation utility
</property>
<property name="version" type="str">
3.7.1-3
</property>
</package>
<package id="1337" name="lsb-base">
<property name="description" type="str">
Linux Standard Base 3.2 init script functionality
</property>
<property name="version" type="str">
3.2-4ubuntu1
</property>
</package>
<package id="1338" name="lsb-release">
<property name="description" type="str">
Linux Standard Base version reporting utility
</property>
<property name="version" type="str">
3.2-4ubuntu1
</property>
</package>
<package id="1339" name="lshw">
<property name="description" type="str">
information about hardware configuration
</property>
<property name="version" type="str">
02.12.01-2ubuntu1.1
</property>
</package>
<package id="1340" name="lsof">
<property name="description" type="str">
List open files
</property>
<property name="version" type="str">
4.78.dfsg.1-3
</property>
</package>
<package id="1341" name="ltrace">
<property name="description" type="str">
Tracks runtime library calls in dynamically linked programs
</property>
<property name="version" type="str">
0.5-3ubuntu1
</property>
</package>
<package id="1342" name="lzma">
<property name="description" type="str">
Compression method of 7z format in 7-Zip program
</property>
<property name="version" type="str">
4.43-12ubuntu1
</property>
</package>
<package id="1343" name="make">
<property name="description" type="str">
The GNU version of the &quot;make&quot; utility.
</property>
<property name="version" type="str">
3.81-3build1
</property>
</package>
<package id="1344" name="makedev">
<property name="description" type="str">
creates device files in /dev
</property>
<property name="version" type="str">
2.3.1-84ubuntu1
</property>
</package>
<package id="1345" name="man-db">
<property name="description" type="str">
on-line manual pager
</property>
<property name="version" type="str">
2.5.1-3
</property>
</package>
<package id="1346" name="manpages">
<property name="description" type="str">
Manual pages about using a GNU/Linux system
</property>
<property name="version" type="str">
2.77-1
</property>
</package>
<package id="1347" name="mawk">
<property name="description" type="str">
a pattern scanning and text processing language
</property>
<property name="version" type="str">
1.3.3-11ubuntu2
</property>
</package>
<package id="1348" name="mdetect">
<property name="description" type="str">
mouse device autodetection tool
</property>
<property name="version" type="str">
0.5.2.1ubuntu4
</property>
</package>
<package id="1349" name="memtest86+">
<property name="description" type="str">
thorough real-mode memory tester
</property>
<property name="version" type="str">
1.70-3ubuntu1
</property>
</package>
<package id="1350" name="mesa-utils">
<property name="description" type="str">
Miscellaneous Mesa GL utilities
</property>
<property name="version" type="str">
7.0.3~rc2-1ubuntu3
</property>
</package>
<package id="1351" name="metacity">
<property name="description" type="str">
A lightweight GTK2 based Window Manager
</property>
<property name="version" type="str">
1:2.22.0-0ubuntu4
</property>
</package>
<package id="1352" name="metacity-common">
<property name="description" type="str">
Shared files of lightweight GTK2 based Window Manager
</property>
<property name="version" type="str">
1:2.22.0-0ubuntu4
</property>
</package>
<package id="1353" name="mii-diag">
<property name="description" type="str">
A little tool to manipulate network cards
</property>
<property name="version" type="str">
2.11-2
</property>
</package>
<package id="1354" name="mime-support">
<property name="description" type="str">
MIME files 'mime.types' &amp; 'mailcap', and support programs
</property>
<property name="version" type="str">
3.39-1ubuntu1
</property>
</package>
<package id="1355" name="min12xxw">
<property name="description" type="str">
Printer driver for KonicaMinolta PagePro 1[234]xxW
</property>
<property name="version" type="str">
0.0.9-1build1
</property>
</package>
<package id="1356" name="mktemp">
<property name="description" type="str">
Makes unique filenames for temporary files
</property>
<property name="version" type="str">
1.5-5ubuntu2
</property>
</package>
<package id="1357" name="mlocate">
<property name="description" type="str">
quickly find files on the filesystem based on their name
</property>
<property name="version" type="str">
0.18-2ubuntu1
</property>
</package>
<package id="1358" name="module-init-tools">
<property name="description" type="str">
tools for managing Linux kernel modules
</property>
<property name="version" type="str">
3.3-pre11-4ubuntu5
</property>
</package>
<package id="1359" name="mono-common">
<property name="description" type="str">
common files for Mono
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1360" name="mono-gac">
<property name="description" type="str">
Mono GAC tool
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1361" name="mono-jit">
<property name="description" type="str">
fast CLI JIT/AOT compiler for Mono
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1362" name="mono-runtime">
<property name="description" type="str">
Mono runtime
</property>
<property name="version" type="str">
1.2.6+dfsg-6ubuntu3
</property>
</package>
<package id="1363" name="mount">
<property name="description" type="str">
Tools for mounting and manipulating filesystems
</property>
<property name="version" type="str">
2.13.1-5ubuntu2
</property>
</package>
<package id="1364" name="mousetweaks">
<property name="description" type="str">
mouse accessibility enhancements for the GNOME desktop
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="1365" name="mscompress">
<property name="description" type="str">
Microsoft &quot;compress.exe/expand.exe&quot; compatible (de)compressor
</property>
<property name="version" type="str">
0.3-2ubuntu1
</property>
</package>
<package id="1366" name="mtr-tiny">
<property name="description" type="str">
Full screen ncurses traceroute tool
</property>
<property name="version" type="str">
0.72-2ubuntu1
</property>
</package>
<package id="1367" name="myspell-en-gb">
<property name="description" type="str">
English_british dictionary for myspell
</property>
<property name="version" type="str">
1:2.4.0~m240-1ubuntu1
</property>
</package>
<package id="1368" name="myspell-en-us">
<property name="description" type="str">
English_american dictionary for myspell
</property>
<property name="version" type="str">
1:2.4.0~m240-1ubuntu1
</property>
</package>
<package id="1369" name="myspell-en-za">
<property name="description" type="str">
English_shouthafrican dictionary for myspell
</property>
<property name="version" type="str">
1:2.4.0~m240-1ubuntu1
</property>
</package>
<package id="1370" name="nano">
<property name="description" type="str">
free Pico clone with some new features
</property>
<property name="version" type="str">
2.0.7-1ubuntu1
</property>
</package>
<package id="1371" name="nautilus">
<property name="description" type="str">
file manager and graphical shell for GNOME
</property>
<property name="version" type="str">
1:2.22.3-0ubuntu2
</property>
</package>
<package id="1372" name="nautilus-cd-burner">
<property name="description" type="str">
CD Burning front-end for Nautilus
</property>
<property name="version" type="str">
2.22.1-0ubuntu1
</property>
</package>
<package id="1373" name="nautilus-data">
<property name="description" type="str">
data files for nautilus
</property>
<property name="version" type="str">
1:2.22.3-0ubuntu2
</property>
</package>
<package id="1374" name="nautilus-sendto">
<property name="description" type="str">
integrates Evolution and Pidgin into the Nautilus file manager
</property>
<property name="version" type="str">
0.13.2-0ubuntu1
</property>
</package>
<package id="1375" name="nautilus-share">
<property name="description" type="str">
Nautilus extension to share folder using Samba
</property>
<property name="version" type="str">
0.7.2-0ubuntu5
</property>
</package>
<package id="1376" name="ncurses-base">
<property name="description" type="str">
Descriptions of common terminal types
</property>
<property name="version" type="str">
5.6+20071124-1ubuntu2
</property>
</package>
<package id="1377" name="ncurses-bin">
<property name="description" type="str">
Terminal-related programs and man pages
</property>
<property name="version" type="str">
5.6+20071124-1ubuntu2
</property>
</package>
<package id="1378" name="net-tools">
<property name="description" type="str">
The NET-3 networking toolkit
</property>
<property name="version" type="str">
1.60-19ubuntu1
</property>
</package>
<package id="1379" name="netbase">
<property name="description" type="str">
Basic TCP/IP networking system
</property>
<property name="version" type="str">
4.30ubuntu1
</property>
</package>
<package id="1380" name="netcat">
<property name="description" type="str">
TCP/IP swiss army knife -- transitional package
</property>
<property name="version" type="str">
1.10-36
</property>
</package>
<package id="1381" name="netcat-traditional">
<property name="description" type="str">
TCP/IP swiss army knife
</property>
<property name="version" type="str">
1.10-36
</property>
</package>
<package id="1382" name="network-manager">
<property name="description" type="str">
network management framework daemon
</property>
<property name="version" type="str">
0.6.6-0ubuntu5
</property>
</package>
<package id="1383" name="network-manager-gnome">
<property name="description" type="str">
network management framework (GNOME frontend)
</property>
<property name="version" type="str">
0.6.6-0ubuntu3
</property>
</package>
<package id="1384" name="notification-daemon">
<property name="description" type="str">
a daemon that displays passive pop-up notifications
</property>
<property name="version" type="str">
0.3.7-1ubuntu11.2
</property>
</package>
<package id="1385" name="ntfs-3g">
<property name="description" type="str">
read-write NTFS driver for FUSE
</property>
<property name="version" type="str">
1:1.2216-1ubuntu2
</property>
</package>
<package id="1386" name="ntpdate">
<property name="description" type="str">
client for setting system time from NTP servers
</property>
<property name="version" type="str">
1:4.2.4p4+dfsg-3ubuntu2
</property>
</package>
<package id="1387" name="nvidia-kernel-common">
<property name="description" type="str">
NVIDIA binary kernel module common files
</property>
<property name="version" type="str">
20051028+1ubuntu8
</property>
</package>
<package id="1388" name="o3read">
<property name="description" type="str">
standalone converter for OpenOffice.org documents
</property>
<property name="version" type="str">
0.0.4-1
</property>
</package>
<package id="1389" name="obex-data-server">
<property name="description" type="str">
D-Bus service for OBEX client and server side functionality
</property>
<property name="version" type="str">
0.3.1-0ubuntu1
</property>
</package>
<package id="1390" name="onboard">
<property name="description" type="str">
Simple On-screen Keyboard
</property>
<property name="version" type="str">
0.91ubuntu2
</property>
</package>
<package id="1391" name="openoffice.org-base-core">
<property name="description" type="str">
OpenOffice.org office suite -- libdba
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1392" name="openoffice.org-calc">
<property name="description" type="str">
OpenOffice.org office suite - spreadsheet
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1393" name="openoffice.org-common">
<property name="description" type="str">
OpenOffice.org office suite architecture independent files
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1394" name="openoffice.org-core">
<property name="description" type="str">
OpenOffice.org office suite architecture dependent files
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1395" name="openoffice.org-draw">
<property name="description" type="str">
OpenOffice.org office suite - drawing
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1396" name="openoffice.org-gnome">
<property name="description" type="str">
GNOME Integration for OpenOffice.org (VFS, GConf)
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1397" name="openoffice.org-gtk">
<property name="description" type="str">
GTK+ Integration for OpenOffice.org (Widgets, Dialogs, Quickstarter)
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1398" name="openoffice.org-help-en-gb">
<property name="description" type="str">
English_british help for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1399" name="openoffice.org-help-en-us">
<property name="description" type="str">
English_american help for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1400" name="openoffice.org-hyphenation">
<property name="description" type="str">
Hyphenation patterns for OpenOffice.org
</property>
<property name="version" type="str">
0.3
</property>
</package>
<package id="1401" name="openoffice.org-hyphenation-en-us">
<property name="description" type="str">
US English hyphenation patterns for OpenOffice.org
</property>
<property name="version" type="str">
2.3.1-2ubuntu1
</property>
</package>
<package id="1402" name="openoffice.org-impress">
<property name="description" type="str">
OpenOffice.org office suite - presentation
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1403" name="openoffice.org-l10n-common">
<property name="description" type="str">
common files for OpenOffice.org language and help packages
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1404" name="openoffice.org-l10n-en-gb">
<property name="description" type="str">
English_british language package for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1405" name="openoffice.org-l10n-en-za">
<property name="description" type="str">
English_southafrican language package for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1406" name="openoffice.org-style-human">
<property name="description" type="str">
Human symbol style for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1407" name="openoffice.org-thesaurus-en-au">
<property name="description" type="str">
Australian English Thesaurus for OpenOffice.org
</property>
<property name="version" type="str">
2.1-3ubuntu1
</property>
</package>
<package id="1408" name="openoffice.org-thesaurus-en-us">
<property name="description" type="str">
English Thesaurus for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.0~m240-1ubuntu1
</property>
</package>
<package id="1409" name="openoffice.org-writer">
<property name="description" type="str">
OpenOffice.org office suite - word processor
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1410" name="openprinting-ppds">
<property name="description" type="str">
OpenPrinting printer support - PostScript PPD files
</property>
<property name="version" type="str">
20080211-0ubuntu1
</property>
</package>
<package id="1411" name="openssh-client">
<property name="description" type="str">
secure shell client, an rlogin/rsh/rcp replacement
</property>
<property name="version" type="str">
1:4.7p1-8ubuntu1.2
</property>
</package>
<package id="1412" name="openssl">
<property name="description" type="str">
Secure Socket Layer (SSL) binary and related cryptographic tools
</property>
<property name="version" type="str">
0.9.8g-4ubuntu3.3
</property>
</package>
<package id="1413" name="parted">
<property name="description" type="str">
The GNU Parted disk partition resizing program
</property>
<property name="version" type="str">
1.7.1-5.1ubuntu9.1
</property>
</package>
<package id="1414" name="passwd">
<property name="description" type="str">
change and administer password and group data
</property>
<property name="version" type="str">
1:4.0.18.2-1ubuntu2
</property>
</package>
<package id="1415" name="pciutils">
<property name="description" type="str">
Linux PCI Utilities
</property>
<property name="version" type="str">
1:2.2.4-1.1ubuntu4
</property>
</package>
<package id="1416" name="pcmciautils">
<property name="description" type="str">
PCMCIA utilities for Linux 2.6
</property>
<property name="version" type="str">
014-4ubuntu1
</property>
</package>
<package id="1417" name="perl">
<property name="description" type="str">
Larry Wall's Practical Extraction and Report Language
</property>
<property name="version" type="str">
5.8.8-12
</property>
</package>
<package id="1418" name="perl-base">
<property name="description" type="str">
The Pathologically Eclectic Rubbish Lister
</property>
<property name="version" type="str">
5.8.8-12
</property>
</package>
<package id="1419" name="perl-modules">
<property name="description" type="str">
Core Perl modules
</property>
<property name="version" type="str">
5.8.8-12
</property>
</package>
<package id="1420" name="pidgin">
<property name="description" type="str">
graphical multi-protocol instant messaging client for X
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1421" name="pidgin-data">
<property name="description" type="str">
multi-protocol instant messaging client - data files
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1422" name="pidgin-otr">
<property name="description" type="str">
Off-the-Record Messaging plugin for pidgin
</property>
<property name="version" type="str">
3.1.0-1
</property>
</package>
<package id="1423" name="pkg-config">
<property name="description" type="str">
manage compile and link flags for libraries
</property>
<property name="version" type="str">
0.22-1
</property>
</package>
<package id="1424" name="pm-utils">
<property name="description" type="str">
utilities and scripts for power management
</property>
<property name="version" type="str">
0.99.2-3ubuntu10
</property>
</package>
<package id="1425" name="pnm2ppa">
<property name="description" type="str">
PPM to PPA converter
</property>
<property name="version" type="str">
1.12-16
</property>
</package>
<package id="1426" name="policykit">
<property name="description" type="str">
framework for managing administrative policies and privileges
</property>
<property name="version" type="str">
0.7-2ubuntu7
</property>
</package>
<package id="1427" name="policykit-gnome">
<property name="description" type="str">
GNOME dialogs for PolicyKit
</property>
<property name="version" type="str">
0.7-2ubuntu1.1
</property>
</package>
<package id="1428" name="poppler-utils">
<property name="description" type="str">
PDF utilitites (based on libpoppler)
</property>
<property name="version" type="str">
0.6.4-1ubuntu2
</property>
</package>
<package id="1429" name="popularity-contest">
<property name="description" type="str">
Vote for your favourite packages automatically
</property>
<property name="version" type="str">
1.43ubuntu1
</property>
</package>
<package id="1430" name="powermanagement-interface">
<property name="description" type="str">
platform neutral powermanagement interface
</property>
<property name="version" type="str">
0.3.18
</property>
</package>
<package id="1431" name="powermgmt-base">
<property name="description" type="str">
Common utils and configs for power management
</property>
<property name="version" type="str">
1.29build1
</property>
</package>
<package id="1432" name="powernowd">
<property name="description" type="str">
control cpu speed and voltage using 2.6 kernel interface
</property>
<property name="version" type="str">
0.97-2ubuntu4
</property>
</package>
<package id="1433" name="ppp">
<property name="description" type="str">
Point-to-Point Protocol (PPP) daemon
</property>
<property name="version" type="str">
2.4.4rel-9ubuntu2
</property>
</package>
<package id="1434" name="pppconfig">
<property name="description" type="str">
A text menu based utility for configuring ppp
</property>
<property name="version" type="str">
2.3.17ubuntu1
</property>
</package>
<package id="1435" name="pppoeconf">
<property name="description" type="str">
configures PPPoE/ADSL connections
</property>
<property name="version" type="str">
1.17ubuntu1
</property>
</package>
<package id="1436" name="procps">
<property name="description" type="str">
/proc file system utilities
</property>
<property name="version" type="str">
1:3.2.7-5ubuntu2
</property>
</package>
<package id="1437" name="psmisc">
<property name="description" type="str">
Utilities that use the proc filesystem
</property>
<property name="version" type="str">
22.6-1
</property>
</package>
<package id="1438" name="pulseaudio">
<property name="description" type="str">
PulseAudio sound server
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1439" name="pulseaudio-esound-compat">
<property name="description" type="str">
PulseAudio ESD compatibility layer
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1440" name="pulseaudio-module-gconf">
<property name="description" type="str">
GConf module for PulseAudio sound server
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1441" name="pulseaudio-module-hal">
<property name="description" type="str">
HAL device detection module for PulseAudio sound server
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1442" name="pulseaudio-module-x11">
<property name="description" type="str">
X11 module for PulseAudio sound server
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1443" name="pulseaudio-utils">
<property name="description" type="str">
Command line tools for the PulseAudio sound server
</property>
<property name="version" type="str">
0.9.10-1ubuntu1
</property>
</package>
<package id="1444" name="pxljr">
<property name="description" type="str">
Driver for HP's Color LaserJet 35xx/36xx color laser printers
</property>
<property name="version" type="str">
1.1-0ubuntu1
</property>
</package>
<package id="1445" name="python">
<property name="description" type="str">
An interactive high-level object-oriented language (default version)
</property>
<property name="version" type="str">
2.5.2-0ubuntu1
</property>
</package>
<package id="1446" name="python-apport">
<property name="description" type="str">
apport crash report handling library
</property>
<property name="version" type="str">
0.108.2
</property>
</package>
<package id="1447" name="python-apt">
<property name="description" type="str">
Python interface to libapt-pkg
</property>
<property name="version" type="str">
0.7.4ubuntu7
</property>
</package>
<package id="1448" name="python-brlapi">
<property name="description" type="str">
Python bindings for BrlAPI
</property>
<property name="version" type="str">
3.9-6ubuntu1
</property>
</package>
<package id="1449" name="python-cairo">
<property name="description" type="str">
Python bindings for the Cairo vector graphics library
</property>
<property name="version" type="str">
1.4.0-2ubuntu2
</property>
</package>
<package id="1450" name="python-central">
<property name="description" type="str">
register and build utility for Python packages
</property>
<property name="version" type="str">
0.6.7ubuntu0.1
</property>
</package>
<package id="1451" name="python-cups">
<property name="description" type="str">
Python bindings for CUPS
</property>
<property name="version" type="str">
1.9.34-0ubuntu1
</property>
</package>
<package id="1452" name="python-dbus">
<property name="description" type="str">
simple interprocess messaging system (Python interface)
</property>
<property name="version" type="str">
0.82.4-1ubuntu1
</property>
</package>
<package id="1453" name="python-gconf">
<property name="description" type="str">
Python bindings for GConf2
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1454" name="python-gdata">
<property name="description" type="str">
Google Data Python client library
</property>
<property name="version" type="str">
1.0.9-1ubuntu1
</property>
</package>
<package id="1455" name="python-gdbm">
<property name="description" type="str">
GNU dbm database support for Python
</property>
<property name="version" type="str">
2.5.2-0ubuntu2
</property>
</package>
<package id="1456" name="python-glade2">
<property name="description" type="str">
GTK+ bindings: Glade support
</property>
<property name="version" type="str">
2.12.1-0ubuntu1
</property>
</package>
<package id="1457" name="python-gmenu">
<property name="description" type="str">
an implementation of the freedesktop menu specification for GNOME
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="1458" name="python-gnome2">
<property name="description" type="str">
Python bindings for the GNOME desktop environment
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1459" name="python-gnome2-desktop">
<property name="description" type="str">
Python bindings for the GNOME desktop environment
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1460" name="python-gnomecanvas">
<property name="description" type="str">
Python bindings for gnomecanvas (debug extension)
</property>
<property name="version" type="str">
2.22.0-0ubuntu1
</property>
</package>
<package id="1461" name="python-gnupginterface">
<property name="description" type="str">
Python interface to GnuPG (GPG)
</property>
<property name="version" type="str">
0.3.2-9ubuntu1
</property>
</package>
<package id="1462" name="python-gobject">
<property name="description" type="str">
Python bindings for the GObject library
</property>
<property name="version" type="str">
2.14.1-2ubuntu2
</property>
</package>
<package id="1463" name="python-gst0.10">
<property name="description" type="str">
generic media-playing framework (Python bindings)
</property>
<property name="version" type="str">
0.10.11-1
</property>
</package>
<package id="1464" name="python-gtk2">
<property name="description" type="str">
Python bindings for the GTK+ widget set
</property>
<property name="version" type="str">
2.12.1-0ubuntu1
</property>
</package>
<package id="1465" name="python-gtkhtml2">
<property name="description" type="str">
Python bindings for the GtkHTML2 library
</property>
<property name="version" type="str">
2.19.1-0ubuntu7
</property>
</package>
<package id="1466" name="python-gtksourceview2">
<property name="description" type="str">
Python bindings for the GtkSourceView widget
</property>
<property name="version" type="str">
2.2.0-0ubuntu2
</property>
</package>
<package id="1467" name="python-imaging">
<property name="description" type="str">
Python Imaging Library
</property>
<property name="version" type="str">
1.1.6-1ubuntu5
</property>
</package>
<package id="1468" name="python-launchpad-bugs">
<property name="description" type="str">
simple Python Interface to Bugs in Launchpad
</property>
<property name="version" type="str">
0.2.30.1
</property>
</package>
<package id="1469" name="python-launchpad-integration">
<property name="description" type="str">
library for launchpad integration
</property>
<property name="version" type="str">
0.1.19
</property>
</package>
<package id="1470" name="python-libxml2">
<property name="description" type="str">
Python bindings for the GNOME XML library
</property>
<property name="version" type="str">
2.6.31.dfsg-2ubuntu1
</property>
</package>
<package id="1471" name="python-minimal">
<property name="description" type="str">
A minimal subset of the Python language (default version)
</property>
<property name="version" type="str">
2.5.2-0ubuntu1
</property>
</package>
<package id="1472" name="python-notify">
<property name="description" type="str">
Python bindings for libnotify
</property>
<property name="version" type="str">
0.1.1-2
</property>
</package>
<package id="1473" name="python-numeric">
<property name="description" type="str">
Numerical (matrix-oriented) Mathematics for Python
</property>
<property name="version" type="str">
24.2-8ubuntu2
</property>
</package>
<package id="1474" name="python-problem-report">
<property name="description" type="str">
Python library to handle problem reports
</property>
<property name="version" type="str">
0.108.2
</property>
</package>
<package id="1475" name="python-pyatspi">
<property name="description" type="str">
Assistive Technology Service Provider Interface - Python bindings
</property>
<property name="version" type="str">
1.22.1-0ubuntu1
</property>
</package>
<package id="1476" name="python-pyorbit">
<property name="description" type="str">
A Python language binding for the ORBit2 CORBA implementation
</property>
<property name="version" type="str">
2.14.3-2ubuntu1
</property>
</package>
<package id="1477" name="python-sexy">
<property name="description" type="str">
python language bindings for libsexy
</property>
<property name="version" type="str">
0.1.9-1ubuntu1
</property>
</package>
<package id="1478" name="python-software-properties">
<property name="description" type="str">
manage the repositories that you install software from
</property>
<property name="version" type="str">
0.63ubuntu1
</property>
</package>
<package id="1479" name="python-support">
<property name="description" type="str">
automated rebuilding support for python modules
</property>
<property name="version" type="str">
0.7.5ubuntu1
</property>
</package>
<package id="1480" name="python-uno">
<property name="description" type="str">
Python interface for OpenOffice.org
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1481" name="python-virtkey">
<property name="description" type="str">
Library to emulate keyboard keypresses.
</property>
<property name="version" type="str">
0.50ubuntu0.1
</property>
</package>
<package id="1482" name="python-vte">
<property name="description" type="str">
Python bindings for the VTE widget set
</property>
<property name="version" type="str">
1:0.16.13-1ubuntu1
</property>
</package>
<package id="1483" name="python-xdg">
<property name="description" type="str">
A python library to access freedesktop.org standards
</property>
<property name="version" type="str">
0.15-1.1ubuntu3
</property>
</package>
<package id="1484" name="python2.5">
<property name="description" type="str">
An interactive high-level object-oriented language (version 2.5)
</property>
<property name="version" type="str">
2.5.2-2ubuntu4
</property>
</package>
<package id="1485" name="python2.5-minimal">
<property name="description" type="str">
A minimal subset of the Python language (version 2.5)
</property>
<property name="version" type="str">
2.5.2-2ubuntu4
</property>
</package>
<package id="1486" name="radeontool">
<property name="description" type="str">
utility to control ATI Radeon backlight functions on laptops
</property>
<property name="version" type="str">
1.5-5build1
</property>
</package>
<package id="1487" name="rdesktop">
<property name="description" type="str">
RDP client for Windows NT/2000 Terminal Server
</property>
<property name="version" type="str">
1.5.0-3+cvs20071006
</property>
</package>
<package id="1488" name="readahead">
<property name="description" type="str">
read files into the page cache
</property>
<property name="version" type="str">
1:0.20050517.0220-0ubuntu14
</property>
</package>
<package id="1489" name="readline-common">
<property name="description" type="str">
GNU readline and history libraries, common files
</property>
<property name="version" type="str">
5.2-3build1
</property>
</package>
<package id="1490" name="reiserfsprogs">
<property name="description" type="str">
User-level tools for ReiserFS filesystems
</property>
<property name="version" type="str">
1:3.6.19-6
</property>
</package>
<package id="1491" name="rhythmbox">
<property name="description" type="str">
music player and organizer for GNOME
</property>
<property name="version" type="str">
0.11.5-0ubuntu8
</property>
</package>
<package id="1492" name="rss-glx">
<property name="description" type="str">
Really Slick Screensavers GLX Port
</property>
<property name="version" type="str">
0.8.1-8ubuntu4
</property>
</package>
<package id="1493" name="rsync">
<property name="description" type="str">
fast remote file copy program (like rcp)
</property>
<property name="version" type="str">
2.6.9-6ubuntu2
</property>
</package>
<package id="1494" name="samba-common">
<property name="description" type="str">
Samba common files used by both the server and the client
</property>
<property name="version" type="str">
3.0.28a-1ubuntu4.4
</property>
</package>
<package id="1495" name="scim">
<property name="description" type="str">
smart common input method platform
</property>
<property name="version" type="str">
1.4.7-3ubuntu8
</property>
</package>
<package id="1496" name="scim-bridge-agent">
<property name="description" type="str">
IME server of scim-bridge communicate with SCIM
</property>
<property name="version" type="str">
0.4.14-1ubuntu2
</property>
</package>
<package id="1497" name="scim-bridge-client-gtk">
<property name="description" type="str">
IME server of scim-bridge communicate with SCIM
</property>
<property name="version" type="str">
0.4.14-1ubuntu2
</property>
</package>
<package id="1498" name="scim-gtk2-immodule">
<property name="description" type="str">
GTK+2 input method module with SCIM as backend
</property>
<property name="version" type="str">
1.4.7-3ubuntu8
</property>
</package>
<package id="1499" name="scim-modules-socket">
<property name="description" type="str">
socket modules for SCIM platform
</property>
<property name="version" type="str">
1.4.7-3ubuntu8
</property>
</package>
<package id="1500" name="screen">
<property name="description" type="str">
terminal multiplexor with VT100/ANSI terminal emulation
</property>
<property name="version" type="str">
4.0.3-7ubuntu1
</property>
</package>
<package id="1501" name="screensaver-default-images">
<property name="description" type="str">
Wallpapers for image processing screensavers
</property>
<property name="version" type="str">
0.2-1
</property>
</package>
<package id="1502" name="scrollkeeper">
<property name="description" type="str">
A free electronic cataloging system for documentation
</property>
<property name="version" type="str">
0.3.14-15ubuntu1
</property>
</package>
<package id="1503" name="seahorse">
<property name="description" type="str">
A Gnome front end for GnuPG
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="1504" name="sed">
<property name="description" type="str">
The GNU sed stream editor
</property>
<property name="version" type="str">
4.1.5-5
</property>
</package>
<package id="1505" name="sgml-base">
<property name="description" type="str">
SGML infrastructure and SGML catalog file support
</property>
<property name="version" type="str">
1.26
</property>
</package>
<package id="1506" name="sgml-data">
<property name="description" type="str">
common SGML and XML data
</property>
<property name="version" type="str">
2.0.3
</property>
</package>
<package id="1507" name="shared-mime-info">
<property name="description" type="str">
FreeDesktop.org shared MIME database and spec
</property>
<property name="version" type="str">
0.23-5
</property>
</package>
<package id="1508" name="smartdimmer">
<property name="description" type="str">
Change LCD brightness on Geforce 6200Go cards
</property>
<property name="version" type="str">
0.1-2build1
</property>
</package>
<package id="1509" name="smbclient">
<property name="description" type="str">
a LanManager-like simple client for Unix
</property>
<property name="version" type="str">
3.0.28a-1ubuntu4.4
</property>
</package>
<package id="1510" name="software-properties-gtk">
<property name="description" type="str">
manage the repositories that you install software from
</property>
<property name="version" type="str">
0.63ubuntu1
</property>
</package>
<package id="1511" name="sound-juicer">
<property name="description" type="str">
GNOME 2 CD Ripper
</property>
<property name="version" type="str">
2.22.0-1ubuntu2
</property>
</package>
<package id="1512" name="splix">
<property name="description" type="str">
Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
</property>
<property name="version" type="str">
1.1.1-0ubuntu1
</property>
</package>
<package id="1513" name="sqlite">
<property name="description" type="str">
command line interface for SQLite
</property>
<property name="version" type="str">
2.8.17-4build1
</property>
</package>
<package id="1514" name="sqlite3">
<property name="description" type="str">
A command line interface for SQLite 3
</property>
<property name="version" type="str">
3.4.2-2
</property>
</package>
<package id="1515" name="ssh-askpass-gnome">
<property name="description" type="str">
interactive X program to prompt users for a passphrase for ssh-add
</property>
<property name="version" type="str">
1:4.7p1-8ubuntu1.2
</property>
</package>
<package id="1516" name="ssl-cert">
<property name="description" type="str">
Simple debconf wrapper for openssl
</property>
<property name="version" type="str">
1.0.14-0ubuntu2
</property>
</package>
<package id="1517" name="startup-tasks">
<property name="description" type="str">
definitions of essential tasks to run on startup
</property>
<property name="version" type="str">
0.3.9-2
</property>
</package>
<package id="1518" name="strace">
<property name="description" type="str">
A system call tracer
</property>
<property name="version" type="str">
4.5.15-1.1ubuntu1
</property>
</package>
<package id="1519" name="sudo">
<property name="description" type="str">
Provide limited super user privileges to specific users
</property>
<property name="version" type="str">
1.6.9p10-1ubuntu3.2
</property>
</package>
<package id="1520" name="synaptic">
<property name="description" type="str">
Graphical package manager
</property>
<property name="version" type="str">
0.61ubuntu9
</property>
</package>
<package id="1521" name="sysklogd">
<property name="description" type="str">
System Logging Daemon
</property>
<property name="version" type="str">
1.5-1ubuntu1
</property>
</package>
<package id="1522" name="system-config-printer-common">
<property name="description" type="str">
Printer configuration GUI
</property>
<property name="version" type="str">
0.7.81+svn1976-0ubuntu9
</property>
</package>
<package id="1523" name="system-config-printer-gnome">
<property name="description" type="str">
Printer configuration GUI
</property>
<property name="version" type="str">
0.7.81+svn1976-0ubuntu9
</property>
</package>
<package id="1524" name="system-services">
<property name="description" type="str">
definitions of essential system services
</property>
<property name="version" type="str">
0.3.9-2
</property>
</package>
<package id="1525" name="system-tools-backends">
<property name="description" type="str">
System Tools to manage computer configuration -- scripts
</property>
<property name="version" type="str">
2.6.0-0ubuntu7
</property>
</package>
<package id="1526" name="sysv-rc">
<property name="description" type="str">
System-V-like runlevel change mechanism
</property>
<property name="version" type="str">
2.86.ds1-14.1ubuntu45
</property>
</package>
<package id="1527" name="sysvutils">
<property name="description" type="str">
System-V-like utilities
</property>
<property name="version" type="str">
2.86.ds1-14.1ubuntu45
</property>
</package>
<package id="1528" name="tangerine-icon-theme">
<property name="description" type="str">
Tangerine Icon theme
</property>
<property name="version" type="str">
0.26
</property>
</package>
<package id="1529" name="tar">
<property name="description" type="str">
GNU version of the tar archiving utility
</property>
<property name="version" type="str">
1.19-3
</property>
</package>
<package id="1530" name="tasksel">
<property name="description" type="str">
Tool for selecting tasks for installation on Debian systems
</property>
<property name="version" type="str">
2.70ubuntu5
</property>
</package>
<package id="1531" name="tasksel-data">
<property name="description" type="str">
Official tasks used for installation of Debian systems
</property>
<property name="version" type="str">
2.70ubuntu5
</property>
</package>
<package id="1532" name="tcpd">
<property name="description" type="str">
Wietse Venema's TCP wrapper utilities
</property>
<property name="version" type="str">
7.6.dbs-14
</property>
</package>
<package id="1533" name="tcpdump">
<property name="description" type="str">
A powerful tool for network monitoring and data acquisition
</property>
<property name="version" type="str">
3.9.8-2
</property>
</package>
<package id="1534" name="telnet">
<property name="description" type="str">
The telnet client
</property>
<property name="version" type="str">
0.17-35ubuntu1
</property>
</package>
<package id="1535" name="thunderbird-locale-en-gb">
<property name="description" type="str">
Thunderbird English language/region package
</property>
<property name="version" type="str">
1:2.0.0.0+1-0ubuntu1
</property>
</package>
<package id="1536" name="time">
<property name="description" type="str">
The GNU time program for measuring cpu resource usage
</property>
<property name="version" type="str">
1.7-21build1
</property>
</package>
<package id="1537" name="tomboy">
<property name="description" type="str">
desktop note taking program using Wiki style links
</property>
<property name="version" type="str">
0.10.2-0ubuntu1
</property>
</package>
<package id="1538" name="toshset">
<property name="description" type="str">
Access much of the Toshiba laptop hardware interface
</property>
<property name="version" type="str">
1.72-6ubuntu1
</property>
</package>
<package id="1539" name="totem">
<property name="description" type="str">
A simple media player for the Gnome desktop (dummy package)
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="1540" name="totem-common">
<property name="description" type="str">
Data files for the Totem media player
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="1541" name="totem-gstreamer">
<property name="description" type="str">
A simple media player for the Gnome desktop based on gstreamer
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="1542" name="totem-mozilla">
<property name="description" type="str">
Totem Mozilla plugin
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="1543" name="totem-plugins">
<property name="description" type="str">
Plugins for the Totem media player
</property>
<property name="version" type="str">
2.22.1-0ubuntu2
</property>
</package>
<package id="1544" name="tracker">
<property name="description" type="str">
metadata database, indexer and search tool
</property>
<property name="version" type="str">
0.6.6-0ubuntu3.8.04.1
</property>
</package>
<package id="1545" name="tracker-search-tool">
<property name="description" type="str">
metadata database, indexer and search tool - GNOME frontend
</property>
<property name="version" type="str">
0.6.6-0ubuntu3.8.04.1
</property>
</package>
<package id="1546" name="transmission-common">
<property name="description" type="str">
free, lightweight BitTorrent client
</property>
<property name="version" type="str">
1.06-0ubuntu6
</property>
</package>
<package id="1547" name="transmission-gtk">
<property name="description" type="str">
free, lightweight BitTorrent client (graphical interface)
</property>
<property name="version" type="str">
1.06-0ubuntu6
</property>
</package>
<package id="1548" name="tsclient">
<property name="description" type="str">
front-end for viewing of remote desktops in GNOME
</property>
<property name="version" type="str">
0.150-1ubuntu1
</property>
</package>
<package id="1549" name="ttf-arabeyes">
<property name="description" type="str">
Arabeyes GPL TrueType Arabic fonts
</property>
<property name="version" type="str">
2.0-1ubuntu1
</property>
</package>
<package id="1550" name="ttf-arphic-uming">
<property name="description" type="str">
&quot;AR PL UMing&quot; Chinese Unicode TrueType font collection Mingti style
</property>
<property name="version" type="str">
0.2.20080216.1-0ubuntu1
</property>
</package>
<package id="1551" name="ttf-bitstream-vera">
<property name="description" type="str">
The Bitstream Vera family of free TrueType fonts
</property>
<property name="version" type="str">
1.10-7
</property>
</package>
<package id="1552" name="ttf-dejavu-core">
<property name="description" type="str">
Vera font family derivate with additional characters
</property>
<property name="version" type="str">
2.23-1
</property>
</package>
<package id="1553" name="ttf-freefont">
<property name="description" type="str">
Freefont Serif, Sans and Mono Truetype fonts
</property>
<property name="version" type="str">
20060501cvs-12
</property>
</package>
<package id="1554" name="ttf-indic-fonts-core">
<property name="description" type="str">
Core collection of free Indian language fonts
</property>
<property name="version" type="str">
1:0.5.0-0ubuntu1
</property>
</package>
<package id="1555" name="ttf-kochi-gothic">
<property name="description" type="str">
Kochi Subst Gothic Japanese TrueType font without naga10
</property>
<property name="version" type="str">
1.0.20030809-4ubuntu2
</property>
</package>
<package id="1556" name="ttf-kochi-mincho">
<property name="description" type="str">
Kochi Subst Mincho Japanese TrueType font without naga10
</property>
<property name="version" type="str">
1.0.20030809-4ubuntu2
</property>
</package>
<package id="1557" name="ttf-lao">
<property name="description" type="str">
TrueType font for Lao language
</property>
<property name="version" type="str">
0.0.20060226-2
</property>
</package>
<package id="1558" name="ttf-malayalam-fonts">
<property name="description" type="str">
Free TrueType fonts for the Malayalam language
</property>
<property name="version" type="str">
1:0.5.0-0ubuntu1
</property>
</package>
<package id="1559" name="ttf-opensymbol">
<property name="description" type="str">
The OpenSymbol TrueType font
</property>
<property name="version" type="str">
1:2.4.1-1ubuntu2
</property>
</package>
<package id="1560" name="ttf-thai-tlwg">
<property name="description" type="str">
Thai fonts in TrueType format
</property>
<property name="version" type="str">
1:0.4.8-1
</property>
</package>
<package id="1561" name="ttf-unfonts-core">
<property name="description" type="str">
Un series Korean TrueType fonts
</property>
<property name="version" type="str">
1.0.1-6ubuntu1
</property>
</package>
<package id="1562" name="tzdata">
<property name="description" type="str">
time zone and daylight-saving time data
</property>
<property name="version" type="str">
2008c-1ubuntu0.8.04
</property>
</package>
<package id="1563" name="ubufox">
<property name="description" type="str">
Ubuntu Firefox specific configuration defaults and apt support
</property>
<property name="version" type="str">
0.5-0ubuntu1
</property>
</package>
<package id="1564" name="ubuntu-artwork">
<property name="description" type="str">
Ubuntu themes and artwork
</property>
<property name="version" type="str">
41
</property>
</package>
<package id="1565" name="ubuntu-desktop">
<property name="description" type="str">
The Ubuntu desktop system
</property>
<property name="version" type="str">
1.102
</property>
</package>
<package id="1566" name="ubuntu-docs">
<property name="description" type="str">
The Ubuntu Documentation Project
</property>
<property name="version" type="str">
8.04.2~hardy
</property>
</package>
<package id="1567" name="ubuntu-gdm-themes">
<property name="description" type="str">
Ubuntu GDM themes
</property>
<property name="version" type="str">
0.29
</property>
</package>
<package id="1568" name="ubuntu-keyring">
<property name="description" type="str">
GnuPG keys of the Ubuntu archive
</property>
<property name="version" type="str">
2008.03.04
</property>
</package>
<package id="1569" name="ubuntu-minimal">
<property name="description" type="str">
Minimal core of Ubuntu
</property>
<property name="version" type="str">
1.102
</property>
</package>
<package id="1570" name="ubuntu-sounds">
<property name="description" type="str">
Ubuntu's GNOME audio theme
</property>
<property name="version" type="str">
0.6
</property>
</package>
<package id="1571" name="ubuntu-standard">
<property name="description" type="str">
The Ubuntu standard system
</property>
<property name="version" type="str">
1.102
</property>
</package>
<package id="1572" name="ubuntu-wallpapers">
<property name="description" type="str">
Ubuntu Wallpapers
</property>
<property name="version" type="str">
0.25
</property>
</package>
<package id="1573" name="ucf">
<property name="description" type="str">
Update Configuration File: preserve user changes to config files.
</property>
<property name="version" type="str">
3.005
</property>
</package>
<package id="1574" name="udev">
<property name="description" type="str">
rule-based device node and kernel event manager
</property>
<property name="version" type="str">
117-8
</property>
</package>
<package id="1575" name="ufw">
<property name="description" type="str">
program for managing a netfilter firewall
</property>
<property name="version" type="str">
0.16.2.1
</property>
</package>
<package id="1576" name="unattended-upgrades">
<property name="description" type="str">
Install security upgrades automatically
</property>
<property name="version" type="str">
0.30ubuntu1
</property>
</package>
<package id="1577" name="unzip">
<property name="description" type="str">
De-archiver for .zip files
</property>
<property name="version" type="str">
5.52-10ubuntu2
</property>
</package>
<package id="1578" name="update-inetd">
<property name="description" type="str">
inetd.conf updater
</property>
<property name="version" type="str">
4.27-0.6
</property>
</package>
<package id="1579" name="update-manager">
<property name="description" type="str">
GNOME application that manages apt updates
</property>
<property name="version" type="str">
1:0.87.27
</property>
</package>
<package id="1580" name="update-manager-core">
<property name="description" type="str">
manage release upgrades
</property>
<property name="version" type="str">
1:0.87.27
</property>
</package>
<package id="1581" name="update-notifier">
<property name="description" type="str">
Daemon which notifies about package updates
</property>
<property name="version" type="str">
0.70.7
</property>
</package>
<package id="1582" name="update-notifier-common">
<property name="description" type="str">
Files shared between update-notifier and adept
</property>
<property name="version" type="str">
0.70.7
</property>
</package>
<package id="1583" name="upstart">
<property name="description" type="str">
event-based init daemon
</property>
<property name="version" type="str">
0.3.9-2
</property>
</package>
<package id="1584" name="upstart-compat-sysv">
<property name="description" type="str">
compatibility for System-V-like init
</property>
<property name="version" type="str">
0.3.9-2
</property>
</package>
<package id="1585" name="upstart-logd">
<property name="description" type="str">
boot logging daemon
</property>
<property name="version" type="str">
0.3.9-2
</property>
</package>
<package id="1586" name="usbutils">
<property name="description" type="str">
Linux USB utilities
</property>
<property name="version" type="str">
0.73-5ubuntu2
</property>
</package>
<package id="1587" name="usplash">
<property name="description" type="str">
Userspace bootsplash utility
</property>
<property name="version" type="str">
0.5.19
</property>
</package>
<package id="1588" name="usplash-theme-ubuntu">
<property name="description" type="str">
Usplash theme for Ubuntu
</property>
<property name="version" type="str">
0.18
</property>
</package>
<package id="1589" name="util-linux">
<property name="description" type="str">
Miscellaneous system utilities
</property>
<property name="version" type="str">
2.13.1-5ubuntu2
</property>
</package>
<package id="1590" name="util-linux-locales">
<property name="description" type="str">
Locales files for util-linux
</property>
<property name="version" type="str">
2.13.1-5ubuntu2
</property>
</package>
<package id="1591" name="uuid-runtime">
<property name="description" type="str">
universally unique id library
</property>
<property name="version" type="str">
1.40.8-2ubuntu2
</property>
</package>
<package id="1592" name="vbetool">
<property name="description" type="str">
run real-mode video BIOS code to alter hardware state
</property>
<property name="version" type="str">
1.0-1.1
</property>
</package>
<package id="1593" name="vim-common">
<property name="description" type="str">
Vi IMproved - Common files
</property>
<property name="version" type="str">
1:7.1-138+1ubuntu3
</property>
</package>
<package id="1594" name="vim-tiny">
<property name="description" type="str">
Vi IMproved - enhanced vi editor - compact version
</property>
<property name="version" type="str">
1:7.1-138+1ubuntu3
</property>
</package>
<package id="1595" name="vinagre">
<property name="description" type="str">
VNC client for the GNOME Desktop
</property>
<property name="version" type="str">
0.5.1-0ubuntu1
</property>
</package>
<package id="1596" name="vino">
<property name="description" type="str">
VNC server for GNOME
</property>
<property name="version" type="str">
2.22.2-0ubuntu1
</property>
</package>
<package id="1597" name="w3m">
<property name="description" type="str">
WWW browsable pager with excellent tables/frames support
</property>
<property name="version" type="str">
0.5.1-5.1ubuntu1
</property>
</package>
<package id="1598" name="wamerican">
<property name="description" type="str">
American English dictionary words for /usr/share/dict
</property>
<property name="version" type="str">
6-2.1
</property>
</package>
<package id="1599" name="wbritish">
<property name="description" type="str">
British English dictionary words for /usr/share/dict
</property>
<property name="version" type="str">
6-2.1
</property>
</package>
<package id="1600" name="wget">
<property name="description" type="str">
retrieves files from the web
</property>
<property name="version" type="str">
1.10.2-3ubuntu1
</property>
</package>
<package id="1601" name="whiptail">
<property name="description" type="str">
Displays user-friendly dialog boxes from shell scripts
</property>
<property name="version" type="str">
0.52.2-11.2ubuntu1
</property>
</package>
<package id="1602" name="whois">
<property name="description" type="str">
the GNU whois client
</property>
<property name="version" type="str">
4.7.24
</property>
</package>
<package id="1603" name="wireless-tools">
<property name="description" type="str">
Tools for manipulating Linux Wireless Extensions
</property>
<property name="version" type="str">
29-1ubuntu2
</property>
</package>
<package id="1604" name="wodim">
<property name="description" type="str">
command line CD/DVD writing tool
</property>
<property name="version" type="str">
9:1.1.6-1ubuntu6
</property>
</package>
<package id="1605" name="wpasupplicant">
<property name="description" type="str">
Client support for WPA and WPA2 (IEEE 802.11i)
</property>
<property name="version" type="str">
0.6.0+0.5.8-0ubuntu2
</property>
</package>
<package id="1606" name="wvdial">
<property name="description" type="str">
PPP dialer with built-in intelligence
</property>
<property name="version" type="str">
1.60.1
</property>
</package>
<package id="1607" name="x-ttcidfont-conf">
<property name="description" type="str">
TrueType and CID fonts configuration for X
</property>
<property name="version" type="str">
27
</property>
</package>
<package id="1608" name="x11-apps">
<property name="description" type="str">
X applications
</property>
<property name="version" type="str">
7.3+1
</property>
</package>
<package id="1609" name="x11-common">
<property name="description" type="str">
X Window System (X.Org) infrastructure
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1610" name="x11-session-utils">
<property name="description" type="str">
X session utilities
</property>
<property name="version" type="str">
7.3+1
</property>
</package>
<package id="1611" name="x11-utils">
<property name="description" type="str">
X11 utilities
</property>
<property name="version" type="str">
7.3+1
</property>
</package>
<package id="1612" name="x11-xfs-utils">
<property name="description" type="str">
X font server utilities
</property>
<property name="version" type="str">
7.3+1
</property>
</package>
<package id="1613" name="x11-xkb-utils">
<property name="description" type="str">
X11 XKB utilities
</property>
<property name="version" type="str">
7.3+1
</property>
</package>
<package id="1614" name="x11-xserver-utils">
<property name="description" type="str">
X server utilities
</property>
<property name="version" type="str">
7.3+2
</property>
</package>
<package id="1615" name="xauth">
<property name="description" type="str">
X authentication utility
</property>
<property name="version" type="str">
1:1.0.2-2
</property>
</package>
<package id="1616" name="xbase-clients">
<property name="description" type="str">
miscellaneous X clients - metapackage
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1617" name="xbitmaps">
<property name="description" type="str">
Base X bitmaps
</property>
<property name="version" type="str">
1.0.1-2ubuntu1
</property>
</package>
<package id="1618" name="xcursor-themes">
<property name="description" type="str">
Base X cursor themes
</property>
<property name="version" type="str">
1.0.1-5ubuntu1
</property>
</package>
<package id="1619" name="xdg-user-dirs">
<property name="description" type="str">
tool to manage well known user directories
</property>
<property name="version" type="str">
0.10-1ubuntu1
</property>
</package>
<package id="1620" name="xdg-user-dirs-gtk">
<property name="description" type="str">
tool to manage well known user directories (Gtk extension)
</property>
<property name="version" type="str">
0.7-1
</property>
</package>
<package id="1621" name="xdg-utils">
<property name="description" type="str">
desktop integration utilities from freedesktop.org
</property>
<property name="version" type="str">
1.0.2-2
</property>
</package>
<package id="1622" name="xfonts-100dpi">
<property name="description" type="str">
100 dpi fonts for X
</property>
<property name="version" type="str">
1:1.0.0-4
</property>
</package>
<package id="1623" name="xfonts-75dpi">
<property name="description" type="str">
75 dpi fonts for X
</property>
<property name="version" type="str">
1:1.0.0-4
</property>
</package>
<package id="1624" name="xfonts-base">
<property name="description" type="str">
standard fonts for X
</property>
<property name="version" type="str">
1:1.0.0-5
</property>
</package>
<package id="1625" name="xfonts-encodings">
<property name="description" type="str">
Encodings for X.Org fonts
</property>
<property name="version" type="str">
1:1.0.2-3
</property>
</package>
<package id="1626" name="xfonts-scalable">
<property name="description" type="str">
scalable fonts for X
</property>
<property name="version" type="str">
1:1.0.0-6
</property>
</package>
<package id="1627" name="xfonts-utils">
<property name="description" type="str">
X Window System font utility programs
</property>
<property name="version" type="str">
1:1.0.1-2ubuntu1
</property>
</package>
<package id="1628" name="xinit">
<property name="description" type="str">
X server initialisation tool
</property>
<property name="version" type="str">
1.0.7-2
</property>
</package>
<package id="1629" name="xkb-data">
<property name="description" type="str">
X Keyboard Extension (XKB) configuration data
</property>
<property name="version" type="str">
1.1~cvs.20080104.1-1ubuntu6
</property>
</package>
<package id="1630" name="xml-core">
<property name="description" type="str">
XML infrastructure and XML catalog file support
</property>
<property name="version" type="str">
0.11
</property>
</package>
<package id="1631" name="xorg">
<property name="description" type="str">
X.Org X Window System
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1632" name="xsane">
<property name="description" type="str">
featureful graphical frontend for SANE (Scanner Access Now Easy)
</property>
<property name="version" type="str">
0.995-1ubuntu1
</property>
</package>
<package id="1633" name="xsane-common">
<property name="description" type="str">
featureful graphical frontend for SANE (Scanner Access Now Easy)
</property>
<property name="version" type="str">
0.995-1ubuntu1
</property>
</package>
<package id="1634" name="xscreensaver-data">
<property name="description" type="str">
data files to be shared among screensaver frontends
</property>
<property name="version" type="str">
5.04-4ubuntu1
</property>
</package>
<package id="1635" name="xscreensaver-gl">
<property name="description" type="str">
GL(Mesa) screen hacks for xscreensaver
</property>
<property name="version" type="str">
5.04-4ubuntu1
</property>
</package>
<package id="1636" name="xserver-xorg">
<property name="description" type="str">
the X.Org X server
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1637" name="xserver-xorg-core">
<property name="description" type="str">
Xorg X server - core server
</property>
<property name="version" type="str">
2:1.4.1~git20080131-1ubuntu9.2
</property>
</package>
<package id="1638" name="xserver-xorg-input-all">
<property name="description" type="str">
the X.Org X server -- input driver metapackage
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1639" name="xserver-xorg-input-evdev">
<property name="description" type="str">
X.Org X server -- evdev input driver
</property>
<property name="version" type="str">
1:1.2.0-1ubuntu2
</property>
</package>
<package id="1640" name="xserver-xorg-input-kbd">
<property name="description" type="str">
X.Org X server -- keyboard input driver
</property>
<property name="version" type="str">
1:1.2.2-3ubuntu1
</property>
</package>
<package id="1641" name="xserver-xorg-input-mouse">
<property name="description" type="str">
X.Org X server -- mouse input driver
</property>
<property name="version" type="str">
1:1.2.3-2
</property>
</package>
<package id="1642" name="xserver-xorg-input-synaptics">
<property name="description" type="str">
Synaptics TouchPad driver for X.Org server
</property>
<property name="version" type="str">
0.14.7~git20070706-1ubuntu4
</property>
</package>
<package id="1643" name="xserver-xorg-input-vmmouse">
<property name="description" type="str">
X.Org X server -- VMMouse input driver to use with VMWare
</property>
<property name="version" type="str">
1:12.4.3-1ubuntu1
</property>
</package>
<package id="1644" name="xserver-xorg-input-wacom">
<property name="description" type="str">
X.Org X server -- Wacom input driver
</property>
<property name="version" type="str">
1:0.7.9.8-0ubuntu3
</property>
</package>
<package id="1645" name="xserver-xorg-video-all">
<property name="description" type="str">
the X.Org X server -- output driver metapackage
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1646" name="xserver-xorg-video-amd">
<property name="description" type="str">
Geode GX2/LX display driver (dummy transitional package)
</property>
<property name="version" type="str">
2.9.0-1ubuntu2.4
</property>
</package>
<package id="1647" name="xserver-xorg-video-apm">
<property name="description" type="str">
X.Org X server -- APM display driver
</property>
<property name="version" type="str">
1:1.1.1-10
</property>
</package>
<package id="1648" name="xserver-xorg-video-ark">
<property name="description" type="str">
X.Org X server -- ark display driver
</property>
<property name="version" type="str">
1:0.6.0-9
</property>
</package>
<package id="1649" name="xserver-xorg-video-ati">
<property name="description" type="str">
X.Org X server -- ATI display driver
</property>
<property name="version" type="str">
1:6.8.0-1
</property>
</package>
<package id="1650" name="xserver-xorg-video-chips">
<property name="description" type="str">
X.Org X server -- Chips display driver
</property>
<property name="version" type="str">
1:1.1.1-9
</property>
</package>
<package id="1651" name="xserver-xorg-video-cirrus">
<property name="description" type="str">
X.Org X server -- Cirrus display driver
</property>
<property name="version" type="str">
1:1.1.0-8ubuntu1
</property>
</package>
<package id="1652" name="xserver-xorg-video-cyrix">
<property name="description" type="str">
X.Org X server -- Cyrix display driver
</property>
<property name="version" type="str">
1:1.1.0-8
</property>
</package>
<package id="1653" name="xserver-xorg-video-dummy">
<property name="description" type="str">
X.Org X server -- dummy display driver
</property>
<property name="version" type="str">
1:0.2.0-7
</property>
</package>
<package id="1654" name="xserver-xorg-video-fbdev">
<property name="description" type="str">
X.Org X server -- fbdev display driver
</property>
<property name="version" type="str">
1:0.3.1-4
</property>
</package>
<package id="1655" name="xserver-xorg-video-geode">
<property name="description" type="str">
X.Org server -- Geode GX2/LX display driver
</property>
<property name="version" type="str">
2.9.0-1ubuntu2.4
</property>
</package>
<package id="1656" name="xserver-xorg-video-glint">
<property name="description" type="str">
X.Org X server -- Glint display driver
</property>
<property name="version" type="str">
1:1.1.1-8
</property>
</package>
<package id="1657" name="xserver-xorg-video-i128">
<property name="description" type="str">
X.Org X server -- i128 display driver
</property>
<property name="version" type="str">
1:1.2.1-4
</property>
</package>
<package id="1658" name="xserver-xorg-video-i740">
<property name="description" type="str">
X.Org X server -- i740 display driver
</property>
<property name="version" type="str">
1:1.1.0-7
</property>
</package>
<package id="1659" name="xserver-xorg-video-i810">
<property name="description" type="str">
X.Org X server -- Intel i8xx, i9xx display driver
</property>
<property name="version" type="str">
2:1.7.4-0ubuntu7
</property>
</package>
<package id="1660" name="xserver-xorg-video-imstt">
<property name="description" type="str">
X.Org X server -- IMSTT display driver
</property>
<property name="version" type="str">
1:1.1.0-7
</property>
</package>
<package id="1661" name="xserver-xorg-video-intel">
<property name="description" type="str">
X.Org X server -- Intel i8xx, i9xx display driver
</property>
<property name="version" type="str">
2:2.2.1-1ubuntu13.4
</property>
</package>
<package id="1662" name="xserver-xorg-video-mga">
<property name="description" type="str">
X.Org X server -- MGA display driver
</property>
<property name="version" type="str">
1:1.4.8.dfsg.1-1
</property>
</package>
<package id="1663" name="xserver-xorg-video-neomagic">
<property name="description" type="str">
X.Org X server -- Neomagic display driver
</property>
<property name="version" type="str">
1:1.1.1-8
</property>
</package>
<package id="1664" name="xserver-xorg-video-newport">
<property name="description" type="str">
X.Org X server -- Newport display driver
</property>
<property name="version" type="str">
1:0.2.1-4ubuntu1
</property>
</package>
<package id="1665" name="xserver-xorg-video-nsc">
<property name="description" type="str">
X.Org X server -- NSC Geode GX1 display driver
</property>
<property name="version" type="str">
1:2.8.3-2ubuntu0.1
</property>
</package>
<package id="1666" name="xserver-xorg-video-nv">
<property name="description" type="str">
X.Org X server -- NV display driver
</property>
<property name="version" type="str">
1:2.1.8-1ubuntu1
</property>
</package>
<package id="1667" name="xserver-xorg-video-openchrome">
<property name="description" type="str">
X.Org X server -- VIA display driver
</property>
<property name="version" type="str">
1:0.2.901-0ubuntu4
</property>
</package>
<package id="1668" name="xserver-xorg-video-psb">
<property name="description" type="str">
2D graphics driver for Poulsbo
</property>
<property name="version" type="str">
0.2.1-1ubuntu3
</property>
</package>
<package id="1669" name="xserver-xorg-video-rendition">
<property name="description" type="str">
X.Org X server -- Rendition display driver
</property>
<property name="version" type="str">
1:4.1.3.dfsg.1-4
</property>
</package>
<package id="1670" name="xserver-xorg-video-s3">
<property name="description" type="str">
X.Org X server -- legacy S3 display driver
</property>
<property name="version" type="str">
1:0.5.0-4
</property>
</package>
<package id="1671" name="xserver-xorg-video-s3virge">
<property name="description" type="str">
X.Org X server -- S3 ViRGE display driver
</property>
<property name="version" type="str">
1:1.9.1-7
</property>
</package>
<package id="1672" name="xserver-xorg-video-savage">
<property name="description" type="str">
X.Org X server -- Savage display driver
</property>
<property name="version" type="str">
1:2.1.3-5
</property>
</package>
<package id="1673" name="xserver-xorg-video-siliconmotion">
<property name="description" type="str">
X.Org X server -- SiliconMotion display driver
</property>
<property name="version" type="str">
1:1.5.1-3
</property>
</package>
<package id="1674" name="xserver-xorg-video-sis">
<property name="description" type="str">
X.Org X server -- SiS display driver
</property>
<property name="version" type="str">
1:0.9.3-6
</property>
</package>
<package id="1675" name="xserver-xorg-video-sisusb">
<property name="description" type="str">
X.Org X server -- SiS USB display driver
</property>
<property name="version" type="str">
1:0.8.1-9
</property>
</package>
<package id="1676" name="xserver-xorg-video-tdfx">
<property name="description" type="str">
X.Org X server -- tdfx display driver
</property>
<property name="version" type="str">
1:1.3.0-6
</property>
</package>
<package id="1677" name="xserver-xorg-video-tga">
<property name="description" type="str">
X.Org X server -- TGA display driver
</property>
<property name="version" type="str">
1:1.1.0-9ubuntu1
</property>
</package>
<package id="1678" name="xserver-xorg-video-trident">
<property name="description" type="str">
X.Org X server -- Trident display driver
</property>
<property name="version" type="str">
1:1.2.4-1
</property>
</package>
<package id="1679" name="xserver-xorg-video-tseng">
<property name="description" type="str">
X.Org X server -- Tseng display driver
</property>
<property name="version" type="str">
1:1.1.1-4
</property>
</package>
<package id="1680" name="xserver-xorg-video-v4l">
<property name="description" type="str">
X.Org X server -- Video 4 Linux display driver
</property>
<property name="version" type="str">
1:0.1.1-6ubuntu1
</property>
</package>
<package id="1681" name="xserver-xorg-video-vesa">
<property name="description" type="str">
X.Org X server -- VESA display driver
</property>
<property name="version" type="str">
1:1.3.0-4ubuntu4
</property>
</package>
<package id="1682" name="xserver-xorg-video-vga">
<property name="description" type="str">
X.Org X server -- VGA display driver
</property>
<property name="version" type="str">
1:4.1.0-8
</property>
</package>
<package id="1683" name="xserver-xorg-video-via">
<property name="description" type="str">
X.Org X server -- VIA display driver
</property>
<property name="version" type="str">
1:0.2.2-5
</property>
</package>
<package id="1684" name="xserver-xorg-video-vmware">
<property name="description" type="str">
X.Org X server -- VMware display driver
</property>
<property name="version" type="str">
1:10.15.2-1ubuntu2
</property>
</package>
<package id="1685" name="xserver-xorg-video-voodoo">
<property name="description" type="str">
X.Org X server -- Voodoo display driver
</property>
<property name="version" type="str">
1:1.1.1-5
</property>
</package>
<package id="1686" name="xsltproc">
<property name="description" type="str">
XSLT command line processor
</property>
<property name="version" type="str">
1.1.22-1ubuntu1
</property>
</package>
<package id="1687" name="xterm">
<property name="description" type="str">
X terminal emulator
</property>
<property name="version" type="str">
229-1ubuntu1
</property>
</package>
<package id="1688" name="xulrunner-1.9">
<property name="description" type="str">
XUL + XPCOM application runner
</property>
<property name="version" type="str">
1.9+nobinonly-0ubuntu0.8.04.1
</property>
</package>
<package id="1689" name="xulrunner-1.9-gnome-support">
<property name="description" type="str">
Support for Gnome in xulrunner-1.9 applications
</property>
<property name="version" type="str">
1.9+nobinonly-0ubuntu0.8.04.1
</property>
</package>
<package id="1690" name="xutils">
<property name="description" type="str">
X Window System utility programs metapackage
</property>
<property name="version" type="str">
1:7.3+10ubuntu10.2
</property>
</package>
<package id="1691" name="xutils-dev">
<property name="description" type="str">
X Window System utility programs for development
</property>
<property name="version" type="str">
1:7.2.ds2-1ubuntu1
</property>
</package>
<package id="1692" name="yelp">
<property name="description" type="str">
Help browser for GNOME 2
</property>
<property name="version" type="str">
2.22.1-0ubuntu2.8.04.1
</property>
</package>
<package id="1693" name="zenity">
<property name="description" type="str">
Display graphical dialog boxes from shell scripts
</property>
<property name="version" type="str">
2.22.1-1
</property>
</package>
<package id="1694" name="zip">
<property name="description" type="str">
Archiver for .zip files
</property>
<property name="version" type="str">
2.32-1
</property>
</package>
<package id="1695" name="zlib1g">
<property name="description" type="str">
compression library - runtime
</property>
<property name="version" type="str">
1:1.2.3.3.dfsg-7ubuntu1
</property>
</package>
</packages>
</software>
<summary>
<architecture value="i386"/>
<client name="hwtest-gtk" version="0.1-0ubuntu10"/>
<contactable value="False"/>
<date_created value="2008-09-07T13:01:43"/>
<distribution value="Ubuntu"/>
<distroseries value="8.04"/>
<live_cd value="False"/>
<private value="False"/>
<system_id value="f6e0c4232b92ca06b7356f8ed2a0ae61"/>
</summary>
</system>

---

### Post by Bucky Ball on 2008-09-07
In the hardware test, did it say you were 'fully connected'?

---

### Post by sunilkumar on 2008-09-07
Yes. It said. But cant surf or ping result is 0%. It is not in the above summary?

---

### Post by Bucky Ball on 2008-09-07
Easier to ask as there is a ton of info there which I spent 5 minutes trying to find the result in. The WPASupplicant could be causing a problem, but that is for wireless and you are using a wired connection so it shouldn't be activating by default.

```
auto lo
iface lo inet loopback

# iface ppp0 inet ppp
# provider ppp0

auto ppp0

# iface eth0 inet dhcp

# iface eth0 inet ipv4ll

auto eth0
```

Don't hash out **iface lo inet loopback** or **auto eth0**.

Perhaps try that variation. You could experiment using the hash marks and see if it changes your results but your card is working, you are just not getting through to the router (or should I say, you are not getting a stable connection with the router). It could just be getting the right combination of hash marks.  Are you sure you have the correct details in System->Administration->Network? You mentioned at one point you could ping the router and it gave you the network name? These details you need to have in System->Administration->Network, same as the router to get onto your network. Pinging is one thing but to make a stable connection your computer and router both need the same network name.

Getting very late over here so I need to sleep and I am running out of ideas sorry. Sometimes it's easy and things work 'out of the box', other cases, like this one, it is the opposite. ;( 

If you have no luck with experimenting with the hash marks, my suggestion would be ...

Take the /etc/network/interfaces to where you are able to ping the router and re-post in the 'Networking and Wireless' forum (rather than this one) where you will hopefully get a couple of brains that have dealt with your situation and can identify your problem quickly. We are just trying things to see if they work. Post:

1/ Your network card
2/ Exactly what error messages you are getting 
3/ Your /etc/network/interfaces file

and anything else you can think of that might help. Good luck and I will keep thinking. Let me know how you go. \\:D/

---

### Post by sunilkumar on 2008-09-07
Sorry. no result. Again I rebooted and tried. But no result.
(I did the same old **sudo gedit /etc/network/interfac**es
command and copy paste this code.)

Do you think I should try some other Eg:FEDORA linux distro?

---

### Post by Bucky Ball on 2008-09-07
Nope, read my last post. :) You will find it won't make much difference. Post in the Internet and wireless forums before you take any drastic measures. :)

---

### Post by phil66 on 2008-09-07
You could also try stating your problem at irc//#ubuntu live chat
They are constantly on line and usually about 1300 users.

They have been helpful with some of my problems in Ubuntu

---

### Post by sunilkumar on 2008-09-08
I tried [this]("http://www.jamesonwilliams.com/hardy-r8168.html") [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

Now the Access concentrator problem gone. But still I cant ping or browse.

Perhaps the changes made as per the previous posts action/commands. How can I revert back to original state?


Also in Win XP Wake-On-Lan is enabled through Control Panel>System>Hardware>Device Manager>Network card properties. Checked the BIOS ofr Wake-On-Lan and not found anything like that.

Anybody please help me.

---

### Post by Bucky Ball on 2008-09-08
```
auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider ppp0

auto ppp0

iface eth0 inet ipv4ll

auto eth0
```That's what your original file looked like. It is on page three of this thread. Re-post in 'networking and wireless' forum.

---

### Post by sunilkumar on 2008-09-08
Hats of to YOU all.

I reposted it here. [http://ubuntuforums.org/showthread.php?p=5749658#post5749658](http://ubuntuforums.org/showthread.php?p=5749658#post5749658)

The problem not yet solved, because I am unlucky. But you people are very helpfull. I should appreciate that. 

THANK YOU ALL.

Regards,

---

