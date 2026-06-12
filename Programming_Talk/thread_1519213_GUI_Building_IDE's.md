---
title: "GUI Building IDE's"
date: 2010-06-27
forum: Programming Talk
---

### Post by KdotJ on 2010-06-27
There are many... Visual Studio, Netbeans, Qt Creator to name a few. IDE's that have the abilities to allow the user to create graphical interfaces by simply dragging and dropping components onto a window/frame/container etc.

My question is, do you consider using them somewhat 'cheating'?

My personal opinion is varied. For example, I believe its good to use them provided you have a fairly good idea of what is being done for you. I don't believe such IDE features are good for beginners, as you don't get to learn how GUI's are actually written, set up and handled. When I first started to program, years a go using Visual Basic, I used the Visual Studio Express Edition program for it.. I was able to build wonderful GUIs, with lovely looking graphics and masses of complex components. But I ad no actual knowledge of how to build them by hand, let alone any knowledge of signals/event handlers, I just had to double click on a button for example and the IDE created an event handler event for me.
When I went to uni, we were required to learn java and for the first year we wasn't allowed to use Netbeans, just simply a text editor. My programming skills were suddenly capped as I had to learn about Swing and Listeners from scratch. Now I feel much more involved and when I finished my projects, I had a much greater sense of achievement as I had literally written these things from nothingness. Now I write the majority of my GUI code by hand, and I feel I have much more control over things, and things are much easier when it comes to maintenance.

On the other side of the coin, GUI builders are great for time constraints, or when you want an easy ride, and when you want to knock up a prototype. And I know in the real world, where projects are worked on by hundreds of people, and consist of hundreds of code files, that IDE features such as this are a god send.

So my over all answer, no I do not consider it 'cheating', I just think that people shouldn't rely on them.

Opinions?

By the way, I do not wish to start any wars here lol.

---

### Post by unter on 2010-06-27
I am ne to programming and idd build one interface using glade ... but now I have no idea what to do with it lol 

so I guess you is correct hehe

---

### Post by mmix on 2010-06-27
IMHO, glade worst gui build tool ever.

Better off to use gambas or vala.

---

### Post by Simian Man on 2010-06-27
Is it cheating to use a compiler if you don't know assembly language?  Programming **is** abstraction.  To say one level is OK and another is cheating is retarded.

---

### Post by slavik on 2010-06-27
> **Simian Man said:**
> Is it cheating to use a compiler if you don't know assembly language?  Programming **is** abstraction.  To say one level is OK and another is cheating is retarded.
more on this.

1. glade is not horrible. if you think glade is horrible, it means that you do not understand GTK.
2. if you are building a complex app which requires/uses a gui, it is very nice to build the gui separate from code so that you can get feedback on it.
3. since glade does not involve writing code, any designer can build a mock up of the app with good design guidelines.

back to point 1. the first gui I built was in visual basic. it's ncie to drag and drop buttons and then click on them and fill in the code. visual basic is nice in that it hides the plumbing of the application (no need to call vb->main(); or similar). just remember to write in the code when you resize the window ;)

GTK is centered around containers and elements, containers can contain other containers and elements fill containers. GTK takes resizing work away from you. when you design an app with gtk, you have to remember to design the layout of the app with containers first. this takes some getting used to.

points 2 and 3. if the app being built is supposed to take a bunch of options and run them through some main function (think a gui for a sound transcoder) then you can code the functionality separate from the gui. and the gui can have re-arranged buttons and styles and whatever else you want. basically, you are separating the gui from the core code of your app. this allows you to update one or the other without much dependencies (except if you have a button, you want some code behind it).

---

### Post by unter on 2010-06-27
> **slavik said:**
> more on this.

1. glade is not horrible. if you think glade is horrible, it means that you do not understand GTK.
2. if you are building a complex app which requires/uses a gui, it is very nice to build the gui separate from code so that you can get feedback on it.
3. since glade does not involve writing code, any designer can build a mock up of the app with good design guidelines.


I find interface of glade very enjoyable. tho i find when i saved file it just saved to small markup file with not big statements. so i conclusion that maybe for developed programmer glade is not so necessary and can be written easy fast by hand without visual.

---

### Post by slavik on 2010-06-27
> **unter said:**
> I find interface of glade very enjoyable. tho i find when i saved file it just saved to small markup file with not big statements. so i conclusion that maybe for developed programmer glade is not so necessary and can be written easy fast by hand without visual.
I agree with you, but see my point 3. ;)

Also, I think it would be easier to modify .glade files (which are gtkbuilder xml anyways) and have gtkbuilder->new_window(XMLFILE) than to have gui code inside your program code.

one extra thing that I love about gtk in combination with perl/ruby/python is that you can have a class/package with callbacks and get them assigned via one function (provided you put callback info in the interface properties), single function call. unlike C/C++ where you have to bind each function manually.

This is really old code that uses gladeXML instead of gtkbuilder. (it's from my treeview code which you can find by searching forums).

```

my $app = new Gtk2::GladeXML("treeview.glade");
$app->signal_autoconnect_from_package("callbacks");

```

---

### Post by splicerr on 2010-06-28
> **slavik said:**
> I agree with you, but see my point 3. ;)

Also, I think it would be easier to modify .glade files (which are gtkbuilder xml anyways) and have gtkbuilder->new_window(XMLFILE) than to have gui code inside your program code.


Agreed.

> 
one extra thing that I love about gtk in combination with perl/ruby/python is that you can have a class/package with callbacks and get them assigned via one function (provided you put callback info in the interface properties), single function call. unlike C/C++ where you have to bind each function manually.
Not sure about Glade, but with GtkBuilder you can autoconnect signals to signal handlers in C code.

---

### Post by kalaharix on 2010-06-28
I thought KdotJ's question well balanced. I fear many of the replies may not be! 

"I had a much greater sense of achievement as I had literally written these things from nothingness". Yup, and just imagine the sense of achievement if you had written the whole thing in assembler.

Slavik: "Also, I think it would be easier to modify .glade files (which are gtkbuilder xml anyways) and have gtkbuilder->new_window(XMLFILE) than to have gui code inside your program code." Gambas (and even VB) keep the gui definitions in a separate file. Any fule no that! Anyway it is not as simple as that. Many guis are dynamic and respond to input.

Slavik:"if you are building a complex app which requires/uses a gui, it is very nice to build the gui separate from code so that you can get feedback on it." Anybody would think you can't program Gambas that way. You can. You can even write stand-alone components in Gambas for use within Gambas.

At the end of the day it's a case of each to his own. All I can say is that a less condescending attitude by the community towards integrated-gui IDEs will encourage more newcomers to write code for Linux. Who knows: if that happened maybe desktop Linux would actually achieve critical mass.

One has only to look at the 'beginners' programming challenges in this forum to realise how unworldly it can all become. 

Where do I get my sense of achievement? From writing a piece of software which others (some not very computer-literate) can use without it crashing. With the minimum of effort. I'll stick to Gambas.

---

### Post by slavik on 2010-06-28
> **splicerr said:**
> Not sure about Glade, but with GtkBuilder you can autoconnect signals to signal handlers in C code.

I did not know that. Thanks.

---

### Post by SledgeHammer_999 on 2010-06-28
I agree with the OP. I write my gui code by hand and I have A LOT about gtkmm(and gtk) by doing that. I voted for "couldn't care less". I sometimes use glade just to *design* my layout and then I code it by hand.

---

