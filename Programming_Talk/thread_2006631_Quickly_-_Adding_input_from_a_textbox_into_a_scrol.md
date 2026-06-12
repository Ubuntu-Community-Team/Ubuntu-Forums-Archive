---
title: "Quickly - Adding input from a textbox into a scrolling list"
date: 2012-06-19
forum: Programming Talk
---

### Post by AllRadioisDead on 2012-06-19
Hi there, I only have a little bit of programming experience and I'm trying to use python to create an python app.

I'm getting stuck though.

I'm trying to follow this tutorial: 
[http://theravingrick.blogspot.ca/2011/01/quickly-tutorial-for-natty-diy-media.html](http://theravingrick.blogspot.ca/2011/01/quickly-tutorial-for-natty-diy-media.html)

But instead of using a prompt to open a directory and scan for media files, I'd simply like to create a prompt for the user to enter a string, and then add that to a scrolling list.




```

        # Code for other initialization actions should be added here.

#Add new Text button
    def on_addbutton_clicked(self, widget, data=None):
#prompt user for text
        response, text = prompts.string("Enter Text", "Please enter some text:", "Here!")

   #remove any children in scrolled window
        for c in self.ui.scrollinglist.get_children():
            self.ui.scrolling.remove(c)


#not sure what goes here.

        self.ui.scrollinglist.add(text)


        



```


Any help would be appreciated. Sorry if my example is really poor, I've been messing around with this all night.
In the tutorial, the dev used a dictionary list to store all of the file locations and add them to the scrolling list.

I just need to add text to the list, I tried modifying his example but it didn't work. The quickly reference in the python index of modules is broken and I'm having a really hard time finding any other documentation.

Thanks!

---

### Post by Jacobonbuntu on 2012-06-19
> **AllRadioisDead said:**
> Hi there, I only have a little bit of programming experience and I'm trying to use python to create an python app.

I'm getting stuck though.

I'm trying to follow this tutorial: 
[http://theravingrick.blogspot.ca/2011/01/quickly-tutorial-for-natty-diy-media.html](http://theravingrick.blogspot.ca/2011/01/quickly-tutorial-for-natty-diy-media.html)

But instead of using a prompt to open a directory and scan for media files, I'd simply like to create a prompt for the user to enter a string, and then add that to a scrolling list.




```

        # Code for other initialization actions should be added here.

#Add new Text button
    def on_addbutton_clicked(self, widget, data=None):
#prompt user for text
        response, text = prompts.string("Enter Text", "Please enter some text:", "Here!")

   #remove any children in scrolled window
        for c in self.ui.scrollinglist.get_children():
            self.ui.scrolling.remove(c)


#not sure what goes here.

        self.ui.scrollinglist.add(text)


        



```
Any help would be appreciated. Sorry if my example is really poor, I've been messing around with this all night.
In the tutorial, the dev used a dictionary list to store all of the file locations and add them to the scrolling list.

I just need to add text to the list, I tried modifying his example but it didn't work. The quickly reference in the python index of modules is broken and I'm having a really hard time finding any other documentation.

Thanks!

I am not sure I understand what you mean...
is it that you want the user to be able to enter text in an entry field, accompanied by a button to add it to a listbox?

I am not too experienced myself, but on this site, so far, I found all answers to my questions and more. It is pretty good; when I google for answers, I always pick the hits from this site first...
[http://stackoverflow.com/](http://stackoverflow.com/)

---

### Post by AllRadioisDead on 2012-06-19
> **Jacobonbuntu said:**
> I am not sure I understand what you mean...
is it that you want the user to be able to enter text in an entry field, accompanied by a button to add it to a listbox?

I am not too experienced myself, but on this site, so far, I found all answers to my questions and more. It is pretty good; when I google for answers, I always pick the hits from this site first...
[http://stackoverflow.com/](http://stackoverflow.com/)

Thanks.

In the tutorial above, the author uses a prompt to ask the user for a directory. Using a for loop, the program then scans the directory for valid media files, adds them to a list, and then adds the list to the scrollable widget.


I would like to do something similar. Instead of adding a list of media files, I would like to prompt the user to enter a string, and then add that string to a list. Does that make sense? Sorry if I'm doing a poor job of explaining it.

Thanks for the link.

---

### Post by Jacobonbuntu on 2012-06-19
> **AllRadioisDead said:**
> Thanks.

In the tutorial above, the author uses a prompt to ask the user for a directory. Using a for loop, the program then scans the directory for valid media files, adds them to a list, and then adds the list to the scrollable widget.


I would like to do something similar. Instead of adding a list of media files, I would like to prompt the user to enter a string, and then add that string to a list. Does that make sense? Sorry if I'm doing a poor job of explaining it.

Thanks for the link.

Ah, I see...
In python/tkinter, this would be not too difficult, the code in the example is not familiar to me.....

---

### Post by AllRadioisDead on 2012-06-19
> **Jacobonbuntu said:**
> Ah, I see...
In python/tkinter, this would be not too difficult, the code in the example is not familiar to me.....

Thanks, I guess I'll have to look into doing it with standard pyGTK. There isn't very much documentation on quickly unfortunately.

---

