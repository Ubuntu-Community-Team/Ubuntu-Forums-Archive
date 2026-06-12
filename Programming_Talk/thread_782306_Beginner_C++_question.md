---
title: "Beginner C++ question"
date: 2008-05-04
forum: Programming Talk
---

### Post by Polar67 on 2008-05-04
Hi Everybody.

I recently started programming again after nearly 2 decades.
Found a book from 1996 on C++ and, given that Linux comes with some nifty tools, i thought i'd give it a try.
I am however having a problem with this piece of, admittedly very basic, code:

#include <iostream>

using namespace std;

int main(void)

{
      cout << "Bip\a\t";
      sleep(10);
      cout << "Bip\a\t";
      sleep(10);
      cout << "Bip\a\n";
}
 
comments:
Originally this was an exercise in output switches, and the "cout" command consisted of one line only, looking like this:

cout << "Bip\a\tBip\a\tBip\a";

The original command gave me 3 Bip's on a line but i only heard one beep from the speakers.
I then added the sleep commands, thinking that i'd force the three "\a" switches apart so that i'd be able to actually _hear_ three beeps.

Instead, and this is basically where i'm :confused: stuck, the program acts kind of like a ketchup bottle, i.e. nothing for 20 seconds and then everything happens at once.
Evidently the "sleep" commands are yanked out of context and executed first.
Please help - what am i doing wrong.

---

### Post by pmasiar on 2008-05-04
What are your goals? If you do not program for living, IMHO time investment needed to really grok C++ is not worth the reward. After 20 years :-) there are more approachable languages. Even if you programmed before, it was 20 years ago, and starting with Python would make sense IMHO.

See my sig

---

### Post by stroyan on 2008-05-04
You need to either flush the cout buffer or set it to be unbuffered.
Either
```

int main(void)

{
    cout << "Bip\a\t";
    cout.flush();
    sleep(10);
    cout << "Bip\a\t";
    cout.flush();
    sleep(10);
    cout << "Bip\a\n";
    return 0;
}
```
or
```

#include <iostream>

using namespace std;

int main(void)

{
    cout << unitbuf;
    cout << "Bip\a\t";
    sleep(10);
    cout << "Bip\a\t";
    sleep(10);
    cout << "Bip\a\n";
    return 0;
}
```

---

### Post by Polar67 on 2008-05-04
> **stroyan said:**
> You need to either flush the cout buffer or set it to be unbuffered.
Either
```

int main(void)

{
    cout << "Bip\a\t";
    cout.flush();
    sleep(10);
    cout << "Bip\a\t";
    cout.flush();
    sleep(10);
    cout << "Bip\a\n";
    return 0;
}
```
or
```

#include <iostream>

using namespace std;

int main(void)

{
    cout << unitbuf;
    cout << "Bip\a\t";
    sleep(10);
    cout << "Bip\a\t";
    sleep(10);
    cout << "Bip\a\n";
    return 0;
}
```
Thanks a bundle. The code worked and i learned something.

---

### Post by Polar67 on 2008-05-05
> **pmasiar said:**
> What are your goals? If you do not program for living, IMHO time investment needed to really grok C++ is not worth the reward. After 20 years :-) there are more approachable languages. Even if you programmed before, it was 20 years ago, and starting with Python would make sense IMHO.

See my sig
Thanks for the promt answer.

My goal - well - from time to time i found myself in need of a small program and it irritated me that i wasn't able to write one.
I gave up on Pascal about 20 years ago on account of too little spare time, so C++ isn't something absolute & holy.
At the moment i've got about 4-6 hrs. a week spare time and i always thought that programming was fun!
My goal: Having an interesting hobby that, while learning something new, might eventually amass to a usefull skill.
My reasons for C++:
1.:Affordable compiler. Checked the first of your suggested links and found that a Python compiler evidently was equally affordable.
2.:Someone told me that Linux and all the other OS's are written mainly in C++. This gave me the idea that C++ was the most universally useful language.

