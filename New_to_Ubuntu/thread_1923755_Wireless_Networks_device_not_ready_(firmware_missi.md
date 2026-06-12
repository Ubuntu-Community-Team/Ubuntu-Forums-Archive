---
title: "Wireless Networks device not ready (firmware missing)"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by keuspastis on 2012-02-11
Hi there, I have re-installed Ubuntu 11-10 on my HP Pavilion zd8000 as I had forgotten my password and couldn't do any update. Everything seems to work fine except my wifi connection. When I go to my network manager it says Wireless Networks device not ready (firmware missing).

Could anyone help me please?

Thank you.

---

### Post by lkraemer on 2012-02-11
If you can, connect your computer with an Ethernet Patch Cable, and 
do a Software Update.  Then Click on Hardware Drivers, and update
any that are displayed as being available.  If none show up for
update, then you are going to need to download the firmware for your
Wifi Hardware.

Search the Forum for HOWTO: Broadcom......assuming you have Broadcom Wifi
Hardware on your Computer.  (Most older HP & Compaq use Broadcom)

REF:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

This is just one of the many Postings on the Forum.......This is a bit out of date as
far as the Driver used as DEFAULT, but you will get the idea.
Start at the line:  ** #2 Use DEFAULT B43 Driver in 10.04**
and just substitute XXX for the B43 in the HOWTO:

When you get to **FINISH:**.......you should have a working Wifi.

**OR** follow one of the latest **updated HOWTO's:**

Post as noted on the HOWTO:

SEARCH & GOOGLE are your BEST FRIENDS!

lk

---

### Post by keuspastis on 2012-02-11
Hi lkraemer,

thanks for your help, I tried what you said but after entering my password I get the following text.


philippe@philippe-Pavilion-zd8000-EL030EA-ABF:/lib/firmware$ sudo cp -r /home/loginname/Desktop/XXX* .
[sudo] password for philippe: 
cp: cannot stat `/home/loginname/Desktop/XXX*': No such file or directory
philippe@philippe-Pavilion-zd8000-EL030EA-ABF:/lib/firmware$ 

Thanks.

---

### Post by lkraemer on 2012-02-12
That is because your loginname isn't included in the characters contained in "/home/loginname/Desktop/XXX*"

To find you loginname Open a Terminal Window (Console) and type:
```

pwd

```
Now you have your loginname,  Next you are going to need the Subdirectory
where you copied the files.....Maybe Desktop.....But, I don't know where
you saved them to......I'm assuming Desktop.......Hopefully you now get the idea!

Also, note that B43 was the DEFAULT in Ubuntu 10.04 LTS, and I haven't a clue as to
what your Version is, or what the DEFAULT Driver is......So, replace the XXXX
with your DEFAULT Driver in the HOWTO:......

And if you Copy & Paste you can prevent ERRORS......

When you cd to /lib/firmware and do the ls   or   ls -alt command,
you should see some *.fw files for Broadcom.

lk

---

