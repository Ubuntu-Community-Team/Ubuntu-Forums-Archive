---
title: "batch renaming with the rename command"
date: 2008-05-29
forum: Programming Talk
---

### Post by deltaromeo on 2008-05-29
Hello, I'm trying to use the rename command to batch rename some files and could use some help.  I'm trying to rename files that look like this:
[I]
one-file
another-file[/I]

to this:
[I]
one - file
another - file[/I]

ie. i want to put spaces around the dash if they don't exist.

I have tried this:

**rename -n 's/\S-\S/\1 - \2/' ***

but it tells me:

\1 better written as $1 at (eval 91) line 1.
\2 better written as $2 at (eval 91) line 1.

so I tried:

**rename -n 's/\S-\S/$1 - $2/' ***

but that doesn't work either.

Anyone?

---

### Post by HalPomeranz on 2008-05-29
You need to use parens:

```

rename -n 's/(\S)-(\S)/$1 - $2/' *

```

In a Perl regular expression, parens create what are referred to as "sub-expressions".  The sub-expressions are what get assigned to the $1, $2, ... variables.

Btw, the above expression won't work if there's whitespace on one side of the dash and not the other (e.g. a file named "foo- bar").  You might prefer to use:

```

rename -n 's/\s*-\s*/ - /' *

```

The above code will eat up whatever whitespace is on either side of the dash and replace that with "<space>-<space>".  And it will also work for filenames where there is no whitespace around the dash.

---

### Post by george9233 on 2008-05-29
Or if you want a graphical way, just install "Bulk Rename" from Add/Remove...

---

### Post by uarale on 2008-11-17
Hi everyone,

I want to rename images in a folder. Their names and their extentions are in different types, and i am trying to rename them to 01.jpg, 02.png, 03.jpg, 04.gif...

Somebody can help? Thanks.

---

### Post by gaosanyong on 2013-03-07
Hi 

To use back-reference, i.e. \1 or $1, one has to define a sub-expression with parentheses as shown by Halpomeranz. However, the fact that it is recommended to use $1 instead of \1 (even though \1 works as well) is surprising to me. When I learned regular expression, back reference was done by \1, \2, ... I guess I just have to keep that in mind. 

Cheers, 
Ye

---

### Post by erind on 2013-03-07
> **gaosanyong said:**
> Hi 

To use back-reference, i.e. \1 or $1, one has to define a sub-expression with parentheses as shown by Halpomeranz. However, the fact that it is recommended to use $1 instead of \1 (even though \1 works as well) is surprising to me. When I learned regular expression, back reference was done by \1, \2, ... I guess I just have to keep that in mind. 

Cheers, 
Ye
This thread is a bit old, but here goes my answer.

Using backreferences *outside* of the regex pattern will give you problems in certain situations (see below). **$1** and **\1** are slightly different concepts.** $1** is a matching *variable*, which can be safely used *outside *the regex block as a variable, whereas "\1" is just a backreference (see below).

From *perlretut - Perl regular expressions tutorial*:

> Backreferences.
Closely associated with the matching variables $1, $2, ... are the backreferences \1, \2
Backreferences are simply matching variables that can be used* inside a regexp* ...

Although $1 and \1 represent the same thing, care should be taken to use matched variables $1, $2,... only outside a regexp and backreferences \1, \2,... only inside a regexp; **not doing so may lead to surprising and unsatisfactory results.**


Also from *perlre* online manual pages, check this section - "*Warning on \1 Instead of $1*":

> This is grandfathered (for \1 to \9) for the RHS of a substitute to avoid shocking the *sed* addicts, but it's a dirty habit to get into.  That's because in PerlThink, the righthand side of an [s///]("http://perldoc.perl.org/functions/s.html") is a double-quoted string.  \1  in the usual double-quoted string means a control-A.  The customary Unix meaning of \1  is kludged in for [s///]("http://perldoc.perl.org/functions/s.html").  H**owever, if you get into the habit of doing that, you get yourself into trouble if you then add an /e modifier**.

  s/(\d+)/ \1 + 1 /eg;            # causes warning under -w

http://perldoc.perl.org/perlre.html#Warning-on-\1-Instead-of-$1

---

