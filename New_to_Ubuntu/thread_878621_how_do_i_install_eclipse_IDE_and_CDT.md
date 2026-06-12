---
title: "how do i install eclipse IDE and CDT ???"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by maxreason on 2008-08-03
I have searched and searched and searched (on google, ubuntu, ubuntuforums, eclipse, eclipseforums) but not been able to figure out how to install the eclipse IDE and CDT on my newly created ubuntu linux system 8.04.1 - sigh.I give up.  So where-and-how do I download and install the most recent version of eclipse IDE and CDT on ubuntu 8.04.1 (32-bit) so I can continue developing my 3D simulation/graphics/game engine?Also, what else might I need to download and install to do OpenGL 2.0+ and GLSL development in C/C++ with eclipse?  For example, are all the C/C++ standard libraries already installed, or do they too need to be found/downloaded/installed?

---

### Post by pbpersson on 2008-08-03
Typically I would go to the Synaptic Package Manager and search on Eclipse.

One time when I wanted to install the latest version of Eclipse I went to their web site and followed their instructions.

This was six months ago, I don't know if this has changed.

I am personally now using NetBeans for my Java development so I have not looked at Eclipse in some time.

---

### Post by oDEIMOSo on 2008-08-03
I`m having problems with my graphics all of a sudden , everything was fine except some games i couldnt open because it said i was out of range . I tried to fix the problem now only simple programs are running and anything like animations and 3d effects does not work , i can only run my browsers and simple programs , can anyone help .

---

### Post by pbpersson on 2008-08-03
> **oDEIMOSo said:**
> I`m having problems with my graphics all of a sudden , everything was fine except some games i couldnt open because it said i was out of range . I tried to fix the problem now only simple programs are running and anything like animations and 3d effects does not work , i can only run my browsers and simple programs , can anyone help .

Does this question relate to installing Eclipse or did you mean to start a new thread?

---

### Post by oDEIMOSo on 2008-08-03
no i was trying to start a new thread sorry about that !!!

---

### Post by wruslan on 2008-08-30
uname --all
Linux wruslan-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
Eclipse SDK
Version: 3.2.2
Build id: M20070212-1330 (Ubuntu version: 3.2.2-5ubuntu2)

root@wruslan-laptop:/home/wruslan# apt-get install eclipse-cdt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  exuberant-ctags
The following NEW packages will be installed:
  eclipse-cdt exuberant-ctags
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9MB of archives.
After this operation, 20.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main exuberant-ctags 1:5.7-3 [115kB]
Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/universe eclipse-cdt 3.1.2-1 [17.8MB] 

I hope the above helps.

---

