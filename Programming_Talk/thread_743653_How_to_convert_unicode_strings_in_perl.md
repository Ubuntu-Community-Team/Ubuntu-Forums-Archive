---
title: "How to convert unicode strings in perl?"
date: 2008-04-02
forum: Programming Talk
---

### Post by ladybug118 on 2008-04-02
Hi there,

I'm sort of a beginner to perl and DEFINITELY new to unicode issues.  Apologies if this is a totally newbie question, but I can't seem to figure it out on my own.  

I have two files which contain unicode strings that I'd like to compare.  One file is a javascript file, so the unicode characters are represented by \uXXXX (it's called an escape sequence I think?).   The other file is a utf8 text file, so the characters appear correctly when viewed in my browser (Safari for Mac) with the text encoding set to utf8.  Is there a function in perl which would allow me to convert one unicode format to the other?  I am using "encoding(utf8)" to read both files...maybe there is another way I should be reading the .js file in order to convert all \uXXXX characters when opening/reading the file?  Or do I have to write some function from scratch in order to do this (I hope not)?

For example:

In the .js file, the registered trademark symbol appears as \u00AE
But in the .txt file, it appears as ®   <--registered trademark symbol

Thanks!

---

### Post by slavik on 2008-04-03
read this: [http://perldoc.perl.org/perluniintro.html](http://perldoc.perl.org/perluniintro.html)

\x{charcode} :)

EDIT, couldn't sleep till I was able to get the following to work:

```

$string = "In the .js file, the registered trademark symbol appears as \\u00AE But in the .txt file, it appears as ® <--registered trademark symbol";
$string =~ s/\\u([[:xdigit:]]{1,4})/chr(eval("0x$1"))/egis;
print $string;

```

---

### Post by ladybug118 on 2008-04-03
WOW!!!  I think that just might work, thank you SO MUCH!!!  You didn't have to lose sleep over it though, but I appreciate it.  You totally rock!!

:guitar:

---

