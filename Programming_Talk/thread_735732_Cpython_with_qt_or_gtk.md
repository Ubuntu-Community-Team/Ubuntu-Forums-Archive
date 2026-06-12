---
title: "C/python with qt or gtk"
date: 2008-03-25
forum: Programming Talk
---

### Post by sujoy on 2008-03-25
i am confused in choosing an appropriate gui for my project, its supposed to be a simple chat server.

what is the difference between qt and gtk as far as performance is concerned or ease of programming? i can't really decide which one to opt for. my code will probably be mostly in c or python.

and one more thing. in some ide like say turbo C, i could just write the name of a function and press ctrl+F1 to see info regarding that function. is there a similar functionality available in any IDE for linux (ubuntu/debian specially)?

---

### Post by LaRoza on 2008-03-25
GTK is used in GNOME (and others), and QT is used in KDE (and others)

If you have a specific target, use the one that fits, otherwise, it doesn't matter and use the one you like best.

My wiki has information on several GUI toolkits, including GTK, QT and wxWidgets.

---

### Post by sujoy on 2008-03-25
no i dont have a specific target, just because i dont have much experience in coding, i am thinking maybe i might lack the functionality of one or the other in the long run, since i do intend to maintain the project and improve upon it.

---

### Post by pmasiar on 2008-03-25
I am not sure why you need GUI for a chat **server**?

And why you start with a server programming if you don't have much experience?

That said, **twisted** is Python framework for creating exactly such kind of servers.

---

### Post by LaRoza on 2008-03-25
> **sujoy said:**
> no i dont have a specific target, just because i dont have much experience in coding, i am thinking maybe i might lack the functionality of one or the other in the long run, since i do intend to maintain the project and improve upon it.

Both QT and GTK are used to make entire desktop environments, so they both have a complete toolkit.

Both will work on Windows, but QT doesn't worth with C, GTK does.

Both have GUI builders, to help make GUI's

Both work with many languages, including Python.

For Python, if you want a quick and easy GUI (no events), EasyGUI is great.

---

### Post by sujoy on 2008-03-25
umm, sorry, i am also supposed to have a client for interacting with the server. i am studying up on server/socket programming.

 its the gui i am not experienced in hence the confusion. anyways, thanks.

EDIT: fine then, i will start with GTK. :)

---

