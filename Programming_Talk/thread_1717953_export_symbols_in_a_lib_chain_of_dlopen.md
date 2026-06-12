---
title: "export symbols in a lib chain of dlopen"
date: 2011-03-30
forum: Programming Talk
---

### Post by lqbweb on 2011-03-30
If I create a parent executable which loads a single library through dlopen, if I have compiled the main executable with -rdynamic, then I can use its simbols in the library with the clasule "extern". This is not a problem and it's working, but....

If I have an already made executable (which is out of my control) which loads my library1, and my library1 loads another library2 (also mine), then, even if I link library1 with -rdynamic, library2 cant see symbols from library1...

In a word, rdynamic sems to be working within executables but not within shared libraries....

How can I make it and why its not working?

Thanks

---

### Post by MadCow108 on 2011-03-30
rdynamic should not be required for shared libraries, it is only for linking executables where the executable provides a symbol needed by the library.

library symbols are all exported by default unless you set the visibility attribute/command line argument to hidden.

maybe you accidentally defined the symbol in the executable via a header? then rdynamic would be required
can you provide an example set of files reproducing your problem?

---

### Post by lqbweb on 2011-03-30
> **MadCow108 said:**
> rdynamic should not be required for shared libraries, it is only for linking executables where the executable provides a symbol needed by the library.

library symbols are all exported by default unless you set the visibility attribute/command line argument to hidden.

maybe you accidentally defined the symbol in the executable via a header, then rdynamic would be required?
can you provide an example set of files reproducing your problem?

the problem is that i dont know how the executable open my library1 because it's closed code... mmm but my library1 open my library2 with dlopen("name.so", RTLD_NOW), and then, library2 cannot see any symbol declared in library1....

but your words make me think that maybe if I open the library2 from library1 with dlopen("name.so", RTLD_GLOBAL) maybe works?

I can provide code but it's at work... tomorrow

thanks

---

### Post by MadCow108 on 2011-03-30
maybe I did also not understand the situation correct
attached my interpretation which works

edit, no it does not, see below

---

### Post by lqbweb on 2011-03-30
uhhmmmm interesting..... very much....

let me have something to eat and i post in a while some results :)

thanks

---

### Post by MadCow108 on 2011-03-30
now I understand.
executable opens library1 with dlopen(RTLD_LOCAL), this means the symbols of this library will not be visible to subsequently loaded libraries like library2.
You have to use RTLD_GLOBAL for that but as you can't control that you could open library1 itself from library1 with RTLD_GLOBAL to load the symbols.

```

//library1.c

// load symbols
dlopen("library1.so", RTLD_LAZY | RTLD_NOLOAD | RTLD_GLOBAL);
// load library which needs them
void * handle = dlopen("library2.so", RTLD_LAZY);

```

---

### Post by lqbweb on 2011-03-30
yep, that's the key! i'll try it tomorrow, i dont have here the development tools for it (it's an embedded) :) ill post results :)

thanks very much, you point me in the right way :)

---

