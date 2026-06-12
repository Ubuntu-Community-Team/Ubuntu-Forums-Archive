---
title: "Problems Linking with g++"
date: 2008-01-15
forum: Programming Talk
---

### Post by vertex78 on 2008-01-15
I have downloaded a library for serial port programming and I am having problems getting the example programs to compile because of a linking error

Here is how I am trying to compile the program
```

 g++ read_port.cpp -l/usr/local/lib/libserial.so

```

And here is what it gives me
```

/usr/bin/ld: cannot find -l/usr/local/lib/libserial.so
collect2: ld returned 1 exit status

```

Now this files does exist in that directory so I am not sure why it is saying that it cannot find it. There is also a file called libserial.a and I tried linking to that instead but I get the same problems.

---

### Post by WearZeeP on 2008-01-15
Shouldn't there be a space between -l and /?

---

### Post by hod139 on 2008-01-15
Use -L to specify library paths not in the default path and -l to list the library names (dropping the lib prefix and .so suffix).  For your example (since /usr/local/lib/ should be in the default path) it should be:
```

 g++ read_port.cpp -lserial

```
If /usr/local/lib is not in the path, you would write
```

 g++ read_port.cpp -L/usr/local/lib/  -lserial 

```

> **WearZeeP said:**
> Shouldn't there be a space between -l and /?
There does not need to be a space.

---

