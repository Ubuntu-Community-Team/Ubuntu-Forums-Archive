---
title: "Writing &quot;UTF-8&quot; programs"
date: 2007-09-01
forum: Programming Talk
---

### Post by quark_77 on 2007-09-01
Hi all,

This may seem like a basic question to most. I'd like to know how programs become UTF-8 aware. How do I know I'm outputting UTF-8 to the shell, for example? Does this simply mean my source files are UTF-8?

Using all those self-teach books for C I'm given to understand char[] with "\0" on the end is an ASCII string. How would I represent unicode strings? Do these fill the char character too? How do I know, when writing files for example, whether I'm writing Unicode-16, UTF-8, big endian, little endian, or whatever.

Basically, whilst ASCII I/O is no problem for me testing my programs, distribution is another matter. I speak French, for example, so if I translated my program I would need Unicode. I don't understand how I "achieve" this and would be grateful if someone could point me in the right direction / explain the encoding game.

Thanks very much for your time,

Quark_77

---

### Post by triptoe on 2007-09-01
this might help

[http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html)

---

### Post by kostkon on 2007-09-01
Just a tip: GTK is UTF ready, in case you are going to use it.

---

### Post by pmasiar on 2007-09-01
It depends in what language. Every language designers make this decision own way.

Python 3.0 will have unicode variable names, and all strings are unicode, coming next year. :-) You can have unicode strings (explicit, default is ASCII) and unicode in comments right now.

---

### Post by quark_77 on 2007-09-16
Hi everyone,

Thanks for your input everyone, the links were incredibly useful. I was concerned the char definition in C represented only the older (ANSI) string type, which is what I suspected and what is still taught in the books I'm currently using.

I wanted to know which type to use in C for UTF-8 strings. Looks like the best option is to use wchar_t internally.

Would I use a different variable type for UTF-8 strings? Is this the purpose of TCHAR?

Thanks,

Quark_77

---

### Post by engla on 2007-09-16
> **triptoe said:**
> this might help

[http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html)

Some genius has written that text; it's funny and pretty well written. Thanks for the link; even though I knew about UTF-8 before but now I feel assured.


About variables: You can use 'char' for UTF-8. UTF-8 is 8 bits (1 byte) and so is the char. So as long as you work with **UTF-8** (and don't munge the non-ascii part, i.e. the high bit) that should work. Referring to the article; wchar_t should be for wide chars like UCS-2 or something like that?

---

### Post by quark_77 on 2007-09-18
> **engla said:**
> Some genius has written that text; it's funny and pretty well written. 


Couldn't agree more - I "knew" of UTF-8 as in use it on web-pages, e-mails etc but was totally ignorant of how to program using it.

Character variables can hold up to 127 so I take it the "higher byte" would be the next character in the array which will also be 0-127, making up a total, or the next one again... basically I'm not to treat each char as one single character? I think I understand this better now, thanks for all your help.

Quark_77

---

### Post by engla on 2007-09-20
> **quark_77 said:**
> Couldn't agree more - I "knew" of UTF-8 as in use it on web-pages, e-mails etc but was totally ignorant of how to program using it.

Character variables can hold up to 127 so I take it the "higher byte" would be the next character in the array which will also be 0-127, making up a total, or the next one again... basically I'm not to treat each char as one single character? I think I understand this better now, thanks for all your help.

Quark_77
The thing here is that in UTF-8, you don't know how "wide" a  character is. To make americans/western europeans feel right at home, A-Za-z 0-9 etc are just 1 byte, 1 char. But many (most of course, since there is only 128 of the simple type) characters are more than one byte or char.

Looking at [http://en.wikipedia.org/wiki/Utf-8]("http://en.wikipedia.org/wiki/Utf-8"), I see that some really smart people thought out utf-8. Hurray for UTF-8! :)

---

