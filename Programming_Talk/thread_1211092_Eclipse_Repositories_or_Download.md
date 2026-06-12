---
title: "Eclipse: Repositories or Download?"
date: 2009-07-12
forum: Programming Talk
---

### Post by gzunk on 2009-07-12
I'm a Java developer by trade, and I've just installed Ubuntu.

The eclipse in the respository seems to bring down lots of dependencies, and I was wondering, do people here use the eclipse from the repository, or one downloaded externally?

I'm used to maintaining my own set of Java libraries and JVM's, and I don't know if I'm quite ready to hand over that responsibility to Ubuntu.

I have the same issue with things like Tomcat, Glassfish, JBoss, Ant, OpenLDAP etc - do I rely on the repository which will get me automatic updates etc, or do I roll my own, which means I get complete control...

---

### Post by Copernicus1234 on 2009-07-12
The latest version in the repositories is still 3.2 I believe? The one on the web site is 3.5.

For me it was a easy choice. I got the newest version. Its just a folder and everything runs from there so it doesnt change your existing system.

---

### Post by fballem on 2009-07-12
> **gzunk said:**
> I'm a Java developer by trade, and I've just installed Ubuntu.

The eclipse in the respository seems to bring down lots of dependencies, and I was wondering, do people here use the eclipse from the repository, or one downloaded externally?

I'm used to maintaining my own set of Java libraries and JVM's, and I don't know if I'm quite ready to hand over that responsibility to Ubuntu.

I have the same issue with things like Tomcat, Glassfish, JBoss, Ant, OpenLDAP etc - do I rely on the repository which will get me automatic updates etc, or do I roll my own, which means I get complete control...

I'm not as extensively into development as you are, but the versions that are in the repository for most of the tools are quite outdated.

You may need to come up with some means to install some of these. 

For example, this is how I install Eclipse from eclipse.org

Eclipse

