---
title: "How to print to a Windows XP networked printer"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by allynm on 2013-06-18
Hello everyone,

I have a very small networked printer (HP1505 laserjet).  It exists on a wireless network consisting of two XP boxes and 1 windows 7 box.  The network works fine as such.  I'd like to be able to print to the networked printer from Ubuntu 12.04.  I have spent a few hours attempting this using the printer configuration gui.  When I attempt to print to the printer using  lpr -laserjet myfile.s the file is sent to the queue and just sits there.  A message indicates that the printer is not reachable.

I'd appreciate any suggestions.  

Regards,
Mark Allyn

---

### Post by HiImTye on 2013-06-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
give this a read
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by SeijiSensei on 2013-06-19
I suggest using a browser on the Ubuntu box and navigating to [http://localhost:631/](http://localhost:631/) to use the CUPS utility. I find that the most reliable method. You'll be prompted for your password if you select an admin task like adding a printer.

---

### Post by allynm on 2013-06-19
Seiji and Hylm,

As nearly as I can tell from the tute that Hylm sent, I should be trying to use Samba since I am on a ubuntu box trying to print from a windows networked machine.  That is the gist of the very first diagram on the tute.  Maybe I'm missing something?

Well, it turns out that when I attemp to install Samba (v. 4) I get a torrent of error messages.  As usual, they are notably unhelpful in explaining what the problem is that the installer is having.  The upshot is that Samba can "see" the MSFT networked printer, but it can't get a message into the queue and print it.

Now as for CUPS, my understanding (and it is severely limited) is that it won't work to talk between ubuntu box and a nonunbuntu printer.  I followed Seiji's link and attempted to use the CUPS server and it simply would not allow me to add a printer of any sort.  Indeed, it can't "see" the printer at all.

So, I'm nowhere on this one.  But, thanks for trying to help me.  Appreciated.

Mark

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by SeijiSensei on 2013-06-19
I believe Windows natively supports the "Internet Printing Protocol."  If you connect to the CUPS utility, click Administration, then Add Printer (enter your username and password), then choose ipp and enter the XP machine's IP address.  Does that work?

---

### Post by allynm on 2013-06-19
Ok, so by messing around for another couple of hours I finally got the connection to the networked printer to function as desired.  Once again, I'm printing from a ubuntu 12.04 box to a Windows XP printer.  

What I did:
1. go to System->printers
2. click "Add"
3. click "network printers"
4. select the very last entry.  This references a samba app.
5. A window opens which allows you to btrowse to a file smb:\\dir\dir\printerx.   In my case the fully qualified directory was smb:\\MARKPC\HP1505.
6. follow the "forwards" after this.
7. The crucial window that you must select from gives the manufacturer and the model number.  You absolutely must make the right selections here or it won't work.  Trust me...
8. After naming the printer, and giving a few other specs like its human readable name and location, you're done.
9. Going back and selecting "Properties" you have an opportunity to print out a test page.  do it.

That's all, but what I'm telling you is that it took two solid afternoons to make the darn printer do its thing.

Regards,
Mark

---

