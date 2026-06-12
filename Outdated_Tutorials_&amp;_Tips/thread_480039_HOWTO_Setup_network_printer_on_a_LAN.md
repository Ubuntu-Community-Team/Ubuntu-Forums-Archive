---
title: "HOWTO: Setup network printer on a LAN"
date: 2007-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2007-06-21
Note: This is a really simple howto. I thought that it would be posted already. However, after a few searches, I couldn't find a similar howto, so I'm posting this one. If it exists already, then I apologize.

This guide will tell you how to use a printer that is not connected to your computer, but connected to a different computer on the same network. I have the home or small office network in mind while writing this.

This guide assumes that you're using CUPS:

1. Log on to the computer that the printer is connected to.

2. Open your CUPS daemon configuration file: ```
gksudo gedit /etc/cups/cupsd.conf
```3. Hit Ctrl+F and search for > <Location /> Then close the Search dialogue. You should see something that looks like this: ```
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>
```4. Edit it to look like this: ```

<Location />
  Order Deny,Allow
  Allow From 127.0.0.1
  Allow From 192.168.1.*
</Location>
```Note: the IP address will vary based on your network settings. If you want to allow all interfaces on the network, you can do this:
```
 <Location />
  Order Deny,Allow
  Allow From @LOCAL
</Location>
```5. IF YOU'RE USING DAPPER - Open your CUPS Port Configuration file: ```
gksudo gedit /etc/cups/cups.d/ports.conf
```IF YOU'RE USING A LATER RELEASE- Open this file again: ```
gksudo gedit /etc/cups/cupsd.conf
```6. Replace the line > Listen localhost:631 with this: ```
Listen *:631
```Note: This tells CUPS to listen to port 631 for any requests. This is a potential security risk- > Enabling LAN printers detection will open port 631 on your system. This exposes you to the risk of exploiting any security vulnerabilities of the printing system. Remote attackers could potentially gain access to your system with the privileges of the "cupsys" user.Now, go on the computer(s) which you want to remotely print from.

1. Go to System > Administration > Printing, or launch ```
gnome-cups-manager
```2. Go to 'Global Settings'

3. Click 'Detect LAN Printers'

You should now be able to print from any computer on the network.

---

### Post by mitch.c on 2007-06-22
Great howto, and definitely one that's needed. I see a lot of confusion in the forums about network printing. Thanks for your post.

Here's a couple things I think are worth mentioning:

> **dbbolton said:**
> 
2. Open your CUPS daemon configuration file: ```
gksudo gedit /etc/cups/cupsd.cong
```3. Hit Ctrl+F and search for  Then close the Search dialogue. You should see something that looks like this:
```
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>
```
4. Edit it to look like this: ```

<Location />
  Order Deny,Allow
  Allow From 127.0.0.1
  Allow From 192.168.1.*
