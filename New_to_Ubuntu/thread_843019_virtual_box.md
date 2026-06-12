---
title: "virtual box"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-27
got it installed created VM and now want to install vista.  it's not installing.  there is an error window "fail to access usb subsystem"  is this why after mounting my dvd drive nothing installs or is it something I'm not doing?  what can I do?

---

### Post by flytripper on 2008-06-27
make sure nothing is mounted in the usb icon at the bottom .....also maybe try installing with usb disabled

---

### Post by adamogardner on 2008-06-27
i don't really now what that means..lets see, under settings i hilight USB and it is not selected.  I tried selecting it but nothing happens  it deselects on its own.

---

### Post by adamogardner on 2008-06-30
how do i set write permissions for /dev/vrboxdrv by adding them to vboxusers group?  this is what the window says to do.

---

### Post by damis648 on 2008-06-30
For the permissions:
Go to System>Administration>Users and Groups and unlock it with your password. Go to Manage Groups and get to the properties of the "vboxusers" group. Put a check next to your user and root. Click OK and close that.

For the USB message:
Open a terminal and type
```
sudo gedit /etc/fstab
```
and enter. Type your password. At the end of the document that opened, paste in
```
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
at the very end. USB devices will now work when mounted in the VM.

Now reboot and your problems will be solved. :popcorn::popcorn::popcorn:

---

### Post by bumanie on 2008-06-30
Suggest you download the binary (free for home use) from the sun/innotek site and then follow [this guide]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")

---

### Post by dondad on 2008-06-30
> **adamogardner said:**
> got it installed created VM and now want to install vista.  it's not installing.  there is an error window "fail to access usb subsystem"  is this why after mounting my dvd drive nothing installs or is it something I'm not doing?  what can I do?


If you are using the open source version from the repos, it doesn't support usb. To get that, you need to download and install the binary version from the virtual box website.

---

### Post by adamogardner on 2008-06-30
how do I check to see what version I have? 

The usb warnning popps up when I hit the settings button, still after follow damis' s directions

---

### Post by damis648 on 2008-06-30
Did you reboot? And could you paste the exact message?

---

### Post by adamogardner on 2008-07-01
yes i rebooted   i cant copy and paste  but will write it out,   also I got several operating systems started on it but there is a problem getting any touchpad control.  Could this be why the USB window popps when I hit the settings button?

'failed to access the usb subsystem
could not host the usb proxy service (VERR_FILE_NOT_FOUND)
THE SERVICE MIGHT NOT BE INSTALLED ON THE HOME COMPUTER      {sorry caps on}

then it goes on to describe the result code, component, interface and callee; 0x00004005, Host, IHost, Ihost{81729c22-laec-46f5-b7co-cc7364738fdb, and IMachine{f95c0793-7737-49a1-85d96da81097173b} , respectively.  Thanks for helping out!

---

### Post by wariskampar on 2008-07-01
Facing similar problem this morning. Able to solve it by following instruction in this page:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

Make sure to re-start

Success!

---

