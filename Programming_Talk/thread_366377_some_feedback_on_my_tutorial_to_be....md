---
title: "some feedback on my tutorial to be..."
date: 2007-02-20
forum: Programming Talk
---

### Post by Choad on 2007-02-20
ok i am making a little "bridge" tutorial for people that have started learning pyGTK/glade and want to move on to more complex programs with multiple source files and whatnot

but before i bother writing anything to explain what does what, would someone with a bit more experience than me review my programs and tell me if i have figured stuff out correctly. no point in teaching bad habits... plus if anything im doing is bad practice then i need to know lol

anyway, have a look. they're pretty obvious, shouldnt need any explanation

---

### Post by Choad on 2007-02-21
38 views and no one has anything to say?

---

### Post by Unisted on 2007-02-21
I viewed because I thought I might be able to comment upon the tutorial but I'm not learning pyGTK/glade so I can't!

Maybe repost with learning pyGTK/glade tutorial? or amend the title to this thread (if you can)?

---

### Post by po0f on 2007-02-21
Choad,

So, uhh, where's the tutorial?  All that was in the tarball was a bunch of source files.  They weren't even commented.

Now, if it was the actual source files you wanted comments on, you need to comment your source.  *Especially* if they are components of a tutorial.  And those "#____________________ Import _________________________" and "#____________________ /Import _________________________" style comments are a total waste of space and, IMO, detract from (not enhance) the layout/flow of your program.  If you really want to comment where you do all your imports, a simple "# import modules" or something would suffice.  I always thought the "import" keyword gave away what you were doing, but that's just me.  ;)

And the preferred way of importing modules is standard modules first (anything that came with the default distribution of Python), third party modules (PyGTK, database adapters, whatever) second, and *your* modules last.

That was based on opening up one of the files.

---

### Post by Choad on 2007-02-21
thats the point, i havent written the tutorial yet. thus "tutorial to be"

i was just wondering about the programs themselves. ill take in to account what you've said

---

### Post by Choad on 2007-02-24
ok, well so far i have "modules imported in the wrong order"

can i assume the rest of the source is up to scratch then? its "tutorial" 3 that im most interested in peoples opinions on.

---

### Post by jvc26 on 2007-02-24
I'd second the long comments are a bit messy and don't really help you that much: Just a simple:
```

#Imports

try:
	import pygtk
	pygtk.require("2.0")
except:
	pass
try:
	import gtk
except:
	sys.exit(1)

# Onscreen Keyboard Class
# this class creates an on screen keyboard to enter text with. to pack it in
# a gtk container, use it's vBox widget. it requires a widget with a get_text 
# and set_text method to be passed to it. it uses this widget to write in.

```
for instance looks a bit neater in my opinion - you don't need the big _______import__________ and _______/import_________
Il

---

### Post by Choad on 2007-02-24
enough about the comment style lol. i like them, because when you have a big source file with lots of classes its nice to be able to see what class is what, even from the end of the class code, without scrolling up to see it at the top. but anyway, ill remove them, due to popular demand, but would like some feedback on the code side of things if its possible

---

### Post by Choad on 2007-02-24
i told a lie. i kept it in, but refined it somewhat

```

# <[ Imports ]>
try:
	import pygtk
	pygtk.require("2.0")
except:
	pass
try:
	import gtk
except:
	sys.exit(1)
# <[ /Imports ]>

# <[ On Screen Keyboard ]>
#
# this class creates an on screen keyboard to enter text with. to pack it in
# a gtk container, use it's vBox widget. it requires a widget with a get_text 
# and set_text method to be passed to it. it uses this widget to write in.

class OnScreenKeyboard:

<snip>
		
# <[ /On Screen Keyboard ]>

```

still serves the same purpose but its less obtrusive. everyones a winner

---

### Post by jvc26 on 2007-02-25
Thats not too bad :) Prefer it to the old way anyhow!
Il

---

### Post by Choad on 2007-02-25
cool. i think ill start writing the tutorial soon. i have started a different project now tho... was using windows and remembered how good minesweeper is. must make a clone. (i realise there are probably a half dozen minesweeper clones already available but w/eva)

---

