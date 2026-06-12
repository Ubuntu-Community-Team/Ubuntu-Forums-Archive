---
title: "open pictures through java GUI"
date: 2011-10-09
forum: Programming Talk
---

### Post by raac on 2011-10-09
Hello guys, let say I have a JList displayed. It contains a bunch of pictures names.
Is it possible to double click on them and open up the correspondent picture?

I'm guessing the pictures need to be placed on the current directory where java is running, but I don't know if I'm able to open them through java GUI.

---

### Post by cgroza on 2011-10-09
I am sure you can. Take a look at this:
[http://stackoverflow.com/questions/299495/java-swing-how-to-add-an-image-to-a-jpanel](http://stackoverflow.com/questions/299495/java-swing-how-to-add-an-image-to-a-jpanel)

You will have to handle the List click events, and do the necessary actions.

---

### Post by ofnuts on 2011-10-09
> **raac said:**
> Hello guys, let say I have a JList displayed. It contains a bunch of pictures names.
Is it possible to double click on them and open up the correspondent picture?
Depends what you call "open up". Is it "display" or "read the data in the file"? Both can be done, the first being a bit more complicated, depending on what you really want to do. 

> **raac said:**
> I'm guessing the pictures need to be placed on the current directory where java is running, but I don't know if I'm able to open them through java GUI.Not necessarily, it depends a lot on how you got the names. Maybe you can use a default directory, or even ask the user where the pictures are on the disk. But on the whole, in an application, you either get the full path to the pictures, or the picture are part of your application (in Java, they would be "resources"), in which case they are found by the classloader.

---

