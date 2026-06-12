---
title: "Ubuntu antivirus"
date: 2008-06-04
forum: Recurring Discussions
---

### Post by adobrakic on 2008-06-04
I'm sick of hearing "you can't get a virus on linux." Gets really irritating after the 1000th time. With that said, **please** don't reply to this thread by insisting on I can't get a virus. If you're going to, just close this thread now. Anyway..
What's a good antivirus for ubuntu? I've tried ClamTK, but when i input clamscan in command, nothing opens. Neverthless if i did have it working, i like testing out different kinds of AVs. So what are some other good ones?
Thanks.

---

### Post by starcannon on 2008-06-04
AVG has a linux client

[http://free.grisoft.com/ww.download?prd=afl](http://free.grisoft.com/ww.download?prd=afl)

oh and you can't... nm hehehe... sorry couldn't resist

---

### Post by adobrakic on 2008-06-04
lmao, you ***. jk. :p
thanks for the suggestion.

---

### Post by SunnyRabbiera on 2008-06-04
What is cotton in your ears or something?
Why do you want antivirus for you linux system anyway?
You are just too paranoid, I know under windows you are used to it, worrying about the littlest thing infecting yours system.
But Ubuntu and linux takes that worry away, there are no viruses that can effect you, how hard is that to understand?

---

### Post by lisati on 2008-06-04
AV isn't really needed for Linux, unless you're worried about passing one on to a Windows machine that you're in contact with.

AVG has a scanner that you can use with Linux - you can get it from [here]("http://free.grisoft.com") - but you'll have to add the user who will be running it to the "avg" group in order for the updates to work properly from the GUI.

---

### Post by sam_delta on 2008-06-04
ive heard of clamAV, duno if its the same package as ClamTK but it might be worth checking it

sam

---

### Post by adobrakic on 2008-06-04
> What is cotton in your ears or something?
Why do you want antivirus for you linux system anyway?
You are just too paranoid, I know under windows you are used to it, worrying about the littlest thing infecting yours system.
But Ubuntu and linux takes that worry away, there are no viruses that can effect you, how hard is that to understand?

I'm sensing a bit of sarcasm, heh. Hopefully it is.

> 
ive heard of clamAV, duno if its the same package as ClamTK but it might be worth checking it

sam


Yeah it is, thanks for your time though. :D

---

### Post by starcannon on 2008-06-04
ears another one from panda soft, I used them quite a bit back when I was into winders.

[http://www.pandasoftware.com/download/linux/linux.asp](http://www.pandasoftware.com/download/linux/linux.asp)

Oh yeah and don't forget Avast

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

that should be enough to wet yer whistle.

---

### Post by SunnyRabbiera on 2008-06-04
> **adobrakic said:**
> I'm sensing a bit of sarcasm, heh. Hopefully it is.



Yeah it is, thanks for your time though. :D

well yes I can be sarcastic, but really there is nothing out there that will harm you using Ubuntu unless you have root permissions.
The virus scanners for linux are more for WINDOWS partitions and even wine, they help but they wont fend off linux viruses.
BUT the viruses that DO exist for linux need root access, and in ubuntu this is disabled or in short: THEY WONT WORK unless you have a root account.
Really I know that it must be insane to have a secure OS that has little issues coming from a OS that is more bug ridden then a colony of ants but its true... Linux is practically bulletproof to a majority of issues facing windows, and if you are smart any issues it does have can be avoided.

---

### Post by superzorro on 2008-06-04
I think clamAV it's a good option. In order to open it:

```
user@user-desktop:~$clamtk 
```

And to update the virus signatures you must run it as root, however I think it's updated through the normal update manager.

You could also use F-Prot or Karspersky, however they aren't free.

---

### Post by SunnyRabbiera on 2008-06-04
A better front end if you ask me is Klam, but really its pointless unless you have windows drives.

---

### Post by Bri0 on 2008-06-04
[http://www.techthrob.com/tech/linuxav.php]("http://www.techthrob.com/tech/linuxav.php")

---

### Post by adobrakic on 2008-06-04
> 
well yes I can be sarcastic, but really there is nothing out there that will harm you using Ubuntu unless you have root permissions.
The virus scanners for linux are more for WINDOWS partitions and even wine, they help but they wont fend off linux viruses.
BUT the viruses that DO exist for linux need root access, and in ubuntu this is disabled or in short: THEY WONT WORK unless you have a root account.
Really I know that it must be insane to have a secure OS that has little issues coming from a OS that is more bug ridden then a colony of ants but its true... Linux is practically bulletproof to a majority of issues facing windows, and if you are smart any issues it does have can be avoided.


I understand this, but i don't get the wine part. Doesn't the Wine community actually need to program the virus into wine for it to be able to even run? And I don't understand why you would need a AV on linux for windows virii, if linux can't even run windows files. 
All in all, i'd just rather be safe than sorry. I know it's close to impossible to get a virus on linux, but it's not like it's such a big hassle to get an antivirus.

> 
And to update the virus signatures you must run it as root, however I think it's updated through the normal update manager.

You could also use F-Prot or Karspersky, however they aren't free


Yeah, i think ClamTk is my favorite so far.

---

### Post by SunnyRabbiera on 2008-06-04
> **adobrakic said:**
> I understand this, but i don't get the wine part. Doesn't the Wine community actually need to program the virus into wine for it to be able to even run? And I don't understand why you would need a AV on linux for windows virii, if linux can't even run windows files. 
All in all, i'd just rather be safe than sorry. I know it's close to impossible to get a virus on linux, but it's not like it's such a big hassle to get an antivirus.

Well using antivirus for wine is a good idea so that the windows app does not get effected... but it wont effect the rest of the OS.
But your "better safe then sorry" stance is not needed under linux, like I understand i can understand your paranoia but it is unfounded.

---

### Post by Paqman on 2008-06-04
Well, we could just recommend some random Linux AV clients, but that's a bit pointless without knowing what it is you want it for.

If you're just running a desktop system, then the advice you've been given is correct, you don't need one. At all.

If you're operating a mail server then it might be good manners to scan mail before shifting it on. But if that's the case then you could be running headless, so suggesting a client with a GUI is pointless.

If you're running a web-facing server then you definitely DO need to take precautions against malware, but that's a whole separate field.

So the bottom line is: what are you using the machine for? We can't tell you what you need unless you tell us this.

---

### Post by cariboo on 2008-06-04
:)I've been playing with Linux since 1998, and using it as my main system since 2000. I've never had a virus yet. I even used to play with windows viruses when they came attached to emails.:)

Never felt the need for an av program. Now if you are running a mail server and windows user access it all bets are off.

Jim

---

### Post by wdaniels on 2008-06-04
[Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html") has a linux version, but I've never tried it myself (or any other). Obviously it is entirely *possible* to get viruses on Linux - I seem to recall there was a Windows one once that ran perfectly through Wine, and there are even a handful of native ones, but they are so uncommon (and generally unsuccessful given the highly varied nature of linux systems) that an AV scanner seems unlikely to provide any real defense.

A Linux virus that became sufficiently prolific to turn up on an AV developer's radar would surely have come to the attention of Ubuntu/upstream developers even sooner. Essentially, the normal security updates from Ubuntu are your best anti-virus in Linux. The main use for AV scanners in Linux is to scan for Windows viruses on a Linux mail server, or on a Windows file share.

I can fully understand that you don't want to be told that "linux is just so great that you can't get any virus ever", but ultimately it's not just stupid "fanboy" talk, it's *effectively* the reality of the matter, at this point in time.

---

### Post by roaldz on 2008-06-04
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

the list is just too short..

---

### Post by cacycleworks on 2008-06-04
FYI, if any computer in a workplace doesn't have AV software actively running, they are not PCI compliant and the workplace cannot have access to consumer credit cards.

Obviously, this "rule" has windblows inoperative system in mind but I'm glad to see this thread so I can install this and tick the box saying we've got it...

(insert eye rolly icon)

Cheerios,
Chris

---

### Post by hyper_ch on 2008-06-04
Well, AV on linux is not needed. There are exceptions if you want to make sure fellow windoze users don't have problems.

Running viruses in wine: Someone tried it with a few viruses and most just refused to work at all... there was only one virus which just used all the CPU but didn't do any damage besides that. So even with wine you don't really need an AV.

The situation is different if you run windoze in a VM. There you need one (for windows).

---

### Post by billgoldberg on 2008-06-04
I don't run any anti-virus on linux.

I have no windows machines on my network, so I don't have to bother about that.

I do share the occasional file with windows users (through msn or flash disk) but I don't have to take care of their security issues.

---

### Post by wdaniels on 2008-06-04
> **adobrakic said:**
> I understand this, but i don't get the wine part. Doesn't the Wine community actually need to program the virus into wine for it to be able to even run?

Yes, but to get a lot of Windows programs to run, you have to have the same bugs there that it expects to exist in real Windows. So Wine has to implement "bug for bug" compatibility with Windows. Not a nice policy, but mostly unavoidable without defeating the whole purpose of the project.

---

### Post by Primefalcon on 2008-06-04
> **SunnyRabbiera said:**
> What is cotton in your ears or something?
Why do you want antivirus for you linux system anyway?
You are just too paranoid, I know under windows you are used to it, worrying about the littlest thing infecting yours system.
But Ubuntu and linux takes that worry away, there are no viruses that can effect you, how hard is that to understand?

Even if Linux is virus free, we do pass on emails and whatnot, I know people who run Windows and I don't know if you don't care about your friends and family, but I do and I don't want to send them a virus.

for even if linux is immune it can still send them on and cripple the windows systems of people

---

### Post by cjm5229 on 2008-06-04
Avast  works well, is easy to install and is free. Avg works but is more difficult to set up. I had Avast find a virus in my Windows partition that I couldn't detect from Windows while it was operating:). There are also a couple of pretty good ClamAV front ends in  Synaptic. or Add/Remove, look for "Virus Scanner".

---

### Post by lisati on 2008-06-04
> **primefalcon said:**
> even If Linux Is Virus Free, We Do Pass On Emails And Whatnot, I Know People Who Run Windows And I Don't Know If You Don't Care About Your Friends And Family, But I Do And I Don't Want To Send Them A Virus.

For Even If Linux Is Immune It Can Still Send Them On And Cripple The Windows Systems Of People

+1

---

### Post by davidsrsb on 2008-06-04
Another valid reason for an anti-virus scanner is running Samba server.

---

### Post by sayakb on 2008-06-04
Ok, let me put it this way. I live in a hostel of 1400 students. We connect to a local server through the LAN and all 1400 of us are under the same subnet. File sharing is enabled on **each** PC, and **each** PC has atleast one of Passma, Small.I or and some virus that makes Powerpoint.exe file in all folders. I have NO ANTIVIRUS and I access the shares **daily**. I can literally "see" the virus executables (in some RECYCLER folder or some Autorun info file -- autorun.inf pointing to some executable). They never **infect** my PC. Anyway, if you want an antivirus anyway, go for Avast (links provided in previous posts). It has a good GUI. Invoke it using:
```
avastgui
```

---

### Post by ardvark71 on 2008-06-04
Hi...

I've used Avira (AntiVir for Linux desktops) in the past, it seemed to work OK, although I'm not sure if they still offer the free version. :roll:

Best Regards...

---

### Post by hyper_ch on 2008-06-04
> **Primefalcon said:**
> for even if linux is immune it can still send them on and cripple the windows systems of people

Well, when their systems get crippled again just tell them you don't have those worries. I don't see it as my job to "protect" windows users from viruses. They should do that themselves.

---

### Post by sayakb on 2008-06-04
But I don't understand. I don't think that a virus on Wine can even harm the system. We don't run it as superuser, so it can't do much I guess. So there's no way the Ubuntu gets infected. And as far as Windows boxes are concerned, +1 to what hyper_ch said:

> **hyper_ch said:**
> I don't see it as my job to "protect" windows users from viruses. They should do that themselves.

---

### Post by lisati on 2008-06-04
> **hyper_ch said:**
> Well, when their systems get crippled again just tell them you don't have those worries. I don't see it as my job to "protect" windows users from viruses. They should do that themselves.

True, you aren't obliged to protect other people's machines, but not taking precautions to prevent passing on viruses could put some people at risk of being in violation of their email provider's TOS: Have a look at the "Member conduct" section [_here_]("http://nz.docs.yahoo.com/info/terms/")

---

### Post by SunnyRabbiera on 2008-06-04
> **hyper_ch said:**
> Well, when their systems get crippled again just tell them you don't have those worries. I don't see it as my job to "protect" windows users from viruses. They should do that themselves.

Well me I do run AV for emails sometimes, especially when passing on mail to my relatives.

---

### Post by Paqman on 2008-06-04
> **hyper_ch said:**
> I don't see it as my job to "protect" windows users from viruses. They should do that themselves.

I agree. Even if a Linux user passes a Windows virus to a Windows user, their Windows antivirus will protect them.

I can understand that running desktop Linux in a corporate environment might be different. Passing on malware to clients or customers would be unprofessional. But for personal use there's no sense in putting the bandages on the patient who isn't bleeding.

---

### Post by ByteJuggler on 2008-06-04
> **SunnyRabbiera said:**
> well yes I can be sarcastic, but really there is nothing out there that will harm you using Ubuntu unless you have root permissions.
The virus scanners for linux are more for WINDOWS partitions and even wine, they help but they wont fend off linux viruses.
BUT the viruses that DO exist for linux need root access, and in ubuntu this is disabled or in short: THEY WONT WORK unless you have a root account.
Really I know that it must be insane to have a secure OS that has little issues coming from a OS that is more bug ridden then a colony of ants but its true... Linux is practically bulletproof to a majority of issues facing windows, and if you are smart any issues it does have can be avoided.

+10.  Just to reiterate and add emphasis:  ***There are in reality literally no successful linux viruses (meaning which propagate successfully) in the wild.***  Most "linux viruses" that do exist, are proof-of-concept oddities that cannot spread unless systems are deliberately hobbled to help them.  

Maybe you'll believe [this article]("http://nnucomputerwhiz.com/linux-virus.html"), if you don't want to believe us.

---

### Post by insane_alien on 2008-06-04
i use an AV extensively on linux, though its for cleaning out windows drives. i fix peoples computers for them(occasionally switch them to linux if its going to be simple(ie they just surf the web and do email). i've rescued many an unbootable windows with clamAV, t'interwebs and a cup of cafeinne enriched coffee.

---

### Post by Primefalcon on 2008-06-04
oh cut out the eliteism, we all know linux is not the virus danger windows is.

but do you think it'd encourage others to swithc to linux if they see the linux users sending viruses on?

---

### Post by roaldz on 2008-06-04
> **Primefalcon said:**
> oh cut out the eliteism, we all know linux is not the virus danger windows is.

but do you think it'd encourage others to swithc to linux if they see the linux users sending viruses on?

It´s more likely a windows user passes on a virus, because the virus takes care about passing it on, and linux users (don´t quote me on this) are somewhat more aware of what they are doing than windows users. A virus doesn´t ¨slip through¨ that simple. Don´t see this black on white, but I´ll guess you know what I mean.
See it this way: Would it encourage a windows user to move to linux if he sees linux doesn´t send virussus in emails? I think it doesn´t.

---

### Post by Primefalcon on 2008-06-05
I know what your saying personally I am just not the sort to pass on a virus (cool email attachment) to my friend saying if their computer blows up, not my problem.

---

### Post by lisati on 2008-06-05
> **Primefalcon said:**
> I know what your saying personally I am just not the sort to pass on a virus (cool email attachment) to my friend saying if their computer blows up, not my problem.

+1

I think most of us here, regardless of where we stand on the level of extra protection needed, are like that.

---

### Post by hyper_ch on 2008-06-06
> **lisati said:**
> +1

I think most of us here, regardless of where we stand on the level of extra protection needed, are like that.
[irony on]
You mean you don't forward the latest virus-infected windows screensaver to all the people in your addressbook? :confused:
[/irony off]

---

### Post by lisati on 2008-06-06
> **hyper_ch said:**
> [irony on]
You mean you don't forward the latest virus-infected windows screensaver to all the people in your addressbook? :confused:
[/irony off]

<borg voice>Resistance is futile</borg voice>
Edit: It could have been my neighbour AFTER I removed his NT machine's MAC address from our wireless router. He wasn't too happy about being disconnected

:lolflag:

---

### Post by VitalBodies on 2008-06-18
Can one run ClamTk to check their email (like old email from their Windows days) and check all the files? 

When I run the program it say something like **Files Numbers Limit Exceeded**. 
So for the inbox it will say 1 virus found Files Numbers Limit Exceeded. 

In my Windows days Clamwin did not give such messages?

---

### Post by valjour on 2008-06-18
Hi-

I haven't ever had a virus since i gave up on Clam and switched to Avast.  I use it for protection of others and see if I have made any errors as I find my way into the Ubuntu world. 

An AV may be unnecessary but it does not hurt as we interact with the microsludge many.  Remember we are but the few even though our numbers are increasing. My usage has prompted at least 6 local users to at least try Ubuntu out for a drive.  :)

What about dual-boot machines? Of which I am not.  I like to keep them completely separated.

Pete

---

### Post by hyper_ch on 2008-06-18
> **valjour said:**
> Remember we are but the few even though our numbers are increasing
And this means?

---

### Post by valjour on 2008-06-19
Hi Hyper CH,

This means that the more of us that there will be less viruses going around.  I believe that we respect each other and linux users are working together to make the computer world better safer place.  Other users lack the comprehension of how much work goes into "freedom" as 'money' attempts to push the world around and make us compliant drones (mindless users)that get sucked dry to get needs met and keep the world fear based.  The reason I believe viruses began, a counter to an outdated philosophy.  We are the future...educated sharers looking for advancement and enrichment.

Good to hear from you my friend,  thanks for your help and support.

As an aside I had been having trouble with Hardy's update manager when the new .. ".19" kernel came out. Lots of failed updates and error messages.  I was away for about a month. I used <apt-get dist-upgrade> in the terminal and all is well in Ubuntu Hardyland and update manager works well again. It actually is preferable to work through the terminal because there are questions to answer along the updates way... 

Pete

---

### Post by RequinB4 on 2008-06-19
I think one thing that there are two things that haven't been mentioned.

First, anti-virus is not really anti-virus - it is virus-checking.  AV works (for 99.999% of the time, there are exceptions) by comparing files or parts of files to known patterns of virus interaction.  Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.

Second, there is the beleif that we should run AV to protect those we contact via the internet getting infected.  Assuming we're not talking about a mail or SAMBA server or something, let's think about this for a second - what are the possible outcomes?

1)  Linux box doesn't get a virus.  No problem.

2)  Linux box gets a virus, and doesn't transmit it.  No harm done, maybe a few wasted bytes of space.

