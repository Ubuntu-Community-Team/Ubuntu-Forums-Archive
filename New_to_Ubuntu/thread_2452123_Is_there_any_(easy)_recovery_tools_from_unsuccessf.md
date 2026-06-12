---
title: "Is there any (easy) recovery tools from unsuccessful upgrade"
date: 2020-10-17
forum: New to Ubuntu
---

### Post by Odense on 2020-10-17
I wanted to upgrade my Ubuntu to the latest LTS (Ubuntu 18.04.5 LTS > Ubuntu 20.04.1 LTS) but first got a warning that I would have to remove some ppa's


After I removed the kazam ppa the update was able to start - but stopped again after a while. I rebooted and tried again and it stopped again.
After another reboot get to the gnome classic desktop I prefer but it does not react to the keyboard, the mousepad or the USB mouse I normally use so I cannot even log on.

Can I get these things to work again or should I abandon hope?

---

### Post by CelticWarrior on 2020-10-17
Do you have backups, don't you? If not you can boot a live session and save the personal files somewhere else.
Then install from scratch.

---

### Post by Impavidus on 2020-10-17
The easiest recovery after a failed upgrade is a fresh install.

---

### Post by T6&amp;sfpER35% on 2020-10-17
i upgraded awhile ago to 20.04.1 without any problems,also had kazam ppa installed ,so not sure why you get errors.
i didn't get errors so unfortunately i don't know what to say lol

