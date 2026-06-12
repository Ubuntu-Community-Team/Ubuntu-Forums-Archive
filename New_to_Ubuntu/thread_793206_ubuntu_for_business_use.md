---
title: "ubuntu for business use?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by oisuxx on 2008-05-13
i work in a large company, and we use windows here. is it possible to switch to ubuntu? what are the stipulations for putting ubuntu on machines for work. price wise, i know that ubuntu is free, i use it at home on 2 machines. but i didnt know what the rules were for using it in a business setting.

at work im not talking about 3-5 pcs. im talking 100's network wide.

---

### Post by SunnyRabbiera on 2008-05-13
Its perfectly legal to use ubuntu on servers and such, though if you ask me a better distribution for servers is debian as it tends to be more stable for servers and for the workplace.

---

### Post by hyper_ch on 2008-05-13
The biggest obstacles are:

(1) hardware compatibility... might be not all computer can run it

(2) software ... if you have specialized windows software there might be no alternative to it...

apart from those two, just go ahead :)

---

### Post by rockerphil on 2008-05-13
if you're wanting to switch to Linux for a work/server environment i'd suggest going to Red Hat/Fedora, it's tweaked more for the business where as Ubuntu is tuned to be used more as a home desktop/home network, hope this helped

---

### Post by Inxsible on 2008-05-13
Because you want to install it on 100s of machines, the only obstacle like hyper_ch suggested would be some Windows software that everyone uses or "is used to"

Something like Outlook for email. You will have to use Crossover Office or Wine to run these. Office is said to work under both, but some other Windows software might not.

You can choose many distros : RedHat, Suse, Ubuntu & Debian all have excellent support. I would advise you to definitely buy the customer support from whichever distro you choose. That would be much easier than having to fix individual computers within the company

---

### Post by mlentink on 2008-05-13
From the ubuntu site:

The Ubuntu promise

    * Ubuntu will always be free of charge, ***including enterprise releases*** and security updates.
    * Ubuntu **_comes with full commercial support_** from Canonical and hundreds of companies around the world.
    * Ubuntu includes the very best translations and accessibility infrastructure that the free software community has to offer.
    * Ubuntu CDs contain only free software applications; we encourage you to use free and open source software, improve it and pass it on.

---

### Post by oisuxx on 2008-05-13
these responses really help out alot. all we are using windows for is mail, web, powerpoint, and excel.

seems like a logical choice to run linux (ubuntu is what im used to).
instead of paying high dollars for using a crappy bug ridden, OS, like windows.

---

### Post by Inxsible on 2008-05-13
> **oisuxx said:**
> these responses really help out alot. all we are using windows for is mail, web, powerpoint, and excel.

seems like a logical choice to run linux (ubuntu is what im used to).
instead of paying high dollars for using a crappy bug ridden, OS, like windows.Web is just the web. Powerpoint and excel are easily handled with Open Office unless you are doing some heavy macros and stuff which I am not sure OOo can handle.

If everyone is willing to move to a web based email -- or get a gmail account and use Thunderbird, you can do away with Outlook as well. Although meetings and such will be a difficult task. Using Crossover office or Wine for Outlook would seem to be the best option. Wine is free, Crossover isn't.

---

### Post by mlentink on 2008-05-13
> **Inxsible said:**
> If everyone is willing to move to a web based email -- or get a gmail account and use Thunderbird, you can do away with Outlook as well. Although meetings and such will be a difficult task. Using Crossover office or Wine for Outlook would seem to be the best option. Wine is free, Crossover isn't.

Seems like you want to avoid Evolution, which works fine enough for me in an Exchange infrastructure...

---

### Post by Inxsible on 2008-05-13
> **mlentink said:**
> Seems like you want to avoid Evolution, which works fine enough for me in an Exchange infrastructure...Yeah. I have never been a fan of Evolution :(

---

### Post by oisuxx on 2008-05-13
> **Inxsible said:**
> Yeah. I have never been a fan of Evolution :(
we use outlook. this is the only drawback, i guess using it in wine would be an option. but you would still have to pay to use it in wine reguardless.

---

### Post by mlentink on 2008-05-13
> **oisuxx said:**
> we use outlook. this is the only drawback, i guess using it in wine would be an option. but you would still have to pay to use it in wine reguardless.

before you start drawing your checkbook, why not set up a testbench with a couple of ubuntu users, including a few that use Evolution? Might as well try it out before pulling your wad of dough.... ;-)

---

### Post by hyper_ch on 2008-05-13
I like Kontact (instead of evolution) quite a bit

---

### Post by JoshuaRL on 2008-05-13
> **mlentink said:**
> before you start drawing your checkbook, why not set up a testbench with a couple of ubuntu users, including a few that use Evolution? Might as well try it out before pulling your wad of dough.... ;-)

That's a good idea.  You could even have each of them run a different client:  thunderbird, evolution, and Outlook in Wine.  And you could see if they can handle running OO.o instead of Office.  If you can find a useable FOSS solution all the better.

---

### Post by sunstriker on 2008-05-13
I think Ubuntu could work well as server. Debian is faster, true. But Ubuntu is easier for more inexperienced users and systemadmins. 
For word, excel and that kind of stuff: openoffice or staroffice. If you want to stick with office: wine runs Office 2003 very well (not tried it myself though).
About your mail: You don't have to choose a client:
You could setup a mail system with fetchmail, postfix/sendmail, spamassasin... and use courier on top, it's an imap server which uses Maildir. You can put any mailclient on top of it (evolution, mutt, thunderbird) or install squirrelmail (webmail). It takes some time to tweak this all. But this system is extremely scalable and performant if tweaked well. (My isp uses this software too ;-))

EDIT: and there are some pretty good replacements for exchange server to cooporate with eachother. I didn't use them myself so far.

