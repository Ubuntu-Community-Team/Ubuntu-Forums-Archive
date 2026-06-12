---
title: "quick question while installing nvidia drivers (What is &quot;Change to init 3&quot;?)"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by swarup on 2011-11-17
My question regards the instructions on [this]("http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html") site

I am pasting the instructions from the site here. There is one instruction I don't understand. In the below instructions, step #6 says "Change to init 3". What does that mean? How do I do it? Am I supposed to go back into the recovery mode root console, as I had been instructed to do for the previous steps, and type that there?

-------------

How To : Install NVIDIA Graphic Card Driver on Ubuntu 10.10

To install NVIDIA driver, of course, you must disable the Kernel Nouveau. Ok, let’s start it from beginning.

1. Go to NVIDIA website and download the compatible driver for your graphic card series.
2. Reboot your Ubuntu.
3. Choose the ‘Recovery Mode’ on GRUB.
4. Go to the bottom of menu list, choose ‘root console’.
5. Disable the Kernel Nouveau.

#echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
#update-initramfs -u

Reboot.

6. Change to init 3

#init 3

7. Install the NVIDIA driver

#sh NVIDIA-XXXXXX.run

8. Reboot your Ubuntu.

---

### Post by matt_symes on 2011-11-17
Hi

 > Change to init 3It means change the runlevel to runlevel 3. (multi-user text). This is the same as runlevel 2 in debian like systems. It's asking you to stop X and any window managers.

In your case just drop to a virtual terminal (ctrl + alt + f1), log in, and stop GDM (<=11.04) or LightDM (11.10). Then run the install command from the tutorial.

For 10.10...

```
sudo service gdm stop
```or

```
sudo /etc/init.d/gdm stop
```When the driver is installed, restart gdm by replacing the *stop *command above with *start* or reboot as suggested in the tutorial.

Kind regards

---

### Post by swarup on 2011-11-17
Thank you!

I dropped down to the virtual terminal, stopped GDM, and gave the command to install [sudo sh NVIDIA-Linux.x86...run]. It asked me to accept, which I did, and then give the following message:

```
The distribution-provided pre-install script failed! Continue installation anyway?
```

Should I go ahead and accept to install in this condition, or is it going to wreck something if I do?

ADD: I went ahead and accepted, and everything worked beautifully. Thank you for the beautiful guidance! :)

---

