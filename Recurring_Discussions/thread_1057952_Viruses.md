---
title: "Viruses"
date: 2009-02-02
forum: Recurring Discussions
---

### Post by Jack Shankle on 2009-02-02
Yes I am an old Windows guy.
I have to have a good virus checker and lots of other goodies to keep the bad boys out of my Puter. Do I need virus checkers and other goodies with Ubuntu? If so, will the ones I have installed with Windows work with Ubuntu? For Ex: ESET Smart Security and Ccleaner. What about Firewalls? How are they handled on Ubuntu? In general, how is security handled in Ubuntu.
Thank for any replies.

2% Ubuntu working on 3% Ubuntu

---

### Post by Zevik on 2009-02-02
No virus scanning software is needed for good ol' Ubuntu :) CCleaner is, for the most part, a registry cleaner and just removes extraneous files, and this is mostly taken care of in Ubuntu. For information on firewalls, I reccomend a quick google search or checking out one of these guides:

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

[http://www.linux.com/articles/55319](http://www.linux.com/articles/55319)

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by ozbolt on 2009-02-02
NO you don't need any of that, only if you really need good firewall (that one in your router is not enough?) than try to set up m0n0wall :D
Google it.
And for ccleaner just run sudo apt-get autoremove (in terminal) after uninstalling software  and this will do most of the job. Other is hadled by Linux (Debian (Ubuntu)).

---

### Post by dESAI on 2009-02-02
> **Zevik said:**
> No virus scanning software is needed for good ol' Ubuntu :) CCleaner is, for the most part, a registry cleaner and just removes extraneous files, and this is mostly taken care of in Ubuntu. For information on firewalls, I reccomend a quick google search or checking out one of these guides:

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

[http://www.linux.com/articles/55319](http://www.linux.com/articles/55319)

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

I have windows and ubuntu pcs on my network. Could an ubuntu pc be a host of a virus that could somehow find it's way onto one of my XP pc's? or would the virus be unable to function at all?

Thanks :)

---

### Post by lykwydchykyn on 2009-02-02
> **Jack Shankle said:**
> Yes I am an old Windows guy.
I have to have a good virus checker and lots of other goodies to keep the bad boys out of my Puter. Do I need virus checkers and other goodies with Ubuntu? 

No, though that's likely to segue into a lengthy rehashed debate over might-be's and may-be's.
> 
If so, will the ones I have installed with Windows work with Ubuntu? For Ex: ESET Smart Security and Ccleaner. 

No.  They're pretty much optimized for Windows.  Ubuntu is a completely different animal under the hood, and those tools probably wouldn't begin to know what to do with it, even if they did run.
> 
What about Firewalls? How are they handled on Ubuntu? In general, how is security handled in Ubuntu.

The Linux kernel has a firewall engine built in.  There are a number of tools available to configure it.  UFW is a command line tool, I'm not sure what vanilla ubuntu is shipping with now in the way of graphical tools (used to be firestarter, but I think that's defunct).  

Security is a pretty broad topic; which aspect do you want to know about?

---

### Post by sydbat on 2009-02-02
> **dESAI said:**
> I have windows and ubuntu pcs on my network. Could an ubuntu pc be a host of a virus that could somehow find it's way onto one of my XP pc's? or would the virus be unable to function at all?

Thanks :)Technically yes. But only if you allow your XP boxes access to the ext3 file system. Or you physically move an infected file while in Ubuntu to XP. Otherwise, no.

You may want to use an AV program to scan shared files, as it will look for Windows-based malware. However, it will only be reactive, not proactive.

---

### Post by lykwydchykyn on 2009-02-02
> **dESAI said:**
> I have windows and ubuntu pcs on my network. Could an ubuntu pc be a host of a virus that could somehow find it's way onto one of my XP pc's? or would the virus be unable to function at all?

Thanks :)

The virus would be unable to function.  Unless of course someone specifically designed it that way, though I'm not aware that anyone has ever done that.

If you had an ubuntu machine acting as a fileserver, it could certainly store a virus.  But a windows virus will not execute on a non-windows platform.

