---
title: "Profiles, and security I think"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by thatredbird on 2013-11-25
I have just recently started messing around with Linux, and am trying to figure out the whole user profiles, and how it is recommended to set them up.  I am the only one using Lubuntu on this computer, however I keep seing information about rwx settings and the like.  It looks like I should not be using the owner profile, instead have a lesser privilaged acout set up.  Is there a wiki/suggestion on how to read up and set up things so that I am doing things the righter way?

thanks

redbird.

---

### Post by DuckHook on 2013-11-25
Start with this:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Owlcroft is old and not maintained, but still covers the basics well:

[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)

Last, but far from least, this:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)

---

### Post by texaswriter on 2013-11-25
> **thatredbird said:**
> I have just recently started messing around with Linux, and am trying to figure out the whole user profiles, and how it is recommended to set them up.  I am the only one using Lubuntu on this computer, however I keep seing information about rwx settings and the like.  It looks like I should not be using the owner profile, instead have a lesser privilaged acout set up.  Is there a wiki/suggestion on how to read up and set up things so that I am doing things the righter way?

thanks

redbird.

The default file ownership is fine for all default Ubuntu installations (I have tried Kubuntu/Lubuntu/Xubuntu/Ubuntu). You should not change this default setting unless there is a specific and actionable reason. 

Although it can't hurt to learn more about file permissions.

---

### Post by thatredbird on 2013-11-25
Thankyou DuckHook, I am attempting to very slowly catch up. It would appear that the wealth of information is out there and this helps my understanding it.
Thankyou texaswriter, I think that was what I needed to hear,  My main concern was that I was using the owner profile and it sounds as though that is ok as long as I dont fiddle with root, and the like.

I still intend to get through all of the information, but its a reasurance at least.

---

### Post by DuckHook on 2013-11-26
> **thatredbird said:**
> My main concern was that I was using the owner profile and it sounds as though that is ok as long as I dont fiddle with root...Ubuntu's default install does the following:

1. It disables the actual root account. This is good. Leave it disabled. Never enable it unless you become a power user and know exactly what you are doing and why you are doing it.
2. It sets you up as a "regular" user but adds you to the *sudo* group. This allows you to temporarily *elevate* to root privileges on a single command basis only when you prepend "sudo" to the desired command.
3. If you want to be really secure, you can create yet another user *without* sudo privileges (by not adding it to the *sudo* group) so that it is completely incapable to elevating to root, even temporarily, and then stick with that user account for most of your day-to-day tasks. Most of us would consider this overkill, but no one would fault you for wanting to be extra safe.

For a short and dirty security primer, you may be interested in [this]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") thread posted a few weeks ago. I'm afraid that I went on a bit of a rant, but if you ignore the tone, you might find the info therein useful. And if that doesn't bury you, then this:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by texaswriter on 2013-11-26
> **DuckHook said:**
> 
3. If you want to be really secure, you can create yet another user *without* sudo privileges (by not adding it to the *sudo* group) so that it is completely incapable to elevating to root, even temporarily, and then stick with that user account for most of your day-to-day tasks.

Yeah, this isn't a bad idea, but it would make alot of things very unintuitive for somebody new to Linux. Also, alot of people who might try to help you by giving you commands would have more difficulty in helping you because commands that required the "sudo" command would not work on that user. You could keep that in mind though for having an additional account for *other* people who might use the computer, though isn't there still a guest account enabled by default in Ubuntu?

---

### Post by thatredbird on 2013-11-26
Truth be told, I am a low level user at best, most of what I do is fairly basic.  I have been trying to figure out terminal commands and vi,  it sounds like it would be hard to mess things up as long as I use my brains and research anything that looks fishy.

---

