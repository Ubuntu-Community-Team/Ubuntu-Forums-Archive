---
title: "How exactly is Ubuntu more secure??"
date: 2010-02-01
forum: Recurring Discussions
---

### Post by PCA on 2010-02-01
Hello guys,
            I have been trying my best to learn as much as I can about Ubuntu. I'm quite satisfied with it, mainly because it seems to be a lot more faster than my XP(with my h/w configuration I didn't think it was wise to install 7). One of the things that I have been hearing is that it's quite secure relative to Windows.

            After searching the net, what I have come to know is that the Kernel is quite robust, the restrictions on user accounts sort of contain any virii spread to a local area, there are only a handful of virii due to the low market share etc.

            Is there any truth in all these? how exactly is the kernel more robust? regarding the restrictions, can't the same be achieved by setting up user accounts properly in Windows? about the virii, when more people start using Ubuntu, won't this advantage be nullified?

            Also I would like to know more reasons why it's considered more secure.

thanks in advance

---

### Post by Monotoko on 2010-02-01
The kernal is more rebust because it has a lot of people working on it, and you can easily view the source, test anything you like, etc, it is the work of a community that makes the kernal better...the great philosophy of open source software :)

About the viruses, it can indeed be secure in Windows if you set up the permissions properly, if your on a limited account you have a reduced risk of getting any viruses. But how many people do you know who will use a limited account, as opposed to there first "administrator" account in Windows.

In ubuntu (and linux in general) it is customary for the first account you set up to be a limited account, then gain root access by using a special account (the "root" account)

And theoretically, if more people start using linux, someone will try and find an exploit, but with the amount of people working on the kernal and other bits of linux, because of its open-sourceness, any exploits will probably be fixed before anyone has a chance to use them.

---

### Post by arubislander on 2010-02-01
There's lots of information about that here and elsewhere... and the plural of *virus* in English really is *viruses* and not *virii* (as it's not Latin we're speaking, and the word is not spelled *virius*)

But you are on to something though. If the user scheme in Windows were set up to mimic the one on Linux then Windows would be more secure (even though that might be simply because not every user of the PC would be able to install stuff...)

Considering the large amount of servers running some flavor of Linux it could be argued by comparing their track record with Windows servers that Linux security has proven itself to be more robust than Windows security irrespective of it's market share. And since the Linux desktops share the same kernel as their server counterparts in principle, then the kernel at least would boast the same robustness.

---

### Post by Vaphell on 2010-02-01
> regarding the restrictions, can't the same be achieved by setting up user accounts properly in Windows?

yes it can, newer windows versions have proper architecture regarding user restrictions, but there are few big problems - many legacy apps require admin privileges, even many quite new apps require that because they were written by the lame and lazy programmers. Windows users in general prefer convenience to security and any amount of configuration required to secure their pcs is a pain in the ***, so they just grant themselves permanent admin rights. Sheer inertia of decades of bad habits is tough to overcome. Linux was never meant to be for clueless users who would sell their grandma for convenience. Security was always taken into account in design phase, not as an afterthought like in case of various windows systems.

> when more people start using Ubuntu, won't this advantage be nullified?

Security through obscurity (low market share of linux systems) is a very weak layer, it's cool to have as you don't need to run av software at the moment, but nobody should depend on that. At 10% of market someone would target linux with malicious code. After all MacOS is an unix at 5-10% and there are viruses.

---

### Post by howefield on 2010-02-01
> **arubislander said:**
> ...Linux has proven itself to be more robust than Windows security irrespective of it's market share.

Since we are having an English lesson, "it's" is a contraction of "it is". Makes your sentence sound a little weird. ;)

For the OP, have a read here for more info on security.

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by aysiu on 2010-02-01
> **PCA said:**
> 
            Is there any truth in all these? how exactly is the kernel more robust? regarding the restrictions, can't the same be achieved by setting up user accounts properly in Windows? about the virii, when more people start using Ubuntu, won't this advantage be nullified?

            Also I would like to know more reasons why it's considered more secure.

