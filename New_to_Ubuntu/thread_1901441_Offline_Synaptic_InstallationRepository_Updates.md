---
title: "Offline Synaptic Installation/Repository Updates"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by cortman on 2011-12-28
[SIZE="4"]**Offline Synaptic Installation/Repository Updates**[/SIZE]



**Goal:** To allow users with fresh installations of Ubuntu that don’t have internet access with that machine to install software from the Ubuntu repositories. I’ve never seen a tutorial or tip like this, so I hope it will meet some hitherto unmet needs.


**Skill level:** Basic. I’ve tried to make this pretty simple. I recommend you copy/paste all code given in this tutorial rather than type it out, to make sure no typos occur. 
If you have any questions at all leave a comment at the bottom of the page. I’ll try and keep this updated and provide support.


**About:** This tutorial is especially aimed at users with a fresh installation of Ubuntu 11.10 on their computer but with no internet connection available to that computer. If you can get your computer online, by all means skip this tutorial and install your software the easy way. 

Many people still don’t have internet access at home, and many of those people own desktop computers, which aren’t very portable to local wifi hotspots or internet cafés. That’s where these instructions will be handy.

This tutorial assumes you have access to a second computer running Ubuntu with an internet connection. We’ll refer to this as your “online” PC, and your first machine as the “offline” one.
Since the easiest and most common tool for offline software installation, Synaptic Package Manager, doesn’t come bundled with Ubuntu any more (as of 11.10) this tutorial will guide you through installing Synaptic first.


**[SIZE="2"]IMPORTANT:[/SIZE]** Before you do anything else, you first need to know whether your **offline** Ubuntu installation uses 32 or 64 bit architecture. To find this out, open a terminal by typing 

> Control+Alt+t

When the terminal is open, copy/paste the following code at the prompt:

```
uname –m
```

This will give an output of either **x86_64** (64 bit) or **i686 – i386** (32 bit). The packages are different for 64 and 32 bit, but the whole basic procedure will remain the same. Just remember throughout this tutorial which your system uses.


Now to install Synaptic!


**[SIZE="2"]1.[/SIZE]** **[SIZE="2"]On the online computer:[/SIZE]** Make a new folder in your home folder called “synaptic” (no quotes, obviously).

**[SIZE="2"]2.[/SIZE]** If your offline system is **32 bit**, open a text editor and copy/paste the code below into it-

```

#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libstdc++6_4.6.1-9ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libgcc1_4.6.1-9ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.30.0-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.4.4-2ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdk-pixbuf/libgdk-pixbuf2.0-0_2.24.0-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.24.6-0ubuntu5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.29.3+git20110916-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.11_0.8.16~exp5ubuntu13_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.13-20ubuntu5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.3_0.8.16~exp5ubuntu13_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hicolor-icon-theme/hicolor-icon-theme_0.12-1ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libe/libept/libept1_1.0.5build1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration1_0.1.54_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.28.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xapian-core/libxapian22_1.2.5-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.75.2ubuntu8_i386.deb 
```


If your offline system is **64 bit**, copy/paste this code instead:

```

#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libstdc++6_4.6.1-9ubuntu3_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libgcc1_4.6.1-9ubuntu3_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.30.0-0ubuntu4_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.4.4-2ubuntu1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdk-pixbuf/libgdk-pixbuf2.0-0_2.24.0-1ubuntu1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.24.6-0ubuntu5_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.29.3+git20110916-0ubuntu1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.11_0.8.16~exp5ubuntu13_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.13-20ubuntu5_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.3_0.8.16~exp5ubuntu13_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hicolor-icon-theme/hicolor-icon-theme_0.12-1ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libe/libept/libept1_1.0.5build1_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/liblaunchpad-integration1_0.1.54_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.28.2-0ubuntu2_amd64.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xapian-core/libxapian22_1.2.5-1ubuntu1_amd64.deb
wget –c http://us.archive.ubuntu.com/ubuntu/pool/universe/s/synaptic/synaptic_0.75.2ubuntu8_amd64.deb 
```


This is a complete download script for Synaptic, with all dependencies. Save this file as synapt.sh in the folder “synaptic” that you just created.


**[SIZE="2"]3.[/SIZE]** Open a terminal (Control+Alt+t again) and copy/paste the following code at the prompt.


```
 chmod +x synaptic/synapt.sh
```


Then run


```
./synapt.sh
```


All the required packages for Synaptic will be downloaded into the “synaptic” folder. They’ll all have a .deb file extension.


**[SIZE="2"]4.[/SIZE]** Use a flash drive to copy the folder to the **[SIZE="2"]offline[/SIZE]** computer’s home. Open a terminal and type


```
sudo dpkg –iR synaptic 
```


Enter your password at the prompt. This will install Synaptic on your offline computer. The first step is done!



**[SIZE="3"]STEP 2: Update Repositories[/SIZE]**


Almost all the software available for Ubuntu is stored on Canonical servers. These software groups are called repositories. In the software installation process Synaptic simply sends a message to these servers telling them which packages to download, and then installs it for you. You did the process manually yourself when you installed Synaptic in the previous step.

