---
title: "Burned DVD's plays on linux but not windows"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by darkerlink on 2008-05-03
I have used Nautilus to burn iso's onto dvd's and they all work fine until one day it froze on me and I pressed the off button and manually shutdown my computer. So I had to burn a bunch of DVD's for my sister and all of the dvd's doesn't work on her windows vista. So I've been making dvd's to test and she was right. They all were busted. Could be read.

I started digging the forums and tried to turn on "burnproof" running gconf-editor and going to apps>nautilus. The dvd burns fine but it can't be read. So I am using K3B now using the DAO (disc at once) setting with speed as "ignore" and finally I can get a successful burn... or so I though. I loaded it up onto my computer and opened it with VLC and YES! it works! So I gave it to my brother to load it onto his laptop (Windows XP) and it says something like "Cannot be read. Data might be currupt" and "Could not find video directory" . I have not tried these disc on a standalone DVD player but even if it does work, it would be pointless because my ahem "customer"(sister) can't watch these movies on her laptop.

I've been burning lots of dvd's with nautilus and everything used to go fine until now. I like using K3B as it has more options so I guess I'll stick to that. Anyone got a clue as to why these DVD's don't work on windows? Or better yet, anyone got a fix to this problem?:guitar::guitar:

---

### Post by SunnyRabbiera on 2008-05-03
have you tried disk finalization?

---

### Post by darkerlink on 2008-05-03
When I right click the ISO and burn with Nautilus, it goes through the status bar and at the end, it says "Finalizing Disc" so yes I guess I have tried that even thought it is automatic. It would have to be finalized anyways if I can read it on Ubuntu but not Windows right?

---

### Post by SunnyRabbiera on 2008-05-03
right, as if its not finalized it will only be readable on the machine it was burned on IE your ubuntu computer.
but you should be able to finalize them, I am not exactly sure how it works on this as I dont have a dvd burner on this computer but at least I gave you a starting point eh?

---

### Post by darkerlink on 2008-05-04
Though it did give me something to consider, I do not think that is the issue as I have burned movies for my sister before and it worked fine on her computer. The only thing I can think of is the manual shutdown that I did. Ever since I've restarted my computer 4 times and still no luck on a windows system. The reason I did a shutdown was because the DVD was spinning in the drive for about 5 minutes without the progress bar movie. Tried to cancel and everything froze on me. Couldn't shutdown from the top-right so I had to do it. So during my dig, I found that many people were having this same issue but under the Dapper release. I am using the Hardy release.

---

### Post by SunnyRabbiera on 2008-05-04
it still might be a bug, always consider this.
sometimes bugs slip by or have too many issues to resolve right away.
next time be a little more careful, and maybe use another speed.
if you have k3b use it, I still think k3b is the best burner linux can offer...
heck it makes me wish the windows port was out there already :D

---

