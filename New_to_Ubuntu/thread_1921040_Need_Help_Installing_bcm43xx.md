---
title: "Need Help Installing bcm43xx"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by Alo1 on 2012-02-06
Ok so, I installed Ubuntu v11.10 on my Presario c500 laptop. Im completely in love with ubuntu but after installing, im having a problem with my bcm4311 network controller.

Im not able to get online with my laptop that has ubuntu installed so im not able to perform an update to get the drivers automatically. Using a cable to plug into my router is NOT an option. Completely impossible for me :)

So as you can probably guess im not able to pick up any wifi connections with my laptop now. What i can do though is connect to the internet with my desktop that runs windows, download files from there, and bring them over to my laptop with ubuntu  via flash drive.

I installed ubuntu with an external hard drive formatted as a FAT32 so i could boot and install on startup.

So im in need of in depth help (Im really new to this stuff so try to make everything as simple as you can) on what i should do. I have to do everything on my laptop offline, though i can still download files and bring them over to my laptop. keep that in mind please!

Im really desperate at this point, help would be much appreciated!

---

### Post by dgharmon on 2012-02-06
> **Alo1 said:**
> Ok so, I installed Ubuntu v11.10 on my Presario c500 laptop. I'm completely in love with Ubuntu but after installing I'm having a problem with my bcm4311 network controller. I'm not able to get online from the installed Ubuntu laptop, so I'm not able to perform an update to get the drivers automatically. Using a cable to plug into my router is NOT an option, completely impossible for me :)

Bring the computer to a local Internet Cafe and ask permission to plug it into the network then following the instructions here: [Ubuntu 11.10 getting wireless BCM4311 working]("http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/")

---

### Post by DGINSD on 2012-02-06
This site helped me [http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

### Post by westie457 on 2012-02-06
Boot your system normally then plug in the USB stick you used to install with. When the File Browser opens navigate your way to pool > main > b. here you will see 2 folders open the one called 'build-essential' and double click on the .deb file. After that go to the folder called 'b43-fwcutter' again double clicking on the .deb file.When things have settled down wait for about a minute then click on the Network Manager icon at the top of the screen (left hand end of all the icons on the right), you should see a list of available networks. If you see nothing there then reboot and check again.

Any problems post back here and we will try something else.

---

