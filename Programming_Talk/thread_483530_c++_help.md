---
title: "c++ help"
date: 2007-06-24
forum: Programming Talk
---

### Post by zerobinary on 2007-06-24
i dont get what is manipulator

---

### Post by ios_base on 2007-06-25
Why are you asking what a manipulator is?  Can you be more specific?

---

### Post by hod139 on 2007-06-25
Are you asking about IO manipulation?
[http://www.cppreference.com/io_flags.html#format_flags](http://www.cppreference.com/io_flags.html#format_flags)
[http://www.cprogramming.com/tutorial/iomanip.html](http://www.cprogramming.com/tutorial/iomanip.html)

---

### Post by Golyadkin on 2007-06-25
Do you maybe want to overload the C++ manipulator functions?

---

### Post by zerobinary on 2007-06-25
but the book accelrated c++ page 4 say statement std::cout<<"helloworld"<<std::endl 
and std::endl is manipulator just wonder what is it 
plz help
that's all i know 
since i am newbie i don't know how to be more specific

---

### Post by Mis_Uszatek on 2007-06-25
Manipulator in your context...

it is just a 'thing' which manipulates stream(std::cout in your example).
There are more of these manipulators, e.g. you are able to set big letter for example
(it is a pseudocode, I do not remember what is a value)
```

std::cout << std::big_letters << "hello" << std::endl;

```
result is:
```

HELLO\n

```

**hod139** gave you a link
> [http://www.cprogramming.com/tutorial/iomanip.html](http://www.cprogramming.com/tutorial/iomanip.html)

There is a good explanation.

---

### Post by zerobinary on 2007-06-26
errr is there a easier definition for it 
is it basically control ???

plz help me i mean i still don't quite get it

---

### Post by skullmunky on 2007-06-26
i guess you could call it control, or a better description would be "filtering".   the manipulators in the examples in that link below are better examples - they "manipulate" or "filter" the text you're printing by formating it in different ways, changing to upper case or lower case, controlling how many decimal places get printed, etc.  

std::endl  is "end line" - a newline or carriage return.  it doesn't really do any manipulation or filtering, but it's included in the "manipulators" category anyway.

---

### Post by zerobinary on 2007-06-26
thx now i have some idea about it

---

