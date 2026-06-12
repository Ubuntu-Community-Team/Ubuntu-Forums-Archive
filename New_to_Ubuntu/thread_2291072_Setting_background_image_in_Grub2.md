---
title: "Setting background image in Grub2"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by Samyak_Raj_Pasala on 2015-08-17
I'm a noob to Ubuntu. I intend to change the background image of the Bootloader. After an extensive search, I found that we had to edit the configuration in /etc/default/grub. How do I get to that directory? Using `gksu gedit`? Brownie points for explaining alternate methods too

---

### Post by Bucky Ball on 2015-08-17
Welcome. Unless you're specifically wanting to learn how to do this using the terminal, [Grub Customizer]("https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer") could be your friend. :)

[Here's]("http://ubuntuforums.org/showthread.php?t=1664134") how. I think you can also use Ubuntu Tweak.

---

### Post by deadflowr on 2015-08-17
Alternative:
```
sudo cp /path/to/image /boot/grub/
```
change the /path/to/image to the path to where the image is (ie /home/you/Pictures/imagefile.png)
then run
```
sudo update-grub
```
the output should show an entry for background.
Then reboot and see.

---

### Post by grahammechanical on 2015-08-17
The Ubuntu Software Centre has a selection of images designed especially to be used as Grub background images. Search for grub2-splashimages. They will install into /usr/share/images/grub/. Copy an image to /boot/grub/ and run this command

```
sudo update-grub
```

We do not need to edit any grub configuration files. All we need to do is put a suitable image in /boot/grub/ and run that command and any editing is done for us. To copy the file you will need to open the file manager with administrator privileges as /boot is a system folder.

```
sudo -H nautilus
```

And browse to the relevant folders. Or us Grub Customizer. It will do it for us.

Regards.

---

