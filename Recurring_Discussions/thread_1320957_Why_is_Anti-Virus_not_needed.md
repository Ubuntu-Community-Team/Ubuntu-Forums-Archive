---
title: "Why is Anti-Virus not needed?"
date: 2009-11-09
forum: Recurring Discussions
---

### Post by Joe Ker1086 on 2009-11-09
Ok, I have never gotten a definitive answer on this one. What exactly is the reason that people say there is no need to run AV or anti spyware software on linux/unix?

---

### Post by michy99 on 2009-11-09
The main reason is that a virus would have to have root privileges to do any damage, and it can only do that if you let it. That's one reason you don't normally operate as root.

---

### Post by Calixte on 2009-11-09
Simply because there are no viruses on Linux. That may be because of the low market share Linux has or because it is inherently more secure (The debate is on, but you can guess where I stand ;))

---

### Post by Somme on 2009-11-09
[Read this article]("http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed") ..

> **Calixte said:**
> Simply because there are no viruses on Linux. That may be because of the low market share Linux has or because it is inherently more secure (The debate is on, but you can guess where I stand ;))

You might be wrong .. I have one :twisted:

---

### Post by Jean-Danjou on 2009-11-09
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by Commander_Keen on 2009-11-09
Most Virus are contained in a file called, filename.exe, or  filename.com
Linux does not know how to handle any file name that end with exe or Com.
  Even it Linux did know how to run an Exe file, the file structor between Windows and Linux is completly different. that the file would not be able to make heads or tails out of it.

---

### Post by Joe Ker1086 on 2009-11-09
so basically the main reason that viruses dont exist is becuase there arent enough ppl using linux to warrant a hacker building them for linux programming? I understand that it wouldnt make that much sense but lets say linux really takes off, and it becomes 50% of the market, Will linux users be in alot more danger b/c there isnt really any anti spyware/virus software?

---

### Post by The Cog on 2009-11-09
Agreed, there are no known Linux viruses in the wild at the moment. And since AV programs look for signatures of known viruses, there is really nothing to look for. Existing Linux AV programs are really just to catch windows viruses that you might receive acquire from downloads, emails etc and pass on to other windows users.

However, root kits for Linux do exist and get installed by hackers if they manage to get in, usually by weak SSH passwords. So it is possibly worth looking at chkrootkit and rkhunter. The situation is nowhere near as dire as with windows though.

---

### Post by sisco311 on 2009-11-09
> **Joe Ker1086 said:**
> so basically the main reason that viruses dont exist is becuase there arent enough ppl using linux to warrant a hacker building them for linux programming? I understand that it wouldnt make that much sense but lets say linux really takes off, and it becomes 50% of the market, Will linux users be in alot more danger b/c there isnt really any anti spyware/virus software?

Nope ~60% of servers run Linux. 

[http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses]("http://en.wikipedia.org/wiki/Linux_malware#Viruses_and_trojan_horses")

[thread=510812][COLOR="Red"]Ubuntu Security[/COLOR][/thread]

---

### Post by alphaniner on 2009-11-09
Linux users may become a more enticing target, but that doesn't mean we will be in so much more danger.  Windows and Linux are different from the ground up.  In Linux, ownership and permissions form the foundation of the filesystem, and a cornerstone of security.  Contrast this with Windows UAC, which is a hacked-on afterthought.

---

