---
title: "Weird Javascript Application Question"
date: 2008-05-09
forum: Programming Talk
---

### Post by open_coder on 2008-05-09
Hello everybody. I have a weird question. I am writing a Music player for the KDE4 desktop. I started using C++ with the Qt4.0 framework. This project was originally for a class. After the class, I decided to continue work on it. Me and my friends started talking about Foobar. Foobar has a component called PanelsUI. This component lets you design the interface you want. In our discussion the idea to incorporate this functionality into Crescendo(working title for the project) was presented. I really loved the idea. 

We eventually decided that it would be much easier to create the interface using HTML, CSS and Javascript. But the application still has its streaming capabilities, and the SQL database where all the information is housed. So that brings me to my question. Can this be done? I know that MacOS X uses HTML, CSS and Javascript to create widgets. I assume the same thing would apply here. I would create the application(now the language has changed to python), have it running and use the Javascript to issue the commands. 

However, the problem is that I don't know Javascript beyond a few sever side includes and injections we used in my computer security class. And I don't want to waste my time learning Javascript if it wont work for the project. So can somebody tell me if this sounds plausible? Or maybe give me a good starting point for research? I know that Mac's Widget can execute command line arguments. Would it be something similar? 

Thanks for the help
Alex

---

### Post by smartbei on 2008-05-09
You may be looking for something like XUL. See [http://www.mozilla.org/projects/xul/](http://www.mozilla.org/projects/xul/) and [http://en.wikipedia.org/wiki/XUL](http://en.wikipedia.org/wiki/XUL) for more information.

---