3)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box has equivalent or better anti-virus.  They don't get infected, so no harm done.

4)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box doesn't have antivirus or it fails to detect.  Windows user is very sad.

So, let's examine 4.  Since the box doesn't have antivirus, and has an open connection to the internet, and (for the sake of argument) is running unsafe applications such as IE or Outlook, its security is already very low.  In fact, it's far, far, far more likely that they get the virus not from  you but from normal browsing or from ANOTHER windows box which is ACTIVELY propagating the virus.  Add the fact that the probability of 1, 2, and 3 is also MUCH higher than 4, and you begin to see my point.

So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable?

---

### Post by BwackNinja on 2008-06-19
Because a picture is worth a thousand words, and xkcd is the best web comic ever....

[http://xkcd.com/272/](http://xkcd.com/272/)

and yes, all linux users can do backflips

---

### Post by kansasnoob on 2008-06-19
Since I never send important info by email anyway I just use Yahoo Mail which checks to see if I'm sending my Windows friends something that might break their fragile systems so I feel vindicated!

---

### Post by anewguy on 2008-06-19
> **SunnyRabbiera said:**
> well yes I can be sarcastic, but really there is nothing out there that will harm you using Ubuntu unless you have root permissions.
The virus scanners for linux are more for WINDOWS partitions and even wine, they help but they wont fend off linux viruses.
BUT the viruses that DO exist for linux need root access, and in ubuntu this is disabled or in short: THEY WONT WORK unless you have a root account.
Really I know that it must be insane to have a secure OS that has little issues coming from a OS that is more bug ridden then a colony of ants but its true... Linux is practically bulletproof to a majority of issues facing windows, and if you are smart any issues it does have can be avoided.


While I can appreciate what you are saying, "practically bulletproof" is not completely bulletproof.  I can guarantee you the more people who use Linux, the more viruses there will be.  There already are some, as you mentioned.  Do they all need root access - I'm not so sure.  My feelings in this matter has always been (comes from 23 years of systems programming and systems administration experience) NOTHING is bulletproof.  With that said, there is nothing wrong with people running an anti-virus application in Linux.  Some would say it is rarely needed - but rarely leaves a hole that I am not willing to have.

It is very true that Linux is built so differently from Windows that the horror stories from viruses on Windows is nearly impossible in Linux - particularly things like buffer overruns which allow a process in.  The various internal layers of Linux are so different it is nearly impossible.  So, hoping you don't mind (because I really do respect what you have said!), my personal belief is that you can never be too safe.  However, do not think you will have the same type of virus problems in Linux as in Windows - they are so different that some of those things are impossible.  My main reason for running anti-virus in Linux is not to protect me, but rather to protect others whom I may be in IM or email contact with who do not run Linux but instead run Windows.  While they should be responsible for their own computer, I feel it is a "good computer users'" responsibility to also not pass along a virus.  With no checking, it possible to pass along a Windows virus to another Windows user and not know it.  Not many of them, but some.

So, when someone asks, I tell them it may not be needed currently in Linux for Linux's sake, but is a good idea to stop the potential of spreading a Windows virus via email, etc..

Just my opinion obviously!

---

### Post by jrusso2 on 2008-06-19
Well its kind of pointless if  you worried about Linux virii, all the antivirus programs for Linux just detect Windows virus so if there was a Linux one that came out your avg, avast, bitdenfender probably would not find it anyway.

---

### Post by hyper_ch on 2008-06-20
> **anewguy said:**
> I can guarantee you the more people who use Linux, the more viruses there will be.
You guarantee wrongly... Numbers of base installs have no direct correlations to numbers of malware on a plattform.

> **anewguy said:**
> With that said, there is nothing wrong with people running an anti-virus application in Linux. Some would say it is rarely needed - but rarely leaves a hole that I am not willing to have.
It is because all the AV for linux don't scan for any linux virus... so you are wasting your space and your ram and your cpu for something that does nothing to protect your system...

> **anewguy said:**
> My main reason for running anti-virus in Linux is not to protect me, but rather to protect others whom I may be in IM or email contact with who do not run Linux but instead run Windows.  While they should be responsible for their own computer, I feel it is a "good computer users'" responsibility to also not pass along a virus.
Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.
Rather tell them how to protect themselves instead of cleaning up the mess all the time ;)

