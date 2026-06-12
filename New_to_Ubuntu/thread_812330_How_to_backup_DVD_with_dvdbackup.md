---
title: "How to backup DVD with dvdbackup?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by O-pos on 2008-05-29
Hello.

I have installed dvdbackup but don't know how to specify the target dvd as an input. when I just type dvdbackup in terminal, it does not work. Any ideas?

---

### Post by kostkon on 2008-05-30
Just give
```
man dvdbackup
```
to see the available options or you can check the man page [here]("http://www.penguin-soft.com/penguin/man/1/dvdbackup.html").

You'll have to specify your DVD drive, in most cases giving */dev/dvd* will work, i.e.:
```
dvdbackup -i /dev/dvd
```

---

### Post by O-pos on 2008-05-30
My dvd is in /media/cdrom0

I tried and neither dvdbackup -i /dev/dvd nor dvdbackup -i /media/cdrom0 works, I get the same output: 

Usage: dvdbackup [OPTION]...
-h, --help         display this help and exit
...etc & etc

---

### Post by kostkon on 2008-05-31
> **O-pos said:**
> My dvd is in /media/cdrom0

I tried and neither dvdbackup -i /dev/dvd nor dvdbackup -i /media/cdrom0 works, I get the same output: 

Usage: dvdbackup [OPTION]...
-h, --help         display this help and exit
...etc & etc
Quoting [from the man page]("http://www.penguin-soft.com/penguin/man/1/dvdbackup.html")
> #   Option notes
      -i is mandatory
      -o is mandatory except if you use -I
      -a is option to the -F switch and has no effect on other options
      -s and -e should preferably be used together with -t 

It's obvious that you get this output because you don't use all the mandatory options. A right call of the application could be something like this
```
dvdbackup -i /dev/dvd -o ~/mydvdbackup
```

---