### Post by rjrenjian on 2008-09-06
Jack is a Vietnamese. One day, he sold a piece of [replica  rolex watch](http://www.cheap-replica-rolex.com/)to an American, John.After John received the watch, he found it didn't work and he immediately wrote an Email to Jack, which read "Hi, there. I have received the [watch](http://www.cheap-replica-rolex.com/). You said it is perfect in quality, but it didn't work here. Why?"Jack replied soon "Dear John, I am so sorry to hear that. Also please be patient , because of time difference,It's at night in Vietnam now, the watch is sleeping ."

---

### Post by fballem on 2008-09-21
> **maxreason said:**
> I have searched and searched and searched (on google, ubuntu, ubuntuforums, eclipse, eclipseforums) but not been able to figure out how to install the eclipse IDE and CDT on my newly created ubuntu linux system 8.04.1 - sigh.I give up.  So where-and-how do I download and install the most recent version of eclipse IDE and CDT on ubuntu 8.04.1 (32-bit) so I can continue developing my 3D simulation/graphics/game engine?Also, what else might I need to download and install to do OpenGL 2.0+ and GLSL development in C/C++ with eclipse?  For example, are all the C/C++ standard libraries already installed, or do they too need to be found/downloaded/installed?

The following notes may be helpful in doing a basic installation of Eclipse. Please note that this does not include the 'tuning' (i.e. setting parameters) that is required to get the installation working correctly.

**Eclipse**

This is a general purpose IDE used for development. The current version is 3.4 (Ganymede). This must be installed directly from the website ([http://www.eclipse.org](http://www.eclipse.org)), since the version of eclipse in the repositories is not current.

The original source for these instructions is: [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html). The original instructions were applicable to Eclipse Europa and have been updated here to include Ganymede.

**Overview**
As the result of these installation instructions
	1.	the main eclipse application will be installed in /opt/eclipse.
	2.	there will be a command shell located in /usr/local/bin.
	3.	there will be an eclipse folder in /usr/local/share.
	4.	there will be a desktop launcher (eclipse.desktop) in /usr/share/applications.

Prior to starting this process, a suitable icon must be found and downloaded. When completed, the icon will be located in /opt/eclipse. A suitable icon is located at [http://blogs.sun.com/arungupta/resource/images/ganymede-logo.png](http://blogs.sun.com/arungupta/resource/images/ganymede-logo.png) and may be initially downloaded to the Desktop or to any other location where it can be easily located.

**Installation Instructions**
1.	Verify that any previous installation has been completely removed. In particular, the following needs to be verified:
	a.	There is no eclipse folder under /opt. If there is, it must be deleted. Sudo access will be required to delete the folder.
	b.	There is no eclipse folder under /usr/local/share. If there is, it must be deleted. Sudo access will be required to delete the folder.
	b.	There is no entry for eclipse in either /usr/bin or /usr/local/bin. If there is, then the entry must be deleted.
	c.	There is no entry for eclipse.desktop in /usr/share/applications. If there is, then the entry must be deleted.
	b.	There is no configuration files for eclipse in the users' home folders. These are hidden directories. If there are any, these must be deleted.

2.	Obtain the appropriate file from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/). Only one of the packages is required. The file should be saved to the Desktop.

3.	When the download has been completed, open a Terminal and execute the following commands:
		cd ~/Desktop
		tar xzf eclipse-SDK-3.4-linux-gtk.tar.gz	(note that the filename may differ, depending on what was downloaded in step 2)
		sudo mv eclipse /opt/eclipse
		sudo mv ganymede-logo.png /opt/eclipse	(this will move the icon. The filename and location for the logo may differ - depending where it was saved)
		cd /opt
		sudo chown -R root:root eclipse
		sudo chmod -R +r eclipse
		cd /opt/eclipse
		sudo chmod +x eclipse

4.	Create an executable shell for eclipse. This is done through Terminal by executing the following commands:
		sudo touch /usr/local/bin/eclipse		(this assumes that /usr/local/bin is in the path)
		sudo chmod 755 /usr/local/bin/eclipse
		sudo nano /usr/bin/eclipse				(this will open the nano editor)

5.	When the eclipse shell file is open (in nano), the following contents need to be inserted and the file saved:
		#!/bin/sh
		export ECLIPSE_HOME="/opt/eclipse"
		$ECLIPSE_HOME/eclipse $*

6.	Create a GNOME menu item. This is done through Terminal by executing the following command:
		sudo nano /usr/share/applications/eclipse.desktop

7.	When the GNOME menu item is open (in nano), the following contents need to be inserted and the file saved:
		[Desktop Entry]
		Encoding=UTF-8
		Name=Eclipse
		Comment=Eclipse Ganymede IDE
		Exec=eclipse
		Icon=/opt/eclipse/ganymede-logo.png
		Terminal=false
		Type=Application
		Categories=GNOME;Application;Development
		StartupNotify=True

8.	Initialise eclipse by running the following command in Terminal: /opt/eclipse/eclipse --clean.

From this point forward, eclipse may be run from the Application menu.

Please let me know how these work for you, and if you need any additional help.

---

### Post by Sef on 2008-09-23
Moved to Absolute Beginner.

---

### Post by Chav on 2008-10-17
In step four 

> sudo nano /usr/bin/eclipse (this will open the nano editor)

should be 

> sudo nano /usr/**local**/bin/eclipse (this will open the nano editor)

Thank you for the guide.

---

### Post by cmarcel on 2008-11-23
To install eclipse, what's much easier is to do the following (on Ubuntu 8.10):

from the global Applications menu --> Add/Remove

In the popup window, pick 'Programming' on the left and 'show' 'All Open Source applications' in the top.  Search for Eclipse and install...

Worked like a charm for me.

My problem then was in getting CDT installed...  From Eclipse itself you can add add-ons from the Help menu, but I was getting an error partway through, with a 'failure' with the package 'org.eclipse.platform...'.  It ends up, as you might imagine, that you need to run Eclipse as sudo when you install the add-ons.

So...  Start a terminal session, do 'sudo Eclipse' from the folder where Eclipse was installed, then
- Click Help --> Software Updates --> Find and Install
- Choose 'Search for new features to install' & click Next
- Pick the 'Callisto Discovery Site', 'Ignore features not applicable' & click Finish
- This is where things get a bit confusing: following the steps from here on (I don't have them written down) it will install something like 39 add-ons and it does not seem to let you pick only the CDT add-on: it's all-or-nothing.  

It takes quite a while for it to get the list of add-ons, find the mirror, download everything and finally install it.  But the end result is that everything is properly (& easily) configured :)

Best,

Christophe

P.S.: you don't need to run Eclipse as sudo other than when you want to do software updates through that Help menu - in fact, as you can imagine, you should NEVER run it as sudo when you are developing (well, I can imagine some rare cases, but you get the idea).

---

### Post by leden on 2008-12-02
I downloaded "Eclipse IDE for Java EE Developers (162 MB)" (from [http://www.eclipse.org/downloads/]("http://www.eclipse.org/downloads/")) then I followed the insructions and in the last step, when I try to initialise Eclipse the following error occurs:
"The Eclipse executable launcher was unable to locate its 
companion shared library."
The same error occurs if I just run Eclipse from any directory.

It seems like libraries are missing, or what? What should I do?

---

### Post by sykemyke on 2010-02-01
eclipse-cdt is currently out of Karmic, reason is "broken" due compatibility problems with new eclipse version. See [https://launchpad.net/ubuntu/karmic/+source/eclipse-cdt/3.1.2-2](https://launchpad.net/ubuntu/karmic/+source/eclipse-cdt/3.1.2-2) **Deleted**       on 2009-10-27...

Meantime, workaround by manually install it...

In eclipse 6: 

0) exit eclipse.

1) aptitude install eclipse-pde   (plugin developement environment)

2) start eclipse.

3) Help -> Install New Software -> Add... -button
Location = [http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)

4) Click Work with -field drop-down list, choose previously inserted source as above.

5) Select CDT Main Features (rest can be added after Eclipse restart below)

