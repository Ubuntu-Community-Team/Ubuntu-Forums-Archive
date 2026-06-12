---
title: "Linux users protecting Windows users?"
date: 2008-08-26
forum: Recurring Discussions
---

### Post by darrelljon on 2008-08-26
Most security advice I read seems to suggest running antivirus software on Ubuntu to protect Windows users. Why is this the conventional wisdom? Why should Linux users protect Windows users from viruses by scanning attachments with antivirus software? It uses up the time and resources of Linux users to protect Windows users who continue to use an insecure operating system. You could even argue it prolongs the Windows monopoly.

---

### Post by .nedberg on 2008-08-26
Well, I do not want to be guilty of sending a file with a virus to any of my friends... No matter what OS they run...

---

### Post by insane_alien on 2008-08-26
because i would hope that most users of linux(or any other operating system):

1/ are considerate enough to help those who either don't know any better or have no choice.

2/ despise the writers of malware enough to combat the propagation of malware as much as they can.

3/ aren't smug prats that go around trying to push linux onto everyone whether they want it or not.

---

### Post by fiddledd on 2008-08-26
I agree with the previous posts, but not the OP.

---

### Post by xravexheavenx on 2008-08-26
I agree with Insane.  Most people do not know any better.  And, a LOT of people dual-boot.  My main machines and work machine are running Ubuntu but I DO have a dual-boot on my work laptop in case I need it at all and an external for booting WinBlows if I need to.  I only boot it to use Adobe products and Delphi for work on a rare occasion.  A LOT of mainstream users do not know *nix even exists.  We shouldn't be against them for their lack of knowledge.

---

### Post by ilrudie on 2008-08-26
If you run an OS with many, many viruses in the wild and you don't run anti-virus linux users not virus scanning is the least of your worries. Just my opinion.

---

### Post by Anzan on 2008-08-26
I don't run anti-virus because I don't send anything to anyone that isn't running Linux or at least that I know has anti-malware running (except for windows itself). Otherwise I certainly would.

---

### Post by cmat on 2008-08-26
It's everyone's duty to stop the spread of malicious code. If linux ever gains market share you bet there will be viruses in the wild.

---

### Post by karellen on 2008-08-26
it's like saying why not crash people that drive minis with a SUV because they refuse to drive it as you do

---

### Post by insane_alien on 2008-08-26
> If linux ever gains market share you bet there will be viruses in the wild.

it has the majority share in servers. servers are prize targets for hackers.

---

### Post by cmat on 2008-08-26
> **insane_alien said:**
> it has the majority share in servers. servers are prize targets for hackers.

servers are not administered by people's grandmothers.

---

### Post by ilrudie on 2008-08-26
> **cmat said:**
> It's everyone's duty to stop the spread of malicious code. If linux ever gains market share you bet there will be viruses in the wild.

I agree to a certain point.  I'd say its everyones responsibility to protect themselves and this makes everyone around them safer.  For me this means running Linux which effectively means I'm not infected with a virus spewing and spamming viruses everywhere.  When I am unfortunate enough to run Windows I run anti-virus/malware.  It is the responsible thing to do on Windows not because (ideally) it prevents me from emailing a virus to a few other people but because (ideally) it prevents me from becoming a spam bot and spreading viruses to tons of people.  Its really those who chose not to protect themselves that are the problem.

ATM I email through gmail which I believe virus scans all my attachments making running anti-virus on my Linux box even more of a waste.

I also think that if/when there are Linux viruses in the wild it will be time for me (and the Linux community at large) to bite the bullet and run anti-virus or switch to an even more security minded distro or OS.

---

### Post by insane_alien on 2008-08-26
> **cmat said:**
> servers are not administered by people's grandmothers.

no, but they are high priority targets for a lot of hackers as they tend to have more important data than someones grandmothers holiday snaps.

[quote=ilrudie]I agree to a certain point. I'd say its everyones responsibility to protect themselves and this makes everyone around them safer. For me this means running Linux which effectively means I'm not infected with a virus spewing and spamming viruses everywhere. When I am unfortunate enough to run Windows I run anti-virus/malware. It is the responsible thing to do on Windows not because (ideally) it prevents me from emailing a virus to a few other people but because (ideally) it prevents me from becoming a spam bot and spreading viruses to tons of people. Its really those who chose not to protect themselves that are the problem.

ATM I email through gmail which I believe virus scans all my attachments making running anti-virus on my Linux box even more of a waste.

I also think that if/when there are Linux viruses in the wild it will be time for me (and the Linux community at large) to bite the bullet and run anti-virus or switch to an even more security minded distro or OS.[/quote]

