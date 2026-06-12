---
title: "Antivirus XP 2008 on Ubuntu"
date: 2008-08-28
forum: Recurring Discussions
---

### Post by RedPandaFox on 2008-08-28
Today while I was at work, my mother (a teacher at a primary school) calls me with a question. 

"One of my computers in my room came up with a message ```
"WARNING!!! Quick System Scan Results 
```
What should I do?"

I instantly recognised the sinister "Antivirus XP 2008" malware.
My answer was simply, "SHUT IT DOWN NOW!"

Being a network of about 100 computers I didn't want there to be a big problem.

There network admin was off sick but as luck would have it, the IT guys from the local tafe stopped in to fix a computer that wouldn't boot, so she mentioned what happened and how I reacted, and they checked it out and they just looked at her and said "You are the first person I know who didn't fall for that the first time"

Long story short they fixed the problem before it caused any damage.

That got me thinking :evil: What will happen if I run it over Wine on my old laptop? (after clean install wiping all my info, anyway i don't keep anything sensitive on it)

What are your thoughts?

Also where can I get access to the malware?

---

### Post by ad_267 on 2008-08-28
Someone's tried this sort of thing before: [http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Sounds like it shouldn't do too much damage.

---

### Post by SunnyRabbiera on 2008-08-28
If you run something like this in wine, it wont do @#$#.
ubuntu is immune to this sort of crap.

---

### Post by RedPandaFox on 2008-08-28
> **SunnyRabbiera said:**
> If you run something like this in wine, it wont do @#$#.
ubuntu is immune to this sort of crap.

Not completely, it will run the program but it wont affect your system to much, it will try and it will do its processes but the worst it can do is mess with your virtual c drive and even then you can just kill the process.

I mainly just want to watch it, like a fish in a tank.

---

### Post by SunnyRabbiera on 2008-08-28
> **RedPandaFox said:**
> Not completely, it will run the program but it wont affect your system to much, it will try and it will do its processes but the worst it can do is mess with your virtual c drive and even then you can just kill the process.

I mainly just want to watch it, like a fish in a tank.

well slowdown and such are probably as far as they can go, plus for them to effect linux they must have root access and be able to read the linux directory system...
so far very little covers these two areas as for one root access isnt given by default in ubuntu and two most of these things target the windows file structure.

---

### Post by barbedsaber on 2008-08-28
I am not sure if this had been said, I didn't check.
Wine doesn't run with root privileges, and the only thing is should have full read/write access, is the .wine directory (there may be one in the usr directory, I am not sure) If Antivirus XP were to run (which it might not) the only thing it would be able to "break" would be the .wine drive.
That is why its a bad idea to run as root.

---

### Post by Delever on 2008-08-28
> **ad_267 said:**
> Someone's tried this sort of thing before: [http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Sounds like it shouldn't do too much damage.

Design flaw :P

> **SunnyRabbiera said:**
> If you run something like this in wine, it wont do @#$#.
ubuntu is immune to this sort of crap.

Again, made with Windows(TM) in mind.

> **barbedsaber said:**
> I am not sure if this had been said, I didn't check.
Wine doesn't run with root privileges, and the only thing is should have full read/write access, is the .wine directory (there may be one in the usr directory, I am not sure) If Antivirus XP were to run (which it might not) the only thing it would be able to "break" would be the .wine drive.
That is why its a bad idea to run as root.

First virus capable of wiping out home contents will be a blast. Yeah, it does not run with root privileges, it runs with your privileges. What you can delete, it can delete too. Get ready, target audience seems to be rising :popcorn:

You are right, Linux is immune. Linux, kernel. It will continue working. Whatever happens to user folders.

---

### Post by gn2 on 2008-08-28
> **Delever said:**
> 
First virus capable of wiping out home contents will be a blast. Yeah, it does not run with root privileges, it runs with your privileges. What you can delete, it can delete too. Get ready, target audience seems to be rising

Target audience size is really irrelevant.

---

### Post by red_Marvin on 2008-08-28
I think it is time for an [xkcd]("http://xkcd.com/350/") link this this point.

---

### Post by ad_267 on 2008-08-28
> **red_Marvin said:**
> I think it is time for an [xkcd]("http://xkcd.com/350/") link this this point.

Haha yeah I was thinking of that one too.

---

### Post by RedPandaFox on 2008-08-28
Thats the kind of thing I want :)

I want my little pet virus, trying to attack me but failing, so cute!

:lolflag:

No seriously, anyone know where to get it?

---

### Post by Delever on 2008-08-29
> **RedPandaFox said:**
> Thats the kind of thing I want :)

I want my little pet virus, trying to attack me but failing, so cute!

:lolflag:

No seriously, anyone know where to get it?

Create virtual machine in VirtualBox, install Windows 2000, set up internet connection, and wait few minutes.

---

### Post by Cresho on 2008-08-29
as far as I can tell, it will install depending on what libraries wine provide to make it work.  Also, it will not do damage to linux to a certain point.  what I mean is it might create directories or such but they are basically shooting blanks.

I once had a zip file that I extracted in windows and it exploded in size from 1 kb to about 10gb.  iT WAS A BOMB but i simply rebooted windows.  I wonder how that would work in linux.

---

### Post by barbedsaber on 2008-08-29
> **Delever said:**
> Create virtual machine in VirtualBox, install Windows 2000, set up internet connection, and wait few minutes.

its funny cause its true.

---

### Post by lisati on 2008-08-29
Suggested security precaution for those game enough to check out malware using Wine: disable Wine's access to /

---

### Post by RedPandaFox on 2008-08-29
> **lisati said:**
> Suggested security precaution for those game enough to check out malware using Wine: disable Wine's access to /
How do you limit it to just access to the virtual C drive?

---

### Post by Johnsie on 2008-08-29
> ubuntu is immune to this sort of crap

I wish people would stop saying stuff like this. Ubuntu is not immune to malware or viruses. It's just that you are less likely to get malware on Ubuntu at this stage in time. Like any other operating system Ubuntu has many vulnerabilities, and the humans who use it make mistakes too.  The  Ubuntu vulnerabilities just haven't been fully exploited yet because more people use Windows.If Linux becomes more popular then you can expect that eventually we will be dealing with this sort of thing in Ubuntu.

---

### Post by Johnsie on 2008-08-29
Oh yeah, the virus we are talking about here installs itself using a vulnerability in the java runtime envrionment. It attaches itself to winlogin.dll and internet explorer. So this virus wouldn't work properly under wine because wine doesnt use windows logins. It might work a bit but you wouldn't get full 'functionality'.

---

### Post by Twitch6000 on 2008-08-29
> **Johnsie said:**
> I wish people would stop saying stuff like this. Ubuntu is not immune to malware or viruses. It's just that you are less likely to get malware on Ubuntu at this stage in time. Like any other operating system Ubuntu has many vulnerabilities, and the humans who use it make mistakes too.  The  Ubuntu vulnerabilities just haven't been fully exploited yet because more people use Windows.If Linux becomes more popular then you can expect that eventually we will be dealing with this sort of thing in Ubuntu.

Thank you for blowing off some steam for me :).

---

### Post by t0p on 2008-08-29
> **Johnsie said:**
> The Ubuntu vulnerabilities just haven't been fully exploited yet because more people use Windows.If Linux becomes more popular then you can expect that eventually we will be dealing with this sort of thing in Ubuntu.

I don't buy that.  The set-up of Linux, where users do not have root access by default, versus the windoze model of everyone being admin so they can get stuff done, is inherently more secure.  You might not like hearing this, but it's the truth nevertheless.

The other stuff you wrote, about stupid humans being the weak link in every chain, is obviously true.  But in Linux, those humans can't do as much damage.  Unless they're *real* stupid humans who log in as root cos the nice malware asked them too.

---

### Post by RedPandaFox on 2008-08-31
The reason Windows has so many vunerablilities, is its long life cycle, relatively small development branch, and its a pre-Internet system running on the Internet.

Where as Linux (I'm referring mainly to Ubuntu) Has a short life cycle, meaning changes to security are implemented fast, large development groups (open source so if a problem is found there are litterelly hundred working on it) and it was literally born on the Internet.

---

### Post by gn2 on 2008-09-02
Also, *every* Windows PC has the same file names for it's system files and huge numbers of them have no password protection whatsoever.

---

### Post by fiddledd on 2008-09-02
> **t0p said:**
> I don't buy that.  The set-up of Linux, where users do not have root access by default, versus the windoze model of everyone being admin so they can get stuff done, is inherently more secure.  You might not like hearing this, but it's the truth nevertheless.

The other stuff you wrote, about stupid humans being the weak link in every chain, is obviously true.  But in Linux, those humans can't do as much damage.  Unless they're *real* stupid humans who log in as root cos the nice malware asked them too.

Everyone is not Admin by default, at least not in Vista, or, I believe XP SP3. As for Linux being safer, yes, ATM, it is. However if Linux becomes a dominant force on the Desktop it will suddenly get the attention of the hackers/crackers, so I don't think complacency is a good thing. Also I hear a lot of people say "you are safe unless you have/grant root access", and this is true as far as the OS is concerned. However, you don't need to have root access to delete your personal files in your Home folder. There is no substitute for safe practices and common sense. So I think the advice should be, be careful, don't trust 3rd party repositories, and don't be complacent.

---

### Post by ad_267 on 2008-09-02
> **fiddledd said:**
> Everyone is not Admin by default, at least not in Vista, or, I believe XP SP3. As for Linux being safer, yes, ATM, it is. However if Linux becomes a dominant force on the Desktop it will suddenly get the attention of the hackers/crackers, so I don't think complacency is a good thing. Also I hear a lot of people say "you are safe unless you have/grant root access", and this is true as far as the OS is concerned. However, you don't need to have root access to delete your personal files in your Home folder. There is no substitute for safe practices and common sense. So I think the advice should be, be careful, don't trust 3rd party repositories, and don't be complacent.

Linux already is a dominant force, probably the most dominant, in servers and supercomputers, where a lot more valuable information is stored. Wouldn't crackers much rather go after that information than just personal data?

You're right about safety of the home folder. It doesn't matter how secure the OS is, users will always be able to muck things up.

---

### Post by fiddledd on 2008-09-02
> **ad_267 said:**
> Linux already is a dominant force, probably the most dominant, in servers and supercomputers, where a lot more valuable information is stored. Wouldn't crackers much rather go after that information than just personal data?

You're right about safety of the home folder. It doesn't matter how secure the OS is, users will always be able to muck things up.

I know Linux dominates in servers and supercomputers, that's why I said Desktop. If you try and hack a server you are probably dealing with a system that's been secured by an IT pro. When you try and hack a desktop, you have a much better chance of success. Oh, and Linux servers also get hacked, but AFAIK, not often. Please don't make me search google for examples, I'm going to sleep soon. But I guess I'll do it tomorrow if I must.

---

### Post by Tindytim on 2008-09-02
Well, the servers with really important Data or some Super Computers run their own distros.

> **gn2 said:**
> Also, *every* Windows PC has the same file names for it's system files and huge numbers of them have no password protection whatsoever.

It is pretty funny that most of those files are 'hidden' by default from the user, but still easily accessible. While in Ubuntu, you can see it all, you just can't edit it.

---

### Post by EmanresuusernamE on 2008-09-02
> **ad_267 said:**
> Linux already is a dominant force, probably the most dominant, in servers and supercomputers, where a lot more valuable information is stored. Wouldn't crackers much rather go after that information than just personal data?

You're right about safety of the home folder. It doesn't matter how secure the OS is, users will always be able to muck things up.

Super Computers: Maintained by IT professionals, have potentially large quantities of cash but few sources, ability to hunt you down like a dog, probably logging everything making it easier to hunt you down like a cat as well.

Personal Computers: Maintained by ID10Ts, have very little cash but have near endless amounts of sheep for the slaughter, likely to not notice anything till it's way to late as well as get rid of the evidence for you, (Computer's slow? Toss it).

Who would you go after?

---

### Post by ad_267 on 2008-09-02
Yeah I guess there probably would be more attacks on personal computers then. But I still have to say that Linux/Ubuntu's security model is a lot better than Windows. Windows is only just catching up with the idea of not being the administrator by default.

---

### Post by Johnsie on 2008-09-02
> **t0p said:**
> I don't buy that.  The set-up of Linux, where users do not have root access by default, versus the windoze model of everyone being admin so they can get stuff done, is inherently more secure.  You might not like hearing this, but it's the truth nevertheless.

The other stuff you wrote, about stupid humans being the weak link in every chain, is obviously true.  But in Linux, those humans can't do as much damage.  Unless they're *real* stupid humans who log in as root cos the nice malware asked them too.


First of all... it's possible that a security vulnerability could be exploited so that nasty code gets admin access. This could happen with any software that is running with root priviledges. There are services permanently running in Ubuntu that need to have root access to function, even if the actual user doesn't have root/admin. If those services were compromised then there could be serious security implications...

Another way is trickware/trojans. Alot of people use non-official repositories or get their debs from untrusted places like these forums. A deb can easily be disguised as something legit and could have nasty code in it that installs itself into your system startup, thus having root access. 

Another way is by attacking the official repository servers. This has actually happened in the past. Hackers could break into the repository servers and replace debs with files of their own.

Linux is only as secure as the software that manages it and people are finding security holes all the time. That's why there are so many security updates applied to Ubuntu. Never believe that any system is foolproof or completely secure because there will always be someone who finds a hole. I've been using Ubuntu since 2005, long enough to know that it does have weaknesses.

---

### Post by kpatz on 2008-09-02
Also, there are lot more Windoze desktops out there to exploit than Linux desktops or servers for that matter.

And look at what virus writers do it for.  Not for the fame, like in the past, or the potential of doing damage (viruses that wipe drives are a thing of the past, pretty much).  Nowadays they do it for MONEY.  Mostly by selling services (aka bots) to spammers and scam artists.  The Antivirus XP series is also a money maker, by plastering fake virus warnings on people's PCs and making them fork over money to buy the "product" to "remove" them.  For this purpose, home/desktop PCs are a much more viable target, and that target is 99.99999999% Windows, than Linux based servers.

Of course, if a different OS becomes the dominant end-user OS, whether it's a Linux variant, Mac OS, Solaris, or what have you, it too will become a target of scam artists and their malware.

---

### Post by RedPandaFox on 2008-09-03
But Linux tends to have security at mind, any vunrabilty  is quickly patched in the most cases

---

### Post by fiddledd on 2008-09-04
> **RedPandaFox said:**
> But Linux tends to have security at mind, any vunrabilty  is quickly patched in the most cases

Yes, in my experience, that's true. With Windows you may have to wait a month for a security patch to become available from Microsoft. Although there are often third party patches available beforehand if the security risk is severe.

---

### Post by rune0077 on 2008-09-04
> **t0p said:**
> 
The other stuff you wrote, about stupid humans being the weak link in every chain, is obviously true.  But in Linux, those humans can't do as much damage.  Unless they're *real* stupid humans who log in as root cos the nice malware asked them too.

Theoretically, a virus could also just ask for root access with a password prompt. Let's face it, some who gets a flashy message on their screen and the goes "uhhh shiny button saying 'Install', I think I'll just push that", won't be particularly protected on Linux either, where they'll just go "uhhh nice password prompt, I think I'll type in my password here." If you don't bother to check what you're installing on your computer before installing it, you're not going to bother checking what a program requesting root access does either before accepting it.

---

### Post by cardinals_fan on 2008-09-04
> **rune0077 said:**
> Theoretically, a virus could also just ask for root access with a password prompt. Let's face it, some who gets a flashy message on their screen and the goes "uhhh shiny button saying 'Install', I think I'll just push that", won't be particularly protected on Linux either, where they'll just go "uhhh nice password prompt, I think I'll type in my password here." If you don't bother to check what you're installing on your computer before installing it, you're not going to bother checking what a program requesting root access does either before accepting it.
Bingo.

---

### Post by RedPandaFox on 2008-09-04
> **rune0077 said:**
> Theoretically, a virus could also just ask for root access with a password prompt. Let's face it, some who gets a flashy message on their screen and the goes "uhhh shiny button saying 'Install', I think I'll just push that", won't be particularly protected on Linux either, where they'll just go "uhhh nice password prompt, I think I'll type in my password here." If you don't bother to check what you're installing on your computer before installing it, you're not going to bother checking what a program requesting root access does either before accepting it.

You make the assumption most Linux users havnt been sucked into bad Windows habits...

---

### Post by rune0077 on 2008-09-04
> **RedPandaFox said:**
> You make the assumption most Linux users havnt been sucked into bad Windows habits...

Just making the assumptions that most Linux users are no different from most Windows users, except they use a different OS. I used Windows for years, and it's not like I suddenly changed the moment I switched to Linux and started becoming any more or less proficient with my computer. People are people, no matter what OS they use. Windows doesn't make you dumber, Linux doesn't make you smarter.

---

### Post by RedPandaFox on 2008-09-04
> **rune0077 said:**
> Just making the assumptions that most Linux users are no different from most Windows users, except they use a different OS. I used Windows for years, and it's not like I suddenly changed the moment I switched to Linux and started becoming any more or less proficient with my computer. People are people, no matter what OS they use. Windows doesn't make you dumber, Linux doesn't make you smarter.

I mean that alot of windows users, and even myself at times after getting sick of reading, click ok on most pop ups(that look like windows) just to get rid of them.

---

### Post by rune0077 on 2008-09-04
> **RedPandaFox said:**
> I mean that alot of windows users, and even myself at times after getting sick of reading, click ok on most pop ups(that look like windows) just to get rid of them.

Yeah, I guess. But seriously, don't you think a lot of Linux-users kind of just type in their password when prompted to as well, just to get on with what they're doing? Of course not if we were on the net and a webpage suddenly prompted it (which wouldn't even be possible), but there would still be ways to smuggle the virus in.

---

### Post by RedPandaFox on 2008-09-04
How bout a Trojan that gets root access then uses that to open a backdoor and let others in?

Simply plant something in a valid program in the Debian repos and we are up the creek.

---

