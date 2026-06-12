---
title: "Why not login as root?"
date: 2008-06-27
forum: Recurring Discussions
---

### Post by kenbb99 on 2008-06-27
Why do I keep reading that I shouldn't log in as root?  So far as I can tell, the reasons, and my thoughts on them, are as follows:

1)  "You can wreck your install by mistake."
I can wreck my install by mistake without logging in as root.  I've done it.  I didn't even have to type a password to do it.  To do a lot of basic tasks I have to sudo or sudo su which, so far as I can tell, sets me up to wreck my system in the same way as logging in as root.

2)  "It's insecure."
No one else uses my system.  It's in my home office.  No one comes in here.  (Now if I vacuumed once in a while ...)

3)  "The outside world can run scripts and viruses that will wreck your install."
I have a hardware firewall.  I read in a forum somewhere that Ubuntu does not have a software firewall or virus scanner because Linux is inherently secure.  I think you could make almost any operating system secure by including a software firewall and a virus scanner, putting them behind a hardware firewall and asking users to type in passwords all the time.

4)  "This protects you from yourself."
This sounds very paternalistic.  I don't want to be protected from myself.  Not letting me drink beer would also protect me from myself but I like to have one now and then.  I've read that one of the strong features of Linux is that it is configurable.  That is probably so, but it sure is like pulling my own teeth to do it.  Now if I was logged in as root all the time ...

5)  "That is the way it is designed."
Is that a bug or a feature?

I find these answers unconvincing and still want to log in as root.  All the time.  I tried to set up auto login as root but the message says that that's forbidden.  I guess that's one of those things that's not configurable.

In case it is not obvious, I am pretty new to Ubuntu.  I have spent about 50 hours setting up and configuring my system - most of it researching how to solve problems, not actually solving the problems by the way - and about 5 hours using it.  I have about another 10 hours to go, I think.  Logging in as root could possibly reduce this figure a bit and make me a lot happier with the system or increase it a lot and make me just a bit annoyed.

What am I missing?  Why not go the root route?

---

### Post by blazercist on 2008-06-27
the reason linux and ubuntu especially are "inherently secure" is because most competent users will work under a user account with limited priveleges and only use root account wen necessary.  That way wen you are doing arbitrary stuff like surfing the apps and scripts etc that get run dont all have root permissions.  You are most likely coming in from a winXP environment or something similar where u were always logged in as an Administrator and you are feeling the pain of transition and change.  One of the major reasons why windows is so insecure is because of the fact that most people always run as Admin or Power User as opposed to using the regular user accounts.  Ubuntu has root disabled by default to prevent such a behavior, sudo requires a password and allows you the flexibility to use root privileges when its necessary without the tediousness of logging in and out of the root account.

also running in the user account without root access gives you a special "heads up" basically, if you are a user and you try to change something that could possibly affect the way your system operates from example xorg.conf (video configuration file) it wont allow you.  itll tell you that you dont have the permission, this is a final line of defense for newbies and experts alike, it gives you a warning that what you are about to do may have serious consequences and you should think twice. 

Perhaps you dont mind screwing up your system and having to reinstall because you want to learn from your mistakes, but for the most part the majority of users want that extra line of protection because they dont want to have to reinstall.

---

### Post by sdennie on 2008-06-27
First, read this post: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

> **kenbb99 said:**
> 
4)  "This protects you from yourself."
This sounds very paternalistic.  I don't want to be protected from myself.  Not letting me drink beer would also protect me from myself but I like to have one now and then.  I've read that one of the strong features of Linux is that it is configurable.  That is probably so, but it sure is like pulling my own teeth to do it.  Now if I was logged in as root all the time ...


It doesn't matter how smart you are or how long you've used Unix/Linux, if you login as root all the time, you *will* at some point completely destroy your machine.  It's a matter of "when" and not "if".

---

### Post by bodhi.zazen on 2008-06-27
> **kenbb99 said:**
> Why not login as root?

For all the reasons you gave, :lolflag:

Although there are exceptions, this kind of sentiment is most often voiced by inexperienced users who do not want to be bothered to learn a new OS. They take short cuts and eventually regret it.

Even Microsoft learned this lesson (even Windows no longer auto logs you in, let alone as an administrator).

Now you are of course welcome to run your machine as you see fit, but, if you are experienced, what is the big deal of typing :

```
sudo -i
``` and entering a password ? It is not really that big a deal.

And no, you are not the only one on your computer (as long as it is connected to the internet).

With the exception of security (I know of no security expert who would advise you run X as root) your points are valid and you may run as root if you wish. This is not supported on these forums.

Your analysis of firewalls is flawed, they help, but they are by no means a panacea. Even windows security goes way beyond a firewall. If you run a server you need to know how to secure it. By default, Ubuntu Desktop has no servers running, so there is nothing to firewall.

---

### Post by forger on 2008-06-27
Can I add a real reason?
1) Say you have openssh-server / sshd enabled. While someone tries to break into your desktop, they'll logically try "root" as the first account, which doesn't have a password set :) This way you keep unwanted visitors off your private electronic (and physical) property...

---

### Post by kenbb99 on 2008-06-27
blazercist:

I understand that an operating system that makes you type passwords all the time (along the lines of "are you sure?") will be more secure than one that doesn't.  I don't think that's the same as inherently secure, it just makes it a lot harder to change things.  It sounds like you're saying that Windows would be more secure if you had to type in passwords all the time.  I'm not sure that's what people mean by "inherently secure" since it is possible to log in as regular user in XP and only log in as Admin when you want to change something.  (Yes, I am trying to transition from Windows XP.)

I'm not sure why I don't want to have root rights when I'm surfing.  I'm not making any changes to my system then.  I don't write scripts too much (just 8 so far), and if I need to, can't I just log in as user to keep from making a mistake?  I would rather experience the tediousness of logging out and then in as user occasionally than having to type my password in, literally, at least 50 times a day.

Having to type my password in all the time doesn't give me a heads up since it happens so often, for even the seemingly most routine tasks.  I now just ignore it and type in my password as fast as I can so I can go on with what I'm doing.  I may change my password from a secure one to 1 character to speed this up.  I don't seem to be able to change my password to "Enter".

I do mind screwing up my system all the time, or at all for that matter, but, as I mentioned, I was able to do that when logged in as user without having to enter a password.

vor:

Thanks, but this is one of those paternalistic "we're just saving you from yourself" answers I've seen before.  As I mentioned to blazercist, I am a Windows XP user.  I have not completely destroyed my XP machine in at least 10 years.  I am logged in as Admin all the time under XP.  How can anyone predict that I *will* completely destroy my machine?  Even if I'm not very smart and haven't used Ubuntu for very long, I won't necessarily destroy my machine.  Unless there's something about Ubuntu I don't know.


