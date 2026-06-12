---
title: "My code's not working?!? Python help."
date: 2007-01-09
forum: Programming Talk
---

### Post by RussianVodka on 2007-01-09
Python with Tkinter. Copied it straight out of the book. Don't think I made any typos. For some reason it's not recognizing the functions. And "app = Application(root)" doesn't work either.

I don't see anything wrong with it.

Here is the code, I bolded the places that get errors:
```

#Movie Chooser
#Demonstrates check buttons

from Tkinter import *

class Application(Frame):
	""" GUI Application for favorite movie types. """
	def __init__(self, master):
		Frame.__init__(self, master)
		self.grid()
		**self.create_widgets()**
		
	def create_widgets(self):
		""" Create widgets for movie type choices. """
		#Create description label
		Label(self,
			text = "Choose your favorite movie types"
			).grid(row = 0, column = 0, sticky = W)
		
		#Create instruction label
		Label(self,
			text = "Select all that apply:"
			).grid(row = 1, column = 0, sticky = W)
			
		#Create Comedy check button
		self.likes_comedy = BooleanVar()
		Checkbutton(self,
			text = "Comedy",
			variable = self.likes_comedy,
			**command = self.update_text**
			).grid(row = 2, column = 0, sticky = W)
			
		#Create Drame check button
		self.likes_drama = BooleanVar()
		Checkbutton(self,
			text = "Drama",
			variable = self.likes_drama,
			**command = self.update_text**
			).grid(row = 3, column = 0, sticky = W)
		
		#Create Romance check button
		self.likes_romance = BooleanVar()
		Checkbutton(self,
			text = "Romance",
			variable = self.likes_romance,
			**command = self.update_text**
			).grid(row = 4, column = 0, sticky = W)
			
		#Create text field 
		self.results_txt = Text(self, width = 40, height = 5, warp = WORD)
		self.results_txt.grid(row = 5, column = 0, columnspan = 3)
		
		def update_text(self):
			""" Update text widget and display user's favorite movie types. """
			likes = ""
			
			if self.likes_comedy.get():
				likes += "You like comedic movies.\n"
			if self.likes_drama.get():
				likes += "You like comedic movies.\n"
			if self.likes_romance.get():
				likes += "You like romantic movies."
				
			self.results_txt.delete(0.0, END)
			self.results_txt.insert(0.0, likes)

#Main
root = Tk()
root.title("Movie Chooser")
**app = Application(root)**
root.mainloop()

```


And here is the messages I get when I run it:
> 
Traceback (most recent call last):
  File "movie_chooser.py", line 70, in ?
    app = Application(root)
  File "movie_chooser.py", line 11, in __init__
    self.create_widgets()
  File "movie_chooser.py", line 30, in create_widgets
    command = self.update_text
AttributeError: Application instance has no attribute 'update_text'


---

### Post by pmasiar on 2007-01-09
maybe you should use command = self.update_text() -- adding () -- update_text is a method, not attribute?

---

### Post by RussianVodka on 2007-01-09
> **pmasiar said:**
> maybe you should use command = self.update_text() -- adding () -- update_text is a method, not attribute?

Tried it, didn't change anything.

---

### Post by duff on 2007-01-09
def update_text is indented too far

---

### Post by pmasiar on 2007-01-09
duff: Good eye - this is exactly why good IDE is important with Python. i was too lazy to copy - paste it.

RussianVodka: update_text() is defined as internal function inside method create_widgets(), not as method of the Application class

---

### Post by RussianVodka on 2007-01-09
> **duff said:**
> def update_text is indented too far

Ah! I see now!

This is why programming languages need brackets.

---

### Post by pmasiar on 2007-01-09
wrong. thats why you need decent programmers editor with capabilities beyound notepad. Try SPE.

---

### Post by RussianVodka on 2007-01-09
> **pmasiar said:**
> wrong. thats why you need decent programmers editor with capabilities beyound notepad. Try SPE.

I'm using Geany.

Also, the program still isn't working. But I'll try to figure it out tomorrow.

---

### Post by pmasiar on 2007-01-09
SPE shows indent guides -- so you can see wrong place immediately. But of course you are free to shoot yourself to your own foot - that way you learn more than by just mindless copy-pasting tutorial code :evil:

---

### Post by ghostdog74 on 2007-01-10
this is working:

```

from Tkinter import *
class Application(Frame):
    """ GUI Application for favorite movie types. """
    def __init__(self, master):
        Frame.__init__(self, master)
        self.grid()
        self.create_widgets()


    def create_widgets(self):
        """ Create widgets for movie type choices. """
        # create description label
        Label(self,
              text = "Choose your favorite movie types"
              ).grid(row = 0, column = 0, sticky = W)


        # create instruction label
        Label(self,
               text = "Select all that apply:"
               ).grid(row = 1, column = 0, sticky = W)

        # create Comedy check button
        self.likes_comedy = BooleanVar()


        Checkbutton(self,
                     text = "Comedy",
                     variable = self.likes_comedy,
                     command = self.update_text
                     ).grid(row = 2, column = 0, sticky = W)

        # create Drama check button
        self.likes_drama = BooleanVar()
        Checkbutton(self,
                     text = "Drama",
                     variable = self.likes_drama,
                     command = self.update_text
                     ).grid(row = 3, column = 0, sticky = W)

        # create Romance check button
        self.likes_romance = BooleanVar()
        Checkbutton(self,
                     text = "Romance",
                     variable = self.likes_romance,
                     command = self.update_text
                     ).grid(row = 4, column = 0, sticky = W)


        # create text field to display results
        self.results_txt = Text(self, width = 40, height = 5, wrap = WORD)
        self.results_txt.grid(row = 5, column = 0, columnspan = 3)


    def update_text(self):
       """ Update text widget and display user's favorite movie types. """
       likes = ""

       if self.likes_comedy.get():
           likes += "You like comedic movies.\n"

       if self.likes_drama.get():
           likes += "You like dramatic movies.\n"

       if self.likes_romance.get():
           likes += "You like romantic movies."
       self.results_txt.delete(0.0, END)
       self.results_txt.insert(0.0, likes)


# main
root = Tk()
root.title("Movie Chooser")
app = Application(root)
root.mainloop()


```

---

