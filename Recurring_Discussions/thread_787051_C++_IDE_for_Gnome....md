---
title: "C++ IDE for Gnome..."
date: 2008-05-08
forum: Recurring Discussions
---

### Post by Kdar on 2008-05-08
Hello.
I am thinking to use only or mostly Linux in future..
I already have almost everything to do it..

But I need some good IDE as well.. And I am not sure which one is better.

I am just planning to write some C++ ( I am just learning it..)

On Windows I used to use Visual Studio.. It would be nice if I can find something as easy to use as Visual Studio for Linux..

---

### Post by Lau_of_DK on 2008-05-08
> **Kdar said:**
> Hello.
I am thinking to use only or mostly Linux in future..
I already have almost everything to do it..

But I need some good IDE as well.. And I am not sure which one is better.

I am just planning to write some C++ ( I am just learning it..)

On Windows I used to use Visual Studio.. It would be nice if I can find something as easy to use as Visual Studio for Linux..

If you really want to work in C++ then I recommend the Qt4 integration into Eclipse - its fantastic. Eclipse is written in Java so it sucks of course, but its very usable with Qt. Even has a wannabe-intellisense.

```

sudo apt-get install eclipse eclipse-cdt

```

And then download

[Eclipse integration download]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")

...and then read:

[Installation manual]("http://trolltech.com/developer/downloads/qt/qteclipse-installmanual")

Now since Eclipse is written in Java it will sometimes probably hang a bit when youre designing big UIs (ie. more thn 2 buttons), if thats the case:

```

sudo apt-get install qt4-designer

```

Thats it, youre all set in the closet thing to Visual Studio I can think of :)

/Lau

---

### Post by LaRoza on 2008-05-08
> **Kdar said:**
> Hello.
I am thinking to use only or mostly Linux in future..
I already have almost everything to do it..

But I need some good IDE as well.. And I am not sure which one is better.

I am just planning to write some C++ ( I am just learning it..)

On Windows I used to use Visual Studio.. It would be nice if I can find something as easy to use as Visual Studio for Linux..
See the sticky, and every other thread on this.

As for VS being easy, I tried it once and couldn't figure out how to use it to compile a simple hello world. It also didn't have any man pages. It was worthless.

---

### Post by LaRoza on 2008-05-08
> **Lau_of_DK said:**
> If you really want to work in C++ then I recommend the Qt4 integration into Eclipse - its fantastic. Eclipse is written in Java so it sucks of course, but its very usable with Qt. Even has a wannabe-intellisense.


The problem with this is, of course, GNOME used GTK+ ;)

---

### Post by Lau_of_DK on 2008-05-08
> **LaRoza said:**
> The problem with this is, of course, GNOME used GTK+ ;)


LaRoza - Your first post was unhelpful, the second pointless. You can go to sleep now :)


/Lau

---

### Post by Kdar on 2008-05-08
> **Lau_of_DK said:**
> If you really want to work in C++ then I recommend the Qt4 integration into Eclipse - its fantastic. Eclipse is written in Java so it sucks of course, but its very usable with Qt. Even has a wannabe-intellisense.

```

sudo apt-get install eclipse eclipse-cdt

```

And then download

[Eclipse integration download]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")

...and then read:

[Installation manual]("http://trolltech.com/developer/downloads/qt/qteclipse-installmanual")

Now since Eclipse is written in Java it will sometimes probably hang a bit when youre designing big UIs (ie. more thn 2 buttons), if thats the case:

```

sudo apt-get install qt4-designer

```

Thats it, youre all set in the closet thing to Visual Studio I can think of :)

/Lau


Actually I tried Eclipse.. 
But I wasn't able to get it to work.. Maybe I installed it incorrectly.
I will try what you wrote.

---

### Post by LaRoza on 2008-05-08
> **Lau_of_DK said:**
> LaRoza - Your first post was unhelpful, the second pointless. You can go to sleep now :)


/Lau

There is no point in answering the exact same question daily. The sticky was created to fulfill such frequently asked questions.

The second one is pointing out for GNOME development, QT isn't the best option. GTK+ and its tools would be. The sticky has a link to the GUI developer for GTK+ and other toolkits.

---

### Post by Lau_of_DK on 2008-05-08
> **LaRoza said:**
> There is no point in answering the exact same question daily. The sticky was created to fulfill such frequently asked questions.

The second one is pointing out for GNOME development, QT isn't the best option. GTK+ and its tools would be. The sticky has a link to the GUI developer for GTK+ and other toolkits.

I disagree. Qt is to prefer over Gtk+. If nothing else, its good to sometimes go through these threads and bring new developments to the surface. 

In my oppinion that is.
/Lau

---

### Post by LaRoza on 2008-05-08
> **Lau_of_DK said:**
> I disagree. Qt is to prefer over Gtk+. If nothing else, its good to sometimes go through these threads and bring new developments to the surface. 

In my oppinion that is.
/Lau

There are is nothing new here that I see.

---

### Post by WitchCraft on 2008-05-08
> **Kdar said:**
> Actually I tried Eclipse.. 
But I wasn't able to get it to work.. Maybe I installed it incorrectly.
I will try what you wrote.

I recommend Code::Blocks.

It works on Windows, Linux and Mac, is completely free, resembles Visual Studio, and has built in support for wxWidgets.
And in contrast to Eclipse, it's functional and it works.

[SIZE="4"]http://www.codeblocks.org/[/SIZE]

---

### Post by Vadi on 2008-05-08
Geany. If you ever used Notepad++, this is that, but even better.

---

