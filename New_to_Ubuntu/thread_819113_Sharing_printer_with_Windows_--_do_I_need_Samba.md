---
title: "Sharing printer with Windows -- do I need Samba?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by anton on 2008-06-05
After having read just about every guide I could find on the Web, I'm still battling to share my printer with a Windows machine. Here's my current status:

Ubuntu 8.04 installed on desktop (dual boot with Windows XP SP2)
Windows XP SP2 running on laptop
Desktop connected by cable to Netgear wireless router
File and printer sharing successful with both machines running Windows
Can ping desktop (running Ubuntu) from laptop using IP address
Can't ping desktop using computer name
Can access CUPS server using IP address via Web from both machines and print test page
Can also access CUPS with computer name from Ubuntu machine but not from laptop
Can't install printer on laptop using the Windows Add Printer Wizard, even when copying and pasting the URL from Firefox.  

Windows gives the following message: "Windows cannot connect to the printer. Either the printer name was typed incorrectly, or the specified printer has lost its connection to the server."  Clearly, Windows is wrong on both counts.

Do I need to install Samba to get this to work?  Some discussions & articles on the Web say yes, others say no.  I like to keep things simple, so would rather avoid setting up Samba if it's not necessary.  Surely the fact that I can access the printer via Firefox indicates that this should work?

And if I have to set up Samba, what is the simplest, most newbie-friendly way?

Any help would be appreciated.  I'm very frustrated after struggling with this for the past couple of days.

---

### Post by Xiong Chiamiov on 2008-06-05
I'm not sure about printer-sharing to Windows machines, as I can't get my printer to share to Linux machines atm (used to work, but doesn't anymore - hmph).  If you *do* need to use Samba, though, [here're]("http://del.icio.us/xiong.chiamiov/samba") the guides I used back when.

---

### Post by anton on 2008-06-05
Thanks for the guides.  I probably will end up installing Samba, as I'm sure I'll want to do some file sharing eventually.

Still, I'd like to know whether printer sharing can work without Samba, and if so what I'm missing . . .

---

### Post by anton on 2008-06-05
I've just had a look at the one guide.  It says the following:

[INDENT]The Samba metapackage is not necessary on clients to:

[ . . .]
* Have your Windows computer use (via a network) a printer that is attached to a Linux computer. CUPS can be configured to make the printer accessible to the network.[/INDENT]

So apparently I don't need Samba just for printer sharing.  I've carefully followed the Ubuntu instructions for setting up CUPS.  Basically, I have two questions:

1) Why is it that I can access the printer via the web browser from the client (Windows) machine, but the Add Printer Wizard can't find it?
2) Why can I ping the Ubuntu machine using the IP address, but not the computer name (which should also be the hostname,as far as I can tell)?

Any help would be most appreciated . . .

---

### Post by miciurin on 2008-06-05
There is a post outlining a very simple way of sharing drives and printers. I have tried in the past using the add printer and it did not work in XP. However after following this post it worked:

[http://ubuntuforums.org/showthread.php?t=806699&highlight=share+printer](http://ubuntuforums.org/showthread.php?t=806699&highlight=share+printer)

---

### Post by avtolle on 2008-06-05
On sharing the printer from Ubuntu; did you, in setting up the printer under Ubuntu, check the box to share the printer with others (from memory, hopefully you will understand what I'm "saying".)?

---

### Post by cariboo on 2008-06-05
> **anton said:**
> 

2) Why can I ping the Ubuntu machine using the IP address, but not the computer name (which should also be the hostname,as far as I can tell)?

Any help would be most appreciated . . .

The only way you can ping a computer by its hostname, is if that computers hostname is in your hosts file, in linux it is located at /etc/hosts here is an example:

```
jimk@intrepid:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	intrepid
xxx.xxx.xxx.xxx	willy
xxx.xxx.xxx.xxx	router

```

Jim

---

