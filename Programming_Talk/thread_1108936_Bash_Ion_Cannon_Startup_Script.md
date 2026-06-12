---
title: "Bash: Ion Cannon Startup Script"
date: 2009-03-28
forum: Programming Talk
---

### Post by Blacklemon67 on 2009-03-28
Just a novelty bash script I made as a joke. Simulates the starting up of an orbital ion cannon. :P

[http://pastebin.com/f81df77c](http://pastebin.com/f81df77c)

---

### Post by JordyD on 2009-03-28
Invite your neighbors over, put a computer in the livingroom with a fullscreen terminal (of course with the scary green text on black background) and execute. Observe reaction.

---

### Post by jimi_hendrix on 2009-03-28
you rock, make it require some mysterious passcode (like some quote from literature)

---

### Post by Blacklemon67 on 2009-03-29
> **jimi_hendrix said:**
> you rock, make it require some mysterious passcode (like some quote from literature)

Good idea! Just I have no clue what book has a quote that relates to Ion Cannons... :confused:

---

### Post by jimi_hendrix on 2009-03-29
just think of some well known quote...but one thats kinda...out there

---

### Post by Blacklemon67 on 2009-03-29
“The most powerful weapon on earth is the human soul on fire.”

Humm, that's a good one. But too long for a passcode...

How about a fill in the blanks type thing

---

### Post by jimi_hendrix on 2009-03-29
why not?

---

### Post by Blacklemon67 on 2009-03-29
Well, If you're gonna use this as often as one should, it shouldn't be **that** long.

---

### Post by Can+~ on 2009-03-29
Maybe some reference from "Hackers"?

Like "[Hack the Gibson]("http://www.urbandictionary.com/define.php?term=Hack%20the%20Gibson")".

---

### Post by Blacklemon67 on 2009-03-29
> **Can+~ said:**
> Maybe some reference from "Hackers"?

Like "[Hack the Gibson]("http://www.urbandictionary.com/define.php?term=Hack%20the%20Gibson")".

lol, like the term will say:

What do you tell the noob to do?
then you need to input "Hack The Gibson"

Does the read command work well for passwords?

---

### Post by curvedinfinity on 2009-03-29
Haha, awesome script. You have to make it request a target also. Then we can blow up New York or Tokyo or Paris all day long! Muhahaha!

---

### Post by Nevon on 2009-03-30
You should use some kind of speech synthesizer to do the countdowns and read some of the messages (like "Ion beam fired" and "Awaiting user input").

---

### Post by Blacklemon67 on 2009-03-30
> **curvedinfinity said:**
> Haha, awesome script. You have to make it request a target also. Then we can blow up New York or Tokyo or Paris all day long! Muhahaha!

That could work, just get some sort of parameter parser... Of course I have no clue how to do *that*. Lol. :P

> **Nevon said:**
> You should use some kind of speech synthesizer to do the countdowns and read some of the messages (like "Ion beam fired" and "Awaiting user input").

Tried speech synth once before and it's actually a real disappointment. The numbers come up before the synth finishes and the sounds start garbling up.

---

### Post by Blacklemon67 on 2009-03-30
Ok version two. [http://pastebin.com/pastebin.php?dl=m3b96cb64](http://pastebin.com/pastebin.php?dl=m3b96cb64)

---

### Post by Nevon on 2009-03-31
I rewrote the script in Python as a learning excersise. It has some minor improvements, but it's still pretty much identical to the bash version. However, I can't seem to get the last loop to end. I want the user to be able to enter 0 as the target in order to quit, but for some reason it doesn't work, so the loop continues on forever.

Anyway, here's the script:
[http://pastebin.com/f1b4311dd](http://pastebin.com/f1b4311dd)

---

### Post by Blacklemon67 on 2009-03-31
> **Nevon said:**
> ...However, I can't seem to get the last loop to end. I want the user to be able to enter 0 as the target in order to quit, but for some reason it doesn't work, so the loop continues on forever.

Fixed it, The input is a string and the condition checks it as if it's a integer.

[http://pastebin.com/pastebin.php?dl=f780b3cc0](http://pastebin.com/pastebin.php?dl=f780b3cc0)

---

