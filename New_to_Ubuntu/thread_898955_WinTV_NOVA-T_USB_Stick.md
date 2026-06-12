---
title: "WinTV NOVA-T USB Stick"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Bristol Rogue on 2008-08-23
I've just bought one of these, model 70019.  It is detected and works under XP on one machine and under vista on another, being recognized instantly on the USB bus and providing a noise free picture :).  However it is not detected on either PC when running under Ubuntu 8.04:(.

 dmesg | grep -i 'dvb'
returns nothing.

Kernel 2.6.24-19-generic
I would eventually like to use this with Kaffeine, although at present I'm less than fussy!
Can anyone tell me what I should have done to get this stick detected, or point me to a thread please.
Thanks for your patience.

---

### Post by super.rad on 2008-08-26
To check it's showing up in hardy open a terminal and type
```
lsusb
```
which will list all the USB devices plugged in.
You'll need the module dvb-usb. Open a terminal and type
```
lsmod
```
and check if the dvb-usb module is already loaded, if not load it by typing
```
sudo modprobe dvb-usb
```
then try opening kaffeine and see if it's being detected and working. If it is you'll need to add the dvb-usb module to the list of modules that are loaded at boot
```
gksu gedit /etc/modules
```
Hopefully it should now work (that's all I have to do to get my WinTV Nova PCI card working).

---

### Post by Bristol Rogue on 2008-08-27
Many thanks for your effort, sadly Kaffeine will still not indicate that can see a dvb tuner, even after a cold start.  My outputs are as follows:

roger@ASUSX50N:~$ lsusb
Bus 004 Device 002: ID 2040:7070 Hauppauge 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0bda:0116 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
roger@ASUSX50N:~$ 

At least the device is there!

roger@ASUSX50N:~$ lsmod | grep -i 'usb'
dvb_usb                22796  0 
dvb_core               94380  1 dvb_usb
i2c_core               28544  2 dvb_usb,nvidia
usb_storage            82496  0 
libusual               23520  1 usb_storage
scsi_mod              178488  5 sg,sr_mod,sd_mod,usb_storage,libata
usbcore               169904  6 dvb_usb,usb_storage,libusual,ehci_hcd,ohci_hcd
roger@ASUSX50N:~$

the module is loaded, I did have to edit /etc/modules to force it to load, as you recommended.

But still nowt, any further help would be appreciated.

---

### Post by super.rad on 2008-08-27
Seems like this is what you're looking for [HOWTO: Kaffeine & (Hauppauge) WinTV-Nova-T Stick]("http://ubuntuforums.org/showthread.php?t=533528")

---

### Post by Bristol Rogue on 2008-08-28
Thanks fo the pointer, it will be a while before I get back to you now as, having already followed that thread once to no effect, I am about to reload the notebook with 8.04, but this time with the 32 bit version, although the processor is an Athlon Turion 64x2.  Of interest is that Vista was supplied as the 32 bit version and the documentation only recommends 32 bit Vista in which it works well using the Hauppauge application and driver.  I'll be back, but as I said, not too soon.   Thanks for your persistance.

---

### Post by Bristol Rogue on 2008-09-01
I've just reloaded and updated with 32 bit Hardy - the notebook is now much faster - no I don't know why it should be - but there it is.  I've worked through the first suggestion with exactly the same (non) result as before, I'm beginning to think that it might have something to do with the lack of 'firmware' specific to my model of USB DVB-T stick.  Next test, however is the HOWTO posted for me.

I've now tried the HOWTO and it falls at the first hurdle - dmesg doesnt return anything about dvd-usb! any more thoughts please?
Anyone?

---

