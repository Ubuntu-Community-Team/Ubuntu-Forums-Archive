---
title: "HOWTO: Watch digital TV (Freeview)"
date: 2007-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by tom56 on 2007-04-24
[SIZE="5"]**Watching Digital TV (Freeview) in Ubuntu **[/SIZE] :popcorn:

**[SIZE="3"]Introduction - PLEASE READ[/SIZE]**
I haven't tried this since 8.04 (I no longer have a Freeview tuner), so some steps may no longer be necessary. It should still work though (on 8.10 or 9.04).

This guide is aimed towards the UK, but it may work in other countries too.

There are now two ways to watch TV:
(1) If you have a digital tuner continue reading the post below.
(2) If you don't have a tuner (or you can't be bothered to set it up) you can now watch most digital channels over the internet using [Zattoo]("http://zattoo.com"). Simply go to the website, download and install.

**[SIZE="3"]What is required?[/SIZE]**
Most of what you need to watch digital TV in Ubuntu is installed by default. There are three things required:
[LIST=1]
[*]A tuner
[*]The right modules
[*]The right firmware
[*]And a program to watch TV with
[/LIST]

Go through each heading in this guide and after each section check if the TV is working yet by using Kaffeine (see below). Hopefully, by the end of the page you will have installed everything you need to enjoy digital TV in Ubuntu.

[SIZE="3"]**TV App and Codecs**[/SIZE]
The best program by far for watching TV is Kaffeine. It is installed by default in Kubuntu but not in Ubuntu, so that's the first thing we need to do. Launch the terminal and enter the following. This will install Kaffeine and the necessary codecs. If you feel more comfortable doing this in Synaptic then by all means, go ahead.
```
sudo apt-get install kaffeine libxine1-ffmpeg
```

It is also important to make sure that the user who is trying to watch TV is in the "video" group. To add them launch the terminal and add the following (replacing "tom" with the name of the user you want to add to the group).
```
sudo usermod -G video -a tom
```

[SIZE="3"]**Modules**[/SIZE]
Kernel modules are a tricky business and outside the scope of this HOWTO. Suffice it to say that modules are to Linux what drivers are to Windows. The right modules are already installed by default and are usually loaded automatically when needed. There are a few digital TV devices that aren't always autodetected. Bugs are filed against these so this should be fixed soon*. Try loading these modules then see if Kaffeine works. Try only one module at a time.
```
sudo modprobe em28xx
sudo modprobe cx88-dvb
sudo modprobe dvb-bt8xx
```
If that works then you need to set the module to be loaded each boot. enter the following in the terminal. Replace the module name (i.e. "cx88_dvb") with whichever of the above it was that worked.
```
sudo sh -c "echo "cx88_dvb" >> /etc/modules"
```

* As of March 19th 2008 there seem to be no bugs filed - maybe these have been fixed?

[SIZE="3"]**Firmware**[/SIZE]
As well as the module, Ubuntu needs the firmware for the device so that the two know how to talk to eachother. Firmwares are stored in /lib/firmware/ in folders by kernel version (take a look at /lib/firmware/ to see what I mean). These are installed by the package linux-restricted-modules. However the package doesn't always contain all the firmware files available. Therefore I have produced a collection of extra firmware files (attached). Install this package then reboot your TV tuner (by unplugging and plugging in or by rebooting the computer) and then launch Kaffeine. To install simply download the attachment then double-click it to install.

**---**

_[SIZE="3"]**Edits**[/SIZE]_

**Januray 11 2009**
[INDENT][LIST]
[*]Added info about Zattoo.
[/LIST][/INDENT]

**April 19 2008**
[INDENT][LIST]
[*]Updated with new package (see changelog below). I've kept the old package in case the new one breaks something.
[*]Removed list of old changes. Does anyone care?
[/LIST][/INDENT]

_[SIZE="3"]**Changelog for Firmware Bundle**[/SIZE]_

**April 2008 - 1.5.5-0ubuntu1**
[INDENT][LIST]
[*]Added files from [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)
[/LIST][/INDENT]

**---**

For more information on digital TV in Linux, visit [http://www.linuxtv.org/wiki/index.php/DVB_USB](http://www.linuxtv.org/wiki/index.php/DVB_USB)
If this tutorial fails, and I don't respond to your cries for help within 2 weeks, give this page a try - [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

I will try and keep the firmware package updated every few months or as requested.

Post any questions/problems you have and I'll do my best to answer :D
Please run dmesg|tail then plug in your device and post the output in your question.

---

### Post by tom56 on 2007-04-25
Sorry - just posting to subscibe myself to email notifications

* MOD - PLEASE DELETE*

---

### Post by brencamb on 2007-04-26
> **tom56 said:**
> 
4. Then run the script (replacing tda10046 with whatever firmware you need)
```
sudo /usr/src/linux-source-2.6.20/Documentation/dvb/get_dvb_firmware tda10046
```


I can't seem to complete this step - I am unsure what to enter in place of "tda10046". I have a Nebula DigiTV USB unit, but I can't figure out what to enter from the page you linked to.

Any help is greatly appreciated. :)

