---
title: "java program problem plz help! (Image dir.)"
date: 2009-10-13
forum: Programming Talk
---

### Post by Eremis on 2009-10-13
Hi everybody!

I have a very strange problem. I am trying to insert an icon into a button
and the only way it works in ubuntu is if i specify the whole directory like so:

```

// make a private icon
private ImageIcon newButtonIcon = new ImageIcon("/home/andriy/Desktop/Programming/JAVA/Senior project/Open Encrypt/src/images/new.png");

// make a private button
private JButton newButton = new JButton("New", newButtonIcon);

```

In Windows just doing this works:
```

// make a private icon
private ImageIcon newButtonIcon = new ImageIcon("images/new.png");

// make a private button
private JButton newButton = new JButton("New", newButtonIcon);

```

I want to be able to distribute the application... aka... I dont know the directory's were the program will be on their comp. so I want to just be able to do "images/new.png" instead of the whole "/home/andriy/Desktop/Programming/JAVA/Senior project/Open Encrypt/src/images/new.png".....


BTW I use Netbeans IDE under ubuntu 9.04 if this helps any

Thanks for the help!

---

### Post by PaulM1985 on 2009-10-13
I think the thing is to do with where Netbeans thinks the root folder of the project is.  I couldn't say where to take the path exactly, but try:

"src/images/new.png"

or

"Open Encrypt/src/images/new.png"

I have had the same issue before and been able to reduce it.  Although I think it is just trial and error to how far back to start the path.

Paul

---

### Post by pbrockway2 on 2009-10-13
> 
...
In Windows just doing this works:
...


Java behaves the same way on both OSs: the string argument you use will be resolved agaist the user's current working directory.

> 
I want to be able to distribute the application... aka... I dont know the directory's were the program will be on their comp.


You could use [getResource()/getResourceAsStream()]("http://java.sun.com/javase/6/docs/api/java/lang/Class.html#getResource(java.lang.String)") and put the images along with the .class files that make up the jar. ImageIcon has a constructor that takes a URL argument and this is ideal for accessing images (and other resources) using getResource().  

(This strategy can be followed whether or not the classes and images are packaged up into a jar file.)

If the images really have to be distributed as image files for some reason (like you actually intend the user to change them) then you could put them in some well known location like "user.dir" (the user's current working directory) or "user.home" (their home directory).

---

### Post by Eremis on 2009-10-13
Thanks for the help!

BTW do you know of any examples where getResource()/getResourceAsStream() are used (other then the docs)?

Thanks again!

---

### Post by pbrockway2 on 2009-10-13
I looked around (a little) when I posted before, but didn't see anything all that great.

JavaWorld discusses their use here: [http://www.javaworld.com/javaworld/javaqa/2002-11/02-qa-1122-resources.html]("http://www.javaworld.com/javaworld/javaqa/2002-11/02-qa-1122-resources.html").  But this focuses on the difference between slight variants.

The [Java Developer's Almanac]("http://www.exampledepot.com/") - a reasonable source of usage examples - has nothing (that I can see).

Java2s have this [http://www.java2s.com/Code/JavaAPI/java.lang/ClassgetResourceStringnamerelativetotheclasslocation.htm]("http://www.java2s.com/Code/JavaAPI/java.lang/ClassgetResourceStringnamerelativetotheclasslocation.htm")

Sun's Tutorial includes a usage example of getResource() when talking about ImageIcon.  Specifically, they discuss the implementation of a method that "finds the specified file and returns an ImageIcon for that file, or null if that file couldn't be found".  It's here: [http://java.sun.com/docs/books/tutorial/uiswing/components/icon.html]("http://java.sun.com/docs/books/tutorial/uiswing/components/icon.html")

edit:  I notice in another thread someone has referred you the Tutorial in connection with a Swing question.  Of the examples given above I would give the last (Sun's Tutorial), the highest value.

---

### Post by MrStill on 2009-10-13
Could you not place the image directory in the same folder as you class files or jar file? You can get the system dependent path separator as a static value in (string or character) from class file.

---

