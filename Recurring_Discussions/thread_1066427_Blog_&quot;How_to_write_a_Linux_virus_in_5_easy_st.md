---
title: "Blog: &quot;How to write a Linux virus in 5 easy steps&quot; (Requires social engineering)"
date: 2009-02-10
forum: Recurring Discussions
---

### Post by newbie2 on 2009-02-10
> The rumor of the bullet-proof Linux architecture

There is this rumor going around that Linux is virus free. It is said that the old-fashioned multi-user heritage of Linux (and other *nix OSs) prevents malware, since users are not normally running their programs in admin mode (as root user). We are reminded that execute bits are needed to run anything – contrary to Windows – and that execute bits aren't set on any attachments or files saved from emails or from a web-browser.

Therefore, we are told, the very architecture of Linux is so much more superior to Windows that it's just not possible to successfully spread malware. Of course – it is acknowledged – a low-level bug, a buffer overflow or other issue is exploitable. But nevertheless, users can't just catch a virus by email or downloading malware from the Internet, contrary to “those Windows users”. Linux will protect them from their own stupidity.

At least so the story goes. But sadly, that's not true. I will show how it is possible in a few easy steps to write a perfectly valid email borne virus for modern desktop Linux. I will do so not because I want to put down Linux. Quite the opposite: I like and support Linux, which is all I'm running at home and at work. I'm a big supporter of free and open software as readers of this blog will know. But if there are any security risks, even in my favorite OS or distribution then they will need to be discussed. Even more important: A false sense of security is worse than a lack of security. And unsubstantiated claims of superiority don't help in a reasonable discussion either.
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)
:rolleyes:

---

### Post by lisati on 2009-02-10
While it's good to know that sneaky things are possible, why would I want to knowlingly do something to hurt my fellow *nix users?

---

### Post by cariboo on 2009-02-10
THe article states that you still have to do some social engineering in order to install the malware, so it still is dependent on the user. How is this supposed to spread to other computers?

Jim

---

### Post by The Tronyx on 2009-02-10
"The rumor of the bullet-proof Linux architecture" is when I stopped reading.

---

### Post by Dr Small on 2009-02-10
> What I'm showing here is merely an example of how the old-school social engineering "viruses" 
Once again, the use is the biggest threat to security.

---

### Post by tbraun on 2009-02-10
> **2point0 said:**
> "The rumor of the bullet-proof Linux architecture" is when I stopped reading.

In that case you missed some pretty good stuff. Too bad for you.

---

### Post by hyper_ch on 2009-02-11
a user can also chose to dd the whole harddrive. what's there to stop him? without user intercation this will do nothing.

---

### Post by mcduck on 2009-02-11
it's not a virus if it's not able to spread on it's own, and its not even a proper trojan since it's not able to hide the fact that it is a program, not something else like a picture. And even when running and configured to autostart, it's not able to hide itself, you'll see it in your sessions and you'll see the file itself, and can delete them to get rid of the malware program.


At the point when you get somebody to download that to your desktop and start it you could have done a lot more damage just by telling the stupid user to run some nasty command. Like hyper_ch said, why not just tell the user to dd his harddrive? It's already installed, and will definitely work just as well. The user is less likely to suspect anything since he doesn't need to download anything.. Does that make "dd" a virus as well? NO, it doesn't, and thus the program desribed in that article isn't a virus either.

---

### Post by JoshuaRL on 2009-02-11
> 
For example, it can start to pilfer through the user's address book to harvest email addresses, send them off to our malware server, start sending spam email or it can spread itself by email. It can install a Firefox extension that captures passwords as the user types them. It may start to share the user's desktop via VNC without the user's knowledge. It can start a background daemon that pops up ads. Linux adware!


Here's the most important part of the article as far as I (an admitted security non-expert) can tell.  It still seems like the kinds of things malware could do even once installed would be minor.  It can't install anything to the root filesystem or harm any vital piece.  Like was said, the base OS is not vulnerable to this.  And while personal data could be lost, I don't think some of the other things could happen.  I wasn't aware you could install Firefox Addons invisibly, or outside the application.  And you'll need to have VNC and your router configured to make remote desktop work.  Plus, isn't /tmp emptied every reboot?  So while annoying, couldn't you just reboot and have everything fixed?

In the end, this falls down to social engineering.  And if I am convincing someone to install malware on their computer, why not just package it as a deb and make it easy on myself?

---

### Post by jerome1232 on 2009-02-11
The title of this thread is soooo misleading it's not even funny.

Non of that had anything to do with a virus. It was all just tricking people into running a malicious program. No sh!t you can hurt any OS doing that...

---

### Post by NE Key on 2009-02-11
The author claims to have written a virus..

....However the user must first install the virus before it can run.

---

### Post by detroit/zero on 2009-02-11
This is just some spammer trying to drive traffic to his blog. If you look at other posts by OP, in his first page of 25 posts, I only counted three that didn't include a link to some blog or "news" site right in the first sentence.

Please don't feed the animals.

