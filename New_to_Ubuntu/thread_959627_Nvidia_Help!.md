---
title: "Nvidia Help!"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Kingsid3 on 2008-10-26
Hey, i'm trying to set up Dual screens with my Nvidia card, but when i go to terminal and type```
nvidia-settings
```

It opens it but give me the error

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

I ran
```
nvidia-xconfig
```

And then restarted x but its till the same error. Help?

Plus my screen it stuck in 800x600 when i change it it only give me that and 640x(somthing) and that it and it says my moniter is unknown

Help me!

---

### Post by scorchgeek on 2008-10-26
You need to run the command as root. Try
```
sudo nvidia-xconfig
```

instead.

---

### Post by Kingsid3 on 2008-10-26
Nope tried it it gives me this error.

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

---

### Post by Kingsid3 on 2008-10-27
Any other ideas?

---

### Post by taqkavar on 2008-10-27
I don't know the solution to your problem, but you can always try and reinstall the driver manually to see if it works. 

Go to [www.nvidia.com](www.nvidia.com)
download your driver
Press ALt+Ctrl+F2 and log in
sudo /etc/init.d/gdm stop
sudo sh <the name of the driver>
Say yes when it asks to modify the X setting using the driver.
finish the install
sudo reboot

now run:
sudo nvidia-settings

---

