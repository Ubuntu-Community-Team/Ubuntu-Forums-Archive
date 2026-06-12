---
title: "How to close a GtkWindow"
date: 2008-03-12
forum: Programming Talk
---

### Post by songuke on 2008-03-12
Hi guys,
I'm new to GTK+ and now I cannot find any functions (or its related document) to show how to close a GtkWindow?

I want it to invoke when I click my "exit" button.

Of course, we can use the "X" button on the top right corner. So what I want is to make an invoke like the invoke of the X button.

Can anyone help?

Thanks in advance.

---

### Post by shifty2 on 2008-03-12
Depends what you want to do:
gtk.main_quit() will totally kill the program
gtk.window.destroy() will destroy the window but keep the program running
gtk.window.hide() will hide the window so it can be opened again

replace gtk.window with the name of your actual window.

---

