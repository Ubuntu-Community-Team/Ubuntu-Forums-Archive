---
title: "Python Example Program That Does This? Please?"
date: 2011-11-20
forum: Programming Talk
---

### Post by ammyt on 2011-11-20
Hello all,

I am really getting in love with python, and I've already launched a python app in a forum with really good feedback.

As part of updating it, I would love to add the option of editing a few values in a file, like:
*It shall read the values in a file say located in:
/home/user/foo
*foo contains:
OPTION_1: "12"
OPTION_2:"23"
OPTION_3:"57
*The GUI built should be like the sketch attached with:
A box to show the Option, i.e. 3 boxes named as Option 1 Option 2 Option 3
A box to show the current values in foo, i.e. 3 boxes showing 12 23 57
A box where the user submits a new value that should replace the current values.

I would appreciate if somebody provides me with a sample py script, or guide me in working my way out, it means the world to me.

I am using an N900, Maemo 5 OS which is Debian, all python modules exist.

---

### Post by ammyt on 2011-11-20
Of course, there should also be an Update button which triggers the script to that performs the replacing.

---

### Post by ammyt on 2011-11-20
Bump...

---

### Post by simeon87 on 2011-11-20
What options have you found so far to create a GUI application for your system?

---

### Post by ammyt on 2011-11-20
What exactly do you mean by "options"?

---

### Post by simeon87 on 2011-11-20
GUI toolkits or any other software that helps you to create an application for that system. Does Gtk work there? Or Qt? I know they can be run on Ubuntu but I don't know about Maemo OS 5 / N900.

---

### Post by ammyt on 2011-11-20
Of course!
gtk is the soul of maemo 5, and as I said before, all python modules (pygtk....) are included.
Qt 4.7 is perfect on the platform, but I truly didn't master that yet.

My first app was built bash, zenity, and python (pyGTKj

---

### Post by simeon87 on 2011-11-20
Well, I don't know an existing Python program that does that but it shouldn't be too difficult to write it yourself with Gtk. It's just a read / write function and some buttons to modify the data.

---

### Post by cgroza on 2011-11-20
If it is a administrator script, I really recommend Tk to build the GUI with because it is bundled with python and nobody needs to install an extra toolkit just to perform maintenance tasks.

---

### Post by pelle.k on 2011-11-22
Here is a quick and dirty (it really is, no error checking etc) qt4 (pyside) version in case you haven't found anything else to go by...
It doesn't do any checking to see if the values are numbers or whatever. It's up to you to suit it to your needs.

```
import sys, json
from PySide import QtGui, QtCore	
				
class InputBox(QtGui.QWidget):
	def __init__(self, dict_data, on_data_changed):
		super(InputBox, self).__init__()
		self.dict_data = dict_data
		self.on_data_changed = on_data_changed
		
		self.label_name = QtGui.QLabel(self.dict_data["LABEL"])
		self.label_value = QtGui.QLabel(self.dict_data["VALUE"])
		self.input_box = QtGui.QLineEdit()
		self.push_button = QtGui.QPushButton("Update %s" % (self.dict_data["LABEL"]))
		
		self.widget_layout = QtGui.QHBoxLayout(self)
		self.widget_layout.addWidget(self.label_name)
		self.widget_layout.addWidget(self.label_value)
		self.widget_layout.addWidget(self.input_box)
		self.widget_layout.addWidget(self.push_button)
		
		self.push_button.clicked.connect(self.push_button_clicked)
		self.input_box.returnPressed.connect(self.return_pressed)
		
	def return_pressed(self):
		self.update_value()
		
	def push_button_clicked(self):
		self.update_value()
		
	def update_value(self):
		text = self.input_box.text()
		self.dict_data["VALUE"] = text
		self.label_value.setText(text)
		self.input_box.clear()
		self.input_box.clearFocus()
		self.on_data_changed()
		
class MainWindow(QtGui.QWidget):
	def __init__(self):
		super(MainWindow, self).__init__()
		self.widget_layout = QtGui.QVBoxLayout(self)
		
		with open("config.json", mode="r") as data_file:
			try:
				self.application_data = json.load(data_file)
			except ValueError:
				# json data doesnt exist, create list with dicts manually
				# they will be dumped as json data to file, if changed
				self.application_data = [	{ "LABEL" : "value1", "VALUE" : "99"},
											{ "LABEL" : "value2", "VALUE" : "99"},
											{ "LABEL" : "value3", "VALUE" : "99"} ]
		
		for dict_data in self.application_data:
			self.widget_layout.addWidget(InputBox(dict_data, self.on_data_changed))
		
	def on_data_changed(self):
		with open("config.json", mode="w") as data_file:
			json.dump(self.application_data, data_file)
		
		
if __name__ == '__main__':
	application = QtGui.QApplication(sys.argv)
	mainwindow = MainWindow()
	mainwindow.show()
	sys.exit(application.exec_())
```

---

### Post by nvteighen on 2011-11-23
> **cgroza said:**
> If it is a administrator script, I really recommend Tk to build the GUI with because it is bundled with python and nobody needs to install an extra toolkit just to perform maintenance tasks.

That's only in the case of a GNU/Linux system that uses a more-or-less upstream version of Python. Remember that Python has no standard specs, so in theory someone could deploy a Tk-less Python platform.

As Maemo uses GTK+, GTK+ wouldn't entail installing any additional toolkit.

---

