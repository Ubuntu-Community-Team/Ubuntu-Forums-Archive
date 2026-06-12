---
title: "Is Linux actually completely virus free?"
date: 2009-05-07
forum: Recurring Discussions
---

### Post by gymophett on 2009-05-07
Ok, please don't move this to recurring questions. There needs to be an updated thread.

Back to topic. Can Linux really get a virus? I heard it can, but it would only affect Gnome or KDE. It cant get to your core system.
I really don't want Linux to even be able to have viruses, it is getting bigger, and I don't want it to turn to crap. :(

---

### Post by Kareeser on 2009-05-07
Short answer: Yes.

Slightly longer answer: Yes, with a but.

---

### Post by gn2 on 2009-05-07
There are no viruses for Linux in the wild. Not one.
Viruses are a Windows phenomenon, Linux vulnerabilities take other forms.

---

### Post by gymophett on 2009-05-07
> **gn2 said:**
> There are no viruses for Linux in the wild. Not one.
Viruses are a Windows phenomenon, Linux vulnerabilities take other forms.

Can you extrapolate?

---

### Post by Glucklich on 2009-05-07
Yes, you can get a virus on Linux. The difference is that virus are more common on Windows than on Linux. Since Windows is a more common system, bad intentioned people will obviously try to affect the highest number of people possible. And Linux offers a better security system "out of the box". But if virus get common on Linux, virus security will also develop. As it was on Windows... and it's beginning to be on Macintosh. It's a cause and effect thing.

---

### Post by Alterax on 2009-05-07
Yes, it can.  There are relatively few, though, and they're more nuisances than disasters.

Windows is pretty prone because it's a popular target AND because there are way too many ways that MS put in for user-level programs to run in system-space.  It comes mainly from the original assumption that the user will be the one administering the system, as well as hooks that they put in to allow their software (office, exchange, MS-SQL) to integrate more tightly with the underlying systems.  Each hook is a potential vulnerability; it's the nature of the game, and since they go to the core, they can get REALLY dangerous to the whole system.

Linux, on the other hand follows Unix's design, which was from a shared main computer with multiple users.  With that in mind, Unix was designed with the idea of a clear division between users and administrators--that way Bob the astronomer's programming flaw wouldn't interfere with Dianne the physicist's work.  That design was carried over into Linux--which is why of the few viruses that do exist, they usually just mess with the user and not the system as a whole.

---

### Post by Keyper7 on 2009-05-07
All operating systems can get viruses.

No operating system is protected from user stupidity.

---

### Post by Kareeser on 2009-05-07
Building on the posts of the other contributors to this thread, please also note the following.

No computer system is safe from "social engineering" attacks. If you are tricked (hence the "social" aspect) into typing your password into a root access dialogue, all the fancy Linux coding in the world won't save you.

---

### Post by gymophett on 2009-05-07
So, it couldn't delete my files and drivers, etc?

---

### Post by Skripka on 2009-05-07
In contemporary OSes, the single LARGEST potential for a breach in security/safety resides somewhere between the monitor and the chair.

---

### Post by connorh123 on 2009-05-07
If you feel you need a virus scanner, look in add/remove, and type in virus. It scans all of your files.

---

### Post by albinootje on 2009-05-07
> **gymophett said:**
> Can Linux really get a virus? 

Yes. See here : [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
> 
I heard it can, but it would only affect Gnome or KDE. 

You're probably referring to this : [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)
> 
It cant get to your core system.

Indeed, normally not.
But it can if the attacker can use a root exploit, or if the attacker manages to let you type in your password to run sudo.
> 
I really don't want Linux to even be able to have viruses, it is getting bigger, and I don't want it to turn to crap. :(

The problem with the older versions of MS-Windows is that a lot of home users use the default user account from the installation which has administration rights. Another problem is that MS-Windows will happily run/execute .bat .com .exe .scr etc. if you want to by simply double clicking on it.

In Linux this is not at all not like that, you simply cannot execute a file (For example within Firefox or Thunderbird) if it doesn't have the executable bit (with the current exception of .desktop files in Gnome and KDE).

Another problem with MS-Windows is that MS-IE had been tightly integrated into the OS, which made it even more difficult to protect against viruses, also because MS-Windows is not a true multi-user OS, it is still carrying the design failures of the one user OS called DOS.

---

### Post by aysiu on 2009-05-07
> **gymophett said:**
> Ok, please don't move this to recurring questions. There needs to be an updated thread. It is a recurring discussion, though, and there doesn't need to be an updated thread.

All the threads on this just repeat the same stuff, believe me. I've been here a long time now.

Here are the threads on this topic that were posted to even in just the last *week*:
[Does ubuntu have viruses](http://ubuntuforums.org/showthread.php?t=1131534)
[Virus, malware and spyware scanners?](http://ubuntuforums.org/showthread.php?t=1149516)
[ Reminder: Social engineering still works on Linux](http://ubuntuforums.org/showthread.php?t=1120670)
[Anti-Virus and Linux](http://ubuntuforums.org/showthread.php?t=1131189)

---

### Post by nathang1392 on 2009-05-07
i know this is a little off topic and all but i have a question...its gonna sound dumb, but what exactly does a virus do? i mean can it hurt anything outside of software?

---

### Post by suitedaces on 2009-05-07
> **Skripka said:**
> In contemporary OSes, the single LARGEST potential for a breach in security/safety resides somewhere between the monitor and the chair.

I've never trusted my keyboard.

---

### Post by Calmatory on 2009-05-07
Virus free somehow, but definitely not _malware free_. 

From time to time there are exploits found from software which possibly allow root access. Then, it takes only around few dozen lines of shell script to infect a machine's boot script, few python scripts to find other computers to exploit and report them to the malware creator.

Yes, this is possible but **highly** unlikely, unless you ask for it. ;)

---

### Post by connorh123 on 2009-05-07
It infects your files and destroys your computer.

---

### Post by aysiu on 2009-05-07
> **nathang1392 said:**
> i know this is a little off topic and all but i have a question...its gonna sound dumb, but what exactly does a virus do? i mean can it hurt anything outside of software?
If malware of some kind infects your computer, it can do *anything* it wants.

It could just sit there.

Or it could erase all your files.

Or it could log everything you type. It could use your computer to launch denial of service attacks.

It could start sending spam from your computer.

It has control of your computer and can do whatever it wants. You do not want your computer to be infected with malware.

Unfortunately, most users don't care about security. They just want a placebo (i.e., antivirus) to pretend to protect themselves with to make themselves feel better.

---

### Post by linsux on 2009-05-07
I'll start off by saying that I don't understand why "Well, it won't ruin the core of your system, just the home folder!" is something to be proud of. Maybe on a multi user system, or on servers this is could be useful, but the fact remains: All of my personal data is in my home folder! I could care less if I lost the core files, because I would just reinstall and attach the new stuff to my home partition, and that's the case for many desktop users.

Yes, there are viruses for Linux (though, there's probably not any in the wild currently) and they are rare. There are many reasons for this; Linux has a smaller desktop market share, Linux has a history of being somewhat secure and getting updates quickly, it's less integrated, it interacts with the user differently and the way it does this makes it harder for viruses to spread, the user-base is much more tech savvy than some other operating systems, etc...

It's pretty safe to say that viruses are of little concern for Linux users. But, remember that it's always possible and as more people start to use it, the sooner the day will come before there's a sizable attack on the operating system. People who write viruses are very good at what they do, and I'm sure there are many holes in the Linux kernel (and the rest of the large desktop components) just waiting to be abused. Last year they found a hole in the kernel that allowed access to the root account. Anything is possible.

---

### Post by CyanideSyntax on 2009-05-07
Basicly, your secure.

But, there are "rampid bugs," if you will.
They could screw up your GUI, but are very simple to get rid of.

They are in no way viruses, just developer mistakes, or system errors.

---

### Post by aysiu on 2009-05-07
> **linsux said:**
> 
It's pretty safe to say that viruses are of little concern for Linux users. But, remember that it's always possible and as more people start to use it, the sooner the day will come before there's a sizable attack on the operating system. People who write viruses are very good at what they do, and I'm sure there are many holes in the Linux kernel (and the rest of the large desktop components) just waiting to be abused. Last year they found a hole in the kernel that allowed access to the root account. Anything is possible. Yes, it's very important that people not get complacent or smug. I don't believe Linux is invincible, and nobody should.

What really annoys me is people thinking "Oh, I'll install antivirus, just in case..."

Antivirus is useless!

Really. If another flaw in the kernel gets discovered, what will antivirus do? Nothing.

So, yeah, Linux isn't invincible. Not big news. Antivirus is useless. Also should be not big news.

If people are paranoid, they should read [this guide](http://ubuntuforums.org/showthread.php?t=510812).

---

### Post by jwbrase on 2009-05-07
> **linsux said:**
> I'll start off by saying that I don't understand why "Well, it won't ruin the core of your system, just the home folder!" is something to be proud of. Maybe on a multi user system, or on servers this is could be useful, but the fact remains: All of my personal data is in my home folder! I could care less if I lost the core files, because I would just reinstall and attach the new stuff to my home partition, and that's the case for many desktop users.

Well, if it can get to the core of your system, it can infect *every* user's home folder and destroy *every* user's data, not just the user who was using the system when it got infected. Also, if the virus can infect the core of the system, it can make it alot harder to recover damaged data.

---

### Post by jwbrase on 2009-05-07
> **nathang1392 said:**
> i know this is a little off topic and all but i have a question...its gonna sound dumb, but what exactly does a virus do? i mean can it hurt anything outside of software?

It can destroy data, make software useless, and stuff like that, and a few viruses can even do physical damage to poorly built machines by telling the machine to do something with its hardware that isn't safe.

The big problem with the question "can it hurt anything outside of software" is that just hurting software without doing any physical damage can already be harmful enough.

---

### Post by Sef on 2009-05-07
>  					Originally Posted by **nathang1392** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7234861#post7234861") 				
 				*i know this is a little off topic and all but i have a question...its gonna sound dumb, but what exactly does a virus do? i mean can it hurt anything outside of software?*
 			 		 	 	 It can destroy data, make software useless, and stuff like that, and a few viruses can even do physical damage to poorly built machines by telling the machine to do something with its hardware that isn't safe.

The big problem with the question "can it hurt anything outside of software" is that just hurting software without doing any physical damage can already be harmful enough.

Also they can make your computer part of a spam bot.

---

### Post by albinootje on 2009-05-07
> **jwbrase said:**
> Well, if it can get to the core of your system, it can infect *every* user's home folder and destroy *every* user's data, not just the user who was using the system when it got infected. Also, if the virus can infect the core of the system, it can make it alot harder to recover damaged data.

Not only that, but if an attacker in Linux manages to get "root", then the chapter about rootkits suddenly applies, in other words you're "0wned".

In the older versions of MS-Windows, where users are running with administration rights all the time, this would be very very easy, one bug in your web browser, and you can lose the control over the whole machine, and then become part of a giant spam bot net, even after rebooting etc. :(

---

### Post by linsux on 2009-05-07
> **jwbrase said:**
> Well, if it can get to the core of your system, it can infect *every* user's home folder and destroy *every* user's data, not just the user who was using the system when it got infected. Also, if the virus can infect the core of the system, it can make it alot harder to recover damaged data.

That's true, and I pointed that out. But, programs can be reinstalled, I can't reinstall my personal files.

My point was this:

I would just be just as pissed if it only touched my personal files.

---

### Post by jwbrase on 2009-05-08
Except that your data might in fact be recoverable if the system in general is safe, whereas if /* gets infected, and your home directory is an infection risk to /* on any computer that connects to it, you might be forced to wipe everything.

And my point was this:

If it only affects /home/you/*, you're the only one that's pissed.

If it affects /*, every user on that system is pissed. And if you got the virus while doing something really unsafe like browsing websites of ill repute, they're pissed *at you*.

---

### Post by doas777 on 2009-05-08
> **gymophett said:**
> Ok, please don't move this to recurring questions. There needs to be an updated thread.

Back to topic. Can Linux really get a virus? I heard it can, but it would only affect Gnome or KDE. It cant get to your core system.
I really don't want Linux to even be able to have viruses, it is getting bigger, and I don't want it to turn to crap. :(

ok, please remember there are several families of malware (of which viruses are one). some of them can affect ubuntu, others cannot. 

Viruses- a parasitic peice of code that targets a specific applications vulnerability to acomplish its aims, and to spread by vectors like email, disks, etc. they can spread over net protocols but this is rare. viruses can be prevented via secure application design.
 
Worms- a pathogenic program, that contains all the code needed to accomplish it;s aims, and to spread itself via more flexible means than viruses. network protocol infection is common. worms can be prevented via secure Os design.

Trojans- non-spreading malware, that the user is tricked (knowingly or not) into downloading and executing, to acheive its aims. trojans are the most common form of windows malware these days. you cant scan for stupid.

Rootkits- a low level comprimise of the operating system kernel. this allows escalation of privledge and hiding bad actions from monitoring software. you''ll never know a good rootkit is there. they are scary.

spyware/adware- usually a purely browser comprimise, which may threaten your privacy and often system stability.

ok, so Linux is not very infectable with viruses. there have been some wormable vulnerabilities in past, but I don't believe that there are any current ones in the wild.

Trojans are a theoretical problem, but are rare, as few people run linux. as spear-phishing attacks increase however, it becomes more likely that visible targets may have issues with custom trojans.

Rootkits are a problem for linux, and are used to complete control over a comprimised linux server. 

spyware/adware are a problem for linux, as they only need the browser itself to be evil, so if it works in firefox in windows, it prolly works as well on linux.

people are divided on whether having wine installed will allow windows malware to run sucessfully on linux. i've seen stories online to support both positions.

have fun,

---

