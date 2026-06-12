---
title: "Bash scripting assistance"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by AddictiveStew on 2008-10-10
Can anyone provide me the proper syntax for this statement:

"If  either directory 1 OR directory 2 DO NOT exist, then do this"

I currently have this:

if [ ! -d /media/DIR ] || [ ! -d /media/DIR ]
then
echo whatever
fi

Thanks in advance!

---

### Post by The Cog on 2008-10-10
It works for me. What problem are you having?
if [ ! -d /media/DIR1 ] || [ ! -d /media/DIR2 ]; then echo whatever; fi

---

### Post by ayenack on 2008-10-10
You're missing the "**;**" Think it should look exactly as The Cog has it.

You.
**if [ ! -d /media/DIR1 ] || [ ! -d /media/DIR2 ] then echo whatever fi**
The Cog.
**if [ ! -d /media/DIR1 ] || [ ! -d /media/DIR2 ]; then echo whatever; fi**

---

### Post by AddictiveStew on 2008-10-10
Thanks guys, the ; did it.

---

### Post by The Cog on 2008-10-10
That's odd. I copied and pasted the web page into gnome-terminal and hit enter. Then recalled the line with up arrow, and it reappeared on a single line with the semicolons there. I copied/pasted that into my reply. I never actually touched the semicolon key.

---

### Post by unutbu on 2008-10-10
What shell do you use, Cog?
(Copy/pasting does not do that for me in bash).

---

### Post by ayenack on 2008-10-10
> **The Cog said:**
> That's odd. I copied and pasted the web page into gnome-terminal and hit enter. Then recalled the line with up arrow, and it reappeared on a single line with the semicolons there. I copied/pasted that into my reply. I never actually touched the semicolon key.

I've just entered it used the up arrow to recall it and it's put it in the correct syntax with the ";" in place.

I think I remember a little app that does this that's in the repo's but can't for the life of me remember what it's called (could be imagining it.)

BTW I use gnome-terminal the standard one that comes with Ubuntu.

---

### Post by unutbu on 2008-10-10
Thanks ayenack. Copy/pasting each line separately works, copy/pasting the code as a multi-line block does not.

Edit: My mistake. multi-line pasting works too.

---

### Post by The Cog on 2008-10-11
I just use bash in gnome-terminal. I just didi it again to confirm what I said:
* drag over the code in the web page to highlight it,
* middle-click on a gnome-terminal bash shell to paste it
* Press enter to enter the command (it prints 'whatever' because the directories don't exist)
* Use up arrow to recall the command - there is is on one line with semicolons.
It surprised me too.

---

### Post by ayenack on 2008-10-11
> **The Cog said:**
> I just use bash in gnome-terminal. I just didi it again to confirm what I said:
* drag over the code in the web page to highlight it,
* middle-click on a gnome-terminal bash shell to paste it
* Press enter to enter the command (it prints 'whatever' because the directories don't exist)
* Use up arrow to recall the command - there is is on one line with semicolons.
It surprised me too.

Yep this worked for me to.

---

