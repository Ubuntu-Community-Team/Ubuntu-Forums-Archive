---
title: "System &quot;freezes&quot; when starting to type in Firefox Adress Bar"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by couchilla on 2011-11-27
Hi
since yesterday my whole laptop seem to freeze when i start typing a url in the adress bar of firefox. i say seem because i still can move my mouse and my banshee plays the music in the background but i cant use alt-tab , close firefox, use buttons. i have to pull the plug on my laptop :D
cant think of something i changed yesterday..it doesnt happen all the time, for example now its working. 

ps. im fairly new to ubuntu (or unix systems in general) so maybe its something absolutely trivial what causes my problem..something like an interface lock i dont know of.

thanks in advance if anyone can help me

---

### Post by LinuxFan999 on 2011-11-27
What are the specifications of your laptop?

---

### Post by MG&amp;TL on 2011-11-27
Can you open a terminal (press Ctrl-Alt-T or search for it in Unity search thing), type:

```
firefox
```

 and then press RETURN.

Firefox will launch. Split the screen so that you can see the terminal. Now do whatever you do in FF to get it to freeze. Now either note down the messages displayed on the terminal, and reboot your laptop, or use another pc, put the messages here. Wrap them in CODE tags (hash button, #), and post.

then we'll be able to see what's going wrong. :)

---

### Post by lovinglinux on 2011-11-27
It is probably an issue with your bookmarks database.

You can try to optimize it or export your bookmarks, delete the database and import the bookmarks back.

To optimize it, see [http://www.webgapps.org/tutorials/firefox/optimization/database-optimization](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)

You can also use one extension like [Places Cleaner](https://addons.mozilla.org/en-US/firefox/addon/placescleaner/) or [Vacuum Places Improved](https://addons.mozilla.org/en-US/firefox/addon/vacuum-places-improved/?src=search).

If you don't care about your bookmarks, simply delete the file *places.sqlite* from your Firefox profile, under ~/.mozilla/firefox/<profilename>/.

If you want to restore the bookmarks later, export them as html using the Bookmarks Manager, then close Firefox, delete the places.sqlite file, then import the bookmarks from the html file.

---