I'm not trying to defend XP.  I'm trying to get away from it and still be able to set my system up the way I want and work reasonably efficiently.  Still looking for an answer ...

---

### Post by Frak on 2008-06-27
> **kenbb99 said:**
> 1)  "You can wreck your install by mistake."
I can wreck my install by mistake without logging in as root.  I've done it.  I didn't even have to type a password to do it.  To do a lot of basic tasks I have to sudo or sudo su which, so far as I can tell, sets me up to wreck my system in the same way as logging in as root.

It's to keep you from wrecking your system while on it.

> **kenbb99 said:**
> 2)  "It's insecure."
No one else uses my system.  It's in my home office.  No one comes in here.  (Now if I vacuumed once in a while ...)

When you're on the internet, everybody uses your system.

> **kenbb99 said:**
> 3)  "The outside world can run scripts and viruses that will wreck your install."
I have a hardware firewall.  I read in a forum somewhere that Ubuntu does not have a software firewall or virus scanner because Linux is inherently secure.  I think you could make almost any operating system secure by including a software firewall and a virus scanner, putting them behind a hardware firewall and asking users to type in passwords all the time.

Linux has a built-in firewall called iptables. There are anti-virus programs available for Linux, but they are used to scan Windows computers/partitions. But yes, Hardware firewalls are inherently more secure because they cannot be tampered with as easily.

> **kenbb99 said:**
> 4)  "This protects you from yourself."
This sounds very paternalistic.  I don't want to be protected from myself.  Not letting me drink beer would also protect me from myself but I like to have one now and then.  I've read that one of the strong features of Linux is that it is configurable.  That is probably so, but it sure is like pulling my own teeth to do it.  Now if I was logged in as root all the time ...

Paternalistic is not allowing you to log in as root at all. You always have the option of using the root privileges.

> **kenbb99 said:**
> 5)  "That is the way it is designed."
Is that a bug or a feature?

Feature. Even Windows has a "sudo" like mode when run under limited account instead of default administrative (Virii cannot install themselves without an admin account)

OS X uses carbon-sudo as its main authentication system.

---

### Post by mrgnash on 2008-06-27
If you know what you're doing, you can configure Ubuntu to login as root without too much trouble. If you don't, then you shouldn't even be contemplating it.

---

### Post by Dr Small on 2008-06-27
I am all for you running your system the way you want to, and will not stop you. But you can't come complaining to us if you do wreck the system.

Running as Root is somewhat dangerous, but I believe it is over exagerated at times, like alot of things in life. Run your system as you see fit.

---

### Post by wrtpeeps on 2008-06-27
> **kenbb99 said:**
> 

Thanks, but this is one of those paternalistic "we're just saving you from yourself" answers I've seen before.  As I mentioned to blazercist, I am a Windows XP user.  I have not completely destroyed my XP machine in at least 10 years.  I am logged in as Admin all the time under XP.  How can anyone predict that I *will* completely destroy my machine?  Even if I'm not very smart and haven't used Ubuntu for very long, I won't necessarily destroy my machine.  Unless there's something about Ubuntu I don't know.


I'm not trying to defend XP.  I'm trying to get away from it and still be able to set my system up the way I want and work reasonably efficiently.  Still looking for an answer ...

Even as admin in xp, there is a limited amount you can do. Windows will still block you from doing things that will damage your system.

---

### Post by Bastaard on 2008-06-27
It's not hard to set up a login as root, if you want to, why don't you?

The reasons you gave yourself are the reasons I don't do it. I like to know that I won't be ******* things up, or malfunctioning software is ******* things up for me. I like drinking beer, and I wouldn't mind someone asking me: "are you sure you want to get completely wasted tonight?" when I'm drinking too much. When I buy a coke and it turns out to be pure vodka, I wouldn't mind someone telling me this beforehand. I can still decide if I want to drink it, but it builds in some security.

Now if you'll excuse me I'm off to drink beer.

---

### Post by paul101 on 2008-06-27
so, tell me... why exactly do you *need* to log in as root?? (to the origanal poster)

---

### Post by Tatty on 2008-06-27
> **kenbb99 said:**
> I have not completely destroyed my XP machine in at least 10 years.  I am logged in as Admin all the time under XP.  How can anyone predict that I *will* completely destroy my machine?  Even if I'm not very smart and haven't used Ubuntu for very long, I won't necessarily destroy my machine..

The classic line is "Linux is not Windows", and this certainly applies here.

Windows is designed to protect users from themselves by hiding all the more powerful features, and preventing the editing and deletion of the vast majority of the system.

Linux takes a different approach and there are a lot of very powerful utilities sitting just in front of you with no limits on what you can do.  With just one slip of the finger you can make a typing mistake and instead of deleting a folder, you are deleting every file on the system.  Root and sudo are a very happy safety net.


There is nothing to stop you from logging in as root if you wish to do so - doing so is well documented - but there is certainly no way I would do this without good reason.

---

### Post by reyfer on 2008-06-27
Let him run his system as root, come on, he has the right to be one of the few people that are victims of an online exploit because they surf the net with their root account, therefore giving any script around permission to run on his machine.

> I'm not sure why I don't want to have root rights when I'm surfing. I'm not making any changes to my system then.

Neither are the thousands that get viruses and trojans in windows, and still they get them

---

### Post by monstermudder78 on 2008-06-27
> **paul101 said:**
> so, tell me... why exactly do you *need* to log in as root?? (to the origanal poster)

Probably because he is tired of:
```
sudo aptitude update && upgrade
```
Then enter password.

Then: ```
sudo aptitude install *whatever*
```
Then: ```
gksudo nautilus
```
Then enter password.

Then: ```
gksudo gedit
```
Then enter password.
By this time sudo has expired in terminal so when you ```
sudo aptitude *whatever*
```
he has to enter the password AGAIN.

---

### Post by K.Mandla on 2008-06-27
Moved to Recurring Discussions.

---

### Post by Darkade on 2008-06-27
> **paul101 said:**
> so, tell me... why exactly do you *need* to log in as root?? (to the origanal poster)
I was about to post the same question.

Why would you need to login as root all the time?

Do you install apps every 5 minutes?
Do you edit config files every 10?

What I mean is that there's no regular need to be root. I think that I type sudo and my pwd once every two days, probably less. 

At the beging of using this OS, when you are setting it up just the way you want it to be, you proably need to type sudo frequently but you just stop needing it so often

---

### Post by p_quarles on 2008-06-27
> **monstermudder78 said:**
> Probably because he is tired of:
```
sudo aptitude update && upgrade
```
Then enter password.

Then: ```
sudo aptitude install *whatever*
```
Then: ```
gksudo nautilus
```
Then enter password.

Then: ```
gksudo gedit
```
Then enter password.
By this time sudo has expired in terminal so when you ```
sudo aptitude *whatever*
```
he has to enter the password AGAIN.
For such a case, it's completely acceptable and expect to run:
```
sudo -i
```
to obtain a root terminal interface. 

