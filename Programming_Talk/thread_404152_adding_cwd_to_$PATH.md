---
title: "adding cwd to $PATH"
date: 2007-04-08
forum: Programming Talk
---

### Post by wtruong on 2007-04-08
How do i add ./ to $PATH permanently in bash??

---

### Post by heimo on 2007-04-08
It's a security risk, you probably shouldn't add it. At least for me it hasn't been a big trouble to prefix commands with "./" 
[http://www.arsc.edu/support/policy/dotinpath.html](http://www.arsc.edu/support/policy/dotinpath.html)
[http://www.math.psu.edu/guide/node30.html](http://www.math.psu.edu/guide/node30.html)

---

### Post by jordanmthomas on 2007-04-08
If you *do* want to, here's what you need to do for a bash prompt.  I only quickly glanced at heimo's links, but they seemed to be mostly talking about korn shell and csh.

```
echo "export PATH=$PATH:." >> ~/.bashrc
```
Then, next time you log in . will be in your path.

I only told you this because you asked, but I agree with heimo that you really shouldn't put . in your path.
Good luck to you whichever way you decide to go here.

---

### Post by wtruong on 2007-04-08
hmm true enough that it is a security risk, i'll just stick with using ./a.out 

thanks

---

### Post by rplantz on 2007-04-08
Another way to do this is to create a personal bin directory in your home directory. Then place ```

/home/*your_user_name*/bin

```
in your PATH. Then place all your own executables in your personal bin directory.

---