(I get this terminal output)

get_dvb_firmware nxt6000
Unknown component "nxt6000"
syntax: get_dvb_firmware <component>
Supported components:
        sp8870
        sp887x
        tda10045
        tda10046
        tda10046lifeview
        av7110
        dec2000t
        dec2540t
        dec3000s
        vp7041
        dibusb
        nxt2002
        nxt2004
        or51211
        or51132_qam
        or51132_vsb
        bluebird

So I guess I have to use one of those, but I dunno which one!!

---

### Post by lukew on 2007-04-26
Nice howto. I thought that usb support was suppose to be very limited. 

Can i be rude and ask which USB TV card you have? I tried to gt my old mans Cute TV USB box to work but it was a no show!

Thanks

Luke

---

### Post by tom56 on 2007-04-26
> **brencamb said:**
> I can't seem to complete this step - I am unsure what to enter in place of "tda10046". I have a Nebula DigiTV USB unit, but I can't figure out what to enter from the page you linked to.

Unplug and plug back in your usb tv card. Then wait a few seconds and enter the following in the terminal and post the results here.

```
dmesg|tail
```

---

### Post by tom56 on 2007-04-26
> **lukew said:**
> Nice howto. I thought that usb support was suppose to be very limited. 

Can i be rude and ask which USB TV card you have? I tried to gt my old mans Cute TV USB box to work but it was a no show!

Thanks

Luke

I have a WinTV Nova-T USB (the old USB 1.1 one not the new USB 2.0 one). It works perfectly - better on Linux than in Windows actually!

---

### Post by easyease on 2007-04-27
Yep kaffeine is the best app for watching digi tv in linux, mythtv is way too much hassle to set up.
i just followed this code to set up my card and it worked off a fresh feisty install....

sudo modprobe cx88-dvb

---

### Post by Erlander on 2007-04-28
For PAL DVB Kaffeine under Feisty has a problem.  Additional Xine plugins and codecs have to be installed.

Without them Kaffeine throws up an error message.

I'm not sure which one precisely is needed because I just installed everything for Xine that looked relevant.

Under Edgy it was OK so I guess someone removed the vital dependency.

In spite of the above yes I agree that Kaffeine is an excellent program for watching digital TV.

Rob

---

### Post by tom56 on 2007-04-28
> **Erlander said:**
> For PAL DVB Kaffeine under Feisty has a problem.  Additional Xine plugins and codecs have to be installed.

Without them Kaffeine throws up an error message.

I'm not sure which one precisely is needed because I just installed everything for Xine that looked relevant.

Under Edgy it was OK so I guess someone removed the vital dependency.

In spite of the above yes I agree that Kaffeine is an excellent program for watching digital TV.

Rob

That's true. Following instructions for enabling DVD Playback gets the stuff you need so I'll add the relevant bit to the original post.

---

### Post by Erlander on 2007-04-28
No its not the DVD playback filters.  Its one for TS (Transport Streams)  I'll do some more checking and find precisely which one it is for PAL DVB_T

Also if this thread is going to become a How-To then it needs to acknowledge that som tuners work out of the box and don't need firmware installed.  Everything for them is included in the kernel.  In the Mythtv documentation there is a list of tuners known to be in this category.

All I have to do is the install Kaffeine and then the TS filter and I'm able to use my tuner with kaffeine.  I'll check on the filter/plugin needed and get back.

Hope this is of use.

Rob

---

### Post by brencamb on 2007-04-28
> **tom56 said:**
> Unplug and plug back in your usb tv card. Then wait a few seconds and enter the following in the terminal and post the results here.

```
dmesg|tail
```

Finally got round to doing what you suggested - here's the results:

