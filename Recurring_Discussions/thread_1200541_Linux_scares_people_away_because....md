---
title: "Linux scares people away because..."
date: 2009-06-30
forum: Recurring Discussions
---

### Post by xouns on 2009-06-30
I used the Live-CD yesterday to enable my brother to boot to linux, because he had a virus on his XP (stupid boy, it's the third (!) time this year) and I told him he could back-up his music using Ubuntu before re-formatting.

While running the live-CD, an error was printed saying something the like of "bad cluster [number] on device sr-0" and this error came up alot, like 60 or more times. Device errors scare the crap out of everything. Some quick forum-browsing learned me it's probably a broken CD or smudged lens (which was true, cleaning the CD did the trick), but my dad had already opened the computer and was removing the hard-drive to replace it with a new one (true story, 'tis...). "Clusters, that's the hard drive, isn't it?".

So, my idea, in order to make Ubuntu a user-friendly, low-effort distro, can't you make these errors less informative, though evenly helpfull? Like adding that the sr-0 is probably the CD/DVD drive? Or make it say "There seems to be a problem with the disk, please reboot and run the "Check CD for errors""/ "Clean the disk, please". Or make them look less technical? 

**Since Ubuntu is trying to gain grip on the naive user ** (read people-who-use-Windows-because-they-don't-know-any-better), **these errors only add to the "Linux is for Nerds and Geeks"-reasoning. **

People already have to learn that the C: drive is now called hd(0,1) and it is quite confusing for new users (like myself). And I understand that long time users will be on there hind legs for this, it's a bad thing to reduce the information in error messages, but for new users, it doesn't add. And I for one see Ubuntu as a step-in-model-Linux, a get-to-learn-Linux distro.

Any ideas?

---

### Post by 4th guy on 2009-06-30
You can try adding this to [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

---

### Post by Paqman on 2009-06-30
Error messages written in impenetrable jargon is a bit of a problem for all software and OSes, not just Linux. 

However, Linux has the advantage that if you find one, it's easy to feedback to the devs about how much their error message sucks. Get yourself a Launchpad account and file it as a bug. You might be pleasantly surprised by the response.

---

### Post by jespdj on 2009-06-30
Have you ever seen a blue screen in Windows? It's also full of technical terms and hexadecimal numbers that a non-technical person can't understand. So it's not just Linux that has these kinds of error messages.

Long ago I tried OS/2 Warp on my computer, and all I got was a black screen with some strange code in the top left, something like "SYS0203". No further information on the screen. After a lot of searching, I found out that it meant that I had no mouse connected to the computer.

But OK, the fact that it happens in other OSes as well is not an excuse to let Ubuntu be user-unfriendly. I agree that some error messages could be improved upon. But I don't agree that this is a major reason why Linux scares people.

---

### Post by lisati on 2009-06-30
> **jespdj said:**
> Long ago I tried OS/2 Warp on my computer, and all I got was a black screen with some strange code in the top left, something like "SYS0203". No further information on the screen. After a lot of searching, I found out that it meant that I had no mouse connected to the computer.
Speaking of OS/2, I once saw an ATM that was having a bad day: it seemed to be stuck in a cycle of booting OS/2, crashing, and restarting itself. Not much help to anyone who wanted to use it to get some money.....

---

### Post by swoll1980 on 2009-06-30
Yeah, I don't think I've ever seen an error message that I understood. A CD does have clusters on it though. The cool part about Linux though, like some one else said, file a bug report. Maybe they'll change it.

---

### Post by caravel on 2009-06-30
Error messages can be googled and the source of the problem usually can be found.  Generic output like "there has been a problem" is pretty useless.

---

### Post by Odemia on 2009-06-30
> **caravel said:**
> Error messages can be googled and the source of the problem usually can be found.  Generic output like "there has been a problem" is pretty useless.

I for one like the detailed error messages, and the ability to run apps from the cli with and without the debuging symbols for even more verbose output, and I have to agree that generic outputs are useless.  If it had said "there is a problem with the disk (or boot volume)", would your dad have understood that it meant the cd?  Unforetunately decrypting the error messages often involves context and it can be really hard if not impossible for a dev to gather enough context and transform it into common english.  Not to mention very time consuming.

At the same time, I agree with the original post that throughing technical jargon at people is also not great.  I guess my point is generic=bad for solving the problem, current error messages=bad/scary for non-techies so why not balance them in a way that tells people who don't understand where they can find help.

Why not have:

[LIST=1]
[*]generic message, like "there has been a problem with one of your drives")
[*]a button to show the detailed cli version
[*](this is the crucial part) a message suggesting the user search for the cli error message in an online database/forum.
[/LIST]
I think this type of message might have actually prevent people from ripping out harddrives unnessecarily.  And shouldn't be too much work for devs :).  Or maybe I am just being hopeful, anyone see any issues with my suggestion?  If not I think I will take it to launchpad.

---

### Post by Dr Small on 2009-06-30
Who doesn't know that /dev/sr0 is your CD-ROM drive?

---

### Post by xouns on 2009-06-30
> **Dr Small said:**
> Who doesn't know that /dev/sr0 is your CD-ROM drive?
Naive users (new users) don't, which is part of the reason I posted this. Linux knows, why should I know what the system calls my DVD-drive. It's the DVD-drive, not sr-0. 

But I am specifically pointing at the installation and boot procedure errors here. Any beef on that?

*Edit: Wrong interpretation of quote, fixed*

---

### Post by automaton26 on 2009-06-30
Try explaining to someone who has never used Windows that "see colon" means the "hard drive"...my grandmother thought I had gone peculiar   :)

