---
title: "GUI application"
date: 2009-07-17
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-17
I need to develop a GUI application capable of following:
.receive and send data serially
.display a moving map similar to google earth or better integrate google earth in the application

Last time i had used  java in windows along with rx-tx library
this time i wish to move completely to linux using c\cpp
is it a good choice to leave java?
i am confused between gtk and qt?
which one shall i go with?
anyone to help?

---

### Post by Leslie Viljoen on 2009-07-17
Do you have a reason to leave Java? Why do you want to develop the app again?
If you want your app to look native, Java has bindings to both Gtk and Qt. Gtk is the GUI toolkit native to Gnome (Ubuntu's default window manager), Qt is KDE's native toolkit (KDE is Kubuntu's default window manager).

---

### Post by nipunreddevil on 2009-07-17
i was not able to get my java code work in linux.
though it ran well on windows but only in win xp.
i want to make os independent program.
it is for ground control station of a uav.
confused between qt/java/gtk.
like to programme in c and cpp.
Guidance needed

---

### Post by raronson on 2009-07-17
You may also want to take a look at the Wikipedia entries for GTK and Qt, which have lists of the most popular applications for both.  GTK apps include Open Office, Firefox, and now Google Chrome...

It's just my opinion, but unless there's a specific reason to use Qt, I'd pick GTK.  Gnome/GTK is currently leading the pack in terms of popularity (Gnome is sponsored by Redhat, and used by default in SuSE and Ubuntu), and now that Google's using it for it's own operating system, it's only a matter of time before Qt becomes known as "that other GUI kit."

---

### Post by nipunreddevil on 2009-07-17
how easy is to do the following in gtk:
serial port interfacing,gui develepment with and without glade,display images.file read write
or is qt better suited

---

### Post by Leslie Viljoen on 2009-07-23
> **nipunreddevil said:**
> i was not able to get my java code work in linux.
though it ran well on windows but only in win xp.
i want to make os independent program.
it is for ground control station of a uav.
confused between qt/java/gtk.
like to programme in c and cpp.
Guidance needed

Surely trying to get your Java app working under Linux is going to be easier than completely rewriting it in another language? What was the problem with getting it to run?

---

### Post by nipunreddevil on 2009-07-23
was not able to install rx tx libraries i used for serial interfacing

---

### Post by Leslie Viljoen on 2009-07-23
Did you see these?
[http://www.agaveblue.org/howtos/Comm_How-To.shtml](http://www.agaveblue.org/howtos/Comm_How-To.shtml)
[http://www.captain.at/howto-java-serial-port-javax-comm-rxtx.php](http://www.captain.at/howto-java-serial-port-javax-comm-rxtx.php)

---

### Post by nipunreddevil on 2009-07-23
Yes,
But still not able to do things
Dont know whether the shortcoming was due to my inability or what?
Also i think limited books are meant for applications in JAVA.

---

### Post by Leslie Viljoen on 2009-07-24
> **nipunreddevil said:**
> Yes,
But still not able to do things
Dont know whether the shortcoming was due to my inability or what?
Also i think limited books are meant for applications in JAVA.

Well you are free to use any language! I just spend a lot of time with C and C++, and Java is a very great improvement. I haven't tried serial comms in Java yet but will probably need to sooner or later.

---

### Post by nipunreddevil on 2009-07-24
i am shifting to python
Seems simpler,for serial communications on it check out pySerial.
Hope you find it useful

---

### Post by jacksaff on 2009-07-24
Have you looked at marble? It sounds like it does a fairly similar job to what you want. You should be able to plug a marble widget into any qt application fairly painlessly.

---

