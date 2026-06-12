---
title: "Windows Wireless Drivers Help"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by k scott on 2008-07-31
I have a Belkin 54g Wireless USB adapter, as well as the CD that came with it.  I have copied the rt73.inf file to the desktop, but whenever I try to load it into Windows Wireless Drivers it keeps saying "Invalid Driver."  What could the problem be?

---

### Post by superprash2003 on 2008-07-31
once you insert the usb adapter, go to mycomputer->Device manager and there you should find your usb ddapter with a yellow exclamation mark, right click on it and click on Reinstall driver/update driver and then select "Search for drivers in cd rom drive" or manually browse to the cd drive.. and it should pick up the drivers..

---

### Post by caljohnsmith on 2008-07-31
That Windows Wireless Drivers program, since it is a GUI for ndiswrapper, it needs both the .inf and .sys files for your wireless driver. But it's confusing because you need to have the .sys file in the same folder as the .inf file, and then ndiswrapper will install the driver properly; but the program will only ask for the .inf file. That never made sense to me, because I think if the program needs both files, it should specifically ask the user for the location of both of them; it shouldn't assume the .sys file is in the same folder as the .inf file.

---

### Post by k scott on 2008-07-31
Ok, I placed the inf and the sys file in the same location and it worked.  Now it says that the hardware is present, but when I go to System> Admin.> Network the "Wireless Connection" isn't there.  Any ideas?

---

### Post by caljohnsmith on 2008-08-01
Make sure the ndiswrapper module is loaded first:
```
sudo modprobe ndiswrapper
```
And then:
```
ifconfig
```
That should show your wireless interface, most likely wlan0 or possibly eth1. Then do:
```
sudo iwlist <interface> scan
```
Where <interface> is you wireless interface. That should show a list of available networks in the area.

---

### Post by k scott on 2008-08-01
> **caljohnsmith said:**
> Make sure the ndiswrapper module is loaded first:
```
sudo modprobe ndiswrapper
```


Do I do this before or after I install the driver in Windows Wireless Drivers?

---

### Post by caljohnsmith on 2008-08-01
Do that command after you install the wireless drivers. :)

---

### Post by james_vanb on 2008-08-01
I've used the Belkin USB on a couple of computers - In both Gutsy and Hardy.  This is the process I use if you want to compare against the process you have used:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:


```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```
Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```
Reboot

---

### Post by MichaelSM on 2009-04-14
WOW!

Thank you, James_VanB.

I'd completely mangled my wireless setup by making errors with Compat-Wireless trying to get a Netgear WG111v3 usb adaptor to work ...

So now I'm back with my TP-LINK (rt73 chipset) installed and doing fine.

Which was perfect out of the box until I wrecked things.

One thing to add to your superb instructions:

After the final reboot, the usb adaptor was flashing away merrily, so got into Wcid which detected the interface, refound my old passphrase, so I hit CONNECT which it did, but it didn't. The connection was up, but I couldn't get on the Net.

Intuitive solution: unplug then re-plug the adaptor.

All fine now.:guitar:

Now that I know how to repair the wifi interface, I'll have another go at the WG111v3 usb adaptor install using your instructions, except that(guessing here) there's no need to blacklist anything because 8.10 came pre-loaded with rt73 gear - which I killed - and there shouldn't be those issues with WG111v3 which 8.10 has never heard of.... until soon.

Cheers and thanks again.

Mike.

PS. re. Netgear WG111v3 usb adaptor. That .inf would never load successfully from Desktop as a drag into the ndisgtk gui.

However:

sudo ndiswrapper -i /home/michael/WG111v3/WG111v3.info

(once I'd created that folder with the .sys and .inf inside)

worked perfectly. In a running session, I unplugged the TP-LINK adaptor and replaced it with the Netgear WG111v3 adaptor. ALL GOOD!

Note to anyone else who reads this:

The inputs are all majorly case-sensitive! 

wg111v3 is not the same as WG111v3, or wg111V3, or WG111V3. What one types into Terminal with the command mentioned above must reflect precisely the name of one's home folder, the name one has given to the folder containing the .inf file, and the exact case of the name of that .inf file.

I learnt that the hard way...most inputs AREN'T case-sensitive ...

Couldn't be happier!

Thanks again, James.

---

### Post by james_vanb on 2009-04-14
Glad you got it sorted out.

---

### Post by MichaelSM on 2009-04-15
Hi again, James.

One small hitch which I don't know how to correct ...help if you can.

The Netgear WG111v3 adaptor won't connect from boot. Oh well.

The TP-LINK rt73 works always either at boot, or hotplugged.

However; once the connection has been established, I can unplug the 

TP-LINK, hotplug the Netgear adaptor, and Wicd will flash through its

connection sequence and connect via the Netgear adaptor.....

Obviously drivers for both are installed in ndiswrapper.

It's not quite an either/or issue. All I can think of is that there may be some WG111v3 drivers hanging around in some other place after a previous attempt. I wouldn't know where to start with that issue.

Hope I'm not wasting your time.

Cheers,

Mike.

---

### Post by james_vanb on 2009-04-15
If you have an old driver hanging around that might be conflicting, get the Netgear USB working and run the following:

```
ndiswrapper -l
```

This should show that the Netgear driver is installed and the hardware present.  It may also list an alternate driver.  You can try blacklisting the alternate, reboot and see if it connects.  If not try the above code and see if another alternate driver has been associated - blacklist and try again.

If the adapter flashes when you boot, it may be a configuration issue with wicd.  I had problems getting NetworkManager to connect with WEP enabled.  Tried wicd and couldn't get it configured right.  Ended up installing WiFi Radar.  No problems since.

Good luck.

---

