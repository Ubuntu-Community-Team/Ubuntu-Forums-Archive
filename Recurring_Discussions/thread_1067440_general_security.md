---
title: "general security"
date: 2009-02-11
forum: Recurring Discussions
---

### Post by hot dog on 2009-02-11
I've been a Windows user for most of the time...

I just installed Ubuntu 8.04 onto an old desktop.  

One of the things that first comes to mind is, how much more secure is Linux than Windows?

From what I've read so far, Linux deals with permissions differently than Windows in the sense that anything that needs to be installed requires root privileges while Windows does not require root privilages.

In a nut shell, that what I've gathered... Could anyone describe more specifically why Linux is more secure?  :|

thanks

---

### Post by x33a on 2009-02-11
apart from permissions, linux has only a few known (useless) virii. and, linux doesn't keep your ports open in the background unless you specify an application to do so.

---

### Post by acracker on 2009-02-11
A lot of the famed security of Linux comes from the ability given to the user to secure their system. For instance, it is entirely possible to have a Windows computer that is more secure than an Ubuntu Linux system; it's a balance between how much time you want to spend on you system configuring things and what you need your system to do. Ubuntu just seems to make it easier to secure your system than Windows does.

Check out the program ufw for an easy way to lock down ports. Or, if you want more control, look into iptables.

---

### Post by trikster_x on 2009-02-11
How much more secure linux is than windows will all depend on the user.  The biggest part of Linux security is the permissions.  Basically, when you log into your user account, you are merely a guest in your own system.  You can install, run and change files in your account without impedement, but in order to change another user's or a root file, you must tell the system that you are smart enough to do so by typing a set command into a terminal or knowing the password to change things as a root user if there is an interface program for the command you want to perform.  This is the greatest strength and weakness of Linux in my opinion.  While it does keep the soopernoob user from doing irreparable damage to his own system, an overzealous beginner can destroy an entire OS with an errant command, or by allowing a malicious program to run with root privileges.  And therein lies the reason for Linux being a secure OS.  A program is never installed by default with root permissions unless the user specifies it should be, whereas in windows, if you are in an administrative account, programs are considered administrative programs.  That means if you download, install and run a malicious program in linux, the most damage it can do is mess up the user account that it was installed on.  So if a piece of software frags your system, you end up having no one to blame but yourself, because you gave it permission to do it.

---

### Post by georgegerm on 2009-02-11
i hope to hear more on this issue,
i am a skeptic by nature and a newbie to linux
so i do not take for granted the statement linux is more secure
i would love more words on as to why ,,,,
i want to know more but on a level i can understand why these is so,,,
thanks to the posters and more 
thanks

---

### Post by 3rdalbum on 2009-02-11
In my signature there is a link to "permanent articles" on my blog. One of those is an article of what, in my opinion, makes Linux more secure than Windows.

---

### Post by overlord.gaurav on 2009-02-11
Perhaps [this article]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") might help you!

---

### Post by Vaedrah on 2009-02-11
so if I understand you trickster, the "security" in Linux/Ubuntu etc is to "protect" - "you" against "you"

Otherwise protectionism can be over-leavening. For example, it's reasonable to take car keys out when you leave a car - but what if someone wants to smash your windscreen - do you want a wire cage over your car when you leave?

Obviously, security is relative and should be connected (in some way) to the likelihood of security transgressions - going overboard can be far worse than the threat!

The main reason (it seems to me) is publication space.

Windows is very public.

Linux is not well publicized.

Therefore people attack windows (viruses etc) and of course Linux stuff is too small a picking!

This is the main reason Linux is "secure"

I don't give any audience to moronic reasons that "security" is in any way connected to "some other mechanism" protects a really untalented dupe "being protected against free will"

Loosing a OS in no big deal - it takes minor intelligence to "back up files". Are we children? Why let a OS treat us as children?

Why not respect ourselves and retain control on any OS - if you are a child, then fine, let mummy guide your hand. To those of us more mature - we are responsible for our actions. So somewhat wants to "nappy us" from my position - keep that in your wet-dreams.

---

