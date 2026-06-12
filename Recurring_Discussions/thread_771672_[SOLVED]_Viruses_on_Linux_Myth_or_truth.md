---
title: "[SOLVED] Viruses on Linux Myth or truth?"
date: 2008-04-27
forum: Recurring Discussions
---

### Post by tropdoug on 2008-04-27
I am making the transition from vista and xp to Ubuntu. I have now reached the stage of having an almost fully functional system with the programs I want, so thats great. However on MS I suffered some trojan and worm attacks a while ago. I am told that Linux does not have the same issues with viruses etc, but then I see that there are available commercially virus checking programs specifically for Linux, so the question is, do I need to install these types of programs, or is the security of Ubuntu sufficient on its own?

---

### Post by pacsum on 2008-04-27
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses#Threats)

I would say it's quite secure.

---

### Post by dondad on 2008-04-27
> **tropdoug said:**
> I am making the transition from vista and xp to Ubuntu. I have now reached the stage of having an almost fully functional system with the programs I want, so thats great. However on MS I suffered some trojan and worm attacks a while ago. I am told that Linux does not have the same issues with viruses etc, but then I see that there are available commercially virus checking programs specifically for Linux, so the question is, do I need to install these types of programs, or is the security of Ubuntu sufficient on its own?

Those anti-virus programs are to protect Windows users that you might be forwarding stuff to. The viri won't affect your system, but will possibly remain in the content and hit your recipient that is running Windows.

---

### Post by scragar on 2008-04-27
to get a linux virus you actualy have to go out of your way to find, download, make executable, then run with root permtions for it to do any damage, so I'm to go ahead and say that antivirus software for linux is more planning for the future if linux becomes more popular(and thus has more than about 2 viruses per 10 years(that actualy make it more than 2 days in the wild before disapearing :P)). Personaly I don't use one. You don't need a firewall, since IPtables is preinstalled, and works wonderfully, firestarter is a handy monitoring program if wanted.

---

### Post by mgmiller on 2008-04-27
There aren't any viri or trojans in the wild for Linux.  The purpose of those AV programs is to weed out infected files that you might pass along to a windows user.  They can't infect you in any way.  I rely on the AV software in the other guys machine to stop anything I may send him/her.  I don't want to bog my machine down with AV software that I don't need to protect me.

Oh yeah, you never have to defrag either.

Welcome to Ubuntu.

---

### Post by akiratheoni on 2008-04-27
If I recall correctly, most if not all viruses for Linux were developed specifically just to prove Linux could potentially maybe be susceptible to viruses :P So I'd say you're safe. But you can PASS on viruses to Windows computers, so if you're using Linux for a file server or an email server, you'll want to install an anti-virus program on there.

---

### Post by tropdoug on 2008-04-27
Wow thanks guys, that was the easiest of all questions, now I feel secure. :guitar:

---

### Post by mr.lee on 2008-04-27
And now I'm wondering... for Ubuntu, what is the best AV at all? Coz I'm running it as a web server. thx

---

### Post by akiratheoni on 2008-04-27
> **mr.lee said:**
> And now I'm wondering... for Ubuntu, what is the best AV at all? Coz I'm running it as a web server. thx

Your best bet is probably ClamAV. I've never used it but it should be in the repos.

---

### Post by Solrac924 on 2008-04-27
good answer dondad!

---

### Post by Can+~ on 2008-04-27
If you stick to the applications on your repository, then you should have no problems with viruses.

The thing is that viruses do exist, viruses are just code that do damage or try to steal something. As long as you know what you're executing, everything is fine (should apply also to windows). And the Multi-user design of linux makes the potential damage of an attack, lesser.

So yeah, you're pretty safe on linux, but don't go into internet an execute whatever file you run into, be a smart user, try to be on root power the less time possible.

---

