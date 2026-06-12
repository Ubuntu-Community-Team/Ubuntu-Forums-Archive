---
title: "Cannot install nvidia driver"
date: 2011-08-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Dawnrazor on 2011-08-01
Hello

I am not able to install the prop. nvidia drivers

my steps

```
sudo apt-get install nvidia-current
```

then put following in the xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection
```

after reboot i get an black screen and nothing happens

is this a known problem?

the nouveau driver is not bad, but has massiv tearing in videos

---

### Post by sgage on 2011-08-01
After installing nvidia-current, run nvidia-xconfig to create the appropriate xorg.conf. That usually works for me.

If not, I have had success using jockey to uninstall the nvidia drivers, reboot, then use jockey again to install nvidia drivers.

---

### Post by dino99 on 2011-08-01
better to let the kernel doing its job itself and remove xorg.conf (dont add conflict with xconfig, kernel now directly deal with x)

---

### Post by Dawnrazor on 2011-08-01
ok thank you for your replies, i will test it this evenig

---

### Post by realzippy on 2011-08-01
> **dino99 said:**
> better to let the kernel doing its job itself and **remove xorg.conf** (dont add conflict with xconfig, kernel now directly deal with x)


..also when using nvidia-proprietary driver**?**

---

### Post by Harry33 on 2011-08-01
> **realzippy said:**
> ..also when using nvidia-proprietary driver**?**

No, xorg.conf is not necessary only if open source drivers are used.
Proprietary drivers. like nvidia-current and fglrx need xorg-conf.

And like Sgage said, you need to run nvidia-xconfig after the installation of nvidia-current.

```
sudo nvidia-xconfig
```

---

### Post by realzippy on 2011-08-01
@ Dawnrazor

please show output from:

```
lspci |grep VGA
```

---

### Post by Dawnrazor on 2011-08-01
```
dawn@dawn-pc:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT200b [GeForce GTX 275] (rev a1)
dawn@dawn-pc:~$ 

```

i tried all 

nothing worked

error in xorg

```
[    87.803] (EE) Failed to load module "nvidia" (module does not exist, 0)
```

---

### Post by lucazade on 2011-08-01
> **Dawnrazor said:**
> ```
dawn@dawn-pc:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT200b [GeForce GTX 275] (rev a1)
dawn@dawn-pc:~$ 

