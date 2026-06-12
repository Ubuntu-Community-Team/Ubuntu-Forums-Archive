---
title: "Foreign Characters in C Programs"
date: 2007-12-29
forum: Programming Talk
---

### Post by ZuLuuuuuu on 2007-12-29
Hello,

What is the most common solution for C programs to solve foreign character problems? (With GCC)

When I don't do any particular thing then on Linux I am able to display foreign characters but when I try some manipulation on them then they can cause some problems; on Windows I can not even display a foreign character. Also I wonder why it can display foreign characters on Linux and not on Windows?

I guess I cannot use UTF-8 source codes, because GCC does not compile them or can it?

---

### Post by daou on 2007-12-29
> **ZuLuuuuuu said:**
> Hello,

What is the most common solution for C programs to solve foreign character problems? (With GCC)


With glib, perhaps. I think they had a string type capable of handling UTF-8... at least glibmm does with ustring.

---

### Post by ZuLuuuuuu on 2007-12-29
> **daou said:**
> With glib, perhaps. I think they had a string type capable of handling UTF-8... at least glibmm does with ustring.

But because we cannot use UTF-8 in source code, we should write them by using escape characters?

---

### Post by daou on 2007-12-29
> **ZuLuuuuuu said:**
> But because we cannot use UTF-8 in source code, we should write them by using escape characters?

Yes, use escapes. It won't look nice in source, but I'm not aware of other ways to do it. btw, glib uses UTF-8 internally for all strings.

---

### Post by ZuLuuuuuu on 2007-12-29
I did some tryings:

 - I tried to use Unicode escape character and Unicode sequences like: "\u0131" which is "&#305;" in Turkish. But on Windows it couldn't be displayed (instead 2 meaningless characters displayed (I think it is because Unicode is 16 bit and ASCII is 8/7 bit?). Also the compiler gave me a warning that Unicode characters can only be used in C99 standard.

 - I put -std=c99 flag while compiling. The warnings has gone but nothing changed, still meaningless characters are displayed.

 - On a GTK+ program (again on Windows) I tried using Turkish characters right away because I also heard about that GTK+ treats strings directly as UTF-8. But, unfortunately, it couldn't be displayed... (What can be the problem?)

 - I tried using Unicode escape sequence above on GTK+ program and it worked.

---

### Post by wolfbone on 2007-12-29
> **ZuLuuuuuu said:**
> But because we cannot use UTF-8 in source code, we should write them by using escape characters?

#include <stddef.h>
#include <stdio.h>

int main () {
  char * str = "Î› âˆª Îž âˆ© ç¾Ž";
  printf("%s\n", str);
}

$ gcc -std=c99 -o aprog aprog.c
$ ./aprog
$ Î› âˆª Îž âˆ© ç¾Ž

Well it may not  look too good in the browser but the string in my source code and program output includes (in TeX) \Lambda, \cup, \Theta, \cap, and the Chinese symbol for beauty.

---

