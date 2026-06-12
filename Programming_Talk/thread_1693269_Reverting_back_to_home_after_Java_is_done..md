---
title: "Reverting back to home after Java is done."
date: 2011-02-22
forum: Programming Talk
---

### Post by Hosmion on 2011-02-22
Hello everyone.  I am deciding I should go into Java programming.  Well, I don't like having to open and close the terminal all the time so I can start on my next program.  Is there a way to go backward in the path?

For example:

Suppose I was in:
lenni@ubuntu:~/Desktop/Java/Scripts/IncrementOperators$

How would I get back to:
lenni@ubuntu:~/Desktop/Java/Scripts/

?

Thanks ^_^

---

### Post by myrtle1908 on 2011-02-22
Do you mean to go back one directory in the shell?  If so ...

```
cd ..
```

---

### Post by Hosmion on 2011-02-23
That worked, thanks so much!

---

### Post by Portmanteaufu on 2011-02-24
Other useful directory navigation tricks:

Return to your home directory
```
cd
```

Return to the previous directory (not necessarily the parent directory)
```
cd -
```
(Note: this only works one time. For something that remembers more than one directory, see below.)

Switch directories, but add the current directory to a list of visited directories:
```
pushd /directory/to/enter
```

Go backwards in the list of visited directories:
```
popd
```

Enjoy! :D

---

