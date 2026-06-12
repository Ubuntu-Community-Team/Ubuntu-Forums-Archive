---
title: "How to install GCC's &lt;ssl/blowfish.h&gt; library"
date: 2008-06-26
forum: Programming Talk
---

### Post by padawanmuda on 2008-06-26
I have a C script, and it needs <ssl/blowfish.h> library. Unfortunately, it hasn't been installed in my Ubuntu Hardy by default :(
Anybody can help me please..?

---

### Post by LaRoza on 2008-06-26
This might fix it (remember to link!)

```

sudo aptitude install libssl-dev

```

---

### Post by padawanmuda on 2008-06-26
Okay, i've executed the command. Now, according to my Synaptic Package Manager, the installed libssl-dev is 0.9.8g-4ubuntu3. My script still can't run though.. :(
What did you mean by "linking" it?

---

### Post by Zugzwang on 2008-06-26
Look [http://packages.ubuntu.com/search?searchon=contents&keywords=blowfish.h&mode=exactfilename&suite=hardy&arch=any]("http://packages.ubuntu.com/search?searchon=contents&keywords=blowfish.h&mode=exactfilename&suite=hardy&arch=any") here. As you can see, there's no such file names "ssl/blowfish.h" in any Ubuntu package. Maybe you mean "openssl/blowfish.h"?

BTW: Do you really use C for scripting or are you compiling your program to an executable? How do you run/compile your program?

---

### Post by padawanmuda on 2008-06-27
Oh my God.. You are absolutely right. Sorry, it must be **<openssl/blowfish.h>**. 
I was trying to compile my C script using GCC, but failed due to the need of that blowfish.h header.
Now the header has appeared, but these errors occured:
      [I]undefined reference to `BF_set_key'
      undefined reference to `BF_ecb_encrypt'[/I]
I just don't get it, since the **BF_set_key** and **BF_ecb_encrypt** functions are already defined in blowfish.h :confused:

---

### Post by Zugzwang on 2008-06-27
> **padawanmuda said:**
> I just don't get it, since the **BF_set_key** and **BF_ecb_encrypt** functions are already defined in blowfish.h :confused:

You should seriously read something about the build process. The blowfish.h just contains the *declarations* and not the *definitions* of the functions. This is why the linker complains about undefined references. You need to link to the library (as Laroza already pointed out). So if you compile your program somewhat like this:
```

gcc -o program program.c

```
change it to:
```

gcc -o program -lssl program.c

```

If you use makefiles, IDEs, etc. you need to specify this at some point depending on the method you are using.

---