---

### Post by valjour on 2008-06-20
Thanks RequinB4 for the wisdom



> **RequinB4 said:**
> I think one thing that there are two things that haven't been mentioned.

Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.


So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable?

I hope I did not come off as being cocky.  I hope that we remain fairly safe but there are destructive types everywhere.  I am just extremely optimistic and hopeful that we continue with the great track record.  I do know we have to be careful of the advice we listen to.  I think it is common courtesy to check our mail and files regularly.  Running Ubuntu Linux that's about once a month for me rather than twice a day when I was on the microsludge surf.

Pete

---

### Post by valjour on 2008-06-20
Hyper CH,

My surf habits are quite different these days that I have grown up and know what not to do and avoid surfing with sharks in the water. Linux and learning keep me busy enough most of the time.

Avast only runs when I ask it to, once a month update and scan.  Is this really a waste of time and energy?

Sorry I didn't use quotes back.  Getting used to posting too. Last post was first using quotes. A little slow for me as of yet.

Pete, a new guy that hangs in there and keeps on learning

---

### Post by gn2 on 2008-06-20
> **valjour said:**
> 
Avast only runs when I ask it to, once a month update and scan.  Is this really a waste of time and energy?

Yes, it's a complete and total waste of your time and electricity.

---

### Post by anewguy on 2008-06-21
> **hyper_ch said:**
> You guarantee wrongly... Numbers of base installs have no direct correlations to numbers of malware on a plattform.

Let's see - if the installed base was reversed, Windows desktops versus Linux desktops, do you seriously believe malware producers would "waste their time" with Windows instead of going after the larger installed base?  Seriously, there is a big flaw in your thought here.  Windows has generated so many attacks not because it is vunerable (which it undoubtably is), but because it is the largest installed base.  There are holes in any product, the amount of effort it takes to exploit them is directly related to the potential return.  There ARE holes in Linux/Unix - the amount of effort it takes to exploit them is not worth it at this time because of 2 things:

