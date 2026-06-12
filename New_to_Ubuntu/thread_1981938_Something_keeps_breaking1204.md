---
title: "Something keeps breaking1204"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by thorbs on 2012-05-17
I have had problems since changing to 12.04. It happened in lubuntu and I got so tired of it I changed to xubuntu, but it is the same. 

Here thought I get the message that it is a systemfile that keeps breaking. 

Any help or thoughts?

---

### Post by Lisiano on 2012-05-17
Would help if you tell us exactly what the text says.

---

### Post by thorbs on 2012-05-21
Well the exact text is in danish, so I do not know if you can use it. 

But i basically get to errors,

one saying that ubuntu has experienced an internal error 

and the other sayin that a specific program has to close.

But the frequency seems to be less lately, so maybe something has been fixed in the latest updates.

---

### Post by mlentink on 2012-05-21
Hi thorbs,

Please try and translate the error messages as they would help us help you. I for one got frequent messages at startup about bluetooth. This is a known issue, so if you get those, you can tick the box that says something about not being notified of such a bug again. 
But it could be something else that could help the devs hunt down what causes the bug. So if at alle possible, says yes to notifying the developers about it and ask for a report, so you can see what gets transmitted.

---

### Post by Lisiano on 2012-05-21
You can temporarily switch Ubuntu to English and copy paste the errors here, this will provide the most accurate translation. To do that, go to System Settings -> Language Support -> Drag English to the top. Then re-log. To revert it, just drag English to whatever spot it was before.

---

### Post by thorbs on 2012-05-22
Ok, I have changed language and will comeback with the exact.

But the error message says in translation.

We regret that Ubuntu has experiend an internal error.

If you keep exeriencing problem you can restart the computer.

---

### Post by thorbs on 2012-05-27
The error message reads:

"Sorry, Ubuntu 12.04 has experineced an internal error. If you experience further problems, try restarting the commputer"

This is the error that keeps comming, however not as frequent as in the start when it was several times every session.

---

### Post by Shadius on 2012-05-27
> **thorbs said:**
> The error message reads:

"Sorry, Ubuntu 12.04 has experineced an internal error. If you experience further problems, try restarting the commputer"

This is the error that keeps comming, however not as frequent as in the start when it was several times every session.

It appears to be a bug. I made a thread about it and was told it was a bug.

[http://ubuntuforums.org/showthread.php?t=1984537](http://ubuntuforums.org/showthread.php?t=1984537)

---

### Post by JOHNNYG713 on 2012-05-27
Uninstall apport and whoopsie

---

### Post by thorbs on 2012-05-27
what is apport?

---

### Post by The Cog on 2012-05-27
This is the description in synaptic:> apport automatically collects data from crashed processes and compiles a
problem report in /var/crash/. This utilizes the crashdump helper hook
provided by the Ubuntu kernel.

This package also provides a command line frontend for browsing and
handling the crash reports. For desktops, you should consider installing
the GTK+ or Qt user interface (apport-gtk or apport-kde).

---

### Post by JOHNNYG713 on 2012-05-27
apport and whoopsie are crash reporters, I have uninstalled them and my 12.04 runs fine, no errors, steady and stable !

---

### Post by bennypr0fane on 2012-05-27
> **JOHNNYG713 said:**
> apport and whoopsie are crash reporters, I have uninstalled them and my 12.04 runs fine, no errors, steady and stable !

I seem to have pretty much the same problem.
So what, we just kill the messenger? What about the actual problems that are being reported?

---

### Post by mlentink on 2012-05-27
Apport allows you to gather info about the crash before it sends out a report. This info can tell you what is crashing and sometimes when and how. 
Personally, I would not 'shoot the messenger' but try to find out why the message was sent in the first place.

---

### Post by xedi on 2012-05-27
If you don't experience any problems except notifications that something crashed, I would just ignore these reports.

---

### Post by bennypr0fane on 2012-05-27
> **mlentink said:**
> Apport allows you to gather info about the crash before it sends out a report. This info can tell you what is crashing and sometimes when and how. 
Personally, I would not 'shoot the messenger' but try to find out why the message was sent in the first place.
How do I find out?
I can't post the error reports in here, because they can't be copied, and are way too long to just retype them. I could look at the filepath at the top of the report, but it always seems to be sth. different...
Any suggestions what to look out for specifically?

---

### Post by JOHNNYG713 on 2012-05-28
for some reason 12.04 sees closing an app as a crash. this is not a system failure but  a false positive ! dont sweat it! unless your system starts killing your pets and becomes a menace to public welfare ! Chill out ! its all good ! you dont really want to chase your tail now do ya ! its just a bug, so yes at this point I would advise, kill the messenger ! and enjoy  your system !

---

### Post by mlentink on 2012-05-28
You can find crash reports in /var/crash/

For more info on apport, please see here: [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

