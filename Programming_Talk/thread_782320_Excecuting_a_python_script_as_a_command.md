---
title: "Excecuting a python script as a command"
date: 2008-05-04
forum: Programming Talk
---

### Post by blithen on 2008-05-04
Such as typing ```
music-collecter
``` in the terminal just like a normal program, how do you do that?

---

### Post by LaRoza on 2008-05-04
> **blithen said:**
> Such as typing ```
music-collecter
``` in the terminal just like a normal program, how do you do that?

Mark it as executable and run it.

If it is not in your $PATH, put it there, or add the path to your $PATH. Do not add ~ to your $PATH.

(There is a link in the sticky on scripting languages, which includes marking as executable and shebangs)

---

### Post by blithen on 2008-05-04
I messed up >.>

---

### Post by blithen on 2008-05-04
> **LaRoza said:**
> Mark it as executable and run it.

If it is not in your $PATH, put it there, or add the path to your $PATH. Do not add ~ to your $PATH.

(There is a link in the sticky on scripting languages, which includes marking as executable and shebangs)

```
blithen@sparky:~/python$ sudo cp musiccollect /usr/bin/
[sudo] password for blithen:
blithen@sparky:~/python$ musiccollect
/usr/bin/musiccollect: line 1: syntax error near unexpected token `('
/usr/bin/musiccollect: line 1: `def Walk( root, recurse=0, pattern='*', return_folders=0 ):'

```
I get that error, I have no idea what you are talking about when you say $PATH

---

### Post by Can+~ on 2008-05-04
Now it will be executed directly, similar to doing

```
./musiccolect
```

So, to bash now how to execute it, you must set the first line of your application with

```
#!/usr/bin/env python
```

And by PATH it means, the places that bash usually look for executables, you can see this places doing:

```
echo $PATH
```

So yeah, you put it on /usr/bin, which is a typical place for PATH.

---

### Post by blithen on 2008-05-04
> **Can+~ said:**
> Now it will be executed directly, similar to doing

```
./musiccolect
```

So, to bash now how to execute it, you must set the first line of your application with

```
#!/usr/bin/env python
```

And by PATH it means, the places that bash usually look for executables, you can see this places doing:

```
echo $PATH
```

So yeah, you put it on /usr/bin, which is a typical place for PATH.

Sweet it works, thanks!

---

### Post by LaRoza on 2008-05-04
> **blithen said:**
> Sweet it works, thanks!

Of course, all of that was in the sticky...

---

### Post by mssever on 2008-05-05
One other thing:

/usr/bin is where Ubuntu packages go. It's preferable to not pollute that namespace. Instead put stuff you write or otherwise manually add in /usr/local/bin or ~/bin. /usr/local/bin is part of the default $PATH. I'm not sure about ~/bin; you might have to manually add it.

---

