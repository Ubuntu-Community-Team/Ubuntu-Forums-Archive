---
title: "Core System Folders"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by CYNIST on 2008-11-13
Question 1:  When I'm looking at all the core folders the OS installs how do I know what types of data goes in each folder?  Is there a list or general guideline?

Question 2:  How do I locate an internal cd-rom drive from the terminal and then copy something from a cd to a file?

---

### Post by lincoln32 on 2008-11-13
what verion of ubuntu are you using?

---

### Post by CYNIST on 2008-11-13
8.1 server.  Nothing like learning the hard way!  I just installed it a few days ago and I am working my way through the posted manual.  My ultimate goal is to get the server set up and then try to network a Ubuntu 8.1 client and windows xp client.

---

### Post by lincoln32 on 2008-11-13
I tried the same but found too hard for me to line by line commands and so Installed gnome desktop so I could find and setup. since i swapped to clark connect but cannot remember line commands had a cheat sheet i will look for it and get back to you

---

### Post by CYNIST on 2008-11-13
I figured out question 2 of how to mount my cdrom drives.  But for some reason I can't mount the floppy drive.  Yes it's an old computer.  I tried mount /dev/fd0 and fd1 but it can't find it.

---

### Post by lincoln32 on 2008-11-13
here is a basic cheat sheet I found if you need more let me know and you can down load the sheet from fosswire.com
 Ubuntu Reference
                          Privileges                                                             Network
sudo command – run command as root                                 ifconfig – show network information
sudo -s – open a root shell                                        iwconfig – show wireless information
sudo -s -u user – open a shell as user                             sudo iwlist scan – scan for wireless networks
sudo -k – forget sudo passwords                                    sudo /etc/init.d/networking restart – reset
gksudo command – visual sudo dialog (GNOME)                        network for manual configurations
kdesudo command – visual sudo dialog (KDE)                         (file) /etc/network/interfaces – manual
sudo visudo – edit /etc/sudoers                                    configuration
gksudo nautilus – root file manager (GNOME)                        ifup interface – bring interface online
kdesudo konqueror – root file manager (KDE)                        ifdown interface – disable interface
passwd – change your password
                                                                                          Special Packages
                                                                   ubuntu-desktop – standard Ubuntu environment
                           Display
sudo /etc/init.d/gdm restart – restart X and                       kubuntu-desktop – KDE desktop
return to login (GNOME)                                            xubuntu-desktop – XFCE desktop
sudo /etc/init.d/kdm restart – restart X and                       ubuntu-minimal – core Ubuntu utilities
return to login (KDE)                                              ubuntu-standard – standard Ubuntu utilities
(file) /etc/X11/xorg.conf – display                                ubuntu-restricted-extras – non-free, but useful
configuration                                                      kubuntu-restricted-extras – KDE of the above
sudo dexconf – reset xorg.conf configuration                       xubuntu-restricted-extras – XFCE of the above
Ctrl+Alt+Bksp – restart X display if frozen                        build-essential – packages used to compile
Ctrl+Alt+FN – switch to tty N                                      programs
Ctrl+Alt+F7 – switch back to X display                             linux-image-generic – latest generic kernel
                                                                   image
                                                                   linux-headers-generic – latest build headers
                    System Services1
start service – start job service (Upstart)
stop service – stop job service (Upstart)                                                       Firewall1
status service – check if service is running                       ufw enable – turn on the firewall
(Upstart)                                                          ufw disable – turn off the firewall
/etc/init.d/service start – start service                          ufw default allow – allow all connections by
(SysV)                                                             default
/etc/init.d/service stop – stop service (SysV)                     ufw default deny – drop all connections by
/etc/init.d/service status – check service                         default
(SysV)                                                             ufw status – current status and rules
/etc/init.d/service restart – restart service                      ufw allow port – allow traffic on port
(SysV)                                                             ufw deny port – block port
runlevel – get current runlevel                                    ufw deny from ip – block ip adress
                 Package Management1                                                     Application Names
