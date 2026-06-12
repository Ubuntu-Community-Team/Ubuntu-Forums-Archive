---
title: "Do you use virus protection software?"
date: 2011-06-28
forum: Recurring Discussions
---

### Post by Buster52 on 2011-06-28
Hi, all. We have finally been able to convince the powers that be to install Linux on a server in our library to run our online cataloging system (Koha is the one selected).

Mostly.

We have one councilman who is a former Windows IT guy and he is insisting we have a virus filter. He also suggested that Linux is less secure than Windows. If we can't convince him at tonight's council meeting, the rest of the council might side with him and we might not get the system, after all. So, my questions are...

Do you use virus protection software with your Linux server? Why or why not?

If you do use such software, which one do you use?

Do you have any other advice for a Linux novice who has to convince a Windows guy Linux is a secure choice for our system?

Thanks in advance!

--Jim

---

### Post by uRock on 2011-06-28
Hello and welcome to the forums,

Unless you are sharing files I wouldn't bother with AV. I have ClamAV, which is in the Ubuntu repository, and BitDefender installed. Both are decent, though I would say BitDefender has more up to date signatures. ClamAV is free, but since you won't be installing BitDefender on a home user system you will have to pay for a license to install it.

You can find more security information here [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I hope this helps,
uRock

---

### Post by Rasa1111 on 2011-06-28
Here's a good article Ive had saved for a bit..
[http://www.pcworld.com/businesscenter/article/204423/five_reasons_linux_beats_windows_for_servers.html](http://www.pcworld.com/businesscenter/article/204423/five_reasons_linux_beats_windows_for_servers.html)

Clearly your windows guy is unaware that Linux is used more than windows by many major corporations/businesses/etc. 

 I don't myself run a server yet,
So i can't answer the question directly,
But I can take a guess and say that most Linux users probably don't use virus protection on theirs. 
If Im wrong, my apologies. 

 I really wanted to get this thread bumped though, as i know there are many here with enough great info that should be able to convince anyone (all but the most ignorant) that Linux is the way to go here. 

 I wish I could remember where to find all the great info Ive read around here on this very subject.

Heres to hoping the resident server gurus hop in and enlighten us.  lol

 Good luck, 
I hope things turn out the *right* way. 
You know.. going Linux... lol ;P

good luck mate

---

### Post by e79 on 2011-06-28
> **uRock said:**
> Hello and welcome to the forums,

Unless you are sharing files I wouldn't bother with AV. I have ClamAV, which is in the Ubuntu repository, and BitDefender installed. Both are decent, though I would say BitDefender has more up to date signatures. ClamAV is free, but since you won't be installing BitDefender on a home user system you will have to pay for a license to install it.

You can find more security information here [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I hope this helps,
uRock

+ 1 for ClamAV

> ....He also suggested that Linux is less secure than Windows.....

Just lol....he obviously don't know what he's talking about.... and i bet he's scare of the word Linux because he don know much about it....ask him in what way Linux is less secure than windows if Google Farms are running on a custom flavor or Unix...
[http://en.wikipedia.org/wiki/Google_platform](http://en.wikipedia.org/wiki/Google_platform)

---

### Post by HermanAB on 2011-06-28
Well, you cannot win an argument with a council member and no computer is an island, so install something such as ClamAV and configure it to scan /home, /var and /tmp.  It won't hurt, since it won't actually do much and if someone would use the server to share Windows files, then it will help to prevent the spread of Windows malware.

---

### Post by walt.smith1960 on 2011-06-28
If agreeing to install antivirus is the difference between being able to implement what you want vs. not, I'd agree to install the antivirus software. Once you get the new system up and running and it's working well, is anyone likely to check if the the antivirus software is still running? As long as the antivirus software doesn't impose a Nortonesque performance penalty and doesn't cause any other problems, make the powers-that-be happy.

---

### Post by mcduck on 2011-06-28
An online catalog server wouldn't be sharing any files with Windows machines, so an antivirus scanner on such machine would be complete waste of resources. They pretty much only scan for Windows viruses and the server itself would be perfectly safe without one.

I'd say you have two options: 

You can try to inform the person about the lack of need for antivirus on such server, perhaps asking him to prove his point about Linux being insecure and needing such thing.

...or install ClamAV or something so he can feel happy, even though it's completely unnecessary and doesn't actually do anyhting on such server. (Perhaps you can at some later time "forget" to install it again after some update... ;)) This would probably be the easiest route, even though I'm generally against doing stupid things just to keep stupid people happy. :)


(actually I pretty much find the idea of scanning for Windows viruses on Linux useless feat anyway, apart from corporate e-mail servers and such situations. Even if you'd some day happen to send an infected file to a friend, his antivirus will protect him anyway. If it doesn't, he's already in serious troubles regardeless if you sent him an infected file or not. So the way I see it not having an antivirus app on a Linux machines will not help spreading viruses or malware anyway. You can't protect a Window user if that Windows user doesn't protect himself.)

---

### Post by psusi on 2011-06-28
I have never bothered with antivirus software even on Windows.  When I am given a machine at work that comes with it, I always disable it because it slows the machine down so much.  I have no need for such things because I am not dumb enough to blindly click yes when a malicious web site or email wants to install an activex control or something, or to try running an executable I get in an email.

Linux has no need for for antivirus since there has never been a Linux virus actually in the wild, and the system is not broken by design, so there are no easy attack vectors for a virus to spread.  To theoretically become infected you would have to manually download a program, save it, flag it as executable, and then run it with sudo ( which requires that you are an administrator ).

---

### Post by haqking on 2011-06-28
The facts are, is Linux immune to Viruses...then NO

Is it likely, then NOT VERY

But it is free (clamav etc) to protect incase and it certainly wont resource hog your machine like Symantec or other equal products within windows.

Is linux immune to viruses:

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

[http://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses](http://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses)

Viruses and malware that can effect Linux:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

The fact is Linux is as likely to be infected with a virus as Windows is as likely to become open source and free of charge ;-)

And the best protection against malware/viruses which will beat any software is user/security awareness training.

---

### Post by dFlyer on 2011-06-28
I don't. My wife does. We both run linux as our only OS. I currently feel it's a waste of resources as in the 15 plus years of using Linux I've never had a virus. I can say the same for my wife, but she still scans her computer once a week.

The only time I recommend someone use a virus protection program is when they are sharing files with windows users. Someday virus may become a problem for Linux, but that day hasn't arrived yet.

---

### Post by Thewhistlingwind on 2011-06-28
No, lol. 

How about this, install the (Only a resource hog while running) ClamAV, then set it to like once a week on crontab.

No ones gonna notice slowness if it's only from the hours of 1 to 5AM.

---

### Post by bodhi.zazen on 2011-06-28
No I personally do not need "virus protection software", but I do not think that is exactly what you are asking.

A better question is what do you know about Linux security and what do you intend to use antivirus for ?

IMO many people transitioning from windows feel a compulsive behavior to run anti virus. I usually let the do so until they either are frustrated with false positives or convince themselves it is not needed.

There are no know active Linux viruses, and you system was patched to the significant viruses long ago.

Linux is not windows and linux security does not for the most part include running antivirus.

The potential user cases for running antivirus would be if you are running a file serve or mail server or web proxy with Windows clients.

Some people advocate running antivirus on files you share with windows, but I have never seen a virus on such a share that entered through Linux, so I would focus on the windows side of this user case.

See also [The short life and hard times of a Linux virus](http://librenix.com/?inode=21) 

Or any other credible online security site (NOT one run by someone selling an antivirus product, those folks are using a heavy dose of the what-if-virus-to-sell-you-something-you-don't-need-combined-with-FUD ).

---

### Post by The_Invincible on 2011-06-28
Well . As of what i have come through . Antivirus for Linux first of all do not provide real time protection . If they do , then it requires additional tweaking . Plus , Ubuntu uses many other mechanisms for enhancing security eg. Permissions , Access Levels and much more .

But he is a council member , and if u do not win an argument atleast go ahead and install a free virus protection . ClamAv is what i go for .... Good Luck

---

### Post by haqking on 2011-06-28
> **The_Invincible said:**
> Well . As of what i have come through . Antivirus for Linux first  of all do not provide real time protection . If they do , then it requires additional tweaking . Plus , Ubuntu uses many other mechanisms for enhancing security eg. Permissions , Access Levels and much more .

But he is a council member , and if u do not win an argument atleast go ahead and install a free virus protection . ClamAv is what i go for .... Good Luck 


what you have come through ? would infer you had a virus infection in linux ? or do i read that wrong ?

---

### Post by idoitprone on 2011-06-28
> **e79 said:**
> + 1 for ClamAV



Just lol....he obviously don't know what he's talking about.... and i bet he's scare of the word Linux because he don know much about it....ask him in what way Linux is less secure than windows if Google Farms are running on a custom flavor or Unix...
[http://en.wikipedia.org/wiki/Google_platform](http://en.wikipedia.org/wiki/Google_platform)


it sound like he is afraid of losing his job. Window is getting replace by the unix guy

---

### Post by lisati on 2011-06-28
I have AVG free on my Windows partition, and use Clamav to check incoming emails on my server. Other than that, I haven't seen the need.

---

### Post by handy on 2011-06-29
Is there a page in the Ubuntu wiki that is dedicated to a simple & clear explanation of the situation re. Linux & viruses?

If not, there should be, so every time this question gets asked, all we have to do is point the one with the query to the answer.

bodhi, your previous post is a great start for such a page. :)

[I]**[edit:]** I just searched the Ubuntu help wiki, for virus, anti virus, antivirus, anti-virus, & security & got nothing each time.

You know what scares so many of us off from starting to work on the wiki, is that it is so far out of date & there is so much work to be done it is daunting. I don't even use Ubuntu, so I'm at a disadvantage to begin with when it comes to writing in the wiki.[/I]

---

### Post by Buster52 on 2011-06-29
Thanks for the replies. We sent him an email listing serveral virus protection programs that run on Linux and promised to install one of them. That appears to have satisfied him. The measure passed without incident.
 
With a councilman, it is usually easier to just do what he asks than to convince him he is wrong.
 
Thanks again.
 
Buster

---

### Post by haqking on 2011-06-29
> **haqking said:**
> The facts are, is Linux immune to Viruses...then NO

Is it likely, then NOT VERY

But it is free (clamav etc) to protect incase and it certainly wont resource hog your machine like Symantec or other equal products within windows.

Is linux immune to viruses:

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

[http://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses](http://www.linux.com/learn/tutorials/284124-myth-busting-is-linux-immune-to-viruses)

Viruses and malware that can effect Linux:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

The fact is Linux is as likely to be infected with a virus as Windows is as likely to become open source and free of charge ;-)

And the best protection against malware/viruses which will beat any software is user/security awareness training.

> **handy said:**
> Is there a page in the Ubuntu wiki that is dedicated to a simple & clear explanation of the situation re. Linux & viruses?

If not, there should be, so every time this question gets asked, all we have to do is point the one with the query to the answer.

bodhi, your previous post is a great start for such a page. :)

[I]**[edit:]** I just searched the Ubuntu help wiki, for virus, anti virus, antivirus, anti-virus, & security & got nothing each time.

You know what scares so many of us off from starting to work on the wiki, is that it is so far out of date & there is so much work to be done it is daunting. I don't even use Ubuntu, so I'm at a disadvantage to begin with when it comes to writing in the wiki.[/I]

see my earlier post above for a link to wiki on viruses on linux etc though not strictly the ubunut wiki and also [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by handy on 2011-06-29
**@haqking:** Thanks. :)

Out of interest, I thought I'd check the wiki, so I called it via the Ubuntu Help link that is situated in the Ubuntu forum's top right hand corner & then searched for linuxvirus & I still got NOTHING! <doh!>

---

### Post by kaldor on 2011-06-29
Use antivirus if Windows users will be interacting with the Linux machine(s) a lot. Linux isn't immune to malware. Malware can be passed through Ubuntu unnoticed, hence why you should use some sort of AV if you will be sharing stuff with Windows users. 

Someone saying that Linux is less secure than Windows is like saying Linux is better than Windows for hardcore gamers.

---

### Post by Habeouscorpus on 2011-06-29
Did someone say ~*wiki page*~? 

I might be game to write one. Anyone want to help?

---

### Post by handy on 2011-06-29
> **Habeouscorpus said:**
> Did someone say ~*wiki page*~? 

I might be game to write one. Anyone want to help?

There is a wiki page, the problem is that searching for it using all of the ways that you would think would work (& one that you wouldn't - which is its name "Linuxvirus" don't. Which makes it very close to useless, I'm sorry to say.

---

### Post by guzjd on 2011-06-29
I install antivirus regardless of OS because I never know which OS I may be dealing with and as I work with Unix, Linux, and Windows predominately in enterprise environments.
 
This Admin is misinformed. I would refer him to the NSA/CSS or NIST guidelines for Securing Operating Systems. If anything I agree with others here and say Linux has a lot more security features out of the box. To include:

[LIST]
[*]AppArmor or SELinux
[*]Utilities for Cryptography
[LIST]
[*]md5 and sha sum
[*]STRONG encryption
[LIST]
[*]EFS in Windows is not that great
[/LIST]
[/LIST]
[*]Principle of Least Privilege
[LIST]
[*]Who does a better job at implementing this?
[LIST]
[*]Linux gives full admin rights to uid=0 (root); while in Windows the initial user is given full admin rights instead of just the Administrator account
[/LIST]
[/LIST]
[/LIST]Some additional applications that have proven useful are AIDE, Tripwire, Snort, and Rootkit Hunter.
 
With all that being said, I would recommend using antivirus to enhance your overall security posture. 
 
Just ask yourself how this all fits in and balances out with your organizations needs, requirements and the principles of Information Security.
 
BTW  [[COLOR=#980101]**[SIZE=5]bodhi.zazen[/SIZE]**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") has a post on Security in Ubuntu and may help those new to the Linux world.

---

### Post by handy on 2011-06-29
**@Habeouscorpus:** You should PM manzdagratiano as he has been doing some seriously good work on the wiki & would love some help.

---

### Post by Habeouscorpus on 2011-06-29
> **handy said:**
> **@Habeouscorpus:** You should PM manzdagratiano as he has been doing some seriously good work on the wiki & would love some help.

I will do that! Also, First order of business is making that page easy to find. Thanks guys!

---

### Post by handy on 2011-06-29
> **guzjd said:**
> 
I install antivirus regardless of OS because I never know which OS I may be dealing with and as I work with Unix, Linux, and Windows predominately in enterprise environments. 

Courses for horses. The way that you work is not the way the most of us here do. If we are in an environment such as yours then we would take the appropriate steps to secure it.
 
> **guzjd said:**
> 
This Admin is misinformed. 

I doubt it.

> **guzjd said:**
> 
...

With all that being said, I would recommend using antivirus to enhance your overall security posture. 
 
OSX, & Linux systems that aren't serving Windows machines still do not need antivirus protection as there is no threat. 

> **guzjd said:**
> 
Just ask yourself how this all fits in and balances out with your organizations needs, requirements and the principles of Information Security. 
 
Again:- Most of us don't have an organisation. If we do then we have already asked ourselves that question & have taken the appropriate steps - which I'll say again, again, are only necessary if you are serving Windows machines.

---

### Post by haqking on 2011-06-29
Though not on the actual wiki is is on the Official Ubuntu Documentations and easily searchable

[https://help.ubuntu.com/](https://help.ubuntu.com/)

is there an actual Wiki page then cause i couldnt find that at all

---

### Post by handy on 2011-06-29
> **Habeouscorpus said:**
> I will do that! Also, First order of business is making that page easy to find. Thanks guys!

No! We thank you, profusely, indeed.

---

### Post by handy on 2011-06-29
> **haqking said:**
> Though not on the actual wiki is is on the Official Ubuntu Documentations and easily searchable

[https://help.ubuntu.com/](https://help.ubuntu.com/)

is there an actual Wiki page then cause i couldnt find that at all

When I search that page I draw a blank, & I tried all the possible antivirus word combinations & Linuxvirus which is the actual name of the page.

I have allowed the page in NoScript, so I really shouldn't be blocking myself with a Firefox add-on.

---

### Post by guzjd on 2011-06-29
Handy:  
 
I understand your POV.  I deal with large enterprise deployments predominately and am giving my perspective.  Take it for what it is, information.
 
I've seen plenty of admins get terminated over Unix and Linux Servers compromises because they fall into the trap of not fully implementing protections.
 
Think of the dangers of Social Engineering... 
 
What if I told you it was safe to install an application on your hosts, are you going to review it beforehand or take my word for it?
 
Security is supposed to be "layered" in the environments I work in.

---

### Post by haqking on 2011-06-29
> **handy said:**
> When I search that page I draw a blank, & I tried all the possible antivirus word combinations & Linuxvirus which is the actual name of the page.

I have allowed the page in NoScript, so I really shouldn't be blocking myself with a Firefox add-on.

thats weird.

I can search for virus, antivirus, linux virus, linuxvirus

and it brings me to what i need everytime mainly the following:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) and
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

weird ?

---

### Post by handy on 2011-06-29
> **haqking said:**
> thats weird.

I can search for virus, antivirus, linux virus, linuxvirus

and it brings me to what i need everytime mainly the following:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) and
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

weird ?

Sometimes I think that the add-ons & edits that I've made to Firefox in the interest of security lock me out of things. 

It happens rarely enough that it doesn't bother me & fits with my browsing mentality that will not use a site if for *_whatever_* reason I don't like it. 

Such a reason can be that I can't see it properly, though that is really quite rare. (There are a pile of other reasons too.)

Anyway ??? I likely prefer my settings as they are, as in general I don't miss what I miss. :)

---

### Post by haqking on 2011-06-29
> **handy said:**
> Sometimes I think that the add-ons & edits that I've made to Firefox in the interest of security lock me out of things. 

It happens rarely enough that it doesn't bother me & fits with my browsing mentality that will not use a site if for *_whatever_* reason I don't like it. 

Such a reason can be that I can't see it properly, though that is really quite rare. (There are a pile of other reasons too.)

Anyway ??? I likely prefer my settings as they are, as in general I don't miss what I miss. :)

ha yeah i hear ya.  For the most part i do a global allow for the Ubuntu based sites (probably too trusting but there you go ;-)

---

### Post by handy on 2011-06-29
> **guzjd said:**
> 
Handy:  
 
I understand your POV.  I deal with large enterprise deployments predominately and am giving my perspective.  Take it for what it is, information. 
 
It is valuable input too, thanks. :)

> **guzjd said:**
> 
I've seen plenty of admins get terminated over Unix and Linux Servers compromises because they fall into the trap of not fully implementing protections. 
 
System security is becoming increasingly important every day, so I can fully appreciate what you say there.

> **guzjd said:**
> 
Think of the dangers of Social Engineering... 
 
What if I told you it was safe to install an application on your hosts, are you going to review it beforehand or take my word for it?
 
Security is supposed to be "layered" in the environments I work in.

Reminds me of that movie about Kevin Mitnick, that made social engineering infamous.

---

### Post by haqking on 2011-06-29
> **handy said:**
> 

Reminds me of that movie about Kevin Mitnick, that made social engineering infamous.


Takedown...grossly biased movie ;-)

---

### Post by handy on 2011-06-29
> **haqking said:**
> Takedown...grossly biased movie ;-)

I know, whilst I was watching it on my computer I paused it, went to another desktop & searched for info'/history on Mitnick. He wasn't too happy about the story if I remember correctly.

---

### Post by haqking on 2011-06-29
> **handy said:**
> I know, whilst I was watching it on my computer I paused it, went to another desktop & searched for info'/history on Mitnick. He wasn't too happy about the story if I remember correctly.


yeah, Freedom Downtime from 2600 (it is on youtube and google videos or torrent)

is a slightly more (though this time mitnick biased) realistic non hollywood take on it ;-)

---

### Post by owiknowi on 2011-06-29
maybe it would be sensible to search companies/organizations in your vicinity who have more experience with linux based servers?
ask them about the pros and cons and how they implemented it..
afaik: a lot of very big data and server centers use linux as server software...

try to find out why that guy is unwilling. maybe he has reached a comfortable position in his career with his 'knowledge' of only ms w.?

every change brings risks with it too, and maybe that's what he's afraid of: learning new things, having to report on new matters he doesn't quite understand?

in general we are pretty conservative, and with good reason i believe, since life is no picknick.

my experience within government and bigger organizations is that, maybe due to their hierarchical structure, people often reach positions for which they are actually not well suited.

hope you succeed and also still have a bit of fun with it in the bargain!
see: sun tzu, the art of war, or maybe more accurate: reach your goals with knowledge, respect and minimal damage and suffering. 
_O_

---

### Post by bodhi.zazen on 2011-06-29
> **guzjd said:**
> Handy:  
 
I understand your POV.  I deal with large enterprise deployments predominately and am giving my perspective.  Take it for what it is, information.
 
I've seen plenty of admins get terminated over Unix and Linux Servers compromises because they fall into the trap of not fully implementing protections.
 
Think of the dangers of Social Engineering... 
 
What if I told you it was safe to install an application on your hosts, are you going to review it beforehand or take my word for it?
 
Security is supposed to be "layered" in the environments I work in.

Security is a skill and one needs to consider a number of factors, clients, servers, value of the data, etc.

Because of this, one can not make statements that apply to everyone.

In general, antivirus adds little or nothing to Linux security on a Desktop because there are no known active linux viruses of significance. If that changes , so would the advice for antivirus. As the threats change, so does the response.

Antivirus is reactive, it acts after the virus has already done it's damage, so there is no need to install it proactively, it will work just as well after the fact.

That is not the same as saying there is no role for antivirus. The potential uses for antivirus on Linux have been outlined on the wiki page:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

If you want to have a rational discussion on antiviurs you need to specify the user case.

As this is not a support thread in that there is not a specific request for support on a specific user case I am moving it from security to recurring discussions.

If you want to actually learn Linux security, I highly advise selinux or apparmor, both are fare more secure then antivirus.

---

### Post by psusi on 2011-06-29
It doesn't even make sense to bother scanning a file server that has windows clients.  Those windows clients will already have their own antivirus anyhow, or they would just get infected from sources other than the file server.

Besides, I don't think there are any true virus out there these days; just trojans, worms, and malware, which spread through email and web sites, not by infecting other programs.

Back in the DOS days you had to be careful about your executables on the file server because an infected client would actually infect that executable on the server when they tried to run it, but I don't think there has ever been a windows virus like that.

---

### Post by handy on 2011-06-29
Back in the Amiga days you had to suspect every disk of carrying a boot sector virus. At one point for a short time even the Workbench disks that came with a new computer had a virus that infected the CMOS on board clock!

They were the good old days. :D 

[http://vxheavens.com/lib/arr00.html](http://vxheavens.com/lib/arr00.html)

---

### Post by createdcreature on 2011-07-02
I have used Linux on a server for a year now and it has never been not functioned properly.

---

