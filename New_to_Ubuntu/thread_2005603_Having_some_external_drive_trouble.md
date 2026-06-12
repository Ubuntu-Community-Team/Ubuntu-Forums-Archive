---
title: "Having some external drive trouble"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by OneBlueSky on 2012-06-17
Hello everyone!

I am having a bit of a hard time with my external hard drives. I have done a *lot* of searching here and on Google, but I have yet to really find a solution that worked, or that I can understand how to do, being an Ubuntu noob.

I am running Ubuntu 12.04. My specs are - Intel i7 3.40GHz, 16GB RAM, 6TB of internal storage. I have 2 3TB external drives, and a 1TB external. I know the problem is that they are GPT. I've been able to learn that much from the searches. When I plug any of them in, nothing happens. They never show up. I've seen some command line stuff, but either the person posting the issue said they didn't help and it remained unresolved, or it got into a lot of stuff that I don't understand how to do myself.

One interesting thing - If I put the drives in my computer's internal bay, they are all recognized. In the (self powered) enclosures plugged in via USB, they never show up.

If it's not too much trouble, could someone in very basic, beginner terms tell me how I should proceed? These all work with Windows 7. I'd love to make the permanent move to Ubuntu, but without the ability to backup everything, there's really not much point! Thanks! :)

---

### Post by LawM on 2012-06-17
I have the same issue. Out of curiosity, what is your kernel?

---

### Post by OneBlueSky on 2012-06-17
How exactly do I get that information? (Sorry, again this is a whole new world to me! )

---

### Post by OneBlueSky on 2012-06-17
Nevermind, found that bit...

I show to be using 3.2.0-25-generic

---

### Post by LawM on 2012-06-17
i'm using 3.2.0-24-generic and it works. Some days ago I tried the 3.4 and the 3.37 ones and it wasn't working. Have you tried using any other kernel? Do you have any installed?

---

### Post by OneBlueSky on 2012-06-17
Oh really? So you're able to mount/use GPT external drives on that kernel? Nope! I wouldn't even know where to begin installing one, however if that's a solution, I will certainly begin looking it up!

---

### Post by LawM on 2012-06-17
Oh, i'm afraid i missed the GPT part =(. After you pointed it to me i did some searches, and it should work with that kernel (support for it started long ago, kernel 2.6) and with the new ubuntu, so i don't think it's worth it to install a new kernel.

What have you tried in command line? Maybe we can make some sense out of it, as i understand you need to mount it using a volume label...

---

### Post by OneBlueSky on 2012-06-17
No problem! Well, that's kind of what I have seen too, but for some reason for me (and several others it seems as many of the google results show this to be unresolved for a good deal of folks) it won't work at least not fresh after an install/update. I have done nothing in command line, I don't know nearly enough. I have tried...

Plugging them into the computer's internal bay. Recognizes them fine there, and reads them/writes to them perfectly. 

I have tried formatting them while they were plugged into the internal bay, then put them back in the external, nada.

Since they work in Windows, I have tried changing them from GPT, still never mount or show up in Ubuntu.

That's about as much as I did. I am too unfamiliar with Ubuntu at this point to proceed further

---

### Post by OneBlueSky on 2012-06-18
Any ideas?

---

### Post by OneBlueSky on 2012-06-19
Figure I'll try one more time before I have to go back to Windows :| Anyone got any ideas? [-o<

---

### Post by OneBlueSky on 2012-06-20
Just one more try! Gonna have to reinstall Windows when I get home if no one can help! Thanks for your time!

---

