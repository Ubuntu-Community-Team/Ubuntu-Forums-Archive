---
title: "Is Adobe Air a good cross platform solution?"
date: 2011-01-01
forum: Programming Talk
---

### Post by sideburn on 2011-01-01
If a developer's goal is to create a stand-alone application with one file that can run on all major platforms (linux, mac & windows),  is Adobe Air a good cross platform solution?  What I mean by cross platform, is when the user just download the file and run it without worrying too much about compatibility issues.  And that exact same file can be run on either linux, mac or windows.  The only thing user have to do beforehand is to install Adobe Air in order to read the file.  Any thoughts?

---

### Post by PaulM1985 on 2011-01-01
I don't know too much about Adobe Air, but both Python and Java allow for cross-platform compatibility too.

---

### Post by kostkon on 2011-01-01
It's a good cross platform solution. The only problem is that it's based on Flash; thus, adobe air apps tend to consume a lot of cpu and ram.

---

### Post by dv3500ea on 2011-01-01
You should have a look at [Appcelerator Titanium]("http://www.appcelerator.com/products/titanium-desktop-application-development/"). It is like Adobe Air in that it is cross platform bundled apps but it uses less resources, is open source and is more flexible. You create applications using HTML5, CSS3 and Javascript/Ruby/Python/PHP.

---

### Post by sideburn on 2011-01-01
Appcelerator Titanium looks real good but two things made me wonder...

1)  When you "compile" the code, it says it goes to their "cloud"?  Can you get a copy of "compiled" file offline?

2) Does users have to download Appcelerator Titanium in order to run the "compiled" file or does the users have to access and run the file thru Titanium's "cloud"?

---

### Post by dv3500ea on 2011-01-01
From what I remember, once it has 'compiled' you get a link to a page with download links for Linux, Mac and Windows. For each, you can download a 'bundled' version which is an installer that contains all the dependencies or a 'net install' version which is an installer that downloads dependencies from the internet.

---

### Post by tgalati4 on 2011-01-01
Maybe it's just me, but every Adobe Air widget that I installed on my Ubuntu Jaunty machine ran like molasses.  Fun to look at, but not fast enough for everyday use.

---

### Post by sideburn on 2011-01-01
This what I've gathered from users' experience  (not from developer's experience):

(Adobe Air)
Advantages:
One file that can run on all major platforms

Disadvantage:
Slow performance

(Appcelerator Titanium)
Advantage:
Performance?

Disadvantage:
Cannot run same files across major platforms

(Python)
Advantage:
Performance?
One file that can run on all major platforms?

Disadvantage:
Not user friendly to run file via windows?

(Java)
Advantage:
Performance?
One file that can run on all major platforms?

Disadvantage:
(from my experience),  I cannot just double click "jar" file.  I would have to go to CLI and type "java -jar [filename]"...dont know how is user friendly running jar file on windows and mac.

Free to correct me if I'm wrong...are there other programming options?

---

### Post by tgalati4 on 2011-01-01
That's a great summary.  The other option is to write a cloud application and provide a link.  Google is doing some interesting things in the cloud.

---

### Post by juancarlospaco on 2011-01-02
No.

---

### Post by pelle.k on 2011-01-02
Python + wxpython/pyqt4 (used with py2exe/py2app to contain dependencies on windows/OSX). Or C++ and WxWidgets/Qt4 if that's your thing.
Another option would be to package a simple python webserver like cherrypy (again, with py2exe/py2app) and run the application as a html5 app in a browser window.
Personally, i would replace python with ruby for all the above, but since there is no real equivalent to py2app for ruby/OSX, you loose the full platform compatibility you are seeking right there.

---

