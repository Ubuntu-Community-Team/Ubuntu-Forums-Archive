---
title: "JAR File won't show pictures"
date: 2010-12-17
forum: Programming Talk
---

### Post by gustehn on 2010-12-17
Hey!

I have developed a game in java, through windows but switched to ubuntu today due low prestanda on my pc..

The game does show pictures in windows when I run the game but in ubuntu they don't show.

Anyone got a clue ?

---

### Post by r-senior on 2010-12-17
The first thing that springs to mind is the path of the file. Did you use the static methods on System to get the system-dependent path separators?

[../javase/6/docs/api/java/io/File.html#separatorChar]("http://download.oracle.com/javase/6/docs/api/java/io/File.html#separatorChar")

If that is not the problem you probably need to post some details of your code.

---

### Post by PaulM1985 on 2010-12-17
Have you definitely used a relative path to the image rather than an absolute path?

When I have been developing stuff in Java, I tend to package the image in the JAR file.  I then use:

URL url = getClass().getResource("Your/Relative/Path.pic");

To get the file.

Paul

---

### Post by gustehn on 2010-12-17
Okey. the pictures show when I start it through the terminal. but not when I start it as executable in folder. for creating pictures in java I use:

Image img = new ImageIcon("img.gif").getImage();
is this not compatible with linux.(ofcourse if works when starting in terminal but why not as executable in folder ?)

---

### Post by lykeion on 2010-12-17
EDIT:
Misread post, please disregard this...

---

### Post by PaulM1985 on 2010-12-17
This sounds like a relative path issue.  You say you see the images if you navigate the folder in the terminal and can run it, so you are essentially doing:

```
some/Special/Path$java RunGame
```

where if you run from the folder using the UI, I think the equivalent of this happens:

```
root$java /some/Special/Path/RunGame
```

so the pic.gif exists in some special path, so everything is fine on terminal, but it does not exist in root, so it can't find it.

Hopefully this is right, and makes sense.

Like I said earlier, try packaging your images inside the jar file.  It also makes it easier for distribution because everything is packaged together.

Paul

---

### Post by gustehn on 2010-12-17
By this means to include the pictures before making it to a jar in eclipse ? 
I tried to include the pictures in the jar file now. Just dragging it but it did not succeed.

---

### Post by PaulM1985 on 2010-12-18
I'm not sure how you do it in Eclipse.  I know in netbeans that you just need to add the files in the src section of your app, then when it builds it packages all of the images in to you JAR.  I usually have a folder called resources inside the src folder with images and text resources (usually with details of levels for a game) that I want bundled in the JAR for loading at runtime.  

Hopefully it is easy to do in Eclipse. Based on this link [http://dev.eclipse.org/newslists/news.eclipse.platform/msg51124.html](http://dev.eclipse.org/newslists/news.eclipse.platform/msg51124.html) it sounds like the images just have to be in your source directory like in Netbeans.

Paul

---

### Post by Some Penguin on 2010-12-18
Eclipse has the ability to designate 'resource' directories in each project's build path, IIRC.

---

