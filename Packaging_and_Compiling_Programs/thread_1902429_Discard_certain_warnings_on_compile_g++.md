---
title: "Discard certain warnings on compile g++"
date: 2011-12-30
forum: Packaging and Compiling Programs
---

### Post by gameguy on 2011-12-30
I have been programming in C++, and have been reading from files. Unfortunately, for every read command I give it, it gives me the warning "ignoring return value of 'int fscanf'"...
It has always worked fine, so I would like to discard those particular warnings (ie. not print them out upon compile).
I was wondering if there was a way to change the settings for g++ to ignore that particular warning.

If not, is it possible to pipe it into grep with the -v option (inverse) so I don't display those lines?

---

### Post by MG&amp;TL on 2011-12-30
I imagine you can block that, but:

```
g++ <stuff> | grep -v <error>
```

Isn't fstream a better option?

---

### Post by MadCow108 on 2011-12-31
best way to silence the warning:
fix the warning.
the compiler is very rarely wrong with warnigns nowadays. The return of fscanf should be used for a reason.

silence it in code (not recommended):
```
if (myfunc) {}
```

silence it completely (not recommended)
-Wno-unused-result

---

### Post by gameguy on 2011-12-31
An example of my input:

```

int main() {
    FILE* fin = fopen("aflin.txt", "r");
    FILE* fout = fopen("aflout.txt", "w");
    int n, t, b, s;

    fscanf(fin, "%d", &n);
    fscanf(fin, "%d", &t);
    for (int i = 0; i < t; i++) {
        fscanf(fin, "%d", &s);
        taken[i] = s;
    }
    fclose(fin);
    return 0;
}

```

That will give off a warning. It, however, does work fine. When I went to a programming camp the tutors told us not to pay attention to those warnings.

---

### Post by Bachstelze on 2011-12-31
> **gameguy said:**
> An example of my input:

```

int main() {
    FILE* fin = fopen("aflin.txt", "r");
    FILE* fout = fopen("aflout.txt", "w");
    int n, t, b, s;

    fscanf(fin, "%d", &n);
    fscanf(fin, "%d", &t);
    for (int i = 0; i < t; i++) {
        fscanf(fin, "%d", &s);
        taken[i] = s;
    }
    fclose(fin);
    return 0;
}

```

That will give off a warning. It, however, does work fine. When I went to a programming camp the tutors told us not to pay attention to those warnings.

For one thing, the file fout and the variables n and b are not used. For another, what do you think will happen if the input file is malformed and and there is no number on the second line?

If you want to be a good programmer, never ignore a warning.

*EDIT:* And third thing, this code is C, not C++, so it should be compiled with gcc, not g++.

---

### Post by gameguy on 2011-12-31
That's just a code snippet. Everything there is used later in the program. Also, because I am doing this for informatics, not general programming, they make sure that every input file is valid (and if the second line is 0, there are 0 lines following, so that works fine).

EDIT: why isn't it C++?

---

### Post by Bachstelze on 2011-12-31
> **gameguy said:**
> That's just a code snippet. Everything there is used later in the program. Also, because I am doing this for informatics, not general programming, they make sure that every input file is valid.

"They make sure" is not a valid answer. Remember Murphy's law.

---

### Post by MG&amp;TL on 2011-12-31
If you're using C++, AFAIK:

