---
title: "typing non standard characters"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by taith on 2008-11-26
hey everyone...

does anyone know how to type non-standard characters? like the ï (an i with 2 dots)... i can copy/paste it from the character map... but thats rather slow and annoying...

i know in windows you just hold [alt] and type its decimal entry(239 for the ï)... but its not doing anything here...

---

### Post by Titan8990 on 2008-11-26
There might be an easier way but you can go to System -> Preferences -> Keyboard Layout

and add US-intl for accent marks.


I recommend leaving the standard 104-105 US layout as your default.

---

### Post by dnairb on 2008-11-26
Try this:

Hold [shift], [control] and [u] together (ignore the underlined u on screen)
type the unicode number (again ignore output)
press [enter]

example:

[shift][control[u] 00ef [enter] produces: ï

---

### Post by taith on 2008-11-26
> **dnairb said:**
> [shift][control[u], 0176 [enter] produces: &#374;

perfection! thanks!

---

### Post by dnairb on 2008-11-26
You're welcome.

It does mean one has to go through the whole character set, noting the codes for each character. But then it's easy after that.

---

### Post by CGS_Saltire on 2008-11-28
Hi,
I have a similar problem but it is with the Euro symbol... I tried using your technique but it keeps giving me the Null symbol instead of the C with the two strokes through the middle.

I have tried installing new European language bases and used synaptic to search for the symbol and install it but I still have the Null symbol. Even switching from USA (International) to UK with dead keys or Irish doesn't help. I enabled the third level moderator on one of my Win keys but each time i use it I still get the same result.

Typing the pound symbol is easy as is other symbols but this is eluding me!:confused:

Steve

---

### Post by Maringouin on 2008-12-11
If you make one key into a Compose key, you can type a lot of non-standard characters quite easily:

[www.hermit.org/Linux/ComposeKeys.html]("http://www.hermit.org/Linux/ComposeKeys.html")

As far as I've been able to tell so far, this works with inputting non-standard characters in Open Office, Text editor and also the Bibus bibliographic software--great!

My problem with this system is that I can only get Unicode characters up to U00ff; after that, nothing seems to work.

Since I need quite a few characters above that, especially letters with macrons (small lines over them), I'd be grateful if anyone can give me an easy way of inputting them, e.g. with the Compose key. For the meantime, thanks for the method of inputting using the Unicode.

---

### Post by dnairb on 2008-12-12
> **CGS_Saltire said:**
> Hi,
I have a similar problem but it is with the Euro symbol... I tried using your technique but it keeps giving me the Null symbol instead of the C with the two strokes through the middle.

I have tried installing new European language bases and used synaptic to search for the symbol and install it but I still have the Null symbol. Even switching from USA (International) to UK with dead keys or Irish doesn't help. I enabled the third level moderator on one of my Win keys but each time i use it I still get the same result.

Typing the pound symbol is easy as is other symbols but this is eluding me!:confused:

Steve

The code for € is 20ac

i.e.:

[shift][control[u] 20ac [enter] produces: €

---

### Post by MarkieB on 2010-04-04
no longer participating in ubuntuforums.org

---

