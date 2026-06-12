---
title: "scanner DCP-135 wont scan now!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by CAMEMBEAR on 2008-04-28
We have just updated to Hardy Heron & the scanner on our all-in-one printer (Brother DCP-135c) wont scan. We have looked on the brother website which tells us what to type into the Terminal, but the system keeps saying invalid file/location etc.  Can anyone help?

---

### Post by phr0ze on 2008-04-28
Can you give us a link to the instructions you are following? Also what is the file name it says it can't find?

Thanks,
John

---

### Post by CAMEMBEAR on 2008-04-29
The link for Brother website is: [http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html)

Under Scanner FAQ: go into:-

"I cannot use the scanner function with a normal user. When scanning I receive the error "Error during device I/O". (only for USB Users)" (which is the error message we are getting). 

Then open the link and go to the following section; 

# For Ubuntu Users (version 6.06 or later)]

1. Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
2. Add the following description to the file as below:

=================
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"
=================

3. Restart the OS.


We have done this, but everytime we try to save it we get a message saying "Could not save the file /etc/udev/rules.d/45-libsane.rules~. You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again."

Any ideas please.

Thanks.

---

### Post by plucky on 2008-04-29
Try ```
gksudo gedit /etc/udev/rules.d/45-libsane.rules
``` which will create the file.Copy the instructions into the file,save and reboot.

You need super user privileges to create a system file.

Can you post the output of ```
lsusb
```


Good Luck

---

### Post by CAMEMBEAR on 2008-05-23
We have done as you said and as per your request - this is what comes up in terminal after typing lsusb:


Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04f9:01ce Brother Industries, Ltd 
Bus 001 Device 001: ID 0000:0000  

Look forward to hearing from you!

---

### Post by plucky on 2008-05-23
> # I cannot use my usb-connected-scanner with a normal user. (1) (for Ubuntu)


[For Ubuntu Users (version 8.04)]

1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
2. Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

3. Restart the system.


[For Ubuntu Users (version 6.06, 6.10, 7.04, 7.10)]

1. Open "/etc/udev/rules.d/45-libsane.rules"
2.Add the following 2 lines before "LABEL="libsane_rules_end"":

Lines to be added----------------
#Brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

3. Restart the OS.



That is what it actually says on the site and as you are using Hardy Heron which is Ubuntu 8.04,you need to edit a different file ```
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules
```

and change 664 to 666.I would also delete the other file as that was for previous versions ```
sudo rm /etc/udev/rules.d/45-libsane.rules
```


Also something I learned this week on the forums,is that the **Brother** printer drivers are now included in Synaptic so no more having to download them from the brother website and installing.Just open synaptic and search for **brother** and search for the correct driver file and install.


Good Luck

---

