---
title: "Return path that the .class resides in."
date: 2011-04-28
forum: Programming Talk
---

### Post by stchman on 2011-04-28
Hello all.  I have devised a way to return the absolute path that the .class file resides in.  Does everyone agree or are there better ways.

[PHP]
import java.util.*;
import java.io.*;

public class ReturnPath {
    public static void main( String[] args ) {
        ReturnPath m = new ReturnPath();
        m.getPath();
    }

    public void getPath() {
        File f = new File( "" );
        
        String pathName = f.getAbsolutePath();
        
        System.out.println( pathName );
    }
}

[/PHP]

---

### Post by myrtle1908 on 2011-04-28
You could use the class loader and getResource to do that

```
getClass().getClassLoader().getResource("MyClass.class").toString()
```

---

### Post by stchman on 2011-04-29
Apparently the following command:

```

System.getProperty( "user.dir" )

```

Will return the working directory.

---

