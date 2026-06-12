---
title: "[Pyton] System beep not working"
date: 2009-06-02
forum: Programming Talk
---

### Post by mhoy06 on 2009-06-02
I'm using python 2.6 and Ubuntu. The following code isn't work either in the interpreter or run from a file:

[PHP]
import sys
sys.stdout.write('\a')
[/PHP] 

It's the weirdest thing because I recall it working the other day. Since that day I haven't done much to my system besides adding a new user and installing languages for that account. I'm the only one using this computer. I've checked in SYSTEM>PREFERENCES>SOUND and it seems fine. Correct me if I'm wrong but that beep is not controlled by the settings right?

Anyway I must be missing something really simple. Any help appreciated.

---

### Post by s.fox on 2009-06-02
Hi,

Try this:
```

     print "\a"

```

Hope this helps

-Ash R

---

### Post by mhoy06 on 2009-06-02
> **Ash R said:**
> Hi,

Try this:
```

     print "\a"

```

Hope this helps

-Ash R

Forgot to mention that I tried that too. No luck. Thanks for the reply though.

---

### Post by unutbu on 2009-06-02
Perhaps check
```
xset q | grep bell
```
If you see ```

**  bell percent:  0**    bell pitch:  400    bell duration:  100
```
Then turn the bell on with
```

xset b on
```

---

### Post by mhoy06 on 2009-06-02
> **unutbu said:**
> Perhaps check
```
xset q | grep bell
```
If you see ```

bell percent:  0    bell pitch:  400    bell duration:  100
```
Then turn the bell on with
```

xset b on
```

Nice. Didn't know about that. Anyway here is my xset q | grep bell:

[PHP]
bell percent:  50   bell pitch:  400    bell duration:  100
[/PHP]

So that tells me that the bell is on. Tried this anyway:  
[php]
xset b on
[/php]

Still no beep.
Edit:
Also tried xset b off then xset b on as well.

---

### Post by unutbu on 2009-06-02
When you type```

lsmod | grep pcspkr
```
do you see```

pcspkr                 10624  0 
```
?

and when you open a gnome-terminal and type Ctrl-g do you hear the beep?

---

### Post by mhoy06 on 2009-06-02
I see:

[php]
pcspkr                 10496  0 
[/php]

and no when I type control g I hear no beep

---

### Post by unutbu on 2009-06-02
Hm, sorry, I'm stumped. :confused:

---

### Post by mhoy06 on 2009-06-02
> **unutbu said:**
> Hm, sorry, I'm stumped. :confused:

NP, I appreciate the effort. Hey at least I learned something about how to grep for pc speakers and verify that the bell is on :)

---

### Post by sujoy on 2009-06-02
i have a pc beep channel in alsamixer for my desktop, not there in laptop though. so if you have such a channel, check if its muted or not.

---

### Post by mhoy06 on 2009-06-02
Thanks, checked for it and it wasn't there. It's a laptop, might be why.

I tried to turn them all on, but most of them wouldn't turn on. The ones that did didn't solve the problem.

---

### Post by bsund on 2009-06-02
My laptop beeps in it's speakers, you made sure that you got volume on? :)

And if I have headphones it beeps in them etc.

Check in your bios if there is any option about it..

Strange problem though :)

---

