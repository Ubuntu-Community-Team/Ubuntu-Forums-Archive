---
title: "Can a virus 'live' in ubuntu ?"
date: 2009-03-27
forum: Recurring Discussions
---

### Post by listerdl on 2009-03-27
hi, is it possible for a virus to sort of live in ubuntu and you dont know anything about it? When I had windows, :roll: I would suddenly realise that the reason why something hadnt been working properly was because of a virus.

Does that simply not happen with GNU/Linux and Ubuntu?

....just wanna make sure...

---

### Post by humphreybc on 2009-03-27
No not really. Linux isn't as susceptible to viruses as Windows is because of a few reasons:

- Linux accounts for under 2% of all OS' in the world, whereas Windows has around 90% therefore most viruses are .exe, targeted at Windows for this reason.

- Linux can't open .exe files by default so even if you got a Windows virus on your computer, chances are it can't run. There is one exception, and that is if you are using Wine windows emulation layer - but in this case the virus would only be installed to your Wine folder, therefore not damaging any system components and providing easy removal.

- Linux has tighter security than Windows. You could almost say that Ubuntu has learnt from Microsofts mistakes. It doesn't use a registry like Windows, and has a more rigid file system. It also uses the "sudo" tool to ensure that everything is run with the users permission.

- By default, all ports in Ubuntu are blocked on a fresh install. If an application has to use a port, it will open it itself.

- But what if that application is a virus? All applications that are in the repositories have been checked and given security clearances to ensure they pose no threat.

---

### Post by listerdl on 2009-03-27
wow thats amazing.

Basically I think that owing to the above...isnt linux just going to - eventually - overtake windows? I mean, surely it has to? People are becoming more educated about viruses and software.....

Thanks for your reply.

---

### Post by sgosnell on 2009-03-27
I think it's the opposite - people are becoming less educated about viruses, overall.  There are more and more people using computers every day, and the percentage who actually know something about them is probably decreasing.  One of the more frequent subjects here is about wanting to quash the annoying requests for entering one's password.  It's inconvenient, so they don't want to have to do it, although that's one of the chief ways viruses can be prevented.  They want instant gratification and convenience, and don't care about the risk of infection.  It won't happen to them...

---

### Post by 3Miro on 2009-03-27
A viruses actually do not "live" in windows. Viruses are files or more often, parts of files. Thus they can exist on every system. The question is: What can a virus do?

A windows virus cannot affect a non Windows machine.

Windows has very poor security, unlike Unix systems that are build from the ground up with security and most of all security in them, windows considers security something secondary. The base of the Linux security is the Linux Kernel that is ultimately responsible for making sure that things behave and no program accesses data that it is not supposed to. Windows biggest weakness is the kernel that not even Microsoft is sure how it works. The biggest issues in Windows are Internet Explorer and Outlook, both of which integrate within the kernel and once one finds a security hole, one gets access directly to the hearth of the system. On Linux all mail clients and browsers and web programs in general know their place.

Can one make a virus for Ubuntu? I suppose it is theoretically possible, it would be different from a windows virus, but still. I don't think it is possible to have the windows type of virus that gets on one machine and then on another and has a chain reaction. I am not very clear on why, but in Unix that cannot happen. 

There are security holes in any system, but here is the power of the open source community, everything is transparent and anyone can find and fix an issue.

The security problems on Linux come most of all from downloading programs and scripts from shady sources. If you run a script with root privileges, then you are in effect giving full control of your system to the person that made the script. If it isn't someone that you trust (i.e. Canonical or a good friend) then don't run the script. (Hey here is way to make your system run faster, type this: sudo ** -fr /, put the right thing on the ** and your system is a toast).

---

### Post by kidux on 2009-03-27
> **3Miro said:**
> Windows biggest weakness is the kernel that not even Microsoft is sure how it works.

What do you mean by this?

---

### Post by albinootje on 2009-03-27
> **listerdl said:**
> is it possible for a virus to sort of live in ubuntu and you dont know anything about it?


First of all, there are viruses, worms, trojan horses, spyware, keyloggers, rootkits etc.

Don't believe the MS-Windows-has-most-of-the-marketshare therefore virus-writers have not yet shown any interest to write viruses for Linux or MacOSX.

The truth is that MS-Windows is a paradise for virus-and-the-like writers.

