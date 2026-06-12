---
title: "Trying to install a printer"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Taadaa on 2008-11-27
I'm trying to install a Brother MFC-5460CN printer. It's on my network and when I try to print to it, the LCD screen on the printer lights up saying it's receiving data but nothing happens.

Went to the Brother site and downloaded their deb package for this printer and went through the installation of the package. Then when it came time to choose the printer driver from the list, it wasn't there. Back to the Brother site and followed their linux installation instructions. This is what I did and what I got:

carolyn@carolyn-Linux:~$ sudo aa-complain cupsd
sudo: unable to resolve host carolyn-Linux
[sudo] password for carolyn:
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
carolyn@carolyn-Linux:~$ sudo mkdir /usr/share/cups/model
sudo: unable to resolve host carolyn-Linux
mkdir: cannot create directory `/usr/share/cups/model': File exists
carolyn@carolyn-Linux:~$ in -s /etc/init.d/cupsys /etc/init.d/lpd
bash: syntax error near unexpected token `in'
carolyn@carolyn-Linux:~$ In -s /etc/init.d/cupsys /etc/init.d/lpd
bash: In: command not found
carolyn@carolyn-Linux:~$ cd /var/spool/lpd
bash: cd: /var/spool/lpd: No such file or directory
carolyn@carolyn-Linux:~$ cd var
bash: cd: var: No such file or directory
carolyn@carolyn-Linux:~$ cd /
carolyn@carolyn-Linux:/$ cd /var
carolyn@carolyn-Linux:/var$ cd spool
carolyn@carolyn-Linux:/var/spool$ cd lpd
bash: cd: lpd: No such file or directory
carolyn@carolyn-Linux:/var/spool$ mkdir lpd
mkdir: cannot create directory `lpd': Permission denied

To my knowledge, I am logged in as administrator but it apparently won't let me create directly lpd which it seems, I need. Any ideas??

---

### Post by Barriehie on 2008-11-27
When I'm logged in as admin my prompt changes from a $ to a #.   

Barrie

---

### Post by Taadaa on 2008-11-27
It asked me for the password and I typed it in.  I don't know how to "log in" at the terminal as supervisor, sorry?  Can you tell me?  I have a book on Ubuntu coming in at the library so I won't always appear so stupid

Thanks

---

### Post by Barriehie on 2008-11-27
Not a stupid thing! :-)  Does the printer show up if you go to System / Administration / Printing???

Next time you get to a terminal try **sudo su** and that should log you in as **s**uper**u**ser.  See then if you can make the dir.  

BTW: after logging in with sudo su entering 'exit' (without the ') will log you out of su mode.

Barrie

---

### Post by plucky on 2008-11-28
> carolyn@carolyn-Linux:/var/spool$ mkdir lpd
mkdir: cannot create directory `lpd': Permission denied

You still need to use **sudo** with the command so the system knows to use super user mode.

If you are using Hardy or Intrepid,the Brother printer drivers are packaged in the **Synaptic Package Manager**.Search for your printer name and install both the LPR and Cupswrapper drivers and then see if Cups can see your printer on the network.

If not then use the documented procedure on the Brother website for installing a Network printer,making sure you don't miss any of the steps.


Good Luck

---

