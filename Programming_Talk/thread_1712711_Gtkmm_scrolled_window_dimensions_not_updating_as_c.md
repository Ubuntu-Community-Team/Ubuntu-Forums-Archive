---
title: "Gtkmm scrolled window dimensions not updating as child object changes"
date: 2011-03-23
forum: Programming Talk
---

### Post by simonj21 on 2011-03-23
Hi there!

I'm using Gtkmm, and I've got a problem that I can't for the life of me figure out.

I have a window, that contains a VPaned (called 'pane'). At the top of the pane, I have an OpenGl scene, and at the bottom I've got my own object, 'curAttributePane'

```
 
  scroll = new Gtk::ScrolledWindow();
  scroll->set_policy(Gtk::POLICY_AUTOMATIC, Gtk::POLICY_AUTOMATIC);
  scroll->add(curAttributePane);
  pane.pack2(*scroll, Gtk::SHRINK);
```

curAttributePane is an instance of AttributePane (my own class) which inherits from 'Gtk::Layout'. This above code is in the constructor of the main window.

Now, everything works great, except the scrolling. I am adding elements to 'curAttributePane', and I continually redraw it. However, the scrolling dimensions do not update, so that as the window gets bigger, the scroll won't allow us to see it.

I'd greatly appreciate any response, I'm completely stuck. Also, thanks in advance :)

---

### Post by simonj21 on 2011-03-23
I really hate to bump, but I'm desperate here :)

---

### Post by SledgeHammer_999 on 2011-03-23
**I am adding elements to 'curAttributePane', and I continually redraw it**

What do you mean 'continually'? Do you let the main loop process any gui signals/updates between redraws or are you in a 'busy' loop that redraws?

If yes, then you have to let the main loop process gui events. Every few iterations of your redraw code run ```
while (Gtk::Main::events_pending()) Gtk::Main::iteration(false);
```

or something equivalent.

Related docs: [http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Main.html](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Main.html)

Also guard against code reentrance(especially from the user hitting buttons) when iterating the loop manually.

---

### Post by simonj21 on 2011-03-24
Thanks for responding.

There's no busy waiting here, it's multithreaded, and so the main loop can process signals fine. It's quite a large program, so there's plenty of buttons and that sort of thing. 

Essentially the main Gtk loop will run, then we'll click on a button which will add a label to the bottom of 'curAttributePane'. This displays fine, but the scroll bar does not update its dimensions to reflect the enlarged 'curAttributePane'.

I've uploaded images: [http://imgur.com/a/QSDss](http://imgur.com/a/QSDss)
The top image shows no scroll bar down the bottom right. This grey pane is the 'curAttributePane', and this shows all the elements in it ('Title', 'Author', etc...).
The lower image shows that when this pane is made smaller, the size of the scroll is not large enough to reach the bottom elements of this 'curAttributePane'. As I add more elements to 'curAttributePane', the size of this scrollbar does not update at all.

---

### Post by SledgeHammer_999 on 2011-03-24
I think I found the problem. From the gtk docs(bold mine):

> 
If a widget has native scrolling abilities, such as GtkTextView, GtkTreeView or GtkIconview, it can be added to a GtkScrolledWindow with gtk_container_add(). **If a widget does not, you must first add the widget to a GtkViewport, then add the viewport to the scrolled window.** The convenience function gtk_scrolled_window_add_with_viewport() does exactly this, so you can ignore the presence of the viewport. 


gtk link->[http://library.gnome.org/devel/gtk/stable/GtkViewport.html](http://library.gnome.org/devel/gtk/stable/GtkViewport.html)

But it seems that Gtk::ScrolledWindow::add() already does that automatically:
> 
Puts the child inside a Gtk::Viewport if it doesn't have native scrolling capability.


gtkmm link->[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1ScrolledWindow.html#a17c588d56d93923841d38f0d5e2ec9d7](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1ScrolledWindow.html#a17c588d56d93923841d38f0d5e2ec9d7)

Try putting 'curAttributePane' in a viewport manually. Maybe the gtkmm ::add() has a bug.

---

### Post by simonj21 on 2011-04-01
Hey Sledge,

Very sorry for the long delay. I had job interviews, which stopped me from working on this project.

I wasn't able to find a way to add the child differently, but I did find a solution.

The child widget (which inherits from Gtk::layout), has to call 'set_size', with the appropriate size. So, what I now do is work out the size of all the elements in the widget (I couldn't find an easy way to do this, so instead I just do an individual count), and then set that as the height in the 'set_size' command. This call caused the scroll bars to automatically update, making me a happy man.

Thanks for your help sledgehammer, it gave me a good chance to think through the problem, and hopefully this will help someone out in the future.

Simon

---

