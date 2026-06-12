---
title: "Start-up log-in problem, Ubuntu 13.1"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by Grimster on 2014-01-20
Hi, wondered if anyone can help me as I'm not a 'techie' and don't understand the terminology and advice that's usually given in the 'how to' answers!
  I've recently upgraded from 12.04 to 13.1, which worked fine until I clicked on the 'update' section, which presumably downloads the letest updates. The next time I booted up, there is a black screen with a flashing cursor followed by a request for my log-in name and password, along with 'tty1'  -whatever that is.  This process now doubles the time taken before I can access the desktop and is really annoying. I resolved to re-load Ubuntu from scratch and to avoid the updates section. This worked great, but I've recently attempted to update the driver for my nVidia GT610 card by cut and pasting command prompts suggested in the forum (didn't have a clue what I was doing but it seemed to work as I now have a better resolution available.  Trouble is it has now jumped back to the command prompt type of log-in requirement. Doh!! 
 Can anyone please suggest a way to bypass that so I'm free to log in normally on the usual log-in or select user section?   (please bear in mind that I don't as yet understand any terminology, and what has often been referred to as a simple step by step fix has had my eyes glazing over within seconds!)

Cheers,  Grim.

---

### Post by Bashing-om on 2014-01-20
Grimster; Hi !

As a first approximation, has there been a  misuse of "sudo" causing a reassignment of permissions ?
1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority and .Xauthority" are owned by you:
```

ls -al .ICEauthority 
ls -al .Xauthority

```
Example of what it should result in:
> 
sysop@1310mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 12714 Jan 20 10:58 .ICEauthority
sysop@1310mini:~$ 
 where "sysop" is my username and group.
4. If it isn't (but possibly by root), we will need then to change it to you.

We be look'n
[INDENT][INDENT][INDENT]it is all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by Grimster on 2014-01-21
Hi, many thanks for your reply, much appreciated. However, unfortunately I hardly understood a word. I had the same problem with some work colleagues who tried to help me, mo one seems to understand that I really do not understand all this terminology. I don't understand things like 'sudo' ,  'log in screen'  or root, and wouldn't have a clue how to find out if I 'own' an ICE or X authority.
I'm afraid that I will just have to accept that the Ubuntu community can't really explain things in very simple non-technical sentences that me or my 86 year old mother could understand!  -but thanks for trying.   My best bet before I give up and return to Windows is to re-format and re-load Ubuntu 13.1 and make sure I don't accept any updates and accept that my graphics resolution will have to be fairly low def.
Rgs,  Grimster.

---

### Post by Bashing-om on 2014-01-21
Grimster; Hey !

Sorry for the late response .. busy busy busy.

Believe me not knowing is not a sin, we can always back up and keep it simple as needed to get the job done,
one step at a time.
OK ?
Boot up ubuntu
when you reach the screen where you normally would enter your password (where your username is displayed)
at the same time press the 3 keys ctl and alt and f1
Now you should be at a text terminal, yes ?

if so advise and standby for the next lesson.

[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by Grimster on 2014-01-22
Hi again!  Bravely battling on with this one, determined to have another go. Amazing what a good night's sleep does!   Thanks for your response, I really do appreciate it that there's someone out there who has the time to bother with helping an old git like me. When I boot up there is no longer any normal log-in screen, the first screen to appear is the blacked out screen with a flashing cursor and the request to enter log-in and password (mentions something about TTY1)   It does not accept ny normal log-in and password entries, constantly saying that they are incorrect. However, that does not matter as around a minute later  the screen disappears and then a few seconds later my normal desktop has loaded.  So the bottom line is that I can still use my PC but it takes a couple of minutes to load up rather than the 28 seconds that I achieved before. (got a new SSD drive installed last week)    Maybe I should just keep it this way as it could be a good way to instill the virtues of patience and to give me a moment of calm serenity and meditation before proceeding. In fact, in the interests of slowing down the pace of modern hectic life, maybe I should load up my dusty old copy of Windows 95 and revel in the relaxed slow-paced flow of 95 and good old dial-up 56K connectivity!

---

### Post by Bashing-om on 2014-01-22
Grimster; Hey,

Something is hosed up somewhere, The system having to validate and hunt up what to boot (??) , Presently I have not the foggiest where to start looking for the cause of the system's misdirections, Which I would think is the only reason for the behavior.

You want to take the time and effort to poke and prod about until we isolate the cause - will be a learning experience !- ?

Or take the nuclear - guaranteed to fix - approach, -> (re-install), and start all over. That is the quick thing, but we learn nothing from doing so.

We can start the trouble shooting by seeing how quick you boot to a terminal on purpose, and from this terminal take a look around, make sure the base system is intact.
And -< carry forth from there.

Your system, your problem, your time -> your call 

[INDENT][INDENT]what ya wanna do
[/INDENT][/INDENT]

---