</Location>
```
Note: the IP address will vary based on your network settings.

You can actually leave this alone.. @LOCAL will allow access from all interfaces. So unless you are trying to restrict access from a particular network, this edit is not necessary.

> 
5. Open your CUPS Port Configuration file: ```
gksudo gedit /etc/cups/cups.d/ports.conf
```6. Replace the line ```
Listen localhost:631
```with this: ```
Listen 631
```Note: This tells CUPS to listen to port 631 for any requests. This is a potential security risk- Now, go on the computer(s) which you want to remotely print from.

The recommended syntax for the Listen directive (in the context you describe) is:
```
Listen *:631
```

Also, it's important to note that this directive is contained in /etc/cups/cups.d/ports.conf in Dapper and earlier, but after that, it's part of /etc/cups/cupsd.conf. Without adding an Include directive when using in these later releases, this file will never be read.

---

### Post by dbbolton on 2007-06-22
> **mitch.c said:**
> Great howto, and definitely one that's needed. I see a lot of confusion in the forums about network printing. Thanks for your post.

Here's a couple things I think are worth mentioning:



You can actually leave this alone.. @LOCAL will allow access from all interfaces. So unless you are trying to restrict access from a particular network, this edit is not necessary.



The recommended syntax for the Listen directive (in the context you describe) is:
```
Listen *:631
```Also, it's important to note that this directive is contained in /etc/cups/cups.d/ports.conf in Dapper and earlier, but after that, it's part of /etc/cups/cupsd.conf. Without adding an Include directive when using in these later releases, this file will never be read.
thanks for your input. i'll go ahead and modify my original post.

but, i can say that i did this on a network in which the printer was conneted to a feisty machine and other network computer was running dapper, and it worked fine.

does port 631 have to be open on all computers on the network, or just the computer connected to the printer, or just the computers that want to print remotely?

---

### Post by Yendor on 2007-06-26
> **dbbolton said:**
> 2. Open your CUPS daemon configuration file: ```
gksudo gedit /etc/cups/cupsd.cong
```

Hate to nitpick, but this should read: ```
gksudo gedit /etc/cups/cupsd.conf
```For those of you who are more GUI minded, this worked for me:

On the computer connected to the printer to share:
Open System->Administration->Printing
Note the exact name of the printer you wish to share.
(i.e. Stylus-Photo-R300)
Under "Global Settings" select (make checked) "Share Printers"
Carefully read the notice informing you of the risk of exploits, debate about it briefly, then click "OK"
(or just forget about sharing your printer)

On the computer you want to access the printer through:
Open System->Administration->Printing
Under "Global Settings" select "Detect LAN Printers"
Carefully read the notice informing you of the risk of exploits, debate about it briefly, then click "OK"
Double-Click "New Printer" (or select Printer->ADD Printer)
Select "Network Printer" radio button on the window that pops up
in the URI: box, type:
ipp://<hostname>/printers/<printer name>
(i.e. ipp://192.168.1.1/printers/Stylus-Photo-R300)
Click "Forward"
Select Manufacturer, Model, and Driver to be the same as the sharing computer
(i.e. Epson, Stylus Photo R300, High Quality Image (Gutenrpint)(en)(Suggested))
Click "Forward"
Give it a mind-numbingly inappropriate Name, Description and Location to scare away any would-be snoopers.
Click "Apply"

---

### Post by dbbolton on 2007-06-26
> **Yendor said:**
> Hate to nitpick, but this should read: ```
gksudo gedit /etc/cups/cupsd.conf
```
well, thank god somebody caught it, before any real damage was done.

---

### Post by Yendor on 2007-06-26
> **dbbolton said:**
> well, thank god somebody caught it, before any real damage was done.

My wife tried setting things up so she could print from her computer, and ended up coming to me because she couldn't get it to work.  She was following this tutorial.  No, there wasn't any real damage, but there was some very real frustration.  I posted in hopes of clarifying for others so they didn't suffer through the same frustration.  It seems to me, if your going to write a tutorial, it should be accurate.  It also seems to me, if you post a legitimate correction, it shouldn't be responded to with sarcasm.

---

### Post by Mickeysofine1972 on 2007-06-27
Hey How about a HOWTO: connect to a password protected network printer using CUPS?

Mike

---

### Post by dbbolton on 2007-06-27
> **Yendor said:**
> My wife tried setting things up so she could print from her computer, and ended up coming to me because she couldn't get it to work.  She was following this tutorial.  No, there wasn't any real damage, but there was some very real frustration.  I posted in hopes of clarifying for others so they didn't suffer through the same frustration.  It seems to me, if your going to write a tutorial, it should be accurate.  It also seems to me, if you post a legitimate correction, it shouldn't be responded to with sarcasm.
i was only kidding.

---

### Post by dbbolton on 2007-06-27
> **Mickeysofine1972 said:**
> Hey How about a HOWTO: connect to a password protected network printer using CUPS?

Mike
it might be possible to make a device like a printer only accessible to members of a certain group. i'm not sure about password protection though. i'll have to do some reading about that.

---

### Post by RaZoR1394 on 2007-07-01
Thanks I had to edit this section too:

# Restrict access to the admin pages...
#<Location /admin>
#  Order allow,deny
#  Allow localhost
#</Location>

<Location /admin>
  Order Deny,Allow
  Allow From 127.0.0.1
  Allow From 192.168.1.*
</Location>

---