---

### Post by bailbath on 2009-02-11
Well it is worth telling newbies that they should not open attachments from emails most may know but some people are not so up on security. This article is pointing that out I guess in a round about way. Hopefully we all say to others you don't have to worry about virus on Linux but you can open a malicious email attachment and put it on your desktop and execute it.
Ian

---

### Post by Kinstonian on 2009-02-11
The reactions to the article seem a lot like the reactions of people talking about religion or politics.  Many people in the Linux world think that permissions will protect them from all malware, now there is proof that's not true, yet you dismiss the article.  Religion, politics, and now Linux. :(

---

### Post by hyper_ch on 2009-02-11
what proof? you can't protect people from their own stupidity...

---

### Post by detroit/zero on 2009-02-11
Can't protect us from spam, either, apparently.

---

### Post by Kinstonian on 2009-02-11
> **hyper_ch said:**
> what proof? you can't protect people from their own stupidity...

You can't dismiss every attack on Linux as user stupidity.  The article used more than just social engineering the user, he exploited vulnerabilities in Linux.  He demonstrated how to get attachments to execute, that you don't have to have root privileges to cause damage, and how you can get your code to run on reboots without the root account.  He proved that those common beliefs many Linux users have about Linux and malware are false.

---

### Post by cb951303 on 2009-02-11
Quote from wikipedia
> 
A computer virus is a computer program that can copy itself and infect a computer without the permission or knowledge of the user. The term "virus" is also commonly but erroneously used to refer to other types of malware, adware and spyware programs that do not have **the reproductive ability**.


I highlighted the keyword. Unless virus has root access, it can't infect executables. That's, all by it self, makes linux a lot safer (although not completely)

Also, the author doesn't describe a virus in his article. Just a malware script...

---

### Post by roshanjose on 2009-02-11
Wonder what many people have posted without going through the fundamentals of linux...

read the books...you'll find out

---

### Post by UbuKunubi on 2009-02-11
This sounds like FUD to me!
If there were ANY proof of this being workable it would be all over the professional news technology sites!

---

### Post by hyper_ch on 2009-02-11
> **Kinstonian said:**
> You can't dismiss every attack on Linux as user stupidity.  The article used more than just social engineering the user, he exploited vulnerabilities in Linux.
Not every attack but most...

and what he described is social engineering

(1) the user must download this script
(2) the user must place this script on his desktop
(3) the user must run then this script

You not notice the "the user must" part in that? That's social engineering.

---

### Post by Kinstonian on 2009-02-11
> **hyper_ch said:**
> Not every attack but most...

and what he described is social engineering

(1) the user must download this script
(2) the user must place this script on his desktop
(3) the user must run then this script

You not notice the "the user must" part in that? That's social engineering.

Yes, the user was **one** of the vulnerabilities exploited.  There are flaws in Linux that were exploited as well, which shouldn't just be ignored.  It's impossible to run a OS securely if you don't recognize its weaknesses.  The world won't end if you admit that Linux is vulnerable to malware. Come on, just between you and me, just admit it... I won't tell anyone!  :)

---

### Post by lykwydchykyn on 2009-02-11
It seems patently obvious to me that any system capable of running third-party code can be made to run malicious third-party code.  It's also obvious Linux and FOSS programs have security flaws, like every other OS and type of application.  Otherwise we wouldn't get security updates.

But reading the original article, all I come away with is that while it's possible to do malicious things to Linux users, there are more barriers than there are with the other OS, and the damage is confined to home directories.   At least, unless you are more clever than the author of this article.

I guess if you have grossly unrealistic expectations of Linux, this article might be a wake-up call.  I'm just left thinking, "so what?"

---

### Post by donkyhotay on 2009-02-11
By that token I can write a linux 'virus' that's only one line!
```
sudo rm -fr /
```
Obviously do *not* run the following code listed above as it will wipe your system. But save this as a text file and name it happypuppies.sh or something and then convince someone to run it. Obviously there is nothing malicious here because you named it happypuppies.sh even though it asks for your root password. The post from the OP is pretty much the same thing, sure it tries to be less obvious and technically launches something everytime the user logs on but without root access the worse it could do is delete your personal files. It can't spread, can't gain control of the system, or really do much of anything. A real linux virus would need to be started on boot regardless of whether or not a user even logged in or not. Getting something to place into all the runtime levels would do it but of course this requires root access and no system can protect against a user giving root access to programs he doesn't know.

---

### Post by UbuKunubi on 2009-02-11
@Kinstonian

RE: You can't dismiss every attack on Linux as user stupidity. The article used more than just social engineering the user, he exploited vulnerabilities in Linux.

I made no such statement of dismissal in my post!

---

### Post by bodhi.zazen on 2009-02-11
> **Kinstonian said:**
> Yes, the user was **one** of the vulnerabilities exploited.  There are flaws in Linux that were exploited as well, which shouldn't just be ignored.  It's impossible to run a OS securely if you don't recognize its weaknesses.  The world won't end if you admit that Linux is vulnerable to malware. Come on, just between you and me, just admit it... I won't tell anyone!  :)

