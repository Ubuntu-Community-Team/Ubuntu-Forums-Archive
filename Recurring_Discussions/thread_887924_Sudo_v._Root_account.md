---
title: "Sudo v. Root account"
date: 2008-07-17
forum: Recurring Discussions
---

### Post by Morpheun on 2008-07-17
> **snowpine said:**
> Hi there, you don't need to (and in fact, shouldn't) enter a root password, ever! Just preface whatever command needs superuser rights with 'sudo'.

Hope that helps.

Now thats just wrong. Why wouldn't you add a root password? Adding a root password and then removing sudo rights from everyone on a multiuser computer is often a good idea. If it was a single user computer then a root password might be unnecessary.

---

### Post by snowpine on 2008-07-17
> **Morpheun said:**
> Now thats just wrong. Why wouldn't you add a root password? Adding a root password and then removing sudo rights from everyone on a multiuser computer is often a good idea. If it was a single user computer then a root password might be unnecessary.

Hi Morpheun, read the link from Sef for more details, but in a nutshell, lack of a root password (and use of sudo instead) is one of the defining security features of Ubuntu (which sets it apart from many other flavors of Linux).

If it is a multiuser computer, you can easily set up individual users as sudo'ers, or not.

---

### Post by Morpheun on 2008-07-17
> **snowpine said:**
> Hi Morpheun, read the link from Sef for more details, but in a nutshell, lack of a root password (and use of sudo instead) is one of the defining security features of Ubuntu (as opposed to many other flavors of Linux).

If it is a multiuser computer, you can easily set up individual users as sudo'ers, or not.

That is the default setting yes. But ubuntu still is linux, and still is all about customization. Telling someone that they should NEVER make a technically viable choice, without explaining why, sounds like a bad piece of advice to me. I personally have a seperate root password so I can login as root and because I'm used to it that way (coming off Arch)

---

### Post by Inxsible on 2008-07-17
> **Morpheun said:**
> Now thats just wrong. Why wouldn't you add a root password? Adding a root password and then removing sudo rights from everyone on a multiuser computer is often a good idea. If it was a single user computer then a root password might be unnecessary.

> **snowpine said:**
> Hi Morpheun, read the link from Sef for more details, but in a nutshell, lack of a root password (and use of sudo instead) is one of the defining security features of Ubuntu (as opposed to many other flavors of Linux).

If it is a multiuser computer, you can easily set up individual users as sudo'ers, or not.IMO, it varies from person to person.

Since I started using Debian and Arch - which by default have a different password for root, I have become accustomed to it and I kinda like it. I do not even install sudo. Just become root and then do my work for system upgrades....

For everything else I know for sure that I cannot screw up anything except my home drive.

Having said that, you need to be careful in what you do no matter which option you choose....because as root you can muck with anything and you can with sudo as well.

So understanding what you are doing is more important than blindly copy pasting commands.

---

### Post by snowpine on 2008-07-17
> **Morpheun said:**
> That is the default setting yes. But ubuntu still is linux, and still is all about customization. Telling someone that they should NEVER make a technically viable choice, without explaining why, sounds like a bad piece of advice to me. I personally have a seperate root password so I can login as root and because I'm used to it that way (coming off Arch)

Hi Morpheun, you make a good point, and I'm sorry if I came off as a bit of a dictator. :) I can definitely see why you think that, coming from a different distro--I learned on Ubuntu, so that way of thinking is ingrained in my psyche.

