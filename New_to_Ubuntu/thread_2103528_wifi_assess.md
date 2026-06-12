---
title: "wifi assess"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by ashwanibajaj78 on 2013-01-10
i have installed ubuntu on my dell inspiron 1564i3,but i am unable to assess wifi on it. how could i configure wifi on ubuntu

---

### Post by mevets on 2013-01-10
> **ashwanibajaj78 said:**
> i have installed ubuntu on my dell inspiron 1564i3,but i am unable to assess wifi on it. how could i configure wifi on ubuntu

You might need to install proprietary drivers. Try running 'addition drivers'. Or 'jockey-gtk' from the command line.

---

### Post by mlentink on 2013-01-10
Open Ubuntu Software Center. In the menu, select Edit > Software Sources. In the window that opens, click on the "Additional Drivers" tab. See if there are any proprietary drivers available for your network interface. Most likely they will be Broadcom or some such.

---

### Post by squakie on 2013-01-10
The above assumes you have network access - via hardwire since your wireless isn't working yet.

Let's start at finding out what type of adapter you have and the chipset - things we need to give you instructions on getting a driver loaded.

Open a terminal window, then type:

lspci | grep Network > ~/abs-forum-net.txt <press enter>

Please note that "|" is the piping symbol - not a 1, not a lower case "L".  On my keyboard it is located above the "\" key - yours may be else where.  Please also note the single ">" indicates to route the output to a new file (or if the file exists, replace its contents) - in this case abs-forum-net.txt in your home folder.

iwconfig  >> ~/abs-forum-net.txt <press enter>

Please note the double ">", not a single.  This appends the output to the file abs-forum-net.txt in your home folder.

ifconfig  >> ~/abs-forum-net.txt <press enter>

Please note the double ">", not a single.  This appends the output to the file abs-forum-net.txt in your home folder.

Now create a reply here and use the paper clip symbol to attach a file - select the abs-forum-net.txt file from your home folder.


p.s. - I think you meant your title to say wifi "access", not wifi "assess" ? ;)

---

