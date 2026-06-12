---
title: "[SOLVED] PyGTK from scratch to a simple app, best way to go?"
date: 2008-05-14
forum: Programming Talk
---

### Post by Vadi on 2008-05-14
I'd like to make a PyGTK app that features a very simple non-interactive terminal widget, with several buttons (one to send a kill signal to the app running in the terminal).

I however know very little of gtk, and python. Can anyone recommend me the fastest / easiest way to go about learning this? Unfortunately I don't have time to learn the ins and outs of gtk, and then python :)

---

### Post by tamoneya on 2008-05-14
i would start by learning python.  Then start reading the pygtk documentation.  The reason behind this is because you wont really understand the pygtk documentation very well since it is in python.

---

### Post by Can+~ on 2008-05-15
Learn python fully (or any language for that matter), rather than start making half-designed half-thought applications.

You can build powerful shell applications in the mean time, when you grow better, you can go and learn any GUI toolkit.

---

### Post by LaRoza on 2008-05-15
> **Vadi said:**
> I'd like to make a PyGTK app that features a very simple non-interactive terminal widget, with several buttons (one to send a kill signal to the app running in the terminal).

I however know very little of gtk, and python. Can anyone recommend me the fastest / easiest way to go about learning this? Unfortunately I don't have time to learn the ins and outs of gtk, and then python :)

Perhaps you could use something simpler. Bash and Zenity for example. If you know the terminal commands you want to use, zenity is just a man page away.

---

### Post by Vadi on 2008-05-15
Alright, so giving zenity a try first (although, I found Glade yesterday evening ... it's amazing).

"ls | zenity --text-info" displays the ls fine, as do other commands too. However "./bot | zenity --text-info" just comes up with a blank box, and nothing that the program normally outputs into the terminal is shown. Any idea why?

---

### Post by Vadi on 2008-05-15
Ignore that, I figured it out. The output is only given to zenity when the program is terminated.

I really don't feel like learning a whole language just to make a simple app with one button and a widget :(

---

### Post by MicahCarrick on 2008-05-15
> Learn python fully (or any language for that matter), rather than start making half-designed half-thought applications.

I half-disagree. I think that many people are eager to see something "pretty" and may not have the discipline for study long enough to master a language before writing any code to do what they actually want and my not yet have developed the passion for programming. Although I think firmly learning the fundamentals of a language is the "right" way to approach getting into programming, many people are hobbyists with a little free time and there's nothing wrong with experimenting.

I think you can "jump in" to something like PyGTK so long as you have an understanding that what you will accomplish will be done "wrong" and more of a learning experience than anything else. You wont' understand how most of your own application does what it does. But if it accomplishes what you want, that gratification can go a long way towards inspiring you to learn how to do it right.

I would also stress that your first projects should not be pursued as applications for distribution--not until they've been completely rewritten once you know what you're doing :) 

With something like PyGTK, you will be picking up Python and GTK as you go. GUI applications programming is a very different animal than "regular" programming--and you won't know either. You're essentially going to have to piece together bits from other applications, the web, samples, and learning the manual. Every line of code will likely take you some time on the internet and in manuals to understand what is going on. Slowly you'll start to piece together how things work.

So you can start by building your interface in Glade. You will need to read up just a little bit on how GUI programming works. You can read this tutorial which covers designing a GUI in Glade without getting into the programming used to implement that design later: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

Then you can start trying to make the magic happen with Python... perhaps starting with a Libglade or GtkBuilder example "hello world" sort of application and building on it from there.

---

### Post by Delever on 2008-05-15
I would suggest installing screenlets and messing around with code. Translating weather screenlet to my language helped alot :)

Of course, you will still need to learn python, but at least you would have something working at your fingertips.

---

### Post by Vadi on 2008-05-15
> **MicahCarrick said:**
> -post-

Yes, you got me spot on. I actually tried out glade last night, and I've already got the buttons, widgets in place, and the quit buttons quits, as well as the X closes.

I've figured out that I can use popen to spawn the process I'd like; now I just need to connect that output to the text area and I'm good to go.

---

### Post by Vadi on 2008-05-15
Okay, now it's the question of glade2 vs glade3. Glade3 doens't generate any code, in C you're supposed to use the converted xml file. But the converter just gives some errors.

I think I'll just stick with glade2...

Edit: I just realized you're the guy who wrote it. Thanks so much!

---

### Post by MicahCarrick on 2008-05-15
> I've figured out that I can use popen to spawn the process I'd like; now I just need to connect that output to the text area and I'm good to go.
Here's an example: [_Execute command into a GtkTextView (C and Libglade)_]("http://www.gtkforums.com/about906.html")

