---
title: "antivirus  for ubuntu"
date: 2008-09-24
forum: Recurring Discussions
---

### Post by esmailgad on 2008-09-24
Hi everyine
Can some one tell me about an antivirus for ubuntu and at the same time detect widows viruses and spyware
Thank you for your help

---

### Post by tuxxy on 2008-09-24
ClamAV, Avast etc are available, you would ideally use an AV if your regularly sharing files with or accessing a windows drive.

---

### Post by ounas on 2008-09-24
As tuxxy said try Clam it's the best :)

---

### Post by hyper_ch on 2008-09-24
(1) you don't need antivirus

(2) you don't need anti-spyware

---

### Post by esmailgad on 2008-09-24
Of course I need an antivirus. I think you know that linux also has own viruses and malwares. Sure they are much lesser than those for windows but they exist. Also in my case I use a dual system Linux/Windows. Under linux I clean the files before using them under windows. 
Now I have a question. I have a flash memory that is contaminated with viruses. under linux I detected and deleted  some of them.How can I delete the other viruses specially when I use the normal (move to trash) order it is denied, or How  can I formate it under linux to be used under windows.

---

### Post by esmailgad on 2008-09-24
I downlaoded AVAst.tar and how can I install it?

---

### Post by hyper_ch on 2008-09-24
> **esmailgad said:**
> I think you know that linux also has own viruses and malwares.
30 known viruses on linux - none in the wild - most of them just proof of concept... compared to over 80'000 known malware on Windows?
Good luck at catching a virus on linux - I'd say you have better chances winning the lottery.

> **esmailgad said:**
> Also in my case I use a dual system Linux/Windows. Under linux I clean the files before using them under windows.
So then you'll have no need for AV then on windows. Right?

As for the flash memory:
- you can format it as fat32
- you can just format it to any filesystem and then reformat it in windows to ntfs
- you can format it to ext3 and install ext2/3 drivers in windows

---

### Post by SunnyRabbiera on 2008-09-24
> **esmailgad said:**
> Of course I need an antivirus. I think you know that linux also has own viruses and malwares. Sure they are much lesser than those for windows but they exist.

No there is no addware/ spyware for linux.
And viruses are conceptual mostly, most virus scanners you will find for linux are for WINDOWS viruses.
No need for paranoia!

---

### Post by lazyart on 2008-09-24
> **esmailgad said:**
> Of course I need an antivirus. I think you know that linux also has own viruses and malwares.
Hahaha.  If you believe that I have some beachfront property in Nevada to sell you...
> Sure they are much lesser than those for windows but they exist. Also in my case I use a dual system Linux/Windows. Under linux I clean the files before using them under windows.You clean them or you want to clean them?  Linux antivirus scans for infections that would affect Windows users.  It will probably throw up a good number of false positives.
>  
Now I have a question. I have a flash memory that is contaminated with viruses. under linux I detected and deleted  some of them.How can I delete the other viruses specially when I use the normal (move to trash) order it is denied, or How  can I formate it under linux to be used under windows.Use GParted to repartition and format as fat16.

---

### Post by Dr Small on 2008-09-24
> **SunnyRabbiera said:**
> No there is no addware/ spyware for linux.
And viruses are conceptual mostly, most virus scanners you will find for linux are for WINDOWS viruses.
No need for paranoia!
+1
No need for an anti-virus.

---

### Post by oldsoundguy on 2008-09-24
the basic install principle behind Unix/Linux precludes installing a virus into the system unless you run a specific set of commands.  MOST virus programs written are for WINDOWS and those listed as for Linux are, in the main, targeted at Linux servers and are set up to infect WINDOWS users of said servers.

Having said that, IF you are going to run Windows in a VM or a second drive on the same computer or even as a dual boot and especially take it on line .. Anti-Virus programs and anti spyware programs are the order of the day for you.  The will reside IN your Windows program area, not in your Linux program unless you get the server stuff from most of the AV sources (F-Prot, ClamWin and so on)

Why is it that so many actually BELIEVE the crap coming out of Redmond as to how "insecure" Linux is? (same with how "difficult" it is to use the system. ... total BS!!)

