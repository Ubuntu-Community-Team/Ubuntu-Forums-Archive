---
title: "GTK2 Data outside visible Window"
date: 2009-06-27
forum: Programming Talk
---

### Post by bcz on 2009-06-27
Hi All

Am porting to 1024x600 netbook.

I display widget at bottom of window, say 800 pixels and wait for input.

However due to screen size, no dialog is visible to the user unless they scroll down the window.

Is it possible to force the window to scroll so that the entry widget is visible to the user?

In this case I display the date at 800 and want confirmation that the date is OK.  Reasonably both the date and confirmation dialogue would display without the user having to scroll down to see what interaction was expected

Anyone point me to any documentation

Rgds Bill C

---

### Post by unutbu on 2009-06-27
If you are using a gtk.TextView, you could use something like this:

[php]
def scroll_to_end(self):
    mark=self.buffer.create_mark('end',self.buffer.get_end_iter())
    self.textview.scroll_to_mark(mark,0)
    self.buffer.delete_mark_by_name('end')
[/php]

This makes the TextView display the end of the TextView buffer.

---

### Post by bcz on 2009-06-27
Thanks for points on treeview.  The idea might help me.

Main window has scrollbars.  The scrollable window contains a box packed with various widgets.  I have a general problem, but will detail the case of getting the date.

I open a window to get the date as 260609.  I display the reformatted date 26th June 2009 and request confirmation.  (This is not Y3000 OK, but not an immediate issue)

On a 1024x600 screen, I display the date at say 800 pixels down.  I then ask confirmation.  No problem here

But the date at 800 pixels is not visible, so the user has to know to scroll down before system becomes intuitive to use.  Far better if I could force the date widget into the viewable window.

Is there a way to do this.

Rgds Bill C

---

### Post by unutbu on 2009-06-27
In the python-gtk2-tutorial package, there is a demo program called layout.py.

I recommend you take a look at and run this demo program.
It uses a gtk.Table widget with VScrollbar and HScrollbar attached.
Each Scrollbar has an associated gtk.Adjustment widget which controls how the Scrollbar behaves. 

When you press the buttons, the position of the buttons jump around, sometimes out of view. 
The following code modifies layout.py so that when you click a button, the scrollbars jump to show you when the button has moved to.

[PHP]
    def ButtonClicked(self, button):
        # move the button
        x=random.randint(0,500)
        y=random.randint(0,500)
        self.layout.move(button, x, y)
        self.vAdjust.set_value(y)
        self.vAdjust.value_changed()
        self.hAdjust.set_value(x)
        self.hAdjust.value_changed()[/PHP]

Maybe something like this could help you with your situation.

---