thanks in advance I don't really know much about the kernel being robust, but I think these are the factors that make Ubuntu more secure right now: [list=1][*]*sudo* restricts even the administrator users from operating as full admins without a password authentication. In Windows 7, you just get a UAC prompt, which can be easily turned off.[*]Many people still use Windows XP and run as administrator (which is the default). I am probably the only person I know (in real life anyway) who purposefully runs XP as a limited user (some people are forced to by their workplace--not the same thing).[*]Microsoft seems to have an arbitrary policy when it comes to fixing security bugs. Sometimes they'll be fixed right away. Other times they'll be fixed without Microsoft admitting there was even a bug in the first place. And still other times, the bug will just go unpatched for years inexplicably. In Linux, there are times when security flaws are unpatched for years, but it's usually because no one is aware of the flaw for all those years. Once the flaw is discovered, it's patched right away.[*]The primary means of obtaining software in Linux is through a trusted repository (akin to the iTunes App Store). That means you are far less likely to be installing software from random dodgy sites, which means you are far less likely to be installing malware.[*]At the moment, Linux has a higher proportion of power users than Windows does, which means its users are far more likely to employ good security practices and have computing common sense.[/list] But you're absolutely right--if you install Windows updates regularly and run a limited user account in Windows, you're pretty secure. I put together a list of things you can do to make Windows just as secure as Linux:
[http://www.psychocats.net/ubuntucat/windowssecurity/](http://www.psychocats.net/ubuntucat/windowssecurity/)

Likewise, if Windows users switch to Linux in droves **and** do not better educate themselves, they'll be just as vulnerable to social engineering attacks on Linux as they were on Windows. Social engineering works on any platform, since it takes advantage of user gullibility and ignorance instead of flaws in the software.

---

### Post by adam814 on 2010-02-01
For one thing Linux was built from the beginning as a multi-user operating system.  That was a feature added to Windows later (before NTFS it had no access controls on the filesystem).

It's also worth noting that not everyone who runs Linux runs the exact same kernel.  In Windows, at least for any given Version/Service Pack AFAIK this is the case.  This diversity makes exploiting vulnerabilities that much harder.

The UAC setup in Vista (haven't used 7 much, I've heard it's less annoying about it though) will help prevent virus/malware infection provided the user has the presence of mind to question why the app they're running needs to run as Administrator.  It is an improvement over XP where no such system is in place.

I wouldn't have too much confidence in small market share as the sole protection from malware.  UNIX-like systems aren't invincible.  For example now that it's becoming popular there are more Mac OS X malware out there than there were initially.  But I believe they've all been cases where a user downloaded and installed pirated software from torrent sites.  Installing software from untrusted sources can get you nasty rootkit or trojan on Linux just as easily, so be careful where you get your apps from the same way you would with Windows (Ubuntu repos are always safe, beyond that YMMV).

---

### Post by lykwydchykyn on 2010-02-01
"more secure" is meaningless outside of a context.  Secure from what?

It's like asking, "Are brick houses really more secure than wooden houses?"

Well, they're a little more secure from fires and termites, but no less likely to be burglarized if you don't have an alarm system or strong locks.

That's not an attempt at a 1:1 analogy between Windows and Linux, but just to illustrate that when you talk about security you have to look at it from the standpoint of how individual threats are addressed.

Beware of anyone who makes blanket statements about security on the basis of individual metrics  -- e.g. "We're more secure because we release more security patches more frequently" or "We're more secure because there are fewer viruses for our platform".

---

### Post by aysiu on 2010-02-01
> **adam814 said:**
> 
I wouldn't have too much confidence in small market share as the sole protection from malware.  UNIX-like systems aren't invincible.  For example now that it's becoming popular there are more Mac OS X malware out there than there were initially.  But I believe they've all been cases where a user downloaded and installed pirated software from torrent sites.  Installing software from untrusted sources can get you nasty rootkit or trojan on Linux just as easily, so be careful where you get your apps from the same way you would with Windows (Ubuntu repos are always safe, beyond that YMMV). I'm just going on memory here, too, but all the Mac OS X malware I've read about has all relied on social engineering. I haven't seen any automated compromises yet. But that's the way to do it. If you're going to write malware, why bother looking for flaws in the software (after all, flaws can be patched) when you can just trick the user into giving you the keys to kingdom? Works on any platform, and there are plenty of gullible users out there.

---

### Post by PCA on 2010-02-02
First of all, thank you for all those quick replies :P

@Monotoko, I've heard about that one too. The flaws are open to everyone and therefore removed quickly.

@arubislander, thanks for the advice

@Vaphell, I had some applications like that. They would simply crash when I use them on my limited account. In Karmic, I've installed ClamTk for the sole purpose of removing win viruses.

@Howefield, thanks for the links, they were helpful. I haven't configured the IP tables manually but Firestarter seems to be really good.

@aysiu, you've just found another person who does that:D. People think I'm paranoid when I use a limited account in windows..... who cares

I've never had any security issues with Windows so far, the internet cafe's here are notorious for spreading viruses, so I have been careful when using flash drives.

That being said, I reinstall the OS quite often, because I experiment a lot with certain critical stuff, other times Im just bored;)

Regarding the repository, there are some software that seem to be useful but are not present in the main repository, is it possible to submit something for review?

@adam814, I've heard that one too. The heterogeneity apparently makes it harder for people to write a common 'bad' code. I have a doubt on this. As far as security holes are considered I agree to this point, but when it comes to installing programs, isn't it possible to install something that meant for another distro in ubuntu(rpm using alien for eg)? so you could have a common virus right?

@lykwydchykyn, I agree with that, that's why I wanted to know about the security thing in detail.

@all, I prefer knowing what I'm doing in detail rather than installing some software that would take care of 'everything'.

---

### Post by arubislander on 2010-02-02
> **howefield said:**
> Since we are having an English lesson, "it's" is a contraction of "it is". Makes your sentence sound a little weird. ;)
Touché :D

---

### Post by adam814 on 2010-02-02
> **PCA said:**
>  @adam814, I've heard that one too. The heterogeneity apparently makes it harder for people to write a common 'bad' code. I have a doubt on this. As far as security holes are considered I agree to this point, but when it comes to installing programs, isn't it possible to install something that meant for another distro in ubuntu(rpm using alien for eg)? so you could have a common virus right?


Sure, that's possible alright.  I suppose it could even cross certain architectures (i386 trojan being run on amd64 for example).

I guess my post was a little confusing, I meant it's unlikely a software vulnerability will be shared across all Linux machines since they're all a little different.  If they can convince a user to install it they don't have to worry about exploiting flaws in software.

---

### Post by aysiu on 2010-02-02
> **PCA said:**
> 
That being said, I reinstall the OS quite often, because I experiment a lot with certain critical stuff, other times Im just bored;) If you're talking about Windows, I hope you don't do a reinstall from scratch. You can use CloneZilla or PartImage to create an image of your freshly installed OS so you can just reimage if something goes wrong or if you want a clean slate.

---

### Post by juancarlospaco on 2010-02-02
*Because APT has Super Cow Powers.*

---

### Post by PCA on 2010-02-03
@Aysiu, yeah, I was talking about reinstalling from scratch. Thanks for the info. I'll use Clonezilla from now on. Also, I think it would be quite useful for me in the near future, I'm planning on trying out Gentoo and I have a feeling that I'll mess up something :(

---

### Post by darrenn on 2010-02-12
Also don't be afraid to install windows steadystate. It does wonders to fix a broken install.

---

