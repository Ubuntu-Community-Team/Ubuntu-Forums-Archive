---
title: "HOWTO: Install FirstClass Client (AKA Ednet) for Rock Valley College in Ubuntu 7.10"
date: 2008-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by hurtstotalktoyou on 2008-03-22
*Introduction*

Ubuntu is probably the most popular operating system after Windows and Mac OS, yet Rock Valley College does not provide adequate or even correct Ednet installation instructions for Ubuntu users. I have therefore created this brief guide to help users of Ubuntu and its derivatives in the process. Please keep in mind this guide is written for Ubuntu 7.10 (Gutsy Gibbon), but it should work for any derivatives thereof (e.g. Kubuntu, Xubuntu, gOS, etc.), as well as later versions and their derivatives. Just keep in mind that if you're using an earlier version of Ubuntu , or a derivative based on an earlier version (e.g. Freespire), you may need to improvise a little bit. Either way, though, this guide should be very helpful, especially to Linux newbies.

*The big question: i686 or i386?*

If your computer has a 64-bit processor, and you're running the 64-bit version of Ubuntu, the i686 package for Debian should be your best bet. However, I have not been able to test that; I simply assume it will work. To make sure Ednet installs properly, you may need to install the i386 version. Unfortunately, the i386 version is not available for Debian. To solve this problem, I have shown how to install the Fedora Core version. Don't be put off by the fact that Fedora Core software isn't guaranteed to install on Ubuntu; I assure you that in this case it works very well. However, if you want to try the i686 version, I have included a guide for that, too.

Well, are you ready? Let's go install Ednet!

[B]
Installation procedure for the i386 (32-bit) version of Ednet[/B]

*Step 01:* If you have not already done so, you must install Alien, a tool allowing Ubuntu users to install non-Debian packages. To do this, go to the Synaptic Package Manager (System > Administration > Synaptic Package Manager) and mark "alien" for installation. You will be asked to mark other files as well; just click "Mark" to do this. Click "Apply" to install the marked applications. Exit Synaptic Package Manager when finished.

*Step 02:* Click on [this link](http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2.fc5.i386.rpm). When the download window pops up, choose "Save to Disk". If prompted, choose the home folder as your save location (it will be the same as your Ubuntu username).

*Step 03:* In terminal (Applications > Accessoried > Terminal), type "sudo alien -i fcc-8.315-2.fc5.i386.rpm". If you did not save the file in step 03 to your home folder, you may have to navigate to that location (e.g. "cd Desktop"). The installation will proceed quickly. When you are given another $ prompt, exit terminal.

*Step 04:* To run Ednet for the first time, click on Applications > Internet > FirstClass Client.
[I]
Step 05:[/I] You will have to set up your RVC login before you can be connected to the EdNet server. To do this, click on "Setup..." in the FirstClass Login window.

*Step 06:* In the "Username" box, type the letter "s" followed by your seven-digit student ID number. If you are an instructor, you will need to instead type the letter "e" or "a" followed by your seven-digit ID number. NOTE: If your ID number is only six digits, you must make it seven by adding a zero to the left. E.g. if your ID number is 340575, you should type in "s034575" (or "e034575" or "a034575" if you're an instructor).

*Step 07:* In the "Password" box, type in your MMDDYY date of birth.

*Step 08:* In the "Server" box, type "ednet.rvc.cc.il.us".

*Step 09:* Click "Save". This will close the Setup window.

*Step 10: *In the FirstClass Login window, click "Login". This will connect you to Ednet @ RVC.

*Step 11:* If you'd like to add an icon to your desktop, go to Applications > Internet, and right-click on "FirstClass Client". A menu will appear; click "Add this launcher to desktop".


**Installation procedure for the i686 (64-bit) version**

*Step 01:* Click on [this link](http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb). A window will pop up asking you what to do. Choose "Open with gdebi-gtk (default)", then click "OK".

*Step 02:* A new window will pop up. In it, click "Install Package". The installation will proceed quickly.

*Step 03:* When it tells you "Installation finished", click "Close", then exit the Package Installer window.

*Step 04:* To run Ednet for the first time, go to Applications > Internet > FirstClass Client.

*Step 05: *If the FirstClass Login window pops up, then the installation was successful, and you can skip to step 05 in the i386 instructions above. If not, you will have to uninstall the i686 version. To do this, run terminal (Applications > Accessories > Terminal), and type "sudo dpkg -r fcc". Only once you uninstall the i686 version can you try to install the i386 version.


**Final thoughts**

As you can see, this installation process is a little more involved than we'd hope. I'm a little disappointed that RVC chose not to explain the proceedures. You might be tempted to try the Windows version of Ednet in Wine. Let me assure you, this does not work, and in fact causes some lag problems in Ubuntu. So, if you tried Ednet in Wine, I suggest you uninstall it, reboot Ubuntu, and install the Linux version as described above.

Good luck!

---

