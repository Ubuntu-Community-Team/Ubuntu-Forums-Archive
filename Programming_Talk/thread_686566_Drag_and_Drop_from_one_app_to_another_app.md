---
title: "Drag and Drop from one app to another app"
date: 2008-02-03
forum: Programming Talk
---

### Post by ayampanggang on 2008-02-03
Is it possible to code an application that accepts a drop (as in "drag and drop") from other application?

for example, i want to create an application that can receive playlist from the rhythmbox music application by dragging and dropping.

this application that i want to develop is a java application.

thank you so much :)

---

### Post by xlinuks on 2008-02-03
> **ayampanggang said:**
> Is it possible to code an application that accepts a drop (as in "drag and drop") from other application?

for example, i want to create an application that can receive playlist from the rhythmbox music application by dragging and dropping.

this application that i want to develop is a java application.

thank you so much :)

1) Yes it's possible to drag from an application (even a native one) to your own Java application.
2) It's much easier to get what you want when dragging _from_ other application than _to_ other application. Because when you drag from an application to yours you can just see what strings the app is sending to you during drag'n'drop and then just (manually) split them.
It's completely different when you drag _to_ an application, especially a native one, cause you have to comply with the rules that such an app is looking for - which as it apparently turns out - requires writing native (C/C++) code.
I had same headache/issue in Java, and posting it didn't help (nobody seems to know):
[http://ubuntuforums.org/showthread.php?t=656954](http://ubuntuforums.org/showthread.php?t=656954)

---

### Post by ayampanggang on 2008-02-03
I've just tried to drag the playlist in rhythmbox to desktop and the data copied is the actual mp3 file. If i want my application to handle such data, this means i'll have to have mp3 processing routine within my program using some kind of mp3 processing library, is that correct?

> you have to comply with the rules that such an app is looking for How do i found out what types of data the app is expecting? Should i refer to the app doc? Because it doesn't seem to be a thing covered in a doc

thank you, you've enlightened me a bit :)

---

### Post by xlinuks on 2008-02-03
> **ayampanggang said:**
> I've just tried to drag the playlist in rhythmbox to desktop and the data copied is the actual mp3 file. If i want my application to handle such data, this means i'll have to have mp3 processing routine within my program using some kind of mp3 processing library, is that correct?

 How do i found out what types of data the app is expecting? Should i refer to the app doc? Because it doesn't seem to be a thing covered in a doc

thank you, you've enlightened me a bit :)

Basically the application that is being dragged over decides what to do with the data. During DND you basically have to do with "links" rather than with real objects, thus, when dragging a file the application tells the path to the file rather than feeding the whole file (which could be several GB).
Here's a very short program that gives you a clue how you can handle DND into your applications (only 7KB, the .jar file is executable created with java 6, but if you unzip it you'll find the source code inside):
[http://xlinuks.googlepages.com/javatransfer.jar](http://xlinuks.googlepages.com/javatransfer.jar)

---

