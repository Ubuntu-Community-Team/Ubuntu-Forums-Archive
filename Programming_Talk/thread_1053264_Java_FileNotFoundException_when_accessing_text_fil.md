---
title: "Java: FileNotFoundException when accessing text files in jar archive"
date: 2009-01-28
forum: Programming Talk
---

### Post by meanburrito920 on 2009-01-28
I recently wrote an interpreter for a dialect of lisp on top of the JVM. It accesses libraries written in the dialect, which are packaged with the jar (as text source). When I access these files through Eclipse, everything works like a charm. However, when the jar'ed version tries to access them, It throws a FileNotFoundException. Does anyone know why this might occur?

---

### Post by shadylookin on 2009-01-28
how are you trying to open the file. 

my guess is you need to open the file like this

getClass().getResource("YOUR FILE NAME");

for instance 

Icon icon = new Icon(getClass().getResource("ICON NAME"));

---

### Post by meanburrito920 on 2009-01-28
I'm trying to open the file with FileInputStream. It is a text file, so I dont believe that getResource is the solution I am looking for. I think the issue is more one of relative working directories.

EDIT:
I looked at getResource and will give it a shot, hopefully it will work.

---

### Post by shadylookin on 2009-01-28
> **meanburrito920 said:**
> I'm trying to open the file with FileInputStream. It is a text file, so I dont believe that getResource is the solution I am looking for. I think the issue is more one of relative working directories.

EDIT:
I looked at getResource and will give it a shot, hopefully it will work.

any luck?

---

### Post by timvoet on 2009-01-28
you cannot open a file from within an archive ( jar ) using FileInputStream.  this goes for jar, zip or other.  As shadylookin said, use getClass().getResource(), or if you want the input stream, you can alternatively use getClass.getResourceAsStream(), which will give you an input stream directly.

hope this helps.

---

### Post by meanburrito920 on 2009-01-30
This still does not work. I set up a test project to demonstrate what I want. I have:

```

Test
  >src
    >lib
      >test.txt
    >stuff
      >Test.class

```
My demo code is:

```

URL fileurl = Class.class.getResource("lib/stuff.txt");

```
but this returns null. according to my directory structure, shouldnt this work?

---

### Post by HotCupOfJava on 2009-01-30
check this out:

[http://www.cejug.org/display/~htmfilho/How+a+jar+file+application+can+access+files+in+itself](http://www.cejug.org/display/~htmfilho/How+a+jar+file+application+can+access+files+in+itself)

the example w/ the .xml file is most like what you are trying to do

---

