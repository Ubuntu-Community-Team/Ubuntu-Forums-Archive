---
title: "Unmet Dependencies, Broken Package Catalog, Cannot Install anything."
date: 2013-03-31
forum: New to Ubuntu
---

### Post by thatstheway on 2013-03-31
I installed 12.04 a few days ago. Recently Update Manager kicked into  action and suggested a few updates, and I installed them all without a  hitch, except for "[COLOR=#000000][FONT=Arial]Linux  kernel image for version 3.5.0 on 32 bit X86 SMP"  (linux-image-3.5.0-26-generic). I tried to install this a few times and  got errors. I'm afraid I didn't capture them but they had to do with  "unmet dependencies."
[/FONT][/COLOR]
Then I read the description of the update and it says: 

You likely do not want to install this package directly. Instead,  install the linux-generic meta-package, which will ensure that upgrades  work correctly, and that supporting packages are also installed.

However it's too late, because now I can't install anything. 

Also, I tried removing it with apt, and was told it wasn't there to remove. 

Related: When I visit the Software Center, I get: 

Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now? 

And when I click Repair I get: 

Package Operation Failed

Details:
Unpacking linux-image-3.5.0-26-generic (from .../linux-image-3.5.0-26-generic_3.5.0-26.42~precise1_i386.deb) ... 
This kernel does not support a non-PAE CPU. 
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-26-generic_3.5.0-26.42~precise1_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-3.5.0-26-generic_3.5.0-26.42~precise1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal: 
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-26-generic; however: 
  Package linux-image-3.5.0-26-generic is not installed. 
dpkg: error processing linux-image-generic-lts-quantal (--configure): 
 dependency problems - leaving unconfigured 

How to proceed? Thanks!

---

### Post by AlecJ on 2013-03-31
[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

---

### Post by thatstheway on 2013-03-31
Thanks AlecJ, I actually saw that, and after trying a few things unsuccessfully tried posting here.  Ok, going through this again slowly:

**On "sudo apt-get -f install," I get:**
[COLOR=#000000][FONT=Arial]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Correcting dependencies... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The following extra packages will be installed:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  linux-image-3.5.0-26-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Suggested packages:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  fdutils linux-lts-quantal-doc-3.5.0 linux-lts-quantal-source-3.5.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  linux-lts-quantal-tools[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The following NEW packages will be installed:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  linux-image-3.5.0-26-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1 not fully installed or removed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Need to get 40.1 MB of archives.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]After this operation, 118 MB of additional disk space will be used.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Do you want to continue [Y/n]? y[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.5.0-26-generic i386 3.5.0-26.42~precise1 [40.1 MB][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Fetched 40.1 MB in 26s (1,533 kB/s)                                            [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](Reading database ... 188828 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Unpacking linux-image-3.5.0-26-generic (from .../linux-image-3.5.0-26-generic_3.5.0-26.42~precise1_i386.deb) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This kernel does not support a non-PAE CPU.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-26-generic_3.5.0-26.42~precise1_i386.deb (--unpack):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] subprocess new pre-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Examining /etc/kernel/postrm.d .[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] /var/cache/apt/archives/linux-image-3.5.0-26-generic_3.5.0-26.42~precise1_i386.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]

The line about non-PAE baffles me. [Here]("http://ubuntuforums.org/showthread.php?t=2055932")  they talk about 12.04 as a good solution, and that's exactly what I'm  running. It is possible that I don't need, or can't use, this update,  despite Update Manager saying I needed?

**Next I tried to remove the new package with :sudo apt-get remove linux-image-3.5.0-26-generic" and got**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-3.5.0-26-generic is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-quantal : Depends: linux-image-3.5.0-26-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Very baffled. Any help on troubleshooting this, or next steps, would be most appreciated!

---

### Post by AlecJ on 2013-03-31
There must be a problem with the repository's judging by the amount of posts here about this.
I think I would leave this a day or so and try again?

---

### Post by thatstheway on 2013-03-31
SOLVED!!!! : ) AlecJ, you got me thinking about repositories, so I tried the steps below from the above Ask Ubuntu link, which worked. After that all I did was go to the software center, click Repair  (Broken Package Catalogs), and a few seconds later all was well and the  system notifications disappeared from the desktop menu.

Here are the steps with slight annotations:

[h=1]Selecting a better server to download from[/h]  Hit Alt F2 to run a command in the dash. 

Type gksu software-properties-gtk and you'll get this window

  [IMG]http://i.stack.imgur.com/VLGND.png[/IMG]
  
Click the Download from the Dropdown box and select other

  [IMG]http://i.stack.imgur.com/a8X7X.png[/IMG]
  
Click Select Best Server

  [IMG]http://i.stack.imgur.com/mS3an.png[/IMG]

When you click Best Server, it actually runs a series of tests to see which one would be best for you.  I'm on the west coast of California in the US, and ended up with a  server in Europe.

---

