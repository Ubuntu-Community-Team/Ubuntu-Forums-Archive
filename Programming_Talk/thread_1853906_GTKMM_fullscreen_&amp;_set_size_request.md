---
title: "GTKMM fullscreen &amp; set_size_request"
date: 2011-10-03
forum: Programming Talk
---

### Post by dicoj on 2011-10-03
Hello,
 
I'm new to GTK. Sorry for my bad english.
 
I've got such problem.
 
I have textview in box (and other boxes). Textview is 40 * 25 chars. Font type (monospace) and size is set outside. I need to set size of this textview in pixels and show everything fullscreen.
 
I must have textview shown[show_all_children] to get line height (yrange).
 
At on_realize event I calculate textview's height and width. I set its size(set_size_request) and run. It isn't fullscreen.
 
When I remove "show_all_children" it goes fullscreen but it can't get line height.
 
Thanks in advice for help.

---

