---
title: "Robot program, possible?"
date: 2011-04-20
forum: Programming Talk
---

### Post by SpinningAround on 2011-04-20
Would it be possible to write a program in java that act as a robot or AI? What I would like to create is a program that right click on an image in f-spot, select the menu item "get path", change program to firefox and copy the file location into an upload file field.

There are a few things that need to be possible to do this.
Get items in a menu (outside java app) and select the correct item.
Find a specific area within a webpage.
If those can be done without using super position, I know that a specific field is on a webpage, but not exactly where.

I don't know if this is possible or not, maybe would it be easier to make a video tutorial if that is the case where to I start.

---

### Post by simeon87 on 2011-04-20
You don't need to interact with a window/menu to do this, from what I can tell.

If you know where the files are located, you can simply write code that submits them to the website. You can visit a website, fill in forms and submit automatically by editing the HTML code of a webpage.

You'll need to look into how this works in Java but as far as I can see there's no need to take the complicated route of right-clicking, menus, etc.

---

### Post by hakermania on 2011-04-20
Can this done via macros as well?

---

### Post by ve4cib on 2011-04-20
I'm afraid I don't quite follow what you want to do with the menus and right-clicking and such, but I can answer this part:

> Would it be possible to write a program in java that act as a robot or AI?

Absolutely.  You can write AI/robot control programs in pretty much any language you want.  Usually anything running on the robot itself is written in C or C++, since most robot kits out there are pretty low-powered spec-wise (the robots we use in the lab at university have 14MHz CPUs and somewhere around 128 kB of memory).  But you could certainly write Java software that would run on a PC to send commands to a robot.  Nothing wrong with that.

---

### Post by kostkon on 2011-04-20
There's [*Sikuli*]("http://sikuli.org/").

---

### Post by nvteighen on 2011-04-21
AI are written using algorithms modelled by computer scientists, therefore they are meant to be as general as possible and not language/platform-dependent at all. CompSci is a theoretical subject, obviously related to programming, but it isn't programming... Implementations will be language dependent and the algorithm may be easier to write in one language than in another, but it will always be possible in any Turing-complete language.

---

### Post by schauerlich on 2011-04-21
> **nvteighen said:**
> AI are written using algorithms modelled by computer scientists, therefore they are meant to be as general as possible and not language/platform-dependent at all. CompSci is a theoretical subject, obviously related to programming, but it isn't programming... Implementations will be language dependent and the algorithm may be easier to write in one language than in another, but it will always be possible in any Turing-complete language.

I think when he says "AI" he means "something to simulate clicks," which isn't an AI at all.

---

### Post by gutux on 2012-06-30
Hy there,

if Java AND AI is needed, then i think,
tis is the right place to go:

[http://robocode.sourceforge.net/](http://robocode.sourceforge.net/)
[]("http://ubuntuforums.org/Hy%20there,%20%20if%20Java%20AND%20AI%20is%20needed,%20then%20i%20think,%20tis%20is%20the%20right%20place%20to%20go:%20%20http://robocode.sourceforge.net/")
and to simulate clicks it maybe 
[U]
sikuli.org
[/U] 
regards

---

### Post by PaulM1985 on 2012-06-30
If all you need are a certain amount of button clicks, this can be done with the Java Robot class:
[http://docs.oracle.com/javase/1.5.0/docs/api/java/awt/Robot.html](http://docs.oracle.com/javase/1.5.0/docs/api/java/awt/Robot.html)

It is possible to move the mouse to a position, click, press keys, etc.

I guess you are simulating clicks and that should be fairly straightforward using that class.  One thing that is worth noting, if you simulate a click to bring a window to the front, make sure that you put a sufficient "sleep" command in your application to allow the window to come to the front.  The commands executed by Java happen very quickly in relation to how the user interface reacts and your robot could end up running away before the rest of the PC catches up.

Paul

---

