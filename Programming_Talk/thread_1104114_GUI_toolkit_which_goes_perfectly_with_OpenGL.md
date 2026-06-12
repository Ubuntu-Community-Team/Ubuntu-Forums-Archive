---
title: "GUI toolkit which goes perfectly with OpenGL?"
date: 2009-03-23
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-23
I got a program, which is built around SDL+OpenGL. Now I need a GUI toolkit for it.

The GUI should do the following:
[list]
[*]Button
[*]Container with slider
[*]Right-click menu (not 100% necessary)
[*]Render in OpenGL
[/list]
So I just need the very basic functions.

And I don't want a GTK+ with OpenGL canvas. That would require too much changes.

Also the GUI should be easy to use, so it will take less time to learn the GUI than to write my own.

The program is also Python-scriptable, so Python libaries are OK as well (if they render in OpenGL and I can inject the user input).

---

### Post by cabalas on 2009-03-23
What about an OpenGL base GUI toolkit like [Crazy Eddies]("http://www.cegui.org.uk/wiki/index.php/Main_Page") that way you shouldn't have to change any of your underlying code.

A friend of mine uses it on all of his projects a demo of one using CEGUI can be found [here]("http://bieh.net/bsod2_updat/").

---

### Post by shatterblast on 2009-03-23
I think there are a number you could possibly use that come oriented with LWJGL.org.  The first that comes to mind is the one from FengGUI.org.  I recently tried to compile it though and had problems doing so.  I didn't mess with it much how ever nor did I look for a precompiled API library.  There are a number of other "game" GUIs as well, which might serve your purposes since Xith.org and the jmonkeyengine.com I think can both integrate well with Swing.  Expect to encounter an involving learning curve with those last two.

I think a number of others can coordinate with JOGL as well.  Any how, just rambling off some links....

