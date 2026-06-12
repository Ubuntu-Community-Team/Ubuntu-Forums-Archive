---
title: "Ubuntu what if questionable repository.."
date: 2014-10-11
forum: New to Ubuntu
---

### Post by joonwo on 2014-10-11
hello,
new to ubuntu and it's great.
keep my question short about security. In Ubuntu forums everyone says there are no viruses and it's almost impossible to get one.
i don't fully understand why.
Let's say you install an application from a foreign repo. Isn't there a chance that they have some malware hidden in their programs. And since antivirus for Linux is apparently not very common, you couldn't even check.
Sometimes the Ubuntu Software Center doesn't have the program i need.

Maybe i haven't fully understand the concept of Linux :) thanks !

---

### Post by kc1di on 2014-10-11
Hi joonwo and welcome to Ubuntu,

It's partly the file structure and the way things run in Linux that makes it hard to have a virus, like Windows does.  It's not impossible but there are not many in the wild. 
There are virus checkers for linux however most of them basically check for windows viruses so you want pass them to windows machines
you can install clamtk which is a Linux virus checker it's in the ubuntu repostitories. 
there are also third party virus checkers some free, some not .. 
Bit defender makes one for linux you can get it [here. ]("http://www.bitdefender.com/business/antivirus-for-unices.html")

and[ here is a page]("https://help.ubuntu.com/community/Antivirus") with a good explanation of antivirus for ubuntu and list of possible virus scanners.  
The major point is not many viruses can bring down a Linux system like they can on windows. -- But there are other security problems that must be faced. 
and the best defense is always an alert op and up to date system , so keep the up dates fresh. 
other than that enjoy this fine Distro. 
:)

---

### Post by nerdtron on 2014-10-11
> **joonwo said:**
> 
Let's say you install an application from a foreign repo. Isn't there a chance that they have some malware hidden in their programs. And since antivirus for Linux is apparently not very common, you couldn't even check.
Sometimes the Ubuntu Software Center doesn't have the program i need.


Yes its true. That's why you should use the software from the official repos as much as possible.
Anyway, be sure to trust you foreign repo because you won't know what they put in there.
As for malware, remember in Ubuntu/Linux in general, any program won't run unless you told it to. And any malicious program that would change system settings will require privileges such as your password before they can do so.
Running programs that are not from the official repo is up to you.

---

### Post by whitesmith on 2014-10-11
It's safest to stick with the USC. Someone could theorectically introduce a virus into a package, but the payload would only affect your home directory--not the entire machine, as in that Other Operating System. Unix, from which Linux is derived, was designed to be ground-up secure since it's a multi-user OS. I'm not sure if this is pertinent, but I read that of the 500 fastest supercomputers in the world, Linux runs around 70%, Unix 30%, and Windows exactly 1. These are highly expensive machines running task-critical software. Why would their owners have chosen Linux/Unix if it were not secure?

---

### Post by joonwo on 2014-10-11
> **nerdtron said:**
> Yes its true. That's why you should use the software from the official repos as much as possible.
Anyway, be sure to trust you foreign repo because you won't know what they put in there.
As for malware, remember in Ubuntu/Linux in general, any program won't run unless you told it to. And any malicious program that would change system settings will require privileges such as your password before they can do so.
Running programs that are not from the official repo is up to you.

