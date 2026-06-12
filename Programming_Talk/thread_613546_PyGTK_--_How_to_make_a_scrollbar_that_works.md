---
title: "PyGTK -- How to make a scrollbar that works?"
date: 2007-11-15
forum: Programming Talk
---

### Post by WinterWeaver on 2007-11-15
Good day all,

I was wondering if someone could help me with my scrollbars in PyGTK. I've googled and searched for the last 2 days, but I'm getting really confused with this.

I have a Treeview (List) and populate it with a list of files. My problem is that, when the list grows larger than my window, then there aren't any scrollbars? I can scroll down my clicking  a item in the list, and using the up/down arrows, but this is not ideal of course :P

I'm using Glade to create my GUI, btw.
So basically I'm asking for someone to explain to me what I need to do to make Scrollbars work in PyGTK & Glade, as they do in other apps.

a Screenshot is attached to show what it looks like. Please note that the Scrollbar in the screenshot you see, is one I manually added, but it doesn't actually do anything.

Thanks for any advice/help. ^_^

---

### Post by WakkiTabakki on 2007-11-15
Simply drop your treeview in an ScrolledWindow-container and it'll take care of it all for you...

Check out the attachment...

/N

---

### Post by WinterWeaver on 2007-11-15
omg... lol... that simple!!??

hehe... Thanks for that, it worked perfectly ^_^

---

