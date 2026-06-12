---
title: "[SOLVED] wireless for toshiba laptop"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by misswham on 2008-08-27
i need to connect wirelessly to the internet here is the output of a command I typed in the terminal.  Can someone tell me how to connect my laptop please?

lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by markjensen on 2008-08-27
You have a line for Ethernet that says you have a Atheros AR242x.  The Atheros site has a [Linux page](http://www.atheros.com/news/linux.html) the pretty much points to using **madwifi**.

If you don't have madwifi already installed, I recommend connecting on your hardwired port, and installing madwifi via synaptic.   (do a full update too, if you haven't already)

---

### Post by misswham on 2008-08-27
I have done the update through synpathic but still lost at what to do now?  It still isn't connecting

---

### Post by Dougie187 on 2008-08-27
You have to install the madwifi package. An Update isn't going to fix your issue, he just recommended it because its good practice to update your system.

you can search for the package in synaptic, or you can go to a command line and type
```
sudo apt-get install madwifi
```

---

### Post by Michael.Godawski on 2008-08-27
can you please also post the results of these commands:

```
iwconfig
sudo iwlist scan
```

they will tell us if the wlan drivers are active.

---

### Post by misswham on 2008-08-27
Apparently I have done something wrong.  I went to the site mentioned and downloaded the package then i went to the synpatic manager and installled it and still this is what i got

sudo apt-get install madwifi
[sudo] password for 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package madwifi

---

### Post by misswham on 2008-08-27
I went back to synpatic and just checked everything that showed up when i typed madwifi in the search bar.  Everything downloaded and it asked me to restart i did and now it wont start in ubuntu anymore.  when grub boots up and then it goes to the next screen it says

Starting up...

[   24.924478]  ..MP-BIOS bug:  8254 timer not connected to I0-APIC

what have I done and how can I correct it?

Also I am dual-booted this laptop with vista/linux with vista installed first

---

### Post by nothingspecial on 2008-08-27
Here is a solution for your wireless card. It looks good.

[http://egoleo.wordpress.com/2008/06/02/howto-enable-wireless-on-acer-4520-on-ubuntu-hardy/](http://egoleo.wordpress.com/2008/06/02/howto-enable-wireless-on-acer-4520-on-ubuntu-hardy/)

---

### Post by nothingspecial on 2008-08-27
Near the bottom of the how to is the word make. Whoever made that post forgot to put the word "make" in **bold**. You still have to type it.

Where it says this - 

6. Now you can build your madwifi and install the modules:
make

I hope I`m being clear.

---

### Post by misswham on 2008-08-27
Now it wont boot up in ubuntu it is just stalled at the starting up menu after the grub screen.  I cant even get back into ubuntu at all.  I want to delete the ubuntu part of the harddrive and reinstall.  I think I just need to start from scratch again.  I have windows vista how can I just start over?

---

### Post by nothingspecial on 2008-08-27
I have never dual booted, I`m sorry I don`t know. I normally just install over the whole hard drive.
 However, that is a different question, as is the problem with Ubuntu not booting, (which, I`m sorry to say I don`t know about either). My point is that you need to start a new thread. Something like - 

"Can`t boot ubuntu [ 24.924478] ..MP-BIOS bug: 8254 timer not connected to I0-APIC"

to see if anyone can fix that problem. If not then - 
How to reinstall ubuntu without affecting Vista partition

It`s no good asking those questions in a thread about wireless things `cause the guys who can help you with your new problem might not read it -  if you get what I mean.

---

### Post by porchrat on 2008-08-27
the MP_BIOS bug crops up often in ubuntu installs.

I experience that problem on one of my ubuntu machines.  However my problem doesn't prevent booting.

That bug means that ubuntu can't utilise APIC properly, meaning you won't have functionality such as SMP (symmetric multi processing).  Apparently this is important if you're looking for performance from a machine with more than one procesor core.

Try turning off ACPI in the BIOS as that stops anything to do with APIC, hopefully it will at least allow you to boot and undo the damage.

---

### Post by misswham on 2008-08-27
I am back online now and I have done everything that has been posted and still cant see the wireless card when i double click the icon in the toolbar.  i just see the wired connection.  I dont have the ethernet hooked up when i do it.  I hate that I cant get this one to work because this is the laptop that i use the most and i need the wireless connection to work.

Can someone please walk me through it again?

---

### Post by Miljet on 2008-08-27
Try following this guide. It is old but still good.

[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

---

### Post by misswham on 2008-08-28
I booted from live cd and still no wireless network showed up.  Now my other older laptop worked because I used windows drivers from a suggestion from a previous post.  Anyone think that this might be better with my wireless card than the ways that have been posted and if so how?  If not then I am stumped.  I have probably not understood some of the commands in the prior posts.  I know someone said put something in a console and I assumed they were speaking of the terminal and I did and still nothing.  Can someone in leymans terms tell me step by step what to do if you dont mind?

---

### Post by nothingspecial on 2008-08-28
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

This is downloading a zipped file that is supposed to make your wireless work. wget is the download program, followed by the web address, followed by the name of the file you are down loading.

```
tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

This command is unzipping the file you just down loaded. In linux we use tar (amongst other things) insread of zip.

```
cd madwifi-hal-0.10.5.6-r3835-20080801
``` 

This bit moves you into the unzipped folder, just like clicking on an .exe
```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Now you are installing software that allows you to to configure and install programs from the original code.

```
sudo make
```

```
sudo make install
```

Theses 2 commands are installing  software on your system a bit like following a set up wizard.

Sorry if I`m being too basic. 
Are you getting any errors.
You need an internet connection to download the 2 packages, so plug your laptop in.
After you`ve completed the steps you may need to reboot.

---

### Post by misswham on 2008-08-29
OH MY GOD!  FINALLY I CAN SLEEP.  IT WORKED IT WORKED!!!!!!!!  Thank you sooo much so much!!

Smooches

---

### Post by delanov on 2008-08-29
Just installed Ubuntu 8.04.1 and registered. I'm totally impressed with the outpouring of help received on this thread.  I need help with my USB wireless adapter, but it's late and I must go to work. When I return, i'll begin a new thread. :)

Regards

---

### Post by nothingspecial on 2008-08-29
"Smooches"

:oops:

---

### Post by misswham on 2008-09-18
hi there.  my laptop all of a sudden stopped getting wireless.  when i log on it automatically connects but now the 2 icons have an exclamation point and the other has a minus sign.  I dont know why it stopped connecting but it did.  also the negative sign error message says 

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error:  No such device

and when i right click on the one with the exclamation point 

enable network is checked

and edit wireless network is in bold and when i left click edit wireless network i see my router listed under networks.

can someone help?

---

