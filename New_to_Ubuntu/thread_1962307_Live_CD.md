---
title: "Live CD"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by Deadman390 on 2012-04-20
is there anyway possible to create a LiveCD on a usb stick.  i have no internet access and am currently trying to get ndiswrapper. i have read that it is in the repository on the livecd but since i had to use a iso file to install (old motherboard unable to boot from usb) i think i have missed out on all the goodies that comes with the livecd.  desperate need of help so that i can get my wireless to work and finally get on with the fun

---

### Post by critin on 2012-04-20
> **Deadman390 said:**
> is there anyway possible to create a LiveCD on a usb stick.  i have no internet access and am currently trying to get ndiswrapper. i have read that it is in the repository on the livecd but since i had to use a iso file to install (old motherboard unable to boot from usb) i think i have missed out on all the goodies that comes with the livecd.  desperate need of help so that i can get my wireless to work and finally get on with the fun

Yes, unetbootin creates live usb's.   But if you installed an iso file, it should have everything already.  If you're using 11.10, it won't have synaptic package manager installed, so synaptic has to be installed through Software Center.   Was the iso installed by a CD?  

The live usb must be able to boot, and if anything is installed on it while live, it won't save it unless you've made it persistent before copying the iso onto it.   All the goodies are on the iso, and it doesn't matter how its installed--it's the same iso.

---

### Post by sffvba[e0rt on 2012-04-20
I am not sure that a livecd is the answer to your problem.

Looking at this ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) at point 2.2 it shows how to get and use ndiswrapper if you have internet access available on a secondary system.


404

---

### Post by josephmills on 2012-04-20
> **Deadman390 said:**
> is there anyway possible to create a LiveCD on a usb stick.  i have no internet access and am currently trying to get ndiswrapper. i have read that it is in the repository on the livecd but since i had to use a iso file to install (old motherboard unable to boot from usb) i think i have missed out on all the goodies that comes with the livecd.  desperate need of help so that i can get my wireless to work and finally get on with the fun

What is your wireless card ? can you open up your terminal and enter in 
```
lspci -nn 
```

look for your card it is something like 

12:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)


I am sure you know your card already if you are trying to use ndiswrapper 
I have seen that most if not all cards now-a-days do not need this anymore. Maybe we can do a work-a-around ? 

Thanks

---

### Post by Deadman390 on 2012-04-20
i tried the link you had up there and all it does is act like a link to the software center i have all of those files currently on my machine with ubuntu on the desktop but everytime i click them all it does is link me to software center where the install button is greyed out

EDIT
Its a usb card its the Netgear n300 wna3100 my ethernet port on the tower is completely gone

---

### Post by Deadman390 on 2012-04-20
> **critin said:**
> Yes, unetbootin creates live usb's.   But if you installed an iso file, it should have everything already.  If you're using 11.10, it won't have synaptic package manager installed, so synaptic has to be installed through Software Center.   Was the iso installed by a CD?  

The live usb must be able to boot, and if anything is installed on it while live, it won't save it unless you've made it persistent before copying the iso onto it.   All the goodies are on the iso, and it doesn't matter how its installed--it's the same iso.

I had to mount the iso and install from windows bc i dont have a blank dvd and my motherboard is to old to boot from usb :(

---

### Post by Deadman390 on 2012-04-20
> **not found said:**
> I am not sure that a livecd is the answer to your problem.

Looking at this ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) at point 2.2 it shows how to get and use ndiswrapper if you have internet access available on a secondary system.


404

ok i think i found what you were talking about and i got it on there i am trying to follow his directions but i cant get the directory right i guyss i tell it 

sudo dpkg -i ndiswrapper-common.deb/desktop 

like the guy said place it in a directory like home folder i fig desktop would work and it keeps giving me errors 

cannot access archive:no such file or directory

im lost and confused now lol

---

### Post by josephmills on 2012-04-20
> **Deadman390 said:**
> 
EDIT
Its a usb card its the Netgear n300 wna3100 my ethernet port on the tower is completely gone

Could you give us the number that is under the command that I asked for? The one that is in []  
like on mine it is the part in red 


12:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express)[COLOR="Red"] [168c:002b][/COLOR] (rev 01)


thanks

---

### Post by Deadman390 on 2012-04-20
> **josephmills said:**
> Could you give us the number that is under the command that I asked for? The one that is in []  
like on mine it is the part in red 


12:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express)[COLOR="Red"] [168c:002b][/COLOR] (rev 01)


thanks

when i type in the command network adapter doesnt even show up on the list

---

### Post by josephmills on 2012-04-20
> **Deadman390 said:**
> when i type in the command network adapter doesnt even show up on the list


Is this a usb ? if so lets see 
```
lsusb
``` 
please

---

### Post by Deadman390 on 2012-04-20
> **josephmills said:**
> Is this a usb ? if so lets see 
```
lsusb
``` 
please

yes i just pulled it up actually its a broadcom BCM43231 and i think it installed in did the unpackage and installing in the terminal and i even got ndisgtk but i cant find where to access it in order to get the drivers for the device i have up and running

---

### Post by Deadman390 on 2012-04-21
ok i have succesfully slapped my ketboard in the correct sequence and installed ndiswrapper and ndisgtk althought it doesnt work lol and now i have installed the drive only to get incorrect driver......what now lmfao

---

