---
title: "Problem whith mono, C# and gtk#"
date: 2005-08-31
forum: Programming Talk
---

### Post by valter on 2005-08-31
Hi 

I tried [this](http://www.mono-project.com/Gtk:HelloWorld)  tutorial but:


admin@ubuntu:~/c#$ mcs hellow.cs hellow.cs(6) error CS0234: The type or namespace name `Drawing' could not be found in namespace `System'
hellow.cs(17) error CS0246: Cannot find type 'DeleteEventArgs'
hellow.cs(3) error CS0246: The namespace `Gtk' can not be found (missing assembly reference?)
    Try using -pkg:gtk-sharp
hellow.cs(4) error CS0246: The namespace `GtkSharp' can not be found (missing assembly reference?)
    Try using -pkg:gtk-sharp
hellow.cs(6) error CS0234: The type or namespace name `Drawing' could not be found in namespace `System'
hellow.cs(6) error CS0246: The namespace `System.Drawing' can not be found (missing assembly reference?)
    Try using -r:System.Drawing
Compilation failed: 6 error(s), 0 warnings
admin@ubuntu:~/c#$

Yes gtk-sharp is installed and gtk-sharp2 too. Is problem in backports packages?  :-?

---

### Post by LordHunter317 on 2005-08-31
[QUOTE=valter]Hi 

I tried [this](http://www.mono-project.com/Gtk:HelloWorld)  tutorial but:


admin@ubuntu:~/c#$ mcs hellow.cs hellow.cs(6) error CS0234: The type or namespace name `Drawing' could not be found in namespace `System'
hellow.cs(17) error CS0246: Cannot find type 'DeleteEventArgs'
hellow.cs(3) error CS0246: The namespace `Gtk' can not be found (missing assembly reference?)
    Try using -pkg:gtk-sharp
hellow.cs(4) error CS0246: The namespace `GtkSharp' can not be found (missing assembly reference?)
    Try using -pkg:gtk-sharp
hellow.cs(6) error CS0234: The type or namespace name `Drawing' could not be found in namespace `System'
hellow.cs(6) error CS0246: The namespace `System.Drawing' can not be found (missing assembly reference?)
    Try using -r:System.Drawing
Compilation failed: 6 error(s), 0 warnings
admin@ubuntu:~/c#$

Yes gtk-sharp is installed and gtk-sharp2 too. Is problem in backports packages?  :-?[/QUOTE]
 Did you umm, try the steps to correct the problem the compiler gave you?

---

### Post by valter on 2005-08-31
[QUOTE=LordHunter317]Did you umm, try the steps to correct the problem the compiler gave you?[/QUOTE]
 Maybe you can advice what I should to. I have installed all I found in repositories about mono c# and gtk# - what else?
And I tried 
mcs -r:System.Drawing
still errors

---

### Post by LordHunter317 on 2005-08-31
It told you to do more than that.

I hate to be harsh, but if you cannot try all the recommended compiler options and post the error, perhaps you should fine a new language or line of work.

The error isn't especially cryptic and it tells you exactly what to do, afterall.

---

### Post by valter on 2005-09-01
[QUOTE=LordHunter317]It told you to do more than that.

I hate to be harsh, but if you cannot try all the recommended compiler options and post the error, perhaps you should fine a new language or line of work.

The error isn't especially cryptic and it tells you exactly what to do, afterall.[/QUOTE]
I am very sorry if I upset you, didn't want to.
I misunderstand the output -pkg:gtk-sharp. I thought that it recommends me to install the gtk-sharp but now I see that there's a "-" and the problem is solved. Sorry again - my mistake, I should have seen that before. That was my first try width C#, so I can forgive myself that  - maybe you can too. Thanks for your time, I appreciate that

---

### Post by LordHunter317 on 2005-09-01
No, it's ok.  It's just extremely fustrating for me when the program tells you how to solve your problem and you don't even try it first ;)

I understand misreading the output, I do it all the time ;)

---

