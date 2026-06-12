---
title: "[SOLVED] Network Printer stopped working"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by WilhelmGGW on 2008-09-08
I have my Ubuntu machine set to print documents via a home network, print on an HP printer connected to my Windows machine on the same network. I set this up a couple of months ago and everything worked splendidly till just now -- and I can't seem to get the printer to work now from this Ubuntu machine.

I went away for a few days and shut down both computers and my network. When I got back I started the network, then the Ubuntu machine, then the Windows. The Windows machine prints fine, as does another Windows machine on the same network. But this Ubuntu machine does not.

Below is the diagnosis of the print troubleshooter. Thanks for your help.

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8716260>,
 'cups_instance': None,
 'cups_queue': 'LaserJet_4L_Econ',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb:///192.168.1.101/HPLaserJecon',
                       'printer-info': u'LaserJet_4L_Econ',
                       'printer-is-shared': True,
                       'printer-location': u'dell-desktop',
                       'printer-make-and-model': u'HP LaserJet 4L Foomatic/ljet4 (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to connect to CIFS host, will retry in 60 seconds...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143364,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LaserJet_4L_Econ'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Unable to connect to CIFS host, will retry in 60 seconds...',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [168],
 'test_page_job_status': [(168, 'LaserJet_4L_Econ', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Unable to connect to CIFS host, will retry in 60 seconds...',
 'printer-state-reasons': 'none'}

---

### Post by Thelasko on 2008-09-08
Are there any shared folders on these Windows machines?  Can you view them from your Ubuntu machine?  

It's probably something simple, like Windows requiring a password to access shared folders/printers over the network.  Sharing between Linux and Windows usually is done using Samba.  Samba handles both folder sharing and printer sharing.  If you can view shared folders, you should be able to use the shared printer.

It could also be a software firewall issue.  When you shut off your machines and restarted them, they may have been issued new IP addresses via DHCP.  This new IP address being blocked by the firewall could cause this issue as well.

---

### Post by lazyart on 2008-09-08
I'm willing to bet that your machines are getting ip addresses via DHCP.  When you shut them down for a few days the lost their leases.  No, they didn't move out but due to the order you turned them back on they have changed addresses.

On the Windows machine with the printer attached, do an ipconfig.  Ubuntu expects that machine to be 192.168.1.101 and it's probably .102.

For sanity reasons, you'll want to set that windows machine to a static address, that way Ubuntu will always know where to find the printer.  192.168.1.99 is probably a good choice.

Go back to the windows machine and type ipconfig /all ...this will give yo the info you need to set up the static address.

Go to Control Panel>Network Connections. Right click on your NIC and select properties.  Find TCP/IP in the middle window and double click on it.  Instead of acquiring an address automatically, set it to 192.168.1.99.  The subnet mask is probably 255.255.255.0, but check the output of ipconfig /all that you did previously.  The gateway is probably 192.168.1.1, but again double check and enter the info.  Finally, enter the address of the DNS servers, again referring to ipconfig /all.  Confirm everything by hitting OK to close the windows.

Now back at your ubuntu box, go to your printer configuration and change the address to 192.168.1.99.  You should be all clear.

---

