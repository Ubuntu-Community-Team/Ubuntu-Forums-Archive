---
title: "fun with variables"
date: 2007-10-19
forum: Programming Talk
---

### Post by nickoli on 2007-10-19
I need to write a script to count the number of characters in a variable. I wrote this script   test=abc | echo '$test' | wc -c and it keeps coming up with five. I am trying to figure out what I'm missing. The answer should be four. Any help will be appreciated.

---

### Post by Malibu Illusion on 2007-10-20
"" = 1 byte

So:

```
#!/usr/bin/sh
len=`echo "test" | wc -c`
len=`expr $len - 1`
echo "length = $len"
```

= 4 and what you want.

---

### Post by ghostdog74 on 2007-10-20
use awk instead
```

 #var="test"
 # echo $var|awk '{print length}'

```

---

### Post by nickoli on 2007-10-20
Thanks for your help. Awk was my missing command. I never used awk so far. Is there anyway you can give me a brief description of how it works. I really appreciate your help. Once again thanks.
:popcorn:

---

### Post by ghostdog74 on 2007-10-20
this [online boo]("http://www.unix.org.ua/orelly/unix/sedawk/ch07_01.htm")k explains much better than me

---

### Post by CptPicard on 2007-10-20
> **nickoli said:**
> I need to write a script to count the number of characters in a variable. I wrote this script   test=abc | echo '$test' | wc -c and it keeps coming up with five. I am trying to figure out what I'm missing. The answer should be four. Any help will be appreciated.

Just to note what you're doing wrong with your initial solution. The first obvious problem is with quoting. You are using single quotes which prints the literal $test into stdout, which is five characters, which wc -c counts correctly.

The first pipe also does nothing, and I'm not sure these answers you're getting are actual solutions... let's get this straight, you want to count the characters in the *variable name*? In that case, a simple echo "varname" | wc -c should suffice...

---

### Post by nickoli on 2007-10-20
I want to count the text that is assigned to the variable.  #var="test"
 # echo $var|awk '{print length}' appears to  be the solution. Example var=abcdefg the answer should be 7. Thanks for the tip on the quotes. We just started working on them. I've yet to get that down to a science. Obviously. :)

---

### Post by nickoli on 2007-10-20
I see a mistake that I had made on my original posting could have lead to misunderstanding. I had typed test=abc and the answer should be 4 where as it should have actually been 3. Sorry for any misunderstanding on that.

---