What's foolish is running the whole system (e.g., your web browser, your e-mail program, the GUI itself, and the little widget that gives you the current weather) as root. They don't need root privileges to do anything they should ever be doing. 

"Why not run as root?" == "Why not give the mall rent-a-cop a bazooka?"

---

### Post by monstermudder78 on 2008-06-27
> **p_quarles said:**
> For such a case, it's completely acceptable and expect to run:
```
sudo -i
```
to obtain a root terminal interface. 

What's foolish is running the whole system (e.g., your web browser, your e-mail program, the GUI itself, and the little widget that gives you the current weather) as root. They don't need root privileges to do anything they should ever be doing. 

"Why not run as root?" == "Why not give the mall rent-a-cop a bazooka?"

Ok, honest question for my own information, will sudo -i allow gedit and nautilus to run as root?  That is where I get hung-up.

---

### Post by Frak on 2008-06-27
> **monstermudder78 said:**
> Ok, honest question for my own information, will sudo -i allow gedit and nautilus to run as root?  That is where I get hung-up.
As long as they are invoked over the command line, yes.

---

### Post by monstermudder78 on 2008-06-27
> **Frak said:**
> As long as they are invoked over the command line, yes.

Very well, thank you.

---

### Post by p_quarles on 2008-06-27
> **monstermudder78 said:**
> Ok, honest question for my own information, will sudo -i allow gedit and nautilus to run as root?  That is where I get hung-up.
Yes, but it's better to run those using gksu/gksudo. If the 15 minute timeout for sudo is troubling you, you can edit /etc/sudoers to extend that to something you can deal with. Doing that is *far* better than running everything as root.

---

### Post by kenbb99 on 2008-06-27
monstermudder78 sums up my situation very succinctly.  I easily type in my password 50 times a day, probably many more.  Darkade's comments fit in just right with this.  I don't install apps every 5 minutes or edit config files every 10, but I'm still have to enter my password dozens of times a day.  Most recently I've been trying to get my USB wireless network adapter set up.  Sequence is very similar to what monstermudder78 described: installing apps, editing config files, copying driver components to various subdirectories, etc.  Test.  Repeat.  It's been the same with many components since I got started - video driver, network drive access, and so on.  There are many more components, applications, and settings to go.  And apparently a lot more password-typing.

mrgnash's comment that I shouldn't even be contemplating setting Ubuntu to log in as root appears to take paternalism to a whole new level.  Now someone's telling me not just what I can't do but what I can't think.  Fortunately I haven't found that sentiment representative of what I've read elsewhere on the forum.

Bastaard - I didn't say I want to get wasted, I said that I like to have a beer now and then.  But if I do decide to get wasted, as long as I don't put myself in the position to hurt anyone but myself, I don't want to be nagged about it every time I take a sip.  That is what the password screens are doing.

Tatty - I recognize that Linux is not Windows and that's want I want to use Linux.  Windows may or may not hide all the powerful features to keep me from hurting myself, but I have no trouble getting to them without typing a password all the time.

reyfer - I've never gotten a virus or trojan running Windows.  I don't have to type a password all the time.  It sounds like you're saying that setting up Ubuntu to run without passwords is less secure than running XP (without passwords, as I've always had it set up).

p_quarles - If sudo -i accomplishes the same thing, then I's all for it.  My experience in running terminal is that there are still piles of things (accessing network drives, editing Users and Groups, setting installing and uninstalling software, etc.) that require passwords even if I have elevated privileges in terminal.  I understand that many of these same things can be done through terminal, but I do want to use the GUI whenever possible.  That's one of the things I like about Ubuntu.  I think one of the main reasons you don't want to give a bazooka to a rent-a-cop is the harm he can do to others, not just himself.  I am not aware that logging in as root could hurt anyone but me.

I would just like to repeat that I am not a fan of Windows and want to get away from it.  I would also like to get away from having to type my password all the time and to be able to change the settings I want to - most of which are required to apply the solutions listed elsewhere in this forum - without be blocked or nagged.

Forgot to mention:

If I screw up my system with root, I promise to accept responsibility for my stupidity.  I will not whine or ask for help because of it.  In this forum (smilie-wink goes here, but I can't seem to add it in edit mode.)

---

### Post by Greyed on 2008-06-27
> **blazercist said:**
> itll tell you that you dont have the permission, this is a final line of defense for newbies and experts alike, it gives you a warning that what you are about to do may have serious consequences and you should think twice. 

Now if only the password prompt sported the words, "There be dragons" all would be right with the world.

---

### Post by monstermudder78 on 2008-06-27
> **p_quarles said:**
> Yes, but it's better to run those using gksu/gksudo. If the 15 minute timeout for sudo is troubling you, you can edit /etc/sudoers to extend that to something you can deal with. Doing that is *far* better than running everything as root.

Ok, this is what I just did:
```
user@desktop:~$ sudo -i
[sudo] password for user:
root@desktop:~# gedit

```
This allowed me to run gedit as root, correct?  I was able to save a file owned as root without giving another password.  Is there a problem with this?

---

### Post by Greyed on 2008-06-27
> **kenbb99 said:**
> Most recently I've been trying to get my USB wireless network adapter set up.  Sequence is very similar to what monstermudder78 described: installing apps, editing config files, copying driver components to various subdirectories, etc.  Test.  Repeat.

If you know you're going to be doing an extended sequence of items in root it is ok to "sudo -i" to get to a root shell for the duration.  The point is to elevate *when you need to* and **only as long as needed**.  For many things one entry of the password is enough.  Sometimes it isn't.  So elevate until you're done then drop back down you your user account.

Or, in a shorter sentence.

**You** are the master, not the computer.

---

### Post by p_quarles on 2008-06-27
> **monstermudder78 said:**
> Ok, this is what I just did:
```
user@desktop:~$ sudo -i
[sudo] password for user:
root@desktop:~# gedit

```
This allowed me to run gedit as root, correct?  I was able to save a file owned as root without giving another password.  Is there a problem with this?
Yes, that worked correctly, but it's not the recommended solution.The 'gksu' application is a graphical wrapper for root commands that helps avoid common errors. More information:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Frak on 2008-06-27
> **kenbb99 said:**
> monstermudder78 sums up my situation very succinctly.  I easily type in my password 50 times a day, probably many more.  Darkade's comments fit in just right with this.  I don't install apps every 5 minutes or edit config files every 10, but I'm still have to enter my password dozens of times a day.  Most recently I've been trying to get my USB wireless network adapter set up.  Sequence is very similar to what monstermudder78 described: installing apps, editing config files, copying driver components to various subdirectories, etc.  Test.  Repeat.  It's been the same with many components since I got started - video driver, network drive access, and so on.  There are many more components, applications, and settings to go.  And apparently a lot more password-typing.

sudo -i
Do what you need
exit
later, rinse, and repeat

> **kenbb99 said:**
> mrgnash's comment that I shouldn't even be contemplating setting Ubuntu to log in as root appears to take paternalism to a whole new level.  Now someone's telling me not just what I can't do but what I can't think.  Fortunately I haven't found that sentiment representative of what I've read elsewhere on the forum.

Suggestions != forced
Nobody here can force you to do anything.

> **kenbb99 said:**
> Bastaard - I didn't say I want to get wasted, I said that I like to have a beer now and then.  But if I do decide to get wasted, as long as I don't put myself in the position to hurt anyone but myself, I don't want to be nagged about it every time I take a sip.  That is what the password screens are doing.

With power comes responsibility.
With responsibility comes ignorance.
Ignorance is bliss.

> **kenbb99 said:**
> Tatty - I recognize that Linux is not Windows and that's want I want to use Linux.  Windows may or may not hide all the powerful features to keep me from hurting myself, but I have no trouble getting to them without typing a password all the time.

Administrative account != limited
Of course it's just going to let you in, along with anything else that wants access.

> **kenbb99 said:**
> reyfer - I've never gotten a virus or trojan running Windows.  I don't have to type a password all the time.  It sounds like you're saying that setting up Ubuntu to run without passwords is less secure than running XP (without passwords, as I've always had it set up).

