---
title: "PyGTK + Glade ? Scrollbar for Textview"
date: 2010-01-10
forum: Programming Talk
---

### Post by qalimas on 2010-01-10
I am new to Python and Glade, and am learning by writting a board game.

I am building it with network support and no AI.  Therefore I am putting in a 'chat box' that will allow players to talk and show game information as it happens (example: "Player 1 rolled a 3").

The problem I am having is I made a textview object, and I can put text in just fine, everything works, almost.  I have set it so the user can't edit it.  The problem is I need to at the least make the textbox auto-scroll when new text is inserted into it.  I'd like to also tie a scrollbar to that.


Current function that inserts text into chat box:
```
def textentryChat(self, widget):
	#Need to make chat box auto-scroll
	global counterI
	chatview = self.wTree.get_widget("textviewChat")
	textentry = self.wTree.get_widget("textentryChat")
	
	text = textentry.get_text()

	if len(text) > 0:
		if text[0] == "/":
			#Remove the /, then bust it into an array for scanning
			command = text[1:].split(" ")
			
			#Run through our ocmmands for testing
			#Temp function to move a token
			if command[0] == "move":
				#Make sure we are in-bounds
				if int(command[2]) > 26:
					command[2] = 26
				if int(command[3]) > 16:
					command[3] = 16

				#Move the token
				self.wTree.get_widget("layout2").move(self.wTree.get_widget("token" + str(command[1])), (int(command[2])*24), (int(command[3])*24))

			textentry.set_text("")
		else:
			testvarName = "Player"
			chatview.get_buffer().insert(chatview.get_buffer().get_end_iter(), str(counterI) + " " + testvarName + ": " + textentry.get_text() + "\n")
			textentry.set_text("")
		

	counterI = counterI + 1
# end textentryChat
```



Edit: Solved it.
```
self.wTree.get_widget("textviewChat").scroll_to_iter(self.wTree.get_widget("textviewChat").get_buffer().get_end_iter(), within_margin=0.1, use_align=False, xalign=0.5, yalign=0.5)
```

---

### Post by marlos.maur on 2011-05-31
I found a better way:

buffer = self.MyTextView.get_buffer()
iter = buffer.get_end_iter()
mark = buffer.create_mark("end", iter, False)
self.MyTextView.scroll_to_mark(mark, 0.05, True, 0.0, 1.0)
buffer.place_cursor(iter)

...

---