surely as we are aware of the problem and the threat to those that are unaware we have a responsibility to be more active in the prevention of malware than just securing our own systems.

---

### Post by CoryMathews on 2008-08-26
I cannot believe you even asked this question. Get over yourself... linux is something like less then 4% of the desktop world. Of course you should check for virus' that effect other os's.

---

### Post by aysiu on 2008-08-26
This post pretty much sums up my opinion on the matter: > **RequinB4 said:**
> I think one thing that there are two things that haven't been mentioned.

First, anti-virus is not really anti-virus - it is virus-checking.  AV works (for 99.999% of the time, there are exceptions) by comparing files or parts of files to known patterns of virus interaction.  Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.

Second, there is the beleif that we should run AV to protect those we contact via the internet getting infected.  Assuming we're not talking about a mail or SAMBA server or something, let's think about this for a second - what are the possible outcomes?

1)  Linux box doesn't get a virus.  No problem.

2)  Linux box gets a virus, and doesn't transmit it.  No harm done, maybe a few wasted bytes of space.

3)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box has equivalent or better anti-virus.  They don't get infected, so no harm done.

4)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box doesn't have antivirus or it fails to detect.  Windows user is very sad.

So, let's examine 4.  Since the box doesn't have antivirus, and has an open connection to the internet, and (for the sake of argument) is running unsafe applications such as IE or Outlook, its security is already very low.  In fact, it's far, far, far more likely that they get the virus not from  you but from normal browsing or from ANOTHER windows box which is ACTIVELY propagating the virus.  Add the fact that the probability of 1, 2, and 3 is also MUCH higher than 4, and you begin to see my point.

So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable? If we want to protect Windows users, we should tell them to use SuRun instead of running as administrator all the time. That is far better than us running antivirus on Linux machines.

P.S. I never forward attachments from my Ubuntu computer. Every single attachment I send via my home computer is a file I've created myself, so it would not have a Windows virus on it.

---

### Post by doas777 on 2008-08-26
heres the way i see it. just my two bits

a large portion of the linux deployed-base is in servers, mostly providing services that clients can cosume (and most are windows clients).

now if your server is inside your network (of wintel clients) then it is your responsiblity to make sure that your network is as close to clean as possible. lets say the server is your mail server or your intranet web server. wouldn't you rather not infect all the clients? remember that you (or your colleagues) would be the one(s) who had to clean them up. not performing intense scanning on your email server is tantamount to suicide on the career ladder.

or you pass on an email to a distro list full of friends. would you want to get a bunch of angry emails from them complaining that all their files are now gone?

and lets say someone comes up with a good trojan for *nix. something tells me that the guys at clam have heard about it before I have.

---

### Post by aysiu on 2008-08-26
> **doas777 said:**
> heres the way i see it. just my two bits

a large portion of the linux deployed-base is in servers, mostly providing services that clients can cosume (and most are windows clients).

now if your server is inside your network (of wintel clients) then it is your responsiblity to make sure that your network is as close to clean as possible. lets say the server is your mail server or your intranet web server. wouldn't you rather not infect all the clients? remember that you (or your colleagues) would be the one(s) who had to clean them up. not performing intense scanning on your email server is tantamount to suicide on the career ladder.

or you pass on an email to a distro list full of friends. would you want to get a bunch of angry emails from them complaining that all their files are now gone?

and lets say someone comes up with a good trojan for *nix. something tells me that the guys at clam have heard about it before I have.
I'm sorry. I thought we were talking about antivirus for home users of Linux.

If you're running a Linux mail server, it'll almost certainly be used by a lot of Windows clients, and you do not want to be responsible for their propagating viruses via your server.

---

### Post by cardinals_fan on 2008-08-26
> **insane_alien said:**
> no, but they are high priority targets for a lot of hackers as they tend to have more important data than someones grandmothers holiday snaps.

But most server admins won't fall for "Free Awesome Wallpapers!".

---

### Post by ilrudie on 2008-08-26
> **insane_alien said:**
> surely as we are aware of the problem and the threat to those that are unaware we have a responsibility to be more active in the prevention of malware than just securing our own systems.

I don't know about that.  Just because some people don't have air bags or wear their seat belt I don't really feel I should cover my car in big squishy balloons so that if there is an accident they don't get hurt.  Even if I cover my car with the biggest squishiest balloons ever developed that are 100% effective in preventing injury 100% of the time someone else is just as likely to hit them and injure them.  Its really your problem if you choose not to protect your self.  Wouldn't it be better to try to inform the uninformed so they can protect themselves from everyone rather than going out of our way to protect them just from us?

