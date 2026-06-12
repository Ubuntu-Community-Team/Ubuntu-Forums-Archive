---
title: "Ubuntu keeps crashing"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-11
Hi,

Since today, Ubuntu keeps crashing (has crashed about 5 times today so far).

When it crashes I can move the mouse, but when I click on anything, nothing happens.
Ctrl Alt Backspace does nothing, so I have to do Ctrl Alt SysRq and then do REISUB.

How can I find out what is causing the crash, as I'm trying to do work, but keep being interrupted by the computer crashing.

Thanks

---

### Post by dwally89 on 2008-05-11
Any ideas anyone?

---

### Post by daschl on 2008-05-11
and when does it crash? at random times or do you perform specific tasks?

---

### Post by SunnyRabbiera on 2008-05-11
hmm, well what are you doing at the times of these crashes?
I know hardy has been reported to be a stability issue, but lets see what you are doing.

---

### Post by dwally89 on 2008-05-11
I've had openoffice, adobe reader, amsn, and firefox open at the time.

I think it it related to either openoffice or adobe reader, because for about the past hour or so I've not had openoffice or adobe reader open and its not crashed.

However I've tried using both openoffice 2.4 and 3beta, and the official adobe reader and the one that comes with ubuntu, and it crashes with both of them, so I'm not sure if its related to them or not

Thanks

---

### Post by linuxisfree on 2008-05-11
> **dwally89 said:**
> I've had openoffice, adobe reader, amsn, and firefox open at the time.

I think it it related to either openoffice or adobe reader, because for about the past hour or so I've not had openoffice or adobe reader open and its not crashed.

However I've tried using both openoffice 2.4 and 3beta, and the official adobe reader and the one that comes with ubuntu, and it crashes with both of them, so I'm not sure if its related to them or not

Thanks

Ok, from what i see you're opening all those programs at the same time, right? Try opening them, then, 1 at a time and see at which program it crashes. Hope that'll help pinpoint the problem.

---

### Post by xeth_delta on 2008-05-11
Just an idea. It might worth seeing if anything wrong is being reported in "/var/log/messages".

---

### Post by SunnyRabbiera on 2008-05-11
what about firefox, are you using flash?
Firefox 3 might be your issue too, FF3 was repsonsible for crashing me out five times so I downgraded to firefox 2.

---

### Post by dwally89 on 2008-05-11
I think its to do with openoffice or adobe, as my computer was running fine for an hour and a half, and I just opened openoffice and adobe, and within minutes the computer crashed.

Could it be to do with the actual pdf itself?

---

### Post by SunnyRabbiera on 2008-05-11
Unknown, but it can be an issue with openoffice as well.
do you use quickstart for open office?
also I still want to know if you are browsing flash pages with firefox 3 when  this happens.

---

### Post by dwally89 on 2008-05-11
I just start openoffice by clicking on OpenOffice.org Word Processor.

The websites I'm viewing at the time are the ubuntu forums, gmail, and facebook, and I don't think any of them use flash.

---

### Post by SunnyRabbiera on 2008-05-11
alright, you your issue must be adobe reader....
did you try envince to open up your pdfs?

---

### Post by dwally89 on 2008-05-11
I've tried using the default ubuntu reader (not sure what it's called) to open up the PDF, and I've also used the official adobe reader, and it crashes with both of them.

Could it be the PDF itself?

---

### Post by SunnyRabbiera on 2008-05-11
its possible, where did you get this pdf from?

---

### Post by dwally89 on 2008-05-11
Its from [www.aqa.org.uk](www.aqa.org.uk)

---

### Post by dwally89 on 2008-05-11
OK, I tried it with another PDF, and it still crashed.

Could the problem be openoffice then perhaps?

---

### Post by SunnyRabbiera on 2008-05-11
well could be, do you have openoffice loaded when you do this?
like I said do you have open office to start up when you log in?

---

### Post by dwally89 on 2008-05-11
Openoffice is loaded when it crashes, and I have not set openoffice to start up when I login.

---

### Post by SunnyRabbiera on 2008-05-11
then dont load openoffice and see what happens, this is hard to pinpoint.

---

### Post by dwally89 on 2008-05-11
I just loaded openoffice word processor, and in a blank document I started typing, and after about 10 seconds it crashed, so the problem is definitely to do with openoffice.

Any ideas on what the problem is?

---

### Post by sunstriker on 2008-05-11
Maybe try reinstalling it...

---

### Post by dwally89 on 2008-05-14
OK after a few days I have come to the conclusion that OpenOffice.org Word Processor is causing my system to crash, as I can run the Spreadsheet and other openoffice programs without my system crashing.

I've tried doing a complete reinstall of openoffice, but the word processor still crashes after less than 2 minutes of usage.

I do not want to use another office suit, so how can this problem be fixed?

Thanks

---

### Post by xeth_delta on 2008-05-14
> **dwally89 said:**
> OK after a few days I have come to the conclusion that OpenOffice.org Word Processor is causing my system to crash, as I can run the Spreadsheet and other openoffice programs without my system crashing.

I've tried doing a complete reinstall of openoffice, but the word processor still crashes after less than 2 minutes of usage.

I do not want to use another office suit, so how can this problem be fixed?

Thanks

I don't know if anyone has already sugested this (didn't find it in the thread), but you could start the program in a terminal and see what messages are shown after the crash. I suppose there would be some output regarding the crash:

```
ooffice -writer
```

---

### Post by dwally89 on 2008-05-15
OK heres the latest.

I reinstalled Ubuntu today (using an official CD), leaving my home partition intact.
I then started open office word processor, and again, within a few minutes, it crashed.
Someone recommended to me to delete the .openoffice.org2 folder in my home directory, so I did it, but its still crashing.

Does anyone else know wot to do?

Just to clarify, I've:
1. Reinstalled Ubuntu
2. Deleted my .openoffice.org2 folder

Thanks

---

