---
title: "How does a distro become a distro?"
date: 2012-06-30
forum: Recurring Discussions
---

### Post by Curtis6767 on 2012-06-30
I'm having an argument with a friend about Linux. He says that Linux is prone to viruses, is easy to hack, and that anyone could create a Linux distro filled with viruses that would wreck a person's computer.

I've explained to him that Linux.org (hope that's right) oversees the kernel and that Linux is relatively safe from viruses, but I don't know about the hacking.

What I would like to know, for myself and so I can explain to him, is who is watching to make sure a malicious distro doesn't get released. Is there some kind of organization in place that has to sign off on a distro before it can go public? 

Thanks

---

### Post by xedi on 2012-06-30
This [video]("https://www.youtube.com/watch?v=yVpbFMhOAwE") gives a nice basic overview of Linux development and as you can see is quite regulated so you cannot just put some malicious code in it without anybody noticing. However, even if and that is the strength of open source, there are so many individuals and companies (like Red Hat, Intel, IBM, Google + many more) working and looking at the code thus increasing the chance of finding a security vulnerability*, that the chances are quite good that somebody will notice. 

* Compared to a proprietary OS where you have to rely on a single company to find and fix security issues.

I guess you could always do your own distro with a custom Linux kernel which you modified to be as evil as possible and convince somebody to install it, but I don't know if such thing exists and how likely it would be that you would install it... However, regarding all the established distros this is not the case, obviously. If you don't trust Canonical in the case of Ubuntu you can always look into the Ubuntu code (besides noticing the fact that nobody has reported anything like that.)

---

### Post by David Andersson on 2012-06-30
It's about *trust*

**You have to trust someone. Not everyone. But someone.**

You trust the Linux Kernel Team that they are honest and don't put trojans in. You have to trust Apple or Microsoft if you choose to use their kernels. You trust companies like Canonical or RedHat if you chose one of their distros.

I think linux is a little easier to trust. It is *open source* so if you don't trust them, you only need to trust third parties that eyeball their code (or eyeball it yourself).

**You need to trust more than one. Not everyone. But a few.**

You have to trust Mozilla if you use Firefox, or Google if you use Chrome. GNU if you use Gimp or Gnome. Most of those have open source, so they are much easier to trust than e.g. Skype or Adobe.

**You trust a site. Or a few.**

If you find an Ubuntu download at *ubuntu.com* it is much safer than if you find something claiming to be Ubuntu on *cracked-softwarez.biz*. (If you download via a torrent file from ubuntu.com, you are actually downloading the iso file from numerous unknown personal computers around the world, but it is still as safe as a direct download, because the iso file is automatically checked against the hash signatures in the torrent file.)

Windows users typically trust sites like softpedia and tucows for downloading free Windows programs.

---

### Post by GreatDanton on 2012-06-30
> **Curtis6767 said:**
> I'm having an argument with a friend about Linux. He says that Linux is prone to viruses, is easy to hack, and that anyone could create a Linux distro filled with viruses that would wreck a person's computer.

Thanks

This will happen only once and after that nobody would ever use software from that person/community.

Is it possible that someone stick trojans into Linux distro, but I am pretty sure that you will notice that. For example on Windows machine after virus infection, you notice that system become slow. However Linux is fast, therefore there is no virus infection;).

Tell your friend that if he doesn't trust in Linux he can stay on his Windows till end. I am pretty sure he will enjoy it, hehe.:lolflag:

---

### Post by user1397 on 2012-06-30
i don't know what linux.org does, but kernel.org is the site where the linux kernel "lives"

---

### Post by Dlambert on 2012-06-30
And if someone were to submit a patch with a "trojan" etc. It would be nipped in the butt before public release. They are all reviewed.

---

### Post by Primefalcon on 2012-06-30
you don't even really have toi trust canonical even tbh...

since it's all open source, and a very large userbase, if there was something malicious put in, you can trust people would be screaming a fit about it......

the same goes for any large open source project such as gimp, blender and so on....

---

### Post by Elfy on 2012-06-30
> For example on Windows machine after virus infection, you notice that system become slow. However Linux if fast, therefore there is no virus infection.
What?

