---
title: "Open and edit a document with AI extension (Adobe)"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by honeybear on 2011-10-04
Hello,

I would like to know under linux what would be the best program to edit and modifiy a document with AI extension (Adobe Illustrator) ? 

Thank you !

:popcorn:

---

### Post by cavh on 2011-10-04
You are probably better off to post your question in the Art & Design forum as that's where the arty types tend to hang out :)

The Art forum is [here]("http://ubuntuforums.org/forumdisplay.php?f=16")

---

### Post by mcduck on 2011-10-04
> **honeybear said:**
> Hello,

I would like to know under linux what would be the best program to edit and modifiy a document with AI extension (Adobe Illustrator) ? 

Thank you !

:popcorn:

To be honest, there is no such program. .ai  is Adobe's proprietary format and the only program that can fully handle it is Illustrator.

You might be able to run Illustrator with Wine, although last time I did that was with CS2 and it required some trickery to get working (like installing on a Windows machine and copying some registry keys from there to Wine by hand).

Inkscape has some level of .ai support, but you definitely shouldn't expect it to correctly open every .ai file you throw at it. It is a great vector graphics app, though, so if working in .ai format isn't an absolute requirement you should definitely check it out. (I've pretty much fully replaced Illustrator with Inkscape these days myself).

---

### Post by honeybear on 2011-10-04
> **mcduck said:**
> To be honest, there is no such program. .ai  is Adobe's proprietary format and the only program that can fully handle it is Illustrator.

You might be able to run Illustrator with Wine, although last time I did that was with CS2 and it required some trickery to get working (like installing on a Windows machine and copying some registry keys from there to Wine by hand).

Inkscape has some level of .ai support, but you definitely shouldn't expect it to correctly open every .ai file you throw at it. It is a great vector graphics app, though, so if working in .ai format isn't an absolute requirement you should definitely check it out. (I've pretty much fully replaced Illustrator with Inkscape these days myself).

that's bad because most of the vectors files are usually *.ai. Actually that's very bad.

wine is buggy and slow :( 

Is inkscape as good as Adobe Illustrator?

---

### Post by mcduck on 2011-10-05
> **honeybear said:**
> that's bad because most of the vectors files are usually *.ai. Actually that's very bad.

wine is buggy and slow :( 

Is inkscape as good as Adobe Illustrator?

If you ask me, it's a lot better. ;) That's why I have replaced Illustrator with Inkscape on my work. SVG is pretty popular format as well, and highly compatible between different programs, web standards etc.

Of course that doesn't help if you need to work together with people who only know how to use Illustrator (or simply refuse to use anything else, whcih seems to be the case quite often). In that case using Wine, virtual machine or dual booting for Illusrator are the only options.

---

