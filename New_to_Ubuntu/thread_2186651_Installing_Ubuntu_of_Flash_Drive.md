---
title: "Installing Ubuntu of Flash Drive"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by cowboy.bebop on 2013-11-08
What would be the best route to installing ubuntu on to a flash drive (usb)? Is it better to create the LiveISO and save data to the flash while in LiveISO format, or repartition the flash drive and installing to new partitions? I was wondering if installing to partitions would cause the OS to be hardware dependant of the originating system that you installed ubuntu on and wont be compatible when using the flash drive between devices such as laptops or PC's.

I tried using gparted under crucnhbang to partition the USB but when I booted up, it stayed in TTY and after running startX, it failed and stayed in TTY, at this point I figured it depended on the hardware of the Virtual OS that I installed it from.

---

### Post by grahammechanical on 2013-11-08
This works for me.

1) Download the ISO image

2) follow the instructions on this page

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

Make sure you tick the button Stored in Reserved Extra Space and then move the slider to give as much space as allowed. Then the result will be a Live Ubuntu session that you can use to install Ubuntu to hard disk but also use as an OS that you can install applications on and also store data. And because it works as a live session it should be hardware independent.

Regards.

---

### Post by newb85 on 2013-11-08
Either way, you'll likely have trouble if you use more than generic drivers. 

Best to stick with a live iso with extra space or a persistence file.   There are directories in Ubuntu file structure that chance a lot.   All those writes will eventually wear out your flash drive if you do an actual install.

---

### Post by monkeybrain20122 on 2013-11-08
Depends on what you want to do with the flash drive. If you make a live usb with persistence it is in FAT format and cannot normally access more than 4G of storage and doesn't support certain operations, like updating kernel or installing kernel module and proprietary graphic drivers. If you do a real install in the flash drive (partition into ext4, yada yada) then it is a normal Ubuntu installation except that it is now portable. Now I never tried this with usb3 but my experience is that if you install in a flash drive Ubuntu is kind of slow. Installing and updating would take a long time and the system hangs frequently if multitasking, however, if you do it on an external hard drive instead then you get the same speed as installing internally (any external hard drive works a lot better than flash drive, even for old hard drives you remove from broken laptops as long as the drive is not damaged)

To install in an external or usb drive you need to create a live CD or a live usb first, then connect the targeted usb drive to the computer and install. Choose "something else" and make sure you install into the correct drive and **very important** make sure you install the boot loader in the correct drive. You should be able to boot and run on any machine on which Ubuntu works. It shouldn't be dependent on hardware on which you create the installation unless you have installed proprietary graphic cards (then obviously it won't work on machines with different cards)

---

