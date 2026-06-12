---
title: "Changing a line in a text file with bash..?"
date: 2006-07-11
forum: Programming Talk
---

### Post by Eric_T on 2006-07-11
Hello

I have a fortran program that reads an input file and then does a bunch of computations based on that file. What I want to do is to write a script to change some of the variables, say run the program 10 times and each time increment the variable input_velocity in file input.txt by 10. I know how to make all the parts except how to change that one line. I know several ways of finding it, like grep input_velocity input.txt and awk '/input_velocity/' input.txt, but that doesn't help me much.. ](*,) 
Could anyone give me some tips?

Thanks!

---

### Post by Eric_T on 2006-07-11
Heh, figured out one way to do it...
```
perl -pi -e 's/input_velocity = ".*"/input_velocity = "somethingelse"/' input.txt
```

But if anyone have another way to do it, it would be great to hear from you!

---

### Post by 23meg on 2006-07-11
You can also use **ed** and **sed**.

---

### Post by Eric_T on 2006-07-11
> **23meg said:**
> You can also use **ed** and **sed**.

Yep, like this:
```
sed -i 's/input_velocity = .*/input_velocity = 200/' input.txt
```

---

### Post by schkovich on 2009-09-12
In case you need to assign to input_velocity value from variable then you might do:
```

speed=314
replacement=s/input_velocity = .*/input_velocity = ${speed}/
sed -i $replacement input.txt

```

---

### Post by frenchn00b on 2009-09-12
awk does also the job:

[http://www.sunsite.ualberta.ca/Documentation/Gnu/gawk-3.1.0/html_chapter/gawk.html](http://www.sunsite.ualberta.ca/Documentation/Gnu/gawk-3.1.0/html_chapter/gawk.html)

---