Before downloading anything from a repository, Synaptic needs to know exactly what is in the repository in the first place. Each repository contains a compressed text file with a long list of all software packages available in that repository. Synaptic looks at that info and relays that to you in the program. Since our offline Synaptic can’t query a server, we need to download those lists of packages, copy them onto the offline computer, and tell Synaptic to look on the computer itself for the info. Follow this part very closely.

**NOTE:** This step is for users of Ubuntu 11.10 Oneiric Ocelot. I’ll try and keep this page updated for later versions. The same procedures will still apply no matter what version of Ubuntu you have; the only difference will be the name of the version.

**[SIZE="2"]1. On your online computer:[/SIZE]** Direct your web browser to

[http://ubuntu.secs.oakland.edu/dists/](http://ubuntu.secs.oakland.edu/dists/) 

This is where the repositories for all Ubuntu versions from Hardy Heron to Oneiric Ocelot are kept. If you’re running Oneiric (as this tutorial assumes you are) select “oneiric”.
This will take you to another page, where you’ll select “main/”. 
On the next page, select “binary-i386/” if your computer is 32 bit, or “binary-amd64/” if it is 64 bit. 
On the next page, select “Packages.gz”. 
This will download a compressed text file with the list of all available software in the Main Ubuntu repository. Save the compressed file (don’t uncompress it!) to its own folder on your flash drive. Since you’ll be downloading 4 of these compressed files (all having the same name) saving them in individual folders will help keep them sorted out.
Go back to 

[http://ubuntu.secs.oakland.edu/dists/oneiric/](http://ubuntu.secs.oakland.edu/dists/oneiric/) 

and follow the above procedure with “multiverse/”, “restricted/” and “universe/”.
When it’s all said and done you should have 4 Packages.gz files on your flash drive. 


**[SIZE="2"]2.[/SIZE]** Take your flash drive to the**[SIZE="2"] offline[/SIZE]** computer and open a terminal. Copy/paste the following command-

For a 32 bit system: 

```
mkdir –p ~/dists/oneiric/main/binary-i386 ~/dists/oneiric/multiverse/binary-i386 ~/dists/oneiric/restricted/binary-i386 ~/dists/oneiric/universe/binary-i386

```

For a 64 bit system: 

```
 mkdir –p ~/dists/oneiric/main/binary-amd64 ~/dists/oneiric/multiverse/binary-amd64 ~/dists/oneiric/restricted/binary-amd64 ~/dists/oneiric/universe/binary-amd64

```

This command makes a number of new folders in your home folder. It’s important that you don’t delete or edit these folders in any way in the future.

**[SIZE="2"]3.[/SIZE]** Copy each Packages.gz file to its corresponding folder in home- i.e., the file you got from Main goes in dists/oneiric/main/binary-i386, the file from Multiverse goes in dists/oneiric/multiverse/binary-i386, etc. Again, don’t uncompress any of these files!

**[SIZE="2"]4. [/SIZE]**Once these are all copied over, open a terminal and type


```
synaptic
```


To open Synaptic Package Manager. In Synaptic, click Settings>Repositories.
This will bring up the repository dialog box. Select the “Other Software” tab.


[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/new%20repo.png[/IMG]
 

Select “Add…”.
What you’ll be doing is telling Synaptic where it can look to find software information other than the online repositories. 
In the Add Repository dialog, type the following

```
 deb file:/home/your_user_name oneiric main 
```

[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/repo_name.png[/IMG]
 
Obviously, change your_user_name to your user name. Note that after your user name there’s a space, the name of the Ubuntu version (oneiric), space, and then the repository name (main, multiverse, universe, restricted).

Click Add Source and you’re done. Repeat this process, substituting the name of each repository for “main”. When you’re done you’ll have added four new repositories. It should look like this.


[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/sources.png[/IMG]
 

Synaptic will automatically add four other “Source Code” repositories. In my experience with offline package managing these don’t serve any purpose and generate confusing error messages, so go ahead and remove each one that has “Source Code” appended to the end of the name.
When you’re done with that, close out of the Repositories dialog and click the large “Reload” button in the upper left.

The reloading process WILL give you an error message, simply because it wasn’t able to contact the Ubuntu servers. Scroll down to the bottom of the error log. If you don’t see any errors about your recently added repositories, the update was successful!


[IMG]http://dl.dropbox.com/u/54881717/synaptic%20tutorial/error.png[/IMG]


You’re all set to install software now! For info on how to get started with that, see [my other tutorial]("http://ubuntuforums.org/showthread.php?t=1900550") on how to install software offline using Synaptic.

---

### Post by a5h3n on 2012-03-06
Trying this solution with 10.04 results in all of the package management utilities no longer being able to open and, for some reason, terminal no longer being able to open.

Like I said, I'll have more info when I have time to fix a problem that makes even viewing the errors a pain.

For now, are there any changes I'd need to make (besides the obvious change to the repository name) to make this work for 10.04 that might result in the program installing with unmet dependencies (the error I saw said that was likely the cause).

---

### Post by cortman on 2012-03-06
I must say I have not tested this in 10.04. The reason is that you should have no need to install Synaptic in 10.04. It comes bundled with the OS. Maybe trying to manually install over an existing installation is what messed it up?

---

