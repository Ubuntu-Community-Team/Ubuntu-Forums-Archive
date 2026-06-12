---
title: "NetworkPrintingFromWinXP"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-05-05
I runniing 8.04 on lap top A and XP on lap top B. The printer is attached to A. Printing on A is no problem. B can see A but not the attached printer in the XP "add new printer" wizard. B can see a printer in the "show workgroup" wizard..but the printer icon contains nothing.

I have been tearing out my hair (what is left of it!) trying to solve the network printing problems using the advice in NetworkPrintingFromWinXP. I can seem to get so far but the last step eludes me....any help is much appreciated.


PS The document mentions "displayed casing" - what is that...please give example.

---

### Post by ant2ne on 2008-05-05
B can see A? How? Is A using samba?

---

### Post by dunbrokin on 2008-05-05
Yes..it is using Samba

---

### Post by fmartinez on 2008-05-05
> **ant2ne said:**
> B can see A? How? Is A using samba?

"ant2ne" has the right idea. To fully share a Linux networked printer with a Windows machine: You need a combination of both Samba files share and CUPS (Common Unix Printing Services) enabled and running. 
If you google "ubuntu server guide" these pages have real good how to guides to get you started. 
FYI - I've shaved my head since using Linux... No more hair to pull! :)

---

### Post by dunbrokin on 2008-05-05
Thanks for that...but I seem to have exhausted my ability to get any more out of these sources.

---

### Post by fmartinez on 2008-05-05
> **dunbrokin said:**
> Thanks for that...but I seem to have exhausted my ability to get any more out of these sources.

Don't give up! 
- Are you able to share files from your Linux computer using SAMBA? 
- If not you may not have Samba up and running correctly. 
- Check to see if you have CUPS running. 
$ps aux |grep cups      #This will tell you if you have cups running. You can do the same for samba to see if samba is running.

---

### Post by dunbrokin on 2008-05-06
I am able to share form A to B i.e. Ubuntu can read and write to XP machine.
XP machine can see but not read or write from Ubuntu machine....which suggests what?

Where should I be looking....I am so close I can almost feel the answer...but I need some detail please...

---

### Post by hyper_ch on 2008-05-06
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_print_on_remote_Ubuntu_machine_via_samba](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_print_on_remote_Ubuntu_machine_via_samba)

---

### Post by HereInOz on 2008-05-06
Essentially you connect to the printer on A as an Internet printer.

First you need to change the lines in /etc/cups/cupsd.conf to read:

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 'use the IP address of A':631

so if the IP address of A is 192.168.1.3, then the last line would read:
Listen 192.168.1.3:631

You will need to use sudo gedit /etc/cups/cupsd.conf to edit this file.  Maybe restart computer A to make sure all is running properly - not sure if this is essential.

Then once you have done that, you can go to the Windows machine and set it up as an internet printer (you may have to install the printer as a local Windows printer first to get the driver into the driver cache) using the URL of (assuming A is 192.168.1.3) 

[http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)

You can also try opening a web browser on the Windows machine and entering

