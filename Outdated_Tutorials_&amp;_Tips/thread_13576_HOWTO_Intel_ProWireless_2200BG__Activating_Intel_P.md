---
title: "HOWTO: Intel Pro/Wireless 2200BG / Activating Intel Pro/Wireless 2200BG network card"
date: 2005-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Spif on 2005-02-01
**Intel Pro/Wireless 2200BG HowTo for Ubuntu Warty Warthog 4.10 x86**


1.Before we start, make sure you have the appropriate *linux-headers* installed for your kernel. If you are not sure which kernel you are currently using, open a console and type

*uname -r*

     Kernel version number will appear. For example, if you have the kernel 2.6.8.1-3-386, you will                      
     need the package *linux-headers-2.6.8.1-3-386*. 

*sudo apt-get install linux-headers-2.6.8.1-3-386*
 
2.Later in this guide you will need components from the *build-essential* package. If it is not already installed, do so by typing

*sudo apt-get install build-essential*

     in the console. 

3.Next step is to download the ipw2200 drivers: [http://ipw2200.sourceforge.net/#downloads](http://ipw2200.sourceforge.net/#downloads). This guide will assume you are using version 1.0.0.

4.You will also need the latest version of the binary firmware. It can be downloaded here: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php). The HowTo will assume you are using version 2.2. 
 
5.When you have finished downloading, write

