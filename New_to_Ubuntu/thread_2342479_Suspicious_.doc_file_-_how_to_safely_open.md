---
title: "Suspicious .doc file - how to safely open?"
date: 2016-11-07
forum: New to Ubuntu
---

### Post by cwmoser on 2016-11-07
Got a suspicious *.doc file in my email.
Don't want to just open it with LibreOffice.
Tried to open it with antiword viewer but it fails - something about Macros.

So, my question is, what is a best practice to deal with suspicious doc files?
Like to be able to open the file but have anything malicious disabled.

---

### Post by howefield on 2016-11-07
Delete it.

Or run it through an online virus scanner if you don't have one installed locally, most of the "well known" vendors have such a service, free of charge.

---

### Post by vasa1 on 2016-11-07
> **cwmoser said:**
> ... - something about Macros.
...
I think opening it in LibreOffice should be quite safe. Macros from a document created in Windows using Word don't work in LibreOffice (whether Linux or Windows).

---

### Post by mastablasta on 2016-11-07
the safe way to open it:
1. install virtualbox or similar virtualizaiton software
2. install an OS (something light like Lubuntu) inside virtualbox and lock down network access for the os (e.g. disable network device).
3. make a snapshot of the device.
4. open the file (you can also install monitoring software and then see if anything happens)
5. if it is malicious - restore the OS snapshot. or just delete the whole virtual appliancion.

scanning before opening is also a good idea.

---

### Post by cwmoser on 2016-11-07
> **mastablasta said:**
> the safe way to open it:
1. install virtualbox or similar virtualizaiton software
2. install an OS (something light like Lubuntu) inside virtualbox and lock down network access for the os (e.g. disable network device).
3. make a snapshot of the device.
4. open the file (you can also install monitoring software and then see if anything happens)
5. if it is malicious - restore the OS snapshot. or just delete the whole virtual appliancion.

scanning before opening is also a good idea.

Thanks.  Didn't think of this.
I do have VMware and Virtual Box but I didn't "connect the dots" as they say.
So I should make a snapshot to save my VM, then open the file and restore the snapshot if something goes wrong.
Think I'll give it a go.  Always wanted a safe process to deal with issues like this.

---

### Post by irraref on 2016-11-07
didn't know that .doc documents can be dangerous in ubuntu...

---

### Post by RobGoss on 2016-11-07
If I felt there was any suspicious docs of any kind I would not open it just delete it

---

### Post by Habitual on 2016-11-07
upload it to virustotal.com and let them analyze it.

---

### Post by SeijiSensei on 2016-11-07
Email messages containing MS Office files with malicious macro scripts are a widespread problem these days.  If it appears the file came from someone you know, ask her if she sent it to you.  It's more likely the sender's address was forged.  If you don't recognize the sender, delete it.

At one client's site we use clamd to scan every attached file.  Ones with macros are automatically marked as infected (see the "OLE2BlockMacros" directive in clamd.conf) and quarantined.

---

### Post by cwmoser on 2016-11-07
> **Habitual said:**
> upload it to virustotal.com and let them analyze it.


Thanks.  That certainly was convenient. 

VirusTotal.com confirmed my suspicion that it was a threat:

```

 Antivirus 	        Result 	Update
AVG 	                W97M/PWS 	20161108
AhnLab-V3 	W97M/Downloader 	20161107
Avira (no cloud) W2000M/Agent.50611572 	20161107
Fortinet 	        WM/Agent.63A3!tr 	20161108
Kaspersky 	        Trojan.VBS.Agent.aep 	20161108
McAfee 	        Downloader-FBJE!79681A3EACA9 	20161108
McAfee-GW-Edition 	Downloader-FBJE!79681A3EACA9 	20161108
Qihoo-360 	heur.macro.powershell.b 	20161108
Symantec 	        W97M.Downloader 	20161108
TrendMicro-HouseCall 	W2KM_HANCITOR.YYSWZ 	20161108 

```

