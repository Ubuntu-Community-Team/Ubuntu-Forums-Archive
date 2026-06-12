---
title: "Need your thoughts on something"
date: 2008-07-18
forum: Recurring Discussions
---

### Post by itix on 2008-07-18
I just thought about the future of open source, and now I need to know what you think about this.

I'd claim that the main reason for linux being spared from most viruses is that it is largely unpopular. Windows has most viruses, and after them comes macs and last comes linux.

Now think about the idea that linux would become the worlds largest OS, wouldn't it be really bad to be open source in that case??

A hacker could easily find and exploit any weakness in the security just by looking through the source...

---

### Post by tuxxy on 2008-07-18
> A hacker could easily find and exploit any weakness in the security just by looking through the source...

This can be just as eaily done with windows, aslong as you dont log in as root you should be ok now.  Also another reason is that VB is not fully supported :)

---

### Post by hyper_ch on 2008-07-18
most servers run linux and they have very seldom a problem... well, they don't get nearly as hacked as often as server running windows 2xxx and IIS... so the nature of open source makes it not easier to hack.

---

### Post by timcredible on 2008-07-18
> **itix said:**
> 

I'd claim that the main reason for linux being spared from most viruses is that it is largely unpopular. Windows has most viruses, and after them comes macs and last comes linux.

there's almost no viruses for linux because it's harder to break linux than windows.  a large percentage of websites are run on linux, so the 'unpopular' theory doesn't hold water.  linux is only 'unpopular' on the desktop.

> Now think about the idea that linux would become the worlds largest OS, wouldn't it be really bad to be open source in that case??

A hacker could easily find and exploit any weakness in the security just by looking through the source...

not a problem because bugs can be found and fixed just as easily.  no need to wait months for a 'service pack'.

---

### Post by FTBPrimeEvil on 2008-07-18
Windows is more subjected to spyware than virus's these days, an actuall virus doesn't exist anymore, you gotta laugh when some say's my brandnew vista computer has a virus

---

### Post by bapoumba on 2008-07-18
Moved to "Recurring Discussions".

---

### Post by ShodanjoDM on 2008-07-18
> **itix said:**
> A hacker could easily find and exploit any weakness in the security just by looking through the source...

Just as easy for another (good) hackers, security researchers, or anyone with coding skills and good intentions to close the gaps.

---

### Post by itix on 2008-07-18
You're right on the servers. Google and last.fm and other large software developers use linux for their servers.
I was just a bit worried about the desktop and the "common" user. I have my bank-id on my Eee PC. If someone were to read the code to EeeXubuntu, wouldn't they be able to design a petty good "entry vehicle" by analyzing the code??

I mean, wouldn't we see more (or should I say any) open source anti-virus programs for windows if open source was good against virues??

---

### Post by hyper_ch on 2008-07-18
not really... windows is completely differently designed from linux/unix.... linux/unix were designed as true multi-user networking OSes with a strong emphasis on security.

---

### Post by Canis familiaris on 2008-07-18
> **hyper_ch said:**
> not really... windows is completely differently designed from linux/unix.... linux/unix were designed as true multi-user networking OSes with a strong emphasis on security.

True!
The only way Linux could  suffer will be through social engineering and user neglected which is frankly not the problem of the OS.

---

### Post by hyper_ch on 2008-07-18
> **anurag_panda said:**
> true!
The Only Way Linux Could  Suffer Will Be Through Social Engineering And User Neglected Which Is Frankly Not The Problem Of The Os.

Pebcak

---

### Post by aysiu on 2008-07-18
But if Linux gets more popular on the desktop/laptop, there will also be a larger percentage of users who are more susceptible to social engineering. There will also, as we have seen with the Xandros preinstalled on the Eee PC, be more versions of Linux available to consumers that have badly implemented security (no password authentication for *sudo* commands, in the case of the Eee Xandros).

---

### Post by xeth_delta on 2008-07-18
As other users have mentioned before, Linux has rather different architecture to what windows has, it was build from the very start as a multi-user OS, and hence has the necessary infrastructure for such an environment has been for quite some time in place.

In my view, the fact that the code is open source and a vailable to a huge number of developers, only makes it easier to find vulnerabilities and correct them faster and more efficiently before they become a real issue than in a closed environment.

I believe that there was not long ago a contest in which three systems were to be cracked, a Linux, a Mac and a Windows box. After the three days of the event, only the Linux box kept its integrity.

---

### Post by madjr on 2008-07-18
> **itix said:**
> You're right on the servers. Google and last.fm and other large software developers use linux for their servers.
I was just a bit worried about the desktop and the "common" user. I have my bank-id on my Eee PC. If someone were to read the code to EeeXubuntu, wouldn't they be able to design a petty good "entry vehicle" by analyzing the code??

I mean, wouldn't we see more (or should I say any) open source anti-virus programs for windows if open source was good against virues??

**NOPE**

@itix

you must realize that anti-viruses is a **[SIZE="4"]Billion dollar industry[/SIZE]**.

M$ is also getting a piece of the cake too. They will never make it too secure.

Even **Apple** is working along some anti-virus companies.

**Antivirus companies** are the ones who **create** these viruses in the first place. They pay the developers, hackers, w/e.

**greed** moves companies, simple fact.

---

