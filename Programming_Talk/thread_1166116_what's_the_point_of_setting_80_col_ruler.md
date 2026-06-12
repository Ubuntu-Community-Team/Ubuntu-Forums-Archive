---
title: "what's the point of setting 80 col ruler?"
date: 2009-05-21
forum: Programming Talk
---

### Post by Ascenti0n on 2009-05-21
Hi all, I have noticed on many posts and blogs from webdevs who set a column ruler within their editor, and they usually set this to 80, why is this? what is the reasoning behind it?

---

### Post by simeon87 on 2009-05-21
The idea is to keep the length of the lines within 80 characters. This keeps the code readable and you can have two files next to each other on a screen when you want to see a diff.

---

### Post by Dorzu on 2009-05-21
Ah. Good ol' computing history. Succinctly, it's because that was the standard for a very long time. Apple II's, Commodore's, Amiga's, IBM clones, the DEC VT terminals... at some point most of the early terminals used (or had an option for) 80 columns. Even when hardware allowed for more, say 132 columns, many stayed with 80 to ensure compatibility. By maintaining an 80-column habit, you could be sure that most folks, if not all, can read your text without ugly wraparound. Now? It's probably just a long-term habit. I do it, personally. I feel like keeping things at 80 keeps the text quite readable, regardless of how I view it.

---

### Post by Ascenti0n on 2009-05-21
Thanks guys.

@Dorzu: Now you mentioned I remember some of this, yes, I'm that old. :D

So really it to set 80 col width because of limits in software but mainly hardware, including small screen sizes and resolutions.

Today my screen res is 1920x1200 and I have a 22" widescreen LCD display, so I might get a bit brave and expand the 80 ruler to say 120. I hope I can live with the guilt ;)

---

### Post by ZuLuuuuuu on 2009-05-22
> **Dorzu said:**
> Ah. Good ol' computing history. Succinctly, it's because that was the standard for a very long time. Apple II's, Commodore's, Amiga's, IBM clones, the DEC VT terminals... at some point most of the early terminals used (or had an option for) 80 columns. Even when hardware allowed for more, say 132 columns, many stayed with 80 to ensure compatibility. By maintaining an 80-column habit, you could be sure that most folks, if not all, can read your text without ugly wraparound. Now? It's probably just a long-term habit. I do it, personally. I feel like keeping things at 80 keeps the text quite readable, regardless of how I view it.

Nice to hear the historical reasons. I have one more question; some developers prefer to set the limit to 72 or 78 characters, is it safe to assume the 72 or 78 limit is not because of historical hardware reasons but it appeared later as a convention among some programmers?

---

### Post by hessiess on 2009-05-22
Generally I tend to stick to around 70 chars width for writing source code. There are two reasons for this, one it allows me to split the screen vertically to display two files side by side without any wrapping, i.e. a HTML and CSS document. The other reason is that it is beater typographically, thus easier to read. This is why newspapers and the like are printed in columns and not very wide blocks of text, for example.

---

### Post by txcrackers on 2009-05-23
The 80-column rule pre-dates fancy things like terminals: 80 columns was the width of a standard IBM punch-card. Most languages at the time were expressed as one line of code **per card**. Programs ran to 100s, if not 1000s of cards - and woe be it unto you if you got one out of order.

FYI, Apple II and II+ were 40 columns. It wasn't until the //e and //c came out that Apple went to "true" 80 columns.

---

### Post by lisati on 2009-05-23
> **txcrackers said:**
> The 80-column rule pre-dates fancy things like terminals: 80 columns was the width of a standard IBM punch-card. Most languages at the time were expressed as one line of code **per card**. Programs ran to 100s, if not 1000s of cards - and woe be it unto you if you got one out of order.


Memories!
 The first data compression programs I ever looked at and one of the few I've managed to understand was intended for software coded on cards so that a tape-based backup would require less tape. The basic idea for the compression was that for each fixed length 80-byte "card image" was replaced by a variable length record: the compressed record contained a 2-byte integer for the length of the data, 2 bytes containing "goodness knows what" (a requirement of the OS), an 80-bit (10 byte) data structure and a copy of the original data with the spaces removed. The 80-bit data structure indicated where spaces were in the original record.

---

### Post by samjh on 2009-05-23
> **ZuLuuuuuu said:**
> Nice to hear the historical reasons. I have one more question; some developers prefer to set the limit to 72 or 78 characters, is it safe to assume the 72 or 78 limit is not because of historical hardware reasons but it appeared later as a convention among some programmers?

It's not just screens, but printers.  Different printers had different margins, and although most could fit 80 columns, some could not.  In addition, if you were using a 80-column screen but had stuff like line numbers, etc. enabled (which you can do in both vi/vim or emacs), then it will chew up more column space.

The reasons are still pretty relevant.  When you print a text file with fixed-width fonts, you'll end up running into column-width problems.  80 columns are a pretty safe bet for the sake of making things readable on both screen displays and print-outs.  72 or 78 columns, even more so.

---

### Post by Ascenti0n on 2009-05-24
Absolutely fascinating. I got more than I bargained for, from my OP.

---