This is a general purpose IDE used for development. The current version is 3.5 (Galileo). This must be installed directly from the website ([http://www.eclipse.org](http://www.eclipse.org)), since the version of eclipse in the repositories is not current.

Overview

When this installation is complete:
[LIST=1]
[*]The eclipse program files will be installed in the /opt/eclipse folder.
[*]A user group called 'eclipse' will exist and authorized users will be associated with that group.
[*]All entries in the /opt/eclipse folder will: be owned by root, be associated with the eclipse group.
[*]The eclipse group will have full access to the entries in the folder. Other users will be denied access.
[*]There will be a launch item in Applications > Programming that will start eclipse.
[*]The default update site: [http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo) will be added to the Available Software sites in the eclipse installation.
[/LIST]
Installation Instructions
[LIST=1]
[*]Verify that any previous installation has been completely removed. In particular, the following needs to be verified:
[LIST=2]
[*]There is no eclipse folder under /opt. If there is, it must be deleted. Sudo access will be required to delete the folder.
[*]There is no eclipse folder under /usr/local/share. If there is, it must be deleted. Sudo access will be required to delete the folder.
[*]There is no entry for eclipse in either /usr/bin or /usr/local/bin. If there is, then the entry must be deleted.
[*]There is no entry for eclipse.desktop in /usr/share/applications. If there is, then the entry must be deleted.
[*]There is no configuration files for eclipse in the users' home folders. These are hidden directories. If there are any, these must be deleted.
[/LIST]
[*]Verify that there is a group called 'eclipse' and that users are authorized in that group:
[LIST=2]
[*]Select System > Administration > Users and Groups.
[*]Select Unlock and provide your password.
[*]Select Manage Groups
[*]Scroll the list to determine if there is a group called 'eclipse'. If there is not, then add the group.
[*]Ensure that all users, including root, are members of the eclipse group.
[/LIST]
[*]Obtain the appropriate file from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/). Only one of the packages is required. The file should be saved to the Desktop.
[*]When the download has been completed, open a Terminal and execute the following commands:
```

cd ~/Desktop				(change to where the file was downloaded)
tar xzf eclipse-SDK-3.5-linux-gtk-x86_64.tar.gz		(note that the filename may differ, depending on what was downloaded in step 2)
sudo mv eclipse /opt/eclipse				(move the files to a folder under the /opt folder)
cd /opt							(change to the /opt folder)
sudo chown -R root:eclipse eclipse			(change the owner to root and the group to eclipse)
sudo chmod -R 775 eclipse				(owner and group can read/write/delete, other users may read the files)
cd /opt/eclipse						(change to the eclipse folder)
sudo chmod +x eclipse					(eclipse must be executable)

```
[*]Create a menu item. This is done by right-clicking on the menu on the top panel and adding the item. Note that the command is /opt/eclipse/eclipse. The icon can be found in the /opt/eclipse folder.
[*]Start eclipse.
[*]Use Window > Preferences > Install/Update > Available Software Sites to add:
[LIST=2]
[*][http://download.eclipse.org/releases/galileo](http://download.eclipse.org/releases/galileo)
[*][http://download.eclipse.org/technology/epp/packages/galileo/](http://download.eclipse.org/technology/epp/packages/galileo/)
[/LIST]
[/LIST]
The EPP update site will allow for the installation at the package level, and may be used to install complete packages, such as the RCP plugins.

From this point forward, eclipse may be run from the Application menu:

---

### Post by mikhmv on 2009-08-21
Good Totorial!!
Thanks.

Could you like to correct this link: [http://download.eclipse.org/technology/epp/packages/galileo/](http://download.eclipse.org/technology/epp/packages/galileo/)

It doesn't exist....

---

### Post by credobyte on 2009-08-21
Repositories is what I prefer - versions are pretty much the same and you will not get tons of new options in case of using the latest version from their official website.

---

### Post by Mirge on 2009-08-21
Older thread I know, but I would advise ppl to download latest from eclipse's site... not from repositories. The version from site is faster than repositories.. by a good bit.

---

### Post by Can+~ on 2009-08-21
Download. As simple as untar into a folder and run it.

---

### Post by karlmp on 2009-08-21
the version from the repositories is buggy

[https://blueprints.launchpad.net/ubuntu/+spec/eclipse](https://blueprints.launchpad.net/ubuntu/+spec/eclipse)

---

### Post by MrPok on 2010-08-04
> **karlmp said:**
> the version from the repositories is buggy

[https://blueprints.launchpad.net/ubuntu/+spec/eclipse](https://blueprints.launchpad.net/ubuntu/+spec/eclipse)

Hi, I'm normally not really fond of bumping old threads, but this is perhaps a more fundamental issue -- from the [Ubuntu Documentation]("https://help.ubuntu.com/community/EclipseIDE") I read that:

> Ubuntu 9.10 and up
Since Ubuntu 9.10, the following Eclipse versions are available as a standard package (eclipse) in the Universe repository, via any package manager in Ubuntu.

* Ubuntu 10.04 LTS: Eclipse 3.5.2 * Ubuntu 9.10: Eclipse 3.5.1

Note: to install plugins not available in Package Manager, you'll need to install them in user mode. Do not run Eclipse as root to install plugins.

My question is based on the documentation note that perhaps *(I hope)* indicates that the repositories will stay closer to the most recent version from 9.10 onwards..
*versus*
..the blueprint of karlmp above, and the fact that a respository maintainer will always stay a step behind the developer:

[INDENT]**Is using the repository version of Eclipse a better choice if you're running 10.4, or is a manual install (that gets you version 3.6) still the best way to go?**[/INDENT]

I guess this question will pop up every once in a while, so I'm trying to think of a general best practice (maybe something for the FAQ as well)... *(I used to run multiple installs of Eclipse, because of the hassle)*

Again, sorry for the bump.

Kind regards,
Paul

---

### Post by karlmp on 2010-08-04
> Is using the repository version of Eclipse a better choice if you're running 10.4, or is a manual install (that gets you version 3.6) still the best way to go?

use the repository version.

---

### Post by MrPok on 2010-08-04
> **karlmp said:**
> use the repository version.
I'm surprised this is coming from you! ;) 
What is it that made you change your mind?

---

### Post by jtcady on 2010-08-04
I think its easier to download from website and then run it from folder.

---

### Post by karlmp on 2010-08-05
the repo version works fine.

but if you want to have the latest of everything, I recommend you archlinux [http://wiki.archlinux.org/index.php/Beginners'_Guide](http://wiki.archlinux.org/index.php/Beginners'_Guide). It's a hemorrhaging edge distro and more stable than ubuntu!

---

