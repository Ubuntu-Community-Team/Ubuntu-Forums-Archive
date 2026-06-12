---
title: "[ C++ ] Adding argument value to a stirng results in an error."
date: 2009-09-22
forum: Programming Talk
---

### Post by credobyte on 2009-09-22
Any ideas ?

```
for (int i = 0; i < argc; i++) {
    string pckg = argv[i];
    string cmd = "apt-get install " + pckg;
    system(cmd);
}
``````
g++ "main.cpp" -o "main" (in directory: /home/dainis/Programming)
[COLOR=DarkRed]main.cpp: In function ‘int main(int, char**)’:[/COLOR]
main.cpp:23: error: cannot convert ‘std::string’ to ‘const char*’ for argument ‘1’ to ‘int system(const char*)’
[COLOR=Red]Compilation failed.[/COLOR]
```

---

### Post by dwhitney67 on 2009-09-22
In a nutshell, you want the C-style string:
```

system(cmd.c_str());

```
P.S.  Also, did you not want your loop to begin with the index equal to 1??  Otherwise, argv[0] is the program name.

---

### Post by credobyte on 2009-09-22
> **dwhitney67 said:**
> In a nutshell, you want the C-style string:
```

system(cmd.c_str());

```P.S.  Also, did you not want your loop to begin with the index equal to 1??  Otherwise, argv[0] is the program name.

Yes, sorry .. c_str() was there before I edited it to make it look nicer :D Anyway, even elimination of argv[0] will not solve this problem, right ?

Edit :: Looks like I'm wrong :(

```
for (int i = 1; i < argc; i++) {
    string pckg = argv[i];
    string cmd = "apt-get install " + pckg;
    system(cmd.c_str());
}
```

Works just fine.

---

