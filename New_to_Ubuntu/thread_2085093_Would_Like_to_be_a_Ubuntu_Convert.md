---
title: "Would Like to be a Ubuntu Convert"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by OceanBitz on 2012-11-17
Long time Windows user and programmer trying to make the change but still lost in the syntax. What I want to do, and Netbootin appears the answer, is take an USB external hard drive, create a boot sector (in your language) and in one partition a Ubuntu OS. My Windows computer is set to boot from the USB first. When I cold boot I should then see the new os displayed. From the UNetbooin main window I assume I should either "Select Distribution" or have downloaded an iso. The choices under the "Select Distribution" of Ubuntu confuse me (I am sorry I need such hand holding). I do not believe I want something from which an installer can be launched - I want the OS installed. I hope somebody is willing to walk an old Windows user into the new world or point me to the correct tutorial (I have read dozens but simply do not know enought to select the one appropriate).
Ed

---

### Post by zombifier25 on 2012-11-17
Have you downloaded the .iso image from Ubuntu's download page? If so, no need to choose "Choose Distribution", simply tell UNetBootin to use the .iso file, and then proceed to write it to a USB disk.

If you need help with the actual installation, you should post.

---

### Post by newb85 on 2012-11-17
As I understand it, you want a traditional install, not simply a Live USB with persistence.  Provided your external drive is not solid state, that's probably the better approach.

Unetbootin will not directly create a traditional install.  It creates Live media (USB/CD/DVD).

In order to do a traditional install, you need to create a Live USB/CD/DVD that is separate from the external HDD where you want the traditional install.  Then, boot from the Live media, attach the external HDD, run the installer, and select the external HDD as the destination drive.

---

### Post by OceanBitz on 2012-11-17
Newby85 you read me load and clear.  So what I want is a traditional install and would not be solid state..  So how do I create  Live  "one"?  I have cability to place on a 7GB memory stick or create a CD.  I could even put on another external conventional HD (I keep old HD's and have a exernal transformer and USB cables).  Once that is done then I gather there is an "installer" choice where I can select my final destination on an external.
 
Ed

---

### Post by holiday on 2012-11-17
For trying out distros, I use VirtualBox.

VirtualBox creates a virtual machine to which you can install the OS from the downloaded iso file. 

Performance is slightly degraded - give it more than the suggested memory - but for most applications, I don't notice a difference. 

When I buy a new PC, with the Windows installation a condition of the warranty,  I'll run it through the warranty period using various flavors of Ubuntu - depending on my mood - using my VirtualBox VMs. This gives me experience with the various distros so that I can choose which one to physically install when the warranty period is over.

And you're not limited to Ubuntu distros. You can try OpenSuse, Fedora, and so on. 

I stick with Ubuntu because I'm familiar with apt-get, but if you don't mind learning the installation procedures of other distros, you could sample Linux for a long long time.
]

---

### Post by Paqman on 2012-11-17
You don't need Unetbootin. Simply download the standard Ubuntu image, put it on a USB stick using the instructions on the download page, and install it to your USB disk. Make sure you install the bootloader (Grub) onto the USB disk too, not to your internal disk, or else it won't boot Windows without the USB disk in.

[http://ubuntu.com/download]("http://ubuntu.com/download")

---

### Post by newb85 on 2012-11-17
A 7 GB flash drive is more than sufficient for a Live USB, provided you don't have anything on it.

You will need to install an application in Windows to create a Live USB from the .iso.  I know of three such applications:

[list]
[*] [Pendrivelinux.com]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") (Recommended by the instructions at [help.ubuntu.com]("https://help.ubuntu.com/community/Installation/FromUSBStick")) I've heard the most good about this one.
[*] [linuxliveusb.com]("http://www.linuxliveusb.com/en/download") (Recommended by the instructions at [ubuntu.com/download]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")) I haven't heard any testimonials on this one.
[*][http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) (recommended by several here in the forums) I've heard that it occasionally doesn't work, but if you already have the application installed on your Windows system, you might as well try it, and if it doesn't work, then move on to pendrivelinux.
[/list]

---

### Post by OceanBitz on 2012-11-17
OK guys, think I have enought to go a couple rounds by myself.  Looks like I have been posting on the wrong site since I will not need UNetbootin. So many thanks for steping over the line and helping me get started.  Tough for a guy who started with a IBM PC with one floppy and never been outside Windows once it replaced MS DOS.  When I get a bootable Ubuntu on one of my USB externals I'll have to return and identify the purpose of UNetbootin.
 
Ed

---

