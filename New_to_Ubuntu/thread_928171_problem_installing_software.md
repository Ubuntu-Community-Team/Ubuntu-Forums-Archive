---
title: "problem installing software"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by carl321 on 2008-09-23
Hi i am a linux newbie and i have come across a problem installing software. I keep getting the following (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.) Please help me understand this..:(
thanks..

---

### Post by oilchangeguy on 2008-09-23
open a terminal (command line) and type sudo dpkg --configure -a and press enter.

---

### Post by hyper_ch on 2008-09-23
well, have a read at what that error message says... I mean it's not that complicated...

---

### Post by oilchangeguy on 2008-09-23
> **hyper_ch said:**
> well, have a read at what that error message says... I mean it's not that complicated...

now there's no reason to be an a** hole. does it say anywhere in the error message to add sudo to the command? think before you speak.

---

### Post by lisati on 2008-09-23
> **oilchangeguy said:**
> open a terminal (command line) and type ```
sudo dpkg --configure -a
``` and press enter.
+1: You'll be asked for a password. Don't worry if it doesn't show (this is a normal Ubuntu security precaution), just use the same one you use for your normal login.

---

### Post by carl321 on 2008-09-23
Thank oilchangeguy works fine. As for the smart **** as i said i am a total beginner at linux so try taking a leaf out of oilchangeguys book.
Thanks again..:)

---

### Post by hyper_ch on 2008-09-24
> **oilchangeguy said:**
> now there's no reason to be an a** hole. does it say anywhere in the error message to add sudo to the command? think before you speak.

(1) watch your language and keep this forum friendly

(2) if he did what the error message said, then he would have gotten another one and could have asked about that

(3) do you think before you speak?

---

### Post by overdrank on 2008-09-24
Hi and to all, please remember the COC and be polite in responding. If you do not think you can then please do not respond. :)
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
Also watch the language. :KS

---

### Post by Paqman on 2008-09-24
To be fair, we get this question so often in this forum that i'm inclined to think that error message should be filed as a bug.

---

### Post by hyper_ch on 2008-09-24
paqman:

If he had run the command given by the error message then he would have encountered another problem and maybe asked for a solution for that one here.

The problem is not with the error message itself but that people are not willing to read what the error message tells them.

---

### Post by Paqman on 2008-09-24
> **hyper_ch said:**
> 
The problem is not with the error message itself

I disagree. First of all, it's not the correct command, and not prefixing it with sudo doesn't generate an error message that tells the user to do so explicitly. This is easy to fix, and so it should be done.

Second of all, why should the user have to copy a command from an error message and paste it into a terminal? The user contributes nothing, they're just shifting bits around. That's a process that is crying out for automation if you ask me.

---

### Post by t0p on 2008-09-24
> **hyper_ch said:**
> paqman:

If he had run the command given by the error message then he would have encountered another problem and maybe asked for a solution for that one here.

The problem is not with the error message itself but that people are not willing to read what the error message tells them.

I disagree.  The error message certainly *is* a problem.

Every day, new users are confronted with that error message.  It tells them to run **dpkg --configure -a**. They run that command, get another error, and come here for help.  Every day!  If the error message said **run sudo dpkg --configure -a**, fewer people would have this problem.

You can repeat what you already said twice about "if he had run the blah blah"... but that doesn't change the fact that every day new users have this problem, just cos the error message doesn't mention sudo!

---

### Post by hyper_ch on 2008-09-24
> **Paqman said:**
> I disagree. First of all, it's not the correct command
It is the right command... installing software is limited to users with root rights. So there's nothing wrong with the command itself - only that you are lacking the rights to run it ;)

> **Paqman said:**
> and not prefixing it with sudo doesn't generate an error message that tells the user to do so explicitly. This is easy to fix, and so it should be done.
```

hyper@xubi:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
hyper@xubi:~$

```
You call that a meaningless error message? It tells you exactly what must be done.

> **Paqman said:**
> Second of all, why should the user have to copy a command from an error message and paste it into a terminal? The user contributes nothing, they're just shifting bits around. That's a process that is crying out for automation if you ask me.
The error gives just one possible option of what might be wrong... in most cases that will solve the issue but not in all ;) so by having the user enter it into the terminal and if it doesn't work then he will have more data to solve the problem.


> **t0p said:**
> Every day, new users are confronted with that error message.  It tells them to run **dpkg --configure -a**. They run that command, get another error, and come here for help.  Every day!  If the error message said **run sudo dpkg --configure -a**, fewer people would have this problem.
Hmmm, I can recall hundreds of threads from users just posting that error message... but I can't recall any posts by new users coming to the forum and stating, that they just run **dpkg --configure -a** and still nothing works. Problem is not the error message, problem is that people aren't bothered to read them.

---