---

### Post by Elfy on 2012-06-30
> **Primefalcon said:**
> you don't even really have toi trust canonical even tbh...

since it's all open source, and a very large userbase, if there was something malicious put in, you can trust people would be screaming a fit about it......

the same goes for any large open source project such as gimp, blender and so on....

piskie remembers along with a whole bunch of other people - wallpapers

at the end of the day you have to trust someone or something ...

Edit - mmm loosk like I'm not in agreement with the jist of primefalcon's post - ftr I am.

---

### Post by Mikeb85 on 2012-07-01
> **Curtis6767 said:**
> I'm having an argument with a friend about Linux. He says that Linux is prone to viruses, is easy to hack, and that anyone could create a Linux distro filled with viruses that would wreck a person's computer.


Linux is most definitely NOT prone to viruses, in fact it's nearly immune to them.  Linux isn't easy to hack, depending on what security settings you use it's more or less impossible.  That's why most countries' military, stock markets, large websites, etc..., depend on Linux.  

Could someone create a trojan in a distro, of course it's possible, but if you stick to the well known Linux distros (Red Hat, SUSE, Ubuntu), they don't have trojans, and are very secure.  Also keep in mind some Linux distros have some very big corporations sponsoring them (IBM and SUSE come to mind).

---

### Post by Paqman on 2012-07-01
> **Curtis6767 said:**
> anyone could create a Linux distro filled with viruses that would wreck a person's computer.


Of course they could. But why would anyone install it? After the first few early adopters got their fingers burned and reported it to the cops the "distro" would find itself in trouble quickly.

That's not a problem specific to Linux either. Plenty of Windows and OS X users get infected by installing booby-trapped software from torrents and warez sites. The solution is to get your software from trusted sources, and in this regard Linux has a significant advantage, due to the widespread use of software repositories (although Mac and Win are catching up on this with their new app stores).

As for "wrecking a person's computer", well it might wreck the OS that they installed, but installing a new one is easy. Generally speaking software can't harm hardware so a full reinstall will fix any wreckage.

---

### Post by Artemis3 on 2012-07-01
The unix like OSes (like linux) are not very prone to viruses, because the system was designed to separate system from user files. It is generally difficult to make a virus run because it would take the user to commit many chained mistakes, and even if it manages to run, its damage is contained to that user's data, not the whole system.

In reality this design is much older than Windows, but Microsoft took too many shortcuts in the past, and people trusting them have suffered the consequences.

Also Linux (and Distros) are Free Software, you have access to the source code, and can study in detail what every little piece of program do, and because its open, many people are searching these things (and some pay others to audit).

