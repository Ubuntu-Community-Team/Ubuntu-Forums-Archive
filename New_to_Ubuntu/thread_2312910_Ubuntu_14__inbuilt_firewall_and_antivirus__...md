---
title: "Ubuntu 14  inbuilt firewall and antivirus  .. ?"
date: 2016-02-08
forum: New to Ubuntu
---

### Post by will111 on 2016-02-08
Hi,

Total newbie to Ubuntu and rather baffled by the many web pages debating the value of Linux third party Firewalls and Antivirus.

However its interesting that the Ubuntu 14 Desktop page says "SECURE With a built-in firewall and virus protection software"

So my first question is do they need to be enabled or are they on by default  ?  ( seems earlier versions you have to enable them )

My second question is am I right in assuming that,  unlike the third party firewalls and AV suites which are said to present a profile for hackers, these Ubuntu inbuilt ones are much safer ?

It seems that running a online third party AV scanner once in a while is a safe practice ? any suggestion as to which are the better ones ?

Final comment, while I do not have the ability to full understand the third party firewall/av situation, it would be good to see a forum like this, or even on Ubuntu main site,  giving a much clearer and qualified view on this subject for beginners; though please excuse me if there is somewhere, so much info to look at and try and take in !

thanks

---

### Post by maglin2 on 2016-02-08
The firewall isn't enabled by default (but there are no open ports in a default install).
```
sudu ufw enable 
```
will get the firewall going to block all incoming. 

Whether outbound firewall rules are useful for a linux desktop, and whether you should run an AV are 'recurring discussions'.

You will find many threads of this type, and the experienced consensus seem to me to be that there are other things that contribute far more to security than outbound firewall or AV.

---

### Post by grahammechanical on 2016-02-08
The Uncomplicated FireWall (UFW) is part of the default installation of Ubuntu. As already stated, it is not enabled by default. And there is a Graphical User Interface to it that we can install - Gufw. That will make things easier.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

The bit about "virus protection software" means that there are a couple of applications in the Ubuntu Software Centre. To be accurate, just one. It is not installed by default. Please do not think that anti-virus software is built into Ubuntu.

Regards.

---

### Post by Habitual on 2016-02-08
I never use it on desktop systems.
15 years in Linux and never seen a Linux virus yet.

---

### Post by ian-weisser on 2016-02-08
> **will111 said:**
> ...
So my first question is do they need to be enabled or are they on by default  ?  ( seems earlier versions you have to enable them )

My second question is am I right in assuming that,  unlike the third party firewalls and AV suites which are said to present a profile for hackers, these Ubuntu inbuilt ones are much safer ?

Your old Windows habits are leading you astray.
Ubuntu is not Windows.
Ubuntu, as others have noted, does not have open ports by default that you need to block with a third-party firewall. Most users find that properly managing their services is adequate protection.
Ubuntu's malware and antivirus scheme is totally different from Windows. Ubuntu components are regularly updated to patch known vulnerabilities. So a separate 'Antivirus' application is generally uneccessary.
Ubuntu has a very different permission structure than Windows. A compromised application cannot wander through your system, installing and replacing system files, installing backdoors, etc.

It's not foolproof.
You are still vulnerable to social-exploit and browser-based attacks...happily, most of those target Windows vulnerabilities instead of Linux vulnerabilities.
You can restrict or disable many security features, creating new vulnerabilities. The system will do it if you tell it to. Don't tell it to.
Some users do use an antivirus application (clamav) to clean files that they exchange with other users, to prevent spreading malware. That's a good idea if you share files with Windows and Mac users.

---

### Post by Geoffrey_Arndt on 2016-02-08
"Some users do use an antivirus application (clamav) to clean files that  they exchange with other users, to prevent spreading malware. That's a  good idea"
                                                                                                                                                                                      

Applies mainly to sharing files with users running Windows versus Linux systems.   (from what I've read).

.

---

### Post by sammiev on 2016-02-08
> **Geoffrey_Arndt said:**
> "Some users do use an antivirus application (clamav) to clean files that  they exchange with other users, to prevent spreading malware. That's a  good idea"
                                                                                                                                                                                      

Applies mainly to sharing files with users running Windows versus Linux systems.   (from what I've read).

.

+1

---

### Post by HermanAB on 2016-02-09
Hmm... relax and enjoy your Ubuntu system.  It is very unlikely that you will have any security issues.

The reasons are multiple, but one that is easy to understand is that the Linux maintenance philosophy is different from Windows.  

On Linux systems, there are no known issues at this time for any hacker to exploit.  When an issue is identified, it is fixed within a matter of minutes or hours and then everyone can update their systems from the free repositories, after which the previous sentence is true again.

On Windows systems, there are thousands of known issues to exploit and Microsoft is very slow at fixing them.  Some issues have been known for decades.  Consequently, users depend on third party tools to try and stop most of the gaps, but obviously that doesn't work very well.

---

### Post by coldraven on 2016-02-09
Hi Will111, as no-one has yet said welcome I'll do it :) Welcome to the forum!
I've been using Ubuntu for about 8 years and never had a virus problem. I do occasionally install ClamAV but as mentioned above it's for scanning a file that I'm sending to a Windows user.
As for a firewall I used to run Zonealarm back in my Windows days. Now I just install Ubuntu and go on the internet! Oh Joy!! 
If you only install software from the Software Centre or from trusted sources you will have no problems. If in doubt ask here before searching for an application and we will help you.
Unlike Windows where you have to update each application separately, we can do the whole system with one click.
Happy computing :)

---

### Post by Habitual on 2016-02-09
> **Geoffrey_Arndt said:**
> "Some users do use an antivirus application (clamav) to clean files that  they exchange with other users, to prevent spreading malware. That's a  good idea"
                                                                                                                                                                                      

Applies mainly to sharing files with users running Windows versus Linux systems.   (from what I've read).

.
clamav does not clean infections. Remove or move. no clean.

---

### Post by will111 on 2016-02-09
> **coldraven said:**
> Hi Will111, as no-one has yet said welcome I'll do it :) Welcome to the forum!


Many thanks,  and thanks to all who replied.

Linux / Ubuntu certainly takes a lot of initial effort to understand its methods, but think we have been spoilt by windows in that respect, though I did originally start with micros machine code and XTs  DOS around y 1980, just hope some of those old brain cells are still around  !

---

