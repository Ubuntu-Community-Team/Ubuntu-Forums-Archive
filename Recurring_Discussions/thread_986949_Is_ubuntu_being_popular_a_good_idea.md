---
title: "Is ubuntu being popular a good idea?"
date: 2008-11-19
forum: Recurring Discussions
---

### Post by Karilex on 2008-11-19
Now I'm all for popularity and this isn't some cranky old man's rant about ubuntu (no offense to cranky old men) but is ubuntu's increasing popularity necessarily a good thing security wise i mean if linux/ubuntu becomes too popular won't hackers and other evil entities decide to get off their lazy buts(no offense to hackers and evil entities) and start making viruses and other nasties dedicated to linux/ubuntu I know that with root and everything linux/ubuntu is waay more secure than windows and only my home folder can get infected but i like my home folder so is linux/ubuntu being popular good?

Have a nice day and thanks for reading 

PS: if you feel that what i said is ridiculous feel free to include a note asking me to beat myself with a cane at the end of your post i will gladly oblige.

---

### Post by hyper_ch on 2008-11-19
> **Karilex said:**
> Now I'm all for popularity and this isn't some cranky old man's rant about ubuntu (no offense to cranky old men) but is ubuntu's increasing popularity necessarily a good thing security wise i mean if linux/ubuntu becomes too popular won't hackers and other evil entities decide to get off their lazy buts(no offense to hackers and evil entities) and start making viruses and other nasties dedicated to linux/ubuntu 

No... (maybe a little)

Number on base installs does not directly correlate to the number of malware:

- The most used webserver is apache
- However IIS gets targeted a lot more and breaken a lot more into

Rationale: You have to calculate to total "ROI" (return on investements). For this you have to take into account

- how difficult is it to exploit the remote computer
- by getting access to one service, what can you do with it
- how many base installs are there

Now take into consideration that (a) the source code for linux and apache is easily available and (b) that the source code for IIS isn't. This would indicate that it is a lot simpler to find a weakness and get access to it.

However you will still be limited to just apache due to the separation of apache and the rest of the system.

In case of IIS, if you can get access to IIS (or internet explorer or ....) then you "own" the whole computer.

Furthermore you don't have just "one" linux platform. You have all those different distributions and system (ix86, sparc, arm, .....) that will make it even more difficult to get a decent ROI even if Linux or one distro becomes more popular.

Fact is despite lacking availabilty source code of IIS it gets hacked/breaken into a lot more than apache.

---

### Post by patrickballeux on 2008-11-19
I would say yes because now, you go on some closed source softwares and have a package version of their product for Ubuntu.  (Skype, Adobe, etc...)

It means that Ubuntu is making it's way not only in the open source world but also in the closed source world.

And that's good for us...


So now, we just have to be ready for a new horde of newbie that will installed anything on everything...  I am more affraid of the user than any particuliar software that could let any trojan/virus in...


My 2 cents.

---

### Post by cdenley on 2008-11-19
Obscurity isn't the best defense from hackers, but I think it helps. As Ubuntu (or Linux in general) becomes more popular, it will become more of a target. However, at the same time, the source code will probably be reviewed by more people as more depend on it's security.

I don't think there is an operating systems which aims to be obscure, but maybe that's because it's so obscure that I never heard of it. If you want a very secure and obscure operating system, use OpenBSD. If you want a  easy-to-use but not quite as secure as OpenBSD OS with a large support community, use Ubuntu.

---

### Post by hyper_ch on 2008-11-19
> **cdenley said:**
> Obscurity isn't the best defense from hackers, but I think it helps. As Ubuntu (or Linux in general) becomes more popular, it will become more of a target. However, at the same time, the source code will probably be reviewed by more people as more depend on it's security.

I don't think there is an operating systems which aims to be obscure, but maybe that's because it's so obscure that I never heard of it. If you want a very secure and obscure operating system, use OpenBSD. If you want a  easy-to-use but not quite as secure as OpenBSD OS with a large support community, use Ubuntu.

Obscurity doesn't work... look at windows. OpenBSD is not obscure, the source code is freely available also.

---

### Post by cdenley on 2008-11-19
> **hyper_ch said:**
> Obscurity doesn't work... look at windows. OpenBSD is not obscure, the source code is freely available also.