[  116.640981] dvb-usb: recv bulk message failed: -75
[  117.656871] dvb-usb: recv bulk message failed: -75
[  118.420778] usb 1-4: USB disconnect, address 4
[  118.422007] dvb-usb: Nebula Electronics uDigiTV DVB-T USB2.0) successfully deinitialized and disconnected.
[  123.196481] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  123.328826] usb 1-4: configuration #1 chosen from 1 choice
[  123.328908] dvb-usb: found a 'Nebula Electronics uDigiTV DVB-T USB2.0)' in cold state, will try to load a firmware
[  123.435561] dvb-usb: did not find the firmware file. (dvb-usb-digitv-02.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[  123.435571] dvb_usb_digitv: probe of 1-4:1.0 failed with error -2
[  123.435592] usb 1-4: device_add(1-4:1.0) --> -2

---

### Post by brencamb on 2007-04-28
> **tom56 said:**
> That's true. Following instructions for enabling DVD Playback gets the stuff you need so I'll add the relevant bit to the original post.

I have now also gotten to this point - I have no idea where to get the codecs I need from though!

---

### Post by Erlander on 2007-04-28
If you get the error message below you need to install libxine-extracodecs.  I did it with Synapatic.

For me to get Kaffeine to work I only 

(1)  Install Kaffeine and
(2)  Install libxine-extracodecs

Rob

---

### Post by tom56 on 2007-04-29
> **Erlander said:**
> If you get the error message below you need to install libxine-extracodecs.  I did it with Synapatic.

For me to get Kaffeine to work I only 

(1)  Install Kaffeine and
(2)  Install libxine-extracodecs

Rob

Actually, the package needed is libxine1-ffmpeg. I've updated the original post to reflect this.

---

### Post by tom56 on 2007-04-29
> **brencamb said:**
> Finally got round to doing what you suggested - here's the results:

[  116.640981] dvb-usb: recv bulk message failed: -75
[  117.656871] dvb-usb: recv bulk message failed: -75
[  118.420778] usb 1-4: USB disconnect, address 4
[  118.422007] dvb-usb: Nebula Electronics uDigiTV DVB-T USB2.0) successfully deinitialized and disconnected.
[  123.196481] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  123.328826] usb 1-4: configuration #1 chosen from 1 choice
[  123.328908] dvb-usb: found a 'Nebula Electronics uDigiTV DVB-T USB2.0)' in cold state, will try to load a firmware
[  123.435561] dvb-usb: did not find the firmware file. (dvb-usb-digitv-02.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[  123.435571] dvb_usb_digitv: probe of 1-4:1.0 failed with error -2
[  123.435592] usb 1-4: device_add(1-4:1.0) --> -2

You need dvb-usb-digitv-02.fw. The tool for grabbing firmware from the internet doesn't have this, but I found the file in an RPM package on the internet. Move the attached to /lib/firmware

EDIT: This is irrelevant now, please see 1st post.

---

### Post by det345 on 2007-11-30
Hello,

I just bought a WinTV Nova-USB Stick in Germany. Because I can't get it to work under Ubuntu 7.10 I looked around in the internet and different HowTos. Nothing works. Finally I noticed that my stick seems to have a different Product-ID than the ones mentioned in the HowTos. My shows up with product-ID 7070 as the output of lsusb shows:
  idVendor           0x2040 Hauppauge
  idProduct          0x7070 
  bcdDevice            1.00
  iManufacturer           1 Hauppauge
  iProduct                2 Nova-T Stick
  iSerial                 3 4030943411
Any idea how to get it work?

Thanks in advance
det

---

### Post by cocojambo on 2007-11-30
I have the same problem with a new hauppauge usb receiver, bought from Conrad in Germany. Product id is 0x7070...:

Is there a way to get it running?

Bus 004 Device 004: ID 2040:7070 Hauppauge 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2040 Hauppauge
  idProduct          0x7070 
  bcdDevice            1.00
  iManufacturer           1 Hauppauge
  iProduct                2 Nova-T Stick
  iSerial                 3 4030940730
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
...

Bye,
coco.

---

### Post by cocojambo on 2007-12-02
I got my DVB-T stick with product id 0x7070 up and running. Look at:

[http://www.linuxtv.org/pipermail/linux-dvb/2007-December/022177.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-December/022177.html)

to see how!

Bye,
Coco.

---

### Post by nab on 2008-01-04
Well,

I have the same DVB-Stick.

properly just me,

But could please anybody explain in simple words what I have to do?
Or gve me an link which explains a little bit more :-)

Thanks in avance!
Niko

---

### Post by keithk50 on 2008-01-04
This is really great work.    I cannot thank you enough for this 'how to'.   I had given up with getting my DVB USB (Freecom) to work with Ubuntu many months ago.   I followed your guide with an element of doubt (oh he of little faith) but when I seen the scan working through the Freeview channels, wow!   
What a great application Kaffeine is.   I salute you sir............    Well done.   There were only two applications keeping me from dropping Windoze completely.   Skype (Video version) and DVB USB.    Both have now been achieved in the past two days.    Thanks again.
 
Keith

---

### Post by Sukarn on 2008-01-05
> **tom56 said:**
> Sorry - just posting to subscibe myself to email notifications

You can subscribe to a thread by using the thread tools at the top of the thread without having to post any useless messages.

---

### Post by nab on 2008-01-05
ok, I think I figured it out.

Just so i don't forget:

I followed this guides:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick)
(here I got the firmware)

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)
(here I follow the guide for 2.4 kernel to get the source, compile and install)

[http://linuxtv.org/pipermail/linux-dvb/2007-December/022177.html](http://linuxtv.org/pipermail/linux-dvb/2007-December/022177.html)
(here are the 3 changes in 2 files listed to get the card working)

with "sudo make unload" and "sudo modprobe dvb_usb_dib0700
" and "sudo modprobe dib0070" I got the modules loaded as needed. "dmesg" is showing the card is up and running.

[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device)
(just what the title says :-) Testing)

Niko

---

