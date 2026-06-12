---
title: "Trying to get Nokia 3110 to connecxt via bluetooth"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by ubername on 2008-10-11
Hi

I have just got a Nokia 3110 (but i don't think the phone is the problem) and I want to connect it via bluetooth to my ubuntu (heron) box). I use a USB bluetooth dongle. When I plug the dongle in, the phone can see the computer and asks for a pairing code, but I can't find any way of setting the pairing code on the computer. Any Help?

TIA

---

### Post by ww711 on 2008-10-11
If you input the pin on the phone prompt (the pin can be anything, 1234, 1111, etc), then it should prompt on the computer...then you can pair.

---

### Post by ubername on 2008-10-11
> **ww711 said:**
> If you input the pin on the phone prompt (the pin can be anything, 1234, 1111, etc), then it should prompt on the computer...then you can pair.

I put a code in (e.g. 0000)  but I get no prompt on the computer. I think I may not have the GUI for bluetooth installed, but I have searched synaptic for 'blue' and everything is installed.

---

### Post by ww711 on 2008-10-11
My experience is - When I plug my bluetooth dongle into the usb port, it displays the bluetooth icon on my top panel. Then I select 'browse device' by right clicking on the bluetooth icon and then pair up my device.

---

### Post by ubername on 2008-10-11
> **ww711 said:**
> My experience is - When I plug my bluetooth dongle into the usb port, it displays the bluetooth icon on my top panel. Then I select 'browse device' by right clicking on the bluetooth icon and then pair up my device.

Thanks so much for the help.  I don't see any bluetooth icons anywhere (not sure what the 'top panel' is: do you mean the one that has 'Applications Places System' on it?

---

### Post by ubername on 2008-10-11
> **ww711 said:**
> My experience is - When I plug my bluetooth dongle into the usb port, it displays the bluetooth icon on my top panel. Then I select 'browse device' by right clicking on the bluetooth icon and then pair up my device.

Would you do me a favour and right click on your bluetooth icon, and tell me what it says in something like 'help' or 'about'?

TIA

---

### Post by ww711 on 2008-10-11
> **ubername said:**
> Would you do me a favour and right click on your bluetooth icon, and tell me what it says in something like 'help' or 'about'?

TIA

On the bluetooth icon, 'about' it displays Bluetooth applet 0.25.

---

### Post by ubername on 2008-10-11
Does this help anyone diagnose? (I have no idea what It does, but was following help [https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/206549](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/206549))

sudo /usr/sbin/hcid -d -n
[sudo] password for xxxx: 
hcid[6505]: Bluetooth HCI daemon
hcid[6505]: Enabling debug information
hcid[6505]: Could not become the primary owner of org.bluez
hcid[6505]: Unable to get on D-Bus

---

### Post by micke4 on 2008-10-11
I have just purchase a Nokia 3110 mobile phone. But I think so that mobile phone is not problem because main problem is connectivity. I want top to be connected via bluetooth to my ubuntu. I mostly use Bluetooth so many time error in paring code computer and plug. 


 [Crystal Meth](http://www.crystalrecovery.com)

---

### Post by ww711 on 2008-10-11
If you look at this screenshot, you can see a bluetooth icon, this appears when I plug in my bluetooth dongle. Do you get this far? If you can, then you should be able to right click that icon and select 'browse device'.

---

### Post by ubername on 2008-10-12
> **ww711 said:**
> If you look at this screenshot, you can see a bluetooth icon, this appears when I plug in my bluetooth dongle. Do you get this far? If you can, then you should be able to right click that icon and select 'browse device'.


Nope, I don't get that icon!

---

### Post by ubername on 2008-10-12
I have moved to an intrepid machine and I now get the icon. My phone can see the intrepid box, and the intrepid box can see the phone, but when I try to pair them, from either the phone or the intrepid box I get 'failed' messages. Interestingly only the phone asks for a pairing code.

---

### Post by ubername on 2008-10-12
> **ubername said:**
> I have moved to an intrepid machine and I now get the icon. My phone can see the intrepid box, and the intrepid box can see the phone, but when I try to pair them, from either the phone or the intrepid box I get 'failed' messages. Interestingly only the phone asks for a pairing code.

Now seems to work, using the connection from the intrepid box and letting it generate a code for me, which I then type in the phone.

---

### Post by ubername on 2008-10-12
Just installed Gnokii. It just sits there trying to connect. Wammu crashes on start up. Hmm - harder than I thought.

---

### Post by Tom--d on 2008-10-12
What I think has happened is there was no driver for your Bluetooth in the kernel 2.6.24 (which is in Ubuntu 8.04) but in 8.10, the kernel is 2.6.27 which has your bluetooth support which you need.

---

