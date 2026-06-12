---
title: "[SOLVED] Can someone please help to connect my WIFI"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by germanix on 2008-10-01
I have installed Ubuntu on my Laptop. LAN connection works fine but not WIFI.
Here some output.
jac@jac-laptop:~$ sudo lshw -C network
[sudo] password for jac: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:06:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:c4:ed:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
jac@jac-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:06:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:c4:ed:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
jac@jac-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jac@jac-laptop:~$ 

[COLOR="Black"]**[B]**[/B][/COLOR]

---

### Post by Nxion on 2008-10-01
OK I have a guide that I created because I was having the same issues as you. First can you do me a favor, run this command for me and post the output here:

```
lspci
```

AND...

```
uname -r
```

I just want to make sure what kernel you are using so I cn give you the correct guide to fix the wifi issue. 

Thanks

---

### Post by germanix on 2008-10-01
jac@jac-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
jac@jac-laptop:~$ uname -r
2.6.24-19-generic
jac@jac-laptop:~$

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> jac@jac-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
jac@jac-laptop:~$ uname -r
2.6.24-19-generic
jac@jac-laptop:~$

Awesome, OK are you using the default installed kernel or are you using a different one?

Thanks

---

### Post by germanix on 2008-10-01
I am using the default installed directly from the LiveCD

---

### Post by Nxion on 2008-10-01
Sorry, ignore that I just relised what kernel you are using, I should read :) anyway, here is the guide. If you need any clarity on anything please let me know.

