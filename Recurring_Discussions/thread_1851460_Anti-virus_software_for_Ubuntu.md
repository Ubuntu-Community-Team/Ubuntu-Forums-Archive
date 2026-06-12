---
title: "Anti-virus software for Ubuntu"
date: 2011-09-28
forum: Recurring Discussions
---

### Post by Acquisitio on 2011-09-28
I am an absolute beginner in Ubuntu and would like to install the anti-virus software. How to chose and find the adequate software for Ubuntu and how to install it. I noticed that the installation process is not the same as the one in Windows.

---

### Post by cj13579 on 2011-09-28
I would recommend ClamAV. Take a look at the following Ubuntu page for more info and install instructions: [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by haqking on 2011-09-28
Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

**See here for Anti-Virus information:**

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by HermanAB on 2011-09-28
The short answer is: You don't need it.

Relax and enjoy your nice, new, trouble free and secure Linux system.

---

### Post by CharlesA on 2011-09-28
> **HermanAB said:**
> The short answer is: You don't need it.

Relax and enjoy your nice, new, trouble free and secure Linux system.
This ^

ClamAV throws a load of false positives.

---

### Post by Acquisitio on 2011-09-28
> **haqking said:**
> Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

**See here for Anti-Virus information:**

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

Thanks for this usfull post.




> **haqking said:**
> Linux does not suffer from Viruses like other  OS, there are no known viruses in the wild, the main reason using AV on  linux is to scan incase you share files with windows users.

What do you mean when you say ''sharing files''.Do you mean e-mails, photos,etc. ...




> **haqking said:**
> Common sense, dont tell your system you want it to do something unless  you are sure etc. Linux assumes you know what you are doing :wink:

That is exactly why I need the advice. I do not know to do it by myself and I need someone to guide me and help me to do the complete procedure without making mistakes. I would apreciate help.

---

### Post by Acquisitio on 2011-09-28
> **cj13579 said:**
> I would recommend ClamAV. Take a look at the following Ubuntu page for more info and install instructions: [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Thank you.

---

### Post by Ubunski on 2011-09-28
I am in the same boat as you. I worry that If something pops up on package update manager that I am going to download a virus. I am mostly using ubuntu for better hardware usage and thus better gaming experience. I worry about some websites I visit will pop me and I have no clue what to do. I feel like to use linux i should know how to manually find and destroy the virus and then retaliate! Alas this is just an amibition.

---

### Post by haqking on 2011-09-28
> **Acquisitio said:**
> Thanks for this usfull post.






What do you mean when you say ''sharing files''.Do you mean e-mails, photos,etc. ...






That is exactly why I need the advice. I do not know to do it by myself and I need someone to guide me and help me to do the complete procedure without making mistakes. I would apreciate help.

> **Ubunski said:**
> I am in the same boat as you. I worry that If something pops up on package update manager that I am going to download a virus. I am mostly using ubuntu for better hardware usage and thus better gaming experience. I worry about some websites I visit will pop me and I have no clue what to do. I feel like to use linux i should know how to manually find and destroy the virus and then retaliate! Alas this is just an amibition.

Sit back and enjoy Linux without worrying about viruses, as i said before there are none currenlty in the wild.

If you share files with windows users then by all means use a scanner to prevent further spread of malware but dont worry too much about your Linux system when it comes to viruses.

If you read all the links i posted you would understand why.

Though it is possible to get infected through using WINE and such the malware would need to be targeted at doing that type of thing and like i said there is no current viruses in the wild for linux.

Being aware is use only the trusted repositores, dont add dodgy PPA's or if unsure then ask on here to see if they seem ok.

and use [**ROOTSUDO**]("https://help.ubuntu.com/community/RootSudo") to prevent things running under admin privelege.

and as i said before use noscript and adblock in your browser, i suggest you read the links to be clear on what people are telling you here.

enjoy

In short as said above, realx and enjoy a 99.9% malware free environment and stay vigilent.

---

### Post by collisionystm on 2011-09-28
If you feel more comfortable having an anti-virus, I suggest you use Eset-Nod32. 
Here is a link to a beta version you can try out.
[http://go.eset.com/us/beta/file-security-linux](http://go.eset.com/us/beta/file-security-linux)

---

### Post by Paqman on 2011-09-28
Don't bother with ClamAV. It won't give you any additional protection against Linux malware than an up-to-date Ubuntu install would have anyway, and even when scanning for Windows threats (which is what it mostly does) it isn't very effective.

If you want to install a package on your Linux system to scan for Windows malware try something like Avast.

---

### Post by Dangertux on 2011-09-28
> **Ubunski said:**
> I am in the same boat as you. I worry that If something pops up on package update manager that I am going to download a virus. I am mostly using ubuntu for better hardware usage and thus better gaming experience. I worry about some websites I visit will pop me and I have no clue what to do. I feel like to use linux i should know how to manually find and destroy the virus and then retaliate! Alas this is just an amibition.


Interesting ambition. 

As far as package manager goes so long as you're not adding a bunch of untrusted PPAs you shouldn't have problems there. 

As far as web based attacks go drive by downloads have the same argument that they are not written to be run in Linux thus will not work. That being said if you run into someone who decided they want to target Linux this way it could work. But you should be browsing with noscript regardless, since there are plenty of web based attack methods you can run into that have absolutely nothing to do with your operating system or data stored on your computer. Generally since these attacks target sensitive data stored online they can be equally if not more devastating.

---

### Post by oldsoundguy on 2011-09-28
> **Ubunski said:**
> I am in the same boat as you. I worry that If something pops up on package update manager that I am going to download a virus. I am mostly using ubuntu for better hardware usage and thus better gaming experience. I worry about some websites I visit will pop me and I have no clue what to do. I feel like to use linux i should know how to manually find and destroy the virus and then retaliate! Alas this is just an amibition.

Said over and over .. you do not need a virus protection program for Linux ITSELF .. only if you are acting as a server and there are Windows computers involved .. and that protection is for the Windows computers, not Linux

Since everything that goes into the REGULAR repositories is pre screened before being made available, updates are SAFE.  (when you start using PPA's .. private repositories .. use with caution.  Use only PROVEN CLEAN PPA's .. such as Mozilla's and you can sleep well, also!)

Linux is NOT Windows .. it does not act the same way and is not subject to the same vulnerability as Windows.

---

### Post by yetiman64 on 2011-09-28
> **Paqman said:**
> ...If you want to install a package on your Linux system to scan for Windows malware try something like Avast.
This is the very package I initially installed and used for antivirus on moving across from Windows OP, but after about 6-8 months of use and reading quite a few of the links that haqking has now posted for you, I no longer use it. 

If you are purely running Ubuntu / Linux (no dual booting/wubi/wine etc) antivirus is really not necessary. As haqking noted read all the links and you will understand why. Cheers.

---

### Post by oldsoundguy on 2011-09-28
AND, if you really need an AV for Windows .. the WINDOWS one (Microsoft Security Essentials) coupled with both Spyware Guard and Spyware Blaster (both free .. keep them updated manually) and NOT clicking on every damn link you see, should suffice for most.

---

### Post by amjjawad on 2011-09-28
> **Acquisitio said:**
> I am an absolute beginner in Ubuntu and would like to install the anti-virus software. How to chose and find the adequate software for Ubuntu and how to install it. I noticed that the installation process is not the same as the one in Windows.

You don't need it, period :)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Acquisitio on 2011-09-28
If I get a virus is it enough to re-install the Ubuntu using wubi
Would it solve the problem

---

### Post by haqking on 2011-09-28
> **Acquisitio said:**
> If I get a virus is it enough to re-install the Ubuntu using wubi
Would it solve the problem

after all that is written above you still assume you are going to get one ?

simply put yes, if you get one then reinstall or have a backup.

---

### Post by Acquisitio on 2011-09-28
> **Paqman said:**
> Don't bother with ClamAV. It won't give you any additional protection against Linux malware than an up-to-date Ubuntu install would have anyway, and even when scanning for Windows threats (which is what it mostly does) it isn't very effective.

If you want to install a package on your Linux system to scan for Windows malware try something like Avast.

If I install the anti-virus software for Windows on my Ubuntu will it work and is it possible for this software to cause some kind of demage on the system.

What is an up-to-date Ubuntu install.

---

### Post by Paddy Landau on 2011-09-28
> **Acquisitio said:**
> If I get a virus...
If you get a virus, post it on this forum and hear the sound of dropping jaws.

Search these forums -- no one has reported a Linux virus. Yet.

A virus can't exist because it has to be manually installed. Trojans can exist -- if you are dumb enough to download and run them -- but they can affect only your files, not the system files or the files of any other user.

---

### Post by Paqman on 2011-09-28
> **Acquisitio said:**
> If I install the anti-virus software for Windows on my Ubuntu will it work

No. Even if you install a Linux antivirus package it's unlikely to do anything, because you don't need one.

You already have the best antivirus software in the world installed. It's called the Linux kernel, and it's the heart of Ubuntu. Not needing to worry about viruses is half the fun of running Linux. Relax and enjoy!

> 
and is it possible for this software to cause some kind of demage on the system.


No, Windows software just doesn't run on Linux. There is a system for tricking Windows software into running, but it's pretty sketchy, and not what you're looking for.

> 
What is an up-to-date Ubuntu install.

Whenever Update Manager tells you there are updates  to be installed, say yes to them all. That will apply any security patches that your system needs. It's like a much,much better version of Windows Update.

---

### Post by Acquisitio on 2011-09-28
> **haqking said:**
> after all that is written above you still assume you are going to get one ?

simply put yes, if you get one then reinstall or have a backup.

Dear haqking,
I am new here and have my suspicions. I like to play safely. :popcorn:
 I need  more time to start feeling comfortable with this. :cool:

---

### Post by Acquisitio on 2011-09-28
> **Paqman said:**
> You already have the best antivirus software in the world installed. It's called the Linux kernel, and it's the heart of Ubuntu. Not needing to worry about viruses is half the fun of running Linux. Relax and enjoy!

What a beginner should know about using the Linux kernel.





> **Paqman said:**
> Whenever Update Manager tells you there are updates  to be installed, say yes to them all. That will apply any security patches that your system needs. It's like a much,much better version of Windows Update.

Shall I check for it somewhere or it will just appear the way I can notice it.

---

### Post by Acquisitio on 2011-09-28
> **Paddy Landau said:**
> Trojans can exist -- if you are dumb enough to download and run them -- but they can affect only your files, not the system files or the files of any other user.

If I want to be smart enough and avoid the problems, how can I avoid to download and run them.  As far as I know, there is no person in this world who would chose to get them.

---

### Post by oldsoundguy on 2011-09-28
aquisto.... RELAX  the chances of you getting any malware of ANY kind are about the same as Beyonce moving in with you.  

YOU install items in Linux .. not some site.  And the programs in the repositories are checked and re checked and re checked.
UNLIKE WINDOWS, programs can not be piggybacked and installed without your knowledge.  (I am thinking of Babylon and how it has wormed it's way through the CNet uploads enough to make using CNet for Windows files a BAD IDEA for right now.)

Your BROWSER can be chopped up, though. But in Linux it will go no further .. so a simple un-install and re-install is all it takes to fix that .. IF you are running X-Marks (in FireFox) and have stored your bookmarks regularly, all you do is re-sync and you are back to work.

---

### Post by Stray Wolf on 2011-09-28
I've been using Ubuntu for about two years.  I was like you and bothered with ant-virus software at first but it was pointless.  Viruses in Ubuntu are like fish out of water.  They're not in an environment they recognize or "know" how to interact with.  As long as you only install from trusted sources (the software center or known and trusted websites) you'll be fine.  Software not in the software center may have tracking software in it though.  For example:  Google Chrome downloaded from the web has tracking, Chromium (same as chrome minus tracking) is in the software center.  Ubuntu wouldn't allow Chrome into the software center because of tracking.  Google removed tracking and security issues for Ubuntu and called it Chromium.  That's the power of open-source.  The code is published and the community combs over it to see if it's in line with its ideals.  If there's anything questionable in the code you'll find out pretty quick from the community.

As far as the internet I recommend adding NoScript and BetterPrivacy to firefox.  Yes, you have to click more with NoScript but it's empowering.

---

### Post by Dangertux on 2011-09-28
I think we really shouldn't go too far with the Linux is impenetrable thing. That is quite simply not the case, and the reality is there is already a lot of fiction moving around this thread.

Truth - Linux can get malware, the same as Windows.
Truth - While this is the case : Malware developers do not target Linux avidly and there is no KNOWN (I emphasize this because it's really not hard to write malware) self-propogating Linux malware that functions properly under Ubuntu (any thing that isn't end of life)
Truth - Linux can get trojans, they can locally escalate and they can access things other than the files of the user who installed them
Truth - The "trusted repositories" are called trusted for a reason. You are fairly safe to trust them, this again does not make them impervious to attack.
Truth - Linux can be compromised, and is often compromised in the corporate world.
Truth - Some Windows malware works under Wine
Truth - Browser based attacks can bypass sandboxing (including SELinux) and make system calls to locally escalate.
Truth - The odds of this type of targeted attack happening to a home user are miniscule.
Truth - The biggest issue with security can and likely will be the user.

---

### Post by oldos2er on 2011-09-28
> **Acquisitio said:**
> Dear haqking,
I am new here and have my suspicions. I like to play safely. :popcorn:
 I need  more time to start feeling comfortable with this. :cool:

May I suggest you read the Security sticky?

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Paqman on 2011-09-28
> **Acquisitio said:**
> What a beginner should know about using the Linux kernel.

You don't need to know anything. A kernel is the central component of an operating system. Windows has one too, and you didn't need to know anything about that to use Windows. Same goes for Linux. It just does it's thing behind the scenes.

> 
Shall I check for it somewhere or it will just appear the way I can notice it.

If updates are available it will tell you by putting an icon in your top panel. Click on the icon to launch Update Manager.

Apart from that, you can launch it yourself any time you like and make it check for updates.

---

### Post by dirtrider1 on 2011-09-28
Linux is not Windows the same solutions do not always apply.

There are no known viruses in the wild for Linux making your antivirus essentially worthless unless your trying to protect Windows machines that are connected or may share files with.

Linux does have security threat's but Linux is generally more secure because Linux is FOSS, source code is analyzed and scrutinized much more thoroughly and by many more people.And also Linux is a true multiuser system built from the ground up with a much better security model and much more robust file permissions.

But security still comes down to the user to some extent no matter what, especially when dealing with server applications. Watch some of the videos on linux honeypots where ssh is intentionally made insecure with a very easy passphrase and the server will get brute forced very easily unlike ssh key authentication. That shows you even very secure applications can be easily cracked if setup incompetently . 

For new users watch out for script's or shady programs that you install from untrustworthy sources, Anyone could make a script that is malicious under the guise of some legitimate use. Also I have even seen websites post malicious tutorials although this is rare.

Ubuntu does has have anti-rootkit software chkrootkit rkhunter

---

### Post by Dangertux on 2011-09-28
> **dirtrider1 said:**
> 
But security still comes down to the user to some extent no matter what, especially when dealing with server applications. Watch some of the videos on linux honeypots where ssh is intentionally made insecure with a very easy passphrase and the server will get brute forced very easily unlike ssh key authentication. That shows you even very secure applications can be easily cracked if setup incompetently . 


Lest we not forget that this gem effected Ubuntu as well :-)

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0166](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0166)

---

### Post by amjjawad on 2011-09-29
> **oldos2er said:**
> May I suggest you read the Security sticky?

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Bookmarked for future use. Thanks, oldos2er :)

---

### Post by 3rdalbum on 2011-09-29
> **Dangertux said:**
> Lest we not forget that this gem effected Ubuntu as well :-)

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0166](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2008-0166)

