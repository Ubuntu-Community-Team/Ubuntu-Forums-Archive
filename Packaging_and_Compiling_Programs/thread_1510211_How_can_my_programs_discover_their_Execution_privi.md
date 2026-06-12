---
title: "How can my programs discover their Execution privileges?"
date: 2010-06-15
forum: Packaging and Compiling Programs
---

### Post by Kerubu on 2010-06-15
I'm writing some programs that use the libusb libraries to access usb devices using code written in user space. However with just normal user privileges the functions my program can do are limited e.g. I cannot even open a device.

To open a device I have to execute my program with 'sudo' to give it superuser rights. Now yes I know this is bad programming but it's only a temporary measure.

But what I'd like to know is how can I or what code do I need to include for the program to check what privileges it has when it is executed?

Many thanks

Kerubu

---

### Post by SevenMachines on 2010-06-16
hi, i imagine the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") is probably the better place for this. i dont know libusb but if the library calls _open() and doesnt have the privileges then it should return an error or a value to let your program handle it, thats effectively the way the program handles discovering its privileges. still, they'll know more in the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") about this.

---

### Post by Kerubu on 2010-06-16
> **SevenMachines said:**
> hi, i imagine the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") is probably the better place for this. i dont know libusb but if the library calls _open() and doesnt have the privileges then it should return an error or a value to let your program handle it, thats effectively the way the program handles discovering its privileges. still, they'll know more in the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39") about this.

Thanks SevenMachines. I just noticed I made my post in the packaging forum !! Slip of the mouse click there by me.

libusb does indeed give an error if it tries to execute without the correct privileges but I'd like to know how my program can check without the need for libusb failing. Afterall libusb somehow manages to check it's rights.

anyway.. time to post this thread in the correct place !

---

### Post by Umang on 2010-06-17
By running `less /usr/share/applications/synaptic.desktop` I saw that Synaptic uses su-to-root. Is that what you are looking for? (I am not very sure myself)

---

