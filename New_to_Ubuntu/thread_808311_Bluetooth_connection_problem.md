---
title: "Bluetooth connection problem"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by ConcreteDonkey on 2008-05-26
I have just started to have problems with my bluetooth connection, I frequently use my USB Bluetooth drive to transfer files between my phone and computer this has worked perfectly up till now, At first I tried getting the phone to send a file through its "Recent Devices List" when I selected my computer it said "Service not Supported".

I then tried to remove the bonding between the computer and phone after I did this I set the computer to "Discoverable and Connectable" although my phone cannot even see the computer. I have also tried my older phone and it is having the exact same problem. I have made sure that the computer has the "Recieve Files" is on which it is. 

I have tried most basic things such as restarting the computer, taking the battery out of the phone and unplugging and replugging in the bluetooth module but with still no luck.

Any help would be appreciated,

---

### Post by kostkon on 2008-05-27
Try to restart the bluetooth service of your PC by doing
```
sudo hciconfig hci0 reset
```
and then try again.

---

