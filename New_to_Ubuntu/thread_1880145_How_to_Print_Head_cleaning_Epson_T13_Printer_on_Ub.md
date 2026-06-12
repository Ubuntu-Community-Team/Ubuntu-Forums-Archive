---
title: "How to Print Head cleaning Epson T13 Printer on Ubuntu ?"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by lolly325 on 2011-11-13
Hello all Ubuntu users !
I want to ask something about printing.
I want to print head cleaning my printer. My printer is Epson T13.

Before I've used Ubuntu, I'm using Windows, but I moved into Ubuntu. Because, I love Ubuntu OS.

Do I need to install Epson program with Wine so i can clean print head ? 

Or, is there any way for me to cleaning it ?
Please, i need a help, without that, my works file will be bad to print...

---

### Post by jjex22 on 2011-11-13
Heya,

Should just be a case of hold down the power button for three seconds :D

---

### Post by philinux on 2011-11-13
> **lolly325 said:**
> Hello all Ubuntu users !
I want to ask something about printing.
I want to print head cleaning my printer. My printer is Epson T13.

Before I've used Ubuntu, I'm using Windows, but I moved into Ubuntu. Because, I love Ubuntu OS.

Do I need to install Epson program with Wine so i can clean print head ? 

Or, is there any way for me to cleaning it ?
Please, i need a help, without that, my works file will be bad to print...

There is an app called mtinc which works for most Epson printer. It works with my R200 and correctly shows ink levels etc etc.

---

### Post by lolly325 on 2011-11-15
> **philinux said:**
> There is an app called mtinc which works for most Epson printer. It works with my R200 and correctly shows ink levels etc etc.

hmmmm....
is there any other option like terminal way ??
and where can i get mtinc ?

---

### Post by arvevans on 2012-01-17
It's a bug.  **mtink**, **mtinkc** and **ttink** all rely on your printer being on a standard parallel or serial port.  If your printer interface uses USB, there is no way provided to configure these tools to connect to your USB printer.

As far as I know, there is no workaround or fix for this situation.

---

### Post by arvevans on 2012-01-18
Try using **escputil** (may have to download and install it).  It works in 11.10 with my USB connected Epson CX7400 all-in-one printer.  For newer printers you do have to use the -u" option.

---

