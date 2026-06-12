---
title: "How to autorun a CD"
date: 2016-01-30
forum: New to Ubuntu
---

### Post by claiment on 2016-01-30
I am a beginner and I don t know how is the way for make and autorun in a CD. The CD is charged in my laptop, but only it allows me starting with a folder. I click in a folder, and there is a program called autorun but I don t know how to make it run. I don t know how to use the terminal of the ubuntu environment.

Thank you

---

### Post by howefield on 2016-01-30
What is on the CD - is it a Windows application ?

---

### Post by grahammechanical on 2016-01-30
Autorun is designed to work in Windows. I have no experience getting autorun to work on anything later than Windows 98 but you need to edit autorun.ini or may be autorun.inf. Trying copying an existing autorun.ini or autorun.inf and editing that. It will not work with a Linux OS.

Where would you get an existing autorun.ini? From a DVD being given away by a Windows magazine?

I have an old DVD given away by a Linux magazine and it has Ubuntu 8.10 on it but it also has an autorun.inf

> [autorun]
open=umenu.exe
icon=umenu.exe

And it loads an application called umenu.exe which is also on the disk. So, I guess that you use autorun.inf. But how it is done in Linux I have no idea.

Regards.

---

### Post by claiment on 2016-02-06
Hello Howefeld

Yes, is a cd installer for a printer. Yes, obviously is for windows environment.

---

### Post by coffeecat on 2016-02-06
> **claiment said:**
> Yes, is a cd installer for a printer. 

Then please post details of the printer. The CD will be for the Windows drivers and utilities which won't work in Ubuntu. There is a good chance that your printer is already supported with the bundled drivers in Ubuntu. If not, there are other ways of installing drivers in Linux operating systems. In any event, for members to advise we need details of the printer.

---

### Post by claiment on 2016-02-06
Hello grahammechanicals

I am very glad with your answer, but you talk about windows. Thanks, i will continue investigating.
We are conected.

hello cofeecat
 
your work like a administrator is very useful. Thanks

Then, yes, then printer is a canon pixma mg2550

---

### Post by coffeecat on 2016-02-06
> **claiment said:**
> 
Then, yes, then printer is a canon pixma mg2550

There is already a driver for that printer in Ubuntu 15.10, but I don't know whether that is true for earlier versions of Ubuntu, and you don't tell us which version of Ubuntu you are using. 

So, probably, all you have to do is to follow the instruction howefield gave you in this thread: [http://ubuntuforums.org/showthread.php?t=2311843](http://ubuntuforums.org/showthread.php?t=2311843)

Why did you not respond to that post?

---

### Post by claiment on 2016-02-06
> **coffeecat said:**
> There is already a driver for that printer in Ubuntu 15.10, but I don't know whether that is true for earlier versions of Ubuntu, and you don't tell us which version of Ubuntu you are using. 

So, probably, all you have to do is to follow the instruction howefield gave you in this thread: [http://ubuntuforums.org/showthread.php?t=2311843](http://ubuntuforums.org/showthread.php?t=2311843)

Why did you not respond to that post?

OH sorry cofeecat,
I am spanish and i don t understand words 
this web is new for me too
My english is not very high level
My ubuntu versioni is 14.04
Thanks

---

### Post by Vladlenin5000 on 2016-02-06
I suggest you simply connect the printer then go to System Settings > Printer and, if not there already, try the Add Printer dialog. Chances are, as commented above, this is all you need. The CD you can trow in the recycling bin (contenedor amarillo).

---

### Post by claiment on 2016-02-09
> **Vladlenin5000 said:**
> I suggest you simply connect the printer then go to System Settings > Printer and, if not there already, try the Add Printer dialog. Chances are, as commented above, this is all you need. The CD you can trow in the recycling bin (contenedor amarillo).

Hello
that's what I do it. I choose the printer in the printer list and ther's impossible to print a sheet.

---

### Post by Vladlenin5000 on 2016-02-09
[http://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg2550.aspx?type=drivers&language=&os=Linux%20%2864-bit%29](http://www.canon.co.uk/support/consumer_products/products/fax__multifunctionals/inkjet/pixma_mg_series/pixma_mg2550.aspx?type=drivers&language=&os=Linux%20%2864-bit%29)

Scroll down and download IJ Printer Driver and ScanGear MP (_debian_ packages). Install it in the same order by double-clicking. It'll open with Ubuntu Software Centre by default.

---

