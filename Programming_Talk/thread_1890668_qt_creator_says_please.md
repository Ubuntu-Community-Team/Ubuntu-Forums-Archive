---
title: "qt creator says please"
date: 2011-12-04
forum: Programming Talk
---

### Post by shubham1 on 2011-12-04
the error is in the image
i cant add a qt version please help me add an screen shot would be easy

---

### Post by McNils on 2011-12-04
I installed the program. Here is how the settings looks in my qtcreator.

---

### Post by shubham1 on 2011-12-04
what changes should i make

---

### Post by shubham1 on 2011-12-06
please reply back

---

### Post by shubham1 on 2011-12-06
i just get this problem see the image

---

### Post by shubham1 on 2011-12-06
help me here how to make a qmake file

---

### Post by Zugzwang on 2011-12-06
Try to install the "libqt4-dev" package. This should install everything absolutely needed for QT4 development, along with qmake. See  [http://packages.ubuntu.com/oneiric/libqt4-dev](http://packages.ubuntu.com/oneiric/libqt4-dev) for details. Restart qtcreator afterwards, without loading any old project.

---

### Post by McNils on 2011-12-06
> **shubham1 said:**
> help me here how to make a qmake file
[http://doc.qt.nokia.com/latest/qmake-tutorial.html](http://doc.qt.nokia.com/latest/qmake-tutorial.html)

---

### Post by shubham1 on 2011-12-07
its already installed

---

### Post by shubham1 on 2011-12-07
this windows contiue comming when i open qt if i close it it opens again

---

### Post by shubham1 on 2011-12-07
please some body help i really want to run it

---

### Post by Zugzwang on 2011-12-07
EDIT: Hey, wait, in your screenshot in post #5, QT4 is actually listed as being installed. Remove the additional "manual" lines in the settings dialog, though, as they are not correct.

With respect to this window: when precisely does it appear? "QT" is a library, so you cannot open it. Thus, your description in a bit vague.

---

### Post by shubham1 on 2011-12-07
> **Zugzwang said:**
> EDIT: Hey, wait, in your screenshot in post #5, QT4 is actually listed as being installed. Remove the additional "manual" lines in the settings dialog, though, as they are not correct.

With respect to this window: when precisely does it appear? "QT" is a library, so you cannot open it. Thus, your description in a bit vague.
yes the folder is there

---

### Post by Zugzwang on 2011-12-07
> **shubham1 said:**
> yes the folder is there

Which folder? Sorry, could you elaborate on your answer? Nobody knows which folder you are referring to. Did you remove the additional lines in the dialog?

---

### Post by shubham1 on 2011-12-07
you have edited your post first you asked for a folder

---

### Post by shubham1 on 2011-12-07
> **Zugzwang said:**
> Which folder? Sorry, could you elaborate on your answer? Nobody knows which folder you are referring to. Did you remove the additional lines in the dialog?
ypu have edited your post

---

### Post by Zugzwang on 2011-12-07
> **shubham1 said:**
> ypu have edited your post

Ah, ok, that was non-obvious since you quoted the modified post. Yeah, I've edited the post because I have later seen in your post #5 that apparently qtcreator *was* able to find your qt4-make executable and that you added some non-standard additional reference to development kits that are invalid. Try to remove those and things should work. (Also, I asked for checking if the file "qt4-qmake" is contained in /usr/bin. Since "qt4-qmake" is not a folder, I discarded the possibility that you meant it).

You might still want to answer the following question: 
With respect to this window: when precisely does it appear? "QT" is a library, so you cannot open it. Thus, your description in a bit vague.

---

### Post by shubham1 on 2011-12-08
> **Zugzwang said:**
> Ah, ok, that was non-obvious since you quoted the modified post. Yeah, I've edited the post because I have later seen in your post #5 that apparently qtcreator *was* able to find your qt4-make executable and that you added some non-standard additional reference to development kits that are invalid. Try to remove those and things should work. (Also, I asked for checking if the file "qt4-qmake" is contained in /usr/bin. Since "qt4-qmake" is not a folder, I discarded the possibility that you meant it).

You might still want to answer the following question: 
With respect to this window: when precisely does it appear? "QT" is a library, so you cannot open it. Thus, your description in a bit vague.
when i open qt creator it appears when i close it then it again comes

---

### Post by shubham1 on 2011-12-08
i jsut tried to create a new project and it created but this problem is still on when ever i tries to open new windows in qt should i reinstall it

---

### Post by Zugzwang on 2011-12-08
> **shubham1 said:**
> when i open qt creator it appears when i close it then it again comes

Try to open qtcreator from the terminal without referring to any project. So just typ "qtcreator" in the terminal. Then, copy&paste all qtcreator output that appeared on the terminal here.

Also, did you remove these 2 extra lines in the dialog, as suggested in the posts above?

---

### Post by shubham1 on 2011-12-08
> **Zugzwang said:**
> Try to open qtcreator from the terminal without referring to any project. So just typ "qtcreator" in the terminal. Then, copy&paste all qtcreator output that appeared on the terminal here.

Also, did you remove these 2 extra lines in the dialog, as suggested in the posts above?
[CODE(qtcreator:23474): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qtcreator:23474): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qtcreator:23474): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qtcreator:23474): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Timeout running '/home/shubham/testqt/2dpainting/2dpainting' (30000ms).


][/CODE]
and that ediot popup appears too

---

### Post by Zugzwang on 2011-12-08
> **shubham1 said:**
> and that ediot popup appears too 

And what about the second question that I asked?

---

### Post by shubham1 on 2011-12-08
actually yhte windows is not opening and that ediot popu is comming
reinstall

---

### Post by Zugzwang on 2011-12-08
> **shubham1 said:**
> actually yhte windows is not opening and that ediot popu is comming
reinstall

Is it possible that you named your executable "qtcreator"? Try to start qtcreator from "/tmp/". So open a terminal and type:

```

cd /tmp
qtcreator

```

If the error still persists, please tell us how large the file "/usr/bin/qtcreator" is on your system and which Ubuntu version you are using.

---

### Post by shubham1 on 2011-12-08
Timeout running '/home/shubham/testqt/2dpainting/2dpainting' (30000ms).
Timeout running '/home/shubham/testqt/2dpainting/2dpainting' (30000ms).
Timeout running '/home/shubham/testqt/2dpainting/2dpainting'.
shubham@workspace:~$ cd /tmp
shubham@workspace:/tmp$ qtcreator

(qtcreator:27734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qtcreator:27734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qtcreator:27734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(qtcreator:27734): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by Zugzwang on 2011-12-08
You forgot to answer the second question...

Anyway, my best bet is that you should try to get rid of your QTCreator settings. Unfortunately, where they are depends on your concrete QTCreator version. See, for example, [here]("http://doc.qt.nokia.com/qtcreator-2.2/creator-faq.html").

---

### Post by shubham1 on 2011-12-08
yes your second question get rid of your settings when i open windows its not opening and that ediot popup is comming so i cant should i go for a reinstall

---

### Post by shubham1 on 2011-12-08
i purged qt and then installed again it installed in a flash i dont know how then i opened the windows after much try and did what you said and that worked thanks :)

---