Patched properly almost as soon as it was reported. No viruses used it.

Honestly, to the person who was asking about anti-virus: Almost everybody here has been telling you that anti-virus software is a waste of time on Linux. I've been using Linux since 2005 and I've not heard of any Linux viruses being released in that time. There's been a couple of trojans, but **anti-virus software did not detect them**.

*In short, don't even bother with anti-virus programs on Linux.*

Update Manager will tell you when there are updates available. Just make sure you click on the little icon and download and install the updates whenever it gives you that notification. That's the best defence against any future viruses or security holes that might appear.

Try to stay away from the seedy corners of the internet. In other words, don't visit "warez" sites or sites with illegal content. Don't download software outside the Ubuntu Software Center unless it's by a company or developer that you (or others) trust.

Don't install "server" software unless you are either firewalled completely, or you know what you're doing. So, don't install Apache, SSH or ProFTP - unless you have a firewall built into your router or don't mind taking the small risk of being attacked through it.

---

### Post by mschooler93 on 2011-09-29
For what it's worth, the one I use (when at all) is the Virus Scanner in the software center. Apparently, its clamTK, and it is slow, but works when I need it (torrents).

---

### Post by haqking on 2011-09-29
> **mschooler93 said:**
> For what it's worth, the one I use (when at all) is the Virus Scanner in the software center. Apparently, its clamTK, and it is slow, but works when I need it (torrents).

