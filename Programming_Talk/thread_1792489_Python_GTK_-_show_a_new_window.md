---
title: "Python GTK - show a new window"
date: 2011-06-28
forum: Programming Talk
---

### Post by tubunu on 2011-06-28
I'm a beginner browsing through python/GTK tutorials. I have already created a simple window with a couple of buttons that do basic things. 

The next thing I'd like to do is to link a button that is on the main window so that when it is clicked a new window pops up. How do I go about doing that? Or better yet, what should I google to find more information about that? THANKS.

---

### Post by Tony Flury on 2011-06-28
You create a new Window object - populate it with the relevant controls - and show it.

Have you tried doing that ?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-28
> **tubunu said:**
> I'm a beginner browsing through python/GTK tutorials. I have already created a simple window with a couple of buttons that do basic things. 

The next thing I'd like to do is to link a button that is on the main window so that when it is clicked a new window pops up. How do I go about doing that? Or better yet, what should I google to find more information about that? THANKS.
You can use message dialogs.....but are u trying to create a new window with widgets or just displaying some info or choice...
if u r trying to open a new window u can create a window object and show it at the click of a button or an event
here's the code:
```

def but_call(widget,data=None):
              #do what u want here
               win.show_all()   #this shows ur new window
     
win=gtk.Window()
win.connect("destroy",lambda wid:gtk.main_quit())
mywin=gtk.Window()
mywin.connect("destroy",lambda wid:gtk.main_quit())


#now show this window when somebody presses a button in ur main window... mywin
button=gtk.Button()
button.connect("clicked",but_call)
mywin.add(button)
mywin.show_all()
gtk.main()


```

---

### Post by tubunu on 2011-06-29
Thanks everyone! 
After a bit of experimenting, I came up with this code:

```
		
	def answer(self, widget=None, data=None):
		answerwin = gtk.Window()
		answerwin.set_position(gtk.WIN_POS_CENTER)
		answerwin.set_size_request(400, 200)
		answerwin.set_title("Answer")
		answerwin.show()
			
	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_position(gtk.WIN_POS_CENTER)
		self.window.set_size_request(400, 200)
		self.window.set_title("Main window")	
		self.window.set_tooltip_text("hello")
		
		self.answer_button = gtk.Button("Answer")
		self.answer_button.connect("clicked", self.answer) 
		self.answer_button.set_tooltip_text("See the answer...")
```


Now I'd like to place an OK button on that new window (answerwin). Where do I place the code for it? Thanks.
(I've done a new def for okbutton, connected and packed it, but it doesn't show on answerwin. Do I need to create a new class for it?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-29
> **tubunu said:**
> Thanks everyone! 
After a bit of experimenting, I came up with this code:

```
        
    def answer(self, widget=None, data=None):
        answerwin = gtk.Window()
        answerwin.set_position(gtk.WIN_POS_CENTER)
        answerwin.set_size_request(400, 200)
        answerwin.set_title("Answer")
        answerwin.show()
            
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.window.set_size_request(400, 200)
        self.window.set_title("Main window")    
        self.window.set_tooltip_text("hello")
        
        self.answer_button = gtk.Button("Answer")
        self.answer_button.connect("clicked", self.answer) 
        self.answer_button.set_tooltip_text("See the answer...")
```Now I'd like to place an OK button on that new window (answerwin). Where do I place the code for it? Thanks.
(I've done a new def for okbutton, connected and packed it, but it doesn't show on answerwin. Do I need to create a new class for it?
No u dont have to create a new class for that just place your button code below the answerwin=gtk.Window() 
line and add it to the window like 
answerwin.add(button_ok) #assuming button_ok is the name of the button object...
and then add answerwin.show_all() #use show_all() or else only the window will show up not the widgets....
*tip:don't forget to place the gtk.main() at the right place
       use window.show_all() not window.show()

---

### Post by tubunu on 2011-06-29
Perfect! Thank you so much!

---

### Post by tubunu on 2011-06-30
I've come up against another stumbling block... How do I add a new window, but this time from a file I created in Glade? I'd like it to pop up with the UI I created in glade rather than code everything by hand.

```

    def on_button2_clicked(self, widget, data=None):
        print "Button 2 has just been clicked!"
        builder.add_from_file([COLOR="Magenta"]"data/ui/Winopen.ui"[/COLOR])
        builder.connect_signals(self)
        self.window.show_all()  

```

I've spent several hours looking at pygtk docs, but being totally new to this I don't know how to apply the information in my code. I would appreciate if someone could point me in the right direction. Thanks.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-30
> **tubunu said:**
> I've come up against another stumbling block... How do I add a new window, but this time from a file I created in Glade? I'd like it to pop up with the UI I created in glade rather than code everything by hand.

```

    def on_button2_clicked(self, widget, data=None):
        print "Button 2 has just been clicked!"
        builder.add_from_file([COLOR=Magenta]"data/ui/Winopen.ui"[/COLOR])
        builder.connect_signals(self)
        self.window.show_all()  

```I've spent several hours looking at pygtk docs, but being totally new to this I don't know how to apply the information in my code. I would appreciate if someone could point me in the right direction. Thanks.
hey....... although glade is good but i'll advise u to code everything that way u'll understand the working behind the interface....

U can add message dialogs showing some info...but i must ask why r u going so fast...i'll advise u to take everything slow...without the basics u'll have problems like this everytime if u want i can post a gud buk here....

---

### Post by tubunu on 2011-06-30
> **Dhiraj Thakur(Invincible) said:**
> hey....... although glade is good but i'll advise u to code everything that way u'll understand the working behind the interface....

Yes, you're absolutely right. I've already educated myself a bit (and still am in the process of learning more) by following a nice [Python GTK video tutorial]("http://www.youtube.com/watch?v=MxYl3cnn4yw") and can already do basic things like show a window, insert a button, add message dialog, etc. I suppose what I would like to achieve now is to be able to test my ability to link two windows created in glade. It can't be that hard, but I just don't know how to do that and I can't find any tutorials about it. :(

> **Dhiraj Thakur(Invincible) said:**
> if u want i can post a gud buk here....

I would like that very much. Thank you.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-30
I am also studying pygtk from this buk and hv done the pygtk widgets and am doing cairo ...so if u have any problem in widgets u can ask me..it wud help me as well...:p

one or two pages are missing because i made the pdf from html...but  i am also giving u the link..

[http://svn.majorsilence.com/pygtknotebook/trunk/pygtk-notebook-latest.html](http://svn.majorsilence.com/pygtknotebook/trunk/pygtk-notebook-latest.html)

---

### Post by tubunu on 2011-06-30
Wow, that is a great resource! I think this will answer a lot of my questions. Thanks again! **((Bear hug))** :D

---

### Post by tubunu on 2011-07-02
> **tubunu said:**
> I've come up against another stumbling block... How do I add a new window, but this time from a file I created in Glade? I'd like it to pop up with the UI I created in glade rather than code everything by hand.

Well after spending two days on trying to figure this out, browsing through countless tutorials/web pages/whatnot, I have finally discovered how to do it. It's so plain simple that I'm chuckling at myself right now. It's enough to add 'ui' in front of the window you're trying to show. I'm giving the code so that any other beginner into GTK/python/glade may also benefit from that. 

```
 def on_button1_clicked(self, widget, data=None):
        self.[COLOR="Magenta"]ui.window1[/COLOR].show()
```

where window1 is the new window you create in Glade's dock inspector.

---