(1) The installed base of home user Linux installations can not generate the huge potential on return as the large installed Windows base.

(2) With the syntax in Linux versus Windows, finding such things as passwords, cc numbers, etc., is not an easy task in Linux compared to Windows.  If the installed base was large enough, the effort would be made.

There is one other thing I want to mention here for debate (after all, that is what we are doing here - anyone who posts a personal attack should look elsewhere :) ).  The more people say Linux/Unix is bullet proof, that there are no viruses, that it's impossible, I can guarantee someone out there will generate an attack just to prove those people wrong.


> It is because all the AV for linux don't scan for any linux virus... so you are wasting your space and your ram and your cpu for something that does nothing to protect your system...

Again, if a person wishes to be more than just a user, and instead desires to try to protect others as well, where is the harm?  The biggest clue you give here - MY space, MY ram, MY cpu - not anyone elses, so who does it hurt - no one.


> Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.
Rather tell them how to protect themselves instead of cleaning up the mess all the time ;)

It has always been a nice sentiment, but it will never happen.  If I can help protect my sisters and my elderly parents, I will continue to do so.  Since this is not the place for details on the internals of an OS, I will refrain from that type of debate.  However, I do appreciate the honest exchange of ideas and opinions such as is happening with this thread.

Please understand I mean no personal attacks to anyone, just trying to keep a debate open!  :)

---

### Post by barbedsaber on 2008-06-21
but, you can't get vir... never mind.

---

### Post by hyper_ch on 2008-06-21
> **anewguy said:**
> Let's see - if the installed base was reversed, Windows desktops versus Linux desktops, do you seriously believe malware producers would "waste their time" with Windows instead of going after the larger installed base? [...]
It's not a believe, it's a fact and your thoughts are flawed here...
[http://www.theregister.co.uk/2004/10/22/linux_v_windows_security/](http://www.theregister.co.uk/2004/10/22/linux_v_windows_security/)

> **anewguy said:**
> The more people say Linux/Unix is bullet proof
Who says it's bullet-proof? Largest threats to linux security are rootkits and PEBKAC ;) and besides, security is an ongoing process ;)

> **anewguy said:**
> Again, if a person wishes to be more than just a user, and instead desires to try to protect others as well, where is the harm?  The biggest clue you give here - MY space, MY ram, MY cpu - not anyone elses, so who does it hurt - no one.
(1) it's your choice
(2) you read the proverb I posted? I rather have to make people think and make an informed choice than treat them as mindless zombies

> **anewguy said:**
> If I can help protect my sisters and my elderly parents, I will continue to do so.
I gave my parents a choice... either switch to a perfectly setup Ubuntu or I'll install a last time windows and then they are on their own... so they use now linux and I haven't had a request for help for over a year and computer's running fine.

---

### Post by Felicity_X on 2008-06-21
I have used both AVG and Panda in the windows environment.  They are both well recommended, should a Ubuntu user need them.

Does the watertight security hold true, if you do not have a root user, where spyware is concerned, though?

---

### Post by stinger30au on 2008-06-21
> **SunnyRabbiera said:**
> 
Really I know that it must be insane to have a secure OS that has little issues coming from a OS that is more bug ridden then a colony of ants but its true....


i wish you did not pick on ants. believe it or not they are *EXTREMELY* smart and very well organized, so i think you picked the wrong insect for your analogy. i would have picked something like the [dodo bird]("http://en.wikipedia.org/wiki/Dodo")

Ants Rock!!!:guitar:

---

### Post by akiratheoni on 2008-06-21
> **stinger30au said:**
> i wish you did not pick on ants. believe it or not they are *EXTREMELY* smart and very well organized, so i think you picked the wrong insect for your analogy. i would have picked something like the [dodo bird]("http://en.wikipedia.org/wiki/Dodo")

Ants Rock!!!:guitar:

It's word play... get it? Bug-ridden? Ant colony? The dodo bird wouldn't have worked with the analogy lol. He's not saying ants are dumb.

---

### Post by ByteJuggler on 2008-06-21
> **anewguy said:**
>   Windows has generated so many attacks not because it is vunerable (which it undoubtably is), but because it is the largest installed base.  

This is a proposition often put forward by Microsoft apologists, but one that is in fact refuted by the facts.  So, if it was indeed true as you suggest, that the primary driver for number of flaws/exploits was primarily "size of installed base" as you assert, then we should find no counter-examples where a smaller installed base (of some software/platform) actually have larger numbers of vulnerabilities/attacks.  However, this is not what we find.

I demonstrate this proposition/idea is (in principle) flawed by counterexample. Consider web server softwaer, IIS vs. Apache.  

Apache has pretty much always been the most popular web server and thus has (and has had for at least about the last 12 years) the largest installed base of web server software, period.  IIS have by comparison always had a substantially smaller installed base.  By your proposition/suggestion above, Apache should then have (and have had) many more attacks and exploits over the years, due to having the largest installed base, but this is not found to be the case when the numbers are investigated.  In fact, IIS has had in some period *orders of magnitude* more (and indeed also more serious) attacks during its lifetime (or in particular year periods of its existence) than Apache.  

Consequently, this example demonstrates that "largest installed base" does not neccesarily imply having the most vulnerabilities, although I am conversely not saying that it doesn't play any role all.  I am however pointing out that saying that a particular software product will be more attacked due to having the largest installed base is at best an oversimplifaction and possibly misleading.

For more on this and some background where these and other facts and figures are discussed, see [here]("http://www.dwheeler.com/numbers/oss_fs_why_presentation.pdf") and [here]("http://www.dwheeler.com/oss_fs_why.html").

---

### Post by hyper_ch on 2008-06-21
another important point is how software is run. Traditionally on Windows if you run something you run it as administrator (VISTA changed this now - I think). But normal home users up to XP will run everything as administrator. If you can take over one process you will own the whole machine.

On linux this is also completely different. Most stuff runs as own user and if you take over apache on linux you don't control the whole computer. So you are fairly more limited on what you can do with own just one process on linux compared to Windows.

---

### Post by anewguy on 2008-06-23
> **ByteJuggler said:**
> This is a proposition often put forward by Microsoft apologists, but one that is in fact refuted by the facts.  So, if it was indeed true as you suggest, that the primary driver for number of flaws/exploits was primarily "size of installed base" as you assert, then we should find no counter-examples where a smaller installed base (of some software/platform) actually have larger numbers of vulnerabilities/attacks.  However, this is not what we find.

I demonstrate this proposition/idea is (in principle) flawed by counterexample. Consider web server softwaer, IIS vs. Apache.  

Apache has pretty much always been the most popular web server and thus has (and has had for at least about the last 12 years) the largest installed base of web server software, period.  IIS have by comparison always had a substantially smaller installed base.  By your proposition/suggestion above, Apache should then have (and have had) many more attacks and exploits over the years, due to having the largest installed base, but this is not found to be the case when the numbers are investigated.  In fact, IIS has had in some period *orders of magnitude* more (and indeed also more serious) attacks during its lifetime (or in particular year periods of its existence) than Apache.  

Consequently, this example demonstrates that "largest installed base" does not neccesarily imply having the most vulnerabilities, although I am conversely not saying that it doesn't play any role all.  I am however pointing out that saying that a particular software product will be more attacked due to having the largest installed base is at best an oversimplifaction and possibly misleading.

For more on this and some background where these and other facts and figures are discussed, see [here]("http://www.dwheeler.com/numbers/oss_fs_why_presentation.pdf") and [here]("http://www.dwheeler.com/oss_fs_why.html").

Actually, I'm no Microsoft apologist.  Additionally, the numbers may show that for servers at this time, but I still feel that if every average user out there who uses Windows was suddenly reversed and you had millions upon millions of Linux desktops, and the subsequent huge reduction in number of Windows desktops, those figures would change dramatically.  It make not make any sense to you, and it is just my opinion, but it's also an opinion backed by 23+ years of system administrator and systems programming duties on large, medium ,mini and micro computers.  Yes there are problems with Windows, and yes there have been problems with the level the user normally ran at.  But any serious virus/key capture, etc., person worth their salt will still only go for the place where there is highest likely hood of the highest amount of return.  That does translate into installed base, particularly for desktops.  You all sound knowledgeable, so you know the extra care that is normally put into server management.  But look at the average Joe Schmoe user, and then replace all the installed user base of Windows PC's with Linux PC's, and you will see the tides turn.  It's a given in statistical analysis.  Would that make it as easy as Windows?  No way.  Would it require some pretty technical things to accomplish?  Yes.  Impossible? - never.  Current statistics on servers may say something different at this time, but again that is the server market.  I'm quite familiar with the tremendous internal differences between an operating system like Windows and any Unix variant.  So sometimes it is really difficult to draw any type of outside opinions because of the differences, but my whole point is that "can't" and "won't" should not be used in the context of this thread.  It IS possible, it DOES happen, and it WILL happen.  Remember back when viruses were first shared on PC's by a simple diskette?  We are at that level with Linux, and I'm not saying in anyway shape or form that Linux is a vunerable as Windows on the average users' desktop.  But the risk is real, not imagined.  We are at the beginning of where the virus problem used to be with Windows years ago.  Everyone is more aware, more intelligent now (not just the OS developers), so I don't perceive a day when they can be as prevalent or damaging as they have been in Windows.  I would never debate otherwise.  Let's just not lull users into believing "can't" "won't" and "couldn't".  That's a very unsafe path to suggest.

I'm enjoying the debate and the opportunities to state my opinions.  All of this discussion pro and con can only help and make our users more intelligent.  It stops them from just being a button pusher and hopefully makes them think a little.  That makes it all worthwhile!

Thanks guys!  :)

