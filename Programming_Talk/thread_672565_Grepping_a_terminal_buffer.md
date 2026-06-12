---
title: "Grepping a terminal buffer???"
date: 2008-01-19
forum: Programming Talk
---

### Post by ikunat33 on 2008-01-19
I am assuming this can be done I just do not know how. I can not find the information on the web either... perhaps I am just not asking the question properly

I simply want to be able to grep the buffer of an active terminal session for information. I am not after command output. 

Thanks.

---

### Post by popch on 2008-01-19
Would ***~/.bash_history*** be of any use?

---

### Post by LaRoza on 2008-01-19
Could you dump the results of the terminal into a file?

---

### Post by Thund3rstruck on 2008-01-19
the term.h header includes a multitude of options for dealing with the terminal. You can investigate the available members. 

```

#include <term.h>

```

---

### Post by ikunat33 on 2008-01-19
Thanks for the replies;

POPCH:
No the history would not help as I am not looking for a command. I could grep that easily. 

LaRoza:
ummm... was not aware you could dump the contents of the buffer into a file... that would more or less address my problem. How do you  do it? I will see if I can find out while awaiting your response.


THUND3RSTRUCK:
Thank you for this. I will look at it right quick. I have to give my girl a few minutes first though... judging by the look in her eye she may try to take a hammer to my computer if I don't.

---

### Post by dwhitney67 on 2008-01-19
If you are running commands in the terminal, and you want to see output directed to the terminal _and_ directed to a file, you can use something like:

$ *cmd* | tee *file*

where *cmd* is the command you want to run and *file* is the name of the output file.

P.S.  Use the -a option with tee if you want to append to the output file.

---

### Post by ikunat33 on 2008-01-20
Thanks dwhitney67,

unfortunately tee does not seem to work with commands that manipulate the terminal screen. it works fine with things like Grep but does not work for me. I need a way of directly accessing the buffer.

---

### Post by naugiedoggie on 2008-01-21
> **ikunat33 said:**
> Thanks dwhitney67,

unfortunately tee does not seem to work with commands that manipulate the terminal screen. it works fine with things like Grep but does not work for me. I need a way of directly accessing the buffer.

Hello,

Have you looked at [screen]("http://www.gnu.org/software/screen")?

It might also be helpful to know exactly what kinds of information you are seeking.

Thanks.

mp

---

### Post by stroyan on 2008-01-21
I have often thought it would be nice to have a way that gnome-terminal would highlight a particular string or regular expression in its buffer.  The simplest interface would be to have it highlight every occurance of the selected text instead of just the single one that has been selected.  Then I could double click on a word like 'hostname' and have that word highlighted with inverse colors everywhere that it appears in the buffer.  Unfortunately such a feature does not exist at present.
One thing you can do is to select all the text in the buffer and send that to a file or pipe it to grep.
[LIST=1]
[*]Use <shift>Home to seek to the top of the buffer.
[*]Use mouse button 1 to drag across the top line, (or triple-click to do it).
[*]Use <shift>End to seek to the bottom of the buffer.
[*]Use <shift> and mouse button 1 to extend the selection to the bottom line.
[*]Use "xclip -o | grep *pattern*" to grep for a pattern.
[*]Use mouse button 1 to select something harmless before you paste that big buffer somewhere you don't want to.  ;-)
[/LIST]
The xclip command is in the xclip package.

---

### Post by fyplinux on 2008-01-21
terminal handling and pseudo-terminals might be the answer

---

### Post by RMKrug on 2011-09-19
This is  quite an old thread - but in emacs' shell, you can do exactly that: search in everything you see in the buffer.

Rainer

---

### Post by nothingspecial on 2011-09-19
Please let sleeping threads lie.

Thread closed.

---

