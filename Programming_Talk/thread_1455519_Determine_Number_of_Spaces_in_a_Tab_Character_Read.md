---
title: "Determine Number of Spaces in a Tab Character Read in From Text File C++"
date: 2010-04-16
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-16
Ey guys, I am making a simple programming language so I am reading in from a text file and need to be able to print out an error message similar to the likes of python that points to the problematic variable in the line like so:
```

No loaner variables! at line 53:
51: 3
52: 
53: 	can=b s 4s= f //check behavior with tabs
           ^   //this indicator should be pointing to the single 's' character, but because there is a tab it is off

```
I have it working and everything but am having a hard time with reading in tab characters. I need to be able to determine how many spaces a tab character takes in the file being read so that I can account for it later. Does anyone know how to go about doing this? Thanks!

---

### Post by Bachstelze on 2010-04-16
The tab character, like any other character, normally takes one byte, but I don't think that's what you want to know... Care to explain more precisely?

---

### Post by StunnerAlpha on 2010-04-16
> **Bachstelze said:**
> The tab character, like any other character, normally takes one byte, but I don't think that's what you want to know... Care to explain more precisely?

Sure. So in the following block:
```

53: 	can=b s 4s= f //check behavior with tabs
   ^^^^^

```
the '^'s represent the tabbed amount. That just happens to be 5 in this example, but on different systems and different programs with different settings the tab character can vary. It is often 4 spaces("    "), it can even be 2("  ") or 8 ("        "). But when I read it into my program, my program merely sees that tab as a '\t' character. So I am wondering how to decipher how many spaces a tab character actually represents. Is this even possible? I am having my doubts as I found nothing on this after some extensive googling. Thanks for asking for clarification.

---

### Post by Bachstelze on 2010-04-16
Since as you said, the amount of spaces that represents a tab is normally program-defined, there is probably no universal way to do it (you would have to query the program responsible for display and ask it how many spaces it uses, provided it supports this at all).

I think it is a safe assumption, though, to consider that a given user doesn't mix tabs and spaces, so you could just check for *either* a tab or a given number of spaces, which will probably be constant throughout a given program.

---

### Post by StunnerAlpha on 2010-04-16
> **Bachstelze said:**
> I think it is a safe assumption, though, to consider that a given user doesn't mix tabs and spaces, so you could just check for *either* a tab or a given number of spaces, which will probably be constant throughout a given program.

Wait, I can't check for one OR the other I have to know both so that I can position the indicative symbol '^' in the right position. So if I have a line with tabs and spaces, which is very common in program files I will come across spaces as spaces(' ') which is not a problem, but if I come across a tab('\t') I have no idea of knowing how many spaces that tab character represents. So I have no idea how many character spaces I should move over the '^' symbol to have it point to the proper character in the line above it. I could always just hard code it, but that would be a very crude approach, and I would not like to go that route. If you happen to have any other thoughts please let me know. Thanks.

---

### Post by Bachstelze on 2010-04-16
> **StunnerAlpha said:**
> Wait, I can't check for one OR the other I have to know both so that I can position the indicative symbol '^' in the right position.

If the code is indented with tabs, just ident the '^' with tabs too, it will be aligned with other tabs. ;)

---

### Post by StunnerAlpha on 2010-04-16
/hand to the face, Why didn't I think of that??? Haha, I'll try that, thanks.

---

