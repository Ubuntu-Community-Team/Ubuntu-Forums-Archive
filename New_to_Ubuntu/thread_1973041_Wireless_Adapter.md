---
title: "Wireless Adapter"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Segofam on 2012-05-04
I have a fresh install of 12.04, and have plugged in a SkyCity Wireless Adaptor, but I cannot get any thing wireless to work, and there is no other internet connection to the pc.

Would anyone be able to help me get the Wireless Adaptor working?

Sincerely,

Scott.

PS The package says it works with Linux...if that's any help to you!

---

### Post by NikTh on 2012-05-04
Hi , 
please open a terminal (Ctrl+alt + t) and give the output of these commands so someone can help you. Further info needed. 
```
lspci -nnk | grep -iA2 net 
lsusb
rfkill list all 
lsmod
```Put the results inside code tags for better reading. Select the text and hit # symbol.
Thanks

---

### Post by Segofam on 2012-05-04
I will try and do that with a memory stick...not sure about what you mean by the code tags, as I haven't done that before!?
BRB with a mem stick.

Here goes...

  	 	 	 	 	 	   scott@scott-HP-Compaq-dx2200-MT:~$ lspci -nnk  
 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge [1002:5a33] (rev 01)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel modules: ati-agp  
 00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge [1002:5a3f]  
 	Kernel modules: shpchp  
 00:12.0 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller [1002:4379] (rev 80)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: sata_sil  
 	Kernel modules: sata_sil  
 00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller [1002:4374] (rev 80)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: ohci_hcd  
 00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller [1002:4375] (rev 80)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: ohci_hcd  
 00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller [1002:4373] (rev 80)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: ehci_hcd  
 00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller [1002:4372] (rev 82) 
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: piix4_smbus  
 	Kernel modules: i2c-piix4  
 00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller [1002:4376] (rev 80)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: pata_atiixp  
 	Kernel modules: pata_atiixp  
 00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: snd_hda_intel  
 	Kernel modules: snd-hda-intel  
 00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)  
 01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] [1002:5a61]  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:7254]  
 	Kernel driver in use: radeon  
 	Kernel modules: radeon  
 02:00.0 Communication controller [0780]: LSI Corporation V.92 56K WinModem [11c1:048c] (rev 03)  
 	Subsystem: LSI Corporation Device [11c1:044c]  
 02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)  
 	Subsystem: Micro-Star International Co., Ltd. Device [1462:254c]  
 	Kernel driver in use: 8139too  
 	Kernel modules: 8139too, 8139cp  
 scott@scott-HP-Compaq-dx2200-MT:~$ lspci -nnk | gre[ -iA2 net  
 >  
 

 

 scott@scott-HP-Compaq-dx2200-MT:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter  
 Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical  
 Bus 001 Device 004: ID 0c76:0005 JMTek, LLC. Transcend Flash disk  
 scott@scott-HP-Compaq-dx2200-MT:~$  
 

 

 scott@scott-HP-Compaq-dx2200-MT:~$ rfkill list all  
 scott@scott-HP-Compaq-dx2200-MT:~$  
 

 

 scott@scott-HP-Compaq-dx2200-MT:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17308  1  
 fat                    55605  1 vfat  
 uas                    17699  0  
 usb_storage            39646  1  
 snd_hda_codec_realtek   174055  1  
 snd_hda_intel          32765  3  
 snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13276  1 snd_hda_codec  
 snd_pcm                80845  2 snd_hda_intel,snd_hda_codec  
 snd_seq_midi           13132  0  
 snd_rawmidi            25424  1 snd_seq_midi  
 rfcomm                 38139  0  
 bnep                   17830  2  
 bluetooth             158438  10 rfcomm,bnep  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 ppdev                  12849  0  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              28931  2 snd_pcm,snd_seq  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                72846  0  
 serio_raw              13027  0  
 i2c_piix4              13093  0  
 soundcore              14635  1 snd  
 snd_page_alloc         14108  2 snd_hda_intel,snd_pcm  
 radeon                733693  3  
 ttm                    65344  1 radeon  
 drm_kms_helper         45466  1 radeon  
 drm                   197692  5 radeon,ttm,drm_kms_helper  
 parport_pc             32114  1  
 mac_hid                13077  0  
 i2c_algo_bit           13199  1 radeon  
 ati_agp                13242  0  
 shpchp                 32325  0  
 lp                     17455  0  
 parport                40930  3 ppdev,parport_pc,lp  
 usbhid                 41906  0  
 hid                    77367  1 usbhid  
 8139too                23283  0  
 8139cp                 26759  0  
 pata_atiixp            12999  0  
 sata_sil               13275  2  
 scott@scott-HP-Compaq-dx2200-MT:~$
  
That's a whole heap of another world right there!

---

### Post by NikTh on 2012-05-04
> **Segofam said:**
> not sure about what you mean by the code tags, as I haven't done that before!?
 
Hi,

Click edit on your post , then Go advanced , then select the text of every output separately and click this symbol** # ** 

If you open a terminal and write ```
jockey-gtk
``` in the open window , what additional drivers you have ? 
Thanks

---

### Post by Segofam on 2012-05-04
> **NikTh said:**
> ...then select the text of every output separately and click this symbol** #**

Just leaves the # symbol in its place!

Anyway, after putting in jockey -gtk, I get command not found.

---

### Post by SuaSwe on 2012-05-04
Hi Segofam,

I think NikTh meant press the button marked "#" (above the editing window) after highlighting the text. ;)

