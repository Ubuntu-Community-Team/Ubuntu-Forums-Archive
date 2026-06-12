---
title: "Best text-typing function in Python"
date: 2014-01-02
forum: Programming Talk
---

### Post by blackout2 on 2014-01-02
What, in your opinion is the best way to make text look like it's being typed?
I know you all will have different ways about doing it, and I'm curious about what makes each solution different. So, please post your best way to print text as if it was being typed, in Python.

Have a good day!

---

### Post by blackout2 on 2014-01-02
I've tried doing this:
```



import time
text = "Hello"
def type_text(text):
	list(text)
	for b in text:
		print b,
		time.sleep(0.2)
	
type_text(text)

```
But it waits for 0.2 seconds, then prints out the whole word.
Weird...

---

### Post by ofnuts on 2014-01-02
This is due to line-buffering on stdout when it goes to a terminal. No I/O happens until your write a newline character. You have to flush the stream after each character, or find how to make it non-buffered.

---

### Post by blackout2 on 2014-01-02
Ah, that makes sense, thanks!

---

### Post by blackout2 on 2014-01-02
My version of the function:
```

def type_text(text):
	list(text)
	for a in text:
		sys.stdout.write(a)
		sys.stdout.flush()
		time.sleep(0.1)

```

---

### Post by Vaphell on 2014-01-02
for bonus points add typewriter sounds ;-)

---

### Post by blackout2 on 2014-01-02
I did, but it got annoying when I was debugging other parts of the program so I removed it.
```

import pygame
import sys
import time
pygame.mixer.init()
pygame.mixer.music.load('/root/Python/audio.wav')


def type_text(text):
	list(text)
	for a in text:
		sys.stdout.write(a)
		pygame.mixer.music.play()
		sys.stdout.flush()
		time.sleep(0.05)


type_text("Hello")

```

There ya go!

---

### Post by Vaphell on 2014-01-03
but where is the 'ching' at newline? ;-)

Yes, such things surely get annoying, even printing char by char gets old after a while when you debug stuff for the hundredth time.
You should have such fluff&bling things that add non-negligible delay and/or noise parametrized (program param or constant) so when you debug you can choose to go through the path that shortcircuits things 

```
debug=True

def type_text( text, debug ):
    if debug:
        print text
    else:
        <fluff>
```

---

### Post by blackout2 on 2014-01-03
> **Vaphell said:**
> but where is the 'ching' at newline? ;-)

Yes, such things surely get annoying, even printing char by char gets old after a while when you debug stuff for the hundredth time.
You should have such fluff&bling things that add non-negligible delay and/or noise parametrized (program param or constant) so when you debug you can choose to go through the path that shortcircuits things 

```
debug=True

def type_text( text, debug ):
    if debug:
        print text
    else:
        <fluff>
```
Good idea!

---

### Post by ofnuts on 2014-01-03
> **Vaphell said:**
> but where is the 'ching' at newline? ;-)
Yes, such things surely get annoying, even printing char by char gets old after a while when you debug stuff for the hundredth time.


A very long time ago, I wrote a PC-DOS keyboard driver and debugged it by ear by adding beeps in strategic places in the code :) The code path for alphabetic letters would play the Indiana Jones theme (yes, that long time ago).

---

### Post by blackout2 on 2014-01-03
> **ofnuts said:**
> A very long time ago, I wrote a PC-DOS keyboard driver and debugged it by ear by adding beeps in strategic places in the code :) The code path for alphabetic letters would play the Indiana Jones theme (yes, that long time ago).

That's awesome, I hope someday I'll be good enough at programming in general to make drivers...whew.
That must have sounded so cool when you finally got your code to work!

---

### Post by ofnuts on 2014-01-03
Well, then I removed the beeps :)

---