when you say it works ? how do you know.

Clam is full of False positives, even from a windows scan point of view.

---

### Post by vasa1 on 2011-09-29
> **Stray Wolf said:**
> ...  Ubuntu wouldn't allow Chrome into the software center because of tracking.  Google removed tracking and security issues for Ubuntu and called it Chromium.  ...

Any source for this ^^^ ?

---

### Post by josephmills on 2011-09-29
Hi there there are a lot of things that have been all ready covered in this post ie security and snort sticky anti virus and and what not. With everything that is in life if you want to learn about it you kinda have to jump in head first. Figure out how the professional's do it IE pentesters, tiger teams, red teams ect. Offensive security has some real good courses. So do others google " CEH "  I think something that is overlooked far to often with linux and isp in general is open ports that may or may not be filtered. hope that you are enjoying ubuntu so far  :)

---

### Post by josephmills on 2011-09-29
> **vasa1 said:**
> Any source for this ^^^ ?

edit need more reading

---

### Post by haqking on 2011-09-29
> **vasa1 said:**
> Any source for this ^^^ ?

from:

[http://en.wikipedia.org/wiki/Chromium_(web_browser](http://en.wikipedia.org/wiki/Chromium_(web_browser))

RLZ tracking when Chrome is downloaded as part of marketing promotions and distribution partnerships. This transmits information in encoded form to Google, e.g. when and from where Chrome has been downloaded. In June 2010, Google confirmed that the RLZ tracking token is not present in versions of Chrome downloaded from the Google website directly or in any version of Chromium. The RLZ source code was also made open source at the same time so that developers can confirm what it is and how it works

---

### Post by Acquisitio on 2011-09-29
> **oldos2er said:**
> May I suggest you read the Security sticky?

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Thank you. I have already read many texts on this forum but still I do not understand everything. For example, before I have Ubuntu installed on my computer I had read the full text about it. I understood the point but not every single detail that could be imoprtant and when the time has come for me to do it I  had to ask someone to do that for me. As haqking has already said in his reply

Common sense,** dont tell your system you want it to do something unless  you are _sure _**etc.** Linux assumes you know what you are doing **:wink:


P.S. I like your avatar.

> **Dangertux said:**
> I think we really shouldn't go too far with the Linux is impenetrable thing. That is quite simply not the case, and the reality is there is already a lot of fiction moving around this thread.

Truth - Linux can get malware, the same as Windows.
Truth - While this is the case : Malware developers do not target Linux avidly and there is no KNOWN (I emphasize this because it's really not hard to write malware) self-propogating Linux malware that functions properly under Ubuntu (any thing that isn't end of life)
Truth - Linux can get trojans, they can locally escalate and they can access things other than the files of the user who installed them
Truth - The "trusted repositories" are called trusted for a reason. You are fairly safe to trust them, this again does not make them impervious to attack.
Truth - Linux can be compromised, and is often compromised in the corporate world.
Truth - Some Windows malware works under Wine
Truth - Browser based attacks can bypass sandboxing (including SELinux) and make system calls to locally escalate.
Truth - The odds of this type of targeted attack happening to a home user are miniscule.
Truth - The biggest issue with security can and likely will be the user.

Thanks.

> **Paqman said:**
> You don't need to know anything. A kernel is the central component of an operating system. Windows has one too, and you didn't need to know anything about that to use Windows. Same goes for Linux. It just does it's thing behind the scenes.



If updates are available it will tell you by putting an icon in your top panel. Click on the icon to launch Update Manager.

Apart from that, you can launch it yourself any time you like and make it check for updates.

Thanks.

> **3rdalbum said:**
> Try to stay away from the seedy corners of the internet. In other words, don't visit "warez" sites or sites with illegal content.

When you say ''warez'' sites do you mean sites like ''4shared'' or ''bmp3'' or ''mp3 skull'', etc.




 > **3rdalbum said:**
> Don't download software outside the Ubuntu Software Center unless it's by a company or developer that you (or others) trust.

Don't install "server" software unless you are either firewalled completely, or you know what you're doing. 

That's why I ask about anti-virus software. How can I be sure about the validity of the softwares I want to install and what is Ubuntu Software Center.

> **mschooler93 said:**
> For what it's worth, the one I use (when at all) is the Virus Scanner in the software center. Apparently, its clamTK, and it is slow, but works when I need it (torrents).

Does ''Virus Scanner'' mean a software that we can download and use or the option like scanning the computer online.

***Multi-posts consolidated - 404***

---

### Post by Acquisitio on 2011-09-29
When I asked about the anti-virus software I didn't mean only to viruses but to the other threats, also. What about Trojans, malwares, key-loggers, etc.

---

### Post by haqking on 2011-09-29
> **Acquisitio said:**
> When I asked about the anti-virus software I didn't mean only to viruses but to the other threats, also. What about Trojans, malwares, key-loggers, etc.

all of this has been covered in the posts and in the links provided.
Malware is a term that encompasses all of what you mention.

---

### Post by oldos2er on 2011-09-29
> **Acquisitio said:**
> That's why I ask about anti-virus software. How can I be sure about the validity of the softwares I want to install and what is Ubuntu Software Center.

Ubuntu Software Center is your gateway to all the software in the repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Dangertux on 2011-09-29
In regards to the CVE related to OpenSSL it was actually utilized quite successfully in multiple phalanx2 implementations.

---

### Post by amjjawad on 2011-09-29
> **Acquisitio said:**
> When I asked about the anti-virus software I didn't mean only to viruses but to the other threats, also. What about Trojans, malwares, key-loggers, etc.

With all due respect and please don't be offended but if ALL what already had been posted here and you still in doubt then please do yourself a favour and:

[www.google.com](www.google.com)
OR
[www.googlubuntu.com](www.googlubuntu.com)

:)

