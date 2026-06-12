---
title: "Advanced shell script?"
date: 2010-09-22
forum: Programming Talk
---

### Post by C4pt41n 5k33t on 2010-09-22
Hello, I was wondering if this could be made possible.
I play a game called diablo2 and I have hack that injects itself into a process id with the following command: surgeon -i (PID) /usr/local/lib/snoogans.so

Instead of having to lookup the PID in terminal and then run the inject command using terminal, couldnt I just write a shell script to do both at one time?
It would need to do the following:

Open terminal - type: ps aux | less.
Find the PID for diablo 2 - copy it then close that terminal.
Open a new terminal and type: surgeon -i (PID) /usr/local/lib/snoogans.so
Then close that terminal also.

PID is short for process id, for those who were wondering what it is. =p
BTW, any help is appreciated. Thanks.


This has been solved, thanks everybody =D.

---

### Post by lloyd_b on 2010-09-22
> **C4pt41n 5k33t said:**
> Hello, I was wondering if this could be made possible.
I play a game called diablo2 and I have hack that injects itself into a process id with the following command: surgeon -i (PID) /usr/local/lib/snoogans.so

Instead of having to lookup the PID in terminal and then run the inject command using terminal, couldnt I just write a shell script to do both at one time?
It would need to do the following:

Open terminal - type: ps aux | less.
Find the PID for diablo 2 - copy it then close that terminal.
Open a new terminal and type: surgeon -i (PID) /usr/local/lib/snoogans.so
Then close that terminal also.

PID is short for process id, for those who were wondering what it is. =p
BTW, any help is appreciated. Thanks.
Your script will look something like this:```
#!/bin/bash

PID=`ps ax -o pid,comm  | grep diablo2 | cut -d ' ' -f2`

if [ -n $PID ]; then
    surgeon -i $PID /usr/local/lib/snoogans.so
fi
```A couple of notes.  First off, those are "backtics" at the start and end of the commands on the "PID..." line, not single quotes.  It makes a difference.

Second, I just guessed that the name that appears for Diablo 2 is "diablo2" - could be something completely different.

Lloyd B.

---

### Post by C4pt41n 5k33t on 2010-09-22
Your script is pretty much a perfect match of what I was looking for.
But my only problem is that when I run the ps aux | less command and lookup the proccess id, this is what it shows up as: C:\Program Files\Diablo II\Game.exe -direct -txt -w. 
And that would be fine, but when I run the script I get this: 
grep: unknown directories method. So then it cant run my injection without the pid. =(

---

### Post by conundrumx on 2010-09-22
You really should find something better to do with your time than cheat in a 10 year old video game, that being said...

```

#! /bin/bash

surgeon -i `pgrep diablo2` /usr/local/lib/snoogans.so 
```

Assuming the process name is diablo2 and there are no other processes matching the same string.  This, of course, assumes you're running on a system with pgrep (which is included in the base install of virtually every *nix except OSX).

---

### Post by C4pt41n 5k33t on 2010-09-22
> **conundrumx said:**
> You really should find something better to do with your time than cheat in a 10 year old video game, that being said...

```

#! /bin/bash

surgeon -i `pgrep diablo2` /usr/local/lib/snoogans.so 
```Assuming the process name is diablo2 and there are no other processes matching the same string.  This, of course, assumes you're running on a system with pgrep (which is included in the base install of virtually every *nix except OSX).

First, my mod isn't cheating; all it lets me do is put skills on the left...on the right. Also,  the pgrep command doesn't do anything when I use it.

---

### Post by conundrumx on 2010-09-22
What's the name of the process you look for?  pgrep will return the PID (and nothing else) of any process matching the string you feed it.

---

### Post by C4pt41n 5k33t on 2010-09-22
I'm running diablo2 in wine. So when I use ps aux | less, it comes up as this C:\Program Files\Diablo II\Game.exe -direct -txt -w. But I have tried to use that with both of scripts posted and the process id lookup commands cant find the process for some reason.

---

### Post by tgm4883 on 2010-09-22
Hmm, notepad.exe comes up as notepad.exe when I grep it, but from what you have posted, couldn't you just grep for Diablo II?

Something like (edited from above)
```
#! /bin/bash

surgeon -i `pgrep 'Diablo II'` /usr/local/lib/snoogans.so
```

obviously Diablo II must be running, but doing just a 

```
pgrep 'Diablo II'
```

should give you the PID

---

### Post by C4pt41n 5k33t on 2010-09-22
I wish it would, but I don't get anything back when I use pgrep. But when I use ps aux I get this instead of just diablo II: C:\Program Files\Diablo II\Game.exe -direct -txt -w. It still shows a process id, it's just showing a command rather than a game name. Thats what is getting me confused. =(

Nvm I solved it using:

#! /bin/bash

surgeon -i `pgrep 'Game.exe'` /usr/local/lib/snoogans.so

---

### Post by conundrumx on 2010-09-22
Please do ```
 ps aux | grep iablo 
```

And paste the results.

Edit: As I suspected, the process name is not diablo or any variation there of.

---

