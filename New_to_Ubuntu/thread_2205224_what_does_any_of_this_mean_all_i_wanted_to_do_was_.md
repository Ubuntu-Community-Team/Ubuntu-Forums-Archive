---
title: "what does any of this mean all i wanted to do was run kali from usb"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by nick58 on 2014-02-12
and for some insane reason this is the on option from ubuntu
can some help me by turning thsi in to something use aka english 
do i just copy and past on to the usb????

 

[LIST=1|INDENT=1]
[*]Plug in your USB device to your Linux computer’s USB port.
[*]Verify the device path of your USB storage with **dmesg**.
[*]Proceed to (carefully!) image the Kali ISO file on the USB device:
[/LIST]
[COLOR=#000000][FONT=Monaco] [COLOR=#2060A0]dd[/COLOR] [COLOR=#008080]if[/COLOR]=kali.iso [COLOR=#008080]of[/COLOR]=/dev/sdb [COLOR=#008080]bs[/COLOR]=512k
[/FONT][/COLOR]

---

### Post by deadflowr on 2014-02-12
Seems english enough to me, but maybe look at doing it this way
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

Adding: If you need help with what those instructions are, then maybe running one of the more advanced-level systems like kali is not what you should be doing in the first place.

---

### Post by david98 on 2014-02-12
1 plug usb into computer format to fat32 through gparted
2 have iso image of kali on computer
3 open unetbootin if you don't have it install by using sudo apt-get install unetbootin
4 remount usb then proceed to create a live usb through the gui you dont have to select your disto or version just leave blank then direct the disk image to you iso file then click ok

---

### Post by nick58 on 2014-02-12
ok
thats is english 
thank you 
for all yoiur help

---

### Post by Psil0cybin on 2014-02-15
Yes, or you can use System > Startup disk creator > Pick your .ISO , Erase USB Completely, load ISO. 

> [COLOR=#000000]Adding: If you need help with what those instructions are, then maybe running one of the more advanced-level systems like kali is not what you should be doing in the first place.[/COLOR]

You should really take the time using Ubuntu to learn about how Linux functions, what it does, what certain commands do. You can always find GUI's for terminal commands, but you should  take the time to learn how to use those commands - They are simple and are used to place any ISO on a USB, etc. 

Just type 'sync' after the dd command.

If you think you can pick up kali linux without knowing simple linux commands, you will find that you are going to be thrown into a bigger sea than you can swim in.

---

