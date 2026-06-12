---
title: "AntiVirus"
date: 2004-11-22
forum: Recurring Discussions
---

### Post by hitchhiker on 2004-11-22
Just wondeed what AntiVirus software people are using with ubuntu.

I've installed the Aegis Virus Scanner from the ubuntu repositories and that picked up a w32/magistr.a@mm virus in /usr/lib/win32/vp31vfw.dll which is a windows codec that I've now deleted. This was also from the ubuntu repositories so it is probably worth people checking theirs out.

HH.

---

### Post by mjpowersjr on 2004-11-23
[QUOTE=hitchhiker]Just wondeed what AntiVirus software people are using with ubuntu.

I've installed the Aegis Virus Scanner from the ubuntu repositories and that picked up a w32/magistr.a@mm virus in /usr/lib/win32/vp31vfw.dll which is a windows codec that I've now deleted. This was also from the ubuntu repositories so it is probably worth people checking theirs out.

HH.[/QUOTE]
 I'm not in my ubuntu distro right now so i dont know if a package is available but ClamAV ( [http://www.clamav.net/](http://www.clamav.net/) ) looks promising. Interesting, i've never tried Aegis, gonna test it out tonight. 
-mike powers

---

### Post by ubuntu_demon on 2004-11-23
[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

You don't need a virusscanner unless you want to protect windowsmachines in your network.

---

### Post by Perfect Storm on 2004-11-23
Yep, if you're only using linux there's no need of anti-virus programs. A firewall at least (there is no such thing as a 100% bullet proof OS)

---

### Post by jdong on 2004-11-23
[QUOTE=hitchhiker]Just wondeed what AntiVirus software people are using with ubuntu.

I've installed the Aegis Virus Scanner from the ubuntu repositories and that picked up a w32/magistr.a@mm virus in /usr/lib/win32/vp31vfw.dll which is a windows codec that I've now deleted. This was also from the ubuntu repositories so it is probably worth people checking theirs out.

HH.[/QUOTE]
 good chance that's a false alarm! Also, Windows viruses can't infect Linux.

---

### Post by mr_ed on 2004-11-26
Reading that, though, made me wonder if the original DLL was an infected file.  I know it won't affect my system, but if I were to copy it to a Windows machine, would the machine get infected?
Not that I plan on trying... :)

---

### Post by Sniffer on 2004-11-26
Yes, that's the all point of having an AV in Linux System, if you didn't scan you linux system you will never know if you have win32 virus, so if you pass that data to M$$$ machines....you are done

GOD HELP YOU :)

---

### Post by T31 on 2005-03-17
This is a false alarm, if use a little google u find out this virus infects files .exe and this   case is a file .dll, using aegis-virus-scanner tells me as well i got that virus, just a false alarm :)

---

### Post by dumbbeatnix on 2007-01-02
This strikes home for me though, why?

Wine ... Wine ... Wine!!!

I ran an installer from a loki site, to install Command & Conquer Tiberian Sun.  This program worked.  When I reboot DISASTER, lost the whole operating system.  Could only get as far as working in the shell.](*,) :twisted: :confused: 

I too did what the author of this post did, and fiddled around with the same virus scanner.:KS 

If you have a command and conquer or anything for that matter, and you use a loki installer, good luck to you.:-? 

As a consequence of this I do not intend to wine any longer.:neutral: :-k 

I too will be getting rid of the little nasty and installing another .dll file that is not infected.  For those of you who want infection free computers, I suggest you google and get an uninfected file.:-D

Cheers
dumbbeatnix

---

### Post by MrHorus on 2007-01-02
> **dumbbeatnix said:**
> 
I too will be getting rid of the little nasty and installing another .dll file that is not infected.  For those of you who want infection free computers, I suggest you google and get an uninfected file.:-D


As stated several times previously, this is a false alarm.

DLL files are NOT executeable files - they are software libraries that contain function calls useful to programes.

---

### Post by gregor171 on 2007-01-05
OK guys. I see some very claver answers 
:D dll could act as a virus on MS if it would replace an existing dll that is runned by some other programs.  
But I'd also like to know what antivirus are linux people using. I'd like to scan emails on something like Postfix email server, but also html files posted by users (if possible also links with those pages), than NO user that reads mails and opens web pages on apache web server could in any way get infected. 
:-k

---

