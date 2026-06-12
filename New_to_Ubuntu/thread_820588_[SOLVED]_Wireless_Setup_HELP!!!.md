---
title: "[SOLVED] Wireless Setup HELP!!!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by cnhindland on 2008-06-06
I just installed ubuntu on my computer. I am having problems setting up my wireless connection. Network manager does not show any wireless networks. Do I have to install a driver for my wireless card. I am running a duel boot and my wireless works great from windows. What do I do?

---

### Post by alexandremrj on 2008-06-06
Hello,

we would like to help you but you have to give us more information like your hardware.

---

### Post by avtolle on 2008-06-06
Go to Terminal and run```
lspci
``` and post results for review. Thank you.

---

### Post by cnhindland on 2008-06-06
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT
Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GM L Express Integrated Graphics Controller (rev 3)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 3)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: 02 Micro, Inc. CardBus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): 02 Micro, Inc. FireWire (IEEE 1394) (rev 02)
0c:00.0 Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by ukripper on 2008-06-06
> **cnhindland said:**
> 
0c:00.0 Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Follow this guide -
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

### Post by stchman on 2008-06-06
You figure with all the Linux people out there Broadcom would create a restricted driver for their freaking 43xx cards.

They are absolutely ridiculous.

---

### Post by valmorel on 2008-06-06
I had the same problem with a Broadcom chip set card and Hardy Heron. Fixing it is dead simple. Connect your pc to the net with a cabled connection via your normal network card, not the wireless card, wait about three mins, and Ubuntu will suddenly offer to download and install a fix for your wireless card. Follow the on screen prompts. It worked perfectly for me, requiring just a few mouse clicks. All works perfectly now. Magic.
ps. I had to connect the network cable with the pc turned of, then turn it on to get it to recognise the connection. Dont know if this works with earlier versions of Ubuntu.

---

### Post by cnhindland on 2008-06-06
> **valmorel said:**
> I had the same problem with a Broadcom chip set card and Hardy Heron. Fixing it is dead simple. Connect your pc to the net with a cabled connection via your normal network card, not the wireless card, wait about three mins, and Ubuntu will suddenly offer to download and install a fix for your wireless card. Follow the on screen prompts. It worked perfectly for me, requiring just a few mouse clicks. All works perfectly now. Magic.
ps. I had to connect the network cable with the pc turned of, then turn it on to get it to recognise the connection. Dont know if this works with earlier versions of Ubuntu.

I never saw this, that would have been nice.

---

### Post by radical3 on 2008-06-06
my wileless usb is supposedly unsupported by ubuntu yet im on the net right now. heres what i did

i put in my wireless install cd for my usb and i ripped everything off the cd, there were a bunch of folders, there was also a  USB folder and a PCI folder. in your cd navigate to your folder for your specicific wireless card (as companies often put numerous drivers on the same cd) then search for a file that ends with .INF  and not the cd's actual "autorun.inf" file  as that runs the cd and not the drivers. 

when you have that file put it on your desktop or something. 
next download
the three file i have attached and install them , they are .debs so just double click them hit the install button and type in your password , install "common" first then "utils" then "gtk"

the third one is the most important one 

when your finished in either you preferences or administration menu (at the main menu bar) there should be a program called "windows wireless drivers" click it

install a new driver (which is the inf file i told you to put on the desktop) it takes a few seconds to install, once its done its should read "hardware present" YOU DONT HAVE INTERNET YET.

next go to administration > network something , a window should open up and there would be a button at the bottom saying unlock. click it and put yor password in, there click on wireless connection to highlight it then click the properties button to the right . 

disable roaming by uncheking the box then choose WEP from a drop down menu . above the WEP dropdown menu there is another dropdown menu, click it and you will be able to see all the connections you are close to, select yours then enter your wep key.YOU ARE NOT ON THE INTERNET YET.

next there is another dropdown menu at the bottom asking the connection type, the options are automatic , static ip, and something else, set it to automaic and apply the settings, then at the very bottom there's an "apply" button which should highlight indicating you can save your settings now,click it, a psuedo loading bar should appear and read "applying interface" or something like that. 

now heres the funny part which i still dont understand myself, at this point despite entering the WEP , the internet still wont work, funny. anyway open firefox and type in a url and go to it, obviously nothing will show, this act is mereley to INVOKE the connection. go back to the network menu where you entered the WEP key and go to the dropdown menu with "automatic" "static" and the "other one", select the "other one" **and apply the changes **after the chages have been made, **change it back to automaic **and [SIZE="5"]BOOM[/SIZE] internet is working and it will automatically connect to the internet everytime you login. 

why you have to change from automatic to the other one then back again? i do not know , what i do know is it works.

p.s you can tell that im an ubuntu noob as i have supplied you with absolutley nothing to place in a command line. [SIZE="5"]GUI's RULE[/SIZE]

---

### Post by cnhindland on 2008-06-06
Thanks everyone I got it working.

---

### Post by ukripper on 2008-06-07
> **cnhindland said:**
> Thanks everyone I got it working.

Can you post solution here for others to see thanks.

---

