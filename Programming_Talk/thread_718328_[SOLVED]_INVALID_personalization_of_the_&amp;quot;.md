---
title: "[SOLVED] INVALID personalization of the &amp;quot;ls&amp;quot; sort algorithm"
date: 2008-03-08
forum: Programming Talk
---

### Post by ecsd on 2008-03-08
The "ls" command produces an INVALID COLLATION of ASCII
AND
"man ls" does not show a flag to produce the CORRECT COLLATION.

It is understood throughout the KNOWN UNIVERSE how to SORT ASCII STRINGS.

FACT: "+" PRECEDES "a"
FACT: "_" FOLLOWS "Z"
FACT: "Z" PRECEDES "a"

If I create a directory and then do this:

touch a _b C +d

On FreeBSD (or any other CORRECTLY PROGRAMMED SYSTEM):

# ls -l
-rw-r--r--  1 root  mail  -    0 Mar  7 21:54 +d
-rw-r--r--  1 root  mail  -    0 Mar  7 21:54 C
-rw-r--r--  1 root  mail  -    0 Mar  7 21:54 _b
-rw-r--r--  1 root  mail  -    0 Mar  7 21:54 a

On Ubuntu (Gutsy 6?):

$ ls -l
-rw-r--r-- 1 ecsd ecsd 0 2008-03-07 21:54 a
-rw-r--r-- 1 ecsd ecsd 0 2008-03-07 21:54 _b
-rw-r--r-- 1 ecsd ecsd 0 2008-03-07 21:54 C
-rw-r--r-- 1 ecsd ecsd 0 2008-03-07 21:54 +d

WHO SAID IT WAS ALRIGHT TO IGNORE PRECEDING NONALPHA CHARACTERS WHEN SORTING FILENAMES?

WHY WOULD SOMEONE ASSIGN SUCH LEADING CHARACTERS? TO >>GET THEM TO SORT IN A KNOWN FASHION.<<< TO IGNORE THIS (AND FAIL TO PROVIDE ANY MEANS TO >>>GET<<< A CORRECT COLLATION) IS SHORTSIGHTED, THOUGHTLESS AND ABSURD.

THE OUTPUT FROM UBUNTU LS IS >>>INCORRECT<<< BECAUSE SOMEONE TRIED TO BE "CUTE". MAKE THE "CUTE" SORTING A NONDEFAULT FLAG-INVOKED OPTION AND MAKE THE LS COMMAND OUTPUT >>>CORRECT COLLATION<<<.

THIS IS NOT SUBJECT TO "PERSONAL PREFERENCE". THIS IS AN INTERNATIONAL STANDARD.

PLEASE FIX IT AS SOON AS HUMANLY POSSIBLE.

---

### Post by imdano on 2008-03-08
That's caused by your locale settings.  If you open a terminal, and type ```
Export LC_COLLATE=C
```You'll see them get sorted the way you expect.   See here for more info: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg301934.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg301934.html)

Also, you need to chill out.  No need to be so hostile.

---

### Post by ecsd on 2008-03-08
It's fine to be HOSTILE when SYSTEM DEFAULTS produce INVALID RESULTS.

I have yet to find a BOOK (or FAQ) that addresses the myriad little "gotchas" that make Ubuntu mysteriously unworkable for no apparent reason.

Witness that your note about the behavior of "ls" was taken from a discussion list for BUGS.

Thanks for the tip. The correct command is "export", not "Export".

==

LC_COLLATE=C should be the DEFAULT; and instead of ASSUMING the user would die from confusion
to see ASCII sort as ASCII DOES sort, then HAVE A DIALOGUE WITH THE USER following installation,
that walks the user through such settings - so WE KNOW WHAT WE CAN CHANGE AND CONTROL.

"man ls" should SAY SOMETHING about the LC_COLLATE variable because the man page SAYS
"alphabetic sorting unless otherwise specified" and as I said, ASCII SORTS IN EXACTLY ONE WAY,
even if "average user Joe" didn't know that. The SYSTEM DEFAULT should be compatibility with other
systems and known behavior, and again, if Ubuntu wants to offer what it thinks are "usability features",
make them OPTIONAL, elected by ACTIVE CHOICE, and DOCUMENTED.

The _default_ for ascii collation is not ASCII collation?? What's the world coming to ...

---

### Post by olejorgen on 2008-03-08
I'd say it's nautral to sort according to your locale. Kinda strange that _'s postition really is different across locals though

---

### Post by ecsd on 2008-03-08
It's nice to see Ubuntu install with "no muss, no fuss." It's also a trojan horse though, since the user MUST DO additional things to get their system to behave PROPERLY, and the user is NOT LED to any such dialogue. If LC_COLLATE=C is the default locale setting for the US then (a) it SHOULD HAVE BEEN SET FOR ME when I set the system up - the system should want to know its own locale, yes? And it should have ASKED and then SET THINGS ACCORDINGLY. But it DID NOT and here I am having ask "what gives?" and (b) Ubuntu can default the locale to the USA, or NOT default it and force the user to choose - but since that was not set for me nor was I asked, then obviously something is missing or wrong.

If "man ls" documented (as it SHOULD) the LC_COLLATE variable, then I would already have found out what my trouble was. THAT IS a bug.

---

### Post by imdano on 2008-03-08
[http://www.gnu.org/software/coreutils/faq/coreutils-faq.html#Sort-does-not-sort-in-normal-order_0021](http://www.gnu.org/software/coreutils/faq/coreutils-faq.html#Sort-does-not-sort-in-normal-order_0021)

I think using the en_US locale results in sorting that doesn't follow the POSIX standard.

---

### Post by ecsd on 2008-03-08
So much for standards. (*SOB*)

---

### Post by CptPicard on 2008-03-08
IT IS ALSO UNDERSTOOD GENERALLY that this is the PROGRAMMING TALK forum and not the UBUNTU DEVELOPMENT FORUM. Thus you should understand to post in the RIGHT FORUM or alternatively even TAKE THE SOURCE and MODIFY IT TO YOUR NEEDS AND SUBMIT A PATCH as is the way in open source...

---

### Post by mssever on 2008-03-08
If you think that's a bug, file a bug report. Remember, Ubuntu doesn't default to the C locale, nor should it. It defaults to the locale for the user's country. My locale is en_US.UTF-8. I'll admit that I was a bit surprised by the sort order, but it makes sense. If I were scanning an alphabetical list, that's the order I would expect. After all, what's the point of sorting according to ASCII? ASCII is outdated and USA-centric. That's why Ubuntu defaults to utf-8.

In addition, any sensible sorting algorithm must be locale-dependant. For example, in English we'd expect accented letters to be sorted together with unaccented ones, ignoring the accent, But ASCII wouldn't accomplish that. But some languages are different. In Spanish, ñ is a separate letter sorted after n, while, for example, é is sorted together with e. In Swedish, ä is a separate letter sorted after z. Following ASCII order would result in incorrect sorting results. Besides, what use is there in sorting according to ASCII anyway?

There's a reason I use Linux, not FreeBSD. FreeBSD's CLI tools are quite primitive in comparison. GNU-style long options are awesome for script maintainability when you don't use those options frequently. Being stuck with single-letter options as in FreeBSD is a real pain. Maybe they're more in line with POSIX. I don't know (or care). I do know, though, that if you set the environment variable POSIXLY_CORRECT, a number of GNU/Linux tools will modify their behavior to be in line with POSIX. That's documented in many man pages. I don't know specifically about ls, though.

---

