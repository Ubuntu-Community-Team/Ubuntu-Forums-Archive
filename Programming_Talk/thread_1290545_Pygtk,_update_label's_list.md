---
title: "Pygtk, update label's list"
date: 2009-10-13
forum: Programming Talk
---

### Post by benevolent on 2009-10-13
Hello everyone!

I have the following problem. I'm having a list of strings, which is created from clients on my server (via sockets) and I want the list to be printed on a label. How can I make the label to get the updated list ??

Example:

List = [a, b, c]

#after some appending, final list
List = [a, b, c, d, e, f]

the label's code: label = gtk.Label(""" {0} """.format(List))

What i get on the label is obviously a, b, c. How can I achieve having the updated list???? 


Thank you in advance, any help will be appreciated :guitar:

---

### Post by days_of_ruin on 2009-10-13
Just use ```
label.set_text
``` after you've updated the list.

---

### Post by benevolent on 2009-10-14
Hmm.. Let me analyze it a little more.

I have a server. The list I want is there. It's initialized with [a,b,c] for example.

I also have, lets say, 3 clients. Every each client adds 1 element to the list, so the list would be like [a,b,c,d,e,f].

The problem is that when I run server.py, the label is getting the initialized list first and after that the clients send their elements. That way the label cannot be updated.

Somehow, I need to refresh the label's contents, after I make my final list, through clients.

thx again :)



**edit: I found a solution, I just created a button, so every time i click it, it updates the lists I want by using the set.text you told me!**


cheers :)

---