---

### Post by esmailgad on 2008-09-24
I must tell you that  I am so happy to work under linux since I do not worry about viruses.

---

### Post by Twitch6000 on 2008-09-24
> **hyper_ch said:**
> 30 known viruses on linux - none in the wild - most of them just proof of concept

You wonder why people call Linux users stuck up?You also wonder why people call linux users zealots instead.

This is the reason...

You don't even know what you are talking about....

Linux was reported in 03 or 04 to have over 100 viruses.

In 96 there was already one virus for Linux.

In 04 or 05 there was a big Virus known called Bliss and it is still a active virus.(well at first 97 then it restruck at 04 or 05 I found the info on it)

In the latest news from 07 it is reported that linux has over 800 viruses.Even has some trojans and worms.

So please do not give out false info.

---

### Post by tuxxy on 2008-09-24
> **Twitch6000 said:**
> You wonder why people call Linux users stuck up?You also wonder why people call linux users zealots instead.

This is the reason...

You don't even know what you are talking about....

Linux was reported in 03 or 04 to have over 100 viruses.

In 96 there was already one virus for Linux.

In 05 there was a big Virus known called Bliss and it is still a active virus.

In the latest news from 07 it is reported that linux has over 800 viruses.Even has some trojans and worms.

So please do not give out false info.

+1 

It is still unlikely you will need an anti-virus for a sole linux system

---

### Post by Twitch6000 on 2008-09-24
> **tuxxy said:**
> +1 

It is still unlikely you will need an anti-virus for a sole linux system

Now this is true :).(except for a Linux server ofcourse ;))

I just hate it when false info is given out to Linux beginners wondering about such things.

I rather them hear the truth then a lie :).

---

### Post by Bölvaður on 2008-09-24
> **Twitch6000 said:**
> You wonder why people call Linux users stuck up?You also wonder why people call linux users zealots instead.

This is the reason...

You don't even know what you are talking about....

Linux was reported in 03 or 04 to have over 100 viruses.

In 96 there was already one virus for Linux.

In 05 there was a big Virus known called Bliss and it is still a active virus.

In the latest news from 07 it is reported that linux has over 800 viruses.Even has some trojans and worms.

So please do not give out false info.

Remind me on how many of them have their source code released ^^ and how many of them are able to spread between computers :)

Btw there are viruses that are not OS based, I would believe many of the ones of those hundreds you are talking about are some of those.

---

### Post by tuxxy on 2008-09-24
> **Twitch6000 said:**
> Now this is true :).(except for a Linux server ofcourse ;))

I just hate it when false info is given out to Linux beginners wondering about such things.

I rather them hear the truth then a lie :).

You hit the nail on the head sir, I thought 30 was an awfully low figure aswell, but didnt have an accurate figure as yours but knew there was over 30 listed at [URL="http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses"]wikipedia
[/URL]

---

### Post by lisati on 2008-09-24
Every user has to make up their own mind. Just because malware is unlikely to hurt the system you use, it isn't automatically prevented from doing mischief on the computers used by people you might interact with - this is particularly true when it is attached to files and documents you might want to share with others.

---

### Post by Twitch6000 on 2008-09-24
> **Bölvaður said:**
> Remind me on how many of them have their source code released ^^ and how many of them are able to spread between computers :)

Btw there are viruses that are not OS based, I would believe many of the ones of those hundreds you are talking about are some of those.

Well I know the ones that made the big geek news like Bliss and Staog gave the source code.

As they were mainly experiments to see if Linux could be infected and they proved that it could.They gave the source code to be learned from.

Also note I am not trying to say Linux has to use anti virus just because they are out there.I just want people to know that it is possible to get infected,but very unlikely.
Heck if you would be smart with windows you won't get a virus.(ofcourse that is alot harder to do :()

---

### Post by lisati on 2008-09-24
Perhaps the pedantic part of my makeup is making a nuisance of itself, but has anyone else ever noticed how people tend to talk about viruses as if they're the only kind of "naughty" pieces of code that exist?

---

