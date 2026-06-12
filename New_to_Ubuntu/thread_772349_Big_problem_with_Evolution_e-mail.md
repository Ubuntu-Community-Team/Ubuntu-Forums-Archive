---
title: "Big problem with Evolution e-mail"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Indy452 on 2008-04-28
I screwed up my evolution e-mail by trying to send a short video attachment and its stuck in the outbox. I use Ubuntu 7.10

I don't store alot of e-mails and I've tried to delete it but the evolution just crashes and returns to the desktop and I have to re-launch evolution only to do the same thing over.

What can I do to clear out this video that is stuck in the outbox?

I'm even willing to uninstall Evolution and re-install if needed. I would just need some tips on doing that.

I hope someone can help.  Thanks.

---

### Post by forrestcupp on 2008-04-28
Well, if you don't mind losing your archived emails, contacts, and calendar events, the first thing you could try is deleting your .evolution settings directory in your /home folder.  Then when you run Evolution again, it should create a new settings directory and reset itself.  To do this, you can open a terminal and type:
```
rm -rf ~/.evolution
```
Before someone freaks out because of all of the warnings for similar commands, let me explain it to you.  First, you need to **make sure** to get that command right.  If you mistype, you could really screw things up.  I recommend copy/pasting.  This command will remove (rm) the entire .evolution directory and everything in it, including the offending out going message.  It's not the actual directory where Evolution is installed; it is just where it stores its settings and emails, etc.

Then try running Evolution again.  You will have to set it up for your email account again, but at least it should work.  If it still doesn't work right, you could try reconfiguring it:
```
sudo dpkg-reconfigure evolution
```

---

### Post by mlentink on 2008-04-28
This seems to me like a very crude solution. More likely the OP could just delete his outbox, which is in /home/{user}/.evolution/mail/local, or am I mistaken?

---

### Post by f37u5g0d on 2008-04-28
Indy.  If you are weary of using such a powerful command that forrestcup suggested you can navigate to your home directory and in the view menu check "view hidden folders" then you will be able to see all of the /.whatever files.  Find the evolution one and delete it.  This basically does the same thing the command does.  It's just a more user friendly way of doing it especially if you aren't used to command lines.  Also if you do accidentally delete the wrong file they go into the trash before they're gone so you can move them back if you need to.

---

### Post by Golem XIV on 2008-04-28
Before you go deleting all your mails, contacts etc. I have a suggestion.  Don't delete the .evolution directory, but move it elsewhere or rename it (removing the period in front would keep Evolution from reading and it would have the added bonus of being able to see it in the directory listing later for recovering the information).

But before you do that, try placing Evolution in offline mode (File -> Work offline) and then deleting the problematic message.

---

### Post by mlentink on 2008-04-28
Indy452, I advise against deleting your entire .evolution directory. If you contemplate on doing so, at least first make a backup of it so you do not lose critical data (your e-mails!).
Then I would advise on first deleting the outbox only, including the accompanying index files, which you can find at the location I mentioned earlier. If that doesn't work, you can always follow the advice to delete the whole directory, but I do not think that will be necessary.

---

### Post by tuskenraider on 2008-04-28
I have a huge problem with eveolution email as well.... LOL  it wont go away! LOL is it me or is evolution email more intertwined into ubuntu than aol is in windoze? :lolflag:

tusken

p.s your welcome for the spam! :)

---

### Post by Indy452 on 2008-04-28
Well, thanks everyone for the great responses.

Unfortunately I'm at work and away from my machine so I'll have to look into it later this eve. I'll try some of the little more user friendly suggestion before I remove with command which is no big deal to me. I really keep my mail boxes clean and I only have about twenty contacts that I have elsewhere also, so starting from scratch is O.K. if I need to.

I'll work on it this eve and hopefully post back some results and solved if needed.

Thanks to all.

Neal

---

### Post by Indy452 on 2008-04-28
> **f37u5g0d said:**
> Indy.  If you are weary of using such a powerful command that forrestcup suggested you can navigate to your home directory and in the view menu check "view hidden folders" then you will be able to see all of the /.whatever files.  Find the evolution one and delete it.  This basically does the same thing the command does.  It's just a more user friendly way of doing it especially if you aren't used to command lines.  Also if you do accidentally delete the wrong file they go into the trash before they're gone so you can move them back if you need to.


This is exactlly what I did and walla! Evolution is up and working like new again! I did not lose anything either, wierd I know. I was fully expecting to lose all my contacts but they are still alive and well. 

Thanks everyone!  I'd mark it solved but I guess I can't figure out how to mark it solved. 

Neal

---

### Post by forrestcupp on 2008-04-28
So you deleted your entire .evolution folder and still didn't lose your emails?  Weird.  Evolution must not work like Thunderbird.

I'm glad it worked for you.

---

### Post by Indy452 on 2008-04-28
> **forrestcupp said:**
> So you deleted your entire .evolution folder and still didn't lose your emails?  Weird.  Evolution must not work like Thunderbird.

I'm glad it worked for you.

No, I lost the e-mails but I did'nt loose the settings and contacts.

Neal

---

