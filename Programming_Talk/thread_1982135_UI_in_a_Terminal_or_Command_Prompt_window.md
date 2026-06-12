---
title: "UI in a Terminal or Command Prompt window"
date: 2012-05-18
forum: Programming Talk
---

### Post by GeissT on 2012-05-18
Hi guys!

First of all I want to say, I love the new theme on the forums :3

Right to the point, I was wondering how I make a UI for a Linux Terminal or a Windows Command Prompt? I am currently working with the C# Language and Mono on Linux and .NET on Windows, I am not 100% sure this can be accomplished with the C# Language, but I guess you won't know unless you ask.

Thanks,

GeissT.

---

### Post by MG&amp;TL on 2012-05-18
You could look at some form of curses library...[http://en.wikipedia.org/wiki/Ncurses]("http://en.wikipedia.org/wiki/Ncurses")

...although I'm not sure it would work with a windows command prompt and/or C#.

---

### Post by PaulM1985 on 2012-05-18
What do you mean exactly?  Do you want to display your own version of the terminal, or do you want to print/read text to/from the terminal using your application?

You can print to the terminal using:
```

Console.WriteLine("Hello I am some text");

```
in C#.

Paul

---

