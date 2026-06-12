---
title: "[SOLVED] Qt Jambi: UnsatisfiedLinkError"
date: 2008-10-17
forum: Programming Talk
---

### Post by snova on 2008-10-17
I'm trying to run the first Qt tutorial app in Java:

[PHP]
import com.trolltech.qt.gui.*;

public class Test
{
    public static void main( String args[] )
    {
        QApplication.initialize( args );
        QPushButton hello = new QPushButton( "Hello World!" );
        hello.resize( 120, 40 );
        hello.setWindowTitle( "Hello World" );
        hello.show();
        QApplication.exec();
    }
}
[/PHP]

Nothing special. Running it, unfortunately, produces:

```

xxxx@xxxxxxxx[03:33]:~/Desktop$ java -cp /usr/share/java/qtjambi.jar:Test.jar Test
Exception in thread "main" java.lang.UnsatisfiedLinkError: com.trolltech.qt.core.QtJambi_LibraryInitializer.__qt_initLibrary()V
        at com.trolltech.qt.core.QtJambi_LibraryInitializer.__qt_initLibrary(Native Method)
        at com.trolltech.qt.core.QtJambi_LibraryInitializer.<clinit>(QtJambi_LibraryInitializer.java:10)
        at com.trolltech.qt.core.QAbstractFileEngineHandler.<clinit>(QAbstractFileEngineHandler.java:10)
        at com.trolltech.qt.QtJambi_LibraryInitializer.<clinit>(QtJambi_LibraryInitializer.java:35)
        at com.trolltech.qt.QtJambiObject.<clinit>(QtJambiObject.java:40)
        at Test.main(Test.java:7)

```

Googling shows that this error has something to do with not finding native Qt libraries, but I can't find a *solution* anywhere.

How do I fix this?

---

### Post by jamesstansell on 2008-10-17
Assuming that you _have_ the proper QT library you need to make sure it's on your library path.  One expedient option to try is the LD_LIBRARY_PATH variable.

I haven't looked at the Jambi docs - do they say anything about the QT libraries?

---

### Post by snova on 2008-10-17
```
LD_LIBRARY_PATH=/usr/lib/jni java -cp /usr/share/java/qtjambi.jar:Test.jar Test
```

Works perfectly. I was expecting it would be a Java setting somewhere, I didn't expect that...

---

