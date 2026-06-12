---
title: "I just upgraded to 8.04 and I need help with graphics"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by cpu_medic on 2008-07-16
so as the post states, i have just upgraded to ubuntu 8.04. i have an ibm t42 laptop with a ati rage 7500. (i know i need to upgrade but i dont have th $$$) with 7.10 i had all the compiz stuff(the desktop cube, wobbly windows, etc.) working. now it doesnt. do i need new drivers? or should i just stick with 7.10? please help :(

---

### Post by nowshining on 2008-07-16
have u ran a check and installed all updates?

---

### Post by mike290481 on 2008-07-16
Hi I have this is my first time using a linux based OS. I am using ubuntu and cant seem to find any details about my graphics card and when I try to enable visual effects it wont let me. Looked at help and it said enable a restricted driver went to the restricted drivers and there werent any. Any ideas?

---

### Post by Ryadt on 2008-07-16
In terminal type
```
lshw -C Display
```
this will give you your graphic card.
If you are using Hardy then Restricted Drivers is known as Hardware Drivers. System > Administration > Hardware Drivers.

---

### Post by mike290481 on 2008-07-16
Thanks for quick reply I am using Ubuntu where do i put that code in

---

### Post by Ryadt on 2008-07-16
In the terminal.Application > Accessories > Terminal.

---

### Post by mike290481 on 2008-07-16
I found it. Thank You.

---

### Post by mike290481 on 2008-07-16
This is what it produced. Do i just get a driver off ATI or is there an ubuntu driver site?

username@username-desktop:~$ lshw -C Display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV100 QY [Radeon 7000/VE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32 mingnt=8
username@username-desktop:~$

---

### Post by Ryadt on 2008-07-16
Go in Hardware Drivers and enable the driver.

---

### Post by mike290481 on 2008-07-16
It just says "there are no proprietary drivers in use on this system"

---

### Post by Ryadt on 2008-07-16
Try this in terminal
```
sudo apt-get install xorg-driver-fglrx
```
Then retry to enable the driver in Hardware Drivers.

---

### Post by philinux on 2008-07-16
> **mike290481 said:**
> Hi I have this is my first time using a linux based OS. I am using ubuntu and cant seem to find any details about my graphics card and when I try to enable visual effects it wont let me. Looked at help and it said enable a restricted driver went to the restricted drivers and there werent any. Any ideas?

I think you've hijacked the OP thread. Not a good thing to do. Next time you really should start your own

---

