---
title: "Tutorial on threading in pyGTK"
date: 2010-10-02
forum: Programming Talk
---

### Post by Shazzner on 2010-10-02
I'm creating an app with Quickly that uses OpenCV to detect faces via the OpenCv library which has to poll the camera constantly while GTK is doing it's thing so, I assume, it needs to be on a separate thread.

The final app should act very much like Cheese does, only using the OpenCv framework.

Threading is always a bit confusing to setup and I'm pretty new to python, so any links or info to go about doing this would be great. Thanks!

---

### Post by StephenF on 2010-10-02
You can add callbacks to the event loop with gobject.timeout_add. No need for a separate thread unless one of your GTK callbacks is taking too long and even then they can sometimes be broken up.

---

### Post by diesch on 2010-10-02
Have a look at the section "20. The GTK Mainloop and Threading" of the [PyGTK FAQ](http://faq.pygtk.org/index.py?req=index)

---

### Post by Shazzner on 2010-10-02
Wow, that was much simpler than I thought it was going to be. Thanks for the help!

---

