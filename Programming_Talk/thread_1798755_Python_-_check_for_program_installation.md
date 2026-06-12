---
title: "Python - check for program installation"
date: 2011-07-06
forum: Programming Talk
---

### Post by KoolPenguin on 2011-07-06
I need an effective way to check for program installations from within Python.  I'm currently using the apt.cache class and it works fine for programs install (returns True) however, if the program does not exist it will return an error and not continue with the function.

```

cache = apt.Cache()
cache.open()
result = cache['program'].is_installed

```

Is my coding not correct or is there another way to do this?

Thanks
--
Chris

---

### Post by cgroza on 2011-07-06
You could catch the error and then handle it. The error message would be useful too.

---

### Post by DangerOnTheRanger on 2011-07-06
Your code should be restructured like this:

```

cache = apt.Cache()
cache.open()

try:
    program_installed = cache['program'].is_installed
except KeyError:
    # The APT cache doesn't include a package named "program", so handle that here

```Going slightly off topic: cgroza, you just broke the 1,337 bean mark! :D

---

### Post by cgroza on 2011-07-06
> going slightly off topic: Cgroza, you just broke the 1,337 bean mark! :d1337! :p

---

### Post by TwoEars on 2011-07-06
Now, I don't know much about the apt module, but a better way of doing would be to test if the prorgam is in the cache, not use error trapping, but error prevention ;)

```

import apt
cache = apt.Cache()
cache.open()
program = raw_input('What is the name of the program?')
if program in cache:
    if cache[program].is_installed:
        print 'The program is installed!'
    else:
        print 'The program is not installed!'
else:
    print 'Are you sure that's what you mean? Well, it doesn\'t exist!'


```

---

### Post by cgroza on 2011-07-06
> **TwoEars said:**
> Now, I don't know much about the apt module, but a better way of doing would be to test if the prorgam is in the cache, not use error trapping, but error prevention ;)

```

import apt
cache = apt.Cache()
cache.open()
program = raw_input('What is the name of the program?')
if program in cache:
    if cache[program].is_installed:
        print 'The program is installed!'
    else:
        print 'The program is not installed!'
else:
    print 'Are you sure that's what you mean? Well, it doesn\'t exist!'


```
Nice approach.

---

### Post by nvteighen on 2011-07-07
Don't worry, using the apt module is the best way. Always prefer modules or libraries to calling popen or a system command, as APIs allow you much more access than using I/O to communicate with another process.

There are different approaches. You can use an "error catching" or an "error preventing" style and the results are the same, in this case.

---

### Post by slavik on 2011-07-07
what about running `which $command` to know if it's available?

edit: better yet, make a package and depend it on whatever other packages it needs to depend on.

---

### Post by TwoEars on 2011-07-07
> **slavik said:**
> what about running `which $command` to know if it's available?

edit: better yet, make a package and depend it on whatever other packages it needs to depend on.

Well, first idea -
1) Because he's asking about Python, not Bash
2) Using an API/Python module is always better than running commands on the system 
3) There are much better ways to tell if a program is installed than using which. which will only return if the program is in the bin directories. What about things that don't live there, like libraries? They need to be checked too.

Second idea - 
4) If creating an application to act as an interface to apt, then there should be dynamic package management, not static.

---

### Post by cgroza on 2011-07-07
> **TwoEars said:**
> 
Second idea - 
4) If creating an application to act as an interface to apt, then there should be dynamic package management, not static.
Well, the OP did not give too much information about that.

---

### Post by TwoEars on 2011-07-07
> **cgroza said:**
> Well, the OP did not give too much information about that.

That's true, but the best programmers are those who make their code as reusable as possible ;)

---

### Post by juancarlospaco on 2011-07-07
I also use:

```

try:
    import psyco  # Speed Up if avaliable
    psyco.full()
except ImportError:
    print(" No PYTHON-PSYCO avaliable... ") 
    print(" Try: sudo apt-get install python-psyco ") 
    pass

```

On the example i use Psyco but other cn be used...

---

### Post by TwoEars on 2011-07-07
> **juancarlospaco said:**
> I also use:

```

try:
    import psyco  # Speed Up if avaliable
    psyco.full()
except ImportError:
    print(" No PYTHON-PSYCO avaliable... ") 
    print(" Try: sudo apt-get install python-psyco ") 
    pass

```

On the example i use Psyco but other cn be used...

As a note, there's no need for the pass statement ;)

---

### Post by juancarlospaco on 2011-07-07
True

---

