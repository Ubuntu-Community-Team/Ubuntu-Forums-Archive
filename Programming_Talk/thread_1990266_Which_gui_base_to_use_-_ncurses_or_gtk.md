---
title: "Which gui base to use - ncurses or gtk ?"
date: 2012-05-29
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-29
Hello friends,

I am creating a project in c. I want to clarify from you guys that which gui base should I use, NCURSES or GTK.

Since, I am programming in C both of the above needs lot of coding for a project which I am creating. 

Anybody, please suggest me.

---

### Post by dniMretsaM on 2012-05-29
Ncurses isn't a GUI toolkit. GTK will almost certainly be better for your project.

---

### Post by etdsbastar on 2012-05-29
> **dniMretsaM said:**
> Ncurses isn't a GUI toolkit. GTK will almost certainly be better for your project.

Thanks for the reply, I know that NCURSES is a terminal based option.

---

### Post by Barrucadu on 2012-05-29
Well, do you want a terminal program or a GUI program?

---

### Post by etdsbastar on 2012-05-29
> **Barrucadu said:**
> Well, do you want a terminal program or a GUI program?

Ah, that was a nice question Barracuda, Actually, I can drink both type of beers - local and national, I mean to say I can make in ncurses and gtk both, that's where I am confused, actually I want something different to be made regarding my project.

---

### Post by PeterP24 on 2012-05-29
One can probably bring many arguments into discussion. For me it reduces to this: do you do your program for yourself or do you target a much larger audience? If the answer is a larger audience, then you might want to go with gtk. ncurses is ok, but in my opinion is just an enhancement to the terminal interface (I used some time ago and this is all I can say about it - very nice tool though). I would personally chose either gtk, either a gtk + ncurses solution. What I mean is that if your program fails to find the gtk libs on that system it should default to ncurses interface. But it is not really a good proposal, since you can impose upon the user during the installation to grab the gtk related dependences also and thus ensuring that he/she can use the gtk gui.

---

### Post by etdsbastar on 2012-05-29
Thanks for your replies. I will stick with GTK... 

Thanks a lot again.

---

