---
title: "Seeing the output of a C file"
date: 2006-05-18
forum: Programming Talk
---

### Post by TrendyDark on 2006-05-18
I'm just starting out learning C. I decided to learn it the other day. I looked up a beginner's guide on the internet()and i wrote out the first program they have:

```
 #include
<stdio.h>

int main()
{
  printf( "Hello\n" );
  getchar();
  return 0;
}

```

but when I save it as "test.c" and run it in the terminal using "gcc test.c" nothing happens. I get an error code. I know this is simple, but I'm a newbie to programming. haha, please don't hate me](*,)

error:

```
test.c:1:9: error: #include expects "FILENAME" or <FILENAME>
test.c:2: error: syntax error before &#8216;<&#8217; token
test.c:7: warning: data definition has no type or storage class
test.c:8: error: syntax error before &#8216;return&#8217;

```

---

### Post by Gustav on 2006-05-18
there should be no linebreak between #include and <stdio.h>

And I don't hate you :)

---

### Post by TrendyDark on 2006-05-18
Thanks, that got rid of the error message. Nothing shows up in the terminal when I run it though, is that suppose to be that way?

---

### Post by xenmax on 2006-05-18
"gcc test.c" will only compile your code and create an executable for you. You have to run it yourself. There should be a file called a.out in dir where you compiled your program. To run it, try 
```
./a.out
```

---

### Post by TrendyDark on 2006-05-18
Thanks, again, I know it's simple. lol

---

### Post by cstudent on 2006-05-18
If you would like to compile it with a name for the executable do:

```

gcc test.c -o test

```


PS

To run your test executable do:

```

./test

```


.

---

### Post by lnostdal on 2006-05-19
great book to get you further started with GCC:
[http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/)

and of course:
[http://gcc.gnu.org/onlinedocs/gcc/](http://gcc.gnu.org/onlinedocs/gcc/)

---