If I were you, I would spend my time searching first before posting but that's me.

I totally understand where are you coming from and it's so good to ask and learn but if all these information and you still confused or in doubt then there is something wrong.
Linux is NOT Windows and I have posted that article for you earlier. Here it is again: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Also, many users already told you they have been using Linux for years now and they haven't faced any problem with any virus.

One of the things that made me switch to Linux is it's Virus-Free.
Another good thing about it is you don't have to go to any website to install your programs, you have 3 ways to do that:

1- The Terminal

Usually:

```
sudo apt-get update
sudo apt-get install appname
```


2- Synaptic

Click Reload then on the Search box, type the program you are looking for. Right Click and Mark for Installation then Apply.

3- Ubuntu Software Centre

It could be the easier tool for users coming from Windows. Not my cup of tea but many users are using it.

You don't have to go to [www.whatever.com](www.whatever.com) and install from there.

Make sure your password is long enough.
You can install Firewalls if you want to.

If you are new and can't understand much (I don't blame you, too much info in a short period is a real headache), read slowly and remember, if you won't break it, you won't be able to fix it. Learning is a very good thing ... just look at the full half and the bright side ;)

ALL the best and again, please don't be offended, we all had the same question when we first started :)

---

### Post by Paddy Landau on 2011-09-30
> **amjjawad said:**
> You can install Firewalls if you want to.
One minor clarification that confused me when I came to Linux from Windows:


