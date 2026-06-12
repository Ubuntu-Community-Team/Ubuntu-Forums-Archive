---
title: "HP Printer Install"
date: 2015-11-18
forum: New to Ubuntu
---

### Post by misasoup on 2015-11-18
Hello,
I am trying to use my old HP printer (5-8 years old) on Ubuntu 14.04.  I came across the [http://hplipopensource.com/hplip-web/install/installtree.html](http://hplipopensource.com/hplip-web/install/installtree.html) site and did the following: 

[COLOR=#000000][FONT=Arial]"Run in a terminal window:[/FONT][/COLOR]
dpkg -l hplip
[COLOR=#000000][FONT=Arial]You may see something that looks like this:[/FONT][/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name             Version                  Description
-----------------------------------------------------------------------------
ii  hplip            1.7.3-0ubuntu1           HP Linux Printing and Imaging
[COLOR=#000000][FONT=Arial]If you see "ii" in the first column before "hplip", then HPLIP is already installed. If you want to use the currently installed version of HPLIP, try running hp-setup in a terminal shell. "



there was an "ii" in front of the hplip

I then assumed that everything's fine and tried system settings which asked me for an "URI".  All I know about URI is that his surname is Geller and that he bends spoons.

Could You please help me to make my printer work on Ubuntu?

Best regards,

Michele[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-11-18
Welcome to the forums.  There are several ways to set up HP printers.  What is the model of the printer?

Open a terminal.

```
apt-cache policy hplip
```

Version 3.14.3 is usually supplied with 14.04.

Plug the printer in, connect it to the network or use a USB cable (don't use both).  Make sure it is awake, push a few front panel buttons.  Set up the network settings for your network from the front panel.  Typically:

IP: 192.168.1.155
Mask:  255.255.255.0
Gateway: 192.168.1.1

```
hp-setup
```

It should show up automatically.  If it doesn't, then put [http://192.168.1.155:631](http://192.168.1.155:631) in the URI box.

Print something.

---

### Post by Geoffrey_Arndt on 2015-11-18
Hello Michele,

HP printers practically install themselves.   In other words, don't assume you have to install them manually.

If you've hooked up your printer via USB cable (always a good first step even for wireless printers), then, go through the process of adding the printer (without installing any drivers) by going to "System Settings>Printers>Server>New" .   This is the screen that shows "URI" - - - which is not old Uri Geller, but instead stands for Universal Resource Identifier (which is basically the network address of the printer, (as shown in a browser window . . . e..g., 192.168.1.155) . . . BUT, only if you have awireless printer AND you have a wireless network.    That's why the physical USB connection is required . . . . because then Ubuntu will "see" (detect) the printer and offer to install it for you via the System Settings>Printers>Server>New dialog windows.    Most of the time, for common HP printers, that's all that's required to finish the install  . . . then just run your print test page to confirm.

If above doesn't work, what you then want is a "stand-alone" printer driver from HP-Lip website where you search for your printer model (in other words, click on "Supported Printers" in the left panel), AND then download the specific deb file to your downloads folder so you can install it.     The deb file can easily be installed via the "gdebi" program (available from the Ubuntu Software Center), or right clicking the deb may offer you the option to use the Ubuntu Software Center to run the install script automagically.

---

### Post by misasoup on 2015-11-19
Thank you Geoffrey and [COLOR=#000000]tgalati4 for your help.  

I managed to add the printer in settings by using [http://192.168.1.155:631/](http://192.168.1.155:631/) as URI. however when put hp-setup into the terminal it gave me "error: No devices found on bus:usb" I tried  connection (I/O) type Universal bus (USB) and Network/Ethernet/wireless network (direct connection or JetDirect).  I used a cable to connect the printer.
 
Could you please advise what to do?

i would add a screenshot but I struggle to add it to this post.

Best regards,

Michèle


[/COLOR]

---

### Post by tgalati4 on 2015-11-19
Did you set up the network connections on the printer itself using the front panel:  Maintenance, Settings, Network?

Post:

```
ifconfig
netstat -r
```

---

### Post by kurt18947 on 2015-11-19
> [COLOR=#000000]I managed to add the printer in settings by using [http://192.168.1.155:631/](http://192.168.1.155:631/)[/COLOR]

The above is the address when communicating via network, I don't know that it makes a difference when attaching via USB. A second thought is that my networked printers all use port 9100. Port 631 is typically used by CUPS. So I suspect your printer's network address should look something like [http://192.168.1.155:9100](http://192.168.1.155:9100). Mine use port 9100 and they work quite reliably. I've seen and used port 631 for CUPS administration but not for sending print jobs.

---

### Post by tgalati4 on 2015-11-19
Yes, that is correct, port 9100 is the typical communication port for printing.  It's also possible that the printer has developed a hardware fault--5 to 8 years old.  HP printers are not known for their quality or reliability.  HP printers are generally plug-and-play.  When they are not, then I tear them down and often find hardware faults that are difficult and expensive to repair.  I have a closet-full of old HP printers that I use for parts.  Every once in a while, I assemble a working one by cobbling parts together.  Excellent Linux support, crappy quality.

---

### Post by Geoffrey_Arndt on 2015-11-20
The basic HPLip drivers, libraries are installed by default in Ubuntu, xubuntu, lubuntu, etc.    Trying to install additional versions on top of those can mess up the originals and confuse the installer.   

Did you follow the basic procedures on post #3?   What error(s) did you get?    By cable, I'm assuming you mean USB . . . It may not be required, but it's often a good idea to reboot after first connecting a new device.

And lastly, the first thing you should have done in post #1 is to _let us know the exact printer model of HP_ . . . . perhaps we can look it up and find the specific driver you need to download.

---

### Post by misasoup on 2015-11-30
Hello,
 

 Thank You for your further help and no, I have not given up despite appearances :-)

 

 I changed the URI to [http://192.168.1.155:9100]("http://192.168.1.155:9100/") and tried to print a test page but the message was still &#8220;printer not connected&#8221; in the printer queue.  I did follow all the steps in message 3 and the error message was the same.

 

 The printer is recognised as HP F300 but it is an F380. It still possible to make good quality copies with it.

 

 I also typed &#8220;ifconfig&#8221; in  the black box and the result was

 

 sabese@sabese-NQ851AA-B14-IQ830be:~$ ifconfig 

 eth0      Link encap:Ethernet  HWaddr 00:24:8c:5b:c0:e3   
           inet addr:192.168.178.20  Bcast:192.168.178.255  Mask:255.255.255.0 
           inet6 addr: fe80::224:8cff:fe5b:c0e3/64 Scope:Link 
           inet6 addr: 2001:7e8:c252:1:49d3:1359:e743:19e4/64 Scope:Global 
           inet6 addr: 2001:7e8:c252:1:224:8cff:fe5b:c0e3/64 Scope:Global 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:442 errors:0 dropped:0 overruns:0 frame:0 

           TX packets:489 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:92248 (92.2 KB)  TX bytes:89149 (89.1 KB) 
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:65536  Metric:1 

           RX packets:535 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:535 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:54067 (54.0 KB)  TX bytes:54067 (54.0 KB) 
  
 wlan0     Link encap:Ethernet  HWaddr 00:22:5f:6c:f1:8d   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 

           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
 sabese@sabese-NQ851AA-B14-IQ830be:~$  
 

 Many thanks in advance for any help you can give me with this.
 

 Best regards,
 

 Michele

---

### Post by buzzingrobot on 2015-11-30
To get my HP printer working, I've always just installed and executed the "hplip-gui" package, which puts a GUI wrapper around the hplip script. My printer requires a driver and this will download and install the correct driver from the HP site. 

I've noticed it is common for Ubuntu and other Linux distributions to show this printer to be successfully "enabled" using the distro's printer setup tools when, in fact, the driver has not been installed.  Of course, it does not work and it is easy to go off on fruitless attempts to fix things.

So, get and run "hplip-gui". It is *essential* to know how your printer is connected.  The easiest way to make this work is to use a USB cable connection even if you want later to switch to wireless or a network link. hplip-gui asks you to identify how the printer is connected, then it attempts to locate the printer on that connection.  Having found and identified the printer, it downloads the correct driver and installs it, prompting for a password twice.

When that's done, you may need to use Ubuntu's printer setup tool to mark the printer as the default.

---

### Post by LukeMorrison on 2015-11-30
According to this information, it looks like your printer should be on 192.168.178.155 not 192.168.1.155, which may be one of the reasons it is not making a connection.

[EMAIL="sabese@sabese-NQ851AA-B14-IQ830be:~$"]sabese@sabese-NQ851AA-B14-IQ830be:~$[/EMAIL] ifconfig 

 eth0      Link encap:Ethernet  HWaddr 00:24:8c:5b:c0:e3   
           inet addr:192.168.178.20  Bcast:192.168.178.255  Mask:255.255.255.0 
           inet6 addr: fe80::224:8cff:fe5b:c0e3/64 Scope:Link 
           inet6 addr: 2001:7e8:c252:1:49d3:1359:e743:19e4/64 Scope:Global 
           inet6 addr: 2001:7e8:c252:1:224:8cff:fe5b:c0e3/64 Scope:Global 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:442 errors:0 dropped:0 overruns:0 frame:0

---

