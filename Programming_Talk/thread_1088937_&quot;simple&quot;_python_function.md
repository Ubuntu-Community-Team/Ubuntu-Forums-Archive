---
title: "&quot;simple&quot; python function"
date: 2009-03-06
forum: Programming Talk
---

### Post by Sandsound on 2009-03-06
Hi all

Still trying to learn a little Python and have been banging my head against the keyboard because of a simple problem.
I have a function in my code that I would like to call inside another function :

```
#!/usr/bin/python
# This app require gnome-python-extras

import sys, os, re, os.path, string, gtkmozembed, fileinput

try:  
	import pygtk  
	pygtk.require("2.0")  
except:  
	pass  
try:  
	import gtk  
	import gtk.glade  
except:  
	print("GTK Not Availible")
	sys.exit(1)

class buttons:

	wTree = None

	def __init__( self ):
		url = os.getcwd()
		self.wTree = gtk.glade.XML( "main.glade" )
		self.mozillaWidget = gtkmozembed.MozEmbed()
		self.wTree.get_widget("frame1").add(self.mozillaWidget)
		self.mozillaWidget.set_size_request(400,400)
		self.mozillaWidget.show()
		self.mozillaWidget.load_url('file:///'+ url + '/index.html')
		# Reload stylesheet
		text_style = self.wTree.get_widget("textview_style")
		file = open('style.css')
		string = file.read() 
		buffer = text_style.get_buffer()
		buffer.set_text(string)
		# Reload HTML-source
		text_html = self.wTree.get_widget("textview_html")
		file = open('index.html')
		string = file.read() 
		buffer = text_html.get_buffer()
		buffer.set_text(string)

		for line in fileinput.input("style.css",inplace =1):
			line = line.strip()
			if 'body' in line:
				print line 			
				s= line.split()
				body_bgcolor = str(s[3])
				body_font = str(s[6]) + ' ' + str((str(s[9]))[0:-2])
				body_font_color = str(s[12])
				body_bg_image = str(s[16])
				body_margin = int((str(s[20]))[0:-2])
				body_padding = int((str(s[23]))[0:-2])
				self.wTree.get_widget("colorbutton_body_bg").set_color(gtk.gdk.color_parse(body_bgcolor))
				self.wTree.get_widget("fontbutton_body").set_font_name(body_font)
				self.wTree.get_widget("colorbutton_body_text").set_color(gtk.gdk.color_parse(body_font_color))
				self.wTree.get_widget("filechooserbutton_body").set_filename(body_bg_image)
				self.wTree.get_widget("spinbutton_body_margin").set_value(body_margin)
				self.wTree.get_widget("spinbutton_body_padding").set_value(body_padding)
		fileinput.close
		
		dic = { 
			"on_colorbutton_body_bg_color_set" : self.body_bgcolor,
			"on_toolbutton_refresh_clicked" : self.reload,
			"on_windowMain_destroy" : self.quit,
		}
		
		self.wTree.signal_autoconnect( dic )

		gtk.main()

	def body_bgcolor(self, widget):
		for line in fileinput.input("style.css",inplace =1):
			line = line.strip()
			if not 'body' in line:
				print line 
			elif 'body' in line:
				red = hex(self.wTree.get_widget("colorbutton_body_bg").get_color().red >>8)[2:]
				green = hex(self.wTree.get_widget("colorbutton_body_bg").get_color().green >>8)[2:]
				blue = hex(self.wTree.get_widget("colorbutton_body_bg").get_color().blue >>8)[2:]   
				if len(red) == 1:
					red = '0' + red
				if len(green) == 1:
					green = '0' + green
				if len(blue) == 1:
					blue = '0' + blue
				line = line.strip()
				s= line.split()
				s[3] = '#' + red + green + blue
				line=" ".join(s)
				print line
		fileinput.close
#################
################# The part below should be a call to reload
################# But how do I call it ?
#################
		# Reload preview 
		self.mozillaWidget.reload(True)
		# Reload stylesheet
		text_style = self.wTree.get_widget("textview_style")
		file = open('style.css')
		string = file.read() 
		buffer = text_style.get_buffer()
		buffer.set_text(string)
		# Reload HTML-source
		text_html = self.wTree.get_widget("textview_html")
		file = open('index.html')
		string = file.read() 
		buffer = text_html.get_buffer()
		buffer.set_text(string)

	def reload(self, widget):
		# Reload preview 
		self.mozillaWidget.reload(True)
		# Reload stylesheet
		text_style = self.wTree.get_widget("textview_style")
		file = open('style.css')
		string = file.read() 
		buffer = text_style.get_buffer()
		buffer.set_text(string)
		# Reload HTML-source
		text_html = self.wTree.get_widget("textview_html")
		file = open('index.html')
		string = file.read() 
		buffer = text_html.get_buffer()
		buffer.set_text(string)

	def quit(self, widget):
		sys.exit(0)

if __name__ == "__main__":
    widgets = buttons()
    gtk.mainloop()
```

