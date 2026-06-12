---
title: "Noob with printer problems( didnt see that coming did you?)"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by rthatchjr on 2012-07-10
Hello again all!! I am trying to get my HP-6500A e710n-z printer to work wirelessly with 12.04. So far I suck! I have been reading for days trying to get this to work, and I get this every time.

Printer status: printer Officejet_6500_E710n-z is idle.  enabled since Tue 10 Jul 2012 10:34:04 PM EDT
error: Unable to communicate with device (code=12): hp:/usb/Officejet_6500_E710n-z?serial=CN15P230YC05JW
error: Device not found
error: Communication status: Failed

Officejet_6500_E710n-z_fax
--------------------------
Type: Fax
Device URI: hpfax:/usb/Officejet_6500_E710n-z?serial=CN15P230YC05JW
PPD: /etc/cups/ppd/Officejet_6500_E710n-z_fax.ppd
PPD Description: HP Fax hpcups
Printer status: printer Officejet_6500_E710n-z_fax disabled since Tue 10 Jul 2012 10:29:Unplugged or turned off
error: Unable to communicate with device (code=12): hpfax:/usb/Officejet_6500_E710n-z?serial=CN15P230YC05JW
error: Device not found
error: Communication status: Failed

If you have any suggestions I would greatly appreciate them!!
 Thank you in advance
                Russell

---

### Post by mapes12 on 2012-07-11
Download the latest HPLIP driver from their site. The one that ships with Ubu is out of date.

You will need to follow the instructions to install it (Terminal commands). By default the driver will download to your **Download** folder. Drag it to your **Desktop** and the installation instructions will work perfectly.

---

### Post by rthatchjr on 2012-07-12
I did all that, several times now, followed the instructions on the hplip page. Still will not connect to the printer, the printer is a HP Officejet 6500A E710n-z, drive I downloaded and installed was the 3.12.6.

---

