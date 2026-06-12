---
title: "A different Python Question"
date: 2009-01-17
forum: Programming Talk
---

### Post by abeisgreat on 2009-01-17
This is an odd question, and I kinda doubt that it is possible,but I need to copy the contents of a text field from **another** program, that I don't have the source code for. 

What I mean is, that the other application reads inputs from a very specific parallel cable, and I need to grab the text that the other application is printing out in itself..

As I type this it sounds so impossible haha.

Hopefully you understand what I mean.

---

### Post by TreeFinger on 2009-01-17
vzsdga

---

### Post by abeisgreat on 2009-01-17
I can't thats the thing. Its quite complex to read the data from the cable

---

### Post by ssam on 2009-01-18
you could try dogtail [http://people.redhat.com/zcerza/dogtail/](http://people.redhat.com/zcerza/dogtail/)

its meant for testing gui programs. i think you do things along the lines of.
*launch program
*press this button then that button
*read the text from this field

but i think it might need for the program to be accessible.

---

### Post by spupy on 2009-01-18
Can you call the other program with os.system() and redirect its output to file, which you read afterwards?
Or you need the output immediately as it is printed from the other program.

---

### Post by abeisgreat on 2009-01-27
> **spupy said:**
> Can you call the other program with os.system() and redirect its output to file, which you read afterwards?
Or you need the output immediately as it is printed from the other program.

I guess thats possible, but the thing is, it doesnt print anything in the terminal, its all in a text windows in the app, its pretty much a straight port from a windows app so it doesnt have any stuff like that

---

