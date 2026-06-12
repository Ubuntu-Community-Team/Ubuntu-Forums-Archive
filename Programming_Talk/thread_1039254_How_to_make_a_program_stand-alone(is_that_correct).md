---
title: "How to make a program stand-alone(is that correct?)"
date: 2009-01-14
forum: Programming Talk
---

### Post by myromance123 on 2009-01-14
I wrote stand-alone cos Im not sure what the term is for a program that can run without using the command prompt or terminal as in it can run just by double clicking it and functioning on its own (not running in the terminal) and the sorts

Okeh, sorry if this is REALLY newb of me but I have searched the net for hours and read the stickies before posting so I wouldnt be violating any rules (I hope this isnt violating any.).

 I was hoping if anyone could direct me to a guide on making programs that run as stated above or help give me some guidelines or a walk through on how to do so. I read the making a basic .deb package but thats kinda far ahead for me (I think) (is it closely related to what Im talking about? or is it the absolute solution??).

  Im in the midst of learning C and the books I have read (nor the countless guides on learning programming on the net that I have read.. >.< ) dont seem to say how to make a program that runs on its own without having to type in a terminal or command prompt and having the program run in there.


 Hope Im understandable, and I hail all you kind sirs who try to help me :)

---

### Post by DFord425 on 2009-01-14
You said your learning C. Have you gottan to the point where you can compile a C program? Its usually a gcc or a cc command that you use to compile. If you have gottan that far, what is the file extension of the file that the is produced after compiling. It should be a .exe file which should be able to run without having to type in a command from a command promt.

---

### Post by myromance123 on 2009-01-14
Yeah I have compiled some of the programs I have written(really simple stuff).

 Yeah its icon changes but thats it... I have to run it in the terminal using the "./programname" command. I tried running the programs I compiled just by double clicking and such but nothing happens.

  Im using Ubuntu 8.04 desktop. If the program did run just by double clicking, would it still end up running in the terminal again?

Thanks for the swift reply :)

---

### Post by DFord425 on 2009-01-14
No problem with the reply, im bored at work hoping someone will reply to my post further down. 

Anyway, if you double click on it, yes it will still run in a terminal, unless you specify otherwise in the code, and it sounds like you havent gottan that far yet.

As for nothing happening when you click it, i havent done much programming in C for a while, but when i was in school and using windows, it worked. It might be that Ubunut doesnt let the program run like that. The only C programming i did in Ubunutu was for a class where we had to run it in a terminal bc we were making programs that ran like terminal commands(ls cp find...) So if something else has to be done, i dont know what it is. sorry i could not be of more help.

---

### Post by eye208 on 2009-01-14
Unlike Windows, Linux does not really distinguish between console and GUI programs. Any GUI program can (and usually does) use the console for debug messages, but of course, if you start the program by double-clicking its icon, no console window will be assigned, so all the output will be discarded.

If you want to write GUI programs, there are lots of options. You have to decide which GUI toolkit you want to use. The two most popular ones are GTK+ and Qt. Another well-known one is wxWidgets.

---

### Post by Zugzwang on 2009-01-14
> **DFord425 said:**
> You said your learning C. Have you gottan to the point where you can compile a C program? Its usually a gcc or a cc command that you use to compile. If you have gottan that far, what is the file extension of the file that the is produced after compiling. It should be a .exe file which should be able to run without having to type in a command from a command promt.

This is incorrect. DOS and Windows uses .exe extensions. For Linux, it doesn't matter.

> **myromance123 said:**
> Yeah its icon changes but thats it... I have to run it in the terminal using the "./programname" command. I tried running the programs I compiled just by double clicking and such but nothing happens.

Im using Ubuntu 8.04 desktop. If the program did run just by double clicking, would it still end up running in the terminal again?


Double-clicking is the correct procedure. However, if your program only outputs to the console, you won't see anything because that is hidden if you start it that way. 

You can circumvent this problem by either writing a GUI program (best alternative) or hack some circumvention like:

[PHP]
#include <stdio.h>

int main(int argv, char **args) {
  if (argv==1) {
    system("xterm -e ./myapp myparam");
  } else if (argv>1) {
    // Test for your param and do the rest
    printf("Hello Ubuntu!\n");
    getchar();
  }
}
[/PHP]