-use fstream: [http://www.cplusplus.com/doc/tutorial/files/]("http://www.cplusplus.com/doc/tutorial/files/")

-considered good practice to intialise variables.

If you are indeed using C, use gcc, as Bachstelze said.

---

### Post by gameguy on 2011-12-31
This is for a training website. The program is marked by computer, and they run it with various test files, and the computer checks for the validity of test files.

---

### Post by gameguy on 2011-12-31
> **MG&TL said:**
> If you're using C++, AFAIK:

-use fstream: [http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)

-considered good practice to intialise variables.

If you are indeed using C, use gcc, as Bachstelze said.

I'll give fstream a try, see how that goes then.

I initialise variables unless they are used for fscanf. I suppose I probably should anyway.


I am using C++ and G++ - this code is perfectly valid C++ code. The stuff that wouldn't be valid C comes later in the program.

---

### Post by Bachstelze on 2011-12-31
> **gameguy said:**
> This is for a training website. The program is marked by computer, and they run it with various test files, and the computer checks for the validity of test files.

You're not going to do training all your life, are you?

---

### Post by gameguy on 2011-12-31
No, but I can't really be bothered to check the validity of the output file, since I'm not really sure how I would go ahead with it anyway.

---

### Post by Bachstelze on 2011-12-31
"I can't be bothered to..." will not make you a good programmer, either. What you should do looks something like this:

```
int main() {
    FILE* fin = fopen("aflin.txt", "r");
    if (fin == NULL) {
        perror("Could not open input file");
        return 1;
    }
    FILE* fout = fopen("aflout.txt", "w");
    if (fout == NULL) {
        perror("Could not open output file");
        fclose(fin);
        return 1;
    }
    int n, t, b, s;

    if (fscanf(fin, "%d", &n) != 1) {
        goto error;
    }
    if (fscanf(fin, "%d", &t) != 1) {
        goto error;
    }
    for (int i = 0; i < t; i++) {
        if (fscanf(fin, "%d", &s) != 1) {
            goto error;
        }
        taken[i] = s;
    }
    fclose(fin);
    fclose(fout);
    return 0;

error:
    fprintf(stderr, "Error: Invalid file!\n");
    fclose(fin);
    fclose(fout);
    return 1;
}
```

---

### Post by gameguy on 2011-12-31
Right. I didn't realise fscanf returned anything. I assumed it was a void function. Also, with the error for the output txt file, that isn't really nessecary, is it? What that does is it just creates a new file, overwriting any previous file if one exists.

---

### Post by Bachstelze on 2011-12-31
> **gameguy said:**
> Right. I didn't realise fscanf returned anything. I assumed it was a void function.

If it were, you wouldn't get that warning in the first place. ;) Another lesson: never assume anything.

> Also, with the error for the output txt file, that isn't really nessecary, is it? What that does is it just creates a new file, overwriting any previous file if one exists.

Even then, there are a lot of things that could go wrong. What if you don't have write permission to the current folder? What if you have exhausted the number of file descriptors you can open?

In those cases, and other less common, the returned pointer will be NULL, and it will make your program crash when you try to access it. Why take chances?

> 	
If a function be advertised to return an error code in the event of difficulties, thou shalt check for that code, yea, even though the checks triple the size of thy code and produce aches in thy typing fingers, for if thou thinkest ``it cannot happen to me'', the gods shall surely punish thee for thy arrogance.

[http://www.lysator.liu.se/c/ten-commandments.html](http://www.lysator.liu.se/c/ten-commandments.html)

---

### Post by MadCow108 on 2011-12-31
> **gameguy said:**
> 

That will give off a warning. It, however, does work fine. When I went to a programming camp the tutors told us not to pay attention to those warnings.

that camp was not very good then, thats pretty much the worst advice you can give to learners.
probably every second of all beginner C/C++ questions in the programming talk forum would not happen if people would read and understand the compiler warnings.

and not checking return/error codes is one of the more common sources of bugs.

---

### Post by gameguy on 2011-12-31
> **MadCow108 said:**
> that camp was not very good then, thats pretty much the worst advice you can give to learners.
probably every second of all beginner C/C++ questions in the programming talk forum would not happen if people would read and understand the compiler warnings.

and not checking return/error codes is one of the more common sources of bugs.

They were actually great tutors, but they were not focusing on real world programming. We were focusing on solving a particular problem, assuming correct input, so there was no need to check.

---

### Post by gameguy on 2011-12-31
> **Bachstelze said:**
> If it were, you wouldn't get that warning in the first place. ;) Another lesson: never assume anything.



Even then, there are a lot of things that could go wrong. What if you don't have write permission to the current folder? What if you have exhausted the number of file descriptors you can open?

In those cases, and other less common, the returned pointer will be NULL, and it will make your program crash when you try to access it. Why take chances?



[http://www.lysator.liu.se/c/ten-commandments.html](http://www.lysator.liu.se/c/ten-commandments.html)

Suppose so then. I tried your previous thing and it fixed the problem. Thanks

---

