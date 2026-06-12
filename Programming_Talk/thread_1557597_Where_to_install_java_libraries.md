---
title: "Where to install java libraries?"
date: 2010-08-21
forum: Programming Talk
---

### Post by PeterChrisF on 2010-08-21
Hi Folks, I just downloaded a java library (Joda Time) and I am wondering where I am "supposed" to stick it.  /usr/lib/java? /usr/local/lib/java??  Does it matter, and if so, why?  I have multiple,local users on my system.  Is /usr/lib supposed to be for remote and local users, while /usr/local/lib for local only?  

I have this link: [http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSE18](http://www.pathname.com/fhs/pub/fhs-2.3.html#PURPOSE18) which goes through a quick explanation, but since there a few examples, I am many times left wondering.

Thanks
Pete

---

### Post by phrostbyte on 2010-08-21
Usually there is a variable defined called $CLASSPATH that tells the JVM where to look for classes should something you run reference one.

Note that Java is a bit tricky in that the directory structure must follow package conventions.


Eg if $CLASSPATH is /opt/java

and you have a class named org.foo.bar.ninja.WidgetFactory

It should be in:

/opt/java/org/foo/bar/ninja/WidgetFactory.class

If your Java stuff is in a jar file this shouldn't be a problem since the jar file should follow package conventions.

---

### Post by shadylookin on 2010-08-21
you can put it anywhere. When you want to use it with a program you add it to your java classpath.

java -cp LIBRARY_NAME.jar CLASSFILE_NAME

---

