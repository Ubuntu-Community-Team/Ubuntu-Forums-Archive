---
title: "[SOLVED] Problems with spanish accents in Latex"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by fulgencio on 2008-07-01
Hi, I'm trying to write accents in spanish using latex, I normally just use \'e to obtain é, but now I'm interested in writing the accent in the source (for easy spell checking mainly) and it is giving me some trouble, for example if I input: 
[PHP]\documentclass{article}
\usepackage[spanish]{babel}
\usepackage[latin1]{inputenc}
\begin{document}
Gracián: Lo bueno, si breve...
\end{document}
[/PHP]

I get all this strange characters instead of what I want 

[PHP]
      &#771;
GraciA¡n: Lo bueno, si breve...

[/PHP]

I'm using Texlive, I've installed everything that seemed relevant

---

### Post by ChameleonDave on 2008-07-01
Surely LaTeX is not able to accept accents in its source?

Have you read some documentation that suggests otherwise?  If so, follow it; if not, then don't try it!

---

### Post by fulgencio on 2008-07-01
I also thought latex wouldn't accept it but apparently it does, I'm reading
a pretty common book: [lshort-spanish]("http://tezcatl.fciencias.unam.mx/tex-archive/info/lshort/spanish.zip")

---

### Post by ChameleonDave on 2008-07-01
> **fulgencio said:**
> I also thought latex wouldn't accept it but apparently it does, I'm reading
a pretty common book: [lshort-spanish]("http://tezcatl.fciencias.unam.mx/tex-archive/info/lshort/spanish.zip")

Interesting.

I can't find the part of that document that says that you can input accents directly.  In fact, it has sections explaining the usual Babel escapes.

However, looking at the source code of that document, I can see that they have indeed directly inputted the accents for the Spanish text.  When I opened the source in Kate, the accents didn't appear correctly, because the file was apparently saved as UTF but with non-UTF encoded characters.  I experimented with different encodings, until I managed to open it correctly as "ISO 8859-9".

I suspect that this is a feature only available in LaTeX2e, rather than plain LaTeX. 

I shall play with this a bit more, because I am interested in my French documents being free of all those awful Babel escapes for the many accents.

---

### Post by fulgencio on 2008-07-02
thanks, keep me informed.

---

### Post by ChameleonDave on 2008-07-02
Got it.

Try this code:

```

\documentclass[]{article}
\title{Test}
\usepackage[spanish]{babel}
\selectlanguage{spanish}
**\usepackage[utf8]{inputenc}**
\begin{document}

\huge{¿Está bien así en español?}

\end{document}

```

Make sure it is saved as UTF-8.

Then LaTeX it.  It works for me.  Yay!

---

### Post by fulgencio on 2008-07-02
Works great here too!!!! thanks a lot.

---

### Post by km0r3 on 2010-05-19
Thanks! Solved my problem!

---

