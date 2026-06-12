---
title: "[SOLVED] Printer Setup"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by WilhelmGGW on 2008-07-24
I have this new Dell computer that came with Ubuntu. I have it on a network with a Windows XP machine, set to share its connected printer with other users. Another XP machine on the network prints fine.  But I need help setting my new Ubuntu machine to use the printer, too.

I have searched in all the helps I've found, and tried everything I find there.  But I still can't make it work.  Can someone help me with this, please?  Thanks so much.  -g

---

### Post by GMod on 2008-07-24
I had to tweak my XP firewall to allow my Ubuntu machine to access the printers I have installed. It could be as simple as allowing the Ubuntu machines network address access to the XP machine. 

On a funny note... When I print from my Ubuntu box to any one of my 3 printers (all attached to XP machine) they get printed faster than my XP machine. Dunno why but I'm not complaining

---

### Post by WilhelmGGW on 2008-07-24
This may help. When I go to add a new printer, and choose Windows Printer via SAMBA, I don't know what to put in the SMB Printer box location. If I click on Browse, it scans, then stops with nothing. No available choices.

I have checked my Windows firewall, and I don't think that has anything to do with it.

---

### Post by LowSky on 2008-07-24
Is the printer connected directly to the XP machine or through an ethernet connection?

If its the Computer, you need to share the printer on the network
Network Settings> Right-click on the print and click shre printer.

If on a network type try typing this adress in firefox 
[http://localhost:631/](http://localhost:631/)

you might be able to find the printer and set it up

here is a nice write up about CUPs based printing on a gentoo linux install but it should work no problem
[http://gentoo-wiki.com/Cups](http://gentoo-wiki.com/Cups)

---

### Post by WilhelmGGW on 2008-07-24
> **LowSky said:**
> Is the printer connected directly to the XP machine or through an ethernet connection?

If its the Computer, you need to share the printer on the network
Network Settings> Right-click on the print and click shre printer.

Yes, the printer is connected directly to the XP, which (in turn) is connected to the network.  And the printer on the XP is set for sharing. It took that for my other XP machine on the network to recognize the printer and connect with it fine.

---

### Post by WilhelmGGW on 2008-07-25
Can someone check this out for me, please? I still haven't got my printer to work.  With my latest setup attempt, when I run Troubleshooting from Printer Setup, I get the following message. I don't know enough about all this to tell where to go from here.  Thanks so much.


Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86f9b60>,
 'cups_instance': None,
 'cups_queue': 'HPLaserJet4L',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'file',
 'cups_printer_dict': {'device-uri': u'file:/dev/null',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'dell-desktop',
                       'printer-make-and-model': u'Local Raw Printer',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 131076,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HPLaserJet4L'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(16, u'Job completed.')],
 'test_page_job_id': [16],
 'test_page_job_status': [(16, 'HPLaserJet4L', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by bobnutfield on 2008-07-25
You will probably have to edit your smb.conf file.  But, before trying that, here is a Debian HOWTO which should work fine with Ubuntu:

[http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html]("http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html")

Hope that helps

Bob

---

### Post by WilhelmGGW on 2008-07-25
Yipes! Most of that document is way over my head.  I only got as far as confirming I can connect to the Windows PC with smbclient. Here's that:

[INDENT]Domain=[DELLDESKTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	HPLaserJreg     Printer   HP LaserJet 4L Reg
	HPLaserJecon    Printer   HP LaserJet 4L Econ
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
Domain=[DELLDESKTOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
[/INDENT]

Beyond that, I'm lost. I don't know enough terminology -- and am too afraid to blunder through things I don't understand, at the risk of messing something up.

Can you take me on from here, Bob?  Thanks so much.

---

### Post by bobnutfield on 2008-07-25
OK, go etc/samba/smb.conf.  Open it with a text editor and scroll down to a section that looks like this:

> [printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

For a network printer, you will have to enter the IP address of the host Windows machine, something like this:

> smb://<ipaddress/<name of printer>

As mentioned before, make sure the windows firewall is not blocking your connection.

If you don't know the IP address of the Windows machine, open a command line and type:

> ipconfig

This will tell you the IP address of the windows machine.  Once the correct entry is made in smb://,  you should be able to print.  Post back with any difficulty, but there are a number of threads here on the forum about this topic.  Type in the forum search "print to Windows network host" and you should get a number of threads to peruse.

Bob

Bob

---

### Post by WilhelmGGW on 2008-07-25
Great Help, Bob.  I think we're almost there.

Name of Printer.  Is that the sharename of my above post?  Something like
HPLaserJreg

---

### Post by bobnutfield on 2008-07-25
Yes, whatever it is called when you click on Printers in the Windows control panel.  The smb:// entry may take a couple of tries to get the correct entry.

Going away from the computer for a couple of hours, but I will check back then to see how you are getting on.  Others may jump in to help as well.

---

### Post by WilhelmGGW on 2008-07-25
Bob, my section under printers looks just like what you have here. Then what you wrote about entering the IP for the host, is this something I have to edit into this section on printers, or just use it when I set up printing with Samba?  Thanks for your help.

[INDENT]OK, go etc/samba/smb.conf. Open it with a text editor and scroll down to a section that looks like this:

Quote:
[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = no
read only = yes
create mask = 0700

For a network printer, you will have to enter the IP address of the host Windows machine, something like this:

Quote:
smb://<ipaddress/<name of printer>[/INDENT]

---

### Post by WilhelmGGW on 2008-07-25
All Set.  Mission Accomplished.  Thanks so much, Bob!

---

### Post by bobnutfield on 2008-07-25
My pleasure, great you got it working.

Bob

---