[http://nifty-gui.sourceforge.net/](http://nifty-gui.sourceforge.net/)
[http://slick.cokeandcode.com/thingle/](http://slick.cokeandcode.com/thingle/)

I found Thingle interesting, yet it may not serve the purpose of quick and easy.  My personal preference would start with FengGUI.org for non-game OpenGL software.  Xith in my experience could also do the job.  It would just take time.  Also, Xith has a decent UI case test where widgets can be placed where ever by dragging items around.  I think it's something related to a "widget manipulator."

I have yet to find a "drag and drop" open source functionality for GUIs in OpenGL.  If unconcerned about performance tweaks, an alternate solution would be going with building a Swing UI and then integrating it with some other API of choice.  Visual Swing Designer for Eclipse is relatively new.  I've yet to experiment with it, but it does install easily if you prefer Eclipse as your environment.  The site for it is at:

[http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1449.html](http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1449.html)

I'm not sure if this next link would be useful at all, but it could possibly export a premade Swing GUI into OpenGL.  EclipseP5Exporter for Eclipse:

[http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1422.html](http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1422.html)

Again, FengGUI is suppose to have widgets like buttons, scroll bars, and similar already available.  Lastly if you know anything about QT Jambi, it too can integrate with OpenGL in some fashion unfamiliar to me.

---

### Post by crazyfuturamanoob on 2009-03-24
> **cabalas said:**
> What about an OpenGL base GUI toolkit like [Crazy Eddies]("http://www.cegui.org.uk/wiki/index.php/Main_Page") that way you shouldn't have to change any of your underlying code.

A friend of mine uses it on all of his projects a demo of one using CEGUI can be found [here]("http://bieh.net/bsod2_updat/").

I tried CEGUI already, but it seems to take more time to compile/setup, learn API, and make XMLs than write my own GUI (because I don't need much).

> **shatterblast said:**
> I think there are a number you could possibly use that come oriented with LWJGL.org.  The first that comes to mind is the one from FengGUI.org.  I recently tried to compile it though and had problems doing so.  I didn't mess with it much how ever nor did I look for a precompiled API library.  There are a number of other "game" GUIs as well, which might serve your purposes since Xith.org and the jmonkeyengine.com I think can both integrate well with Swing.  Expect to encounter an involving learning curve with those last two.

I think a number of others can coordinate with JOGL as well.  Any how, just rambling off some links....

[http://nifty-gui.sourceforge.net/](http://nifty-gui.sourceforge.net/)
[http://slick.cokeandcode.com/thingle/](http://slick.cokeandcode.com/thingle/)

I found Thingle interesting, yet it may not serve the purpose of quick and easy.  My personal preference would start with FengGUI.org for non-game OpenGL software.  Xith in my experience could also do the job.  It would just take time.  Also, Xith has a decent UI case test where widgets can be placed where ever by dragging items around.  I think it's something related to a "widget manipulator."

I have yet to find a "drag and drop" open source functionality for GUIs in OpenGL.  If unconcerned about performance tweaks, an alternate solution would be going with building a Swing UI and then integrating it with some other API of choice.  Visual Swing Designer for Eclipse is relatively new.  I've yet to experiment with it, but it does install easily if you prefer Eclipse as your environment.  The site for it is at:

[http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1449.html](http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1449.html)

I'm not sure if this next link would be useful at all, but it could possibly export a premade Swing GUI into OpenGL.  EclipseP5Exporter for Eclipse:

[http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1422.html](http://www.eclipseplugincentral.com/Web_Links-index-req-viewlink-cid-1422.html)

Again, FengGUI is suppose to have widgets like buttons, scroll bars, and similar already available.  Lastly if you know anything about QT Jambi, it too can integrate with OpenGL in some fashion unfamiliar to me.

Did I forgot to mention I use C++, not Java?

---

### Post by tneva82 on 2009-03-24
> **crazyfuturamanoob said:**
>  but it seems to take more time to compile/setup, learn API, and make XMLs than write my own GUI (because I don't need much).

Well. If you are looking for really simple GUI why not just write your own? I did barebone GUI with windows, buttons, textfield and textlabels(with freetype font library I found from net and which is darn easy to use) in justabout day. Need to do multiline text fields(pretty easy, just haven't got time to do it as I'm working with 3d-engine now), frames, containers and what I call placeholders but barebones it's working.

Shouldn't be too hard if you know openGL and some sort of keyboard/mouse handling system(I used SDL). I mean if *I* can get barebones GUI with windows, buttons, textfields and textlabels with mouse clicks and drag&drop working within ~day(double click is something I decided to forego after I figured I could live without it and SDL doesn't directly support it so would be more complicated) then so can anybody do it in quick time. I'm not a pro programmer ;-) (and it shows in the code but atleast it does what I want it to do)

Of course feasibility of this is heavily dependant on how fancy GUI you are looking but since I didn't need fancy one(and wanted to see wether I could get it working...Also wasn't sure I could get GUI appearance I want(well dream of more of. Since I'm no artist either my ability to create GUI I would like is rather limited :D) with CEGUI that was also bummer. Somehow I got "office style" feeling out of it which isn't what I want) I went this way.

---

### Post by the_unforgiven on 2009-03-24
How about using QT?
It already has module for OpenGL:
[http://doc.trolltech.com/4.5/qtopengl.html](http://doc.trolltech.com/4.5/qtopengl.html)

And it's cross-platform (X11/Windows/OSX) + [LGPLed]("http://doc.trolltech.com/4.5/lgpl.html") (since v4.5).

---

### Post by crazyfuturamanoob on 2009-03-24
> **the_unforgiven said:**
> How about using QT?
It already has module for OpenGL:
[http://doc.trolltech.com/4.5/qtopengl.html](http://doc.trolltech.com/4.5/qtopengl.html)

And it's cross-platform (X11/Windows/OSX) + [LGPLed]("http://doc.trolltech.com/4.5/lgpl.html") (since v4.5).

Then I should switch to qmake.

I just want to be programming, not setting up environments.

> **tneva82 said:**
> Well. If you are looking for really simple GUI why not just write your own? I did barebone GUI with windows, buttons, textfield and textlabels(with freetype font library I found from net and which is darn easy to use) in justabout day. Need to do multiline text fields(pretty easy, just haven't got time to do it as I'm working with 3d-engine now), frames, containers and what I call placeholders but barebones it's working.

Shouldn't be too hard if you know openGL and some sort of keyboard/mouse handling system(I used SDL). I mean if *I* can get barebones GUI with windows, buttons, textfields and textlabels with mouse clicks and drag&drop working within ~day(double click is something I decided to forego after I figured I could live without it and SDL doesn't directly support it so would be more complicated) then so can anybody do it in quick time. I'm not a pro programmer ;-) (and it shows in the code but atleast it does what I want it to do)

Of course feasibility of this is heavily dependant on how fancy GUI you are looking but since I didn't need fancy one(and wanted to see wether I could get it working...Also wasn't sure I could get GUI appearance I want(well dream of more of. Since I'm no artist either my ability to create GUI I would like is rather limited :D) with CEGUI that was also bummer. Somehow I got "office style" feeling out of it which isn't what I want) I went this way.

Can I use your GUI? That would save me some time. But if no, then the only way is to write my own GUI.

---

### Post by tneva82 on 2009-03-24
> **crazyfuturamanoob said:**
> Can I use your GUI? That would save me some time. But if no, then the only way is to write my own GUI.

Well technicly no reason why not but not sure how much time you would save by trying to understand my code rather than making your own :D If you still wish them just say so and I'll put them available(and try to give some rough guide on how to use them).

---

### Post by days_of_ruin on 2009-03-24
Have you looked at clutter?
[http://www.clutter-project.org/]("http://www.clutter-project.org/")
It has python bindings too ;)

---

### Post by the_unforgiven on 2009-03-25
> **crazyfuturamanoob said:**
> Then I should switch to qmake.

I just want to be programming, not setting up environments.

AFAIK, qmake is required only to create the project makefiles from the project description file - which is a one-time job. IIRC, qmake is not a complete build-system on its own.

Also, if you don't want to do all that manually, you can use kdevelop to generate the project skeleton from a template and just focus on coding - using whatever tools you prefer.

---

### Post by abhilashm86 on 2009-03-25
> **the_unforgiven said:**
> 

Also, if you don't want to do all that manually, you can use kdevelop to generate the project skeleton from a template and just focus on coding - using whatever tools you prefer.
now we can use just GUI Qt 4.5, that dosen't really need qmake, because we can create files and link everything using sdk package of qt 4.5,
can you please tell why we need to use qmake?

---

### Post by NathanB on 2009-03-25
I think the Open graphics Tool Kit is very close to your specs:

[http://otk.sourceforge.net/](http://otk.sourceforge.net/)

---

### Post by crazyfuturamanoob on 2009-03-25
> **NathanB said:**
> I think the Open graphics Tool Kit is very close to your specs:

[http://otk.sourceforge.net/](http://otk.sourceforge.net/)

Yes. Easy to use, requires very few lines to use, but one major thing makes it unusable:
```

OtkMainLoop();

```
That is needed to make the GUI display. But I got my own mainloop! I can't use that, or anything which needs to use a main loop function,

---

### Post by the_unforgiven on 2009-03-26
> **abhilashm86 said:**
> now we can use just GUI Qt 4.5, that dosen't really need qmake, because we can create files and link everything using sdk package of qt 4.5,
can you please tell why we need to use qmake?
You don't - that's what I was saying..
qmake was used in older version of QT build process - but, it's no longer a requirement.

---

### Post by crazyfuturamanoob on 2009-03-26
I will just make my own GUI. All other GUIs are either way too complex and large, take long time to setup and learn, or they got that stupid main loop thing.

---

### Post by Delever on 2009-03-26
I did some work on [text rendering]("http://code.google.com/p/glstext/"), if you need that.

---

### Post by clustermonkey on 2009-03-27
If you haven't started already, I would suggest looking
at [GLUT]("http://http://www.opengl.org/resources/libraries/glut/") (OpenGL Utility Toolkit) and [FLTK]("http://http://www.fltk.org/") (Fast Light TK).
Both of these are fairly simple and lightweight.

---

### Post by shatterblast on 2009-03-27
Doesn't Ogre have something for GUIs?  I think that's an SDL game development library intended for C / C++.  I skipped over it back in the day when I decided to develop in Java instead because of its cross-platform nature.

This may prove interesting:

[http://sourceforge.net/projects/assortedwidgets/](http://sourceforge.net/projects/assortedwidgets/)
[http://sourceforge.net/projects/agar/](http://sourceforge.net/projects/agar/)
[http://sourceforge.net/projects/guilib/](http://sourceforge.net/projects/guilib/)
[http://sourceforge.net/projects/mysdlgui/](http://sourceforge.net/projects/mysdlgui/)

---

### Post by crazyfuturamanoob on 2009-03-28
> **clustermonkey said:**
> If you haven't started already, I would suggest looking
at [GLUT]("http://http://www.opengl.org/resources/libraries/glut/") (OpenGL Utility Toolkit) and [FLTK]("http://http://www.fltk.org/") (Fast Light TK).
Both of these are fairly simple and lightweight.

As I stated already (did I?) I stick with SDL+OpenGL. GLUT is too restrictive for me, and it would require some major changes.

> **shatterblast said:**
> Doesn't Ogre have something for GUIs?  I think that's an SDL game development library intended for C / C++.  I skipped over it back in the day when I decided to develop in Java instead because of its cross-platform nature.

This may prove interesting:

[http://sourceforge.net/projects/assortedwidgets/](http://sourceforge.net/projects/assortedwidgets/)
[http://sourceforge.net/projects/agar/](http://sourceforge.net/projects/agar/)
[http://sourceforge.net/projects/guilib/](http://sourceforge.net/projects/guilib/)
[http://sourceforge.net/projects/mysdlgui/](http://sourceforge.net/projects/mysdlgui/)

Ogre uses CEGUI by default, which I found too large for my project. And Ogre is overkill for my small project.


Assorted Widgets is windows-only. Just VB project files, DLL's and EXE's. 

Can't compile MySdlGui because it doesn't find sigc++ headers. 
I installed libsigc++-2.0 devs and everything. "locate" says the headers don't exists.

Agar has that evil EventLoop() function, making it completely useless.

And Guilib's sourceforge page doesn't have download link.


I make my own GUI. I don't like the existing GUI libraries.

---

### Post by nvteighen on 2009-03-28
Maybe you should think about direct Xlib programming... as you seem to need a lower level abstraction than that provided by GUI toolkits...

---

### Post by c174 on 2009-03-28
Did you look at FreeGLUT? It is GLUT + some extra functionality, such as stopping/starting the main loop.

---

### Post by crazyfuturamanoob on 2009-03-28
> **c174 said:**
> Did you look at FreeGLUT? It is GLUT + some extra functionality, such as stopping/starting the main loop.

I got a project, which relies heavily on SDL, and that's not going to change.

> **nvteighen said:**
> Maybe you should think about direct Xlib programming... as you seem to need a lower level abstraction than that provided by GUI toolkits...

No. SDL can create the window, SDL can setup the window like so OpenGL renders on it. And the GUI only has to render in OpenGL and update.

The main problem of all GUI libraries is that they got main loop function, which updates and draws the GUI, preventing me from using the GUI simultaneously with OpenGL and other stuff.

Instead of main loop, the GUI should have an update function, which takes mouse/keyboard input as arguments, and updates, so I can call the function in my main loop, and a render function.

And that wouldn't be cross-platform either (although I don't care about cross-platform compatibility).

---

### Post by nvteighen on 2009-03-28
Hm... I see that you can iterate the GTK+ main loop at will using gtk_main_iterate()... If so, you can create your own loop which at the end calls one iteration of GTK+'s main loop...

---

### Post by c174 on 2009-03-28
> **crazyfuturamanoob said:**
> The main problem of all GUI libraries is that they got main loop function, which updates and draws the GUI, preventing me from using the GUI simultaneously with OpenGL and other stuff.

Did you consider a multi-threaded program? One thread for your computations and another one for the graphics. For example someting like this

```

// global variables can be used to share information between threads
double ...

void graphics_thread_start() {
   // init SDL / FreeGLUT / whatever
   // add GL-canvas, menues, etc
   // start main-loop
}

int main( ... ) {
   // start graphics thread (use some thread library)

   for( ... ) {
      // carry out computations
      // post redisplay request to SDL / FreeGLUT ...
   }
}
```
 
I did something like that one time. It worked fine :)

---

### Post by crazyfuturamanoob on 2009-03-28
> **nvteighen said:**
> Hm... I see that you can iterate the GTK+ main loop at will using gtk_main_iterate()... If so, you can create your own loop which at the end calls one iteration of GTK+'s main loop...

Thanks, perfect solution! :)

[s]Should I use gtk_main_iteration() or gtk_main_iteration_do()? The other one "blocks", whatever it means.[/s]

Edit: I tried them both. gtk_main_iteration() makes insane laag but gtk_main_iteration_do(0) works just fine.

> **c174 said:**
> Did you consider a multi-threaded program? One thread for your computations and another one for the graphics. For example someting like this

```

// global variables can be used to share information between threads
double ...

void graphics_thread_start() {
   // init SDL / FreeGLUT / whatever
   // add GL-canvas, menues, etc
   // start main-loop
}

int main( ... ) {
   // start graphics thread (use some thread library)

   for( ... ) {
      // carry out computations
      // post redisplay request to SDL / FreeGLUT ...
   }
}
```
 
I did something like that one time. It worked fine :)

I use Gtk because I already know some of the API and it doesn't need as big changes as the thread thing.

---

### Post by nvteighen on 2009-03-29
Great! As far as I read at the API docs (btw, have you DevHelp installed?) gtk_main_iteration() iterates once but waits for some GTK+ signal if none has occurred. gtk_main_iteration_do(0) won't wait and will return if no event is needed to be processed.

I guess I don't need to explain I love GTK+ :)

---