### Post by NoaHall on 2009-11-09
Linux works in a different way - a much more secure way. With windows, anyone can do harm simply by opening a webpage, as they are run with enough privileges to cause major damage to the system files. In Linux, nothing outside your /home/ can be accessed without the right privileges. Also, if a dangerous application is made, then the source is easily viewed and fixed (unless closed source, and that's always a reason for being wary).

---

### Post by mrmooge88 on 2009-11-09
I also feel that the basic way Linux usually gets an application is very secure. When you use apt, synaptic, or aptitude to install something, it only comes from trusted sources. Most people only use their main distro's software repository, which has been carefully created and managed.

While Window's users have to go to a website, which they hope is the correct one for their desired program. Then download and install the software. This allows hackers to fake legitimate websites to get access to your computer.

---

### Post by cariboo on 2009-11-09
> **Somme said:**
> [Read this article]("http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed") ..



You might be wrong .. I have one :twisted:

You have one what?

---

### Post by sisco311 on 2009-11-09
> **cariboo907 said:**
> You have one what?

[evilmalware]("http://www.gnu.org/fun/jokes/evilmalware.html")?

---

### Post by Somme on 2009-11-09
> **cariboo907 said:**
> You have one what?

Before we go on, I should edit my previous post ( have -> had ). All I wanted to say was, 2 weeks ago I had a virus ( and I don't refer to the term and it's definition .. virus, malware, trojan, etc. - they all are under the same hood anyway ), which successfully broke ( constantly got new Firefox windows with all kinds of websites, including some fake Spyware cleaner, and upon destroying the process, which I thought should be the right one, I ended up with no home directory ) 2 of my 3 Ubuntu powered boxes. As stated previously, they are very uncommon but still possible.

---

### Post by Chronon on 2009-11-09
It sounds like some malicious javascript, not a virus.  Do you use NoScript?  I have never had this happen with either Windows or Linux versions of firefox when running with this add-on.

---

### Post by Joe Ker1086 on 2009-11-09
Thanks guys, Makes a lot more sense now.

---

### Post by wojox on 2009-11-09
> **Somme said:**
> Before we go on, I should edit my previous post ( have -> had ). All I wanted to say was, 2 weeks ago I had a virus ( and I don't refer to the term and it's definition .. virus, malware, trojan, etc. - they all are under the same hood anyway ), which successfully broke ( constantly got new Firefox windows with all kinds of websites, including some fake Spyware cleaner, and upon destroying the process, which I thought should be the right one, I ended up with no home directory ) 2 of my 3 Ubuntu powered boxes. As stated previously, they are very uncommon but still possible.

You need Addblock Plus

Did you install Firefox in your /home directory?

---

### Post by Somme on 2009-11-09
> **wojox said:**
> You need Addblock Plus

Did you install Firefox in your /home directory?

Umm ..  it's a part of Ubuntu ( Gnome ). I didn't installed it separately.

---

### Post by SteveHillier on 2009-11-09
Can I throw in further thoughts on this.
There are a number of people who think if they can write an effective virus they will be able to make the Windows world come crashing around our ears - they are out to get at Microsoft specifically.  They are of course just as misguided as those who think that sending lots of spam will cause the internet to stop working!
A lot of people who write virus code are young lads who have just found out how to program, they take someone elses virus code and make a few mods and off we go again.  I suspect that their level of undertanding would not extend to the more complex understanding required in Linux based coding and so they simply cannot be bothered to do it.
Most Linux users are people who want to extend and enhance the system not destroy it.  Their mind set would be not to do it.

---

### Post by NoaHall on 2009-11-09
> **Somme said:**
> Umm ..  it's a part of Ubuntu ( Gnome ). I didn't installed it separately.

It's still not a virus. It's adware, probably because of the sites you had open.

---

### Post by Chronon on 2009-11-09
How do you know their motives?  Maybe they just want notoriety.  Some malware has financial payoff, etc.

---

### Post by wildweathel on 2009-11-09
Let's not be silly.  *[There is Linux malware.]("http://en.wikipedia.org/wiki/Linux_malware#Threats")  *It exists, it hates you and it's out to get you.  (cue: OMINOUS STRINGS)  The difference is the security model and the way vulnerabilities are detected and fixed.

All malware depends on a flaw of some sort or another in the security of a system.  This could be a flaw in the software a "security bug."  It could be a flaw in configuration: someone has set up SSH to allow root logins with a weak password (this counts on Ubuntu: if Chuck Cracker has the password to your administrative account, he has root, too, thanks to sudo).  Finally, there could be a flaw in the system.  MS-DOS, as an extreme example, was not designed for any privilege separation at all, so exploits are trivial.

The security model is decent, though not extremely robust.  Generally, Linux systems are good at protecting system files.  User's data isn't as well guarded: a misbehaving program can easily wipe your entire home directory.  This is an area that's seeing slow improvement: AppArmor, PolicyKit, stack overflow protection, etc. provide lots of new infrastructure, but there's still the question of putting it to use without driving the user crazy.  Let's not get complacent here, because *Ubuntu's security model has its limits*.  Just being better than Windows shouldn't be good enough.

Configuration is still, like with all other systems, the administrator's responsibility.  'Nuff said.

That leaves bugs, which no one really has control of.  All security bugs begin with programmer error, which can be reduced but not eliminated.  Originally, nobody knows about it.  Once it's noticed, it can either be exploited or fixed.  _Security is broken by a bug when and only when a bug is exploited before it is fixed_.With that in mind, consider what a malware scanner (whether a "spyware detector" or "antivirus" or whatever) does: it keeps a list of "bad programs" and looks through your computer, using disk and cpu time, for anything on that list.   This technique can only protect you when 1) a vulnerability is known to your attacker, 2) the attack has been around long enough for it to have been blacklisted, but 3) the vulnerability has not been fixed yet.  

If the vendor of proprietary software or the maintainer of free software has a history of not fixing vulnerabilities before the keeper of your blacklist identifies malware, then yes, you will benefit from a malware detector.  But, in the free software world, this is a rare occurrence.  When development is open it becomes easier to just *patch that damn hole* than try to chase down every single wild exploit that uses it.

Does that leave room for after-the-fact detection?  Yes.  It's possible a vulnerability be found and exploited before it's patched.  But, these "intrusion-detection" systems are not canned "set and forget" deals.  Their purpose is to notice *unknown* threats, and that takes skill and experience on the part of the system administrator.

Bottom line: Ubuntu doesn't have a role for antivirus to play.  We kill malware by closing holes, not deleting worms.  If you need more security, research your options and consider your needs.  If you're too busy running your business to do that, hire someone (trustworthy!) who can.

---

### Post by Chronon on 2009-11-09
Solid post.

---

### Post by c2006 on 2009-11-09
Agreed. I still have antivirus installed on here (ClamAV), but mainly because I use USB drives and don't want to inadvertently infect Windows users.

---