apt-get update – refresh available updates                         nautilus – file manager (GNOME)
apt-get upgrade – upgrade all packages                             dolphin – file manager (KDE)
apt-get dist-upgrade – upgrade with package                        konqueror – web browser (KDE)
replacements; upgrade Ubuntu version                               kate – text editor (KDE)
apt-get install pkg – install pkg                                  gedit – text editor (GNOME)
apt-get purge pkg – uninstall pkg
apt-get autoremove – remove obsolete packages                                                    System
apt-get -f install – try to fix broken packages                    Recovery - Type the phrase “REISUB” while
dpkg --configure -a – try to fix broken                            holding down Alt and SysRq (PrintScrn) with
packages                                                           about 1 second between each letter. Your system
dpkg -i pkg.deb – install file pkg.deb                             will reboot.
(file) /etc/apt/sources.list – APT repository                      lsb_release -a – get Ubuntu version
list                                                               uname -r – get kernel version
                                                                   uname -a – get all kernel information
1. Prefix commands with sudo to run.
Ubuntu is a trademark of Canonical Ltd. Licensed under CC-BY-SA 3.0. Free to redistribute; see creativecommons.org for details.
me know

---

### Post by CYNIST on 2008-11-13
> **lincoln32 said:**
> I tried the same but found too hard for me to line by line commands and so Installed gnome desktop so I could find and setup. 

Thanks for the response.  I to find it a little hard but not enough to discourage me.  I get to learn this at work so what could be better than getting paid to learn Linux!  I'm so tired of micro$oft.  I have the desktop version installed at home to help me understand better through the gui.

---

### Post by lincoln32 on 2008-11-13
try            mount /media/cdrom0
then cd/cdrom0 to access but there may be someone out there better at this than me

---

### Post by lincoln32 on 2008-11-13
I found it better to install a GUI gnome to get it up and working found a post on it and worked well. and after 5 months on ubuntu I think it is way better than m/s bloatware

---

### Post by CYNIST on 2008-11-14
Thanks for the tips.

Yes, it would be easier but everything I read says it's less secure.  I'm the administrator at a correctional facility and secure is good!  Plus, I think I would miss out on a lot of knowledge by not keeping my server terminal.  I've already learned so much in the last week!  I think this forum is key.  It makes me feel like I'm not climbing a mountain alone.  I'd still like to get a basic laymen's summary of what types of files goes in the all of the root directories at install.  It would help me (as a prior :)micro$oft guy) to departmentalize Linux's logical file structure.

---

### Post by CYNIST on 2008-12-24
I found a listing of the system folder uses.  There is fantastic free Linux training on the HP website.  It uses Fedora as its examples but so far everything applies to ubuntu.

Here is what I was looking for.  Hope this may help other newbies like me!

 The most important subdirectories inside the root directory are:

    * /bin: Important Linux commands available to the average user.
    * /boot: The files necessary for the system to boot. Not all Linux distributions use this one. Fedora 7 does.
    * /dev: All device drivers. Device drivers are the files that your Linux system uses to talk to your hardware. For example, there's a file in the /dev directory for your particular make and model of monitor, and all of your Linux computer's communications with the monitor go through that file.
    * /etc: System configuration files.
    * /home: Every user except root gets her own folder in here, named for her login account. So, the user who logs in with linda has the directory /home/linda, where all of her personal files are kept.
    * /lib: System libraries. Libraries are just bunches of programming code that the programs on your system use to get things done.
    * /media: When you temporarily load the contents of a CD-ROM or USB (universal serial bus) drive, you usually use a special name under /media. For example, many distributions (including Fedora) come, by default, with a directory such as /media/cdrom, which is where your CD-ROM drive's contents are made accessible.
    * /mnt: Permanent mount points -- those that aren't used for removable media, such as CD-ROMs. If your system administrator attaches a drive over the network for your backups, it may be placed under this location.
    * /opt: Where some additional software is installed.
    * /proc: A directory tree used by your kernel -- don't mess with this.
    * /root: The root user's home directory.
    * /sbin: Essential commands that are only for the system administrator.
    * /sys: A directory related to /proc -- again, don't mess with this.
    * /tmp: Temporary files and storage space. Don't put anything in here that you want to keep. Most Linux distributions (including Fedora) are set up to delete any file that's been in this directory longer than three days.
    * /usr: Programs and data that can be shared across many systems and don't need to be changed.
    * /var: Data that changes constantly (such as log files that contain information about what's happening on your system, data on its way to the printer, and so on).

---

### Post by snova on 2008-12-24
Filesystem Hierarchy Standard: [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

Not totally respected, but a good guide.

---

### Post by CYNIST on 2008-12-31
Thanks for the link.  This is exactly what I was looking for.

---