### Post by Peter Larsen on 2008-01-17
I'm a new Ubunto 7.10 user and to get my Hauppauge WinTV-NOVA USB DVB-T stick to work, I followed **tom56**'s HOWTO - great thanks!
But i can't get my IR remotecontrol to work - any ideas?

---

### Post by nab on 2008-02-06
Hi all,

after the upgrade today I lost my ability to use my dvb-t-Stick.

Has anybody the same problem?

The kernel modules aren't anymore loaded.
TIA
Niko

---

### Post by Erlander on 2008-02-06
My DVB-t tuner is still working.

Rob

---

### Post by nab on 2008-02-09
well, I didn't find the error, :confused:

but reinstalling firmware and v4l-dvb
solved my problem :popcorn:

Niko

---

### Post by tom56 on 2008-03-19
> **cocojambo said:**
> I got my DVB-T stick with product id 0x7070 up and running. Look at:

[http://www.linuxtv.org/pipermail/linux-dvb/2007-December/022177.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-December/022177.html)

to see how!

Bye,
Coco.

I have included this in the firmware package now

---

### Post by tom56 on 2008-03-19
I have updated the howto and firmware bundle

 Feel free to ask for help - make sure to include the output of dmesg from when you plug in your card (see tutorial). :D

---

### Post by baz.g on 2008-03-31
hi, i have managed to lay my hands on a seemingly unnamed DVB USB stick, all it says is DVB-T 355U

I followed your guide, without the extra modules and the first time i started kaffeine it said it could not find a DVB stick. So I installed the modules:

```

bazgrant@bazgrant-desktop:~$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device
bazgrant@bazgrant-desktop:~$ sudo modprobe dvb-bt8xx
bazgrant@bazgrant-desktop:~$ 

```

i rebooted the usb stick and restarted kaffeine and manually turned on the DVB client option but still nothing.

Here is the result of dmesg|tail:

```

bazgrant@bazgrant-desktop:~$ dmesg|tail
[29507.664362] usb 3-5: USB disconnect, address 108
[29507.774588] usb 3-5: new high speed USB device using ehci_hcd and address 109
[29507.828782] usb 3-5: configuration #1 chosen from 1 choice
[29507.828935] usb 3-5: USB disconnect, address 109
[29507.939162] usb 3-5: new high speed USB device using ehci_hcd and address 110
[29507.993363] usb 3-5: configuration #1 chosen from 1 choice
[29507.993513] usb 3-5: USB disconnect, address 110
[29508.103735] usb 3-5: new high speed USB device using ehci_hcd and address 111
[29508.157934] usb 3-5: configuration #1 chosen from 1 choice
[29508.158082] usb 3-5: USB disconnect, address 111

```

am i right in thinking that it has disconnected itself then and possibly the usb stick is faulty?

many thanks in advance :)

---

### Post by tom56 on 2008-04-01
Try this:
sudo modprobe em28xx

And post the result

---

### Post by baz.g on 2008-04-01
that just seems to hang when i put in that command, if kaffeine is running at the same time:

```

bazgrant@bazgrant-desktop:~$ sudo modprobe em28xx
[sudo] password for bazgrant:


```

but if kaffeine isnt running i dont get any response whatsoever:

```

bazgrant@bazgrant-desktop:~$ sudo modprobe em28xx
bazgrant@bazgrant-desktop:~$ 

```

it also says cannot bind info socket when i enable the dvb client in kaffeine :(

[IMG]http://i220.photobucket.com/albums/dd166/bazg13/screenshots/Screenshot.png[/IMG]

---

### Post by tom56 on 2008-04-01
Sorry, I should have been more clear with my instructions. First of all, forget about kaffeine for now.

1. Enter sudo modprobe em28xx, and when prompted type in your password and press enter.
2. Plug in your device.
3. Wait a few seconds, then enter dmesg|tail, and post the results here.

---

### Post by baz.g on 2008-04-02
ahh ok, will get that done when i get home from work today :)

thanks for your help so far :)

---

### Post by jjsh on 2008-04-02
Mmm, having some problems here. Mine is a Pinnacle DVB-T USB stick. All went OK, until I launch Kaffiene. I then get an error that it cannot bind to socket. Here is the output of dmesg|tail

```

jjsh@jjsh-desktop:~$ dmesg|tail
[ 4914.656000] usb 2-1: USB disconnect, address 4
[ 4942.156000] usb 2-1: new high speed USB device using ehci_hcd and address 5
[ 4942.288000] usb 2-1: configuration #1 chosen from 1 choice
[ 4991.604000] usb 2-1: USB disconnect, address 5
[ 4993.492000] usb 2-1: new high speed USB device using ehci_hcd and address 6
[ 4993.624000] usb 2-1: configuration #1 chosen from 1 choice
[ 5095.736000] Linux video capture interface: v2.00
[ 5095.808000] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[ 5095.812000] cx2388x dvb driver version 0.0.6 loaded
[ 5095.812000] cx8802_register_driver() ->registering driver type=dvb access=shared
```

