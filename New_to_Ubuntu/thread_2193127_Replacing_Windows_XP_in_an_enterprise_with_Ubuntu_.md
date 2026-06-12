---
title: "Replacing Windows XP in an enterprise with Ubuntu or Lubuntu"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by mpxxuk on 2013-12-11
I have about 10 old computers running XP in an enterprise which we can't upgrade to Windows 7, and rather than just junk them when Microsoft support ends, I was looking for an alternative, and it looks as if Ubuntu or Lubuntu is the answer!  It seems to me that you can do everything in Ubuntu that you can do in Windows, but without the endless security concerns, bugs, slow running, etc.

I have started a list of steps for **beginners (like myself)** which details the process of turning old computers into Lubuntu workstations (or Ubuntu if the hardware supports it), to make the conversion easier.  If anyone would like to add to the list, please do so.

I have based the list on Lubuntu, and some of the steps are not necessary if you use Ubuntu.

Note:  To create scripts similar to BAT files, use the text editor to create a file, starting with #!/bin/bash, save the file with any extension and then in file manager, right click and change permissions to make them executable.

1. Install Lubuntu from disk.  Choose the option to require password on login

2.  Install Libre Office:  sudo apt-get install libreoffice

3.  Install Evolution mail client: Sudo apt-get install evolution.  Also install Evolution MAPI client: apt-get install evolution-mapi

4.  Create script to disable touchpad while typing: 

#!/bin/bash

syndaemon -d -t

5.  Install rdesktop: sudo apt-get install rdesktop
Create rdesktop scripts: 

#!/bin/bash
rdesktop -f xxx.xxx.xxx.xxx

This enables you to connect to Microsoft Remote Desktop, and if your network is based on this, this is all you need to do.

The f switch makes the RDP window full screen. To get out of it click ctrl alt enter

6.  Install PPTP plugin

Sudo apt-get install network-manager-pptp

7.  Connect to Windows PPTP if desired.  Remember to check the encryption box in network manager, and choose 128 bit encryption

8.  For convenience, install Ubuntu software center:  sudo apt-get install software-center

9. Install Nautilus, which makes it easier to connect to network shares. sudo apt-get install nautilus.  Connect to Windows network shares

10. Create users not in the Sudo group so that users cannot install software or damage system files.

11. Install wine (sudo apt-get install wine) for applications that won't run natively in Ubuntu.

---

### Post by aromo2 on 2013-12-11
You're right.  All the stuff MOST people do in Windows can be done in Linux for free.

I would replace rdesktop with Remmina, a more robust Remote Desktop client.

Depending on your network setup, you may want to set LDAP authentication against a MS domain controller to have password management centralized.

Good luck with your plans, I hope you share with us a success story once it's executed.

---

### Post by Mark Phelps on 2013-12-11
>  It seems to me that you can do everything in Ubuntu that you can do in Windows,

Not really ...

What you CAN do is all the mundane stuff that folks typically do with their home PCs: browse the Web, do emails, engage in social media.

What you can't do is run Windows software with the same level of features that you had previously in XP.  This includes connecting to exchange servers, and using any MS Windows web clients that require Internet Explorer to work.

Also, you need to understand that Linux is a free ALTERNATIVE to MS Windows, not a free VERSION.  What this means is that your folks using the XP machines will have to learn all new apps to continue what they are doing now in XP.

How hard will this be?  Depends on the following:
1) What apps your folks use.  If they rely daily on  MS Office 2010 apps, Internet Explorer, MS Outlook (connected to an Exchange server), they will find Linux a challenge to learn -- since they will not be able to use the same apps.
2) How much the work that is being done depends on Windows apps -- for which there are not very similar alternative in Linux.  Speaking from experience (as I have done Change Management on the Enterprise level), almost no one likes change, and the more they have to change how they do their jobs to use Linux apps, they less they are going to like the switch over to Linux apps.
3) Degree of interchange of files with other MS-oriented systems.  The Open-office alternatives do NOT handle the MS "XML" format files well.  If your folks regularly exchange Word and/or Excel files with other folks using Office 2007 or newer, they are likely to encounter problems in file conversion.

Practice has shown that the best way to handle the kind of migration you are planning is to convert one or two folks over, let them experiment with Linux, and have those folks serve as the tutors for the other folks.  Going "cold turkey" (switching everyone at once, with no one experienced with the changes) is asking for problems.

---

### Post by mpxxuk on 2013-12-11
Thank you both for taking the time to  reply, and you have given some very good advice:  One of the reasons I like Ubuntu is the intelligent, helpful forums which really tell you what you need to know:  With windows one has to wade through endless nonsensical technet articles.

