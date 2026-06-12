---
title: "baseband signal not registering in sound card"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by nycap on 2012-11-28
sending baseband signal to "line in" but its not showing up in the sound card.  it works in windows so i know my disc tap is good.  Any ideas would be much apprecitated.

---

### Post by audiomick on 2012-11-28
Ummm, what is a baseband and what do you mean by "disc tap"? Excuse my ignorance. I am only a sound engineer. Don't understand all this modern computer stuff.... ;)

---

### Post by nycap on 2012-11-28
i was remiss in not explaining this but i not exactly sure myself.  all i know is its a radio frequency signal that is unfiltered.  it is found in a receiver at the discriminator chip; hence the name "discriminator tap".   so whats the point?  in order to do signal processing in the computer with code (instead of the receiver with circuits) i need to feed what is loosely called baseband audio into the soundcard.

---

### Post by audiomick on 2012-11-28
OK, I found this
[http://en.wikipedia.org/wiki/Baseband]("http://en.wikipedia.org/wiki/Baseband")

What is it you are trying to do? Generate audio in some form, or is it more in the radio area?

Any rate, can you see a signal from anything at all on that input? Headphone out from a phone, or an mp3 player or something?

---

### Post by nycap on 2012-11-28
just want to do signal processing in the software, call it a hobby.  but no i dont get any signal from the soundcard "line in"

---

### Post by audiomick on 2012-11-28
You'd better post which version of Ubuntu you are using.

I suppose you have already checked all the setting in the mixer thing to make sure it isn't just muted or something?

---

### Post by nycap on 2012-11-28
im using the latest version of ubuntu.  yeah its not muted.  its getting audio from the mic array but not the "line in"

---

### Post by audiomick on 2012-11-29
I've got a drop down list for choosing record source, as in the screenshot. You would have checked that too, I guess.

---

### Post by nycap on 2012-11-29
i went to sound settings and selected "line in".  but my menu looks different that what you show.  thanks

---

### Post by audiomick on 2012-11-29
> **nycap said:**
>  but my menu looks different that what you show.  thanks
Yeah, you are on 12.10, aren't you? This machine is still on 10.04.

You could try looking at the alsamixer in the terminal, though I don't know if that will change anything. I also don't know if it is installed by default, but I think so.

Anyway, in the terminal
```
alsamixer
```

Look in the top left and right corner for the Fx keys for changing what you are looking at and esc to quit. Use the left-right cursor arrows to move from element to element, and the up-down arrows to changed the values.

---

