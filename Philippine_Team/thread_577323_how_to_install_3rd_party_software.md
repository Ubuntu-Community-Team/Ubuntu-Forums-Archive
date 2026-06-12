---
title: "how to install 3rd party software"
date: 2007-10-16
forum: Philippine Team
---

### Post by jak0lyte on 2007-10-16
hi guys,

im new with ubuntu, im trying to install a RIP software for linux on ubuntu 7.04.
i cant install the program
it uses terminal command that im not familiar with
the installer is on the cd
can someone help give me step by step procedure to install the content
from the cd
i really need that software to be installed on ubuntu os

thanks
gener

---

### Post by jak0lyte on 2007-10-16
Installing the RIP
You must install into the default directory recommended by the installer, which is Fusion_72r0 of the home directory of the
user installing the RIP.
Pre-installation steps
If you have not already done so...
1. Insert the installation CD into your Linux system or download the Fusion RIP 7.2r0 for Linux ISO image file.
2. If you download the ISO image, you may uncompress it and write it to CDROM, or mount it directly using the
     “loop” device:

          gunzip Fusion_7.2r0_Linux.iso.gz

          mount -o loop Fusion_7.2r0_Linux.iso <mount/directory>
Installation steps
1. Open a Terminal window
2. In the Terminal window navigate to the top level of the CD-ROM or mounted disk image and enter the command:

       ./install-linux
This will launch the RIP installer interface.
3. In the Choose Package section, select “Fusion, 7.2r0”. In the Choose Product section, select “Fusion” if you
         have a hardware dongle and license for operating the RIP (please ensure that your hardware dongle is
         attached to a system USB port), or “Fusion (Wmark)” to evaluate the RIP. Click the Add button.
4. Sentinel Driver. If you are installing the fully licensed, dongle protected RIP, you will need to install the Senti-
         nel driver. In the Choose Package section, select “Drivers, 7.2r0”. In the Choose Product section, select
         the “Sentinel” driver. Without the Sentinel driver you will be unable to run the RIP. Click the Add button. You
         will NOT need to install the Sentinel Driver if you are installing the Watermark RIP.
                                                                                        Last Modified - March 20, 2007 7:08 AM
5. [Optional Step] Choose other products according to your needs and add them to the List of products to install.
6. Click the Install button.
Post-Installation steps
For fully-licensed, dongle-protected RIP installs only
1. In your Terminal window, become “root” and “cd” to the “sentinel” folder under the main RIP installation folder.
2. Invoke the sentinel installer shell script as follows:


       ./drvr-install.sh
3. The shell script will prompt you to make the choices appropriate for your system for the Rainbow Sentinel
        Dongle driver. The driver is installed into the /opt/RainbowTechnologies/SUD5.5/~ directory. A link to the
        startup script for the Rainbow daemon is placed into your /etc/rc.d/rc2.d directory.
4. When the install is complete, reboot your Linux system in order to install the dongle driver.


this is the steps provided by the manual
navigate to the top level of the CD-ROM or mounted disk image and enter the command: -dont know how to do this :-(

pls help

thanks

---

### Post by jak0lyte on 2007-10-16
1. Restart the system.
2. Before installing the new RIP you should ensure the HLS is not running.
   See Section 5.3 on page 15 for more information.
3. Mount the CD using:
   mount /mnt/cdrom
4. At the command prompt, type the following:
   export LANG=en_US
   export LC_ALL=en_US
5. Navigate to the top level of the CD-ROM (using cd /mnt/cdrom) and
   enter the command:
   ./install-linux


another install guide
not working
dont know whats wrong :confused:

---

### Post by loell on 2007-10-16
saan po ba makikita ang **RIP Software** na gusto nyong e-install?

i googled RIP software but its too common a word for a keyword.

---

