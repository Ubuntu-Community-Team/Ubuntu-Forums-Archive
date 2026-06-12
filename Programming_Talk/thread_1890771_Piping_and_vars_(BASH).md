---
title: "Piping and vars (BASH)"
date: 2011-12-04
forum: Programming Talk
---

### Post by zero2xiii on 2011-12-04
Hay all,

I'm having a hard time finding the solution online:

```
!#/bin/sh

echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" > test.txt

**file=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | tr -d '\n'**

echo $file >> test.txt

dd if=/dev/null of=$file

exit 0

```

The bold line is the one not working. How do I send altered data (through a pipe, in this case tr, but can be sed, grep, awk or anything else) to a var? Is there an 'easy' way for doing that. This is a very simple script (and can probably be made into a single line) but its for me to learn some new functions and their uses in a useful manner.

The problem I am trying to solve by the above process is:
```
dd if=/dev/null of="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```
does not overwrite the selected file or folder. It creates a new file with a newline character appended. Now I am trying to remove that newline character using tr.

```
 echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | tr -d '\n' > test.txt
```
works perfectly, giving me the correct result.

Thanks in advance

---

### Post by Bachstelze on 2011-12-04
Then just do the same thing. ;)

```
file=` echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | tr -d '\n'`

```

You could also use Bash string manipulation, but I would advise against it. Your script is simple enough, you don't want to make it unnecessarily depend on Bash.

*EDIT:* Also you might want to use sed instead of tr. tr is non-standard.

---

### Post by ofnuts on 2011-12-04
> **Bachstelze said:**
> *EDIT:* Also you might want to use sed instead of tr. tr is non-standard.Hmmm. All my googling seems to indicate that TR is part of POSIX.[ Wikipedia ]("http://en.wikipedia.org/wiki/Tr_%28Unix%29")seems to imply that tr is part of Posix: *"In [POSIX]("http://en.wikipedia.org/wiki/POSIX") compliant versions of tr". *Otherwise, I couldn't get hold of a free version of the standard, but this[ Fujitsu doc of Posix commands]("http://manuals.ts.fujitsu.com/file/8867/posix_k.pdf") lists tr.

---

### Post by MG&amp;TL on 2011-12-04
Maybe he means it's more commonly used for the application in question?

---

### Post by Lars Noodén on 2011-12-04
[font=Courier New]sed[/font] is in [font=Courier New]/bin[/font] and [font=Courier New]tr[/font] is in [font=Courier New]/usr/bin[/font]  So, [font=Courier New]sed[/font] belongs to the programs available in single user mode or when bringing the system up.  [font=Courier New]tr[/font] belongs to the programs not needed for booting or repairing the system.  See [hier](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html) for the details.

Myself, I just used [font=Courier New]sed[/font] out of habit.  Now I have an excuse.

---

### Post by zero2xiii on 2011-12-04
> file=` echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | tr -d '\n'`
Works perfectly :) thanks.
I seemed to not be able to find a reference to using those `..` characters. Wonder if I'm just missing it. Been trying dubbel qoutes and all forms of brackets hahahahaha but nothing worked. 

As far as sed vs tr etc.

This is just a script for personal use to purge some personal and bussiness files for security. So I don't have to worry about portability to much. However, I see tr is in ubuntu 10.04, 11.04 and studio 10.04 aswell as backtrack. So I doubt I will encounter problems porting it to other computers also running ubuntu. Maybe I have just installed it with some other software without knowing it and its coincedently on all the distros I use.

Thanks for all the help, marking as solved :)

Ooh just another question, if anyone sees this, will it be beter to use /dev/random and then /dev/null, or does /dev/random not generate random data?

---

### Post by Bachstelze on 2011-12-04
> **ofnuts said:**
> Hmmm. All my googling seems to indicate that TR is part of POSIX.[ Wikipedia ]("http://en.wikipedia.org/wiki/Tr_%28Unix%29")seems to imply that tr is part of Posix: *"In [POSIX]("http://en.wikipedia.org/wiki/POSIX") compliant versions of tr". *Otherwise, I couldn't get hold of a free version of the standard, but this[ Fujitsu doc of Posix commands]("http://manuals.ts.fujitsu.com/file/8867/posix_k.pdf") lists tr.

D'oh. Long ago I searched for it [here](http://pubs.opengroup.org/onlinepubs/9699919799/) and didn't find it. But actually it's because "tr" triggers too many results. :p

---

### Post by ofnuts on 2011-12-05
> **Bachstelze said:**
> D'oh. Long ago I searched for it [here]("http://pubs.opengroup.org/onlinepubs/9699919799/") and didn't find it. But actually it's because "tr" triggers too many results. :pThere used to be a newsgroups import utility called "suck", very hard to find on Google :)

---