### Post by Paqman on 2008-09-25
> **hyper_ch said:**
> It is the right command... installing software is limited to users with root rights. So there's nothing wrong with the command itself - only that you are lacking the rights to run it ;)

The command doesn't even do anything, therefore it's wrong and pointless. Splitting hairs doesn't help the newbie who can't understand what's going on.

> 
```

hyper@xubi:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
hyper@xubi:~$

```
You call that a meaningless error message? It tells you exactly what must be done.

Yes, it's an extremely poor error message. How is the user supposed to know the "requires superuser privilege" means "you should prefix this command with sudo"? Any error message which uses jargon or assumes prior knowledge on the part of the user is a bad error message.
Writing useful error messages is important, and something not all geeks are  good at.

> 
The error gives just one possible option of what might be wrong... in most cases that will solve the issue but not in all ;) so by having the user enter it into the terminal and if it doesn't work then he will have more data to solve the problem.


I think it would be much better to automatically run sudo dpkg --configure -a, then if that doesn't work, provide a button to view the terminal output. Technically feasible, automated, and useful for users at all skill levels.

Clearly, the current situation is unsatisfactory. Just count how many threads we get about this.

---

### Post by nickgaydos on 2008-09-25
sudo dpkg --configure -a usually works but sometimes dosen't, there is this one website that fixed it for me once, it is definitly on Google. But if you do come across it, it will have a rm command to remove your locks or something of the sort.

---

### Post by hyper_ch on 2008-09-25
> **Paqman said:**
> The command doesn't even do anything,
The command does exactely what it's supposed to do ;) and actually the error message it also correctly... you don't run synaptic/adept/... in non-root mode ;)

> **Paqman said:**
> Yes, it's an extremely poor error message.
It's not... it's straight to the point as of why it's not working.

> **Paqman said:**
> How is the user supposed to know the "requires superuser privilege" means "you should prefix this command with sudo"? Any error message which uses jargon or assumes prior knowledge on the part of the user is a bad error message.
So you credit the user as totally stupid and not be able to do anything - then I wonder how such a user managed to install linux... at least I accredit a bit of intelligence to any user ;)
You could also say "how is a user supposed to know what "did you google it" means? It's also jargon. Or here in the forums what a pm is... you have jargon everywhere ;)

> **Paqman said:**
> Writing useful error messages is important, and something not all geeks are  good at.
Those error messages are straight to the point of what's wrong... unlike that one here:
[IMG]http://www.dashboardwidgets.com/showcase/data/57/BSOD-0p6b.png[/IMG]

> **Paqman said:**
> Clearly, the current situation is unsatisfactory. Just count how many threads we get about this.
We wouldn't have so many threads if people just wouldn't be lazy do a little research before posting.

---

### Post by Paqman on 2008-09-25
> **hyper_ch said:**
> 
So you credit the user as totally stupid and not be able to do anything - then I wonder how such a user managed to install linux... at least I accredit a bit of intelligence to any user ;)


Desktop operating systems should (IMO) be usable by anybody, regardless of their geek factor. You shouldn't have to be able to install Linux to use Linux. My girlfriend is a Linux user, and i'm pretty sure that error message (or indeed anything that pointed her in the direction of the command line) would stump her. She's not stupid, far from it, she's just not that interested in technology.

Ubuntu as a distro aims to be usable by everybody, which is an excellent goal. There will always be distros available for people who like to feel smug about how 1337 their OS is. They can have as many cryptic, unhelpful error messages as they like.

As for the BSOD: I don't see your point. Just because the error message is better than the worst possible example, doesn't mean it's actually any good.

> 
We wouldn't have so many threads if people just wouldn't be lazy do a little research before posting. 


A simple change to the text of the error message would be an even better solution though, don't you think? It's hardly difficult.

Better yet, Ubuntu would handle this common error elegantly, and the user wouldn't have to intervene at all. I don't see why you'd argue against this being better than the status quo?

---

### Post by hyper_ch on 2008-09-25
> **Paqman said:**
> Desktop operating systems should (IMO) be usable by anybody,
Then there is no single OS that satisfies your opinion ;)

> **Paqman said:**
> regardless of their geek factor.
How much geekness is required to have the abilty to read "run ..."... close to none ;)

> **Paqman said:**
> You shouldn't have to be able to install Linux to use Linux.
Re-read what I said ;)


> **Paqman said:**
> she's just not that interested in technology.
Yet you conclude that she wouldn't be able to comprehend...


> **Paqman said:**
> They can have as many cryptic, unhelpful error messages as they like.
What is cryptic about "Run 'dpkg --configure -a'"? It's not cryptic, it's straight forward... you're told what to do ;)