By obscure operating system, I meant it would be uncommon. OpenBSD is much more uncommon than Linux. Windows certainly isn't obscure (uncommon). OpenBSD is one of the most obscure OS's I know of, but I guess it's all relative. Obscurity does help, but isn't a definitive solution. Changing the port for ssh to something high and obscure (uncommon) is a very common security practice. It stops nearly all automated attacks, and decreases the chances your server will be compromised. Of course, it isn't a definitive solution, since attackers can still find it if they look hard enough.

I guess you're interpreting obscure OS in the sense of the functionality or source code being hidden. If you read my post in the context of the entire thread, you will see it differently. Preventing attackers from having access to the source code is a security benefit. However, it is greatly outweighed by the benefit of allowing the open-source community access to the source code as well.

---

### Post by HermanAB on 2008-11-19
Uhmmm, Linux isn't obscure at all.  There are far more Linux machines directly on the internet than Windows machines.  Windows machines are usually hidden behind dinky little Linux based firewalls in a vain effort to keep them safe.  

Linux servers are juicy targets since they tend to be on high speed optical fibre links. So if a spammer can compromise a Linux server, then he can send out tons more spam than with a whole farm full of Windows machines on comparatively slow DSL modems.

Don't be fooled by skewed marketing statistics indicating that Linux has a small market share.  Obviously Ford is the most important manufacturer of F150 trucks with near 100% market share.

If you look at the total computer market, then Linux runs on more than 2 billion devices (mostly cell phones and routers) versus Windows on about 600 million devices.  Now ask yourself when last you had a virus on your cell phone...

Cheers,

Herman

---

### Post by aysiu on 2008-11-19
More popularity for Ubuntu (desktops/laptops, not servers) will mean more attacks of the social engineering type ("You need a special codec to view this webpage. Click here to get it") and it will also mean more users who are likely to fall for such attacks.

I know there are tech-savvy people and not-so-tech-savvy people on Mac, Windows, and Linux, but I think the concentration of not-so-tech-savvy people (the kind who are more likely to fall for social engineering-based malware) is higher among Mac and Windows users, because preinstalled systems for Mac and Windows are more common.

If Ubuntu becomes one of the *de facto* standards of preinstalled systems for home consumers, then you can bet your bottom dollar that all sorts of social engineering attacks will affect users in droves. Ironically, many of these will be of the "You have a virus. Click here to remove it" variety (hint: the click is what helps to install the malware, not remove the previously non-existent malware).

I don't really see how a self-replicating virus could work on Ubuntu unless people start enabling all sorts of unnecessary network services without locking them down and also use easy-to-guess dictionary passwords and enable remote root logins.

If you're worried about your computer, educate yourself about social engineering and how to avoid it, use strong passwords, don't enable network services you don't know how to lock down properly, and back up your important files regularly. If you do all that, it won't matter how popular Ubuntu gets, as far as the security of your computer is concerned.

---

### Post by Paqman on 2008-11-19
I'll take guaranteed improved hardware support in exchange for a theoretical risk of more malware any day. 

Hardware support is the single biggest problem Linux has, and that will only come with more users.

---

### Post by cmay on 2008-11-19
> If Ubuntu becomes one of the *de facto* standards of preinstalled systems for home consumers, then you can bet your bottom dollar that all sorts of social engineering attacks will affect users in droves. Ironically, many of these will be of the "You have a virus. Click here to remove it" variety (hint: the click is what helps to install the malware, not remove the previously non-existent malware).i do not think so. it will take advantage of a few commercial programs that already has opened backdoors like it already does on windows. there will maybe come some more social enginering targeted at linux users but in the end if it was possible to abuse the system the same way it can be done with windows then it would already had happened. i have been hacked on windows more than twice but also on ubuntu as result of doing the same things as i did as a windows user ,eq install strange things from outside the respotories  and that is the only way i can see other than fake emails or trick sites that looks like as the example install adobe flash sites. the rootkit was invented on unix but there is still not so much chances at getting such things if only stay away from commercial programs with out full open sources and stick to using only the programs in the respotories. so in fact instead of looking for vira protection a linux user must help improve betatest and translate the software to protect one self and still have many programs.

but i am no expert in security.it is just how i think it is.

---

### Post by aysiu on 2008-11-19
I'm not talking about "hacking" (or "cracking," as some like to call it in this context). I'm talking about being tricked into installing something, and yes there's absolutely no reason it couldn't happen in Linux.

Obviously popularity has to do with targeting for social engineering. How many Linux users have laughed when they get an "antivirus" pop-up that has Windows XP borders on a clearly non-Windows Linux theme?