I like the idea of using LDAP, and testing the OS on a few people first.  It's useful to know that interchanging between office suites creates difficulties. 

The computers I plan to convert are in a production environment where they mainly use the web and a bespoke database system which I have tested and it works.

I definitely think, though, that one reason for using Ubuntu is the way folks are so happy to give useful advice, non juidgementally to beginners like myself. It makes life much easier and more pleasant!

---

### Post by CamPsych on 2013-12-11
Sounds like a great idea in principle, but just be careful as mentioned by a few other posters that there can be issues with people adapting to the change, especially considering people's different tech education and ability. 

The forums are great, don't get me wrong, but sometimes you may find that your questions aren't answered or only partly answered, the community is fantastic, but everyone has their own lives and priorities, and thefore may not be able to focus on your specific questions. Consider getting a professional on board as a consultant if your questions can't be answered, that way you always have a fall back.

---

### Post by mpxxuk on 2013-12-11
The first computer I conveted belongs to a 78 year old who really doesn't understand IT at all, and he is getting on very well, in fact he hasn't called me for support once.

About a third of computers are running XP:  It would be a real tragedy if a large number of them were junked when they can be turned into very good workstations with a simple, fast and intuitive OS like Linux.

So far I have found answers to everything I need on the forums, a real tribute to the generosity of people here.

---

### Post by mörgæs on 2013-12-11
In stead of struggling with own office package, own mail servers and own this-and-that you could also consider switching to Google Apps. After that the only thing you need is a number of computers (say, previous XP machines) capable of running Lubuntu and a browser. Full integration with mobile units. Maybe invest in one Windows 7 computer for unforeseen events.

---

### Post by DuckHook on 2013-12-11
Were I to set up an office today (I've done this a few times in my past lives), I would start with pure Linux and enforce a Linux regime. Back in my day, this was not possible because Linux on the desktop was just not ready for prime time. These days, Desktop Linux has advanced to the point where it will work in a small office/business environment that uses general apps and does not need specialty software. Here are some of the areas that are still problematic:

1. Exchanging documents with the Windows world. You will invariably get documents from people who format their docs with some obscure or loopy MSOffice functions. These will not open or display properly in LibreOffice.
2. CAD stuff. The professional CAD world is dominated by AutoCAD. There is no equivalent in the Linux-sphere.
3. Project software. The Linux equivalents to MSProject are either poor also-rans, or expensive proprietary high-powered project-ware.
4. Accounting packages. There is no small-to-mid sized accounting package in the Linux-sphere equivalent to similarly-positioned packages in the Windows world. There are proprietary industrial-strength Linux packages, but you are back to expensive proprietary systems again.
5. Professional Linux page layout packages lag far behind. Scribus is not even close to Windows packages like Quark or Indesign.
6. POS, CRM, and other customer/sales-ware are very primitive in Linux compared to Windows. This is mitigated by the fact that some great CRM is net-based these days, but this is not practical for POS.
7. By far the biggest challenge is Linux/Windows coexistence. Windows is a bully who doesn't play nice with anyone else on the playground. If you can't get out of Exchange or Outlook for the majority of your users, then you will have huge barriers to surmount. This is why I wrote at the outset that the easiest way is to start from the ground up enforcing a pure Linux environment. MS is like crack. If you get hooked up front, the withdrawal process is both painful and awful.

The above are just the areas I'm familiar with. Members here can advise you of other roadblocks.

The use-cases that tend to port well are industries whose outputs are primarily in the area of expertise. Consulting, coaching, tutoring, etc. where the output is not tied to specific formats. If your industry is advertising, architectural design, project work, accounting, etc. it's almost impossible to run a Linux shop. Linux can still play a significant role, but it tends to be in the backoffice and not up front.

---

### Post by mastablasta on 2013-12-12
> **DuckHook said:**
> 
4. Accounting packages. There is no small-to-mid sized accounting package in the Linux-sphere equivalent to similarly-positioned packages in the Windows world. There are proprietary industrial-strength Linux packages, but you are back to expensive proprietary systems again.


my wife worked arround this one by using a web based service.

for a few others a combo of OS could be used. e.g. where i work only development department works with CAD the rest use emails, word and excel for the most part. and an ERP that has a linux client. i believ we could switch in majority of computers, instead they are tying themselves more and more in windows. e.g. making websites that work in IE only, using MS cloud solutions...

---

### Post by DuckHook on 2013-12-12
> **mastablasta said:**
> my wife worked arround this one by using a web based service.This is an excellent workaround if it is just one or two users, but won't really work in a team environment that is heavily collaborative. Even an accounting department of a half-dozen users will find it impossible to work effectively on web-based apps. In such an environment, a database-oriented package that has proper record-locking, data-redundancy, on-site and off-site backup, etc is the only real option. If the accounting needs are strictly mainstream, I suppose that gnucash in SQL mode might by hook and by crook be made to work, but the accounting staff will grumble and moan so loadly about its limitations that any CFO will give in and buy a high-gauged package just for the sake of his/her sanity.> for a few others a combo of OS could be used. e.g. where i work only development department works with CAD the rest use emails, word and excel for the most part.The problem is precisely because it's only "for the most part". It's those infrequent but still necessary occasions where someone will suddenly want access to CAD/Accounting/CRM/Project/etc while making a presentation in the boardroom, or updating the COO, or cross-collaborating with the marketing group, that will show up the limitations of a mixed OS strategy. Few businesses today isolate their activities into well defined silos and most dynamic businesses encourage collaboration and interdepartmental outreach. In such an environment, no one will put up with an IT structure that cannot transparently facilitate such communication.> and an ERP that has a linux client. i believ we could switch in majority of computers, instead they are tying themselves more and more in windows. e.g. making websites that work in IE only, using MS cloud solutions...+1

Hence my equating MS to crack. The further problem is that, like most addicts, MS addicts won't admit that they are addicts, and therefore won't seek treatment.

I still believe that a lot of organizations these days actually can make the full-fledged leap to a pure Linux environment. Most orgs don't use CAD at all, and if they must invest in a full-fledged accounting package, then so be it. The savings in the rest of the organization will more than offset the cost of the accounting/CRM/specialty Linux package that must be purchased.

---

### Post by whitesmith on 2013-12-12
Have a look at the website mentioned in my sig line. The author strives to disabuse those who think Linux is by some magical process "free Windows." It isn't.  Linux is free but there is a price to be paid for that freedom. Whether you are willing to pay it is up to you. Best of luck in your efforts!

---

### Post by mpxxuk on 2013-12-14
I started this post as a way of putting my toe in the water to see what reaction I would get, and I am very favourably impressed by the exceptionally high quality advice I have received from people who generously give their time to give very detailed and helpful replies!  

I am slowly getting over the wow factor of an operating sytem which, although it requires a little getting used to, is flexible, intuitive, secure, and above all FAST, and am realising that replacing Windows will not be as simple and as straightforward as I thought.

I think I can conclude the following:

[LIST=1]
[*]It *is *possible to replace Windows with Linux, or specifically, Ubuntu, but it will not all be plain sailing, and I will encounter resistance from users who have to get used to doing things the Linux way, which is different from Windows and has to be learned.
[*]For the last 10 years I have been addicted to 'Crack' Windows, and have been on the endless upgrade treadmill as each product reaches the end of its life cycle, and have junked far to many old computers.  This addiction has been very expensive for the people I work for! I really need to go to Windowsaholics Anonymous! :)
[*]Linux is not a free version of Windows:  It is a completely different world.
[/LIST]