---

### Post by hyper_ch on 2008-06-24
> **anewguy said:**
> But any serious virus/key capture, etc., person worth their salt will still only go for the place where there is highest likely hood of the highest amount of return.
Exactely... assuming you have a market share of 50% windoze desktops and 50% linux desktops... where would you try to hack yourself in?

I'd go for Windoze because
(1) poor user levels
(2) many unneeded services waiting
(3) proven to be an easy target
(4) by owning one of the many things running you own the whole machine
(5) very likely there's already malware on it that you can exploit further
(6) single plattform where all is the same
(7) ...

As long as linux will not outmatch Windoze in vast numbers, as long as stuff like MSIE is so deeply rooted inside Windoze, as long as ..... you would target Windoze. IMHO Windoze first needs a complete change in security before Linux will become interesting on equal numbers...

---

### Post by gtdaqua on 2008-06-24
> **hyper_ch said:**
> 
.......

IMHO Windoze first needs a complete change in security before Linux will become interesting on equal numbers...

They (windoze) need a complete change in the kernel which should pretty much take care of security. Their whole kernel idea is monolithic. Then the kernel itself is monolithic. They went to reformat security in Vista and ended in the wrong place. Vista still does not protect users as linux does. 

And then the boring names they come up with - 'User Access Control'. They had the vision. That was perfect. But when they actioned it, it became worse than a greek tragedy. There are simply so many people in their 'teams' and the final product looks dog. I mean, for a company that has $40 billion in cash comes up with an OS that is more memory and processor hungry which is simply not acceptable. 

Dont forget that this is also the company that made us believe that 'more apps, slow down the machine'. I mean, ask a simply techie in a windows environment why one XP machine is faster than the other. Obvious reason would be 'that XP machine has more apps installed than the other one.'

Ask why user logon process is faster in some and slower in some machines. Answer: 'that user's desktop is flooded with files. So it will take a while to load the desktop'. True - lesser desktop items fasten your desktop loading process.

Why the hell is OS trying to process the installed apps even when they are not used? Why is it bothered about each and every desktop item as if its trying to execute them? Why should the machine simply become slower because a dozen apps are installed?

And then Linux came and we were all surprised that having 100 items on the desktop and 300 apps installed on a simple Gnome takes the same 12 seconds to start up and 7 seconds to login. No change. So we think Linux is a miracle. No its not. This is how OS is supposed to 'behave'. Not like a toothless-mongrel crying for more bones than it can chew.

And then their licensing......

I could go on - but in a nutshell, M$ is the new IBM. There you go.


EDIT: M$ did give and is giving a lot of business to other IT players. Especially security vendors. AV is not required in Linux-based machines. You dont normally see a security vendor complaining M$'s architechture. If it were stronger, those vendors would not have any business.

See this: [The Internet security business is a big fat con]("http://www.theinquirer.net/en/inquirer/news/2007/05/30/the-internet-security-business-is-a-big-fat-con").

---

### Post by gn2 on 2008-06-24
I'm with hyper_ch on this.

Criminals, for that is what virus writers are, will *always* attack the soft target.

In a street of houses they will leave the ones with intrusion alarms and target the ones without.

Muggers will not tackle a 240lb lump of male athlete, they will attack those who are less able to defend themselves.

Viruses only exist because of how Windows was created.
It was created weak. Linux is strong.

Other security problems *may* allow Linux to be exploited in the future, but they will not be viruses.
Any Linux exploits will be discovered and fixed far quicker than any holes in Windows because of the Open Source model.

---

### Post by hyper_ch on 2008-06-24
> **gtdaqua said:**
> I mean, for a company that has $40 billion in cash comes up with an OS that is more memory and processor hungry which is simply not acceptable.

I think they could but that would make hardware producers angry. You know, people want to have the latest bling-bling and while M$ did a fairly good job at persuading that people need bling-bling up to XP M$ made sure that it was Windoze installed on the new machines. It's a deal between hardware manufacturer. They want to sell new hardware so they need stuff that requires that hardware.

XP came out in 2001. If VISTA would run in an acceptable manner on the standard hardware from 2001 - how many people would use now VISTA? I bet it's a lot more.

---

### Post by 3rdalbum on 2008-06-24
If you're careful enough with what you download, and you have an operational firewall, you don't need antivirus on Windows let alone on Linux.

My workplace runs Windows XP SP1 computers with Internet Explorer and Outlook Express, no anti-virus and no anti-spyware. Recently our head office decided to run anti-virus and anti-spyware software, and update one of our computers. The only one with spyware was the one that the boss's niece used to download games off the Internet.

My father's computer is unpatched SP2, and is completely clean (I tested it for him with some "portable" anti-virus and anti-spyware applications).

If you're not careful with what you download off the Internet, then frankly in this day and age you shouldn't be using computers. If you are careful but don't trust others, then give your computer's other users limited accounts. If everyone using your computer knows safe computing practice, then you don't need anti-virus.

---

### Post by gtdaqua on 2008-06-24
> **3rdalbum said:**
> If you're careful enough with what you download, and you have an operational firewall, you don't need antivirus on Windows let alone on Linux.

My workplace runs Windows XP SP1 computers with Internet Explorer and Outlook Express, no anti-virus and no anti-spyware. Recently our head office decided to run anti-virus and anti-spyware software, and update one of our computers. The only one with spyware was the one that the boss's niece used to download games off the Internet.

My father's computer is unpatched SP2, and is completely clean (I tested it for him with some "portable" anti-virus and anti-spyware applications).

If you're not careful with what you download off the Internet, then frankly in this day and age you shouldn't be using computers. If you are careful but don't trust others, then give your computer's other users limited accounts. If everyone using your computer knows safe computing practice, then you don't need anti-virus.

Not a good suggestion, mate. There are plenty of malware out there sweeping IPs by the second. You could get infected simply by going online. Vulnerabilities are one thing. Malware is another. The exploits are so intelligent (or windoze is weak), they could hijack your browser and 'twist' your search results without you knowing. 

Its like saying, you dont need an helmet when you are riding a motorcycle coz you ride very slow. Ah, but you aint the only one on the highway, are you??

[The 12-minute Windows heist]("http://www.zdnet.com.au/news/security/soa/The-12-minute-Windows-heist/0,130061744,139200021,00.htm?omnRef=http://www.google.co.in/search?q=infected%20going%20online")

> 
If everyone using your computer knows safe computing practice..


where is this actually happening? havent you heard of 'accidents'? that is not in the scope of 'safe practices'.

From what you have said with XP SP1 and no-anti-virus-required,  I can see you never had to spend time chasing a virus in a network. You are just lucky.  Try it someday and I dont think you will stick to your idea again.

---

### Post by gaffurabi on 2008-06-24
**sophos** has a very proffessional and nice one.
but unfortunately it's not free, ask your organisation/university if they are a customer of sophos and can supply you one.

despite that i don't run any antivirus on ubuntu :D

---

### Post by sujoy on 2008-06-24
i am satisfied with the firewall in my router and iptables.

