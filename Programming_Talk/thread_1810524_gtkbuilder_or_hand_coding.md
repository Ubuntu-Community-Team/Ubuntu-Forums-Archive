---
title: "gtkbuilder or hand coding?"
date: 2011-07-23
forum: Programming Talk
---

### Post by nickos on 2011-07-23
title is clear.what do you prefer to do when creating gtk gnome apps?Do everythingwith GtkBuilder or use your own fingers to make menus, boxes, buttons etc?

welli prefer the second one and i want to know if thats stupid or i am the only one who does so even though it may be a little more time consuming.

---

### Post by PaulM1985 on 2011-07-23
I don't know much about gtkbuilder, but I have experience of other user interface designers.

I think that it is important to know how the user interface code works, so I recommend designing user interfaces by hand.

I used to design all of my Java interfaces by hand.

However, if you have been doing this sort of thing for a while and know how the user interface code works, I would recommend moving to a designer.  You will have learnt your lessons on how user interfaces work and now let the designer deal with it all to speed up your development time.

So I now let Netbeans make all my interfaces for me so that I can spend my time working on the more complex parts of my application.

Paul

---

### Post by JupiterV2 on 2011-07-23
I am not an overly experienced interface designer. In my first major project I wrote the interface by hand. Having done that, and trying to maintain the code, I will use an interface builder in the future. Why?

1) Faster development - Making even a minor change requires the project to be recompiled and run. Changing the interface within a UI designer allows you to see the changes as you make them. Development is also more rapid because you can focus on writing your handlers and algorithms rather than maintaining/tweaking the UI code.

2) Maintainability - As stated in the above, its all about maintenance. With a UI designer I simply reopen the UI file, adjust the interface and I'm done. All I have to do, code wise, is maintain the handlers.

I'm very glad I designed the interface by hand. It gave me a much deeper understanding of the UI and how all its parts work together. It's a worthwhile exercise. However, from a pure development point of view I wouldn't do it again.

Oh, and Glade is used to make GtkBuilder files. I don't recommend building the xml files by hand.

---

