---
title: "Help with Glade 3.4.0"
date: 2007-11-06
forum: Programming Talk
---

### Post by jondecker76 on 2007-11-06
I'm trying to get a grasp on programming in Linux as I have a ton of ideas of for applications that I would like to make.

I have Glade v3.4.0 installed but actually using it to make something has proven to be quite difficult. On top of that, all of the tutorials I can find are for older 2.x versions. And even on the gnome glade website, there is no real documentation on how to actually use it (i found a VERY small quick start guide that might have been 10 pages long)

I was expecting Glade to be similar to how VB in Windows works, but Its the containers that are messing me up and I can't find any good documentation on them.

Does anybody know where a good Glade 3 tutorial is? I've searched everywhere..

thanks,

Jon

---

### Post by ssam on 2007-11-06
it is probably worth learning a bit about gtk. (glade just make it easier to build a gtk interface).

start with [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)
the packing widgets section explains what containers are for.

also when looking at glade stff, look for libglade. glade code generation is depreciated.

if you want something more like VB ish have a look at [http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)

---

### Post by xeo_pt on 2007-11-06
> **jondecker76 said:**
> I'm trying to get a grasp on programming in Linux as I have a ton of ideas of for applications that I would like to make.

I have Glade v3.4.0 installed but actually using it to make something has proven to be quite difficult. On top of that, all of the tutorials I can find are for older 2.x versions. And even on the gnome glade website, there is no real documentation on how to actually use it (i found a VERY small quick start guide that might have been 10 pages long)

I was expecting Glade to be similar to how VB in Windows works, but Its the containers that are messing me up and I can't find any good documentation on them.

Does anybody know where a good Glade 3 tutorial is? I've searched everywhere..

thanks,

Jon

You need to known a "linux programming language" ( I know it doesn't exist) like C++, python, perl, ruby. after that you design your interface with Glade and the put your code on it.
Try python and wxGlade.

---

### Post by Tuna-Fish on 2007-11-06
If you want to add stuff like in windows, just choose a "new window" as a template and add a single "layout" or "fixed" on it. In layout, the buttons and such will resize & move when the window is resized, in fixed they don't.

The plague of linux desktop developement is the lack of integration between IDE's/editors and interface designers.

Even though pascal is just utterly awful language, I think that on windows/deplhi can whip out a simple phonebook software or similar in about 1/10 of the time that it would take me in linux.

When things get more complicated, things even out though.

---

### Post by jondecker76 on 2007-11-06
Thanks all, I will do some more reading..

I'm an experienced programmer, just never with FOSS tools or dealing with any Linux API's. It almost feels like starting all over again.

---

### Post by Quikee on 2007-11-06
> **Tuna-Fish said:**
> 
Even though pascal is just utterly awful language, I think that on windows/deplhi can whip out a simple phonebook software or similar in about 1/10 of the time that it would take me in linux.


This is where I started to wonder how much it would take me to create a dumb and very simplistic phone book with glade3 and geany using python without any thing else. The result is [this screencast]("http://freeweb.siol.net/tvajng/phoneBook.ogg") (and I even made stupid mistakes because of the excitement ;) ).

---

### Post by AlexThomson_NZ on 2007-11-06
Like most things, it takes a bit of practise and getting used to.  I used to find it quite frustrating at first too, but now I can whip out GUI C programs without too much effort (well, all effort being the program logic, GUI is trivial).  Just follow some of the tutorials, and ask for help when you need it.  

I learnt to love the code+GUI seperation too with Glade+libGlade, that you don't really get with VB/Delphi

---

### Post by Tuna-Fish on 2007-11-07
> **Quikee said:**
> This is where I started to wonder how much it would take me to create a dumb and very simplistic phone book with glade3 and geany using python without any thing else. The result is [this screencast]("http://freeweb.siol.net/tvajng/phoneBook.ogg") (and I even made stupid mistakes because of the excitement ;) ).

I don't have a screencast, but on delphi: 
1. Create a database table with proper fields (this takes by far the longest)
2. Start a new form, add the database components, link them together, link them to the created table and a proper view component, make the connection to database live.

Time taken: less than 3 mins, of which some was starting delphi.
Code written by hand: 0 bytes.

> **AlexThomson_NZ said:**
> 
I learnt to love the code+GUI seperation too with Glade+libGlade, that you don't really get with VB/Delphi

Yes. The glade way is by far better when the application gets very complex, as it is easy and comfortable to do a proper mvc separation, leading to less buggy and more readable and maintainable code.

the problem are the quick and dirty little apps that just need to do one thing, that are a breeze to do in windows, but take ages in linux.

---

### Post by MicahCarrick on 2007-11-07
I started an article a while back: _[VB Programmer’s Intro to Linux Programming with GTK+]("http://www.micahcarrick.com/08-19-2006/vb-in-linux-with-gtk.html")_ which discusses some of the issues a programmer may have when beginning to use Glade. Although this article is based on Glade2, it would likely help. The section on layout out an interface in glade shows how the GtkBoxes are used.

The main thing coming from a Windows developer background, is the way GTK+ uses "packing" of it's widgets. At first is seems awkward, but you'll absolutely love it once you get it. Instead of having to position, size, and move everything explicitly through code (fixed positioning), you pack widgets into containers and specify their packing options.

It all boils down (for the most part) to boxes (GtkHBox and GtkVBox) and maybe GtkTable. Learn what those widgets are and what homogeneous, expand, and fill properties do and you'll be good to go.

---

