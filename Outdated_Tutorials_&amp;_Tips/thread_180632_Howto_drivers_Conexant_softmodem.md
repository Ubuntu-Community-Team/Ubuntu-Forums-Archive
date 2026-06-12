---
title: "Howto drivers Conexant softmodem"
date: 2006-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-05-22
Hi,
   Here is a short howto on compiling the drivers for a Conexant softmodem/winmodem/linmodem. It works in dapper, but should also work in the other versions. Hope it helps someone. It does not have the 14400 speed limitation.
[U]Howto get Conexant modem to work in dapper
[/U]
Rafael Espíndola ported the latest Conexant open source version to 2.6.x kernels. AlexandreOttoStrube packaged it to Ubuntu Breezy using kernel 2.6.12-9 The.deb file will not work on any other kernel unless you compile it yourself as below, the files can be downloaded from  [http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/) or [ftp://ftp.wizzy.com/pub/wizzy/conexant/](ftp://ftp.wizzy.com/pub/wizzy/conexant/) courtesy AndyRabagliati 
Determine the make and model of your modem, by looking at the chipset. If it shows HSF and the number CX11252 on the chip you have a softmodem/winmodem/linmodem and this driver should work. You can also install it on a Windows pc and do a modem query and if it shows PCI/VEN_14F1&DEV2F00 then you know it should work.
Download the file conexant_192-1ubuntu-1.tar.gz from the above website. This is the old open source and not the one you have to buy for for linux and get free for Windows!.
This software supports the Conexant HSF 56k HSFi Modem (pci id 14f1:2f00), and was not tested with other models.

1.Put the downloaded file  conexant_192-1ubuntu-1.tar.gz on your Desktop and right click &#8220;Extract to here&#8221; and a folder &#8220;conexant&#8221; will be created on your Desktop.
2.Read the txt files in the folder for more info.
3.Open the file /conexant/modules/makefile by right clicking and select edit in root and find the 2 lines that start with # KERNELDIR? = /lib/modules..... etc. and KERNELDIR?= /usr/src... etc Remove the comment # in the first line and insert comment # on second line and save changes.
4.Now open the /conexant/makefile in the same way and find the commented line # rm -rf $$DESTDIR/dev/ttySHFS0. Remove the comments from the mentioned line and the following 3 lines up to &#8220;update modules&#8221; and save changes
5.Now ensure that you have all the packages installed to compile the drivers. Use Synaptic and install or check that, build-essential, linux-headers-ARCH, fakeroot is installed, ARCH is the result you get if typing uname-r in a terminal &#8211; version of kernel.
6.cd Desktop/conexant
7.make
8.sudo make install
9.sudo modprobe hsfserial     (you should get no result reports if OK)
10.dmesg | grep hsfserial         ( you should get no result reports if OK)
11.The /dev/ttySHFS0 is created for the modem
12.To test, use the query modem on Kppp

To remove the installation:
rm /dev/ttySHFS0
rm -r /etc/hsf
rm /lib/modules/ARCH/misc/hsf*
rm /etc/modutils/hsf

Note: Please note that to actually get your browser working means that your network settings must be in order as well and your PC is not connected to a lan for starters. If your PC hangs or slows after an unsuccessfull dialup disconnect, please reboot to get the modem to reset properly before attempting to dialup again. The modem is a bit finicky and may require a boot after installing. If anyone works out the settings for the country code changes and the proper connection speed indication or has anything to add please let us have so we can update this for our laptop friends.

---

### Post by habib_seif on 2006-05-28
Thank you so much Matchless for your HOWTO,

I performed the steps above and all of them worked fine. Finally /dev/ttySHSF0 was created but when I use it via wvdial for connecting to internet, I encounter to this problem:

--> WvDial: Internet dialer version 1.55
--> Cannot open /dev/ttySHSF0: No such device or address
--> Cannot open /dev/ttySHSF0: No such device or address
--> Cannot open /dev/ttySHSF0: No such device or address

I guess the driver is'nt for my chipset. (My computer is Dell inspiron 6000 laptop with a conexant modem) What's your idea?

and do you have any suggestion?

Actually, all of my hardware is detected by Ubuntu unless the modem :-( If I can cope it, it will be great !!!

Cheers,
Habib

---

### Post by Matchless on 2006-06-03
Hi,
    Check under the dev list to see if you can see /dev/ttySHFS0.
If not then something went wrong. Have you been able to confirm that your modem is an HSF and not a HCF? Only the HSF will work and must be pci id 14f1:2f00. A bit of a long way to check a laptop will be to install XP and then install the modem drivers and use modem diagnostics and it may show the model If you have the correct modem then the process should work.
Good luck

---

### Post by golfbuf on 2006-06-03
[QUOTE=Matchless]Hi,
.........
is an HSF and not a HCF? Only the HSF will work and must be pci id 14f1:2f00. A bit 
..............
Good luck[/QUOTE]

If you check the DialupModemHOWTO in the wiki, you'll see it's now possible to extend this to other pci id's.  I'm successfully using it on 14f1:2013 on dapper.  There's a new script 'modem-hsfpci.tar.bz2' to download to create a package that can be built for other kernels and pci ids.

regards,

---

### Post by Matchless on 2006-06-03
Golfbuf,
           Excellent work. I will test during the week when I have done a clean install of dapper. This should make life a lot easier for some.

If you are the script author, then I would like to know if someone can write a script that will copy all the installed files from the cache to a local folder and create the packages.gz file. It should also have a option to only copy the latest version, such as after an update. The idea is to keep a local repository of files downloaded due to having a dialup and linited bandwidth for repeat downloads etc. I have no idea how to write scripts myself/

---

### Post by habib_seif on 2006-06-04
[QUOTE=golfbuf]If you check the DialupModemHOWTO in the wiki, you'll see it's now possible to extend this to other pci id's.  I'm successfully using it on 14f1:2013 on dapper.  There's a new script 'modem-hsfpci.tar.bz2' to download to create a package that can be built for other kernels and pci ids.

regards,[/QUOTE]

Thank you for your useful help...
I checked deviceID of my modem for setting it in modem-hsfpci conf file, it is 8086:266d, so I put a line in the configuration file and used /usr/bin/modem-hsfpci --install to install driver for it.(all of previous steps mentioned in HOWTO.txt of modem-hsfpci went perfectly)
But the command  /usr/bin/modem-hsfpci --install complained that "modprobe -v hsfserial" has a Segmentation fault and after that when I start the computer, Ubuntu freezes :-(
any suggestion?

---

### Post by Matchless on 2006-06-04
Habib_seif,
              Have a look at this post [http://www.ubuntuforums.org/showthread.php?t=128270](http://www.ubuntuforums.org/showthread.php?t=128270)
It seems as if you MAY have an Intel type and it MAY even work with the Smartlink drivers. These are on the repos as sl-modem. Otherwise you will have to carefully follow the post above
Good luck

---

### Post by habib_seif on 2006-06-04
[QUOTE=Matchless]Habib_seif,
              Have a look at this post [http://www.ubuntuforums.org/showthread.php?t=128270](http://www.ubuntuforums.org/showthread.php?t=128270)
It seems as if you MAY have an Intel type and it MAY even work with the Smartlink drivers. These are on the repos as sl-modem. Otherwise you will have to carefully follow the post above
Good luck[/QUOTE]

Hi again Mathless,

You were exactly right. my modem is Intel not Conexant, but Windows put me in this wrong road, because it shows Conexant in the device manager of control panel for the modem!!! but why???

Of course, I installed the driver for another ACTUAL Conexant modem with 14f1:2f00 and it works perfectly now. thank you so much, guys.

By the way, I can't get my modem to work with sl-modem-daemon yet. the modem says no dial tone in dialing time. I know this thread is for conexant not smlink and because of this I put the problem into another thread, but if you have an experience, please help me,
Cheers,
Habib

---

### Post by polo_step on 2006-06-05
[FONT="Courier New"]This is a very interesting thread!

Has anyone tested this with the "Sterling S20" modem?

Chip markings:

CONNEXANT
HSFi
CX11252-11
0407Y1RC
0408 TAIWAN

I recently picked one of these up free-after-rebate and found it sort of amusing that I would have been expected to pay TWENTY DOLLARS for a "licensed" Connexant Linux driver for this free modem.:rolleyes: 

Do these open source drivers listed above have any significant differences from the TWENTY DOLLAR drivers?

Thanks for any info on this.  Though I do not currently use dialup, I occasionally build parts computers for others and this would be useful to know. [/FONT]

---

### Post by habib_seif on 2006-06-05
Hi again friends,
I finally found the trick of my modem:
The 8086:266d id is not vendorID:deviceID of modem. it's just controller id.
The right id of such modem is 14f1:5423 and hence it is a conexant one. so I tried the free driver you adviced but unfortunately the driver doesn't support this conexant modem yet.
Do you know the activies about improving this driver to support my modem?
Cheers,
Habib

---

### Post by Matchless on 2006-06-06
Hi,
   I have posted a new Howto for smartlink and conexant. as soon as the moderator releases it you should be able to see. it has much more detail and you should be able to get your Conexant modem working by just adding your device number. i will add this to your other post with the details

---

### Post by sb73542 on 2006-06-09
Hello,

So glad to see this thread, it really irritates me to think about paying for a driver for a modem I already own.....

Anyone know what modem Dell Inspiron laptops usually have?  I'm getting an Inspiron 1300 (B130) and I'd like to know if it has the modem that works with the smartlink drivers.

Thanks!

---

### Post by Gyrotwister on 2006-06-15
Hi, just found this thread.  I have one of these conextant modems and am looking forward to the reading the new HowTo.  

Will it be posted in this thread or will it appear somewhere else?

---

### Post by adajar99 on 2006-06-16
Hello,

I hope that this will include instructions on how to get the build-essential and other files needed to compile using another computer with Linux or Windows.  Sometimes it is forgotten that we are trying to get the modem to connect to the internet, so as such, Synaptic/apt are not possible at this point in the machine we are working on.

Thanks!

---

### Post by Gyrotwister on 2006-06-16
After spending some more time finding my way around this web site, I’ve answered my own question.   
It’s going into the Wiki when moderators approve the content.  

Also found the yet to be approved instructions in another thread if anybody else is looking for it and can't wait.  
[http://ubuntuforums.org/showthread.php?t=189009](http://ubuntuforums.org/showthread.php?t=189009)

---

### Post by Matchless on 2006-06-16
Hi,
    Here it is [http://ubuntuforums.org/showthread.php?t=190728&highlight=conexant](http://ubuntuforums.org/showthread.php?t=190728&highlight=conexant)

---

### Post by golfbuf on 2006-06-16
[QUOTE=Matchless]If you are the script author, then I would like to know if someone can write a script that will copy all the installed files from the cache to a local folder and create the packages.gz file. It should also have a option to only copy the latest version, such as after an update. The idea is to keep a local repository of files downloaded due to having a dialup and linited bandwidth for repeat downloads etc. I have no idea how to write scripts myself/[/QUOTE]

... you asked for it, [http://ubuntuforums.org/showthread.php?p=1142208#post1142208](http://ubuntuforums.org/showthread.php?p=1142208#post1142208)

This works for me, but /bin/bash can be a bear if some editing causes a syntax error .. use them only if you can bear occasional frustration.

regards,

---

### Post by Matchless on 2006-06-16
Golfbuf,
             Thanks! Excellent i will try all of them this week. I have also been given an HCF Conexant modem and will try and see if it can be used with the old drivers as well during the week.
Thanks again.

---

### Post by leeyee on 2006-06-20
Hi guys,
I'm glad to find such a thread here, it's my 3 months seeking for! However, I think my box is a more general one, in which the softmodem is

      0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

and the Vendor/Device number is 8086:24c6. It's the embedded softmodem in my laptop ASUS M2400C, I think this modem is very common on laptop motherboards.
After I ran the scanModem and was told this controller is capable of supporting from "Conxant, Smartlink, Intel, Broadcom etc". Now please you guys help me where can I find an exact HOWTO for this model softmodem, or just use a smartlink driver mentioned here? I DO NOT want the linuxant driver, it's ugly and slow!!!

---

### Post by Matchless on 2006-06-24
Hi,
   It seems as if you modem is an Intel AC-link Controller (ICH) and could be an Angere AC97 modem. This link should put you on the way as it also seems as if the smartlink drivers and daemon should work [http://linmodems.technion.ac.il/travelmate800.ubuntu.slmodem.html](http://linmodems.technion.ac.il/travelmate800.ubuntu.slmodem.html)
Let us know.

---

### Post by habib_seif on 2006-06-29
[QUOTE=Matchless]Hi,
it has much more detail and you should be able to get your Conexant modem working by just adding your device number. i will add this to your other post with the details[/QUOTE]

Hi dear friends,
First of all, thanks for your useful helps. I can easily make most of coexant modems to work by using [ftp://ftp.wizzy.com/pub/wizzy/conexant/](ftp://ftp.wizzy.com/pub/wizzy/conexant/) driver and modem-hsfpci.tar.bz2 patch, these days.
But as I mentioned before my own conexant modem id is : 14f1:5423, and there is no such id in modem-hsfpci.tar.bz2 configuration file. Even, when I add a line with this id in configuration file and install modem-hsfpci, /dev/modem insn't created.
This means my modem isn't supported by this driver? Can I change the source code of the driver or the patch to support 14f1:5423 conexant modems?
Again, thank you so much,
Habib

---

### Post by leeyee on 2006-06-29
Okay, thanks for your guys's replies! I think my modem is still a ConXanT one, and I got it worked for me by installing the hsfmodem from linuxant.com. However, it has a 14.4kbps limitation, I'm wondering if I can install an opensource version, and I will have a try!
Thank you guys!
Here is the output of the scanModem running on my system, any idea?
```

The kernel was assembled with compiler:  4.0.3
 with current System compiler GCC=4.0.3
-------------
 Found make utility.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-headers supporting compiling are resident: 

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at  0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:24c6   Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
  SubSystem 1043:1826  ASUSTeK Computer Inc.: Unknown device 1826
	Flags: bus master, medium devsel, latency 0, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ohci1394, Intel 82801DB-ICH4, hsfmc97ich, yenta, yenta, fglrx
      XT-PIC  ide1

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 1043:1826 debian_version 2.6.15-23-686  4.0.3 4.0.3    i686
              From records, 1043:1826 has soft modem codec type CXT
 The hsfmodem drivers from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) are the ONLY support of ConeXanT codec modems under Linux!!

       
 The controller: 8086:24c6 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)1DB ICH4 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Broadcom
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers

  Driver snd-intel8x0m  may enable codec acquisition 

```

---

### Post by hokutonoken on 2007-02-27
Link to a more recent thread:

[http://www.ubuntuforums.org/showthread.php?t=190728](http://www.ubuntuforums.org/showthread.php?t=190728)

Hint: read until the end of the thread (at least the latest posts) before beginning installation. There are some important add-ons to the original howto.

The latest Ubuntu version compatible with Conexant free drivers is 6.06 Dapper.
There isn't any way of installing free modules on later Ubuntu versions, yet (as of February 2007)

---

### Post by Topinambur on 2007-05-15
First of all guys, thanks for the awesome thread. My modem has a vendor ID 8086:2486, which gives me some hope it may work. Now to my cup of problems...

I am trying to install the Conexant driver in Feisty (kernel 2.6.20-15) as suggested by Matchless. Apparently, some of the headers, such as linux/config.h have been depreciated in this kernel and the compilation gives me a buch of errors starting with
"/usr/share/conexant-192-1ubuntu/modules/osspec/include/oscompat.h:57:26: error: linux/config.h: No such file or directory"

Creating a symbolic link "config.h" pointing to "autoconf.h" in /usr/src/linux-headers-2.6.20-15/include/linux as suggested by some other threads was of no avail and gave me even more errors such as bunch of undefined variables and functions, mismatch of the number of passing arguments and so forth.
Commenting #include linux/config.h lines in the source code didn't do any good either.

May I ask for any help here?

---

### Post by reza_reza_reza on 2007-10-21
Hi, thanks about this guidance.

when I run step 7 , recive this errors :

[IMG]http://i23.tinypic.com/289x07p.png[/IMG]

[IMG]http://i20.tinypic.com/xo31gp.png[/IMG]

[IMG]http://i23.tinypic.com/n6f77m.png[/IMG]


how can I correct this error?

Special thanks whom help me.

---

### Post by IvanQ on 2009-04-20
A more recent thread: 

[http://ubuntuforums.org/showthread.php?t=1015673](http://ubuntuforums.org/showthread.php?t=1015673)

and an updated wiki:

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

---