Run a ClamAV scan on your Windows partition, then show me the report that shows no malware on your system. You'd be suprised.

> **kenbb99 said:**
> p_quarles - If sudo -i accomplishes the same thing, then I's all for it.  My experience in running terminal is that there are still piles of things (accessing network drives, editing Users and Groups, setting installing and uninstalling software, etc.) that require passwords even if I have elevated privileges in terminal.  I understand that many of these same things can be done through terminal, but I do want to use the GUI whenever possible.  That's one of the things I like about Ubuntu.  I think one of the main reasons you don't want to give a bazooka to a rent-a-cop is the harm he can do to others, not just himself.  I am not aware that logging in as root could hurt anyone but me.

It can hurt the other files/programs around you.

> **kenbb99 said:**
> I would just like to repeat that I am not a fan of Windows and want to get away from it.  I would also like to get away from having to type my password all the time and to be able to change the settings I want to - most of which are required to apply the solutions listed elsewhere in this forum - without be blocked or nagged.

If you want to not type in the password every time you want to do something that may harm your system, you came to the wrong place.

P.S. Why didn't I get a response?

---

### Post by sisco311 on 2008-06-27
> **kenbb99 said:**
> Why do I keep reading that I shouldn't log in as root?  So far as I can tell, the reasons, and my thoughts on them, are as follows:

1)  "You can wreck your install by mistake."
I can wreck my install by mistake without logging in as root.  I've done it.  **I didn't even have to type a password** to do it.  To do a lot of basic tasks I have to sudo or sudo su which, so far as I can tell, sets me up to wreck my system in the same way as logging in as root.

Did you do it with a hammer?

---

### Post by wrtpeeps on 2008-06-27
> **monstermudder78 said:**
> Ok, this is what I just did:
```
user@desktop:~$ sudo -i
[sudo] password for user:
root@desktop:~# gedit

```
This allowed me to run gedit as root, correct?  I was able to save a file owned as root without giving another password.  Is there a problem with this?

I would say there wouldn't be a problem, so long as you remember which terminal you have given root access to.

Though, I am no expert :p

---

### Post by Frak on 2008-06-27
> **sisco311 said:**
> Did you do it with a hammer?
I too found the post to be more relevant to Home Depot than to Ubuntu Security.

---

### Post by monstermudder78 on 2008-06-27
> **p_quarles said:**
> Yes, that worked correctly, but it's not the recommended solution.The 'gksu' application is a graphical wrapper for root commands that helps avoid common errors. More information:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

But how do I use gksudo with the benefit of -i ?  In this case am I not running gedit AS ROOT?  Not using sudo, so gksudo shouldn't be needed right?  It would be the same as a user running gedit from the command line, no?

---

### Post by Frak on 2008-06-27
> **monstermudder78 said:**
> But how do I use gksudo with the benefit of -i ?
gksudo is a gtk frontend to sudo that (ironically) is best used over the command line.

gksudo <application>

Thats it, or

gksudo

will launch the gksu app.

---

### Post by monstermudder78 on 2008-06-27
> **Frak said:**
> gksudo is a gtk frontend to sudo that (ironically) is best used over the command line.

gksudo <application>

Thats it, or

gksudo

will launch the gksu app.

Ok, I understand all that, but I was told that in this case:
```
user@desktop:~$ sudo -i
[sudo] password for user:
root@desktop:~# gedit
```
it would be 'more correct' or better to use gksudo, somehow.  My response to that is 'How?' and then this argument: In this case am I not running gedit AS ROOT? Not using sudo, so gksudo shouldn't be needed right? It would be the same as a user running gedit from the command line, no?

---

### Post by Darkade on 2008-06-27
> **kenbb99 said:**
> I've never gotten a virus or trojan running Windows.  I don't have to type a password all the time.  It sounds like you're saying that setting up Ubuntu to run without passwords is less secure than running XP (without passwords, as I've always had it set up).


There you have a point. I think this shouldn't be about "should I log in as root" but instead it should be about "Is there a *real* point to login as root?"As I've said before there is no reason to do it even more that a couple of times a day, at most. And as p_quarles said editing your  /etc/sudoers  is a far better solution to type your password less. time may depend in how many times would it be acceptable for you to type in your password.

Finally if you really want to login as root you can do it. You can do it both in command line and in graphics mode, actually at the begginig of my ubuntu days I did that, as you I saw no point in not beeing root the whole time so I would only use root to login. And truth to be told is I found it was just about the same as beeing a regular user(I saw no point in beeing able to all the time editing config files), so I disabled it.

So I say go ahead  try it, beeing root all the time ain't that great and there's a chance *you* by mistake mess all your installation. as with a regular user account you may just mess your home folder.

---

### Post by Frak on 2008-06-27
> **monstermudder78 said:**
> Ok, I understand all that, but I was told that in this case:
```
user@desktop:~$ sudo -i
[sudo] password for user:
root@desktop:~# gedit
```
it would be 'more correct' or better to use gksudo, somehow.  My response to that is 'How?' and then this argument: In this case am I not running gedit AS ROOT? Not using sudo, so gksudo shouldn't be needed right? It would be the same as a user running gedit from the command line, no?
For one
sudo <command>
and
sudo -i
<command>
do the EXACT SAME THING

Think of gksudo as a refined sudo for graphical apps (in a gtk setting).
so
gksudo <command>
is a preffered way to launch a graphical app, while
gksudo
will launch the gksu interface to help you authenticate for running admin apps.

