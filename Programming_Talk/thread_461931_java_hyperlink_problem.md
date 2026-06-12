---
title: "java hyperlink problem"
date: 2007-06-02
forum: Programming Talk
---

### Post by jinxen on 2007-06-02
Hi!

I am parsing RSS from a site. And when i am getting the URL into my java application i would like it to be a clickable hyperlink? How do i manage that? Should i use JTextArea och JTextPane? If JTextPane how do i add multiple lines like into a JTextArea (using insert(), as in JTextPane setText())?

```

Main.test2.insert("Title: " + item.getTitle() + "\n" + "URL: " + item.getLink() + "\n\n", 0);

```

The inserting code for now. I would like the item.getLink() to be a clickable URL.

Regards, Tommy

---

### Post by jinxen on 2007-06-02
Ok the code has now changed a bit. I can parse the site into a jlist, and are now able to get the value. For example the webadress. So now the only problem is when i doubleclick on the selected index i want it to open in the browser?

Regards Tommy

---

### Post by jinxen on 2007-06-02
Problem solved :)

---

### Post by inksmithy on 2009-04-26
HOW? I hate it when people do this. When you find a solution to a problem, even if the solution didn't come from this forum, if you can be arsed to reply to a message to say its been solved, put the solution in the message!

Otherwise what happens is, like me, I do a search for a similar solution, find this damn useless post and get absolutely no joy from it. Incredibly frustrating!

---

### Post by ecimon on 2009-04-27
Try [http://java.sun.com/docs/books/tutorial/uiswing/components/html.html]("http://java.sun.com/docs/books/tutorial/uiswing/components/html.html")

---

### Post by evade1 on 2009-11-05
> **jinxen said:**
> Problem solved :)

How? Please help!

---

