---
title: "simple python question"
date: 2010-07-14
forum: Programming Talk
---

### Post by ubudog on 2010-07-14
Hello, I am wondering how to make a Tkinter button make a text area (or label, I think) say something.  In the callback for the button, what is the syntax?  Thanks.

---

### Post by Bachstelze on 2010-07-14
label.configure(text="blah blah blah")

---

### Post by ubudog on 2010-07-14
Exactly what I was looking for.  Thanks!  Another question, the text goes off the screen when I run the app, so how do I make the text area bigger?

---

### Post by Bachstelze on 2010-07-14
Probably

label.configure(width=n)

where n is the nmber of characters in the text. Not sure about that one, though.

---

### Post by ubudog on 2010-07-15
Thanks for all the help, but one more question.  How do I make a button open another program?  Like when I click the button, it opens firefox, or another python program I created.  Thanks.

---

### Post by ubudog on 2010-07-15
Nevermind, figured it out.  Thanks for your help!

---