---

### Post by cardinals_fan on 2008-06-27
I must confess a powerful hatred for sudo.  It blurs what I feel should be a very clear line - the line between different users.  If I need to perform system maintenence, I use "su" to sign in as root, complete my business, and leave the root account.  Clear and simple.

---

### Post by p_quarles on 2008-06-27
You can use gksu from within a root shell.

All of these commands that we've been discussing are just different ways of granting root privileges to an application. You don't use sudo "instead of" root -- it's just one way of getting root permissions.

What is specifically not recommended is using a login manager to obtain root status.

---

### Post by Frak on 2008-06-27
> **p_quarles said:**
> You can use gksu from within a root shell.

All of these commands that we've been discussing are just different ways of granting root privileges to an application. You don't use sudo "instead of" root -- it's just one way of getting root permissions.

What is specifically not recommended is using a login manager to obtain root status.
As I believe, the login manager for Gnome deny's root login by default.

---

### Post by p_quarles on 2008-06-27
> **cardinals_fan said:**
> I must confess a powerful hatred for sudo.  It blurs what I feel should be a very clear line - the line between different users.  If I need to perform system maintenence, I use "su" to sign in as root, complete my business, and leave the root account.  Clear and simple.
But the whole purpose of sudo is to maintain those "lines" between users. It allows a system administrator to actually dole out privileges in an intelligent way, rather than having to do everything him- or herself or (even worse) giving the root password to everyone who has any cause to use it.

---

### Post by monstermudder78 on 2008-06-27
> **p_quarles said:**
> You can use gksu from within a root shell.
Cool thanks.
> **p_quarles said:**
> 
All of these commands that we've been discussing are just different ways of granting root privileges to an application. You don't use sudo "instead of" root -- it's just one way of getting root permissions.
But doesn't
```
root@desktop:~# gedit
```
Accomplish the same thing as
```
user@desktop:~$ gksudo gedit
```
? Or am I sadly mistaken?
> **p_quarles said:**
> 
What is specifically not recommended is using a login manager to obtain root status.
Roger that.

---

### Post by aysiu on 2008-06-27
It's probably possible to walk around with, in cash, all the money you have all the time and never get mugged, too. Still, it's a good security practice to keep your money safely in a trustworthy bank and carry around only the cash you plan to spend in the next few days.

*sudo* allows you to run with administrative privileges only what needs to be run (Gedit, Users-Admin, Nautilus, etc.) instead of running *everything* as root when you need to run only one application as root to accomplish the task at hand.

This security practice is a sound one that applies to all operating systems that are connected to the internet. You can read more here about how it applies to Windows:
[Applying the Principle of Least Privilege to User Accounts on Windows XP](http://technet.microsoft.com/en-us/library/bb456992.aspx)

The "Well, I've done _____ and have never had such-and-such bad thing happen to me" is not a valid defense of bad security practices. It's possible to ride your bicycle for years without having your head split open in accident, run across streets without looking both ways without ever getting hit by a car, or tell all your friends and family members your ATM password without any of them stealing your money, but none of those practices is good from a security or safety standpoint.

It is the job of the Ubuntu Forums to support the official security practices implemented in Ubuntu. We will not stop you from doing your own research on how to use other security implementations of varying quality, but it also isn't out job to encourage bad practice. Deviate from the default setup at your own risk, and with this forums' help. Do it on your own, and we won't stop you.

If you find yourself making a lot of root changes to a lot of files in a particular go, create a keyboard shortcut for the command ```
gksudo nautilus
``` and that should pretty much take care of it. It's actually more convenient than logging in separately graphically as root, since *gksudo nautilus* launches as a window directly inside of your regular user session.

---

### Post by cardinals_fan on 2008-06-27
> **p_quarles said:**
> But the whole purpose of sudo is to maintain those "lines" between users. It allows a system administrator to actually dole out privileges in an intelligent way, rather than having to do everything him- or herself or (even worse) giving the root password to everyone who has any cause to use it.
I like to look at my shell and immediately see what user I'm running.  That user has a certain amount of permissions, and that's that.

---

### Post by sisco311 on 2008-06-27
???OFFTOPIC:
to exit from root shell:
```
exit
```or
```
logout
```use
```
whoami
```to print the username.
Can somebody add this information to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Darkade on 2008-06-27
> **aysiu said:**
> It's probably possible to walk around with, in cash, all the money you have all the time and never get mugged, too. Still, it's a good security practice to keep your money safely in a trustworthy bank and carry around only the cash you plan to spend in the next few days.


Great analogy. Aysiu every time I see one of your posts it has all the sencibility that is needed. Great writing work as always:lolflag:

---

### Post by monstermudder78 on 2008-06-27
> **aysiu said:**
> 
If you find yourself making a lot of root changes to a lot of files in a particular go, create a keyboard shortcut for the command ```
gksudo nautilus
``` and that should pretty much take care of it. It's actually more convenient than logging in separately graphically as root, since *gksudo nautilus* launches as a window directly inside of your regular user session.

All I am trying to accomplish is have one terminal window with "sudo privilages" as well as gedit and nautilus with "sudo privilages".  At no time do I want to browse the internet as root, I just want to stop wasting time inputting my password over and over again.  If I use:
sudo -i, then launch gedit and nautilus from there, as well as use that terminal for my root tasks, what is the issue?

---

### Post by p_quarles on 2008-06-27
> **cardinals_fan said:**
> I like to look at my shell and immediately see what user I'm running.  That user has a certain amount of permissions, and that's that.
Okay, but seriously: what you're talking about is only suitable for a computer being used by a single person, or on which the administrative needs are incredibly simple. My response was basically to point out that your objection to sudo completely ignores how essential it is to any kind of complicated system setup.

---

### Post by jrusso2 on 2008-06-27
> **kenbb99 said:**
> Why do I keep reading that I shouldn't log in as root?  So far as I can tell, the reasons, and my thoughts on them, are as follows:

1)  "You can wreck your install by mistake."
I can wreck my install by mistake without logging in as root.  I've done it.  I didn't even have to type a password to do it.  To do a lot of basic tasks I have to sudo or sudo su which, so far as I can tell, sets me up to wreck my system in the same way as logging in as root.

2)  "It's insecure."
No one else uses my system.  It's in my home office.  No one comes in here.  (Now if I vacuumed once in a while ...)

3)  "The outside world can run scripts and viruses that will wreck your install."
I have a hardware firewall.  I read in a forum somewhere that Ubuntu does not have a software firewall or virus scanner because Linux is inherently secure.  I think you could make almost any operating system secure by including a software firewall and a virus scanner, putting them behind a hardware firewall and asking users to type in passwords all the time.