However, thanks to the folks who inhabit this forum, and specifically the respondents to this thread, I am confident that this is a project that is feasible, and the learning process will be enlightening and worthwhile, not only from an technical point of view, but from the point of view that being part of the Ubuntu community seems to bring out the best in people.  Thank you again for your excellent replies!

---

### Post by cmcanulty on 2013-12-14
Realize you can still install XP using your key in a virtual box for the rare time you may need it also could install office in wine in case there are formatting issues. I think you'll be fine. Also libre office lets you save docs in windows format if you like

---

### Post by mörgæs on 2013-12-14
So, what will be your decision?

---

### Post by mpxxuk on 2013-12-14
Good question:  I plan to do the following:
1.  Set up one user with a box running lubuntu, after I get VNC working, and try it out for a month.    I mostly support this site remotely, and need to ensure that I can easily solve problems by telephone and VNC if they occur.  

2.  I will also give the user access to a fully configured XP virtualbox if he really needs XP

3. If it doesn't work out, which I doubt, I will retire all XP computers from the system in April, install either Ubuntu or Lubuntu on them and give them away to charitiable organisations or individuals who can't afford to buy a computer.  My main concern is that the computers in question do not end up in landfill when they are perfectly serviceable.

That's the plan.  I will keep the thread updated, because as I mentioned earlier, a third of the world's computers are running XP, and I would like to create a simple plan of action for Windows administrators like myself to follow, to enable them to re-use at least some of them.

---

### Post by DuckHook on 2013-12-14
If setting up VNC for remote support, please do read [this]("http://ubuntuforums.org/showthread.php?t=510812") thread. The biggest issue with all remote desktops is security. VNC is one of the two protocols that, in its default configuration, are the most often and easily cracked. If you are lucky, the scumbag who does so will just wipe out your user's /home directory. If you are unlucky, said scumbag will install a keylogger and shortly have access to all areas of your organization that the user can access—perhaps inclusive of admin accounts including yours.

