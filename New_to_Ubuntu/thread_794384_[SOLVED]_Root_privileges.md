---
title: "[SOLVED] Root privileges"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by ellalan on 2008-05-14
Hi
I am trying to install the USB ADSL modem manager and when I try to do the authentication I get a message
"The firmware needs to be copied to /lib/firmware, For this to happen Root privileges are needed"
Could someone help me with this please. I am completely lost and I would appreciate any help and thank you.

---

### Post by shifty_powers on 2008-05-14
how are you trying to install it?  synaptic? apt-get? what?

---

### Post by will1911a1 on 2008-05-14
If you're installing through the command line you should be using sudo to run the installation with root access.

---

### Post by NightwishFan on 2008-05-14
put ```
sudo
``` before any command that needs to be run as root.

---

### Post by ellalan on 2008-05-14
Hi
I have installed the downloaded .deb file using debian package installer.When I tried to Authenticate with the user name and password, this message appears.
I have previously used this modem but yesterday I had to change the password and my IP provided a new password.
When I was using the previous password the installation was smooth and I didn't have any problems.
My OS is Ubuntu7.10 and the modem is Speedtouch 330. I'll keep on trying.
Thank you all for the quick response.

---

### Post by shifty_powers on 2008-05-14
what is the deb file you downloaded?

---

### Post by ellalan on 2008-05-15
Hi Shifty_powers,
It is usbadslmodemmanager  0.5.8 i386.deb,written by Steven Harper for Speedtouch 330 modem users. Thank you.

---

### Post by ellalan on 2008-05-15
Hi,
I have solved the problem by following the instructions in Troubleshooting section of the installation procedure. I have removed the conflicting files from my previous installation and removed the usbadslmodemmanager in Synaptics then I installed the modem manager and it worked.
Thank you all for your help and support.

---

### Post by shifty_powers on 2008-05-15
good. glad you got it sorted would have replied but i was sleeping. even i have to occasionally ;)

---

