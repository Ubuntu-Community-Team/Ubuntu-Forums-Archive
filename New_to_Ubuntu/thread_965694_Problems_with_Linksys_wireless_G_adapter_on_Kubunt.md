---
title: "Problems with Linksys wireless G adapter on Kubuntu"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by EdwardCullen on 2008-10-31
I am having problems with my Linksys wireless g network USB adapter.
The model is WUSB54GS
It is made for windows, but I found a driver, but I can not get it transferred from my windows computer which I am on to my Kubuntu laptop.

The Driver is RT2500 USB I think.

Does anyone know how to help me?

---

### Post by stephanvaningen on 2008-10-31
You don't need to port from windows, you can get a native .so-file and do a mod-probe if I remember well... give me a few minutes to find the instructions...

---

### Post by EdwardCullen on 2008-10-31
Okay Thank you, I am very confused :(

---

### Post by EdwardCullen on 2008-10-31
Anyone else?

---

### Post by stephanvaningen on 2008-10-31
As far as I know, ther's a rt2500usb.ko module in the distro now. I have on my machine this file:
 ```
/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
```
Which gets loaded after running this command:
 ```
sudo modprobe rt2500usb
```
I'ld suggest to furst run this command and after that load the USB device.

---

### Post by stephanvaningen on 2008-10-31
> **EdwardCullen said:**
> Anyone else?
patience friend ;-)

---

### Post by stephanvaningen on 2008-10-31
Some tech background info?:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/wusb54gv4-getting-access-point-not-associated-590377/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/wusb54gv4-getting-access-point-not-associated-590377/)

---

### Post by EdwardCullen on 2008-10-31
Alright, how about the Setup.exe on the disk, I will not need it?

---

### Post by EdwardCullen on 2008-10-31
> **stephanvaningen said:**
> Some tech background info?:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/wusb54gv4-getting-access-point-not-associated-590377/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/wusb54gv4-getting-access-point-not-associated-590377/)

I think this is a diffrent model

---

### Post by stephanvaningen on 2008-10-31
Nope, forget about all that,
devices should work out-of-the-box setup.exe is for windoze...

---

### Post by LookTJ on 2008-10-31
Do a lshw for us, copy the info. most chipsets by linksys/cisco is a rt61 or rt2500 but it depends on your rev model.

---

### Post by EdwardCullen on 2008-10-31
Thanks a lot.
When I type in my password for the command, is it suppose to give me any output?

---

### Post by EdwardCullen on 2008-10-31
I have no way to copy output from the terminal. I do not have a USB on me to transfer it with..

---

### Post by LookTJ on 2008-10-31
> **EdwardCullen said:**
> I have no way to copy output from the terminal. I do not have a USB on me to transfer it with..Are you saying that you can't copy and paste into gedit and save as a txt onto a flashdrive? Because that would suck. :( Hmm I'll wait until you do :)

---

### Post by EdwardCullen on 2008-10-31
I dont have a flashdrive on me right now and wont till about 12am Eastern Time...

---

### Post by LookTJ on 2008-10-31
I've found something close to what your card model is. it is a usb also. Linksys WUSB54GC

It uses the rt73(ralink 2573) driver(used by most usb dongles)

---

### Post by LookTJ on 2008-10-31
[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) here's the daily tarball for your card. Copy the files onto a flash drive. 

here's an April 07 howto: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

and an ArchWiki howto: [http://wiki.archlinux.org/index.php/RT73_Wireless](http://wiki.archlinux.org/index.php/RT73_Wireless)

Whichever one you prefer

---

### Post by EdwardCullen on 2008-10-31
I got my laptop hooked up to the wired connection on kubuntu, now what do I need to install to get that to work?

---

### Post by EdwardCullen on 2008-10-31
Help anyone?

---

### Post by LookTJ on 2008-10-31
> **EdwardCullen said:**
> I got my laptop hooked up to the wired connection on kubuntu, now what do I need to install to get that to work?
```
lspci | grep Network
```
I would like to know your network cards

---

### Post by LookTJ on 2008-10-31
I'm sorry, Ii screwed up the command it's

```
lspci | grep Ethernet
```

---

### Post by EdwardCullen on 2008-10-31
> 02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)

That is what it done...

---

### Post by EdwardCullen on 2008-10-31
umm..taylor you on?

---

### Post by RealG187 on 2008-11-01
I have the WUSB54G.

It worked on 6.10.

It didn't on 7.10 until I did [this]("http://ubuntuforums.org/archive/index.php/t-588045.html").

not sure about 8.04 as I only have it on my Laptop (built in wireless) and the "Family PC" (Wired)

---

### Post by LookTJ on 2008-11-01
> **EdwardCullen said:**
> umm..taylor you on?Sorry, I was busy
  earlier... follow what post #17 and the post above says.

---

### Post by EdwardCullen on 2008-11-01
I am still confused how to install things.

---

### Post by RealG187 on 2008-11-01
What version are you using? I got my WUSB54G working without a driver.

---

### Post by flutti-tutti on 2008-11-02
I would like to add this, if I may.

The 32bit version of Ubuntu 8.10 has worked with WUSB54GC and WPA setup; the Kubuntu-Desktop has been added and still worked.  (Wireless network setup becomes actually very easy on 8.10.)

The 64bit version of Ubuntu 8.10 does not work, while Ubuntu 8.04 64bit does.

---

### Post by firecat53 on 2008-11-14
I have the WUSB54GC (this is the rt73usb driver) working great on Ubuntu(Gnome 32 bit) 8.10 with the following small modifications. Please note it worked out of the box complete with WPA using NetworkManager, except for suspending, which would freeze the computer every other suspend (same thing with WICD and the Rutilt). This computer is also a desktop, so I've given up the ability to easily switch networks (which I don't need), but gained the suspend to RAM which is veeeery quiet in the family room :)

1. sudo aptitude remove network-manager networkmanager gnome (or remove w/ Synaptic)
2. sudo gedit /etc/network/interfaces and make it look something like:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
address 192.168.0.102
netmask 255.255.255.0
network 192.168.0.1 
gateway 192.168.0.1 
    pre-up ifconfig wlan0 up
    pre-up iwconfig wlan0 essid myessid
    pre-up iwconfig wlan0 mode Managed
        pre-up /sbin/wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -BD wext -iwlan0
```

3. sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
  - Make it look like:
[code]network={
        ssid="myessied"
        psk="mypassphrase"
        priority=5
}

4. sudo /etc/init.d/networking restart
5. Open firefox and type about:config in the address bar. Find the value 'toolkit.networkmanager.disable' and double-click it to change the value to true. This prevents your browser starting up in offline mode each time because networkmanager isn't installed.
6. You can add the Gnome Network Monitor applet (just right click on the bar and find it under 'add applet') if you want to see that you are connected.

Hopefully that works for someone, and I hope I didn't forget anything!

Good luck!

Scott

---

