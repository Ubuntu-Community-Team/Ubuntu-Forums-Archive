---
title: "Impossible to work with files named &quot;con&quot;"
date: 2007-09-11
forum: Programming Talk
---

### Post by xlinuks on 2007-09-11
Hi!
I came across a weird problem. I'm creating home an application in Java (on  Ubuntu) and testing it at work (on windows).
When I come to work and try to copy the files onto my windows box, there are two of them which don't wanna copy, the files: "Con.class" and "Con.java". I found out that this is done in purpose, that Bill Gates didn't like this word (the "con" word) so he made sure no one can create a file with such a name on windows with whatever extension it might be.

Does anyone know if this is the _real_ reason??

Did anyone have similar problems, or, did you as I programmer know that  you might have such "cross-platform problems"?

I tested it on several computers running windows XP SP2.

---

### Post by fct on 2007-09-11
If I remember correctly "con" is a reserved keyword in MS-DOS, so files named "con" are disallowed because it clashes with the keyword.

---

### Post by lisati on 2007-09-11
> **fct said:**
> If I remember correctly "con" is a reserved keyword in MS-DOS, so files named "con" are disallowed because it clashes with the keyword.

It is also reserved in a command-line prompt under windows, and is is short for "console"

---

### Post by fct on 2007-09-11
> **lisati said:**
> It is also reserved in a command-line prompt under windows, and is is short for "console"

Yep. Considering the shell of Windows has basically the same design of MS-DOS when it comes to the language, that's expected.

---

### Post by rivalarrival on 2007-09-11
I just stumbled on this same phenomenon while looking for command line based internet mail retrieval programs.

No, there is no malicious intent, just some historical significance...

There are actually (at least) 6 hidden files in every DOS/Windows directory: "." ".." NUL, PRN, CON, and AUX. This comes in from early DOS days: back in 1981, if you wanted to print some text in DOS, you wrote that text to a file called PRN.  If you wanted to send it to the serial port, you wrote it to a file called AUX. CON, I believe, is sent to the Console, and NUL went into the bottomless pit of despair.

Unix systems work similarly: saving a file to /dev/null, for instance, sends it to that same bottomless pit of despair. Unlike Unix, Microsoft wrote these "device" files to EVERY DIRECTORY ON THE DISK!!! Any file you save as con, aux, prn, or nul anywhere on a microsoft system since 1981 just disappears.

There's some more detail here:
[http://heirloom.sourceforge.net/mailx_aux_c.html](http://heirloom.sourceforge.net/mailx_aux_c.html)

---

### Post by osx424242 on 2007-09-11
obligatory quote...
REAL programmers use "copy con"...

---

### Post by xlinuks on 2007-09-11
OMG the system in windows is so dumb!
rivalarrival you seem to be right, I tried creating "aux.txt" and I just can't! Thanks for the comprehensive explanation!

---

### Post by xlinuks on 2007-09-11
I can't believe that they haven't removed these shortcomings yet!
I wonder whether the same behaviour happens in Vista.

---

