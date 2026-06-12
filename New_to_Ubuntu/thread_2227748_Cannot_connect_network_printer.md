---
title: "Cannot connect network printer"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-06-03
I have a brother laser printer connected to a ubuntu 14.04 system via USB. I can print on the printer from the local ubuntu 14.04 system. 

But I cannot print to the printer via my ubuntu 14.04 remote system or my ubuntu 12.04 system. This use to work the system to which the printer is connected to directly was Ubuntu 12.04. 

I add a printer as a network printer. I type in the host IP address and click find. It can not find any printer on the computer. This use to work when everything was Ubuntu 12.04.

---

### Post by pdc on 2014-06-03
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

have a read at this; some find it very helpful eg sharing

---

### Post by Paper Pusher on 2014-06-03
We have tried this (below) and it did not work on destination being 14.04

 Now let's configure the client (the Ubuntu computer from where you want to print):

    System -> Administration -> Printing

    Add - Network printer

        Click Find network printer
            Specify the host IP address or name. (It may also work without, try) (IP address worked for me, hostname did not.)

            Click Find 
        Printers on the target machine should be found, no matter whether they are connected using CUPS or SAMBA.
            BUT if both protocols are available, e.g. because you have shared your printer on a Linux box both using CUPS and Samba, prefer CUPS (ipp://) over Samba (smb://), because you won't be prompted to install a driver in general. 

        findNetworkPrinterScreenshot.png 
    You **may** be prompted to select a driver. Select your model in the list.
        (to be done) What to do if driver is not in the list

---

### Post by gifford on 2014-06-04
Sorry you are having the issues.
Did you forget the step of setting it up as a print server?
Try reading the link again and do this step to share the printer.

Otherwise, have you thought of connecting the printer directly to your network
and accessing it either through Ethernet or wireless?

---

### Post by oldrocker99 on 2014-06-04
I did have to enter my hostname and WPA-2 password **on** my printer, but it works just fine wireless.

---

### Post by Vladlenin5000 on 2014-06-04
> **oldrocker99 said:**
> I did have to enter my hostname and WPA-2 password **on** my printer, but it works just fine wireless.

That's exactly what gifford meant... Any printer with network features should be connected to the network, wired or wireless, as a standalone network device. For printers without it then a small dedicated ARM based print server is the second best option. Only use a power hungry desktop you must keep on in order to "serve" the printer if you can't use the previous options.

---

### Post by Paper Pusher on 2014-06-04
Thank you for all the advice. The printer is a HL-2240D laser printer. It does not have direct network capabilities.
[http://www.brother-usa.com/Printer/ModelDetail/1/hl2240d/spec#.U4_YmXKzB3A](http://www.brother-usa.com/Printer/ModelDetail/1/hl2240d/spec#.U4_YmXKzB3A)
It is connected by USB to a server running Ubutntu 14.04 on an Intel Atom processor. This system used to run Ubuntu 12.04 and everything was working fine. Now that the system has upgraded to Ubuntu 14.04, our systems on the house network cannot find the printer.

WPA-2 is not an option for my wired installation. Also, my print server desktop system is not power hungry it uses an Intel Atom processor. Atom processors are designed to very energy efficient.
The main desktops are all 64-bit procesasors. The Atom system, however, is only 32-bit for energy efficiency.

---

### Post by pdc on 2014-06-05
Hi Paper Pusher; sorry to hear of your continuing difficulties;

we don't seem to be able to get you to acknowledge one particular point that has been made twice: it would be really helpful if you could; we are asking you to check if the computer that we understand is directed connected to your Brother printer; via usb cable? ........has its server settings set to enable sharing of the printer ..publish shared printers ..............

Can you please tell us or acknowledge that: I enclose a screenshot: it comes from the reference about ubuntu networking

---

### Post by Paper Pusher on 2014-06-05
Yes the printer has its server settings enabled to share.

---

### Post by Paper Pusher on 2014-06-06
I am apologize, I did not understand the question exactly. I guess that is why I am a absolute beginner! 

It looks like Ubuntu 14.04 has a new option under print server settings. By going to printer setting and publishing the printer to be shared on a network connection, I was able to find the printer on my other computer which allowed me to print through the internet. This is the exact thing I was hoping to do! 

Thanks to pdc and his screenshot I was able to get a outstanding image on what I needed to find, making my job a lot easier.

---

### Post by pdc on 2014-06-06
so it is all working now?

If so, well done and enjoy;

as it is your thread, you can go to THREAD TOOLS near the top right of the page; and you can select SOLVED for the title

---

