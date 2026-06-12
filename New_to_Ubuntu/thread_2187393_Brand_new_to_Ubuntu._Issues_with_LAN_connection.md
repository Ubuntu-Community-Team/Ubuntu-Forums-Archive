---
title: "Brand new to Ubuntu. Issues with LAN connection"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by zach.toolson on 2013-11-11
I have verified that the wireless connection works using another computer. I just installed Ubuntu for the first time. Is there a specific way to set up a wired connection? The wire is plugged into the computer, but it doesn't seem to recognize it.

---

### Post by fantab on 2013-11-12
The Wired connections, most often, work out of the box.

What LAN card do you have on board? Check for 'Ethernet controller' with following command in Terminal:
```
lspci
```

The following can help you diagnoze the issue:
[http://www.cyberciti.biz/faq/how-can-i-find-out-if-my-ethernet-card-nic-is-being-recognized-or-not/](http://www.cyberciti.biz/faq/how-can-i-find-out-if-my-ethernet-card-nic-is-being-recognized-or-not/)

---

### Post by zach.toolson on 2013-11-14
When I run that command, no Ethernet controller is shown.  I know there is an ethernet port on the motherboard though.

---

### Post by Bucky Ball on 2013-11-14
This command is much more concise and comprehensive:
```

sudo lshw -C network
```

Post the output thanks.

---

### Post by zach.toolson on 2013-11-17
sudo lshw -C network output

*-network DISABLED      
       description: Wireless interface
       physical id: 1
       bus info: usb@3:3
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=prism2_usb driverversion=3.11.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11b

This is after I have plugged in a Linksys Wireless Usb Adapter Model WUSB11 ver. 2.5 and did a complete reinstall of ubuntu with this wireless adapter plugged in during the reinstall.

---

### Post by couder on 2013-11-17
Hello, one idea - try to check the BIOS setup wheter the etherner card is enabled.

---

### Post by fantab on 2013-11-17
Are you dual-booting Ubuntu with any other OS? If you are, then check in the other OS if Ethernet is working.
You can check in the BIOS to see if it is Enabled, if it isn't then enable it.

---

### Post by zach.toolson on 2013-11-17
I am not dual booting with any other OS. How do you check the BIOS to see if it is enabled?

---

### Post by electrohandyman501 on 2013-11-17
When you 1st power on the machine you should see near the upper right corner during the bios boot a listing of f-key boot options. The list may not stay listed long. You have have to boot it once to see the list, write it down, then boot a 2nd time to actually key in the option. 
The key listing is bios dependant. Some machines use F2, some F12, some use the DEL key to enter bios setup screen.
Once in the bios setup, you will have to page thru the setup options for the motherboard you have.

---

### Post by zach.toolson on 2013-11-17
I accessed the BIOS for my motherboard, but couldn't find any options even close to on board LAN or ethernet. My motherboard is [http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=451](http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=451) . Any other ideas?

---

### Post by electrohandyman501 on 2013-11-17
On page 29 of the bois manual pdf from the mfgr website, lists the lan setup page.

Under the "chipset" header.

MAC ID Information
This area shows the MAC ID.
Realtek PCIE NIC
This option allows you to control the onboard LAN controller.
Options: Enable (Default) / Disable
Realtek Option ROM
This item allows you to enable or disable the Onboard LAN Boot ROM.
Options: Disabled (Default) / Enabled

---

### Post by couder on 2013-11-17
What type of bios this motherboard have? Is it amibios (american megatrends)?

---

### Post by electrohandyman501 on 2013-11-17
> **couder said:**
> What type of bios this motherboard have? Is it amibios (american megatrends)?

I would say yes, the bios pdf indicates that it is supposed to be AMIBIOS. 

I am only reading information from the mfgr web link provided by the zach.....

---

