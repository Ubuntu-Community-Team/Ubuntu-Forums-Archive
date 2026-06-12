---
title: "Can't use Accent Marks :("
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Jason2gs on 2008-04-30
Hiya :)

I was on my computer yesterday, and decided to try and get accent marks working. I searched Google, and found a thread on the ubuntuforums about how someone who was trying to get it to work.

[http://ubuntuforums.org/showthread.php?t=74638](http://ubuntuforums.org/showthread.php?t=74638)

I did what it said, but it didn't work for me.

I have the Compose Character set to the left Windows key, and I use:

```
Left-Win + ` + a
```

And it just prints "`a"...

I read about the .Xmodmap file, as well, and created it in my $HOME directory. I have the following line in it:

```
keycode 115 = Multi_key
```

Keycode 115 is the left Windows key. I found that out by using xev.

I saved it, logged out, logged back in, fully expecting it to work. It didn't. It still only prints "`a".

Could I get some help on this? I'd really like to be able to use accent marks by simply pressing a key combination, and not having to use the character map utility :)

Thanks for reading,

-Mike

Edit: And to (whoever/whomever) changed it, I like the new look of the forums! It has a very clean look to it.

---

### Post by Jason2gs on 2008-04-30
Wow, busy day today. Bump?

---

### Post by annda on 2008-04-30
strange, it works for me too. what is your keyboard model in keyboard preferences? that may be a factor. do you have generic 105-key international or something else?

---

### Post by Jason2gs on 2008-04-30
Lemme grab that, and thanks for the reply :)

[IMG]http://img403.imageshack.us/img403/3458/screenshotkeyboardprefecp0.png[/IMG]

Edit: It did cross my mind that having the Dvorak keyboard configured may complicate things, so I tried it again after removing it. Didn't help.

Edit #2: I just checked my laptop on HP's website:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00783092&lc=en&cc=py&product=3231960)

And it says that the keyboard is 101-key compatible. Does that mean the only option is to use the 101-key PC keyboard? Tried that, and it's still not working :(

---

### Post by annda on 2008-04-30
the standard configuration works with my laptop keyboard (a samsung) and the usb apple keyboard.

can anyone confirm this (i mean having a problem with an HP laptop)?

in the spirit of trying to figure out a solution when no "solvers" post, i'd recommend trying out all the compose keys available. and if you have spare time, pop in the live cd and see if it works...

---

### Post by Jason2gs on 2008-04-30
Ah, LiveCD. Splended idea ;) I'll try that as soon as I get the chance, and post here with the results.

---

### Post by Jason2gs on 2008-04-30
Alright. Just tried the Ubuntu LiveCD, and it worked. I don't know how, but I was able to type with accent marks.

If it matters, I have figured out where my xmodmap file is. It's located at /usr/share/xmodmap/xmodmap.us_intl

Mm, don't have anything else to add...

*Sits back and waits for a Solver*

---

### Post by Jason2gs on 2008-05-01
Bump.

---

### Post by Vicfred on 2008-05-01
Use the US International with Dead keys it works fine, I think the keyboard model doesn't matter.

[IMG]http://img247.imageshack.us/img247/7695/keyboardvicmu0.png[/IMG]

---

### Post by Jason2gs on 2008-05-01
Hey it works! Thank you :)

Not quite sure what keys are 'dead', but it seems the majority of them do...

---

### Post by Jason2gs on 2008-05-01
Mm... Where are the different keyboard layouts kept? If I have three differnet layouts configured (U.S., U.S. Dvorak, and U.S. International with dead keys.), they can't all be kept in one file. Can they? Reason I'm asking, is because some of the keys on the Dead Key layout, I simply don't like. For instance, the ['] and ["] keys turn out to be [´] and [¨] :(

I know it should be possible, but I can´t figure out any way to do it...

Thanks again,

-Mike

---

### Post by Vicfred on 2008-05-02
I just use one type of english keyboard when I want to an accent I just type the apostrophe then I type the letter, when it's an apostrophe ['] I type the apostrophe then I type a space, maybe it's your keyboard I'm using a spanish keyboard (it looks almost like this: 
[http://en.wikipedia.org/wiki/Keyboard_layout#Spanish_.28Latin_America.29](http://en.wikipedia.org/wiki/Keyboard_layout#Spanish_.28Latin_America.29)) maybe you modified something before, reset your keyboard preference and then use the us international with dead keys

---

