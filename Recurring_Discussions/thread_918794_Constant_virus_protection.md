---
title: "Constant virus protection?"
date: 2008-09-13
forum: Recurring Discussions
---

### Post by Grimhound on 2008-09-13
Are there any options for more Windows-esque virus scanners for Ubuntu that run a 24/7 diagnostic scan of the system as well as scanning all incoming files and website data? I know that many would argue that 'Linux doesn't have viruses', but that's the sort of arrogance that makes me hate Apple. I may honestly end up just using Vista if there are no options for a comprehensive defense against all forms of incoming malware and viruses.

I like to believe that Linux can be something, but it isn't worth giving hackers and viruses a weak point in my network to strike at.

---

### Post by northern lights on 2008-09-13
Even though, it might be repetitive, especially given you mentioning "many arguing that Linux doesn't have viruses".

What you are looking for is really only relevant if you dual boot or share you're data on a Windows network.

Otherwise, as far as [QUOTE=Grimhound]I like to believe that Linux can be something, but it isn't worth giving hackers and viruses a weak point in my network to strike at.[/QUOTE]is concerned, a Linux OS is by nature giving less of a "weak point" as is an XP install with McAffee, AntiVir, Norton Security Suite and what not else all installed and running simultaneously.

Still, to finally answer your question, there are several such pieces of software, both proprietary and free.

[This article]("http://www.linux.com/articles/22899") should be of help.

Nonetheless though, this is more about *perceived* security than anything else...

---

### Post by Grimhound on 2008-09-13
> **northern lights said:**
> 
Nonetheless though, this is more about *perceived* security than anything else...

I perceive my safety to be greater using Windows with SpyBot and Avast! installed and running than I do with just Linux. Just because Windows viruses don't affect the Linux kernel doesn't mean I want to have them piled up a mile high in the corner of my hard drive somewhere. I'd rather have support against viruses, though the fun thing you have to ask yourself is how many people are actually looking to try and /find/ possible Linux viruses VS possible Windows viruses? Is there even a percentile of the force rooting through Windows? What if someone created a unique little virus to enter into Linux-based systems just to one day decide to active it and clear the board?

I'd rather be Rome repelling the Huns at the gates than Pompei being wiped out by Vesuvius.

---

### Post by Zzl1xndd on 2008-09-13
As a list of options has already been given, I am inclined to agree with Northern lights. It isn't that there are no Linux virus' its that it is overly difficult for them to propagate because of the nature of the Linux OS. 

Perhaps this will offer more insight.

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

[http://www.linux.com/feature/60208](http://www.linux.com/feature/60208)

---

### Post by Grimhound on 2008-09-13
I just have to note that I find this hilarious.

[http://www.ravantivirus.com/](http://www.ravantivirus.com/)

"RAV technology acquired by Microsoft."

---

### Post by northern lights on 2008-09-13
> **Grimhound said:**
> I perceive my safety to be greater using Windows with SpyBot and Avast! installed and running than I do with just Linux
This perception is factually wrong.

> **Grimhound said:**
> What if someone created a unique little virus to enter into Linux-based systems just to one day decide to active it and clear the board?It is another misconception, that Linux is virus-free only because of malware creator's little interest in the OS because of Windows' gigantic market share. Linux is foremost safe because of its security model. Windows is foremost unsafe because most users do not create separate user and administration accounts and work with admin rights and 100% of the time...

---

### Post by Sef on 2008-09-13
> I like to believe that Linux can be something, but it isn't worth giving hackers and viruses a weak point in my network to strike at.

Anti-virus won't do anything to stop a hacker.  To stop a hacker that involves locking down your system.

> I just have to note that I find this hilarious.

[http://www.ravantivirus.com/](http://www.ravantivirus.com/)

"RAV technology acquired by Microsoft."

For something really funny, read [this old article]("http://www.linux.com/articles/42031").

---

### Post by northern lights on 2008-09-13
> **Sef said:**
> For something really funny, read [this old article]("http://www.linux.com/articles/42031").
Nice one. Chuckled quite a bit.

---

### Post by original_jamingrit on 2008-09-13
Viruses are not something to worry about for Linux.  You've probably already heard all about how you'd need to be root or you need write access to executable binaries, for the possibility of Linux viruses to exist.

The thing is that viruses are userland, and userland is pretty much locked down in Linux.  And ironically, some security software can actually be used as an attack vector.  Instead of viruses in Linux, however, you may want to watch out instead for rootkits.  Rootkits, like viruses, generally just "don't happen" at all in Linux.  The difference is that a rootkit can actually do something to a Linux system, (if it's engineered for Linux, of course).  I suggest you install rkhunter available in the repos, if you want an extra layer of security.  Because there are currently no viruses existing for Linux, there are no malware options for Linux viruses.  But there is rkhunter.

---

### Post by Grimhound on 2008-09-13
My main concern isn't about viruses picked up through executable files, as I really never came across any of those on Windows as it is. Half the experience of personal computer use is fully dependent on savvy and intelligent navigation of the internet. My primary concern is more for web-executed scripts, which for the most part make up the vast majority of viruses I've encountered in the last many years.

I don't mean to sound ungrateful, as I really am appreciative of your assurances.

One more thing I'd like to inquire. When I install clamav-daemon, does that automatically keep it running in the background and scanning as I'd generally like it to, or do I have to do something special to get a realtime protection?

Also, how do I go about creating icons for the ClamAV and RkHunter programs in the Applications menu? Mind me being a newbie.

Edit: Does RkHunter even have a GUI, or is it just a terminal-based program. If it is, there is no problem. My main concern is on getting some sort of net up against possible threats.

---

### Post by northern lights on 2008-09-13
> **Grimhound said:**
> Also, how do I go about creating icons [...] in the Applications menu?
Navigate to "System > Preferences > Main Menu"

---

### Post by aysiu on 2008-09-13
ClamAV just looks for Windows viruses anyway.

While a good case could be made that Linux by its design is highly virus-resistant, it's also a moot point in this case.

Even **if** a potent and viable virus targeting Linux were released in "the wild," **having antivirus installed would not protect you from it**.

---

### Post by BenAshton24 on 2008-09-13
For someone to create a Linux virus, they would have to achieve all of the following:

A) Make it compatible with all of the ditros out there (that already makes the code massive)
B) Well this is a difficult one, get past the security to gain root access. hmm what can it do? 1) brute force your computer (if you had an ounce of intelligence you would notice this when your computer began to run like a snail on sleeping pills) 2) ask you to enter your password (once again it's back to your intelligence,"hmm should i enter my password when i'm prompted for no apparent reason?"
C) Lug this huge binary onto your computer. i suppose it could be disguised as a program, but if the program isn't open source and you don't know where its coming from then you DON'T DOWNLOAD IT! how else could it get on? well, it couldn't. you would actually have to physically download it because there are no viruses in the Ubuntu repositories and Firefox is pretty much security tight.