---

### Post by Jack Shankle on 2009-02-02
Thanks for all the info. It will take me awhile to absorb it.
I think this is a correct statement. Virus checkers are NOT necessary.
Garbage files that can be taken care of with "Ccleaner" can be handled with: sudo apt-get autoremove  in the terminal.  
A two way firewall would have to be installed.

---

### Post by stchman on 2009-02-02
> **Jack Shankle said:**
> Yes I am an old Windows guy.
I have to have a good virus checker and lots of other goodies to keep the bad boys out of my Puter. Do I need virus checkers and other goodies with Ubuntu? If so, will the ones I have installed with Windows work with Ubuntu? For Ex: ESET Smart Security and Ccleaner. What about Firewalls? How are they handled on Ubuntu? In general, how is security handled in Ubuntu.
Thank for any replies.

2% Ubuntu working on 3% Ubuntu

Linux is immune to Windows viruses and the security features keep your computer safe.

Ubuntu has a firewall by default in the iptables.  You can feel safe.

---

### Post by EvilRobotDrew on 2009-02-02
if you are concerned about an infected file sitting in ubuntu, you could install clamav, and chkrootkit, i don't know how they stack up compared to ESET but it will give you a little bit of a safety net. While there aren't a lot of viruses for Linux, i always feel it is better to be safe then sorry, especially if windows boxes are in communication with the linux boxes. 

Linux may be a fortress compared to windows, but it doesn't matter how high your walls are if you leave the gate open.

---

### Post by mcduck on 2009-02-02
> **Jack Shankle said:**
> Thanks for all the info. It will take me awhile to absorb it.
I think this is a correct statement. Virus checkers are NOT necessary.
Garbage files that can be taken care of with "Ccleaner" can be handled with: sudo apt-get autoremove  in the terminal.  
A two way firewall would have to be installed.

almost.. :)

No viruses, malware, spyware or stuff like that, so no need for any program that scans for them.

There's no registry, and hardly any junk files, although running the autoremove command sometimes might save you a few megabytes worth of disk space.

A firewall is not required in the default install, there are no running services that would respond to incoming connections from the network so there's nothing the firewall would protect you from. Thus, there is no active firewall by default. If you install any server software you should enable the firewall, it's included in linux itself but you most likely want some fairly easy tool to manage firewall rules. For that, I recommend ufw(command-line) or Gufw (graphcal).

edit:
Some people insist on running antivirus app on Linux to scan for windows viruses, to make sure they aren't sending any infected files to Windows users. in my opinion this is useless, if the Windows user isn't running proper antivirus program himself he's in very deep trouble no matter what you do. And if he *is* running one, it will detect the infected file anyway. :D

I'd leave that stuff for those running corporate e-mail servers etc, which is actually what clamav was made for.

---

### Post by ibuclaw on 2009-02-02
```
sudo ufw default deny
```
and
```
sudo ufw enable
```

Is really all you require for the built-in Ubuntu firewall if you are a "Desktop-only" user. (Since you won't be using your computer as a service, it makes sense to deny all inbound attempts to connect to your computer that don't have the ACK bit turned on).

But what that won't do is stop you connecting to the outside world. So use the internet responsibly :)

For a more indepth view into security, and the mindset of most Linux users. Have a look at [Bodhi.Zazen's brilliant tutorial on Ubuntu Security.]("http://ubuntuforums.org/showthread.php?t=510812")

Regards
Iain

---

### Post by Thelasko on 2009-02-02
> **lykwydchykyn said:**
> UFW is a command line tool, I'm not sure what vanilla ubuntu is shipping with now in the way of graphical tools (used to be firestarter, but I think that's defunct).
[GUFW]("http://packages.ubuntu.com/intrepid/gufw") is the [graphical front end for UFW.]("http://en.wikipedia.org/wiki/Gufw")

---

### Post by halovivek on 2009-02-02
Till now i am working on ubuntu from past six months. i went to virus seeding sites and malware sites for testing. Till now i did not get any worms or virus in ubuntu. really excellent one. 
basically virus or programs need root permission to run. but it is not possible in linux environment-