```

i tried all 

nothing worked

error in xorg

```
[    87.803] (EE) Failed to load module "nvidia" (module does not exist, 0)
```

try to rebuild the nvidia module:

sudo dpkg-reconfigure nvidia-current

---

### Post by zenarcher on 2011-08-01
I'm having the same problem here with Kubuntu 11.10.  I'm using a GeForce 210 PCI-e video card.

zenarcher

---

### Post by SevenMachines on 2011-08-01
> **Harry33 said:**
> Proprietary drivers. like nvidia-current and fglrx need xorg-conf.
Think this is no longer true and instead nvidia-current does something clever with alternatives (setting up the xorg driver and blacklisting nouveau etc). The only reason here for xorg.conf is to disable nvidia's logo.

---

### Post by sgage on 2011-08-01
> **SevenMachines said:**
> Think this is no longer true and instead nvidia-current does something clever with alternatives (setting up the xorg driver and blacklisting nouveau etc). The only reason here for xorg.conf is to disable nvidia's logo.

Wow, I think you might be right. I renamed xorg.conf, confirmed that nouveau was blacklisted, and sure enough - up came nvidia. It did take a long time though - I wonder what it was doing, and if it will take that long every time...

---

### Post by Harry33 on 2011-08-01
> **SevenMachines said:**
> Think this is no longer true and instead nvidia-current does something clever with alternatives (setting up the xorg driver and blacklisting nouveau etc). The only reason here for xorg.conf is to disable nvidia's logo.

Well what do you know. :P
You were right SevenMachines and Dino99.

I did remove xorg.conf and my setup boots just fine with nvidia-current.
So kernel must now see the nvidia dkms module.

---

### Post by realzippy on 2011-08-01
,,,then I guess kernel uses
/etc/X11/xorg.conf.d/20-nvidia.conf

---

### Post by SevenMachines on 2011-08-01
Some sort of alternatives update magic for a lot of handy things

/var/lib/dpkg/info/nvidia-current.postinst:
```
   update-alternatives --force \
            --install /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf x86_64-linux-gnu_gl_conf /usr/lib/nvidia-current/ld.so.conf 9700 \
            --slave /usr/share/man/man1/nvidia-xconfig.1.gz x86_64-linux-gnu_man_nvidiaxconfig.gz /usr/share/man/man1/alt-nvidia-current-xconfig.1.gz \
            --slave /usr/share/man/man1/nvidia-smi.1.gz x86_64-linux-gnu_nvidia-smi.1.gz /usr/share/man/man1/alt-nvidia-current-smi.1.gz \
            --slave /usr/share/applications/ubuntu-nvidia-settings.desktop x86_64-linux-gnu_nvidia_desktop /usr/share/nvidia-current/ubuntu-nvidia-settings.desktop \
            --slave /usr/bin/nvidia-smi x86_64-linux-gnu_nvidia_smi /usr/lib/nvidia-current/bin/nvidia-smi \
            --slave /usr/bin/nvidia-xconfig x86_64-linux-gnu_nvidia_xconfig /usr/lib/nvidia-current/bin/nvidia-xconfig \
            --slave /usr/bin/nvidia-bug-report.sh x86_64-linux-gnu_nvidia_bug_report /usr/lib/nvidia-current/bin/nvidia-bug-report.sh \
            --slave /usr/lib/XvMCConfig x86_64-linux-gnu_xvmcconfig /usr/lib/nvidia-current/XvMCConfig \
            --slave /etc/xdg/autostart/nvidia-autostart.desktop x86_64-linux-gnu_nvidia-autostart.desktop /usr/share/nvidia-current/nvidia-autostart.desktop \
            --slave /usr/lib/xorg/modules/drivers/nvidia_drv.so x86_64-linux-gnu_nvidia_drv /usr/lib/nvidia-current/xorg/nvidia_drv.so \
            --slave /etc/modprobe.d/nvidia-graphics-drivers.conf x86_64-linux-gnu_nvidia_modconf /lib/nvidia-current/modprobe.conf \
            --slave /usr/lib/xorg/extra-modules x86_64-linux-gnu_xorg_extra_modules /usr/lib/nvidia-current/xorg \
            --slave /usr/lib/vdpau/libvdpau_nvidia.so.1 x86_64-linux-gnu_libvdpau_nvidia.so.1 /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1 \
            --slave /usr/lib/libvdpau_nvidia.so x86_64-linux-gnu_libvdpau_nvidia.so /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so \
            --slave /usr/lib32/vdpau/libvdpau_nvidia.so.1 x86_64-linux-gnu_libvdpau_nvidia.so.1_lib32 /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 \
            --slave /usr/lib32/libvdpau_nvidia.so x86_64-linux-gnu_libvdpau_nvidia.so_lib32 /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so \
            --slave /usr/share/grub-gfxpayload-lists/blacklist/10_$PACKAGE_NAME x86_64-linux-gnu_grub_fb_blacklist /usr/share/nvidia-current/nvidia-current.grub-gfxpayload

