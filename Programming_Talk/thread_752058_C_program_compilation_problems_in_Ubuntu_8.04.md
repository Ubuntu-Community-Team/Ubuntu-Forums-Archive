---
title: "C_program compilation problems in Ubuntu 8.04"
date: 2008-04-11
forum: Programming Talk
---

### Post by parijathakumar on 2008-04-11
Hai all !
            When I am trying to compile even a basic "hello world"  C-program in Ubuntu 8.04 beta, it says it could not find any file named "stdio.h". I have even included the complete path in the #include statement. But it is not working. I can see the stdio.h file in /usr/include directory. But 'gcc' is not compiling my c-programs. Why is it so ? I have found the same problem with 'Linux Mint' also. Please help me.

-Parijatha Kumar

---

### Post by LaRoza on 2008-04-11
> **parijathakumar said:**
> Hai all !
            When I am trying to compile even a basic "hello world"  C-program in Ubuntu 8.04 beta, it says it could not find any file named "stdio.h". I have even included the complete path in the #include statement. But it is not working. I can see the stdio.h file in /usr/include directory. But 'gcc' is not compiling my c-programs. Why is it so ? I have found the same problem with 'Linux Mint' also. Please help me.

-Parijatha Kumar

Did you run:

Is the code written like this:

```

#include <stdio.h>

```

Note, no spaces or quotes.

Did you install build-essential?

---

### Post by parijathakumar on 2008-04-11
Thanks for the immediate reply. I have written exactly as you have written. No spaces and no quotes.
 I don't know about 'build-essential'. I am a novice programmer. I have just installed the default OS that is bundled in the CD.

--Parijatha Kumar


> **LaRoza said:**
> Did you run:

Is the code written like this:

```

#include <stdio.h>

```

Note, no spaces or quotes.

Did you install build-essential?

---

### Post by LaRoza on 2008-04-11
Ah, run:

```

sudo aptitude install build-essential

```

This is a common question when starting with C or C++ in Ubuntu, so common, it has two fine links in the sticky ;)

---

### Post by parijathakumar on 2008-04-11
Thank you.
Will it ask for any internet connection ?  I don't have one at that PC.


> **LaRoza said:**
> Ah, run:

```

sudo aptitude install build-essential

```

This is a common question when starting with C or C++ in Ubuntu, so common, it has two fine links in the sticky ;)

---

### Post by parijathakumar on 2008-04-11
I have searched the forum. I think I need to download the package from internet. Please suggest me any other alternative since I don't have internet connection to that PC.


> **parijathakumar said:**
> Thank you.
Will it ask for any internet connection ?  I don't have one at that PC.

---

### Post by LaRoza on 2008-04-11
> **parijathakumar said:**
> I have searched the forum. I think I need to download the package from internet. Please suggest me any other alternative since I don't have internet connection to that PC.

It is on the CD, and when you run the command, it asks for the CD.

If it doesn't, make sure the CD is enabled as a repository in System->Administration->Software Sources.

---

