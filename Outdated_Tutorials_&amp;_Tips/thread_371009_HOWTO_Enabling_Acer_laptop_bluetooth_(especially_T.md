---
title: "HOWTO: Enabling Acer laptop bluetooth (especially Travelmate series, acerhk)"
date: 2007-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by gvoima on 2007-02-26
I didn't find so much information on how to enable the Acer bluetooth Broadcom device on this forum. So I made up a little howto, hope it helps!

This hotwo is based on information i mainly collected from **[http://users.tkk.fi/~jwagner/tablet/suse93.htm](http://users.tkk.fi/~jwagner/tablet/suse93.htm)**

I tested this only on my Acer 312XMi (C310 Travelmate series) laptop.
I try to support this thread as good as I can.

The test was made on Ubuntu 6.10 Edgy, kernel 2.6.17-11-generic, on 32bit architecture.

Enabling the bluetooth is based on the Acer Hotkey driver for Linux, now, notice that this driver (module) came with Edgy release, so I will not guide you through on how to compile it.

More information on how to download and compile the driver is found from **[http://www.cakey.de/acerhk/](http://www.cakey.de/acerhk/)**. (You really should check out this site and the included README/INSTALL instructions.)

So, in Ubuntu 6.10 Edgy release, there is (should be) a module called acerhk.

On my Acer C310 Tablet PC, this enabled the buttons above the keyboard (bluetooth, wlan, email etc.), the bluetooth device and the ability to control email led (if anyone really needs it anywhere).
The buttons on the screen (tablet buttons) are also supported, but doesn't show up on xev, it only produces a bunch of dmesg errors if you don't map them (mapping them is not explained in this guide).



**1.** Loading the module:
```
sudo modprobe acerhk
```

After that you shouldn't get any errors. (if you did, read from the beginning about compiling the module for your needs).


**Update:**
*Note! On Hardy (8.04 LTS) if your wlan-card uses the module ipw2200, you can't get the wireless led working unless you load the module with the option **led=1**, e.g. the ipw2200 that I have -> modprobe ipw2200 led=1. You can add this line to /etc/modprobe.d/options*


Ensure that the module got loaded:
```
lsmod | grep "acerhk"
```

You should see something like this:
```
acerhk                 26492  0
```


**2.** When you loaded the module acerhk, a driver should have appeared under the /proc/ filesystem (these files here represent the current state of the kernel).
So go and check if there is path like this in /proc:

**/proc/driver/acerhk/**

This may vary, but based on which laptop you run, under that directory should be these files:
```
--w--w--w- 1 root root 0 2007-02-26 18:55 blueled
-r--r--r-- 1 root root 0 2007-02-26 18:55 info
-r--r--r-- 1 root root 0 2007-02-26 18:55 key
--w--w--w- 1 root root 0 2007-02-26 18:55 led
--w--w--w- 1 root root 0 2007-02-26 18:55 wirelessled
```
Notice the **blueled** file above.
The way how the bluetooth behaves is, when you "enable" the **blueled**, which turns on the Bluetooth LED, also enables the Bluetooth device.

So, now go ahead and enable the device with command:
```
echo "1" > /proc/driver/acerhk/blueled
```
Now Gnome should report about a device being detected. If not, the last rows in **dmesg** command should report something like this:
```
[17179879.700000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[17179879.920000] usb 4-1: configuration #1 chosen from 1 choice
[17179880.064000] Bluetooth: HCI USB driver ver 2.9
[17179880.068000] usbcore: registered new driver hci_usb
```
and the Bluetooth light on your laptop should turn on (if it has one).

Notice that my bluetooth was detected on the usb bus.
So, list usb devices:
```
lsusb
```
and you should see something like this:
```
Bus 005 Device 001: ID 0000:0000  
**Bus 004 Device 003: ID 0a5c:200a Broadcom Corp.** 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c518 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
The Broadcom device above is the bluetooth device that was not detected before.


**3.** There is plenty of HOWTO:s on how to install bluetooth tools (bluez, hcitool etc.). So please use the search :)

**I now assume that you have the bluetooth tools installed** so let's go on.

Issue the command:
```
hcitool dev
```
and you should now see that the hcitool actually found a device, in my case it was:
```
Devices:
        hci0    00:0B:6B:90:B5:1C
```
If your device is not on the usb bus and lsusb didn't find it, **hcitool dev** still might. And this means that your bluetooth device is ready to be used :)

From this point on (if successful) you can relate to other HOWTO:s, on how to use the bluetooth tools and configure the device.


**4.** Last but not least, how to turn the bluetooth off.
If you already didn't guess, instead of echoing "1" to the device, you can turn it off by echoing "0" to it.
So:
```
echo "0" > /proc/driver/acerhk/blueled
```
this turns it off.


**5.** You probably noticed that there is some other files under /proc/driver/acerhk/.

- **blueled** is for bluetooth
- **wirelessled** turns on/off your wlan led (also turns off the DEVICE!) the LED didn't work for me. My WLAN was found without this module on install, but the LED is not working.
- **led** is for the e-mail led that blinks. On my C310 there is a e-mail button that also blink green when you enable this.

all those above can be turned on/off with the **echo "x" > xxx** command.

you can use the **cat** command to following files:
- **info** has some information of the module
- **key**, I have no idea what this is used for.


**6.** On Ubuntu Edgy, there is a file called **/etc/modules**, you can add **acerhk** to this file, this makes sure that it is loaded on every reboot.

If you want to remove **acerhk**, just issue this command:
```
sudo rmmod acerhk
```


So, all the above folders/files/devices etc. is what was found on my laptop, yours may vary!


Please report if you had any success with your bluetooth, include the laptop maker/model, what buttons and devices were found and what kernel & architecture was used.

Thank you.

---

### Post by Reschat on 2007-03-31
*EDIT* Deleted. A completely other problem.

---

### Post by jterroux on 2007-04-06
I got the bluetooth LED to turn on and my laptop now works with my bluetooth mouse.  Any ideas on how to get the bluetooth button on the laptop to enable the bluetooth.  It would be much easier to use the bluetooth button rather than type echo on > /proc/driver/acerhk/blueled and then sudo hidd --search to connect my mouse.

---

### Post by mrojas73 on 2007-04-08
I followed your guide and I get to the end of it without any errors but no blue led.  The drivers are the same as yours.  I have an Acer Aspire 5601AWLMi.

---

### Post by Zdravko on 2007-04-08
I have an ACER TravelMate 2493NWLMi. Does the article apply to it, too?

---

### Post by jterroux on 2007-04-08
All I had to do to get my bluetooth mouse to work was install the acerhk drivers (i followed this guide on how to load the acerhk drivers: [http://ubuntuforums.org/showthread.php?p=2382786]("http://ubuntuforums.org/showthread.php?p=2382786"))
Then all i have to do is type "echo on > /proc/driver/acerhk/blueled"  the led comes on and i type "sudo hidd --search" and make sure your mouse or device is in discover mode (I have to push the reset button on the bottom of my mouse to get it to connect) and it will say it found device and give a mac address XX:XX:... and it should be connected. 

I only have connected my mouse so far, so I do not know if it as easy to connect other devices.  

I got my acerhk drivers from: [http://freshmeat.net/projects/acerhk/]("http://freshmeat.net/projects/acerhk/")
The drivers on site say acerhk-current version.  so they might be newer then the ones on sourceforge.net

I have written a script to do the echo on > .. and sudo hidd.. stuff and make it load at startup.  
I have not however made my bluetooth button on my keyboard work with this yet.

---

### Post by gvoima on 2007-04-09
> **jterroux said:**
> All I had to do to get my bluetooth mouse to work was install the acerhk drivers (i followed this guide on how to load the acerhk drivers: [http://ubuntuforums.org/showthread.php?p=2382786]("http://ubuntuforums.org/showthread.php?p=2382786"))
Then all i have to do is type "echo on > /proc/driver/acerhk/blueled"  the led comes on and i type "sudo hidd --search" and make sure your mouse or device is in discover mode (I have to push the reset button on the bottom of my mouse to get it to connect) and it will say it found device and give a mac address XX:XX:... and it should be connected. 

I only have connected my mouse so far, so I do not know if it as easy to connect other devices.  

I got my acerhk drivers from: [http://freshmeat.net/projects/acerhk/]("http://freshmeat.net/projects/acerhk/")
The drivers on site say acerhk-current version.  so they might be newer then the ones on sourceforge.net

I have written a script to do the echo on > .. and sudo hidd.. stuff and make it load at startup.  
I have not however made my bluetooth button on my keyboard work with this yet.

On my laptop the BT-button stopped working without a reason that I couldn't find...and I don't even use it anyway, I made myself a automated BT-script when i use it with my PPP connection (GRPS).

But, when pressing the button, acerhk should produce a kernel event that you can view with dmesg, or capture it with xev. If it produces a event, it can be remapped to for example your own script.
I haven't familiarised myself on that how to remap buttons to certain files on gnome, i know it can be done in KDE. But not sure about gnome. :)

---

### Post by gvoima on 2007-04-09
And for the BT-support. Notice that on the site [http://www.cakey.de/acerhk/]("http://www.cakey.de/acerhk/") it states that > (some models are only partially supported) and > The newer Travelmate series aren't supported very well, since Acer uses different hardware. and this doesn't apply to the BT-part at all.

It's a lucky strike to get the actual module working, 'cause acer doesn't give any information for how to handle their hardware.

I have no idea is the module even continued?

And this module only controls for example the LEDs, extra button events and wlan hardware on some models (listed on the site above).
And it appears that the actual BT hardware works so that when you turn the led on, you turn the device on. That means that you actually don't use the BT-hardware directly while controlling it through this module.
Funny way to do it, but this makes it easy to use and power efficient.


Correct me if I'm wrong.

---

### Post by gvoima on 2007-04-09
> **mrojas73 said:**
> I followed your guide and I get to the end of it without any errors but no blue led.  The drivers are the same as yours.  I have an Acer Aspire 5601AWLMi.


> I have an ACER TravelMate 2493NWLMi. Does the article apply to it, too?


Check the current list on the topic link. If your laptop isn't listed, i can't really help you on that matter :(

---

### Post by koshari on 2007-05-06
i have an Acer TM5625WSMi with bluetooth and cannot get it to work, 


anyone have any pointers i can try, 

basicly i cannot turn the bluetooth tranceiver on so as it will be recigniced on the USB bus.

the hotkey doesnt work, 

i have it working in windows and this is the only thisn stopping me wiping windows and reclaiming that space for linux.

windows device manager wont show the device at all until you hit the bluetooth buton then it appears through device managet through the usb bus.

i have little doubt that if i can activate the device hal will pick it up and i will be right, but it is being able to switchi it on that eludes me,

---

### Post by gvoima on 2007-05-13
> **koshari said:**
> i have an Acer TM5625WSMi with bluetooth and cannot get it to work, 


anyone have any pointers i can try, 

basicly i cannot turn the bluetooth tranceiver on so as it will be recigniced on the USB bus.

the hotkey doesnt work...

hmmm, so you mean when you load the module, you can see the /proc/driver/acerhk/blueled path and echoing "on" or "1" does nothing? Or you can't se it at all? And can you even load it without or with errors?

In the acerhk package there is a README with some module parameters, you should try to load the module with them.

---

### Post by koshari on 2007-05-14
> hmmm, so you mean when you load the module, you can see the /proc/driver/acerhk/blueled path and echoing "on" or "1" does nothing? 

precisely. i do get a message in dmesg after echoing on/1 ect  like the one i get when i actually press the button, however the device is simply not connecting to the usb bus or powering up.


> In the acerhk package there is a README with some module parameters, you should try to load the module with them.

i can load the module and it is shown in lsmod.

however i have a sneaking suspiscion that acer have changed the way that the bluetooth device is switched on/connected to the usb bus because none of the ways described in on various acerhk tuitions will let me turn the device on,

---

### Post by gvoima on 2007-05-15
> **koshari said:**
> i can load the module and it is shown in lsmod.
however i have a sneaking suspiscion that acer have changed the way that the bluetooth device is switched on/connected to the usb bus because none of the ways described in on various acerhk tuitions will let me turn the device on,

What I meant was, that you should try to load the module with kernel polling etc. the modes are descriped in the README.

But, it's true that Acer could have changed the behaviour, what this module does, is that it only enables the LED of the bluetooth and the bt dongle is connected so, that it powers up with the LED.

And the module is IMHO discontinued, so no luck for you if you're not a programmer, I myself don't have so much time this summer that I could look into the matter more closely. :neutral:

---

### Post by koshari on 2007-05-27
well just for the reference of others that may have the same notebook, i got my bluetooth going with  the
```
force_series=610
``` switch

all is well now :-)

---

### Post by gvoima on 2007-05-29
Yes indeed, as for others in the future please do check the README in acerhk-0.5.35.tgz and the [http://www.cakey.de/acerhk/]("http://www.cakey.de/acerhk/") site for more information on the modes with which you can load the module :)

---

### Post by angelman99 on 2007-11-08
I'm a newbie, where do I put in the switch to force it to a model.
I saw in the file a 5020 which I hope is close enough to my 5630, but I have no idea how to make that happen.

Thanks,

---

### Post by gvoima on 2007-11-08
Well, on the acerhk module page, there is a Aspire model 5610 which says (force_series=2020).

In the readme it states that, when loading the module (modprobe acerhk), you can insert parameters to it, force_series is one of them.
e.g. modprobe acerhk force_series=2020
For possible force_series values, look at setup_model_features() function.

Hope this helps :)

---

### Post by Ltmboy on 2007-12-10
I followed the howto, but I still can't enable bluetooth on my Acer 5601 AWLMI. I tried enabling it using ```
sudo modprobe acerhk force_series=2020
``` but still no luck. When I run ```
cat /proc/driver/acerhk/info
``` I get the following: ```
Acer hotkeys version 0.5.34
Model(Type)     : TravelMate xxxx(unknown)
request handler : 0xc00fde60
CMOS index      : not available
kernel polling  : active
autoswitch wlan : disabled
```

The mail, wireless and internet buttons work, just not the bluetooth. :confused: So now I'm kinda stuck. Any help would be great.

---

### Post by gvoima on 2007-12-12
> **Ltmboy said:**
> The mail, wireless and internet buttons work, just not the bluetooth. :confused: So now I'm kinda stuck. Any help would be great.
AFAIK, acer have updated the hardware on some laptops, so it acts differently and is not compatible with the current module. Besides, it's not under development anymore, I guess you're out of luck if someone haven't got a newer version of this module :(
Or a different approach..

---

### Post by OnuJack on 2008-06-05
Thank you for the nice How-To. I was able to activate BT on my Aspire 3023 Wlmi without any problems (Using Ubuntu 8.04TLS with 2.6.24.18 kernel). So far I have tried testing it with Jabra BT620s headset and my phone/pda E-ten glofiish m600 which runs WM6.
The headset has not been able to connect yet - gives an error: Couldn't display "obex://[00:13:17:71:2F:99]/". Error: Host down
Please select another viewer and try again. - it connects just fine to the PDA, so the problem has to be with BT on the machine

I am able to browse for files on my PDA but not able to transfer anything yet. Gives an error: Operation not supported by backend

will try to solve these issues

---

### Post by gvoima on 2008-06-05
Glad to be of service.

---

### Post by yuta on 2008-07-11
Arghh....

Darn...

Doesn't work on Travelmate 2480...

I wish someone could continue acerhk project...

*I know I should had bought a dell instead...*:lolflag:

---

### Post by arm-c on 2009-02-02
If you are reading this and using the AcerHK driver, you may find this little utility/GUI helpful.

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

I wrote it to address my own problems with turning on and off the bluetooth radio.

READEME file is a must read.

---

### Post by gvoima on 2009-02-03
> **arm-c said:**
> If you are reading this and using the AcerHK driver, you may find this little utility/GUI helpful.

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

I wrote it to address my own problems with turning on and off the bluetooth radio.

READEME file is a must read.

Thank you of this little program. I'm sure someone will be pleased about it :)

---

### Post by hadynd88 on 2009-04-10
Excellent HowTo!

I'm running a C310 as well but on Intrepid and was pulling my hair out trying to 'discover' my bluetooth device to sync my phone contacts (I just hate cables). You don't ned to download or compile anything from my experience it was all sitting there ready to go, someone just had to push the button.

Thanks again!

---

### Post by gvoima on 2009-04-11
> **hadynd88 said:**
> Excellent HowTo!

I'm running a C310 as well but on Intrepid and was pulling my hair out trying to 'discover' my bluetooth device to sync my phone contacts (I just hate cables). You don't ned to download or compile anything from my experience it was all sitting there ready to go, someone just had to push the button.

Thanks again!

Yes, the newer ubuntu versions apparently has this module already loaded, so you don't need to load it separetly after hardy heron I think. I'm not sure about this though, moved from ubuntu to debian a long time ago.

And if you use gnome, it's quite easy to map the bluetooth button from configuration editor to a script file, that then does whatever needed :)

---

### Post by arm-c on 2009-06-21
Re: AcerHK GUI -- GUI for users of the 'acerhk' driver to control wireless/bluetooth
Version 0.5 of the AcerHK GUI is now released and available for download on SourceForge!

My main thread here that I post updates is located at the following URL:
[http://ubuntuforums.org/showthread.php?t=1059704](http://ubuntuforums.org/showthread.php?t=1059704)

I am open to suggestions on what additional functionality I should work into my development plan.  I'm not a programmer by trade and this is my first real program... which I happen to be writing as I am learning! :)

---

### Post by arm-c on 2009-06-23
Version 0.6 of AcerHK GUI has been released.  It now simplifies configuration for new users.  Feeback welcome.  More info at previous link in message 27.

---

