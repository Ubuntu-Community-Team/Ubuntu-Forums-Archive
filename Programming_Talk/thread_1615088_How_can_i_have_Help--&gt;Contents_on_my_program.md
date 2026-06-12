---
title: "How can i have Help--&gt;Contents on my program?"
date: 2010-11-06
forum: Programming Talk
---

### Post by leon.vitanos on 2010-11-06
If you see some programs on ubuntu have the Help-->Contents thing and  if you click it, the Program Help will open and it will show some  information about the program.. 
Is there anyway i can do this on my app or is only for preinstalled applications on ubuntu...? ( If yes is there any example of it ? It would be helpful )...

P.s 
I am using Qt Creator...

---

### Post by leon.vitanos on 2011-01-06
Any ideas?

---

### Post by dwhitney67 on 2011-01-06
Add a Help cascading menu option to your Qt application, with a menu button for Contents.

Within the callback routine for the menu button, pop-up a dialog box with the relevant information you want displayed.  The dialog should provide the user the ability to dismiss the dialog when they are done with it.

All of this is done using the C++ code that presumably you are using for your Qt application.

---

### Post by leon.vitanos on 2011-01-06
> **dwhitney67 said:**
> Add a Help cascading menu option to your Qt application, with a menu button for Contents.

Within the callback routine for the menu button, pop-up a dialog box with the relevant information you want displayed.  The dialog should provide the user the ability to dismiss the dialog when they are done with it.

All of this is done using the C++ code that presumably you are using for your Qt application.

Yes ok but it will be a simple dialog... It will not open yelp like the other ubuntu applications...

---

### Post by dwhitney67 on 2011-01-06
"Other Ubuntu applications"... do you mean Gnome applications?  Gnome is based on the GTK+ GUI development API; you are using Qt.  If you are not satisfied with Qt, then switch to something else.

As for a dialog window, they are easy to lay out and display.  If you are looking for something more elaborate, such as an HTML driven user's guide, then use Qt's QTextBrowser.

---

### Post by leon.vitanos on 2011-01-06
> **dwhitney67 said:**
> "Other Ubuntu applications"... do you mean Gnome applications?  Gnome is based on the GTK+ GUI development API; you are using Qt.  If you are not satisfied with Qt, then switch to something else.

As for a dialog window, they are easy to lay out and display.  If you are looking for something more elaborate, such as an HTML driven user's guide, then use Qt's QTextBrowser.

Yes ok Gnome applications... I know exactly how to create a dialog... But for example.. Do you have ubuntu? If yes go the calculator and at the menubar Help->Contents it will open Yelp with information about the calculator.. How is this possible?

---

