---
title: "gettext and marking translatable strings"
date: 2010-09-02
forum: Programming Talk
---

### Post by GeoMX on 2010-09-02
Has someone tried marking translatable strings for existing code using emacs and PO mode?

I'm willing to translate a C program, it has lots of source files. I'm thinking of writting a script that would export character strings in the sources, I'd translate them and later replace them into the original files.

Before writting such a script, I found that gettext could be of some help here, there is an Emacs PO mode that would allow me to search for candidate strings for translation: [http://www.gnu.org/software/gettext/manual/gettext.html#Marking](http://www.gnu.org/software/gettext/manual/gettext.html#Marking)

The problem is, I've never used emacs before, I've just installed and read the tutorial, but don't know how to make the commands work for my source file:

> 
,
    Search through program sources for a string which looks like a candidate for translation (po-tags-search).
M-,
    Mark the last string found with ‘_()’ (po-mark-translatable).
M-.
    Mark the last string found with a keyword taken from a set of possible keywords. This command with a prefix allows some management of these keywords (po-select-mark-and-mark). 

I just can't figure out how to make these commands work, I open one file and enter PO mode, but typing [,] does not search strings but opens a buffer window for entering notes.

Any help is appreciated, thanks.

---

### Post by worksofcraft on 2010-09-02
> **GeoMX said:**
> I'm thinking of writting a script that would export character strings in the sources, I'd translate them and later replace them into the original files.


With gettext you do not have to replace the strings in the original files. It saves your translations separately. One for each language. That gets used **at run time** to replace the original text depending on the user's chosen language.

What you do have to do is surround all the translatable text strings in the source file with a call to gettext, but they recommend you use a macro like _() to make this a bit less verbose. For instance:
```

  printf("Hello, world!\n");
// becomes
  printf(gettext("Hello, world!\n"));
// but if you this...
#define _(X) gettext(X)
// you can abreviate it so:
  printf(_("Hello, world!\n"));

```
 This is what emacs is supposed to be able to help you with, but I haven't ever used that facility because I put it in from the start on my programs.

You may find it helps a lot to do a little example program of your own first. Like here is a good introduction:
[http://oriya.sarovar.org/docs/gettext_single.html](http://oriya.sarovar.org/docs/gettext_single.html)

---

### Post by GeoMX on 2010-09-03
Thanks a lot for your reply.
I have used gettext some time ago when porting a Linux app to Windows, it already used gettext and had all translatable strings marked with the macro you mention _(string).

But, now I want to integrate gettext to an already existing application, I can manually add the gettext call, but would like to find a tool that could help me with the process (there are too many files), I was thinking of writting a script (have to find some information on how to do it), but thought I could use Emacs PO mode as stated in the gettext manual:
> 
In PO mode, one set of features is meant more for the programmer than for the translator, and allows him to interactively mark which strings, in a set of program sources, are translatable, and which are not. Even if it is a fairly easy job for a programmer to find and mark such strings by other means, using any editor of his choice, PO mode makes this work more comfortable.

The manual indicates three commands: ',' searches for strings that are candidates for translation, 'M-,' marks the string with _() and 'M-.' that marks a string with a keyword. The problem is that I'm new to Emacs and can't figure out how to use this mode.

Anyway, about the other option, writing a script that can search  and extract character strings from the program source, do you know of an already existing application that could do this job? Or any advice on how I could write such a script/program?

---

