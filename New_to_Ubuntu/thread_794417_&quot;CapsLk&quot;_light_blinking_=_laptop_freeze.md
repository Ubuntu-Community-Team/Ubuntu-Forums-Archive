---
title: "&quot;CapsLk&quot; light blinking = laptop freeze"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by cseljatib on 2008-05-14
Hi there,
i am using ubuntu 8.04 in a lenovo t60.

the problem:
sometimes when i am working (does not matter in what program), the light of the CapsLk at the bottom of the laptop-screen (the one that shows "A", and is on when you hit once the CapsLk key, and is off when you hit again) start to blink, and the laptop just freeze, showing either a black screen or the screen that i was seeing before of the freezing.

What can i do??,
PLEASE help!!

thanks

---

### Post by will1911a1 on 2008-05-14
> **cseljatib said:**
> Hi there,
i am using ubuntu 8.04 in a lenovo t60.

the problem:
sometimes when i am working (does not matter in what program), the light of the CapsLk at the bottom of the laptop-screen (the one that shows "A", and is on when you hit once the CapsLk key, and is off when you hit again) start to blink, and the laptop just freeze, showing either a black screen or the screen that i was seeing before of the freezing.

What can i do??,
PLEASE help!!

thanks

So it just starts blinking and the laptop freezes up?

Have you tried hitting CTRL+ALT+Backspace to see if it will restart X?

---

### Post by cseljatib on 2008-05-14
i just tried that (CTRL+ALT+Backspace) and i did not produce any change, the light is still blinking

any new recommendation?

---

### Post by will1911a1 on 2008-05-14
> **cseljatib said:**
> i just tried that (CTRL+ALT+Backspace) and i did not produce any change, the light is still blinking

any new recommendation?

Does it eventually unfreeze or do you have to power the laptop off to get everything working again?

---

### Post by cseljatib on 2008-05-14
i have been waiting like an hour now, and it does not unfreeze, then i have to turn-off the computer.
do you want that i do that? (i mean the problem is going to be there anyway)

if so, what should i do?, start as "recovery mode" or something like that?, if so, what should i type?

---

### Post by sharpycore on 2008-05-14
A blinking capslock light indicates a kernel panic. I don't completely understand what this means but from my experience it can't be recovered from and you just have to restart the system.
Please tell us what you are running when the computer freezes, particularly any torrent programs.

---

### Post by cseljatib on 2008-05-14
it seems to be independent of any program, last time i just turn it on, and i did not open any program, and still freezed

---

### Post by will1911a1 on 2008-05-14
Sounds like a kernal panic. 

Are you running the 64 bit version of 8.04 or the 32 bit version?

---

### Post by cseljatib on 2008-05-14
32 bits (as far as i know)
i do also have the computer with dual-boot (i have a winXP partition just in case, which by the way seems to be working OK)

and also let me point out that, if i just turn off the laptop, then it will take me like 3 trails to make it turn on, i mean, the first one, it will turn on, but it will freeze even after of showing me the GRUB screen (the one in which if i choose, ubuntu normal, o recovery mode, or WinXP, etc)

---

### Post by shifty_powers on 2008-05-14
heh this clears something up for me partially.

been having a similar problem with my desktop machine, but only occasionally, and always when it is doing something with the dvd drive.

very annoying but doesn't happen too often.

wonder what about my dvd drive that is causing a kernel panic :shock:

---

### Post by will1911a1 on 2008-05-14
> **cseljatib said:**
> 32 bits (as far as i know)
i do also have the computer with dual-boot (i have a winXP partition just in case, which by the way seems to be working OK)

and also let me point out that, if i just turn off the laptop, then it will take me like 3 trails to make it turn on, i mean, the first one, it will turn on, but it will freeze even after of showing me the GRUB screen (the one in which if i choose, ubuntu normal, o recovery mode, or WinXP, etc)

If it doesn't freeze at all in XP the best I can suggest is try try a fresh install of Ubuntu and see if that fixes it.

---

### Post by cseljatib on 2008-05-14
actually, i already did that. Last time, i also installed VirtualBox, and just some days after that, i started to have this problem, then i thought, maybe virtualbox was the problem, then i did a clean install of ubuntu (leaving the winXP partition untouch)without later installing VirtualBox, i did so, but unfortunately i got the same problem

---

### Post by will1911a1 on 2008-05-14
Not sure what to tell you then.  I had a similar problem with 7.10 and got fed up with it enough that I installed Arch and never looked back.

Hopefully someone with some other ideas sees this thread.

Sorry I can't help you more.

---

