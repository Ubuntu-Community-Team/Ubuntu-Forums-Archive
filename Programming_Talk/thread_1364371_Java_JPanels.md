---
title: "Java JPanels"
date: 2009-12-25
forum: Programming Talk
---

### Post by JayKay3000 on 2009-12-25
Hi. I'm having some problems with JPanels.

I have created a menu with buttons with a layout manager but I am unsure how to load different parts of the program using the menu.

I am used to making web pages where clicking a menu item loads a different page.

So how do you initialise different JPanels from a menu? Is this the way it works or are all panels loaded and simply hidden till needed?

And how would I load a different part of my program from the menu?

I've found out how to do loads of other things for the program I am making but this part is never explained in the tutorials.

Thanks for any help or some pointers.

---

### Post by kahumba on 2009-12-26
What do JPanels have to do with a JMenu?
Have you read this:
[http://java.sun.com/docs/books/tutorial/uiswing/components/menu.html](http://java.sun.com/docs/books/tutorial/uiswing/components/menu.html)
The logic for creating a desktop Java GUI is (very) different from a web-based approach.
Next time for a more qualitative answer consider posting your source code.

---

### Post by LeifAndersen on 2009-12-26
I'm also unsure about what you want.  So this may be completely useless to you.

But perhaps you could load each individual part in a new thread.  At the start of each new thread, you could add your new jpanel, and then make sure to ste the visibility to true.

---

### Post by Zugzwang on 2009-12-26
@OP: You can still use the approach you know from website making. Just create a class for each Panel you might want to display, deriving from JPanel (if you are using Netbeans: You can also use the GUI builder for designing such panels).

Then you add a blank JPanel to the window where you want it to be. Store the current Panel in some JPanel variable. Now when some menu item is selected, remove the panel from the window, instantiate the new one and add it in the same way to the window layout as you added the blank panel in the first instance. You might need to call update() or something like that via invokeLater afterwards.

The hiding technique you sketched can also be used, especially if you want the GUI elements to retain their values when a panel is not currently being displayed.

---

### Post by quip on 2009-12-26
> **JayKay3000 said:**
> Hi. I'm having some problems with JPanels.

I have created a menu with buttons with a layout manager but I am unsure how to load different parts of the program using the menu.

I am used to making web pages where clicking a menu item loads a different page.

So how do you initialise different JPanels from a menu? Is this the way it works or are all panels loaded and simply hidden till needed?

And how would I load a different part of my program from the menu?

I've found out how to do loads of other things for the program I am making but this part is never explained in the tutorials.

Thanks for any help or some pointers.

As others, I am a little unsure about your query, but you can always make things visible/invisible or focusable/unfocusable with methods derived from JComponent (from which JPanel is derived), like setVisible(bool) and others.

Also, you can write your code in a manner that does not create the GUI component until it is needed, and then does some type of hiding afterwards.

---

### Post by JayKay3000 on 2009-12-26
well. when i meant menu i did not mean with file, etc.

I meant something like the following:

I have a panel with:

Item 1

Item 2

Item 3

Exit


So if you click 'item 1' then i'm not totally sure how to 'load' another panel.

Or imagine if I have a Log in panel with a password then how do you assign the 'ok button' to then load the panel with 'item 1, item 2, item 3' on it.

I'm currently hard coding this.

Any ideas? Sample code or link to something. I've googled with no luck.

---

### Post by LeifAndersen on 2009-12-26
MMm...looks like you need a mouse listener object.  There are some nice APIs for that, look for the mouselistener class.  Also, this sample may go down in a few months, but this may help: [http://eng.utah.edu/~cs1410/Examples/CS%201410%20and%20CS%201021%20-%20Fall%202009/src/example18/](http://eng.utah.edu/~cs1410/Examples/CS%201410%20and%20CS%201021%20-%20Fall%202009/src/example18/)

---

### Post by JayKay3000 on 2009-12-29
Thanks for the link. That was a little simplistic. I've found an example I made a few years ago using tabs so am investigating that to use the login to hide the tabs till the correct password is put in and then show the tabs and allow users to do the things they want.

I'm not even sure if what i'm trying to do is even possible. But there is probably some simple method i'm missing. I've never really used swing much without being within the confines of applications that require only 1 'screen'

Menus i've written in this style before have been comman line driven.

Anywho. Thanks for the help :lolflag: but i think i'll plod on under my own steam.

Also going to try out NetBeans to see if it can help speed up the coding process. I've never used it but any tool that can be of some use could be a good thing.

---

