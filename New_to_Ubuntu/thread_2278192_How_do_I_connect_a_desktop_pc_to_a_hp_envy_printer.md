---
title: "How do I connect a desktop pc to a hp envy printer"
date: 2015-05-14
forum: New to Ubuntu
---

### Post by colin_stephenson on 2015-05-14
Can anyone help with this topic please. I am new to Ubuntu

---

### Post by stalkingwolf on 2015-05-14
I use a usb cable.

---

### Post by cariboo on 2015-05-14
This page may help you:

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by Geoffrey_Arndt on 2015-05-14
> **colin_stephenson said:**
> Can anyone help with this topic please. I am new to Ubuntu

1.   Initially,connect the printer via usb cable.,
2.   Check in Software Ctr that "hplip" is installed (should be but if not, install it).,
3.   Use the "add printer" app in the Systems Settings.,
4.   Search for hp Envy
5.   Finish the add printer dialog (run print test to confirm)
6.   Turn on wireless on printer & let it find network
7.   Complete network dialog including password input
8.   Disconnect usb and test if can send print command (via a common app such as Librewriter
9.   Set up cloud print (via google and/or IPP protocol) (HP website should have more info & instructions
10.  Youtube has additional tutorials re all the above

---

### Post by colin_stephenson on 2015-05-19
Then what?

---

### Post by colin_stephenson on 2015-05-19
Thanks for your help but still unable to print from my desktop computer. My computer is a Dell which does not have wifi therefore I am trying to print via USB cable. The computer is able to recognise the HP Envy 4500 series printer but when it searches for the driver it can only find one for an Envy 110 printer. I tried this driver but it did not work. I have an installation CD for my printer but its only suitable for Windows, Mac or Mountain OS. I have been able to copy the driver folder (contains 9 items, totalling 8MB) to the Ubuntu desktop but the driver search still cannot find the correct driver. Are you able to offer further help please?

---

### Post by leunam12 on 2015-05-19
Your printer is listed as supported at the HPLIP page. Try downloading the latest HPLIP and run the automatic installer, it will remove the older version and take you through the necessary steps.

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Go to the section that says: "To use the Automatic Installer, follow these steps:"

---

### Post by Geoffrey_Arndt on 2015-05-19
Follow Leunam12's advice . . but if you run into issues, here is a bit more info:

1).   Wireless info just pertains to printers that have access to a wireless network, but, if no wireless, USB cable is all that's needed.
2).   Can you confirm that Hplip 3.15.2 is installed? (go to Ubuntu Software Center and type "hplip" in the search field . . . does it have a green checkmark (indicating installed))?
3).   Although not required, you can also install the HPLIP Toolbox . . . it may help with install & subsequent maintenance.
4).   As Leunam12 states, your printer is supported . . . . HP Envy 4500 thru HP Envy 4508 are all listed.
5).   _**Just in case **_. . . what version of Ubuntu are you using . . . if it's a really old version, that may account for the "Systems Settings>Printers>Add Local Printer" dialog not seeing the HP 4500 series.

**PS:   just a thought** . . . IF the HP Envy 4500 was "seen" or recognized by your DELL desktop, that should be all that's required to complete the add dialog and then do the print test.   In other words, it's usually NOT needed to install any driver (because it's already installed) and when you tried to install another driver on top of the already installed, configured printer - - you in effect may have "hosed" the install).  . .  you see, in many cases for all kinds of devices (printers, monitors, etc., drivers are not by routine needing a user install as they are in older versions of Windows - - but the newbie Linux user often "assumes" they are).

---

### Post by colin_stephenson on 2015-05-20
Thanks again, I have now succeeded with your help. By choosing the HP Envy 110 series driver it worked fine.

---