### Post by WitchCraft on 2008-05-08
> **LaRoza said:**
> 
As for VS being easy, I tried it once and couldn't figure out how to use it to compile a simple hello world. It also didn't have any man pages. It was worthless.

There is a blue triange (the run icon as found on any tape recorder / cd player) in the debug toolbar. Click it, and it compiles your entire project. Could it be made any more simple ?

---

### Post by Vadi on 2008-05-08
Uh oh, relax people. Different people expect different things, after using completely different OS's!

---

### Post by rye_ on 2008-05-08
I don't mean to hijack this thread, but...

I'd be really interested to know at what point an IDE (eclipse, codeblocks, borland etc) becomes an advantage over a powerful programming text editor (gedit, textmate).

I've only ever really coded small commandline apps in c/c++ (my code never really cleary adhered to one or the other), and nowadays I'm trying to come to grips with scripting.  That said, I always found a Heavy IDE as bieng a pain.  Is it mainly just for GUI apps that it comes into play?

Thanks,

Ryan

---

### Post by Vadi on 2008-05-08
I think IDE's just help when you're working on enourmous projects, and not so much on the small ones.

---

### Post by samjh on 2008-05-08
> **rye_ said:**
> I don't mean to hijack this thread, but...

I'd be really interested to know at what point an IDE (eclipse, codeblocks, borland etc) becomes an advantage over a powerful programming text editor (gedit, textmate).

I've only ever really coded small commandline apps in c/c++ (my code never really cleary adhered to one or the other), and nowadays I'm trying to come to grips with scripting.  That said, I always found a Heavy IDE as bieng a pain.  Is it mainly just for GUI apps that it comes into play?

There is no advantage for small projects.

But for larger projects involving more than a dozen source files and perhaps multiple people, IDEs are quite useful.

---

### Post by LaRoza on 2008-05-08
> **WitchCraft said:**
> There is a blue triange (the run icon as found on any tape recorder / cd player) in the debug toolbar. Click it, and it compiles your entire project. Could it be made any more simple ?

Of course! A blue triangle. That makes a lot of sense. Just press it and the compiler reads your mind and does exactly what you want. Extraordinary.

---

### Post by LaRoza on 2008-05-08
> **LaRoza said:**
> There are is nothing new here that I see.

I was right. People are just reiterating what is already in the sticky.

I have seen this before...

---

### Post by dempl_dempl on 2008-05-08
so... that was 36 hours before thread like this.... 

A new record !  :D

---

### Post by WitchCraft on 2008-06-21
> **LaRoza said:**
> Of course! A blue triangle. That makes a lot of sense. Just press it and the compiler reads your mind and does exactly what you want. Extraordinary.

A blue triangle, better known (internationally) as run-icon...

Well, if you selected an ADO.NET project instead of a command line project or a dll, then you're the one to blame.

There are of course no man pages on Windows, Microsoft calls the useless 4 DVD part of it's documentation MSDN, but there also is a (less known) useful part, called TechNet. Additionally, there is an awful lot of documentation from MicrosoftPress, but you of course have to pay for it, since Microsoft actually pays it's developers.

As for Visual Studio: It reads your mind. And the Visual Basic edition now comes with built-in spelling correction, and some kind of anti-nonsense grammar test, so you can more easily see infinite loops etc...

It's just annoying that they do not develop a cross-platform version that works on linux and mac, too. they used to, but that was long ago...


> **rye_ said:**
> I don't mean to hijack this thread, but...

I'd be really interested to know at what point an IDE (eclipse, codeblocks, borland etc) becomes an advantage over a powerful programming text editor (gedit, textmate).

I've only ever really coded small commandline apps in c/c++ (my code never really cleary adhered to one or the other), and nowadays I'm trying to come to grips with scripting.  That said, I always found a Heavy IDE as bieng a pain.  Is it mainly just for GUI apps that it comes into play?

Thanks,

Ryan

There is no point in using an IDE, it just takes longer to load, and is more likely to crash without reason. Additionally, you have to read the documentation of the IDE, and you can run into trouble from different IDE versions...

But the advantage is that a good IDE writes the Makefile for you if you have a large project using many libraries.
Code::Blocks writes one makefile that will work on Windows, Mac and Linux...

The specific advantage of MS-VC++ is that it has the standard C++ libraries ported to Windows (unlike MinGw), and it's code is more compact (=smaller), efficient and fault-free than that of GNU-C++. 

But anyway, since there is Scons, who needs makefiles anymore?

(actually I started to write my own python compile scripts. that's much faster than reading the scons documentation, and it allows for pre-C-Preprocessing...)

---

### Post by LaRoza on 2008-06-21
> **WitchCraft said:**
> [noparse][QUOTE=LaRoza;4914588][/noparse]
Well, if you selected an ADO.NET project instead of a command line project or a dll, then you're the one to blame.

There are of course no man pages on Windows, Microsoft calls the useless part MSDN, and the useful part TechNet. Additionally, there is an awful lot of documentation from MicrosoftPress, but you of course have to pay for it, since Microsoft actually pays it's developers.

As for Visual Studio: It reads your mind. And the Visual Basic edition now comes with built-in spelling correction, and some kind of anti-nonsense grammar test, so you can more easily see infinite loops etc...

It's just annoying that they do not develop a cross-platform version that works on linux and mac, too. they used to, but that was long ago...

If you are trying to quote me somehow, please be a little more specific ;)

If you are referring to my efforts to use VS, I did chose command line (and I was also pointing out that nothing is "inuitive" and is based on what one is used to)

---