Correct me if I'm wrong but I'm pretty certain that a virus creator would A) not bother going through all the above hassle B) give up after 3 days of coding and realizing that he still has around 500 distros to get it working on
As for windows viruses getting on your computer, unless your going to run internet explorer in wine then your fine :P
if your still worried check out "clamav" it's in the safe and secure Ubuntu repositories :P

Hope this Helps
Ben.

---

### Post by aysiu on 2008-09-13
BenAshton24, I don't think you should discount social engineering so quickly. We did, some months ago, have a spate of people asking new users to paste malicious commands into the terminal, and the trusting new users did. It's hard when you're a new user--you don't immediately know what's trustworthy or what's not.

Of course, having antivirus installed won't stop social engineering any more than it would stop this imaginary new Linux virus from spreading.

---

### Post by BenAshton24 on 2008-09-13
Aysiu, ye i suppose i was a bit hasty to put social engineering aside, i remember when i first started using Linux as my main os, it does require a certain amount of trust to follow what people say when they are helping you and it's quite easy for your average "evil person" to exploit this trust. I suppose everyone no matter how much they know about what they're doing should double check because it's quite easy to fall into a false sense of security that everyone who is giving you advice is trustworthy. :D

Ben.

---

### Post by SunnyRabbiera on 2008-09-13
> **Grimhound said:**
> I perceive my safety to be greater using Windows with SpyBot and Avast! installed and running than I do with just Linux

You got to be kidding me, most of the time Windows is as secure as the titanic after it hit the iceberg and about ready to go under.
Linux security is vastly superior to Windows in security, for the simple fact that windows needs antivirus and antispyware tools in the first place.
You know nothing on how the linux security structure works, well its easy to educate you:

In windows the main reason why you need so many antivirus tools and have so many issues is because of the way it is built.
By default Windows gives the main user root access, it uses no main password (unless you set one) and its software model is just as vulnerable.
Even with Vista and the UAC (which is a joke compared to the linux root system) Windows just opens itself to danger.

Under linux things are much different, the root account is separated from the rest of the users and the execution of such things like viruses is limited due to how the security model is built.
Granted yes someone can still build a virus for linux and yes there are ones that are in concept phases but most of them are concept only or need different situations to work (like running as root)
In linux the user is discouraged from using root access, instead of encouraged like in windows.
In terms of security Windows is as sensible as a screen door on a submarine.
 
> Just because Windows viruses don't affect the Linux kernel doesn't mean I want to have them piled up a mile high in the corner of my hard drive somewhere. I'd rather have support against viruses, though the fun thing you have to ask yourself is how many people are actually looking to try and /find/ possible Linux viruses VS possible Windows viruses? Is there even a percentile of the force rooting through Windows? What if someone created a unique little virus to enter into Linux-based systems just to one day decide to active it and clear the board?

Like I said it can happen, no operating system is 100% safe and that includes linux.
But for its credit Linux is practically Fort Knox in comparison to windows, because open source developers are always fixing bugs while the bugs in windows still flower.
Want to be 100% safe on your computer?
Do you really want your computer to never have the chance of being compromised?
then your answer is simple: dont use the internet.

> I'd rather be Rome repelling the Huns at the gates than Pompei being wiped out by Vesuvius.

Well dont use windows then, as compared to linux Windows is Pompeii

---

### Post by northern lights on 2008-09-13
> **aysiu said:**
> Even **if** a potent and viable virus targeting Linux were released in "the wild," **having antivirus installed would not protect you from it**.+1 Very valid point. Further nullifying the sense in the argument.

+1 for Sunny's remarks also.

---

