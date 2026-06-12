---
title: "PyQt Programming Questions"
date: 2012-08-22
forum: Programming Talk
---

### Post by ngrieb on 2012-08-22
I have been developing a number of applications at work in PyQt, and am almost ready to release them to people for normal use, but have two issues that I need to resolve before I finish them. 

First I am having an issue opening a subwindow of class QWidget in the main loop modally (the window opens and does what it is supposed to, but the main loop exits the function called by the slot before the user has time to input things). The result is that the update/refresh action doesn't happen until the next time the signal is given to enter that function. I realize that the main loop is continuing in the background and that the update function is executed before any data is given to print onto the main window. My question is how do I stop/pause the main loop while this subwindow widget is running (I have seen this called a modal window; correct my jargon if I am wrong)?

The second problem I am having is that I have been developing under a Windows environment, and need to compile the code into an exe, msi, or bin. I have grabbed py2exe, but have absolutely no idea how to compile correctly (the tutorial given is worthless to me...). Can anyone give me an example of the correct way to compile using py2exe or another compiler like add-on?

Thanks

---

### Post by spjackson on 2012-08-23
The QDialog class has modal capabilities. Why are you using QWidget instead of QDialog? I don't know anything about py2exe.

---

### Post by ngrieb on 2012-08-24
I have read something about this, but didn't use it because it seemed as though I would have to customize my QDialog window. Customization seemed a bit too tedious for the simplicity of what I had in mind, and I couldn't quite figure out what was going on. I suppose that I can look into it in more detail. Perhaps you can help a bit:

I need a QLineEdit() slot, and 2 customized QPushButtons: one that leads to a QFileDialog.getOpenFileName() call, and the other that returns the data of the two above widgets.

Just out of curiosity, is there a way to cause a pause in the main loop, and then resume it when the QWidget window closes?

Thanks.

---

### Post by spjackson on 2012-08-24
> **ngrieb said:**
> I have read something about this, but didn't use it because it seemed as though I would have to customize my QDialog window. Customization seemed a bit too tedious for the simplicity of what I had in mind, and I couldn't quite figure out what was going on. I suppose that I can look into it in more detail. Perhaps you can help a bit:

I need a QLineEdit() slot, and 2 customized QPushButtons: one that leads to a QFileDialog.getOpenFileName() call, and the other that returns the data of the two above widgets.

It's not hard to make an example like that. Are you using designer to layout your gui or are you creating the widgets in code? Do you want to post what you've done?

> 
Just out of curiosity, is there a way to cause a pause in the main loop, and then resume it when the QWidget window closes?
You can't do that easily no. If the main loop is paused, then there's nothing to process events. So your QWidget can't draw itself or respond to clicks. QDialog.exec() does pause the main event loop, but QDialog has its own event loop to process the events. It seems to me that you would need to effectively reimplement most of QDialog in your QWdiget. Doable but crazy in C++, and probably not even doable in python.

---

### Post by spjackson on 2012-08-25
> **ngrieb said:**
> I need a QLineEdit() slot, and 2 customized QPushButtons: one that leads to a QFileDialog.getOpenFileName() call, and the other that returns the data of the two above widgets.

I believe that the attached example does what you describe.

---

