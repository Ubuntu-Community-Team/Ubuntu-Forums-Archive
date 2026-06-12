---
title: "Integrating a Mathematical Keyboard With TeX"
date: 2009-06-23
forum: Programming Talk
---

### Post by Penguin Guy on 2009-06-23
I am trying to make a [[COLOR="Blue"]mathematical keyboard[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195145") and this topic is about integrating it with various Linux programs. Any code can be posted [[COLOR="Blue"]here[/COLOR]]("https://code.launchpad.net/~joshbrown/+junk/GTeX") (just send me a message if you want permissions to add code or anything).

Perhaps Open Office formula editor for a start?

One way we could integrate it is to make the keyboard output the correct characters for what we want - however this does not seem a very professional approach.

---

### Post by hessiess on 2009-06-23
This is completely dependent on the text editor you are using, you would just need to map the key as a macro which outputs `\pi' or whatever.

---

### Post by Penguin Guy on 2009-06-23
I understand that, but I am wondering if there is a Unicode(?) TeX editor for Linux. So you press the key that has a picture of pi on and a picture of pi appears on the screen rather than \pi appearing on the screen.

---

### Post by hessiess on 2009-06-23
Any text editor which supports unicode should be able to do that. You would also need to use XeTeX.

---

### Post by hugmenot on 2009-06-24
> **Penguin Guy said:**
> I'm planning on making a [[COLOR="Blue"]mathematical keyboard[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7504354") with mathematical symbols on, which can (hopefully) be used with TeX.

Perhaps all I will need is a keymap . However, if there are no Linux TeX programs that support Unicode-thingy(?) input then hopefully we can write a program that *does* support Unicode-thingy(?) input.

When I say 'Unicode-thingy(?)', I am talking about pressing a pi key and pi appearing on the screen - just like normal typing rather than how LaTeX works. I would appreciate it if someone could give me a name for this.


I don&#8217;t think it&#8217;s going to work like that. If I understood you correctly you expect to be typing math formulas directly in a WYSIWYG fashion. I don&#8217;t now any system that does this. Either they are syntax-based and interpreted or they are plugged together via buttons and shortcuts.
LaTeX of XeTeX certainly require real TeX syntax. I mean, it&#8217;s easy to type some symbols in Unicode like this: &#8776;&#937;&#8704;&#8707;&#969;&#964;&#8592;&#8595;&#8594;&#961;Ø&#931;&#963;&#948;&#916;&#966;&#915;&#949;&#960;&#945;&#954;&#733;µº but these aren&#8217;t all that you need to typeset formulas. You need actual brackets, matrix syntax, fractions super and subscripts, etc. This is only possible with proper scoping and old fashioned syntax.

---

### Post by Penguin Guy on 2009-06-24
**hessiess:** Normal text editors don't work - how would you do fractions?

> **hugmenot said:**
> I don’t now any system that does this.
My calculator. But no, as far as I know there are no Linux WYSIWYG TeX editors.

---

### Post by Penguin Guy on 2009-06-24
I've set up a Launchpad project for this since I expect the program will be pretty big.

---

### Post by Can+~ on 2009-06-24
I don't get the idea of the project; are you trying to create an analog to Word's Equation editor?

---

### Post by jpkotta on 2009-06-24
In Emacs, I would do something like
```
(local-set-key (kbd "p") "&#960;")
```
for each key I wanted to reassign.  But how are you going to type Roman letters if all of your keys are bound to Greek/math symbols?  And why don't you use something like Lyx?

---

### Post by hessiess on 2009-06-25
> **Penguin Guy said:**
> **hessiess:** Normal text editors don't work - how would you do fractions?.

The TeX typesetting engine is *NOT* designed to be WYSIWYG, and to be honest, that is what I personally like about it, and WHY it manages to produce superior typesetting to GUI programs(it does not have to be real time). If you want your whole equations to appear visually, not just greek characters, TeX is not what you are looking for, try the OO equation editor.

---

### Post by Penguin Guy on 2009-06-25
> how are you going to type Roman letters
Either two keyboards or an on-screen keyboard.

I see that there are actually a lot of GUI formula programs so I suppose it would be best to just try and integrate a keyboard into as many of them as possible.

---

### Post by fr4nko on 2009-06-25
> **Penguin Guy said:**
> My calculator. But no, as far as I know there are no Linux WYSIWYG TeX editors.
I believe that a WYSIWYG TeX editors already exists, is [TeXmacs]("http://www.texmacs.org/"). Probably you should consider this project as a starting point and see if you can adapt the code for a gnome environment.

Personally I don't like this application, I prefere to use LaTeX directly, but it is nevertheless a remarkable software.

Francesco

---