### Post by Twitch6000 on 2008-09-24
> **lisati said:**
> Perhaps the pedantic part of my makeup is making a nuisance of itself, but has anyone else ever noticed how people tend to talk about viruses as if they're the only kind of "naughty" pieces of code that exist?

I kind of like viruses I hexedit them in windows LOL.

With Linux I just grab the source code and well I do naughty things >.>.

Really though there are other bad things that are out there its just viruses are most well known.

There are other such things as false sites(I forget the tech term).

Then there are rootkits.

Finally there is the age old mis click leading to you getting a keylogger or your id stolen.

---

### Post by hyper_ch on 2008-09-24
> **Twitch6000 said:**
> You don't even know what you are talking about....
It seems you dont...

> **Twitch6000 said:**
> Linux was reported in 03 or 04 to have over 100 viruses.
Source?

> **Twitch6000 said:**
> In the latest news from 07 it is reported that linux has over 800 viruses.
Source?

> **Twitch6000 said:**
> Even has some trojans and worms.
[http://en.wikipedia.org/wiki/Malware](http://en.wikipedia.org/wiki/Malware)

> **Twitch6000 said:**
> So please do not give out false info.
So please do not give out false info.

If there are so many viruses - as you claim - then you should add them here: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses) (I currently count there less than 30 viruses)