Back in the days of DOS there was the very primitive FS called FAT, and DOS was a single user OS, which took MS quite a long time to more or less get rid of.
Even now there's quite some software for MS-Windows which cannot run properly as a non-priviledged user, and apart from that a lot of MS-Windows users are also badly informed about the risks of running software with administrator rights.

This is a big difference with Linux already. Linux is a Unix-alike, and Unix has always (or almost always?) been a true multi-user system.
The separation between the normal user and the administrator (root) has always been very strict by default.

Read the following for more information :
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[http://linuxmafia.com/~rick/faq/index.php?page=virus#virus](http://linuxmafia.com/~rick/faq/index.php?page=virus#virus)

---

### Post by 3Miro on 2009-03-27
A quick note, Unix was build in the late 60s early 70s, way before Microsoft. Linux first started in early 90s. Those have security in-build from the first line of code.

Windows 98 (note how many years later), has no concept of security. The web is still full of videos taken with people's web-cameras without them even knowing. In win 98 anyone form anywhere could connect to your computer and make annoying messages appear on the screen or watch you from your camera without you knowing or put files on your computer and so on. Those were not hacks, those were the things that the system allows by defaults. Windows 2000 had some security in it, but it wasn't until XP service pack 2 that windows had an in-build firewall (and since the firewall wasn't considered in the initial design, it did not work well at all).

It wasn't Ubuntu that learned from Microsoft's mistakes, it was Microsoft that refuses to learn from Linux AND their own mistakes. Unix is much older than Windows and Linux is as old as Windows 3.1.

The reason why Unix did not take over at the time was that the US court ban its use for commercial purposes under the anti trust laws, they were afraid of total Unix monopoly. Ironically now we are stuck with almost total Windows monopoly (and windows is the inferior system).

---

### Post by albinootje on 2009-03-27
This is also very interesting :
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)
It talks about a design fault the KDE and Gnome developers made with the dot desktop files.

---

### Post by 3Miro on 2009-03-27
> **kidux said:**
> What do you mean by this?

For backwards compatibility, there is old code that is still preserved within windows (I don't know about Vista or Windows 7, but it is true for XP). People that wrote the code at the time, no longer work for MS or just don't remember what it was for. If they were to remove the code, things broke and they did not invest in cleaning it up, figuring it out and so on.

Windows 2000 was more stable and more secure than the first release of XP. Windows 2000 had trouble running old win95 or win98 programs, while XP did that well. Old code ....

A fact is that there are far more people working for Linux (not just Ubuntu) than there are working for MS. MS has limited resources, while the community is almost infinite.

---

### Post by kidux on 2009-03-27
> **3Miro said:**
> For backwards compatibility, there is old code that is still preserved within windows (I don't know about Vista or Windows 7, but it is true for XP). People that wrote the code at the time, no longer work for MS or just don't remember what it was for. If they were to remove the code, things broke and they did not invest in cleaning it up, figuring it out and so on.

Windows 2000 was more stable and more secure than the first release of XP. Windows 2000 had trouble running old win95 or win98 programs, while XP did that well. Old code ....

A fact is that there are far more people working for Linux (not just Ubuntu) than there are working for MS. MS has limited resources, while the community is almost infinite.
Hmm...did not think of that. Did wonder about the backwards compatibility, but I figured their people would know that old code.

The "employee" number thing is what I bring up all the time when people ask me what the benefit of open source is over MS/Apple.

---

### Post by 3Miro on 2009-03-27
> **albinootje said:**
> This is also very interesting :
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)
It talks about a design fault the KDE and Gnome developers made with the dot desktop files.

The design flaw is not so much with the dot files as with the ability of Gnome and KDE to run a script from within user space with root privileges. The system should be made so that nothing that I can do as user XYZ would permit me to have a piece of code executed as root at any time. If KDE and Gnome have those startup scripts in user space, then that is MAJOR security flaw (I almost find it hard to believe).

---

### Post by 3Miro on 2009-03-27
> **kidux said:**
> Hmm...did not think of that. Did wonder about the backwards compatibility, but I figured their people would know that old code.

The "employee" number thing is what I bring up all the time when people ask me what the benefit of open source is over MS/Apple.

MS Supervisor: Hey Joe, good job on that piece of DOS code, but now that we have it, we don't need you anymore. You are fired!
----- 5 years later -----
MS Supervisor: What does this piece of code do?
MS Employee: I don't know, Joe made it 5 years ago. If we remove it, things don't work, be should at least know what it does. Give me a week to see how it interfaces with the rest of the code.
MS Supervisor: No I need you to work on that new feature because we have to make the release on time or we are both fired. Just keep the code.

And while interfacing with the new code, old Joe's code created a huge security hole - say hello to the virus and good buy to your data.

---

### Post by doas777 on 2009-03-27
I once attended a conference exibition on how to best protect your laptop while stuck in the most dangerous place in the world - DefCon.

the talk was all based on ubuntu hardy, so I felt at home. I was amazed at the lengths needed to compute safely in such an environment. they recommended reconfiguring ufw to block all outbound packets except those to your custom VPN connection (to your home base) and to perform all net access from there. they provided a script to hash all your files and do before/after comparison, lock down all apps with selinux, special mount parameters, onetime passwords, no sudo time frame, full disk encryption, grub lockdown, IDS, uninstall hibernate, remove all compilers....
 they even suggested handcuffing the laptop to your  person, just to be safe.

if I ever went to defcon, I don't think I'd take a computer at all.

I started this post with a point in mind, and I've completely lost it, but i guess you could say, the moral of the story is, no computer is "Safe". it's only a question of whether it is "safe enough".

BTW, viruses specifically are only a small part of the malware landscape. ubuntu is susceptible to some spyware and adware. anything that does all it;s work within firefox, will run just fine on your ubuntu system.
rootkits are also a problem if you add untrusted repos, or one of the trusted ones gets attacked. viruses, no. worms/rootkits(rare), spyware, and adware, yes.

---

### Post by albinootje on 2009-03-27
> **3Miro said:**
> The design flaw is not so much with the dot files as with the ability of Gnome and KDE to run a script from within user space with root privileges. 

Where did you read about that "ability" ?
I've never heard about KDE and Gnome have the option of running scripts as root without using sudo by the user.

The problem is with the dot desktop files in KDE and Gnome which do  not require the executable bit on those files.
The trouble with that is that a normal user can double-click on an (dot desktop file) attachment in KDE or Gnome, and it will be executed.
Any other file apart from those dot desktop files would need the executable bit first in the scenario of an email attachment.

---

### Post by albinootje on 2009-03-27
> **doas777 said:**
> 
 they even suggested handcuffing the laptop to your  person, just to be safe.

An extreme example. ;-)
> 
if I ever went to defcon, I don't think I'd take a computer at all.

Why not ? Just make a backup of all your important data, and leave your important data on that backup at home, change your password before you go, and change them again after you're back. No need to become totally paranoid.
> 
 viruses, no. worms/rootkits(rare), spyware, and adware, yes.
Flash is becoming more and more of a problem with the new clickjacking, but there's the excellent noscript addon for Firefox.

---

### Post by 3Miro on 2009-03-27
> **albinootje said:**
> Where did you read about that "ability" ?
I've never heard about KDE and Gnome have the option of running scripts as root without using sudo by the user.

The problem is with the dot desktop files in KDE and Gnome which do  not require the executable bit on those files.
The trouble with that is that a normal user can double-click on an (dot desktop file) attachment in KDE or Gnome, and it will be executed.
Any other file apart from those dot desktop files would need the executable bit first in the scenario of an email attachment.

Probably I misunderstood. There was part describing how to get from user space to root space by placing a start up script in .kde something.

Anyway, why is the kernel allowing execution of a command without the x bit set. That should be impossible.

---

### Post by doas777 on 2009-03-27
> **albinootje said:**
> 

Why not ? Just make a backup of all your important data, and leave your important data on that backup at home, change your password before you go, and change them again after you're back. No need to become totally paranoid.

Flash is becoming more and more of a problem with the new clickjacking, but there's the excellent noscript addon for Firefox.

lol. your right. I'm not worried about my data, I just don't want to suffer the ignomity of being posted on their famous "wall of shame".

NoScript rocks!

have fun.

---

### Post by doas777 on 2009-03-27
> **3Miro said:**
> 
Anyway, why is the kernel allowing execution of a command without the x bit set. That should be impossible.

well the problem is gnome (kinda). all shortcuts would need to be marked as x in order to work, and that may or may not be possible depending on the permissions on ~/ and the rights of the user. creating a shortcut should be somthing that can be done in userspace.

also gnome is used on systems that use other auth methods than sudo. they have to leave authorization up to the host distro.

---

### Post by Angel Villablanca Luoni on 2009-03-27
We know that every time the trash of Ubuntu is cleaned, appears a folder named .Trash-1000 and when the trash is empty there is nothing inside. BUT, many colleages and I have a problem with the USB devices, like flash memories or external HD, in this way:
Inside de folder mentioned in the USB devices appear two folders, one named Files and the other Win98, and the worst, it is impossible to format that devices, including using Ubuntu commands and programs. When I try to delete or format these folders and others, it appears the note: "Protection against writing"...
My PC has a 80 Gb HD with XP and a 350 Gb with Ubuntu, so I must use my flash memories and external HD with both.
I did ask advice in the Ubuntu forums from Spain and Latin America, but with no possitive results.

An idea?

Greetings,

Angel

---

### Post by blackgr on 2009-03-28
> **Angel Villablanca Luoni said:**
> We know that every time the trash of Ubuntu is cleaned, appears a folder named .Trash-1000 and when the trash is empty there is nothing inside. BUT, many colleages and I have a problem with the USB devices, like flash memories or external HD, in this way:
Inside de folder mentioned in the USB devices appear two folders, one named Files and the other Win98, and the worst, it is impossible to format that devices, including using Ubuntu commands and programs. When I try to delete or format these folders and others, it appears the note: "Protection against writing"...
My PC has a 80 Gb HD with XP and a 350 Gb with Ubuntu, so I must use my flash memories and external HD with both.
I did ask advice in the Ubuntu forums from Spain and Latin America, but with no possitive results.

An idea?

Greetings,

Angel

If the device is set to read only im afraid you cant do much. I have a free usb stick with ads in it and it was impossible to erase them. THe  device was configured to read only mode. Well i cant be 100% sure for this. Just google more. Use mount commands to figure out the filesystem of the usb devices, and if you like send us more info.

---

### Post by humphreybc on 2009-03-29
This has turned into a very interesting thread! I love Ubuntu :D

---

### Post by Sef on 2009-03-29
> - Linux accounts for under 2% of all OS' in the world, whereas Windows has around 90% therefore most viruses are .exe, targeted at Windows for this reason.

For desktops, Microsoft has the majority of oses on desktops; however, even Microsoft admits that GNU/Linux is the majority in the server market, yet the majority of malware are written for Microsft.

The 2% number is just an estimate.  No one really knows how many GNU/Linux desktops there are.  I would not be surprised if it was double that at least.

---

### Post by Icehuck on 2009-03-29
> **Sef said:**
> For desktops, Microsoft has the majority of oses on desktops; however, even Microsoft admits that GNU/Linux is the majority in the server market, yet the majority of malware are written for Microsft.



Attacking servers doesn't get you any money. If you attack the user you can bombard them with ads, get credit card numbers, social security numbers, ATM pin numbers, and anything else you could use to make money. With that said it's obvious why no one goes after the server.

---

### Post by pbpersson on 2009-03-29
When Linux has more that 5% of the market share and it becomes an easy target there will be more viruses.  If it ever approaches the popularity of Windows, there will be tons of viruses, trojans, whatever.

I am tired of people saying, "Oh, a virus cannot ever do anything without root access" because that argument makes no sense to me.

If a grandma or typical-user is at the keyboard....as a virus all I need to display is:

**For optimal efficiency the system will now need to re-align your Heisenburg Compensators.  Please enter the administrative password at this time so this process can begin immediately.**

Furthermore.....as a trojan running in your system embedded inside a data file as a macro, if I delete everything I find in your /home/user directory including all your data and all your application settings and your email.....how is that not as bad as any Windows virus?

Or.....I am sure that just by sending an email to Linux computers I can get people to double-click on a shell script.

**The center for Linux security has recently received reports concerning viruses that might attack Linux machines.  In order to scan your machine for any malicious code that you might have already unknowingly downloaded, please double-click on the attachment and we will scan your hard drive and remove any viruses that might destroy your data.  Please be patient, this process might take a few minutes.**

---

### Post by pbpersson on 2009-03-29
<comment>

People on these forums keep picking on grandmas, using them as the image of the typical user who has no idea how a computer works.

If I was an 80-year-old grandma who was a master kernel developer, I would feel very maligned and highly offended.

</comment>

I really need to stop doing that  ;)

