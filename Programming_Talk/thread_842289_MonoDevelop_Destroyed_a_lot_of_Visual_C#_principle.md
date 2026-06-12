---
title: "MonoDevelop Destroyed a lot of Visual C# principles"
date: 2008-06-27
forum: Programming Talk
---

### Post by dinbrca on 2008-06-27
Things I have done with visual C# in Windows XP I cant do with MonoDevelop for example:
the Clipboard..
If i want to do some Clipboard functions like Clipboard,Clear() then it is diffrent in MonoDevelop.. can someone show me how to do it?

---

### Post by nvteighen on 2008-06-27
> **dinbrca said:**
> Things I have done with visual C# in Windows XP I cant do with MonoDevelop for example:
the Clipboard..
If i want to do some Clipboard functions like Clipboard,Clear() then it is diffrent in MonoDevelop.. can someone show me how to do it?

Actually, because there's no clipboard in GNOME... :) (KDE seems to have one?)

---

### Post by dinbrca on 2008-06-27
then how do i get or set the ctrl+x, ctrl+c, ctrl+v?

---

### Post by Quikee on 2008-06-27
There is some sort of clipboard - the "visible" difference is that the content of the clipboard vanishes if the application that owned the content is closed.

The documentation for GTK# I found: [Gtk.Clipboard]("http://www.go-mono.com/docs/index.aspx?link=T%3AGtk.Clipboard")

However I don't know why this shouldn't work with Windows.Forms in the same way - that is if you have all the necessary packages for Windows.Forms installed.

---

### Post by dinbrca on 2008-06-27
plus how do i do MessageBox.Show?

---

### Post by Quikee on 2008-06-27
> **dinbrca said:**
> plus how do i do MessageBox.Show?

OK, For your sake I learned how to program in C# and use MonoDevelop!

I see what your problem is... you are probably used to work with Windows.Forms in VisualStudio which are not available by default in MonoDevelop. 

First you need to check if you have Windows.Forms available at all - just install libmono-winforms1.0-cil and libmono-winforms2.0-cil from a package manager (like Synaptic for example or just execute "sudo apt-get install libmono-winforms1.0-cil libmono-winforms2.0-cil" in console).

The next step is to actually use them in your project. Generate a new project - if you don't yet have done so - and in the left (solution) pane select "references", right click on "references" and click "edit refrences". A dialog shows up and in the dialog search for "System.Windows.Forms" and enable it + "OK".

Now you can say "using System.Windows.Forms;" in your solutions *.cs files and can "normally" use at least "MessageBox.Show("Booo!");"

Have fun!

---

### Post by dinbrca on 2008-06-27
yes ok thx but if i use System.Windows.Forms will the software work on Ubuntu? Cause I am working on a nice program and i want ubuntu repositories to have it (if they can)..

---

### Post by CptPicard on 2008-06-27
FWIW Monodevelop is for writing C# code on Linux, not for doing "Windows programming". If you want to code for Windows, use Windows... this *is* a different platform.

---

### Post by Quikee on 2008-06-27
It should work for the most part - but the look and feel probably won't be the same as in a Gnome application. The alternative is to use GTK# but for this you need to learn how to use it - via MonoDoc for example.

---

### Post by LaRoza on 2008-06-27
> **dinbrca said:**
> yes ok thx but if i use System.Windows.Forms will the software work on Ubuntu? Cause I am working on a nice program and i want ubuntu repositories to have it (if they can)..