If you were in the shoes of an attacker who wanted to exploit social engineering, would you create tricks to fool Windows users or Linux users? I'd pick Windows users any day, for the following reasons: [list][*]I know there are plenty of easily fooled Windows users and not so many easily fooled Linux users[*]Windows XP defaults to an administrator account, so no password authentication is probably needed to affect system files[*]Windows users are used to double-click-installing stuff downloaded off the internet; Linux users are used to using trusted repositories to find software[/list]

---

### Post by wersdaluv on 2008-11-19
> **Karilex said:**
> Now I'm all for popularity and this isn't some cranky old man's rant about ubuntu (no offense to cranky old men) but is ubuntu's increasing popularity necessarily a good thing security wise i mean if linux/ubuntu becomes too popular won't hackers and other evil entities decide to get off their lazy buts(no offense to hackers and evil entities) and start making viruses and other nasties dedicated to linux/ubuntu I know that with root and everything linux/ubuntu is waay more secure than windows and only my home folder can get infected but i like my home folder so is linux/ubuntu being popular good?

That's a long sentence you've got there. 

Anyway, I guess, Linux will still be as secure even if Ubuntu becomes more and more popular. Geeks will always find a way to kill bad software sources.

---

### Post by cardinals_fan on 2008-11-19
> **cmay said:**
> i do not think so. it will take advantage of a few commercial programs that already has opened backdoors like it already does on windows. there will maybe come some more social enginering targeted at linux users but in the end if it was possible to abuse the system the same way it can be done with windows then it would already had happened. i have been hacked on windows more than twice but also on ubuntu as result of doing the same things as i did as a windows user ,eq install strange things from outside the respotories  and that is the only way i can see other than fake emails or trick sites that looks like as the example install adobe flash sites. the rootkit was invented on unix but there is still not so much chances at getting such things if only stay away from commercial programs with out full open sources and stick to using only the programs in the respotories. so in fact instead of looking for vira protection a linux user must help improve betatest and translate the software to protect one self and still have many programs.

but i am no expert in security.it is just how i think it is.
Social engineering by definition requires the user to do something foolish.  It is really quite easy to compromise **any** operating system if the user lets you.

---

### Post by Karilex on 2008-11-19
> **aysiu said:**
> 

If Ubuntu becomes one of the *de facto* standards of preinstalled systems for home consumers

one word: eeepc
Also the only thing that could currently go wrong can be avoided by installing no-scrpit and not being stupid but if ubuntu becomes very popular to the mainstream public it will be easy for people to get into ubuntu computers since a lot of people aren't really all that tech savy and may inadvertently make stupid mistakes

---

### Post by Karilex on 2008-11-20
> **wersdaluv said:**
> That's a long sentence you've got there. 

I don't believe in breathing between sentences and I think those little dots look suspicious

---

### Post by tsali on 2008-11-20
> **aysiu said:**
> More popularity for Ubuntu (desktops/laptops, not servers) will mean more attacks of the social engineering type ("You need a special codec to view this webpage. Click here to get it") and it will also mean more users who are likely to fall for such attacks.

I know there are tech-savvy people and not-so-tech-savvy people on Mac, Windows, and Linux, but I think the concentration of not-so-tech-savvy people (the kind who are more likely to fall for social engineering-based malware) is higher among Mac and Windows users, because preinstalled systems for Mac and Windows are more common.

If Ubuntu becomes one of the *de facto* standards of preinstalled systems for home consumers, then you can bet your bottom dollar that all sorts of social engineering attacks will affect users in droves. Ironically, many of these will be of the "You have a virus. Click here to remove it" variety (hint: the click is what helps to install the malware, not remove the previously non-existent malware).

I don't really see how a self-replicating virus could work on Ubuntu unless people start enabling all sorts of unnecessary network services without locking them down and also use easy-to-guess dictionary passwords and enable remote root logins.

If you're worried about your computer, educate yourself about social engineering and how to avoid it, use strong passwords, don't enable network services you don't know how to lock down properly, and back up your important files regularly. If you do all that, it won't matter how popular Ubuntu gets, as far as the security of your computer is concerned.

Yes! +1

---

