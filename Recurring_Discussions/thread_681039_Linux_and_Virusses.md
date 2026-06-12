---
title: "Linux and Virusses"
date: 2008-01-28
forum: Recurring Discussions
---

### Post by Jelmoh on 2008-01-28
Well, me and a friend of mine were talking about Windows and Linux and games, games mostly.. And the enormous prizes!

We wondered, what if game designers started to design games for Linux (made it possible some how to play games with Linux as 'good' as you can with windows) and many people were getting Linux (as it's free) in stead of Windows... There would obviously be many virusses made for Linux.. but is Linux as easy to get by virusses as Windows?

Didn't express myself that well.. But you'll probably understand! ;)

---

### Post by Whiffle on 2008-01-28
Nope its not.  Linux is an entirely different kettle of fish as far as viruses go, and that isn't dependent on how many users it has.  Its not perfect, nothing made by man is, but its pretty darn good ( i don't even run antivirus software, and it doesn't worry me in the least).

---

### Post by aaaantoine on 2008-01-28
This is one of those Recurring questions regarding Linux.

Short Answer: Yes, it is *possible* for a Linux machine to get infected, but not probable.

"Viruses" for Linux already exist: they're called [Rootkits](http://en.wikipedia.org/wiki/Rootkit).  As long as you don't use root privileges or sudo to install programs from untrusted sources, and as long as you reserve root/sudo for system maintenance tasks (eg, don't run Firefox as root), they will never be a problem for you.

However, it would be easy to create a program that, when executed as root, can do horrible, horrible things to your Linux machine.  One of the first things such a program could do is replace key system files with its own customized files.  From there, it could do pretty much whatever it wants.

---

### Post by LaRoza on 2008-01-28
Only through social engineering...

Keep in mind that most servers run Linux or another *nix, and servers are prime targets for malware, yet that is not a problem.

---

### Post by snakeeyes on 2008-01-28
Linux is not Windows, infecting a Linux machine with a virus is very difficult and the major reason is because of user account control. A regular user will never have full access to the system. That is the best security feature ever something Vista also has. Vista is pretty secure as well for example on my family's pc has not got a single virus or spyware since user account control came in Vista.

Linux i still more secure though for 3 more reasons.
1. The Linux community deals with security threats very seriously, if anyone finds a security flaw than also Linux security experts r on the alert and immediately fix it.
2. Its open source so since the code is freely available anyone can repair it or improve it if something goes wrong or if they find a flaw in it.
3. Also this last reason I think is the most important one, Linux is made by regular people and we r like a community so since its made for the people by the people then no one will ever want to harm it.

That means no matter how popular Linux gets u won't see people try and harm it.

---

### Post by Jelmoh on 2008-01-28
Your last 2 arguments...
Just because it's OpenSource means it's obviously easier to infect it, am I right?
The last thing... I don't think that's right... because people who want to do harm to something don't care if its created by a really devoted group of people..

But what seems pretty clear now is that Linux is safer than Windows... :) Which eases me! ;)

---

### Post by Steveway on 2008-01-28
> **Jelmoh said:**
> Your last 2 arguments...
Just because it's OpenSource means it's obviously easier to infect it, am I right?
The last thing... I don't think that's right... because people who want to do harm to something don't care if its created by a really devoted group of people..

But what seems pretty clear now is that Linux is safer than Windows... :) Which eases me! ;)

No infact it's harder to hide hide malicious code in open-source code than in closed-source ones. Also normally the changes get checked by several people before they get merged together with the rest.
Also, a thing that is a little thorn in my eye in this thread: It's virii! Not viruses or virusses etc.
Also there are allready several game-developers making their games for Linux, too. For example: The UT series by Epic. The Quake and Doom series by ID-software. And some others like Introversion (awesome games but not very mainstream.)
The Linux version of Doom3 for example even has lower minimal specs than the windows-version. It's pretty clear why, overhead by the OS and such things.
That's what I wanted to say, I think.

---

### Post by bodhi.zazen on 2008-01-28
> **Steveway said:**
> Also, a thing that is a little thorn in my eye in this thread: It's virii! Not viruses or virusses etc.

Umm ... sorry, but WRONG :

[http://linuxmafia.com/~rick/faq/plural-of-virus.html](http://linuxmafia.com/~rick/faq/plural-of-virus.html)

[http://www.merriam-webster.com/dictionary/virus](http://www.merriam-webster.com/dictionary/virus)

> *plural* vi·rus·es

---

### Post by snakeeyes on 2008-01-28
> **Jelmoh said:**
> Your last 2 arguments...
Just because it's OpenSource means it's obviously easier to infect it, am I right?
The last thing... I don't think that's right... because people who want to do harm to something don't care if its created by a really devoted group of people..

But what seems pretty clear now is that Linux is safer than Windows... :) Which eases me! ;)
No open source makes it harder to affect cause once someone does then they will obviously have to release the code before someone uses it and if the developers at the time realise and see the risk which they do they they will fix it immediately.

The second thing is true that when people want to harm something they wont stop, but most hackers and programmers know Linux very well. Lets just say people don't want to harm linux because its made by people and not companies and hackers like to mess with proprietary systems more. I know a few people who would really like to exploit flaws in OS X because they dislike apple.

---

### Post by y-lee on 2008-01-28
> **Steveway said:**
> Also, a thing that is a little thorn in my eye in this thread: It's virii! Not viruses or virusses etc..

Hmmm, we speak english not latin. Languages change and evolve. "[Viruses]("http://www.m-w.com/dictionary/viruses")" is a correct plural of virus. I can understand where you are coming from but that is a losing battle these days.

Anyway I feel Linux is unlikely to ever have much of a virus threat for the reasons already mentioned.

