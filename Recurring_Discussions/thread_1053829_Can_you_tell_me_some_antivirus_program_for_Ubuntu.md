---
title: "Can you tell me some antivirus program for Ubuntu?"
date: 2009-01-29
forum: Recurring Discussions
---

### Post by GSI on 2009-01-29
Hello. Can somebody tell me an antivirus program for ubuntu ?

---

### Post by jrusso2 on 2009-01-29
clam av is open source and is in the repository.

AVG for Linux have to get from avg.free website.

Avast have to get from avast.

Antivir have to get from them.

---

### Post by hyper_ch on 2009-01-29
you don't need antivirus on linux

---

### Post by mcduck on 2009-01-29
> **jrusso2 said:**
> clam av is open source and is in the repository.

AVG for Linux have to get from avg.free website.

Avast have to get from avast.

Antivir have to get from them.

Of course you should note that all these programs are mainly for scanning for *Windows* viruses.. For Ubuntu itself, you don't need any antivirus software.

---

### Post by lisati on 2009-01-29
> **hyper_ch said:**
> you don't need antivirus on linux

Maybe not FOR Linux, but more out of courtesy to Windows machines and users that you might interact with.

I heard a whisper that support for the Linux-friendly version of AVG Free was ending: see [here]("http://ubuntuforums.org/showpost.php?p=5939398&postcount=10")

---

### Post by GSI on 2009-01-29
Thanks :)

---

### Post by hyper_ch on 2009-01-29
> **lisati said:**
> Maybe not FOR Linux, but more out of courtesy to Windows machines and users that you might interact with.

So, if they can't protect themselves, what do you think is more plausible:

(1) That it is you who infects them?
(2) That they get infected from a third party?

---

### Post by movieman on 2009-01-29
> **hyper_ch said:**
> So, if they can't protect themselves, what do you think is more plausible:

If one Windows PC on your network gets virused and then uploads a file to your Linux server, you don't want that file passed on to another Windows PC that will then get infected.

---

### Post by hyper_ch on 2009-01-29
> **movieman said:**
> If one Windows PC on your network gets virused and then uploads a file to your Linux server, you don't want that file passed on to another Windows PC that will then get infected.

Why not? If you run windows you must protect yourself. If you don't do it, then don't complain you get malware. So, what has my linux server to do with the negligence of the others?

---

### Post by Dr Small on 2009-01-29
> **movieman said:**
> If one Windows PC on your network gets virused and then uploads a file to your Linux server, you don't want that file passed on to another Windows PC that will then get infected.
Windows users out of habit use antivirus. It's their responsibility to protect themselves from incoming viruses, not Linux administrators. Let Windows users take on some responibility for using such an infested OS, and scan for viruses.

---

### Post by sydbat on 2009-01-29
+1 to both hyper_ch and Dr Small. 

It is not our responsibility to protect those who are unwilling to protect themselves. 

Some feel that it is a courtesy, so they can do what they need to do. But please do not think that everyone else *should* do the same.

---

### Post by overlord.gaurav on 2009-01-29
> **hyper_ch said:**
> you don't need antivirus on linux

Says who?
Linux isn't 100% secure !
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

@Topic: You can find a list of anti virus programs on the link too!

---

### Post by uberdonkey5 on 2009-01-29
since no need to worry about viruses on my home (linux) PC, for the last year I didn't use anything.

Recently, being extra vigiliant, I downloaded firestarter (look in add/remove programs) which is a gui for software already within ubuntu. (although this was more to control how I appeared on the internet and manage information going in/out).

Unless you are worried about windows viruses on your computer (for some reason), at the PC level, you are wasting time and resources scanning for viruses.

So, question is, for what reason to you want to stop windows viruses??

(nb. the link on linux viruses is good, and ironically helps to explain why ubuntu is very safe unless you are constantly running things as root, or decide not to use repositories regularly). Also, java is a potential source of viruses... I use firefoxes 'no-script' now, which can be a little annoying, but also stops me having to use internet bandwidth to run java script adverts and also allows me to stick two fingers up at google-analytics (why should people get info from me secretly without paying for it?)

