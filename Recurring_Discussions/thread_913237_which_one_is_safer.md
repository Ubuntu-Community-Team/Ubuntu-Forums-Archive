---
title: "which one is safer ?"
date: 2008-09-07
forum: Recurring Discussions
---

### Post by lundish on 2008-09-07
hi there,
I'm wondering which OS is safer on average  ? 
Is it Ubuntu 8.4 with latest updates and that would be all or is XP with a standard anti virus (avg or sth) and firewall ?

PC will be used only for skype, instant messages, e-mails and , most important, usage of bank account.

---

### Post by aysiu on 2008-09-07
> **lundish said:**
> hi there,
I'm wondering which OS is safer on average  ? 
Is it Ubuntu 8.4 with latest updates and that would be all or is XP with a standard anti virus (avg or sth) and firewall ?

PC will be used only for skype, instant messages, e-mails and , most important, usage of bank account.
Ubuntu, definitely, for several reasons:

1. There is more active malware for Windows XP in "the wild."

2. Antivirus isn't an effective guard against malware.

3. Windows XP runs as administrator by default

---

### Post by fiddledd on 2008-09-07
If, as you say, your main concern is on line banking, then you may be asking the wrong question. Or at least, not all the right questions.

Your main concern should probably be Phishing, and the protection from that depends on what browser you use.

EDIT: Yes I know Key Loggers are also a concern.:)

---

### Post by SunnyRabbiera on 2008-09-07
Ubuntu by like a million miles.

---

### Post by Vivaldi Gloria on 2008-09-07
> **lundish said:**
> hi there,
I'm wondering which OS is safer on average  ? 
Is it Ubuntu 8.4 with latest updates and that would be all or is XP with a standard anti virus (avg or sth) and firewall ?

PC will be used only for skype, instant messages, e-mails and , most important, usage of bank account.

Ubuntu is much more secure but also I always use a seperate browser for my bank account. (In my case ff for all web and epiphany for bank only). This will decrease the chance of phishing, browser hijacking, persistent cookies etc. Don't use that browser for something else.

---

### Post by LaRoza on 2008-09-07
> **lundish said:**
> hi there,
I'm wondering which OS is safer on average  ? 
Is it Ubuntu 8.4 with latest updates and that would be all or is XP with a standard anti virus (avg or sth) and firewall ?

PC will be used only for skype, instant messages, e-mails and , most important, usage of bank account.

XP is a malware magnet by design. (Connecting XP to the internet with no firewall results in malware being automatically downloaded in less than 5 minutes, open and listening ports...)

For XP, anti-virus is a waste of CPU cycles and RAM. All infections I have seen took place when the person had anti-virus.

Have a firewall, and use a limited account. Use a browser other than IE.

---

### Post by Giant Speck on 2008-09-07
I believe the question is too vague.

You can't really compare two operating systems by asking a vague question to compare them, especially not on a forum that is full of users of one of the choices.  It tends to open up a can of biased worms.

---

### Post by LaRoza on 2008-09-07
> **Giant Speck said:**
> I believe the question is too vague.

You can't really compare two operating systems by asking a vague question to compare them, especially not on a forum that is full of users of one of the choices.  It tends to open up a can of biased worms.

No, I think in this respect one can.

Do a fresh install of Ubuntu on machine, one of XP on another. Connect them to the internet (with no firewalls) and wait.

In less than 10 minutes, you'll find Ubuntu is more safer.

No biases there.

In XP and Ubuntu, make a script that has some shell/batch command that would delete all files, give it an appropriate extensions (.sh/.bat) and double click on it. In Ubuntu, it will open in a text editor. If executed, it would do nothing because of permissions. Windows is only too happy to hide the file extension and execute it.

---

### Post by Giant Speck on 2008-09-07
> **LaRoza said:**
> No, I think in this respect one can.

Do a fresh install of Ubuntu on machine, one of XP on another. Connect them to the internet (with no firewalls) and wait.

In less than 10 minutes, you'll find Ubuntu is more safer.

No biases there.

