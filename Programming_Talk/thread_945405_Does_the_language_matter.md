---
title: "Does the language matter?"
date: 2008-10-12
forum: Programming Talk
---

### Post by ChrisBookwood on 2008-10-12
Hi,

I have never made any such extension for linux, or actually extension for anything before - sure, i have fiddled different small standalone apps together, but never anything which should be an extension for Linux.
Now it's going to change... I have this little idea about bringen the Gnome Global menu back to life, since I love this (buggy) hack, and want to make it better, greater and more stable.

As before mentioned, I have never done such thing. I know my way around different languages (I'm definetly strongest in C++ when talking Generel Purpose languages), so I wonder how to use it in Linux?
How does the whole process work? I really know nothing about it, and I can't even imagine how I would write a such thing that would work with anything other than it self.


Regards,
ChrisBookwood

---

### Post by lisati on 2008-10-12
For stand-alone programs, C++ is probably fine if it suits the task at hand.

---

### Post by ChrisBookwood on 2008-10-12
Well, what I meant was : but does the language matter if it's an extension (lets say an applet for AWN) I'm writing?

---

### Post by Tomosaur on 2008-10-12
> **ChrisBookwood said:**
> Well, what I meant was : but does the language matter if it's an extension (lets say an applet for AWN) I'm writing?

That depends entirely on AWN :P What language are applets written in - how does AWN execute them? You should be able to find all of this info in the AWN developer documentation.

If you just want to extend AWN itself to include this as a feature, then you'll have to use whatever language AWN itself is written in.

For a standalone program, then no, it doesn't really matter what language you use.

Hope that helps!

---

### Post by ChrisBookwood on 2008-10-12
That really helps, thanks!

I wonder... If you got a extensible app written in C++, would it be able to create extensions for it on python? Actually, I think the question I'm asking is whether two different languages can work together and if positive; How?

---

### Post by nvteighen on 2008-10-12
> **ChrisBookwood said:**
> Hi,

I have never made any such extension for linux, or actually extension for anything before - sure, i have fiddled different small standalone apps together, but never anything which should be an extension for Linux.
Now it's going to change... I have this little idea about bringen the Gnome Global menu back to life, since I love this (buggy) hack, and want to make it better, greater and more stable.

Just a note. If you plan to something related to GNOME, you may be restricted to C or alternatively, to those languages that have bindings to GTK+ and/or the GNOME API. Officially supported are C++, C#, Python, Perl and Java. Look at [http://www.gtk.org/language-bindings.html](http://www.gtk.org/language-bindings.html) (GTK+ bindings) and [http://live.gnome.org/TwoPointTwentyfive/Bindings/](http://live.gnome.org/TwoPointTwentyfive/Bindings/) (bindings to other subparts of the GNOME desktop, such as GnomeVFS, GConf, etc.)

---

### Post by Tomosaur on 2008-10-12
> **ChrisBookwood said:**
> That really helps, thanks!

I wonder... If you got a extensible app written in C++, would it be able to create extensions for it on python? Actually, I think the question I'm asking is whether two different languages can work together and if positive; How?

Again, it depends on what you actually want to achieve.

If the libraries you use have python bindings, then you can use C/C++ and Python together. Many libraries do, in fact, have Python bindings, but you'll have to check for yourself really. Unless the extensible program explicitly supports extensions written in other languages, then whatever solution you come up with is likely to be fairly hackish anyway. The original program needs to be able to load your extension, so unless it explicitly supports extensions written in another language, you won't be able to do it (easily, anyway).

Is there any particular reason you want to use a language other than that which the original program is written in?

Possibly the best (most widely supported and possibly 'easiest') way to get seperate programs written in different languages to work together is to use 'dbus' - but the original program needs to be registered with the dbus system.

So to summarise: Can you write extensions in languages other than the main program? Answer - 'yes, but...'. I would suggest that doing this is just going to lead to complications further down the line.  The easiest way, by far, is to just use the original language and develop your extension the way the developer documentation describes. Don't make it harder for yourself than it needs to be :P

---

### Post by ChrisBookwood on 2008-10-12
You ask why I wanna write the extension in another language?
Well, as it is now,  I don't. But it could happen that i wanted to write an extension for a app written in a language I'm not familiar with. It's just for the sake of knowing things I'm asking.

> So to summarise: Can you write extensions in languages other than the main program? Answer - 'yes, but...'. I would suggest that doing this is just going to lead to complications further down the line. The easiest way, by far, is to just use the original language and develop your extension the way the developer documentation describes. Don't make it harder for yourself than it needs to be :P

I didn't know it worked like that! Interesting...

---

### Post by ChrisBookwood on 2008-10-15
** aah, this was faultly placed here:D

---