---

### Post by crjackson on 2008-05-13
I use Thunderbird with the lightning extension.  It works great...  It will remind you of Outlook.

---

### Post by mlentink on 2008-05-13
> **crjackson said:**
> I use Thunderbird with the lightning extension.  It works great...  It will remind you of Outlook.

As a tool for personal use, perhaps. But Outlook performs best in the Echange-environment, which is what most corporate users are accustomed to. I doubt if Lightning support group-scheduling, resource-scheduling, group discussion folders and the like. I don't want to pitch Exchange here, there are other groupware-packages as good and for a lot less.

---

### Post by peterroots on 2008-05-13
I'd go for Kubuntu as many MS users find it easier and less intimidating than Ubuntu.
Kontact makes as nice replacement for Outlook.  egroupware is good for sharing of address books and calender though I have never tried to set up a mail server with it but it should work with either web mail or pop3.
my only true business experience of Kubuntu is in an internet cafe but this was a lot less bother than when we ran windows in it!

---

### Post by ubunu on 2008-05-13
While I might be a total ubuntu newbie (3 days) I've been doing windows tech support & training for SME's for a few years now and latterly have been involved in switching people to safer software for some time now.

So far the discussion in the thread has focussed on the packages available and whilst we all know (and often enjoy the discovery process) that new alternatives can outperform you'll find that, in most business environments, it will be the PEOPLE and not the software that will occupy your time and absorb your costs.

In general I have found the following;

Switching people to Firefox has been no problem at all, a very high acceptance level and a small training cost. The majority came to prefer it in a short time and also switched at home.

Thunderbird I have found some very high resistance, especially from people who have been using Outlook for many years and who have become very used to using all its facilities such as calendar etc.

T'bird does not always import with total grace and does have a habit of throwing passwords out. In the end it can be cudgelled into use because of the extra security.

OpenOffice. I found people migrated to text/word very easily however one company that used an enormous amount of Powerpoint files found that they had to re-write all their transition and animations as they did not cohere in their new environment.

Moving from Access to the inbuilt dbase facility in OpenOffice is hard work and, in some cases has proved very expensive in terms of time and training.

Publisher. I am often surprised at how much this is used in the business environment, converting users ( and files) is not easy.

The point I am making is that the costs and effort can really come back and kick you and there are many people out there who, having been bred on MSOffice in sixth form and on are incredibly resistant.

As mlentink suggested get some test users but choose them carefully lest they poison the well. 

I have started switching OS now because I intend to follow through even though a significant portion of my income is derived from removing malware and updating defensive software.

I just wanted to shift the focus slightly as those of a techie disposition can sometimes fail to see things from 'users' point of view.

There, just 2p's worth

---

### Post by Inxsible on 2008-05-13
I don't know if this is an option but you can forget exchange just get some free web based email service. Of course this would not give you all the fancy features in Outlook like resource scheduling, appointment scheduling and such.

Outlook is one piece of software that still needs to be used in the Corporate environment.

But I tend to agree with mlentink, see what the users accept easily.

---

### Post by hyper_ch on 2008-05-14
> **sunstriker said:**
> I think Ubuntu could work well as server. Debian is faster, true. But Ubuntu is easier for more inexperienced users and systemadmins.
Why?

---

### Post by ugm6hr on 2008-05-14
> **ubunu said:**
> So far the discussion in the thread has focussed on the packages available and whilst we all know (and often enjoy the discovery process) that new alternatives can outperform you'll find that, in most business environments, it will be the PEOPLE and not the software that will occupy your time and absorb your costs.


Some of these changes could be made in parallel with Windows.

Perhaps it is worth trying Firefox, OpenOffice and Thunderbird on a few people on Windows to see whether it is possible to wean people off their MS Apps.

A period of transition might make things easier.

---

### Post by frozenjim on 2008-05-25
> **Inxsible said:**
> 
Something like Outlook for email. You will have to use Crossover Office or Wine to run these. Office is said to work under both, but some other Windows software might not.

Be cautious if you require Outlook functionality.  Wine does NOT support it at all.  Not since Outlook '97.

My company has not been able to switch our clients to Linux for exactly this reason.  There is NO replacement for Exchange/Outlook.  It's the business killer.

We have deployed test servers of OpenExchange, ClarkConnect and Evolution trying to find a groupware solution that will work on the Linux desktop.  There is no groupware solution in Linux yet.

Kontact groupware is the closest thing we have found but it requires you to load the entire KDE library set and it is buggy with frequent crashes if an IMAP message gets delayed during synchronization.

While there are some "kludge" solutions for Thunderbird, the truth is that there is no other Linux client for groupware.

Even the Linux groupware servers support only Outlook.  The Toltec connector works great - in Windows.

Currently my only solution is to run VirtualBox (like VMWare - only free) in order to use Outlook in my Ubuntu machines.  This is NOT an idea that I can sell to my clients.  It just makes me feel a bit better to still use my Linux machine for everything else.

(I would be thrilled for someone to prove me wrong!)

---

### Post by Jimmy9pints on 2008-05-25
I have found that Open Office writer cannot handle copy/pasted graphs, spreadsheets, and pictures. They often disappear, randomly change size and when exported to word become unviewable. 

This is my only gripe with open office so far, otherwise I would wholly recommend it. 

By the way, on this subject, what's a good opensource business solution for accounting? And how about CRM?

---

### Post by rpage on 2008-05-25
oisuxx,

when at work, if you login to the domain using active directory, good luck. I have been trying to get my ubuntu system to join the domain and have yet to do so. I have read many things on the web and tried some of them. But I have yet to get it to work. I am an IT person but very new to Linux.

If you do not have to join a domain, and need strictly office type software, openoffice is the way to go.

---

