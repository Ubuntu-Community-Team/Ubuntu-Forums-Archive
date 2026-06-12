---
title: "C++ How to flush stream?"
date: 2009-12-17
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-17
Hello.

I need a way to correctly use the sleep() function, using library <uninstd.h>

for example, when I use

int main()
{
cout << "text";
sleep(10);
...
}

I have to wait 10 seconds because cpu sleeps. How can I flush stream or make program work immediately (not to wait 10 seconds)?

---

### Post by TheBuzzSaw on 2009-12-17
```
cout.flush();
```

Another way is to use the **endl** line-break. That automatically flushes.

```
cout << "text" << endl;
```

---

### Post by dwhitney67 on 2009-12-17
@ the OP -

What is point of calling sleep()?  What were you hoping to gain by it?

---

### Post by OVERPOWER8 on 2009-12-17
> **TheBuzzSaw said:**
> ```
cout.flush();
```Another way is to use the **endl** line-break. That automatically flushes.

```
cout << "text" << endl;
```

Thanks, TheBuzzSaw, your post was quite helpfull.

---

### Post by OVERPOWER8 on 2009-12-17
> **dwhitney67 said:**
> @ the OP -

What is point of calling sleep()?  What were you hoping to gain by it?

I needed time dalay.

Program above is just an example.

---

### Post by dwhitney67 on 2009-12-17
That's obvious... the time delay... by why?

If all you wanted to do is block the program from exiting until you have seen the output, then just read from the user.

```

#include <iostream>

int main()
{
   std::cout << "test" << std::endl;
   std::cin.get();
}

```

---

### Post by TheBuzzSaw on 2009-12-17
> **dwhitney67 said:**
> That's obvious... the time delay... by why?

If all you wanted to do is block the program from exiting until you have seen the output, then just read from the user.

```

#include <iostream>

int main()
{
   std::cout << "test" << std::endl;
   std::cin.get();
}

```

You are oversimplifying his point. He probably needs the timer for other applications. He is just running a really simple, dry test just to understand how it behaves. You really shouldn't pry so deeply into his intent.

---

### Post by Habbit on 2009-12-18
The "flush" operation is also available as an IO manipulator, so it can be used with the << operator: ```
std::cout << "mytext" << std::flush;
sleep(10);
```

Additionally, the "endl" manipulator is equivalent to writing a line terminator *and* flushing the stream.

---