> **Paqman said:**
> As for the BSOD: I don't see your point. Just because the error message is better than the worst possible example, doesn't mean it's actually any good.
One tells you what to do and it works and the other one doesn't... I'll let you guess which one's which.

> **Paqman said:**
> A simple change to the text of the error message would be an even better solution though, don't you think?
Nope, the error message would then be erroneous ;) you can't run synaptic as non-root and hence that error message is to 100% accurate.

> **Paqman said:**
> I don't see why you'd argue against this being better than the status quo?
See above ;)

---

### Post by Paqman on 2008-09-25
Look, we can argue about this all you like, but the bottom line is that users ARE confused by the current error message, and need to come here to get an answer.

They're not stupid, and once given the right information they can and do sort the problem out themselves. I just think it'd be nice if our lovely operating system could dish out this information itself and save us all the hassle.

I'm an engineer by trade. Wasteful processes that could be easily streamlined bug me. :)

---

### Post by hyper_ch on 2008-09-25
> **Paqman said:**
> Look, we can argue about this all you like,
Yet the message is still to 100% correct

> **Paqman said:**
> but the bottom line is that users ARE confused by the current error message, and need to come here to get an answer.
They aren't confused by the error message, they just aren't bothered to read it - spoon-feed mentality.

> **Paqman said:**
> They're not stupid, and once given the right information they can and do sort the problem out themselves.
They are given the right information.

---

### Post by billgoldberg on 2008-09-25
This error gets posted around 10 times a day.

I think apt should automatically try to run the command after the error.

It would help a lot of users.

cypher_ch:

I agree the error message is useful for people who know at least the minimum of Ubuntu/linux.

For newcomers (this is the ABT) that error means nothing.

---

### Post by hyper_ch on 2008-09-25
billgoldberg:

You don't even have to comprehend the error message but just do what it says ;) Now if that is asked too much then .... ;)

Let's face it: x years of experience with Windows indoctrinated people that they can't possibly understand what's going on so they don't even try to read simple, straight-forward error message.

---

### Post by billgoldberg on 2008-09-25
> **hyper_ch said:**
> billgoldberg:

You don't even have to comprehend the error message but just do what it says ;) Now if that is asked too much then .... ;)

Well, I can imagine there are people who have no idea how to "run" something.

:p

But yes, most people don't even read the error message. They just presume they are going to need help.

---

### Post by hotrod6657 on 2008-09-25
not to play devil's advocate here or anything but i feel like maybe if everyone wants to continue debating this that you should start your own topic somewhere else in the forum...

It's not very encouraging for newcomers to Linux to be greeted with this sort of bickering when all they did was ask a simple question.  And it's not going to help win anyone over who just happens to stumble upon this thread while looking through the "Absolute Beginner Talk" section of the forum.

If seeing this question posted so much angers you then just don't comment on it, someone else who doesn't mind helping out someone new to Linux will surely take care of it.

As far as i'm concerned, end of discussion, start a new thread if you want and link to it here for all those interested, but please don't taint carl321's first forum experience with this petty debate.

carl321, if you're even still reading this thread, I hope you enjoy Linux and please try and not let this little episode speak poorly for the whole Linux Community.

I've said what i feel needed to be said,

hotrod

---

### Post by krede21 on 2008-09-25
Sorry for posting in more than one thread, but this is a real pain in the a**

I actually did type:

```
dpkg --configure -a
```

and I got this response:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
mv: cannot stat `/boot/initrd.img-2.6.24-19-generic.new': No such file or directory
dpkg: underproces post-installation script returnerede afslutningsstatus 1
root@John:/home/christian#


underproces post-installation script returnerede afslutningsstatus 1

means something like:

"subprocess post-installation script returned finishing-status 1".

What's my problem? And most important, how do I solve it?

---

### Post by Paqman on 2008-09-25
> **hyper_ch said:**
> Yet the message is still to 100% correct


Well, you're entitled to your opinion, but [it's already been filed as a bug](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/124443) in Launchpad so it may well be changed at some point. Given the low priority on that bug i'm not holding my breath.

---

### Post by hyper_ch on 2008-09-25
> **billgoldberg said:**
> But yes, most people don't even read the error message. They just presume they are going to need help.

That's true... like a chinese proverb says:
> 
Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime.


Make the people to help themselves.

---

### Post by hyper_ch on 2008-09-25
@ Krede

Better to start an own thread with that. You got a far bigger problem with the initramfs generation.

Besides, you should not be logged in as root.

---

### Post by krede21 on 2008-09-25
> **hyper_ch said:**
> @ Krede


Besides, you should not be logged in as root.

Why not?

Because of my noob-ness? ;-)

---

### Post by hyper_ch on 2008-09-25
krede21:

have a little read here... not exact the answer but it'll give you some impressions: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by krede21 on 2008-09-25
Can't really see the difference between that and what I said ;-)

---

