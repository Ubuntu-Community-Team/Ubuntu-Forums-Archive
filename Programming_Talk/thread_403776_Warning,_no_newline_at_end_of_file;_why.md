---
title: "Warning, no newline at end of file; why?"
date: 2007-04-07
forum: Programming Talk
---

### Post by M$LOL on 2007-04-07
Why does GCC warn about not having a newline at the end of the file? What difference would it make to the compiled program? :-k

---

### Post by treak007 on 2007-04-07
its part of the language standard:

"A source file that is not empty shall end in a new-line character, which shall not be immediately preceded by a backslash character."

---

### Post by Fhernd on 2008-06-19
Hi!


That's not an error. It's just a warning.

Open the file in an editor, go to the last line of the file, and hit enter to add a blank line to the end of the file. :)

Though, besides that, you should be using #include <iostream> instead of <iostream.h>. Then put in a "using std::cout;" after it.


So long!

---

### Post by KingTermite on 2008-06-19
Did it warn you that there was no newline at the end of the file, or did it say something like "reached the end of file and no EOF character found" (or something like that?).

I ask because the 2nd one is an error I've seen in Visual Studio many times when you have mismatched (usually missing) braces.

---

### Post by xlinuks on 2008-06-19
> **treak007 said:**
> its part of the language standard:

"A source file that is not empty shall end in a new-line character, which shall not be immediately preceded by a backslash character."

This is something I would really want C/C++ to get rid of. It has nothing to do with "real programming" but rather with "bureaucracy", I've been programming for years in other languages and did fine without this annoying issue.

---

### Post by LaRoza on 2008-06-19
> **xlinuks said:**
> This is something I would really want C/C++ to get rid of. It has nothing to do with "real programming" but rather with "bureaucracy", I've been programming for years in other languages and did fine without this annoying issue.

Tell the working group: ISO/IEC JTC1/SC22/WG14.

(Now you know why it is "bureaucracy", a committee made it)

---

### Post by xlinuks on 2008-06-19
The ISO is lately no more a "committee" for me and a lot of other persons, but a bunch of losers, after what they did with ooxml.

---

### Post by RIchard James13 on 2008-06-20
Yes the standard is stupid but we should either ignore the warning or alter our files. I alter my files, if I want the standard to be changed I will also want to win lotto. I know which one will happen sooner :)

---

### Post by evymetal on 2008-06-20
I disagree (slightly) - It's always a good idea to end files in a newline, especially in Unix (for back compatibility reasons). 

e.g. when running a shell script or something that requires a newline to tell the program to run that line

---

### Post by kutlu on 2010-01-16
when this file is included somewhere, it will be problem.

it replaces itself with include statement, and a replacement without a new line is sometimes problematic.

Once, I had a tough day since visual studio does not give this warning, and an unsolvable error instead.

so, put the new line there! I am serious.

---

