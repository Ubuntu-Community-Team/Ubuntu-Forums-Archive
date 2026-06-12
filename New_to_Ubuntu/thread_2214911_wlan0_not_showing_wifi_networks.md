---
title: "wlan0 not showing wifi networks"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by Jeff_Martin on 2014-04-03
Hi, as the title suggests, wlan0 is not showing wifi networks. When I ran rfkill it returned that there was a softblock, though rfkill unblock all does not fix the issue. I'm at an impasse here and would appreciate any suggestions from the community.

Thanks!

---

### Post by wildmanne39 on 2014-04-03
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by grahammechanical on 2014-04-03
Softblock can mean that there is not a WiFi driver for your WiFi adapter. Have you tried going to Additional drivers and seeing if it presents you with a wireless driver to install. Other than that we will need to know more information about your machine and the wireless adapter it has in it. It might not seem a useful piece of information to you but telling us the Version of Ubuntu can help us give you directions that are suitable to your version.

When I run nm-tool in the terminal this is a little bit of the information that I see about my WiFi access

> - Device: wlan0  [PlusnetWireless] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           no
  HW Address:        00:15:AF:0E:9B:E0


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


Notice, I have a driver installed and working because the State is Connected and there is an Hardware (HW) Address.

Regards.

---

### Post by Jeff_Martin on 2014-04-04
[ATTACH=CONFIG]251716[/ATTACH]
I have attached the script, thanks Wild Man. I have access to ethernet, though right now I'm using my phone through usb tethering.

I have installed additional drivers, but when trying to turn on the wireless through the command line, I think I must have changed something badly. I wish I would have saved the commands I'd given. I'll have to do that from now.

---

### Post by squakie on 2014-04-05
I'll just throw in my 2-cents worth from a brief look at the output you provided.

The network manager status listed in the output shows wireless is not enabled.

You need to click on the network manager icon in the top bar.  Check to see if "Enable WiFi" has a check mark in front - judging from your output it won't.  Use your mouse and click in the little box in front of "Enable WiFi".  It should end up showing a check mark.  If you get any error messages at this point please post them back.  If no error messages, then available networks to connect to should show in about 30 seconds or a little longer (it needs to scan).  If none show, I would suspect a driver isn't installed.  I'm not sure right now if a driver is actually installed of not myself, but let's just try one thing at a time.

---

### Post by Jeff_Martin on 2014-04-05
Somehow I uninstalled nm-applet and after reinstalling I was able to "Enable WiFi" and fix my problem. What would have been the terminal equivalent of this solution?

---

### Post by steeldriver on 2014-04-05
You should be able to use nmcli to talk to network-manager without the GUI tools (nm-applet / nm-connection editor) e.g.

```

nmcli nm enable true      # equivalent of Enable Networking

nmcli nm wifi on          # equivalent of Enable Wireless

```

---

### Post by Jeff_Martin on 2014-04-05
Thanks steeldriver and everyone else. Problem solved.

---

### Post by squakie on 2014-04-08
Your welcome!  Glad that enabling wireless did it for you.

---

