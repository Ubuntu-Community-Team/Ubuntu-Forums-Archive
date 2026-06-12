---
title: "How to &quot;system&quot; an input command? (C++)"
date: 2008-04-17
forum: Programming Talk
---

### Post by howbag on 2008-04-17
Hey! 
What im trying to do is to run a system("INPUT COMMAND"), replacing the INPUT COMMAND with a string inputed by the user.

What my compiler tells me is that it cannot convert std::string to const char*.

Source¨:
[http://pastebin.ubuntu.com/7280/](http://pastebin.ubuntu.com/7280/)

By the way, im currently on windows if it matters (I program on both win and linux and havent noticed so much of a difference.)

I use code::blocks which is brilliant by the way.

Thanks! :)

---

### Post by pedro_orange on 2008-04-17
The system() command obviously requires a cstring input rather than a c++ string.

To copy a string into a cstring you need to use strcpy()

---

### Post by Zugzwang on 2008-04-17
> **pedro_orange said:**
> To copy a string into a cstring you need to use strcpy()

...not necessarily, you can use the ".c_str()" method of a std::string. For details, see [here]("http://www.cplusplus.com/reference/string/string/c_str.html").

---

### Post by WW on 2008-04-17
Change **system(command)** to **system(command.c_str())**.

---

### Post by pedro_orange on 2008-04-17
> **Zugzwang said:**
> ...not necessarily, you can use the ".c_str()" method of a std::string. For details, see [here]("http://www.cplusplus.com/reference/string/string/c_str.html").

True true. 
Replace the "need to use" from my previous statement to "can use"

:lolflag:

---

### Post by howbag on 2008-04-18
Great thanks! I used the .c_str() addon, and then it worked.

Thanks again :)

([http://pastebin.ubuntu.com/7413/](http://pastebin.ubuntu.com/7413/))

---

