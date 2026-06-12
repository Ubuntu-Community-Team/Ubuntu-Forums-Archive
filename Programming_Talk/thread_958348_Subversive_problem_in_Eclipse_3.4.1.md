---
title: "Subversive problem in Eclipse 3.4.1"
date: 2008-10-25
forum: Programming Talk
---

### Post by zpzpzp on 2008-10-25
Hi

I have this following error when trying to update a project from SVN:

------------
SVN: '0x0040011a: Call Menu Action' operation finished with error: Selected SVN connector library is not available or cannot be loaded.
If you selected native JavaHL connector, please check if binaries are available or install and select pure Java Subversion connector from the plug-in connectors update site.
If connectors already installed then you can change the selected one at: Window->Preferences->Team->SVN->SVN Client.
Selected SVN connector library is not available or cannot be loaded.
If you selected native JavaHL connector, please check if binaries are available or install and select pure Java Subversion connector from the plug-in connectors update site.
If connectors already installed then you can change the selected one at: Window->Preferences->Team->SVN->SVN Client.
---------

There is no "SVN Client" under "SVN" folder as indicated in the error message. I downloaded a new Eclipse, installed Subversive, and tried to checkout the project but I got the same error.

Does anyone know how to solve this problem?

Thanks.

Paul

---

### Post by cipi.ro on 2008-10-31
Hi,

I have installed today eclipse on Ubuntu 8.10 and decided to try subversive (I am working with subclipse). For subversive it appears that we need to add an Update site for the SVN connectors, because of licensing...

This is the update site: [http://www.polarion.org/projects/subversive/download/eclipse/2.0/ganymede-site/](http://www.polarion.org/projects/subversive/download/eclipse/2.0/ganymede-site/)


For more information, look here: [http://www.eclipse.org/subversive/documentation/gettingStarted/aboutSubversive/install.php](http://www.eclipse.org/subversive/documentation/gettingStarted/aboutSubversive/install.php)

---

### Post by Mugatu on 2008-12-08
I had the same exact problem.  I'm not 100% sure, but I think mine wasn't working because of the version of SVN I was trying to connect to (1.4.2).  I had to go back into Software Updates in Eclipse, search the site where I got the Subversive SVN Connector ([http://www.polarion.org/projects/subversive/download/eclipse/2.0/update-site/](http://www.polarion.org/projects/subversive/download/eclipse/2.0/update-site/)), and under Subversive SVN Connectors I had to install the "SVNKit 1.1.7 Implementation (Optional)"

That fixed my problem, so I'm guessing there must have been some kind of issue with compatibility.

---

