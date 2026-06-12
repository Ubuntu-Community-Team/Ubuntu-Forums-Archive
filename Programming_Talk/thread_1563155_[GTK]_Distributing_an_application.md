---
title: "[GTK] Distributing an application"
date: 2010-08-28
forum: Programming Talk
---

### Post by Odexios on 2010-08-28
Hello everyone!

I'm kind of a noob, so I will ask you to be patient [img]http://forum.gamesvillage.it/images/smilies/asd.gif[/img]

I started programming a few months ago, in March, and I got a decent deftness writing programs in C (I'm completely self-taught, so I had to stick with the Kernighan - Ritchie). I had some experience with Ruby, but it was few years ago, and I never really studied it.

Anyway, after spending some time writing command-line-style programs, I decided to move on and started to learn using GTK. I've just begun; I'm using "The Official GNOME 2 Developer's Guide" and I just (finally) finished the GLib and GObject sections.

Now that I'm starting to make something, I realized that whenever I'll be able (and willing) to release my (groundbreaking) applications I can't make everyone install the developer's libraries.

So, here's the question.

How do you distribute an application without having to make everyone install tons of dependencies? I really haven't the slightest idea XD

And, while we're at it... if anyone has any advice on a good and free Unix-understanding manual (both meanings of free, as a beer too [img]http://forum.gamesvillage.it/images/smilies/asd.gif[/img]), please let me know.

---

### Post by SledgeHammer_999 on 2010-08-28
Users of your programs don't need the "development packages" of GTK to run your program. They need them(the dev-packages) only if they want to compile your programs from source.

Most linux distros come with gtk installed (if they use the Gnome/xfce/lxde DEs). Others have packages in their repos that can be downloaded (if they use KDE).

But if you absolutely have to not have any external dependencies then you must link gtk statically to your program. That means that compiler/linker will take the whole gtk libs and stick them together with your code. This will produce a huge program if it's a simple "hello world" program(because the size of the libs is quite big. 6.5MB for Gtk and 2.4MB for glib in my system).

---

### Post by Odexios on 2010-08-28
> **SledgeHammer_999 said:**
> Users of your programs don't need the "development packages" of GTK to run your program. They need them(the dev-packages) only if they want to compile your programs from source.

Most linux distros come with gtk installed (if they use the Gnome/xfce/lxde DEs). Others have packages in their repos that can be downloaded (if they use KDE).

But if you absolutely have to not have any external dependencies then you must link gtk statically to your program. That means that compiler/linker will take the whole gtk libs and stick them together with your code. This will produce a huge program if it's a simple "hello world" program(because the size of the libs is quite big. 6.5MB for Gtk and 2.4MB for glib in my system).Thanks for the answer. The next question, then, would be...

What's the alternative to compiling from source?

I mean, let's say I just wrote a simple GTK application; can I just compile it and give it away? How does it work?

Wasn't the compiling part machine dependant?

---

### Post by km0r3 on 2010-08-28
> **Odexios said:**
> 
What's the alternative to compiling from source?

I mean, let's say I just wrote a simple GTK application; can I just compile it and give it away? How does it work?

That's one option.

You could also offer binary packages like a [.deb]("http://en.wikipedia.org/wiki/Deb_%28file_format%29") or .exe for your users.

---

### Post by Odexios on 2010-08-28
> **km0r3 said:**
> That's one option.

You could also offer binary packages like a [.deb]("http://en.wikipedia.org/wiki/Deb_%28file_format%29") or .exe for your users.
Ok, that's kinda surprising.

I've always thought that an executable file compiled on a computer didn't necessarily work on a different machine.

I don't really know where I took this idea from, but I was sure that you had to compile from source on the machine you were going to use the application if you wanted to be sure everything would work fine.

Well, as expected it was a noob question. 

Thank you for your answers!

---

### Post by SledgeHammer_999 on 2010-08-28
Well if you compile a program on Ubuntu Lucid then that binary will work on every other Ubuntu Lucid installation(provided that the gtk libs are installed also). It MAY work on other versions of Ubuntu too. It MAY work on other distros too. But that is not entirely sure, since some distros put some libraries in different places and your binary-program may not find them. The most important thing is that a different distro may have an older version of gtk installed than the one you compiled your program with, and if you use new APIs then your program will not work.

Also programs compiled for 32bit OSes probably won't work in 64bit OSes and vice versa. Also programs compiled under Linux won't work under Windows and vice versa.

---

### Post by Odexios on 2010-08-29
> **SledgeHammer_999 said:**
> Well if you compile a program on Ubuntu Lucid then that binary will work on every other Ubuntu Lucid installation(provided that the gtk libs are installed also). It MAY work on other versions of Ubuntu too. It MAY work on other distros too. But that is not entirely sure, since some distros put some libraries in different places and your binary-program may not find them. The most important thing is that a different distro may have an older version of gtk installed than the one you compiled your program with, and if you use new APIs then your program will not work.

Also programs compiled for 32bit OSes probably won't work in 64bit OSes and vice versa. Also programs compiled under Linux won't work under Windows and vice versa.
I expected as much for Windows-Linux compatibility. Thanks for the explanation!

So if I want to distribute an application for both 32bit and 64bit OSes I need to compile two different applications from the same source? Thought 64 bit ones could handle 32 bit software.

---

### Post by James78 on 2010-08-29
> **Odexios said:**
> I expected as much for Windows-Linux compatibility. Thanks for the explanation!

So if I want to distribute an application for both 32bit and 64bit OSes I need to compile two different applications from the same source? Thought 64 bit ones could handle 32 bit software.
They can, but it gets much messier. I have a few 32-bit applications that I can use perfectly, but the thing is that to use them I need to install all the 32-bit versions of the dependency libraries. Actually, it's pretty easy to do with Linux and even Windows. Getlibs will get the 32-bit libraries in Linux, and as for Windows, I'm not entirely sure, but it's supposed to work mostly out of the box.

But the point is, that running a 32-bit app on a 64-bit os isn't a good idea unless you really have to and have no other choice, there's always problems that can arise (especially if the 32-bit app wasn't tested on a 64-bit os). If you can build the binary for both archs, why not do it? It's not too hard, unless you come in with major problems.

---