---

### Post by mastablasta on 2016-11-08
> **SeijiSensei said:**
> Email messages containing MS Office files with malicious macro scripts are a widespread problem these days.  If it appears the file came from someone you know, ask her if she sent it to you.  It's more likely the sender's address was forged.  If you don't recognize the sender, delete it.
.

2 days ago in search of an IM to replace Skype i found qTox. donwloading it from official site to a widnows PC made my antivirus go balistic. it demanded that i upload it to them and blocked all access to the file. after wrestling with overriding the denied access the whole thing crawled down and stopped the PC (so i hard rebooted it). anyway it is all working now and next day i got also recived a desktop notification that the virus was checked and found safe. 


so yes depends on where suspicions come from. sometimes they are unfounded or we know it should be good, but then again you can't be sure that the sender is maybe not infected. when i send out files ot cusotmers i would work to remove macros from them. if there are any that really have to be inside i would specify that along with file size. come ot think of it ... i could also give a md5sum or SHA1 hash. heh, just thought of that. i doubt they would know how to check it though. one of my trusted USA clients once had their laptop took over by maleware. so you never know what you are going to get.

---

### Post by SeijiSensei on 2016-11-08
Before we started blocking files with macros, one of the people at my client's site received such a document.  Since the versions of Office running on the network were configured not to run macros by default, the document had an explicit instruction to "click here to enable running macros then click the link below."  So this person merrily disabled the protection against macro viruses and promptly got infected.  After that experience we starting blocking documents that contained macros sent by email using clamd and MailScanner.

---

### Post by cwmoser on 2016-11-08
I know curiosity killed the kitty cat, and I am curious.
Many years ago I did some programming with Word Macros in a job I had.
If say I opened that file with LibreOffice, would the Macros that would infect Microsoft Word
also affect Writer?
Are there threats in the wild that attack Writer?

---

### Post by mastablasta on 2016-11-08
from LO wiki: [URL="https://help.libreoffice.org/Common/Using_Microsoft_Office_and#Macros_in_Microsoft_Office_and_LibreOffice"]https://help.libreoffice.org/Common/Using_Microsoft_Office_and#Macros_in_Microsoft_Office_and_LibreOffice
[/URL]

> 
**Macros in Microsoft Office and LibreOffice**

With a few exceptions, Microsoft Office and LibreOffice cannot run the same macro code. Microsoft Office uses VBA (Visual Basic for Applications) code, and LibreOffice uses Basic code based on the LibreOffice API (Application Program Interface) environment. Although the programming language is the same, the objects and methods are different.
[TABLE]
[TR]
[TD][[IMG]https://help.libreoffice.org/images/c/cc/Note.png[/IMG]]("https://help.libreoffice.org/File:Note.png")[/TD]
[TD]The most recent versions of LibreOffice can run some Excel Visual Basic scripts if you enable this feature at **Tools - Options'** *- Load/Save - VBA Properties'*.[/TD]
[/TR]
[/TABLE]
If you use macros in one of the applications and want to use the same functionality in the other application, you must edit the macros. LibreOffice can load the macros that are contained within Microsoft Office files and you can then view and edit the macro code in the LibreOffice [Basic IDE]("https://help.libreoffice.org/Common/Programming") editor.
**You can choose to preserve or delete VBA macros**

Open a Microsoft Office document that contains VBA macro code. Change only the normal contents (text, cells, graphics), and do not edit the macros. Save the document as a Microsoft Office file type. Open the file in Microsoft Office, and the VBA macros will run as before.
You may delete the VBA macros from the Microsoft Office file on loading or on saving.

[LIST=1]
[*]Choose '*Tools - Options'* **-** [Load/Save - VBA Properties]("https://help.libreoffice.org/Common/VBA_Properties") to set the VBA macro handling of LibreOffice.
[/LIST]


---

