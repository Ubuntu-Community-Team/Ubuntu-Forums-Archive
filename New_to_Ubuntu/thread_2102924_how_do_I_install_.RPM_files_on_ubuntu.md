---
title: "how do I install .RPM files on ubuntu?"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by Athena's Owl on 2013-01-08
I'm having a huge problem trying to get my printer to work with ubuntu. I'm not getting any answers for my request for help, but no one is answering me. I'm trying to fix the problem myself, I swear I am, but I can't, because I don't know how to make .rpm files work in ubuntu, which uses .deb.

I have looked around for answers on this and I found out about Alien, which is a command line program, and that's okay. But it won't work.

The reason why it won't work is that it keeps saying "file not found" when I try to use it, even though the file is demonstably THERE.

I have tried:

carefully typing the file name
copying the filename and pasting it
pasting the entire command.

the command that I am attempting to use is:

sudo alien -d epson-inkjet-printer-201105w-1.0.0-1lsb3.2.i486.rpm

which is the actual name of an actual file that I actually downloaded, but I keep getting

"epson-inkjet-printer-201105w-1.0.0-1lsb3.2.i486.rpm" not found.

as a response, and I don't know why, I don't know what I'm doing wrong

can someone please help me? I really need to get these documents printed and I can't use my other computer to print them, there's a huge problem on the drive and it won't open programs that I use all the time, even if I uninstall them and reinstall them. I only have this computer and this operating system to get this printer working.

no, I can't hook it up to USB. there is no USB outlet on the printer, at all.

no, I can't just use the driver CD and see what happens. there is no CD drive on this computer. it's a netbook.

---

### Post by steeldriver on 2013-01-08
An .rpm file is for Redhat based systems - the only reason to try to use it would be if no .deb file was available (there are translator packages but they are not 100% reliable).

If a .deb file was provided but didn't work then there are more than likely other problems which you need to figure out / fix

---

### Post by Athena's Owl on 2013-01-08
There were two .deb files and I installed them, but it didn't solve my problem. there are more, other .deb files I could add, so i'll try that.

---

### Post by cbanakis on 2013-01-08
Try opening terminal, and typing in ```
sudo alien -d 
``` then drag the actual icon of the rpm file into terminal to complete the statement.

File not found tells me that terminal cannot find the file.

What better way to help it find it, than to drop it in its lap?

---

### Post by ibjsb4 on 2013-01-08
Im not running that printer, but looks to me the ".deb" file is here.

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

EDIT: late post, forget it

---

### Post by Athena's Owl on 2013-01-08
> **cbanakis said:**
> Try opening terminal, and typing in ```
sudo alien -d 
``` then drag the actual icon of the rpm file into terminal to complete the statement.

File not found tells me that terminal cannot find the file.

What better way to help it find it, than to drop it in its lap?

hot diggity, that worked! now to see if converting all these rpm files makes my printer automagically appear...

---

