---
title: "Ubuntu Quickly, Glade UI change by code?"
date: 2012-01-06
forum: Programming Talk
---

### Post by nshiell on 2012-01-06
Hi,
I am playing with Ubuntu quickly and I have designed a UI with glade for a window.

I want to change some text in a text view using Python, all the tutorials I have seen don't tell you how to work with UIs made with an interface designer.

E.g.
[http://www.learngtk.org/pygtk-tutorial/textviewconstruction.html](http://www.learngtk.org/pygtk-tutorial/textviewconstruction.html)

Do you guys know of an EASY turorials for how to make programic runtime changes to UIs with Ubuntu Quickly?

---

### Post by Russss on 2012-01-07
I used quickly to make an application to store and submit codes to the coke rewards program. Here is one method I have in the program that show how to change the text.

```
 
def save_dialog(self, text_e, text_s):
        saver = SavecodesDialog()
        #write the valid codes to saver
        buff = saver.ui.textview_s.get_buffer()
        buff.set_text(text_s)
        #write the invalid codes and error message to saver
        buff = saver.ui.textview_e.get_buffer()
        buff.set_text(text_e)
        saver.run()
        saver.destroy()
```

It first creates a dialog window that shows the codes that have been save to the database(text_s) in one textview and the codes that were not saved because they were not right format (text_e) in another text view.

If you want to see more of the context here is the rest of the code. [http://bazaar.launchpad.net/~stilesr28/pymcr/quickly_trunk/files/head:/pymcr/]("http://bazaar.launchpad.net/~stilesr28/pymcr/quickly_trunk/files/head:/pymcr/")

That method is from PymcrWindow.py
Hope it helps some.

---

### Post by Brandon Williams on 2012-01-07
Have you tried "quickly -t ubuntu-application tutorial"? It walks you through the basics of application creation, and includes examples of both retrieving and modifying the text in a textview.

---

