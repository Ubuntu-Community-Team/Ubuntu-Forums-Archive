---
title: "Getting my Netgear WG111T working"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by m_ad on 2008-07-17
I just installed Xubuntu on my last computer in the house (been installing a lot lately). I have a Netgear WG111T connected via USB. Xubuntu doesn't recognize it (I don't think) or any wireless networks. I've read around and found ndiswrapper, which I used to install the xp driver for the device with no errors. 'ndiswrapper -l' shows it as installed.

I've never configured a wireless adapter before, can anyone help me?

---

### Post by phantomjoker on 2008-07-17
sounds like you need the drivers for your
> Netgear WG111T
So does it come with a disk or if not grab them from online -
[http://kbserver.netgear.com/products/WG111T.asp]("http://kbserver.netgear.com/products/WG111T.asp")
is this the help you need? post back if not

---

### Post by m_ad on 2008-07-17
> **phantomjoker said:**
> sounds like you need the drivers for your

So does it come with a disk or if not grab them from online -
[http://kbserver.netgear.com/products/WG111T.asp]("http://kbserver.netgear.com/products/WG111T.asp")
is this the help you need? post back if not

this is my device. I've installed those drivers using ndiswrapper, but I don't know what to do now :confused:

---

### Post by phantomjoker on 2008-07-17
ok so go into your system>administrator>hardware drivers and see if its located.. it should be.

If not then it hasn't been installed

If it is then move on to system>administrator>network and try to locate an internet connection by confuguring your network.

post back if you need.

---

### Post by m_ad on 2008-07-17
> **phantomjoker said:**
> ok so go into your system>administrator>hardware drivers and see if its located.. it should be.

If not then it hasn't been installed

If it is then move on to system>administrator>network and try to locate an internet connection by confuguring your network.

post back if you need.

yeah, the driver isn't located in hardware drivers :(

---

### Post by m_ad on 2008-07-17
'ndiswrapper -l' returns
```
netwg11t: Driver installed.
```

(which is the driver for this device)

---

### Post by phantomjoker on 2008-07-17
right so you've downloaded and installed the restricted drivers and its not there...

give me a min - im sure i've seen the code in another thread. I'll have a look

---

### Post by phantomjoker on 2008-07-17
ok - i think this is the code 

-get-apt -netwg11t

but im not sure...

---

### Post by phantomjoker on 2008-07-17
[duplicate post]

---

### Post by phantomjoker on 2008-07-17
heres something else that sometimes works - go into system>administration>hardware testing

obviously with the netgear in - this is sometimes enough for the computer to register the hardware - although I don't know whether it does USB testing.

---

### Post by m_ad on 2008-07-17
> **phantomjoker said:**
> ok - i think this is the code 

-get-apt -netwg11t

but im not sure...

I don't have the internet to access the repos, and I can't find any package starting with 'netwg' on the Ubuntu cd either. I don't think there is a package for this driver in the repos anywhere..

---

### Post by ibuclaw on 2008-07-17
ndiswrapper works like so:

To install a driver:
```
sudo ndiswrapper -i name.inf
```

To load the driver
```
sudo modprobe ndiswrapper
```

You don't need restricted drivers or anything from the apt repositories, because the device isn't supported natively. (Lucky we have ndiswrapper to use windows drivers instead :D)

I've  used the WG111T model many a times with Backtrack, if you stare at the device when you hit enter on the above command, you should see the blue light come on, it is a sign that it is active and scanning.

Then use your wireless network app to connect to your router.

Regards
Iain

---

### Post by m_ad on 2008-07-17
that's what I thought! however, 'sudo modprobe ndiswrapper' does not turn the light on nor give any indication that the device is working properly.


by the way, what is the wireless application in xubuntu? the network connection icon in the system tray only has "Wired Connection" (which is greyed out) and "Manually configure."

---

### Post by ibuclaw on 2008-07-17
hmm...

Can you post the output of this command for us?

```
ifconfig
```

Regards
Iain

---

### Post by m_ad on 2008-07-17
> **tinivole said:**
> hmm...

Can you post the output of this command for us?

```
ifconfig
```

Regards
Iain

do you need the whole output? :) I can write it all down if I have to. but there is an 'eth0' and 'lo' with a bunch of other stuff after them..

---

### Post by ibuclaw on 2008-07-17
Maximise the terminal, run the command, and you can click and drag the mouse to select it all.

Then press **Ctrl+Shift+C** to copy it. **Ctrl+V** to paste it in firefox, of course ;)

