---
title: "Is Ubuntu really immune to a virus?"
date: 2010-01-08
forum: Recurring Discussions
---

### Post by garyed on 2010-01-08
I've been thinking about this lately since two friends of mine have been having virus problems & of course are running Windows. Are we really that secure or is it just the mean virus writers don't want to bother with us since we are so relatively few?  What's to stop a virus from reading our password after sudo is entered & then doing the nasty on our machines.
I only know some programming basics so security is way over my head but I would think that an Ubuntu virus is not that far fetched since it is gaining popularity. I'm curious as to what others might think of my concerns.

---

### Post by NoaHall on 2010-01-08
The system is more secure. While it is possible to get a virus, as long as you don't knowingly install some rubbish from a dubious website, and make sure you don't run applications like Firefox from root, there's no problem. The files in your /home/ aren't so secure, as the files here can be hacked without being run as root. However, in general, the core system is much stronger. We have encountered two pieces of malware before, in the wild, both by the same writer, and do you know how long it took for us to make a cure? About 20 minutes, during which time a "system guard" type system against it was made by a user here on the forums, while I and others put together the commands to fix it.

---

### Post by Marlonsm on 2010-01-08
Windows viruses can do no harm to Ubuntu itself, although they might mess up with Wine (the program to run Windows applications in Ubuntu).

Virus, by definition is a malware that can spread by itself, using things like emails, websites and pen-drives. These do not exist, they would need to be run by the user and get the root password to do harm.

But there are some proof-of-concepts out there that can get the root password without your permission, you just need to run them and when you type the password elsewhere they will get it.

There can also be Trojan horses, there was one recently in a theme site. You downloaded a file, that was supposedly a theme, and when it was run, it warned you that you could have been infected.


But all those "threats" can be easily avoided, just like people do in Windows, by not running programs from untrusted sources. And they are in a very small number, also.

---

### Post by amauk on 2010-01-08
[http://ubuntuforums.org/showthread.php?p=8424962#post8424962](http://ubuntuforums.org/showthread.php?p=8424962#post8424962)

---

### Post by spiderbatdad on 2010-01-08
I would agree Linux is generally safe from DOS types of viruses or those that might run unwanted services in the background, but your talking about file access. I think you are only as safe as the software you install. If you carelessly download packages from untrusted or un-verified sources, you have little way of knowing what you are introducing to your system. My personal feeling is that the information people store on and transmit from their computers is far less private than they think it is.

---

### Post by bodhi.zazen on 2010-01-08
Because Windows makes things "easy" at the expense of "security". With a Windows installation there are both documented and undocumented servers and then there are bugs.

Every "virus" or "worm" takes advantage of a security hole. Microsoft does not patch known security flaws in a timely manor (known flaws have gone unpatched for years or decades), thus you need to rely on 3rd party applications to remove malware AFTER you have been infected (virus and spy ware scanners).

Add to that that nothing is "free" with Windows, thus many people are downloading and installing trial versions of products or worse pirated copies == social engineering rich environment.

Linux is built from the ground up to be both multiuser and secure. Bugs / security flaws are patched in a timely manor, often within 24 hours or less. Thus we are not vulnerable to known bugs (as a general rule, there are always exceptions) and we do not need 3rd party applications to fix a problem after the fact.

See also : 

[Evil malware](http://www.gnu.org/fun/jokes/evilmalware.html)

[The short life and hard times of a Linux virus](http://librenix.com/?inode=21)


If you are interested in the topic, start here:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

and keep reading as much as you like.

If you have a specific question, feel free to ask.

Otherwise I am moving this thread to "recurring discussions".

---

### Post by bodhi.zazen on 2010-01-08
> **spiderbatdad said:**
> I think you are only as safe as the software you install.

I am not trying to be harsh, but, software you install is not a virus.

Most Window susers are used to considering any and every problem they have as due to a "virus". It is helpful, however, if you use proper terminology when discussing malware.

[http://www.cisco.com/web/about/security/intelligence/virus-worm-diffs.html](http://www.cisco.com/web/about/security/intelligence/virus-worm-diffs.html)

---

### Post by Grifulkin on 2010-01-08
Secure != No Virus.

---

### Post by argos3016 on 2010-01-08
Ehem...
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by NoaHall on 2010-01-08
> **argos3016 said:**
> Ehem...
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

That's not a virus or malware.

---

### Post by garyed on 2010-01-08
Since going over to Ubuntu I've become complacent about viruses & I assume a lot of other users have also. I thought about the possibility of a nasty virus writer using that to their advantage. I guess even though Ubuntu is a very secure OS the best anti-virus is common sense & caution.

---

### Post by leveled on 2010-01-08
;) At this current time there is no active virus on Linux, and has been that way for a long time.

---

### Post by spiderbatdad on 2010-01-09
> **bodhi.zazen said:**
> I am not trying to be harsh, but, software you install is not a virus.

Most Window susers are used to considering any and every problem they have as due to a "virus". It is helpful, however, if you use proper terminology when discussing malware.

[http://www.cisco.com/web/about/security/intelligence/virus-worm-diffs.html](http://www.cisco.com/web/about/security/intelligence/virus-worm-diffs.html)

Of course, no offence is taken. That article says viruses are a type of malware and can be bundled in programs the user installs...so I'm not sure of the point, unless it is that in my post I was referring to what would actually be termed a "backdoor," not a virus. Thanks for suggesting the use of proper terminology. You are right it is easy to fall into the lazy way of calling everything a virus, especially for those of us who are not heavily IT oriented.

---

### Post by Frak on 2010-01-09
You are not immune to viruses regardless of the OS you choose. To say that Linux is immune is just as erroneous as to say Windows will get a virus no matter what you do. The only thing you can do is be a savvy computer user and watch what you do.

---

### Post by del_diablo on 2010-01-09
> **Frak said:**
> To say that Linux is immune is just as erroneous as to say Windows will get a virus no matter what you do.

This is reality for a standard computer user anyhow. Windows = Viruses and trouble. Anything else(as in OS X, Linux, similar): No viruses.

---

### Post by Frak on 2010-01-09
> **del_diablo said:**
> This is reality for a standard computer user anyhow. Windows = Viruses and trouble. Anything else(as in OS X, Linux, similar): No viruses.
Let's take all the users from Windows, plant them into a completely Linux-only environment. Linux would be virus rampant. Those who want to will find a way, and no amount of eyes will stop them before hand.

---

### Post by derekeverett on 2010-01-09
In terms of functioning properly, or even functioning at all, there is already lots of things that are quite hit and miss with Linux. We don't need malware and such to get frustrated and angry at our computers. 

:D

---

### Post by marco123 on 2010-01-09
> **Frak said:**
> Let's take all the users from Windows, plant them into a completely Linux-only environment. Linux would be virus rampant. Those who want to will find a way, and no amount of eyes will stop them before hand.

Got to agree with that!  - They'd be running as root, and installing every piece of software they could find on the internet, within 2 hours! :lol:

---

### Post by Frak on 2010-01-09
> **marco123 said:**
> Got to agree with that!  - They'd be running as root, and installing every piece of software they could find on the internet, within 2 hours! :lol:
That's pretty close to the truth.

---

### Post by argos3016 on 2010-01-11
> **NoaHall said:**
> That's not a virus or malware.

You are right!!

---