---

### Post by sgosnell on 2009-03-29
My mother, who is an 80+ year-old grandma, won't click on anything unless she knows what it is, or asks me first.  She's very suspicious, and very afraid of doing something to ruin her computer.  I don't know if she's typical, but I suspect she's far from the bottom percentile in that area.  The viruses seem to affect teenagers more than older people, because the kids use limewire, install any game they find, and in general feel impervious to any danger.  

It's also much easier to write viruses for Windows, using that ridiculous Visual Basic Scripting, which makes it a piece of cake for any script kiddie to write malware and put it out in the world.  Writing a virus for Linux requires some actual programming knowledge.

---

### Post by cardinals_fan on 2009-03-29
> **listerdl said:**
> wow thats amazing.

Basically I think that owing to the above...isnt linux just going to - eventually - overtake windows? I mean, surely it has to? People are becoming more educated about viruses and software.....

Thanks for your reply.
The day when the public at large actually becomes more educated about viruses and software will be the day when it doesn't matter what OS they use because they have the know-how to stay safe.

Pbpersson hit the nail on the head above.

Re. Linux malware taking more skill to write: Not really.  It's not rocket science to launch a malevolent script with gksudo and trick the user into entering a password.  The 15-minute sudo timeout is (in my opinion) a grave security risk in this regard - a normal apt-get command could be launched to "install dependencies", and then the malware is free for 15 minutes.

