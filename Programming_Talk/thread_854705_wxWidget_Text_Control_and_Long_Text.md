---
title: "wxWidget Text Control and Long Text"
date: 2008-07-09
forum: Programming Talk
---

### Post by era86 on 2008-07-09
Greetings!

I am writing some code using C++ and wxWidgets to output a huge amount of raw data onto the screen.  I am using a wxTextCtrl for the output.  Is there a way to continue spitting out data without the program hanging?

I try to spit out the raw data, which is millions of line of code.  I want the program to keep spitting out this data until a button is clicked to stop it.  Is this possible?

Please let me know.  Thank you!

---

### Post by SledgeHammer_999 on 2008-07-09
The program isn't "hanging". It's UI justs freezes. The function that "spews text" is executed continuously and it doesn't leave space for the update function(to update the textctrl and show the text). Take a look at [wxApp::Yield](http://docs.wxwidgets.org/stable/wx_wxapp.html#wxappyield).

---

### Post by era86 on 2008-07-10
Thank you for the feedback.  I'll try that out.

---

### Post by archivator on 2008-07-10
You might consider using threads and event-based communication to avoid the problem. The thread would read/manipulate the data and would then pass it to the main thread via a custom event. 

But then again, wxYield() might suffice in your case.

---

### Post by era86 on 2008-07-10
I think I'll try the yield first, then I'll incorporate threads as I go along.  There will have to be many other features so threads might be more of a practical approach.  In my case, anyway.

---

