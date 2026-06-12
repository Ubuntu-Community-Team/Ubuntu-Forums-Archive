---
title: "Ubuntu as overpowered NAS? Never touched linux before."
date: 2015-11-07
forum: New to Ubuntu
---

### Post by wesley12 on 2015-11-07
Hello all,

I am brand new to linux and I'm building a new computer. I plan on using it as a compact gaming pc while I am out of the country for work, and plan to leave my main large tower at home. Once I'm done with that year post I plan on using my main tower and re-purposing this new rig. I want both a media pc and a NAS and was wondering if I could take out two birds with one stone here. 

The specs are as follows:

CPU: Intel i5 4590
MOBO: ASRock H97M-ITX/AC
RAM: 16GB Mushkin DDR3 1600mhz
HDD: Plan on adding drives once I've completed my assignment.
SDD: 240gb Sandisk Ultra II
Case: Bitfenix Prodigy black
PSU: Corsair CX 500M

Any help would be awesome. I have a decent windows background and am trying to transition into the IT field but as of now my experience is limited to the mild amount of dabbling I do, mainly with PC gaming.

---

### Post by tea for one on 2015-11-07
Good evening

Are you familiar with running a "live" Linux OS from a DVD or USB stick?

Have a look at this site for a wealth of information.

[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

I would heartily recommend a trial using a "live" USB to see if:-

You like it?
There are no problems with your hardware?

Best wishes

---

### Post by wesley12 on 2015-11-07
I am not familiar with running a "live" Linux OS. Does that mean the USB would be the boot drive to test out Ubuntu? How would that work in regards to running both ubuntu as a home media OS and FREENAS or something similar as a NAS?

EDIT: I'm looking up a guide to run a virtual machine running ubuntu on my main pc (secondary pc components haven't arrived yet).

---

### Post by grahammechanical on 2015-11-07
The recommendation to run a live session is so that you can try Ubuntu before you install it.

Creating a boot able USB stick with Ubuntu on it

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

After that it is a matter of putting the USB drive into the USB port and then setting the BIOS to boot from the USB stick instead of the hard disk. If only it was that simple! Actually it is that simple on my machine.

What other OS do you have on that machine? If it is Windows 8 or 10 then read this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I will leave it to others to speak about using Ubuntu as a media server or as Network Attached Storage.

[https://en.wikipedia.org/wiki/Network-attached_storage](https://en.wikipedia.org/wiki/Network-attached_storage)

Regards

---

### Post by tea for one on 2015-11-07
> **wesley12 said:**
> I am not familiar with running a "live" Linux OS. Does that mean the USB would be the boot drive to test out Ubuntu? How would that work in regards to running both ubuntu as a home media OS and FREENAS or something similar as a NAS?

EDIT: I'm looking up a guide to run a virtual machine running ubuntu on my main pc (secondary pc components haven't arrived yet).

When you run a "live" Linux OS, you can make sure that your ethernet, wireless, sound and other devices (etc) function OK.

I would recommend a live trial instead of a virtual machine in a Windows environment because it is easier and it will be good fun.........i.e if you have never done it before, you will be pleasantly surprised.

Good luck

---

### Post by dvks on 2015-11-07
If you are willing to install Ubuntu you can have it function both as NAS and as a multimedia center+server and you can also still reinstall your existing windows system as a virtual machine and access it from any computer on the network ether as a virtual machine or as a thin client (if you install LTSP server too on the NAS machine).
For the NAS function you can have SAMBA for connection to windows/Linux networks , NFS mostly for Linux and iscsi for remote drive assignment. 
For storage you can ave both RAID and Logical volume- LVM2
For the media center you may use KODI/XBMC Myth or other options
For multimedia server you may use Susonic
Most of the above protocols and apps are well documented and with good community help
This is a short list of endless options
You can also take a look at some preconfigured complete systems such as KeyScan KSNAS servers etc.

---

