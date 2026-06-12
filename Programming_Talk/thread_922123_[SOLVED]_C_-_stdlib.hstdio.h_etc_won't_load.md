---
title: "[SOLVED] C - stdlib.h/stdio.h etc won't load"
date: 2008-09-17
forum: Programming Talk
---

### Post by Mattlock on 2008-09-17
When I go to create the ?makefile using gcc I get errors such as:
 **error: stdio.h: No such file or directory.**
I generally write the programs in a simple text editor and then do the rest from terminal. I need the stdlib etc too.

What's going on and how do I fix it?

I'm new to Linux at home, I use it frequently for Uni but that was already set up for me :). Thanks for any help in advance.
P.S - I had a good search of the forums and couldn't find anything, sorry if this has been asked before!

---

### Post by Sockerdrickan on 2008-09-17
[php]
#include <stdio.h>

int main() {
    puts("lol");

    return 0;
}
[/php]

gcc test.c && ./a.out
that doesn't work?

---

### Post by Mattlock on 2008-09-17
> **Tux0r said:**
> [php]
#include <stdio.h>

int main() {
    puts("lol");

    return 0;
}
[/php]

gcc test.c && ./a.out
that doesn't work?

Nope. Still getting  error: stdio.h: No such file or directory.

^ Perhaps I need to need to be installing something? Sorry, bit of a newbie with setting this up.

---

### Post by LaRoza on 2008-09-17
The sticky addresses this: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by slavik on 2008-09-17
apt-get install build-essential

---

### Post by Mattlock on 2008-09-17
Excellent, thanks a lot!

---

### Post by Sockerdrickan on 2008-09-17
wait what..? ubuntu comes with gcc but not stdio.h?

---

### Post by LaRoza on 2008-09-17
> **Tux0r said:**
> wait what..? ubuntu comes with gcc but not stdio.h?

Yes. It doesn't come with a lot of things, but they are on the CD (the entire build-essential package is on the Ubuntu disk)

---

