---
title: "DOS / UNIX - CR/LF problems"
date: 2009-01-04
forum: Programming Talk
---

### Post by Krupski on 2009-01-04
Hi all,

I wrote a small simple C program to read lines of ASCII data and operate on them.

This is the line I use:

```

    fgets(buffer, (BUFSIZ), infile); // read a line

```

Problem is, if I compile the code as a Win32 console program (using [[COLOR="Blue"]_Win LCC32_[/COLOR]]("http://www.cs.virginia.edu/~lcc-win32/")), the ASCII files that I read must have CR/LF sequences for end of line, otherwise it fails.

Similarly, in Linux if I compile with GCC, the same program (and same ASCII files) need to end in LF only otherwise the program fails.

The code compiles perfectly in LCC32 and GCC without any changes... but sadly the ASCII files I wish to convert are sensitive to the CR/LF or LF only type of newline.

Anyone know why this is, and what I can do to make the code "universal" so it works on any kind of line?

Thanks!

-- Roger

---

### Post by arvevans on 2009-01-04
Don't know how many times it has been said, but probably bears repeating again, and again..."Linux is not Windows", and conversly, "Windows is not Linux".  There are differences, the end-of-line thing being one of them.

You may have to add a test in your code which looks at the file to determin if the end-of-line contains CR/LF (Windows) or just CR (UNIX & Linux), and then handle each case properly.

Alternatively, there are "conversion programs" available which might be used to pre-process or filter-process your files to make them always Windows compliant, or always Linux compliant.

---

### Post by jpkotta on 2009-01-04
Try getdelim().

---

### Post by dwhitney67 on 2009-01-04
What is the CRLF sequence under Windoze?  Is it a "\r\n" sequence of characters?

If so, then when using fgets(), both of these characters will be stored in the buffer.  To remove them both, one can use strchr() to slap a null-byte where the '\r' exists, and then again for the '\n'.
[php]
char  buf[512] = {0};
char* p = 0;

fgets(buf, sizeof(buf), fp);

if ((p = strchr(buf, '\r') != 0) *p = 0;
if ((p = strchr(buf, '\n') != 0) *p = 0;
...
[/php]

---

### Post by monkeyking on 2009-01-04
It's always messy to make a program work on different systems.
Last week I found out the mingw(gcc for windows), didn't have the strsep function.

If your are parsing the file your likely tokenize it, try putting in a "\r", in the delim part.

Otherwise you can use fromdos, todos from the commandline.

good luck

---

### Post by Krupski on 2009-01-04
> **dwhitney67 said:**
> What is the CRLF sequence under Windoze?  Is it a "\r\n" sequence of characters?

If so, then when using fgets(), both of these characters will be stored in the buffer.  To remove them both, one can use strchr() to slap a null-byte where the '\r' exists, and then again for the '\n'.


In DOS/Windows, a line is "...CR,LF"

In Unix/Linux a line is "...LF"

In Apple Mac a line is "...CR"

I managed to "fix" the problem by scanning the buffer backwards and finding the last valid character before a CR, LF or NUL.

However... in Linux the "fgets" function does not stop when it sees a CR, so it fails if trying to read MAC formatted text.

Now, I really don't care about MAC formatted text since I'll only be encountering DOS or UNIX style text, but in my opinion a good program SHOULD be able to handle all variations.

Oh and to **jpkotta** thanks for the getdelim() suggestion... I should have mentioned that I am trying to stay ANSI compatible in the code... ;)

-- Roger

---