The code above is a part of my CSS-Editor, and the full source is available here : [http://www.sandgreen.dk/index.php?side=prog_python]("http://www.sandgreen.dk/index.php?side=prog_python") (scroll to the bottom).

I understand how to make a simple "print" function outside my class, but I think this have to be inside the class for it to use the things I have defined there ?

---

### Post by nvteighen on 2009-03-06
Hm... Well, you could pass an object to "print" as parameter and use the members from that instance.

---

### Post by Sandsound on 2009-03-06
> **nvteighen said:**
> Hm... Well, you could pass an object to "print" as parameter and use the members from that instance.

I'm sorry to say, but this makes absolutely no sense to me at all :-)

I made my first "hello world" for little over two months ago, so there's a lot of things I don't fully understand. Is it not possible to make a call to one of the functions inside the class ?
And if not... how do I "pass an object to print" ?

---

### Post by Sandsound on 2009-03-06
Maybe I'd better explain my question.

My program have several buttons, spinbuttons and so on, to change a stylesheet, every time I change a value, it should run the reload function

```
	def reload(self, widget):
		# Reload preview 
		self.mozillaWidget.reload(True)
		# Reload stylesheet
		text_style = self.wTree.get_widget("textview_style")
		file = open('style.css')
		string = file.read() 
		buffer = text_style.get_buffer()
		buffer.set_text(string)
		# Reload HTML-source
		text_html = self.wTree.get_widget("textview_html")
		file = open('index.html')
		string = file.read() 
		buffer = text_html.get_buffer()
		buffer.set_text(string)
```

The solution so far has been to add the lines after every function that changes a parameter in the stylesheet, but since I have now have more that 40 functions that does this, I have 40x11 lines (440 lines) that does the same as the reload function.

If I just call reload() it says that the global reload have not been defined.

---

### Post by imdano on 2009-03-06
Use self.reload() when you're doing it inside the class, not just reload().  I would also change the reload function definition to be
[php]	def reload(self, widget=None):[/php]So you don't have to pass a value for the widget parameter.

---

### Post by Sandsound on 2009-03-06
> **imdano said:**
> Use self.reload() when you're doing it inside the class, not just reload().  I would also change the reload function definition to be
[php]	def reload(self, widget=None):[/php]So you don't have to pass a value for the widget parameter.

Thank you \\:D/

EDIT: My program just went from being about 1400 to about 1000 lines :-)

---

### Post by nvteighen on 2009-03-07
Congratulations!

Anyway, what I was trying to tell you is that if you want to use stuff from an object outside its class definition, you just pass the object as a parameter.

```

class SomeClass:
    def __init__(self, init):
        self.value = init * 9

    def dosomething(self):
        return self.value - 2

def somefunction(instance):
    zzzz = instance.dosomething()
    if zzzz == 0:
        return 'a'
    else:
        return 'b'

myobject = SomeClass()
somevalue = somefunction(myobject)

```

Actually, the 'self' does exactly the same: to pass the instance to the function as a parameter. So, if you code a function outside the class that needs certain object, you just pass it and use it... and inside the class, you do the same but using 'self' because it's the object itself which needs to be passed. There are other several advantages on explicit self which I won't detail here unless you're interested.

---

### Post by Sandsound on 2009-03-07
> **nvteighen said:**
> Congratulations!

Anyway, what I was trying to tell you is that if you want to use stuff from an object outside its class definition, you just pass the object as a parameter.

```

class SomeClass:
    def __init__(self, init):
        self.value = init * 9

    def dosomething(self):
        return self.value - 2

def somefunction(instance):
    zzzz = instance.dosomething()
    if zzzz == 0:
        return 'a'
    else:
        return 'b'

myobject = SomeClass()
somevalue = somefunction(myobject)

```

Actually, the 'self' does exactly the same: to pass the instance to the function as a parameter. So, if you code a function outside the class that needs certain object, you just pass it and use it... and inside the class, you do the same but using 'self' because it's the object itself which needs to be passed. There are other several advantages on explicit self which I won't detail here unless you're interested.

Thanks for explaining it, it actually make sense to me now :-)

---

### Post by Can+~ on 2009-03-07
> **nvteighen said:**
> Actually, the 'self' does exactly the same: to pass the instance to the function as a parameter. So, if you code a function outside the class that needs certain object, you just pass it and use it... and inside the class, you do the same but using 'self' because it's the object itself which needs to be passed. There are other several advantages on explicit self which I won't detail here unless you're interested.

In fact, you can also call functions outside handling self as a reference to the current instance:

[PHP]class ClassA:
	x = 9
	
	# Function inside that calls an object with self.
	def calloutside(self):
		print "This is the inside."
		outside(self)
		
# Function outside that accepts an object.
def outside(obj):
	print "This is the outside."
	print obj.x

# Example

a = ClassA()
a.calloutside()

# Another example

outside(a)[/PHP]

self is pretty much a big arrow pointing to the instance of a class, whenever you need something declared in that scope (methods or variables), both self and the instance name point to the same instance.

---