4)  "This protects you from yourself."
This sounds very paternalistic.  I don't want to be protected from myself.  Not letting me drink beer would also protect me from myself but I like to have one now and then.  I've read that one of the strong features of Linux is that it is configurable.  That is probably so, but it sure is like pulling my own teeth to do it.  Now if I was logged in as root all the time ...

5)  "That is the way it is designed."
Is that a bug or a feature?

I find these answers unconvincing and still want to log in as root.  All the time.  I tried to set up auto login as root but the message says that that's forbidden.  I guess that's one of those things that's not configurable.

In case it is not obvious, I am pretty new to Ubuntu.  I have spent about 50 hours setting up and configuring my system - most of it researching how to solve problems, not actually solving the problems by the way - and about 5 hours using it.  I have about another 10 hours to go, I think.  Logging in as root could possibly reduce this figure a bit and make me a lot happier with the system or increase it a lot and make me just a bit annoyed.

What am I missing?  Why not go the root route?

In Lindows the default was to use the root account and the people on the forum over at Linspire are the opposite of here.  They get angry if you tell them running as root as bad.  They all say they have been doing it for years and nothing bad has happened.

On the other hand many of them seem to suffer from an extreme lack of knowledge of Linux compared to other users with thousands of posts and titles like guru.  They got so reliant on CNR a lot of them never learned apt or anything other commands.

To each there own but over there you get flamed for telling them not to run as root and over here you get infractions for telling people how to unlock root.

Not sure which is worse.

---

### Post by kenbb99 on 2008-06-27
aysiu -  I'd have to say I don't find your analogy persuasive.  I think you're trying to point out that certain behavior is risky and that I can't take my own experience as the only measure of the risk.  I agree.  I am inexperienced with Ubuntu and can't judge the risk of surfing with my roots down (sorry, had to do it.) I am knowledgeable about the risks of XP as far as safe surfing behavior.  Based on my practices, my risk is extremely low yet I autologin as Admin and don't have to type any passwords for system tasks.  Again, it sounds like Ubuntu is less secure if set up similarly to the setup used by XP for the vast majority of home users.  I was of the opposite impression.  I'm not defending XP, I'm using it as a benchmark with which I am familiar and, I think, most others on this forum are.

Perhaps darkade's post (#35) is right on point and I am phrasing my question incorrectly.  I am probably in the same position he describes - time will tell - in which I will not think I need to be root in a few weeks or months after I have my system dialed in exactly the way I want it with all the hardware working correctly.  Then I can go back to logging in as user.   

Combining darkade's concept that maybe I just think I need to be root when really I can accomplish what I want without the risks of root - which I absolutely believe are real although no one's described how they apply to me - and monstermudder78 and p_quarles discussion about sudo -i, perhaps I can do what I want without seeing any password prompts (except, apparently when I enter sudo).  I'll have to try it and see if this does it.

Perhaps the combined wisdom of the forum will save me from myself, and root.

---

### Post by cardinals_fan on 2008-06-27
> **p_quarles said:**
> Okay, but seriously: what you're talking about is only suitable for a computer being used by a single person, or on which the administrative needs are incredibly simple. My response was basically to point out that your objection to sudo completely ignores how essential it is to any kind of complicated system setup.
A normal user shouldn't have to perform any system configuration.  The sysadmin (on my computer, me) should handle all that.  What configuration is necessary can usually be handled by tweaking /etc/group and file permissions.

With that said, my response was merely indicating the setup that I prefer on MY computer (which has me as its primary user, with my mom using it occaisonally to browse the web).  Everyone can use whatever system suits them best.

@OP: I think that the real question here is rather simple: why do you need root permissions so often?  Daily use shouldn't require major system configuration...

---

### Post by kenbb99 on 2008-06-27
I don't think sudo -i is going to do what I'm looking for.  It only saved me from one password in the first three tasks I tried - not counting the password I had to put in for sudo.  After sudo -i, I was able to start my network adapter (from terminal) and open a network drive from a desktop link without a password.  The next thing I wanted to do was change my user account back to auto login so I could experiment with sudo -i.  System > Administration > Login Window asked me for a password.  I know this is a very small sample (four tasks, two passwords), but this doesn't seem to solve my problem.  I understand, I think, that tasks run from terminal won't require passwords with sudo -i, but Ubuntu has a beautiful GUI that someone has put a lot of time into and I'd like to use it as much as possible.

Perhaps I need to rephrase my question and start a new thread called "Short of logging in as root, how do I configure my system so that I never get asked for a password?"

---

### Post by p_quarles on 2008-06-27
1) You can run those GUI applications from the terminal.
2) You can create rules in /etc/sudoers that give you passwordless access to certain (or all) commands.

Look: the information is out there, and it's not hard to find if you know what you're looking for (and now, I believe, you have enough information to know) -- but this forum is specifically not suited to this kind of usage. 

In other words, what you're asking for goes against Ubuntu security policy. That doesn't mean that anyone here is telling you what to do or what to think -- it means that we can't help you with those questions.

---

### Post by monstermudder78 on 2008-06-27
> **p_quarles said:**
> 
In other words, what you're asking for goes against Ubuntu security policy. That doesn't mean that anyone here is telling you what to do or what to think -- it means that we can't help you with those questions.

No offense to anyone but in my opinion this answer is a load of crap.  Saying that just because "Ubuntu" doesn't think it's a good idea, we can't help you is no different than windows telling you what to do because it thinks it knows best.  If I misunderstood your post, and you personally are the only one refusing to help, then that is A-O-K with me.  But the way it was phrased and from what others have posted about getting infractions > ...and over here you get infractions for telling people how to unlock root. that is not the way it sounds.  It doesn't seem like that is in line with the official Ubuntu philosophy, either:> Our Philosophy

Our work is driven by a philosophy on software freedom that aims to spread and bring the benefits of software to all parts of the world. At the core of the Ubuntu Philosophy are these core philosophical ideals:

   1. **Every computer user should have the freedom to download, run, copy, distribute, study, share, *change* and improve their software for any purpose,** without paying licensing fees.
   2. Every computer user should be able to use their software in the language of their choice.
   3. Every computer user should be given every opportunity to use software, even if they work under a disability. 

Our philosophy is reflected in the software we produce and included in our distribution. As a result, the licensing terms of the software we distribute are measured against our philosophy, using the Ubuntu License Policy.

When you install Ubuntu almost all of the software installed already meets these ideals, and we are working to ensure that every single piece of software you need is available under a license that gives you those freedoms.

Currently, we make a specific exception for some "drivers" which are only available in binary form, without which many computers will not complete the Ubuntu installation. We place these in a restricted section of your system which makes them easy to remove if you do not need them.

More about components>>
Free software

