---
title: "Getting started on Stanford's Java Course"
date: 2010-05-11
forum: Programming Talk
---

### Post by bradley002 on 2010-05-11
I am taking Stanford's free online [course in introductory programming]("http://see.stanford.edu/see/courseinfo.aspx?coll=824a47e1-135f-4508-a5aa-866adcae1111") (they also have more advanced courses for those interested).

 I am trying to run a java program through eclipse. The program is called StoneMasonKarel, which is a subclass of SuperKarel, a class where a robot moves around and does stuff. My version of eclipse seems to be slightly different than the one they are using, since I could not download their Mac or Windows version on their site. They say to simply click on an icon to run the program. I have to click 'Run As....' and then choose a configuration.

I chose Java Application (out of the choices of Eclipse Application, Equinox OSGi Frame, Java Applet, and JUnit, and SWT Application). It was the only one that seemed to do anything. For the configuration I chose StoneMasonKarel as the main class.

When I run it like this the little robot and his world pop up, but the application automatically freezes. I have tried with a couple really simple subclasses and the same thing happens. Could there be something wrong with my set up? Do you need any more info? 

The library and worlds - the skeleton of the program - is pre-programmed by Stanford. Thanks.

---

### Post by Seal Daemon on 2010-05-11
Can you attach the source code ( preferably tar.gz ) ?

---

### Post by bradley002 on 2010-05-11
Code attached. I thought it might be a problem with my configuration rather than the code because it is basically just the code that Stanford uses for thousands of students. All I did was add a move command to the StoneMasonKarel subclass, which was previously empty. When I run it the application pops up, shown below, but it freezes before I get a chance to actually click on "start program" or anything else. 

[IMG]http://img684.imageshack.us/img684/6443/screenshot1wuj.png[/IMG]

---

### Post by bradley002 on 2010-05-13
Or would it help to try running it in another program? Any ideas? I don't want to take up a lot of anyone's time, but a quick suggestion would help, as I'm at an impasse.

---

### Post by simeon87 on 2010-05-14
According to [http://see.stanford.edu/materials/icspmcs106a/06-karel-in-eclipse.pdf](http://see.stanford.edu/materials/icspmcs106a/06-karel-in-eclipse.pdf), they use two special buttons to run the code of the robots. Given that they have special Eclipse versions, my guess is that they have extendend Eclipse with some functionality which the standard Eclipse doesn't have. By running it as a normal Java application, it's probably not starting the Karel simulator correctly (those extra buttons probably do some extra work under the hood before launching and it would be silly to add more buttons when a normal application launch suffices). If you want to run it, I think you should look into starting the Karel simulator and the code of a robot from the command-line, if that's possible at all. You could also email the teacher, perhaps he can help as he's more familiar with the system than we are.

---

### Post by bradley002 on 2010-05-14
Ohh, I see. I thought the run commands just had different icons. Thanks so much for looking into it!

---

