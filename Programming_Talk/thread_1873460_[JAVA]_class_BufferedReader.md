---
title: "[JAVA] class BufferedReader"
date: 2011-11-01
forum: Programming Talk
---

### Post by ubu87 on 2011-11-01
I don't understand why this codes generates an error. I'm trying to extend the functionalities of the BufferedeReader class, but it seems that the package doesn't exist, even if I've imported it.

```

import java.io.*;

public class ExtendBufferedReader extends BufferedReader {}

```

the error is:
```

cannot find symbol
symbol  : constructor BufferedReader()
location: class java.io.BufferedReader


```

---

### Post by 11jmb on 2011-11-01
Try making a constructor for your class which calls a BufferedReader constructor. I think the problem is that the compiler is looking for a default constructor for BufferedReader and there isn't one.

---

### Post by ubu87 on 2011-11-01
Done, thank you. 

I've defined a constructor BufferedReader, in which I've defined the method read(), when I work with the class ExtendBufferedReader I call the method read() of the superclass through the keyword super.read(), but again I have problems. I'll post code and error message:

```

import java.lang.*;
import java.io.*;


public class BufferedReader {

public int read()
         throws IOException{

       int k = 5;
       return k;

  }
}



import java.io.*;

public class ExtendBufferedReader extends BufferedReader {

public int read() throws IOException {
      return super.read();
 }



public static void main(String[] args) throws IOException {

       int f;
       f = read();
       System.out.println("f is: "+f);
  }

}

```

error message:
```

non-static variable f cannot be referenced from a static context
                f = read();


```


The definition of main is always: static void main(), so I cannot remove static. And if add static to the read function then super cannot be used anymore.

---

### Post by 11jmb on 2011-11-01
This is because you would need to say something like 

```
ExtendBufferedReader r = new ExtendBufferedReader();
int f = r.read();

```

you are trying to call an instance method from a static method.

I don't think you want your program to extend your homebrew Bufferedreader class though. Don't you want to extend the BufferedReader in the java.io package?

---

### Post by ofnuts on 2011-11-01
> **ubu87 said:**
> Done, thank you. 

I've defined a constructor BufferedReader, in which I've defined the method read(), when I work with the class ExtendBufferedReader I call the method read() of the superclass through the keyword super.read(), but again I have problems. I'll post code and error message:

error message:
```

non-static variable f cannot be referenced from a static context
                f = read();


```The definition of main is always: static void main(), so I cannot remove static. And if add static to the read function then super cannot be used anymore.
read() is an instance method. It won't work unless you have an instance of BufferedReader that know what to read (a plain Reader). Ie, you code has to look like:
```

class ExtendedBufferedReader extends BufferedReader {
// constructor

ExtendedBufferedReader(*... some argument(s), likely a Reader...)* {
   super(reader);
[I]   ... more stuff for your class initialization ...
[/I]}

// Use in code as:

ExtendedBufferedReader ebr=new ExtendedBufferedReader(*... some argument(s), likerly a Reader...*)
f=ebr.read();

```

---