But seriously I agree - the *user-domain* name should always be used as a preference, with the *technical-domain* name as an optional extra, certainly throughout a desktop environment.

---

### Post by Swagman on 2009-06-30
I always knew drive definitions as 

Drive Floppy 0: (Zero)

Drive Hard 0:  

Which was later amended to Hard Drive 0: and CD0:

But for some strange reason the floppy remained as DF0:

Guess the platform !!

---

### Post by waspbr on 2009-06-30
Whenever I get a message that says something that I don't understand I google some of the keyworlds. I have yet to get an error message that I cannot figure out with google.

---

### Post by steveneddy on 2009-06-30
.... because the average Windows user doesn't know much at all about PC's in general.

Most people are like sheep and as soon as they see anything different they panic.

Unless they welcome change, like younger people for instance, then they will probably be very reluctant to change operating systems unless:

1. They have a spare machine to play with

2. They have someone to hold their hand

3. They become very bored or frustrated with Windows and want to discover something different without shelling out $$$ for a new (or used) Mac (the original reason I came to Linux)

---

### Post by Yamamaro on 2009-07-01
Just make another CD

---

### Post by 3rdalbum on 2009-07-01
I have to half-agree with this one. There are cases where the kernel already has user-friendly error messages that are still useful for debugging. It probably isn't going to add an awful lot to the workload of the subsystem maintainers either.

Making these changes to prevent users from throwing away their hard disks is a bit extreme. And I don't think the error messages are actually deterring anyone from using Linux. User-friendly error messages are a good idea because they can give suggestions for the user to follow BEFORE they file a bug report. It's also more reassuring to see an error message that you can understand, rather than one that you can't. And if you do a Google search for an error message, you're likely to come across all sorts of uninformed suggestions for fixing the problem, some of which might make the problem worse. Wouldn't it be cool to be able to get suggestions straight from the kernel developers?

While Windows kernel panic messages are not user-friendly either, we're not trying to emulate Windows. We're trying to make an excellent operating system, not a mediocre one.

We can be a little more user-friendly. Although, submitting the idea to Ubuntu Brainstorm is unlikely to be of much use as Ubuntu doesn't submit many patches to the kernel. If you could submit it to a distribution that has kernel developers, it's more likely to be looked at. You might want to try submitting it to Fedora or OpenSuse, but don't say that your Dad is using Ubuntu and don't say that he was about to toss out the hard disk :-)

---

### Post by madjr on 2009-07-01
OP

excellent idea

have you thought of adding this to the ubuntu "papercut" list?


[http://www.linuxloop.com/news/2009/06/28/ubuntus-papercuts-usability-in-little-things/](http://www.linuxloop.com/news/2009/06/28/ubuntus-papercuts-usability-in-little-things/)

u still have time :)

---