When that is said & done you may very well be right. I certainly haven't as of yet digged that deep into C++. Will therefore give Python some time and see what gives.
Regards

---

### Post by pmasiar on 2008-05-05
Linux is the kernel, and is written in C, not C++. Many other utilities are also in C, for many different reasons.

If your program does not have to be as effective as kernel, you might be better off using language which works harder for you, even if the code is not as effective (your CPU is mostly idling anyway :-) ). Programming in high-level language like Python, is often 10-times as productive (hours spent to finish the code), even if code runs 20%-200% times longer than equivalent C/C++ code. If you run your code only couple of times, you are still saving the time :-)

Ubuntu has many system/GUI programs in Python, the preferred language of sabdfl/Canonical. If you are interested how OS, desktop and other system programs are coded, you may want to check OLPC and Sugar - desktop in Python. It would be easier to comprehend than similar C++ code, IMHO, and one reason is that it takes 5-10 lines of C++ to make same action as 1 line of Python. /me runs to hide from flamewar :-)

---

### Post by CptPicard on 2008-05-05
> 
1.:Affordable compiler. Checked the first of your suggested links and found that a Python compiler evidently was equally affordable.

All of them are. You'd be hard pressed not to find a zero-cost implementation of pretty much any language for Linux :)

> 
2.:Someone told me that Linux and all the other OS's are written mainly in C++. This gave me the idea that C++ was the most universally useful language.


There is this strange newbie conception around the forum these days that C/C++ is somehow "the" language to learn... sure, most of the Linux distribution you're using is coded in either C or C++, but seriously... all languages are essentially equally "universal" as long as you're keeping within Turing-completeness. 

For example, I code for a living and am able to code in maybe a dozen languages, and in maybe 5 comfortably... and I won't touch C++ with a 10-foot pole unless I absolutely must, because the gain/pain ratio is too low for my taste. Your algorithmic considerations are either equally well or better served with higher-level languages unless you specifically have to code for the hardware or something...

---

### Post by Can+~ on 2008-05-05
> **pmasiar said:**
> If your program does not have to be as effective as kernel, you might be better off using language which works harder for you, even if the code is not as effective (your CPU is mostly idling anyway :-) ). Programming in high-level language like Python, is often 10-times as productive (hours spent to finish the code), even if code runs 20%-200% times longer than equivalent C/C++ code. If you run your code only couple of times, you are still saving the time :-)

Agree with that, I just made an script that parses certain web pages, checks for links and downloads them if they don't exist locally. Total: 120 lines, using os, time, htmllib modules.

Who cares on raw speed, when your hardware is probably capable on handling 100x times the task you're asking (Unless you work on some pretty intensive algorithms, which, I doubt). In my case, everything was limited to the broadband connection, and I don't mind waiting a few extra seconds.

If I needed raw speed, I would probably write the intensive sections on C(++), the rest on python.

---

### Post by LaRoza on 2008-05-05
> **Polar67 said:**
> 
At the moment i've got about 4-6 hrs. a week spare time and i always thought that programming was fun!
My goal: Having an interesting hobby that, while learning something new, might eventually amass to a usefull skill.
My reasons for C++:
1.:Affordable compiler. Checked the first of your suggested links and found that a Python compiler evidently was equally affordable.
2.:Someone told me that Linux and all the other OS's are written mainly in C++. This gave me the idea that C++ was the most universally useful language.

If you want to have fun and have limited time, you might want to try a language that allows you to do more with less effort.

My wiki is full of free languages, in fact, there are relatively few languages that aren't free.

C++ isn't the most universally useful language. C is that I would say. A C compiler is essential to any new platform. 

I program for fun also, but have had much more time than you have per week, so I do tend to get side tracked by rather pointless studies (most recent is Brainfuck), but if I had less spare time, I would stick with something that is more useful.

---

