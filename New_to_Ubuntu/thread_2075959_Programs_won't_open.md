---
title: "Programs won't open"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by Airycat on 2012-10-25
Everyone tells me that Linux doesn't get viruses, but I'm not sure my computer knows that. 

I have version 12.04 and have never had so many problems since Windows 98!! Programs that were working fine before, don't work at all now. 

I simply got rid of the weather notification. It was not particularly necessary since I have a window to the outside and can see what the weather is.

Today, however, I need my scanner and ... NADA! The one that came with Ubuntu simply closes before it opens. My HP (yes, I have reinstalled the hplip) doesn't even show up. It gives me the option to close, but I can't choose to scan. The printer works as long as I'm using the "Print" function of the browser or other program. I can't access it directly.

Offhand, I can't think of specific problems... except GIMP is always closing after a save, which is merely annoying unless I forgot to save as .xcf before another format.

I'm also constantly getting crash messages. I click on the report button, but then I get a message that it doesn't know what crashed (or caused the crash). 

I update regularly, although I have to do this manually now because it's not doing it automatically any more (past week or so). I HAVE NOT changed any settings.  Like I said, it looks like major virus problems to me. I'm backing up all my important files and plan to do a clean reinstallation. I hope I remember how to get the things I need to work so they are functional again. I may go to wubi so I can get the non-linux programs to finally work, too. Then I can run an antivirus if I need to (of course, I will in Windows!).

Anyone have any better advice?

---

### Post by 2F4U on 2012-10-25
> I'm also constantly getting crash messages. I click on the report  button, but then I get a message that it doesn't know what crashed (or  caused the crash). 

These crash reports are not necessarily an indication for a virus or a real problem. In my experience, the crash reporter is just too sensitive. As long as the crashes are not accompanied by real problems you can ignore them. If they get on your nerves, as they did get on mine, edit /etc/default/apport and set enabled=0. This will prevent crash reports in the future.

---

### Post by mardybear on 2012-10-25
Hi Airycat...

Welcome to Ubuntu. It's unfortunate you're having so many issues. Sounds like really wierd stuff. Hopefully your experience will improve.

Which programs specifically won't open?

Although doubtful it's a virus, there is at least one Linux antivirus program that i'm aware of called clamav. You might want to check it out...should be available in your repositories.

You mentioned frequent crashes. Maybe run a system monitor, such as 'top' via terminal. It might help you identify problematic processes at the time of a crash. Your system also keeps numerous log files, which may be useful but i'm not expereinced enough to direct you with this.

Unless you remember having problems during your initial Ubuntu install, to me a full re-install is a last resort as it's time consuming and often does not yield better results.

Have you tried creating and logging in as a new user to see if most of these problems disappear? If so, then the problem may just be related to your profile. In which case you would need to either transfer your data to your new profile or try to fix your existing profile.

Nothing else that i can suggest off hand, other than back up your data since your system seems unstable. These are the things i would try first. Someone else might be better able to assist.

Good luck,

mardybear

---

### Post by Airycat on 2012-10-28
Thanks for trying to help. Everything is just very annoying right now and I NEED my programs that need Windows, so I'm going to wubi, if I can figure out how to get W7 back on my machine.

---

### Post by Airycat on 2012-10-28
I'm trying virtualbox again, so we'll see.

Weird things continue to happen, though. My auto updates started up again after a week of need to update manually. But last night when I went to check to see if I needed to restart after the updates, the system button in the upper right corner was gone. All I use that for is if I need to check for updates and turning off or restarting my computer. I would not remove it from the top bar. It's just weird. I did remove the weather button because it hasn't updated in at least a month, guessing by the temp it was displaying. I thought maybe that was causing some of the problems. If so, it wasn't all of them.

With the previous version of Ubuntu, I never got any kind of error messages (without knowing why) and the only weird thing was GIMP closing after any non .xcf save, which it still does.

---

### Post by alkh3myst on 2012-10-28
Airycat, just like many math teachers who used to confuse me and make me think I was bad at math, until I realized they were bad teachers, 2F4U has advised you to shut down crash reports if you like, but hasn't told you step by step how to do it. *This is because (s)he knows how to do it like second nature, and somehow assumes you do too.* 

What you need to do is open a terminal, from your menu, or by pressing CONTROL + "T". Next, after the prompt, you type "gedit" (no quotes), your text editor for configuration files. Next, you paste in the filename and hit "return". Now, gedit will open, with the configuration file text in it's window. Make 2F4U's suggested edit, then save the file and exit. Then, you can close the terminal window if you like. 

I'm not condemning 2F4U, obviously this person's a *very* expert Ubuntu user (no sarcasm), but sometimes experts can forget to connect the dots for the rest of us. I hope the "For Dummies" version will be helpful. When I started with Linux in 2007, I was *terrified* to use the terminal, because I understood that an "unlicensed operator" could do serious damage to their filesystem. This is why it's best to take your time and be very painstaking with terminal operations until you feel comfortable with them. There is a useful page here with links to guides on BASH/the terminal. [http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

):P

---

### Post by alkh3myst on 2012-10-28
Airycat, I almost forgot. Sometimes Ubuntu installs don't "take" properly, and are very buggy. A fresh install may be your answer.

---

### Post by daslinkard on 2012-10-28
> **alkh3myst said:**
> 
What you need to do is open a terminal, from your menu, or by pressing CONTROL + "T". 

If I'm not mistaken the general terminal start up command shortcut is
```

CTRL + ALT + T
```

---

