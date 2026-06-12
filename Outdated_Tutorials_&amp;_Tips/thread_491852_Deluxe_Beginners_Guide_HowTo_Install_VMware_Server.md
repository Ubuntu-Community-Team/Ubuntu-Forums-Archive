---
title: "Deluxe Beginners Guide HowTo: Install VMware Server in Ubuntu 7.04"
date: 2007-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by davescafe on 2007-07-04
[SIZE=4]**Install VMware Server in Ubuntu 7.04**[/SIZE]

[SIZE=4]** Introduction**[/SIZE]
VMware is a virtualization product that, among other things, will allow you to run a complete installation of Windows at the same time you are running Linux. VMware server is a cost-free product that allows you to run multiple, virtual machines, in isolation, on the same physical piece of hardware. Each virtual machine has its own set of virtual hardware (e.g., RAM, CPU, NIC, etc.) upon which an operating system and applications are loaded. These virtual machines (called &#8220;guests&#8221;) are encapsulated into files, making it possible to rapidly save, and copy them to other host computers. Users must register with VMware to obtain VMware Server license key, but there is no cost for registration or download.

[SIZE=4]** VMware Server (Formerly VMware GSX Server)**[/SIZE]
VMware Server can create, edit, and play virtual machines. It uses a client-server model, allowing remote access to virtual machines, at the cost of some graphical performance (and 3D support). In addition to the ability to run virtual machines created by other VMware products, it can also run virtual machines created by Microsoft Virtual PC.  Users of VMware Server's internal utilities can preserve (and revert to) a single snapshot copy of each separate virtual machine within their VMware Server environment. More info: [http://en.wikipedia.org/wiki/VMware_Server](http://en.wikipedia.org/wiki/VMware_Server)
 
[SIZE=3]** Why choose VMware Server (instead of Player)?**[/SIZE][LIST]
[*]Server can be     used to create new virtual machines. Player cannot create new     virtual machines. Both Server and Player may be used to modify,     update and save changes to existing virtual machines.
[*]Server can     connect to the virtual machines that are hosted on a network.[/LIST][SIZE=3]**Why choose VMware Player (instead of Server)?**[/SIZE][LIST]
[*]Player     incorporates newer technology. VMware Player 2.0 is actually the 6th     generation of VMware virtualization technology, whereas VMware     Server 1.x is from the 5th     generation.[LIST]
[*]VMware         Player supports USB 2.0 devices. VMware Server 1.x only supports         USB 1.x.[/LIST] [/LIST][LIST]
[*]Player is     easier to set-up. No license key is required for Player, although     both the Server and Player products are free-of-charge.
[*]Player allows for drag-and-drop file transfers between the     guest virtual machine and the host machine. This is a very easy way     to move files, and is a significant advantage over the Server     product.[/LIST][SIZE=4]**Before You Begin**[/SIZE]
Before you begin, be sure you have:<ul>VMware Server     installation software[LIST]
[*]VMware Server     installation software[LIST]
[*]May         also be downloaded from: [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)[/LIST] 
[*]VMware Server     Serial Number[LIST]
[*]These         may be obtained by free registration at: [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)[/LIST] [/LIST][SIZE=4]**Installation**[/SIZE][LIST=1]
[*]Prepare your     installation[LIST=1]
[*]Go to the         (Gnome) System (menu) >> Administration >> Synaptic         Package Manager[LIST=1]
[*]Select and             install the following:[LIST=1]
[*]build-essential
[*]vmware-server-kernel-modules
[*]xinetd[/LIST] [/LIST] [/LIST] 
[*]Extract the     VMware Server installation files[LIST=1]
[*]At a terminal, enter the following command:
```
tar zxvf Vmware-server-1.0.3-44356.tar.gz
```[LIST=1]
[*]Please note that the actual VMware file name you download may not match exactly the name listed above. You may have an updated version. If you do, merely replace the name listed above with the name of the file you have[/LIST] [/LIST] 
[*]Change     directories into the one you just extracted[LIST=1]
[*]Change     directories into the one you just extracted[LIST=1]
[*]At         a terminal, enter the following command:
```
cd vmware-server-distrib
```[/LIST] [/LIST] 
[*]Launch the     install[LIST=1]
[*]At         a terminal, enter the following command
```
sudo ./vmware-install.pl
```[/LIST] 
[*]Once     the install script is complete, you will be asked whether you would     like to automatically run the VMware config script. Select &#8220;yes&#8221;.[LIST=1]
[*]If         you miss this opportunity, it is easy to launch the config script         again. Just go to a terminal and type:
```
sudo vmware-config.pl
```[/LIST] 
[*]The VMware     config script may fail for Ubuntu 7.04 users. To work around this     problem, apply the &#8220;any-any update&#8221;[LIST=1]
[*]Get         the any-any update (vmware-any-any-update110.tar.gz) from:         [http://platan.vc.cvut.cz/ftp/pub/vmware/](http://platan.vc.cvut.cz/ftp/pub/vmware/)
[*]Extract the         any-any update by going to a terminal window and entering this         command:
```
tar zxvf vmware-any-any-update110.tar.gz
```[LIST=1]
[*]Change             directories into this folder by entering the following command at             a terminal:
```
cd vmware-any-any-update110
```
[*]Run the             update script
```
sudo ./runme.pl
```[/LIST] [/LIST] 
[*]You can     accept all defaults[LIST=1]
[*]The only         thing you might want to alter is the directory where the Virtual         Machines are stored. You may prefer to set it to:         /home/<my_username>/vmware[/LIST] 
[*]Create     Application Shortcut[LIST=1]
[*]The any-any         update script does not create an application shortcut, so you must         create it manually.
[*]Go to the         Gnome System menu >> Preferences >> Main Menu[LIST=1]
[*]Click the             &#8220;New Item&#8221; button[LIST=1]
[*]Name:                 VMware Server Console
[*]Command:                 /usr/bin/vmware
[*]Set Icon &#8211;                 click the button[LIST=1]
[*]by                     default you are placed in the /usr/share/pixmaps directory.                     Scroll to the bottom of the list and select &#8220;vmware-server.png&#8221;[/LIST] [/LIST] [/LIST] [/LIST] [/LIST]**[B][SIZE=4]Launching VMware Server[/SIZE]**[/B][LIST=1]
[*]The VMware Server Console may be launched by going to the Gnome Applications     menu >> System Tools >> VMware Server Console
[*]You will be     greeted with a Switch Host dialog. Select &#8220;Local host&#8221; and     click, &#8220;Connect&#8221;[/LIST][B][SIZE=4][B]Steps and Tips for Creating New Virtual Machines
[/B][/SIZE][/B][LIST=1]
[*]Start VMware Server             Console:
Gnome Applications menu >> System Tools >>             VMware Server Console[LIST=1]
[*]Connect to &#8220;Local host&#8221;[/LIST] 
[*]Click the button named, &#8220;Create             a new virtual machine&#8221; to start the &#8220;New Virtual Machine             Wizard&#8221;
[*]Select a typical install
[*]Select your operating system             type and provide a name for your new virtual machine
[*]Disk Size[LIST=1]
[*]Un-check: &#8220;Allocate all disk                 space now&#8221;
[*]You may want to allocate more                 than 8GB (which is the default value)[/LIST] 
[*]Before installing your new,             virtual machine, you may add extra virtual hardware if desired[LIST=1]
[*]Sound Card[LIST=1]
[*]VM (menu) >> Settings[LIST=1]
[*]In the &#8220;Hardware&#8221; field,                         click the Add button
[*]Add a Sound Adapter (auto                         detected)[/LIST] [/LIST] 
[*]USB Controller[LIST=1]
[*]VM (menu) >> Settings[LIST=1]
[*]In the &#8220;Hardware&#8221; field,                         click the Add button
[*]Add the USB Controller[LIST=1]
[*]To connect a USB device to a                             virtual machine, first power on the virtual machine and then                             select the device in the VM >> Removable Devices >>                             USB Devices menu.[/LIST] [/LIST] [/LIST] [/LIST] 
[*]Put a bootable operating system             install CD-ROM in the drive and click the button named, &#8220;Power             on this virtual machine&#8221;[LIST=1]
[*]Alternately, you can edit the                 machine specifics and point the CD-ROM drive to an ISO image.[LIST=1]
[*]Click, &#8220;Edit virtual machine                     settings&#8221;
[*]Select the CD-ROM drive from                     the hardware device list
[*]Select &#8220;Use ISO image:&#8221;                     and browse to your bootable ISO image.[LIST=1]
[*]Note: if your image ends with                         .ISO (in all capital letters), it may not be found unless you                         select &#8220;all files&#8221; from the Browse drop-down file type                         menu.[/LIST] [/LIST] [/LIST] 
[*]After installation of your             virtual machine is complete, be sure to install VMware tools, by             going to the &#8220;VM&#8221; menu and selecting, &#8220;Install VMware             Tools...&#8221;[LIST=1]
[*]IMPORTANT: Install VMware tools                 *before* Windows activation[LIST=1]
[*]VMware tools installs new                     virtual hardware including a video card. Windows only allows a                     limited number of hardware changes before requiring you to                     re-activate, so don&#8217;t let the VMware tools install count                     against that number.[/LIST] [/LIST] 
[*]If you install Windows in a             virtual machine, you can use Samba to connect your virtual machine             to Linux.
[*]Open Device Manager and verify             all devices are working[LIST=1]
[*]Windows Vista virtual machines                 don&#8217;t recognize the sound card installed by VMware. This may be                 easily fixed by[/LIST] 
[*]Defrag the Windows operating             system[LIST=1]
[*]In Windows XP, go to Start >>                 All Programs >> Accessories >> System Tools >>                 Disk Defragmenter
[*]In Windows Vista, right-click                 on the command prompt window and select the option to open as                 Administrator. Then enter the following command
```
defrag c: -v -w
```
[*]Defragging is unnecessary for                 most Linux file systems[/LIST] 
[*]When the OS defrag is complete,             shut-down the virtual machine.
[*]IMPORTANT: Defrag the Virtual             Machine (this is different than defragging the OS)[LIST=1]
[*]Go to the VM menu >>                 Settings
[*]Select &#8220;Hard Disk&#8221; from the                 device listing
[*]Click the button named,                 &#8220;Defragment&#8221;[/LIST] 
[*]If you ever move or rename the             virtual machine files, you may be prompted to keep or create a new             UUID the next time you launch the virtual machine.[LIST=1]
[*]For Windows Vista virtual                 machines &#8211; It is essential that you &#8220;Keep&#8221; or &#8220;Always                 Keep&#8221; your UUID. If you do not, you may have to re-active your                 installation of Vista.
[*]For Windows XP virtual machines                 &#8211; I prefer to &#8220;Create Always,&#8221; although for specific                 situations, it may be preferable to keep the UUID in XP.[/LIST] [/LIST]**[SIZE=4][B]Common VMware Hot Keys and Tips**[/SIZE][/B][LIST]
[*]<Ctrl> + <Alt> will     release the mouse cursor from the virtual machine.
[*]<Ctrl> + <Alt> +     <Enter> will enter full-screen mode.
[*]<Ctrl> + <Alt> in     full-screen mode will get you back to windowed mode.
[*]You can Suspend a running virtual     machine. this way it will start very fast the next time you need it.[/LIST]**[SIZE=4][B]Troubleshooting**[/SIZE][/B]
If the server console doesn&#8217;t come up[LIST=1]
[*]Start the terminal and execute
```
vmware
```or
```
sudo vmware
```
[*]Try re-configuring using the             following command at a terminal:
```
sudo /usr/bin/vmware-config.pl
```[/LIST]

---

### Post by frodon on 2007-07-04
I still prefer using VirtualBox which as much powerful, fully free and easier to use, full guide here :
[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by reclusivemonkey on 2007-07-04
No offence to your excellent guide dude, but I did this from the following link last night, and it was considerably easier :-S

[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

---

### Post by Merritt.kr on 2007-07-25
Well, I followed your guide and it worked perfectly. I now have a VM of Windows XP on my Kubuntu box. Will be very useful for troubleshooting my customers that still use Windows! Thank-you!

---

### Post by gg234 on 2007-07-26
here is [simple vmware server installation  guide ]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")from ubuntu packages

---

### Post by mpm on 2008-11-15
Step 10.1 how to activate the sound card in a Vista guest is not complete.  I got rather excited when I saw it, but was let down.  Vista x64 guest in Ubuntu 8.4 64 bit host.

---

