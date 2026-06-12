---
title: "[SOLVED] VirtualBox &amp;amp; USB devices"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by kestrel1 on 2008-05-10
I run VirtualBox & have eventually got it to recognize my USB webcam. I have been trying to get it to recognize my USB pen drive & USB hard drive, but have had no luck. I have added the devices to the USB list in VirtualBox, but when I run WinXP as a virtual machine it sees my webcam but not the other devices. If I unplug a device (USB pen drive) I get the normal Windows USB unplugged sound & if I plug it in I get the plugged sound (If you know what I mean), but the device will not show up in My Computer or in Disk Management. 
Any ideas on what I need to do?
Cheers
K

---

### Post by TenPlus1 on 2008-05-10
Each time I install VirtualBox, I use this little guide to set it up:

Once VirtualBox is installed, run this command to add vb into the user privelages:

sudo usermod -G vboxusers -a <username>


Check USB Support:

add the group:
sudo groupadd vboxusers


add usb support:
sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers


gksu gedit /etc/udev/rules.d/40-permissions.rules


USB devices, add lines to end of file:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"


sudo gedit /etc/fstab

add this line after other volumes:
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0


When running Windows or whatever Os, use the VirtualBox screen menu and install guest additions so you can access seamless mode...

This will let you share files between Ubuntu and XP (or whatever), use Net use x: \\vboxsvr\<user> to map drive letter to shared files.

---

### Post by kestrel1 on 2008-05-10
I had done all of the above, but USB drives do not show up. Should they? or do I need to share them & use the Net use command?

---

### Post by kestrel1 on 2008-05-10
I used the Net use command after sharing the drive, but the USB drive does not show any files (yes there are some on there) Fixed drive comes up OK.

---

