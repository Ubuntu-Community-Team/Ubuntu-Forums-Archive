---
title: "Help Finding the Right Software"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by jorpoveda on 2012-01-16
Hello, I was hoping I can get some help. I am looking some point outs  for the software I need. I am a computer science and electrical engineer  student. I am looking for an IDE to work on C/C++, Java, Perl,  HTML/CSS, MATLAB and Assembly. MySQL and Oracle as data bases and a good  software for CAD designing for electrical circuitry design.

I thank you for your help since I am new to Linux I do not know where to  start. I have received suggestions on Eclipse and NetBeans, but no  suggestions on the other.

---

### Post by lechien73 on 2012-01-16
I'd second Eclipse...it's the IDE I use for Java and C++. I haven't done any assembly in a few years, so the last development environment I used was vi text editor!! ;-)

For circuit design, try *eagle* or *xcircuit*. Both are available in the repositories.

For general purpose CAD, you could try QCAD - also available in the repositories. You could create your electrical symbols and then use them in this, if you wish.

---

### Post by Mark Phelps on 2012-01-16
I would first check with your Faculty and see what they recommend in terms of platforms and OSs. 

If they don't have any, or don't care, then you can use whatever works best for you.

Assembly is going to be tough -- as that is platform-dependent and is often done using Emulators.  So, whichever course is going to use Assembly language, I would check with the instructors to find out what they recommend.  You would hate to find out they require you to use an Emulator that only runs in MS Windows.

---

### Post by cortman on 2012-01-16
I'd second Matt's recommendation of Eclipse. With that and emacs you can pretty easily do any coding you want.
CAD would be tougher. Unfortunately Autodesk hasn't released any Linux versions of their products. If all you're doing is circuit design a basic program like QCAD would probably work for you. I've tried running ACAD Mech, LT, etc through Wine. It doesn't work.

---

### Post by jorpoveda on 2012-01-16
Good suggestions. I have started using Eagled and QCAD, and as IDEs I am using NetBean (suggested on my school) and Eclipse. I have some experience with Nano and Vi but none on Emacs. Can you please suggest any good books or online tutorials/lessons.

---

### Post by lechien73 on 2012-01-16
Probably the best place to look is: [http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/)

There's a "tour" link on the right side of the page, and the manuals are available for download :)

---

### Post by jorpoveda on 2012-01-16
> **lechien73 said:**
> Probably the best place to look is: [http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/)

There's a "tour" link on the right side of the page, and the manuals are available for download :)

Thanks a lot for this info. Now I can start learning how to use Emacs.

---

### Post by cortman on 2012-01-17
> **jorpoveda said:**
> Thanks a lot for this info. Now I can start learning how to use Emacs.

Emacs has a bit of a learning curve, but once you start grasping how the editor itself works, the shortcuts, the windows and buffers, and totally nifty features like Dired, you won't want to go back to any other text editor. I use emacs for everything from writing essays, bash scripts, letters, java, python, etc. Emacs is AWESOME.
When you install it, be sure to install

```
sudo apt-get install emacs23-nox
```

for the pure terminal version, instead of the funky xwindows version. You can run the graphical version in the terminal with emacs -nw, but with the nox version you can just run "emacs".

---

### Post by jorpoveda on 2012-01-17
> **cortman said:**
> Emacs has a bit of a learning curve, but once you start grasping how the editor itself works, the shortcuts, the windows and buffers, and totally nifty features like Dired, you won't want to go back to any other text editor. I use emacs for everything from writing essays, bash scripts, letters, java, python, etc. Emacs is AWESOME.
When you install it, be sure to install

```
sudo apt-get install emacs23-nox
```

for the pure terminal version, instead of the funky xwindows version. You can run the graphical version in the terminal with emacs -nw, but with the nox version you can just run "emacs".

Good tip! I was working on the xwindows version, now I know how to change that. Thanks.

---

### Post by lechien73 on 2012-01-17
Thank you, too, cortman :-D I'd never investigated emacs until this thread and I'm quickly getting hooked!! Is that some kind of wild heresy for a vi user? ;-)

---

### Post by cortman on 2012-01-18
> **lechien73 said:**
> Thank you, too, cortman :-D I'd never investigated emacs until this thread and I'm quickly getting hooked!! Is that some kind of wild heresy for a vi user? ;-)

Your welcome! I learned a little Vi when I was starting out, but the whole modal thing threw me off a little. I'm definitely in love with emacs.
Next to [Richard Stallman's own emacs manual]("http://www.gnu.org/software/emacs/manual/emacs.pdf") the single most handy resource for learning emacs fast is the [emacs reference card]("http://refcards.com/docs/gildeas/gnu-emacs/emacs-refcard-a4.pdf").

Stay away from Vi solidarity meetings for a while- I hear they can smell the emacs on your fingers. :)

---

