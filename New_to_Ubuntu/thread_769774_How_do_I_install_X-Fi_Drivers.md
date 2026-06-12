---
title: "How do I install X-Fi Drivers?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by xsabrewulf on 2008-04-26
Hi I am trying to install the new beta drivers for Linux.

I have 7.10 and I loaded in Gnome but I have no idea how to install these drivers. I read the readme and I still don't understand. Can someone please help?

> ====================================================================

  Sound Blaster X-Fi Linux 32/64-bit Beta Driver Readme File

  April 2008

====================================================================

The purpose of this document is to describe how the X-Fi Linux device 
driver is built, packaged, and released.



Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.


2) Run one of the following commands as root in the terminal:



   ./installer
   


   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree


   
   On 2.6 kernels, the location of the ALSA source include directory

      is parsed automatically from the running kernel.

      If it is not in the standard place, specify the path via
   
   --with-alsainc=<ALSA_include_directory>.

 
   
  On 2.4 kernels, the location of the ALSA source include directory

      must be specified via --with-alsainc=<ALSA_include_directory>.



  * Note
      If integrated ALSA is to be used to build, --with-alsainc option

      must not be specified.





Uninstall

=========


In the terminal,


1) Change directory to /opt/Creative/XFiDrv_Linux_US-1.18



2) Run the following command as root


   ./configure

   make uninstall



 * Note

      For GNOME users, You may need to close the Volume Control
      applet before uninstalling. Right-click the Volume icon on the
      GNOME panel and select "Remove From Panel"



3) Manually delete all files in /opt/Creative/XFiDrv_Linux_US-1.18







Copyright (c) 2008 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================

---

### Post by xsabrewulf on 2008-04-26
Anyone?

:popcorn:

---

### Post by xsabrewulf on 2008-05-02
Another Bump

---

### Post by spotteddog on 2008-05-02
From everything I've read, they don't work.

---

### Post by flowing on 2008-05-04
I've had no luck as well.  All references by people much more seasoned with the 2.6.x kernel say that the driver refers to outdated linux libraries.  Hopefully Creative gets their head out of their collective a$$es and fixes it sooner than later.

Most likely, they won't.  They probably project supporting Linux won't help their bottom line.   Welcome to the human race..

---

### Post by Siyfion on 2008-05-04
Try searching a bit more carefully next time ;) [http://ubuntuforums.org/showthread.php?t=571656&highlight=creative+fi](http://ubuntuforums.org/showthread.php?t=571656&highlight=creative+fi)

---