> Okay, now it's the question of glade2 vs glade3. Glade3 doens't generate any code, in C you're supposed to use the converted xml file. But the converter just gives some errors.

The errors are from converting a glade file to a GtkBuilder XML file. There are a couple of bugs currently that require you to first remove some things from the XML file in order for it to convert properly That is discussed at: [_Migrating from libglade to GtkBuilder_]("http://library.gnome.org/devel/gtk/2.13/gtk-migrating-GtkBuilder.html") GtkBuilder is essentially the next generation of Libglade built right into GTK (as libglade is a separate library).

To simplify things for the time being if you're unable to figure out why the conversion script is failing, use LibGlade instead of GtkBuilder. They work almost identically and it does not require running the glade file through the conversion script. The only down side is that you have to include the glade library. (import gtk.glade). 

It's better to learn to use Libglade or GtkBuilder than to use Glade 2's deprecated code generation... you'll end up running into problems that way.

If you want, post or send me your .glade file and I'll tell you why gtk-builder-convert is failing.

---

### Post by Vadi on 2008-05-15
> **MicahCarrick said:**
> Here's an example: [_Execute command into a GtkTextView (C and Libglade)_]("http://www.gtkforums.com/about906.html")

Hmm, I tried that, but there's one problem - as my program is still running after it's executed, the window doesn't return the output and compiz even greys it out after a bit. I looked at the manual for g_spawn_command_line_async, but that doesn't have the output and error pipes.

So I thought I'd be smart and make a g_thread. Well, it did work - the window didn't freeze. However it's quite silly because I still have the initial problem of not getting the output from a pipe 'till the program finishes (and by threading it.. it just makes a new thread each time for the program. Heheh).

Any way I can get around that? I'll meanwhile tinker with the .glade file to get it converted nicely - I don't think distributing it would be too professional.

---

### Post by Vadi on 2008-05-15
Strangely enough, my quit/close buttons weren't working in glade3, while they were in glade2, for the same .glade file. Here's the error I was getting with the file last saved by glade3:

> Traceback (most recent call last):
  File "/usr/bin/gtk-builder-convert", line 745, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/gtk-builder-convert", line 733, in main
    conv.parse_file(input_filename)
  File "/usr/bin/gtk-builder-convert", line 161, in parse_file
    self._parse()
  File "/usr/bin/gtk-builder-convert", line 259, in _parse
    self._convert(node.getAttribute("class"), node)
  File "/usr/bin/gtk-builder-convert", line 284, in _convert
    self._convert_menu(node)
  File "/usr/bin/gtk-builder-convert", line 342, in _convert_menu
    item = self._convert_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 378, in _convert_menuitem
    item = self._convert_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 374, in _convert_menuitem
    self._add_action_from_menuitem(uimgr, obj_node)
  File "/usr/bin/gtk-builder-convert", line 425, in _add_action_from_menuitem
    properties['stock_id'] = child
UnboundLocalError: local variable 'child' referenced before assignment


I re-saved the file in glade2, and the conversion went alright.

Oh and I attached my .glade file. It was last saved in glade2.

---

### Post by MicahCarrick on 2008-05-16
Wow, I must admit, GtkBuilder is being troublesome here. I'm going to take the problems I came across and investigate further before promoting GtkBuilder too much more just yet.

It's been a few months since I've dinked around with this stuff, so I wasn't aware that Glade 3 now has the ability to save in GtkBuilder format. But even so, there are several problems.

As a beginner, it would probably be easier to use Libglade. Using your glade file from glade 3, make sure you're saving in "Libglade" format and not "GtkBuilder". Then you can implement you GUI with something like:

```
#!/usr/bin/env python

import sys
import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade
	
class MyApp:      
    def __init__(self):       
        gxml = gtk.glade.XML("test.glade3")
        dic = { "gtk_main_quit" : gtk.main_quit }
        gxml.signal_autoconnect (dic)            
        self.window = gxml.get_widget("window")

    def run(self):
        self.window.show()
        gtk.main()
    
if __name__ == "__main__":   
    app = MyApp()
    app.run()	
```

---

### Post by Vadi on 2008-05-24
I've went with plain C for now since that's what I'm more comfortable with. Python and it's IndentationErrors can wait for a bit.

I've setup my gtk program so now it launches the process asyncronously, and properly keeps reading output from it, and just displays it with "printf". Now, I'd like to connect that to my GtkTextBuffer buffer. One question though, can I use the callbacks auto-generated by Glade2? Because I don't know how to do my own makefiles, and glade3 as I understand doesn't help me with that while glade2 did.

---

### Post by Vadi on 2008-05-27
Much thanks to MicahCarrick for his help. My app is pretty much finished now; I've attached screenshots of what I was using before (xterm) and after. Notice the icon in the system tray too ;)

---