### Post by tsali on 2008-11-20
> **cmay said:**
> i do not think so. it will take advantage of a few commercial programs that already has opened backdoors like it already does on windows. there will maybe come some more social enginering targeted at linux users but in the end if it was possible to abuse the system the same way it can be done with windows then it would already had happened. i have been hacked on windows more than twice but also on ubuntu as result of doing the same things as i did as a windows user ,eq install strange things from outside the respotories  and that is the only way i can see other than fake emails or trick sites that looks like as the example install adobe flash sites. the rootkit was invented on unix but there is still not so much chances at getting such things if only stay away from commercial programs with out full open sources and stick to using only the programs in the respotories. so in fact instead of looking for vira protection a linux user must help improve betatest and translate the software to protect one self and still have many programs.

but i am no expert in security.it is just how i think it is.

By far, the least cost method of getting what you want from someone is to convince them to give it to you. The vast majority of cybercrime doesn't involve direct attack, but includes a social vector to get the user to open the door.

I have some experience with this. It is very, very easy to get someone to enter their root password into a dialog when they believe they are installing something desirable (a weather bug, p2p program, music player, browser "plug-in", etc.)

---

### Post by lakersforce on 2008-11-20
Short comment: Most of malware problems on Windows comes from uneducated (read: stupid) users!

---

### Post by ronnielsen1 on 2008-11-20
>  I think those little dots look suspicious
:lolflag:
I could see an increase of certain types of malware as more companies offer closed source downloads for linux but not to the extent of windows.

---

### Post by tsali on 2008-11-20
> **lakersforce said:**
> Short comment: Most of malware problems on Windows comes from uneducated (read: stupid) users!

Short response: only stupid people equate being uneducated with being stupid.

Mark Twain said 'Never let your schoolin' interfere with your education'

---

### Post by cdenley on 2008-11-20
> **tsali said:**
> Short response: only stupid people equate being uneducated with being stupid.

Mark Twain said 'Never let your schoolin' interfere with your education'

I think what you mean is "only stupid people equate being unschooled with being stupid", given the context of your quote.

uneducated equals stupid
educated doesn't equal schooled
schooled doesn't equal smart

---

### Post by lancest on 2008-11-20
Distro's can just warn users use only the package manager to install software. How many active viruses for Windows 60,000? And Linux has about 4- it runs the interent and they aren't active. I think it's safe to say Linux will never numerically have the huge security problems Windows does. Apple sure doesn't.

---

### Post by tsali on 2008-11-20
> uneducated equals stupid

No, it doesn't. My grandfather only finished elementary school, but he was one of the most intelligent men I have ever met.

stu&#8901;pid
&#8194; &#8194;/&#712;stup&#618;d, &#712;styu&#8209;/ [stoo-pid, styoo&#8209;] Show IPA Pronunciation
adjective, -er, -est, noun
&#8211;adjective
1. 	lacking ordinary quickness and keenness of mind; dull.
2. 	characterized by or proceeding from mental dullness; foolish; senseless: a stupid question.
3. 	tediously dull, esp. due to lack of meaning or sense; inane; pointless: a stupid party.
4. 	annoying or irritating; troublesome: Turn off that stupid radio.
5. 	in a state of stupor; stupefied: stupid from fatigue.
6. 	Slang. excellent; terrific.
&#8211;noun
7. 	Informal. a stupid person.

Therefore, referring to someone who is uneducated as stupid is offensive and stupid in and of itself.

---

### Post by Karilex on 2008-11-21
> **lancest said:**
> Distro's can just warn users use only the package manager to install software. How many active viruses for Windows 60,000? And Linux has about 4- 

True with today's methods it is impossible for linux to have the same security issues windows does but remember that is mainly because no one is adapting things to hijack linux it's not worth the trouble but what i meant was what if linux one day takes over the market then people will have to adapt their hacking methods or just give up since everyone will be using linux and sure they can just warn users but there are other methods again harder and more of a drag but still they exist.

ps: No i won't punctuate my sentences except at the end.

---

### Post by hyper_ch on 2008-11-21
> **Karilex said:**
> because no one is adapting things to hijack linux it's not worth the trouble

lol ;)

sure it's worth the trouble... e.g. google runs all on linux. Take over their server, manipulate their search result and you will be topranked with your viagara (or whatever product) for any search...

Or hijacking dns servers to redirect all quersies to your IPs...

that would generate a lot more cash than all those mail spam botnets...

---

### Post by cdenley on 2008-11-21
> **tsali said:**
> No, it doesn't. My grandfather only finished elementary school, but he was one of the most intelligent men I have ever met.