*sudo mv ipw2200-fw-2.2.tgz /usr/lib/hotplug/firmware/*

     to move the firmware to the correct folder, then

*cd /usr/lib/hotplug/firmware/*

     to go there yourself. Now the file needs to get extracted.

*tar zxf ipw2200-fw-2.2.tg*

6.If you got to this step without any errors, the firmware has been set up correctly. Now you must move the driver to /usr/scr, so type

*sudo mv ipw2200-1.0.0.tgz /usr/src*

     then

*cd /usr/src/*

     and finally

*tar zxf ipw2200-0.21.tgz*

     to extract it.

7.Enter the newly extracted folder by writing

*cd /usr/src/ipw2200-1.0.0*

     The driver needs to get compiled. First check for any problems by using *make*. If it returned any errors, you have not installed the build-essential package and the appropriate linux-headers. If it on the other hand worked flawlessly, type 

*sudo make install*

8.The driver has now been installed, but in order for it to work you can either restart your computer or type 

*sudo modprobe ieee80211*

     and

*sudo modprobe ipw2200*

in the console to load the modules right away.

9.To check whether your wireless functions, write

*sudo iwconfig*

     Your wireless eth connection should now have a lot of information listed. Here is an example:

eth1   IEEE 802.11g  ESSID:"network name"
          Mode:Managed  Channel:11  Access Point: 00:0F:B5:60:1F:E0
          Bit Rate=36Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=77/100  Signal level=-58 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3
 
10. If you are running Ubuntu on a laptop and it is still not working, go to the “Activating Intel Pro/Wireless 2200BG network card under Ubuntu Warty Warthog 4.10 x86” section. Otherwise enjoy your new wireless Internet connection!


**Activating Intel Pro/Wireless 2200BG network card under Ubuntu Warty Warthog 4.10 x86**

This guide was tested on a Zepto Znote 4200 and I can therefore not garatee it will work with all laptops. Use at your own risk!

1.If your network is still not working, your network card may need to be activated with additional software. Download the Acer Hotkey driver from this site: [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/). This guide will assume you have downloaded the acerhk-0.5.19.tgz version.

2.Open the console and type

*sudo mv acerhk-0.5.19.tgz /usr/src/*

      to move the file and

*cd /usr/src/*

      to go to the directory yourself. Extract the file by writing

*sudo tar zxf acerhk-0.5.19.tgz*

3.Go to the newly unpacked folder:

*cd acerhk-0.5.19*

      Use make to test whether there will be any errors compiling it. If none came up, type

*sudo make install *

      to start compiling.

4.Load the module by using these commands:

*sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290*

     followed by

* echo 1 > /proc/driver/acerhk/wirelessled*

5.Enjoy your new wireless connection!

---

### Post by Darrena on 2005-02-01
[QUOTE=Spif]**Intel Pro/Wireless 2200BG HowTo for Ubuntu Warty Warthog 4.10 x86**


1.Before we start, make sure you have the appropriate *linux-headers* installed for your kernel. If you are not sure which kernel you are currently using, open a console and type

*uname -r*

     Kernel version number will appear. For example, if you have the kernel 2.6.8.1-3-386, you will                      
     need the package *linux-headers-2.6.8.1-3-386*. 

*sudo apt-get install linux-headers-2.6.8.1-3-386*
 
2.Later in this guide you will need components from the *build-essential* package. If it is not already installed, do so by typing

*sudo apt-get install build-essential*

     in the console. 

3.Next step is to download the ipw2200 drivers: [http://ipw2200.sourceforge.net/#downloads](http://ipw2200.sourceforge.net/#downloads). This guide will assume you are using version 1.0.0.

4.You will also need the latest version of the binary firmware. It can be downloaded here: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php). The HowTo will assume you are using version 2.2. 
 
5.When you have finished downloading, write

*sudo mv ipw2200-fw-2.2.tgz /usr/lib/hotplug/firmware/*

     to move the firmware to the correct folder, then

*cd /usr/lib/hotplug/firmware/*

     to go there yourself. Now the file needs to get extracted.

*tar zxf ipw2200-fw-2.2.tg*

6.If you got to this step without any errors, the firmware has been set up correctly. Now you must move the driver to /usr/scr, so type

*sudo mv ipw2200-1.0.0.tgz /usr/src*

     then

*cd /usr/src/*

     and finally

*tar zxf ipw2200-0.21.tgz*

     to extract it.

7.Enter the newly extracted folder by writing

*cd /usr/src/ipw2200-1.0.0*

     The driver needs to get compiled. First check for any problems by using *make*. If it returned any errors, you have not installed the build-essential package and the appropriate linux-headers. If it on the other hand worked flawlessly, type 

*sudo make install*

8.The driver has now been installed, but in order for it to work you can either restart your computer or type 

*sudo modprobe ieee80211*

     and

*sudo modprobe ipw2200*

in the console to load the modules right away.

9.To check whether your wireless functions, write

*sudo iwconfig*

     Your wireless eth connection should now have a lot of information listed. Here is an example:

eth1   IEEE 802.11g  ESSID:"network name"
          Mode:Managed  Channel:11  Access Point: 00:0F:B5:60:1F:E0
          Bit Rate=36Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=77/100  Signal level=-58 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3
 
10. If you are running Ubuntu on a laptop and it is still not working, go to the “Activating Intel Pro/Wireless 2200BG network card under Ubuntu Warty Warthog 4.10 x86” section. Otherwise enjoy your new wireless Internet connection!


**Activating Intel Pro/Wireless 2200BG network card under Ubuntu Warty Warthog 4.10 x86**

This guide was tested on a Zepto Znote 4200 and I can therefore not garatee it will work with all laptops. Use at your own risk!

1.If your network is still not working, your network card may need to be activated with additional software. Download the Acer Hotkey driver from this site: [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/). This guide will assume you have downloaded the acerhk-0.5.19.tgz version.

2.Open the console and type

*sudo mv acerhk-0.5.19.tgz /usr/src/*

      to move the file and

*cd /usr/src/*

      to go to the directory yourself. Extract the file by writing

*sudo tar zxf acerhk-0.5.19.tgz*

3.Go to the newly unpacked folder:

*cd acerhk-0.5.19*

      Use make to test whether there will be any errors compiling it. If none came up, type

*sudo make install *

      to start compiling.

4.Load the module by using these commands:

*sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290*

     followed by

* echo 1 > /proc/driver/acerhk/wirelessled*

5.Enjoy your new wireless connection![/QUOTE]
 Spif, are you able to do scanning with that wireless card?  My MA401 works but I have to know all the available connections and it will not just scan for them using iwlist eth1 scanning.

---

### Post by Spif on 2005-02-01
When everything had been set up I could perform a succesful scanning.

---

### Post by blackomegax on 2005-02-16
thank you for this guide. helped me greatly. :)

im a noob to linux and didnt realize why the driver wouldnt compile till i read your guide. then it worked :)

its also nice since it (the guide) seems geared towards the acer 290 series (which is what i have) (unless acerhk is universal for laptop's with hardswitches for wifi :))

---

### Post by ihv on 2005-02-21
i followed all the instructions and recieved no errors but i am stil unable to access wifi

lsmod shows that ipw2200 (and also e100, module for my lan nic) are not loaded, loading them does not give any output and lsmod shows they are still unloaded

my laptop is Dell D505, the blue wifi indicator light is on (controllable by key combination)

during boot i recieve 3 error messages:

error inserting pciehp.ko and 2 others in (dont remember precisely)
/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug 
operation not permitted

what should i do next?

thanks in advance

Ihv

[COLOR=Red]EDIT: ISSUE SOLVED[/COLOR] - passed **acpi=noirq** to kernel and got wifi working perfect, in addition sound card started to work :-)

---

### Post by Spif on 2005-02-23
[QUOTE=blackomegax]its also nice since it (the guide) seems geared towards the acer 290 series (which is what i have) (unless acerhk is universal for laptop's with hardswitches for wifi :))[/QUOTE]

Acerhk works with configurations that resemble Acer's. The program worked flawlessly with my Zepto Znote 4200 (Scandinavian notebook company).

I'm glad you found my guide useful :razz:

---

### Post by blackomegax on 2005-02-24
Znote 4200 appears to be a compal CL56.

travelmate 290's with 9600's in them = CL56.
ones with intel (mine) = CL51

so its no wonder it worked, as its the exact same switch interface (hell, the 51/56 share battery type and 99% form factor) :)

just random info  :grin:

---

### Post by acaus on 2005-03-08
Firstly, thanks for the detailed instructions it is a god send. However, I am still unable to get my wireless to work. When I go into the network configurations and activate it, it drops out. 
When I type sudo iwconfig i get the following

lo        no wireless extensions.

eth0      unassociated  ESSID:"default"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:0102-0304-05   Security mode:restricted
          Power Management:off

eth1      no wireless extensions.

sit0      no wireless extensions.


Any help will be appriciated.

Acaus

---

### Post by Spif on 2005-03-10
[QUOTE=acaus]Firstly, thanks for the detailed instructions it is a god send. However, I am still unable to get my wireless to work. When I go into the network configurations and activate it, it drops out. 
When I type sudo iwconfig i get the following

lo        no wireless extensions.

eth0      unassociated  ESSID:"default"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:0102-0304-05   Security mode:restricted
          Power Management:off

eth1      no wireless extensions.

sit0      no wireless extensions.


Any help will be appriciated.

Acaus[/QUOTE]

I need more details about your system. Are you running Warty or Hoary and what laptop do you have? Have you tried configuring your wireless conncection with the 'Networking' tool?

Did you install Acerhk? Are you aware that you have to run the 'sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290' and 'echo 1 > /proc/driver/acerhk/wirelessled' everytime you start your computer to get the connection up and running?

---

### Post by deviant03 on 2005-03-11
The Intel 2200BG worked right out the box for me. I have a Thinkpad T30 but bought the wireless card separate so I had to do the 1802 bios hack to get the Thinkpad to recognize the wireless card. Once I rebooted the wireless was up. The thing is though the connection is recognized as eth0, there is no option in network preferences to enter a WEP key. I wouldnt want to anyway cause Ive read WEP is not all that safe but does anyone know if its possible to get the Intel 2200bg working with WPA under Ubuntu? Any info would be appreciated.

---

### Post by clov on 2005-03-18
I'm configuring ipw2200 on a compal CL56, but I can't get a HWaddr
```

th1 Link encap:Ethernet **HWaddr 00:00:00:00:00:00**
inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 Base address:0x6000 Memory:d0000000-d0000fff

```
I tried to find out what the problem was, and acerhk came up, but can't put it to work.
I used "make acerhk.ko" (I'm using kernel 2.6.10-5-386) a got:
```

 sudo make acerhk.ko
awk: cannot open /usr/src/kernel-source-2.4.21-acpi-i2c-lmsensors/include/linux/version.h (No such file or directory)
awk: cannot open /usr/src/kernel-source-2.4.21-acpi-i2c-lmsensors/include/linux/version.h (No such file or directory)
make -C /usr/src/kernel-source-2.4.21-acpi-i2c-lmsensors SUBDIRS=/home/clov/acerhk-0.5.19 modules
make: *** /usr/src/kernel-source-2.4.21-acpi-i2c-lmsensors: No such file or directory.  Stop.
make: *** [acerhk.ko] Error 2

```

the weird thing is, if I run windows first wireless lan works fine!

---

### Post by Balle-Larsen on 2005-03-22
clov,

I would appear that you should change your Makefile in acerhk to point to your kernel version.
It is the variable KERNELSRC you should change in top of the Makefile. Also you need to have the linux-headers installed for you kernel to build the acerhk module. If the kernel-headers are correctly installed there will be a link named build in /lib/modules/<version>/ that points to the headers.
therefore
KERNELSRC=/lib/modules/'uname -r'/build
will remove your error messages when building acerhk.

You don't have to have the acerhk running in order to have the wireless run.

---

### Post by clov on 2005-03-22
[QUOTE=Balle-Larsen]clov,

You don't have to have the acerhk running in order to have the wireless run.[/QUOTE]

I don't?!?
well I've notice that I can only get a wireless connections after I run windows and it turns on my wireless card.
before that, I get HWaddr 00:00:00: ..... strange!? I know but WORKS!
I'f I don't need acerhk how can I turn on my wireless card without runnig windows?

---

### Post by Technoviking on 2005-03-22
I'm been having ipw2200 firmware crasheds both in warty and hoary. I had this happen with included firmware and one download from the project page. Any one seen this before.

Mike

---

### Post by Balle-Larsen on 2005-03-23
[QUOTE=clov]I don't?!?
well I've notice that I can only get a wireless connections after I run windows and it turns on my wireless card.
before that, I get HWaddr 00:00:00: ..... strange!? I know but WORKS!
I'f I don't need acerhk how can I turn on my wireless card without runnig windows?[/QUOTE]

I am running wireless with an Acer 1681 with ipw2200 and ubuntu Hoary preview. It runs without firmware crashes and Windows.
Please give more details on the AccessPoint you are trying to connect to. Does it broadcast the SID and what kind of encryption is it running etc.
I use Networkmonitor to connect to a 3com AccessPoint running wep.
The Acer has a hardware button to switch off wireless and unfortunately the acerhk can not switch on the LED for the wireless. It was working with an older kernel and without  loading the ipw2200 module. If anyone has solved this I would like to know about it.

---

### Post by clov on 2005-03-25
the problem is tha if i don't start windows before running ubuntu my wireless card HWaddr is 00:00:00:00: ...

---

### Post by dalmeida on 2005-03-26
Anyone in here have been able to install Ubuntu and get wireless working on a Travelmate 2200? Thanks.

---

### Post by dez on 2005-04-06
Firstly thanks for writing the guide, it really is very useful.

Disclaimer: I am by no means skilled at Linux, this may be a silly question

It went grand up until the modprobe...
[B]
dez@irclap43:/usr/src/ipw2200-1.0.0 $ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.8.1-3-386/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B]

[B]dez@irclap43:/usr/src/ipw2200-1.0.0 $ lsmod | grep ipw
ipw2100                90596  0
firmware_class          9728  1 ipw2100
ieee80211              21124  1 ipw2100[/B]

uname -a
Linux irclap43 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux




I am not sure if this is working or not. 
[B]dez@irclap43:/usr/src/ipw2200-1.0.0 $ sudo /sbin/dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:23:a3:db:c8
Sending on   LPF/eth1/00:04:23:a3:db:c8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

I am running Ubuntu Warty, on a Dell Latitude d600.


Thanks

---

### Post by Spif on 2005-04-09
[QUOTE=dez]Firstly thanks for writing the guide, it really is very useful.

Disclaimer: I am by no means skilled at Linux, this may be a silly question

It went grand up until the modprobe...
[B]
dez@irclap43:/usr/src/ipw2200-1.0.0 $ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.8.1-3-386/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B]

[B]dez@irclap43:/usr/src/ipw2200-1.0.0 $ lsmod | grep ipw
ipw2100                90596  0
firmware_class          9728  1 ipw2100
ieee80211              21124  1 ipw2100[/B]

uname -a
Linux irclap43 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux




I am not sure if this is working or not. 
[B]dez@irclap43:/usr/src/ipw2200-1.0.0 $ sudo /sbin/dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:23:a3:db:c8
Sending on   LPF/eth1/00:04:23:a3:db:c8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

I am running Ubuntu Warty, on a Dell Latitude d600.


Thanks[/QUOTE]

Acerhk will not work with Dell, sorry. If I remeber correctly, there is a HOWTO about a Dell Latitude (either 600 or 800, can't recall) laptop here on the forums. Try doing  search. If you haven't already, nstalling Hoary is also a good idea :wink:

---

### Post by bschmid on 2005-11-24
[QUOTE=ihv]
[COLOR=Red]EDIT: ISSUE SOLVED[/COLOR] - passed **acpi=noirq** to kernel and got wifi working perfect, in addition sound card started to work :-)[/QUOTE]
Hello,

I have a dell D505.
I have acpi=noirq configured.
I load the module ipw2200 and ieee80211 with modprobe.
But unfortunately eth1 is not created.
Of course iwconfig does therefore not see any wireless card.
But the card is up because it works in windows.

What would you suggest to gest my wireless card working?

Thanks in advance.

---

### Post by JOBLESSINUSA on 2007-04-28
I Don't Know About All The Above. I Just Installed The 2200bg In An Adapter ,Attached A Pigtail And Kinda Angled The Machine So It Could "see" The Ap And Booted Ubuntu 7.04. I Right Clicked On The The Little "wired" Icon Did Some Fiddling There And Waited While "ubuntu The Magnificent" Connected Me "automagicaly" ...

---

### Post by depp on 2007-04-28
last entry was posted two years ago, that was a ubuntu that is 4 versions before what you are using.

that's just a result of the rapid development. :)

---

