---
title: "Connecting to a shared printer on a windows 7 desktop"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Tobey666 on 2011-10-23
Hi everyone,

First of all, I am very new to kubuntu, I just installed it a couple of days ago after getting frustrated with unity...so bear with me.

I am trying to connect my laptop running Kubuntu 11.10 to the printer, which is connected to a desktop running Windows 7.  I can print and connect to that desktop via the other computers in my house (a mac and several Windows machines) but not on my laptop.  In fact, if I click on Network in Dolphin, I don't see anything.

What I've tried so far:
Running the Printer Configuration Utility: using smb://ip_address of the desktop/Printer_name
Also tried setting it up using the workgroup name and the deskop's name.
-no dice for either.
I've tried to disable firewalls on both machines, to see if I could at least get them to see each other, but still nothing.
I've also tried to find a comprehensive guide on how to set this up, but all the websites and how-to's I've seen are either for very old versions of kubuntu or for sharing printers connected *to* the linux machine.  What am I missing?  Am I even beginning in the right place?:confused: Is there a how-to somewhere on this site that I just missed?

I'm just at a loss, so any help would be appreciated.  Let me know if you need any additional information.

Thanks.

---

### Post by Tobey666 on 2011-10-24
<bump>

---

### Post by meatytaco on 2011-10-24
Try looking at this?
[http://www.liberiangeek.net/2010/04/linux-beginner-how-to-print-to-a-windows-printer-from-ubuntu-systems/]("http://www.liberiangeek.net/2010/04/linux-beginner-how-to-print-to-a-windows-printer-from-ubuntu-systems/")

best i can come up with. Most tutorials i found are either for printing from windows on a printer connected to ubuntu, or for windows XP.

---

### Post by Tobey666 on 2011-10-25
Well it at least starts with the Windows settings instead of in the middle somewhere.  Thanks.  

I think that the real issue that I'm going to have to figure out is why my laptop can't see the desktop.  There's probably some tiny checkmark in some obscure Windows setting that I've overlooked.

---

### Post by meatytaco on 2011-10-25
> **Tobey666 said:**
> Well it at least starts with the Windows settings instead of in the middle somewhere.  Thanks.  

I think that the real issue that I'm going to have to figure out is why my laptop can't see the desktop.  There's probably some tiny checkmark in some obscure Windows setting that I've overlooked.
yeah. lol that seems to be the issue most of the time :P

---

### Post by mastablasta on 2011-10-25
> **Tobey666 said:**
>  
What I've tried so far:
Running the Printer Configuration Utility: using smb://ip_address of the desktop/Printer_name
Also tried setting it up using the workgroup name and the deskop's name.
-no dice for either.
I've tried to disable firewalls on both machines, to see if I could at least get them to see each other, but still nothing.
I've also tried to find a comprehensive guide on how to set this up, but all the websites and how-to's I've seen are either for very old versions of kubuntu or for sharing printers connected *to* the linux machine. What am I missing? Am I even beginning in the right place?:confused: Is there a how-to somewhere on this site that I just missed?
.
 
don't tell me they did it again?!
 
Anyway in the older version (10.10) there was a package missing when you installed SAMBA that was needed in order to be able to share via SAMBA.
 
here is how i solved this (myself): [http://ubuntuforums.org/showpost.php?p=10504755&postcount=3](http://ubuntuforums.org/showpost.php?p=10504755&postcount=3)
 
As for printing oyu need to know the exact name the Linux sees the printer. i initially installed samba and cups, but that didnt' make it show up. so the only way was to know the exact printer address/name under which the linux sees it. i dont' know how to find this information. i used another Ubuntu mashcine. perhaps using a live Ubunut cd would give similar result?! my (silly) sulution: [http://ubuntuforums.org/showpost.php?p=10511350&postcount=3](http://ubuntuforums.org/showpost.php?p=10511350&postcount=3)

---

### Post by Tobey666 on 2011-10-25
Thanks, I'll give those a shot tonight when I get home.

---

### Post by wgn on 2011-10-25
To get the name of the printer, open the CUPS admin utility

[http://localhost:631]("http://localhost:631")

If I remember correctly, there's a "Printers" tab.  Click that and choose the printer you want (probably only one).

---

### Post by wgn on 2011-10-25
Also, when I was going through this to hook up my wife's XP computer, I think the setting was

[ipp://ip_address:631/printers/printer_name]("ipp://ip_address:631/printers/printer_name")

Don't know if the 631 port is necessary since that's the default but I figured it couldn't hurt.

---

### Post by Tobey666 on 2011-10-26
> **wgn said:**
> To get the name of the printer, open the CUPS admin utility

[http://localhost:631](http://localhost:631)

If I remember correctly, there's a "Printers" tab.  Click that and choose the printer you want (probably only one).


Nothing shows up under printers.  Am I supposed to be opening that on the Windows computer or my laptop?

The good news is, I did manage to get the laptop to see the other computers on the network.  Turns out, none of the tutorials out there deem it worth mentioning that you have to download and install Samba.  Typed in "Samba" in the Muon Software Center, installed it and now, everything can be seen by my laptop...except the printer.

---

### Post by wgn on 2011-10-26
Open it on your Ubuntu box.
Should look like this

---

### Post by wgn on 2011-10-26
Oops, my bad.  First time I read this I thought you had the printer on your Ubuntu machine.

Still need the CUPS admin utility.  Click the Administration tab, and then the Add Printer button.  It should start looking on your network for shared printers.  If it doesn't find any then you're probably right about needing to check some box on your Windows machine.

btw, I don't think you need Samba to share a Windows printer, just for Windows to share a *nux printer

---

### Post by Tobey666 on 2011-10-26
> **wgn said:**
> Oops, my bad.  First time I read this I thought you had the printer on your Ubuntu machine.

Still need the CUPS admin utility.  Click the Administration tab, and then the Add Printer button.  It should start looking on your network for shared printers.  If it doesn't find any then you're probably right about needing to check some box on your Windows machine.

btw, I don't think you need Samba to share a Windows printer, just for Windows to share a *nux printer

I tried adding a printer on the administration tab, however it asks for a user name and password.  Neither my kubuntu nor my windows account credentials work.

---

### Post by Tobey666 on 2011-10-27
Maybe I need to start over, to make sure that I'm not missing anything.  As I understand it, to connect to the network printer, I need to open Printer Configuration and select "New Printer"

On the next page, I select "Windows Printer via Samba" from the list on the left.  After that, I fill in the following information:

smb://[workgroup/]server[:port]/printer

Here's the way I understand how to fill this in:

smb://the name of my workgroup/the name of the desktop/the name of the printer

so mine would be something like
smb://WORKGROUP/SMDESKTOP-PC/HP_Officejet_Pro...etc.

Am I reading this correct or is there something else that's meant by server?  Do I need the port?  If so where do I find it?

---

### Post by mastablasta on 2011-10-27
yeah i think that's about it. i am not sure about port. 
 
for me the problem was how linux sees the printer as it's name wasn't the same as in Windows. it's almost a year since i did this so i forgot it a bit.

---

### Post by cjazz on 2011-10-27
> **Tobey666 said:**
> Maybe I need to start over, to make sure that I'm not missing anything.  As I understand it, to connect to the network printer, I need to open Printer Configuration and select "New Printer"

On the next page, I select "Windows Printer via Samba" from the list on the left.  After that, I fill in the following information:

smb://[workgroup/]server[:port]/printer

Here's the way I understand how to fill this in:

smb://the name of my workgroup/the name of the desktop/the name of the printer

so mine would be something like
smb://WORKGROUP/SMDESKTOP-PC/HP_Officejet_Pro...etc.

Am I reading this correct or is there something else that's meant by server?  Do I need the port?  If so where do I find it?

It's been years since I've done this, but I believe that's correct. Another thing to keep in mind, however, is that case matters in Linux where often in Windows it's irrelevant. I believe you have the case represented correctly in your example, but if problems arise, you may need to experiment.

---

### Post by Tobey666 on 2011-10-28
Status Update.

Still no luck with this.  If I run Ubuntu off of a USB drive on one of my other computers, it is possible to set up the network printer just fine, I don't even have to type anything in: just click "Browse," select the desktop in question, and voila!  It only seems to be Kubuntu.  I've copied the Samba address exactly, so that it is exactly how another buntu computer would see it, but still nothing.  

I can see and share files from every computer on my network, including my kubuntu computer.  I can print from all of those computers regardless of their OS, but I can't print from kubuntu.  The problem is still at large.  I remain hopeful that someday I can make this work.

---

### Post by Tobey666 on 2011-10-28
Success!

I deleted my old configuration and started over.

Here's the only thing that I did differently, which no guide on how to connect kubuntu to a shared printer on Windows 7 bothered to mention:

When I first was trying to do this, I was attempting to write my printer's name as it appeared on every other OS I was using (Windows 7 and ubuntu 10.10.  So the Device URI while I was setting it up looked like this:

smb://WORKGROUP/DESKTOP-PC/HP_Officejet_Pro

Where the underscores represent what appear as spaces on the printer name in Windows and Ubuntu.  

Apparently, when you're running the initial setup, you're supposed to omit any spaces (since the kubuntu utility won't let you type %20 in the configuration utility) Sosetup it should look something like this:

smb://WORKGROUP/DESKTOP-PC/HPOfficejetPro

Now, here's the thing, it won't actually work at this point.  After you finish the configuration, you have to go back into your printer settings and add "%20" where all of the spaces are supposed to be.  Then, it worked.

P.S. Well, it didn't actually work right away at this point.  When I set it up without the spaces, HP didn't appear in the list of drivers.  After I entered in the %20's, I tried looking again and it was there.

---

### Post by MangoChampagne on 2011-12-20
I followed wgn's instructions below (thanks wgn!), and with a bit of playing around got my shared printer to work.  Thought I'd document my steps for the benefit of future visitors to this thread.

My printer is attached to a Windows XP box; I've set it up to be shared in a Windows domain.


[LIST=1]
[*] Install and run the samba client
[*]Run 'smbacls' to look up the resources available for sharing through Samba.  Most importantly you will be able to locate the print server name and the printer name here.  The URI to use (in the next step) is smb://<print server name>/<printer name>.
[*]Point to [http://localhost:631](http://localhost:631) in a browser.  Select the Administration tab.  Click 'Add Printer'. Walk through screens where you have to specify the URI, and the printer make and model.  My printer Canon PIXMA MX310 wasn't listed; so I had research this a bit to find the nearest equivalent driver in that list (turned out to be Canon PIXMA MP220).
[/LIST]
 
And that was it.  The printer was successfully set up.

```
sudo apt-get install samba
smbacls'

```

---

