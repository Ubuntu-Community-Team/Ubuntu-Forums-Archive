---
title: "Getting the internal modem to work on the Acer 5570"
date: 2007-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by alxjl on 2007-05-29
After quite some time getting the modem on my Acer 5570 to work here's what i did,

```
lspci
```

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

Download the scanModem Tool from [http://132.68.73.235/linmodems/index.html#scanModem]("http://132.68.73.235/linmodems/index.html#scanModem")

```
gunzip scanModem.gz
```

then change permissions,

```
chmod +x scanModem
```

Run the utlity,

```
sudo ./scanModem
```

ModemData.txt should read the following (edited text),

```
8086:27d8 is a High Definition Audio card, possibly hosting a soft modem.
HDAmodemChip=0x11c13026
 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
    Subsystem PCI_id  1025:0110 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 11c1, an AgereSystems type.
                        The HDA card softmodem chip is 0x11c13026
An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

```

Download driver from [http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD-1.0.13.tar.gz]("http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD-1.0.13.tar.gz")

Unpack and enter the SLMODEMD-1.0.13 directory

```
sudo chmod a+x slmodemd
```

From the same directory copy the slmodemd file to

```
sudo cp slmodemd /usr/sbin/
```

This completes slmodemd installation. To check for duplicate slmodemd files,

```
find /usr -name slmodemd 
```

It should only report the newly copied slmodemd.Should another older slmodemd copy be found rename it to slmodemd.old

Make sure you have kppp installed

```
sudo apt-get install kppp
```

Open a Terminal, Use the CountryList.txt file on your SLMODEMD-1.0.13 folder to check for your listing


```
sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6 

```

The following txt should appear,

```
SmartLink Soft Modem: version 2.9.11 May  5 2007 01:31:04
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
```

Run kppp from your applications, internet tab or,

```
kppp
```

IMPORTANT: Don't close the terminal while you run kppp otherwise your modem won't be detected

go to "configure"

go to "Modems"

create "New"

enter details on "Device" tab "Modem name", Modem device (in this case /dev/ttySL0), and connection speed

go to "Modem" to test

click on "Query Modem"

ATI query results should display the following:

```
ATI: SmartLink Soft Modem
ATI 1:SmartLink Soft Modem, 2.9.11  Smart Link Ltd.
ATI 2:SmartLink Soft Modem, 2.9.11  Smart Link Ltd.
ATI 3:hw:0,6  alsa modem driver
ATI 4:s00=000 s01=000 s02=043 s03=013 s04=010 s05=008 s06=002 s07=060   s08=002 s09=006 s10=007 s11=100 s12=050 s13=000 s14=001 s15=001   s16=001 s17=000 s18=000 s19=000 s20=000 s21=000 s22=000 s23=000
ATI 5:Stored Profile 0:
ATI 6:Stored Profile 1:
ATI 7:Country:YOUR_COUNTRY
```

Enter your other ISP details and you're good to go!

---

### Post by dgdubya on 2007-06-03
Thanks for the directions I'm going to try this on some other PCs using soft modems. I appreciate the work you've save me.:p

---