Any ideas?

---

### Post by jmore9 on 2008-04-02
Hello !

I use a pinnacle 800i with qam support for tv viewing.  I have got the drivers loaded, the firmware in, have gotten it to scan all the cable channels. I only have cable internet so no tv stations.  When it scans it finds a lot of stations but no qam one can be viewed only two on analog .  Using winxp with his same card in same machine i get about 14 clear qam.  Still trying to figure out why this is.  Any suggestions ?

---

### Post by tom56 on 2008-04-02
> **jjsh said:**
> Mmm, having some problems here. Mine is a Pinnacle DVB-T USB stick

Any ideas?

Do you know the exact model number?

---

### Post by tom56 on 2008-04-02
> **jmore9 said:**
> Hello !

I use a pinnacle 800i with qam support for tv viewing.  I have got the drivers loaded, the firmware in, have gotten it to scan all the cable channels. I only have cable internet so no tv stations.  When it scans it finds a lot of stations but no qam one can be viewed only two on analog .  Using winxp with his same card in same machine i get about 14 clear qam.  Still trying to figure out why this is.  Any suggestions ?

I'll look into this and let you know if I think of anything

---

### Post by jjsh on 2008-04-02
I'm afraid not ~ the packaging just says 'Pinnacle PCTV Hybrid Pro Stick', and there are no markings on the device itself

---

### Post by tom56 on 2008-04-02
> **jjsh said:**
> I'm afraid not ~ the packaging just says 'Pinnacle PCTV Hybrid Pro Stick', and there are no markings on the device itself

The problem here is that the required modules aren't installed with the current Ubuntu kernel. The easiest thing is to wait for 2.6.25, when this will be supported. Hardy is currently using 2.6.24, so this might not be that far off.

Alternatively, you can use this guide, which I haven't used so can't comment on...
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

---

### Post by tom56 on 2008-04-02
> **jmore9 said:**
> Hello !

I use a pinnacle 800i with qam support for tv viewing.  I have got the drivers loaded, the firmware in, have gotten it to scan all the cable channels. I only have cable internet so no tv stations.  When it scans it finds a lot of stations but no qam one can be viewed only two on analog .  Using winxp with his same card in same machine i get about 14 clear qam.  Still trying to figure out why this is.  Any suggestions ?

Sounds like you only have the firmware for the analog tuner. I've found the right firmware but I'm not sure the correct modules are available using the current kernel.

It can't hurt to try the firmware though, so I'm adding it to the package. Try re-installing the firmware package on the first page, rebooting, and trying again.

---

### Post by jjsh on 2008-04-02
Tom

Thanks for the link, that's got it up and running. Much appreciated.

---

### Post by baz.g on 2008-04-02
hi tom, ran the command as you suggested, here is the output:

```

[  528.546684] em28xx v4l2 driver version 0.0.1 loaded
[  528.546777] usbcore: registered new interface driver em28xx
[  531.596141] usb 1-5: new high speed USB device using ehci_hcd and address 5
[  531.650352] usb 1-5: configuration #1 chosen from 1 choice

```

there were other lines above that but they referred to the network connection which i presume is of no interest to you :)

any ideas mate? :)

many thanks

---

### Post by tom56 on 2008-04-03
Hi baz.g

I'm beginning to think your device has the same tuner inside it as jjsh's. I refer you to my response to him. 

However, I am also beginning to think that the changes required in the kernel *HAVE* been committed after all, and all we're missing is the firmware. There's a huge amount of it at the end of that post so I might try adding it to the firmware package.

Unfortunately I'm a bit limited at the moment as to how much I can help as I am at my girlfriend's so don't have acces to an Ubuntu computer or my files.

I suggest you hold off for a few days and I'll add that firmware at the weekend.

:KS

---

### Post by baz.g on 2008-04-03
you are an absolute star tom :)

i look forward to the update :)

many thanks,

Baz

---

### Post by nosami on 2008-04-06
Thanks for the great guide Tom!

I'd like to recommend me-tv [http://me-tv.sourceforge.net/index.html](http://me-tv.sourceforge.net/index.html) for Freeview viewing on GNOME. It loads much faster than kaffeine (no KDE libs) and has built in EPG / sheduling / recording

---

### Post by tom56 on 2008-04-07
Hi all!

First of all, nosami is right about MeTV. It's a great app and I've been using it myself. It doesn't have quite the same level of features and stability as Kaffeine (e.g. subtitles are broken at the moment, no pausing of live TV), so I won't be changing the howto yet, but it is certainly a fantastic program and development seems to be fairly quick. It's only in its early stages, but I don't doubt that it'll soon be a match for Kaffeine.

Secondly, my Easter vacation has finished so I'm back at university. This means that the update I promised might be a little late coming, but I'll try and do it in a few days. My laptop doesn't have Ubuntu installed (wireless doesn't work for me in Gutsy), but I'll try Hardy soon and if it works then I'll do the packaging.

