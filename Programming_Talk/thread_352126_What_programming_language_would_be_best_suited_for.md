---
title: "What programming language would be best suited for..."
date: 2007-02-02
forum: Programming Talk
---

### Post by me1on on 2007-02-02
Alright guys, I'm having a strange problem, and I need some help. :) Somebody has been mysteriously deleting my Firefox history, and I'm suspicious of what he's doing online. I want to back up the history before it is deleted without this person knowing.

Here's my plan: Make a script that starts by examining the length of ~/.mozilla/firefox/xxxxxxxx.default/history.dat, and re-checks the length of the file and makes a copy of the file every 15 seconds or so. Once it notices that history.dat is gone or is shorter than it was when it was checked the first time (i.e. the history has been deleted), it creates a file of the list of the last visited web sites (from the latest backup created) and shows the date and time when the history was deleted. Each time this certain person asks to get on the computer, I'll run the script then let him on. If he deletes the Firefox history again, I'll have a file that will tell me exactly what sites he was on before he deleted the history. :twisted: 

Is this possible, and is there a certain programming language that I should learn that's good at this sort of thing (I only know C++ at the moment)? Is there a better way to do this? I don't necessarily need somebody to provide me a script, I'm just looking for some advice to help me get started. (Besides, it sounds like a fun challenge and it's about time I learned a language besides C++ :)) Would Python or Ruby work for this sort of task? Thanks for the help.

---

### Post by LostShootingStar on 2007-02-02
perl, or even bash scripting could probably do that..

---

### Post by Paerez on 2007-02-02
I would make a really simple bash program that would do this:

every 60 seconds run "tar czf /path/to/log/folder/of/your/choice/`date +%s`.tar.gz ~/.mozilla/firefox/*.default"

that will make an archive (to save space) named after the current time in seconds somewhere.


Or you could sit on a computer on the network and run ethereal :D

---

### Post by me1on on 2007-02-03
Alright, thanks guys. Time to get to work! :)

---

### Post by phossal on 2007-02-03
I suspect you *know* what you're looking for. I say you get in on it, and stop being sneaky. It's always more fun when *two* people do it together. Rather than learning a new language to write your own spyware, why not take the high (and much simpler) road and simply *ask* what you want to know?

[edit] I'm rarely interested in good *answers*. I tend to find the *questions* entertaining. ;)

[edit2] I recommend a *compilable* language, like C or C++, rather than a script. The last thing you want is for someone to learn what you're doing, copy your script, *read* it, and *sue* you. lol

---

### Post by maxamillion on 2007-02-03
bash script .... or python, but probably bash ....

i like being vague, less chance of being wrong :P

---

### Post by Wybiral on 2007-02-03
> **phossal said:**
> I suspect you *know* what you're looking for. I say you get in on it, and stop being sneaky. It's always more fun when *two* people do it together. Rather than learning a new language to write your own spyware, why not take the high (and much simpler) road and simply *ask* what you want to know?

[edit] I'm rarely interested in good *answers*. I tend to find the *questions* entertaining. ;)

[edit2] I recommend a *compilable* language, like C or C++, rather than a script. The last thing you want is for someone to learn what you're doing, copy your script, *read* it, and *sue* you. lol

lmao... I think I just got what you were insinuating...

But seriously, it may be weirder than you think... They could be looking at "How to kill your room mate" tutorials, or ordering "oops, I killed someone" cleanup kits on ebay... Or even worse than those... PRO-republican propaganda!!!

These are things that you might not want to just ask someone about... It could end in disaster.

Good luck though! Also, don't get hurt...

---

### Post by runningwithscissors on 2007-02-03
bash script on a cron job.

---

