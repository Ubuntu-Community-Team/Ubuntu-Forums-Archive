---
title: "Python GTK : updating a scolledwindow"
date: 2015-02-15
forum: Programming Talk
---

### Post by pickarooney on 2015-02-15
I'm writing a small app to help me learn Python and postgreSQL. For the first part, the user enters a string in an Entry Box on the main window. This string is passed to a function which looks up the string in a database and returns results. These results are assigned to a ListView and from there to a TreeView which displays the results by means of a ScrolledWindow.

Couple of issues.

I'm not sure if it's best to declare the ScrolledWindow in the main and pass it to the function which will populate it or if I should only create this Window in the called function. Whichever way I try, the Window will not display until I have added some data.

If I declare the ScrolledWindow first, then pass it to the search function, I get the desired function on the first search, but subsequent searches give an error:
gtk_scrolled_window_add: assertion 'child_widget == NULL'

If I declare the Window in the search function then again it works for the first search but on subsequent searches the Window does not update with the new results.

My question is whether I need to somehow reset the Window in the first scenario or force a refresh in the second

Most of the code (with some irrelevant display widgets omitted_ is here:
[http://pastebin.com/q5bnLxaB](http://pastebin.com/q5bnLxaB)

Lines 33-35 are commented out in this version of the code, so that the ScrolledWindow is declared in function on_search_enter

I also need to figure out how to add a clickable button in the third column of the ScrolledWindow but that's a less immediate concern

---

### Post by ofnuts on 2015-02-15
Not a GTK or PyGTK expert, but:
[LIST]
[*]Your scrolled window will likely not show until you put something in it (the table)
[*]I would create the scrolled window and the table it contains at the beginning, and pass to the search function the lowest window it needs to show the data (the table).
[/LIST]

It can also be a good idea to decouple the search function from the table update ([Model-View-Controller]("https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller") pattern).

---

### Post by pickarooney on 2015-02-15
Even with the window and table created in the main and passing the table to the search function, the two issues remain - the window, with an empty table, does not display and once I add the TreeView in the search function it won't add a second time.

Ideally, I would like to (and originally did have) all the visual elements defined outside and just the table going to the search function, but I found there was simply no way to pass the table back to the main once it had been populated. In fact, each time I redesigned it I encountered the same problem - at some point the retrieved data needs to be sent back outside to the main function but it seems like there's no workable way to do it. The item passed into the function simply stays there. I tried using a return in the function but I couldn't use the returned value as the function was called by a connect action.

---

### Post by ofnuts on 2015-02-16
Looking at the code more closely...  GTK sort of follows the MVC pattern. Here the Model part of the pattern is the Gtk.ListStore. So you should really just have to set up to windows and keep a reference to the list store. This list store can be passed to the search function to be filled with results.

---

