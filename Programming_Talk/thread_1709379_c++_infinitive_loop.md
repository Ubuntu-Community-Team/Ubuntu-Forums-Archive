---
title: "c++ infinitive loop"
date: 2011-03-18
forum: Programming Talk
---

### Post by tushar maroo on 2011-03-18
hey i am a new programmer to c++ and i written a code [http://pastebin.com/9tu2wrjz](http://pastebin.com/9tu2wrjz)
there is some problem in running option number1 in code in giving a 10 digit mobile number.......how can i solve it.

---

### Post by Tony Flury on 2011-03-18
Um - what is the actual problem ?

"There is some problem" does not really help.

---

### Post by Zugzwang on 2011-03-18
> **tushar maroo said:**
> hey i am a new programmer to c++ and i written a code [http://pastebin.com/9tu2wrjz](http://pastebin.com/9tu2wrjz)
there is some problem in running option number1 in code in giving a 10 digit mobile number.......how can i solve it.

Please describe the problem you are having.

---

### Post by burton247 on 2011-03-18
More detail needed.

You shouldn't be using "\n" for new line though, it's not cross platform and therefore bad practice. Use count << endl; instead.

Also you can just use strings instead of a char array and I'm not sure why your phone number is a long double. Double are for storing floating point number and a phone number isn't that. you can just use a standard int. Or if you want to use characters like () and - in it then just use a string.

---

### Post by andrew1992 on 2011-03-18
> **tushar maroo said:**
> hey i am a new programmer to c++ and i written a code [http://pastebin.com/9tu2wrjz](http://pastebin.com/9tu2wrjz)
there is some problem in running option number1 in code in giving a 10 digit mobile number.......how can i solve it.

I'm going to take a wild stab, because you didn't provide much in the way of error messages/output. Maybe you're experiencing an overflow problem? I strongly suggest **not** storing the mobile number as a long type, because I highly doubt you need it for any mathematical reasons, and it may very well be causing your problem. Try storing it in a simple array of 10 integers. 

Or even better, just store it as a string...

---

### Post by matt_symes on 2011-03-18
Hi

Use std::string and not arrays of chars. That way buffer overflows be and you are writing in C++ and not C.

Also why are you using an array of long doubles ? Are you trying to store the number as BCD ?

```
long double mobilenumber[11];
```

Kind regards

---

### Post by trent.josephsen on 2011-03-18
Infinitive loop:

```

to be --> to have --> to do --> to go --> to become
  ^                                           |
  +-------------------------------------------+
```

[SIZE="1"]It's a bad joke.[/SIZE]

---

### Post by schauerlich on 2011-03-18
> **trent.josephsen said:**
> [SIZE="1"]It's a bad joke.[/SIZE]

Making bad jokes is tough work, but somebody's gotta do it. I for one thank you.

---

### Post by forrestcupp on 2011-03-18
> **burton247 said:**
> 
You shouldn't be using "\n" for new line though, it's not cross platform and therefore bad practice. Use count << endl; instead.


endl is good, but what platform doesn't support "\n"?

---

### Post by matt_symes on 2011-03-18
Has this been solved ? It's marked as such.

---

### Post by ve4cib on 2011-03-18
> **forrestcupp said:**
> endl is good, but what platform doesn't support "\n"?

On Windows machines the standard is "\r\n" (or is it "\n\r"?  I can never remember), and I believe on Macs the standard is "\r" (though I may be mistaken there).

If you've ever tried opening a Linux text file in Notepad on Windows it doesn't work, because it's expecting Windows-compliant newlines.

Most (good) software will recognize "\n" as a newline, but some software doesn't.  It's more "proper" to use endl as that will use whatever the OS standard newline is for whatever platform it's been compiled on.  So on Linux endl and "\n are the same, but on Windows you'll get the extra "\r" as well.

If you know you're writing for Linux though it's not a really big issue either way.  But if you're writing a cross-platform program, or you think someone might want to convert it then it's a good practice to use endl.

---

### Post by schauerlich on 2011-03-18
> **ve4cib said:**
> On Windows machines the standard is "\r\n" (or is it "\n\r"?  I can never remember), and I believe on Macs the standard is "\r" (though I may be mistaken there).

I believe is was on Mac OS 9 and below, but OS X is based on unix and uses \n.

---

### Post by forrestcupp on 2011-03-18
> **ve4cib said:**
> On Windows machines the standard is "\r\n" (or is it "\n\r"?  I can never remember), and I believe on Macs the standard is "\r" (though I may be mistaken there).

If you've ever tried opening a Linux text file in Notepad on Windows it doesn't work, because it's expecting Windows-compliant newlines.

Most (good) software will recognize "\n" as a newline, but some software doesn't.  It's more "proper" to use endl as that will use whatever the OS standard newline is for whatever platform it's been compiled on.  So on Linux endl and "\n are the same, but on Windows you'll get the extra "\r" as well.

If you know you're writing for Linux though it's not a really big issue either way.  But if you're writing a cross-platform program, or you think someone might want to convert it then it's a good practice to use endl.

That's not my experience at all. I do most of my programming in Windows, and I only ever use "\n". It works just fine. I've never had any problem opening a Linux text file in Notepad, either.

I can't speak for MacOS, though.

---

### Post by trent.josephsen on 2011-03-18
The UNIX standard is \n.  The old MacOS (9 and below) used \r.  Windows uses \r\n.

BUT, in C (and presumably C++), \n gets automatically translated to the appropriate system line separator when writing to or reading from a file (including stdin and stdout); I looked in the Standard for the clause describing this behavior but couldn't find it.

Python also follows this rule.  Java, on the other hand, does not, and I want to say Perl doesn't either, but I don't have my book to hand atm.

Just something to be aware of when switching between languages and trying to write portable code.

---

### Post by Vox754 on 2011-03-19
> **trent.josephsen said:**
> The UNIX standard is \n.  The old MacOS (9 and below) used \r.  Windows uses \r\n.

BUT, in C (and presumably C++), **\n gets automatically translated to the appropriate system line separator when writing to or reading from a file (including stdin and stdout)**; I looked in the Standard for the clause describing this behavior but couldn't find it.

...

I totally agree with these statements.

The "\n" is translated (printf(), sscanf(), etc.), so you don't have to pay to much attention to this is C. But still, I would recommend using higher level constructs like "std::endl", whenever possible.

This is something not many people know, apparently.

The same thing is true for this: both forward slash (/) and backslash (\) can be used as a directory separator in Windows, at least since Win 95, perhaps.

```

c:/drive/windows

is as valid as

c:\drive\windows

```

Not many people realize this, so they think today writing a directory in the Unix fashion will cause a huge portability problem, but that is not the case.

---