but , probably what he said 
> [COLOR=#000000]The easiest recovery after a failed upgrade is a fresh install.[/COLOR]

---

### Post by Odense on 2020-10-17
> **Impavidus said:**
> The easiest recovery after a failed upgrade is a fresh install.

So that is an area where Ubuntu is seriously behind Windows.
And yes - naturally it is my own fault for not having enough back-ups.

---

### Post by CelticWarrior on 2020-10-17
> **Odense said:**
> So that is an area where Ubuntu is seriously behind Windows.

This is a joke, right?
Any major Linux distro is far more robust than Windows in that regard.
But nothing is immune to user errors and insufficient knowledge about proper system maintenance.

---

### Post by CelticWarrior on 2020-10-17
> **3nd said:**
> yea windows force upgrade your pc whenever it wants and then hold thumbs it doesn't brick your pc
:lolflag:

Exactly! =d>

---

### Post by Odense on 2020-10-17
> **CelticWarrior said:**
> This is a joke, right?
Any major Linux distro is far more robust than Windows in that regard.
But nothing is immune to user errors and insufficient knowledge about proper system maintenance.

No - it is not a joke.
And naturally anything can ruined by the users. But I only used Ubuntu's own upgrade tools and I might need to format that partition without even getting my own data out. 
I am still a newbie since I don't WANT to have to understand the OS - neither Linux nor Windows. But I have used PC's for 30 years now.
In spite of this I have never had Windows "brick a PC" or "scramble" a partition like this. And (without having tested them myself) I know there are/have been several repair options for a defective Windows OS. Apparently there are none of these for Ubuntu.

I will continue to use Ubuntu - but I am running out of arguments for why others should too.

---

### Post by T6&amp;sfpER35% on 2020-10-17
might look into [this](https://ostechnix.com/how-to-fix-broken-ubuntu-os-without-reinstalling-it/)

good luck mate

---

### Post by CelticWarrior on 2020-10-17
Recapitulating...
This all started because *you* decided to do a release upgrade that wasn't urgent, 18.04 is supported until 2023!
That failed for reason we may discuss latter on this post without consequences - no changes have been made at that point -. Then the error message about "ppa-purge" - by the way, a red herring - led you into your current problem because you insisted in upgrading a broken system before actually correcting it. The main problem were those PPAs that you added, most for no reason. At least one - you know which one as it was already mentioned in another thread - broke the update process the moment after it was added. So, before anything else, you should have removed ALL broken PPAs and make sure 18.04 was fully updated BEFORE trying again the release upgrade.
Then the unusual problem of "no mouse, no keyboard" as a direct consequence of an interrupted release upgrade is unheard of. That must be related with something else you did, i.e., another mistake pilling on the aforementioned long list of mistakes.

> [COLOR=#000000]I don't WANT to have to understand the OS[/COLOR]
And yet here you are because you don't have backups and screwed up advanced OS operations, regardless of the OS family, let that be unequivocally clear.
If you don't want to acquire the basic knowledge to do such things with minimal safety options, why don't you pay someone who's job is to do just that?

---

### Post by Odense on 2020-10-17
> **3nd said:**
> might look into [this]("https://ostechnix.com/how-to-fix-broken-ubuntu-os-without-reinstalling-it/")

good luck mate

Thank you 3nd,

But at that page I read: "[COLOR=#313131][FONT=&quot]At the login screen, press [/FONT][/COLOR][COLOR=#313131][FONT=&quot]CTRL+ALT+F1[/FONT][/COLOR][COLOR=#313131][FONT=&quot] to switch to [/FONT][/COLOR][COLOR=#313131][FONT=&quot]tty1[/FONT][/COLOR][COLOR=#313131][FONT=&quot]. You can learn more about switching between TTYs [/FONT][/COLOR][here]("https://ostechnix.com/how-to-switch-between-ttys-without-using-function-keys-in-linux/")[COLOR=#313131][FONT=&quot]."

And unfortunately when I reach the login screen the computer does not react to any input devices - including the keyboard.[/FONT][/COLOR]

---

### Post by T6&amp;sfpER35% on 2020-10-17
> [COLOR=#313131]does not react to any input devices - including the keyboard.[/COLOR]
oh yah , yes ...
highly recommend you make an ISO image for 20.04 ([here]("http://www.releases.ubuntu.com/20.04/ubuntu-20.04.1-desktop-amd64.iso")) somehow ,and start from scratch

PS. i feel sorry for you cause i'm also a newbie and never had any issues with anything ,upgrading,installing stuff or whatever

also ,i see so many users here having troubles with dual booting/ dual OS's , i just decided stuff windows , and did a linux only install. never had any probz\\:D/

---

### Post by crip720 on 2020-10-17
You don't say if this is a laptop or desktop, thinking laptop.  There is a bug in kernels from 5.4.0-44 and up that seems to disable laptop keyboards/touchpads.  USB/wireless units should work, but you say your USB mouse does not.  This has been reported mainly on Acer and HP laptops.  There is a work around for it.

---

### Post by ActionParsnip on 2020-10-17
How did you kick off the upgrade? What steps did you take?

---

### Post by Impavidus on 2020-10-17
> **Odense said:**
> No - it is not a joke.
And naturally anything can ruined by the users. But I only used Ubuntu's own upgrade tools and I might need to format that partition without even getting my own data out. As long as your filesystem is in a somewhat decent condition, it's trivial to get your files out. Just use the live disk, which allows you to access your hard drive.
> I am still a newbie since I don't WANT to have to understand the OS - neither Linux nor Windows.You don't have to understand every technical detail of Linux to use it. Nobody knows everything. And when I first used Ubuntu in 2006 I knew far less than now. I think I did a few stupid things back then, although I never broke my system. It was upgraded from 6.06 to 8.04 to 10.04 to 12.04 to 14.04 (IIRC), when small-scale damage all over the place and obsolete but hard-to-track packages had slowed it down and I did a fresh install of 16.04. But using Linux (in particular if you're the admin) does require a bit more technical knowledge than using Windows. Linux gives you more freedom and it takes some knowledge to use that freedom.
> But I have used PC's for 30 years now.
In spite of this I have never had Windows "brick a PC" or "scramble" a partition like this. And (without having tested them myself) I know there are/have been several repair options for a defective Windows OS. Apparently there are none of these for Ubuntu.

I will continue to use Ubuntu - but I am running out of arguments for why others should too.
The upgrade broke because something happened that the developers hadn't foreseen or had dismissed as too unlikely. That's always the case when something breaks that wasn't supposed to break, Linux, Windows or the Tacoma Narrows Bridge. Whenever something breaks, you may loose entropy. That is, there are multiple starting conditions that lead to the same mess, which makes it maybe theoretically but definitely practically impossible to reconstruct the starting conditions from the mess. And as nobody cared enough to prevent the mess, obviously nobody will build something that can fix it. So all repair tools do basically the same thing. They wipe whatever is broken and replace it with something that's known to work. The same in Linux, you just wipe the entire OS and replace it with a new OS. This can be done without loosing user data and in about 30 minutes, so what else do you need?

---

### Post by Odense on 2020-10-18
I certainly made several mistakes.
I decided to do a fresh install which worked until I tested Windows 10.
After tested Windows 10 the Ubuntu partition does no longer load the kernel but ends with grub >
But I will continue that problem in another thread.

---

### Post by Frank P on 2020-10-19
> **CelticWarrior said:**
> Recapitulating...
This all started because *you* decided to do a release upgrade that wasn't urgent, 18.04 is supported until 2023!
That failed for reason we may discuss latter on this post without consequences - no changes have been made at that point -. Then the error message about "ppa-purge" - by the way, a red herring - led you into your current problem because you insisted in upgrading a broken system before actually correcting it. The main problem were those PPAs that you added, most for no reason. At least one - you know which one as it was already mentioned in another thread - broke the update process the moment after it was added. So, before anything else, you should have removed ALL broken PPAs and make sure 18.04 was fully updated BEFORE trying again the release upgrade.
Then the unusual problem of "no mouse, no keyboard" as a direct consequence of an interrupted release upgrade is unheard of. That must be related with something else you did, i.e., another mistake pilling on the aforementioned long list of mistakes.


And yet here you are because you don't have backups and screwed up advanced OS operations, regardless of the OS family, let that be unequivocally clear.
If you don't want to acquire the basic knowledge to do such things with minimal safety options, why don't you pay someone who's job is to do just that?

I've read thru this thread and feel I have to comment. I'm in the middle of fixing an update from 16.04lts to 18.04lts which completely broke my system. I don't have any ppas and have installed every update as the came up. Yet it broke over a huge number unmet dependencies. Tried all the recommended fixes and then gave up. The "clean" install still has problems; see latest question in General Help re change log. All my bash scripts are also broken but I'm working on them

I would gladly pay someone who could answer questions, recommend, or remotely fix, some of the problems. Can you recommend someone?

Thanks

Frank

---

### Post by Frank P on 2020-10-19
update:
Shutdown; rebooted; logged in. Didn't change anything. After giving the message  every time I logged in (via ssh) yesterday, the message no longer appears
There's way to much of that kind of thing
Frank

---

### Post by rsteinmetz70112 on 2020-10-20
I've done dozens of upgrades over the years and never had one fail completely. I've always been able to eventually solve the problems, but it can be a complicated process. I've recently had Windows 10 upgrade completely corrupt one computer to the point of having to reset it (microsoft for reinstall).

---

### Post by col48 on 2020-10-23
I never upgrade, only clean install.  And always (so far) have a working system.  Why?  How?

Why?
Because there have been many threads about upgrades that have either broken something or have failed, and every such case will be unique in some way - either the old system has unique features or the user has made unique mistakes.  Because I can easily misunderstand how-to instructions.  Because I'm paranoid?  Because I have no backup hardware to use to search for online help if I get in a mess.

How?
Some years ago, with careful and brilliant help from user oldfred on this forum, I partitioned my hard drive and set up dual booting, with two (now three) Ubuntu LTS.  It acts a bit like a grandfather-father-son backup system.  So I can wipe the grandfather partition and install a fresh grandson there without affecting the viable father and son systems.  It isn't foolproof - nothing involving human beings is - but it works for me.

No Windows in sight, other than the one which lets me see the garden!

---

