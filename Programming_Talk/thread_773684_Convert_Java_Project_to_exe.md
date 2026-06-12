---
title: "Convert Java Project to exe"
date: 2008-04-29
forum: Programming Talk
---

### Post by mthalis on 2008-04-29
I created java project using netbeans now i want to convert it single executable file.

---

### Post by CptPicard on 2008-04-29
Java doesn't quite work like that... the closest you can get is to export it as a .jar file with a defined "main" method.

Netbeans builds your .jar automatically for you in the project's build folder, and I suspect it finds your main too for it, but if it doesn't, look into some of the build options, there's probably a way to specify the class that contains main.

---

### Post by mthalis on 2008-04-29
I have to java files,one file contain jframe it contain main method 
other contain file contain java method stuff.if this file can execute different platform it is better.also i have file reader text file inside my project folder.

---

### Post by CptPicard on 2008-04-29
Your project should also have a "build" directory with the .jar, if I'm not mistaken.

---

### Post by mthalis on 2008-04-29
it built .jar file but i use external file,without it not working can i integrate it.that mean i want to include text file too.

---

### Post by CptPicard on 2008-04-29
Oh. In that case, include that file in your project (like copying it into the classpath with your Java source for example), and Google for "loading resources from classpath" or "... from .jar files" or something like that.

---

### Post by mthalis on 2008-04-29
my text file in my project folder,please give me how to do it using example text,plz.

---

### Post by CptPicard on 2008-04-29
[http://www.javaworld.com/javaworld/javaqa/2003-08/01-qa-0808-property.html](http://www.javaworld.com/javaworld/javaqa/2003-08/01-qa-0808-property.html)

Check the "classpath resources" part of the article, it may be helpful.

---

