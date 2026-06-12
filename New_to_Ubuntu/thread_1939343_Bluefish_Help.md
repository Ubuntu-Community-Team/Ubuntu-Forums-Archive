---
title: "Bluefish Help"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by pentathlos on 2012-03-11
Hello everybody, I've just recently got the opportunity to come back to Ubuntu (yay!) but with a huge disappointment I could not find the function that I was appreciating the most of my programming editor of choice (Bluefish): the "find in project" function. At first it looked absolutely impossible for me that such a helpful function was removed from the editor, but I couldn't find any reference to it in any manual.
So my question is the following: is there any new way of doing it (other than opening all the files and using "search in all opened files")? If not: is there any other light program that could do it?

PS: if there is any Bluefish developer reading this: please take that function back ! It was really helpful for people working with large projects and also was a distinctive function of this program (I've never found it in any other php editor) !
(I tried to look for their forum but couldn't find it >.<)

Thank you very much for the help !
*penta*

---

### Post by andrew.46 on 2012-03-12
I can see the feature you describe in the 'advanced' window for Find. Screenshot attached. Hopefully this is what you are after?

---

### Post by pentathlos on 2012-03-12
In fact I cannot understand why they did _remove_ such a helpful feature. Zen mutilation?

The only scope options in the actual version (at least the one that I downloaded from Ubuntu Software Center) are:
- entire document
- forward from cursor
- selection
- all open files

*Penta*

---

### Post by pentathlos on 2012-03-13
Oh, dear Bluefish programmers, I see what you did there ! Too smart for me indeed.
Your documentation anyway is a little bit unordered (at least the ones that Mr. Google suggested to me), therefore I'll explain the found solution for future searchers:

[LIST=1]
[*]open you project
[*]file -> close all
[*]file -> open advanced
[LIST]
[*]bae dir: select the directory that you want Bluefish to scan
[*]pattern: *
[*]recursive: true
[*]contains -> pattern: here you insert the text to be searched
[*]open
[/LIST]
[*]now simply edit -> replace -> scope("all open files")
[/LIST]
and it's done.
o/

---

