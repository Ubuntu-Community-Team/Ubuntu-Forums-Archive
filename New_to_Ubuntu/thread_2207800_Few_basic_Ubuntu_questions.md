---
title: "Few basic Ubuntu questions"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by jay36 on 2014-02-25
[COLOR=#333333]I am not a tech guy and have been using Windows as these years. Recently thought to try Ubuntu as Microsoft will stop XP support. I would be grateful if knowledgeable members here can answer few basic queries.[/COLOR]

[COLOR=#333333]1. Now on download site there are 2 versions.. 12.04 and 13.10[/COLOR]
[COLOR=#333333]Which one should I install? It says 12.04 will be supported till 2017 and 13.10 for nine months?![/COLOR]

[COLOR=#333333]2. Do I have to upgrade every time Ubuntu comes out with new versions? Are every versions very much different from one another?  Ubuntu seems to be upgrading every now and then. It would be a pain to install and learn a new OS every nine months![/COLOR]

[COLOR=#333333]3. Will MS Office 2007 run on Ubuntu?[/COLOR]

[COLOR=#333333]4. What about antivirus? Are there any free Ubuntu free antivirus?[/COLOR]

[COLOR=#333333]I did a basic googling about these queries... but either they were old/not relevant or have only confused me more.[/COLOR]

[COLOR=#333333]Thanks.[/COLOR]

---

### Post by maglin2 on 2014-02-25
Hello, my thoughts are:

1 - Judging from your comments at 2, I would suggest 12.04LTS. It is supported for longer, and is reportedly more stable ( I find it rock solid). 14.04LTS will come out in April, and will also be supported for 5 years (but you don't have to switch from 12.04 until 2017 if you don't want to - at which time you'd probably switch to 16.04LTS anyway!).

2 - No you don't have to upgrade until support stops if you don't want to.

3 - No (unless you use Wine perhaps - I've never tried) - but Libreoffice is provided and is MS Office compatible.

4 - No, not as in real-time AV. Comodo make one, but you have to install unoffical redirect driver patches to get it to run with current Ubuntu releases, and I couldn't recommend that. There are free on-demand scanners if you want (Clam, Bitdefender). The general concensus seems to be that if you use a limited user account, only install from the repositories, keep ypur system up to date, and perhaps do a few other things like enable UFW, Apparmor profile for Firefox and install Noscript FF addon you don't need to run an AV. I'm too new to this game to be able to comment on that really - I've never had a problem though.

I can't claim to be the  'knowledgeable member' you asked to respond  - I've not been using Linuxx too long myself, so you might want to hang on and see what else comes up before taking the plunge.  I've fairly recently had to go through the same questions myself though. 

 Best of luck.

PS
If you've been running XP then you may want to check out your machine specs vs ubuntu requirements before installing. 

If you're borderline/fall short then I would suggest xubuntu 12.04. Also rock solid (apart from a slight annoying bug with the file manager on first opening that you can workaround).

If xubuntu won't run on your machine then I would suggest trying PClinuxOS LXDE. That ran for me on an ancient machine - sadly now passed on.

---

### Post by ibjsb4 on 2014-02-25
Whats your computer specs (cpu, ram, video)?

---

### Post by stalkingwolf on 2014-02-25
1. Now on download site there are 2 versions.. 12.04 and 13.10
Which one should I install? It says 12.04 will be supported till 2017 and 13.10 for nine months?!

Unless you need or want bleeding edge stay with the LTR (12.04)

2. Do I have to upgrade every time Ubuntu comes out with new versions? Are every versions very much different from one another? Ubuntu seems to be upgrading every now and then. It would be a pain to install and learn a new OS every nine months!

No . If you use the LTR you will get the periodic security updates.

3. Will MS Office 2007 run on Ubuntu?

It can either in wine or crossover linux. How reliably  im not sure.  As was mentioned Libre office is included and will do all the ms office will as far as i know.

4. What about antivirus? Are there any free Ubuntu free antivirus?

I always install clam tk  its in synaptic.  Do you need it probably not but i believe its better to have it and not need it.

I did a basic googling about these queries... but either they were old/not relevant or have only confused me more.

---

### Post by grahammechanical on 2014-02-25
Ubuntu is a Linux distribution. Think of Linux distributions as projects that are under continual development and improvement. Linux, itself, is being refined all the time to keep it up to date with the latest hardware. Linux distributions also need to keep up to date with the latest hardware. Otherwise they become as obsolete as Windows 98 or XP. Is that what you want.

I advise you to wait until the end of April and install Ubuntu 14.04 LTS, then you will have a user interface that will be the very latest and you can use it for 5 years. You can set the system to only advise you of new LTS releases (every two years). In fact that is the default setting for an LTS install. But we are not forced to upgrade.

From time to time you will get security updates and during the first two years there will be 4 major upgrades called point releases - 14.04 > 14.04.1 > 14.04.2 > 14.04.3 >14.04.4. It keeps the LTS release up to date with the latest hardware modifications to the Linux kernel. The user interface will not change.

If you install Ubuntu 13.10 you will have to upgrade to Ubuntu 14.10 and then to 15.04 and then to 15.10 and on to 16.04 and there will be changes to the User Interface as Ubuntu moves past 14.10 and on to 15.04. But the changes will not be radically different from what as gone before. The basic method of using the interface has remained similar for more than three years. And will remain similar for years to come.

Regards.

---

### Post by Mark Phelps on 2014-02-25
As to your MS Office question, no, LibreOffice will not do all the stuff MS Office does.

MS Office includes Outllook, which LibreOffice does not do.  There are Linux email clients, but they don't provide the full functionality of Outlook which also includes scheduling and calendar functions.

While you can use LibreOffice to open some Word documents, it doesn't handle the .docx files well -- which is the default MS Word format file format starting with Office 2007.

Quite frankly, if you need to use MS Office daily, then you need to keep MS Windows around -- in a dual boot mode.

---

### Post by nunecas123 on 2014-02-25
1 & 2. It seems you want a stable and well supported machine. If you don't want to get the latest features, I recommend you to use 12.04 LTS(Long Term Support version), as it updates itself but nothing that will harm your system (pretty much like Windows XP doing its updates, but a lot of safer - as we're talking about Linux).

3. I recommend you to use Wine on this one - you see, Microsoft programs do not run on Linux system because the code is different - also, Linux is open-source(open for everybody to join in and reprogram or fix the issues), Office is closed-source(you can't edit the program at all, legally.). You have a lot of alternatives to Office on Linux and LibreOffice can do wonders. If you do not want to change, search out on Google for ***Wine on Linux***[I].
[/I]
4. Ubuntu doesn't need an antivirus, it's almost an hermetic system immune to viruses (there are not a lot of programmers doing that on the Linux world, as there aren't many victims). There's ClamAV to scan your hard-drive. If you have a Windows partition, it's great that you scan on Linux, as it is a lot more effective to remove these when they aren't active.

I hope I helped.

---

### Post by buzzingrobot on 2014-02-25
> **jay36 said:**
> 

[COLOR=#333333]1. Now on download site there are 2 versions.. 12.04 and 13.10[/COLOR]
[COLOR=#333333]Which one should I install? It says 12.04 will be supported till 2017 and 13.10 for nine months?![/COLOR] 

Canonical releases "Long Term Support" (LTS) versions that are supported for 5 years.  In between those, they also produce a series of releases that are supported for 9 months.  The current LTS is 12.04. The next LTS will be 14.04, scheduled for an April release.

The differences between 12.04 and 13.10 have been primarily evolutionary, not revolutionary. 

Support, in this context, means that security and bug fixes are applied to the LTS release.  It does not mean that the most current applications are guaranteed to run on 12.04.  This is the tradeoff:  The LTS is considered more stable, over time, because changes are confined to security and bug fixes.   Upgrading libraries and other core components to support the most current apps would fundamentally alter the LTS.  (Caveat: Ubuntu does release periodic kernel and graphics support updates for its LTS releases.  The most current updates are incorporated in the 12.04.04 release.)

[COLOR=#333333]>  2. Do I have to upgrade every time Ubuntu comes out with new versions? Are every versions very much different from one another?  Ubuntu seems to be upgrading every now and then. It would be a pain to install and learn a new OS every nine months![/COLOR]

When support for a release ends,  users will no longer receive security and bug fixes.  So, yes, you can continue to use such a release, but you will be potentially vulnerable to threats created/identified after its end-of-life. 

When Ubuntu debuted its current Unity interface a few years ago, the change was dramatic.  Since then, the changes between releases have considerably less dramatic and, with the exception of tweaks and new features, each has worked the same as its predecessor.

[COLOR=#333333]> 3. Will MS Office 2007 run on Ubuntu?

Windows applications will not run natively on Linux, just as they will not run natively on OS X, or vice versa. However, a Linux tool called "Wine" simulates [/COLOR]a Windows environment and allows the use of some Windows programs.   In addition, LibreOffice, which essentially mimics Office, is widely used in Linux and elsewhere. 

[COLOR=#333333]> 4. What about antivirus? Are there any free Ubuntu free antivirus?[/COLOR]

No operating system that resides on a network can ever be immune to malware and other threats.  That includes Linux. 

That said, malware attackers are typically in it for the money and, so, get the greatest return for their efforts by targetting Windows.  That greatly reduces the chances that a Linux machine will be attacked, but it does not eliminate it. 

No magic answer here. Your browsing habits will likely determine your vulnerability.  if you often visit unknown sites, follow unknown links, download files from unfamiliar locations, etc., your chances of infection increase, no matter the OS.  If you, however, spend your time on known, trusted, sites, your vulnerability decreases.

If a Linux machine is on a network with Windows machines, e.g., an office LAN, it's probably sensible to run an anti-malware program on it to try to prevent inadvertantly passing Windows-only infected email, etc., around the office.

ClamAV is one popular Linux antivirus program.  In all cases, you want to look at how fast and thoroughly any antivirus programs issues updates to respond to newly identified threats.

If the thought of needing to bump up to a new release every nine months puts you off, then certainly go with an LTS release.  If you are not in a hurry, you might consider waiting until after the next LTS, 14.04, is released. (and, perhaps a couple of weeks after release day, to allow things to settle down a bit. )

---

### Post by jay36 on 2014-02-26
I thank you all for your advice/suggestions.  I think now the things are little clear to me. 

> **jay36 said:**
> 
[COLOR=#333333]1. Now on download site there are 2 versions.. 12.04 and 13.10[/COLOR]
[COLOR=#333333]Which one should I install? It says 12.04 will be supported till 2017 and 13.10 for nine months?![/COLOR]


I will install 12.04 or wait till April for 14.04.  I hope 14.04 comes up before XP support ends.
> **jay36 said:**
> 

[COLOR=#333333]3. Will MS Office 2007 run on Ubuntu?[/COLOR]

[COLOR=#333333]I am a finance manager and do lot of financial modeling on MS Excel.  So I guess ditching MS Office [/COLOR][COLOR=#333333]and learning [/COLOR][COLOR=#000000]LibreOffice [/COLOR][COLOR=#333333]would be too much difficult to me [/COLOR][COLOR=#333333].  No has cursed Microsoft more than me when they introduced drastic changes from Office 2003 to Office 2007.  But I will research about this Wine thing and see how easy it is to install/use MS Office in Ubuntu.

In fact its because of MS Office that I have stuck with Windows all these years.
[/COLOR]> **jay36 said:**
> [COLOR=#333333]
4. What about antivirus? Are there any free Ubuntu free antivirus?[/COLOR]


I have not 100% understood about antivirus suggestions, but will research about ClamAV.  I do lot of research on net and have to download various files, so at times I land up at sites which might not be safe.  Hence I need a robust security mechanism.  

> **ibjsb4 said:**
> Whats your computer specs (cpu, ram, video)?

[TABLE="class: table-noborder sys-font-body sys-color-body, width: 100%"]
[TR="class: sys-table-cell-bgcolor1"]
[TD="class: sys-font-body-bold table-bottomborder sys-table-color-border, colspan: 2"]Acer TravelMate 4335
CPU:Intel Core 2 Duo CPU T5670 @ 1.80GHz
Video Car Model: Mobile Intel(R) 4 Series Express Chipset Family
RAM: 2GB[/TD]
[/TR]
[/TABLE]

---

### Post by ibjsb4 on 2014-02-26
> I will install 12.04 or wait till April for 14.04.  I hope 14.04 comes up before XP support ends.

I don't think you understand.

Both 12o4 and 14o4 are LTS (long term support),  You can install 12o4 now and upgrade directly to 14.04 when it comes out.

Edit:  After reading Odyssey's post.

I’m not sure how Ubuntu will run, but I have installed Xubuntu on similar spec machines and found it quite fast.

---

### Post by newb85 on 2014-02-26
LibreOffice doesn't come with an Outlook equivalent, but Evolution has all the functionality of Outlook.

---

### Post by Odyssey1942 on 2014-02-26
I have been using Ubuntu for some years, but still consider myself a beginner in terms of knowing how to fix things. Thankfully, this forum is very supportive of us guys who need a lot of handholding. I had exactly the same questions when I was considering switching to Linux. Will never look back as Linux is industrial strength compared to Windows, and as I understand it, inherently much more secure than Windows. I do not have any kind of AV nor a software firewall (other than what exists in my router and what may be included in Ubuntu that I am unaware of.) I run 12.04 and likely will so so until 2017 unless 14.04 has some compelling reason to change sooner. Installing updates is simple: just click on "Install", enter your password as required and it is automatic from there.

I use LibreOffice (and previously OpenOffice which was predecessor to Libre), exclusively for about 5 years now, and have yet to find anything that I cannot do in LibreOffice Calc that can be done in Excel (which may more reflect my personal use as opposed to what others may need). I am a financial type and run complex financial modeling in LO Calc. If you know how to use Excel, you will already understand how to do 95% of LO Calc. There are a few things that are done a little differently, but they are easy to figure out.

One word of warning. the Unity interface, which comes on 12.04 may not be to your liking. I hate it unconditionally, although some seem to be OK with it. To me, it is a lot like Apple in that it seems to be designed to keep you "above the fray" that goes on "under the hood". This seems contradictory in that Linux tends to attract those who don't mind getting their hands dirty, and I suspect that most Linux users have to eventually come to terms with the command line. I resisted for too long, but am now finding out how rewarding the terminal can be.

The good news is that you can revert to a more "work friendly" (my view only, some may get all they need done under Unity) desktop (Gnome Desktop) quite easily, and there are readily available instructions on how to do this. If you need assistance, all you need to do is ask on this forum.

I now do 99.9 % of my computing on Ubuntu and it would be 100% except for one program that my wife uses which is for Windows, so we have one computer dedicated for this purpose and it falls to me to keep it updated (uggghh!). Give it a whirl.

---

### Post by mastablasta on 2014-02-26
> **jay36 said:**
> I thank you all for your advice/suggestions. I think now the things are little clear to me. 



I will install 12.04 or wait till April for 14.04. I hope 14.04 comes up before XP support ends.

probably not, however you can upgrade to it. if the system doesn't need some heavy tweaks to work it should upgrade quite calmly. upgrade takes about 1 -2 hours depending on internet connection and computer speed. remember to try it first to see if it works well with all periferal mashcines (printers...).

> 
[COLOR=#333333]I am a finance manager and do lot of financial modeling on MS Excel. So I guess ditching MS Office [/COLOR][COLOR=#333333]and learning [/COLOR][COLOR=#000000]LibreOffice [/COLOR][COLOR=#333333]would be too much difficult to me [/COLOR][COLOR=#333333]. No has cursed Microsoft more than me when they introduced drastic changes from Office 2003 to Office 2007. But I will research about this Wine thing and see how easy it is to install/use MS Office in Ubuntu.

think of libre office as enhanced MS 2003. :-)
2007 - Excel, Word and PowerPoint work well in wine (or Crossover). the only issue is smart art that can crash it if you use it. however i have to say that after certain wine updates i dint' get that crash anymore. i do not use any others from MS. Outlook and Access do not work so well from what i read.
another alternative is WPS office AKA Kingsoft ofice - A chinese clone of MS office that has a native linux verison. works quite well. has a couple of themes such as MS 2003 look, MS 2013 look...
There are also Google docs...

final option is to put windowsxp inside a virtualbox and then isolate it form internet and only have it for MS office. you could even remove some winxp components to make it lighter to run only the office in there.
> 
In fact its because of MS Office that I have stuck with Windows all these years.
[/COLOR]

well if it's just that, then it's a bit ridiculous. :-)

> 
I have not 100% understood about antivirus suggestions, but will research about ClamAV. I do lot of research on net and have to download various files, so at times I land up at sites which might not be safe. Hence I need a robust security mechanism. 

security mechanism is built in with linux. viruses and malware that is written for windows does not work on linux. the biggest threats in linux are - Java and Flash (hwich are also threats in windows). you can block those two in firefox or only alow them when you trust the site. you will also need to give permission for any system changes. you can't runa file unless you explicitly make it executable (again you need toprovide password for that.

what others ment is that antivirus in linux do not scan file unless you tell them to. in windows for exampel Avira will autoscan all files. and evenwhen the do scan they only scan for windows malware (which wont' work on linux). they are mostly ment if oyu are havign a mail server or are passing on files to windows users. but they should provide their own protection.

for firewall ubuntu has UFW (uncomplicated firewall). you can enable it, but unlike windows, ubuntu doesn't have any open listening ports by default (i.e. by default doors are closed :-) ).

otherwise antivirus scanners: Avira, Bitdefender, ClamAV and a few others...most windows AV brands have some sort of linux version so people can put it on linux mail servers ;-)

here is more info on antivirus in Ubuntu: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by SeijiSensei on 2014-02-26
> **Odyssey1942 said:**
> I use LibreOffice (and previously OpenOffice which was predecessor to Libre), exclusively for about 5 years now, and have yet to find anything that I cannot do in LibreOffice Calc that can be done in Excel (which may more reflect my personal use as opposed to what others may need). I am a financial type and run complex financial modeling in LO Calc. If you know how to use Excel, you will already understand how to do 95% of LO Calc. There are a few things that are done a little differently, but they are easy to figure out.

What about Excel spreadsheets that include lots of macros and VB code?  My understanding is that these are not well-supported in Calc, but I don't have any personal experience to know.  Like you I've used open-source spreadsheets for years, but I don't have to interact with people working on Excel.

> **jay36 said:**
> No has cursed Microsoft more than me when they introduced drastic changes from Office 2003 to Office 2007.
jay36, I suggest you install [LibreOffice for Windows]("http://www.libreoffice.org/download/?type=win-x86&version=4.2.1&lang=en-US") on your XP machine and see if it works for you.  You'll find it looks much more like Office 2003 than 2007, particularly because it has no "ribbon."

---

### Post by Nayab Basha Sayed on 2014-02-26
You really don't need AV for Linux as your work is concerned.
Get used to Libre Office as it is compatible with MS Office.
Install 12.04 now and you can upgrade 12.04 to 14.04 without fresh installing Ubuntu.
Anyways.. Welcome to Linux Family

---

### Post by hebrewofyhwh on 2014-02-26
> **jay36 said:**
> [COLOR=#333333]I am not a tech guy and have been using Windows as these years. Recently thought to try Ubuntu as Microsoft will stop XP support. I would be grateful if knowledgeable members here can answer few basic queries.[/COLOR]

[COLOR=#333333]1. Now on download site there are 2 versions.. 12.04 and 13.10[/COLOR]
[COLOR=#333333]Which one should I install? It says 12.04 will be supported till 2017 and 13.10 for nine months?![/COLOR]

I did the ame thing when I learned that XP was no longer to be supported. I chose the 12.04 LTS for the reason that it is supported for the longest time. And my reasoning was that it would be the most stable  and have the least amount of bugs  and that any bugs would be found out faster and solutions provided. 

[COLOR=#333333]> 2. Do I have to upgrade every time Ubuntu comes out with new versions? Are every versions very much different from one another?  Ubuntu seems to be upgrading every now and then. It would be a pain to install and learn a new OS every nine months![/COLOR]  
I don't think so. If you use 12.04 LTS you have access to a high qualtiy OS for a few good years, I forget when they stop supporting 12.04

[COLOR=#333333]> 3. Will MS Office 2007 run on Ubuntu?[/COLOR]
There are built into 12.04 a very fine group of programs that work just about exactly like the expensive Microsoft  versions.

[COLOR=#333333]> 4. What about antivirus? Are there any free Ubuntu free antivirus?[/COLOR]
I don't use one. but that is not to say that I am doing what everyone should be doing.

[COLOR=#333333]> I did a basic googling about these queries... but either they were old/not relevant or have only confused me more.[/COLOR]

[COLOR=#333333]Thanks.[/COLOR]

I hope I have hlped you. I have just recently switched to this 12.04 LTS Ubunto Percise Pangolin and I am quite satisfied. The OS does everything that I need, and for the one program I need XP for I no longer need because I can run the Word.net program on an Ubunto program called "Wine" and it runs   perfectly.   If you need more assistance please feel free to ask.  And there are many people here who are more than willing to help and knowledgable on this. I am not much good on  technical aspects per say but on some things I can assist too.   Peace.

---

### Post by holycow131415 on 2014-02-27
For your machine I would get Xubuntu, and wait for 14.04 release so that you can have a clean install of it.

And to make Wine easier to use, install PlayonLinux. Its a front end for wine, and has wizards that help you install many windows programs.

---

### Post by Thee on 2014-02-28
Chances of getting a virus on Linux are practically slim to none. So you don't really need an anti-virus.
Install your software using the Software Center, keep off the shady websites and think before you enter your system password.
That's all really. So you don't have to worry about it much, because the viruses for Windows simply don't work on Linux.

---

### Post by Mark Phelps on 2014-02-28
> What about Excel spreadsheets that include lots of macros and VB code? Then that, essentially, rules out using MS Office in Wine.  I've linked the WineHQ page for MS Office:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=31]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=31")You'll see that Office 2007 is the latest version that has a decent rating.

Furthermore, if you click on Excel, then on the 2007 version, and read the details -- you'll see that it clearly states that executing macros does not work.

The following quote about macros is from the LibreOffice help page: > With a few exceptions, Microsoft Office and LibreOffice cannot run the same macro code. Microsoft Office uses VBA (Visual Basic for Applications) code, and LibreOffice uses Basic code based on the LibreOffice API (Application Program Interface) environment. Although the programming language is the same, the objects and methods are different.

Furthermore, Wine does NOT simulate a Windows environment -- that would make it an emulator -- and the acronym Wine stands for "Wine Is Not an Emulator'.  Wine is a hack in which some Windows DLLs were rewritten to replace Window OS system calls with Linux OS system calls.  To the degree that the Windows app relies exclusively on these few DLLs, it will work well.  But in recent years, MS had moved away from using these into using different middleware (e.g., Silverlight, .Net) that do not work well in Wine -- which tends to explain why recent MS Office versions get very poor ratings.

---

### Post by Rob Sayer on 2014-02-28
I disagree with running Office in Wine as well.  As mentioned, it's not a virtual machine running windows, and it's buggy and tricky for experienced linux users.  Sorry, but recommending it to a linux newbie is silly.  Actually running windows in a proper virtual machine would actually make sense.

I also disagree that Libreoffice is a substitute for Office.  I know some fairly serious users who run linux or macs and they won't use libreoffice because there are too many imcompatibilities.

I don't believe the OP has listed hardware specs either.  It's not easy to recommend a version without that.

But I *would* recommend dual boot windows/ubuntu.

I use ClamAV antivirus in linux as well but I think what the OP doesn't understand ... most Windoze users don't ... is that you don't need to have an AV program running all the time like you do in windows.  I just use clamav on demand on data files because I still have a windows 7 partition.  Though it must be feeling pretty neglected.

To put it in perspective, I've only had linux installed for a few years but I know geeks who've been running it at home for over 20 years, back when you had to build it yourself.  If ubuntu is like an Ikea store, back then it was like having a sawmill and a pile of logs.  Not one of them uses an AV program running in the background.

A lot of linux users don't even have their firewall turned on.  Many people don't really need one.  That'd be the height of ignorance in windows.

---

