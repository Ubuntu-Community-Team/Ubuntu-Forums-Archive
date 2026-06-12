---
title: "[SOLVED] bluetooth, k610i and connecting to the internet"
date: 2008-11-04
forum: Philippine Team
---

### Post by tagabukid on 2008-11-04
i connect my desktop pc to the net through my k610i and and the datacable that came with the phone. this works very well and i can control the connection with the network manager. however the signal coverage in my area is sometimes spotty and i have to put my phone at a higher perch just to get a signal. now this is impossible with the datacable still tethered to it.

when the signal really drops i use bluetooth to connect so that i can put the phone at a higher perch. although it's not as painless as using a datacable it still works well. the way i do it is with the terminal i use the following commands after enabling bluetooth internet sharing on the phone and selecting the proper APN ('smart internet' in my case):
```
 sudo pand --role PANU --connect 0x:xx:xx:xx:xx:1C 
```
then: ```
 sudo dhclient bnep0
```

my question is this, how do i make a shellscript so that i only have to type in the command in the terminal only once using a shell script?

i tried: ```
!#
sudo pand --role PANU --connect xx:xx:xx:xx:xx:xx
sudo dhclient bnep0

```

it doesn't work all the time since there should be a pause between the two commands. it should be the sudo pand etc. wait, wait, wait (15 to 30 seconds seem to be enough) then the sudo dhclient... i have found a tutorial that uses some configuration editing of /etc/default/bluetooth but that didn't work for me.

thanks for anyone that can help. ):P

---

### Post by tagabukid on 2008-11-05
anyone wants to take a stab at this? or at least offer another way to connect bluetooth internet.. anyone? any comments at all?

---

### Post by Hobgoblin on 2008-11-05
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

Although I found you only need to do the pairing and setting up rfcomm0 then the rest can be done via GUI with Gnome-PPP, specifying /dev/rfcomm0 as the modem.

In answer to your question, instert **sleep 30** between the two lines in your script, that will wait 30 seconds between commands.

---

### Post by tagabukid on 2008-11-06
i actually have that page saved to disk. but gave up trying to make it work that way on my previous gutsy install and didn't bother when i upgraded to hardy after i found the howto using **pand**. that has been how i have been connecting, but i will have to try gnome-ppp. thanks!

thank you also for the fix on my script with **sleep**. i will have to try it after i type this reply and log off. ;-)

and very much later:

it works!

```
#!/bin/bash
sudo pand --role PANU --connect xx:xx:xx:xx:xx:1C
sleep 30
sudo dhclient bnep0
```

thank you!

using the phone with the datacable has been very flaky lately and i have been using this script a lot.. ):P

---

