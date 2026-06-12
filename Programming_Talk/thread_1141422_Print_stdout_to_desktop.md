---
title: "Print stdout to desktop"
date: 2009-04-28
forum: Programming Talk
---

### Post by loomsen on 2009-04-28
Hello.

Well, the header basically asks. Is it possible to redirect output of foobar to desktop?

Like, for instance running cal after login and print it to the background somewhere?

Thank you.

---

### Post by benj1 on 2009-04-28
i think conky can do things like (never used it) that or osd_cat for just text, another option if you want a window is zenity

---

### Post by soltanis on 2009-04-28
If you run conky in the background and change the .conkyrc file to simply execute your program and display the output, you can accomplish this.

---

### Post by loomsen on 2009-04-28
Yes, I'm aware of conky, thank you both.

But I don't want to use conky, just print the output do my rootwindow upon login. For my purpose, conky just doesn't do what I want.
Btw, I like tnote benji :) (but what I wanted to ask you, if I take a not over more than one line, do I have to issue \ and the end of a line or would tnote do this automagically? Like if'd I want to run 
foobar `tnote X`
)

So, anybody?

---

### Post by benj1 on 2009-04-30
im not sure if i understand you correctly
if its before login im not sure sorry.
is this a graphical login??? if its not you should be able to add something to your .bashrc (theres one specifically for bash logins)


re tnote if you want a multiline note you have to do it from a text editor
use 
```
tnote -a
```(no other text)
should take you to it. 
if you want to add a note directly from the command line you are essentially limited to one line, because as soon as you press enter its processed by bash, which includes '\' ive put some notes about it in the man page because unfortunately bash will try to do its stuff with it first.
let me know if the man page isn't clear and ill rewrite it.

I was toying with the idea of implementing quotes but then you introduce new problems (does someone mean \ or newline). coupled with the fact that you then have three differnt input methods with slightly different rules. so i just decided to leave a text editor to do anything more complicated than a simple one line note. if you think something like that would be of value though let me know and i will have a think,

---

### Post by loomsen on 2009-05-10
*up*

Tho I'm slightly losing hope this will work at all...

---

