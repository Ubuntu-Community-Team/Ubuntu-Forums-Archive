---
title: "[HTML/CSS] Text jumps around on hover"
date: 2009-04-10
forum: Programming Talk
---

### Post by fiddler616 on 2009-04-10
Hello,

I became interested in [this]("http://ubuntuforums.org/showthread.php?p=7047221#post7047221") thread (making a gnome-panel out of HTML and CSS), and started messing around with it.

You can see the current product here: [http://tsmacdonald.com/Panel/]("http://tsmacdonald.com/Panel/").
It has a problem though: hovering over a menu item makes the other menus drop down a few lines. After some hacking, I edited the following:
```

ul:hover .hid {
display:block;
**position:absolute;**
}
```
Which fixes the menu titles (Applications, System, etc.)but messes up the menu items--there's only one line shown.

I've been bashing my head against this for several hours, hoping that somebody would come save me on the original thread, tweaking lines of code, and Googling around, and I've come up with nothing.

Thank you.

---

