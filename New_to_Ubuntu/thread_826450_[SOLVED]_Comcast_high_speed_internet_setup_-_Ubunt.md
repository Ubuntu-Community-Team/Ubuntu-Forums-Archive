---
title: "[SOLVED] Comcast high speed internet setup - Ubuntu"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by anewguy on 2008-06-11
I'm switching to comcast broadband via my cable on Friday.  Currently I have AT&T dsl.  I do not have Windows.  Does anyone have experience setting up comcast broadband in Ubuntu?  Is there a sticky or something somewhere?

I want to be fully prepared for when the installer comes out and tries to tell me it can't be done. :)

---

### Post by anjilslaire on 2008-06-11
THere's nothing really to be done. Make sure your NIC is set to DHCP (default setting). Of course, you should have a router in place on any persistant connection, which makes everything simple:
1. Plug cable modem into router
2. Plug router into computer

There's no real relationship between your OS and your ISP, despite what they may try to tell you.

---

### Post by anewguy on 2008-06-11
Thanks for the reply.  I seem to remember they have an "installer" program that is either Windows or OSX, but not Linux.  I know I've used a wireless connection via Comcast in the past, just never "set one up" with just Linux.  I'll give it a go and see what happens!

Thanks!:)

---

### Post by jimrz on 2008-06-11
You do not need to use their installer (or whatever malware comes with it) and most routers anymore will automatically configure themselves with your cable modem. I did their "self install" kit thing several years ago and am on my 3rd cable modem (2 of theirs quit, so I finally just went and bought a Motorola Surfboard and stopped paying for the rental ones) and have never used their installer, ever. Have 5 boxes (2 dual boot + 3 ubuntu only) accessing the modem through a router and no issues (cheapie rental modems aside) at all. If you do not already have a router I would suggest you go pick up one. You can get a good 4 port + wan (netgear, d-link or linksys) pretty cheap, anymore.

---

### Post by abn91c on 2008-06-11
the comcast installer is just crapware, you dont need the disk doctor or any of that other stuff, just setup the router according to the manufacturer, make sure you change the router password, the default is admin for most cable routers and set up at least a WPA encryption.

---

### Post by anewguy on 2008-06-11
Thanks everyone.  I figured it should be a simple matter - even if their installer just set up the dns, gateway, and pointed to an initial site to set up my account.  Their online chat support was useless and after 20 minutes gave me the 888 number for normal service.

I have a wireless adapter on my desktop currently going to a 2WIRE dsl wireless - I picked up a regular wireless router today so I would be ready there.  Guess it might be fun trying to get wap working with another router, but that's another "bridge" (pardon that) to cross.

Thanks again!  :)

---

### Post by anewguy on 2008-06-13
BTW - here are my concerns:

- since Comcast doesn't support Linux, I would imagine I am going to need to manually set up the mail servers, and need to be able to get that information.  I believe it also takes you to a site first thing that goes through the "registration" process - and amongst that is setting up a username and password for email, etc..  Will their tech support be able to give me the address for that page?  So far, they are not interested in saying anything to me about any of this.

---

### Post by cariboo on 2008-06-13
If you've still got windows running I would suggest letting the installer setup everything in windows and then manually transfer what you need to linux. Remember most cable installers are barely computer literate and only know what they've been taught to do setting things up in windows.

Jim

---

### Post by thisiam on 2008-06-13
I hate using my ISP email service. it goes down more than it should and what if you decide to leave the company but you have 1000 contacts emailing you at your comcast email address. gmail works alot better imho and you can get mail server info from their website. amd gmail notifier is cool. its a good service and free.

but if you want to use it, call them and if they ask you what OS you have tell them it doesn't matter and you are looking for mail server info
or just say windoze and get the info you need.

---

### Post by phr0ze on 2008-06-13
> **anewguy said:**
> BTW - here are my concerns:

- since Comcast doesn't support Linux, I would imagine I am going to need to manually set up the mail servers, and need to be able to get that information.  I believe it also takes you to a site first thing that goes through the "registration" process - and amongst that is setting up a username and password for email, etc..  Will their tech support be able to give me the address for that page?  So far, they are not interested in saying anything to me about any of this.

Don't use their mail. When you switch again you have to set up another account. Plus they aren't great at stopping spam. Go get a gmail account and avoid the mess and get more storage.

I told my installer I didn't want any crap and he used his company laptop to setup everything. There is absolutely nothing that comcast puts on your system that you want. Most of the time it causes problems and has features for comcast to remotely access your system.

---

### Post by SunnyRabbiera on 2008-06-13
I am using comcast, and no there is no real issue in using it in my experience... it was pretty much plug and play.
as for mail, I use thunderbird to view my email.
setting it up for comcast is easy.

---

### Post by jimrz on 2008-06-13
they will set you up with your user name and a temp pw that you can (and, of course, should) change on your comcast.net home page.

mail servers = mail.comcast.net + smtp.comcast.net, and are easy enough to set in Evolution or whatever email client you choose. also, they present no problem when using pgp.

---

### Post by abn91c on 2008-06-13
> **anewguy said:**
> BTW - here are my concerns:

- since Comcast doesn't support Linux, I would imagine I am going to need to manually set up the mail servers, and need to be able to get that information.  I believe it also takes you to a site first thing that goes through the "registration" process - and amongst that is setting up a username and password for email, etc..  Will their tech support be able to give me the address for that page?  So far, they are not interested in saying anything to me about any of this.

you can use the linux email applications that comes with openoffice.org, I use Kubuntu so its called Kontact, the setup for comcast is as follows:
pop3 is mail.comcast.net
smtp is smtp.comcast.net
then just put in your comcast user name and password
If you have a comcast account already you dont need to register anything for comcast, you may just have to use Firefox for the internet and make sure the flash and java work

---

### Post by anewguy on 2008-06-14
The big problem is the initial setup - Comcast tries to point you to a web page to set up your user name, password, etc., and that page wants to download a Windows executable.  Seems like I should be able to call them and just tell them to set up the account, but while the tech was here today I overheard his phone conversation and the guy at the other end replied "maybe" when asked if I could call in later to set it up (their registration server was down).  I decided not to sign off on it and forcing them to return in the morning to finish.  It seems so stupid to me - all of this should be platform/OS independent.  They should just have a web page, no extra program to run locally, that let's you set up your account information and then let's you manually configure your mail servers.  All they have to do is "unlock" the portal - everything else is independent.  After I see what they do in the morning, I may send an email off to their tech support about this (like they'll pay any attention).  Just seems stupid to me to say you have to have a supported version of Windows or MacOS to access their registration process.  This was the part I felt would be trouble, and it has been.  Obviously, once your account is set up, you can access it from any OS as long as it supports TCP/IP and hopefully has a web browser. It's just stupid.

:)

---

### Post by jimrz on 2008-06-14
I'm sure that your city/county/whoever issed Comcast their franchise to provde cable services has some sort of oversight department or something to monitor Comcast's operations / performance. If they do not provide you with a reasonable solution, I would tell them that you planning to file an official complaint (and then do so). Since I am reasonably certain that none of the information that they provided prior to or at the time of the sale indicated that you would be required to both run a specific OS (or one of a group of approved OS's) AND allow them to install unwanted software (containing who knows what) on YOUR system, that this may be enough to get them to magically figure a way to resolve the issue without further ado.

---

