---
title: "How do you print super-special characters in C++"
date: 2010-01-16
forum: Programming Talk
---

### Post by Eragon0605 on 2010-01-16
How do you print those extra-special characters, such as a one-character smiley and the single-character clubs symbol (like in cards), in C++. I somehow did it by accident at one point, but I just can't remember how to do it.

---

### Post by Zugzwang on 2010-01-16
On the terminal, you can print only characters in the character set. The good old DOS codepage had the characters you described. But at least my Linux character set doesn't:

```

#include <iostream>

int main() {
    std::cout << "\x01" << std::endl;
}

```

---

### Post by Eragon0605 on 2010-01-16
When I compile that, I get a blank window in linux. What is that supposed to print? Is there any way to get those sort of characters in Linux? I am running Ubuntu 9.10.

EDIT: Oh, and I assume that changing the "\x01" to, say, "\x02" would print a different character.

---

### Post by MindSz on 2010-01-16
Look for an ASCII character table and just replace the hex value with whatever you want to print.

---

### Post by Zugzwang on 2010-01-16
> **Eragon0605 said:**
> 
EDIT: Oh, and I assume that changing the "\x01" to, say, "\x02" would print a different character.

See here for a typical old DOS codepage, for example: [http://en.wikipedia.org/wiki/Code_page_437](http://en.wikipedia.org/wiki/Code_page_437) 

However, as already stated, in Linux, this doesn't work.

---

### Post by Eragon0605 on 2010-01-16
> **MindSz said:**
> Look for an ASCII character table and just replace the hex value with whatever you want to print.
Thanks! It works, I don't know why I didn't think of that before... Anyway, the character prints, but it's *really* small. How do I make it bigger?

---

### Post by Zugzwang on 2010-01-16
> **Eragon0605 said:**
> Thanks! It works, I don't know why I didn't think of that before... Anyway, the character prints, but it's *really* small. How do I make it bigger?

Increase the font size used by your terminal window.

---

### Post by Eragon0605 on 2010-01-16
Hahaha... Sorry, I haven't had my coffee yet, so I'm being a bit of an airhead.

---