**For Ubuntu, the 'free' in 'free software' is used primarily in reference to *freedom*,** and not to price - although we are committed to not charging for Ubuntu. The most important thing about Ubuntu is that it confers rights of software freedom on the people who install and use it. It is these freedoms that enable the Ubuntu community to grow, continue to share its collective experience and expertise to improve Ubuntu and make it suitable for use in new countries and new industries.

Quoting the Free Software Foundation's 'What is Free Software', the freedoms at the core of free software are defined as:

    * The freedom to run the programme, for any purpose.
    * **The freedom to study how the programme works and adapt it to your needs.**
    * The freedom to redistribute copies so you can help others.
    * The freedom to improve the programme and release your improvements to the public, so that everyone benefits. 

Open source
Open source is a term coined in 1998 to remove the ambiguity in the English word 'free'. The Open Source Initiative described open source software in the Open Source Definition. Open source continues to enjoy growing success and wide recognition.

Ubuntu is happy to call itself open source. While some refer to free and open source as competing movements with different ends, we do not see free and open source software as either distinct or incompatible. Ubuntu proudly includes members who identify with both the free software and open source camps, and many who identify with both.

---

### Post by p_quarles on 2008-06-27
Tutorials for root logins are against the rules on this forum, which is in line with Ubuntu's own policy:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

That link explains why. You can call it what you like, but that's the established rule, and it is enforced. You are free to do whatever you like with the software (and again, the information is easy to find!), but that freedom does not extend to turning this forum into a chaotic mess of guesswork and bad advice.

---

### Post by Frak on 2008-06-27
> **monstermudder78 said:**
> No offense to anyone but in my opinion this answer is a load of crap.  Saying that just because "Ubuntu" doesn't think it's a good idea, we can't help you is no different than windows telling you what to do because it thinks it knows best.  If I misunderstood your post, and you personally are the only one refusing to help, then that is A-O-K with me.  But the way it was phrased and from what others have posted about getting infractions  that is not the way it sounds.  It doesn't seem like that is in line with the official Ubuntu philosophy, either:
Ubuntu doesn't restrict you from anything. The forums do. Information is a powerful thing, and it can be used for destruction. It has been outlined in the policy not to subvert the Ubuntu Security Model, and its something we all abide by.

If you want to know, **Google it**.

---

### Post by monstermudder78 on 2008-06-27
> **Frak said:**
> Ubuntu doesn't restrict you from anything. The forums do. Information is a powerful thing, and it can be used for destruction. It has been outlined in the policy not to subvert the Ubuntu Security Model, and its something we all abide by.

If you want to know, **Google it**.

Well, fair enough.  I must say that I am at least a little disappointed though.

---

### Post by sisco311 on 2008-06-27
<philosophy>> **monstermudder78 said:**
> No offense to anyone but in my opinion this answer is a load of crap.  Saying that just because "Ubuntu" doesn't think it's a good idea, we can't help you is no different than windows telling you what to do because it thinks it knows best.  If I misunderstood your post, and you personally are the only one refusing to help, then that is A-O-K with me.  But the way it was phrased and from what others have posted about getting infractions  that is not the way it sounds.  It doesn't seem like that is in line with the official Ubuntu philosophy, either:
[Jean-Jacques Rousseau]("http://en.wikipedia.org/wiki/Jean-Jacques_Rousseau")'s "**[The Social Contract, Or Principles of Political Right]("http://en.wikipedia.org/wiki/The_Social_Contract")**"
</philosophy>

---

### Post by monstermudder78 on 2008-06-27
> **sisco311 said:**
> <philosophy>
[Jean-Jacques Rousseau]("http://en.wikipedia.org/wiki/Jean-Jacques_Rousseau")'s "**[The Social Contract, Or Principles of Political Right]("http://en.wikipedia.org/wiki/The_Social_Contract")**"
</philosophy>
Cliff notes and how it relates to this topic please?  I believe that one just sailed right over my head.

---

### Post by cardinals_fan on 2008-06-27
> **monstermudder78 said:**
> No offense to anyone but in my opinion this answer is a load of crap.  Saying that just because "Ubuntu" doesn't think it's a good idea, we can't help you is no different than windows telling you what to do because it thinks it knows best.  If I misunderstood your post, and you personally are the only one refusing to help, then that is A-O-K with me.  But the way it was phrased and from what others have posted about getting infractions  that is not the way it sounds.  It doesn't seem like that is in line with the official Ubuntu philosophy, either:
[QUOTE=J.R.R. Tolkien]Perilous to us all are the devices of an art deeper than we possess ourselves.[/QUOTE]
If you don't have the technical skills necessary to configure the root account, you shouldn't do it.

With that said, I do believe that the forum policy is a bit out of sync with the Ubuntu Philosophy.  But I don't make the rules around here, I just follow them (you **did** agree to when you signed up).

---

### Post by Frak on 2008-06-28
> **monstermudder78 said:**
> Cliff notes and how it relates to this topic please?  I believe that one just sailed right over my head.
It means the sovereign society or community should create their own laws of will instead of being a "free man, with chains all around him" or bound by laws he does not agree with.

But again, this is just like a bathhouse of speech, where the owner determines the rules where Ubuntu is of itself where it can be discussed with everybodies own opinion wherever it is allowed, including just talking on the street.

---

### Post by monstermudder78 on 2008-06-28
> **Frak said:**
> It means the sovereign society or community should create their own laws of will instead of being a "free man, with chains all around him" or bound by laws he does not agree with.

But again, this is just like a bathhouse of speech, where the owner determines the rules where Ubuntu is of itself where it can be discussed with everybodies own opinion wherever it is allowed, including just talking on the street.

Thanks, I am a little disappointed in the forums to say the least, I have no problems with warnings being given before sensitive information is shared, but an outright "I won't tell you because I don't think you need to know, and no one else can tell you either" is a little too big-brother for me.  I think my days are limited on these forums.  Now if only I could find those greener pastures...

Anyone care to help me enable the root account on my new arch box? lolz

---

### Post by Frak on 2008-06-28
> **monstermudder78 said:**
> Thanks, I am a little disappointed in the forums to say the least, I have no problems with warnings being given before sensitive information is shared, but an outright "I won't tell you because I don't think you need to know, and no one else can tell you either" is a little too big-brother for me.  I think my days are limited on these forums.  Now if only I could find those greener pastures...

Anyone care to help me enable the root account on my new arch box? lolz
Root is automatically enabled on Arch.

---

### Post by p_quarles on 2008-06-28
> **monstermudder78 said:**
> Anyone care to help me enable the root account on my new arch box? lolz
That happens when you install it.

Seriously, no one is saying "no one can tell you how to enable a root account." We are saying "that raises some really difficult support issues for something that is virtually never necessary for functionality -- we don't support that here." If we didn't set limits on what is supported here we wouldn't be a particularly good source of information. 

Entering "set root password linux" in the Google search box, though, will provide you with dozens of people telling you exactly how to do that.

---

