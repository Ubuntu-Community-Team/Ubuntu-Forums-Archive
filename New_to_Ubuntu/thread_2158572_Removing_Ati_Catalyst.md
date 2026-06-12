---
title: "Removing Ati Catalyst"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by Noaner on 2013-06-29
Hy everybody i hope someone could help me.
I installed the ati Catalyst Driver amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run at ubuntu 13.04 and now the guy (Unity) isnt working anymore.
I hope someone could help to remove the driver.

---

### Post by Noaner on 2013-06-29
[COLOR=#000000]I have tried already this but but i couldn't find any of the fglrx packages[/COLOR]


[COLOR=#000000]Anyway, boot Ubuntu in recovery mode, drop to terminal, login to root, and type in "aptitude." This will give you a text-based package manager like the Synaptic GUI. From here, the offending ATI packages can be found and removed from under Misc. Press ? for help. This should ultimately get you back; it did me anyway after days of guessing. Reply with any questions.[/COLOR]

---

### Post by Bashing-om on 2013-06-29
Noaner; Hi !

What driver were you using prior to the attempted change ?
Why did you think you needed a different driver other than what you had installed ?
What driver do you think you need to (re-)install ?

To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

Best to have an idea of what to install before removing the present driver... huh ?

[INDENT][INDENT]just try'n to help[/INDENT][/INDENT]

---

### Post by Noaner on 2013-06-29
> **Bashing-om said:**
> Noaner; Hi !

What driver were you using prior to the attempted change ?
Why did you think you needed a different driver other than what you had installed ?
What driver do you think you need to (re-)install ?

To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

Best to have an idea of what to install before removing the present driver... huh ?[INDENT][INDENT]just try'n to help[/INDENT]
[/INDENT]


Hi thanks for the reply.

```

root@markus-VPCEE3S1E:~# sudo lshw -C display
PCI (sysfs)  
  *-display               
       Beschreibung: VGA compatible controller
       Produkt: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
       Hersteller: Advanced Micro Devices [AMD] nee ATI
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: 00
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm pciexpress msi vga_controller bus_master cap_list rom
       Konfiguration: driver=radeon latency=0
       Ressourcen: irq:45 memory:e0000000-efffffff ioport:a000(Größe=256) memory:f4100000-f410ffff memory:f4120000-f413ffff
root@markus-VPCEE3S1E:~# lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV710/M92 [Mobility Radeon HD 4530/4570/545v] [1002:9553]
    Subsystem: Sony Corporation Device [104d:9077]
    Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
root@markus-VPCEE3S1E:~#  sudo lshw -C display
  *-display               
       Beschreibung: VGA compatible controller
       Produkt: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
       Hersteller: Advanced Micro Devices [AMD] nee ATI
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: 00
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm pciexpress msi vga_controller bus_master cap_list rom
       Konfiguration: driver=radeon latency=0
       Ressourcen: irq:45 memory:e0000000-efffffff ioport:a000(Größe=256) memory:f4100000-f410ffff memory:f4120000-f413ffff


```

Now i have installed gnome at least this is working i wouldnt try to install it agayn. I will be happy if i dont have to reinstall the whole system.

---

### Post by Noaner on 2013-06-29
I was using the amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64 driver.
Maybe someone has an idea how to get Unity working agayn?

---

### Post by sandyd on 2013-06-29
> **Noaner said:**
> Hy everybody i hope someone could help me.
I installed the ati Catalyst Driver amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run at ubuntu 13.04 and now the guy (Unity) isnt working anymore.
I hope someone could help to remove the driver.

If you installed the driver from the ati site, you can remove it by running the following
```

sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

```

Mainly, its safer to install the drivers from the hardware drivers utility.

---

### Post by Bashing-om on 2013-06-29
Noaner;

Here's the deal:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.(Mark Phelps)
so the only driver you can run is the open source driver: -> which performs admirably.
As you installed using a package from AMD/ATI's website; Try This:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --uninstall
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u  ## this to create a new image 

``` 
Then reboot your system and when it comes up it will be should be running with nouveau (open source).

This is but one option ... sandyd's directive could be equally effective.

[INDENT][INDENT]what works, works[/INDENT][/INDENT]

---

### Post by Noaner on 2013-06-29
> **Bashing-om said:**
> Noaner;

Here's the deal:

so the only driver you can run is the open source driver: -> which performs admirably.
As you installed using a package from AMD/ATI's website; Try This:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --uninstall
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u  ## this to create a new image 

``` 
Then reboot your system and when it comes up it will be should be running with nouveau (open source).

This is but one option ... sandyd's directive could be equally effective.
[INDENT][INDENT]what works, works[/INDENT]
[/INDENT]


But the driver worked whit 12.04

---

### Post by ajgreeny on 2013-06-29
But I think all the Mobility Radeon HD 4530/4570 series of radeon cards are no longer supported by ATI's fglrx proprietary driver so you will have to use the open-source driver that you had immediately after installing the OS

---

### Post by Noaner on 2013-06-29
> **ajgreeny said:**
> But I think all the Mobility Radeon HD 4530/4570 series of radeon cards are no longer supported by ATI's fglrx proprietary driver so you will have to use the open-source driver that you had immediately after installing the OS

I have installed now the open-source driver, but unity is still not working  i can se only the wallpaper and work via ctrl+alt+t whit the terminal :confused: (im running gnome).

---

### Post by Noaner on 2013-06-29
Is it possible to everything how it was before or do i have to reinstall the whole os?

---

### Post by deadflowr on 2013-06-29
> **Noaner said:**
> But the driver worked whit 12.04

If I remember, only for 12.04.1, as the xorg/mesa/whatever were upgraded for 12.04.2.

---

### Post by Noaner on 2013-06-29
> **deadflowr said:**
> If I remember, only for 12.04.1, as the xorg/mesa/whatever were upgraded for 12.04.2.

Ok but now what could i do to ghet everthing working like before?

---

### Post by deadflowr on 2013-06-29
Did you follow the commands Bashing-Om listed?

---

### Post by ajgreeny on 2013-06-29
I don't think there is anything you can do.  You may have to acept a different DE for that hardware, eg xfce (xubuntu)

---

### Post by Noaner on 2013-06-29
> **ajgreeny said:**
> I don't think there is anything you can do.  You may have to acept a different DE for that hardware, eg xfce (xubuntu)

Ok so i accept that i could use only the preinstalled version i wish i could reinstall this version in order that unitz wil work again.

---

### Post by Bashing-om on 2013-06-29
Noaner; 

That now may not be so direct or simple to do ... Let's see what happens.
We do not know the state of the gnome-desktop that you installed, nor do I know the effect on the dependcies if and when gnome desktop were to be removed. For now, let's leave it and see if we can restore unity.

In Ubuntu 12.04 resetting the Ubuntu desktop required the running of one command:unity --reset . This was retired in Ubuntu 12.10.

To get your Unity desktop settings back to brand spankin’ new behaviour in 12.10 and 13.04 we need to do a few things…

Step 1
Unity, and Compiz, the window manager that powers Unity, stores its settings in a configuration system called ‘dconf‘.

This isn’t a standard bit of software to play with, so proceed with caution.

Install dconf-tools: -> Terminal commands:
```

sudo apt-get install dconf-tools
```
Next run this terminal command to reset compiz:
```
dconf reset -f /org/compiz/
```

Log out of your desktop session and back into Unity for changes to take effect.

Step 2
To refresh your Unity launcher with the default set of icons, run the following in a Terminal:
```

unity --reset-icons
```
This command will “restart” Unity immediately, running from the Terminal. Closing the Terminal will also ‘close’ Unity, so it’s best to log out and back in after running this command.
Terminal command:
```
sudo shutdown -r now
```
My source:
[http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)

[INDENT][INDENT]worth a shot[/INDENT][/INDENT]

---

### Post by Noaner on 2013-06-29
> **Bashing-om said:**
> Noaner; 

That now may not be so direct or simple to do ... Let's see what happens.
We do not know the state of the gnome-desktop that you installed, nor do I know the effect on the dependcies if and when gnome desktop were to be removed. For now, let's leave it and see if we can restore unity.

In Ubuntu 12.04 resetting the Ubuntu desktop required the running of one command:unity --reset . This was retired in Ubuntu 12.10.

To get your Unity desktop settings back to brand spankin’ new behaviour in 12.10 and 13.04 we need to do a few things…

Step 1
Unity, and Compiz, the window manager that powers Unity, stores its settings in a configuration system called ‘dconf‘.

This isn’t a standard bit of software to play with, so proceed with caution.

Install dconf-tools: -> Terminal commands:
```

sudo apt-get install dconf-tools
```
Next run this terminal command to reset compiz:
```
dconf reset -f /org/compiz/
```

Log out of your desktop session and back into Unity for changes to take effect.

Step 2
To refresh your Unity launcher with the default set of icons, run the following in a Terminal:
```

unity --reset-icons
```
This command will “restart” Unity immediately, running from the Terminal. Closing the Terminal will also ‘close’ Unity, so it’s best to log out and back in after running this command.
Terminal command:
```
sudo shutdown -r now
```
My source:
[http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)
[INDENT][INDENT]worth a shot[/INDENT]
[/INDENT]


Thank you now it is working again :KS

---

### Post by Bashing-om on 2013-06-29
Noaner; Hey !

Outstanding.... you do good work.

Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT]come back and we will read you next time;
[INDENT][INDENT][INDENT][INDENT][INDENT]cheers[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-06-30
> **Noaner said:**
> But the driver worked whit 12.04

That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.

---