Could you also advise: do you have a networking icon in your panel (usually situated along the top of the screen)? If you do, what do you get if you right- and left-click on it?

---

### Post by Segofam on 2012-05-04
I get a grayed our Wired Network then disconnected
under those I get a clickable VPN Connection then a tecked Enable Networking
under that I get a grayed Connection Information
and then a clickable Edit Connections.

It's the same when I left click!

I would like to add that I do have a CD with a tar.bz2 file on it...!!!

We are off to bed, catch you in the morning, thanks for your help so far :)

---

### Post by NikTh on 2012-05-04
> **Segofam said:**
> 

Anyway, after putting in jockey -gtk, I get command not found.
Hi , 
its not ```
jockey -gtk 
``` its

```
jockey-gtk
``` without a space between y and - 
Copy-paste the command from here to your terminal for more accuracy if you want.
Thanks.

---

### Post by Segofam on 2012-05-04
Good morning NikTH, and others :)


The result of typing jockey-gtk is:




scott@scott-HP-Compaq-dx2200-MT:~$ jockey-gtk  
 

 (jockey-gtk:1769): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed  
 

 (jockey-gtk:1769): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed 





Also a popup saying 'Downloading package indexes failed, please check your network status. Most driverss will not be availble.'


Bear in mind that I am transferring this data via usb from the pc in question to this laptop I am now typing on :-)

---

### Post by NikTh on 2012-05-05
> **Segofam said:**
> 
Also a popup saying 'Downloading package indexes failed, please check your network status. Most driverss will not be availble.'


Bear in mind that I am transferring this data via usb from the pc in question to this laptop I am now typing on :-)

Hi , 
connect your pc with an ethernet cable to have stable internet and execute the command again. 
I think that driver missing . 
Ubuntu has proprietary drivers that will suggest for your adapter if connected . 
when connect to internet run again ```
jockey-gtk
``` and the pop up window probably will suggest you a driver for you wireless adapter. 
Thanks

---

### Post by Segofam on 2012-05-06
Ok, got myself a cable and am on my way home :-)
Thanks for the patience, it does appear as though we are on oposite sides of the planet :-)

```
Ok, we are at home with BoB (wireless router) hooked up to pc.
Clearly I don't know enough about setting up the wired connection, so hopefully we will catch each other here and you might! run me through this as my attempts are so far unsuccessful :-/
```...and I figured the code wrap out too, thanks for that :)

Ok, feeling really stupid now. I kept putting in username and password and the internet would not connect. So I deleted and added a new network and just clicked save and the internet now works!!!

So here is the jockey-gtk command you origonally asked for:

```
scott@scott-HP-Compaq-dx2200-MT:~$ jockey-gtk

(jockey-gtk:2633): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2633): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
scott@scott-HP-Compaq-dx2200-MT:~$ 
```

---

### Post by NikTh on 2012-05-06
Hi,
jockey-gtk its a front-end of jockey-text command. It opens the additional drivers window so its not helpful to post the output of this command (jockey-gtk i mean) 
If you want to post an output then give ```
jockey-text
``` and post the output. Remember to give this command with internet enabled and your adapter connected. 
Thanks

