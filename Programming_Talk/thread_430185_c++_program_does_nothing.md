---
title: "c++ program does nothing"
date: 2007-05-01
forum: Programming Talk
---

### Post by kentpend on 2007-05-01
I was having an issue with getting a compiled program to run, so as a test I made a simple "hello world" type program and compiled using g++.  When I specified an executable name and called it from terminal, nothing happened.  When I did not specify a name, letting it use a.out, when I run it I got this error:

```
bash: a.out: command not found
```

Any ideas as to why this is happening?

---

### Post by Wybiral on 2007-05-01
Try "./a.out" instead of just "a.out"

---

### Post by kentpend on 2007-05-01
Thanks, that worked.

Out of curiosity, why do I have to call it that way?  I didn't have to before I upgraded to Feisty, not do I have to on Red Hat.

---

### Post by Wybiral on 2007-05-01
Without changing the binary path to whatever folder you're in, I'm pretty sure you have to execute them that way. Naturally you don't have to if you move them to "/usr/bin" or somewhere. You get used to it (it's only two extra characters)

---

### Post by Jengu on 2007-05-02
What Wybiral said, but more formally: type this in the prompt:

```

echo $PATH

```

You'll get a colon separated list of directories. Anything in those directories you can call simply by typing at the command line, no ./ necessary, and it doesn't matter what folder you're in when you enter them. On the other hand, if the executable is in a folder not in the current path, you need to be in that folder and use "./". Imagine you created a program and had g++ name it "ls". You probably don't want that to replace the normal ls directory listing program. ;) So you use ./ls for your app, to distinguish it.

---

### Post by siiib on 2007-05-02
having to type ./ is a security 'feature' that means you can execute from the current directory.. normally you can't.. some distro's implement it .. some don't .. strictly speaking your distro should force this.

---

