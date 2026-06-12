---
title: "Gnome Shell Themes Isn't Working"
date: 2015-10-17
forum: New to Ubuntu
---

### Post by Quipso on 2015-10-17
Hello Ubuntu Users!

I've been trying to download a theme for my Ubuntu computer (version 14.04)
(If any of you need the theme, here it is: /home/user/themes/Windows 10 Default | [http://gnome-look.org/content/show.php/Windows+10+Theme?content=171327](http://gnome-look.org/content/show.php/Windows+10+Theme?content=171327))

Here is what happens when I try and download "Gnome-Shell":

    user@system-a0d0b9:~$ sudo apt-get install gnome-shell    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    gnome-shell is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 318 not upgraded.
    1 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Do you want to continue? [Y/n] Y
    Setting up plymouth-theme-ubuntu-gnome-logo (14.04.1) ...
    update-initramfs: deferring update (trigger activated)
    /usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.
    dpkg: error processing package plymouth-theme-ubuntu-gnome-logo (--configure):
    subprocess installed post-installation script returned error exit status 1
    Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
    update-initramfs: Generating /boot/initrd.img-3.16.0-38-generic
    103958 blocks
    scripts/init-bottom/scan-user
    scripts/init-bottom/aufs-init
    scripts/factory-restore
    Errors were encountered while processing:
    plymouth-theme-ubuntu-gnome-logo
    E: Sub-process /usr/bin/dpkg returned an error code (1)

This is what happens when I download "gnome-tweak-tool":

    user@system-a0d0b9:~$ sudo apt-get install gnome-tweak-tool
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    gnome-tweak-tool is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 318 not upgraded.
    1 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Do you want to continue? [Y/n] Y
    Setting up plymouth-theme-ubuntu-gnome-logo (14.04.1) ...
    update-initramfs: deferring update (trigger activated)
    /usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.
    dpkg: error processing package plymouth-theme-ubuntu-gnome-logo (--configure):
    subprocess installed post-installation script returned error exit status 1
    Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
    update-initramfs: Generating /boot/initrd.img-3.16.0-38-generic
    103958 blocks
    scripts/init-bottom/scan-user
    scripts/init-bottom/aufs-init
    scripts/factory-restore
    Errors were encountered while processing:
    plymouth-theme-ubuntu-gnome-logo
    E: Sub-process /usr/bin/dpkg returned an error code (1)

Finally, this is what happens when I download "gnome-shell-extensions":

 
    user@system-a0d0b9:~$ sudo apt-get install gnome-shell-extensions
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    gnome-shell-extensions is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 318 not upgraded.
    1 not fully installed or removed.
    After this operation, 0 B of additional disk space will be used.
    Do you want to continue? [Y/n] Y
    Setting up plymouth-theme-ubuntu-gnome-logo (14.04.1) ...
    update-initramfs: deferring update (trigger activated)
   /usr/sbin/grub-probe: error: failed to get canonical path of `aufs'.
    dpkg: error processing package plymouth-theme-ubuntu-gnome-logo (--configure):
    subprocess installed post-installation script returned error exit status 1
    Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
    update-initramfs: Generating /boot/initrd.img-3.16.0-38-generic
    103958 blocks
    scripts/init-bottom/scan-user
    scripts/init-bottom/aufs-init
    scripts/factory-restore
    Errors were encountered while processing:
    plymouth-theme-ubuntu-gnome-logo
    E: Sub-process /usr/bin/dpkg returned an error code (1)

At the time, I was oblivious to the fact that none of what I attempted to install, installed. So I decided to open the "gnome-tweak-tool." This is the outcome:

    user@system-a0d0b9:~$ gnome-tweak-tool
    WARNING : Shell not installed or running
    WARNING : Shell not running
    None
    WARNING : Error detecting shell
    Traceback (most recent call last):
    File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 284, in __init__
    raise Exception("Shell not running or DBus service not available")
    Exception: Shell not running or DBus service not available


    (gnome-tweak-tool:22965): Gtk-WARNING **: Theme file for default has no name




    (gnome-tweak-tool:22965): Gtk-WARNING **: Theme file for default has no directories


    INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)

Does anyone have this problem and or know how to fix it? I really want to download this theme. My current theme is very bland. Thanks!

---

### Post by buzzingrobot on 2015-10-17
Are you running Unity or Ubuntu Gnome?  Each of the three packages you attempted to install are already installed on your system.  That's what the "<something> is already the newest version" line is saying.

(This:
> ser@system-a0d0b9:~$ gnome-tweak-tool
    WARNING : Shell not installed or running

...indicates you are not using Gnome Shell.]

If you have installed Gnome Shell on a Unity system, you need to switch to it when you log in. Click the small icon at the login prompt and it should display a list of the other interfaces installed on the system. 

I can't account for the error that shows up in all three instances. Do you see any other errors in use, especially when you boot and log in?

The theme's page on gnome-look.org indicates it is compatible with a range of environments, including Unity as well as Gnome Shell 3.16.  The page is less than clear about other requirements, but Gnome Shell 3.16 is a newer release I believe is not available for 14.04.  

Specifically, what is not clear is if this theme will work on Unity on 14.04 or on the version of Gnome Shell used in 14.04.  If it requires 3.16, then it is not compatible.

If it is compatible with Unity on 14.04 and you want to use it on Unity, you do not need those 3 Gnome packages. you can install the Unity Tweak Tool package to enable changing themes in Unity.  

I don't see any installation instructions on the page, but you should expand the zip archive and copy the theme's folder to either /usr/share/themes or to a '.themes' folder in your home directory (create it if it does not exist).

---

### Post by claracc on 2015-10-17
I think that to install gnome shell 3.16 you need to have at least ubuntu 15.04.

It seems that in ubuntu 14.04 the more you can install is gnome shell 3.14 but through ppas since the current gnome shell is 3.10

---

### Post by Frogs Hair on 2015-10-21
15.10 including Gnome 3.16 will be released on 10/22. If you install the Gnome Shell on your Ubuntu installation the session needs selected at login if it was installed successfully. From 15.10 you could upgrade 16.04 LTS in the spring. You might also consider installing Ubuntu Gnome if you prefer Gnome to Unity.

---

