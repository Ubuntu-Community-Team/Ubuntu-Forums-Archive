---
title: "[SOLVED] Help with python and glade. Printing user input."
date: 2007-10-07
forum: Programming Talk
---

### Post by Acglaphotis on 2007-10-07
Hey

Im trying to print whatever is that the use wrote in a text entry field, be it by pressing a button or as the user types. I am using python + glade.

Any ideas?

---

### Post by Megaqwerty on 2008-01-30
I don't know if your question has been answered yet, but just in case it helps:

[PHP]def on_okButton_clicked(widget, data, wtree):
	urlEntry = wTree.get_widget("urlEntry")
	brwsrEntry = wTree.get_widget("brwsrEntry")
	url = urlEntry.get_text()
	browser = brwsrEntry.get_text()
	os.system(browser + " " + url)[/PHP]

You'll obviously have to tweak this example to work with your program, but the main idea is that after you initialize the entry widget (in this case, urlEntry and brwsrEntry) you use ".get_text()" to retrieve the text in the field.

Hope that helped,

Megaqwerty

P.S. note that that isn't PHP code, it *is* python, but using the php tags gave me syntax highlighting.

---

### Post by Acglaphotis on 2008-01-30
Thanks, i did find the answer to this question. I guess i forgot to mark it as solved. sorry for the trouble.

---

