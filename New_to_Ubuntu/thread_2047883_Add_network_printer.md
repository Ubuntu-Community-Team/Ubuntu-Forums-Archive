---
title: "Add network printer"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Frank P on 2012-08-25
12.04 LTS server
I have 2 networked printers accessed on my Windows network via router - 1 cabled, 1 wireless
I want to print to them from my Ubuntu server
I can find lots of info on setting them up if they where physically attached to the server but I want to leave them as networked
Where can I look for this information
 
Thanks
 
Frank P

---

### Post by androssofer on 2012-08-26
> **Frank P said:**
> 12.04 LTS server
I have 2 networked printers accessed on my Windows network via router - 1 cabled, 1 wireless
I want to print to them from my Ubuntu server
I can find lots of info on setting them up if they where physically attached to the server but I want to leave them as networked
Where can I look for this information
 
Thanks
 
Frank P

never done it, but is this any help?

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Frank P on 2012-08-26
I've checked that page and several others that are similiar. Unless I'm misreading something they all seem to use some sort of GUI  that finds the printers automatically. I can't seem to find a command line command that does the same thing
 
Thanks
 
Frank P

---

### Post by Morbius1 on 2012-08-26
CUPS on the Ubuntu server has a Web interface:

From a client machine open an internet browser and type:
```
192.168.0.100:631
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the ubuntu server*[/COLOR]

Click the Administration tab > Under "Server" select "Show Printers Shared by Other Systems"

If the CUPS gods are smiling on you today if you then go to the "Printers" Tab a list of all network printers will show up. If not:

Administration > Printers > Add Printer. You will see all sorts of protocols you can use to connect to the networked printer: Samba ( SMB ), lpd, ipp, ipp14 ( for compatibility to a previous version of cups ), etc...

---

### Post by Frank P on 2012-08-28
okay, I've made some progress, I think:mad: I'm now getting a Forbidden message when I try to acces via the browser so it knows it's there.
I'll keep trying
 
Thanks
 
Frank P

---

### Post by Frank P on 2012-08-28
okay, it's working. I had to change <location /> to allow all. Found answer in an old post in this forum
 
I'll to to mark it solved
 
Thanks
 
Frank P

---

