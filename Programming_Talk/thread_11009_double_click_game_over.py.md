---
title: "double click game_over.py"
date: 2005-01-13
forum: Programming Talk
---

### Post by Buffalo Soldier on 2005-01-13
I'm new to programming. Bought a book "Python Programming For Absolute Beginner" by Michael Dawson.

One example he gave in the book is a simple program:

```
print "Game Over"
raw_input("\n\nPress the enter key to exit.")
```

and I save it as game_over.py on my desktop.

Problem is, on my windows XP I can double click the file and the program will run (sort of a DOS prompt windows pops up). But on my Ubuntu desktop double clicking it will open the file in Gedit.

What do I have to do to be able to run the file by double clicking? Any help for a linux & python newbie like me?

---

### Post by gheorghe_pop on 2005-01-13
it's very simple:)
you should set your python script as executable.
How to do that:
right click on the file and on the permision tab check 'execute' for all.
That's it!

---

### Post by Buffalo Soldier on 2005-01-13
Thanx gheorghe. Feel like id!@t for not thinking of that first before posting.

Anyway, your suggestion works. But now the problem is the window pop-up and then dissappear very quickly. It did not wait for me to press the ENTER key.

---

### Post by Buffalo Soldier on 2005-01-13
Found the solution to my problem. I found out that I need to add "#!/usr/bin/python" to the script.

```
#!/usr/bin/python
print "Game Over"
raw_input("\n\nPress the enter key to exit.")
```

And if I want to keep the window terminal open after pressing ENTER, I just go to the terminal window settings. 

Edit -> Current Profile -> Title and Command -> When command exits: Hold the terminal open

---

### Post by DirtDawg on 2005-01-13
Bufallo Soldier,

   Hey, I too am fairly new to Python and trying to figure it out one step at a time. How's that book treating you? Is it any good and what kind of price tag came with it?

---

### Post by Buffalo Soldier on 2005-01-13
DirtDawg,

For someone who has experience in Python or any other programming languages may find the book too simple. It's definitely not something an experienced programmer would buy for as a reference book.

But for a beginner/newbie I think the book is perfect. I'll quote something from an introduction paragraph which I find very true about the lessons throught the book.

"The goal of this book is to teach you the Python programming language, learning to program the same way I did: by creating simple games. There's something more exciting about learning to program by writing software that's fun."

The price of the book is (in Ringgit Malaysia) RM96. I guess that's about US Dollar 25.

---

### Post by DirtDawg on 2005-01-14
Sounds awsome. Thanks alot!

---

### Post by gheorghe_pop on 2005-10-19
When you have enought of txt python programming you should try glade+python. You can build really nice apps with that.

---

