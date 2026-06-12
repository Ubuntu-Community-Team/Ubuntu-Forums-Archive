---
title: "[SOLVED] MS Access App ported to Ubuntu"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Texas Longhorns on 2008-10-16
Does anyone know if you if you can directly port a MS Access Database with embedded VBA code and Macros tied to MS Outlook to Ubuntu. (Automated Email system Send out to our customers via our database). If not, what are your recommendations/strategy regarding my MS Access port.

Thanks everyone for your feedback. My original thought was to prove that we could move away from windows XP (And any Vista OS) via a ubuntu and its base applications, as a proof-of-concept. 

If I understand everyone - I can't directly port my MS app over to Ubuntu. If I want my app on Ubuntu, it requires me plan a major app rewrite. So I ask each of you what's the attraction to run Ubuntu in a business environment? Remember, I'm the new guy.

---

### Post by NESFreak on 2008-10-16
openoffice partially supports it. Some say support has dramatically increased with the new OOo3.0 release.

---

### Post by chrisod on 2008-10-16
Well, VB script doesn't run in Ubuntu, and Outlook doesn't run in Ubuntu, so the answer would be no. You could try running the whole thing in Wine, or run Windows in a virtual machine, but what is the point?

What are you trying to accomplish with Ubuntu? If you have a mission critical application that runs on Windows proprietary software you probably should stay with Windows unless you are willing to rewrite the app for mySQL or some other open source database. Oracle does have a Linux port - but I'm not sure if there are easy tools to port from Access to Oracle. Probably not.

On preview - I totally forgot about OOO. The dB itself should export to OOO OK, but you'll have to redo all the scripting.

---

### Post by Therion on 2008-10-16
I'm thinking the issue is going to be the Outlook Macros.  I know Open Office/Calc supports Microsoft's VB generally speaking but I can't say from loads of experience exactly *how well*.  

I have no idea regarding the Outlook macros.  Any way to write up a couple quick Outlook macros and run an offline test?

---

### Post by chrisod on 2008-10-16
I haven't done much with the dB, but I have not had much luck with the scripting in Excel working 100% right in OOO.  However, that was OOO 2.0. I haven't even downloaded 3.0 yet.

---

### Post by LowSky on 2008-10-16
> **Texas Longhorns said:**
> Does anyone know if you if you can directly port a MS Access Database with embedded VBA code and Macros tied to MS Outlook to Ubuntu. (Automated Email system Send out to our customers via our database). If not, what are your recommendations/strategy regarding my MS Access port.

I would suggest staying with Windows, OOo3 regardless of its new abilities still will not do everytinh easily, not to mention Outlook isn't supported.

So If you really want Ubuntu then you willl have to redesign the Database with MySQL or OpenOffice Base.. and then use Thunderbird or Evolution

---

### Post by NESFreak on 2008-10-16
> **LowSky said:**
> I would suggest staying with Windows, OOo3 regardless of its new abilities still will not do everytinh easily, not to mention Outlook isn't supported.

So If you really want Ubuntu then you willl have to redesign the Database with MySQL or OpenOffice Base.. and then use Thunderbird or Evolution
Wouldn't that be a bit to dramatic?
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12) dont know how successful any MS office version runs under wine, since OOo has always been enough for me.

---

### Post by Texas Longhorns on 2008-10-16
Thanks everyone for your feedback. My original thought was to prove that we could move away from windows XP (And any Vista OS) via a ubuntu and its base applications, as a proof-of-concept. 

If I understand everyone - I can't directly port my MS app over to Ubuntu. If I want my app on Ubuntu, it requires me plan a major app rewrite. So I ask each of you what's the attraction to run Ubuntu in a business environment? Remember, I'm the new guy.

---

### Post by chrisod on 2008-10-18
There are always going to be costs associated with converting from one system to another. That is not a weakness of Ubuntu (or Linux in general), it's just a fact of life. The problem here is not that Linux can't run a Windows app, it's that the application is written in a proprietary tool that only works on the vendor's OS. If it was developed on Open Office on Windows originally (ignoring the Outlook issues), moving to Ubuntu would be trivial. Or it could have been done in mySQL, which runs on multiple operating systems.

Generally speaking, the cost of ownership for Linux is going to be lower. You aren't paying extravagant license fees for software, you aren't rebuilding computers every 6 months when somebody gets hosed by a virus, you aren't forced by vendors to pay for expensive upgrades when they EOL software because they need a revenue bump. You can run Linux on less powerful machines and stretch out the upgrade cycle. Hit Google, there are countess resources addressing the "Windows versus Linux in the Enterprise" question.

The bottom line though is that if you have mission critical applications developed in Windows closed source proprietary technology, you are probably stuck with Windows.

---