stu&#8901;pid
&#8194; &#8194;/&#712;stup&#618;d, &#712;styu&#8209;/ [stoo-pid, styoo&#8209;] Show IPA Pronunciation
adjective, -er, -est, noun
–adjective
1. 	lacking ordinary quickness and keenness of mind; dull.
2. 	characterized by or proceeding from mental dullness; foolish; senseless: a stupid question.
3. 	tediously dull, esp. due to lack of meaning or sense; inane; pointless: a stupid party.
4. 	annoying or irritating; troublesome: Turn off that stupid radio.
5. 	in a state of stupor; stupefied: stupid from fatigue.
6. 	Slang. excellent; terrific.
–noun
7. 	Informal. a stupid person.

Therefore, referring to someone who is uneducated as stupid is offensive and stupid in and of itself.

I think you should re-read my post, and your Mark Twain quote.

education: the gradual process of acquiring knowledge

My point was that education does not imply formal education. Your grandfather may not have much of a formal education, but he gained his knowledge through some sort of process, which would be his education. In other words, your grandfather didn't have to worry about his schooling interfering with his education. As demonstrated by your own quote, the two are not the same. Your grandfather sounds like an educated man.

I wouldn't argue that a formal education is necessary in order to be intelligent. I seem to have more computer knowledge than most people with a degree in computers, yet I never finished college.

---

### Post by beno1990 on 2008-11-21
Security through obscurity is a fallacy; Unix and Unix-like operating systems tend to be more secure than Windows to begin with.

Sure, the amount of malware on Linux might increase, but I'd wager that the only way it'll be able to get on people's computers properly is through user-error, for example running an untrusted script with the sudo command or whatever.

---

### Post by Karilex on 2008-11-21
> **hyper_ch said:**
> lol ;)

sure it's worth the trouble... e.g. google runs all on linux. Take over their server, manipulate their search result and you will be topranked with your viagara (or whatever product) for any search...

Or hijacking dns servers to redirect all quersies to your IPs...

that would generate a lot more cash than all those mail spam botnets...

Ah yes I just got proved wrong but I was mainly talking about people's interest in the home computer although if you were able to take over the google server that wouldn't be half bad either :lolflag:

---

### Post by hyper_ch on 2008-11-21
you have to ask yourself why would other people want to take over your computer? Mostly for turning it into a zombie in a spam botnet or ddos attack or or or... basically it's very likely the only motivation is to make money somehow ;)

---

### Post by Karilex on 2008-11-22
> **hyper_ch said:**
> you have to ask yourself why would other people want to take over your computer? Mostly for turning it into a zombie in a spam botnet or ddos attack or or or... basically it's very likely the only motivation is to make money somehow ;)

I never said it wasn't :D

---

### Post by lakersforce on 2008-11-24
> **tsali said:**
> Short response: only stupid people equate being uneducated with being stupid.

You are missing the point entirely! If Ubuntu (and GNU/Linux in general) becomes so popular that the average Joe is beginning to use it, of course it will see it's share of malware and viruses. The days when a virus where made by a kid in a garage is (for the most parts) over. Computer-fraud is big business!
And when your average computer-user, who does not know what a browser is, though he uses it every day, comes to GNU/Linux, then the people who wants to take away his money are going to follow him.

---

### Post by Grant A. on 2008-11-24
> **lakersforce said:**
> You are missing the point entirely! If Ubuntu (and GNU/Linux in general) becomes so popular that the average Joe is beginning to use it, of course it will see it's share of malware and viruses. The days when a virus where made by a kid in a garage is (for the most parts) over. Computer-fraud is big business!
And when your average computer-user, who does not know what a browser is, though he uses it every day, comes to GNU/Linux, then the people who wants to take away his money are going to follow him.

Not really, Linux is built on a much more secure base than Windows. Windows ALLOWS spyware to install itself, it has 1,000s of ports open just waiting to be manipulated, and it doesn't get patches nearly as fast as Linux. Linux doesn't have any 'wild' malware because Linux has developers from all over the world online all day, all the time, fixing and cooperating to patch any flaws in the kernel that would result in malware to become a problem. Also, don't use the excuse that Windows is less secure because it has more users, Mac OS X has a much larger userbase than Linux, and only has 2 viruses compared to Linux's 30 viruses. And Linux viruses are only proof-of-point viruses and are quickly patched and not around anymore. Linux currently has only 1 virus that was taken care of already by a patched vulnerability. Btw, Mac OS X has a common ancestor to Linux called 'System V' ;)

---

### Post by lakersforce on 2008-11-24
> **Grant A. said:**
> Not really, Linux is built on a much more secure base than Windows. Windows ALLOWS spyware to install itself, it has 1,000s of ports open just waiting to be manipulated, and it doesn't get patches nearly as fast as Linux.

