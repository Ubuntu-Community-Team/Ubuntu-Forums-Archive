---
title: "Pre-detection of harmful downloads ?"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by Innernet on 2013-02-25
The same way anti-virus scan files for danger; and some results from Google show "This site may harm your computer" ; is there a way in Ubuntu to scan a file to be downloaded from the net, to detect if will compromise the health of a system examining it**before downloading** ?

If not necessary, what in Linux makes Ubuntu impervious to a variety of malware ?

---

### Post by audiomick on 2013-02-25
This is a lot of stuff to read, but I suggest you at least fly over it.

This shortest answer to why what you are looking for is not needed is simply that there is not that much malware around aimed a Linux systems. 

Anyway, here is some info

[https://wiki.ubuntu.com/BasicSecurity]("https://wiki.ubuntu.com/BasicSecurity")
[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")
[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

Hope that helps you...

---

### Post by mike555 on 2013-02-25
To show bad sites install "WOT" add-on to browser ..

---

### Post by TimeCrank on 2013-02-25
I agree with adiomick there is really no need for anti-virus, Generally Ubuntu Linux is hardly effected by virus and the reason is its structure and strong community support, any loopholes are worked immediately. For every new virus, its solution is out within two hours thus preventing it to do any further damage. Linux antivirus are also effective against the Windows virus and they are removed if they enter your systems through external hard drive, internet etc.

If your really concerned about it, here is the top free open-source software.
*************************************************************************************

ClamAV Antivirus :
ClamAV is the most popular open source anti-virus software and it is available for both Ubuntu and Kubuntu. Its GUI interface is called Clamtk.
It can be install from the software center or in terminal type
```
$sudo apt-get install clamav clamtk
```[FONT=&quot]**\\:D/**[/FONT]

---

### Post by DuckHook on 2013-02-25
> **TimeCrank said:**
> Linux antivirus are also effective against the Windows virus and they are removed if they enter your systems through external hard drive, internet etc.

I would agree with your statement if you changed the word "also" to "only". That is to say, Linux Antivirus is *only* effective against Windows virii. It is not possible to "attack" a threat that doesn't exist or "solve" a problem that isn't a problem. Therefore, Clam AV serves no purpose on a Linux system.

Frankly, putting antivirus on a Linux system is not only pointless--it fills your system with worthless bloatware that eats up resources, slows everything down and makes Linux resemble nothing so much as Windows. If you like Clam AV, then install it in your Windows system where it serves the purpose for which it exists. Installing it on Linux is like attaching wings to a freight train.

---

### Post by Innernet on 2013-02-25
Thanks, gentlemen.

Minutes ago, the attached showed up, from a site I visit almost daily, had not shown before, and had no changes in my 'security preferences'

Ignore ?  Can it be harmful ?  Hoax ?  :confused:

---

### Post by alphacrucis2 on 2013-02-25
That's a setting in Firefox - default action is to block reported websites. Same default behaviour for Firefox in Windows. Probably safer to leave it on. I presume the website has been blocked for a good reason. If you want to ignore the warning, you can but it is at your own risk.  I believe the "bad site" list is maintained by google.

---

### Post by DuckHook on 2013-02-25
> **Innernet said:**
> Ignore ?  Can it be harmful ?  Hoax ?

You are asking us an impossible question. We don't know this site from Adam. For all we know, it is a malware site, or it has been hijacked.

There are generally accepted procedures for dealing with these sorts of issues:

Contact the web admin and ask them why they suddenly register on Firefox's bad site list, Google for info on recent hijackings, etc.

---