[LIST]
[*]Linux has a firewall *already built in* (called "IP tables").
[*]You can enable, disable and modify IP tables using any firewall program (which is really a firewall *access* program).
[*]Once you have made your changes, the firewall program does **not** have to keep running, as IP tables is already there and built in, and will remember the changes.
[/LIST]

To turn on a firewall for a normal Desktop PC without dangerous software like VNC running (it's more complicated for servers), here is a simple method.


[LIST=1]
[*]Install [gufw]("apt:gufw").
[*]Run gufw (called *Firewall configuration* in the System Administration menu).
[*]Turn on the firewall:
[LIST]
[*]Tick *Enabled*.
[*]Change *Incoming* to *Rejected*.
[*]Change *Outgoing* to *Allow*.
[/LIST]
 
[*]If you belong to a network (you are behind a router):
[LIST]
[*]Select *Add*.
[*]Select *Advanced*.
[*]Select *Allow*, *In*, *Both*.
[*]In the *From* box, type your network address changing the last number to zero and adding [FONT=Fixedsys]/24[/FONT]. For example, if your router is 192.168.7.55, type:
[FONT=Fixedsys]192.168.7.0/24[/FONT]
[*]Leave the other three boxes blank.
[*]Select *Add*, *Close*.
[/LIST]
 
[*]Close GUFW, and you're done.
[/LIST]

To test, connect your computer to the network bypassing the router (most routers have a demilitarised zone (DMZ) to let you do this) and go to [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2"). You should get 100% green. (Afterwards, remember to re-militarise your computer.)

If you use your computer at a public point, you may have to (temporarily) add that network to your firewall or even disable it.

---

### Post by beew on 2011-09-30
You don't need an av,--I have none,-- but if you must have one for ease of mind, get a real one like bitdefender instead of clamAV, clam is a joke.

I understand that new users from WIndows are a bit nervous to run an OS without AV, I install bitdefender when I first installed Ubuntu10.04 around last June but have not been using any AV in my newer installations.

---

### Post by SeijiSensei on 2011-09-30
> **beew said:**
> You don't need an av,--I have none,-- but if you must have one for ease of mind, get a real one like bitdefender instead of clamAV, clam is a joke.

I've scanned thousands of emails on various servers using ClamAV via MailScanner for years now.  It's performed its task quite well, thank you.  Of course, the best first line of defense is to reject messages with attached executables; MailScanner does that as well.

@OP
I've used Linux for over fifteen years on servers and desktops.  I've never had any encounters with malware.  The closest I've come was when the [New York Times]("http://bits.blogs.nytimes.com/2009/09/14/times-site-was-victim-of-a-malicious-ad-swap/") site was used to distribute "[Antivirus 2010]("http://www.pcworld.com/article/171216/what_is_antivirus_2010.html")."  When a window popped up on my screen telling me it was scanning my "C:" drive I just had to laugh!  Even if I had clicked on the link to download the trojan-horse "scanner" it was promoting, it wouldn't have been able to install it anyway.

---

### Post by beew on 2011-09-30
> **SeijiSensei said:**
> I've scanned thousands of emails on various servers using ClamAV via MailScanner for years now.  It's performed its task quite well, thank you.  Of course, the best first line of defense is to reject messages with attached executables; MailScanner does that as well.

I am talking about a general AV, not just a mail scanner (which is apparently the only thing that clam is competent at) Can't find a link now but I remember someone posted a thread a while back where clamav has detected itself as a virus.

---

### Post by amjjawad on 2011-09-30
> **SeijiSensei said:**
> @OP
[COLOR=Red]**I've used Linux for over fifteen years on servers and desktops.  I've never had any encounters with malware.**[/COLOR]  The closest I've come was when the [New York Times]("http://bits.blogs.nytimes.com/2009/09/14/times-site-was-victim-of-a-malicious-ad-swap/") site was used to distribute "[Antivirus 2010]("http://www.pcworld.com/article/171216/what_is_antivirus_2010.html")."  When a window popped up on my screen telling me it was scanning my "C:" drive I just had to laugh!  Even if I had clicked on the link to download the "scanner" it was promoting, it wouldn't have been able to install anyway.

Enough said :)

---

### Post by haqking on 2011-09-30
This thread is more viral than you are likely to encounter in Linux.

Chillax and take heed of the given advice, read the provided links and enjoy.

and if you get malware dont blame us ;-)