---

### Post by MasterNetra on 2009-03-29
> **doas777 said:**
> I once attended a conference exibition on how to best protect your laptop while stuck in the most dangerous place in the world - DefCon.

the talk was all based on ubuntu hardy, so I felt at home. I was amazed at the lengths needed to compute safely in such an environment. they recommended reconfiguring ufw to block all outbound packets except those to your custom VPN connection (to your home base) and to perform all net access from there. they provided a script to hash all your files and do before/after comparison, lock down all apps with selinux, special mount parameters, onetime passwords, no sudo time frame, full disk encryption, grub lockdown, IDS, uninstall hibernate, remove all compilers....
 they even suggested handcuffing the laptop to your  person, just to be safe.

Wouldn't just using a one-time restricted account (maybe allow access to only your CD/DVD drive & Internet with that account and it would be like a temp guest account) be easier? Prehaps if you only have your admin account and a restricted account for daily use, you could have their home directories's file permissions for "other" set to none? After you leave Defcon you could then remove the temp account just to be on the safe side. After all if you have a very strong password on your admin account (mine exceeds 20 characters ;) ) then you should be alright shouldn't you? Of course i guess you could set your pass for the daily account to a very strong one if it isn't then change the passwords for all your accounts after Defcon.

---

### Post by albinootje on 2009-03-29
> **pbpersson said:**
> When Linux has more that 5% of the market share and it becomes an easy target there will be more viruses.  If it ever approaches the popularity of Windows, there will be tons of viruses, trojans, whatever.

