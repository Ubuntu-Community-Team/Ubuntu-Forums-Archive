---
title: "No firewall or antivirus needed??"
date: 2010-12-24
forum: Recurring Discussions
---

### Post by John Galt on 2010-12-24
Hi everyone,

i am new to ubuntu linux.

just got myself ubuntu 10.10 and loving it.

but as i have been a windows xp user for as long i have known what a computer is, i could not help but notice that linux/ubuntu is not in need of any firewall or antivirus.

Some fact finding in the net led me to think that a responsible linux user should have a firewall (a good option being firestarter) and an antivirus ( open source option being clamav and a few others like avira and avast).

now what i need a little clarification is that i believe clam av only "detects" viruses and doesn't remove them.If this is the case then please let me know if there is an antivirus which does both and is not resource/update intensive.

Also a few options on various rootkit/trojan removal program would also help. 

Is there no full fledged internet security suite like that in windows? (just curious)

I know that ubuntu is a very safe and trusted OS, one of the many reasons i find it as the OS of the future. But a few things like those mentioned above give you peace of mind (you can never be too careful nowadays.)

---

### Post by gandaran on 2010-12-24
> **John Galt said:**
> Hi everyone,

i am new to ubuntu linux.

just got myself ubuntu 10.10 and loving it.

but as i have been a windows xp user for as long i have known what a computer is, i could not help but notice that linux/ubuntu is not in need of any firewall or antivirus.

Some fact finding in the net led me to think that a responsible linux user should have a firewall (a good option being firestarter) and an antivirus ( open source option being clamav and a few others like avira and avast).

now what i need a little clarification is that i believe clam av only "detects" viruses and doesn't remove them.If this is the case then please let me know if there is an antivirus which does both and is not resource/update intensive.

Also a few options on various rootkit/trojan removal program would also help. 

Is there no full fledged internet security suite like that in windows? (just curious)

I know that ubuntu is a very safe and trusted OS, one of the many reasons i find it as the OS of the future. But a few things like those mentioned above give you peace of mind (you can never be too careful nowadays.)
ubuntu already has a firewall, firestarter is just a gui and is old, it is no longer supported, I recommend instead 'gufw' which is easy to use.
for antivirus you don't need any, windows virus don't work on linux! what you can install is a linux rootkit application, 'rkhunter' scans for linux rootkits and linux virus, both rkhunter and gufw are in the ubuntu repos.

---

### Post by TeoBigusGeekus on 2010-12-24
You don't need an antivirus, unless you share files with windows users and you're concerned with THEIR security. You don't have to worry about your system 99.999% of the times.

Ubuntu has already a firewall, iptables. Firestarter and the likes are just frontends to it. Unless you are a network admin, don't fiddle with it, as it's default settings are perfect for anyone (IMO).

---

### Post by lisati on 2010-12-24
Opinions seem to vary about the value of antivirus software, and there is a lot of interesting reading to be found. A good place to start includes [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Rytron on 2010-12-24
I like the firewall 'Guarddog'. You can also backup your settings.

---

### Post by mr.farenheit on 2010-12-24
i think i remember at one time avg was available for linux. but then again there is no real need for and antivirus for linux.

---

### Post by HermanAB on 2010-12-24
Howdy,

Linux pretty much *is* a firewall and indeed, most firewall devices run Linux.  So no, you don't need a firewall to protect a Linux system.  Adding firewall rules to the default network setup is mostly waste of time and effort.

Viruses is only a Windows problem.  There are various reasons why Linux doesn't have viruses and probably never will - for example: tcpwrappers, netfilter, no execute and program memory randomization to name a few.  The result is that Linux is a very robust system.

So, relax and enjoy your Linux machine.

---

### Post by sve$hnikov on 2010-12-24
you dont need any kind of antivirus ubuntu is secure :D i try it a year ago no probleme with me

---

### Post by TeoBigusGeekus on 2010-12-24
> **HermanAB said:**
> There are various reasons why Linux doesn't have viruses and probably never will...
If you allow me, a small [correction]("http://www.neowin.net/news/a-history-of-viruses-on-linux").

---

### Post by gmenfan83 on 2010-12-24
what would be a good program if we did share files with windows?

---

### Post by OldBoy44 on 2010-12-24
> **TeoBigusGeekus said:**
> If you allow me, a small [correction]("http://www.neowin.net/news/a-history-of-viruses-on-linux").

That's quite an argument for protection.

The question then is, which is best?

:)

---