---

### Post by ibuclaw on 2009-02-02
> **halovivek said:**
> Till now i am working on ubuntu from past six months. i went to virus seeding sites and malware sites for testing. **Till now** i did not get any worms or virus in ubuntu. really excellent one. 
basically virus or programs need root permission to run. but it is not possible in linux environment-

Till now? :)

Odd choice of words, if you intend to say that you never got a virus.

Regards
Iain

---

### Post by SteveNorman on 2009-02-02
you do need to make sure your passwords are not dictionary words (add lots of numbers and symbols), because if someone wanted to get into your system they could with your password. If you are using ssh or another program to connect more than one computer on a network your vulnerability increases. Does anyone know what the keylogger threat is with ubuntu? It seems difficult but not impossible for one to be installed in ubuntu if it was hidden well enough.

---

### Post by Maconvert on 2009-02-02
Be careful when using P2P programs (i.e. Limewire, Deluge).
It's quite possible to download a Windows virus that, although not harmful to the Linux PC, could infect a network Windows PC if opened. Personally, I use Ubuntu for all of my downloading, file conversion, and CD/DVD burning. However, before I move a suspect file (especially software downloads) from the Ubuntu PC to the Windows PC I first scan the file on the Ubuntu PC using Norton Antivirus from the Windows XP computer (across the network).

Cheers.

---

### Post by lykwydchykyn on 2009-02-02
> **Thelasko said:**
> [GUFW]("http://packages.ubuntu.com/intrepid/gufw") is the [graphical front end for UFW.]("http://en.wikipedia.org/wiki/Gufw")

Thanks; I'm out of touch with the generic install, so I wasn't sure what to advise.  Is Gufw installed by default, or do you have to download it extra?  Just want to know how to advise people in the future.

---

### Post by mcduck on 2009-02-02
> **lykwydchykyn said:**
> Thanks; I'm out of touch with the generic install, so I wasn't sure what to advise.  Is Gufw installed by default, or do you have to download it extra?  Just want to know how to advise people in the future.

ufw is installed by default, but Gufw  (or any other graphical tool) isn't. Probably because most people don't really need a firewall anyway, and those who do are quite likely to like ufw more.

---

### Post by halovivek on 2009-02-02
> **tinivole said:**
> Till now? :)

Odd choice of words, if you intend to say that you never got a virus.

Regards
Iain

i am basically test engineer. i use to check virus attacking and spyware sites to test security. So i know LINUX is not WINDOWS.
if you allow user control in windows, spyware and virus may install but not in LINUX. so it is safe. am i right.

---

### Post by redseventyseven on 2009-02-02
> **tinivole said:**
> Till now? :)

Odd choice of words, if you intend to say that you never got a virus.

Regards
Iain

(I think what halovivek means is "so far". Easy mistake to make - it's one of the most amazing things about these forums that so many people make the effort to help others even though English isn't their native language) :)

---

### Post by tripolitan on 2009-02-02
I think everyone pretty much answered the virus question.

As far as the extra packages and orphaned libraries (libraries that are no longer in use by the system) I would open Synaptic package manager and install deborphan ( a suggested package for Synaptic) then, using Synaptic, I do an update then un-install all the packages that are marked under the "auto removable" and the no longer needed configuration files...

If you have a router, you will not need a firewall, just secure your router instead.

I always suggest using the LTS (long-term-support) version of Ubuntu for new users as it tends to be more stable (less headache)...

---

### Post by lykwydchykyn on 2009-02-02
I will add, in addition to cleaning your apt cache (probably the biggest culprit in filling up hard drives), I sometimes find I need to clear out ~/.thumbnails and my web cache.  I think there are utilities to do this, but rm -Rf is perfectly capable too.

---

### Post by tjwoosta on 2009-02-02
antivirus is not necessary for you linux box (linux eats viruses for breakfast)

however if you have windows machines that are networked to (or share files with somehow) it's probably a good idea to use clamav once in a while to scan you linux box, just to avoid accidentally infecting windows with malicous code that would remain dormant in linux

