---
title: "Mono Develop problem"
date: 2010-10-31
forum: Programming Talk
---

### Post by marin123 on 2010-10-31
i have this line of code:

Console.WriteLine ("Enter radius:");
		double radius = Console.Read();

and when i execute it in mono (ctrl+f5) i dont get prompted for entering a value, but instead, i get back radius=-1.
if i change Read with ReadLine, i get an error stating that string cannot be null. obviously mono doest wait for my input...
what is the problem? how can i execute this program so i can input a value?

i really dont want to use visual studio, but ill have to if i dont get this sorted out...

---

### Post by matsuzine on 2010-10-31
The output window in monodevelop is read-only.

This link will explain how to configure it to run in a console window instead:

[http://stackoverflow.com/questions/652936/reading-console-input-in-monodevelop]("http://stackoverflow.com/questions/652936/reading-console-input-in-monodevelop")

---

### Post by marin123 on 2010-11-01
thanks! :)

---

### Post by matsuzine on 2010-11-02
You're very welcome!  
( Could you mark the thread solved if that worked for you?  Thanks! )

---

