---
title: "Need help installing"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by jmnick on 2012-01-21
Greetings:
 
This is my first attempt at Linux. I have tried to install edubuntu 11.10 on a new computer build and I am having problems.
 
My problems:
While installing, I have the system (specs below) plugged into an ethernet connection with connectivity. After I install, I have no connection icon present in the task bar and am unable to connect to the internet. When I go to network, the device is not managed. After finding the NetworkManager.conf file, I receive an error saying I am not authorized to make changes. I tried making changes from terminal with SUDO and had the same results.  Also, I cannot create a new user. When I click on users under the settings, the settings window closes and I am presented with the desktop.
 
System:
Gigabyte, GA-H61M-S2H MOBO
Intel i5 CORE I5 2400 3.1G 6M R
GSKILL F3-10666CL9D-8GBSR
Gigabyte GV-N430OC-1GL 
 
Any help would be appreciated.
 
Thanks in advance,
 
Nick

---

### Post by BC59 on 2012-01-21
You could try removing the Network Manager and installing Wicd, run:

```
sudo apt-get remove network-manager
sudo apt-get install wicd
```

In case the trick is not working you can reverse it:

```
sudo apt-get remove wicd
sudo apt-get install network-manager
```

---

### Post by Sigma1 on 2012-01-21
I don't know much about edubuntu. Since it's meant for educational purposes, might there not be one or two inbuilt restrictions, like "no internet access" as default? You could perhaps just install a plain "ubuntu", and worry about installing the "edubuntu" software packages after you're happy with that.
Do you have internet connectivity on the live CD or during the install?
Have you looked at the Help files on network problems, which will at least tell you whether you're card is detected etc.? Do you have a fixed IP address?
All these questions might be important to troubleshooting your problem: wired ethernet connexions generally work out of the box!

---

### Post by jmnick on 2012-01-22
Thanks for the replies. 
 
I tried the uninstall of network manager. It un-installed and the icon for the connectivity briefly appeared then disappeared. I tried to install the wicd, but couldn't because of no connectivity.  I tried to reverse the uninstall, but it wouldn't re-install because of the lack of internet.
 
I have uninstalled and re-installed a couple of times, both with USB drive and CD. The same thing happens both times. I have connectivity and the ethernet is enabled during the installation, but after I reboot when it is finished, there is no more internet.
 
I am going to try a install of just ubuntu and then download the educational packs afterwards. I'll post the results here when I am finished. Hopefully it is just something wonky with the edubuntu distribution and my hardware. I don't think it is an administrator type issue. I haven't had any trouble putting it on an old laptop and an older dell (mfg 2000) but that one was just too weak on processing to run it efficiently.
 
Thanks,
 
Nick

---

### Post by epicoder on 2012-01-22
If you want to install packages on a computer with no internet connection, you can download .debs from [packages.ubuntu.com]("http://packages.ubuntu.com") and use a usb flash drive to transfer and install them. You'll need to make sure to grab dependencies, and it's a good idea to not remove any packages you don't need to on the network deprived computer. You'll still need to remove network-manager if you install wicd though.[URL="http://packages.ubuntu.com"]
[/URL]

---

### Post by jmnick on 2012-01-22
Well, successfully installed Ubuntu 11.10.  I think I am just going to give up on the edubuntu version and download the different educational packs.
 
After I uninstalled the network-manager, i realized there was no way I could get anything else back on since no internet.  Doh!
 
The next piece of the puzzle is getting the netgear wnda3100 v2 wirless usb working.  It seems there are enough guides out there for me to slog through it.
 
Thanks again for the help and replies.
 
Nick

---