```

I'm supposing good things happen in there with the extra modules, blacklisting, and the nvidia_drv stuff, i dont really know much of the alternatives system though.

---

### Post by Dawnrazor on 2011-08-02
> **sgage said:**
> Wow, I think you might be right. I renamed xorg.conf, confirmed that nouveau was blacklisted, and sure enough - up came nvidia. It did take a long time though - I wonder what it was doing, and if it will take that long every time...

mmmh where do you confirm blacklisting nouveau?

when i delete the xorg.conf the nouveau driver loads

---

### Post by Harry33 on 2011-08-02
> **Dawnrazor said:**
> mmmh where do you confirm blacklisting nouveau?

when i delete the xorg.conf the nouveau driver loads

Installing nvidia-current should blacklist nouveau automatically.
It creates the file /etc/modprobe.d/nvidia-graphics-drivers.conf with the following lines:

Code:
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

---

### Post by Dawnrazor on 2011-08-02
Ok i will check this file this evening and will tell you

---

### Post by zenarcher on 2011-08-02
I seem to have all that, including the blacklisting and the Nvidia driver installed, but still I cannot activate it.  Instead, the Nouveau driver keeps loading.

zenarcher

---

### Post by sgage on 2011-08-02
> **zenarcher said:**
> I seem to have all that, including the blacklisting and the Nvidia driver installed, but still I cannot activate it.  Instead, the Nouveau driver keeps loading.

zenarcher

What does jockey tell you? Does it say "nvidia-current installed but not activated"? If it does, I'd try using jockey to remove it, reboot, and use jockey to reinstall it.

---

### Post by mc4man on 2011-08-02
> **zenarcher said:**
> I seem to have all that, including the blacklisting and the Nvidia driver installed, but still I cannot activate it.  Instead, the Nouveau driver keeps loading.

zenarcher
Is jockey saying what's in screen?
If so I wouldn't believe what it says - run glxinfo and look at lines 3 and 4 - 
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

or run nvidia-settings and see what it says (while you're there, if good, then  click on "nvidia-settings Configuration" and 'Save Current Configuration'  - to the default of ~/.nvidia-settings-rc
(always a good thing to do

I don't think jockey has shown nvidia as 'currently in use' for close to a year here and probably never will again..

---

### Post by zenarcher on 2011-08-02
> **sgage said:**
> What does jockey tell you? Does it say "nvidia-current installed but not activated"? If it does, I'd try using jockey to remove it, reboot, and use jockey to reinstall it.

I tried that and when I rebooted, I ended up with a flashing cursor and black screen...nothing else.  

zenarcher

---

### Post by zenarcher on 2011-08-02
> **mc4man said:**
> Is jockey saying what's in screen?
If so I wouldn't believe what it says - run glxinfo and look at lines 3 and 4 - 
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

or run nvidia-settings and see what it says (while you're there, if good, then  click on "nvidia-settings Configuration" and 'Save Current Configuration'  - to the default of ~/.nvidia-settings-rc
(always a good thing to do

I don't think jockey has shown nvidia as 'currently in use' for close to a year here and probably never will again..

I ran GLXinfo and got this:

Xlib: Extension "GLX" missing on Display ":0"  
Error: Couldn't find RGB GLX visual or fbconfig

When I ran nvidia-settings, I got this:

Gtk Message: Failed to load module "canberra-gtk-module"

Also, Error Message: You do not appear to be using the Nvidia X configuration file (just run nvidia-xconfig as root) and restart the X server.

I did that, but nothing different.  Same situation.

zenarcher

---

### Post by Dawnrazor on 2011-08-02
> **zenarcher said:**
> I tried that and when I rebooted, I ended up with a flashing cursor and black screen...nothing else.  

zenarcher

yes that was my problem, too but today after an update

it works :popcorn:

---

### Post by zenarcher on 2011-08-03
> **Dawnrazor said:**
> yes that was my problem, too but today after an update

it works :popcorn:

Well, I tried that again, rebooted and now I'm back to the black screen with the flashing cursor.  I think I'll just wait until tomorrow when the new Alpha release comes out, download and burn that and try a fresh install again.  I'll see where I can go from there.

Thanks for the help and I'll post what I get with a fresh install.

zenarcher

---

### Post by zenarcher on 2011-08-03
It's probably not the right way, but I have the Nvidia driver working now.  Did a fresh install with the Kubuntu Daily Build for today and still couldn't get it to work right.  

So, I went into Recovery mode, removed and reinstalled the Nvidia driver, as jockey wouldn't let me do so.  I then ran nvidia-xconfig as root, then went in and deleted xorg.config.  After doing all of this, rebooted and the Nvidia driver is now working properly.

zenarcher

---

### Post by Royke on 2011-09-06
What if even recovery-mode turns black:confused: Luckily i still have UbuntuStudio10.04:guitar:

---

### Post by Harry33 on 2011-09-07
> **Royke said:**
> What if even recovery-mode turns black:confused: Luckily i still have UbuntuStudio10.04:guitar:

Recovery mode with the option "Drop to shell with networking" is always kinda black, only a text console. :guitar:

---

### Post by umbertoz on 2011-09-07
You should put them into blacklist.conf and do update-initramfs.

---