---

### Post by tom56 on 2008-04-15
What with updating to Hardy I completely forgot about this! Should be up by the end of tomorrow. Thanks all for being patient.

---

### Post by mattdavis90 on 2008-04-19
Hi All,

Hope you don't mind me joining in. I have a KWorld DVBT 355U, the device definitely works because I use it all the time in vista. I would love to change completely to ubuntu but at the minute have a few issues that need resolving before I can, this being one of them. I installed your firmware package and then did the following in terminal;
```
matt@matt-linux:~$ sudo modprobe em28xx
matt@matt-linux:~$ dmesg|tail
[ 1947.259696] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[ 1954.556425] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[ 3267.931888] usb 7-3.1: USB disconnect, address 3
[ 3281.153957] em28xx v4l2 driver version 0.0.1 loaded
[ 3281.154182] usbcore: registered new interface driver em28xx
[ 3286.014775] usb 7-3.1: new high speed USB device using ehci_hcd and address 6
[ 3286.109939] usb 7-3.1: configuration #1 chosen from 1 choice

```

I unplugged the device before running modprobe and replugged it in before running dmesg|tail to make sure the device had reinitialized. I can't seem to be able to get Kaffeine to do anything but MeTV and MythTV are convinced that theres no tuner. Any help would be much appreciated and I hope that the information I have provided is enough to help debugging.

Thanks,
Matt

---

### Post by tom56 on 2008-04-19
There's a new package today!

Make sure you get the newest one because I've kept the old one up too in case the new one breaks anything (it shouldn't though).

Any one with trouble please install the new package then re-post your issue.

I'm afraid responses from me may be few and far between as I'm quite busy at university at the moment. However if you do need any help just ask and I'll do my best. :D

---

### Post by mattdavis90 on 2008-04-21
I installed the new firmware packages and then ran 'sudo modprobe em28xx'. I then removed the device and re plugged it in and I get the same dmesg|tail again. I am not fully up to speed on the workings of linux but it seems that the system for mapping drivers to devices isn't picking the device up as being an em28xx based device although I am assured by many others on the internet that it is.

---

### Post by tom56 on 2008-04-21
Hmmm... maybe try the instutions on this page:
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

My hunch is that the current em28xx module (from the current Ubuntu kernel) doesn't map to your device, like you said. That link has a patched kernel with a newer em28xx module.