### Post by georgegerm on 2009-02-11
> **overlord.gaurav said:**
> Perhaps [this article]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses") might help you!

thank you it did help
and the next poster (thanks) basically says the same as the wiki article
linux is more secure simply because the would be attackers have little to gain in proportion to getting to windows, and thus is not a matter of vulnerability but economics...
sad i thought linux would be simply more secure for other reasons,
and even sadder is the fact i have no idea how to really protect my laptop (ubu hardy) without a big song & dance on the free antivirus out there for linux (just in case more people notice how popular ubu is getting, along with linux in general)....
in great gratitude of the failure of windblows vista, and its sure to crash windblows 7...
and not forgetting the fact that linux is really getting popular due to the simple versions like ubu who are simple yet interesting distros to use,, ie. linux is no longer just for geeks,,
it is the real deal

---

### Post by mgranet on 2009-02-12
> **Vaedrah said:**
> so if I understand you trickster, the "security" in Linux/Ubuntu etc is to "protect" - "you" against "you"

Otherwise protectionism can be over-leavening. For example, it's reasonable to take car keys out when you leave a car - but what if someone wants to smash your windscreen - do you want a wire cage over your car when you leave?

Obviously, security is relative and should be connected (in some way) to the likelihood of security transgressions - going overboard can be far worse than the threat!

The main reason (it seems to me) is publication space.

Windows is very public.

Linux is not well publicized.

Therefore people attack windows (viruses etc) and of course Linux stuff is too small a picking!

This is the main reason Linux is "secure"

I don't give any audience to moronic reasons that "security" is in any way connected to "some other mechanism" protects a really untalented dupe "being protected against free will"

Loosing a OS in no big deal - it takes minor intelligence to "back up files". Are we children? Why let a OS treat us as children?

Why not respect ourselves and retain control on any OS - if you are a child, then fine, let mummy guide your hand. To those of us more mature - we are responsible for our actions. So somewhat wants to "nappy us" from my position - keep that in your wet-dreams.

I really hate to be the Dwight Schrute of this thread, but this is wrong on many levels. There is no such thing as security through obscurity. It simply does not exist. Linux is secure for a variety of reasons; it separates user tasks from admin tasks, it uses file and user permissions instead of a central registry, and from protections available for the kernel, such as SELinux and AppArmor, as well as a pre-configured firewall. It has nothing to do with user count or user ability.

---

### Post by georgegerm on 2009-02-12
ok now for the newbi in me
i am getting quite confused
is it or is not safer ...
now i speak in terms of an os period with no extras, versus windows with extras ie. firewall and antivirus as in kasp. internet security as an example..
first i get the impression its a matter of numbers (users) and now it seems thats not the case ????????????????
i do realize there's no general consensus or at it appears there is none

---

### Post by jerome1232 on 2009-02-12
Your going to get alot of different and varied opinions.

Why not look in the Security Sections of this forum, there's a sticky about security here.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Linux is built from the ground up as a multiuser system. It boils down to a user can only destroy his own account and not the entire system, he doesn't have permissions to do anything to the rest of the system. Programs are not exectuable becuase they have  a .bin or .sh extension, the user has to expliclty set the permissions of the file to allow execution. 

In order to affect the entire system one has to be able to get root access.

Security can be a highly debated subject. In summary I would say Linux and Unix like Operating Systems are by design very secure. 

However no Operating System can protect against stupid users running x malware/trojan/virus as the root user. (akin to running programs as admin in Windows)

On that note I believe Windows Vista has taken a big step forward in security, not allowing a user to write to directories outside of their own users and the public directory (Similiar to how it works in Linux) without a UAC prompt popping up.

---

### Post by georgegerm on 2009-02-12
> **jerome1232 said:**
> Your going to get alot of different and varied opinions.

Why not look in the Security Sections of this forum, there's a sticky about security here.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Linux is built from the ground up as a multiuser system. It boils down to a user can only destroy his own account and not the entire system, he doesn't have permissions to do anything to the rest of the system. Programs are not exectuable becuase they have  a .bin or .sh extension, the user has to expliclty set the permissions of the file to allow execution. 

