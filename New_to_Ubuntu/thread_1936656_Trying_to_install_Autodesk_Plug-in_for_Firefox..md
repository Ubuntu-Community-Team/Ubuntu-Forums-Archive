---
title: "Trying to install Autodesk Plug-in for Firefox."
date: 2012-03-06
forum: New to Ubuntu
---

### Post by Grrruff on 2012-03-06
Hey Everyone,


Using Ubuntu 11.10.

Critical for us is the ability to run the new Autodesk Plug-in for Firefox.  This Plug-in allows the viewing and measuring of Autodesk 3D part and assembly models of the DWF format.

The download from the Autodesk site is an msi file.

I couldn't seem to download the file in Ubuntu.  It kept wanting to run it regardless of what options I chose.

Downloaded the MSI to a Windows Machine and transfered it via a thumb drive.

When double clicked Ubuntu reported it did not know what to do with this file.  I thought maybe I needed Wine to get the windows installer.  downloaded Wine 1.2.  Still cannot get the MSI to install to firefox.

Any help here?

---

### Post by teward on 2012-03-06
The issue you are having is that this plugin is Windows Only.  This means that in order to make it work with Firefox, you'd have to have the Windows version of Firefox installed in Wine, and then always use the Windows version.

This is the only true solution to your problem, since most installers run with Wine will usually only touch /home/user/.wine/drive_c/*, and not any other system directory on your system.


I should also add that Windows executables don't work on Ubuntu unless you use Wine, because Linux and Windows binaries are not completely compatible with each other (hence why Wine and Mono exist)

---

### Post by Bobhuber on 2012-03-06
> **Grrruff said:**
> Hey Everyone,


Using Ubuntu 11.10.

Critical for us is the ability to run the new Autodesk Plug-in for Firefox.  This Plug-in allows the viewing and measuring of Autodesk 3D part and assembly models of the DWF format.

The download from the Autodesk site is an msi file.

I couldn't seem to download the file in Ubuntu.  It kept wanting to run it regardless of what options I chose.

Downloaded the MSI to a Windows Machine and transfered it via a thumb drive.

When double clicked Ubuntu reported it did not know what to do with this file.  I thought maybe I needed Wine to get the windows installer.  downloaded Wine 1.2.  Still cannot get the MSI to install to firefox.

Any help here?
Install Virtualbox in Ubuntu and run windows and firefox in that. You can even share folders with Ubuntu if needed so it should work fine for you.IMO much better than Wine if you have a legitimate copy (or not) of Windows .
Use the version at the Oracle site (not the repository package) and be sure to install the guest additions.

---

### Post by Grrruff on 2012-03-06
You both may well be right.

Seems odd though as they have plug-ins for the i-Phone, i-Pad, Android, and many browsers.  Why the FireFox plug-in would be the only one that cannot run in Firefox I do not know.

So following your advice I will have two firefox installations.
One in Ubuntu and one inside Wine's Windows emulation.  Correct?

How would I go about installing Firefox in Wine?  I am a total newb at this.

---