---

### Post by myromance123 on 2009-01-14
Thanks for the help DFord425 :)

eye208, I did not know that Qt and GTK+ were used for those purposes :D
 Im gonna give those a go right now hehe (but does it comply with C? or are those toolkits language specific?)
  Thank you :)

Zugzwang, thank you, I see now that nothing appears when I double click them is because they are hidden. Something new to me.

  Im sorry I dont really understand your program you have written very well because my level of C is still quite basic but I believe I understand what you're getting at :)
  

  Thank you guys so much for the help, Im not stranded in the dark anymore

Rock on :P  :guitar::lolflag:

---

### Post by mali2297 on 2009-01-14
> **myromance123 said:**
> (but does it comply with C? or are those toolkits language specific?)


GTK+ is a library for C (although there are bindings to other languages as well). See the official web site [http://www.gtk.org/](http://www.gtk.org/) for more information. There you will also find links to a couple of tutorials.

---

### Post by myromance123 on 2009-01-14
Thanks mate :)

  Im on the site now, having a little bit of a hard time trying to install it... It requires packages,gmake and the such which I'am not familiar with :P

Qt4 was in the repos so that was easy hehe but its popular for KDE, I believe Im a gnome user so thats why Im trying to use GTK+ (hope thats the right decision.)

---

### Post by myromance123 on 2009-01-14
Ahh I was getting so caught up in understanding whats the diff between programs that run in terminals and programs that run on their own that I forgot to check what is the TERM/name used to name a program that runs on its own?

  Is it called GUI program(s)? Or is there a widely used term/name?
If there are several names/terms, please by all means list them all ~

Thanks and hopefully last question from me on this topic :P

---

### Post by slavik on 2009-01-14
gui program is good enough ... don't think anyone bothered to come up with anything else. :)

---

### Post by myromance123 on 2009-01-14
Wooo :)

 Thanks mate, hopefully Im packed with the knowledge to make GUI programs now hehehe

  Thank You Ubuntu Community !

:guitar:

---

### Post by mali2297 on 2009-01-15
> **myromance123 said:**
> Thanks mate :)

  Im on the site now, having a little bit of a hard time trying to install it... It requires packages,gmake and the such which I'am not familiar with :P

Qt4 was in the repos so that was easy hehe but its popular for KDE, I believe Im a gnome user so thats why Im trying to use GTK+ (hope thats the right decision.)

GTK+ is also in the repos. Just install the package **libgtk2.0-dev**.

---

### Post by myromance123 on 2009-01-15
Cool, I got it easily thanks to you :)
 Those binary and source packages on the site are confusing :P

Btw, how is GTK+ used?
  I have been searching for guides but most of them are on about using other libraries and such with GTK+ and not how to actually use it.

Any places I can learn how to use it effectively? I wanna be outta you guys way asap >.<

I found this site:
 [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

*Just thought I would put up a link for a site with a guide that actually teaches how to use GTK+ but you gotta have Glade too it seems

---

### Post by mali2297 on 2009-01-15
> **myromance123 said:**
> Cool, I got it easily thanks to you :)
 Those binary and source packages on the site are confusing :P

Btw, how is GTK+ used?
  I have been searching for guides but most of them are on about using other libraries and such with GTK+ and not how to actually use it.

Any places I can learn how to use it effectively? I wanna be outta you guys way asap >.<


The official site links to at least two tutorials:
[http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)
[http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)

If you have just started to learn programming and you are not necessarily committed to C, then you might consider trying another language that lets you get started more easily. Many here seem to recommend Python for beginners.

---

### Post by crazyfuturamanoob on 2009-01-15
Actually "stand-alone" means a program which doesn't need any installation processes or dependencies.

Not a program which can be ran with a mouseclick.

---

### Post by myromance123 on 2009-01-16
Mali2297, thanks that was exactly what I was looking for. I didn't think to use the tutorial word in the googling I did :P
(I want to be a dedicated C programmer hehe, I'll probably learn C derived languages after I have become accustomed to C well enough)

Crazyfuturamanoob, wow I didn't know that was what the term meant :)
  
  Jolly good fellows :)
Thanks for all the help  :popcorn:

---