Seriously though, using virus protection (other than that intrinsic within the system) for linux is straying into the paranoid.

P.S. as one of the administrators here said ages ago, there is no substitute for regular back ups (with ubuntu, the biggest danger is messing the system up yourself)

---

### Post by hyper_ch on 2009-01-29
> **overlord.gaurav said:**
> Says who?
Linux isn't 100% secure !
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

@Topic: You can find a list of anti virus programs on the link too!

Hmmm, 22 viruses listed there... all of them rather proof-of-concept... none in the wild... possible security issues patched...
hmmm

What do I need antivirus again for on linux?

---

### Post by GSI on 2009-01-29
wait wait wait what server? I dont host any servers am just a home user ;)

---

### Post by mcduck on 2009-01-29
> **overlord.gaurav said:**
> Says who?
Linux isn't 100% secure !
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

@Topic: You can find a list of anti virus programs on the link too!

Hardly any of those was ever running wild, most of the ones that were targeted systems with specific program versions that weren't updated and every single one is history by now.

And then you can compare that list to the list of *active* Windows viruses, tens of thousands of viruses, plus all the other nasty malware and spyware..


Even the very article you posted says this: "There has not yet been a single widespread Linux malware threat of the type that Microsoft Windows software currently faces". ;)

---

### Post by cardinals_fan on 2009-01-29
> **hyper_ch said:**
> Why not? If you run windows you must protect yourself. If you don't do it, then don't complain you get malware. So, what has my linux server to do with the negligence of the others?
If you run any OS, you must use logic and "common" sense (surprisingly rare ;)) to protect yourself.
> **overlord.gaurav said:**
> Says who?
Linux isn't 100% secure !
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

@Topic: You can find a list of anti virus programs on the link too!
Signatures-based antivirus apps don't protect you on Windows, Linux, OS X, or any other platform.  To quote myself:
> **cardinals_fan said:**
> This whole issue depends on your definition of a virus.  Self-replicating viruses are rare on any platform because webmail providers, ISPs, and routers screen pretty thoroughly.  They are even rarer on Linux thanks to a sensible default permissions policy and open development process.

Other malware, on the other hand, could easily be created for Linux.  A few reasons why it hasn't been:

1. Small market share.  While Linux is popular on servers, it's much harder to trick a server admin than many desktop users.  Malware authors want to target as many people as possible.

2. Limited user by default.  While it is simple to set up a decent permissions policy on Windows, the defaults are very bad.  This leaves many people open to infection.  However, this policy can be circumvented in one of two ways:

a) Just convince the user to give the app or installer root privileges.

b) Take advantage of the ridiculous 15-minute sudo timeout in default Ubuntu

3. Most Linux users are more experienced and less gullible.  Since preinstalled Linux systems are rare, most Linux users installed the OS themselves and have some idea of what they're doing.  Such users are harder to scam.

4. The Linux community is quite tight.  If someone began distributing a malicious Debian package or script, the forums would go berserk and most people would hear about and avoid it.

Social engineering scams can work on any platform.  They just require arrogant, incompetent, or ignorant users to take advantage of.

---

### Post by overlord.gaurav on 2009-01-29
> Hmmm, 22 viruses listed there... all of them rather proof-of-concept... none in the wild... possible security issues patched...
hmmm

What do I need antivirus again for on linux?

> Even the very article you posted says this: "There has not yet been a single widespread Linux malware threat of the type that Microsoft Windows software currently faces"
True. But there could be a virus on a widespeard in the future. Why not be pro-active. A virus that deletes just the files inside my home folder is enough dangerous to me.

Need of an antivirus program at the moment...depeds from person to person.
I need it as my external hard drive is attached to a Windows PC very frequently. That's enough a reason for me to use an antivirus everytime I get it infected from another PC running on Windows.

---

