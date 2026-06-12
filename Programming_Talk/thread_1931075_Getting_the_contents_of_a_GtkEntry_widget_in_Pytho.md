---
title: "Getting the contents of a GtkEntry widget in Python"
date: 2012-02-24
forum: Programming Talk
---

### Post by papillion on 2012-02-24
Hello Everyone,

So I've designed a UI in Glade and have loaded it using Python. I've connected the signals so that I can make things happen and, so far, everything is working fine. Now, I find myself needing to access the contents of a GtkEntry widget called txtSearchTerm when the btnPerformSearch button is clicked and I can't figure out how.

In Glade, I've said to call the on_btnPerformSearch_clicked() method whenever the button is clicked. When the button is clicked, the event is fired and the method is called. The method SHOULD check if the GtkEntry widget contains any text. Here is the code of the method:

def on_btnPerformSearch_clicked(set, data=None):
    if self.txtSearchTerm.text == "":
        print "No text to search for"
    else:
        print "I will search for this text"

When the method is called, I am told that the self object doesn't have anything called txtSearchTerm. If I leave the 'self' part off, nothing happens at all.  I've made sure the method is called by replacing all conditions with a simple

print "Button has been clicked"

and it prints out fine. I just don't know how to access the contents of a GtkEntry widget.

Can anyone help?

Thanks,
Anthony

---

### Post by cgroza on 2012-02-24
Did you copy and pasted this code from somewhere?
In that function, there is no single line that accesses a GtkEntry in order to retrieve a value.

You get that error because there is no variable self in that scope.
I don't really know Gtk, but I think the string you are looking for can be retrieved through that "data" argument.
Maybe you are confused about what a function and a class is.

And please use code tags in order to preserve the indentation, which is a crucial thing with python.

---

### Post by papillion on 2012-02-24
No, the code is my own creation and I understand the difference between a class and a function. This function is a member of my class.

The code that references the GtkEntry is the if statement. The GtkEntry widget is called txtSearchTerm. According to the docs, it looks like I should be able to access the text in the widget using the .text() property. But that doesn't work.

As for adding the 'self' part to the code, it was just trying because doing it without self yielded nothing either. I don't think the data parameter has anything to do with it because that would have to do with the data being passed from the calling object.  

I'm totally confused and befuddled by this!

Thanks for helping!

Anthony

---

