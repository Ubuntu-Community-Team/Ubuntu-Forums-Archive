---
title: "Can not connect bluetooth device"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Cebonet on 2008-04-22
Every time a try to connect to a bluetooth device I get this massage: 
"obex://[00:1f:cc:2a:ab:6a"

I don't what that means. I installed several bluetooth tools with no luck.[http://qa.mandriva.com/show_bug.cgi?id=31754](http://qa.mandriva.com/show_bug.cgi?id=31754)

---

### Post by milosz.galazka on 2008-04-29
Maybe you need to pair phone with computer?
[http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu)
[http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)

---

### Post by jbor7755 on 2008-05-09
I just got A Bluetooth mouse (ironically by microsoft) and I'm getting the same message when I try to connect it.  I'm sure there is some bluetooth module not installed by default and this is what's needed.  My guess is that it's the Obex Bluetooth server (in add/remove applications) which is unfortunately a KDE app.  Perhaps there is a gnome equivalent which is suitable....?

---

### Post by jbor7755 on 2008-05-09
I quote this from damis648 from another post. It just worked for me. DONE!


This is easy to fix. In the bluz config in the taskbar, right click it and click preferences. Click the Services tab. Check the box in the list that says "Input service" and then click "input service" and click "add" at the bottom. Just enable your mouse to be found and click on it and click connect. Easy as pie. And it is remembered upon restart.

---

### Post by bumanie on 2008-05-09
Not sure if this is the answer, but you can to System --> Sessions and ensure that bluetooth is enabled at start-up - I think my bluetooth dongle was enabled upon installation.

---

### Post by TWISTED99 on 2008-05-13
Sorry, I'm new at this, but  what is  "bluz config"?

> **jbor7755 said:**
> I quote this from damis648 from another post. It just worked for me. DONE!


This is easy to fix. In the bluz config in the taskbar, right click it and click preferences. Click the Services tab. Check the box in the list that says "Input service" and then click "input service" and click "add" at the bottom. Just enable your mouse to be found and click on it and click connect. Easy as pie. And it is remembered upon restart.

---

### Post by balagosa on 2008-05-14
> **Cebonet said:**
> Every time a try to connect to a bluetooth device I get this massage: 
"obex://[00:1f:cc:2a:ab:6a"

I don't what that means. I installed several bluetooth tools with no luck.

i have a guide for this but you are not giving the full details. i encountered **"obex://[00:1f:cc:2a:ab:6a"** before but i know it is lacking. i know two error messages that has this message, either can not connect to device OR lost connection to device.

try to do "hcitool scan" and see if your bluetooth device can be seen by you PC.

Note: i forgot from which package hictool came from. i think it is from bluez-utils? can someone clarify this.

---

### Post by balagosa on 2008-05-14
> **TWISTED99 said:**
> Sorry, I'm new at this, but  what is  "bluz config"?

it is not bluz but **bluez.** it is just a typo. from what i know it was one important key to get my bluetooth device connected to my PC.

---

### Post by sukka69 on 2008-05-19
Hi, I following this guide and successfully get my Microsoft Bluetooth mouse connected and working.

Try this: [https://help.ubuntu.com/community/BluetoothInputDevices](https://help.ubuntu.com/community/BluetoothInputDevices)

---

### Post by vinod.kollam on 2008-09-06
Excuse me, but I am new to this forum. I am running ubuntu 7.10. On installation there was bluez 0.14 (i think). It was listing my mobile but was showing the error something like this "cannot connectobex://[00:1f:cc:2a:ab:6a". i thought it will be some problem with the bluetooth version. and i am using a bluetooth dongle from my desktop. i visited bluez website and installed bluez-gnome 1.2 and bluez-4.2 and now the bluez applet is showing version 1.2. i restarted my pc and plugged in the dongle in the usb port. it was not recognising. when i use the add new device option, no devices are shown in the list to add. i then used hcitool to scan and then to connect, it recognoses the mac address and phone name . and when i use the gnome-phone-manager it connects giving a warning that  "Model Nokia 3500c not supported natively". and my moblie also detects the pc and also i am able to send sms messages from  pc thru mobile that part is ok , but why is that bluez applet not listing the mobile. previously (with version 0.14), it was at least recogonising my mobile. please help

---

