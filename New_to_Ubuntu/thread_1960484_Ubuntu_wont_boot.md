---
title: "Ubuntu wont boot"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2012-04-17
Hey,

my Ubuntu does not boot anymore... :(. Here is what happens:

While booting i start Ubuntu (it says "Ubuntu with Linux 3.0.0-16 generic-pae" in the bootloader). After that the screen turns purple without the Ubuntu Logo. After a short time (longer as usual) the Ubuntu Logo with the 5 dots appears but the dots are not ticking! Until than nothing happens doesnt matter how long i wait.

The strange thing is, that if i press the Power Button Ubuntu shuts down as usual. I see the ubuntu logo with the ticking dots and than the system shuts down.

I did not run any updates as far as i know (I did not use apt-get or update-manager).

*I dont think that this is relevant but the last time my computer worked i did save the configuration file (Nvidia software for my graphics card) for my monitors settings. (Xconf i think). Could it be that it has overwritten some stuff?*

I dont have network access here.

Does someone know how to fix this problem? 

Ah, and my Ubuntu version is the actual stable Version 10.10 ?!?!?

Thank you

---

### Post by ubudog on 2012-04-17
Hi there, could you boot into recovery mode (from the bootloader), and select 'Drop to root shell'?

As you mentioned you modified your X settings, could you post the output of: 
```
ls /etc/X11
```

And: 
```
cat /etc/X11/xorg.conf
```

Best wishes,
ubudog

---

### Post by Krabby.Linux on 2012-04-17
The Output is too long it would take me an hour to type it here ^^. I could save it to my USB Stick. How can i mount my USB Stick? And were do i find it ? Media ?

EDIT: The USBdrive does not show up if i type in terminal "df"

Thanks for your help!

---

### Post by ubudog on 2012-04-17
Yep, if you plug in your USB stick you can find it mounted in /media/nameofdrive

You could print the output of the command to a file on your USB stick, like so: 
```
echo `cat /etc/X11/xorg.conf` >> /media/nameofyourdrive/catout.txt
```
(that should work, there is probably a better way)

---

### Post by Krabby.Linux on 2012-04-17
I had to mount it manually but it worked after a looong time :-).