First, no one has claimed Linux is invulnerable.

Second, what makes you think security is being ignored ? Security on Linux / Linux is very robust and so long as you remain with a "major" distribution security receives constant attention from the developers.

First we have an entire sub forum here devoted to security with several stickies introducing security. There are regular security updates for Ubuntu, certainly more frequent then Windows.

There is also this : [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I think this thread is "off topic" in that the term "virus" has been used indiscriminately. It seems to me that the problem is not that security is being ignored, but rather there is a fundamental misunderstanding of the terminology. While I encourage every Linux / Ubuntu user to learn security it is clear that the first step is education.

If you are interested in security please start with the sticky here on these forums. Also you should use proper terminology meaning you need to understand the difference between "social engineering" and "virus" as well as other exploits.

Once you understand the basics of security it will be "obvious" that the "virus" under discussion is in fact an example of "social engineering". From there the solution quickly follows and is again education of the end user.

---

### Post by Kinstonian on 2009-02-11
> **bodhi.zazen said:**
> First, no one has claimed Linux is invulnerable.

Second, what makes you think security is being ignored ? Security on Linux / Linux is very robust and so long as you remain with a "major" distribution security receives constant attention from the developers.

First we have an entire sub forum here devoted to security with several stickies introducing security. There are regular security updates for Ubuntu, certainly more frequent then Windows.

There is also this : [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I think this thread is "off topic" in that the term "virus" has been used indiscriminately. It seems to me that the problem is not that security is being ignored, but rather there is a fundamental misunderstanding of the terminology. While I encourage every Linux / Ubuntu user to learn security it is clear that the first step is education.

If you are interested in security please start with the sticky here on these forums. Also you should use proper terminology meaning you need to understand the difference between "social engineering" and "virus" as well as other exploits.

Once you understand the basics of security it will be "obvious" that the "virus" under discussion is in fact an example of "social engineering". From there the solution quickly follows and is again education of the end user.

It's posted nearly every day, in every AV thread here that you don't have to worry about malware if you use Linux.  For example I see things posted like "you could run any virus in Linux and it won't matter since the virus won't have the permissions to do anything"  That's simply not true.  As I've said before, and the article mentioned, you don't have to have root privileges to do bad things.

As far as ignoring security goes-- It seems to me, that at least in this thread, that that the points the article raised about security/linux/malware are being ignored.  I'm certainly aware that security is a big issue among the Ubuntu developers.

I also know the terminology, and to be honest, the attack in the article is clearly comprised of social engineering **and** malicous software (malware).  For example many mass mailing viruses/malware such as the I love you virus, use social engineering to get the user to run it, but it's clearly still a virus.

---

### Post by Therion on 2009-02-11
> **Kinstonian said:**
> It's posted nearly every day, in every AV thread here that you don't have to worry about malware if you use Linux.  For example I see things posted like "you could run any virus in Linux and it won't matter since the virus won't have the permissions to do anything"  That's simply not true.  As I've said before, and the article mentioned, you don't have to have root privileges to do bad things.

As far as ignoring security goes-- It seems to me, that at least in this thread, that that the points the article raised about security/linux/malware are being ignored.  I'm certainly aware that security is a big issue among the Ubuntu developers.

I also know the terminology, and to be honest, the attack in the article is clearly comprised of social engineering **and** malicous software (malware).  For example many mass mailing viruses/malware such as the I love you virus, use social engineering to get the user to run it, but it's clearly still a virus.
You seem to want to lump together the terms "virus" and "malware".  While all viruses are malware, not all malwares are viruses.  

Viruses, by definition, must be capable of self-replication without user interaction.  Malware is any software that does something undesired by the user.  NO computer, no operating system now or ever, will be safe from malware as long as they (the computer/OS) requires a human operator.  No system will ever be perfectly safe, Linux is safER by design; not impregnable.

People who state that Linux is immune from malware are simply misunderstanding.

---

### Post by JK3mp on 2009-02-11
I've never heard anyone say that Linux was invulnerable. Aside from this being a little social engineering trick. If it doesn't establish root on the system thats about all it can be classified with...a simple little social engineering "trick". Linux IS less vulnerable than Windows is the key phrase you hear alot. Not invulnerable. On windows my OS i get at least 50-150 virus alerts through my anti virus a day. (on a full day online and varying on what sites i visit etc.) On linux i get maybe 2-5...warnings..and i've even had days where iv'e gotten none!

---

### Post by Kinstonian on 2009-02-11
> **Therion said:**
> You seem to want to lump together the terms "virus" and "malware".  While all viruses are malware, not all malwares are viruses.  

Viruses, by definition, must be capable of self-replication without user interaction.  Malware is any software that does something undesired by the user.  NO computer, no operating system now or ever, will be safe from malware as long as they (the computer/OS) requires a human operator.  No system will ever be perfectly safe, Linux is safER by design; not impregnable.

People who state that Linux is immune from malware are simply misunderstanding.

Yeah, I know the difference between malware and viruses.  In fact, I've long thought that Anti-Virus software should be renamed to Anti-Malware software due to it protecting from many forms of malware.  I didn't mean for "viruses/malware" to be misleading.

I disagree with your definition of virus though.  A **worm** is what must be capable of spreading without user interaction.  All viruses must be executed by the user doing something such as clicking on something or attaching a storage device to their computer.

---

### Post by cb951303 on 2009-02-11
> **Therion said:**
> You seem to want to lump together the terms "virus" and "malware".  While all viruses are malware, not all malwares are viruses.  

Viruses, by definition, must be capable of self-replication without user interaction.  Malware is any software that does something undesired by the user.  NO computer, no operating system now or ever, will be safe from malware as long as they (the computer/OS) requires a human operator.  No system will ever be perfectly safe, Linux is safER by design; not impregnable.

People who state that Linux is immune from malware are simply misunderstanding.

+1

That's what I tried to underline in my post. The author of that article has no understanding of virus definition. Malware is inevitable because it  depends on user interaction.

---

### Post by JK3mp on 2009-02-11
> **bodhi.zazen said:**
> First, no one has claimed Linux is invulnerable.

Second, what makes you think security is being ignored ? Security on Linux / Linux is very robust and so long as you remain with a "major" distribution security receives constant attention from the developers.

First we have an entire sub forum here devoted to security with several stickies introducing security. There are regular security updates for Ubuntu, certainly more frequent then Windows.

There is also this : [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

I think this thread is "off topic" in that the term "virus" has been used indiscriminately. It seems to me that the problem is not that security is being ignored, but rather there is a fundamental misunderstanding of the terminology. While I encourage every Linux / Ubuntu user to learn security it is clear that the first step is education.

If you are interested in security please start with the sticky here on these forums. Also you should use proper terminology meaning you need to understand the difference between "social engineering" and "virus" as well as other exploits.

Once you understand the basics of security it will be "obvious" that the "virus" under discussion is in fact an example of "social engineering". From there the solution quickly follows and is again education of the end user.

Just read yours xD...well said. :)

---

### Post by Kinstonian on 2009-02-11
> **JK3mp said:**
> I've never heard anyone say that Linux was invulnerable. Aside from this being a little social engineering trick. If it doesn't establish root on the system thats about all it can be classified with...a simple little social engineering "trick". Linux IS less vulnerable than Windows is the key phrase you hear alot. Not invulnerable. On windows my OS i get at least 50-150 virus alerts through my anti virus a day. (on a full day online and varying on what sites i visit etc.) On linux i get maybe 2-5...warnings..and i've even had days where iv'e gotten none!

It's not just a little social engineering trick.  Say that when someone has your passwords.  That "trick" could also be modified to shovel a user shell to an attacker, attack other computers, send spam, propagate by sending to people in your address book, etc.  There's lots of things you can do without root access.

---

### Post by UbuKunubi on 2009-02-11
In my mind, despite reason and rationale being offered, this thread is simply attempting to spread FUD.

I say this because it is now obvious that the antagonistic method in which advice and knowledge is being ignored has now led to a debate about semantics.

---

### Post by Dr Small on 2009-02-11
> **UbuKunubi said:**
> In my mind, despite reason and rationale being offered, this thread is simply attempting to spread FUD.

I say this because it is now obvious that the antagonistic method in which advice and knowledge is being ignored has now led to a debate about semantics.
Don't worry. We have one of these threads at least once a month. It helps keep us on our toes and being able to defend our point. But next time, perhaps we should just refer the OP to one of the previous discussions on viruses/malware, linux isn't safe threads. :)

---

### Post by lykwydchykyn on 2009-02-11
No OS is immune to the *concept* of malware or the *concept* of a virus.  So if someone says "Linux is immune to viruses and malware" in that sense, they're wrong.  

OTOH, if you use the word to refer to the massive body of existing malware/virus/spyware code, then it is true to say Linux/BSD/OSX are immune because the vast majority of that code targets Windows.  In that sense, it's a semantic issue.

---

### Post by tbraun on 2009-02-11
> **donkyhotay said:**
> By that token I can write a linux 'virus' that's only one line!
```
sudo rm -fr /
```
Obviously do *not* run the following code listed above as it will wipe your system. But save this as a text file and name it happypuppies.sh or something and then convince someone to run it. Obviously there is nothing malicious here because you named it happypuppies.sh even though it asks for your root password. The post from the OP is pretty much the same thing, sure it tries to be less obvious and technically launches something everytime the user logs on but without root access the worse it could do is delete your personal files. It can't spread, can't gain control of the system, or really do much of anything. A real linux virus would need to be started on boot regardless of whether or not a user even logged in or not. Getting something to place into all the runtime levels would do it but of course this requires root access and no system can protect against a user giving root access to programs he doesn't know.

And how - pray tell - do you convince a non-technical user to run this script, if they have no idea how to run a script or even open a terminal? Please, wake up!

---

### Post by tbraun on 2009-02-11
Turns out the author of the original article has posted a [follow up]("http://www.geekzone.co.nz/foobar/6236"), in which he addresses many of the issues brought up here in this thread.

---

### Post by johnjohn2 on 2009-02-11
Personally i think this thread should be removed.

But saying that Windows has been on the BBC about security holes "Has This?"
It is the nature of the beast people will keep on finding ways around security that was built from the ground up!

---

### Post by bodhi.zazen on 2009-02-11
> **johnjohn2 said:**
> Personally i think this thread should be removed.

But saying that Windows has been on the BBC about security holes "Has This?"
It is the nature of the beast people will keep on finding ways around security that was built from the ground up!

Why ?

Our goals are to educate not stifle conversations. No one is requiring you to participate in the discussion.

The "problem" with this thread is that there are 3 "behaviors"

The first is a post form someone who is still learning the terminology and these people can learn from the conversation. Security on Linux is a new concept to many uses, both new and old.

The second behavior is that some experienced users have weighed in and posted some useful information.

The third behavior is somewhat less productive and borders on paranoid / trolling / bait and switch. The thread started with a discussion of a linux virus and how easy it is to make one. The original link is not a virus at all and is in fact malicious code and social engineering. The original author of the article, in his response, does not seem to me, and others who have some background in security, to be particularly informative. A simple google search on terms such as malware, virus, worm, and social engineering should set most people straight. I advise you obtain security information from a more knowledgeable source and again a simple google search will yield several security oriented sites in short order.

The conversation then turned to everything from passwords and other off topic issues as if password or escalation of privileges are somehow related.

The bottom line is that security should be of concern to users of all OS. With modern cracking techniques there is no such thing as "I am the only user on this computer" if the computer in question is connected to a network or internet.

If people are interested in learning linux security it is an onion. It has layers and it stinks. There is no substitute of taking an active role in learning security and even the most casual google search and reading reputable security tips from reputable sources will quickly show the fallacies on this thread.

Let that exercise be your first lesson in security - always confirm the information you are reading from reputable sources.

There are many tools that can be deployed, depending on the situation and paranoia level. Security must also be weighted against "usability" and each of us must make choices on how secure we feel we need to make things.

Simple things include appropriate passwords and goes all the way through encryption, learning to secure servers (if you install them), reading the logs, firewalls, HIDS, NIDS, and all the way to selinux/apparmor.

My advice is to just learn security, ignore the trolls. It should be obvious who needs assistance and who is trolling. Ask questions if you have them and ignore the trolls.

---

### Post by donkyhotay on 2009-02-11
> **tbraun said:**
> And how - pray tell - do you convince a non-technical user to run this script, if they have no idea how to run a script or even open a terminal? Please, wake up!

Umm... thats the point, you'd need to convince someone to set file as executable and then convince them to execute it. Yet in the example given you need to convince someone to download a launcher file and once again launch it. You have to convince the user to do something foolish like downloading from [www.ih4xb0xen.com](www.ih4xb0xen.com) or something. Yes the example given bypasses the executable flag and it might be a good idea to plug that potential exploit but ultimately it still requires social engineering to propagate. It doesn't matter how well you develop a piece of technology (whether it's software or something else), if a human does something stupid it's going to break.

---

### Post by init1 on 2009-02-11
> **hyper_ch said:**
> a user can also chose to dd the whole harddrive. what's there to stop him? without user intercation this will do nothing.
No, you need root privileges.

---

### Post by aysiu on 2009-02-11
I don't see why that blog author goes to such pains.

Really, if you want to make a trojan, just make it a .deb file for "cool" software. When the user double-clicks it, GDebi pops up and installs it for you. The user who has been tricked will, of course, enter her password and give the .deb file full root privileges.

That's how the recent pirated iWork / Photoshop trojans worked. As long as you're tricking users, why go small-fry?

P.S. I retitled the thread so people don't start freaking out.

---

### Post by cmat on 2009-02-11
Who the heck writes a virus in Python?

---

### Post by tbraun on 2009-02-11
> **aysiu said:**
> I don't see why that blog author goes to such pains.

Really, if you want to make a trojan, just make it a .deb file for "cool" software. When the user double-clicks it, GDebi pops up and installs it for you. The user who has been tricked will, of course, enter her password and give the .deb file full root privileges.

That's how the recent pirated iWork / Photoshop trojans worked. As long as you're tricking users, why go small-fry?



Except that in a properly administered enterprise the desktop users won't be in the sudoers file and thus cannot run a .deb installer. But they can still click on files they have saved to the desktop. I think we are talking about a much lower hurdle if sudo in any form is not needed for an infection.

---

### Post by cardinals_fan on 2009-02-11
> **cb951303 said:**
> Quote from wikipedia


I highlighted the keyword. Unless virus has root access, it can't infect executables. That's, all by it self, makes linux a lot safer (although not completely)

Also, the author doesn't describe a virus in his article. Just a malware script...
Frak and I have this argument all the time.  I agree with you, and believe that a virus must reproduce on its own.

It is worth noting that, if you accept this definition, true viruses are exceedingly rare on every operating system.
> **tbraun said:**
> Except that in a properly administered enterprise the desktop users won't be in the sudoers file and thus cannot run a .deb installer. But they can still click on files they have saved to the desktop. I think we are talking about a much lower hurdle if sudo in any form is not needed for an infection.
Properly administered enterprises are pretty hard to attack.  They also happen to be rather rare.

The vast majority of attacks on desktop users rely on Trojans and social engineering.  Incompetence, ignorance, and arrogance are bad on any OS.

For a better-written and clearer version of this, read [http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

---

### Post by UbuntuNerd on 2009-02-11
I found this link in the spanish forum and I think everyone should take a look at:[http://www.geekzone.co.nz/foobar/6229]("http://www.geekzone.co.nz/foobar/6229")
I thought it was very interesting

---

### Post by jerome1232 on 2009-02-11
> **cardinals_fan said:**
> 
For a better-written and clearer version of this, read [http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

I thought that was a good write up.

---

### Post by bapoumba on 2009-02-12
One thread merged.

---

### Post by jrusso2 on 2009-02-12
Thank god for merging this we are getting several a week now and everyone has to do the same argument over again each time.  That and KDE vs Gnome and Linux vs Windows are driving me mad.

---

### Post by bapoumba on 2009-02-12
> **jrusso2 said:**
> Thank god for merging this we are getting several a week now and everyone has to do the same argument over again each time.  That and KDE vs Gnome and Linux vs Windows are driving me mad.
Yeah. These are the Recurring Discussions ;)

---

### Post by OjM on 2009-02-12
> **tbraun said:**
> And how - pray tell - do you convince a non-technical user to run this script, if they have no idea how to run a script or even open a terminal? Please, wake up!

We were arguing about conficker with someone, and the topic of course changed to Linux virii, as it always does. He could not give me, nor could anyone there, any single virus that I could possibly get infected with my Linux-distribution. I used crunchbang then, but it is the same with Ubuntu.

Then he gave me a script. He gave me a script autorun.sh, with that <snip>. I wanted to test it, because I just could not believe my Linux system would be harmed by just sticking USB-drive in. Of course that is still not a virus, I know.

It did not work. I also tried to start the script from console, and it did not work. I tried it with sudo and when I tried to just <snip> (I did not care about having to reinstall to prove this), it said, well I'll just paste it here.

ojm@ubuhp:~$ <snip>
[sudo] password for ojm: 
rm: cannot remove root directory `/'
ojm@ubuhp:~$ 

So, Ubuntu at least makes it impossible to remove / and it's contents with that command. I don't know about debian or other distributions, but it seems to be in rm command itself judging by the response. I'm just irritated to always see that warning everywhere, so I tried it. Make yourself a virtual machine or something and try it yourself.

---

### Post by hyper_ch on 2009-02-12
well, it would be:

```

/*

```

---

### Post by OjM on 2009-02-12
> **hyper_ch said:**
> well, it would be:

```

/*

```

Umm, yeah that did so work and I lost my main installation. :P That's how I learn.

I saw it saying lots of cannot remove files, and stopped it, but it had managed to remove a lot of important things before that it seems. Was writing a "didn't work post", but my network didn't work and network-manager didn't know that. Then my background disappeared and lot of funny stuff happened. I'm running with live-cd now. Might try Lenny or something out next.

Do not try that with your main installation.

Does anyone here know why that kind of commmand works? I mean that does it have any useful function other than messing with others? It does not even remove everything.

---

### Post by bapoumba on 2009-02-12
> **OjM said:**
> 
Does anyone here know why that kind of commmand works? I mean that does it have any useful function other than messing with others? It does not even remove everything.
We are not very keen about providing this kind of information on an online help resource forum. There are many other places you can find this.

I'm closing and bringing that thread to the Staff's attention. You have not contributed anything to the forums but asking how a system can be borked.

---

### Post by jdong on 2009-02-12
I took a look over the thread and concur with the decision to close it. Everything productive to be commented about this blogpost has been commented. Namely:

(1) Yes, it is certainly possible to harm Linux users in profound ways both with regular user permissions or superuser access. Most of these attacks will require social engineering, as currently the number of unclosed arbitrary-execution-exploits is small. (Media players used to be a huge threat for this category of attacks but in my experience managing VLC the GCC stack protector has done a great job against these threats)

(2) However, as aysiu points out, it's fairly trivial to feed a user a .deb that carries out such an attack. Remember that debs can contain installation scripts that are executed with root access. In my experience few users except the extremely security-conscious ones will question the contents of a deb or refuse one found on some website / forum post if it gets in the way of having the latest and coolest shiny program.

(3) Virus is probably not the best term for this class of attacks; Malware is the better generic term. Viruses imply the ability to spread via otherwise-innocuous files transmitted from user to user, and "worm" implies the ability to automatically leverage remote exploits to gain entry without user intervention.

---

### Post by sad_iq on 2009-02-19
OK...I found this interesting blog this morning...any opinions??
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

---

### Post by BGFG on 2009-02-19
I think he attempts to, and makes a simple point. Linux is not bulletproof. His model still needs a good deal of user interaction/stupidity and i'm no programmer but it seems he makes a valid arguement.

Check this article also:
[http://www.geekzone.co.nz/foobar/6201](http://www.geekzone.co.nz/foobar/6201)

Seems to me he's an avid linux user and not a fanboy.

---

### Post by rzrgenesys187 on 2009-02-19
> **BGFG said:**
> I think he attempts to, and makes a simple point. Linux is not bulletproof. His model still needs a good deal of user interaction/stupidity and i'm no programmer but it seems he makes a valid arguement.

Check this article also:
[http://www.geekzone.co.nz/foobar/6201](http://www.geekzone.co.nz/foobar/6201)

Seems to me he's an avid linux user and not a fanboy.

It does, however the way he goes about getting the root password after the system is infected is pretty sly

---

### Post by swoll1980 on 2009-02-19
This is a trojan though. It doesn't matter what OS you use, if your dumb enough to install a virus on your own computer there is no hope for you.

---

### Post by dmizer on 2009-02-19
Closing this thread. More information here: [http://ubuntuforums.org/showthread.php?t=1066427&page=6](http://ubuntuforums.org/showthread.php?t=1066427&page=6)

---

### Post by Troll_the_Great on 2009-02-26
Hy all!

   I've been using linux for almost a year now, and I started to now my way around pretty well.I know (or I heard) that are very few linux viruses, and those few can't really harm you.A few days ago I found this article:
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)
and frankly, scared me a bit.Is it that simple to write a linux virus?I'm not as safe as I thought?
Any comments or opinions are welcome!

---

### Post by The Cog on 2009-02-26
That old chestnut.

If you send someone an attachment in an email and persuade them to save it and then execute it, it might do things they don't want it to. You ought to know that, and so ought most users.

---

### Post by Dougie187 on 2009-02-26
Keep in mind, that doesn't really detail the actually virus creation. It just says take some malware, and this is how to turn that malware into a virus. It is just as easy to create viruses on windows and mac's. It's not that you are not safe, you should always be cautious with what you click on. If you don't know someone, or don't trust them, you for sure shouldn't click on an attachment they send you.

In addition to this, not many linux viruses exist, mainly I think because the user base is so much smaller than with windows (and the smaller user base is typically more computer savy) so the viruses have a significantly smaller impact. If the user base ends up getting close to the size of windows we might see more viruses popping up, however if we see this happen, more virus scanning software for linux will most likely pop up as well.

---

### Post by Jesterday on 2009-02-26
If that scares you, then maybe, you shouldn't be using e-mail.

---

### Post by leonardo_neo on 2009-02-26
Thanks for sharing this info....

This guy has some valid points, which needs some considerations. I agree with most the points the author says.

---

### Post by Troll_the_Great on 2009-02-26
> **Jesterday said:**
> If that scares you, then maybe, you shouldn't be using e-mail.

Tkanks for the advice, it was really smart:mad:
I was just asking a simple question and I thought I'd receive valid answers...

---

### Post by mkvnmtr on 2009-02-26
You know those updates you get a couple of times a week that are security related? Every time someone finds a weakness they do an update to close it.

---

### Post by Kareeser on 2009-02-26
What, you agree that Linux has exploits? Of course it does.

What the article fails to convey fully is that the only reason that works is due to human stupidity.

Any OS can be cracked if the user is stupid enough. Don't worry about it.

---

### Post by Therion on 2009-02-26
There is no AV application that can take the place of the one between your ear's:  basic safe-computing habits.

---

### Post by Celegorm on 2009-02-27
To nitpick a bit, it's not a linux virus, it's a GNOME/KDE email trojan. Which means you have to both be running KDE or GNOME and be stupid enough to save a suspicious email attachment to the desktop and click on it (as opposed to merely reading the email).

---

### Post by Troll_the_Great on 2009-02-27
> **Celegorm said:**
> To nitpick a bit, it's not a linux virus, it's a GNOME/KDE email trojan.

So if I have X-face, I am more safe?

---

### Post by p_code on 2010-08-04
I have been a long time Linux user dating back to the kernel 0.8 days, and consider Linux to be a very useful tool in many applications, but I can't say that I am very impressed with desktop security in ANY  Linux distribution including Ubuntu.

The progress on drivers and desktop integration has been good (at the expense of software bloat), but it seems to me that security has only gotten worse, as "ease of use" has been placed ahead of security to woo users (which of course is EXACTLY the kind of stupidity that Microsoft is notorious for).

Someone earlier in the thread asked for a specific example, so ok here we go . . .

Imagine you are sent an attachment containing an apperently harmless text, pdf, or jpg file - then you double click on the file to open it, and find that your web browser cookie and password cache containing your bank account login has been sent to a site half way around the world (something you don't find out until weeks later when your identity is stolen and your account is emptied out).

If you want to see how this could happen, then just right click your desktop and create an empty text file, and paste in the following (don't worry this doesn't do anything malicious, it just pops a dialog to demonstrate that an unauthorized script could have been executed by clicking on an apparently harmless icon)  -

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=WhoCares
GenericName=WhoKnows
Comment=Not Malware - But COULD BE!
Exec=xmessage "BOO! this could have been a virus!"
Icon=text-editor.png
Type=Application
Name[en_US]=You_Must_B_Kidding.txt

```Save the file as something like " a_test.desktop " , and then open a xterm console window, cd to your 'Desktop' directory, and

```
chmod a+x a_test.desktop


```
This second step is necessary because Ubuntu at least makes a half-assed effort to prevent this attack by forcing the execute permission bit to be enabled for desktop launcher files (which is more that some other distributions do), but sadly, as you will see, this will not help in most cases, because it's quite easy to get around.

The reason this is not enough to prevent this attack is that nearly all Linux content is archived for transmission on the web, and when Ubuntu unzips a TAR archive, it helpfully PRESERVES THE EXECUTE PERMISSIONS on all the files.

So, in the scenario I outlined above it would be quite easy for someone to make sure that you get the malicious .desktop launcher file in an archive with the 'execute' bit already set.  Then you would just have to untar the file to  your desktop (or any other folder) from your browser or email  program and then double click the icon and that would be that.

In the above example, the launcher masquerades as a simple text file, but instead launches a xmessage dialog with a message.   The point is that the xmessage dialog could have just as easily been a malicious script.  

In Ubuntu, once ANY script is run (even without root privileges), you are basically SCREWED because Ubuntu by default LACKS ANY OUTGOING FIREWALL PROTECTION WHATSOEVER, so a malicious script can very easily open a FTP session and send your personal information to anywhere on the planet!

Thanks to a very effective firewall, and addon HIPS software, this attack  is nearly impossible to pull off on any of my Windows machines (including  Win98!), but is trivially easy on Ubuntu.

As someone has already pointed out, this is why it's critically important to set a really strong 'Master Password' in Firefox, but since 99% of Ubuntu Firefox users (as well as Windowz Firefox users) think that the program is taking care of security for them, almost no one bothers!!!

So, all they would have to do is to click on a simple harmless 'text file' and next thing you know their bank account is empty - NICE!  ):P

---

### Post by rookcifer on 2010-08-05
> **p_code said:**
> I have been a long time Linux user dating back to the kernel 0.8 days, and consider Linux to be a very useful tool in many applications, but I can't say that I am very impressed with desktop security in ANY  Linux distribution including Ubuntu.

The progress on drivers and desktop integration has been good (at the expense of software bloat), but it seems to me that security has only gotten worse, as "ease of use" has been placed ahead of security to woo users (which of course is EXACTLY the kind of stupidity that Microsoft is notorious for).

Someone earlier in the thread asked for a specific example, so ok here we go . . .

Imagine you are sent an attachment containing an apperently harmless text, pdf, or jpg file - then you double click on the file to open it, and find that your web browser cookie and password cache containing your bank account login has been sent to a site half way around the world (something you don't find out until weeks later when your identity is stolen and your account is emptied out).

If you want to see how this could happen, then just right click your desktop and create an empty text file, and paste in the following (don't worry this doesn't do anything malicious, it just pops a dialog to demonstrate that an unauthorized script could have been executed by clicking on an apparently harmless icon)  -

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=WhoCares
GenericName=WhoKnows
Comment=Not Malware - But COULD BE!
Exec=xmessage "BOO! this could have been a virus!"
Icon=text-editor.png
Type=Application
Name[en_US]=You_Must_B_Kidding.txt

```Save the file as something like " a_test.desktop " , and then open a xterm console window, cd to your 'Desktop' directory, and

 thing you know their bank account is empty - NICE!  ):P

Firefox *does* encrypt passwords, even if a master password is not in use.  When you click "show passwords" within Firefox settings it decrypts the passwords before showing them.  Whether a script can access this is another story.  Why don't you write a POC script that does this?

Modern versions of KDE provide a warning prompt when a .desktop file is clicked (does Gnome?).  And who is going to click an image file that has an accompanying script packed along with it? A .desktop file is merely a front-end for a script (an icon for a script).  The extension is obviously not that of an image or a .pdf.  This would tip most people off.

Besides, who caches their bank passwords?  I know some (most?) bank sites do not even allow the password to be cached in the browser.

Again, write the POC code that steals FF passwords so that we can send it to Mozilla for a fix.  Post the code here or send it to me privately.  I'll be waiting..

---

### Post by aysiu on 2010-08-05
I've merged this with the other thread on the same topic. Social engineering can be successful on any platform, as long as the user is gullible enough.

---