### Post by geoken on 2008-07-18
I'm not arguing one way or another, but I just want to point out that using Linux servers as an example of Linux security makes no sense. 99.9% of Windows malware is user initiated via social engineering. Comparing servers only shows it's strength against remote attacks, which is also extremely rare on Windows boxes.

---

### Post by aysiu on 2008-07-18
I'm not a programmer, so someone who knows more about programming than I do can correct me if I'm wrong, but I don't really see how seeing the code means you can necessarily "design a pretty good 'entry vehicle' by analyzing the code."

Just because you can *see* the code doesn't mean you can randomly insert your own code into the code you see. So you have to be able to *see* a flaw that already exists, not just create your own "entry vehicle." The entry has to already be there - it's just an entry that you're taking advantage of, not creating.

Of course, in theory, it would seem more convenient to find entries to exploit if you see the code as opposed to not see the code, but in practice, you can see that closed source (Windows, for example) has plenty of exploits.

A lot of the exploits take advantage of observable behaviors in the closed source programs and not anything in the code itself. For example, Windows hides extensions by default, so a lot of malware disguised itself as .jpg with a real extension of .exe. Windows also does a lot of autoexecution in Outlook, and you don't need to see the code to know that's an exploit ripe for the picking. Windows XP also defaults to administrator, so malware creators know that a compromised system will give them automatic access to registry keys and system files. Again, you don't need to see the code to know that.

---

### Post by xeth_delta on 2008-07-18
> **aysiu said:**
> Just because you can *see* the code doesn't mean you can randomly insert your own code into the code you see. So you have to be able to *see* a flaw that already exists, not just create your own "entry vehicle." The entry has to already be there - it's just an entry that you're taking advantage of, not creating.
Agree, and such practice would anyway not be possible, as the code being open, such "malicious" entries could be tracked immediately and removed.

> **aysiu said:**
> Of course, in theory, it would seem more convenient to find entries to exploit if you see the code as opposed to not see the code, but in practice, you can see that closed source (Windows, for example) has plenty of exploits.

A lot of the exploits take advantage of observable behaviors in the closed source programs and not anything in the code itself. For example, Windows hides extensions by default, so a lot of malware disguised itself as .jpg with a real extension of .exe. Windows also does a lot of autoexecution in Outlook, and you don't need to see the code to know that's an exploit ripe for the picking. Windows XP also defaults to administrator, so malware creators know that a compromised system will give them automatic access to registry keys and system files. Again, you don't need to see the code to know that.

Again, I am of the same opinion of aysiu, and as has been said before, it seems that the correction of these vulnerabilities is performed faster in an open source environment, as access to the code is readily available.

That said, I agree antivirus companies make a lot of money from the presence of viruses, but I do not believe it is them who make or pay to have the viruses made. It just... helps their business that they exist.

---

### Post by itix on 2008-07-18
> **madjr said:**
> **NOPE**

@itix

you must realize that anti-viruses is a **[SIZE="4"]Billion dollar industry[/SIZE]**.

M$ is also getting a piece of the cake too. They will never make it too secure.

Even **Apple** is working along some anti-virus companies.

**Antivirus companies** are the ones who **create** these viruses in the first place. They pay the developers, hackers, w/e.

**greed** moves companies, simple fact.

Thats being a bit paranoid...

To you other, you've more or less convinced me that open source isn't a model more insecure than other. It's true that seeing the source doesn't make it easier to design direct malware. It does however make it easier to detect loopholes, but that also makes it easier to correct them. That means that as long as those creating malware are fewer than those wanting a secure desktop, linux will stay secure :)

Thank you for convincing me...

---

### Post by lisati on 2008-07-18
To be honest, I've had more problems of my own making (from carelessness and/or doing something stupid and/or not properly understanding what I'm doing) than from malware.

---

### Post by aysiu on 2008-07-18
madjr's allegations don't have any hard evidence. So I can't say definitely that anti-virus companies *are* in collusion with virus-makers, but I also cannot say definitely (considering the financial incentive for anti-virus companies) that they are *not* in collusion.

If in 1960s you had said there was an FBI conspiracy to sic "subversive" (civil rights groups, for example) groups against each other through illegal means, infiltration, psychological warfare, and wiretapping, you would be considered probably a paranoid conspiracy theorist. Now, of course, we know there was such a conspiracy, and it was called COINTELPRO.

Conspiracies, lacking any evidence, are not necessarily true or necessarily untrue. They are just additional explanations for what is occurring.

I cannot say definitely that Norton helps fund directly or indirectly virus-makers, but I can say it wouldn't surprise me if that were the case, since they would be out of business without viruses around.

---

### Post by bobbob1016 on 2008-07-30
The "can't they look at the source and write a virus" is called the "many eyes" problem or something.  But the thing to consider is that reading someone else's code and understanding everything it does, isn't easy.  I'm a Comp Sci major, and when a professor gives us a "skeleton program" as in one to fill in with our code, it takes me a a couple days, depending on the complexity of his code and the assignment, to figure out his few pages of code, inside and out, before I can add my own.  This becomes MUCH more complicated for someone looking at Linux's code, since there are many many times the amount of pages that my professor used, and they have to understand them all enough to get an exploit.  Many eyes != (doesn't equal) many *intelligent* eyes.  The built in security, on top of the code thing is pretty safe.  The intelligent eyes are generally white hat, meaning good guys, or maybe grey, but I don't think there are as many really intelligent black hats, but I could be wrong.

---

