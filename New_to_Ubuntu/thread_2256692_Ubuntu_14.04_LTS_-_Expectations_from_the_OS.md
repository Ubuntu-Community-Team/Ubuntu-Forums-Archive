---
title: "Ubuntu 14.04 LTS - Expectations from the OS"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by magpies89 on 2014-12-14
G'day from Australia,

So basically I am sick of using Windows based operating system and thus decided to migrate to Ubuntu which sounds promising and following are my expectations:

1 To be able to use OS for general internet browsing

2 Use Citrix via Mozilla Firefox to access work

3 Play some basic software on wine such as 'Reckon Personal Finance Manager'. I have checked this software on the website and it is listed on the wine list.

So in order to achieve the most basic task of doing internet browsing requires me to connect internet wireless. I have been using following link to work this out: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

However, in order to install the driver through terminal requires me to download 'ndiswrapper'. Now I was expecting fresh installation of OS would come up with general software packages such as ndiswrapper but obviously such utility is missing.

Would you guys be able to recommend how to download utilities (I am able to download through my partner's laptop - windows 7 based and transfer through usb). One guy from above listed thread commented to use following: "Download the respective DEB files from [http://packages.ubuntu.com]("http://packages.ubuntu.com/") (except "build-essential"), save them in "Downloads" and install them via:"

I do not understand where to download ndiswrapper using above gray highlighted link and also codes which needs to be applied to new OS when installing such utility.

I would highly appreciate if you guys can put in some recommendations/reference points for me to work out the solutions.

Cheers

Abs

---

### Post by grahammechanical on 2014-12-14
Hi,

I have never had any problems using WiFi in Ubuntu. So, if you have the same wireless adapter as me, then it you will be able to set up a wireless connection to your router without needing to download anything.

Question is, what hardware do you have? You do not tell us, Mate.

Better to ask: Is anyone using such and such a machine? Did you have any problems getting Ubuntu to work on it?

Regards

---

### Post by magpies89 on 2014-12-14
'Grahammechanical'

Thanks so much for your reply. I did forgot to mention the hardware so basically it’s a desktop (would you like typical full specs?) and I am trying to connect internet with Net gear WNA3100 USB adapter. Normally I was able to download this hardware through a retail CD and USB would be recognised in the system in windows based OS.

But given the nature of OS same installation method cannot be used. As previously mentioned, I have tried to use following link: [http://ubuntuforums.org/showthread.php?t=2221251&page=2](http://ubuntuforums.org/showthread.php?t=2221251&page=2)

And I am getting the same results when I type 'lsusb'. However, when I use the code in relevance with ndiswrapper. Ubuntu 14.04 does not seem to recognise the command. Thus, I thought following was required and in order to get ndiswrapper running:

Download the respective DEB files from [http://packages.ubuntu.com]("http://packages.ubuntu.com/") (except "build-essential"), save them in "Downloads" and install them via:
Code:
sudo dpkg -i ~/Downloads/*.deb

When I go to the website as mentioned above I do following: [trusty]("http://packages.ubuntu.com/trusty/") (14.04LTS) > [Network]("http://packages.ubuntu.com/trusty/net/") > [ndisgtk]("http://packages.ubuntu.com/trusty/net/ndisgtk") (0.8.5-1ubuntu1) [**universe**] (Do I just download this for ndiswrapper to be installed?)
When I download file from internet [[ndisgtk_0.8.5.orig.tar.gz]]("http://archive.ubuntu.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.8.5.orig.tar.gz"); how am I supposed to install it in OS? Shouldn't file end up with .deb to be able to use above command "sudo dpkg -i ~/Downloads/*.deb"

Hopefully I haven't' confused you, please let me know if you can help anyways.

Cheers

Abs

---

### Post by ian-weisser on 2014-12-14
When you originally installed Ubuntu, was the installer able to use wireless?
(Feel free to boot the installer if you still have it handy. Select 'Try Ubuntu')

Please open a terminal, and enter the command 'lspci'.
Look for your wireless hardware among the output.
When you find it, please tell us the *entire*, *exact* output line for your wireless hardware.

For example, mine looks like:
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

---

### Post by Mark Phelps on 2014-12-15
> Play some basic software on wine such as 'Reckon Personal Finance Manager'. I have checked this software on the website and it is listed on the wine list.Well ... I checked the WineHQ website and this is NOT listed.  Which means, there is no record of it having working in Wine; thus, you'll be on your own getting it to work.

---

### Post by buzzingrobot on 2014-12-15
It's unclear to me if you've installed Ubuntu.  But, if you boot and run a live image (the "Try" option) and if wireless works there, it will work on an actual install. If it does not work, and you want to try the ndiswrapper approach, it's available in the Ubuntu repos ([http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=trusty&section=all)) and installable with a tool like Synaptic or via the command line (sudo apt-get install <name-of-package>) that will download and install the package.  (To manually download, click on the link in red beneath the package name, then the red link under "Architecture -- will either be "All" or  "amd64" or "i386" for 64-bit or 32-bit respectivelly -- and that opens a list of links to mirrors to download the actual file.  Packages in the 'deb' format are intended for installation -- they contain scripts, etc. to put all the files in the right places, etc., when the appropriate tool, e.g., Synaptic or apt-get, is used -- but the files in them can be extracted by right clicking in the file manage and selecting the "Extract Here" option.)

Of course, you'll temporarily need to use an wired ethernet if you've already installec Ubuntu, or download the packeges on another machine for transfer and installation on your system.

---

### Post by magpies89 on 2014-12-15
Thanks ian-weisser for your reply. I did type lspci and I have stated the results below:

abhishek@Transformer-P55-UD3:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cypress HDMI Audio [Radeon HD 5800 Series]
02:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

Any clue? Please let me know.

Cheers

Abs

---

### Post by magpies89 on 2014-12-15
> **Mark Phelps said:**
> Well ... I checked the Wine HQ website and this is NOT listed.  Which means, there is no record of it having working in Wine; thus, you'll be on your own getting it to work.

Thanks Mark Phelps for bringing this to my attention. I believe my actual version wasn't listed in my previous post - apologies. I will need to find the retail CD cover and post the exact title. I am bit worried now.

Thanks for your help.

Cheers

Abs

---

### Post by ian-weisser on 2014-12-15
> **magpies89 said:**
> 03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)

Well, happily your wired ethernet is [certified]("http://www.ubuntu.com/certification/catalog/make/Realtek%20Semiconductor%20Co.,%20Ltd./") for use with Ubuntu.

I don't see your wireless on the lspci list either.
Next, open a terminal, and try 'lsusb'

---

### Post by DuckHook on 2014-12-16
> **magpies89 said:**
> Thanks Mark Phelps for bringing this to my attention. I believe my actual version wasn't listed in my previous post - apologies. I will need to find the retail CD cover and post the exact title. I am bit worried now.Mark was actually being very judicious in his words. I am positive that it won't work at all. Old oddball software tend to choke on WINE (...just re-scanned that. Awful play on metaphor was not intended. Really). Hopefully, my personal experience may be of some assistance:

For a long time, I ran Windows in a VM just so I could run Quickbooks. This nasty piece of jailware won't run in WINE, and being an accounting package, it was critical to me, so all of the extra maintenance, inefficiency and bother of supporting Windows was made necessary by this one legacy program.

About three years ago, I had had enough of this. I devoted a weekend to opening a set of books in GnuCash, transferred all balances from Quickbooks to GnuCash, and ran the two in tandem for about two months. After getting the hang of GnuCash and gaining confidence in it, I dropped Quickbooks altogether and haven't looked back since. GnuCash does everything differently and takes getting used to, but come on... accounting is accounting. It's standardized pretty well throughout the world and hasn't changed much since Pacioli perfected it for the Medici. I doubt that you will find GnuCash too tough to adopt.

If you have the horsepower, then for many Windows apps, running Windows in a VM is a better solution than WINE. At least, you should take heart from having another alternative. However, in the long run, the objective is not to stretch out your dependency on some Windows program, but to wean yourself off of it and make the full switch to Linux. Malingering is not pretty to watch in any OS.

---

### Post by magpies89 on 2014-12-16
> **ian-weisser said:**
> Well, happily your wired ethernet is [certified]("http://www.ubuntu.com/certification/catalog/make/Realtek%20Semiconductor%20Co.,%20Ltd./") for use with Ubuntu.

I don't see your wireless on the lspci list either.
Next, open a terminal, and try 'lsusb'

_**Results from lsusb:**_

abhishek@Transformer-P55-UD3:~$ lsusb
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abhishek@Transformer-P55-UD3:~$

---

### Post by magpies89 on 2014-12-16
> **DuckHook said:**
> Mark was actually being very judicious in his words. I am positive that it won't work at all. Old oddball software tend to choke on WINE (...just re-scanned that. Awful play on metaphor was not intended. Really). Hopefully, my personal experience may be of some assistance:

For a long time, I ran Windows in a VM just so I could run Quickbooks. This nasty piece of jailware won't run in WINE, and being an accounting package, it was critical to me, so all of the extra maintenance, inefficiency and bother of supporting Windows was made necessary by this one legacy program.

About three years ago, I had had enough of this. I devoted a weekend to opening a set of books in GnuCash, transferred all balances from Quickbooks to GnuCash, and ran the two in tandem for about two months. After getting the hang of GnuCash and gaining confidence in it, I dropped Quickbooks altogether and haven't looked back since. GnuCash does everything differently and takes getting used to, but come on... accounting is accounting. It's standardized pretty well throughout the world and hasn't changed much since Pacioli perfected it for the Medici. I doubt that you will find GnuCash too tough to adopt.

If you have the horsepower, then for many Windows apps, running Windows in a VM is a better solution than WINE. At least, you should take heart from having another alternative. However, in the long run, the objective is not to stretch out your dependency on some Windows program, but to wean yourself off of it and make the full switch to Linux. Malingering is not pretty to watch in any OS.


Thanks DuckHook for your reply. It kind of makes sense in relation to what you are saying. If I were to install VMware does it come up with windows installation or would that be a new can of worms? Is running a vmware on Ubuntu 14.04 costs a subscription? Well in that case you are right, getting used to software which work in OS is probably the best way to go about it. Which software from Linux be closely aligned with Quicken Personal Finance 2012 (Australian version)? I know you have mentioned Gnucash, what about Mint? Would I be able to import my .QIF file to this new software? Last thing I want to do is do it over again!!!

---

### Post by magpies89 on 2014-12-16
> **ian-weisser said:**
> Well, happily your wired ethernet is [certified]("http://www.ubuntu.com/certification/catalog/make/Realtek%20Semiconductor%20Co.,%20Ltd./") for use with Ubuntu.

I don't see your wireless on the lspci list either.
Next, open a terminal, and try 'lsusb'

After trying 'lsusb' This is where I am at:

I have used the following web link: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

And Did following 2 commands after trying to install individual *.deb packages from following web link: [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=trusty&section=all)

*abhishek@Transformer-P55-UD3:~$ sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf*
*[sudo] password for abhishek: *
*driver bcmn43xx64 is already installed*

*abhishek@Transformer-P55-UD3:~$ sudo modprobe -v ndiswrapper*
*modprobe: FATAL: Module ndiswrapper not found.*
*abhishek@Transformer-P55-UD3:~$ *
*abhishek@Transformer-P55-UD3:~$ sudo ndiswrapper -ma*
*module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf*
*abhishek@Transformer-P55-UD3:~$ *
*abhishek@Transformer-P55-UD3:~$ dmesg | grep ndis*
*abhishek@Transformer-P55-UD3:~$ *
*abhishek@Transformer-P55-UD3:~$ lsmod*
*Module                  Size  Used by*
*nls_iso8859_1          12713  1 *
*usb_storage            62209  1 *
*bnep                   19624  2 *
*rfcomm                 69160  0 *
*bluetooth             391196  10 bnep,rfcomm*
*snd_hda_codec_hdmi     46254  1 *
*snd_hda_codec_realtek    61438  1 *
*gpio_ich               13476  0 *
*snd_hda_intel          52355  5 *
*snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel*
*coretemp               13435  0 *
*snd_hwdep              13602  1 snd_hda_codec*
*snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel*
*kvm_intel             143060  0 *
*snd_page_alloc         18710  2 snd_pcm,snd_hda_intel*
*snd_seq_midi           13324  0 *
*kvm                   451511  1 kvm_intel*
*snd_seq_midi_event     14899  1 snd_seq_midi*
*snd_rawmidi            30144  1 snd_seq_midi*
*snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi*
*serio_raw              13462  0 *
*i7core_edac            24122  0 *
*snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi*
*edac_core              62291  2 i7core_edac*
*lpc_ich                21080  0 *
*snd_timer              29482  2 snd_pcm,snd_seq*
*radeon               1522422  3 *
*ttm                    85115  1 radeon*
*drm_kms_helper         53081  1 radeon*
*snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi*
*mac_hid                13205  0 *
*drm                   303102  5 ttm,drm_kms_helper,radeon*
*parport_pc             32701  1 *
*soundcore              12680  1 snd*
*i2c_algo_bit           13413  1 radeon*
*ppdev                  17671  0 *
*lp                     17759  0 *
*parport                42348  3 lp,ppdev,parport_pc*
*pata_acpi              13038  0 *
*hid_generic            12548  0 *
*usbhid                 52570  0 *
*hid                   106148  2 hid_generic,usbhid*
*r8169                  67581  0 *
*mii                    13934  1 r8169*
*ahci                   25819  2 *
*libahci                32560  1 ahci*
*pata_jmicron           12758  0 *
*floppy                 69418  0 *
*abhishek@Transformer-P55-UD3:~$ *
*abhishek@Transformer-P55-UD3:~$ iwconfig*
*eth0      no wireless extensions.*

*lo        no wireless extensions.*

*abhishek@Transformer-P55-UD3:~$ *
*abhishek@Transformer-P55-UD3:~$ ndiswrapper -l*


I have tried to individually download .deb packages and following are the current status of the programs as per the screenshots attached:

[ATTACH=CONFIG]258644[/ATTACH][ATTACH=CONFIG]258645[/ATTACH][ATTACH=CONFIG]258646[/ATTACH][ATTACH=CONFIG]258647[/ATTACH]

So my feel is "ndiswrapper-source_1.59-2_all.deb" and "ndiswrapper-dkms_1.59-2_all' haven't been installed correctly and thus I can't seem to execute the command from WNA3100 link properly:

*sudo modprobe -v ndiswrapper*
*sudo ndiswrapper -ma*
*dmesg | grep ndis*
*lsmod*
*iwconfig*
*ndiswrapper -l #*

Please let me know if you guys have any ideas.

Cheers

Abhi

---

### Post by DuckHook on 2014-12-16
> **magpies89 said:**
> Thanks DuckHook for your reply. It kind of makes sense in relation to what you are saying. If I were to install VMware does it come up with windows installation or would that be a new can of worms? Is running a vmware on Ubuntu 14.04 costs a subscription? Well in that case you are right, getting used to software which work in OS is probably the best way to go about it. Which software from Linux be closely aligned with Quicken Personal Finance 2012 (Australian version)? I know you have mentioned Gnucash, what about Mint? Would I be able to import my .QIF file to this new software? Last thing I want to do is do it over again!!!If it's just Quicken and personal finance, then GnuCash is overkill. You may wish to look into a simpler and easier app like Grisbi, HomeBank, etc. There are at least a dozen of them out there, but just type "Accounting" into the software centre and go through them all. I wasn't familiar with your current Windows app, but given what you've told us now, you don't need GnuCash, which is more for SOHO and small businesses that require the rigours of a true double-entry acctng system.

I'm not too familiar with the more user-friendly apps. I use GnuCash because I run an incorporated entity. Perhaps others can jump in here. I have heard that many apps will import QIFs quite well. The app developers' sites will usually tell you if they do or not.

RE: VMs, there are a number of these as well. VMWare is one, but KVM is built into the kernel and VirtualBox is the easiest to use (in my exp). XEN is also built into the kernel and is very powerful, but it is extremely technical and not recommended for beginners. Best to stick with VMWare, KVM or VirtualBox (which is what I use). AFAIK VM Ware for personal use is free. VirtualBox for personal use is definitely free. KVM and XEN are baked into the kernel, so are not only free but open source as well.

You need a Windows license to run Windows inside a VM. There are so many different types of Windows licenses that you will have to read yours and see if it permits running in a VM inside your original computer, but a full original version should allow you to. If not? Well, you'll have to shell out for a license and just one more reason to get off the Microsoft hamster mill.

P.S. You may wish to bypass a resident app altogether and go to a Web-based accntng pkg. Have heard some good reports about this option. I don't know how you feel about having your financial data in the cloud though.

---

### Post by ian-weisser on 2014-12-16
[edit] Withdrawn. You *did* post lsusb, and I missed it.

---

### Post by DuckHook on 2014-12-16
> **magpies89 said:**
> After trying 'lsusb' This is where I am at:RE: Wireless

*lsusb* shows your WIFI stick to be based on the Broadcom BCM43231 chipset. I hate to be the bearer of bad news, but the Broadcom chipsets are absolute trainwrecks when it comes to their affinity with Linux. Not Linux's fault... Broadcom just insists on using proprietary chips and won't or can't release the HW details so that the Linux community can reverse engineer a driver. I've wrestled with BCM chipsets for decades. Thoroughly sick of them. For the older chipsets, there was a way to extract the firmware blob, build it into a Linux driver and load it as a module, but I don't know how this can be done for the 43231. Some people have managed to get it done with *ndiswrapper*, but *ndiswrapper* has always been a kludge and an ugly one at that. Link [here]("http://ubuntuforums.org/showthread.php?t=2221251").

My suggestion is to buy another WIFI stick based on an Atheros chipset. They are very well supported in Linux. It beats wrestling with the stupid BCM stick every time you reinstall the OS. And WIFI sticks are so cheap these days. Available on eBay for a little over $10. Just make sure that you check any potential purchase against Ubuntu's compatibility database so that you don't end up buying another lemon. And stay the heck away from Broadcom stuff no matter what.

---

### Post by praseodym on 2014-12-22
Maybe a kernel upgrade came in between?! Please check
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential ndisgtk dkms ndiswrapper-dkms
```
The "dkms" files will build the module automatically after kernel upgrades

---

### Post by magpies89 on 2014-12-22
> **praseodym said:**
> Maybe a kernel upgrade came in between?! Please check
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential ndisgtk dkms ndiswrapper-dkms
```
The "dkms" files will build the module automatically after kernel upgrades

Praseodym,

Output after following your code:


*abhishek@Transformer-P55-UD3:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential ndisgtk dkms ndiswrapper-dkms*
*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
*Package ndiswrapper-dkms is not available, but is referred to by another package.*
*This may mean that the package is missing, has been obsoleted, or*
*is only available from another source*

*E: Unable to locate package build-essential*
*E: Unable to locate package ndisgtk*
*E: Unable to locate package dkms*
*E: Package 'ndiswrapper-dkms' has no installation candidate*


What's the verdict?

Cheers

Abhi

---

### Post by praseodym on 2014-12-22
Did you activate the package archives
[LIST]
[*]main
[*]restricted
[*]multiverse and
[*]universe
[/LIST]
?

---

### Post by magpies89 on 2014-12-22
Praseodym,

Thanks for your reply. Any tips on activating these packages? First time I have been advised to activate them. What commands etc do I need to use?

Cheers

Abhi

---

### Post by magpies89 on 2014-12-22
> **praseodym said:**
> Did you activate the package archives
[LIST]
[*]main
[*]restricted
[*]multiverse and
[*]universe
[/LIST]
?

Praseodym,

Please ignore my previous requests; I did following (It seems like all the repositories are already enabled, update is probably not working as I do not have wired connection currently:

*abhishek@Transformer-P55-UD3:~$ sudo add-apt-repository main*
*[sudo] password for abhishek: *
*'main' distribution component is already enabled for all sources.*
*abhishek@Transformer-P55-UD3:~$ sudo add-apt-repository universe*
*'universe' distribution component is already enabled for all sources.*
*abhishek@Transformer-P55-UD3:~$ sudo add-apt-repository multiverse*
*'multiverse' distribution component is already enabled for all sources.*
*abhishek@Transformer-P55-UD3:~$ sudo add-apt-repository restricted*
*'restricted' distribution component is already enabled for all sources.*
*abhishek@Transformer-P55-UD3:~$ sudo apt-get update*
*Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty InRelease*

*Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates InRelease*

*Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease*

*Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease*

*Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports InRelease*

*Err [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg*
*  Could not resolve 'extras.ubuntu.com'*
*Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release.gpg*
*  Could not resolve 'au.archive.ubuntu.com'*
*Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates Release.gpg*
*  Could not resolve 'au.archive.ubuntu.com'*
*Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg*
*  Could not resolve 'security.ubuntu.com'*
*Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports Release.gpg*
*  Could not resolve 'au.archive.ubuntu.com'*
*Reading package lists... Done*
*W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/trusty/InRelease)  *

*W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)  *

*W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)  *

*W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)  *

*W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease](http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease)  *

*W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'*

*W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'*

*W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'*

*W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'extras.ubuntu.com'*

*W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Could not resolve 'au.archive.ubuntu.com'*

*W: Some index files failed to download. They have been ignored, or old ones used instead.*

---

### Post by praseodym on 2014-12-23
Update-Manager->Settings->Software from Ubuntu

---

