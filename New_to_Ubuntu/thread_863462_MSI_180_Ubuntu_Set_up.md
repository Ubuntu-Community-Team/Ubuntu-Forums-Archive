---
title: "MSI 180 Ubuntu Set up"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by XRichX on 2008-07-18
Hello again everyone, 

I have a MSI Mega 180 that i use for playing Unreal Tournament 2004 with my clan while on Teamspeak etc. I got a virus on XP and the whole system required a re-install, the hard drive went wrong and was unusable, i thought well i have a Ubuntu CD so why not use that? 

I am now on Linux Ubunut (Latest Version) and typing to you now on Ubuntu Firefox, the problems being (only two) the Belkin N Wireless adapter and onboard Nvidia Graphics.

1; The Belkin Network N wireless isn't working correctly, i need to be connected wired for the internet to work. I tried to follow the instructions on usng the actual windows drivers that i have on CD but the program it required me to get isnt on the package manager. Can someone find me or point me in the right direction to setting up the wireless?

2; Nvidia graphics accelerator on the hardware drivers list in Linux just gives a '404' error when downloading, which means it doesn't exist. Does anyone know of a Nvidia driver for the Geforce 4 MX?

Thanks guys! :KS

---

### Post by LowSky on 2008-07-18
First you need to enable the extra repos. Go to System> Admin> Software Sources. Make sure all the options are checked, EXCEPT Source code and Ubuntu CD. Then close the window and let it update.

As for the drivers

go to a terminal window (Applications > Accessories > Terminal)
For the program that ill help with network drivers
Type in ```
sudo apt-get install ndiswrapper
```
for the nvidia
go to System>Admin>Restricted Drivers
just click to use the driver

---

### Post by XRichX on 2008-07-18
Thankyou for your reply, i went to that software sources window and its all already checked apart from the Cd and Source, but still not working. As for the graphics card, i typed the command and got the following;

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper


Problem righ? Why is nothing simple nowadays!

---

### Post by cariboo on 2008-07-18
To down load ndiswrapper to get your wireless running in a Applications-->Accessories-->Terminal type:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

This will install ndiswrapper as well as a gui to help you set things up. Make sure you have your windows driver disk, as ndiswrapper needs the *.inf file to work properly.

For your video card go to System-->Administration-->Hardware Drivers put a check mark in the box beside Nvidia (Not sure what is in the windows as I am using the Interpid alpha version and it doesn't work properly yet) It should download the proper driver for you and then it will ask you to restart,

Jim

---

### Post by XRichX on 2008-07-18
> **cariboo907 said:**
> To down load ndiswrapper to get your wireless running in a Applications-->Accessories-->Terminal type:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

This will install ndiswrapper as well as a gui to help you set things up. Make sure you have your windows driver disk, as ndiswrapper needs the *.inf file to work properly.

For your video card go to System-->Administration-->Hardware Drivers put a check mark in the box beside Nvidia (Not sure what is in the windows as I am using the Interpid alpha version and it doesn't work properly yet) It should download the proper driver for you and then it will ask you to restart,

Jim
Hey Jim, thanks for your support too. Tried that command and got;

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common


For the hardware drivers, it just comes up with a 404 error when clicking on the tick box. Any ideas?

Regards,

Rich

---

### Post by LowSky on 2008-07-18
try using EnvyNG it actually downloads and compiles the driver from Nvidia's website

```
sudo apt-get install envyng-gtk
```

run it from Applications > System > EnvyNG

---

### Post by XRichX on 2008-07-18
> **LowSky said:**
> try using EnvyNG it actually downloads and compiles the driver from Nvidia's website

```
sudo apt-get install envyng-gtk
```

run it from Applications > System > EnvyNG
Hello :) Thanks for your reply. I think im having a big problem with these packages;

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk


thats the error.

---

### Post by cariboo on 2008-07-18
It looks like you are not connected to the internet, ndiswrapper is also on the hardy cd. Navigate to pool-->main-->n and you will see two folders ndisgtk and ndiswrapper. Double click on the ndiswrapper folder then double click ndiswrapper-utils this will bring up an application called Package Installer click the install button and it will install ndiswrapper for you. Next open the ndisgtk folder and double click it and the installer will open, click the install package button and ndisgtk will install. That should get you started.

Once you have your network setup then use the previous instructions to set up your video card.

---

### Post by XRichX on 2008-07-18
> **cariboo907 said:**
> It looks like you are not connected to the internet, ndiswrapper is also on the hardy cd. Navigate to pool-->main-->n and you will see two folders ndisgtk and ndiswrapper. Double click on the ndiswrapper folder then double click ndiswrapper-utils this will bring up an application called Package Installer click the install button and it will install ndiswrapper for you. Next open the ndisgtk folder and double click it and the installer will open, click the install package button and ndisgtk will install. That should get you started.

Once you have your network setup then use the previous instructions to set up your video card.
Thanks for your reply, i installed ndiswrapper with the package installer, what do i do now? Sorry for being such a novice :P

---

### Post by cariboo on 2008-07-18
I haven't used ndiswrapper for several years, but I'll give it a try. Go to System-->Administration-->Windows Wireless Drivers and click it will bring up a window and ask for your password enter that, Next you will see a window called Wireless Network Drivers. Click Install New Driver, navigate to where your windows drivers are and select the inf file then click install. Once the driver is install click configure network, this brings up the Network Manager, click on you wireless adapter and then click properties make sure roaming mode is enabled. If everything went OK you should have wireless access. I'm typing this on my laptop and I didn't have to go through all these steps as my wireless nic was detected and installed automagically. I'm using Mint Linux and the ndiswrapper gui was already installed so I could help you that far, but I thnk this is about as far as I can help you cause I think my knowledge of wireless adapter installs just ran out.:)

Jim

---

### Post by XRichX on 2008-07-18
lol :) Well thanks for your continued help and detailed explanation, got one problem... havent got 'Windows Wireless Drivers' in the system > Admin menu :( But i followed your instructions to install it off the disk and it was successful. Should i install it another way?

---

### Post by XRichX on 2008-07-18
UPDATE: Good news :) The nVidia driver is finally not giving 404 no more and i have installed it successfully, all i need now is the Realtek (built in wireless) or Belkin (Wireless USB adapter) to work with ndiswrapper, but i need help with that :( (Read previous post), cheers again.

---