---

### Post by Jack Shankle on 2009-02-04
I only ask this because I see conflicting information concerning
Viruses in Ubuntu.
For Instance. I have a very good virus checker by Eset called
Smart Security. This is designed for the Desktop. However Eset
has a Version for servers that use Linux based OS. Why would 
a Server need a program like ESET if the Kernal in Ubuntu is
not vulnerable to viruses? Makes me think something is wrong.
To many bad guys out there to take any chances. :confused:

---

### Post by mcduck on 2009-02-04
> **Jack Shankle said:**
> I only ask this because I see conflicting information concerning
Viruses in Ubuntu.
For Instance. I have a very good virus checker by Eset called
Smart Security. This is designed for the Desktop. However Eset
has a Version for servers that use Linux based OS. Why would 
a Server need a program like ESET if the Kernal in Ubuntu is
not vulnerable to viruses? Makes me think something is wrong.
To many bad guys out there to take any chances. :confused:

Antivirus companies have been claiming for years that there will soon be Linux viruses around and because of that you should buy their product. No surprise, they make money by selling this software.

However this far none of their predictions has became reality, and in the end the truth is that there still aren't any Linux viruses around. Besides, you can't make antivirus software that would detect a virus before the virus itself has been written. ;)

(Servers can use antivirus software to scan for Windows viruses, to protect a company network for example. The server itself doesn't need the protection.)

---

### Post by albinootje on 2009-02-04
> **dESAI said:**
> I have windows and ubuntu pcs on my network. Could an ubuntu pc be a host of a virus that could somehow find it's way onto one of my XP pc's? or would the virus be unable to function at all?


Viruses and trojan horses are just files (or part of files), so if you download software or emails with attachments on your Ubuntu machine(s), and transfer those files to your MS-Windows machine(s) then it's possible that the MS-Windows machine(s) get infected if you're not running proper anti-virus sofware on those MS machines.

But again, floppies, cdroms, DVDs and usb disk and usb sticks can also carry infected files.

Many years ago I read that one anti-virus company (I think it was Sophos) brought out a commercial cdrom at some computer fair which mistakenly had a virus on it.

No, I'm not trying to start a discussion about how guilty the anti-virus companies are concerning the fear about viruses, and keeping the customers in fear, contributing to that world wide fear etc. I'm just trying to say that people make mistakes, and you should try to inform yourself properly and use "common sense" :)

---

### Post by handydan918 on 2009-02-04
> **Jack Shankle said:**
>  However Eset
has a Version for servers that use Linux based OS. Why would 
a Server need a program like ESET if the Kernal in Ubuntu is
not vulnerable to viruses?Two part answer: 1) Servers need to concern themselves with their clients, most of which are windows machines, and highly susceptible to many exploits. If you contact Esat and get some specs, I bet they only use windows virus signatures. 2) It's not that the kernel is virus-proof, it's that a) the unix permissions model makes it VERY difficult (read: virtually impossible) to install anything without root access, and b) all of the successful viruses out there are for windows. (If only because of "a"!) >  Makes me think something is wrong.
To many bad guys out there to take any chances. :confused:
Let me propose that there are many of us, like myself, who have taken the chances for you. I have been running desktop linux for about ten years now, and I've had the luxury of having non-production machines around most of that time, so I v'e done "stupid" stuff like clicking the link from the nigerian businessman, deliberately tried to install malware...
It won't work. The Linux environment is too different. 
Now, if you feel deprived by the lack of viral fun and games, you can try Wine. Some viruses will sorta semi-work in Wine....

Relax.You couldn't be safer in an Abrams M1 in the local walmart parking lot....especially if you're already behind a NAT router.


;)

---

### Post by albinootje on 2009-02-04
> **Jack Shankle said:**
> I only ask this because I see conflicting information concerning
Viruses in Ubuntu.

I've been using Linux since 1995, let me tell you a Linux virus story.

