---
title: "need a tutorial to make a window in ubuntu with c++"
date: 2008-10-18
forum: Programming Talk
---

### Post by rtoot3 on 2008-10-18
ive been searching forever for a tutorial to make a window in ubuntu using c++, but all i can find is windows tutorials! can someone please help me? or at least post a link to a tutorial?

---

### Post by spadewarrior on 2008-10-18
Hi there. Try here:

[http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html](http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html)

C++ and GTK+.

Hope it helps.

---

### Post by ihavenoname on 2008-10-18
> **spadewarrior said:**
> Hi there. Try here:

[http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html](http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html)

C++ and GTK+.

Hope it helps.

That seems to be a gtk+ website, which is C based. I would recommend using gtkmm for C++ gtk programming. [http://gtkmm.org/documentation.shtml](http://gtkmm.org/documentation.shtml) They have the api and some tutorials on that website plus they have a download-able pdf ebook. 

Another toolkit you might be interested in is Qt from trolltech. It's the toolkit used by KDE. If you use gnome I reccomend gtkmm as it will be more integrated with your applications, but if you use KDE then I reccomend Qt (though you could quite easlity mix the two). 

You may need to install something from synaptic to get going, if you need help feel free to ask. 

p.s. there is a tutorial for making a window in gtkmm in the documentation.

---

