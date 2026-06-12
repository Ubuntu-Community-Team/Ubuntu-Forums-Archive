---
title: "Ubuntu 15.04, Bleachbit and Kontact"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by sezhiana on 2015-06-22
Hi,

I suddenly decided to use bleachbit to clear some space in my dual boot Ubuntu/WinXP machine.

Everything looks OK so far except that my To DO list is empty in Kontact. 

Is there any way to recover my To Do list?

Thanks.

Selian

---

### Post by VMC on 2015-06-22
Maybe not unless you try 'testdisk'. In the future 'whitelist' what you don't want bleachbit to remove.

---

### Post by sezhiana on 2015-06-22
Would Bleachbit remove active portions? I have all the other parts of Kontact like contacts, calendar, pop-notes etc. Only To Do list is empty.

What is 'testdisk'?

Thanks.

---

### Post by yetimon_64 on 2015-06-23
Testdisk is data recovery software, it is available in the repositories, some information about it is in the next 2 links.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Whitelisting and proper set up of bleachbit is essential, I stopped using it about 2 years ago as a result of unexpected losses because of errors in configuration (my silly mistake while not paying full attention to what it would remove :-)). I go through what needs cleaning and do the removals/cleanup of my system far more manually nowadays. I no longer trust such software, sometimes it can be a bit too savage in the cleanup process, use it with a cautious attitude if you continue with it. It can do far worse than just clearing your contacts list especially if used as root (where my mistakes happened).

> Would Bleachbit remove active portions? I have all the other parts of  Kontact like contacts, calendar, pop-notes etc. Only To Do list is  empty.

It will clear anything you have selected in the preferences section, have a close look at than section and see if your contacts are selected. As noted above I haven't used it for a couple of years, but a contacts list is **not** something I would have expected to need "cleaning" by bleachbit... :-k maybe something else is involved as well here.

---

### Post by sezhiana on 2015-06-23
SOLVED: 
 After 2 days, the ToDo list has come back. I have no idea why it disappeared after BleachBit and how it reappeared now.
 Thanks for your interest.

---

### Post by wildmanne39 on 2015-06-24
Just know that bleachbit and other applications like it usually remove applications that you do not want it to, I learned the hard way.

---

### Post by monkeybrain20122 on 2015-06-24
Bleachbit is very safe to use provided you know what you want to clean and avoid experimental features (things like  free disk space and Deep Scan) and in general things that you don't understand. You can also preview what will be deleted if not sure. I have screwed up once before but it was my fault, can't blame the software.

---

### Post by yetimon_64 on 2015-06-24
> Bleachbit is **very safe to use** provided **you know** what you want to clean ... Yes, and carrying a loaded gun is very safe as well if "you know" not to point the nasty end at anyone and to keep the safety catch engaged at all times. Problem is, the less experience a person has with the tool in question, be it bleachbit or a loaded gun, the more likelihood of a rather messy/painful end to the story.

As noted in my previous post, through my own carelessness I metaphorically speaking, "blew a hole in my own feet". That happened in a few moments of distraction followed by pressing the clean button too quick before carefully reviewing the proposed changes, and a nasty mess ensued. I had been on Ubuntu for about 5 years and was not a total new user, just a careless/distracted one at the time.

Bleachbit is very good at what it does, but by the very nature of the tasks it carries out new users should, in my opinion, be given a solid warning of its potential to do damage and to use it with caution. The potential danger should always be emphasised never "minimized" as such in a beginners forum with this tool, imo. Cheers, yeti.

---

### Post by VMC on 2015-06-24
> **yetimon_64 said:**
> Yes, and carrying a loaded gun is very safe as well if "you know" not to point the nasty end at anyone and to keep the safety catch engaged at all times. Problem is, the less experience a person has with the tool in question, be it bleachbit or a loaded gun, the more likelihood of a rather messy/painful end to the story.

