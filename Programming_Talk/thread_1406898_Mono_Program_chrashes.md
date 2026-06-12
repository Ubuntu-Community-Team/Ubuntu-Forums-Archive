---
title: "Mono Program chrashes"
date: 2010-02-14
forum: Programming Talk
---

### Post by Sjums07 on 2010-02-14
Hello folks, I've looked threads in here a lot, and found a lot of answers, but can't find one for this :/

Well, I've been programming a lot of C# on windows, but now I converted entirely to ubuntu ;)

So I've began to use Mono (guess why). Though i have a big problem :/ I have this program (very simple), but when i run it it crashes half way throug :(

I've attached two files, one is when i run "mono filename.exe &> debug.txt" and the other is "mono -v filename.exe &> debug-v.txt". I really hope for an answer on this one :popcorn:

//Sjums

---

### Post by SemiBuz on 2010-02-14
[http://www.mono-project.com/Interop_with_Native_Libraries#Strings_as_Return_Values](http://www.mono-project.com/Interop_with_Native_Libraries#Strings_as_Return_Values) - honestly, shooting in a dark wood as you haven't shared a single line of your code.

---

### Post by Sjums07 on 2010-02-15
you have a point there :)

[http://pastebin.com/f33a02c55](http://pastebin.com/f33a02c55)

---

### Post by SemiBuz on 2010-02-15
Check the getSource() return value - it might be empty.

---

### Post by Sjums07 on 2010-02-15
checked it several times now, and it returns a string every time. Also tried to make a void function to do a "click" but it still crashes.

---

### Post by Sjums07 on 2010-02-16
hmm, copy-pasted the code into a console program (ofc edited labels, etc.), and there have been no problems at all so far..

---