---

### Post by 3rdalbum on 2011-10-03
> **Paddy Landau said:**
> 
[*]If you belong to a network (you are behind a router):

If you are behind a router and it's YOUR router, then you don't need a firewall running on your computer. Any incoming connections from the internet will not make it past the firewall in your router.

---

### Post by Dangertux on 2011-10-03
> **3rdalbum said:**
> If you are behind a router and it's YOUR router, then you don't need a firewall running on your computer. Any incoming connections from the internet will not make it past the firewall in your router.

Again -- I remind you of solicited reverse connections and the iptables ESTABLISHED, RELATED parameter. What you are saying is not a true statement.

Scenario 1 :

compromised service yields bind shell on computer behind router, port is not forwarded from router : connection from outside fails.

Scenario 2 :

compromised browser yields reverse shell , internal computer requests an external connection. Router says oh this traffic is coming from the inside out, subsequent traffic is allowed in (RELATED, ESTABLISHED). 


What you said is only 50% true.

---

### Post by Paddy Landau on 2011-10-03
> **Dangertux said:**
> I remind you of solicited reverse connections and the iptables ESTABLISHED, RELATED parameter...
Thank you for that information, which I confess I do not fully understand. However, does this mean that turning on your firewall will prevent this from happening?

---

### Post by Dangertux on 2011-10-03
No it works on the same principle that's why reverse shells are highly effective. 