And for Bliss you mentioned:
> Although it was probably intended to prove that Linux can be infected, it does not propagate very effectively because of the structure of Linux's user privilege system. The Bliss virus never became widespread, and remains chiefly a research curiosity.
[http://en.wikipedia.org/wiki/Bliss_(virus)](http://en.wikipedia.org/wiki/Bliss_(virus))

---

### Post by lisati on 2008-09-24
I got taken to [http://en.wikipedia.org/wiki/Bliss_(virus](http://en.wikipedia.org/wiki/Bliss_(virus) "wikipedia has no article" and think it should be [http://en.wikipedia.org/wiki/Bliss_(virus](http://en.wikipedia.org/wiki/Bliss_(virus))

---

### Post by hyper_ch on 2008-09-24
yeah, it cuts the url...

---

### Post by oldsoundguy on 2008-09-24
According to F-Prot (an anti virus program) As of today, there are 

1,976 .

virus programs written for Unix/Linux in the wild.

A bunch of those are UNIX specific, but some are not.  Also that includes those server targeted virus files that attack WINDOWS computers, but can be placed in Unix/Linux servers that SERVE such.
Am unable to find a break down of just how many have targeted the desktop user. (IMO, I think not very many .. maybe even less than the 71 targeting Mac.)

But with today's trend to repository only downloads, not much of a chance of getting ANY virus if you do just that and don't go searching for "the hot new item" to install on your WORKING SYSTEM.
Now. if you want to build a crash test dummy and go surfing away, feel free, and there IS a chance one of those whiz bang programs you download from that site the guy in the coffee shop told you about will actually BE a proof of concept and crash the machine.

BUT, I really  think that beats the crud out of the 

1,081,904 

virus programs in the wild for WINDOWS.

+40,226 for DOS
+11,375 for Office and it's MACROS
+43,083 for script files (mostly Active X)
+   698 for Java in Windows

Not to mention SPYWARE AND AD-WARE .. TROJANS, KEYLOGGERS, BROWSER HIJACKERS and whatever the script kiddies can come up with to mess you up for fun and profit that are not written as virus files and slide by the standard AV programs!

IF you are really THAT paranoid, then GO GET AN AV!  (a Google search using "anti virus for Linux" will get you a couple of pages of freebies from which to choose.)

---

### Post by Twitch6000 on 2008-09-24
> **hyper_ch said:**
> It seems you dont...


Source?


Source?


[http://en.wikipedia.org/wiki/Malware](http://en.wikipedia.org/wiki/Malware)


So please do not give out false info.

If there are so many viruses - as you claim - then you should add them here: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses) (I currently count there less than 30 viruses)

And for Bliss you mentioned:

[http://en.wikipedia.org/wiki/Bliss_(virus)](http://en.wikipedia.org/wiki/Bliss_(virus))

Source 1 -

[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

Source 2 -

[http://blogs.zdnet.com/security/?p=1445](http://blogs.zdnet.com/security/?p=1445)

Source 3 -

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Source 4 for fun -

[http://vx.netlux.org/vl.php](http://vx.netlux.org/vl.php)

I also did mention in one of my later posts I did know bliss was a test virus.
I also mentioned that some viruses were all for testing and helping Linux while others were out in the wild to harm the users.

So do not try and say I have no clue what I am talking about.

I think I myself am a little out dated due to oldsoundguy showing there is more then 800 Linux viruses out there now.
So all this is truly proving is what I meant from the start be aware Linux does have atleast 1 virus.
It is your choice however how you look at it.

Oh and the reason the wiki does not have all the Linux viruses listed is because no one put them all.It does however mention it is a partial list ;).

---

### Post by cardinals_fan on 2008-09-24
> **Twitch6000 said:**
> You wonder why people call Linux users stuck up?You also wonder why people call linux users zealots instead.

This is the reason...

You don't even know what you are talking about....

Linux was reported in 03 or 04 to have over 100 viruses.

In 96 there was already one virus for Linux.

In 04 or 05 there was a big Virus known called Bliss and it is still a active virus.(well at first 97 then it restruck at 04 or 05 I found the info on it)

In the latest news from 07 it is reported that linux has over 800 viruses.Even has some trojans and worms.

So please do not give out false info.
This is rather irrelevant.  Antivirus/spyware is worthless compared to competence and common sense.

---

### Post by hyper_ch on 2008-09-25
> **Twitch6000 said:**
> Source 1 - [http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)
From Source 1:
> 
Currently there are under 100 native Linux viruses known

And I think he means malware in general - even if not, less than 100 can also mean less than 30 ;)


> **Twitch6000 said:**
> Source 2 - [http://blogs.zdnet.com/security/?p=1445](http://blogs.zdnet.com/security/?p=1445)
From Source 2:
> **Twitch6000 said:**
> Approximately 800 vulnerabilities discovered in antivirus products
Hmmmm, the products suffer from weaknesses more than there are viruses on linux ;)

> **Twitch6000 said:**
> Source 3 - [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
I posted that link earlier and I count there 21 viruses listed for linux... if my math skills don't betray me than 21 < 30.

> **Twitch6000 said:**
> Source 4 for fun - [http://vx.netlux.org/vl.php](http://vx.netlux.org/vl.php)
That's all kind of malware mixed together... no relevance ;)

> **Twitch6000 said:**
> 
I also did mention in one of my later posts I did know bliss was a test virus.
Yes, you did later... but stating it first as active virus is smoething totally different ;) So why make it a bogeyman that you need to be afraid of first-place?

> **Twitch6000 said:**
> So do not try and say I have no clue what I am talking about.
According to the sources you posted I still say that you have no clue what you are talking about. Well, actually I just repeated what you first said towards me ;) So you are allowed to say others have no clue what they are doing but others are not allowed to say the same about you? I got it ;)

> **Twitch6000 said:**
> Oh and the reason the wiki does not have all the Linux viruses listed is because no one put them all.It does however mention it is a partial list ;).
It might be a partial list... but listing 21 viruses for Linux when there are like 2'000 as old soundguy claims, then I wouldn't call that a partial list.

Furthermore, I just checked f-prot and the last viruses added for *nix was in 2002 --> [http://www.f-prot.com/virusinfo/unix.html](http://www.f-prot.com/virusinfo/unix.html)

> 
Name of Virus 	Date Discovered
Unix/Scalper 	29 Jun 2002
UNIX/Slapper 	13 Sep 2002


So I'd like to know where oldsoundguy got his number from.

---

### Post by oldsoundguy on 2008-09-25
I got my numbers from the F-Prot that is installed on one of the Windows boxes I have .. it lists them ALL on the help page with the line at the top:
"F-Prot anti-virus can detect 1,188,498 viruses and Trojans using the current virus signature file."  And below that it breaks them down into the categories I listed .. along with a few more I did not list.

It is on another machine or I would get a screen shot and post it here.

Also READING what I posted would help.  It says UNIX/Linux (which means BOTH!)

---

### Post by Twitch6000 on 2008-09-25
> **hyper_ch said:**
> From Source 1:

And I think he means malware in general - even if not, less than 100 can also mean less than 30 ;)



From Source 2:

Hmmmm, the products suffer from weaknesses more than there are viruses on linux ;)


I posted that link earlier and I count there 21 viruses listed for linux... if my math skills don't betray me than 21 < 30.


That's all kind of malware mixed together... no relevance ;)


Yes, you did later... but stating it first as active virus is smoething totally different ;) So why make it a bogeyman that you need to be afraid of first-place?


