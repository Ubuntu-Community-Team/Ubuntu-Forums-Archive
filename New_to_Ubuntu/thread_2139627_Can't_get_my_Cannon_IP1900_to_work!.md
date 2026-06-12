---
title: "Can't get my Cannon IP1900 to work!"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by Oluhishi on 2013-04-27
Hi, I recently upgraded to Ubuntu 12.10 from Windows. I wanted to install my Cannon IP1900 for me to print documents. So I downloaded the drivers that I needed and followed some steps on another thread. Then Ubuntu has recognised my printer. However, I've come to a problem when I print a document the printer state is "Idle - Sending data to printer." and nothing happens. I clicked on the 'Printer Queue" and its reported that all the task have been completed when nothing has been printed? Then I get an error in the software centre which says I have to use "sudo apt-get install" to remove 2 programs and once I do the Printer State becomes:
 "dle - File "/usr/lib/cups/filter/pstocanonij" not available: No such file or directory"

and there is a status message saying:
"There is a missing print filter for printer IP1900-series"

Can anyone please help me?

---

### Post by trinetra on 2013-05-18
Hi,
  Here is what I have done, Open terminal

sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-ip1900series

After that go to start and search for printers and add a new printer. Here you will see a new option something like "USB Printer "(when you click it, it will be showing the driver URI as cnijusb:/dev/usb/lp0), select it and click forward.

 Thats it, my Canon Pixima iP1900  is working in Ubuntu 12.10

---

### Post by Oluhishi on 2013-05-18
Hi [COLOR=#000000]trinetra,

Thank you ever so much! It works now, and I am able to print out the files I need!

Once again thank you for helping me![/COLOR]

---

