---
title: "Python issues..."
date: 2012-02-15
forum: Programming Talk
---

### Post by ph4nt0m117 on 2012-02-15
Hello!

My current problem is quite hilarious to me...  I don't know about you, reader, but funny to me.

I am currently working on a web browser in python with Vim.  In scripting the program I try to run it before I continue to see if any bugs are in it.  This came up:

Line 3: stynax error in gtk.Window() between 'Window' and ,'('

When I went to see if I was dumb and put a space there, there wasn't anything at all.

So, again I put in the prompt "./browser.py" and the same stynax error.

I updated everything, got a new image installed as well, 500000 things inside of Grub, but nothing was fixed, it still spouted FU LALALAL at me.

Now, now I feel like ripping the sript appart for fun :D

What do.

---

### Post by Tony Flury on 2012-02-15
try deleting that line - and retyping it

It might be you have a funny invisible character in there. It does look like an odd error message.

---

### Post by zippaplick on 2012-02-15
What is the first line of your script?

Does it start with:

```
#!/usr/bin/env python
```


If it doesn't then its invoking the shell, not python, to run the script.

Alternatively, try running it with python directly:

```
python browser.py
```

---

### Post by Tony Flury on 2012-02-16
> **zippaplick said:**
> What is the first line of your script?

Does it start with:

```
#!/usr/bin/env python
```


If it doesn't then its invoking the shell, not python, to run the script.

Alternatively, try running it with python directly:

```
python browser.py
```

Good catch - did not think about that one - my excuse - the shebang line is automaticly added for me by the editor - so i don't even notice it :-)

---

### Post by zippaplick on 2012-02-16
> **Tony Flury said:**
> Good catch - did not think about that one - my excuse - the shebang line is automaticly added for me by the editor - so i don't even notice it :-)

Sweet. Beware of things that should automagically happen. ;)

---

### Post by ph4nt0m117 on 2012-02-16
> **Tony Flury said:**
> Good catch - did not think about that one - my excuse - the shebang line is automaticly added for me by the editor - so i don't even notice it :-)

If I could set VIM up like that I would XD

And yes I put it into python through the shebang line.

I will try putting python in front...  Or rage for eternity.  Either way :D

---

### Post by Tony Flury on 2012-02-16
Try posting your code - or at least the first few lines, and tell us what you have called your files.

---

### Post by HotCupOfJava on 2012-02-16
Interesting problem, but, you're doing a WEB BROWSER? REALLY?

I can't help but ask why.....is it just for giggles?

Hey - more power to ya.

---

### Post by ph4nt0m117 on 2012-02-17
Hobbyist project for shits.

Mainly what I am going to have it dois go around a schools proxy rules so that youcan go to what ever site you like.  Even moreso if SOPA/PIPA/ACTA are passed yet.  Though all that stuff has calmed down so no idea if that will be an issue.

---

### Post by HotCupOfJava on 2012-02-17
A proxy huh? It may be more complicated than just a custom browser, depending on what firewall rules you'll be dealing with - a closed port that is refusing connections, etc.

But hey, sounds like an educational process! You'll undoubtedly learn quite a bit, whether or not you succeed.

---

### Post by ph4nt0m117 on 2012-02-17
Many things have come to mind, like firewalls and such.  The browser would probably be aimed at medium to low level advanced users because it may have a few tools put in it to go around the firewalls and such.  As well as around the governments block on the sites (SOPA, etc...).

When the first release is done I'll probably post it.

---