---

### Post by karellen on 2008-08-27
> **ilrudie said:**
> I don't know about that.  Just because some people don't have air bags or wear their seat belt I don't really feel I should cover my car in big squishy balloons so that if there is an accident they don't get hurt.  Even if I cover my car with the biggest squishiest balloons ever developed that are 100% effective in preventing injury 100% of the time someone else is just as likely to hit them and injure them.  Its really your problem if you choose not to protect your self.  Wouldn't it be better to try to inform the uninformed so they can protect themselves from everyone rather than going out of our way to protect them just from us?

you forget that some viruses pass the antivirus program Windows users run. and I really don't get the logic "let's not prevent hurting someone because someone else would do it anyway" :confused:

---

### Post by imT on 2008-08-27
i don't care, if they use windows they should have protection,
why should i bother protecting them when they don't bother protecting them self...

---

### Post by worx101 on 2008-08-27
I protect them by not forwarding attachments in the first place...

But then again, I don't baby Windows users, if they refuse to use an anti-virus program then I am not going to scan everything for them.

---

### Post by ilrudie on 2008-08-27
> **karellen said:**
> and I really don't get the logic "let's not prevent hurting someone because someone else would do it anyway" :confused:

Its pretty simple actually.  I'm not going to go out of my way and scan for viruses when the likelihood that I give them a virus is insignificant compared to the likelihood that another windows user without anti-virus will give it to them.  I am a strong link in the chain.  I use Linux.  I don't forward attachments.  Making my link an infinitesimal amount stronger by scanning for viruses does not make the internet a safer place for windows users who chose not to use anti-virus or are not informed enough to do so.

---

### Post by sephiroth2212 on 2008-08-27
I see it much more selfishly :D I wouldn't run anti-virus and scan everything to protect linux, because if developers start developing like they do for windows and figure an anti-virus program will solve their security issues they produce bad software. So lets all help to keep linux developers keep an eye on the security of their products and not use anti-virus to protect windows users. In a way I guess natural selection also exists for operating systems :D

---

### Post by karellen on 2008-08-27
> **ilrudie said:**
> Its pretty simple actually.  I'm not going to go out of my way and scan for viruses when the likelihood that I give them a virus is insignificant compared to the likelihood that another windows user without anti-virus will give it to them.  I am a strong link in the chain.  I use Linux.  I don't forward attachments.  Making my link in the an infinitesimal amount stronger by scanning for viruses does not make the internet a safer place for windows users who chose not to use anti-virus or are not informed enough to do so.

if you put things into this perspective, I agree

---

### Post by bmac on 2008-08-30
One thing to consider, is where the infected link/file/whatever originated from. I'm fairly certain it wasn't my system. Why then am I responsible to scan for garbage when the individuals I'm forwarding to don't or refuse to protect themselves? I tend to agree with [sephiroth2212]("http://ubuntuforums.org/member.php?u=652249") regarding natural selection of an OS. 

These same individuals transfer files and links on a regular basis and the odds of infection/corruption increase every time. I can't count how many times I've assisted family members in cleaning up their Windows PC (viruses, corrupted registry, maleware, ect.) just to be called a few days or weeks later and notified that their system's performance is again in the toilet. Every one of them had similar excuses as to why their system was disfunctional. For example:
"If I run that protection program or firewall my Fantasy Football won't work right".
"I can't get access to all the stuff on certain sites, when leaving the protection on".
Etc,Etc,Etc.....

 When we ran Windows (started with 3.1 to XP) all our systems were protected (including firewalls) and all users were under a threat of physical impairment, should they even consider turning off the protection....

Sorry, I guess my attitude has just harden and I am no longer very sympathetic...:wink:

---

### Post by Liviu-Theodor on 2008-10-06
In some cases, I will say yes, in others, I will say no.

The cases with yes involve a linux server with Windows clients.
The cases with no are the rest. Why that?

I have seen a case where a new computer came preinstalled with kiwi linux (which is ubuntu localized for my country). The kids didn't like it (because it was not Windows), although their father did liked it. But they managed somehow to install a so-called pirated copy of Windows Vista instead, and it got virused in less than two weeks, even though they were smart enough to install an antivirus.

They asked me to get out the viruses, after I told them the advantages of using Linux, and the dangers of uisng Windows online (of course, I compared Linux and Windows correctly, with advantages and disadvantages of each one). Honestly, I think this is the job of the one who installed them Vista and have not told them how to use it safe (it is possible?) and the dangers for doing this.

---

