---
title: "Erlang"
date: 2009-07-22
forum: Programming Talk
---

### Post by navaneethan on 2009-07-22
How to do erlang in linux?

how to do java in linux?

---

### Post by smartbei on 2009-07-22
**Erlang**
Well, on Ubuntu linux, first install erlang:
```

sudo aptitude install erlang

```
Than check out [http://erlang.org/starting.html](http://erlang.org/starting.html) - It looks like that is a really good start.

**Java**
You have two options - you can use the gcc (Gnu Compiler Collection) compiler, or the sun compiler:
[list]
[*]To use sun's compiler, install sun-java6-jdk
[*]To use gcc's compiler, install gcj-4.3
[/list]
for a test program, try this:
```

public class Test {
    public static void main(String[] args) {
        System.out.println("hello");
    }
}

```

To compile: javac Test.java
To run: java Test

The above example code stolen from: [http://ubuntuforums.org/archive/index.php/t-536521.html](http://ubuntuforums.org/archive/index.php/t-536521.html)

And if that works, just follow any java tutorial on the internet and you will be fine.

---