The device is definitely supported in some way as evidenced by this post:
[http://www.linuxtv.org/pipermail/linux-dvb/2006-September/012903.html](http://www.linuxtv.org/pipermail/linux-dvb/2006-September/012903.html)

A quick thought: before trying the link at the top, try doing the modprobe AFTER plugging in the stick. It shouldn't make a difference but anything's worth a shot.

N.B. The above link also contains firmware not included in my package. Bizarrely different sticks are supported by different firmwares that are named the same, therefore not all can be included in the package. It could be that you need a different firmware.

---

### Post by mattdavis90 on 2008-04-21
Hi again,

I have tried the instructions from the website given. It has taken a lot longer than hoped but I think I am finally getting somewhere. I downloaded their firmware package, I don't think this did anything as I have already got yours installed but anyway. I downloaded the kernel update thingy and tried to compile it but got loads and loads of errors. I noticed though when compiling that I was referred to [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) which has source code for much more recent drivers. I downloaded and compiled these but had no look since it still wasn't picking my device up properly because of the hardware id no. thing. To fix this with my limited linux and programming knowledge I ran lsusb and wrote down the hardware no. Then I added a section in the source code for my hardware to use a generic em2820 driver. This seemed to work because after recompiling and re-running modprobe my device registered and loaded the correct driver however it keeps complaining about PCM sound. This is where my limited knowledge comes to an end and no matter what I try I can't get the sound to register correctly. I have tried kaffeine and this doesn't detect any DVB devices, MeTV doesn't either but now MythTV is but it doesn't find any stations. I have posted my dmesg for you in case it is of use.

```
[ 1325.622769] usb 7-2: new high speed USB device using ehci_hcd and address 3
[ 1325.649316] usb 7-2: configuration #1 chosen from 1 choice
[ 1325.649796] em28xx new video device (eb1a:e357): interface 0, class 255
[ 1325.649807] em28xx Doesn't have usb audio class
[ 1325.649811] em28xx #0: Alternate settings: 8
[ 1325.649814] em28xx #0: Alternate setting 0, max size= 0
[ 1325.649819] em28xx #0: Alternate setting 1, max size= 0
[ 1325.649822] em28xx #0: Alternate setting 2, max size= 1448
[ 1325.649827] em28xx #0: Alternate setting 3, max size= 2048
[ 1325.649831] em28xx #0: Alternate setting 4, max size= 2304
[ 1325.649834] em28xx #0: Alternate setting 5, max size= 2580
[ 1325.649838] em28xx #0: Alternate setting 6, max size= 2892
[ 1325.649842] em28xx #0: Alternate setting 7, max size= 3072
[ 1325.652949] em28xx #0: em28xx chip ID = 35
[ 1326.637204] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 1326.637218] em28xx #0: Found Kworld DVB-T 355u
[ 1326.666273] em28xx_alsa: disagrees about version of symbol snd_pcm_new
[ 1326.666283] em28xx_alsa: Unknown symbol snd_pcm_new
[ 1326.666847] em28xx_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1326.666854] em28xx_alsa: Unknown symbol snd_pcm_lib_ioctl
[ 1326.667146] em28xx_alsa: disagrees about version of symbol snd_pcm_set_ops
[ 1326.667151] em28xx_alsa: Unknown symbol snd_pcm_set_ops
[ 1326.667258] em28xx_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 1326.667263] em28xx_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[ 1326.667573] em28xx_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[ 1326.667579] em28xx_alsa: Unknown symbol snd_pcm_period_elapsed
```

Thanks so much for all the help, I wouldn't have got anywhere near this close without you.

Matt

---

### Post by tom56 on 2008-06-10
Not able to test it myself, but anyone looking at this thread might find this handy:
[http://martinpitt.wordpress.com/2008/06/10/packaged-dvb-t-drivers-for-ubuntu-804/](http://martinpitt.wordpress.com/2008/06/10/packaged-dvb-t-drivers-for-ubuntu-804/)

---

### Post by tunznath on 2008-06-11
Hi heres the output of dmesg

[ 925.543248] tveeprom 1-0050: Hauppauge model 65018, rev B2C0, serial# 1054xxx
[ 925.543258] tveeprom 1-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[ 925.543262] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[ 925.543265] tveeprom 1-0050: audio processor is None (idx 0)
[ 925.543267] tveeprom 1-0050: has radio
[ 925.618089] tuner&#8217; 1-0061: chip found @ 0xc2 (em28xx #0)
[ 925.698393] xc2028 1-0061: creating new instance
[ 925.698403] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[ 925.744473] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 925.839267] tvp5150 1-005c: tvp5150am1 detected.
[ 925.987980] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[ 925.987991] em28xx #0: Found Hauppauge WinTV HVR 900 (R2)
[ 925.988037] usbcore: registered new interface driver em28xx
[ 926.075335] tvp5150 1-005c: tvp5150am1 detected.

How do i get it to work - pls help

---

### Post by tom56 on 2008-06-11
I'm afraid I can't really spare the time at the moment to offer any real help. However - have you tried the package above? I think it has the firmware file you need.

---

### Post by tunznath on 2008-06-11
Hi Tom
Thanks for pointing me to the package above - but thats how I got to this stage - from the package here 
[http://martinpitt.wordpress.com/2008/06/10/packaged-dvb-t-drivers-for-ubuntu-804/](http://martinpitt.wordpress.com/2008/06/10/packaged-dvb-t-drivers-for-ubuntu-804/) 

and now I am still stuck

---

### Post by tom56 on 2009-01-11
I am still too busy with uni to provide any real support for this howto, but I have updated with information about Zattoo. Hope this helps someone :)

---

### Post by bayvista on 2009-01-19
Hi...
Don't know if I'm trying the impossible. I have a HP laptop with an Hp Express card DVB-T TV Tuner. I have followed your instructions. Kaffeine is there but how do I run it I am using Ubuntu Hardy 8.04. Output from my dmesg:

david@hp-laptop:~$ dmesg | tail
[31044.320550] usb 6-2: configuration #1 chosen from 1 choice
[31251.488278] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[31251.491130] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[31251.491134] cx88/2: registering cx8802 driver, type: dvb access: shared
[31328.161147] bttv: driver version 0.9.17 loaded
[31328.161158] bttv: using 8 buffers with 2080k (520 pages) each for capture
[31328.170463] bt878: AUDIO driver version 0.0.0 loaded
[31376.887447] usb 6-2: USB disconnect, address 5
[31380.307748] usb 6-2: new high speed USB device using ehci_hcd and address 6
[31380.440752] usb 6-2: configuration #1 chosen from 1 choice
david@hp-laptop:~$ dmesg | tail
[31251.491134] cx88/2: registering cx8802 driver, type: dvb access: shared
[31328.161147] bttv: driver version 0.9.17 loaded
[31328.161158] bttv: using 8 buffers with 2080k (520 pages) each for capture
[31328.170463] bt878: AUDIO driver version 0.0.0 loaded
[31376.887447] usb 6-2: USB disconnect, address 5
[31380.307748] usb 6-2: new high speed USB device using ehci_hcd and address 6
[31380.440752] usb 6-2: configuration #1 chosen from 1 choice
[31398.289284] usb 6-2: USB disconnect, address 6
[31408.493205] usb 6-2: new high speed USB device using ehci_hcd and address 7
[31408.626091] usb 6-2: configuration #1 chosen from 1 choice
david@hp-laptop:~$ 

Many thanks if you can help.

---

### Post by tom56 on 2009-01-19
Sounds like it should be working. Start up Kaffiene from Applications->Sound and Video->Kaffiene. Open up the digital tv bit, and click the channels button to scan.

Here's a screenshot of what you're aiming for, if I recall correctly the channels button is the one on the top left (the small black square), but I'd just try each one till I found the right one.

[http://farm4.static.flickr.com/3151/2583287575_edf7b10f59_b.jpg](http://farm4.static.flickr.com/3151/2583287575_edf7b10f59_b.jpg)

---

### Post by bayvista on 2009-01-20
Nope. Kaffeine does not recognise my tuner as there is no TV button. I have loaded the latest Firmware file OK. Any other ideas?

---

### Post by bayvista on 2009-01-20
Just been poking around in Google and found that the Hp Express card is a rebadged Hauppauge HVR1500. Also, the drivers are included in a later kernel, V2.2. I will try to upgrade from Ubuntu 8.04 and see what happens.

---

### Post by bayvista on 2009-02-14
I seem to be getting close. I have now upgraded to Intrepid 8.10 and now have the TV in Kaffeine. It will tune but does not record any stations. Also, I could not load the following:

pam@hp-laptop:~$ sudo modprobe cx88-dvb
[sudo] password for pam: 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

Maybe this is what I need

---

### Post by tom56 on 2009-02-14
> **bayvista said:**
> I seem to be getting close. I have now upgraded to Intrepid 8.10 and now have the TV in Kaffeine. It will tune but does not record any stations. Also, I could not load the following:

pam@hp-laptop:~$ sudo modprobe cx88-dvb
[sudo] password for pam: 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.27-9-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

Maybe this is what I need

You probably don't need to do the modprobe bit, Ubuntu should take care of that itself. If you can watch TV using Kaffeine it's working. Not being able to record is, I expect, a separate problem. Check the Kaffeine settings, and whether you have enough free disk space.

---

### Post by dtmpower on 2009-02-25
dmesg|tail
[  201.626002] usb 5-3: new high speed USB device using ehci_hcd and address 7
[  201.758567] usb 5-3: configuration #1 chosen from 1 choice
[  201.758705] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[  201.758839] dvb-usb: will use the device's hardware PID filter (table count: 15).
[  201.759820] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom))
[  201.759971] DVB: registering frontend 0 (WideView USB DVB-T)...
[  201.760656] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb5/5-3/input/input8
[  201.809651] dvb-usb: schedule remote query interval to 300 msecs.
[  201.809663] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[  204.099408] dvb-usb: recv bulk message failed: -110