[**http://tinyurl.com/4ul7ha**]("http://tinyurl.com/4ul7ha")

---

### Post by germanix on 2008-10-01
How do I know which Linux header to choose. There are so many listed. Once I choose it do I symply copy and paste behind the cursor?

---

### Post by germanix on 2008-10-01
jac@jac-laptop:~$ sudo apt-get install build-essential
[sudo] password for jac: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Vorgeschlagene Pakete:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
Die folgenden NEUEN Pakete werden installiert:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 aktualisiert, 9 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 8704kB Archive geholt werden.
After this operation, 34,3MB of additional disk space will be used.
Möchten Sie fortfahren [J/n]? J
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.41 [696kB]
Hole:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Hole:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1187kB]
Hole:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [2784kB] 
Hole:5 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Hole:6 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30,1kB]
Hole:7 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95,6kB]          
Hole:8 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Hole:9 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7066B]
Es wurden 8704kB in 14s geholt (585kB/s)                                       
Wähle vormals abgewähltes Paket linux-libc-dev.
(Lese Datenbank ... 118101 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke linux-libc-dev (aus .../linux-libc-dev_2.6.24-19.41_i386.deb) ...
Wähle vormals abgewähltes Paket libc6-dev.
Entpacke libc6-dev (aus .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Wähle vormals abgewähltes Paket libstdc++6-4.2-dev.
Entpacke libstdc++6-4.2-dev (aus .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Wähle vormals abgewähltes Paket g++-4.2.
Entpacke g++-4.2 (aus .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Wähle vormals abgewähltes Paket g++.
Entpacke g++ (aus .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Wähle vormals abgewähltes Paket libtimedate-perl.
Entpacke libtimedate-perl (aus .../libtimedate-perl_1.1600-9_all.deb) ...
Wähle vormals abgewähltes Paket patch.
Entpacke patch (aus .../patch_2.5.9-4_i386.deb) ...
Wähle vormals abgewähltes Paket dpkg-dev.
Entpacke dpkg-dev (aus .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Wähle vormals abgewähltes Paket build-essential.
Entpacke build-essential (aus .../build-essential_11.3ubuntu1_i386.deb) ...
Richte linux-libc-dev ein (2.6.24-19.41) ...
Richte libc6-dev ein (2.7-10ubuntu4) ...
Richte libtimedate-perl ein (1.1600-9) ...
Richte patch ein (2.5.9-4) ...
Richte dpkg-dev ein (1.14.16.6ubuntu4) ...
Richte libstdc++6-4.2-dev ein (4.2.3-2ubuntu7) ...
Richte g++-4.2 ein (4.2.3-2ubuntu7) ...
Richte g++ ein (4:4.2.3-1ubuntu6) ...

Richte build-essential ein (11.3ubuntu1) ...
jac@jac-laptop:~$ sudo apt-get install linux-headers `uname-r`
bash: uname-r: command not found
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Paket linux-headers ist ein virtuelles Paket, das bereitgestellt wird von:
  linux-headers-2.6.24-19-xen 2.6.24-19.41
  linux-headers-2.6.24-19-virtual 2.6.24-19.41
  linux-headers-2.6.24-19-server 2.6.24-19.41
  linux-headers-2.6.24-19-rt 2.6.24-19.41
  linux-headers-2.6.24-19-openvz 2.6.24-19.41
  linux-headers-2.6.24-19-generic 2.6.24-19.41
  linux-headers-2.6.24-19-386 2.6.24-19.41
  linux-headers-2.6.24-19 2.6.24-19.41
  linux-headers-2.6.24-18-xen 2.6.24-18.32
  linux-headers-2.6.24-18-virtual 2.6.24-18.32
  linux-headers-2.6.24-18-server 2.6.24-18.32
  linux-headers-2.6.24-18-rt 2.6.24-18.32
  linux-headers-2.6.24-18-openvz 2.6.24-18.32
  linux-headers-2.6.24-18-generic 2.6.24-18.32
  linux-headers-2.6.24-18-386 2.6.24-18.32
  linux-headers-2.6.24-18 2.6.24-18.32
  linux-headers-2.6.24-16-xen 2.6.24-16.30
  linux-headers-2.6.24-16-virtual 2.6.24-16.30
  linux-headers-2.6.24-16-server 2.6.24-16.30
  linux-headers-2.6.24-16-rt 2.6.24-16.30
  linux-headers-2.6.24-16-openvz 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16-386 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
Sie sollten eines explizit zum Installieren auswählen.
E: Paket linux-headers hat keinen Installationskandidaten
jac@jac-laptop:~$  linux-headers-2.6.24-19-generic 2.6.24-19.41
bash: linux-headers-2.6.24-19-generic: command not found
jac@jac-laptop:~$

---

### Post by Nxion on 2008-10-01
can you post the list it gives you?

Thanks

---

### Post by Nxion on 2008-10-01
This is what you need to run:

```
sudo apt-get install linux-headers-2.6.24-19-generic
```

after that is installed continue on and follow the rest of the guide.

---

### Post by germanix on 2008-10-01
The URL which you gave me does not exist? see output
jac@jac-laptop:~$ sudo apt-get install subversion
[sudo] password for jac: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  libapr1 libaprutil1 libpq5 libsvn1
Vorgeschlagene Pakete:
  db4.6-util subversion-tools
Die folgenden NEUEN Pakete werden installiert:
  libapr1 libaprutil1 libpq5 libsvn1 subversion
0 aktualisiert, 5 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 1294kB Archive geholt werden.
After this operation, 6197kB of additional disk space will be used.
Möchten Sie fortfahren [J/n]? J
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main libapr1 1.2.11-1 [115kB]
Hole:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main libpq5 8.3.3-0ubuntu0.8.04 [272kB]
Hole:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main libaprutil1 1.2.12+dfsg-3 [70,0kB]
Hole:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main libsvn1 1.4.6dfsg1-2ubuntu1 [594kB]
Hole:5 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main subversion 1.4.6dfsg1-2ubuntu1 [243kB]
Es wurden 1294kB in 2s geholt (562kB/s)
Wähle vormals abgewähltes Paket libapr1.
(Lese Datenbank ... 120013 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libapr1 (aus .../libapr1_1.2.11-1_i386.deb) ...
Wähle vormals abgewähltes Paket libpq5.
Entpacke libpq5 (aus .../libpq5_8.3.3-0ubuntu0.8.04_i386.deb) ...
Wähle vormals abgewähltes Paket libaprutil1.
Entpacke libaprutil1 (aus .../libaprutil1_1.2.12+dfsg-3_i386.deb) ...
Wähle vormals abgewähltes Paket libsvn1.
Entpacke libsvn1 (aus .../libsvn1_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Wähle vormals abgewähltes Paket subversion.
Entpacke subversion (aus .../subversion_1.4.6dfsg1-2ubuntu1_i386.deb) ...
Richte libapr1 ein (1.2.11-1) ...

Richte libpq5 ein (8.3.3-0ubuntu0.8.04) ...

Richte libaprutil1 ein (1.2.12+dfsg-3) ...

Richte libsvn1 ein (1.4.6dfsg1-2ubuntu1) ...

Richte subversion ein (1.4.6dfsg1-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jac@jac-laptop:~$ sudo svn checkout [http://svn.madwifi.org/madwifi/trunk/madwifi-ng](http://svn.madwifi.org/madwifi/trunk/madwifi-ng)
svn: Die URL »[http://svn.madwifi.org/madwifi/trunk/madwifi-ng«](http://svn.madwifi.org/madwifi/trunk/madwifi-ng«) existiert nicht
jac@jac-laptop:~$ 

My computer is not able to find the Internet address for madwifi, says the URL does not exist

---

### Post by germanix on 2008-10-01
sudo apt-get install linux-headers-2.6.24-19-generic
this was done. Nothing was installed as I already had it on the computer. 
following the rest of the guide is a problem as the URL you mention in your guide does not seem to exist.

---

### Post by germanix on 2008-10-01
This means I cannot get to the subversion driver package!

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> sudo apt-get install linux-headers-2.6.24-19-generic
this was done. Nothing was installed as I already had it on the computer. 
following the rest of the guide is a problem as the URL you mention in your guide does not seem to exist.


OK let me fix that, ill have to find it again. That is strange that it isn't working now.

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> This means I cannot get to the subversion driver package!

Ok I found it. There is actually a space between trunk/ and madwifi-ng.

here is the corrected command:

```
sudo svn checkout http://svn.madwifi.org/madwifi/trunk/ madwifi-ng
```

copy it as I have it about and it should work.

---

### Post by germanix on 2008-10-01
Not Found

The requested URL /madwifi/trunk/madwifi-ng was not found on this server.
Apache/2.2.3 (Debian) DAV/2 SVN/1.4.2 mod_python/3.3.1 Python/2.4.4 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at svn.madwifi.org Port 80

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> Not Found

The requested URL /madwifi/trunk/madwifi-ng was not found on this server.
Apache/2.2.3 (Debian) DAV/2 SVN/1.4.2 mod_python/3.3.1 Python/2.4.4 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at svn.madwifi.org Port 80

did you copy my command exactly as I posted. because I noticed you put 

> The requested URL /madwifi/trunk/madwifi-ngAs i mentioned before there is a space between trunk/ and madwifi-ng. 


This command: 

```
sudo svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng
```

This makes a folder called madwifi-ng, and puts all the files in that folder labled "madwifi-ng". Thats why there is a space between trunk/ and madwifi-ng.

---

### Post by germanix on 2008-10-01
The &#8220;ath_pci" at the end of the file. Should this include the " " or only  ath_ pci without the "" ""
sorry to ask but maybe it is important

---

### Post by germanix on 2008-10-01
sudo echo ath_pci >> /etc/modules

This command did not work
jac@jac-laptop:~/madwifi-ng$ sudo echo ath_pci >> /etc/modules
bash: /etc/modules: Permission denied
the command:
sudo gedit /etc/modules and add &#8220;ath_pci&#8221; to the end of the file.

Save and close.
did work.
I am still not sure if I added the  &#8220;ath_pci&#8221; correctly. I did not use the " "

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> sudo echo ath_pci >> /etc/modules

This command did not work
jac@jac-laptop:~/madwifi-ng$ sudo echo ath_pci >> /etc/modules
bash: /etc/modules: Permission denied
the command:
sudo gedit /etc/modules and add “ath_pci” to the end of the file.

Save and close.
did work.
I am still not sure if I added the  “ath_pci” correctly. I did not use the " "

You added it right. You added it without the quotation marks right?

 Sorry about that, I should have stated not to put it in with the quotes. ill modify the guide now.

Have you already rebooted? Did it work?

Thanks

---

### Post by iponeverything on 2008-10-01
you didn't need the quotes.

echoing a string where you need to preserve a space you do.

---

### Post by germanix on 2008-10-01
I have now rebooted and an sorry to say that nothing have changed. Still no WIFI at all.

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> I have now rebooted and an sorry to say that nothing have changed. Still no WIFI at all.

OK, lets do some digging here.

run this and please post the output:

```
dmesg
```

also when you right click on the network manager icon what shows up?

Thanks

---

### Post by Nxion on 2008-10-01
> **iponeverything said:**
> you didn't need the quotes.

echoing a string where you need to preserve a space you do.

Thanks :) ill remember that for the future.

---

### Post by germanix on 2008-10-01
So I now do have WIFI. 
I used the following commands:
gksu gedit /etc/network/interfaces
and got this answer:
auto lo
iface lo inet loopback
i saved and closed the file.
I then gave the command:
sudo /etc/init.d/networking restart
I then rebooted
when i then clicked on the icon it showed me my wireless connection and all I then neededwas to connect.
I thank you very much for your help. I could not have done it without your help.
have a nice day and may the force be with you.

---

### Post by Nxion on 2008-10-01
> **germanix said:**
> So I now do have WIFI. 
I used the following commands:
gksu gedit /etc/network/interfaces
and got this answer:
auto lo
iface lo inet loopback
i saved and closed the file.
I then gave the command:
sudo /etc/init.d/networking restart
I then rebooted
when i then clicked on the icon it showed me my wireless connection and all I then neededwas to connect.
I thank you very much for your help. I could not have done it without your help.
have a nice day and may the force be with you.

I'm glad that it is working for you :) Enjoy the ability to roam about without wires!!

Cheers!!

---

