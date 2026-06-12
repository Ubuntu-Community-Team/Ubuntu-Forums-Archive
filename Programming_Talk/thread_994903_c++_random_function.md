---
title: "c++ random function"
date: 2008-11-27
forum: Programming Talk
---

### Post by sandro87 on 2008-11-27
hi everyone, i've been wondering about the random function i c++. when i use the one in the standard library it usually keeps giving the same number (if i want 10 random int, it gives me 10 same int :()

could anyone help how to write my own random function ? i have no idea how to do it ..

tnx

---

### Post by dwhitney67 on 2008-11-27
[php]
#include <cstdlib>
#include <ctime>

int main()
{
  srand(time(0));    // seed the random number generator with a large
                     // number; the current system time (in seconds) is as
                     // good as any other large number.

  int value = rand() % 10;   // This will yield a number in the range [0,9]

  ...
}
[/php]

---

### Post by monkeyking on 2008-11-27
How random do you want it to be?

---

### Post by dribeas on 2008-11-27
> **monkeyking said:**
> How random do you want it to be?

How about this [random number generator]("http://web.archive.org/web/20011027002011/http://dilbert.com/comics/dilbert/archive/images/dilbert2001182781025.gif")?

That's the problem with randomness, you can never be sure.

---