Perhaps a better way of rephrasing my point is that logging in to ubuntu as root, while possible, is not "officially" supported, and the OP might have trouble learning how to do it on this particular forum (unless someone pm's him/her :)). Fair enough?

---

### Post by ilrudie on 2008-07-17
The real issue as I see it here is that if you need to ask for help in the forums then enabling root is not a good idea.  Other forum users will assume that you don't have root enabled and do have sudo configured properly.  If you know how to enable root and want to its your choice but if you have to ask how to enable root you should just stick with the default (sudo).

---

### Post by protogenesis on 2008-07-17
Root is, by definition, the default master account on any POSIX-compliant system.  As a result, every cracker out there knows this and will attempt to brute-force their way into any box using a password guessing game with root as the user ID they choose.  When I set up my Ubuntu server three weeks ago, within 24 hours I had my first 'visitor' who spent about 2 - 3 hours trying to brute-force my system with a root/password combo.

Good thing for me I keep the root account deactivated!

I'm an old-school UNIX pern, so I like having a real password on my root account.  However, since the server's admin, at this time, is only me, no reason exists.  For that matter, even when I add two more admins, they won't need root password either as they'll just be able to use sudo.  

Now, sudo comes with a small problem in that if a cracker knows the user ID of someone who is authorized in /etc/sudoers (the file that lets sudo know who is authorized to do what), the cracker will then be able to try to brute-force using the user ID/password combo versus root/password combo.  However, I think this problem is much smaller in scale than having a million root-activated boxes out there on the 'net, ready to be attacked by anyone with some time on their hands.  It's harder to guess a user ID of 'zimongo' than it is to assume, rightfully so, root is a valid user ID.

Now, security issues aside, I think the best reason to not ever enable root with a password is the plain and simple fact that so many people will use root as their main account.  root was never meant to be your workhorse account.  Using root to access X or the likes is just, well, bad.  Since you're root, you have complete filesystem control.  How many bad things do you think happen as a result of being root because someone was careless, sloppy or unsure?  Creating a main user account and using sudo cuts way down on accidents.  

I suggest you create a root environment, that is, home directory, login shell, appropriate .bashrc/.tcshrc/.login for your root account so when you 'sudo su - ' you are able to see quite plainly that you are root.  On my system, my prompts look like this:

(As a regular user):   systemname:working directory > 
(As root)          :   ROOT:working directory:ROOT #

Since years of UNIX are banged into my head, seeing # means I'm root.  Seeing ROOT twice on the same prompt reinforces the fact that I'm root.

Hope that this and other answers have helped!

---

### Post by bodhi.zazen on 2008-07-17
> **Morpheun said:**
> That is the default setting yes. But ubuntu still is linux, and still is all about customization. Telling someone that they should NEVER make a technically viable choice, without explaining why, sounds like a bad piece of advice to me. I personally have a seperate root password so I can login as root and because I'm used to it that way (coming off Arch)

Well, NEVER being open to change could be considered bad as well. Ripping out sudo and setting a root password might seem a little stubborn, no ?

I understand sudo is new to you, but why not give it a chance and learn something new ? I also came from the su school, but now appreciate sudo ... There is no reason for you to come in here and make demands of this community.

The reasons for sudo are numerous and sudo is much, much more flexible then su. su is all or none. sudo can be configured to allow users or groups limited or full root access. 

See : [http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html](http://www.onlamp.com/pub/a/bsd/2002/08/29/Big_Scary_Daemons.html)

[http://www.softpanorama.org/Access_control/sudo.shtml](http://www.softpanorama.org/Access_control/sudo.shtml)

Since you are from arch, you may appreciate some references as well :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

If you need a root shell use sudo ;

```
sudo -i
```

If you want to use a graphical application use gksu :

```
gksu nautilus
```

gksu gives much more sane and secure root access to X then su or running gnome as root.

On these forums we support sudo, not su. 

[New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 

Now there are some occasions when a root password is needed, and that is fine.

If you do not like sudo,  no none is stopping you from setting a root password and disabling sudo, it is not really that big a deal.

If you stop your ranting for a minute you might learn something, and you never know, you may actually like sudo :twisted:

---

### Post by cariboo on 2008-07-17
I have an old computer with a 8 year old debian installation on it. I use it for an mp3 player so I never have to do anything with it. I decided I would finally upgrade it the other day and found myself trying to use sudo everytime I needed to change something, I forgot that I had a root account on the computer. I now find it quite a pain to use the root account first you have su and enter a password then you have to log out to become a regular user agian. I find sudo works better for the way I use  the system.

Jim

---

### Post by clarknova on 2008-07-21
Some programs don't work with sudo in my experience:

1. CUPS
2. ltsp thin client environment.

Although I prefer sudo, I had to make a root account password to work with both of these.

Anyway, Paradoxfox93 evidently already knows how to use sudo. He/she was asking about expired accounts. I don't know why your account would expire unless you set it up to expire.

chage and passwd should both be able to fix that. Check the man pages for specifics, although if it's preventing you from using sudo then you may have to boot ubuntu into recovery mode and update your passwords.

db

---

### Post by t0p on 2008-07-21
> **bodhi.zazen said:**
> 
If you do not like sudo,  no none is stopping you from setting a root password and disabling sudo, it is not really that big a deal.

If you stop your ranting for a minute you might learn something, and you never know, you may actually like sudo :twisted:

I didn't detect any ranting.  In fact, I found it a refreshing change to read a thread where the pros and cons of root vs sudo were honestly and openly debated.

Now, I haven't bothered to enable root login on my box.  Ubuntu's default use of sudo suits me fine.

But I would never presume to declare that what suits me is a perfect fit for everyone.  One of Linux's great strengths is its eminent customisability.

It's interesting to note that no one addressed the OP's issue about the "su account expiring".  Instead, as is usual in these cases, people just wanted to tell him he should use sudo not root.

---

### Post by clarknova on 2008-07-26
> **t0p said:**
> 
It's interesting to note that no one addressed the OP's issue about the "su account expiring".  Instead, as is usual in these cases, people just wanted to tell him he should use sudo not root.

What am I, chopped liver? I repeat: passwd and chage should both be useful in dealing with expired passwords. I'm not experienced with these so I can't copy any useful code at the moment, but it can be done.

If there is no administrator account on the machine (with a password that is not expired) then he may need to boot into recovery mode to get a root console and do the required work.

Oh, and just kidding about the chopped liver ;)

db

---

