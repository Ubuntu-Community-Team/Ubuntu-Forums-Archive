---
title: "Sound output issue, as well as mic"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Etheredge on 2008-05-22
Im having an issue with the output sound volume from my laptop. Im not exactly sure what but it seems like since the change from windows to linux the sound has significantly decreased in volume.

Also since the change my onboard mic fails to work. Although the webcam is still working just fine.

Any help would be much appreciated 

My laptop is ***TOS-SAT-A205-S4777***

Any help would be appreciated.

---

### Post by iaculallad on 2008-05-22
On your terminal, issue this command and post the whatever is displayed.

lspci

---

### Post by Inxsible on 2008-05-22
Does this happen in all apps or just one app?

Type in ```
alsamixer
```in a terminal and max all the volume levels there. See if that works for you.

---

### Post by Etheredge on 2008-05-22
> **iaculallad said:**
> On your terminal, issue this command and post the whatever is displayed.

lspci

etheredge@etheredge-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by Etheredge on 2008-05-22
> **Inxsible said:**
> Does this happen in all apps or just one app?

Type in ```
alsamixer
```in a terminal and max all the volume levels there. See if that works for you.

Thank you that seemed to work for the volume. Now to test out the mic

Damn i wish i could learn all this heh

---

### Post by Etheredge on 2008-05-22
hmmm so far no mic lets see.....

---

### Post by iaculallad on 2008-05-22
> **Etheredge said:**
> hmmm so far no mic lets see.....

try this one:

**sudo /etc/init.d/alsa-utils restart**

or if that doesnt work, try this on your terminal (update the driver):

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)

tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install

---

### Post by Etheredge on 2008-05-22
> **iaculallad said:**
> try this one:

**sudo /etc/init.d/alsa-utils restart**

or if that doesnt work, try this on your terminal (update the driver):

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)

tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install


etheredge@etheredge-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
--22:15:36--  [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
           => `drive...1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.14.tar.bz2 ... 
**No such file `drive...1.0.14.tar.bz2'.**

etheredge@etheredge-laptop:~$

---

### Post by iaculallad on 2008-05-22
Did you try issuing this command?

sudo /etc/init.d/alsa-utils restart

---

### Post by Etheredge on 2008-05-22
yes i did 

it seemed to go through fine but didnt fix the issue

etheredge@etheredge-laptop:~$ sudo /etc/init.d/alsa-utils restart
[sudo] password for etheredge: 
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
etheredge@etheredge-laptop:~$

---

### Post by iaculallad on 2008-05-22
> **Etheredge said:**
> yes i did 

it seemed to go through fine but didnt fix the issue

etheredge@etheredge-laptop:~$ sudo /etc/init.d/alsa-utils restart
[sudo] password for etheredge: 
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
etheredge@etheredge-laptop:~$

Retry getting the updated driver with this:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)
tar -xjf alsa-driver-1.0.14rc3.tar.bz2
cd alsa-driver-1.0.14rc3
./configure
make
make install

---

### Post by Etheredge on 2008-05-22
> **iaculallad said:**
> Retry getting the updated driver with this:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2)
tar -xjf alsa-driver-1.0.14rc3.tar.bz2
cd alsa-driver-1.0.14rc3
./configure
make
make install


etheredge@etheredge-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/drive....14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....14rc3.tar.bz2)
--03:36:02--  [ftp://ftp.alsa-project.org/pub/drive....14rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....14rc3.tar.bz2)
           => `drive....14rc3.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive....14rc3.tar.bz2 ... 
**No such file `drive....14rc3.tar.bz2'.**

---

### Post by Etheredge on 2008-05-22
still nothing

---

