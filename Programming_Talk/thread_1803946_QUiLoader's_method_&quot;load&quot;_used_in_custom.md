---
title: "QUiLoader's method &quot;load&quot; used in custom widget results in &quot;Segmentation fault&quot; in Li"
date: 2011-07-14
forum: Programming Talk
---

### Post by mazzzterZ on 2011-07-14
Hi !
I'm writing an interface program using Qt4 and it came time to internationalize it, so I started reading the Qt Documentation. I was happy to see that all forms loaded by QUiLoader are automatically translated, but I stumbled on a problem. Almost the whole interface consists of custom widgets that are put in the forms from designer. Some of the custom widgets use their own forms that they load using QUiLoader class and here the problem appeared. When I start Linguist and choose a translation that is located on a form that uses some of my custom widgets the program ends with "Segmentation Fault". I put a lot of prints to see where Linguist dies and I fount that when I invoke the method "load" from class QUiLoader with valid ui file the application dies. If the file isn't valid it doesn't die. I'm not sure if this is a bug or not so I'm posting it here.

I made a simple example showing the problem.
"Download it":[http://www.filefactory.com/file/cc52b9f/n/DEMO4_zip](http://www.filefactory.com/file/cc52b9f/n/DEMO4_zip) 

P.P. I forgot to mention that I use Qt 4.7.0 because it comes with SDK that is compiled with the same version. I tried using the new one but in my custom widgets I use things like SQL and OpenGL and some more and designer complains that cannot mix 4.7.1/4.7.2/4.7.3 with 4.7.4. I can workaroung the problem with the enviroment variable LD_PRELOAD but it I don't like this solution.

Edit: It will be helpful and if you tell me where I can find help for my problem.
Edit2: If someone confirmed the problem exists please write to be sure that it's not just me.

---

### Post by mazzzterZ on 2011-08-27
In future if someone else is in need:
[http://lists.qt.nokia.com/pipermail/qt-interest/2011-July/034969.html]("http://lists.qt.nokia.com/pipermail/qt-interest/2011-July/034969.html")

---

