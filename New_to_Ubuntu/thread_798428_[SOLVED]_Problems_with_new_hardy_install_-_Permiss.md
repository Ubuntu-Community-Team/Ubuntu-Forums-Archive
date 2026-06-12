---
title: "[SOLVED] Problems with new hardy install - Permissions etc"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by mixtri on 2008-05-18
Hi my friends in Ubuntu World!!

Here is yet another problem I have.

I have just installed a fresh copy to my disk

Problems is' after applying the customary new updates flagged up by the update manager and rebooting, i got the following message at system startup just before ubuntu loads the desktop environment - 

User's $HOME/.dmrc file is being ignored. This
prevents the default session and language from
being saved. File should be owned by user and 
have 44 permissions. User's $HOME directory must 
be owned by user and not writable by other users.

I have since used root privileges to change the permissions by right clicking on relevant folder. However upon rebooting  I get the same message.

And why has Ubuntu done this? surely I should have complete permission to my home directory as default.

Also, I am also unable to access my backup files which reside on a separate disk on the computer. I can only access the contents with root privileges. 

I have changed the permissions on this disk so that I, the user is now the owner and group. However my problem is, this setting does not cascade through to all sub folders and files. Short of spending hours changing permissions for every folder and file on a 62 Gb disk is there any other means of achieving this? 

Thanks in advance.

---

### Post by mixtri on 2008-05-18
I forgot to mention the version of Ubuntu installed. it's Hardy 8.04! :popcorn:

---

### Post by shifty_powers on 2008-05-18
look

[http://ubuntuforums.org/showthread.php?t=796628](http://ubuntuforums.org/showthread.php?t=796628)

---

### Post by mixtri on 2008-05-18
Thanks Shifty.

That worked fine for me. no problems with .dmrc file message.

However, I still have the issue of changing permissions on the backup disk i have installed on my pc.

Any ideas about that one.

---

### Post by shifty_powers on 2008-05-18
errm...

```
sudo chmod 664 -R *path of external disk*
```

iirc. the -R falg makes it recursive to all the files and folders in that file/directory...

---

### Post by shifty_powers on 2008-05-18
couldn't tell you what the path will be off the top of my head mind ;)

and checked chmod 664

[http://amath.colorado.edu/courses/WebPages/chmod.html](http://amath.colorado.edu/courses/WebPages/chmod.html)

and it will do the job nicely ;)

---

### Post by mixtri on 2008-05-18
Right guys n gals!
Its all good.

Solved the second problem using this thread
[http://ubuntuforums.org/showthread.php?t=790593&highlight=changing+disk+permissions](http://ubuntuforums.org/showthread.php?t=790593&highlight=changing+disk+permissions)

Blimey! responses within 15 mins of posting thread is brilliant!

Thanks all for your dedication. :)

---

### Post by shifty_powers on 2008-05-18
heh, happy to help, and it's amazing what the search function of the forum will throw up ;)

---

### Post by mixtri on 2008-05-18
Absolutely!

It such an invaluable tool for newbiews like myself.

I have now taken to saving all the threads, posts, tips etc that i find useful.

I completely wiped my computer and LIFE; I might add of Microsoft products for good. No looking back! :)

My last three months using Ubuntu has been quite a learning curve. Its been difficult but also rewarding as I seem to learn something new everyday; which has got to be good thing.

I love the fact that help is always only a few clicks of a mouse away and also that you can do whatever you want on this system. The software is there; Package Managers etc are such a f***ing necessity and brilliant idea, which just makes the user experience much more satisfying.

Anyway, thats all from me now. No more rants for the day! 
hmm- maybe its off to the cinema this evening :popcorn::)

---