---

### Post by novatotal on 2008-06-24
well being a member of bot ubuntu forum and ubuntu-es forum, just last night read that, one ubuntu user due to a malpractice off him granted, got his machine hijacked by some one and used to send mails to other people.
you can read the post in ubuntu-es, if you understand spanish.
ok he was runing as root, and did not close the root acount, but it can happen, a memory lapse is all it takes.

---

### Post by hyper_ch on 2008-06-24
if one works as root constantly and doesn't understand the implications of it then this is doomed to happen... nothing will prevent that.

---

### Post by lundish on 2008-06-24
I use AVG (not for ubuntu protection but to scan Windows partitions) in command line. 

AVG's deb ===> [http://free.grisoft.com/ww.download?prd=afl](http://free.grisoft.com/ww.download?prd=afl)

sudo avgupdate -o  ====> to upgrade

avgscan /home/user/  ====> to scan 

that's would be all folks :)

---

### Post by fatality_uk on 2008-06-24
As much as some may dislike the fact, Anti-Virus does ***SOMETIMES*** have a place within Linux. We are currently operating a mixed, Windows XP and Ubuntu 7.10/8.04 network. As the man for whom the IT buck stops, I have to consider the wider implications of a Linux user transmitting a Windows virus into our network.

I can not ignore the fact that it could happen and so I need to take precautions to prevent damage, data loss, security compromise or down time.

By 2009, we will not own a Windows license for any of our locations and I will be happy to give notice to our AV supplier.

---

### Post by hyper_ch on 2008-06-24
nobody doubts that there are scenarios where it is very much adviced to use AV... but just installing AV because it's necessary on Windoze is just FUD. Know what you're doing and why - don't be a zombie ;)

---

### Post by ByteJuggler on 2008-06-24
> **anewguy said:**
> Actually, I'm no Microsoft apologist.
Sorry, I didn't mean to imply you're one, merely that this argument is put forward by Microsoft apologists (who have a vested interest in deflecting criticism from Windows) and that actually, the argument has (as I see it) some fundamental flaws (which is what I tried to point out.)  As you know, many ostensibly (intuitively) correct arguments turn out to in fact not be true/correct.

So at the risk of belaboring the point, I've tried to show that it doesn't not follow that larger installed base always implies more vulnerabilities or exploits, by providing a counter example, which therefore fatally damages the primary premise the argument is founded on.      

> **anewguy said:**
> 
Additionally, the numbers may show that for servers at this time, but I still feel that if every average user out there who uses Windows was suddenly reversed and you had millions upon millions of Linux desktops, and the subsequent huge reduction in number of Windows desktops, those figures would change dramatically.

You are welcome to that opinion but as I've shown you are holding on to it despite real world evidence to the contrary.  You may of course turn out to nevertheless be correct (in some possible future universe), but nevertheless, having such an expectation is simply not supported by currently observed evidence of millions of installed web servers and other applications, clearly demonstrating that things are apparently not quite as simple as you make them out to be, no matter how seemingly intuitive and simple the logic seems.

> **anewguy said:**
> 
It make not make any sense to you, and it is just my opinion, but it's also an opinion backed by 23+ years of system administrator and systems programming duties on large, medium ,mini and micro computers.

*Of course* what you are saying does make sense at first sight (and yes, even to me!) , but as I've tried to (clearly unsuccessfully) demonstrate, the apparently sensible logic appears flawed when one reviews the statitistics as I've tried to show. I am trying to move this argument from a matter of simple conjecture and speculative opinion to one more rigorous, where a stated hypothesis is tested against observed reality and found to contradict reality, and therefore must be modified given the observed reality or discarded outright as totally flawed.  

As for your experience of 23+ years, that's great but I don't see how it's relevant.  I've got about 18+ years of computer industry  experience as well (although that really is in my opinion irrelevant to the argument, this argument can it seems to me, be decided purely on the validity of the propositions it's founded on.)

So anyway, bottom line is, from where I'm sitting I simply think it's not that simple.  The installed base probably plays *a* role, but probably not (and demonstrably not in all cases) *the defining* role.  

> **anewguy said:**
> Yes there are problems with Windows, and yes there have been problems with the level the user normally ran at.  But any serious virus/key capture, etc., person worth their salt will still only go for the place where there is highest likely hood of the highest amount of return.  That does translate into installed base, particularly for desktops.

Agreed, but then, consider this alternate scenario: 

Suppose the largest installed base of software was actually secure enough that it turns out not to provide the highest level of return for would be miscreants?  What would the black hats choose then?  Following your logic, they will still go to the target offering the highest level of overall return, which ipso facto then will not be the target with the largest installed base!!  (And, Apache vs IIS is just one example of exactly this happening!)

> **anewguy said:**
> 
You all sound knowledgeable, so you know the extra care that is normally put into server management.  But look at the average Joe Schmoe user, and then replace all the installed user base of Windows PC's with Linux PC's, and you will see the tides turn.  


Possibly you will see the tides turn as you think. Possibly not. I am simply trying to demonstrate that your opinion of how it might turn out, however intuitive/plausible, is not the only way to look at matters, particularly not when we look at all the facts and figures availalbe to us.   Not everything that seems plausible/intuitive is after all true.  There is then in fact a good chance, I argue, taking into account all the facts, that even when you have Linux on every Joe's PC, that the bottom line level of exploits and security threats will still be far lower than it currently is for Windows.  (Although I do agree that it's entirely possible and probably reasonable to expect that in absolute numbers there will be some increase. )

> **anewguy said:**
> 
It's a given in statistical analysis.  Would that make it as easy as Windows?  No way.  Would it require some pretty technical things to accomplish?  Yes.  Impossible? - never.

I never said it's impossible.  Neverhteless the fact is however that the situation on Linux is orders of magnitude better than on Windows presently.  So good in fact, that there exists no "in the wild" viruses for Linux at the minute.  Does that mean you don't have to be careful?  Of course not.  Does that mean you should be all paranoid about it? Also emphatically no, IMO.  I'm pretty sure the moment a proper wide spread virus that can actually survive in the hostile heterogenous OS enviroment that is Linux rears it's head, it will be *big* news.  

> **anewguy said:**
> 
Current statistics on servers may say something different at this time, but again that is the server market.  I'm quite familiar with the tremendous internal differences between an operating system like Windows and any Unix variant.So sometimes it is really difficult to draw any type of outside opinions because of the differences, but my whole point is that "can't" and "won't" should not be used in the context of this thread.  It IS possible, it DOES happen, and it WILL happen.  Remember back when viruses were first shared on PC's by a simple diskette?  We are at that level with Linux, and I'm not saying in anyway shape or form that Linux is a vunerable as Windows on the average users' desktop.  But the risk is real, not imagined.  We are at the beginning of where the virus problem used to be with Windows years ago.  

Sorry but I think this is an exageration.  Linux (and Unix in general) didn't just pop into existence yesterday now did it?  The black hats have been trying to break Unix and Linux and all the attendant software for as long as they've existed, and many holes *have* been found, are being found, and for that matter, are being plugged.  ("sendmail" for example is one program that for a substantial period of time time probably had a higher than average incidence of hacks and exploits compared to many other popular MTA's.  It's been around since forever.) So yes, the risk is real, but the magnitude of the risk is actually very small, generally speaking.  Hopefully we can agree on that.  

> **anewguy said:**
> 
Everyone is more aware, more intelligent now (not just the OS developers), so I don't perceive a day when they can be as prevalent or damaging as they have been in Windows.  I would never debate otherwise.  Let's just not lull users into believing "can't" "won't" and "couldn't".  That's a very unsafe path to suggest.

Well I certainly am not trying to lull anybody into a false sense of security.  But equally let's not put the frighteners on new users of Linux/Ubuntu.  There really are some profound and fundamental differences between how Windows and Windows applications operates and are designed and how Unix and Unix-like operating systems and applications operates and are designed.  Which does fundamentally affect severity and types of security problems one should look out for and ultimately the way we think about security on Linux/Ubuntu.

If anything, it is precisely that the nature of the threat is different on Linux/Unix compared to Windows.  Paradoxically with Joe user, I'd argue the danger arguably exists that simply carrying over a Windows mindset and just telling people to run a virus scanner (currently targetted at Windows viruses no less) on their Ubuntu install, that by itself might in fact engender a false sense of security, as doing so really does nothing for the security of the Linux box itself.  **There are arguably other more important aspects to Linux/Ubuntu security that should instead be understood, (e.g. Sudo vs. root for a simple example.)**  A simple-minded Windows centric security mindset is not really the best for Linux/Ubuntu, I argue.