### Post by cafeinoz on 2008-04-28
I heard (dont know if its true or false) that some anti-virus software devolopers where making viruses so they could sell us anti-virus software.:(:(:(

---

### Post by p_quarles on 2008-04-28
Moved to Recurring Discussions, as this topic recurs frequently.

Viruses for Linux can and do exist, but none are currently "in the wild." In other words, there are no known threats, and as such, anti-malware software cannot protect you from anything. 

Linux is vulnerable to various attack vectors, it just happens that the underlying design makes a virus one of the least efficient and least likely to succeed methods of attacking. So: yes, you have to think about security, but you have to expand how you think about security. Being careless with passwords and running applications without knowing what you are doing are the big issues. This, amazingly enough, is just as true of Windows as it is of Linux.

---

### Post by WitchCraft on 2008-04-28
> **scragar said:**
> to get a linux virus you actualy have to go out of your way to find, download, make executable, then run with root permtions for it to do any damage, so I'm to go ahead and say that antivirus software for linux is more planning for the future if linux becomes more popular(and thus has more than about 2 viruses per 10 years(that actualy make it more than 2 days in the wild before disapearing :P)). Personaly I don't use one. You don't need a firewall, since IPtables is preinstalled, and works wonderfully, firestarter is a handy monitoring program if wanted.

You should be more careful.

I know there exist 249 rootkits for Linux, plus i probably don't know all... The number of viruses is likely to be much higher.

Plus if you map the user account memory to 0 you can get the equivalent of a root account with a normal user account.

But I agree with the fact, that, at least until now, viruses on Linux are not a problem.

---

### Post by acelin on 2008-04-28
Ubuntu has a built in Virus program to deal with stuff that might crop up. It was implemented with Gutsy I think.

---

### Post by p_quarles on 2008-04-28
> **acelin said:**
> Ubuntu has a built in Virus program to deal with stuff that might crop up. It was implemented with Gutsy I think.
No, no it doesn't.

---

### Post by brian_p on 2008-04-28
> **WitchCraft said:**
> 
I know there exist 249 rootkits for Linux, plus i probably don't know all... The number of viruses is likely to be much higher.

Is that second assertion supposed to have some logical connection with the first one?

> But I agree with the fact, that, at least until now, viruses on Linux are not a problem.

Viruses aren't a problem because there are none.

---

### Post by rune0077 on 2008-04-28
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by brian_p on 2008-04-28
> **rune0077 said:**
> [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Name one in that list which spreads across system boundaries or from system to system without root assistance.

---

### Post by rune0077 on 2008-04-28
> **brian_p said:**
> Name one in that list which spreads across system boundaries or from system to system without root assistance.

I doubt there's any now. But historically speaking, there have been a few that has done major damage. There have always been (and still are) security exploits that allows normal users to obtain root access, and all it really requires is a virus that takes advantage of such exploits.

---

### Post by bikeboy on 2008-04-28
> **cafeinoz said:**
> I heard (dont know if its true or false) that some anti-virus software devolopers where making viruses so they could sell us anti-virus software.:(:(:(

Note sure that it's true, I would be doubtful but not all that surprised. However, Microsoft selling their own anti-malware solutions...To me, *that* is a worry. How about making your OS less susceptible in the first place?

Sorry for the slight off-topic.

---

### Post by rune0077 on 2008-04-28
Everything else said and done, I wouldn't worry if I were you. Yes, viruses are possible, but you'd stand a better chance of winning the lottery than you would of catching one.

---

### Post by xzero1 on 2008-04-28
The discussion of linux virus protection and how a potential virus could infect linux assumes linux is "bug free". There could be some as yet unknown bug that allows for virus penetration. There is no such thing as perfect security for something as complex as an operating system. BTW, most users run foreign code all the time -- ever heard of Javascript?

---

### Post by p_quarles on 2008-04-28
> **xzero1 said:**
> The discussion of linux virus protection and how a potential virus could infect linux assumes linux is "bug free".
Who said that exactly?

> There could be some as yet unknown bug that allows for virus penetration. There is no such thing as perfect security for something as complex as an operating system.
Yes, it is difficult to quantify unknowns. All we have to go on is the historical fact that Linux has been around for a long time, has been a major target for a number of years, and that security problems have not come in the form of viruses. 

> BTW, most users run foreign code all the time -- ever heard of Javascript?
Yes. Don't run your web browser with root privileges.

---

### Post by WitchCraft on 2008-04-28
> **bikeboy said:**
> 
Note sure that it's true, I would be doubtful but not all that surprised. However, Microsoft selling their own anti-malware solutions...To me, *that* is a worry. How about making your OS less susceptible in the first place?

Sorry for the slight off-topic.

You don't need to be doubtful. This is in fact a common practice. It's like the IT department of a large corporation - when they have too few work because their work is too perfect, and they get into danger of having the IT department downsized (=people fired), they start to produce bugs, which they then solve after letting the accountants & co. get desperate for a few hours, which in turn tells the management how important it is to have a competent IT team...

---

### Post by tropdoug on 2008-04-28
> **WitchCraft said:**
> You don't need to be doubtful. This is in fact a common practice. It's like the IT department of a large corporation - when they have too few work because their work is too perfect, and they get into danger of having the IT department downsized (=people fired), they start to produce bugs, which they then solve after letting the accountants & co. get desperate for a few hours, which in turn tells the management how important it is to have a competent IT team...

Nooooo you mean I can't trust the IT department next you will be telling me that **Government** is not trustworthy :lolflag::lolflag:

---

### Post by scragar on 2008-04-29
> BTW, most users run foreign code all the time -- ever heard of Javascript? 
> Yes. Don't run your web browser with root privileges.
I agree about not runnning you browser with root privilages, but javascript is not the problem, since javascript is not able to access anything outside of the browser without some rather strange plugins that exist out there in the world :P The problem with running a browser as root would be the dangers of plugins, and a potential back door to root access by manipulating the browser.

---

### Post by brian_p on 2008-04-29
> **rune0077 said:**
> I doubt there's any now. But historically speaking, there have been a few that has done major damage. There have always been (and still are) security exploits that allows normal users to obtain root access, and all it really requires is a virus that takes advantage of such exploits.

Historically speaking, no damage at all has been done by a virus. There are trojans and worms. Perhaps you are thinking of one of these types of malware?

---

### Post by rune0077 on 2008-04-29
> **brian_p said:**
> Historically speaking, no damage at all has been done by a virus. There are trojans and worms. Perhaps you are thinking of one of these types of malware?

A worm would be the proper term for it, I think. Distinctions varies a little, but the line between what is one and what the other seems a little blurry. But yeah, you're right, worms would be it.

---

### Post by WitchCraft on 2008-04-29
> **tropdoug said:**
> 
Nooooo you mean I can't trust the IT department next you will be telling me that **Government** is not trustworthy :lolflag::lolflag:


:lolflag:
Trust your governemt! They always say the truth. 
You just have to learn to negate everything they say, then you start realize that they actually say the truth ;-)

But I agree, it's sad that you can't even trust the IT department anymore.
:lolflag::lolflag:

---

### Post by Calash on 2008-04-29
> **WitchCraft said:**
> You don't need to be doubtful. This is in fact a common practice. **It's like the IT department of a large corporation - when they have too few work because their work is too perfect, and they get into danger of having the IT department downsized (=people fired), they start to produce bugs, which they then solve after letting the accountants & co. get desperate for a few hours, which in turn tells the management how important it is to have a competent IT team**...

I do what now???

Need to take off that tin-foil hat.

What I have seen are decisions made by people who do not even interact with the computers having negative impacts on the environment.  This is not some secret plot to justify our existence, just good 'ol stupidity.

---

### Post by akiratheoni on 2008-04-29
> **xzero1 said:**
> There could be some as yet unknown bug that allows for virus penetration. 

If it's unknown, how could a virus take advantage of it? It's not like the virus is a self-aware organism that learns as it examines the operating system... it's coded by a human, and if a virus can take advantage of a unknown bug, then another human can find that unknown bug and fix it...

---

### Post by WitchCraft on 2008-04-29
> **Calash said:**
> I do what now???

Need to take off that tin-foil hat.

What I have seen are decisions made by people who do not even interact with the computers having negative impacts on the environment.  This is not some secret plot to justify our existence, just good 'ol stupidity.


Yea, that too. And there certainly is much to blame plain old stupidity for. But what you fail to realize is, that sometimes, some of the stupidity is outright wanted and deliberately provoked... :KS

By the way the example with the accountants is NOT fictious. It's taken from my good old live at the IT department of the postal services...

---

### Post by Calash on 2008-04-30
There are a LOT of stupid people out there, or ones motivated by cutting costs.  In my experience a massive failure, such as one you used for an example, is not a motivation to justify your IT group, but a bullet point on the presentation to why the company should outsource.

---

### Post by WitchCraft on 2008-04-30
> **Calash said:**
> 
In my experience a massive failure ...  a bullet point on the presentation to why the company should outsource.

Yea, I 100% approve with that.

[QUOTE=Goethe]
We need to save money - no matter the costs.
[/QUOTE]

---

### Post by aysiu on 2008-05-02
> **scragar said:**
> to get a linux virus you actualy have to go out of your way to find, download, make executable, then run with root permtions for it to do any damage Unless it comes as .deb, in which case you just double-click it and enter your password to give it root permissions. Social engineering can be successfully regardless of what operating system you use, as long as the user is gullible enough to be tricked.

---

### Post by scragar on 2008-05-02
your right, I know I would proberly fall for that, but my only real argument against is that not all linux distro's use .deb, infact .rpm is more common when searching the internet than .deb - and not all distros use either of those.

:P

---

### Post by HangukMiguk on 2008-05-03
> **scragar said:**
> your right, I know I would proberly fall for that, but my only real argument against is that not all linux distro's use .deb, infact .rpm is more common when searching the internet than .deb - and not all distros use either of those.

:P

Yes, but RPMs still require root priveleges to work.  This is not a trait exclusive to .deb

Moreover, I'd say it's much more prevalent for users to use RPMs from third-party sites than .deb

I could, however, be completely off-base.

---