You have two real choices in terms of stopping the connection, you could use restrictive outbound rules. However it is safe to assume that most peoples firewalls will allow at minimum ports 80 443 and 53 outbound. So this is only a partial solution the other alternative is a deep packet inspection firewall, and or well configured intrusion prevention system

It's actually really hard to truly defeat the reverse shell method on a desktop system due to the fact that you will likely want to access at least some form of network resource.

---

### Post by Paddy Landau on 2011-10-03
@Dangertux: This is really worth a discussion in its own right. As someone who does not understand all the issues, I'm guessing that it comes down to user education -- use only trusted applications from trusted sources, and don't do anything stupid when using the Internet.

---

### Post by Dangertux on 2011-10-03
Heh well there are a lot of factors at work in that. If go want to discuss it we can either in another thread or pm. 

The trusted files thing is good. But like I said there are a ton of factors. One that the average Ubuntu user doesn't take note of. Browser security, sure most exploit methodology is designed to inject a windows payload but there is no reason the typical browser exploits ( flash, iframes, bad javascripts , etc etc) can't target Ubuntu.

That is why I have been stressing all of this so much. I think in a sense for some Ubuntu is a placebo. Alot of folks think I am downing Linux/ubuntu or spreading FUD. But in my opinion it's better to be educated about the threats that can affect you. Truthfully the advantage the Linux community has in the malware department is almost entirely based on the bad guys not caring enough to target us. That is not particularly a security model I am content with. I wouldn't trust my personal belongings with a thief based on the honor system nor do I trust my data. 

Not to say Ubuntu isn't reasonably secure, or even that it can't be made VERY secure. Just that of the userbase as a whole were targeted tomorrow we would see we were ill prepared. Like I said discussion for another place besides I have to be at work in 4 hours and haven't slept yet :-P

---

### Post by Paddy Landau on 2011-10-03
@Dangertux, thank you for your clarifications. It is an interesting subject, and if I had plenty of time I would investigate.

When someone finally targets Linux, I am sure we will hear about it quickly!

---

### Post by Paddy Landau on 2011-10-04
Dangertux has written a [firewall article for simple people]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/") (like me). I found it instructive even though I didn't understand all the iptables commands.

From what I understand, in the end it boils down to having a firewall and the sense not to install malicious programs. I'm sure Dangertux will tell me if I have misunderstood.

---

### Post by 3rdalbum on 2011-10-04
> **Dangertux said:**
> Again -- I remind you of solicited reverse connections and the iptables ESTABLISHED, RELATED parameter. What you are saying is not a true statement.

Scenario 2 :

compromised browser yields reverse shell , internal computer requests an external connection. Router says oh this traffic is coming from the inside out, subsequent traffic is allowed in (RELATED, ESTABLISHED). 

Standalone routers don't work that way. They don't create incoming rules based on outgoing traffic.

