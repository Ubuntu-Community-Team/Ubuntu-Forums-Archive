---
title: "whats wrong with this program?"
date: 2010-02-07
forum: Programming Talk
---

### Post by luposolo on 2010-02-07
What, if anything, is wrong with the following cout statement?

```
cout >> "My name is Maria; << endl
```

What, if anything, is wrong with the following program?

```
#include <iosteam main(){ cout << "Is there something
wrong " << endl << endl cout << "with this program"?; } 
```

thank you and god bless

---

### Post by LKjell on 2010-02-07
We are not suppose to do your home work. So put that in a compiler and read the error message.

---

### Post by luposolo on 2010-02-07
i just need help with this now
```
#include <iosteam main(){ cout << "Is there something
wrong " << endl << endl cout << "with this program"?; }
```

---

### Post by LKjell on 2010-02-07
```
#include <iosteam 
main(){ 
cout << "Is there something wrong " << endl << endl 
cout << "with this program"?; }
```

Same as your code. compile that should make it easier to debug.

---

### Post by MadCow108 on 2010-02-07
wow you win the prize for most syntax errors in one line :/

its iostream not iosteam
the include is unterminated
main has no return type (it needs to int)
there are various missing semicolons or too many semicolons in the wrong places
and finally the actual return is missing from the main function.

---

### Post by lisati on 2010-02-07
> **luposolo said:**
> 
```
cout >> "My name is Maria; << endl
```

Huh? Channelling stuff FROM cout to a string literal? :confused:

---

### Post by Ravenshade on 2010-02-07
Since I'm learning C++ let me have a shot at doing your homework. If you don't want to benefit from it, I want to ^_^

#include **<iostream>**

**int** main()
{ 
cout << "Is there something wrong " << endl << endl;
cout << "with this program?"; 
}


I personally don't use endl, can't see the purpose when \n does the same job really. (Someone tell me I'm wrong)

---

### Post by LKjell on 2010-02-07
Most logic sense is that endl is map to \r\n on windows.

---

### Post by MadCow108 on 2010-02-07
> **Ravenshade said:**
> 
I personally don't use endl, can't see the purpose when \n does the same job really. (Someone tell me I'm wrong)

\n is plattform dependent
also endl serves another purpose, it flushes the stream.
if you need neither "benefits" \n is fine.

---

### Post by Ravenshade on 2010-02-07
but \n works on both windows and linux. Does it not work on mac? 

(At least I used to code in java with \n on windows vista and windows 7)

---

### Post by LKjell on 2010-02-07
> **Ravenshade said:**
> but \n works on both windows and linux. Does it not work on mac? 

(At least I used to code in java with \n on windows vista and windows 7)

Java is special... Actually you should use %n in java.

---

### Post by Ravenshade on 2010-02-07
Odd my lecturer always taught us using \n... No matter, as long as you only mean platform in terms of language. 

I'm trying to stick to C++ since most people say it's the language that will teach you pretty much the basics and make it easier to crack other languages open like a walnut ^_^

---

### Post by wmcbrine on 2010-02-07
'\n' is universal, IF the thing you're writing to was opened in text mode.

As far as I can tell, the difference between '\n' and endl is that endl flushes the output buffer.

---

### Post by Ravenshade on 2010-02-07
That's logical. Though just so I understand you a little better. 

Is that opening in a text editor, or expecting text output? Since I saw it being used in RPGXP as well. (More than likely part of ruby scripting)

---

