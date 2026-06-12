---
title: "printer problem"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by retlawmc on 2008-09-10
I am trying to get my network printer installed on my Ubuntu machine.  Brother( the printer manufacturer) lists this set of instructions on how to install the printer.

# I'm using Ubuntu 8.04. I have installed the drivers, but I am still unable to print.


Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)


Unfortunately, I cannot even uninstall the cupswrapper driver.  can you help?
Thanks

---

### Post by Vivaldi Gloria on 2008-09-10
Do you have the ppd file of your printer?

---

### Post by jemate18 on 2008-09-10
> **retlawmc said:**
> I am trying to get my network printer installed on my Ubuntu machine.  Brother( the printer manufacturer) lists this set of instructions on how to install the printer.

# I'm using Ubuntu 8.04. I have installed the drivers, but I am still unable to print.


Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)


Unfortunately, I cannot even uninstall the cupswrapper driver.  can you help?
Thanks

Have you tried installing via System -> Admistration -> Printing ?

there is an entry for brother there... What model do you have?

---

### Post by retlawmc on 2008-09-11
my model printer is Brother mfd 7420.


I don't have the ppd version of the driver.

---

### Post by Vivaldi Gloria on 2008-09-11
> **retlawmc said:**
> my model printer is Brother mfd 7420.


Do you mean mfc 7420? 

[https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

says that drivers for it are in ubuntu multiverse repositories. So enable multiverse repos and install the drivers in synaptic.

---

### Post by retlawmc on 2008-09-23
Resolved!!!
That fixed it.  Thanks
Walter

---

### Post by jemate18 on 2008-09-23
> **retlawmc said:**
> Resolved!!!
That fixed it.  Thanks
Walter

Would you please POST the steps on how were you able to RESOLVE IT so that other users with similar problems will have insights..

---

