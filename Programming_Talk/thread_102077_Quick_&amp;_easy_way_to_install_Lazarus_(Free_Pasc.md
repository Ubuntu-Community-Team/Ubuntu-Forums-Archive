---
title: "Quick &amp; easy way to install Lazarus (Free Pascal, Delphi) RPM's under Breezy"
date: 2005-12-11
forum: Programming Talk
---

### Post by doitashimashite on 2005-12-11
Install with Synaptic Package Manager:
libgdk
libgdk-pixbuf2
alien

Then download:
[http://prdownloads.sourceforge.net/lazarus/fpc-2.0.1-050923.i386.rpm?download](http://prdownloads.sourceforge.net/lazarus/fpc-2.0.1-050923.i386.rpm?download)
[http://prdownloads.sourceforge.net/lazarus/lazarus-0.9.10-0.i386.rpm?download](http://prdownloads.sourceforge.net/lazarus/lazarus-0.9.10-0.i386.rpm?download)

Install from command line:
sudo alien -i fpc-2.0.1-050923.i386.rpm
sudo alien -i lazarus-0.9.10-0.i386.rpm

Wanna read more first? Lazarus Project page:
[http://www.lazarus.freepascal.org/modules.php?op=modload&name=StaticPage&file=index&sURL=about](http://www.lazarus.freepascal.org/modules.php?op=modload&name=StaticPage&file=index&sURL=about)

I just tested this under Breezy, and it works wonderfully.

---

### Post by unionjak on 2005-12-19
hello,
can i do the following :-
set up a web page that is a clothes catalogue that enables customers to order which in turn i can process at my end ? Its a big ask, but if yes then its for me. What is your opinion on delphi/laz as far as learning curve, compared to say c++ at the top to say java, c# .net python and smalltalk ?
Many thanks for your time, steve.

---

### Post by pelle.k on 2005-12-20
Delphi is rather easy to learn, but quite powerful nevertheless.
Lazarus is just an IDE for freepascal.
Free Pascal is very compatible with borland pascal, and delphi dialects. But it's not the same.

It's object oriented and functional/procedural. I guess you could say it's like a very very powerful BASIC variant. Closer then most languages anyway.

C++ takes years to master, and is very difficult to learn. Complex and often strange and confusing syntax. Not really suited to the hobbyist programmer, unless you really like a challenge.

Java has a very C ish syntax, but more down to earth (according to some...)
It's not very easy to learn, but probably easier than learning C++ anyway.

C# is a .net language. One of many .net languages. It's considered very friendly to program, because of all .net classes you can utilize in your code. think of classes as tools in you toolbox. .net is a big box, full of handy tools.

python might be the easiest of the above to learn. its very high level. but very handy. python is very common on linux systems, in everything from appz to installer scripts. But it is a scripting language though. it's interpreted and run when you click on it. Not pure machine code as you get when you compile a c++ program. So it's not very fast.

I would say if all you have is some dhtml knowledge, then free pascal or python would be a step in the right direction.

---

### Post by poptones on 2005-12-21
Hmm, I just tried this and it seems to be completely gtk1.2 (ick). The screenshots at the host site show it using gtk2. 

Any suggestions?

---

### Post by unionjak on 2005-12-23
hello,
belive it or not i am still looking for a suitable language to learn, so i hope you can help further...?
If lazerus is not quite pascal, then is it wise for me to learn something that is "new" and possibly not that well supported ?
I have tried small talk, but more often than not, the version control is awfull, and it is prone to crashing, or not being looking as per the "walkthru" and therefor you consentrate on the ide not the actual code. Python has been the best bet yet, but again i dont get on with blackadder, boa, etc`s ide.
What i am getting at is that i would like an ide that is simple, but will grow as you get better. I am lookng at the following....Ruby, python and lazerus.
In your opinion which should i go for, and can you recomend an ide ?
Many thanks, steve.

---