Also, can you put it in [ CODE ]  [ /CODE ] brackets too, for easy reading. (just remove the spaces between the brackets and you'll have a box like this)
```
text
```

[EDIT]
Alternately, you can run:
```
iwconfig > iwconfig.txt
```
It will show the most relevant information. Plus, it will redirect the output to a text file for you to open and copy from there.

Regards
Iain

---

### Post by m_ad on 2008-07-17
> **tinivole said:**
> Maximise the terminal, run the command, and you can click and drag the mouse to select it all.

Then press **Ctrl+Shift+C** to copy it. **Ctrl+V** to paste it in firefox, of course ;)

Also, can you put it in [ CODE ]  [ /CODE ] brackets too, for easy reading. (just remove the spaces between the brackets and you'll have a box like this)
```
text
```

[EDIT]
Alternately, you can run:
```
iwconfig > iwconfig.txt
```
It will show the most relevant information. Plus, it will redirect the output to a text file for you to open and copy from there.

Regards
Iain

This command is being run from the computer with no internet access :( I'll bring my laptop down and type it :)

---

### Post by m_ad on 2008-07-17
```
eth0    Link encap:Ethernet  HWaddr 00:0f:1f:48:e5:a6
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interrupt:20


lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:28 errors:0 dropped:0 overruns:0 frame:0
        TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes: 1400 (1.3 KB)  TX bytes:1400 (1.3 KB)
```

---

### Post by ibuclaw on 2008-07-17
Ahh, I get you now ;)

Then I advise you to definately run:
```
iwconfig > iwconfig.txt
```
then.

Then you can transport the file to your PC with Internet access with a Flash storage drive.

Regards
Iain

---

### Post by m_ad on 2008-07-17
:lolflag: that makes sense, never thought of that.


```
downstairs@ubuntu:~$ iwconfig
lo       no wireless extensions.
eth0     no wireless extensions.
```

---

### Post by m_ad on 2008-07-17
that's the results from iwconfig. ifconfig output is posted above :popcorn:

---

### Post by phantomjoker on 2008-07-17
ok - so now you should be able to see your hardware in system > administration > hardware drivers right?

---

### Post by m_ad on 2008-07-17
> **phantomjoker said:**
> ok - so now you should be able to see your hardware in system > administration > hardware drivers right?

I can't, it says "No proprietary drivers are in use on this system."

---

### Post by phantomjoker on 2008-07-17
right - so what stage are you at?

do you have internet?
Is you USB being recognised?
Do you have a visable network in you network connections?

---

### Post by m_ad on 2008-07-17
I haven't made any changes since the original post. I have no internet and the device has no lights on. the only thing I've done is use ndiswrapper to install the .inf xp driver, which was successful. 'sudo modprobe ndiswrapper' does nothing - doesn't even blink the devices light.

I've posted my 'iwconfig' and 'ifconfig' output earlier

---

### Post by m_ad on 2008-07-17
going to bump this once more before I go to bed. maybe someone will have a solution by tomorrow :)

nothing has changed since the first post.

---

### Post by phantomjoker on 2008-07-18
right well check this when you wake up -

try doing a hardware check, it sometimes just wakes up your system enough to recognise a new device.

---

### Post by m_ad on 2008-07-18
where is this option in Xubuntu?

---

### Post by m_ad on 2008-07-18
anyone?

---

### Post by m_ad on 2008-07-19
if anyone can help, no changes have been made to my system since the original post. I still can't configure this device.

---

### Post by m_ad on 2008-07-19
UPDATE: New problem!

I've gotten the device to turn on (the light is blinking), and I see wireless connections available (including mine). ifconfig and iwconfig show 'wlan0' as a device. However, when I try and connect to my network, using the CORRECT passphrase, it won't allow me to connect. It gets stuck on "Waiting for network key.." or something similar.

Yes, I am using the correct key and settings, as I have tried 5x. I enter this key using the same settings on my working laptop all the time :)

---

### Post by Old_Grey_Wolf on 2008-07-19
Are you using WPA?

Does the WG111T connect when it is used on another computer?

---

### Post by m_ad on 2008-07-19
> **Old_Gray_Wolf said:**
> Are you using WPA?

Does the WG111T connect when it is used on another computer?

Yes, I am dual booting with XP and it connects just fine. I use WEP 128-bit Passphrase via Network Manager.

---

### Post by Old_Grey_Wolf on 2008-07-19
In the Network Settings do you have WEP ACSII or WEP Hexadecimal selected?

---

### Post by m_ad on 2008-07-19
When I click the Networks icon in the system tray, I select my wireless network. A dialog opens, and it asks me for Authentication. I select "WEP 128-bit Passphrase," enter my passphrase, and select "Open System."

