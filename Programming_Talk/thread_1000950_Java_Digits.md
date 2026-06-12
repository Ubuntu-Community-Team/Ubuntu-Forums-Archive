---
title: "Java Digits"
date: 2008-12-03
forum: Programming Talk
---

### Post by tashe on 2008-12-03
Hi everybody.
Is there a way to make in Java digits to look like digits from old calculators, like this:
[http://technabob.com/blog/wp-content/uploads/2007/03/single_digit_clock.jpg](http://technabob.com/blog/wp-content/uploads/2007/03/single_digit_clock.jpg)

and to be able to turn on and off some of the lines in the digit so I can make arrangements of them different than the arrangements of the existing decade numbers.
Thank you
Greetings

---

### Post by tinny on 2008-12-03
> **tashe said:**
> Hi everybody.
Is there a way to make in Java digits to look like digits from old calculators, like this:
[http://technabob.com/blog/wp-content/uploads/2007/03/single_digit_clock.jpg](http://technabob.com/blog/wp-content/uploads/2007/03/single_digit_clock.jpg)

and to be able to turn on and off some of the lines in the digit so I can make arrangements of them different than the arrangements of the existing decade numbers.
Thank you
Greetings

This is called a seven segment display. Have a search around with google for "Java 7 segment display". Here is the first useful link I found.

[http://au.answers.yahoo.com/question/index?qid=20080221085453AAdOisx](http://au.answers.yahoo.com/question/index?qid=20080221085453AAdOisx)

---

### Post by tashe on 2008-12-04
Thanks for the reply.
I tried it,but somehow I don't feel that it will work for me. My goal is to make a representation of the 0's and 1's in a digital signal. I think a line like the one below will be better, but I just don't know how to draw one. I know I can make it from more lines, but that makes the job ugly and more complex.
Is there any way I can draw this picture with one line?

---

### Post by Tomosaur on 2008-12-04
It really depends on the application you're creating - is it GUI, command line, or what? Java has drawing toolkits which should do what you want.

Alternatively you could do some clever string printing to the command line, which would be more complicated but **way** cooler.

---

### Post by tashe on 2008-12-07
It should be a GUI.
thanks for the replies

---

### Post by jimi_hendrix on 2008-12-07
i know theres a graphics object that can draw lines and stuff on your gui

---

### Post by tinny on 2008-12-08
[http://leepoint.net/notes-java/GUI-lowlevel/graphics/40drawingpanel/10drawingpanel.html](http://leepoint.net/notes-java/GUI-lowlevel/graphics/40drawingpanel/10drawingpanel.html)

The Graphics class contains various methods for painting.

[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

The above info should get you started.

---

### Post by rbprogrammer on 2008-12-08
> **tinny said:**
> [http://leepoint.net/notes-java/GUI-lowlevel/graphics/40drawingpanel/10drawingpanel.html](http://leepoint.net/notes-java/GUI-lowlevel/graphics/40drawingpanel/10drawingpanel.html)

The Graphics class contains various methods for painting.

[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

The above info should get you started.

As noted in tinny's post, he suggested "painting".  In which case the easiest way of doing this would be to find a font file online from somewhere and somehow incorporate it into your project.

---

### Post by tashe on 2008-12-13
I'm almost at the end of the project. I did it with extending JFrame and using the g.drawline() method. At the end it turned out that it's easy.
Thanks for the suggestions to everyone
):P

---

