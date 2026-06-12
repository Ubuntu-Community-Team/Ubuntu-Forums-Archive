---
title: "Ex-XP User wants to build mail robot"
date: 2007-07-16
forum: Programming Talk
---

### Post by Slippy Lane on 2007-07-16
Hi, I have recently migrated to Ubuntu linux from WinXP. My programming knowledge (mostly VB, TurboPascal, VBscript) doesn't port well, and to be honest, I don't even know which LANGUAGE would be best for my project. I have a smattering of Javascript knowledge - enough to know it isn't what I want.

Essentially, what I want to do is create a single app that runs on my local machine, constantly checking for new mail on a POP3 server using SSL. On receiving new mail, the app then needs to extract details (from, to, subject) from the header, and check the content of the message body against a list of defined keywords and actions.
The app then does a bit of string processing and looking up information either in a local file or in a spreadsheet hosted at google spreadsheets, and creates a response email (dependant on the data it finds), which it then needs to send to an SMTP server (also using SSL).

The bit in the middle, I can handle. String processing isn't much different from one language to the next. Accessing google spreadsheets shouldn't be too hard either, as Google has API's and plenty of samples available.

What I really need help with is communicating with POP3/SMTP using SSL, and of course, figuring out which language is gonna be easiest for me to pick up, given what I want to do with it. I'm not bothered about a development environment, or creating a user interface - I want it eventually to run on a linux console-mode box.

If SSL would be a real problem for someone of my limited skills, I can always have the mail forwarded to another POP account that doesn't require SSL, so that's not such an issue.

I've tried searching numerous resources but I can't make head nor tail of what I've been able to find thus far. If anyone out there can give me a few nudges in the right direction, I'd be eternally grateful.

---

### Post by AlexThomson_NZ on 2007-07-16
Well my first intinct would be to use Perl, there are lots of well documented perl modules that deal with that sort of thing (SSL, etc), and will be able to handle your string processing very easily.  It's pretty easy to pick up too, so has my vote.

---