this is exactly how I do it on my laptop, but it's not working on this PC :confused:

---

### Post by m_ad on 2008-07-19
And it's unfortunate that the computer continues to lock up after a few hours of running. It's happened ever since I've installed Ubuntu on it.

I think I'm going to ditch Ubuntu on this computer.

Is there any cause of these lockups? It happens on my laptop also, after like 30 mins of idle time the computer locks up. I can move the mouse but I can't do/click anything.

---

### Post by Old_Grey_Wolf on 2008-07-19
Try clicking the Network Icon, select "Manual configuration...", Unlock, then Authenticate. Select the wireless connection, click properties. Uncheck Enable roaming mode if it is checked. Change password type WEP ASCII, enter the password and other items. Does it connect?

---

### Post by m_ad on 2008-07-19
Ok, it says "changing network interface.." and it does. I thought it was a good sign since it didn't give an error, and next to the Wireless Connection it had a red signal sign. I clicked ok and tried using firefox but I still have no connection.

---

### Post by m_ad on 2008-07-19
The system locked up again. Alt+SysRQ+b doesn't even work.

I don't think I changed the password type to WEP ASCII, I'll try that when the computer boots back up.

---

### Post by Old_Grey_Wolf on 2008-07-19
> **m_ad said:**
> And it's unfortunate that the computer continues to lock up after a few hours of running. It's happened ever since I've installed Ubuntu on it.

I think I'm going to ditch Ubuntu on this computer.

Is there any cause of these lockups? It happens on my laptop also, after like 30 mins of idle time the computer locks up. I can move the mouse but I can't do/click anything.

You may want to check the Power Management settings. Both Windows and Ubuntu have problems with power management on some computers. I don't put my computer to sleep after no activity.

---

### Post by Old_Grey_Wolf on 2008-07-19
Someone else will need to help you. Your problems a beyond my knowledge. I haven't had very many problems with Ubuntu.

---

### Post by m_ad on 2008-07-19
This didn't work, I tried with every password type.

Thanks Old Gray Wolf for trying to help. I appreciate your time. Hopefully someone else will come by and help out :)

---

### Post by bumanie on 2008-07-19
I had trouble with the same network adapter, but got it working after a reboot, it just hooked up automatically after not doing so previously when trying to install and entering password for the network etc. It then would drop out every five minutes, but the latest kernel seems to have improved that - cuts out when downloading via repositories at times, but seems to be OK with general surfing. Can't really tell you what got it working other than I gave up putting in password etc. and getting told it was wrong, but the next time I booted it connected.

---

### Post by m_ad on 2008-07-19
ah, I used WEP HEX and it worked. But another problem arises: the system locked up again. It's not inactivity either, it just happened while I was configuring.

Another question: what is 'nm-applet?' After I connected to the network, some dialog popped up asking me to set a password for 'nm-applet.' I clicked deny and my system locked up :lolflag:

---

### Post by Old_Grey_Wolf on 2008-07-19
> **bumanie said:**
> I had trouble with the same network adapter...

I have a box of spare parts. I have had home computers since 1980. If a network adapter doesn't work I get a different one out of my box. I had problems getting the Netgear WG111 working with XP using WPA many years ago and just used a Linksys adapter instead.

---

### Post by Old_Grey_Wolf on 2008-07-19
> **m_ad said:**
> ah, I used WEP HEX and it worked. But another problem arises: the system locked up again. It's not inactivity either, it just happened while I was configuring.

Another question: what is 'nm-applet?' After I connected to the network, some dialog popped up asking me to set a password for 'nm-applet.' I clicked deny and my system locked up :lolflag:

Glad you got the wireless working.

Old thread on the applet:  
[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

Here's another link:  
[http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php](http://lifehacker.com/software/ubuntu/stop-nm+applet-from-authenticating-with-the-keyring-276986.php)

---

### Post by m_ad on 2008-07-19
Well, it worked once and now it won't connect again using any password type.

---

### Post by m_ad on 2008-07-19
This is really frustrating. How does it connect once, and not another time? I've rebooted etc.. no password types work. The system continues to lock up also. Luckily, Alt+SysRq+R E I S U B works.

---

### Post by wbesaw on 2008-10-18
> **phantomjoker said:**
> ok so go into your system>administrator>hardware drivers and see if its located.. it should be.

If not then it hasn't been installed

If it is then move on to system>administrator>network and try to locate an internet connection by confuguring your network.

post back if you need.
it worked for me

---