In XP and Ubuntu, make a script that has some shell/batch command that would delete all files, give it an appropriate extensions (.sh/.bat) and double click on it. In Ubuntu, it will open in a text editor. If executed, it would do nothing because of permissions. Windows is only too happy to hide the file extension and execute it.

Yes, but that makes an assumption that the user is someone who is not computer-literate, like your grandmother, or your eight-year-old child.  It assumes that the user doesn't know what they are doing.

Therefore, if the question was specifically worded "Which one is safer for a new computer user?", then the answer would probably be Ubuntu.

However, a more experienced computer user would know the dangers of unsafe internet browsing and double-clicking on files, so the question "Which is safer?" wouldn't really have an answer because the experienced user wouldn't bundle the world security with any operating system.  If the user knows what they are doing, any OS can be safe.

---

### Post by LaRoza on 2008-09-07
> **Giant Speck said:**
> 
However, a more experienced computer user would know the dangers of unsafe internet browsing and double-clicking on files, so the question "Which is safer?" wouldn't really have an answer because the experienced user wouldn't bundle the world security with any operating system.  If the user knows what they are doing, any OS can be safe.

Windows doesn't support the advanced permissions of the Unix's. It isn't transparent (you never know what is doing what really, which is how it is so easily exploited). Even the best security practices are shaky when Windows is connected to a network.

---

### Post by aysiu on 2008-09-07
> **LaRoza said:**
> Windows doesn't support the advanced permissions of the Unix's. Not natively. SuRun is a great program, because it can set up permissions like the *sudo* in Ubuntu and Mac OS X for Windows XP.

---

### Post by cardinals_fan on 2008-09-07
> **aysiu said:**
> Not natively. SuRun is a great program, because it can set up permissions like the *sudo* in Ubuntu and Mac OS X for Windows XP.
Precisely.  Using it at this very moment, in fact :)

---

### Post by lundish on 2008-09-08
yes, phishing  and widely understood indentity theft seem to be the biggest problem and for that no OS can prevent :(

---

### Post by LaRoza on 2008-09-08
> **aysiu said:**
> Not natively. SuRun is a great program, because it can set up permissions like the *sudo* in Ubuntu and Mac OS X for Windows XP.

That's a start, however, I was referring to more basic permissions. In Windows, it extremely simple and dangerous. Nothing like chmod at all. Executing files is done solely on file extension. Very dangerous.

---

### Post by cmat on 2008-09-08
Linux uses magic numbers to determine file type. This was really impressive when I started Ubuntu some few years ago. You wouldn't believe how many files I found that are like .mp3.exe on client systems. 

People aren't stupid, if seeing a 3 letter extension will prevent their system from getting hosed then why not show them by default?

---

### Post by LaRoza on 2008-09-08
> **cmat said:**
> 
People aren't stupid, if seeing a 3 letter extension will prevent their system from getting hosed then why not show them by default?

Especially when you have things like: funnypenguin.jpg.vbs

There should be no option to hide parts of a file name, especially the part which determines if it is executable or not!

---

### Post by Vivaldi Gloria on 2008-09-08
> **LaRoza said:**
> Executing files is done solely on file extension. Very dangerous.

And there are things like [[COLOR="YellowGreen"]scrap files[/COLOR]]("http://www.misec.net/papers/scrapfiles/").

---

### Post by fiddledd on 2008-09-08
> **Vivaldi Gloria said:**
> And there are things like [[COLOR="YellowGreen"]scrap files[/COLOR]]("http://www.misec.net/papers/scrapfiles/").

Judging by the gfx on that page, that's an old article. I doubt it's relevant to XP or Vista.

But I'll happily be proved wrong.

---

### Post by Vivaldi Gloria on 2008-09-08
> **fiddledd said:**
> Judging by the gfx on that page, that's an old article. I doubt it's relevant to XP or Vista.

But I'll happily be proved wrong.

It was for windows 2000 and XP. I doubt it would work for vista. The point is "the file extension was automatically hidden from the user by Windows no matter what the Explorer settings" you use in XP. You need a registry hack to make those extensions visible.

---

