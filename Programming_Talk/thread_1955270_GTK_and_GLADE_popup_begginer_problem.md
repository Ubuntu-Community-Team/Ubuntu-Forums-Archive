---
title: "GTK and GLADE popup begginer problem"
date: 2012-04-09
forum: Programming Talk
---

### Post by sebasira on 2012-04-09
Hello everybody! I'm new eto Glade and GTK. 

I'm messing around, writing some code to get familiar with it. Now I've encountered a problem.

In glade I've made two windows:
- main
- numericPad

In the main window there's a button that popup the other window, the numericPad. In it, there are nine buttons (1-9) and when pressed the number is displayed in an entry box in the main window. 
Till now everything works fine.

This "popup window" should be closed when clicking outside of it. I catch the focus-out-evet and I destroy this window. The problem is that after destroying it I can't show it up again because it doesn't exist anymore.

I try hidding the popup instead of destroying it but if so, then I've got a problem with the numeric buttons. For example, if I open/close the popup 3 times, and I click a number, then the number is written 3 times.

Hope You can help me!

I post .glade and code here! Thanks in advance

---