> **anewguy said:**
> 
I'm enjoying the debate and the opportunities to state my opinions.  All of this discussion pro and con can only help and make our users more intelligent.  It stops them from just being a button pusher and hopefully makes them think a little.  That makes it all worthwhile!


I'm glad you're enjoying the debate.  I hope my response will be taken in the same vein that you offered yours above. :-)  With that said I probably won't be responding again as this is getting slightly off topic and we've both made our points to death now.

All the best.  :-)

---

### Post by fatality_uk on 2008-06-24
> **hyper_ch said:**
> nobody doubts that there are scenarios where it is very much adviced to use AV... but just installing AV because it's necessary on Windoze is just FUD. Know what you're doing and why - don't be a zombie ;)

Who said I was being a Zombie :) :lol:
I carry out a 6 monthly risk analysis across various aspects of the dept. and one area of concern is that our sales people using Linux, often get given USB sticks with orders, prices, documents they need to be able to work sometimes from suppliers and sometimes customers.

I would be VERY remiss if I just dismissed this threat and allowed them to deliver these unchecked.

---

### Post by aysiu on 2008-06-24
This is one of the best posts I've ever read on the subject. Very nicely put. > **RequinB4 said:**
> I think one thing that there are two things that haven't been mentioned.

First, anti-virus is not really anti-virus - it is virus-checking.  AV works (for 99.999% of the time, there are exceptions) by comparing files or parts of files to known patterns of virus interaction.  Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.

Second, there is the beleif that we should run AV to protect those we contact via the internet getting infected.  Assuming we're not talking about a mail or SAMBA server or something, let's think about this for a second - what are the possible outcomes?

1)  Linux box doesn't get a virus.  No problem.

2)  Linux box gets a virus, and doesn't transmit it.  No harm done, maybe a few wasted bytes of space.

3)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box has equivalent or better anti-virus.  They don't get infected, so no harm done.

4)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box doesn't have antivirus or it fails to detect.  Windows user is very sad.

So, let's examine 4.  Since the box doesn't have antivirus, and has an open connection to the internet, and (for the sake of argument) is running unsafe applications such as IE or Outlook, its security is already very low.  In fact, it's far, far, far more likely that they get the virus not from  you but from normal browsing or from ANOTHER windows box which is ACTIVELY propagating the virus.  Add the fact that the probability of 1, 2, and 3 is also MUCH higher than 4, and you begin to see my point.

So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable?

---

### Post by John.Michael.Kane on 2008-06-24
While the post quoted about might have merit. The question still remains how does the community teach users who are new to Linux, the conditions under which AV, routers, ip-tables, IDS, etc should be used, and not used.

---

### Post by hyper_ch on 2008-06-24
> **John.Michael.Kane said:**
> While the post quoted about might have merit. The question still remains how does the community teach users who are new to Linux, the conditions under which AV, routers, ip-tables, IDS, etc should be used, and not used.

Why should the community teach it? All the information on this has been discussed and looked at thousands of times... it shoulb rather those who are new to linux to inform themselves... it should not be the "job" of the community to teach that.

---

### Post by John.Michael.Kane on 2008-06-24
> **hyper_ch said:**
> Why should the community teach it? All the information on this has been discussed and looked at thousands of times... it shoulb rather those who are new to linux to inform themselves... it should not be the "job" of the community to teach that.

That is your opinion, and as long as that is the stance taken you will have threads, post etc debating this.

What is needed is clear, and precise information, not the RTFM approach you seem to be advocating.

This community has documentation/Tutorials ranging from how to set-up ssh, compiz/desktop effects, system backup, gpg, etc. 

These guides never came with the community should not teach it attitude.

So just as community members have written guides which ((Teach/explain)) to users how to do the above, why not a guide encompassing the issues of AV, routers, ip-tables, IDS, etc

So the question still stands how does the community teach users who are new to Linux, the conditions under which AV, routers, ip-tables, IDS, etc should be used, and not used.

---

### Post by hyper_ch on 2008-06-24
> **John.Michael.Kane said:**
> That is your opinion, and as long as that is the stance taken you will have threads, post etc debating this.
So?

> **John.Michael.Kane said:**
> What is needed is clear, and precise information
There is very much of it... have a look at the ubuntu wiki and ubuntuguide...

> **John.Michael.Kane said:**
> not the RTFM approach you seem to be advocating.
If you think that I am of the opinion that he who asks should first spend some time in researching the problem himself before just opening a thread and ask to be spoon-fed, then I advocate the RTFM approach...
Teach people how to help themselves getting the information they need seems to me a better approach than just giving them the one thing they ask for.
And besides, ever had a look at the man pages? there's an aweful lot of information in there ;)

> **John.Michael.Kane said:**
> This community has documentation/Tutorials ranging from how to set-up ssh, compiz/desktop effects, system backup, gpg, etc.
I know, hence my stance that first some research should be done by the one who seeks help ;)

> **John.Michael.Kane said:**
> These guides never came with the community should not teach it attitude.
You are confusing here spoon-feeding and teaching ;)

> **John.Michael.Kane said:**
> So just as community members have written guides which ((Teach/explain)) to users how to do the above, why not a guide encompassing the issues of AV, routers, ip-tables, IDS, etc
Can you put that into other terms? I don't get your point.

QUOTE=John.Michael.Kane;5253194]So the question still stands how does the community teach users who are new to Linux, the conditions under which AV, routers, ip-tables, IDS, etc should be used, and not used.[/QUOTE]
No need to spoon-feed, let them make an informed decision ;)

---

### Post by John.Michael.Kane on 2008-06-24
Research is fine. The problem will always be having information that is understandable by those doing the research you demand they do, and it is obvious that the information is not there or not clear, if it was you would not have xyz many threads asking is AV etc needed.

Second I have read many of the wiki info posted for Ubuntu, and while it is clear to me, this may not be the case for everyone else.

At the end all you have stated are you opinions, not facts. The fact of the matter is there are users who will not, and never read man pages etc, however. They might read a guide/howto/tutorial, and it is obvious there needs to be precise info on when they need to implement the particular items debated about in this thread.

The community has guides for everything else pertaining to Ubuntu, why not a guide encompassing the issues of AV, routers, ip-tables, IDS, etc, and their use.

The question still stands how does the community teach users who are new to Linux, the conditions under which AV, routers, ip-tables, IDS, etc should be used, and not used.

At the end of day, it would seem we will have to agree to disagree.

---

### Post by magnus0 on 2008-06-24
Why would you need an antivirus? Just to keep other windows users safe. But who cares, they have their own antivirus, so that's not your concern what happens to windows users

---

### Post by hyper_ch on 2008-06-24
> **John.Michael.Kane said:**
> Research is fine. The problem will always be having information that is understandable by those doing the research you demand they do, and it is obvious that the information is not there or not clear, if it was you would not have xyz many threads asking is AV etc needed.
I rather think people are lazy to do research and just come on here and ask this or that... I mean it's much more confortable to just get spoon-feeded than to put any effort into it...

> **John.Michael.Kane said:**
> Second I have read many of the wiki info posted for Ubuntu, and while it is clear to me, this may not be the case for everyone else.
Well, I have very rarely seen a thread that goes:

"Hi

I have this and that problem.
I have tried this here. --> didn't work
I tried to follow that guide --> didn't work
I tried this one here but couldn't not understand what step XYZ is supposed to do..."


> **John.Michael.Kane said:**
> They might read a guide/howto/tutorial
I doubt that because I hardly ever see a reference to any guide or what was already tried...

> **John.Michael.Kane said:**
> The community has guides for everything else pertaining to Ubuntu, why not a guide encompassing the issues of AV, routers, ip-tables, IDS, etc, and their use.
There are guides on that also ;)

> **John.Michael.Kane said:**
> At the end of day, it would seem we will have to agree to disagree.
I can agree with that

---

### Post by drunkardivan on 2008-06-24
> **hyper_ch said:**
> 
And besides, ever had a look at the man pages? there's an aweful lot of information in there ;)


