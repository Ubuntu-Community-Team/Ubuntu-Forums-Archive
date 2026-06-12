---
title: "I can not browse and add printer"
date: 2018-08-30
forum: New to Ubuntu
---

### Post by simpos on 2018-08-30
Good night, I'll use a translator:


I have a USB connected printer on a Windows 7 Pro, and shared to the network, in this place I have a Xubuntu 16.04 and another room Xubuntu 18.04, both completely updated.


When in 16.04.5 I put the Ricoh printer in Printers> Add> Windows Printer via Samba> Browse, Linux required the installation of something related to python and already presented the wizard to install, after installed the Navigate function became available and accessible to see the groups and pc's of network.


Now on 18.04.1 I performed the same procedures, but when clicking on Browse something was also missing but did not show the wizard to install python, a popup appeared for the Xubuntu Store, clicking the Store simply said that it did not exist or unavailable, so I installed python3-smbc manually, this corrected and allowed to click Browse, until the navigation window appears but quickly the message below occurs:
"No print sharing was found Please make sure the Samba service is marked as trusted in your firewall configuration"
[ATTACH=CONFIG]280918[/ATTACH][ATTACH=CONFIG]280917[/ATTACH]


I have already checked the ufw status and the firewall is inactive, so why does this happen?

---

### Post by SeijiSensei on 2018-08-31
What if you navigate to [http://localhost:631/](http://localhost:631/) and add the printer that way?

---

### Post by simpos on 2018-08-31
> **SeijiSensei said:**
> What if you navigate to [http://localhost:631/](http://localhost:631/) and add the printer that way?

Also tried, the printer is added, but printing requires authentication for every printout made, and there is no requirement for print authentication.


In short everything remains wrong, while in 16.04 everything works.

---

### Post by simpos on 2018-08-31
At the moment I believe I was able to insert by the cups, putting by the host instead of the IP.


The problem now is that the print is retained and requires user and password, I even put the root but indicated as the wrong password, but it sure is not, I tried because Windows did not give, I do not know what is missing.

---

### Post by SeijiSensei on 2018-09-01
You'll have to examine the authentication settings for the printer on the Windows side.  That's where the authentication request comes from.

---

### Post by simpos on 2018-09-01
> **SeijiSensei said:**
> You'll have to examine the authentication settings for the printer on the Windows side.  That's where the authentication request comes from.

But everything is released, no firewall, Windows without password, network settings with full permission (do not ask for password to enter the network etc ...)


The printer does not have a password set on the panel, even though it is very old, it is a Ricoh SP 3200SF.


I think it's some privacy parameter inside cupsd, I'm virtualizing and it's exactly the same thing on my notebook with a shared printer for VB with the bridge network.

---

### Post by kurt18947 on 2018-09-02
I know nothing of SAMBA and am just a home user. I've had very good luck though printing via a network connection rather than trying to share a printer. If the printer doesn't have a built in ethernet port, USB or parallel port print servers are relatively inexpensive. Each machine 'talks' directly to the printer, no translation via SAMBA required. I did try SAMBA some years ago and could never get it to do what I wanted. Of course I was even less knowledgeable then than I am now.

---

### Post by SeijiSensei on 2018-09-02
Your router might have a print server built-in. Otherwise there are products like this

[https://m.newegg.com/products/9SIA6PF41B0120](https://m.newegg.com/products/9SIA6PF41B0120)

---

### Post by simpos on 2018-09-03
> **SeijiSensei said:**
> Your router might have a print server built-in. Otherwise there are products like this

[https://m.newegg.com/products/9SIA6PF41B0120](https://m.newegg.com/products/9SIA6PF41B0120)

But I mentioned the opening of the topic, I have another room with 16.04 that everything is working, what may be different in this 18.04 that is generating this window of authentication, really is a mystery.


Below is the link for captures:
[https://drive.google.com/drive/folders/1HIuYEF10TyyuFsvi-7obVau3VniNFKBM](https://drive.google.com/drive/folders/1HIuYEF10TyyuFsvi-7obVau3VniNFKBM)
1 - Windows 7 (Server): Ricoh Security
2 - Xubuntu 18.04 (Client): Authentication when sending printout
3 - Xubuntu 18.04 (Client): Print Status
4 - Xubuntu 18.04 (Client: Owned Print Hold
5 - Xubuntu 18.04 (Client): How I added the printer
6 - Xubuntu 18.04 (Client): cupds
7 - Xubuntu 18.04 (Client): cups-file
8 - Xubuntu 18.04 (Client): samba (I admit that I tried to use "force user" but it did not work)

I even configured the router, everything is according to DHCP and etc

---

### Post by simpos on 2018-09-04
Well I've been reading many forums, maybe 20 different ones, with expressively long dates, between 2007 until today ...


and I discovered one thing, that this authentication window is not a problem, but a CANCER, long and long threads of people spinning around unsuccessfully.


I must have virtualized a 10 machines, tried dozens of things, this is an ill-resolved problem of Linux, I do not know how Torvalds sleeps quietly.

---

### Post by kurt18947 on 2018-09-09
My guess is that this is not a Linux problem but a GNU, CUPS or SAMBA problem. Linux is only the kernel and I suspect that is not the issue. I have 3 printers operating on 18.04 with no issues at all, as do many others. You and others have a certain combination of software and permissions that are causing issues. Do you have a means to completely bypass Windows/Samba temporarily? Somehow attach your machine running Xubuntu directly to the printer via USB or ethernet? If so, make the changes in the Xubuntu printers app showing the new connection, make sure printing and sharing are enabled then try to print. If it prints, that would indicate the problem lies somewhere in the SAMBA/Windows portion. If it doesn't, there's something with Xubuntu. I had a problem once where I couldn't print after working perfectly on the same Ubuntu version and machine. Printing was turned off in the Printers app, I have no idea why.

---

### Post by simpos on 2018-09-09
In fact I already set up another medium, I put the printer directly through the ethernet port, and all Xubuntu automatically found the printer and printed without problems.


The problem is when Xubuntu tries to join the Windows printer, I've already managed to run the printer via USB on Xubuntu and share for Windows, but otherwise the Cups is very difficult for years to date

---