If 95% of the world used GNU/Linux, I betcha you are wrong! In my opinion, saying that GNU/Linux can't get viruses "because it's less error prone" is naive!
> And Linux viruses are only proof-of-point viruses...

How do you know? Did you build it? Or did you just read this somewhere?

> Linux currently has only 1 virus that was taken care of already by a patched vulnerability.

And what about malware? I even see a good deal from time to time on this forum (though not much and it's usually removed quickly by administrators).

But a point about few problems in GNU/Linux is that it's users are fairly educated when it comes to security.

One thing to remember though is that a computer system is never more than it's users!

---

### Post by Grant A. on 2008-11-24
> **lakersforce said:**
> If 95% of the world used GNU/Linux, I betcha you are wrong! In my opinion, saying that GNU/Linux can't get viruses "because it's less error prone" is naive!


Actually it's true, several companies have done security audits on the kernel and even conventions are held where people try to find vulnerabilities in the OS just to make it better.

> 
How do you know? Did you build it? Or did you just read this somewhere?


It's common knowledge. Most of these malware actually have been made during black hat conventions and are made just to patch a vulnerability and prove a point. I read about this from the summaries of the events.

> 
And what about malware? I even see a good deal from time to time on this forum (though not much and it's usually removed quickly by administrators).

Stop spreading a myth!

Currently the only way to get malware of any kind in Linux is to compile it yourself from the source code. You can ask anyone here on the forums that, and they will tell you. Linux isn't prone to "drive-by" downloads, proven at black hat conventions.

---

### Post by cmay on 2008-11-24
> **lakersforce said:**
> You are missing the point entirely! If Ubuntu (and GNU/Linux in general) becomes so popular that the average Joe is beginning to use it, of course it will see it's share of malware and viruses. The days when a virus where made by a kid in a garage is (for the most parts) over. Computer-fraud is big business!
And when your average computer-user, who does not know what a browser is, though he uses it every day, comes to GNU/Linux, then the people who wants to take away his money are going to follow him.
i once  tried to do this:
a:
go google and find you tube . stumble upon how to crack windows xp
b:
try to do this on my ubuntu system and on a virtual xp install.
c:
give up on ubuntu since i was not root so it could not be done. even if i wanted to it was hard. on windows. succes. 
d:
get rid of virtual box and windows xp. 


but getting virus is pretty easy. just go to random site and fetch stuff until you hit a place with a linux virus written to be installed as root and download the sources and run 
./configure 
make 
make install
and set up how you would like it to behave. 
if linux goes very popular maybe it could happen with spyware in a commercial application but not as it does on windows for that very reason. its safe from synaptic .
the ting is then . when you surf the internet why do you not even need to download anything to get infected on a windows machine. ?

edit:
found a good example.
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by lakersforce on 2008-11-24
I would like to add to this discussion (to prove my point) that I have been a Windows (and ms-dos) user for many years, and I have _never_ had an infection.

That's why I think that it all comes down to the user. But I agree that GNU/Linux is less prone to get infections by design. But one thing is design, another is user interaction.

---

### Post by ranch hand on 2008-12-05
I feel that a reply from a cranky old man is needed here.  I am all in favor of more popularity and the additional risk.

I ran under MS, both DOS and Windows for 15 years and avoided all but one piece of malware and that was removed less than 30 minutes after the invasion.  I was aware of the danger from that site, USair, that I needed to use IE for.  Did my stuff and got offline.  Scanned, found, got rid of, went back to Netscape.

If you do stupid things you will get infected.  If not, you probably will not.

An up to date linux box is going to be a harder nut to crack than one under MS.

---

### Post by KaiTheory on 2008-12-08
Why is Ubuntu so popular anyway? Upon starting grad school this year I was pleased to discover a good number of my new colleagues were all Linux users. However they were all using Ubuntu and I was the only one using Fedora! Well, here I am...peer pressure? I did notice these dudes were a bit "noobier" than the typical Linux user I was used to. One guy even said, "why would I ever want to use the command line when there's a GUI that can do that." *shudder*

---

### Post by lancest on 2008-12-08
We should remember that any Linux distro is still considered "on the fringe" of desktop computing by many. Ubuntu being popular is good although we must hold our noses sometimes. This is the price we pay to get better driver support. I am truly amazed at how far Linux has come since I started using it in 1997.

---

