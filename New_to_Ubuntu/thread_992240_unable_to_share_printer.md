---
title: "unable to share printer"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-24
I have mixed network of ubuntu and xp machines.two laptops 1 ubuntu and 1 xp and a dual boot desktop which has the usb printer attached.

I want to be able to print to a printer which is attached to my ubuntu desktop, from a windows laptop.

I have used cups on the desktop and enabled sharing and can print from the ubuntu laptop to this printer  but unable to print from windows one.

I have samba installed on the desktop as well, and can share folders between all machines.

Do i have to disable cups could it be in conflict with samba

---

### Post by cmnorton on 2008-11-24
CUPS is how you print; SAMBA merely provides the connection from Windows systems. You'll need to modify the printer section. Unfortunately, I am writing this from a Windows system, and don't have my samba config running. There is a sample (usually) [printers] section in /etc/samba/smb.conf. You'll need to edit it using sudo.

---

### Post by DieB on 2008-11-24
well with a little googling I found:

[http://www.cups.org/articles.php?L230+T+Qcups+on+windows](http://www.cups.org/articles.php?L230+T+Qcups+on+windows)


hope that is a help

---

### Post by Kellemora on 2008-11-24
Hi cork

Have you SHARED the printer itself?????

That seems to be the most common thing overlooked.

ALSO, you MUST have a print driver FOR THAT PRINTER on whatever machine you are sending the print job from.

For example:  If I'm sending a print job from an Ubuntu machine, CUPS is what handles the print job and spools it, then sends it over the LAN via Samba to the printer on a Windows Machine.  
By the same token, If I'm sending a print job from the Windows Machine, the printers Windows Driver handles the print job and spools it, then sends it over the LAN via Samba to the printer on the Ubuntu Machine.  I don't think CUPS ever sees it, but I could be wrong.

I do know the Windows program that came with the printer, which doesn't have anything to do with the actual printing print driver, pops up and says Downlevel Document being sent to Printer on USB3.

I think I can be safe in saying that because I accidentally plugged the printer into the wrong computer and all I did was set it to SHARE and it printed to it just fine!  Actually FASTER than to a Doze machine!

In other words, once the spooled file hits the LAN it's already in the form the printer needs to print it.  So the driver must be on the computer sending the print job.  Cups on Ubuntu, A Winders driver on Winders!

TTUL
Gary

---

### Post by rhcm123 on 2008-11-24
> **cmnorton said:**
> CUPS is how you print; SAMBA merely provides the connection from Windows systems. You'll need to modify the printer section. Unfortunately, I am writing this from a Windows system, and don't have my samba config running. There is a sample (usually) [printers] section in /etc/samba/smb.conf. You'll need to edit it using sudo.

This is my samba file. It forces guest only on user nobody, and i'll explain that here in this thread and then you can just copy paste the file. I prefer to use nobody because it has no priviliges, and is very safe if hacked.

Open terminal on the computer with the printer. Type:
```

~$sudo passwd nobody
(type a password, retype to confirm)

~$login
(it will give you a terminal login window, you cannot by defualt login as nobody with the graphic interface, after login, it will add you to the users list)

~$logout
(this will take you back to the root prompt)

~$sudo smbpasswd nobody
(this will set the samba password for nobody, i just leave it the same as the unix user)

```

That will get your users going.
To add the printer, add the following lines to your smb.conf file:
```

~$sudo nano /etc/samba/smb.conf
(add these lines):
[global]
        log file = /var/log/samba/log.%m
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        map to guest = Bad User
        wins support = true
        dns proxy = No
        netbios name = (JUST TYPE YOUR HOSTNAME)
        server string = (Name your Server, i use Samba-CUPS on [hostname])
        default = Share
        local master = No
        workgroup = (ADD YOUR WINDOWS WORKGROUP!)
        os level = 20
        security = user
        preferred master = no
        max log size = 50
	printing = CUPS
	printcap name = CUPS
	guest account = nobody

[printers]
	browseable = yes   
	printable = yes   
	public = yes   
 	create mode = 0777   
 	guest only = yes   
 	use client driver = no   
	path = /printer

```
Note: You might have to modify your own settings and not just copy pasta this thing in, as i wiped my smb.conf file and replaced it with just that as the only thing my 1999 laptop does is print stuff.

You will have to do 1 more basic step to get this working. This is because the print documents (ones waiting on the computer to be sent to the printer) need to be stored somewhere, and that is used with the "path" variable above. Either make your own directory or do what i did:
```

~$ sudo mkdir /printer
(this will make the /printer directory mentioned above)
~$ sudo chown /printer nobody
(this will make the directory owned by nobody)
~$ sudo chmod 700 /printer
(this will set priviliges so that nobody has full read/write)

```

Be sure to have your printer properly set up and sharing enabled!
HOPE THIS HELPS!!!!

---

