---
title: "'Could not create destination path...' while install"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by alkopop79 on 2012-02-05
Hi,

I'm trying to install Xilinx's Webpack on 32-bit Ubuntu. I have downloaded the image, untarred it and ran a file called xsetup that started the installation manager. When clicking on 'Install' I got this message:

Could not create destination path "/opt/Xilinx/13.4/ISE_DS"

The very same path was set as the destination folder by default. Is it possible that I need permission of some sort for creating the folders? Any ideas would be appreciated!

[IMG]http://i125.photobucket.com/albums/p66/alkopop79/scrnsht2.png[/IMG]

---

### Post by yetiman64 on 2012-02-05
Did you run the xsetup installer as root (with "sudo"before the command - actually from the screenshot I would recommend the use of gksudo rather than sudo - the installer is a graphical application.) ?

The location in /opt is owned by root and if you didn't run the installer with root privileges by using sudo before the installer command the address in /opt cannot be created or altered.

Note: this is general commentary, I am not specifically familiar with that installer.

---

### Post by alkopop79 on 2012-02-05
It worked! Thank you very much!

---

### Post by alkopop79 on 2012-02-05
Cram, it didn't work. The installation starts but I got a similar error:  You may not have write permissions for the /opt/Xilinx/13.4/ISE_DS/PlanAhead directory or its subdirectory. "Error was encountered while extracting archive /home/alkopop79/Documents/Xilinx/Xilinx_ISE_DS_Lin_13.4_O.87xd.3.0/idata/planahead_0009.zip.xz" Please correct this and then select Retry  When I select retry, it appears again and I have to cancel the installation. ANy ideas how to proceed from here?

---

### Post by alkopop79 on 2012-02-05
Cram, it didn't work. The installation starts but I got a similar error:  You may not have write permissions for the /opt/Xilinx/13.4/ISE_DS/PlanAhead directory or its subdirectory. &quot;Error was encountered while extracting archive /home/alkopop79/Documents/Xilinx/Xilinx_ISE_DS_Lin_13.4_O.87xd.3.0/idata/planahead_0009.zip.xz&quot; Please correct this and then select Retry  When I select retry, it appears again and I have to cancel the installation. ANy ideas how to proceed from here?

---

### Post by alkopop79 on 2012-02-05
Please help... I've been struggling with this matter for days. I want to sleep...

---

