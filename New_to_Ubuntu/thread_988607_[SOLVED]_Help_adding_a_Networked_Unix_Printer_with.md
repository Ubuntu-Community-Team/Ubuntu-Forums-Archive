---
title: "[SOLVED] Help adding a Networked Unix Printer with server and queue name"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by jamesrl on 2008-11-20
Hi,
I'm trying to access a network printer at work (which I used to have no problem setting up in 8.04 and earlier), but can't find the "add network printer" setting in 8.10.

Instructions from work are this:
> Printing from your Personal Linux Laptop

Redhat, Fedora, or Scientific Linux

    * Open your system's Printer Configuration GUI
          o depending on your distribution, this may be opened by typing redhat-config-printer or system-config-printer at the command line. 
    * Click on "New"
    * Click "Forward"
    * give the printer a name and short description; click "Forward"
    * For "Select a queue type:" choose Networked UNIX (LPD)
    * For "Server:" enter xxx.xxx.xxx.edu
    * For "Queue:" enter the name of the queue you would like to use.
          o This can be found from [http://www.xxx.xxx.edu/cgi-bin/printers/printer_list.pl](http://www.xxx.xxx.edu/cgi-bin/printers/printer_list.pl) 
    * click "Forward"
    * choose Generic PostScript Printer and click on "Forward"
    * Click on "Apply" to create the printer. 

When I go to printer configuration, and then add a new printer in 8.10 it first searches for printers (not what i want), and then gives me these options:
Two specific printers (that aren't mine, and I have no idea where they are physically located), a Windows Samba option (also not what I want), and then: 
AppSocket/HP JetDirect  (with options):
   Host:
   Port number:

Other: (with option):
   URI:

I tried the AppSocket option, but it didn't work as it never prompted me for the Queue (which really matters as there are many different printers some of which I don't have access to).  I have tried doing this directly with CUPS (firefox [http://127.0.0.1:631/](http://127.0.0.1:631/) ) and ran into basically the same problems.

---

### Post by jamesrl on 2008-11-20
Through a couple of guesses, I found that the Other: method worked, with a URI: of 

lpd://printserver.address.edu/queue_name

I still think for those non-familiar with printing protocols that the old menu GUI method was much simpler (with a lpd unix network print option).

---

### Post by bobnutfield on 2008-11-20
When you go to System>Administration>Printers, and click New, you will get the dialogue that a search is taking place for new printers.  Most of the time, if you are connected to the network, a shared printer will show up automatically.  If it does not, you can add it with the following required information:

1.  The ip address of the printer (or machine the shared printer is connected to)
2.  The name of the printer as it is shown in the printer config of the host printer server machine.

Then you would click "Other", and use the ipp protocol.  You would add the printer with the following entry:

> ipp://IPAdressOfPrintServer:631/printers/NameOfPrinter

This is assuming the print server is a Linux machine.  If it is a Windows machine, you would use Samba to connect.

---

### Post by jamesrl on 2008-11-20
The networked printer i described doesn't use IPP or windows (samba).  It uses the unix LPD protocol and is located on a VMS server.  I got it working, but under 8.04 and previous didn't have to guess/google how to form the URI.

---

### Post by msun on 2008-11-23
Yes it is not so obvious as with 8.04 - in my case I had to enter this for the device URL:- lpd://192.168.0.1:515   This is for a printer attached to my router acting as a print server for IP printing. Knowing that the port number should be 515 for normal IP printing to work is not exactly intuitive.:lolflag:

---

