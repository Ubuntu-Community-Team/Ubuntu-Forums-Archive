---
title: "How to set up a printer?"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by linux12 on 2012-05-27
How do I set up a printer over a local Wifi connection? I clicked "add printer" and got all these settings, and was like, whoa, what?

---

### Post by roton on 2012-05-27
Is your printer connected to the network and on? Just type in the ip address of the printer on the add printer window and follow the steps (you can usually find the ip through the menu on the actual printer).

---

### Post by xedi on 2012-05-27
I don't even think you need the IP Address, at least in my case it wasn't the case. It was just a matter of selecting my printer and I was done.

---

### Post by Shadius on 2012-05-27
If the printer is already connected to the network, Ubuntu should pick it up when you just turn it on. At least, it did for me.

---

### Post by linux12 on 2012-05-27
Well I don't see anything... how can I find my printers' IP address?

---

### Post by Shadius on 2012-05-27
> **linux12 said:**
> Well I don't see anything... how can I find my printers' IP address?

What printer is it you are trying to install? Is the printer connected to the network already? 

Take a look here:
[Printing]("https://help.ubuntu.com/10.04/printing/C/printing.html")

You can also go into Printers>Add Printer>Network Printer>Find Network Printer>Find

---

### Post by linux12 on 2012-05-27
It's like, an HP 8600-something... and yes, it's connected to the network-at least on my windows OS.

---

### Post by Shadius on 2012-05-27
> **linux12 said:**
> It's like, an HP 8600-something... and yes, it's connected to the network-at least on my windows OS.

Try the steps I suggested in the previous post.

---

### Post by daslinkard on 2012-05-27
You can always try the IP address of 192.168.1.102

---

### Post by HerrSubset on 2012-05-28
> **linux12 said:**
> It's like, an HP 8600-something... and yes, it's connected to the network-at least on my windows OS.

There's something in the softwarecentrum called "HPLIP toolbox". You can use it to connect HP printers and scanners to your pc, so perhaps you could give it a try?

---

### Post by roton on 2012-05-28
> **daslinkard said:**
> You can always try the IP address of 192.168.1.102

0.4% chance of success...

---

### Post by buzzingrobot on 2012-05-28
> **linux12 said:**
> It's like, an HP 8600-something... and yes, it's connected to the network-at least on my windows OS.

Setting up my HP printer required installed "hplip" from the Software Center or via "sudo apt-get install hplip". 

Hplip is a proprietary package from HP. It can download and install the proprietary driver needed, at least in my case, by my HP printer.   HP runs a [site]("http://hplipopensource.com/hplip-web/index.html") where they list which printers require an HP driver to function in Linux.

You can launch hplip by clicking on the icon that should appear after it's installed or by running "hp-setup" in a Terminal.  Choose the options that are appropriate for you and it should install your printer.  It should then appear in the "Printing" panel in System Settings where you can set it as the default (right click on the printer icon).

NOTE: HP-Setup apparently needs root access to install an HP driver it downloads.  At least, it did here.  So, if HP-Setup appears to download a driver but then fails to install it, run it as root:  Alt-F2 to open a command line, then enter "gksudo hp-setup". 

Printer IP:  Should be available from the software used to manage the printer on your other machine. HP-Setup may or may not need it. Try first without it, selecting the "network" option in HP-Setup and seeing if it finds your printer.  If not, and if you can't find the printer's IP, enter the IP of your router or the IP address of your other machine.  If you can't find these addresses, they are often in the range from 192.168.0.1 to 192.0.168.9.

---

### Post by linux12 on 2012-05-28
> **HerrSubset said:**
> There's something in the softwarecentrum called "HPLIP toolbox". You can use it to connect HP printers and scanners to your pc, so perhaps you could give it a try?

That worked! You rock!:guitar:

---

### Post by swamyuefa on 2012-05-29
hi buddies,
i am using ubuntu 12.04 lts, i am new to ubuntu. i have connected network printer (ricoh aficio mp c3501) in my office as per instruction given by [COLOR=Red]"shadius buddy"[/COLOR] . i got connected to the printer and showing icon with printer name.
but when i gave command print [COLOR=Red]self test page[/COLOR] - its giving like this in the printed page    
 [COLOR=Red]" userdict dup (\004) cnv { } put (\004\004) cnv { } put
if you can read this, you are using the wrong driver for your printer ".[/COLOR]

how to sort out this, someone help me:confused:

---

### Post by Shadius on 2012-05-29
> **swamyuefa said:**
> hi buddies,
i am using ubuntu 12.04 lts, i am new to ubuntu. i have connected network printer (ricoh aficio mp c3501) in my office as per instruction given by [COLOR=Red]"shadius buddy"[/COLOR] . i got connected to the printer and showing icon with printer name.
but when i gave command print [COLOR=Red]self test page[/COLOR] - its giving like this in the printed page    
 [COLOR=Red]" userdict dup (\004) cnv { } put (\004\004) cnv { } put
if you can read this, you are using the wrong driver for your printer ".[/COLOR]

how to sort out this, someone help me:confused:

It seems you have the wrong driver for your printer, but before we continue I suggest you open up your own thread since this one is marked as solved by the original poster. Once you create your thread, provide us with the link here.

---