The idea of XP in a VM is theoretically sound. Just be careful of my experience where the users never make the transition to Linux because they spend 100% of their time in the VM feeding their addiction to the OS that they know. When under constraints of time and pressure to produce, it is only human nature to fall back to the familiar tools, even if this means pounding in a nail with a scewdriver (I had an accountant who wrote all of his letters with Excel).

If looking for more ideas for old HW, as luck would have it, see [this]("http://ubuntuforums.org/showthread.php?t=2193188") concurrent thread, and do read *mörgæs's* signature link.

Best of luck. Taking liberties with the old Chinese... ehm... phrase: You are a brave one, bound for "interesting" times.

---

### Post by mörgæs on 2013-12-16
Sounds like a good plan, except

> **mpxxuk said:**
> 
Set up one user with a box running lubuntu

I am afraid this guy will feel alone, no matter how well Lubuntu works. A gang of 3-4 people will make for a better environment and should be able to give each other a minimum of support.

---

### Post by SeijiSensei on 2013-12-17
How much memory do these machines have?  Running XP in a VirtualBox VM requires at least 512M and usually runs better in 768M or above.  If these are 2 GB machines, you should be fine with each OS getting 1 GB or so, but if the machines have only 1 GB of memory or less, a virtual machine will run much too slowly in most cases.  You don't want your new Ubuntu users complaining that anytime they need to use Windows their computers grind to a halt.

I agree with the small group approach, too.  It will create some camaraderie among the chosen few, and they can help each other when problems arise.

---

### Post by mpxxuk on 2013-12-22
> **mörgæs said:**
> Sounds like a good plan, except



I am afraid this guy will feel alone, no matter how well Lubuntu works. A gang of 3-4 people will make for a better environment and should be able to give each other a minimum of support.

This is **excellent advice**, and something I tend to forget when dealing with users:  The effect of change.  The user I am thinking of has a very slow XP workstation, so I will give him a Ubuntu replacement and leave his old computer next to it so that he can swop back if he can't cope.  Switching 4 people over at once would be too disruptive, unfortunately.

---

### Post by philinux on 2013-12-22
What are the specs of these machines?

---

### Post by mpxxuk on 2013-12-22
> **SeijiSensei said:**
> How much memory do these machines have?  Running XP in a VirtualBox VM requires at least 512M and usually runs better in 768M or above.  If these are 2 GB machines, you should be fine with each OS getting 1 GB or so, but if the machines have only 1 GB of memory or less, a virtual machine will run much too slowly in most cases.  You don't want your new Ubuntu users complaining that anytime they need to use Windows their computers grind to a halt.

I agree with the small group approach, too.  It will create some camaraderie among the chosen few, and they can help each other when problems arise.

**Also very good advice**.  I'll probably have to abort the virtualbox.  

The whole point of the project, in any case, is to **replace Windows**, so creating the functionality users need that they had with Windows is a much better strategy.

If all users need is to:

[LIST=1]
[*]To open and create documents
[*]Surf the web
[*]Get email from exchange (evolution)
[*]Browse to SMB network shares
[*]Use a bespoke database application that works well in Wine
[/LIST]

Then why would they need to revert to Windows? 

I plan to start the test in early January and will post my experiences here.

---

### Post by oldfred on 2013-12-24
Have you converted users in XP to Firefox & LibreOffice? That is a good first start to get them used to a new system as then the applications are the same. 

Some have said converting from the old Microsoft Office to LibreOffice or OpenOffice is easier than converting to the very new Microsoft Office anyway.

---

### Post by Mark Phelps on 2013-12-24
> If all users need is to:

    To open and create documents
    Surf the web
    Get email from exchange (evolution)
    Browse to SMB network shares
    Use a bespoke database application that works well in Wine

Then why would they need to revert to Windows? 

Ordinarily they wouldn't have to revert -- unless -- the following were true:
1) The documents they use are the more recent MS Office "xml" documents -- which the open-source office products don't handle well. To work well with .docx and .xlsx files, you really need MS Office.
2) They browse the web and either (a) are using Internet Explorer with plugins and/or extensions that only work in IE, or (b) are going to sites that require IE in order to work (and yes, such sites actually exist).
3) Require MS Exchange mail services that are not provided by other mail clients.
4) Require MS-specific network-related functions (e.g., Homegroups) that are not well supported in SMB.
5) Use a data base application that, while it works in Wine, requires daily use of functions and/or features that do not work well in Wine.

I'm not saying any of these are true of your situation -- but am saying that there are host of MS-specific restricts that can make switching over to something else very hard in some situations.

---