True. i really like that Linux always asks for permission. I understand that the program can't run if you don't give it permission. But lets say the foreign repo offers a great program, what you don't know it's infected with malware. Linux asks for permission and you grant it super user permission to install. At this point can't the malware take over the computer or delete everything with a command like ```
[FONT=Open Sans]rm -rf /[/FONT]
```??
it has super user permission. Right ?? or not ?


> [COLOR=#000000]but the payload would only affect your home directory--not the entire machine, as in that Other Operating Syste[/COLOR]
why would it only affect my home directory ? don't you have access to everything as super user including Root ?

thanks for helping me understand the system ;)

---

### Post by nerdtron on 2014-10-11
> Linux asks for permission and you grant it super user permission to install.
The password is for USC or apt-get to have permission to install the software. Not run it. And most programs like apache, mysql etc run on your normal username or their own restricted user. Most programs that would require to run as root are scripts (or other programs too) but they would require to authenticate first.

Yes, rm -rf / may still be executed if you run a program from unknown source. We'll that's really a matter of trust (and your own judgement to run it with super user permission) on why you need to run a software on the source you are not sure of?

Open-source programs have their source code released to public. So if the public sees some malicious code, it will get flagged. That's why sticking with the official sources are pretty much secure.
Linux won't be used as servers if it weren't inherently secure. Plus all software will almost always comes from the official repo. Unless you have a special need, you take the source code, compile and run it yourself.

---

### Post by whitesmith on 2014-10-11
> **joonwo said:**
> why would it only affect my home directory ? don't you have access to everything as super user including Root ? thanks for helping me understand the system ;)
The reason is because you are just using root access to **install** the SW. Installing and using are two different things. **Using** the SW generally runs a script in your home directory. Execution occurs in RAM set aside by the system for **your** exclusive use. Remember, Linux is a **multiuser** system, so other users can't be affected when you run what you installed. Damage from a virus is thus confined to your home directory, not the whole machine. I don't know how to express this more clearly.

---

### Post by joonwo on 2014-10-11
> **whitesmith said:**
> The reason is because you are just using root access to **install** the SW. Installing and using are two different things. **Using** the SW generally runs a script in your home directory. Execution occurs in RAM set aside by the system for **your** exclusive use. Remember, Linux is a **multiuser** system, so other users can't be affected when you run what you installed. Damage from a virus is thus confined to your home directory, not the whole machine. I don't know how to express this more clearly.

I finally understand what you guys mean. Coming from MS Windows you always needed to **run a setup **and then install. So the process was the same thing for me.
I thought the whole time using Linux that i am running a programm like in windows to install my stuff. :p thanks ! 

One last thing. let's say the malicious program is installed. you run it, it asks for whatever reason (update, new features etc) to give it super user rights. that's the point where you have to be careful right ?? 
Let's say you trusted it and entered your password. Now the malware could really mess up your system and other users accounts right ??

---

### Post by buzzingrobot on 2014-10-11
The primary reason Linux is subject to fewer attacks than Windows is that there is much more money in attacking Windows machines. Malware is a tool used by criminals to generate income.  

Linux certainly has its share of expoitable bugs.  And, Linux also has its share of gullible and phish-able users.  

The weakest link in the security chain is the user. Why go to the trouble of dealing with either Windows or Linux security and try to sneak malware on to a system?  Just get some user to deliberately install the thing. No software will protect you if you are conned into installing, say, a keylogger.  Just because Linux prompts you for authentication doesn't mean it's going to stop you from installing anything you want, including malware. (Windows also prompts for authentication.)

---

### Post by joonwo on 2014-10-11
> **buzzingrobot said:**
> The primary reason Linux is subject to fewer attacks than Windows is that there is much more money in attacking Windows machines. Malware is a tool used by criminals to generate income.  

Linux certainly has its share of expoitable bugs.  And, Linux also has its share of gullible and phish-able users.  

The weakest link in the security chain is the user. Why go to the trouble of dealing with either Windows or Linux security and try to sneak malware on to a system?  Just get some user to deliberately install the thing. No software will protect you if you are conned into installing, say, a keylogger.  Just because Linux prompts you for authentication doesn't mean it's going to stop you from installing anything you want, including malware. (Windows also prompts for authentication.)

thanks for replying. i was just so fascinated by the fact that people always say linux is absolutely secure. Already watched dozen of youtube videos from linux experts and all claim that it's impossible to get a virus. 
Just didn't understand how it could be impossible. So thanks to you guys i learned it's definitely possible (but not likely) and that the user is the "weakest link".

---

### Post by Irihapeti on 2014-10-11
Part of the "always secure" thing is semantics. A "virus" is one quite specific way for a system to become infected, which is rare/difficult on Linux. It's not a synonym for malware in general. There are other ways for a system to become harmed which can happen quite easily.

For example, a few years ago, there were some theme packages uploaded to a popular website. The uploader had tampered with the postinstall script (I think it was) to include a command to wipe the entire system. Which is what happened to one or two unfortunate people. So, yes, it can happen.

Personally, I feel that the "no PPAs" rule is too rigid. It's a matter of judgment. I will install some PPAs and not others. For example, if the PPA is managed by the developer (e.g. on Launchpad), then I tend not to worry. But I won't blindly install just any PPA.

---

### Post by joonwo on 2014-10-11
> **Irihapeti said:**
> Part of the "always secure" thing is semantics. A "virus" is one quite specific way for a system to become infected, which is rare/difficult on Linux. It's not a synonym for malware in general. There are other ways for a system to become harmed which can happen quite easily.

For example, a few years ago, there were some theme packages uploaded to a popular website. The uploader had tampered with the postinstall script (I think it was) to include a command to wipe the entire system. Which is what happened to one or two unfortunate people. So, yes, it can happen.

Personally, I feel that the "no PPAs" rule is too rigid. It's a matter of judgment. I will install some PPAs and not others. For example, if the PPA is managed by the developer (e.g. on Launchpad), then I tend not to worry. But I won't blindly install just any PPA.

hey thanks for replying.
I installed  a theme blindly without knowing anything about linux (on my second day of use). i installed a theme from noobslab.com i believe that's a popular site for linux. Are you referring to this "popular website" ??
the theme is called macbuntu and it's nice, but is it safe ? could you have a look pls. thanks.
[http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html](http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html)

---

### Post by deadflowr on 2014-10-11
Noobslab is pretty reputable.
But if you want to know more, they do have a launchpad page.
[https://launchpad.net/~noobslab](https://launchpad.net/~noobslab)
You can dig deeper there, usually with the ppa page you can get even more info per package.

---

### Post by Irihapeti on 2014-10-11
No, it was a different website.

Having had a look at the Mac theme site, I think it's going to be above my pay grade to check out the theme. However, it's been around for a few months now, and other people have used it. If something was badly wrong, I think you'd have heard about it by now. (I recall it was a matter of hours - or even minutes - before users started yelling about the other package.)

If you want to be really safe, back up everything first, and make sure that any other drives, such as external drives or cloud drives, are unmounted. Then if anything goes wrong, it's possible to go back to how things were. It's a trick that's saved me many times - not from malware but my own mistakes. :)

---

### Post by grahammechanical on 2014-10-11
I takes a long time for a developers to get their software into the Ubuntu Software Centre and that is because the code is audited before it is allowed into the software centre catalogue. In fact there is a backlog of applications needing approval.

Things are being done differently in Ubuntu for phones and tablets. Developers have to list all the permissions that their software needs. That list is used to create a profile for that application which is used by something called AppArmor to prevent that application from doing anything it should not do. Also applications are run in a sandbox and are not allowed to access information that other applications have access to. A lot of the security features in Ubuntu for phones and tablets are coming to Ubuntu desktop over the next year or so.

Regards.

---

### Post by buzzingrobot on 2014-10-11
> **grahammechanical said:**
> 

Things are being done differently in Ubuntu for phones and tablets. Developers have to list all the permissions that their software needs. That list is used to create a profile for that application which is used by something called AppArmor to prevent that application from doing anything it should not do. Also applications are run in a sandbox and are not allowed to access information that other applications have access to. A lot of the security features in Ubuntu for phones and tablets are coming to Ubuntu desktop over the next year or so.


That counts as a Very Good Thing. Some folks will surely moan about needing to follow Canonical standards before Canonical will host and distribute their software, but c'est la vie.

---

### Post by buzzingrobot on 2014-10-11
> **joonwo said:**
> hey thanks for replying.
I installed  a theme blindly without knowing anything about linux (on my second day of use). i installed a theme from noobslab.com i believe that's a popular site for linux. Are you referring to this "popular website" ??
the theme is called macbuntu and it's nice, but is it safe ? could you have a look pls. thanks.
[http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html](http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html)


One way to avoid a bit of risk is to avoid rushing to install something new as soon as it's been released.  Let other people be the guinea pigs.  If there's a problem, there's a good chance someone will post about it, here or elsewhere. And, file bug reports, we hope.

It's smart to check out the Launchpad page of a PPA that's new to you before installing it or any of its packages. (Searching for "Launchpad" and the name of the PPA should get you the URL pretty quickly. You can also search at the entry page at launchpad.net.)  Some PPA's host cutting edge packages that may or may not be troublefree on your system. (And websites very often hype these PPA's without mentioning that.) A responsible PPA will be forthright about things like that.  

Be aware that if/when, in the future, you try to do an in-place upgrade of Ubuntu from one version to the next (e.g., from 14.04 to 14.10, *not* routine updates) it's wise to back out PPA's and their software. (You can install a package called 'ppa-puge' to do that.  It's a command line program, but it's simple so long as you get the name of the PPA right.) Upgrades are not examples of artificial intelligence. They make assumptions about what they're going to find.  The more a system has been altered beyond its baseline, the greater the possibility the upgrade process will have problems.

(Linux software is mature enough that, unless you are experiencing specific problems you know are addressed by a PPA package newer than the versions of that package in the Ubuntu repos, there's likely to be little or no payoff in installing shiny new PPA packges to replace slightly older official versions.)

I agree that a flat 'No PPA's!' policy isn't necessary. On the other hand, I'm only using two at the moment.

---

### Post by vasa1 on 2014-10-11
> **joonwo said:**
> thanks for replying. i was just so fascinated by the fact that people always say linux is absolutely secure. Already watched dozen of youtube videos from linux experts and all claim that it's impossible to get a virus. 
Just didn't understand how it could be impossible. So thanks to you guys i learned it's definitely possible (but not likely) and that the user is the "weakest link".
Always be suspicious. No harm in questioning everything. Salespersons (and fanboys and partisan bloggers) tend to gloss over negatives.

Apart from "foreign" software, be suspicious of scripts or commands you don't understand. No harm in asking first.

Think more than twice about changing defaults even in the cause of "optimizing". Just because someone has a blog or post or whatever titled "Top ten things to do after installing *buntu xx.yy" doesn't mean it's mandatory (or safe).

Stay with "official" sources. There are many "linux" sites offering tips, magical beans, whatever, but it's not often that there's something unique there.

Also, be careful of "ancient" sources. What was applicable then may not be applicable now.

---

### Post by Rob Sayer on 2014-10-12
> **joonwo said:**
> ... people always say linux is absolutely secure.

There's no such thing as absolute security, though linux is best.  The worst thing you can do is use an OS or app thinking it'll make you absolutely safe.  The only absolutely safe way is to never ever connect to the net.

> Already watched dozen of youtube videos from linux experts and all claim that it's impossible to get a virus.

Experts?  Youtube?  Give me a break.  It's not impossible to get a virus.  But it's quite hard for them to spread because in linux, unlike windows, the permission levels actually work.  So there aren't any known linux viruses out there.  

But you can still get hacked, and using untrusted ppa's is an good way to do it.  I always advise noobs to avoid them for that reason.

BTW I never watch those youtube videos ... there are good ones but it's not worth the effort for me to find them.  I don't read many blogs either.  There is a lot of bad linux advice out there.  I go here or to askubuntu first.  Actually I've used the archlinux docs a lot too.

---

### Post by buzzingrobot on 2014-10-12
Unix/Linux has the concept of file ownership (related to, but not the same thing as permissions) because Unix was created as a multiuser OS: Multiple users can be logged on to a single system simultaneously.  File ownership keeps one user from interfering with files that belong to another user, and helps the OS keep the active processes sorted out.  It's also why there is a single 'root' user: One user with rights across the system, because ordinary users should not have rights to alter files/directories they don't own. And, it's why there is a /home directory that contains folder names that match our usernames, i.e., /home/MyUserName, rather than just something like /MyUserName. Every user with an account on a Unix/Linux machine gets their own folder in /home.

This multiuser capability is rarely used these days, but it's in there.

---

### Post by sotiris2 on 2014-10-12
> **Irihapeti said:**
> Part of the "always secure" thing is semantics. A "virus" is one quite specific way for a system to become infected, which is rare/difficult on Linux. It's not a synonym for malware in general. There are other ways for a system to become harmed which can happen quite easily.

For example, a few years ago, there were some theme packages uploaded to a popular website. The uploader had tampered with the postinstall script (I think it was) to include a command to wipe the entire system. Which is what happened to one or two unfortunate people. So, yes, it can happen.

Personally, I feel that the "no PPAs" rule is too rigid. It's a matter of judgment. I will install some PPAs and not others. For example, if the PPA is managed by the developer (e.g. on Launchpad), then I tend not to worry. But I won't blindly install just any PPA.

Was this post-install script run manually by the user (with root permissions) or automatically by the package manager? I ask because I always thought that one of the reason for a package manager versus self-executing installers was that even though it does follow 'instructions' from the package, it can refuse to do things such as for example removing the whole root directory or overwriting another package's file. Also the package manager keeps a log of what it did so it can completely remove any files that were installed (while a self-installing program could omit some files it wants hidden). But if also runs arbitary scripts provided by the package then that can't hold true.

---

### Post by Irihapeti on 2014-10-12
Many deb packages have pre/post-install scripts to perform setup and configuration tasks. They are run automatically as part of the installation process, so once you've entered the password to allow the package to install, the scripts can do anything.

In this case, the malicious uploader had edited one of the scripts to include a command that would remove everything from the drive. So, once the user had issued the password to install, the script did its dastardly deed.

It's actually not hard to look at the scripts in a deb package with an ordinary unarchiving tool or a package such as gdebi, if you're concerned about such things. I managed to get hold of a copy of one of these maliciously-altered packages and had it on an encrypted partition for a while - purely out of morbid curiosity, or perhaps as an Exhibit A in case I came across one of those "Linux is totally secure" people in real life. I do remember showing it to my son, who used Ubuntu for a couple of years.

---

