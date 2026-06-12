---
title: "Source Hierarchy"
date: 2010-03-11
forum: Programming Talk
---

### Post by Penguin Guy on 2010-03-11
By following the [Ubuntu Python Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Python") and the [Python Distutils Guide]("http://docs.python.org/distutils/index.html") I finally managed to create a working package. I've attached it below in the hope it'll be useful to someone in the future. Thanks to [snova]("http://ubuntuforums.org/member.php?u=571996") for the help!

**Blobber**
I've attached a copy of the original source package below in the hope that it'll be useful to someone in the future. The upstream project is now registered on Launchpad: [https://launchpad.net/blobber](https://launchpad.net/blobber)

---

### Post by snova on 2010-03-11
I would suggest laying out files according to [these guidelines]("http://jcalderone.livejournal.com/39794.html").

You only seem to have one file, so the third item would apply. I think manually adding lib/ to sys.path is weird though; just move vec2d.py up a level. Alternatively, moving everything into a foodchain/ package would also work.

I also took a look at the code itself, and I would like to say I don't like **Property()**- it's way too magical. What's wrong with the builtin **property()** function?

And it runs out of enemies too quickly. :)

---

### Post by Penguin Guy on 2010-03-11
> **snova said:**
> I would suggest laying out files according to [these guidelines]("http://jcalderone.livejournal.com/39794.html").

You only seem to have one file, so the third item would apply. I think manually adding lib/ to sys.path is weird though; just move vec2d.py up a level. Alternatively, moving everything into a foodchain/ package would also work.

I also took a look at the code itself, and I would like to say I don't like **Property()**- it's way too magical. What's wrong with the builtin **property()** function?

And it runs out of enemies too quickly. :)
The guidelines had the simplicity that I was looking for, but I really wanted something official (you know, with makefiles and stuff) so Launchpad can do all it's automatic mumbo-jumbo.
As for the code - I think the [FONT="Courier New"]Property()[/FONT] function makes the code a lot clearer- although there is no real need for it. Also, this is only attempt 1, in later versions I will be spawning more enemies.

---

### Post by snova on 2010-03-11
> **Penguin Guy said:**
> The guidelines had the simplicity that I was looking for, but I really wanted something official (you know, with makefiles and stuff) so Launchpad can do all it's automatic mumbo-jumbo.

Makefiles in Python are a rarity. distutils is what most Python packages use for installation (setup.py files).

What exactly do you want Launchpad to do?

> As for the code - I think the [FONT="Courier New"]Property()[/FONT] function makes the code a lot clearer- although there is no real need for it.

It's a pretty thin wrapper, serving only to make a new syntax. Changing the way things look for no reason isn't particularly "clear" to me, but more importantly, relying on weird stack introspection tricks (or magic to any degree) is usually a bad idea. It seems like something prone to failing.

---

### Post by Penguin Guy on 2010-03-12
> **snova said:**
> What exactly do you want Launchpad to do?
Turn it into a [FONT="Courier New"].deb[/FONT] and make it available through my repository.

---

### Post by snova on 2010-03-12
> **Penguin Guy said:**
> Turn it into a [FONT="Courier New"].deb[/FONT] and make it available through my repository.

The last time I tried building a .deb from Python code, whatever I used (cdbs?) had good distutils integration and it more or less packaged itself that way.

So, I'll point you in [this direction]("http://docs.python.org/distutils/index.html") for writing setup.py files, but I can't help with actually packaging things.

---

### Post by Penguin Guy on 2010-03-12
> **snova said:**
> The last time I tried building a .deb from Python code, whatever I used (cdbs?) had good distutils integration and it more or less packaged itself that way.

So, I'll point you in [this direction]("http://docs.python.org/distutils/index.html") for writing setup.py files, but I can't help with actually packaging things.
That's exactly what I've been looking for! I'll get writing the [FONT="Courier New"]setup.py[/FONT]! I'll mark this as solved for now because I *think* I can figure out the rest for myself.

Thanks!

---

