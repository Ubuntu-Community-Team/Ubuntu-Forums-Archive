---
title: "Some Helpfull Command Lines."
date: 2008-10-18
forum: New to Ubuntu
---

### Post by cairnzi on 2008-10-18
here is a collection of command lines i have compiled since starting to use ubuntu, no dodgy commands Etc. just helpful and useful one's.

---

### Post by drubin on 2008-10-18
This looks and seems like a very usefully thing to have as a tutorial. It seems nicely set out with headers and things and stuff :). 

It would be must better to write the command as part of the message instead of an attachment this way it is search able and people would not have to download the office document.  Maybe also include the headers and point form like you did in the document. 

I would even go so far as recommending this for a sticky in the ABT forum. or at least part of the [tutorial/tips]("http://ubuntuforums.org/forumdisplay.php?f=100")

---

### Post by cairnzi on 2008-10-18
mmmmm..... thought four pages long would be to long for a post? then again it is a good idea mate :)

_Ubuntu Commands._

sudo apt-get update = update all. 

sudo apt-get upgrade = program update. 

apt-cache search ????? = search for app. 

sudo apt-get install ????? = install app. 

sudo apt-get remove ????? = remove app. 

apt-get help = help menu. 

man sudo_root = root command help. 

sudo -i = root user. 

sudo apt-get autoremove = clean junk files 

sudo apt-get autoclean = as above. 

localepurge = purge residual files (root). 

sudo sh ~/desktop/????? .run = run desktop app/file. 

deborphan = delete orphaned files. 

sudo deborphan | xargs sudo apt-get -y remove --purge = as 

above but all. 

sudo rm -rfvI ~/.local/share/Trash/files/ = remove all files in trash. 

sudo command - run command as root 

sudo su - open a root shell 

sudo su user - open a shell as user 

sudo -k - forget sudo passwords 

gksudo command - visual sudo dialog (GNOME) 

kdesudo command - visual sudo dialog (KDE) 

sudo visudo - edit /etc/sudoers 

gksudo nautilus - root file manager (GNOME) 

kdesudo konqueror - root file manager (KDE) 

passwd - change your password 


_Display_ 

sudo /etc/init.d/gdm restart - restart X (GNOME) 

sudo /etc/init.d/kdm restart - restart X (KDE) 

(file) /etc/X11/xorg.conf - display configuration 

sudo dpkg-reconfigure -phigh xserver-xorg - reset X configuration 

Ctrl+Alt+Bksp - restart X display if frozen 

Ctrl+Alt+FN - switch to tty N 

Ctrl+Alt+F7 - switch back to X display 


_System Services¹_ 

start service - start job service (Upstart) 

stop service - stop job service (Upstart) 

status service - check if service is running (Upstart) 

/etc/init.d/service start - start service (SysV) 

/etc/init.d/service stop - stop service (SysV) 

/etc/init.d/service status - check service (SysV) 

/etc/init.d/service restart - restart service (SysV) 

runlevel - get current runlevel 

_Package Management¹_ 

apt-get update - refresh available updates 

apt-get upgrade - upgrade all packages 

apt-get dist-upgrade - upgrade Ubuntu version 

apt-get install pkg - install pkg 

apt-get remove pkg - uninstall pkg 

apt-get autoremove - remove obsolete packages 

apt-get -f install - try to fix broken packages 

dpkg &#8211;configure -a - try to fix broken packages 

dpkg -i pkg.deb - install file pkg.deb 

(file) /etc/apt/sources.list - APT repository list 

_Network_ 

ifconfig - show network information 

iwconfig - show wireless information 

sudo iwlist scan - scan for wireless networks 

sudo /etc/init.d/networking restart - reset network 

(file) /etc/network/interfaces - manual configuration 

ifup interface - bring interface online 

ifdown interface - disable interface 

_Special Packages._

ubuntu-desktop - standard Ubuntu environment 

kubuntu-desktop - KDE desktop 

xubuntu-desktop - XFCE desktop 

ubuntu-minimal - core Ubuntu utilities 

ubuntu-standard - standard Ubuntu utilities 

ubuntu-restricted-extras - non-free, but useful 

kubuntu-restricted-extras - KDE of the above 

xubuntu-restricted-extras - XFCE of the above 

build-essential - packages used to compile programs 

linux-image-generic - latest generic kernel image 

linux-headers-generic - latest build headers 

_Firewall¹_ 

ufw enable - turn on the firewall 

ufw disable - turn off the firewall 

ufw default allow - allow all connections by default 

ufw default deny - drop all connections by default 

ufw status - current status and rules 

ufw allow port - allow traffic on port 

ufw deny port - block port 

ufw deny from ip - block ip adress 

_Application Names_ 

nautilus - file manager (GNOME) 

dolphin - file manager (KDE) 

konqueror - web browser/filemanager (KDE) 

kate - text editor (KDE) 

gedit - text editor (GNOME)

---