That's nonsense. 
Please do some reading about the definition of a virus, a trojan horse, a worm etc.

Trojan horses and worms for Linux possible, sure.

Viruses for Linux who will be the base of a massive spam botnet ? Highly unlikely.

---

### Post by albinootje on 2009-03-29
> **Icehuck said:**
> Attacking servers doesn't get you any money. If you attack the user you can bombard them with ads, get credit card numbers, social security numbers, ATM pin numbers, and anything else you could use to make money. With that said it's obvious why no one goes after the server.

You're forgotting about the "fun" that people get out of defacing websites, and playing with DDOS attacks.

If I were to make a spam botnet I'd think that MS ISS servers who are on 24/7 are more useful than desktop machines which get turned off every night, although the different timezones do help in the latter scenario, especially when you have control over thousands of infected Windows desktop.

---

### Post by amauk on 2009-03-29
he's also forgotten about the insane amount of financial data present on servers

online banking?

---

### Post by sydbat on 2009-03-29
> **amauk said:**
> he's also forgotten about the insane amount of financial data present on servers

online banking?BIG +1

What is really more worthy of attacking - someone (maybe) online banking? Or the bank themselves?

If I were a cracker, I would go after the big money sitting on a bank's servers...transferring it to a Cayman account and then "retiring" forever. This doesn't happen though. Why?

---

### Post by cardinals_fan on 2009-03-29
> **albinootje said:**
> That's nonsense. 
Please do some reading about the definition of a virus, a trojan horse, a worm etc.

Trojan horses and worms for Linux possible, sure.

Viruses for Linux who will be the base of a massive spam botnet ? Highly unlikely.
I would love to see someone infected with a self-replicating virus on any system.  I never have.