I cant upload the file here so you can take a look at it here: [http://dl.dropbox.com/u/13200114/xorg.conf](http://dl.dropbox.com/u/13200114/xorg.conf)

While i used your command to copy into an .txt file the file he created was always empty so i had to copy the .conf file.

Thanks

---

### Post by ubudog on 2012-04-17
Weird.

Whenever it stalls, on start, press the Escape key.  If possible, could you take a picture of the screen and upload that here?  

It should show the error it's getting there.

---

### Post by Krabby.Linux on 2012-04-18
Somewhere it says : Stopping automatic crash report generation [fail]


Than there are lots of [OK]. The system stalls at:

Checking Battery state [OK]

Thanks

---

### Post by bogan on 2012-04-18
Hi!, **KrabbyLinux**,

You Posted:>  my Ubuntu version is the actual stable Version 10.10 ?!?!?
 [But also:]
 (it says "Ubuntu with Linux 3.0.0-16 generic-pae" in the bootloader). 3.0.0-16 is actually 11.10.

 ```
uname -r 
```will tell you which version is running.

" Stopping automatic crash report generation [fail]" is normal & and can be ignored.

Hanging at:" Checking Battery state [OK] " is usually an indicator of video driver problems.
 Please Post output from ```
lspci -nnv | grep VGA
```Chao!, **bogan**.

---

### Post by Krabby.Linux on 2012-04-18
Hey,

Output from: 
```
lspci -nnv | grep VGA
```


```
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400M GS] [10de:0427] (rev a1) (prog-if 00 [VGA controller])
```

How can i deactivate the Nvidia drivers and activate the standard Drivers with the terminal? Might this solve the problem?

Thanks

---

### Post by Krabby.Linux on 2012-04-20
Does noone have any ideas ? I need my System and the files :(.

If I download the new Ubuntu Version ( Beta) on a CD. Can i start from the CD and install the new System as an upgrade so that all my files and programs are still on my disk?

If i manage to get internet access with my notebook, how can i upgrade to the newest Ubuntu (beta). I only know the command "update-manager-d" but i cant use update-manager with the terminal.

Thanks

---

### Post by bogan on 2012-04-20
Hi!, KrabbyLinux,

You Posted:>  How can i deactivate the Nvidia drivers and activate the standard Drivers with the terminal? Might this solve the problem?It might, but it may be even worse.
The following will do the first and reinstall the chosen version. Alternatively, stop at the blue high-lighted line and reboot, type "add" in the Dash and run 'Additional Hardware' if the default drivers do not work satisfactorily. This will install the nvidia-current driver, but may also offer another choice as well.

Take your pick.

To Install a nvidia driver  from the NVIDIA Downloads site, it is necessary  to CD to the  folder where you have downloaded the .run file, make it executable and  run it.
First, you should add some Blacklists to the /etc/modprobe.d folder, and then remove any previous drivers.
 As the nvidia driver  must only be installed when the GUI Xorg  server and screen is inactive,  reboot to a Text Terminal, or shut down  the Xsession from a GUI screen,  

To do this check the /etc/modprobe.d folder for a file named blacklist.conf,
If it does not exist you will need to create one.

In the terminal enter: 
      ```
gksu gedit /etc/modprobe.d/blacklist.conf 
```then add:     
```
# Added for nvidia driver.
blacklist vga16fb 
blacklist rivafb  blacklist rivatv
blacklist nouveau 
blacklist lbm-nouveau
blacklist nvidiafb  
blacklist nvidia-173
blacklist nvidia-96 
``` And Save As:'  /etc/modprobe.d/blacklist.conf.'

Reboot, preferable to Restart, and either:
1. From a GUI screen Terminal: 
      ```
sudo service lightdm stop    # 'gdm' in place of 'lightdm' if < 11.10 
```OR:
2. From the Grub Menu, put cursor on the Ubuntu entry you intend as your primary usage and press 'e' to edit,
Go to the Linux boot or default line, where it should have ' ro quiet splash' and add ' text'.
press Ctrl+x to boot.
At the prompt log in and enter password. [ It will not show anything, press 'enter' when complete.]

[COLOR=Teal]**To remove redundant or faulty remnants of previous installations:**[/COLOR]
```
uname -r
sudo apt-get update 
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
sudo apt-get install linux-headers-'uname -r' # substitute output of 'uname -r' here. 
sudo nvidia-installer --uninstall 
sudo apt-get remove --purge nvidia-*
```[COLOR=Blue]At this point choose whether to use 'Additional ' or a downloaded .run file, if the later continue as below, otherwise reboot.[/COLOR]

CD to where the nvidia file is and enter: 'dir'.
This will check you are in the right place and enable you to copy the  exact name of the file you have downloaded, and substitute it in the  following:
        ```
cd /home/username/Downloads
dir
sudo chmod a+x NVIDIA-Linux-x86-290.10.run  # Check the exact spelling; 'x86' is for 32bit  
sudo sh NVIDIA-Linux-x86-290.10.run               # ditto 
```Follow screen instructions.
 You may get a warning that nouveau is running and must be purged first, but carry on, that's what the blacklists are for.
When complete reboot.
nvidia-installer, nvidia-settings and nvidia-XServer-config will be   installed and you can adjust things to suit your hardware and wishes.

Chao!,** bogan**.

---

### Post by Krabby.Linux on 2012-04-20
This will probably take a whole day for me. I dont understand how all of it works ( how to uninstall drivers for example) Took me 3 hours even to mount my USBdrive.

I will try it. If I have some time at sunday. You didnt mention the upgrade thing. I am not able to upgrade my system with the terminal (offline)?

---

### Post by bogan on 2012-04-20
> **Krabby.Linux said:**
> Does noone have any ideas ? I need my System and the files :(.

If I download the new Ubuntu Version ( Beta) on a CD. Can i start from the CD and install the new System as an upgrade so that all my files and programs are still on my disk?

If i manage to get internet access with my notebook, how can i upgrade to the newest Ubuntu (beta). I only know the command "update-manager-d" but i cant use update-manager with the terminal.
.......You didnt mention the upgrade thing. I am not able to upgrade my system with the terminal (offline)?     
ThanksI thought I was giving you enough to keep you busy as it was!!

Prefix to all that follows with "AFAIK" !!

It is [will be] possible to do an Upgrade to 12.04 with Update Manager from 11.04, and, presumably, from 11.10, **once 12.04 is released**, but you did not confirm which version you have at present. 
I would not advise you to upgrade to 12.04(Beta), the first 'stable' version is only a few days away.

EDIT 2:[COLOR=SeaGreen][COLOR=DarkRed] I see from Update Manager that 12.04LTS is now available as an upgrade, so the above para is partly out-of-date.[/COLOR]
[COLOR=Black]Even then, if yo[/COLOR][/COLOR]u have disk space, it would be better to do a clean install, to another partition, preferably to different HDD.

Edit 3: Evidently, that was an Update Manager misstook:  Release is not yet [23 April].

Also, I would advise running it from a downloaded .iso to a CD or USB and try it out with your hardware before installing it. That can be done 'offline' provided you have internet access on another computer, or if you have a dual-boot and can use Windows to make the LiveCD/USB.

"update-manager-d" or "update-manager-c" will tell you what updates or upgrades are available, but Update Manager itself needs a graphical environment.

Certainly it is possible to do such things from a text terminal without a graphical interface being available, but that is beyond my competence to explain in detail. The only time I tried was a dismal and complete disaster !!

Chao!, **bogan**.

---

### Post by bogan on 2012-05-04
Hi!,** All,**  There is a new driver, 295.49 available from nvidia downloads
 [http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html)

 Noon Friday May 4th; ```
nvidia-installer --latest 
``` now   returns: v295.49 and     ```
nvidia-installer -f 
``` will install   295.49 after un-installing the previous version.

 NVNews says of version295.49:> **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**
Chao!, **bogan**

---