<dm> I discovered that you'd never get an answer to a problem from Linux Gurus by asking. You have to troll in order for someone to help you with a Linux problem.
<dm> For example, I didn't know how to find files by contents and the man pages were way too confusing. What did I do? I knew from experience that if I just asked, I'd be told to read the man pages even though it was too hard for me.
<dm> Instead, I did what works. Trolling. By stating that Linux sucked because it was so hard to find a file compared to Windows, I got every self-described Linux Guru around the world coming to my aid. They gave me examples after examples of different ways to do it. All this in order to prove to everyone that Linux was better.
* ion has quit IRC (Ping timeout)
<dm> brings a tear to my eye... :') so true..
<dm> So if you're starting out Linux, I advise you to use the same method as I did to get help. Start the sentence with "Linux is gay because it can't do XXX like Windows can". You will have PhDs running to tell you how to solve your problems.
<dm> this person must be a kindred spirit of mine

from bash.org

---

### Post by cardinals_fan on 2008-06-25
> **drunkardivan said:**
> <dm> I discovered that you'd never get an answer to a problem from Linux Gurus by asking. You have to troll in order for someone to help you with a Linux problem.
<dm> For example, I didn't know how to find files by contents and the man pages were way too confusing. What did I do? I knew from experience that if I just asked, I'd be told to read the man pages even though it was too hard for me.
<dm> Instead, I did what works. Trolling. By stating that Linux sucked because it was so hard to find a file compared to Windows, I got every self-described Linux Guru around the world coming to my aid. They gave me examples after examples of different ways to do it. All this in order to prove to everyone that Linux was better.
* ion has quit IRC (Ping timeout)
<dm> brings a tear to my eye... :') so true..
<dm> So if you're starting out Linux, I advise you to use the same method as I did to get help. Start the sentence with "Linux is gay because it can't do XXX like Windows can". You will have PhDs running to tell you how to solve your problems.
<dm> this person must be a kindred spirit of mine

from bash.org
[http://ubuntuforums.org/showthread.php?t=634322](http://ubuntuforums.org/showthread.php?t=634322)

---

### Post by TheThinker on 2008-06-25
> **hyper_ch said:**
> Well, when their systems get crippled again just tell them you don't have those worries. I don't see it as my job to "protect" windows users from viruses. They should do that themselves.

Good point. We linux users shouldn't be seen as cockroaches who spread viruses to others without becoming sick ourselves. If your computer is sick, blame the virus writers then take the proper precautions.

While it makes sense to have a linux machine doing virus scans for windows computers, it makes even more sense if more people had more solid operating systems. Why have one suffer for the mistakes of other people?

---

### Post by jrusso2 on 2008-06-25
If the new former Windows users feel they must have antivirus, anti spyware, firewalls and defrag let them run it.  Who cares its not needed but if they feel its needed who cares.

---

### Post by sports fan Matt on 2008-06-25
Also, why are there THREE of the same topics right on the 1st page?

---

### Post by lisati on 2008-06-25
> **magnus0 said:**
> Why would you need an antivirus? Just to keep other windows users safe. But who cares, they have their own antivirus, so that's not your concern what happens to windows users


[LIST=1]
[*]I dual-boot one of my machines, with XP as its main OS - I've had one scary experience from catching something nasty, and I don't want a repeat.
[*]Some ISPs have a "don't pass on malware" part of their contract - they'd probably consider which OS you use irrelevant when taking you to court.
[/LIST]
EDIT: The following is a quote from [http://nz.docs.yahoo.com/info/terms/](http://nz.docs.yahoo.com/info/terms/)
> 
**6. MEMBER CONDUCT**

 You understand that all information, data, text, software, music, sound, photographs, graphics, video, messages or other materials ("Content"), whether publicly posted or privately transmitted, are the sole responsibility of the person from which such Content originated. This means that you, and not Yahoo!Xtra, are entirely responsible for all Content that you upload, post, email or otherwise transmit via the Service.
  Yahoo!Xtra does not control the Content posted via the Service and, as such, does not guarantee the accuracy, integrity or quality of such Content. You understand that by using the Service, you may be exposed to Content that is offensive, indecent or objectionable. Under no circumstances will Yahoo!Xtra be liable in any way for any Content, including, but not limited to, for any errors or omissions in any Content, or for any loss or damage of any kind incurred as a result of the use of any Content posted, emailed or otherwise transmitted via the Service.
 [COLOR=Blue]You agree to not use the Service to:[/COLOR]
 
[LIST=1]
[*]upload, post, email or otherwise transmit any Content that is unlawful, harmful, threatening, abusive, harassing, tortious, defamatory, vulgar, obscene, libelous, invasive of another's privacy, hateful, or racially, sexually, ethnically or otherwise objectionable or vilifying;
[*]harm minors in any way;
[*]impersonate any person or entity, including, but not limited to, a Yahoo!Xtra official, forum leader, guide or host, or falsely state or otherwise misrepresent your affiliation with a person or entity;
[*]forge headers or otherwise manipulate identifiers in order to disguise the origin of any Content transmitted through the Service;
[*]upload, post, email or otherwise transmit any Content that you do not have a right to transmit under any law or under contractual or fiduciary relationships (such as inside information, proprietary and confidential information learned or disclosed as part of employment relationships or under nondisclosure agreements);
[*]upload, post, email or otherwise transmit any Content that infringes any patent, trademark, trade secret, copyright or other proprietary rights ("Rights") of any party;
[*]upload, post, email or otherwise transmit any unsolicited or unauthorised advertising, promotional materials, "junk mail", "spam", "chain letters", "pyramid schemes", or any other form of solicitation, except in those areas (such as shopping rooms) that are designated for such purpose;
[*][COLOR=Blue]upload, post, email or otherwise transmit any material that contains software viruses or any other computer code, files or programs designed to interrupt, destroy or limit the functionality of any computer software or hardware or telecommunications equipment;[/COLOR]
[*]disrupt the normal flow of dialogue, cause a screen to "scroll" faster than other users of the Service are able to type, or otherwise act in a manner that negatively affects other users' ability to engage in real time exchanges;
[*]interfere with or disrupt the Service or servers or networks connected to the Service, or disobey any requirements, procedures, policies or regulations of networks connected to the Service;
[*]intentionally or unintentionally violate any applicable local, state, national or international law, including, but not limited to, regulations promulgated by the U.S. Securities and Exchange Commission, any rules of any national or other securities exchange, including, without limitation, the New York Stock Exchange, the American Stock Exchange or the NASDAQ, and any regulations having the force of law;
[*]"stalk" or otherwise harass another person; or
[*]collect or store personal data about other users.
[/LIST]
 You acknowledge that Yahoo!Xtra does not pre-screen Content, but that Yahoo!Xtra and its designees shall have the right (but not the obligation) in their sole discretion to refuse or move any Content that is available via the Service. Without limiting the foregoing, Yahoo!Xtra and its designees shall have the right to remove any Content that violates the TOS or is otherwise objectionable. You agree that you must evaluate, and bear all risks associated with, the use of any Content, including any reliance on the accuracy, completeness, or usefulness of such Content. In this regard, you acknowledge that you may not rely on any Content created by Yahoo!Xtra or submitted to Yahoo!Xtra, including without limitation information in Yahoo!Xtra Message Boards, Yahoo!Xtra Clubs, and in all other parts of the Service.
 You acknowledge and agree that Yahoo!Xtra may preserve Content and may also disclose Content if required to do so by law or in the good faith belief that such preservation or disclosure is reasonably necessary to: (a) comply with legal process; (b) enforce the TOS; (c) respond to claims that any Content violates the rights of third-parties; or (d) protect the rights, property, or personal safety of Yahoo!Xtra, its users and the public.
 You understand that the technical processing and transmission of the Service, including your Content, may involve: (a) transmissions over various networks; (b) changes to conform and adapt to technical requirements of connecting networks or devices and (c) transfer and storage of your Content in New Zealand, Australia, the United States or elsewhere.****
I've highlighted the relevant section.
****
[B]
[/B]

---

### Post by hyper_ch on 2008-06-26
> **jrusso2 said:**
> If the new former Windows users feel they must have antivirus, anti spyware, firewalls and defrag let them run it.  Who cares its not needed but if they feel its needed who cares.
Because they don't know better that non of that is needed and so it's in our hands to enlighten them ;)

---

### Post by anewguy on 2008-06-26
Reminds me of a developer from a project years ago - "these edits are so tight...." - we broke them in less than 1 minute.

---

