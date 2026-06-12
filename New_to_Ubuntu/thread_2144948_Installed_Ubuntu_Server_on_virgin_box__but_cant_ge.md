---
title: "Installed Ubuntu Server on virgin box  but cant get network connection"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by tominva on 2013-05-13
New to Linux
Built a server box and Installed ubuntu server 12.04
 Installed OS from USB stick (no optical drive)
  During install setup could not make an automatic network connection. ( I don't know how to manually configure)
   I continued with the rest of the install.

ifconfig shows ports eth0 and virbr0

Could the reason there's no network connection is that I need to load drivers from the CD that came with the new motherboard?
 
 Is so can I copy the disc to the USB stick and install from it?  

What are the commands I need to do this or where can I find them?

Thanks

---

### Post by squakie on 2013-05-13
No, you can't install the Windows drivers like that - they are 2 entirely different animals.  If worse comes to worse, ndiswrapper and ndisgtk are still available, but shy away from those if you can as Ubuntu has more and more drivers with each release.

Chances are that you will need to configure your network - either through the interfaces file, or perhaps some combination of ifconfig from the command line.

---

### Post by tominva on 2013-05-14
Ok I found the correct drivers but no having luck getting them loaded.  Folowing [http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

But when I use this command 

[COLOR=#C20CB9]**tar**[/COLOR][COLOR=#110000] [/COLOR][COLOR=#660033]-xvjf[/COLOR][COLOR=#110000] r8168-8.035.00.tar.bz2 
[/COLOR]
it says can not open file not found.  [COLOR=#110000]r8168-8.035.00.tar is the driver i downloaded.[/COLOR]

---

### Post by 3rdalbum on 2013-05-14
You probably already have a driver preinstalled, you just need to set up your connection.

I don't know how to do this on the command line.

Since you are obviously new to Linux, why not install the Desktop version and run your server box on that? The Server version is basically the Desktop version, minus the desktop.

You will be able to learn the command-line if you want, but from within a window on the desktop.

I would strongly recommend installing yhr Desktop version, even for a server, if you are new.

---

### Post by tominva on 2013-05-14
The driver are not pre installed for some reason see this link.
[http://www.twm-kd.com/linux/realtek-...-ubuntu-linux/]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/")

When I use [COLOR=#110000] [/COLOR][COLOR=#C20CB9]**tar**[/COLOR][COLOR=#110000] [/COLOR][COLOR=#660033]-xvjf[/COLOR][COLOR=#110000]0.tar.bz2
[/COLOR]
I get  'can not open file not found'

File [COLOR=#110000] r8168-8.035.00.tar[/COLOR] is on the usb stick.

---

### Post by steeldriver on 2013-05-14
in that case, you are probably not executing the tar command from the directory that contains the file - try copying the file to your home dir first (unfortunately I don't think the Server edition automounts USB storage devices though so that's not as easy as it sounds)

---

### Post by 3rdalbum on 2013-05-14
Tominva, the link you posted to says that the driver works out-of-the-box on Ubuntu 12.04. Odds are that manually installing the driver will do nothing useful.

Can you at least try the Ubuntu Desktop image? If I'm right, your system will automatically get a connection on the 12.04 desktop Live USB.

---