According to the sources you posted I still say that you have no clue what you are talking about. Well, actually I just repeated what you first said towards me ;) So you are allowed to say others have no clue what they are doing but others are not allowed to say the same about you? I got it ;)


It might be a partial list... but listing 21 viruses for Linux when there are like 2'000 as old soundguy claims, then I wouldn't call that a partial list.

Furthermore, I just checked f-prot and the last viruses added for *nix was in 2002 --> [http://www.f-prot.com/virusinfo/unix.html](http://www.f-prot.com/virusinfo/unix.html)



So I'd like to know where oldsoundguy got his number from.
Your a funny one...
Mainly because you go straight after numbers or certain words.

Anyways Round uhh 3?

> 
From Source 1:

And I think he means malware in general - even if not, less than 100 can also mean less than 30

Hey you are correct there so it could be any number under one hundred.Although please note the date and what my other sources have said ;).

> 

From Source 2:

Hmmmm, the products suffer from weaknesses more than there are viruses on linux

This was my bad I got the wrong link and cannot find the correct one.

> 
I posted that link earlier and I count there 21 viruses listed for linux... if my math skills don't betray me than 21 < 30.

Well yes you did post this eariler and indeed what they PUT is only 21.
HOWEVER right on the wiki it states this -
''The following is a partial list of known Linux malware:''

> 
That's all kind of malware mixed together... no relevance ;)
If you mean for all oses ok...
If you mean all as in spyware,trojans,viruses,etc.. Then it is still valid and proves a whole other point.

---

### Post by Perfect Storm on 2008-09-25
> **oldsoundguy said:**
> I got my numbers from the F-Prot that is installed on one of the Windows boxes I have .. it lists them ALL on the help page with the line at the top:
"F-Prot anti-virus can detect 1,188,498 viruses and Trojans using the current virus signature file."  And below that it breaks them down into the categories I listed .. along with a few more I did not list.

It is on another machine or I would get a screen shot and post it here.

Also READING what I posted would help.  It says UNIX/Linux (which means BOTH!)

I would take that with a grant of salt what anti-virus company writes - afterall they try to sell.
Other than that I've almost used Linux in 9 years and virus have not been an issue.

Some security advise;
#1 Install/run only stuff from trusted sources (like official Ubuntu repo).
#2 Don't run root.

If you keep this in mind - You'll be safe.

---

### Post by oldsoundguy on 2008-09-25
> **Artificial Intelligence said:**
> I would take that with a grant of salt what anti-virus company writes - afterall they try to sell.
Other than that I've almost used Linux in 9 years and virus have not been an issue.

Some security advise;
#1 Install/run only stuff from trusted sources (like official Ubuntu repo).
#2 Don't run root.

If you keep this in mind - You'll be safe.

AI, I posted that because there was an argument going on about just what was in the wild, and F-Prot (an Icelandic company) is a RELIABLE source (their AV for Linux is open source and free and their site license for Windows machines is 29 bucks a year) .. have never failed me since Windows 98 on any Windows machine I have used or are using.

You advice is true.  I have no AV installed on any of my Linux boxes and have never seen the need, as I practice safe hex on line.

But paranoia runs deep for those totally ingrained with the Windows way of life. And some still DO need their security blankie!!

---

### Post by Thomas00 on 2008-12-29
"Choosing anti virus software is such a difficult job, i have a suggestion for you guys use [www.search-and-destroy.com](www.search-and-destroy.com) and see the result you will find best from this software.

Thank You"

---