### Post by chrisfay on 2007-01-05
[http://www.vanja.com/tools/sophie](http://www.vanja.com/tools/sophie)
[http://www.clamav.net](http://www.clamav.net)
[http://www.openantivirus.org](http://www.openantivirus.org)
[http://www.vanja.com/tools/trophie](http://www.vanja.com/tools/trophie)
[http://www.grisoft.com](http://www.grisoft.com)
[http://www.f-prot.com](http://www.f-prot.com)
[http://www.kaspersky.com](http://www.kaspersky.com)
[http://www.centralcommand.com](http://www.centralcommand.com)
[http://www.hbedv.com](http://www.hbedv.com)
[http://www.commandsoftware.com](http://www.commandsoftware.com)
[http://www.symantec.com](http://www.symantec.com)
[http://www.f-secure.com/products/anti-virus](http://www.f-secure.com/products/anti-virus)
[http://www.avast.com](http://www.avast.com)
[http://www.nod32.com](http://www.nod32.com)
[http://www.pandasoftware.com](http://www.pandasoftware.com)
[http://www.nai.com](http://www.nai.com)
[http://www.virusbuster.hu/en/](http://www.virusbuster.hu/en/)
[http://www.cyber.com/](http://www.cyber.com/)
[http://www.ikarus-software.com/](http://www.ikarus-software.com/)
[http://www.bitdefender.com/](http://www.bitdefender.com/)
[http://www.trendmicro.com](http://www.trendmicro.com)
[http://www.sald.com](http://www.sald.com)

some may be a bit old....

---

### Post by wmblowers on 2007-02-07
Total newbie here, so please be patient... ):P 

(Ultimate Ubuntu)

I too ran Aegis which turned up the virus as posted above.  I had two instances; one in a .wine sub dir and one in a Picasa sub dir.  I also had another instance of vp31vfw.dll which was not reported as infected.

Since I'm not currently using Wine I simply removed and purged it; did the same with Picasa as well.  It's ironic that even on a Linux box the viruses follow Windows wherever it goes.  I reran the scan and no further problems reported.

Some have said this could be a 'false alarm'; whether it is or not, I don't want the thing on my machine and since I'm not using Picasa and Wine anyway it's painless; I just trashed them.

Thanks...

WLB  :)

---

### Post by suntin on 2007-03-15
> **ubuntu_demon said:**
> [http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

You don't need a virusscanner unless you want to protect windowsmachines in your network.


You said "Linux doesn't need anti virus" our survey says "uh uh"

While there aren't many viruses for Linux right now and while Linux inherently makes virus writing harder they do happen, they will grow in number as the Linux user base grows, (sadly) particularly on Ubuntu which is rapidly growing in popularity. 

...And statments like "linux is cool, you'll never see a virus again" will eventually make you look stoopid and will make people question the value of a great OS simply because they didn't prepare.

it would be like saying I don't know anyone that's been hit by a car so I don't need to look.

---

### Post by Stingray8989 on 2007-06-01
The dll file must be a false positive. I copied it to a usb drive, rebooted except to windows and scanned it with mcafee. It didn't find any problem

---

### Post by misfitpierce on 2007-06-01
The picasa is a false pos in Aegis and Aegis hasnt been updated in ages! Try Bitdefender for linux protection... Now its run through console and requires manual update by downloading files from net and placing in /opt/bdc/plugins/ but is very simple to use and do. 

 As for viruses growing on linux... It will never be a problem as it is on windows as we have the root function to install anything so it is much safer and built much differently. We should be fine for years to come.

---

### Post by Dragon-64 on 2007-11-24
> **suntin said:**
> You said "Linux doesn't need anti virus" our survey says "uh uh"

While there aren't many viruses for Linux right now and while Linux inherently makes virus writing harder they do happen, they will grow in number as the Linux user base grows, (sadly) particularly on Ubuntu which is rapidly growing in popularity. 

...And statments like "linux is cool, you'll never see a virus again" will eventually make you look stoopid and will make people question the value of a great OS simply because they didn't prepare.

it would be like saying I don't know anyone that's been hit by a car so I don't need to look.

[COLOR=Black] Do you know anything about Linux? As the article in the posted link mentions, and any search on Google will back-up, virus infections on Linux machines is almost an oxymoron and definitely a contradiction in terms!!
Of course anything can be done to some extent, but if you operate a Linux system properly, the only hazard is to the user not the system!!
Please don't try to connect Linux with the failed world of Microsoft and it's viruses!!
And nothing makes you look[/COLOR] _**[COLOR=Red]stupid[/COLOR]**_, [COLOR=Black]worse than not being able to spell such simple and common words, as stupid!! I hope you are not a Ubuntu user!! But if you are an Ubuntu user I hope you are still in school!! And if your not in school at least go take a refresher course in English, and bone up on your spelling and grammar usage!! It would make us all look better!![/COLOR]

---

### Post by HermanAB on 2007-11-24
Here is a Linux Virus scanner for you:

!# /bin/bash
echo Linux virus scanner
sleep(1)
echo Scanning now...
sleep(10)
echo Still scanning...
sleep(10)
echo Almost done...
sleep(5)
echo Drum roll...
sleep(3)
echo No viruses found!!!
sleep(1)
echo Done

---

### Post by koenn on 2007-11-24
patch for HermanAB virus scanner

replace first line with
#! /bin/bash

---

### Post by HermanAB on 2007-11-24
Nice catch! - lsip fo teh fingre...

---

### Post by WIGGMPk on 2007-11-25
The WHOLE concept of "ANTI-VIRUS" is an oxymoron..

Anti Virus software can NOT protect you unless the Virus is ALREADY known to them, which would include most of the rest of the world if its KNOWN to the software.

That being said, READ!!!!!!!!!!!!!!!!!!!!!

This is an open source operating system with literally THOUSANDS of eye's watching the development and code. If a virus/spyware/malware or anything else current/former Windows user's have become a custom to in every day computing, it would be tossed immediatly.

There is a TREMEDOUS difference in the way Microsoft model's their OS to the way Linux is designed by default. Its pretty secure out of the box.

Like the other user's have said, YOU ONLY NEED ANTIVIRUS SOFTWARE IF YOUR PROTECTION WINDOWS BASED COMPUTERS IN YOUR NETWORK OR SERVING FILES TO AND FROM WINDOWS.


For instance, I serve a Samba File Share with my neighbor (Windows XP Pro) so I use ClamAV to protect files he's sending/recieving.

---

### Post by sidncoke on 2007-11-25
Linux being "infection proof" is new information for me "2 days linux newbie" but obviously and eventually any linux box will have some form of data exchange with another non Linux OS. The main questions we should ask ourselves are:

1- If we can't be infected should we be careless, irresponsible, selfish and bad image setting linux users by infecting others? Why not just install an antivirus "ITS FREE" to slow down the spread?
2- If the open source community put their minds and efforts to it, they could come up with the most advanced and updated antivirus software in the market. Why don't they?
3- I agree with one of the previous posts and Murphy's Law: If it could happen It would happen. There is no perfect design and linux certainly isn't gonna be the exception. So what happens when a flaw is found in linux? and a virus hits the linux community and we're not prepared?

I think I'll take my chances with the "free" antivirus and keep suggesting to developers to work on better antiviruses. Better safe than sorry.

---

### Post by koenn on 2007-11-25
> **sidncoke said:**
> 
1- If we can't be infected should we be careless, irresponsible, selfish and bad image setting linux users by infecting others? Why not just install an antivirus "ITS FREE" to slow down the spread?

For viruses to spread, they need to run, need to be executed. Windows viruses don't run on Linux. At best, infected files can be passed on (eg a Linux mail server delivering mail to Windows clients, or a linux file server serving files to Winfows clients). Only in those circumstances, running anti-virus software on a Linux system makes sense. 

> 2- If the open source community put their minds and efforts to it, they could come up with the most advanced and updated antivirus software in the market. Why don't they?
Because there's so little need for it (see 1.) and developers prefer solving real problems. 

> 3- I agree with one of the previous posts and Murphy's Law: If it could happen It would happen. There is no perfect design and linux certainly isn't gonna be the exception. So what happens when a flaw is found in linux? and a virus hits the linux community and we're not prepared?
It is technically possible to create a virus or a worm that runs on Linux. It would have to be completely different from the current Windows viruses, because of the differences in design and implementation between Windows and Linux. So how are you going to design "anti-virus for Linux' if you don't even know what a linux virus is going to look like ?

---

### Post by WIGGMPk on 2007-11-25
> **koenn said:**
> ...It is technically possible to create a virus or a worm that runs on Linux.

Yes, totally forgot to mention that..

Another thing, when the virus runs on a Linux system, it would have to be run as ROOT to do catastrophic damage to the system. Because normal user's are restricted to their /home directory's. Typically normal user's (who might be careless enough to run a Linux based virus) would NOT have enough access/permissions to infect any further.

---

### Post by aysiu on 2007-11-25
> **sidncoke said:**
> 
2- If the open source community put their minds and efforts to it, they could come up with the most advanced and updated antivirus software in the market. Why don't they? I think they already have, but it's for finding Windows viruses, not the virtually non-existent Linux ones. > 3- I agree with one of the previous posts and Murphy's Law: If it could happen It would happen. There is no perfect design and linux certainly isn't gonna be the exception. So what happens when a flaw is found in linux? and a virus hits the linux community and we're not prepared? Well, anti-virus doesn't anticipate new viruses. It deals with them after the fact.

Virus and anti-virus are in a constant arms race. When a new exploit comes out, I promise you I can install anti-virus faster than the anti-virus update maintainers can create a new definition update.

Having anti-virus installed doesn't protect you against newly created viruses, only old ones, and anti-virus programs are for protecting against Windows viruses, anyway.

The most worrisome potential malware in the Linux community involves social engineering, something which no anti-virus program can protect you from.

---

### Post by Chelidon on 2007-11-27
What's a good way of scanning my Windows partition from my Kubuntu? I had my Windows (Vista, urgh, you can see why I'm using Linux) open for not 30 minutes before I got a virus, and the only way I knew was that it loaded itself onto my external drive and I could hear it spin up as it did! I was thrilled when I could load Kubuntu and simply delete it from my external hard drive, but the bugger is still in my main drive!

---

### Post by MeduZa on 2008-02-25
> **HermanAB said:**
> Here is a Linux Virus scanner for you:

!# /bin/bash
echo Linux virus scanner
sleep(1)
echo Scanning now...
sleep(10)
echo Still scanning...
sleep(10)
echo Almost done...
sleep(5)
echo Drum roll...
sleep(3)
echo No viruses found!!!
sleep(1)
echo Done

it works perfect for my linux, ok now I need to scan a friend's windows HD inside my carrydisk on /media/disk and I know that is really infected!!

Normaly we need an antivirus to scan windows disks!!

---

### Post by roaldz on 2008-02-25
I suggest that everybody who´s interested in this topic reads this: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
Especially people who claim there might be a chance they get a (windows) virus on their Ubuntu/linux installation.
As you can see, that list is remarkably short, compared to the list of windows virusus it´s nothing.
Once more: You will not get a virus in Linux!

Roald

---

### Post by fatbuttlarry on 2008-02-27
Sorry to bump and old thread, but I think there's two main discussions  here, and I'd like to separate them.

1.  Windows Virus (on Linux)
2.  Linux Virus


**Windows Viruses:**
Linux and Unix can and have contributed to the spread of viruses.  An Email server is one good example, but iPods are another.  See here: [[link]("http://www.apple.com/support/windowsvirus/")] [[link]("http://www.kaspersky.com/news?id=207575511")]. A third is Wine.

With Macs going to an Intel platform, we'll be seeing Wine (or Darwine) in more places, even running on the 64-bit architectures, allowing the execution of some Windows viruses.  It would not be a surprise if virus coders begin compatibility testing against Wine for more exposure.

Worms should not be as big of a threat.  Many Windows worms attack vulnerabilities in Windows services.  These services are often redundant in Wine, so they're used natively.  

And as the above articles accurately illustrat, most Linux programs (Wine is no exception) don't directly impact the Linux system, so removal is trivial.

**Linux Viruses:**
A Linux binary virus not only is possible, but is a clear threat.  Its scale and applicability are its strongest safeguards today. Gaining root access is possible, and probable with the growing popularity of Linux, especially considering the recent popularity with Ubuntu. [[link]("http://it.slashdot.org/article.pl?sid=08/02/10/2011257&from=rss")]

Desktop systems generally run kernels that this article describes.  They generally run similar, if not identical architecture.  Threats like this are the future of what we can expect in Linux.

Obtaining and spreading of the virus will be the most unlikely part in my opinion.  Linux is so diverse, there is no concrete standard on how people email, instant message, or even surf the internet.  There's no built-in equivalent of Internet Explorer, Outlook Express, or AIM/MSN/Yahoo thats used on a global scale.  

Firefox, Evolution, and Pidgin are the closest to what we can consider "attackable due to popularity".

Firefox:
My site statistics show a good portion of Linux users (about 15%) use Mozilla, Konqueror, Opera, Links, Lynx, and versions of these are so different across the board, coding exploits would be very complicated and incompatible.

Evolution:
With the introduction of Gmail, I find fewer and fewer Linux users using email clients.  In fact, I only know 1 person that still uses a native Linux email client, and it's not Evolution or Thunderbird.

Pidgin:
Pidgin is a great candidate for instant messenger exploits.  The biggest obstacle for the attacker would be targeting the most popular protocols, and the most popular current versions.  Of course, this implies they can find a quick way to get the binary on your system, and make it executable.

Detection:

Current antivirus software searches for signatures in binary code.  It also possible to use a MD5 hash, assuming the file size has stayed identical over time.  Both of these scenarios work well for pre-compiled viruses.  In the event, a virus is written in a scripting language, which then creates the binary, pre-detection is very difficult, as it will need to examine code within the script, and intelligently decide if it will try to perform the exploit.

These detection methods may prove more false positives, which is why antivirus should only come second to mandatory security patches.

So in summary, Linux viruses are possible in both native Linux and Windows formats.  
[list][*]Windows formats are more likely to run on your system, but less likely to devastate it.  It is unlikely a Windows virus will attack your computer through security holes, given Windows is not completely installed.  
[*]Linux formats are less likely to make it to your computer at all, due to diversity in delivery, but can pose a threat.  Antivirus software cannot currently protect you from these threats, and are unlikely to protect you from these threats in the near future, so security updates are our only safeguard.
[/list]

-Tres

---

### Post by akiratheoni on 2008-02-27
> **fatbuttlarry said:**
> **Linux Viruses:**
A Linux binary virus not only is possible, but is a clear threat.  Its scale and applicability are its strongest safeguards today. Gaining root access is possible, and probable with the growing popularity of Linux, especially considering the recent popularity with Ubuntu. [[link]("http://it.slashdot.org/article.pl?sid=08/02/10/2011257&from=rss")]

Desktop systems generally run kernels that this article describes.  They generally run similar, if not identical architecture.  Threats like this are the future of what we can expect in Linux.


I remember reading about the day the exploit was discovered. Yes, it works. I got root access without my password. But the power of open source came to rescue me -- if I recall correctly, less than fifteen hours later, the Ubuntu repositories already had an update to the kernel. Keep in mind that I said the Ubuntu repositories, so that means that the update had been available before that because I think EVERYTHING is tested to work before it's added to the Ubuntu repositories. So if everything is kept up-to-date (which if you're a normal user, there's no reason not to upgrade), then issues like that should not be a problem. Unlike Microsoft, we don't need a 'patch tuesday'.

---

### Post by Tatty on 2008-02-28
> **akiratheoni said:**
> if I recall correctly, less than fifteen hours later, the Ubuntu repositories already had an update to the kernel. Keep in mind that I said the Ubuntu repositories, so that means that the update had been available before that because I think EVERYTHING is tested to work before it's added to the Ubuntu repositories.

Yep, I recall the ubuntuforums thread about that exploit - there was a post on here just a few hours later explaining how to do a temporary fix to tie you over until the new kernels were pushed out.

And that fix was lifted from another linux site elsewhere, so the fix was probably made within a couple of hours of the problem surfacing.



> **fatbuttlarry said:**
> [list][*]Windows formats are more likely to run on your system, but less likely to devastate it.  It is unlikely a Windows virus will attack your computer through security holes, given Windows is not completely installed.  


If you are refering to a linux virus running under wine then windows is not installed at all.  Wine is not "bits of windows", Wine is Wine - completely independantly coded from windows.

---

### Post by jcwmoore on 2008-03-10
with linux you really don't need antivirus... i have been over a year with out it and no problem...

[http://www.linux.com/articles/60208]("http://www.linux.com/articles/60208")

---

### Post by OrangeCrate on 2008-03-10
>  1. If you run Linux and only Linux, you do not need antivirus software. In its efforts to make Windows easier to use, Microsoft simplified the process of running executables under its operating system many years ago. Not only can a user launch a program by clicking an e-mail attachment, but it's possible for an executable to launch automatically just by hitting the preview pane of some email packages, including older versions of Outlook and Outlook Express. Scot's Newsletter Forums member Nathan Williams has provided an excellent FAQ for the All Things Linux forum explaining why Linux when used alone does not need antivirus protection.

Under Linux the steps for launching an executable from an e-mail are separate, discrete steps. A user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. And to be truly damaging, the latter two would have to be done as root — not something informed users would allow. (For more information see Ch- Ch- Changing File Permissions.)

2. If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them — the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

[B]3. If you dual boot, however, you better get a good antivirus program for Windows. Microsoft's operating system and its bundled applications, Outlook and Internet Explorer, offer users powerful functionality in their attempts to be easy to use and easy to update. As a result, it's all too easy for virus writers to exploit the same functionality in a malicious way. Don't leave them an opening. Install an antivirus program and keep it updated.

4. The only time you'll need a Linux antivirus program is if you're running a mail server. And that's just good social behavior. It's not to protect your Linux server or client computer so much as to make sure you don't pass a virus on to a Windows system.[/B]

Think about it this way: If you have two warehouses, and you use the first one to store cheese, are you going to place mouse-traps in the second one where you only store stainless steel? I mean, be reasonable, mice do not eat stainless steel! So don't let antivirus vendors make you unnecessarily paranoid.

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by Oldsoldier2003 on 2008-03-10
> **OrangeCrate said:**
> [http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

Why does everyone insist on telling people they don't need antivirus? the bottom line is if you are dual booting or supporting  windows users, its a good idea to have antivirus because you can run it from within linux, avoiding further contamination of the windows system.

yes we know linux is currently safe from virii, but again a dual boot system or a samba server are potential virus distribution points.

---

### Post by OrangeCrate on 2008-03-10
^, Just not that paranoid I guess.

---

### Post by Oldsoldier2003 on 2008-03-10
> **OrangeCrate said:**
> ^, Just not that paranoid I guess.

LOL! it isnt paranoia. If you are running a samba server or a dual boot machine in a production setting its called "keeping your job"

---

### Post by Kevbert on 2008-03-10
If you run a DOS or Windows emulator under Linux there's a chance you'll get a virus (probably written for DOS/Win).  I had after running DosBox and downloading some old games.  Clamtk (antivirus) solved the problem.  How to install can be found here:
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html")

---

### Post by OrangeCrate on 2008-03-10
^ ^,

I understand your point, but personally I'm of the school that Windows users need to take care of themselves. It's simply not my problem. However, as you stated, if your job depends upon protecting them, have at it...

I've gone back and highlighted my philosophy in my earlier post, and I've done the same below in the Security Sticky posted by bodhi.zazen from this forum:

> The fact of the matter is: viruses/worms take advantage of flaws or holes in the code. At this time of this writing, there are no significant Linux viruses "in the wild". Linux boxes are no less targets than any other OS, many of the large (ie valuable) Internet sites run on *nix so there is no lack of motivation to crack into *nix.

Do not believe the suggestion that the Linux community is complacent or "behind the times" in terms of viruses, or any other security issue. Linux developers have not "ignored" viruses, rather the OS is built to be highly resistant to them and since the code is "Open" there are literally thousands of eyes watching ...

This is an example of what it would take to install malware on an Ubuntu box :

Install evilmalware

(Don't worry, that link will NOT install anything )

For the most part, Linux anti-virus programs scan for Windows viruses which do not run on Linux, even on wine ([http://os.newsforge.com/article.pl?s...30222&from=rss](http://os.newsforge.com/article.pl?s...30222&from=rss)). Anti-virus programs are "reactive" in that they can only protect you from known viruses. They can only protect you against the next Linux virus after it is developed, not before. Furthermore the "fix" will be to close any hole(s) in the code, these fixes will be available through security updates (which are more frequent in Linux then your previous OS if you are coming from Windows).

[B]My advice is to skip the anti-virus if you run Ubuntu. Why ?

   1. They scan primarily for Windows viruses.
   2. There is a high rate of false positives.
   3. Isolation/inoculation is poor.
   4. And currently there are no known active Linux viruses (so there is essentially nothing to detect).

Running antivirus can make some sense if you are intending to "protect" windows users, however, IMO, for a variety of reasons, it is best if Windows users learn to protect themselves. In fact the most common usecase for a Linux antivirus program is to run a Windows fileserver or serve mail to Windows clients.[/B]

Note: There have been many documented cases in Windows and Linux that a buffer overflow in an antivirus product has been an attack vector!

If you would like to run an antivirus program on Ubuntu you have several choices :

    * [http://doc.gwos.org/index.php/How_to_ClamAV](http://doc.gwos.org/index.php/How_to_ClamAV)
    * [http://www.avast.com/eng/avast-for-l...rkstation.html](http://www.avast.com/eng/avast-for-l...rkstation.html)
    * [http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)
    * [http://www.centralcommand.com/linux_server.html](http://www.centralcommand.com/linux_server.html)
    * [http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)


[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)

Edit:

When I had Windows, or when I dual booted, I protected the hell out of Windows, or it's partition, with a firewall, an antivirus program, and the typical witches brew of spyware scanners, etc. But, I've always run naked in Linux, for reasons I posted, and backed up with quotes from reliable Linux sources,

I'm not a good "mark" for all of the virus paranoia posted around here. IMO, the better we can educate newcomers to the differences between Linux and Windows, the better off we/they are.

---

### Post by WarMonkey on 2008-03-31
I love SpySheriff! I can't believe they only charge me 30 bucks a year!

Thanks SpySheriff.

(Just kidding)

---

### Post by Linux_monkey on 2008-10-29
I would have to dis agree with anyone who says you dont need antivirus on Linux. many here will agree that linux is more than likely the platform most viruses are coded right? So the maker is obviously smart enough to start manipulating Linux code. Its not unheard of people. just accept that installing some sort of protection is needed not a luxury. in fact i am certain my box is more than likely infected now.

---

### Post by aysiu on 2008-10-29
> **Linux_monkey said:**
> I would have to dis agree with anyone who says you dont need antivirus on Linux. many here will agree that linux is more than likely the platform most viruses are coded right? So the maker is obviously smart enough to start manipulating Linux code. Its not unheard of people. just accept that installing some sort of protection is needed not a luxury. in fact i am certain my box is more than likely infected now.
You can't just manipulate Linux code. Or if you can, you have to find a way to redistribute the manipulated code. Just because you have access to view the code doesn't mean you can arbitrarily change code on other people's computers. You have to find an exploit or vulnerability **or** trick the user into allowing you to compromise the system.

If there's an exploit or vulnerability, I don't see how having antivirus installed will help you. And if you are being tricked into allowing a malicious program to run on your system, I don't see how having antivirus installed will help you.

Frankly, antivirus is useless even on Windows. Set up some proper user permissions and educate yourself on social engineering instead. Far more effective. Better to have real security than feel-good security.

---

### Post by aysiu on 2008-10-29
> **Linux_monkey said:**
> I would have to dis agree with anyone who says you dont need antivirus on Linux. many here will agree that linux is more than likely the platform most viruses are coded right? So the maker is obviously smart enough to start manipulating Linux code. Its not unheard of people. just accept that installing some sort of protection is needed not a luxury. in fact i am certain my box is more than likely infected now.
You can't just manipulate Linux code. Or if you can, you have to find a way to redistribute the manipulated code. Just because you have access to view the code doesn't mean you can arbitrarily change code on other people's computers. You have to find an exploit or vulnerability **or** trick the user into allowing you to compromise the system.

If there's an exploit or vulnerability, I don't see how having antivirus installed will help you. And if you are being tricked into allowing a malicious program to run on your system, I don't see how having antivirus installed will help you.

Frankly, antivirus is useless even on Windows. Set up some proper user permissions and educate yourself on social engineering instead. Far more effective. Better to have real security than feel-good security.

---

### Post by Perfect Storm on 2008-10-29
> **Linux_monkey said:**
> I would have to dis agree with anyone who says you dont need antivirus on Linux. many here will agree that linux is more than likely the platform most viruses are coded right? So the maker is obviously smart enough to start manipulating Linux code. Its not unheard of people. just accept that installing some sort of protection is needed not a luxury. in fact i am certain my box is more than likely infected now.

Please don't start FUD without proof. In fact if people keep to the repo. The virus infection is close to zero. To have software via the repo eliminates a big risk where in windows you have to hunt for stuff ib more or less obscured places without it haven't been tested or checked.
Also most of the software you get on linux is Open Source which give people (with knowledge ofcause) to check the codes.
Thirdly the structure of Linux makes it hard to make an effective linux virus which have been proven the few times (if you follow the Linux news time to time).

---

### Post by OrangeCrate on 2008-10-29
> **Linux_monkey said:**
> I would have to dis agree with anyone who says you dont need antivirus on Linux. many here will agree that linux is more than likely the platform most viruses are coded right? So the maker is obviously smart enough to start manipulating Linux code. Its not unheard of people. just accept that installing some sort of protection is needed not a luxury. in fact i am certain my box is more than likely infected now.

First post, on a seven month old thread, eh?

Hmm...

Well, if it quacks like a troll...

---

### Post by Linux_monkey on 2008-10-29
i dont like talkin much i like to jump in on the good conversations from time to time. 
P.S. ive spoken to several linux gurus who agree with me.(Plz do not reply to this.)

---

### Post by aysiu on 2008-10-29
You mean you like signing up for an account and having your first post on the forums present a controversial position?

Interesting behavior.

And if you don't want people to reply to you, don't write anything. This is a forum with discussion threads. The whole point is to discuss. If you want to write and not have people respond, start a blog and turn off the comments.

P.S. I've spoken to more than several Linux gurus who agree with me.

---

### Post by Linux_monkey on 2008-10-29
ok look ive only recently signed up because i was tired of just reading posts.i didnt expect you guys to jump right on me for my own opinion and i apologize if ive stepped on some toes.maybe i should go back to just reading

---

### Post by aysiu on 2008-10-29
> **Linux_monkey said:**
> ok look ive only recently signed up because i was tired of just reading posts.i didnt expect you guys to jump right on me for my own opinion and i apologize if ive stepped on some toes.maybe i should go back to just reading
You may want to start by reading this:
[Does Ubuntu need antivirus?](http://www.psychocats.net/ubuntucat/does-ubuntu-need-antivirus/)

---

### Post by Perfect Storm on 2008-10-29
Well people jump because you come with some claims without backening it up with something.

I could say the earth is flat and tell you that's the truth without explaination or prove. It would be the same.

---

### Post by OrangeCrate on 2008-10-29
> **Linux_monkey said:**
> i dont like talkin much i like to jump in on the good conversations from time to time. 
P.S. ive spoken to **several linux gurus** who agree with me.(Plz do not reply to this.)

Who, pray tell, are these "gurus". Please supply names, and sources of their published work please?

---

### Post by Linux_monkey on 2008-10-29
ok once again i apologize and i guess i was a bit quick to post and my future posts will be more thought out.(kinda like the one i just posted about my box crashing every day.

---

### Post by aysiu on 2008-10-29
It's okay to post something a little out there, Linux_monkey. Just realize that people are going to respond. It's the very nature of forums to have discussions and disagreements. Post your opinion, but don't insist others must not respond if they disagree. Be open to the fact that you might be wrong and also properly defend yourself if you have credible sources or logic to back you up.

---

### Post by OrangeCrate on 2008-10-29
> **Linux_monkey said:**
> ok once again i apologize and i guess i was a bit quick to post and my future posts will be more thought out.(kinda like the one i just posted about my box crashing every day.

Personally, I lurked, and read here for almost a year after installing Ubuntu 5.10 (Breezy), prior to needing to ask a question, and finally joining the forums. There's nothing wrong with that.

What was suspect, with your first post, was that it was a little like dousing a seven month old thread with gasoline, and tossing a match.

Just start over, and welcome to the forums!

:)

Edit:

The only reason I got involved here, is that I had a subscription to this thread, and a notice popped up on a response. Being seven months old, I was a bit surprised.

If you read the entire thread, you noticed that I owned a bit of it, so I felt qualified to add comments, and offer challenges.

---

### Post by Linux_monkey on 2008-10-29
ok im stating over ..........


NOW:lolflag:

---

### Post by OrangeCrate on 2008-10-29
^,

Good, and here's your first "thanks". (You're no longer a "virgin" on the forums.) Read a lot, and contribute to the community when you can.

See you down the road...

:)

---

### Post by 3startuna on 2009-03-27
Very sorry for bumping an old thread.I was a XP user that got a nasty trojan that destroyed my windows directory. I was running Mcafee antivirus on the system and it happened anyway. 

It happened very quickly too visited a bad site, (no it wasnt porn :) ) 
And in a few seconds, I was watching my computer shut down programs and restart it self with "NTLDR missing please reboot" the only thing left on my computer.

I switched to Ubuntu and now I'm happier than ever before! this OS makes windows look like a steaming pile. 

Anyway re virus, where there is a will there is a way. Theoretically it can be done. I like how secure linux is but there are ways around every system. 

For example if a virus creating jerk, made a package that contained the virus script. Then the user downloaded and installed the bad package, then you would get infected. Or say you downloaded an infected torrent or archive file.

Other than that I could see some one designing one that loads with a page then sudo $User itself to change the permissions for a target drive then wreak havoc. 

The login could be bypassed by using a loop, and different alpha numeric sequences. 

Basically its possible but it would take a very long time, and any linux user worth their grain of salt would pick up on what's happening. (hopefully)

Also, may just be my opinion but I think most viruses are written for making money. Selling antivirus software is a very lucrative business, Just like human viruses, computer viruses need population density to spread. Currently there isnt a large enough community of people running linux for it to be profitable.

My experience its better to just be smart about how you setup your computer, and practice safe hex. i.e. only download supported packages, and only go to trusted safe sites.

Also check out this site: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

I would hope those guys know what there talking about :)

---

### Post by sabith on 2009-03-27
use avg at avg.com

---

### Post by Linux_monkey on 2009-03-28
you make a good point there,i think if someone really wanted to, they could make a virus for Linux that makes a penguin dance in front of whatever your trying to do.
[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif) but seriously it can be done  so i just stay cautious even on ubuntu.

---

### Post by Bios Element on 2009-03-28
> **3startuna said:**
> Very sorry for bumping an old thread.I was a XP user that got a nasty trojan that destroyed my windows directory. I was running Mcafee antivirus on the system and it happened anyway. 

It happened very quickly too visited a bad site, (no it wasnt porn :) ) 
And in a few seconds, I was watching my computer shut down programs and restart it self with "NTLDR missing please reboot" the only thing left on my computer.

I switched to Ubuntu and now I'm happier than ever before! this OS makes windows look like a steaming pile. 

Anyway re virus, where there is a will there is a way. Theoretically it can be done. I like how secure linux is but there are ways around every system. 

Not unless your an idiot and give them access.

> **3startuna said:**
> For example if a virus creating jerk, made a package that contained the virus script. Then the user downloaded and installed the bad package, then you would get infected. Or say you downloaded an infected torrent or archive file.

No, a package wouldn't auto-install. It would need sudo. Duh. Seriously, this isn't a bug or a flaw. This is human operators being idiots.

> **3startuna said:**
> Other than that I could see some one designing one that loads with a page then sudo $User itself to change the permissions for a target drive then wreak havoc. 

No, Impossible.

> **3startuna said:**
> The login could be bypassed by using a loop, and different alpha numeric sequences. 

No, Not without sudo access.

> **3startuna said:**
> Basically its possible but it would take a very long time, and any linux user worth their grain of salt would pick up on what's happening. (hopefully)
Long time? No, if someone's stupid enough they can fry their system without a virus.

> **3startuna said:**
> Also, may just be my opinion but I think most viruses are written for making money. Selling antivirus software is a very lucrative business, Just like human viruses, computer viruses need population density to spread. Currently there isnt a large enough community of people running linux for it to be profitable.
Excluding 75~% of servers.

> **3startuna said:**
> My experience its better to just be smart about how you setup your computer, and practice safe hex. i.e. only download supported packages, and only go to trusted safe sites.
Downloading them isn't the problem, installing them is. And I've already played the "Let's go to 1,000 spyware packed sites and see if Ubuntu dies!". Doesn't work like that without the malware called Internet Explorer.

---

### Post by Chemical Imbalance on 2009-03-28
Just to add, these scanners don't have any linux virus signatures included!

even if you were the first to get a "in the wild" virus for linux, the scanner wouldn't detect it!

Maybe in the future this could change, but for now they only detect Windows malware.

I *do* however recommend safe practices, running a rootkit checker (chkrootkit), and using only software from the repos if you can.  A hardware firewall is always nice.  Also, Bastille is a great hardening program along with SElinux or AppArmor.

However, a thing to note is the usage of WINE.  WINE is susceptible to viruses, period.  I do recommend scanning your .wine directory with a good scanner such as Avast! antivirus.

---

### Post by Linux_monkey on 2009-03-28
> **Bios Element said:**
> Not unless your an idiot and give them access.


No, a package wouldn't auto-install. It would need sudo. Duh. Seriously, this isn't a bug or a flaw. This is human operators being idiots.



No, Impossible.



No, Not without sudo access.


Long time? No, if someone's stupid enough they can fry their system without a virus.


Excluding 75~% of servers.


Downloading them isn't the problem, installing them is. And I've already played the "Let's go to 1,000 spyware packed sites and see if Ubuntu dies!". Doesn't work like that without the malware called Internet Explorer.

i disagree, if the virus was written into a package you download and willingly install. the virus would be loaded in with whatever the program was. nothing is stopping it from running a script to get sudo. lets say for sake of argument the virus uses said program for access to root and expands from there.. you cant say it cant be done.

---

### Post by aysiu on 2009-03-28
> **Linux_monkey said:**
> **i disagree**, if the virus was written into a package **you** download and **willingly install**. the virus would be loaded in with whatever the program was. nothing is stopping it from running a script to get sudo. lets say for sake of argument the virus uses said program for access to root and expands from there.. you cant say it cant be done. How is that disagreeing?

Bios Element's whole point is that if the user is stupid and willingly installs malware, then the malware can do anything: > **Bios Element said:**
> **Not unless your an idiot and give them access.**

No, a package wouldn't auto-install. It would need sudo. Duh. Seriously, this isn't a bug or a flaw. This is **human operators being idiots.**

Long time? No, **if someone's stupid enough** they can fry their system without a virus.

Downloading them isn't the **problem, installing them** is. Social engineering will always be a threat, because it doesn't take advantage of software flaws. It takes advantage of human user flaws.

We can try to educate users to vet the trustworthiness of what they install, but ultimately it's up to them to uphold that end of security.

That doesn't mean there are virus threats for Linux. And that doesn't mean having antivirus installed would protect you from them if they suddenly appeared.

---

### Post by Linux_monkey on 2009-03-28
no my point was that you dont willingly install this virus and that its hidden in a program u wanted.

---

### Post by aysiu on 2009-03-28
> **Linux_monkey said:**
> no my point was that you dont willingly install this virus and that its hidden in a program u wanted.
I agree fully with that point, and so appears Bios Element to as well.

Here are the points I hope we all fully agree on: [list][*]The biggest malware threats usually rely on social engineering; that is, they trick the user into installing what appears to be desireable software but actually is malware or contains malware. Such threats can appear on any operating system, though at the moment Linux has few if none of these in existence.[*]Self-replicating viruses that take advantage of software security holes are not a threat in Linux currently.[*]If a self-replicating virus were to suddenly appear and take advantage of a previously unknown flaw, then having antivirus installed at that time would not protect you, as the antivirus would have no way of knowing about that threat in advance.[/list]

---

### Post by cardinals_fan on 2009-03-28
> **Bios Element said:**
> Not unless your an idiot and give them access.


No, a package wouldn't auto-install. It would need sudo. Duh. Seriously, this isn't a bug or a flaw. This is human operators being idiots.
This is true with any OS.
> **Bios Element said:**
> 
Excluding 75~% of servers.

...which are most often administered by relatively competent users.

---

### Post by 3startuna on 2009-03-28
> **Linux_monkey said:**
> i disagree, if the virus was written into a package you download and willingly install. the virus would be loaded in with whatever the program was. nothing is stopping it from running a script to get sudo. lets say for sake of argument the virus uses said program for access to root and expands from there.. you cant say it cant be done.

Thats what I was thinking too. I dont believe in imossibility especially when it comes to computers. At the end of the day I believe prevention is better than cure. Practice safe hex. Only download and install supported packages.

> **aysiu said:**
> I agree fully with that point, and so appears Bios Element to as well.

Here are the points I hope we all fully agree on: [list][*]The biggest malware threats usually rely on social engineering; that is, they trick the user into installing what appears to be desireable software but actually is malware or contains malware. Such threats can appear on any operating system, though at the moment Linux has few if none of these in existence.[*]Self-replicating viruses that take advantage of software security holes are not a threat in Linux currently.[*]If a self-replicating virus were to suddenly appear and take advantage of a previously unknown threat, then having antivirus installed at that time would not protect you, as the antivirus would have no way of knowing about that threat in advance.[/list]
Well said  I can cosign to that arguement

Especially the last line The virus that KO'd my computer with windows, my antivirus software didnt even detect LOL

---

### Post by WatchingThePain on 2009-03-28
Yeah once I copied loads of infected directories from Windows into Linux and they never did it any harm. Among them that I can recall was crypt32, Vundo,
Trojandropper.

---

### Post by Linux_monkey on 2009-03-28
i just got the most recent version of Norton for my windows machine a few months ago and I've had to teach it about two different and obvious threats. so yea new viruses cant be helped by anti virus programs automatically. i just like them as a tool i can use manually.

---

### Post by rolleander on 2009-07-13
> **WatchingThePain said:**
> Yeah once I copied loads of infected directories from Windows into Linux and they never did it any harm. Among them that I can recall was crypt32, Vundo,
Trojandropper.

That's only because the viruses would have been written to infect a Windows system. One of the neat things about Linux is that you don't have a c:\windows, c:\windows\system or just a c:\ for that matter - most virus codes are written for c:\something... if a viruse was written to infect \usr\whatever or just \ - it'd have a better chance of infecting a linux filesystem... well slightly better - however unlikely for a virus to infect, remember that nothing is unfallable

I think that so long as M$ is the #1 OS, we shouldn't worry too much though... Although I remember getting viruses on Amiga back in the day... they had silly names like Lamer Tamer virus... but Amiga wasn't widely used

---

### Post by mamamia88 on 2009-07-13
i don't bother if a virus writer wants too harm as many people as possible they will code the virus for windows

---

### Post by ankman on 2009-08-01
> **Artificial Intelligence said:**
> Yep, if you're only using linux there's no need of anti-virus programs. A firewall at least (there is no such thing as a 100% bullet proof OS)

Then mine is. ;-)

I never used a firewall on any of my desktop or server (VPS) Linuxes, and never was hacked in the last 12 years.

That you need a firewall is an urban legend such as that you need a virus scanner.

Keep your systen up to date, don't install unneccesary programs (especially services).  Then there is nothing you would need to protect.

---

### Post by hyperAura on 2009-08-01
i am not using one neither in linux or windows, but a small company i work for use nod32.. u can call me crazy but i dont the point of using an antivirus to be honest if u know what u r doing.. the last 5 years that i can remember nothing happened to me as it concerns virus attacks..

---

### Post by 3startuna on 2009-08-03
When I used to use windows I used to get viruses all the time with the antivirus programs installed. They are a pain too because they drain so much resources. 

The best antivirus is to convert to linux and forget about it.

---

### Post by aysiu on 2009-08-03
> **3startuna said:**
> When I used to use windows I used to get viruses all the time with the antivirus programs installed. They are a pain too because they drain so much resources. I fully agree that antivirus programs do not offer you security, but you *can* make Windows secure:
[http://www.psychocats.net/ubuntucat/windowssecurity](http://www.psychocats.net/ubuntucat/windowssecurity)

It's a bit more convenient in Windows 7 than in Windows XP, but you can make even Windows XP secure... just the "run as" feature isn't quite as robust.

> The best antivirus is to convert to linux and forget about it. That may be the best "antivirus," but there are other security concerns, certainly--running listening services without knowing how to lock them down properly, using weak passwords, falling victim to social engineering attacks... not to mention cross-platform browser-based flaws (usually appearing in JavaScript in Firefox or in Adobe's Flash player plugin).

It's very important to install system updates regularly, to use strong passwords, and to not install server software unless you are running (and know how to maintain) a server.

If you are super paranoid, you may also want to use NoScript in Firefox and learn how to properly configure AppArmor (which comes installed with Ubuntu by default).

"Antivirus" software will be completely useless. It doesn't mean you are complacent or think Linux is invincible. It just means you don't believe "antivirus" software will protect you (and it won't). Antivirus protects you from malware about as much as a sheepskin condom protects you from HIV.

---