This is the message I get using a Freecom USB DVB-T stick.... it appears ok in Kaffeine - but the channel scan brings up nothing ,but both the strength and SNR meters flick up and down as it scans.... can anyone help me ?

John

---

### Post by coldmack on 2009-05-26
I have the Pinnacle PCTV usb stick that came out like in 2007(windows version, but with the pinnacle Mac software works with macs also) and it not working on my hardy machine. All I get with the kaffeine is cannot bind info socket, nothing else. MeTV says there is no drivers or something. What do you suggest I do?

In terminal when I typed lsusb this is the output. 
Bus 005 Device 006: ID 05dc:a720 Lexar Media, Inc. 
Bus 005 Device 005: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 004: ID 10f1:1a08  
Bus 005 Device 003: ID 0411:00be MelCo., Inc. 
Bus 005 Device 002: ID 2304:0227 Pinnacle Systems, Inc. [hex] 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by unclejac on 2009-05-27
hello :D Started following this thread, I figure I may as well get some use out of this Xmas present that someone gave me hehe.

Followed the guide, but Kaffine is not detecting the usb stick. 

```
betai@BETA:~$ dmesg|tail
[ 1849.763811] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 1875.351281] bttv: driver version 0.9.17 loaded
[ 1875.351287] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 1875.370919] bt878: AUDIO driver version 0.0.0 loaded
[ 1877.955295] usb 1-8: USB disconnect, address 5
[ 1882.333050] usb 1-8: new high speed USB device using ehci_hcd and address 6
[ 1882.472767] usb 1-8: configuration #1 chosen from 1 choice
[ 2471.662450] usb 1-8: USB disconnect, address 6
[ 2478.985058] usb 1-8: new high speed USB device using ehci_hcd and address 7
[ 2479.127459] usb 1-8: configuration #1 chosen from 1 choice
```


I see bayvista posted a similar output to what I have below:

```
betai@BETA:~$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device
```

Where can I get this module?

Am using 9.04 with a Hauppauge HVR-H006

Thanks in advance if anyone has time to help ;)

---

### Post by Fry-kun on 2010-07-17
The webpage at [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)  no longer exists. Does anyone have a backup of it?
I have a WinTV-HVR 950 (kernel says 980, a.k.a. em2882/em2883) and it wants firmware xc3028-v27.fw ...  no idea where to get it.

---

