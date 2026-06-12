---
title: "C++ system return value problem"
date: 2011-05-05
forum: Programming Talk
---

### Post by hakermania on 2011-05-05
I want to easily calculate the number of lines of the files that exist in a particular directory, so, inside my c++ code i've typed:
```

double b=system("a=0; if [ X\"$(ls ~/.config/MyProgram/*)\" != X\"\" ]; then for i in ~/.config/MyProgram/*/*; do a=$(expr $a + $(wc -l < \"$i\")); done; exit $a; else exit 0; fi");

```Explanation: This checks to see if there are files in a particular directory, if there are, then they read the number of lines of each file and add this number to a variable called 'a'. Then the scripts exits by calling 'exit $a' and this value goes to 'double b'
By doing this, i noticed that 'double b' has the value of $a * 256, so I used it as:
```
b/=256
```and then I used the variable 'double b' for my own purposes....
But now, that 'a' is a bit larger as a number (a==1936) and now I can see that 'b' is '36864' (which means 144*256). I assume that in a script you cannot exit with a number larger of a specific value or something else is wrong....

This is quite weird and I suspect that my first thought/notice is completely wrong and it is not a fact, but a possibility!

So, is there any way to use the variable $a? i.e. output the $a variable by calling 'echo $a' and catch it inside the c++ program or maybe use again 'exit $a' in a more effective way?

Thx in advance for any answers and please notice that 'a' can take a value up to 100.000

---

### Post by MadCow108 on 2011-05-05
exit codes are limited to 8 bits (=255) on posix systems.

why not call wc directly  (e.g. with popen) instead of this weird script
or let the script echo the result and parse that.
or do it fully within c++.

---

### Post by hakermania on 2011-05-05
Well ;) I did it with popen finally... For anyone following:
```

FILE* pipe = popen("full command goes here that outputs something", "r");
    char buffer[128];
    string result = "";
    while(!feof(pipe)) {
        if(fgets(buffer, 128, pipe) != NULL)
            result += buffer;
        }
    pclose(pipe);

```
this will result the 'result' variable to have the output of the command!

---

