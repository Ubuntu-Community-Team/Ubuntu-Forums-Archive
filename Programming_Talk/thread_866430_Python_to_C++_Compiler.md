---
title: "Python to C++ Compiler?"
date: 2008-07-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-21
I asked a similar question a week ago -- a Java to C++ compiler.  Does anyone know of such a compiler which can take a Perl program and convert it to C++?  In other words, I have a Perl script which I want to run on Windows machines that do not have Perl.  Is there a compiler that will create an C++ based executable from the Perl script?

---

### Post by LaRoza on 2008-07-21
Executables are independant of the language. So there is no such thing as a "C++ executable".

[https://www.governmentsecurity.org/archive/t4695.html](https://www.governmentsecurity.org/archive/t4695.html)

---

### Post by RAOF on 2008-07-21
Basically what you want is a bundle containing a win32 perl executable and the script.  Although I'm not really familiar with perl, because it is interpreted it's likely to be extremely difficult to translate anything but the simplest perl script to native code in an automated fashion without simply bundling an interpreter.  

I know there are tools to do this with python, but I don't know any for perl.

---

### Post by pmasiar on 2008-07-21
> **SNYP40A1 said:**
> I have a Perl script which I want to run on Windows machines that do not have Perl.  Is there a compiler that will create an C++ based executable from the Perl script?

No, C++ lacks many features used in Perl, like dynamic typing. It will not be easy to create such a compiler.

Just install ActiveState Perl and run your Perl code as is.

---

### Post by ceclauson on 2008-07-22
I don't think this project is done yet, but this is probably what you're looking for:

[http://code.google.com/p/shedskin/](http://code.google.com/p/shedskin/)

*edit*

Oops, my mistake, I thought you said Python...

*edit*

Wait, the title *does* say Python!

---

### Post by loell on 2008-07-22
CPAN is wonderful :biggrin:

you could use

[PAR-Packer]("http://search.cpan.org/~smueller/PAR-Packer-0.980/lib/pp.pm")

---

### Post by SNYP40A1 on 2008-07-22
> **ceclauson said:**
> I don't think this project is done yet, but this is probably what you're looking for:

[http://code.google.com/p/shedskin/](http://code.google.com/p/shedskin/)

*edit*

Oops, my mistake, I thought you said Python...

*edit*

Wait, the title *does* say Python!

I was thinking about the previous post when I was typing the title.  Sorry for creating confusion.

---