As noted in my previous post, through my own carelessness I metaphorically speaking, "blew a hole in my own feet". That happened in a few moments of distraction followed by pressing the clean button too quick before carefully reviewing the proposed changes, and a nasty mess ensued. I had been on Ubuntu for about 5 years and was not a total new user, just a careless/distracted one at the time.

Bleachbit is very good at what it does, but by the very nature of the tasks it carries out new users should, in my opinion, be given a solid warning of its potential to do damage and to use it with caution. The potential danger should always be emphasised never "minimized" as such in a beginners forum with this tool, imo. Cheers, yeti.

Also, the '***dd***' command is completely safe and ***not dangerous*** provided you _know what your doing_. What is that saying  "[measure twice, cut once]("https://www.google.com/search?q=measure+twice,+cut+once&client=ubuntu&hs=DbT&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=KMeKVb2WIsXvoAT18qeoBQ&ved=0CCwQsAQ&biw=1238&bih=744")".

---

### Post by monkeybrain20122 on 2015-06-24
> **yetimon_64 said:**
> Yes, and carrying a loaded gun is very safe as well if "you know" not to point the nasty end at anyone and to keep the safety catch engaged at all times. Problem is, the less experience a person has with the tool in question, be it bleachbit or a loaded gun, the more likelihood of a rather messy/painful end to the story.
.

I was very inexperienced when I started. I didn't select options that I didn't understand and looked things up if needed. Just common sense. Never had any problem in normal usage. I screwed up only once but that was because of another program which created links to my system in /tmp (during cloning) and  it was interrupted abruptly (accidentally disconnected the targeted drive) I stupidly cleaned afterwards without rebooting,--which would have safely disengaged the links) first and it deleted all the entries in /tmp which was half the OS. But it was a rare accident that I doubt an inexperienced or even experienced user would run into everyday. I could have prevented it if I just previewed before I cleaned. The same would have happened if I did it manually from the terminal, so it wasn't bleachbit's fault. 

Now there was another thing called gorphan or something which WAS inherently dangerous because the operation was dangerous (removing things which are "orphaned" in that there is nothing dependent on them) and the whitelist options were confusing so you can easily delete your whole OS, but not bleachbit which just runs commands like apt-get autoremove in the back.

---

### Post by monkeybrain20122 on 2015-06-24
> **VMC said:**
> Also, the '***dd***' command is completely safe and ***not dangerous*** provided you _know what your doing_. What is that saying  "[measure twice, cut once]("https://www.google.com/search?q=measure+twice,+cut+once&client=ubuntu&hs=DbT&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=KMeKVb2WIsXvoAT18qeoBQ&ved=0CCwQsAQ&biw=1238&bih=744")".

dd is of course dangerous, you have no way to preview and it doesn't provide any feedback. Moreover it doesn't just remove file systems but does something at the hardware level.

---

### Post by monkeybrain20122 on 2015-06-24
On the level of hazard I find the update-manager a lot more dangerous than bleachbit. What do you think when an inexperienced user, or an experienced user on a bad day, is invited to upgrade the OS by pressing yes out of the blue? (so the second thing I do after installing synaptic is always to disable that notification)

---

### Post by VMC on 2015-06-24
> **monkeybrain20122 said:**
> dd is of course dangerous, you have no way to preview and it doesn't provide any feedback. Moreover it doesn't just remove file systems but does something at the hardware level.

No its NOT dangerous.Its just a command. Did you read the part about _know what your doing_. There are plenty of commands that have the potential of catastrophe.

---

### Post by monkeybrain20122 on 2015-06-24
> **VMC said:**
> No its NOT dangerous.Its just a command. Did you read the part about _know what your doing_. There are plenty of commands that have the potential of catastrophe.

Then Bleachbit is not dangerous. I have heard more people screwing up with dd than bleachbit, among other things, typing errors.

---

### Post by VMC on 2015-06-24
A proverb: "measure twice, cut once". :)

---