### Post by TeoBigusGeekus on 2010-12-24
> **aussiebean said:**
> That's quite an argument for protection.

The question then is, which is best?

:)
Don't get bewildered now... The chances of catching one of the handful of viruses in linux are practically zero.
In fact, I've never heard anyone catching a virus in ubuntu and I've been lurking in ubuntuforums for the last 3 years.
If someone ever got infected, it would be first page in the Times, Newsweek, CNN, etc.

---

### Post by psusi on 2010-12-24
Unlike Windows, Ubuntu does not come with insecure services preinstalled that you then have to block access to with a firewall.  Also while there have been a few proof of concept Linux viruses over the years, none have spread far or long in the wild because Linux systems do not have the plethora of attack vectors that windows does, which are needed for initial infection.  That combined with the fact that Linux users tend not to download and execute unknown programs form untrusted sources, and a program must be run with sudo in order to infect the system, means you don't get virus infections.

---

### Post by lisati on 2010-12-24
> **gmenfan83 said:**
> what would be a good program if we did share files with windows?

I use clamav as part of my email server's checking for undesirable and unwanted content. For just about everything else, I'm selective about what I open.

---

### Post by OldBoy44 on 2010-12-24
Thanks for that guys!

Cheers and Merry Christmas.

):P

---

### Post by gmenfan83 on 2010-12-24
> **lisati said:**
> I use clamav as part of my email server's checking for undesirable and unwanted content. For just about everything else, I'm selective about what I open.
does clam av come configured by default to do this or do we do it manually?

---

### Post by oldsoundguy on 2010-12-24
A thought .. why is it up to Linux users to "help protect Windows users"?  Really, isn't it up to Windows users to protect them self?

Having said that, Linux users should come off as being "the good guys" and yes, IF you are running a mail server or file sharing with Windows clients, you should install a decent AV.

---

### Post by QLee on 2010-12-24
[QUOTE=psusi]Unlike Windows, Ubuntu does not come with insecure services preinstalled that you then have to block access to with a firewall.  Also while there have been a few proof of concept Linux viruses over the years, none have spread far or long in the wild because Linux systems do not have the plethora of attack vectors that windows does, which are needed for initial infection.  That combined with the fact that Linux users tend not to download and execute unknown programs form untrusted sources, and a program must be run with sudo in order to infect the system, means you don't get virus infections.[/QUOTE]

I want to jump in here and agree with psusi.

In addition, I think a good case could be made that they have never really been loose in the wild. All the articles I have read have been either written by or based on references by people who work for AV companies who probably have a vested interest in selling software. In my opinion, AV applications in GNU/Linux are important for mailservers that have Windows clients, not for standard user desktop systems.

---

### Post by bodhi.zazen on 2010-12-24
This is a recurring question and my comments are:

This is not windows and you can not apply your windows security knowledge to Linux without some education.

Speaking of education, education is the best defense on any OS.

I suggest you start with :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

firewall - a better question is what do you want to use a firewall for ? what is your network architecture ? There are no signifigant listening services installed by default so there is nothing to firewall.

Antivirus ? This is not windows. So while there have been viruses in the past, the way Linux manages viruses is to patch the code. So the best defense is to keep your system up to date.

This is not the case in Windows, as the source code is closed, there are multiple documented and undocumented listening services, and the code goes unpatched. In windows you thus need a firewall and antivirus.

This is not windows, do not apply your windows mentalilty here and do not buy into the FUD. Read the security sticky and learn when and if to use these tools and if you use them learn how to use them.

99.99 % of desktop users do not need to configure their firewall or antivirus.

Welcome to Linux, and freedom from the malware that plagues windows.

---

### Post by bodhi.zazen on 2010-12-24
*Thread moved to **Recurring Discussions**.*

---

### Post by handy on 2010-12-25
If the distros were susceptible to viruses, it would be very easy to Scroogle up info on them, or to find talk of them here in the UF.

I've never seen it.

---

### Post by John Galt on 2010-12-25
Thank you all for the information and your comments. Seeing that my lack of knowledge has sparked a confrontation of ideas, into which the administrator had to intervene, i humbly close this thread in order to prevent future ill feelings.

Thank you all.

---

### Post by bodhi.zazen on 2010-12-25
> **John Galt said:**
> Thank you all for the information and your comments. Seeing that my lack of knowledge has sparked a confrontation of ideas, into which the administrator had to intervene, i humbly close this thread in order to prevent future ill feelings.

Thank you all.

Do not let my actions discourage you, you did not cause any problem at all.

Just keep asking questions and keep learning.

---