Yes, it will work. See: [http://ubuntuforums.org/showthread.php?t=841842](http://ubuntuforums.org/showthread.php?t=841842)

While I do recommend you don't use it if you can help it, as System.Windows.Forms isn't part of the ECMA standard (see, it is Microsoft that is not standards compliant. They never are, even for the standards they write)

MonoDevelop is an IDE. You can use mcs from the command line, which is easier.

Also, Visual C# destroys a lot of C# principles, as they go against the standard.

---

### Post by Quikee on 2008-06-27
> **LaRoza said:**
> MonoDevelop is an IDE. You can use mcs from the command line, which is easier.


Why easier? As I said it is the first time I used MonoDevelop and all I had to figure out is how to enable packages so I could do winforms stuff which is nicely displayed in a dialog - after that its only F8 / F5 for the most part.

In console you have to do the same actually just you have to figure it out yourself how to add references and what the name of the reference actually should be - this is not obvious.

---

### Post by LaRoza on 2008-06-27
> **Quikee said:**
> Why easier? As I said it is the first time I used MonoDevelop and all I had to figure out is how to enable packages so I could do winforms stuff which is nicely displayed in a dialog - after that its only F8 / F5 for the most part.

In console you have to do the same actually just you have to figure it out yourself how to add references and what the name of the reference actually should be - this is not obvious.

```

man mcs

```

Pipe it into grep when needed, and the answers are all there.

I don't see any threads about mcs (or other tools) not working from the command line, but I see oodles of threads about some IDE not working with some library and some such. IDE's aren't easier. When they work, they hide everything, when they don't work, you are stuck.

---

### Post by nvteighen on 2008-06-27
> **LaRoza said:**
> 
I don't see any threads about mcs (or other tools) not working from the command line, but I see oodles of threads about some IDE not working with some library and some such. IDE's aren't easier. When they work, they hide everything, when they don't work, you are stuck.

You're so right...

---

### Post by Quikee on 2008-06-27
> **LaRoza said:**
> ```

man mcs

```

Pipe it into grep when needed, and the answers are all there.

I don't see any threads about mcs (or other tools) not working from the command line, but I see oodles of threads about some IDE not working with some library and some such. IDE's aren't easier. When they work, they hide everything, when they don't work, you are stuck.

"man mcs" did not give me any information about what resource name for mono-winforms library should I use or if I even have it available in the system.

IDE are easier because it automates all the repeating tasks and undesired tasks that a programmer otherwise needs to do by hand. It also makes libraries and resource management easier which can be a pain in the ***. 

If it doesn't work I'm not stuck - the same way I'm not stuck if x.org fails to load on boot of Ubuntu. I still have the console way to compile/build if for some obscure bug in the IDE I am forced to do so.

For any serious project I would need to use autotools or any other build system for building anyway. Why shouldn't the IDE just do the scripts and I just modify them if needed - there is no hiding here - it just automates the boring stuff.

Also where is the logic if more people have problems with an IDE (for whatever reason) this means that compiling by hand is easier. I don't understand. Its like saying bananas are tastier than apples because I saw more rotten apples than bananas in the supermarket. 

I am sorry but the argument about libraries is just childish. I have yet to see a IDE that hides what it is doing - at building it will of course invoke the compiler, the parameters are configured in the project and are usually set to some sane default so you mostly don't need to bother if you don't want to.

---

### Post by LaRoza on 2008-06-27
> **Quikee said:**
> "man mcs" did not give me any information about what resource name for mono-winforms library should I use or if I even have it available in the system.

IDE are easier because it automates all the repeating tasks and undesired tasks that a programmer otherwise needs to do by hand. It also makes libraries and resource management easier which can be a pain in the ***. 

If it doesn't work I'm not stuck - the same way I'm not stuck if x.org fails to load on boot of Ubuntu. I still have the console way to compile/build if for some obscure bug in the IDE I am forced to do so.

For any serious project I would need to use autotools or any other build system for building anyway. Why shouldn't the IDE just do the scripts and I just modify them if needed - there is no hiding here - it just automates the boring stuff.

Also where is the logic if more people have problems with an IDE (for whatever reason) this means that compiling by hand is easier. I don't understand. Its like saying bananas are tastier than apples because I saw more rotten apples than bananas in the supermarket. 
Here is a case study for you: [http://ubuntuforums.org/showthread.php?t=841842](http://ubuntuforums.org/showthread.php?t=841842)

I am not really interested in arguing this, I don't feel a need to convince you otherwise.

> 
I am sorry but the argument about libraries is just childish. I have yet to see a IDE that hides what it is doing - at building it will of course invoke the compiler, the parameters are configured in the project and are usually set to some sane default so you mostly don't need to bother if you don't want to.

This forum is loaded with threads of users of IDE's not being able to compile, and people being unable to help and just giving the manual command line method (which works)

---

### Post by CptPicard on 2008-06-27
Quikee, the simple point to take home from your argument just is that you're a power-user enough so that the IDE doesn't help you less than it confuses you.

IDEs of course are valuable, but only after a certain point. I fought IDEs too for a long time (esp. with C++) until I bit the bullet and just learned to do it by hand first. At that point IDEs can become useful... when you're able to fix things on your own when the IDE isn't working. Of course, 95% of the time it will work, and will save your time. The 5% of the time, you're totally hosed if you're not competent.

---

### Post by Quikee on 2008-06-27
> **CptPicard said:**
> Quikee, the simple point to take home from your argument just is that you're a power-user enough so that the IDE doesn't help you less than it confuses you.

IDEs of course are valuable, but only after a certain point. I fought IDEs too for a long time (esp. with C++) until I bit the bullet and just learned to do it by hand first. At that point IDEs can become useful... when you're able to fix things on your own when the IDE isn't working. Of course, 95% of the time it will work, and will save your time. The 5% of the time, you're totally hosed if you're not competent.

I agree.. and I have similar experience from the past and still do a lot of building and programming by hand and without and IDE. 

But I can't accept that building by hand is easier that by IDE - because it isn't. There are a lot of programmers that don't know and care how the IDE compiles the program and where it gets and how it link libraries together. If some IDE has a bug and doesn't compile as it should it doesn't influences this fact. If it is hard to analyze why and how the IDE does not behave correctly it still doesn't influences this fact either - the problem is completely different. 

I am sorry LaRoza, but when I see something with what I don't agree - I need to respond.

---

### Post by LaRoza on 2008-06-27
> **Quikee said:**
> I agree.. and I have similar experience from the past and still do a lot of building and programming by hand and without and IDE. 

But I can't accept that building by hand is easier that by IDE - because it isn't. There are a lot of programmers that don't know and care how the IDE compiles the program and where it gets and how it link libraries together. If some IDE has a bug and doesn't compile as it should it doesn't influences this fact. If it is hard to analyze why and how the IDE does not behave correctly it still doesn't influences this fact either - the problem is completely different. 

I am sorry LaRoza, but when I see something with what I don't agree - I need to respond.

I of course am not against IDE's, I just see a lot of problems caused by them. Technically, any setup is an "IDE", my three terminals (see blog) and CptPicards "slimy" environment are all IDE's.

As for building by hand, a simple "make" is easier than moving the mouse or pressing the function keys :-)

---

### Post by Quikee on 2008-06-27
> **LaRoza said:**
> As for building by hand, a simple "make" is easier than moving the mouse or pressing the function keys :-)

Maybe... but auto compiling on save in Eclipse and occasionally "project clean..." + F5 + "pray you don't see red anymore" vs. "make" - well this is a tough one. :)

---

### Post by slavik on 2008-06-28
> **Quikee said:**
> But I can't accept that building by hand is easier that by IDE - because it isn't. There are a lot of programmers that don't know and care how the IDE compiles the program and where it gets and how it link libraries together. If some IDE has a bug and doesn't compile as it should it doesn't influences this fact. If it is hard to analyze why and how the IDE does not behave correctly it still doesn't influences this fact either - the problem is completely different.

That sentence does not make sense to me at all ...

---

### Post by loell on 2008-06-28
> **slavik said:**
> That sentence does not make sense to me at all ...

maybe because its a paragraph so parsing it as a sentence might be bit large and confusing. :lolflag:

nah.. ;) just trying to be funny, i know i suck at it, just like i suck at IDE and still goes back to command line at compiling things.

---

