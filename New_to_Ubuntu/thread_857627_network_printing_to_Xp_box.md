---
title: "network printing to Xp box"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by hellomoto on 2008-07-12
hello I have an XP machine as a print server. And I would like to print to it via my ubuntu box.

I have tried adding a new printer via system>admin>print as follows:

- I select add new printer icon.

- select WINDOWS printer via SAMBA

-for the smb printer I click browse and it CAN see my printer on the network. So i select that.

- for authentication required i have tryed guest, the windows username + pword, my ubuntu user name + pword and leaving it blank.

- I then click verify and after about 1-2 minutes I get the following error:

> "Inaccessible. This print share is not accessible."

Also I have followed  [Printing to Windows XP printer from Ubuntu]("https://help.ubuntu.com/community/WindowsXPPrinter")
Any ideas please?

---

### Post by cariboo on 2008-07-12
I just setup my printer, Under Authentication I have "Prompt if authentication is needed" checked, and then continue on from there.

I've been doing this for years and never had a problem.

Jim

---

### Post by hellomoto on 2008-07-12
> **cariboo907 said:**
> I just setup my printer, Under Authentication I have "Prompt if authentication is needed" checked, and then continue on from there.

I've been doing this for years and never had a problem.

Jim


hiya, are using hardy? I am and I can't see that check box on my GUI

---

### Post by cariboo on 2008-07-12
No actually I'm running the Alpha 2 version of Intrepid. I'll just boot into Hardy and get back to you.

Jim.

---

### Post by oldsoundguy on 2008-07-12
stupid question .. have you enabled print sharing on the XP box?  I use an XP box as print server for my network and have 4 printers of various kinds hung from it .. no problem printing from any Gutsy box (I have 3) to those printers.

---

### Post by cariboo on 2008-07-12
I looks like they changed the interface a bit in the next version of Ubuntu. I just leave the Authentication required unchecked and then contiune. See attached screenshot.

Jim

---

### Post by hellomoto on 2008-07-13
> **oldsoundguy said:**
> stupid question .. have you enabled print sharing on the XP box?  I use an XP box as print server for my network and have 4 printers of various kinds hung from it .. no problem printing from any Gutsy box (I have 3) to those printers.

yep its shared as 2 other windows boxes can print to the server.




> **cariboo907 said:**
> I looks like they changed the interface a bit in the next version of Ubuntu. I just leave the Authentication required unchecked and then contiune. See attached screenshot.

Jim

I have tried it uncheck and am having no luck.


this is what i get when i run smbtree:

> 
mark@mark-desktop:~$ smbtree
STABLEFORD
	\\PRINTSERVER    		compaq
timeout connecting to 208.69.34.132:445
timeout connecting to 208.69.34.132:139
Error connecting to 208.69.34.132 (Operation already in progress)
cli_start_connection: failed to connect to PRINTSERVER<20> (208.69.34.132). Error NT_STATUS_ACCESS_DENIED
	\\MARK-DESKTOP   		mark-desktop server (Samba, Ubuntu)
		\\MARK-DESKTOP\PDF            	PDF
		\\MARK-DESKTOP\IPC$           	IPC Service (mark-desktop server (Samba, Ubuntu))
		\\MARK-DESKTOP\print$         	Printer Drivers
mark@mark-desktop:~$ 


What is NT_STATUS_ACCESS_DENIED and how do i fix it?

---

### Post by Dedoimedo on 2008-07-13
Hi,

Are you using a firewall on Windows machine? If your XP firewall or any third-party firewall is configured to block incoming connections, then you won't be able to connect.

Furthermore, see if this helps:
[http://www.dedoimedo.com/computers/linux_commands.html#network_sharing](http://www.dedoimedo.com/computers/linux_commands.html#network_sharing)

Cheers,
Dedoimedo

---

### Post by hellomoto on 2008-07-13
> **Dedoimedo said:**
> Hi,

Are you using a firewall on Windows machine? If your XP firewall or any third-party firewall is configured to block incoming connections, then you won't be able to connect.

Furthermore, see if this helps:
[http://www.dedoimedo.com/computers/linux_commands.html#network_sharing](http://www.dedoimedo.com/computers/linux_commands.html#network_sharing)

Cheers,
Dedoimedo

I have disabled the firewall on the print server whilst I am setting up.

I can access the share by putting in the IP via run command.. Which seams really odd. 

This would make me believe that the XP machine is having a problem recognising the smb name I am putting in as there isn't any problems accessing the share via IP.

Is there any way I can access the shared printer via its IP rather than share name?

---

### Post by Dedoimedo on 2008-07-13
Hello,

To use the names, the two need to belong to the same workgroup. Make sure this is the case.

If this does not help, you can use the /etc/hosts file to define the entry for the XP machine. For example:

192.168.10.123  xp-machine

Thus, when you try to access xp-machine, it will point to the IP.

Dedoimedo

---

### Post by jw5801 on 2008-07-15
I'm seeing what appears to be the same issue. If you'll note in my smbtree output below, the IP that I'm attempting to connect to is not correct in the slightest. The IP that should be pointed to is 192.168.0.2, yet I'm being pointed to 208.67.219.132, which isn't even the routers external IP.
```
[ ~ ] smbtree 
Password: 
MSHOME
        \\YOUR-1695C3D4B4               WEBSCAPE
timeout connecting to 208.67.219.132:445
timeout connecting to 208.67.219.132:139
Error connecting to 208.67.219.132 (Operation already in progress)
cli_start_connection: failed to connect to YOUR-1695C3D4B4<20> (208.67.219.132). Error NT_STATUS_ACCESS_DENIED
```

I haven't installed samba, as I don't want to run a samba server or share anything from this machine, simply print to the XP machine. Installing the samba server, and setting up the workgroup as shown in the link Dedoimedo provided, acheived nothing more than show the printers set up on this computer (that I used to be able to connect to) under this machine in smbtree. The other machine still could not be connected to, and still reported the same, wrong IP.

---

### Post by Dedoimedo on 2008-07-15
Hi,
Maybe you could try to manually detect and assign a printer.
I did it this quite a few times and it worked well.
Dedoimedo

---

### Post by jw5801 on 2008-07-15
> **Dedoimedo said:**
> Hi,
Maybe you could try to manually detect and assign a printer.
I did it this quite a few times and it worked well.
Dedoimedo

Not quite sure what you mean by 'manually detect and assign a printer'. I've been using the 'Printing' menu entry, which seems to work fine. I can browse the samba shares and see the workgroup and host, as well as the printers shared by the host. When it comes time to actually connect to the printer (or anything on the host, or any host) however, samba fails to resolve a correct IP for the host, and instead attempts to connect to an odd IP.

I can both browse the share and print through it, if I use the machines IP. ie. smb://192.168.0.3/ rather than smb://WORKGROUP/HOSTNAME/

---

### Post by LowSky on 2008-07-15
I too had issues setting up a shared printer

I have had better luck with CUPS and using the linux machine as the host

[http://localhost:631/](http://localhost:631/)

---

