---
title: "Input on Filesystem Protector"
date: 2011-12-26
forum: Programming Talk
---

### Post by dodle on 2011-12-26
Here's a little background: Just over the past month and a half my mom's Windows computer was demolished by a virus and my dad's personal information was compromised by scammers planting a virus on his machine. Convincing them to switch to a Unix based system will prove difficult. It's driving me crazy and unfortunately Microsoft has left them and their XP machines in the dust as it now focuses on securing Windows 7 and Vista.

So here is the proposed solution that I have come up with: A program that runs on the system at startup (a daemon I guess it's called) and monitors attempted changes in the system and specified directories. When a program or process attempts to make a change to a file, a prompt is displayed with information about the change and asks for a master password to allow it.

Sysinternals has a program called [Process Monitor](http://technet.microsoft.com/en-us/sysinternals/bb896645) but I'm not sure that it does what I want. Maybe I'll test it out on my XP system when I get a chance.

So does this solution that I've come up with sound possible? Does anybody have any input on how I should begin, links to some resources, or with what language I should write it? I have some experience with Python and C++. One obstacle might be allowing a single process to make multiple changes as it would be very annoying to have to input a password 187 times just to install a program and its files.

---

### Post by ofnuts on 2011-12-26
> **dodle said:**
> Here's a little background: Just over the past month and a half my mom's Windows computer was demolished by a virus and my dad's personal information was compromised by scammers planting a virus on his machine. Convincing them to switch to a Unix based system will prove difficult. It's driving me crazy and unfortunately Microsoft has left them and their XP machines in the dust as it now focuses on securing Windows 7 and Vista.

So here is the proposed solution that I have come up with: A program that runs on the system at startup (a daemon I guess it's called) and monitors attempted changes in the system and specified directories. When a program or process attempts to make a change to a file, a prompt is displayed with information about the change and asks for a master password to allow it.

Sysinternals has a program called [Process Monitor]("http://technet.microsoft.com/en-us/sysinternals/bb896645") but I'm not sure that it does what I want. Maybe I'll test it out on my XP system when I get a chance.

So does this solution that I've come up with sound possible? Does anybody have any input on how I should begin, links to some resources, or with what language I should write it? I have some experience with Python and C++. One obstacle might be allowing a single process to make multiple changes as it would be very annoying to have to input a password 187 times just to install a program and its files.Such things are unworkable... how do you recognize that the program is a vrius and not, for instance, Firefox writing in its cache? And if you want good Windows system advice, you aren't exactly in the right forums. There are forums with a better ratio of Windows experts among users :)

This said, there are free and paying security suites for Windows that work decently and that will give your parents' systems a better protection than whatever you'll code up yourself. And you would better teach your parents some good internet habits and give them a good solution for backups.

---

### Post by dodle on 2011-12-26
> **ofnuts said:**
> ...how do you recognize that the program is a vrius and not, for instance, Firefox writing in its cache? ...

Yeah, I thought about that. It would be difficult. I guess the only way to do it would be to have a list of permissible processes. I'm going to look for some free tools, but if I can't find anything that works the way I want it to I will attempt to research and write something up. Seriously, Windows' security sucks.

---

