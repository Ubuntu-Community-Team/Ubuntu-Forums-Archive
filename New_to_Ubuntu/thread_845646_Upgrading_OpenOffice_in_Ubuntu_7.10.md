---
title: "Upgrading OpenOffice in Ubuntu 7.10"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Laodocus on 2008-06-30
How exactly do you go about upgrading the Openoffice suit to 2.4 version? I am currently running 2.3. I noticed that I can d/l the package from Openoffice, however, I would prefer to do it through synaptic or apt-get. Any advice would be greatly appreciated....

---

### Post by Ozor Mox on 2008-06-30
If you want to use Synaptic then the easiest way is to upgrade Ubuntu to 8.04, which will update OpenOffice to the newest version. If you do not want to upgrade the whole OS, then enabling backports might give you the newer OpenOffice through apt.

---

### Post by forger on 2008-06-30
Unless someone created packages for 7.10 release, I don't think you can...

Unless there is a serious bug, I don't think they'll release officially openoffice 2.4. Why not upgrade to Hardy Heron 8.04?

---

### Post by Laodocus on 2008-06-30
I may upgrade, however, I am using software, whose manufacture only supports 7.10. The manufacturer told me I can try to use it on a later version. I will, if it works then I will upgrade 8.04. Otherwise my only option will be to uninstall the existing package and then manually install the tar ball?


thanks a bunch...

---

### Post by t.septekin on 2008-06-30
I'm using OpenOffice.org 2.4 in Ubuntu 7.04 and 7.10. These are my steps:

Download OOo_2.4.0_deb.tar.gz.
Make a temporary folder and copy it there, then extract all. The result should be a bunch of .deb files and a folder named desktop-integration.
Open Synaptic Package Manager and Search for openoffice.org-core, mark it for Removal (NOT Complete Removal) and apply.
In the Terminal, change directory to where the .deb files are located, enter sudo dpkg -i *.deb. Let it happen, when you get the prompt back enter cd desktop-integration and run sudo dpkg -i *.deb again.
Hope it works for you as it has done for me.

---

### Post by Laodocus on 2008-06-30
were exactly do I download OOo_2.4.0_deb.tar.gz?

thanks for the help

---

### Post by t.septekin on 2008-06-30
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)
select Linux DEB
Current version is named OOo_2.4.1_LinuxIntel_install_en-US_deb.tar.gz.
My apologies for incorrect naming.

---

### Post by Laodocus on 2008-07-01
will give it a shot.

thanks

---

### Post by Laodocus on 2008-07-03
Ok, I did what you instructed me to do. I don't know what happened. The only program I can get to open now is writer, but not before I get an error that says: Due to an unexpected error openoffice.org has crashed. All the files you were working on will now be saved. The next time openoffice.org is launched, your files will be recovered automatically. Then it goes on to open writer. It does this with all applications, however, no matter which one I open, it goes to writer no matter what. I may have to do a reinstall of the whole OS. I don't know what went wrong.

---

### Post by Hagar Delest on 2008-07-04
Had you removed all the Ubuntu packages of OOo (have the string 'ubuntu' in their version number)?

See here: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

If still a problem, try to rename your OOo user profile (~/.openoffice.org2).

---

