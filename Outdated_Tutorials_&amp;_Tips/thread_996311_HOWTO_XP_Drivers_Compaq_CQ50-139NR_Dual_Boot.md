---
title: "HOWTO: XP Drivers Compaq CQ50-139NR Dual Boot"
date: 2008-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by lkraemer on 2008-11-28
If you purchased a CQ50, and want to Dual Boot Windows XP and Ubuntu you
will need all the XP Drivers during the XP install.

Audio drivers:
--------------
First install Microsoft Universal Audio Architecture (UAA) Bus Driver for High Definition Audio drivers:

[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33461.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33461.exe)

** Installation Instructions:

1. Download the Softpaq .EXE file to a directory on your hard drive.
2. Execute the downloaded file and follow the on-screen instructions.
3. Restart the notebook when the installation is complete.

Install the Sound Driver: Conexant SmartAudio 221:

[http://www.mediafire.com/?dg0cmmkm4y4](http://www.mediafire.com/?dg0cmmkm4y4)

1. Click on Start and select Run. Now type devmgmt.msc and press enter.
2. Right click on "Audio device on High Definition Audio Bus" and click Update driver.
3. Select "Install from a list or specific location"
4. Click Next. Then select "Don't search, I will choose the driver to install"
5. Click Next and then select "Sound, video and game controller" from the list.
6. Click Next and then click Have Disk.
7. Click and browse to the unzipped folder and choose "WiSVHe5.inf".

            NOTE:  The URL(s) above will take you to a non HP Web site.  HP does
            not control and is not responsible for information outside
            of the HP Web site.

Video driver:
-------------

Download the driver from the following URL:

[http://www.nvidia.com/object/winxp_175.19_whql.html](http://www.nvidia.com/object/winxp_175.19_whql.html)

      NOTE: The URL above will take you to a non HP Web site. HP does
      not control and is not responsible for information outside
      of the HP Web site.


Mobile Intel 4 Series Express Chipset:
--------------------------------------

[http://downloadcenter.intel.com/download.aspx?url=/16944/a08/win2k_xp14363.exe&agr=N&ProductID=2991&DwnldId=16944&strOSs=All&OSFullName=All+Operating+Systems&lang=eng](http://downloadcenter.intel.com/download.aspx?url=/16944/a08/win2k_xp14363.exe&agr=N&ProductID=2991&DwnldId=16944&strOSs=All&OSFullName=All+Operating+Systems&lang=eng)

     NOTE: The URL above will take you to a non HP Web site. HP does
      not control and is not responsible for information outside
      of the HP Web site.


Synaptics Touchpad:
-------------------

[ftp://ftp.hp.com/pub/softpaq/sp37001-37500/sp37065.exe](ftp://ftp.hp.com/pub/softpaq/sp37001-37500/sp37065.exe)

HP Quick Launch Buttons:
------------------------

[ftp://ftp.hp.com/pub/softpaq/sp38001-38500/sp38171.exe](ftp://ftp.hp.com/pub/softpaq/sp38001-38500/sp38171.exe)

Broadcom Wireless LAN Driver:
----------------------------

[ftp://ftp.hp.com/pub/softpaq/sp32001-32500/sp32156.exe](ftp://ftp.hp.com/pub/softpaq/sp32001-32500/sp32156.exe)

or

Intel Wireless LAN Drive:
-----------------------------

[ftp://ftp.hp.com/pub/softpaq/sp32001-32500/sp32204.exe](ftp://ftp.hp.com/pub/softpaq/sp32001-32500/sp32204.exe)

or

Your Notebook may use Atheros WLAN device drivers, I am providing you the Atheros LAN drivers,
which are compatible to your Notebook.

Please download the Atheros WLAN device drivers  from the below ftp link;

[ftp://ftp.hp.com/pub/softpaq/sp39001-39500/sp39403.exe](ftp://ftp.hp.com/pub/softpaq/sp39001-39500/sp39403.exe)
Installation Instructions

1. Download the SoftPaq .EXE file to a directory on your hard drive.
2. Execute the downloaded file and follow the on-screen instructions


Realtek RTL8101 Family PCI-E Fast Ethernet NIC:
----------------------------------------------

[ftp://ftp.hp.com/pub/softpaq/sp38001-38500/sp38329.exe](ftp://ftp.hp.com/pub/softpaq/sp38001-38500/sp38329.exe)

Conexant HDAUDIO Soft Data Fax Modem with SmartCP Driver:
--------------------------------------------------------

[ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33839.exe](ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33839.exe)

Installation Instructions

1. Download the SoftPaq .EXE file to a directory on your hard drive.
2. Execute the downloaded file and follow the on-screen instructions.


Reference for installing Ubuntu ver 8.04 LTS:
[http://ubuntuforums.org/showthread.php?t=988691](http://ubuntuforums.org/showthread.php?t=988691)

lkraemer

---

### Post by fedex1993 on 2008-11-29
Needs to be moved to the how to section.

---

