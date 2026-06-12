---
title: "Problem with video driver installation  (can't boot)"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by ubunbu on 2012-04-01
I followed the directions on this page

[http://askubuntu.com/questions/35273/installing-nvidia-drivers-from-website](http://askubuntu.com/questions/35273/installing-nvidia-drivers-from-website)

the last thing I did was this

```
sudo depmod -a 
sudo update-initramfs -u
```

In the recovery shell I cannot run the NVIDIAdriverdownload.run

I tried exec /home/user/NVIDIAdriver...run

It says permission denied , I tried su , sudo -i and sudo to give myself permissions but it didn't work. What do I do now?

---

### Post by bogan on 2012-04-02
Hi!, **ubunbu,**

You do not give any details of your installation or experience, so I have made this general.

To Install the nvidia driver all that is necessary is to CD to the folder where you have downloaded the .run file, make it executable and run it.
First, you should add some Blacklists to the /etc/modprobe.d folder, and then, as the nvidia driver  must only be installed when the GUI xorg server and screen is inactive,  reboot to a Text Terminal, or shut down the Xsession from a GUI screen,  

To do this check the /etc/modprobe.d folder for a file named blacklist.conf,
If it does not exist you will need to create one.

In the terminal enter:          ```
 gksu gedit /etc/modprobe.d/blacklist.conf
```then add:     

     ```
 # Added for nvidia driver. 
blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-173 
blacklist nvidia-96
``` And Save As:  /etc/modprobe.d/blacklist.conf.

Reboot, preferable to Restart, and either:
1. From a GUI screen Terminal:          ```
 sudo service lightdm stop    # 'gdm' in place of 'lightdm' if < 11.10
```OR:
2. From the Grub Menu, put cursor on the Ubuntu entry you intend as your primary usage and press 'e' to edit,
Go to the Linux boot line where it should have ' ro quiet splash' and add ' text'.
press Ctrl+x to boot.
At the prompt log in and enter password. [ It will not show anything, press 'enter' when complete.]
CD to where the nvidia file is and enter: dir
This will check you are in the right place and enable you to copy the exact name of the file you have downloaded, and substitute it in the following:
   ```
sudo chmod a+x NVIDIA-Linux-x86-290.10.run  # Check the exact spelling; 'x86' is for 32bit 
sudo sh NVIDIA-Linux-x86-290.10.run               # ditto
```Follow screen instructions.
 You may get a warning that nouveau is running and must be purged first, but carry on, that's what the blacklists are for.
When complete reboot.
nvidia-installer, nvidia-settings and nvidia-XServer-config will be  installed and you can adjust things to suit your hardware and wishes.

Good luck.

Chao!, **bogan.**

---

