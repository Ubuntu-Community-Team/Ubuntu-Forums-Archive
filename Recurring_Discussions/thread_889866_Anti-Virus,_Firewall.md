---
title: "Anti-Virus, Firewall?"
date: 2008-08-14
forum: Recurring Discussions
---

### Post by Exile666 on 2008-08-14
After permanently switching over to Ubuntu, I've been stressing out over the fact of my laptop getting a virus. I've read that Ubuntu, or any Linux distro, don't need Anti-Virus' at all. Maybe so. But I'm also stressing over whether or not it's safe to do some online shopping, I know it's never completely safe. Can anyone help me on what to do? A little information to ease my stress.

---

### Post by Nepherte on 2008-08-14
This pretty much covers it all: [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by jerome1232 on 2008-08-14
There are no known viruses for Linux, anti-virus programs in linux just scan for windows viruses, for those how are conscience of transferring infected files and damaging windows computers. So using an anti-virus scanner in linux will not make the box any more sercure

By default Ubuntu comes with no services listening for connections, so a firewall does absolutely nothing for making the box more secure. Firewalls are more for if you have services installed (file sharing and such) then you can filter which addresses can use those services etc.

As for the security of shopping online is more dependent on the website you use. They should use point-to-point encryption when making the actual transfer, if they keep records stored on the machines they should be encrypted/secured in some fashion. Basically only make transactions with trusted/known to be secure websites.

---

### Post by sayakb on 2008-08-14
Articles on Ubuntu security:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

And the recurring discussion: [http://ubuntuforums.org/showthread.php?t=817898&highlight=antivirus](http://ubuntuforums.org/showthread.php?t=817898&highlight=antivirus)

This thread belongs to recurring discussions.

---

### Post by theyranos on 2008-08-14
The most common attacks with regard to online shopping are what's called a "Phishing" attack, in which someone pretends to be amazon.com or your bank and tricks you into getting information. Linux can't protect you from those, but it will protect you from just about everything else that Windows people suffer from--viruses, malicious activex controls, spyware, etc.

As long as you're using Firefox, and as long as you personally entered in the URL you started from to the address bar or got it from Google (as opposed to an e-mail message), you're probably alright as long as your machine isn't compromised. The fact that this is even a concern for you makes you infinitely safer than most computer users.

The one thing linux users have to worry about is some idiot kid with a script gaining access to your machine. This has happened to me twice, but only because I made the same stupid mistake each time. Ubuntu's default settings are relatively safe, but if you'd like to make them a little safer, open up Synaptic and look for a package called **Firestarter**. Firestarter is an extremely easy-to-use configuration program that controls the firewall built in to Linux.

Just like with windows, you should try to keep your system up to date as well. When you get that little "software updates are available" notification in your system tray, click on it and let it do its thing. In my experience, Ubuntu's software updates are orders of magnitude less disruptive than Windows's, and that way you'll benefit from the devs out there who tirelessly find and fix security bugs.

And, whether you're on Windows or Linux, one of the best things you can do for yourself is to have a good, secure password. If you search around, there are a bunch of guides online for making up difficult-to-guess passwords.

All that in mind, I can say with absolute certainty (and I'm sure many others will chime in with something to the same effect) that your machine is more secure now than it was with Windows installed, regardless of what extra stuff (Windows Defender, antivirus, etc) you had bogging your system down.

Hopefully that eases the stress a little :)

---

### Post by Oldsoldier2003 on 2008-08-14
Moved to recurring discussions

---

### Post by sayakb on 2008-08-14
> **Oldsoldier2003 said:**
> Moved to recurring discussions
Thank you.

---

### Post by Exile666 on 2008-08-14
Thanks guys/gals, I wasn't expecting this much help.

0% stress now... kinda

---

### Post by Twitch6000 on 2008-08-14
> **jerome1232 said:**
> There are no known viruses for Linux, 


I swear you Linux Zealots/Lovers are quite stuck up aren't you?

Anyways YES THERE ARE VIRUSES FOR LINUX.

Here is one very well known one,Bliss.
Details [http://math-www.uni-paderborn.de/~axel/bliss/](http://math-www.uni-paderborn.de/~axel/bliss/)
[http://en.wikipedia.org/wiki/Bliss_(virus)](http://en.wikipedia.org/wiki/Bliss_(virus)).

Then there has also been a report of over hundred viruses in **2003** for Linux.
Details-[http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

So please do not give false information.

Now on the good side these viruses cannot infect you unless you install them under **root**.Plus most of them are aimed at the program wine meaning targeting any .exe program.

---

### Post by jerome1232 on 2008-08-14
> Quick summary: if you run bliss (which is, by the way, not specific to Linux and can be compiled for SunOS, Solaris, and OpenBSD) or any binary infected with bliss, it tries to attach itself to (i.e.: infect) all binaries that you have write access to

You shouldn't have write access to Executables so I fail to see the significance.

> When executed, it attempts to attach itself to Linux executable files, to which regular users do not have access. In the case of the alpha version, this prevents the executables from running, so users notice it immediately. Although it was probably intended to prove that Linux can be infected, it does not propagate very effectively because of the structure of Linux's user privilege system. The Bliss virus never became widespread, and remains chiefly a research curiosity.

I guess I should have added in the wild as well, there are proof of concept ones grown in "labs"

Any viruses "aimed at wine" are in fact windows viruses, the nature of wine makes it able to run some windows viruses, of course you have to manually tell wine to do run them and deleting your ~/.wine directory will be rid of them.

---

### Post by lukjad on 2008-08-14
First of all, read this:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

These are the two main questions you seem to have:

Are there and Anti-Viruses for Linux?
Are there any viruses for Linux?

For the first one, Yes.

For the second one, yes... and no.

As my esteemed colleague, Twitch6000, said, there are SOME viruses to be found. ***However***, they are hard to get. The difference between Linux Viruses and Windows Viruses is that Windows is always running as the root user. So, anything that happens to part of the computer, happens to all of the computer. Also, with Ubuntu most of the programs you  will ever install come from authentic repositories that are checked, double checked, and triple checked to be uninfected. If you choose in install programs from repositories other than those supported by Ubuntu, you do so at your own risk. You need to check the references of the repository you are using. If some guy you see at a cracker site tells you to activate the 1337h4xr repository, be suspicious.

The same is true about installing programs. If you install GIMP 2.50 from the GIMP's Official Website ([www.gimp.org](www.gimp.org)), you are giving them a measure of trust since they are a proven entity. However, if you go to [www.SuperCoolThingy.com](www.SuperCoolThingy.com) (I invented the site name) and start installing a bunch of programs, you may have a problem. The point of using Linux is not to be blissfully ignorant, but to be informed and cautious but not constantly in danger. Unlike in Windows, you cannot just accidentally click on a link and get infected. 

Now, if you are worried about loosing data, you need to be wary of any commands given to you. This ***_[COLOR="Red"]DANGEROUS COMMAND[/COLOR]_*** below will destroy your computer if run as root:
```
rm -rf /
```
The point is that you have to be careful, but you have a better foundation upon which to defend yourself. If ever you are suspicious of a program, don't install it until you check it out. If someone you don't trust tells you a command that you don't understand, ask someone what it does. Google is your friend. Look up what chmod is. Look up what rm -rf / does. If you don't like what you see, wait. Read [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) for more on dangerous commands. 

Basically, it is possible to get a virus, if you are not careful. It is also easy to destroy the usability of your computer if you do a dangerous command. 

Below is a Youtube Video I found about what happens when you run rm -rf / as root. The point is that since Windows is always root, any program can destroy the system. In Linux, especially Ubuntu, the damage is limited.

[http://www.youtube.com/watch?v=wWOjmvWPRvQ](http://www.youtube.com/watch?v=wWOjmvWPRvQ)

---

### Post by damis648 on 2008-08-14
> **lukjad007 said:**
> First of all, read this:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

These are the two main questions you seem to have:

Are there and Anti-Viruses for Linux?
Are there any viruses for Linux?

For the first one, Yes.

For the second one, yes... and no.

As my esteemed colleague, Twitch6000, said, there are SOME viruses to be found. ***However***, they are hard to get. The difference between Linux Viruses and Windows Viruses is that Windows is always running as the root user. So, anything that happens to part of the computer, happens to all of the computer. Also, with Ubuntu most of the programs you  will ever install come from authentic repositories that are checked, double checked, and triple checked to be uninfected. If you choose in install programs from repositories other than those supported by Ubuntu, you do so at your own risk. You need to check the references of the repository you are using. If some guy you see at a cracker site tells you to activate the 1337h4xr repository, be suspicious.

The same is true about installing programs. If you install GIMP 2.50 from the GIMP's Official Website ([www.gimp.org](www.gimp.org)), you are giving them a measure of trust since they are a proven entity. However, if you go to [www.SuperCoolThingy.com](www.SuperCoolThingy.com) (I invented the site name) and start installing a bunch of programs, you may have a problem. The point of using Linux is not to be blissfully ignorant, but to be informed and cautious but not constantly in danger. Unlike in Windows, you cannot just accidentally click on a link and get infected. 

Now, if you are worried about loosing data, you need to be wary of any commands given to you. This ***_[COLOR="Red"]DANGEROUS COMMAND[/COLOR]_*** below will destroy your computer if run as root:
```
rm -rf /
```
The point is that you have to be careful, but you have a better foundation upon which to defend yourself. If ever you are suspicious of a program, don't install it until you check it out. If someone you don't trust tells you a command that you don't understand, ask someone what it does. Google is your friend. Look up what chmod is. Look up what rm -rf / does. If you don't like what you see, wait. Read [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) for more on dangerous commands. 

Basically, it is possible to get a virus, if you are not careful. It is also easy to destroy the usability of your computer if you do a dangerous command. 

Below is a Youtube Video I found about what happens when you run rm -rf / as root. The point is that since Windows is always root, any program can destroy the system. In Linux, especially Ubuntu, the damage is limited.

[http://www.youtube.com/watch?v=wWOjmvWPRvQ](http://www.youtube.com/watch?v=wWOjmvWPRvQ)

+1.

PS. I love that video. :popcorn:

---

### Post by lukjad on 2008-08-14
Me too.

---

### Post by Twitch6000 on 2008-08-15
> **lukjad007 said:**
> First of all, read this:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

These are the two main questions you seem to have:

Are there and Anti-Viruses for Linux?
Are there any viruses for Linux?

For the first one, Yes.

For the second one, yes... and no.

As my esteemed colleague, Twitch6000, said, there are SOME viruses to be found. ***However***, they are hard to get. The difference between Linux Viruses and Windows Viruses is that Windows is always running as the root user. So, anything that happens to part of the computer, happens to all of the computer. Also, with Ubuntu most of the programs you  will ever install come from authentic repositories that are checked, double checked, and triple checked to be uninfected. If you choose in install programs from repositories other than those supported by Ubuntu, you do so at your own risk. You need to check the references of the repository you are using. If some guy you see at a cracker site tells you to activate the 1337h4xr repository, be suspicious.

The same is true about installing programs. If you install GIMP 2.50 from the GIMP's Official Website ([www.gimp.org](www.gimp.org)), you are giving them a measure of trust since they are a proven entity. However, if you go to [www.SuperCoolThingy.com](www.SuperCoolThingy.com) (I invented the site name) and start installing a bunch of programs, you may have a problem. The point of using Linux is not to be blissfully ignorant, but to be informed and cautious but not constantly in danger. Unlike in Windows, you cannot just accidentally click on a link and get infected. 

Now, if you are worried about loosing data, you need to be wary of any commands given to you. This ***_[COLOR="Red"]DANGEROUS COMMAND[/COLOR]_*** below will destroy your computer if run as root:
```
rm -rf /
```
The point is that you have to be careful, but you have a better foundation upon which to defend yourself. If ever you are suspicious of a program, don't install it until you check it out. If someone you don't trust tells you a command that you don't understand, ask someone what it does. Google is your friend. Look up what chmod is. Look up what rm -rf / does. If you don't like what you see, wait. Read [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) for more on dangerous commands. 

Basically, it is possible to get a virus, if you are not careful. It is also easy to destroy the usability of your computer if you do a dangerous command. 

Below is a Youtube Video I found about what happens when you run rm -rf / as root. The point is that since Windows is always root, any program can destroy the system. In Linux, especially Ubuntu, the damage is limited.

[http://www.youtube.com/watch?v=wWOjmvWPRvQ](http://www.youtube.com/watch?v=wWOjmvWPRvQ)

I vote for this to be posted as a guide or something lol.
Anyways great explanation :).

---

### Post by lukjad on 2008-08-16
Thanks. ;)

---