6) Click Next and click through wizard.

Voila. I hope eclipse-cdt will be fixed in Karmic.

---

### Post by Zargoon on 2010-05-31
Thanks, this worked great in Lucid.

---

### Post by ubuntify on 2010-10-18
In Lucid multiple users have a problem when for example trying to install the CDT package on top of the basic (Java enabled) installation of Eclipse.

For the CDT example it is possible to "enable" it but it has no effect at all (a new Perspective is never created).

This works only for the first user (that installs Eclipse from the package manager), maybe there is some problems with su rights here?

---

### Post by tomhollis on 2011-05-04
I was having real problems getting the CDT to work with the packages from synaptic for some reason, it just never brought up the C/C++ options. 

I have now got Helios working well on my system, my only issue is that Eclipse doesn't show up in the unity dashboard so you can't click over to it easily. It is in the menu, just doesn't show up when it is running. Any suggestions?

---

### Post by aslacker on 2013-03-14
> **fballem said:**
> The following notes may be helpful in doing a basic installation of Eclipse. Please note that this does not include the 'tuning' (i.e. setting parameters) that is required to get the installation working correctly.

**Eclipse**

This is a general purpose IDE used for development. The current version is 3.4 (Ganymede). This must be installed directly from the website ([http://www.eclipse.org](http://www.eclipse.org)), since the version of eclipse in the repositories is not current.

The original source for these instructions is: [http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html). The original instructions were applicable to Eclipse Europa and have been updated here to include Ganymede.

**Overview**
As the result of these installation instructions
    1.    the main eclipse application will be installed in /opt/eclipse.
    2.    there will be a command shell located in /usr/local/bin.
    3.    there will be an eclipse folder in /usr/local/share.
    4.    there will be a desktop launcher (eclipse.desktop) in /usr/share/applications.

Prior to starting this process, a suitable icon must be found and downloaded. When completed, the icon will be located in /opt/eclipse. A suitable icon is located at [http://blogs.sun.com/arungupta/resource/images/ganymede-logo.png](http://blogs.sun.com/arungupta/resource/images/ganymede-logo.png) and may be initially downloaded to the Desktop or to any other location where it can be easily located.

**Installation Instructions**
1.    Verify that any previous installation has been completely removed. In particular, the following needs to be verified:
    a.    There is no eclipse folder under /opt. If there is, it must be deleted. Sudo access will be required to delete the folder.
    b.    There is no eclipse folder under /usr/local/share. If there is, it must be deleted. Sudo access will be required to delete the folder.
    b.    There is no entry for eclipse in either /usr/bin or /usr/local/bin. If there is, then the entry must be deleted.
    c.    There is no entry for eclipse.desktop in /usr/share/applications. If there is, then the entry must be deleted.
    b.    There is no configuration files for eclipse in the users' home folders. These are hidden directories. If there are any, these must be deleted.

2.    Obtain the appropriate file from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/). Only one of the packages is required. The file should be saved to the Desktop.

3.    When the download has been completed, open a Terminal and execute the following commands:
        cd ~/Desktop
        tar xzf eclipse-SDK-3.4-linux-gtk.tar.gz    (note that the filename may differ, depending on what was downloaded in step 2)
        sudo mv eclipse /opt/eclipse
        sudo mv ganymede-logo.png /opt/eclipse    (this will move the icon. The filename and location for the logo may differ - depending where it was saved)
        cd /opt
        sudo chown -R root:root eclipse
        sudo chmod -R +r eclipse
        cd /opt/eclipse
        sudo chmod +x eclipse

4.    Create an executable shell for eclipse. This is done through Terminal by executing the following commands:
        sudo touch /usr/local/bin/eclipse        (this assumes that /usr/local/bin is in the path)
        sudo chmod 755 /usr/local/bin/eclipse
        sudo nano /usr/bin/eclipse                (this will open the nano editor)

5.    When the eclipse shell file is open (in nano), the following contents need to be inserted and the file saved:
        #!/bin/sh
        export ECLIPSE_HOME="/opt/eclipse"
        $ECLIPSE_HOME/eclipse $*

6.    Create a GNOME menu item. This is done through Terminal by executing the following command:
        sudo nano /usr/share/applications/eclipse.desktop

7.    When the GNOME menu item is open (in nano), the following contents need to be inserted and the file saved:
        [Desktop Entry]
        Encoding=UTF-8
        Name=Eclipse
        Comment=Eclipse Ganymede IDE
        Exec=eclipse
        Icon=/opt/eclipse/ganymede-logo.png
        Terminal=false
        Type=Application
        Categories=GNOME;Application;Development
        StartupNotify=True

8.    Initialise eclipse by running the following command in Terminal: /opt/eclipse/eclipse --clean.

From this point forward, eclipse may be run from the Application menu.

Please let me know how these work for you, and if you need any additional help.
[SIZE=2] ** fballem**,

Thank you very much for your reply. It's a very nice solution (it's a solution
to me as there is no clear instruction on installing eclipse on Linux. 

Your tutorial clear my doubts that I would always get while installing cdt, such as which should be the installation path - what should be the correct permission etc.

It seems eclipse cdt people never bother to inform linux users abut these issues. I am sorry - I am not aware of any solid linux based tutorial.

Almost all the available tutorials  written on win only. There must be some issues which prevents eclipse from writing tutorial on linux/freebsd etc. Are they trying to make people/win-users to replace VC? 

[/SIZE][SIZE=6]**[SIZE=2]Thanks again. [/SIZE]:)**[/SIZE]

---

### Post by wildmanne39 on 2013-03-14
Old thread closed!

---

