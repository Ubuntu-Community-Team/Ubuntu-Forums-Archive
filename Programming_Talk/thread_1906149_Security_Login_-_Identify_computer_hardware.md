---
title: "Security Login - Identify computer hardware"
date: 2012-01-08
forum: Programming Talk
---

### Post by MaxVK on 2012-01-08
Hi, I might get shot down with this question, but unless I ask....

I am using PHP and Javascript to create a web based database application for in-house use by a small company. Things are now progressing nicely.

One of the requirements is that members of the company workforce are able to log into this system from elsewhere (IE: Not on the local network and via the internet). Of course I can use a normal PHP login for this sort of thing, but out of curiosity I have the following question:

Bearing in mind that all company workers will be using company machines installed with Ubuntu by myself, and are therefore compliant with anything I need to install, is there a way to allow a log-in via the internet (To a server running at the company HQ) ONLY from specific machines using some kind of hardware recognition?

I know this is a long shot, and that mac address etc, is not transferred via the http protocol, I was just wondering if there were any alternatives available.

Cheers

Max

---

### Post by ofnuts on 2012-01-08
> **MaxVK said:**
> Hi, I might get shot down with this question, but unless I ask....

I am using PHP and Javascript to create a web based database application for in-house use by a small company. Things are now progressing nicely.

One of the requirements is that members of the company workforce are able to log into this system from elsewhere (IE: Not on the local network and via the internet). Of course I can use a normal PHP login for this sort of thing, but out of curiosity I have the following question:

Bearing in mind that all company workers will be using company machines installed with Ubuntu by myself, and are therefore compliant with anything I need to install, is there a way to allow a log-in via the internet (To a server running at the company HQ) ONLY from specific machines using some kind of hardware recognition?

I know this is a long shot, and that mac address etc, is not transferred via the http protocol, I was just wondering if there were any alternatives available.

Cheers

MaxNothing that  a good hacker won't be able to forge :)  The usual way to solve this problem is to not expose the web site to the internet, keep it accessible from the company intranet only, and provide VPN access to the intranet to employees.

---

### Post by Tony Flury on 2012-01-09
I would agree - if you want decent security then some form of VPN is the way to go.

It depends on the data - a lot of big companies have public available email servers so that employees can log in without needing to connect to VPN's - here the security is determined by the password, and not by any physical hardware check.

---

### Post by Bachstelze on 2012-01-09
> **ofnuts said:**
> Nothing that  a good hacker won't be able to forge :)

Or, much more likely, steal.

---

### Post by ofnuts on 2012-01-09
> **Bachstelze said:**
> Or, much more likely, steal.I thought about that one, but if they have a list of allowed hardware, they can quickly remove the stolen equipment from it.  And stolen hardware doesn't go unnoticed for long, unlike a copied password or certificate.

---

### Post by MaxVK on 2012-01-09
Thanks for your time guys.

I was thinking about this at work and my current thinking is that the home page (The one *before* the log in page) would be on the local machine rather than online. 

It would read a file on that local machine (encrypted) that contained a code of some kind. The log in link on that page would actually take the user online, but the code would be passed along with the log in details (user name and password) but unseen in the background.

This would allow a log on from specific machines and it is easy enough to disable a code from the server if a machine is lost/stolen.

For sure any determined hacker could find the code, but in doing so they would need access to the machine for some time so that they could read all the code and work out the encryption etc, by which time the machine would be recorded as missing and the code would be defunct.

I know this seems a bit of hard work for quite a small thing, but the company are insistent that they want an extra layer of security.

Just to fill in the gaps - each employee who goes out with a laptop will be doing so from the HQ at least three times a week, and the laptop is used for pretty much the whole day, and in close proximity to the team on the road. Theft of the laptop would be noticed and reported pretty quickly.


> if you want decent security then some form of VPN is the way to go
Thanks for this - I didn't think along those lines so Ill look into it. The server would be in the HQ and running connected to the internet so that teams on the road can log in to get information about jobs etc, when they need it.

Any further thoughts would be gratefully received.

Cheers

Max

---

### Post by ofnuts on 2012-01-09
> **MaxVK said:**
> 
It would read a file on that local machine (encrypted) that contained a code of some kind. The log in link on that page would actually take the user online, but the code would be passed along with the log in details (user name and password) but unseen in the background.
MaxYou are reinventing certificates. Better issue login certificates to the employees. This is supported by all browsers (FF>3, IE>5.5)

---

### Post by MaxVK on 2012-01-10
> You are reinventing certificates.
Ill look into this, but I don't need cross browser support - employees will be using Firefox.

---

