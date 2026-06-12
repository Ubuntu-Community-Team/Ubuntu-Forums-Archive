---
title: "Problem using emacs21"
date: 2005-05-11
forum: Programming Talk
---

### Post by Sacre on 2005-05-11
Hello everyone,

I'm sure this forum is not the best to ask question about emacs, but I'm a bit new in the Linux world and since I use Ubuntu, I think this forum is the best place to start.

So, I'm programming in Ada and C, and I have heard that emacs was a really good editor for my programming need. I decided to give it a try by installing the "emacs21" package with the "ada-mode".

It works pretty good (syntax coloration for exemple), but I got really boring problems with the use of the "TAB" key and indentation in general.

Pressing this key when I'm not at the start of line just don't do anything, I excpected it will juste had 3 space indentation. It works perfectly when I'm at the start of a line, in any mode.

In C mode, the indentation of the previous line is not conserved when I press "return". It just go to the first column. 

I tried to activate/deactivate or modify some options with the interface provided by emacs21 (like turning on or off "C Syntactic Indentation") but it doesn't look like to have any effect. Some other options I tried to change worked perfectly anyway.

Finally, I want to know if it is possible to put keyword in bold font and comment in italic. Printers we use at school are black and white, so coloring syntax is not useful when I give back my codes to the teacher.

Unfortunatelly, I don't have a lot of time to search deep in the documentation and to perfectly understand how emacs21 works. That's why I'm asking you to give me tip or a way to explore to resolve my problems.

Thank you in advance for any answer.

---

### Post by vague- on 2005-05-12
[QUOTE=Sacre]It works pretty good (syntax coloration for exemple), but I got really boring problems with the use of the "TAB" key and indentation in general.

Pressing this key when I'm not at the start of line just don't do anything, I excpected it will juste had 3 space indentation. It works perfectly when I'm at the start of a line, in any mode.

In C mode, the indentation of the previous line is not conserved when I press "return". It just go to the first column. 

I tried to activate/deactivate or modify some options with the interface provided by emacs21 (like turning on or off "C Syntactic Indentation") but it doesn't look like to have any effect. Some other options I tried to change worked perfectly anyway.[/QUOTE]

Emacs uses the <TAB> key to signify the "correct" indent at that point.  The function bound to the key will try to indent the code on that line correctly.  If you continue typing in the first column, certain characters will cause it to indent correctly - for example, the semi-colon at the end of the statement.  You can disable this, but most people come to quite like it.  You can always insert a real tab at any point with C-q TAB.

[QUOTE=Sacre]Finally, I want to know if it is possible to put keyword in bold font and comment in italic. Printers we use at school are black and white, so coloring syntax is not useful when I give back my codes to the teacher.[/QUOTE]

This is a part of font-locking (Emacs' name for colouring and styling of text, I think that is what it means anyway - that is what it does).  You would need to either edit your theme or install a theme that provides what you are asking for.

You could look at ColorTheme, an Emacs package for managing the styles - usually via installing a style somebody else has created.  There is information about ColorTheme at the EmacsWiki ( [http://www.emacswiki.org/cgi-bin/wiki/ColorTheme](http://www.emacswiki.org/cgi-bin/wiki/ColorTheme) ).

In fact, the EmacsWiki in general is fairly useful if you have a query.  Often somebody else had that query when they were first using Emacs.

As a side note, if you are only bothered about that textual styling when you are printing, you could look into print processors - programs that stylise text for printing/viewing purposes - they are often more sensitive to the properties of printers.  Most of them will output a PostScript file, usually using bold and italics.  An example of such a program is "a2ps".  However, you may be able to find a program more suited to your particular input.

Hope this helps.

---

### Post by Sacre on 2005-05-12
Thank you a lot,

I didn't think, before, to write an entire C instruction when I discovered my indent problem, that finally was not a problem :) The special way emacs handle it is cool, so I will use it without any modifications.

Emacswiki look like a great source of informations, thank you for the link.

I just read about "a2ps" too, and I think this application will cover my further need for printing. I will give it a try as soon as possible.

---

