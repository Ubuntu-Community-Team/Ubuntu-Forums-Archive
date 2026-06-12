---
title: "Compiling in Geany - *.exe file"
date: 2010-09-28
forum: Programming Talk
---

### Post by _albatros on 2010-09-28
Hi,
influenced the compile (Delphi) in Geany is set up some files but I do not see the *. exe (needed for school). Is it the fault of the program settings? If not, what other word recommend?

---

### Post by NovaAesa on 2010-09-28
Ubuntu doesn't use .exe files. Are you using Windows or trying to cross-compile or something like that? I'm having trouble understanding your question, would you be able to elaborate?

---

### Post by _albatros on 2010-09-28
When compiling a program in Pascal in the FPC was created *.exe file. Why is not created when compiling a program in Delphi?

---

### Post by matthew.ball on 2010-09-28
Sorry, I take it English isn't your first language.

FPC is a cross-platform Pascal compiler. This means you can write your source code on GNU/Linux and produce an executable file which can be run on Windows. During the compilation, there would have been an option for a "host" system (most probably GNU/Linux), and an option for a "target" system (most probably Windows).

Note that an executable file for Windows will **not** run on GNU/Linux (bare WINE or whatever), likewise, an executable file for GNU/Linux will not run on Windows.

I'm not sure what Delphi compiler you are using, but just doing a quick google search returns results about a cross-platform Delphi compiler "in the works" but nothing about the actual compiler. 

Some more googling returns [this]("http://www.embarcadero.com/products/delphi-prism/delphi-prism-downloads") but it costs money and you only get access to a trial version.

Some more googling returns [this]("http://www.freebyte.com/programming/delphi/#freedelphiides") which mentions [Lazarus + Free Pascal]("http://www.freebyte.com/programming/pascal/") but I don't really think this would be what you want.

In short, I don't think it's possible. But note that I have only very briefly searched google, it's possible there is something out there and I just missed it.

---