In order to affect the entire system one has to be able to get root access.

Security can be a highly debated subject. In summary I would say Linux and Unix like Operating Systems are by design very secure. 

However no Operating System can protect against stupid users running x malware/trojan/virus as the root user. (akin to running programs as admin in Windows)

On that note I believe Windows Vista has taken a big step forward in security, not allowing a user to write to directories outside of their own users and the public directory (Similiar to how it works in Linux) without a UAC prompt popping up.

thank you
i will go read
but as newbi to linux one gets the wrong impression or direction i should say..
and certainly the fact there is no general consensus i find good as we can all benefit from different approaches as to how to make it safer as long as it does not go into chaos instead of method

---

### Post by hyper_ch on 2009-02-12
> **Vaedrah said:**
> The main reason (it seems to me) is publication space.

Windows is very public.

Linux is not well publicized.

Therefore people attack windows (viruses etc) and of course Linux stuff is too small a picking!

This is the main reason Linux is "secure"

You're quite wrong on that. Number of base installs has nothing to do with he security of the system. e.g. most webservers do run Linux and Apache for that matter. However IIS on Windows is a lot more attacked (and breached). Why? Because if you find a weakness in IIS you can control the whole machine. If you find a weakness in Apache you can just control the webserver.

Furthermore only in the desktop computer market there's a windows dominance. There are more devices out there running any form of linux than windows. Large enterprises like google and banks run linux or unix and from a ROI perspective it would be a lot "better" for the malicious hacker to get access to one of those than to John Doe's home computer.

---

### Post by Vaedrah on 2009-02-12
If people wish to quote me and then say I am wrong - I don't mind. Security is in the eye of the beholder. At least to these people, at least build a credible response not just some emotive.

Even a barking dog is just an emotive response.

It is said "the road to hell is paved with good intentions" - well perhaps it is and Linux may have good intentions. At the end of the day, people are responsible for their actions and should take it on board as so - an OS is NO SUBSTITUTE - well others here may wish some namby-pamby alternative to common sense. 

I prefer simple common sense.

---

### Post by jrusso2 on 2009-02-12
> **hot dog said:**
> I've been a Windows user for most of the time...

I just installed Ubuntu 8.04 onto an old desktop.  

One of the things that first comes to mind is, how much more secure is Linux than Windows?

From what I've read so far, Linux deals with permissions differently than Windows in the sense that anything that needs to be installed requires root privileges while Windows does not require root privilages.

In a nut shell, that what I've gathered... Could anyone describe more specifically why Linux is more secure?  :|

thanks

You can still install into areas where users have rights like their home directory but its best to install with sudo.

---

### Post by mgranet on 2009-02-13
> **Vaedrah said:**
> If people wish to quote me and then say I am wrong - I don't mind. Security is in the eye of the beholder. At least to these people, at least build a credible response not just some emotive.

Even a barking dog is just an emotive response.

It is said "the road to hell is paved with good intentions" - well perhaps it is and Linux may have good intentions. At the end of the day, people are responsible for their actions and should take it on board as so - an OS is NO SUBSTITUTE - well others here may wish some namby-pamby alternative to common sense. 

I prefer simple common sense.

You can't emotionalize security. Also, it is not in the eye of the beholder. Ever.

---

### Post by bodhi.zazen on 2009-02-13
Moved to the recurring discussions.

Just an FYI: We have reviewed these types of threads amongst the staff and there is a general consensus we would like to let us say improve the quality of security discussions.

This means - Reduce trolling, reduce arguments re: semantics, etc.

The goal is to provide higher quality security information and eliminate recurring discussions.

Edit: Please teach and use proper vocabulary in these threads. If you do not know the definition of a virus, social engineering, worms, malware, root kits, etc look them up and be wiling to learn them.

@ the OP: The bottom line is that this thread is nothing more then an opinion. If you are interested in security start reading and feel free to ask technical questions.

---

### Post by cardinals_fan on 2009-02-13
[http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

There are no absolutes.  Security depends on the user, and is therefore as varied as all the computer users in the world.

---