I clearly remember the day that I read (on FidoNet via BBS) about the Linux virus called Bliss. 
This was an anonymous "proof of concept" by the author of Bliss, only to show that the Bliss author thought that a virus for Linux could be possible in the future.

The author of Bliss uploaded the Bliss virus + information about it to some source (A RedHat ftp-server perhaps) where some RedHat people read about it and starting emailing information about it around.
When running Bliss, it would make nice logfiles about its activities (in /tmp iirc), and was only able to mess up the Linux system when run as "root", and only as "root"!

What happened then ? McAfee anti-virus company came out with some press release where they talked about "First Linux virus found!" and they suggested that they discovered the Bliss virus themselves. McAfee claimed to have a fix for Bliss included in their anti-virus software for Linux.

I searched for the McAfee anti-virus software for Linux, it was not easy to find, not so easy to install, AND as others already wrote at that time, it was also NOT needed to use their anti-virus software since running Bliss as normal user in a testing environment was pretty harmless.

My conclusion : rm -rf /McAfee/

See also here : 
[http://en.wikipedia.org/wiki/Bliss_(virus](http://en.wikipedia.org/wiki/Bliss_(virus))
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
And :
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Concerning your question about Linux versions of anti-virus software for servers : that's only meant for MS-Windows viruses in emails on Linux mail-servers.

---

### Post by lykwydchykyn on 2009-02-04
> **Jack Shankle said:**
> 
To many bad guys out there to take any chances. :confused:

Let's get something clear here:
The bad guys are after Linux as well.

BUT, the primary MO is not virus infection. This is the misconception that always comes along in these discussions.  On Windows, anti-virus == security.  When you say to new Linux users "you don't need anti-virus", they take away from that "you don't need to worry about security".  That's the wrong message.

The right message is that you need to educate yourself on the so-called "threat landscape" for Linux and take the correct precautions.

Do your updates.
Use strong passwords.
Don't abuse sudo.
Use a firewall, and know what ports you have open to the internet.
If you don't know what you're doing, stick to installing software from the repositories.

---

### Post by jrusso2 on 2009-02-04
Seems like we have to go through this whole discussion every couple days.  This has been covered already just have to search the forum.

---

### Post by albinootje on 2009-02-04
> **jrusso2 said:**
> Seems like we have to go through this whole discussion every couple days.  This has been covered already just have to search the forum.

Are you annoyed that we're talking about the same thing in this thread ?

What keywords do you recommend to search for ?
And why don't provide a link to that thread ?

---

### Post by sydbat on 2009-02-04
I would recommend "virus", "anti-virus", "Linux", "Ubuntu", etc, etc, etc...and/or any combination, etc, etc...

You may have to go through a few pages from the search to filter out (for yourself) non-relevant threads, but there will be several pages with this kind of discussion.

Also, just go through this board (Recurring Discussions) page by page and do your own low-tech search. You WILL find far too many threads on this...

---

### Post by Jack Shankle on 2009-02-04
Sorry, Didn't mean to annoy anyone.
But in my defense I have heard that argument a 1000 times.
For Instance: have you ever gone up on Microsoft and looked for a topic
and got 10,000 items not relating to what you asked for? I HAVE. 
It's usually a waste of time to do searches. Extensive indexes need 
to be done and they AREN'T.

---

### Post by cardinals_fan on 2009-02-04
> **Jack Shankle said:**
> I only ask this because I see conflicting information concerning
Viruses in Ubuntu.
For Instance. I have a very good virus checker by Eset called
Smart Security. This is designed for the Desktop. However Eset
has a Version for servers that use Linux based OS. Why would 
a Server need a program like ESET if the Kernal in Ubuntu is
not vulnerable to viruses? Makes me think something is wrong.
To many bad guys out there to take any chances. :confused:
[http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

I want this stickied...
> **Jack Shankle said:**
> 
It's usually a waste of time to do searches.
I can solve 90% of my problems with Google.

---

### Post by Thelasko on 2009-02-05
> **cardinals_fan said:**
> I can solve 90% of my problems with Google.

Yeah, this isn't Microsoft.  You can actually search for a problem and find an answer.

---

