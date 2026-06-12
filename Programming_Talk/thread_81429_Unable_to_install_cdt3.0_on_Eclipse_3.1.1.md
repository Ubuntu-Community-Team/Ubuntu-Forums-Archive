---
title: "Unable to install cdt3.0 on Eclipse 3.1.1"
date: 2005-10-24
forum: Programming Talk
---

### Post by Mike Li on 2005-10-24
Hi ALL,

I just installed ubuntu eclipse 3.1.1 sdk on Breezy Badger.  When I tried to install cdt3.0 with Eclipse Software Update, it failed due to following errors:

Unable to complete action for feature "Eclipse C/C++ Development Tooling SDK" due to errors.

 Unable to create file "/usr/local/lib/eclipse/plugins/org.eclipse.cdt.source_3.0.0/src/org.eclipse.cdt.launch_3.0.0/cdtlaunchsrc.zip". [/usr/local/lib/eclipse/plugins/org.eclipse.cdt.source_3.0.0/src/org.eclipse.cdt.launch_3.0.0/cdtlaunchsrc.zip (No such file or directory)]

If I just install the tools, I got these errors:

Unable to complete action for feature "Eclipse C/C++ Development Tools" due to errors.
  Unable to create file "/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.0/cdtcore.jar". [/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.0/cdtcore.jar (No such file or directory)]

I wonder if I have missed any dependant packages. Any help is appreciated.

Thanks,

---

### Post by Mike Li on 2005-10-25
Problem solved.

Need to be root to install the cdt. By default, root login is not allowed with GDM. I created a root password with "sudo passwd root" command in a terminal and then goto System->Administration->Login Screen Setup, under security, check "Allow root login with GDM". Login as root and install with Eclipse Software Update.

---

### Post by skirkpatrick on 2005-10-25
Another possibility is to change the permissions  of the directory that Eclipse is installed in.

---

### Post by DennisCote on 2005-10-27
A simpler method is to run eclipse as root using the "Run as different user" item in the "System Tools" submenu under the Applications menu. Then proceed to add CDT as usual. This worked for me.

---