There are anti-tampering measures in the distro package system, which is why official repositories use a cryptographic public key to sign each package (and why people don't go to random pages to download software, and instead use their distro repository).

Openness is what prevents malicious code from living long, instead in closeness, a malicious code (or bug) can and will remain hidden for very long.

---

### Post by jonathonblake on 2012-07-01
> **Curtis6767 said:**
> and that anyone could create a Linux distro filled with viruses that would wreck a person's computer.

Anybody could create a distro that will physically damage your system.  There are several steps that users can take, to minimize that potential.

The major issues in computer security are trust, and openess.

The more open the developer is, the less need there is to trust them, because one can examine the software source code.

With closed source software, such as Microsoft Windows, one has to trust that Microsoft is not installing keyloggers that send your data to unknown third parties.

With open source software, sych as Linux, if one thinks Linus is allowing keylogger code into the kernel, one can examine the source code, and find any suspicious code blocks. If need be, one can replace those code blocks. (FWIW, Linus is not the only person who releases Linux kernal tarballs. The kernels released by other people don't have the popularity of the kernel released by Linus.)

> is who is watching to make sure a malicious distro doesn't get released.

Nobody. 
Malicious distros have been released.

Most Linux distro's are released under a Free Libre Open Source Software notice. This enables users to obtain source code. Some people like to examine that source code, to ensure that no "funny business" is going on.

People that like to use potentially hazardous software (beta versions, release candidates, etc.) are going to raise a hue and cry when the software does not do what it is supposed to.  Especially if that includes physical damage to their system. 

Likewise, people that enjoying playing with unknown distros, will cast out a warning, if they discover anything "bad" about the unknown distro, whether it be blowing graphics cards, or wiping out data on backup drives, or sending your keystrokes to unknown to third parties.

> Is there some kind of organization in place that has to sign off on a distro before it can go public?

Officially, no. 

Unofficially, if you can't get listed on DistroWatch, your distro is going to go nowhere. Whilst DistroWatch has been snookered into listing malicious distros, they will add warnings, when and as they receive information about the malicious distro.

If you want a safe, secure system then:
[LIST]
[*]Shun apha software;
[*]Do not beta test software;
[*]Do not beta-test distros, regardless of how well known they are;
[*]Select your distro from the top twenty list at DistroWatch;
[*]Only use software from your distro repository;
[*]Verify hashes and checksums, prior to installation of the software;
[*]Check the hashes and checksums from both the distro repository, and upstream developer. If these values are different, have both parties explain to your complete satisfaction, why you should trust either parties build;
[/LIST]

For extra security:
[LIST]
[*]Only use releases whose vendor provides commercial support;
[*]Look at the reputation of the vendor:
[LIST]
[*]Contributes to open source software development;
[*]Is generally regarded positively;
[*]Has been in business for more than five years;
[/LIST]
[/LIST]

jonathon

---

### Post by F.G. on 2012-07-01
hmm, i think it is more or less the point of open source code, that there isn't a central organisation that signs off on everything. that doesn't mean that each project isn't owned by someone though.

i wonder if this is the same misunderstanding behind the 'oh, but if the source code is open then surely anyone can write anything in it? that can't be secure.' logic, as if some 'evil hacker' can change the source code currently running on my machine by anonymously committing something to the head of the canonical, or linux kernel repository.

curtis6767, there are a couple of things you can tell your friend. mainly that the development system/development life cycle used by open-source software and 
closed-source software (eg Windows) is not inherently different. it's likely that there are only a handful of people at any one time who are allowed to commit/merge any code to the head of the code base of these projects (Windows,OSX or Linux), and this will only happen once the code has been quite rigorously tested. then, when the linux foundation are happy with their code they will release it. a similar process (i guess) happens with companies like canonical, and when they are happy with their distro it will be released. 

so, someone could easily release a malicious distro (just as they could make a malicious os from scratch if they wanted). but they would have to make it themselves and then convince people, somehow, to use it. there is no way anything would propagated back to a parent distro, or the kernel. 

basically if someone made a malicious distro, they would need to peddle it to people, just like the creators of other malicious software do. like 'Windows anti-virus 2008' (or whatever), anyone with any sense will google the thing, see a bunch of complaints about how it is actually malware and then not install it.

---

### Post by Curtis6767 on 2012-07-01
Thanks for all the responses. Very interesting, indeed. I really don't know where my friend got all these weird ideas about Linux. Maybe he has a lot of MS stock.

Basically I wrote Linux off years ago when a geek/IT friend of mine explained how difficult Linux was and that there was little software for it and hardware was a problem. He was running some form of Linux at the time, which was at least 10 years ago. I had no idea until January of this year that Linux had progressed to its current state. I stumbled on a reference to Ubuntu in some post or another and that's how I came to install Ubuntu. 

Anyway I'll be talking to my friend soon and will try to re-educate him. I'm certainly not going to try and persuade him to try Linux unless he happens to have an old XP machine tucked away some place.

Thanks again.

---

### Post by forrestcupp on 2012-07-01
> **Curtis6767 said:**
> Is there some kind of organization in place that has to sign off on a distro before it can go public? 
There are so many distros and derivatives of distros that that would be impossible. With things like Remastersys, any old grandma in the world can create a "distro" derived from Ubuntu, so there's no way all of that can be policed.

Nevertheless, the vast community of users is kind of like the "organization" that you are talking about, only they sign off on it *after* it goes public. Word gets around very quickly whether something is good or bad, and since most of it is open source, it wouldn't take very long for anything malicious to be spotted. Most things that go into a distro are things from bigger projects that we all already know and trust. The smaller distro-specific scripts and apps are going to be scrutinized pretty quickly.

Plus there is the fact that there have never been any known viruses for Linux.

---

### Post by David Andersson on 2012-07-01
> **forrestcupp said:**
> 
Plus there is the fact that there have never been any known viruses for Linux.

That is not true. See e.g. [A history of viruses on Linux]("http://www.neowin.net/news/a-history-of-viruses-on-linux"). 

But. Very few Linux viruses ever got any far, maybe non at all. Many were designed long *after* the security hole they would use was patched. Normal cautious users should be safe.

---

### Post by F.G. on 2012-07-01
my understanding (which may be completely wrong) is that it's a lot harder to make a virus for *nix type systems. something to do with the memory allocation and access privelidges. 

i think windows allocates memory dynamically, making it harder to fix the access priviledges, whereas linux used fixed size chunks, so a process can be locked out of accessing memory that isn't allocated to it. hence why, with a stray pointer, you will always get a segfault in linux, but can still get inteligible output/be able to manipulate the data in windows (from other processes).

anyway, if anyone has any better knowledge, or can clarify my understanding about this i'd be much obliged.

---

### Post by forrestcupp on 2012-07-01
> **David Andersson said:**
> That is not true. See e.g. [A history of viruses on Linux]("http://www.neowin.net/news/a-history-of-viruses-on-linux"). 

But. Very few Linux viruses ever got any far, maybe non at all. Many were designed long *after* the security hole they would use was patched. Normal cautious users should be safe.

Thanks for the correction and the great link. It looks like none of them have really done any big damage in the wild.

---

### Post by rg4w on 2012-07-01
> **Curtis6767 said:**
> I'm having an argument with a friend about Linux. He says that Linux is prone to viruses, is easy to hack, and that anyone could create a Linux distro filled with viruses that would wreck a person's computer.
Bad news for your friend:  it's not limited to distros, and it's certainly not limited to Linux.

Anyone can write any software - even a seemingly-simple application - that can contain malware.

This is true for any OS, but has your friend noticed that it happens with enough regularity on Windows to cause billions of dollars worth of damage every year?

No platform is immune, but Microsoft is far ahead in actual exploits.

---

### Post by Paqman on 2012-07-02
> **F.G. said:**
> my understanding (which may be completely wrong) is that it's a lot harder to make a virus for *nix type systems. something to do with the memory allocation and access privelidges. 


Both Linux and Windows now use [ASLR]("http://en.wikipedia.org/wiki/ASLR"), if that's what you're referring to.

---

### Post by vasa1 on 2012-07-02
The majority of posts in this thread don't deal, IMO, with "How does a distro become a distro?"

It's more like "Is it safe?" ([http://www.youtube.com/watch?v=dG5Qk-jB0D4](http://www.youtube.com/watch?v=dG5Qk-jB0D4))

---

### Post by nothingspecial on 2012-07-02
> **vasa1 said:**
> The majority of posts in this thread don't deal, IMO, with "How does a distro become a distro?"



You are right.

Moved to Recurring Discussions.

---

### Post by forrestcupp on 2012-07-02
> **vasa1 said:**
> The majority of posts in this thread don't deal, IMO, with "How does a distro become a distro?"

It's more like "Is it safe?" ([http://www.youtube.com/watch?v=dG5Qk-jB0D4](http://www.youtube.com/watch?v=dG5Qk-jB0D4))

That's because you have to read more than just the title. The title isn't a good reflection of what the OP is actually asking.

---

### Post by vasa1 on 2012-07-02
> **forrestcupp said:**
> That's because you have to read more than just the title. The title isn't a good reflection of what the OP is actually asking.

But wouldn't it be simpler for a mod to fix the title since it was clear that the OP was more concerned about how secure or insecure is distro is compared to the other OS.

(I was actually hoping to read about the nuts and bolts about how a distro is put together and the thoughts that go into wanting to have a new distro, etc.)

---

### Post by nothingspecial on 2012-07-02
> **vasa1 said:**
> But wouldn't it be simpler for a mod to fix the title since it was clear that the OP was more concerned about how secure or insecure is distro is compared to the other OS.



That would be up to the OP to request.

---

