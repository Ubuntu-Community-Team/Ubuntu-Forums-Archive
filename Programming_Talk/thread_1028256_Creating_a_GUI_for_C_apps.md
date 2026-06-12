---
title: "Creating a GUI for C apps ?"
date: 2009-01-02
forum: Programming Talk
---

### Post by RansomStark on 2009-01-02
Hi all,

I fairly new to development on Ubuntu, but I am happy developing in C and VB in Windows. Basically, I am looking to start developing apps in Ubuntu, ideally I would like to use C as I am already familiar with it and can re-use existing code. However, as users these days expect a GUI I want an easy drop and drag (similar to VB) to create the windows and controls, but have the C running behind it all. My searches so far suggest an IDE called Glade, but its all a little new to me so just trolling for ideas.

I will be designing for the GNOME desktop, Ubuntu 8.04.

---

### Post by mike_g on 2009-01-02
For a GNOME gui app in C you would want to use GTK+ and if you want the drag and drop widget pacement use Glade3 to layout your UI. Check out the stickies for more info.

---

### Post by nvteighen on 2009-01-02
The GTK+ toolkit is for C and it's which GNOME is based on. I recommend you to learn to program in GTK+ manually to get the basic working and also understand the design principles behind it.

Look at [url]http://library.gnome.org/devel/gtk-tutorial/stable/[/url

EDIT: Forgot to continue the post... :p After you have learned the basics manually, step to an UI designer. That way you'll have the background knowledge needed to fix whatever the designer happens to not be useful for.

---

