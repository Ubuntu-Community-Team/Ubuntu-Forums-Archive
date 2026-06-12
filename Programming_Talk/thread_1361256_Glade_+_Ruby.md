---
title: "Glade + Ruby"
date: 2009-12-21
forum: Programming Talk
---

### Post by qalimas on 2009-12-21
I am just learning GTK GUI design with glade, and I knwo a little Ruby from Rails, so I am going to attempt a board game as my first project to learn this with.

MY first, and hopefully simple, question, is if I have a widget (image2), and I want to relocate that image when a button is click (change x from 100 to 50), how is it done?  I've tried guessing with random @glade.get_widget("image2").everything and can not seem to get it to work =/

Any help is appreciated!

---

### Post by qalimas on 2009-12-22
If it helps, the code can be found here:
[https://sourceforge.net/projects/gameoftrace/](https://sourceforge.net/projects/gameoftrace/)



I'd like the show button to simply give the flag image a new x,y coordinate set.


:popcorn:

---

### Post by qalimas on 2009-12-23
After more hours of Googling, I realize I must have been searching for the wrong thing.

The image must be in a GTK::Layout (?).

The test function I used, that worked:
```
  def test_relocate(widget)
    @playericon = @glade.get_widget("image2")
    @glade["layout1"].move(@playericon, 5, 5)
  end
```


I hope this can end up helping someone!

---

