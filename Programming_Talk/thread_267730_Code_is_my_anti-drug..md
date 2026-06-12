---
title: "Code is my anti-drug."
date: 2006-09-29
forum: Programming Talk
---

### Post by Levdir on 2006-09-29
Hey folks.

I find that I spend wholly too much time in front of my computer. I want to remedy this. My idea is as follows: a script to lock my system up entirely on weekend dates, and to disable my network connection after 1 AM. How might I go about this? I was thinking something to force a logout and generate a random password, then change it back early Monday mornings.

Does something like this exist already? If not, what would I need to do to make it?

I am a programming novice, with only limited experience in C++, but I'm alway eager to learn something new. Any help would be appreciated.

---

### Post by po0f on 2006-09-29
Levdir,

Why oh why would you want to do such a thing?  Before you know it, you'll be going outside, maybe talking to people...  ;)

This task is probably best suited for a combination of scripts and cron jobs though.

---

### Post by nereid on 2006-09-29
Maybe you would like to try the leave command (you have to install it first)?

---

### Post by Levdir on 2006-09-29
I'll look into it. Thanks. :)

EDIT: I just looked up Leave with Synaptic, and while it would be useful, I'd like to force myself to get the hell off my computer once in a while. I'd like something I can't outright ignore ;)

---

### Post by nereid on 2006-09-30
You could write a script which will start the shutdown command after leave sends its message.

---

### Post by Note360 on 2006-09-30
wouldn't something like 

gksudo leave

or

gksudo shutdown now

be sufficient, for now atleast. It will prompt you for your password in a giant menu that blocks the whole screen and then shutdown or do whatever leave does. Put it on a cron job and it should work.

---