---

### Post by Steveway on 2008-01-28
> **bodhi.zazen said:**
> Umm ... sorry, but WRONG :

[http://linuxmafia.com/~rick/faq/plural-of-virus.html](http://linuxmafia.com/~rick/faq/plural-of-virus.html)

[http://www.merriam-webster.com/dictionary/virus](http://www.merriam-webster.com/dictionary/virus)

Well well, interesting, you learn something new everyday.
Seems like I've fallen for something that many others have fallen for, too.
Well it seems like, even thoughI prefer the sound of virii to viruses, I'll have to stick to viruses.

---

### Post by mocoloco on 2008-01-28
As has been pointed out, there are a lot of flaws in the notion that Linux only has less viruses because it has less market share. Here's my comparison of the two on security (these are a bit over-generalized I know. Feel free to correct me if I'm wrong on any of these).

WINDOWS
1) Most users are generally running as Administrator (both by default and because life's a pain if you don't), so anything they run has access to the whole system
2) The system determines if files are executable based on name (the file extension), so users can get a file from an e-mail or website and unwittingly execute something dangerous
3) MS has gone out of their way to add scripting functionality to their web browser and e-mail clients (a choice they may now regret), making it easy for Active-X controls, VB scripts, etc to do almost anything they want
4) A culture/tradition of mostly closed source, proprietary apps, so users have to trust the one author or entity that gave them the software

Yes it's true that some measures have been added to deal with this, mostly in the form of dialogs explaining the hazard, as in Outlook and Outlook Express, or the now famously annoying dialogs in Vista that pop up when you run almost anything. These are in my opinion feeble duct-tape patches that users quickly learn to ignore.


LINUX
1) Desktop users rarely if ever run as administrator, so nothing they run could damage the whole system
2) Whether or not a file is executable is determined by a file attribute, not it's name. All browsers, email/ftp clients, p2p, etc that I have seen will by default remove the executable attribute from files, so users can't be easily tricked into executing something they've downloaded
3) No active-X, no embedded VB scripts, no putting users one click away from giving any third-party massive amounts of control.
4) A culture/tradition of mostly free/open source software, so users can put their trust in an entire community that has reviewed the code and found it safe, or if so inclined they can review the source themselves

There are probably a bunch more points I've missed. Of course a Linux user could still be tricked in to actually making a file executable and running it, maybe even giving root access to something they think is safe.  For both systems it's a matter of user-education, knowing what to watch for and who to trust. 

I find it ironic though that the Windows family has the most market share, yet has the cards stacked very much against it as far as security.  No wonder Viruses and Spyware are rampant. For the "average" user whose hardware is compatible and whose software needs can be fulfilled by FOSS I think security and peace-of-mind is the number one reason to switch to Ubuntu or another Linux distro.

---

### Post by peter72 on 2008-01-28
Another big reason for not seeing a lot of viruses in Linux is because of diversity.  Most here run Ubuntu, but there are still a lot of other distro's and versions out there.   One who writes an exploit for program A on Ubuntu 6.10, may not infect Ubuntu 7.10, or Redhat/SuSE/Mandrive etc.

Just like in all organisms, diversity is the best defense to viruses.

---

### Post by xpod on 2008-01-28
Only way i`ve managed to *get* myself overcome with viriiii....viruses, in nearly two years now,is by playing Viruskiller:wink:

 [ATTACH]57892[/ATTACH]

Lillte blighters get me every time:)

Seriously though,i`ve never used actual AV programs in the year & a half i`ve used Ubuntu/Linux OR ever had any viruses and with with 5 kids....and just as many pc`s *thats* got to tell you something:)

---

### Post by aysiu on 2008-01-28
> **mocoloco said:**
> As has been pointed out, there are a lot of flaws in the notion that Linux only has less viruses because it has less market share. And I'd like to point out that there are a lot of flaws in the notion that more marketshare won't bring more malware to Linux:
[Without education, it doesn’t matter which OS is “more secure”](http://ubuntucat.wordpress.com/2008/01/22/without-education-it-doesnt-matter-which-os-is-more-secure/)

---

### Post by Ganton on 2010-01-18
> There would obviously be many virusses made for Linux.. but is Linux as 
> easy to get by virusses as Windows?

"For being a system more popular is more vulnerable to viruses"
False. 
Counterexample: Apache.

"For being a system less popular is less vulnerable to viruses"
False.
Counterexample: MS-DOS, in its beginnings it was not popular and was an easy prey for viruses; later too, even if it was more popular.

The old idea is that Linux is secure because no-one is using Linux is also nonsense, there are millions of internet servers, electrical appliances, routers, remote controls, clusters, supercomputers, PDAs, mobile phones running Linux. If I wanted to write a virus, I would write one that would take out the infrastructure of the internet, rather than hose up some basement dwelling internet poker players/porn junkies pc.

---

### Post by yester64 on 2010-01-18
Hi,

i think there has to be a classification to the topic whats possible and how.
You have personal computing and business.
For a hacker who aims to get on secret data's (cooperate espionage) it does not matter what system is running. The system will be hacked no matter what.
One thing is certain. Linux is harder to crack then other OS's, but it is not impossible.
There are a variety of virus, Trojans and other malware, but not a huge load.
Assuming that 90% of the market would use Linux would raise the bar for mischiefs to attack linux run computers more often.
If you follow the threadlevel on current systems, you see any linux distribution also in the list. Redhat, Suse, Debian.. all have holes. But, they usually get fixed very quickly.

So, even if you run Linux (good choice) you are still not 100% safe. But safer than say Windows.

Further reading here.
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by aysiu on 2010-01-18
This thread is old. There are plenty of other more recent Linux and virus threads to post in.

---

