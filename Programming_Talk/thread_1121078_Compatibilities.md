---
title: "Compatibilities"
date: 2009-04-09
forum: Programming Talk
---

### Post by vurt on 2009-04-09
We have ANSI we have ISO, we have various web standards and we have basic software interoperability.

In this day and age, why do we not have file format standards?  I'm talking about LF/CR/R.  Is this simply an OS thing that is too big to bridge (hard to believe) or something that I'm missing entirely?

v - frustrated comp-sci student.

---

### Post by soltanis on 2009-04-09
Well, what do you mean? I mean we do have file format standards, like GIF, JPEG, PNG, AVI, MPEG, OGG/Theora/Vorbis...

There's even been a big push to make configuration files/serialized data files standardized with XML (which I hate) or YAML (oh yes). And of course, there's always the good old fashioned Text File with ASCII encoding that works no matter where I put it.

If you're talking about the end of line issue, well it's a hangover from the era of teletypewriters, where you had to do a carriage return (CR) and then a new line feed (LF) to start typing a new line. Really retarded, unfortunately, there is absolutely no need for that now, and its sad that Windows, Mac, and Unix descendants have decided to go separate ways on that subject.

Bear in mind, though, that the Internet newline is in fact CR LF. Whether this was from the TTY period or what I don't know.

---

### Post by samjh on 2009-04-09
> **vurt said:**
> In this day and age, why do we not have file format standards?  I'm talking about LF/CR/R.  Is this simply an OS thing that is too big to bridge (hard to believe) or something that I'm missing entirely?

Good point.  I find it puzzling that no-one seems to have standardised line breaks yet.

The "correct" way is (as soltanis pointed out above) LF + CR.  This is also the newline character sequence for the Internet (eg. HTTP, IRC, etc.).  IMHO, LF + CR should be the standard newline, but who cares what I think? ;)

---

### Post by Peasantoid on 2009-04-09
\n is for real men.

---

### Post by Tibuda on 2009-04-09
Looks like only Windows is going in a different way, as you can read in [Wikipedia]("http://en.wikipedia.org/wiki/Newline"):
>     * LF:    Multics, Unix and Unix-like systems (GNU/Linux, AIX, Xenix, Mac OS X, FreeBSD, etc.), BeOS, Amiga, RISC OS, and others
    * CR+LF: DEC RT-11 and most other early non-Unix, non-IBM OSes, CP/M, MP/M, DOS, OS/2, Microsoft Windows, Symbian OS
    * CR:    Commodore machines, Apple II family, Mac OS up to version 9 and OS-9
If you have problems reading LF-only files in Windows, use a good text editor like Notepad++. Even Dreamweaver can read such files.

---

### Post by simeon87 on 2009-04-09
> **samjh said:**
> The "correct" way is (as soltanis pointed out above) LF + CR.  This is also the newline character sequence for the Internet (eg. HTTP, IRC, etc.).  IMHO, LF + CR should be the standard newline, but who cares what I think? ;)

But why would you want to use the LF and CR characters separately? This would allow for some weird files:

```

'a' 'b' 'c' CR 'd' 'e' 'f'

```

would become:

```

defabc

```

as the carriage is returned but no new line is started.

---

### Post by FrankT-Qc on 2009-04-09
Yeah... I miss the good old 
KKKKKKKKRRRRRRRRSSSSSSSSSH (CR) tsssTIINGGG (LF) 

of my "dactylo" ...

---

### Post by slavik on 2009-04-09
> **simeon87 said:**
> But why would you want to use the LF and CR characters separately? This would allow for some weird files:

```

'a' 'b' 'c' CR 'd' 'e' 'f'

```

would become:

```

defabc

```

as the carriage is returned but no new line is started.
that would in fact be "def"

also, os x and linux have different \n definitions.

---

### Post by samjh on 2009-04-09
> **simeon87 said:**
> But why would you want to use the LF and CR characters separately? This would allow for some weird files:

```

'a' 'b' 'c' CR 'd' 'e' 'f'

```

would become:

```

defabc

```

as the carriage is returned but no new line is started.
It's actually:```
def
```
And why not? :D

It would also allow for:
```
'a' 'b' 'c' LF 'd' 'e' 'f'
```which results in:
```
abc
   def
```

:)

---

### Post by slavik on 2009-04-09
there's also vertical tab (\v in C) ... I forget the character code for it.

---

### Post by soltanis on 2009-04-09
Haha, vertical tab...I use that character code when I need to substitute a char that means more or less nothing into a C string.

---

### Post by Tibuda on 2009-04-10
> **slavik said:**
> also, os x and linux have different \n definitions.No, only old Macs uses CR as a new line. Mac OS X, which is based on FreeBSD, uses the same LF as Linux.

---

### Post by pmasiar on 2009-04-11
> **vurt said:**
> In this day and age, why do we not have file format standards?  I'm talking about LF/CR/R.  Is this simply an OS thing that is too big to bridge (hard to believe) or something that I'm missing entirely?.

We have different whitespace characters, because decades ago, people used real typewriter (typing on paper) - which TTY still emulates. Then, different companies used different file formats because printers were differently stupid. Ie CFLF makes sense, if you want to let plain CR to let retype the same line once again (on paper). Read about [http://en.wikipedia.org/wiki/APL_(programming_language](http://en.wikipedia.org/wiki/APL_(programming_language))

Also, different file format is simplest way of vendor lock-in: files from other sources will "look weird". In this sense, CRLF in ideal: if almost works on other platforms (files are readable), but foreign files do not work on MS-DOS. So for MSFT, CRLF makes perfect sense.

---

### Post by scourge on 2009-04-11
> **pmasiar said:**
> Also, different file format is simplest way of vendor lock-in: files from other sources will "look weird". In this sense, CRLF in ideal: if almost works on other platforms (files are readable), but foreign files do not work on MS-DOS. So for MSFT, CRLF makes perfect sense.

True, though these days even MS must recognize other line break formats. Wordpad understands Unix line breaks, and in Visual Studio one can choose which format to use.

---

