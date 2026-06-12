---
title: "Xubuntu to Windows Shared Printer Tips"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by praj.basnet on 2007-02-17
I've finally managed to set up printing between a Xubuntu laptop and a shared Windows printer. So I thought I would shared some advice for everyone else out there.

First place to start is the [**_Debian and Windows Shared printing mini how-to_**]("http://techpubs.sgi.com/library/tpl/cgi-bin/getdoc.cgi?coll=linux&db=HOWTO&fname=/usr/HOWTO/Debian-and-Windows-Shared-Printing.html"). This steps you through the entire process but assumes that you are comfortable with the command line, and understand a bit about linux printing, CUPS and samba. However it is relatively easy to follow along.

A couple of useful additions to this:

A standard Xubuntu installation should have the right packages.

Make sure you can get SMB client to work! My main problem was that the smbclient with just the -L option didn't work (couldn't connect). However with an IP address option it worked. Use the syntax:

```
$ smbclient -I 111.222.333.444 -L hostname -U username
```

If you can't get past this, then you have issues with your file sharing/network/firewall etc. Get this sorted out first.

You can create the printer using Settings > Printing menu in Xubuntu (Xfce) rather than with the command line - this gives you more options and the ability to print a test page.

The steps for this are:

[LIST=1]
[*]Select New Printer
[*]Enter a printer name, description and location
[*]Choose Windows Printer via SAMBA for devices
[*]In the smb:// input box, enter the IP address/Printer_Share_Name. This is the IP address of the Windows computer with the shared printer (obviously make sure your printer is shared correctly and that you have appropriate permissions).
[*]Enter your username and password in authentication and choose verify
[*]Make sure verify is successful, if not, check your printer sharing, security, network, firewall etc.
[*]Choose an appropriate printer driver. See the [OpenPrinting]("http://openprinting.org/printer_list.cgi") website if you need help selecting an appropriate driver.
[*]Apply the settings and create the printer
[/LIST]

Now you are ready to test the printer. Before you do this, open a terminal window. Select print test page, then enter the command to watch the cups error log:

```
$ sudo tail /var/log/cups/error_log
```

If you see errors in here, then you need to go back through the configuration. If you get a unable to connect to CIFS host error, make sure that you entered the IP address and not the hostname of the Windows machine with the shared printer in the CUPS printer configuration.

Hope this helps you out.

---

### Post by osviweb on 2007-07-11
Hallo I'm a total newbie in Xubuntu and linux. I've managed to install the OS and use it a bit. Now I'm stucked in the INSTALLATION OF NETWORK PRINTER (HPLASERJET) SHARED BY WINDOWS 2K . The printer is phisically connected to the 2k via usb and shared by windows on 192.168.0.2

I've tried all the possible solutions found in the documentation and forum (italian forum and di d not find any solution) , I really hope this post may help.

Fist problem in my xubuntu I do not have the option add new printer in Settings > Printing menu in Xubuntu. I just have an interface which let me chose CUPS or nothing :-|

I've found in some posts that CUPS can be used via browser but the admin part of this ask me for a password and gets more complicated of how I can do.. (tried all my passwords)

I think this is something simple but I'm veru confused on what I should do..?

thanks so much for help

---

