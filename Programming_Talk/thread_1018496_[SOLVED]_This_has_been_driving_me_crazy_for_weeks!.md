---
title: "[SOLVED] This has been driving me crazy for weeks!"
date: 2008-12-22
forum: Programming Talk
---

### Post by MONODA on 2008-12-22
I really do not understand why this does not worl properly
[PHP]
bottles = 99
std_verse = "%s bottles of beer on the wall, %s bottles of beer.\n Take one down and pass it around, %s bottles of beer on the wall." % (bottles, bottles, bottles - 1)
while bottles >= 3:
        print std_verse
        bottles = bottles - 1
[/PHP]
it keeps on printing the same verse over and over again, why? I have found other ways to print the lyrics but I just want to know why this wont work.

---

### Post by Tony Flury on 2008-12-22
because it is evaluating the std_verse only once - when bottles=99

even though when you go round the loop - and chance the value of bottles, it does not change the value of std_verse - so think about how you might do that - either change std_verse - or change the code so that use the value of bottles each time through the loop.

---

### Post by MONODA on 2008-12-22
aha, that was a lot easier than it seemed. thanks a lot.

---

### Post by Tony Flury on 2008-12-22
can you mark this thread as solved then - look in the Thread tools at the top of this thread

---