### Post by Quikee on 2007-11-07
> **Tuna-Fish said:**
> I don't have a screencast, but on delphi: 
1. Create a database table with proper fields (this takes by far the longest)
2. Start a new form, add the database components, link them together, link them to the created table and a proper view component, make the connection to database live.

Time taken: less than 3 mins, of which some was starting delphi.
Code written by hand: 0 bytes.


Interesting... I see your point now, but I never liked such "wizard" like programming as it fails on a more complex problems but I agree that such a application really is missing in Linux. 

Also if I'm not mistaken everything is "form" centric, which is not very convenient in larger and more complex programs where you want to have a generic view generated upon the data model. 

However it would be very interesting to create such a program/framework for i.e. Python, that would let you create a model (+ maybe some extra hints) and everything would be created "automagically" - including the code and glade file for GUI (for GUI tuning) and tables for custom configured database (or simply let the persistence layer handle that). 

I'm inspired enough to start such a project.  :)

---

### Post by ankursethi on 2007-11-07
Gambas.

[http://gambas.sf.net](http://gambas.sf.net)

---

### Post by jondecker76 on 2007-11-07
This is just getting more and more depressing..

I fell that I have a lot to offer to the Linux community but I just can't find the information I need. All dev documentation I've come across is horrible and incomplete at best.

Right now I'm just trying to use Glade to design a UI to a much needed linux app that I would like to develop and I'm getting nowhere.

Can anybody here tell me how to put a toolbar into a window??  I can add the Tool Bar item from containers, but how can I add buttons to it?? How can I group these buttons so that one is selected at a time? There is no official Glade documentation on this, nor after over 5 hours of researching can I even find a decent tutorial on it.

I'm finally starting to see why some people say that Linux apps are feature lacking, unpolished etc..  I mean how can they not be when the development tools don't even have documentation??

---

### Post by AlexThomson_NZ on 2007-11-07
I don't have Glade installed on the machine in front of me now, but I think from memory there is a button down the bottom on the right called "add" or something where you can add items to the toolbar (I'll check this when I get to work)

I agree about the documentation 100%, it can be very frustrating, but I guess there is enough on the web to get you started, and plenty of places to ask for help so is not all bad.  Still annoying though, and is a problem that will probably haunt OSS for a long time (I mean, who likes writing docs, especially for bigger apps like that which appeal only to coders?!)

---

### Post by Quikee on 2007-11-07
As AlexThomson_NZ said... and also you can right click on the toolbar and click edit..

---

### Post by Tuna-Fish on 2007-11-07
> **Quikee said:**
> Interesting... I see your point now, but I never liked such "wizard" like programming as it fails on a more complex problems but I agree that such a application really is missing in Linux. 

Also if I'm not mistaken everything is "form" centric, which is not very convenient in larger and more complex programs where you want to have a generic view generated upon the data model. 

However it would be very interesting to create such a program/framework for i.e. Python, that would let you create a model (+ maybe some extra hints) and everything would be created "automagically" - including the code and glade file for GUI (for GUI tuning) and tables for custom configured database (or simply let the persistence layer handle that). 

I'm inspired enough to start such a project.  :)

Note that we are not talking just code generators here: using generated code is always a maintenance nightmare unless the tool that made the code can read it, with changes, back in.

Actually, come to think of it, glade 3 is quite close. All it needs is a good set of components, that have settings fields where you can connect them together.

Currently testing libgnomedb...

---

### Post by Quikee on 2007-11-07
> **Tuna-Fish said:**
> Note that we are not talking just code generators here: using generated code is always a maintenance nightmare unless the tool that made the code can read it, with changes, back in.


Not necessary (and in the name of simplicity I hope I am right :) ). If you keep things separated there should not be any problem. 

For example a user should not touch classes and operations that are generated in model (they are data classes anyway). If he does - the next time he uses code generation he looses the changes - which is OK because the "code" is the model and not the generated class - no other logic should be in this classes anyway. 

Generated user interface file should be generated once or regenerated many times. But fine-tuning of the interface should be done through a program such as glade.

The only problem would be the "glue" between data-classes and the GUI which would have to be coded or "wizarded" in some way. 

I need to remember some use cases and analyse them to see if this will work the way I imagine.

---

### Post by WinterWeaver on 2007-11-07
> **jondecker76 said:**
> This is just getting more and more depressing..

I fell that I have a lot to offer to the Linux community but I just can't find the information I need. All dev documentation I've come across is horrible and incomplete at best.

Right now I'm just trying to use Glade to design a UI to a much needed linux app that I would like to develop and I'm getting nowhere.

Can anybody here tell me how to put a toolbar into a window??  I can add the Tool Bar item from containers, but how can I add buttons to it?? How can I group these buttons so that one is selected at a time? There is no official Glade documentation on this, nor after over 5 hours of researching can I even find a decent tutorial on it.

I'm finally starting to see why some people say that Linux apps are feature lacking, unpolished etc..  I mean how can they not be when the development tools don't even have documentation??

No way dude... just hang in there. I myself am a extremely Novice programmer. I started playing with Python, and then followed the pyGTK tutorials. I quickly understood how packing works etc.

Then I fooled around with Glade, being used to VB, I was quite confused at first. But I quickly discovered how wonderfull Glade is.

The biggest Plus side for me, is how amazingly I can separate my interface (gui) and Logic.

and I have to say, the documentation I've found is very very good. (well... my experience is mainly on Python, so I cant comment on other languages).

Good Luck!

WW

---