If your browser is commanded to run malicious code and yield a shell on an outgoing connection, why would an attacker bother to establish an incoming connection? What advantage would this give when they already have a shell on the computer?

---

### Post by ultrageeky on 2011-10-04
> **Dangertux said:**
> I think we really shouldn't go too far with the Linux is impenetrable thing. That is quite simply not the case, and the reality is there is already a lot of fiction moving around this thread.

Truth - Linux can get malware, the same as Windows.
Truth - While this is the case : Malware developers do not target Linux avidly and there is no KNOWN (I emphasize this because it's really not hard to write malware) self-propogating Linux malware that functions properly under Ubuntu (any thing that isn't end of life)
Truth - Linux can get trojans, they can locally escalate and they can access things other than the files of the user who installed them
Truth - The "trusted repositories" are called trusted for a reason. You are fairly safe to trust them, this again does not make them impervious to attack.
Truth - Linux can be compromised, and is often compromised in the corporate world.
Truth - Some Windows malware works under Wine
Truth - Browser based attacks can bypass sandboxing (including SELinux) and make system calls to locally escalate.
Truth - The odds of this type of targeted attack happening to a home user are miniscule.
Truth - The biggest issue with security can and likely will be the user.

Absolutely correct.

It annoys me when I see people saying "Linux is virus free" and "Linux is like Superman: neither one succumbs to baddies, ever!". It's a load of rubbish.

It seems to have escaped a few people's attention that [kernal.org was recently compromised by hackers]("http://www.theregister.co.uk/2011/10/04/linux_repository_res/") (read the article comments too). Many web servers use Linux. the only web server that is known to be safe is the one that never connects to the Internet, never connects to any other machine, never has new software installed on it and, consequently, never serves anything that it hosts. My point is: Linux is only as secure as its user is security minded. With respect to viruses, Trojans and rootkits, like any other OS, Linux is susceptible to them too; just less susceptible.

For those who've used Linux for several years and never had an issue with a virus or any other kind of malware, if you've never scanned for malware, how can you be sure you've never suffered it? Plus, how often do you reinstall?

A couple of Linux anti-virus programs are Avast, AVG, Bitdefender and Avira. Forget ClamAV because it's not very useful.

ClamAV is mostly mentioned in Linux AV discussions because it's mostly mentioned in AV discussions and people like to regurgitate what they've seen mentioned in AV discussions they've read (like I do, lol). It's also the AV that's found in most distro repositories.

My suggestion is Avast. I would use Avira (it's the best Windows AV) but it's only half-heartedly ported to Linux. Avira for Linux lacks a GUI and is a nuisance to update.

If you want to protect yourself from malicious websites, you can use your computer's hosts file to blacklist bad hosts. It's easy and many bad-host lists already exist. A big bonus to using a hosts blacklist is that your surfing will get faster because of the reduced ads you see. [Here's a guide to blocking bad hosts]("http://journalxtra.com/2011/07/faster-safer-ad-free-browsing-with-a-little-domain-blocking/").

---

### Post by Paddy Landau on 2011-10-04
@ultrageeky: Thank you for posting that site about blocking bad websites. I have added it to my /etc/hosts and it seems to work well.

Now to figure out a script to automatically update it every month...

---

### Post by CharlesA on 2011-10-04
> **Paddy Landau said:**
> @ultrageeky: Thank you for posting that site about blocking bad websites. I have added it to my /etc/hosts and it seems to work well.

Now to figure out a script to automatically update it every month...
You could probably just wget both hosts files then run uniq (I think that's the program) to remove duplicates.

---

### Post by Paddy Landau on 2011-10-05
> **CharlesA said:**
> You could probably just wget both hosts files then run uniq (I think that's the program) to remove duplicates.
It turned out to be a little more complicated (though not much), because dedup needs standardising the whitespace.

I have created a script to automate the process. If anyone is interested, let me know and I'll post a copy.

---

### Post by CharlesA on 2011-10-05
> **Paddy Landau said:**
> It turned out to be a little more complicated (though not much), because dedup needs standardising the whitespace.

I have created a script to automate the process. If anyone is interested, let me know and I'll post a copy.
Oh drat. Glad you got it figured out. :)

---

### Post by ultrageeky on 2011-10-11
[Paddy Landau]("http://ubuntuforums.org/member.php?u=572807"), you're welcome. Just remember that when you can't see a page or a part of a page it might be due to a blocked hostname; and, never, never, never, never, never delete your hosts file. If you want to delete it just replace the contents with a reference for localhost and its IP address otherwise you'll find a lot of strange, unwelcome things will happen to your computer. 

Dangertux, sort -u tends to work better than uniq because (if I correctly recall) uniq requires non uniq rows of text to be listed in succession. sort -u will sort rows into alphanumeric order before it purges non uniques.

---

