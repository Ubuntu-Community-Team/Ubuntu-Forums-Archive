---
title: "[Java] Trouble Installing Google Guice"
date: 2012-10-24
forum: Programming Talk
---

### Post by Skootle on 2012-10-24
Hi,

I'm trying to play around with Google Guice and I can't seem to get it set up properly.

I have installed it as follows:
```
sudo apt-get install libguice-java libguice-java-doc
```

Following [this tutorial]("http://www.theserverside.com/tutorial/Getting-Started-with-Google-Guice-Configuring-Your-Environment"), I am trying to compile this simple program:

```
import com.google.inject.*;

public class GumRunner {

   public static void main(String args[]){

      Injector injector = Guice.createInjector();
     System.out.println(injector);

  }
}
```

and I get the following error when compiling:
```

$ javac GumRunner.java 
GumRunner.java:1: error: package com.google.inject does not exist
import com.google.inject.*;
^
GumRunner.java:7: error: cannot find symbol
      Injector injector = Guice.createInjector();
      ^
  symbol:   class Injector
  location: class GumRunner
GumRunner.java:7: error: cannot find symbol
      Injector injector = Guice.createInjector();
                          ^
  symbol:   variable Guice
  location: class GumRunner
3 errors

```

Any ideas as to why this isn't working? I'm a newbie with Java, so please be gentle!

---

### Post by spjackson on 2012-10-24
I don't know Guice, but that first error indicates that whatever .jar(s) are needed are not on the default classpath.

If you try
```

javac -verbose GumRunner.java

```
it should tell you where it's looking.

The tutorial you link to compiles with a classpath specified, but that's for Windows.

I think that you'll need something like:
```

javac -classpath /usr/share/java/guice.jar GumRunner.java

```

---

### Post by Skootle on 2012-10-26
Hi Spjackson,

Thanks, this really helped. Just had to add . and /usr/share/java/javax.inject.jar to the classpath, i.e.

```
javac -cp '.:/usr/share/java/guice-3.0.jar:/usr/share/java/javax.inject.jar' GumRunner.java
```

Thanks again :)

---