### Post by monstermudder78 on 2008-06-28
> **Frak said:**
> Root is automatically enabled on Arch.

Hahahahaha I know, I was just trying to be funny.  That was actually one of the things I enjoyed about arch, was all the configuration was done as root, so no sudo was needed.

---

### Post by Darkade on 2008-06-28
Don't you think this has grown way beyond what it was meant to be in the first place? I dunno, just wanted to express the way I feel about this. :lolflag:

---

### Post by kenbb99 on 2008-06-28
Discussion seems to have petered out and gone off topic.  I have not meant to flout the rules and purpose of this forum, and I understand that whoever sets up the forum has the right to set the rules to what they want and I don't have to come here if I don't like them.  I misunderstood the rule against subverting the Linux security system to mean that we weren't going discuss how to break /hack other people's systems or non-open source software.  I didn't think there was a problem discussing how to put my system at risk mainly I believe, notwithstanding the foregoing discussion, from myself. I will follow up on p_quarles advice to check out /etc/sudoers.  Perhaps I'm reading between the lines, but it sounds like I should check it out elsewhere.  I may start a new topic regarding how to reduce the password load.  I'm interpreting the rules to allow that.  Thanks.

---

### Post by bodhi.zazen on 2008-06-28
To be honest, I think this whole thread has gotten blown out of proportion.

I think the bottom line is :

1. You can run your computer any way you wish. If you have considered the advantages, disadvantages, and alternates, all the better.

2. To some extent, "when in Rome, do as the Romans" applies here. Each version of Linux has it's own approach to security and enabling root on Ubuntu makes as much sense as installing sudo on Fedora.

3. Along those lines, the forums staff feel new users should be taught how to run Ubuntu "properly" in that they should understand basic security, sudo vs su, permissions, etc first. After understanding the basics, if they choose to make alterations, more power to them. One must learn to walk before learning to run.


All too often, on these forums, I have seen new users given a small piece of information, ie how to set a root password, how to change the permissions of system files, or similar, without sufficient information / warnings on the implications of what they are doing.

IMO, and in the opinion of most, if no all of the staff, such incomplete information is detrimental to new users and time after time we see poor outcomes. Most of the time it leads to re installation. Sometimes, however, there is data loss or compromise of a server.

Generally users fall into 2 groups.

1. Experienced users. If you know what you are doing you may well choose to run as root. I understand this and run as root on some systems. Usually not log in as root mind you, but su - or sudo -i almost immediately after log in.

If you are an experienced user :
[list][*]you may run as root if you wish, you understand the implications.[*]Please take the time to explain permissions and such to the new users.[*]If you are experienced with another distro, but are new to Ubuntu consider learning how Ubuntu works before you dismantle it.[/list]

If you are a new user, both to Linux and Ubuntu:
[list][*]You too may run as you see fit.
[*]I advise you learn the basics before you do major changes to system files and security.[/list]

As staff, we discuss these issues and although it may be "paternal" we do feel our primary role is to educate first, alter random system files second. It may not be the solution for everyone, but it works well on these forums and there is no lack of information available a short google search away.

Linspire is free to run their distro the way they see best. As is Fedora, Debian, SUSE, Arch, Slackware, etc. In my experience, different is not necessarily better and in Linux there are often more then one way to solve any particular problem.

To argue about these issues is pointless, best understand what you are doing and why.

The OP is new to Ubuntu and is learning. Along those lines, Linux is not windows and not everything you know about Windows will apply to Linux. I suggest you start with this link :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Again, you may not agree with everything in that thread, but it is a good starting point.




I am going to leave this thread open for the moment as there is some educational content here, but please try to stay on topic.

---

### Post by kenbb99 on 2008-06-28
I check out visudo.  I thought I might want to make a simple edit as suggested by [https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20SUDO]("https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20SUDO") but I could get any edits to work.  I appeared to run into [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/207369) so I seem to be back where I started.  Any approved, non-work around, non-hacks to edit sudoers?  I did read to the end of the bug report but the suggestions seem to be work-around / hacks.

I read this [http://ubuntuforums.org/showthread.php?t=510812"]"http://ubuntuforums.org/showthread.php?t=510812"]http://ubuntuforums.org/showthread.php?t=510812](""http://ubuntuforums.org/showthread.php?t=510812") and learned some things, but I did find the same patronizing, paternalistic tone ("do not expect to get through this document in one session") I'm starting to recognize as a pattern. I want to learn, but I don't want to be insulted when I try. I know, if I don't like it I can go [fill in the blank].

These seems to be the fully-endorsed work around:

[http://ubuntuforums.org/showthread.php?t=779902]("http://ubuntuforums.org/showthread.php?t=779902")

---

### Post by Dipper on 2008-07-23
I agree completely with kenbb99.  Some of the responses to the question as to why it's not recommended to unlock and use the root account are paternalistic and patronizing.  Here's the two biggest problems I have (philosophically) with the so-called Ubuntu security model:

1. It's my computer.  I built it.  I spent the money on the motherboard, video card, hard drives, memory, and other parts.  I have the right to decide how it is used.  It's an affront to all of my efforts to ever be told (by the OS or by forum members) that I do not have permission to do something.

2. The RootSudo system is designed to work within a command-line environment.  I don't want to ever use command-line.  I use GUI exclusively.  Yes, it's because I'm used to Windows and Mac.  I don't care if CLI is "traditional".  Those are the traditions of old-school Linux users, not me.  From the time I sign on to my machine until the time I shut it down, I want to do nothing but pointing and clicking.  I don't want to be interrupted with password prompts.

For me, it's not about the pain of transition or the fear of trying something new.  It's the simple fact that I like my machine to work the way I want it to.

---

### Post by Bachstelze on 2008-07-23
> **Dipper said:**
> 
1. It's my computer.  I built it.  I spent the money on the motherboard, video card, hard drives, memory, and other parts.  I have the right to decide how it is used.  It's an affront to all of my efforts to ever be told (by the OS or by forum members) that I do not have permission to do something.

And users here, or Ubuntu developers, spend their free time helping others or developing Ubuntu, instead of doing something they could get paid for. It's an affront to all their efforts to tell them: "Do as I say!" You're not talking about computer parts here, you're talking about human beings. If you want, you can send me $200 by PayPal, and I will gladly tell you how to do what you want in Ubuntu. Otherwise, I am free to not tell you if I don't want to, and you can go find that out by yourself. It's not that hard, anyway...

---

### Post by bruce89 on 2008-07-23
> **HymnToLife said:**
> And users here, or Ubuntu developers, spend their free time helping others or developing Ubuntu, instead of doing something they could get paid for.

The core developers are paid for their packaging work.

---

### Post by aysiu on 2008-07-23
This is the forum policy, and contained within is a thorough explanation of why we don't support login-as-root: [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=765414)

---