### Post by p_quarles on 2009-01-30
> **overlord.gaurav said:**
> True. But there could be a virus on a widespeard in the future. Why not be pro-active. 
Proactive is great. Anti-virus software isn't proactive, though.

---

### Post by hyper_ch on 2009-01-30
anti-virus is retro-active and with linux being patched if a weakness is found, what good is an av then for?

---

### Post by GSI on 2009-01-30
I didnt knew that there are viruses for Linux :)

I installed Avast just to be shure :)

---

### Post by hyper_ch on 2009-01-30
avast will not really do anything against linux viruses...

---

### Post by GSI on 2009-01-30
why? Its a bad antivirus program?

---

### Post by hyper_ch on 2009-01-30
no, but it will not scan for linux viruses... those few that exist can't really harm you as the system was patched...

so it will only warn you on windwos viruses... and well, they won't do harm on linux. So avast will not improve your security...

---

### Post by overlord.gaurav on 2009-01-30
> anti-virus is retro-active and with linux being patched if a weakness is found, what good is an av then for?
Assume you connected your external hard drive to a Windows computer. And the computer is infected with a virus that deletes local files randomly. And now you connect the same hard drive to your computer. Wouldn't it be better if you scan it ?

---

### Post by hyper_ch on 2009-01-30
> **overlord.gaurav said:**
> Wouldn't it be better if you scan it ?
Why is it my responsability to scan for a windows virus? If a windows computer is not protected, what is more likely:
- a virus you pass on causes havoc?
- the person who did not secure the windows machine will get malware that causes havoc from other places?

---

### Post by bruce89 on 2009-01-30
> **hyper_ch said:**
> Why is it my responsability to scan for a windows virus?

"Why is it my responsability to not smoke in front of non-smokers?"

Interesting parallel.

---

### Post by hyper_ch on 2009-01-30
> **bruce89 said:**
> "Why is it my responsability to not smoke in front of non-smokers?"

Interesting parallel.

it's a flawed comparison ;) If you smoke in front of non-smokers then you harm them as the don't need to do anything. However if you copy a a windows-malware-ridden file onto an external drive it will not by default do anything. The other will have to plug it in (and mostly also run it). So there is action required on part of the Windows users but not on part of the passiv smokers ;)

---

### Post by overlord.gaurav on 2009-01-30
> **hyper_ch said:**
> Why is it my responsability to scan for a windows virus?

I have a laptop that has Vista installed. So, in order protect Vista from the virus - [as most of the viruses auto run on connecting the hard drive] - I use the anti virus on my Linux system.
And also, if I pass on my hard drive to another friend whose computer is not infected, I would rather be happy if he  returns my hard drive without commenting that my hard drive was infected. 
ALSO, if I am curious enough to run an executable  file [on my Linux system, using wine], I would rather scan it before I do so !

---

### Post by hyper_ch on 2009-01-30
so, and if you friend didn't run an antivirus at all and he gets infected, what do you tell him?

(and besides, what is an antivirus scanner for anyway if it will never report anything going wrong...)

---

### Post by overlord.gaurav on 2009-01-30
> 
(and besides, what is an antivirus scanner for anyway if it will never report anything going wrong...)

Look. I have Norton 360, V2.0 installed on my Laptop. I've seen many viruses getting uploaded to my laptop. By the time the anti-virus warns me about it, my computer is already infected. Whereas, when I connect it to me desktop running on Linux, I can very easily see the unwanted .exe files, as well as scan for viruses which are patched to certain known files as well.

This is the best I can do to convince you on the fact that antivirus on Linux does help, depending on the reason you install it with.

---

### Post by hyper_ch on 2009-01-30
> **overlord.gaurav said:**
> I've seen many viruses getting uploaded to my laptop. By the time the anti-virus warns me about it, my computer is already infected.
So you agree the antivirus software is even pointless on windows also ;)

---

### Post by sydbat on 2009-01-30
This (like every other anti-virus debate here) is pointless. 

