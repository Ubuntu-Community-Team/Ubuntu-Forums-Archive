---
title: "some more pythony questions"
date: 2007-02-12
forum: Programming Talk
---

### Post by Choad on 2007-02-12
im really beggining to love this language

anyhow... question time

if i have a list

weights ("kilos", "grams", "pounds", "ounces")

and so on. and i use it as a list in a function. but what if i wanted to add another dimension to the array, so each weight metric could have a value associated with it (this is for a conversion app, if you hadnt guessed)

how would i go about this, and how would i make sure its still useable by the function that treats it as a string list?

```
def setModelFromList (cb, items):
	""" Setup a ComboBox or ComboBoxEntry based on a list of strings.
	Note: This function was taken from 
	http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq16.008.htp """          
	model = gtk.ListStore(str)
	for i in items:
		model.append([i])
	cb.set_model(model)
	if type(cb) == gtk.ComboBoxEntry:
		cb.set_text_column(0)
	elif type(cb) == gtk.ComboBox:
		cell = gtk.CellRendererText()
		cb.pack_start(cell, True)
		cb.add_attribute(cell, 'text', 0)
```

that be the function in which its used. the list "weights" is passed to this as it's second argument

---

### Post by pmasiar on 2007-02-12
> **Choad said:**
> i wanted to add another dimension to the array, so each weight metric could have a value associated with it 

maybe you are looking for a dictionary. it has keys and values. You can still get keys out: 

dd = dict(kg=1, pounds=2, ...)
dd.keys()

values also can be lists or tuples (instead of plan scalars). But then you are very close to defining objects...

HTH

---

### Post by Choad on 2007-02-13
thanks for the respone. can you get the string "kg" out of that tho?

ill have a google for it anyway

oh, never mind. i see .keys() returns a list of them!

---

### Post by Choad on 2007-02-13
ok so i made it in to a dictionary, but i need to be able to store a record of which dictionary it is that im using. i have a weights dictionary, a lengths dictionary etc. i need to be able to say 

current_dictionary["key"]


or... i just had a thought

i could leave weights, lengths etc. as plain lists and then have a conversion dictionary that conatins everything

yeah that sounds good. tho it does mean its a little wasteful in the memory department.

edit: ok ignore all that.

how do i make it so that when i update my combo box entry, that whatever was previously selected is erased, or at least set to the first option in the combo box or something

---

### Post by dwblas on 2007-02-14
Hopefully you figured it out, that you only use one dictionary as they all (weights, length, etc) have different names/keys.  And sorry, I use Tkinter, not GTK, but it should have something similar to Tkinter's set function.

---