EDIT: Cracking a major server with loads of confidential information would require lots of skill, time, and effort.  Writing a little piece of spyware installed by mindlessly allowing a random popup isn't complex or difficult.

---

### Post by sydbat on 2009-03-29
> **cardinals_fan said:**
> I would love to see someone infected with a self-replicating virus on any system.  I never have.Well...maybe a dozen years ago...

---

### Post by cardinals_fan on 2009-03-29
> **sydbat said:**
> Well...maybe a dozen years ago...
Exactly.  They are a thing of the past (thank your ISP, router, and webmail provider).

---

### Post by listerdl on 2009-03-29
Wow! I started this thread, seems like a opened a can of worms! (pardon the pun)!

---

### Post by mistypotato on 2009-03-29
:)  yep.

Definition:

***A secure OS is one that has never been installed on a computer.***




:guitar:

---

### Post by mistypotato on 2009-03-29
> **pbpersson said:**
> When Linux has more that 5% of the market share and it becomes an easy target there will be more viruses.  If it ever approaches the popularity of Windows, there will be tons of viruses, trojans, whatever.

I am tired of people saying, "Oh, a virus cannot ever do anything without root access" because that argument makes no sense to me.

If a grandma or typical-user is at the keyboard....as a virus all I need to display is:

**For optimal efficiency the system will now need to re-align your Heisenburg Compensators.  Please enter the administrative password at this time so this process can begin immediately.**

Furthermore.....as a trojan running in your system embedded inside a data file as a macro, if I delete everything I find in your /home/user directory including all your data and all your application settings and your email.....how is that not as bad as any Windows virus?

Or.....I am sure that just by sending an email to Linux computers I can get people to double-click on a shell script.

**The center for Linux security has recently received reports concerning viruses that might attack Linux machines.  In order to scan your machine for any malicious code that you might have already unknowingly downloaded, please double-click on the attachment and we will scan your hard drive and remove any viruses that might destroy your data.  Please be patient, this process might take a few minutes.**


This guy is correct like it or not.  An OS is nothing more than 1's and 0's on a hard drive.  Gain the ability to manipulate a few of those through "today's security flaw" and Linux (like any other OS) can be made to do dishes and clean windows  :guitar:

---

### Post by doas777 on 2009-04-01
> **MasterNetra said:**
> Wouldn't just using a one-time restricted account (maybe allow access to only your CD/DVD drive & Internet with that account and it would be like a temp guest account) be easier? Prehaps if you only have your admin account and a restricted account for daily use, you could have their home directories's file permissions for "other" set to none? After you leave Defcon you could then remove the temp account just to be on the safe side. After all if you have a very strong password on your admin account (mine exceeds 20 characters ;) ) then you should be alright shouldn't you? Of course i guess you could set your pass for the daily account to a very strong one if it isn't then change the passwords for all your accounts after Defcon.
lol, based on the presentation, no. #1 priority is physical security. Physical access = root access any way you dice it.

The real fear at Defcon, is that someone will crack your password, at which point you account info and a photo are placed on their "wall of Shame". just being in the building means your playing the game.

in reality I would prolly take a laptop (and follow most of your suggestions, as they are quality), but i would probably expect to be taken out early on. I'm good, but my hat is still on the white side of grey.

best regards,
franklin

---

### Post by albinootje on 2009-04-01
> **MasterNetra said:**
>  After all if you have a very strong password on your admin account (mine exceeds 20 characters ;) ) then you should be alright shouldn't you? 

By default the password encryption software on Linux has a maximum of 8 characters as far as i know.
Unless .. you use blowfish (standard in OpenBSD) in Linux, but installation+configuration of blowfish for system passwords in Linux is not really well documented.
I've set it up on some machines some time ago, you need to install libpam-unix2 and make some changes to some pam configuration files.

---

### Post by xir_ on 2009-04-01
> **doas777 said:**
> lol, based on the presentation, no. #1 priority is physical security. Physical access = root access any way you dice it.

The real fear at Defcon, is that someone will crack your password, at which point you account info and a photo are placed on their "wall of Shame". just being in the building means your playing the game.

in reality I would prolly take a laptop (and follow most of your suggestions, as they are quality), but i would probably expect to be taken out early on. I'm good, but my hat is still on the white side of grey.

best regards,
franklin


security at defcon.... virtualise a system. wouldn't that sandbox any attack into the fake system?


other topic: I don't think that we will ever see a windows style botnet in linux mostly because anyone who made one would come to quickly regret it.

---