[http://192.168.1.3:631/printers](http://192.168.1.3:631/printers)

and you will be able to see the printers attached to A.

Remember, you must change the IP address which I have used, 192.168.1.3, to the actual IP address of the computer A.

Hope this helps.

---

### Post by dunbrokin on 2008-05-06
[http://ubuntuguide.org/wiki/Ubuntu:G...hine_via_samba](http://ubuntuguide.org/wiki/Ubuntu:G...hine_via_samba)

Tried that thanks....no effect.

---

### Post by dunbrokin on 2008-05-06
Then once you have done that, you can go to the Windows machine and set it up as an internet printer (you may have to install the printer as a local Windows printer first to get the driver into the driver cache) using the URL of (assuming A is 192.168.1.3) 

[http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)

You can also try opening a web browser on the Windows machine and entering

[http://192.168.1.3:631/printers](http://192.168.1.3:631/printers)

and you will be able to see the printers attached to A.

Remember, you must change the IP address which I have used, 192.168.1.3, to the actual IP address of the computer A.

Hope this helps.[/QUOTE]

Thanks for the input, your help is much appreciated.

When yo say name_of_Printer, what exactly do you mean?

---

### Post by dunbrokin on 2008-05-06
> **dunbrokin said:**
> Then once you have done that, you can go to the Windows machine and set it up as an internet printer (you may have to install the printer as a local Windows printer first to get the driver into the driver cache) using the URL of (assuming A is 192.168.1.3) 

[http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)

You can also try opening a web browser on the Windows machine and entering

[http://192.168.1.3:631/printers](http://192.168.1.3:631/printers)

and you will be able to see the printers attached to A.

Remember, you must change the IP address which I have used, 192.168.1.3, to the actual IP address of the computer A.

Hope this helps.

Thank you that was extremely useful....I now have got the next step...in that the XP machine is now seeking a driver for the printer...however the driver does not appear to be on the supplied disk...so again (this seems to be a feature of switching form Win to Ubu) two steps forward and one step back.

Thanks for the input, your help is much appreciated.

When yo say name_of_Printer, what exactly do you mean?[/QUOTE]

---

### Post by dunbrokin on 2008-05-06
> **HereInOz said:**
> Essentially you connect to the printer on A as an Internet printer.

First you need to change the lines in /etc/cups/cupsd.conf to read:

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 'use the IP address of A':631

so if the IP address of A is 192.168.1.3, then the last line would read:
Listen 192.168.1.3:631

You will need to use sudo gedit /etc/cups/cupsd.conf to edit this file.  Maybe restart computer A to make sure all is running properly - not sure if this is essential.

Then once you have done that, you can go to the Windows machine and set it up as an internet printer (you may have to install the printer as a local Windows printer first to get the driver into the driver cache) using the URL of (assuming A is 192.168.1.3) 

[http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)

You can also try opening a web browser on the Windows machine and entering

[http://192.168.1.3:631/printers](http://192.168.1.3:631/printers)

and you will be able to see the printers attached to A.

Remember, you must change the IP address which I have used, 192.168.1.3, to the actual IP address of the computer A.

Hope this helps.

Problem solved...thank you very much I can now print....such a simple solution to something that has taken me days to figure out....much appreciated.

---

### Post by dunbrokin on 2009-01-01
> **HereInOz said:**
> Essentially you connect to the printer on A as an Internet printer.

First you need to change the lines in /etc/cups/cupsd.conf to read:

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 'use the IP address of A':631

so if the IP address of A is 192.168.1.3, then the last line would read:
Listen 192.168.1.3:631

You will need to use sudo gedit /etc/cups/cupsd.conf to edit this file.  Maybe restart computer A to make sure all is running properly - not sure if this is essential.

Then once you have done that, you can go to the Windows machine and set it up as an internet printer (you may have to install the printer as a local Windows printer first to get the driver into the driver cache) using the URL of (assuming A is 192.168.1.3) 

[http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)

You can also try opening a web browser on the Windows machine and entering

[http://192.168.1.3:631/printers](http://192.168.1.3:631/printers)

and you will be able to see the printers attached to A.

Remember, you must change the IP address which I have used, 192.168.1.3, to the actual IP address of the computer A.

Hope this helps.

This suggestion has served me very well up until recently when the printer was no longer recognised by the XP machine. When I enter http:/10.1.1.5:631/printers in the XP machine I get a Network is taking too long to receive an answer message. On the XP machine, I can see the MSHOME network and the Ubuntu machine...but there is no printer shown attached.

---

### Post by dunbrokin on 2009-01-07
bump

---

### Post by ant2ne on 2009-01-10
> **dunbrokin said:**
> This suggestion has served me very well up until recently when the printer was no longer recognised by the XP machine. When I enter http:/10.1.1.5:631/printers in the XP machine I get a Network is taking too long to receive an answer message. On the XP machine, I can see the MSHOME network and the Ubuntu machine...but there is no printer shown attached.

Windows Network Neighborhood tends to keep data in their that isn't exactly accurate. So when you say "see" all because you "see" an icon does not mean that the machines are talking. Open a command windows (Start, Run, type "cmd" hit, enter) and type "ping 10.1.1.5" and see if you get a reply. Then you can try to ping by name. 

Also, using CUPS to print to [http://10.1.1.5:631/printers](http://10.1.1.5:631/printers) still requires the windows drivers installed on the windows machine. And the NIX machine will not by default supply them. CUPS printing, I have experieced, is more reliable than samba printing.

Another note: "http:/10.1.1.5:631/printers" is what you typed; "http://10.1.1.5:631/printers" with the second "/" is requried. IDK if that is just a typing error.

---

### Post by dunbrokin on 2009-01-10
> **ant2ne said:**
> Windows Network Neighborhood tends to keep data in their that isn't exactly accurate. So when you say "see" all because you "see" an icon does not mean that the machines are talking. Open a command windows (Start, Run, type "cmd" hit, enter) and type "ping 10.1.1.5" and see if you get a reply. Then you can try to ping by name. 

Also, using CUPS to print to [http://10.1.1.5:631/printers](http://10.1.1.5:631/printers) still requires the windows drivers installed on the windows machine. And the NIX machine will not by default supply them. CUPS printing, I have experieced, is more reliable than samba printing.

Another note: "http:/10.1.1.5:631/printers" is what you typed; "http://10.1.1.5:631/printers" with the second "/" is requried. IDK if that is just a typing error.


I can ping 10.1.1.5 - and according to the XP machine I am using SAMBA and Ubuntu to communicate....I certainly had the driver for the printer installed on the XP machine before as I ran for 9 months with no problem. How do I use CUPS instead of SAMBA?....indeed the http:/ was a typing error...sorry.

Thanks for your help.

---

### Post by ant2ne on 2009-01-11
This is how I got it set up...

On ubuntu (print server) box open a browser and verify that you can navigate to [http://PrintServerIP:631/printers/](http://PrintServerIP:631/printers/) make a note of the exact spelling of the printer name.

Open Firestarter (firewall) and tweak settings so that other computers can connect to your print server

Goto Windows (Print Client) box and Verify you can connect to [http://PrintServerIP:631/printers/](http://PrintServerIP:631/printers/) with your web browser. Then install the printer. Goto Start -> Printers -> Add a printer -> A network printer -> Connect to a printer on the Internet -> Enter URL http://PrintServerIP:631/printers/"PrinterName" -> Next -> Enter Drivers etc.

If you get blocked, I'd check your firewall settings again.

This has worked for me much better than Samba printing. I bet Samba printing is more powerful and better for an enterprise setting. But much harder to configure.

---

### Post by dunbrokin on 2009-01-26
> **HereInOz said:**
> Essentially you connect to the printer on A as an Internet printer.

First you need to change the lines in /etc/cups/cupsd.conf to read:

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
Listen 'use the IP address of A':631

so if the IP address of A is 192.168.1.3, then the last line would read:
Listen 192.168.1.3:631

You will need to use sudo gedit /etc/cups/cupsd.conf to edit this file.  Maybe restart computer A to make sure all is running properly - not sure if this is essential.

Then once you have done that, you can go to the Windows machine and set it up as an internet printer (you may have to install the printer as a local Windows printer first to get the driver into the driver cache) using the URL of (assuming A is 192.168.1.3) 

[http://192.168.1.3:631/printers/name_of_printer](http://192.168.1.3:631/printers/name_of_printer)

You can also try opening a web browser on the Windows machine and entering

[http://192.168.1.3:631/printers](http://192.168.1.3:631/printers)

and you will be able to see the printers attached to A.

Remember, you must change the IP address which I have used, 192.168.1.3, to the actual IP address of the computer A.

Hope this helps.

This was very useful the first time around....but now something has changed (in the XP machine I think)...as the XP machine can no longer see any printer attached to the Ubuntu machine....it can see the Ubuntu machine but not the printer. The printer works perfectly with the Ubuntu machine and also, in a local capacity, with the XP machine.....I am stumpted....I tried turning off Norton and that made no difference either..

---

### Post by dunbrokin on 2009-01-26
> **ant2ne said:**
> This is how I got it set up...

On ubuntu (print server) box open a browser and verify that you can navigate to [http://PrintServerIP:631/printers/](http://PrintServerIP:631/printers/) make a note of the exact spelling of the printer name.

Open Firestarter (firewall) and tweak settings so that other computers can connect to your print server

Goto Windows (Print Client) box and Verify you can connect to [http://PrintServerIP:631/printers/](http://PrintServerIP:631/printers/) with your web browser. Then install the printer. Goto Start -> Printers -> Add a printer -> A network printer -> Connect to a printer on the Internet -> Enter URL http://PrintServerIP:631/printers/"PrinterName" -> Next -> Enter Drivers etc.

If you get blocked, I'd check your firewall settings again.

This has worked for me much better than Samba printing. I bet Samba printing is more powerful and better for an enterprise setting. But much harder to configure.

The XP machine cannot see the printer linked to the Ubuntu machine. http:/10.1.1.5:631/printers/ just times out on the XP machine...

---

### Post by dunbrokin on 2009-01-26
> **ant2ne said:**
> Windows Network Neighborhood tends to keep data in their that isn't exactly accurate. So when you say "see" all because you "see" an icon does not mean that the machines are talking. Open a command windows (Start, Run, type "cmd" hit, enter) and type "ping 10.1.1.5" and see if you get a reply. Then you can try to ping by name. 

Also, using CUPS to print to [http://10.1.1.5:631/printers](http://10.1.1.5:631/printers) still requires the windows drivers installed on the windows machine. And the NIX machine will not by default supply them. CUPS printing, I have experieced, is more reliable than samba printing.

Another note: "http:/10.1.1.5:631/printers" is what you typed; "http://10.1.1.5:631/printers" with the second "/" is requried. IDK if that is just a typing error.

The ping timed out! What do I need to do to reconnect the two machines?

---

### Post by ant2ne on 2009-01-31
5 days ago...

If you ware still having problems, goto the machine with IP of 10.1.1.5, open a terminal and do an ifconfig to verify that it is still at 10.1.1.5. If it is, then begin troubleshooting a physical connection or firewall problem between the 2 devices.

---