@overlord.gaurav - Linux does not need anti-virus software. You can use it if you have Windows partitions/drives. It is your computer, you have the right to choose what to run, so enjoy. One day you will see that GNU/Linux is not Windows, that anti-virus software simply uses resources better allocated elsewhere and realize that this kind of debate is pointless. 

Ask hyper_ch...he and I had this same "discussion" when I moved over from Windows...almost a year ago. Now we agree. 

Do a search and you will see how many times this has been discussed (which is why this thread is now in Recurring Discussions) and how many people started off thinking they needed anti-virus software on Linux...and how many of those same people now point out how there is no need for anti-virus software in Linux.

---

### Post by overlord.gaurav on 2009-01-30
> **sydbat said:**
> This (like every other anti-virus debate here) is pointless. 

@overlord.gaurav - Linux does not need anti-virus software. You can use it if you have Windows partitions/drives. It is your computer, you have the right to choose what to run, so enjoy. One day you will see that GNU/Linux is not Windows, that anti-virus software simply uses resources better allocated elsewhere and realize that this kind of debate is pointless. 

Ask hyper_ch...he and I had this same "discussion" when I moved over from Windows...almost a year ago. Now we agree. 

Do a search and you will see how many times this has been discussed (which is why this thread is now in Recurring Discussions) and how many people started off thinking they needed anti-virus software on Linux...and how many of those same people now point out how there is no need for anti-virus software in Linux.


Well, I already know of the discussion. I've been passively active on the forums since years. And yes, I am already aware that you do not need an anti-virus on Linux at the moment. But, like I said..it depends on the purpose you use it for. Mine I've specified. There could be more.

> So you agree the antivirus software is even pointless on windows also
Agree? Lol ! It's a FACT ! Who can disagree to it ?

---

### Post by GSI on 2009-01-31
I'm Using AVG FREE on Windows but i rearly go in windows now :)

---

### Post by Dr Small on 2009-01-31
> **sydbat said:**
> Do a search and you will see how many times this has been discussed (which is why this thread is now in Recurring Discussions) and how many people started off thinking they needed anti-virus software on Linux...and how many of those same people now point out how there is no need for anti-virus software in Linux.

I am one of them :D
Once I move to Ubuntu from Windows, one of my first tasks was to install the famous AVG to 'protect' myself from viruses. Before long, I found out that Linux is fairly well immune to viruses and the reasoning behind them.

Now I never install AV, and disapprove of those who do, on Linux boxes. It's such a waste of time and resources. If I was running a corporate mailserver, then I would probably run an antivirus seeing how I would have users from every type of platform receiving infected attachments. But any other situation, there is absolutely no need.


If you are afraid of infecting Windows with a virus you downloaded on Linux and transferred to Windows, use antivirus on Windows; not Linux. If you friends use Windows, let them use their antivirus to scan files that you send them, if they care to protect themselves. I can not be held responsible for a infected file that I passed onto a friend, if the receiver doesn't protect himself. It's that simple.

Let Windows users run antivirus to 'protect' themselves, and let Linux users not run antivirus as it isn't necessary.

---

### Post by cardinals_fan on 2009-01-31
> **overlord.gaurav said:**
> Look. I have Norton 360, V2.0 installed on my Laptop. I've seen many viruses getting uploaded to my laptop. By the time the anti-virus warns me about it, my computer is already infected. Whereas, when I connect it to me desktop running on Linux, I can very easily see the unwanted .exe files, as well as scan for viruses which are patched to certain known files as well.

This is the best I can do to convince you on the fact that antivirus on Linux does help, depending on the reason you install it with.
This is why signature-based antivirus apps are worthless for daily use.  Use something heuristics-based like ThreatFire, which scans for malevolent behavior.  No outdated definitions, no resource-hungry scans, no fuss.  And above all else, use a limited account and common sense.

---

### Post by yabbadabbadont on 2009-02-01
> **cardinals_fan said:**
> And above all else, use ... common sense.

The problem is that common sense isn't.  (common that is ;))

---

