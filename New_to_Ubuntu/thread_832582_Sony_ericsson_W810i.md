---
title: "Sony ericsson W810i"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-06-17
Hi all,

  i am having ubuntu hardy heron in my box. My mobile model is Sony ericsson w810i. i have sony ericsson CD to communicate with PC but it install with windows only. I dint tried that CD in ubuntu. Shall i proceed with same CD to install sony ericsson S/w in my PC with ubuntu? If not wat else the option i have to do it. i used to upload photos from mobile to PC. please help me and thanks in advance.

---

### Post by hariprs on 2008-06-17
Hi,

By simply connecting the mobile you should be able to see your memory card mounted in the ubuntu and you can copy the contents from the mobile to PC or vice versa. If you want to do more then see the below link.
[http://howtoforge.com/fedora8-bluetooth-wammu-mobile-phone](http://howtoforge.com/fedora8-bluetooth-wammu-mobile-phone)

---

### Post by mailtwogopal on 2008-06-19
hi,

i connected my sony ericsson w810i to my ubuntu box. my phone recognised that it is connected to PC, but nothing turns up on PC. i typed the "lsusb" command and i could see "Sony ericsson connected". following is the o/p of lsusb command.

home@home-desktop:~$ lsusb
Bus 003 Device 002: ID 0fce:d042 **Sony Ericsson Mobile Communications AB **
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

what i can do to communicate with PC. i tried both modes "File transfer" as well as "Phone mode", but in vain. i also restarted my PC with plugging in the mobile, but that too turned nothing up. please help me. i also read some articles from this forum. with that as reference i installed "multisync" but i dont know how to synchronize my mobile with it. can u guys help me hopefully. thanks in advance.

---

### Post by rraj.be on 2008-06-28
> **mailtwogopal said:**
> 
what i can do to communicate with PC. i tried both modes "File transfer" as well as "Phone mode", but in vain. i also restarted my PC with plugging in the mobile, but that too turned nothing up. please help me. i also read some articles from this forum. with that as reference i installed "multisync" but i dont know how to synchronize my mobile with it. can u guys help me hopefully. thanks in advance.


You dont need any special drivers installed for your mobiles.


i am too using the same  mobile.

could i know  what happens when you select FILE TRANSFER MODE.

---

### Post by Daverobb on 2008-06-29
hey,

i have a similiar problem -- my w810i does connect with my hardy and appears on the desktop as a phone drive and a separate memory stick icon.  i can see everything there and even pull anything over to my system but i cannot do the reverse - ie. copy music or anything onto the phone or mem stick.  (obviously this is in 'file transfer' mode) 

the error message in hardy is that the drive is a read only and i do not have permission to copy onto it.  i've looked around a bit for forums about changing drive permissions for external drives but get nothing.  Weird too because my usb external works flawlessly.

thoughts or suggestions?

---

### Post by prabath_fun on 2008-07-29
Hi,
   I got sony ericssion W810I and Hardy in my PC. I tried copy and paste of files in 'file transfer' mode. It is working fine.
  In order to avoid, missing, calls during my phone is in file transfer mode, I tried with gmobile Media and wammu.

With wammu -> I can able to retrive the messages (SMS) and phone numbers from my mobile. But could not able to get SIM contacts and call details. I can able to send SMS with help of it. But, It is not updating it in my mobile as like Myphoneexplorer in windows.

With gmobile media -> I can able to transfer file in 'phone mode' only if no memory stick is inserted. With memory stick, Gmobile scans and in between hangs and no response there after. Sometimes, It get closes and there after I have to restart my PC.

Please help me to solve the above mentioned problem. I am using USB cable. I dont have bluetooth interface in my Desktop or no Bluetooth doungle.

Prabath

---

### Post by rraj.be on 2008-07-29
> **Daverobb said:**
> hey,


the error message in hardy is that the drive is a read only and i do not have permission to copy onto it.

Just try copy paste with sudo command.

Else just type this in terminal
```

sudo nautilus
```

This will open your nautilus browser in super user mode, so that you can copy with out any permission restrictions

---

### Post by Daverobb on 2008-08-03
I found another solution to the whole issue -- i lost my phone!  Now I can start from scratch.  Maybe an iphone - has anyone tried the new 'neo' linux wifi phone yet?

---

### Post by prabath_fun on 2008-08-03
Hi,
  Still my problem exista. Anybody got the solution?
Description:
I got sony ericssion W810I and Hardy in my PC. I tried copy and paste of files in 'file transfer' mode. It is working fine.
In order to avoid, missing, calls during my phone is in file transfer mode, I tried with gmobile Media and wammu.

With wammu -> I can able to retrive the messages (SMS) and phone numbers from my mobile. But could not able to get SIM contacts and call details. I can able to send SMS with help of it. But, It is not updating it in my mobile as like Myphoneexplorer in windows.

With gmobile media -> I can able to transfer file in 'phone mode' only if no memory stick is inserted. With memory stick, Gmobile scans and in between hangs and no response there after. Sometimes, It get closes and there after I have to restart my PC.

Please help me to solve the above mentioned problem. I am using USB cable. I dont have bluetooth interface in my Desktop or no Bluetooth doungle.

Prabath

---

