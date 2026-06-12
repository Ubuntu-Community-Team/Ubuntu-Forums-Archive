---
title: "Hopefully easy Glade question re GtkEntryBuffer"
date: 2009-11-12
forum: Programming Talk
---

### Post by M4rotku on 2009-11-12
Hey guys,

I'm trying to build an interface with glade and it's my first time starting a GtkBuilder from scratch.  I am finding the buffer things rather confusing.  I have it down for the most part except for this one.  I have a GtkEntry and it needs a GtkEntryBuffer and I know this makes me sound like an idiot, but I can't find the GtkEntryBuffer anywhere in the menu.  I tried using a GtkTextBuffer for it, but I couldn't load it.  Can anyone tell me where to look in the menu.  I think I've gone through all of the options I've been able to find.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-11-13
bump, still can't find how I'm supposed to do it.

---

### Post by M4rotku on 2009-11-15
bump

---

### Post by M4rotku on 2009-11-17
Well, I thought that this would be easy.  If it´s something really obvious, don´t be shy to point it out.

---

### Post by G|N| on 2009-11-17
What language are you using?
I looked on the web and i did not find a lot of information about a GtkEntryBuffer. If you only want to show or get text in an entry, there is no need for a GtkEntryBuffer.

I also think that if you really need it, you have to add it in your code and not in your glade file.

Show us your code or tell us what you are trying to do.

---

### Post by M4rotku on 2009-11-17
I am using python, but this is still all within the glade file.  I am using GTKbuilder for the glade type.  I am going to include snapshots that will hopefully show what is going on.  I can´t really explain it better in words, because I´ve never used gtkbuilder before.

The first screenshot shows the whole glade window with the buffer option and the button I pressed to get to the second screenshot.

All I want to do is put a default string in the GtkEntry.

---

### Post by M4rotku on 2009-11-19
bump

---

### Post by M4rotku on 2009-11-23
bump, still lost and confused.

---

### Post by kknd on 2009-11-23
GTK+ 2.18 separated the GtkEntry into GtkEntry and GtkEntryBuffer, but Glade doesn't support this yet. You will have to wait an update, or write the GtkBuilder XML by hand.

P.S: seems that you can still use GtkEntry with the 'default' buffer (just ignore the buffer property), having the same behavior of older versions.

---

### Post by M4rotku on 2009-11-23
if i start the project over and at the beginning select to use an older version of gtk, then will i be able to avoid this problem?

---

### Post by M4rotku on 2009-11-24
I just checked and I was using GTK 2.16, not 2.18?  does this make a difference or will reverting back to an older version still solve the problem?

I think I may have checked in the wrong place though.  I checked in the ´Preferences´ in Glade.  If this is not the correct place to check/change it, then please let me know.

Much thanks,
M4rotku

---

### Post by ib.lundgren on 2009-11-24
Haven't used gtkBuilder much either but in order to see what the fuss was about I opened up glade (v.3.6.7 Karmic), created a window and put a label, button and a entry in it. Then used this code to try it out:

[PHP]import gtk

class SimpleGtk:
	
	def __init__(self):
		self.builder = gtk.Builder()
		self.builder.add_from_file("/home/ib/Desktop/Test/test.glade") 
		self.builder.get_object("window1").show()
		self.builder.connect_signals(self)
		
	def on_button_clicked(self, args):
		text = self.builder.get_object("entry1").get_text()
		self.builder.get_object("label1").set_text(text)
		
	def on_window_destroy(self, args):
		gtk.main_quit()
	
	
if __name__ == "__main__":
	simple = SimpleGtk()
	gtk.main()[/PHP]

Which simply allows you to type some text, click the button and have the label say what you wrote. Nowhere in glade or elsewhere did I supply a specific buffer for the entry box.

---

### Post by M4rotku on 2009-11-25
I think I was being prompted to use the buffer within the glade program so that I could have a default value for the text entry box.

---