---

### Post by Segofam on 2012-05-07
...and I get this:

```
scott@scott-HP-Compaq-dx2200-MT:~$ jockey-text
Additional Drivers
Searching for available drivers...
scott@scott-HP-Compaq-dx2200-MT:~$
```Before we get into getting my making my wireless adapter working...
I know that this 'code wrap' is used lots on these forums, but what is the purpose?

...as previously mentioned, I would like to add that I do have a CD with a tar.bz2 file on it...!!! Are we able to untar this tar?
I don't know the commands off hand.

And I went through this [http://www.linuxquestions.org/questions/linux-general-1/useful-thread-and-information-about-installing-programs-45094/](http://www.linuxquestions.org/questions/linux-general-1/useful-thread-and-information-about-installing-programs-45094/)
But had to mess around with the su -m bit and did a sudo make install which seemed to run through it paces!

Don't forget me guys, I am just hacking my way through this. The missus doesn't want a cable running across the floor of the house :)

---

### Post by NikTh on 2012-05-07
> **Segofam said:**
> ...and I get this:

```
scott@scott-HP-Compaq-dx2200-MT:~$ jockey-text
Additional Drivers
Searching for available drivers...
scott@scott-HP-Compaq-dx2200-MT:~$
```Before we get into getting my making my wireless adapter working...
I know that this 'code wrap' is used lots on these forums, but what is the purpose?

...as previously mentioned, I would like to add that I do have a CD with a tar.bz2 file on it...!!! Are we able to untar this tar?
I don't know the commands off hand.

Hi , 
no driver found for you adapter. I thought that Ubuntu could  provide additional driver for your adapter. 
Wrap code is for better reading and focus when its about commands and output of commands. 
If you want to decompress tar file then use tar command . For bz2 its
```
tar -xvjf <filename>.tar.bz2
``` 
Also take a look to this thread -->  [http://ubuntuforums.org/showthread.php?t=1800178](http://ubuntuforums.org/showthread.php?t=1800178) 4th post. I think it will help you. 
Thanks

---

### Post by Segofam on 2012-05-07
Hey NikTH,
I have RT2870 Wireless Lan Linux Driver in my Additional Drivers now...
Getting closer...
...can't get it to fire up though!
What should I be looking for?

Says activated but not in use!

Reading the README file now after untarring.

I have untarred into a folder, in my home folder, called Wireless...

In the Home folder I have a Wireless folder, in there I have a Makefile folder that I have to get to, to change some stuff. I can't get to it. Can you tell me how I get into it?

---

### Post by NikTh on 2012-05-07
> **Segofam said:**
> Hey NikTH,
I have RT2870 Wireless Lan Linux Driver in my Additional Drivers now...
Getting closer...
...can't get it to fire up though!
What should I be looking for?

Says activated but not in use!

Hi , 
i think that this is a known 'bug' . I mean the message that "driver is activated but not in use" . See here another example of this bug --> [http://askubuntu.com/questions/40582/how-do-i-use-an-activatedbut-not-in-use-driver](http://askubuntu.com/questions/40582/how-do-i-use-an-activatedbut-not-in-use-driver) . 
My opinion its to ignore that message. If a driver is activated then its active and in use.

Now you must check the network manager (top panel , icon with internet) and see if networks are there. Wireless networks i mean. Maybe **you must reboot** for driver take place.

When reboot search for module with "rt" with this command 
```
lsmod | grep rt
``` 
i am not sure but your module must be something like "rt5730sta" or "rt2870sta"
Thanks

---

### Post by Segofam on 2012-05-08
Got online last night, and Skyped with a guy from Brisbane who is an old flame of Linux. And he thinks there needs to be something extra, that needs to go between the drivers and the network so the two can marry up.
I will be back tonight to go through the links again, that you posted up earlier.
Thanks.
Regards,
Scott.
PS Wifey really not happy with cable running through house ;-)

I have been succonded and should be home soon to move to a resolution with the wireless adaptor :-)

---

### Post by Segofam on 2012-05-22
Hi,
We have spent too much time on this, and someone gave me one that works out of the box so to speak.
Thanks for your help, but I will let this one go.
Kind regards,
Scott.

---

