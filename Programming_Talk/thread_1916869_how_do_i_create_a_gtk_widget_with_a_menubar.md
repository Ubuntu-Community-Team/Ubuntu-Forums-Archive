---
title: "how do i create a gtk widget with a menubar?"
date: 2012-01-28
forum: Programming Talk
---

### Post by kline on 2012-01-28
i'm using 11.10 and have been trying to create a small gtk app with the strings: "File", "Edit", "Help" and so forth nothing i do ctreates theis menubar.  now it's time to ask the forum.  how?

---

### Post by raja.genupula on 2012-01-28
[http://www.gtk.org/tutorial1.2/gtk_tut-13.html](http://www.gtk.org/tutorial1.2/gtk_tut-13.html)

---

### Post by lisati on 2012-01-28
*Thread moved to **Programming Talk**.*

---

### Post by kline on 2012-01-28
> **raja.genupula said:**
> [http://www.gtk.org/tutorial1.2/gtk_tut-13.html](http://www.gtk.org/tutorial1.2/gtk_tut-13.html)

i  tried this exact code about 40 minutes ago.  no luck.  could i be missing some gtk library[ies]?  gcc didn't complain, but still ... [??]

---

### Post by pbrane on 2012-01-30
Have a look at this [www.gtk.org/documentation.php]("http://www.gtk.org/documentation.php")

I was able to compile and run the manual gtk menu code from raja.genupula's link using this command.
```

gcc -Wall -o gtkmenu gtkmenu.c $(pkg-config --cflags --libs gtk+-2.0)

```

---

### Post by nvteighen on 2012-01-30
Menus in handmade GTK are a bit tricky, because GtkMenuBar and GtkMenu aren't what you expect...

Please send us the code you've written and the errors you get when compiling (use [NOPARSE]```

```[/NOPARSE] when posting!).

---

### Post by kline on 2012-02-02
> **nvteighen said:**
> Menus in handmade GTK are a bit tricky, because GtkMenuBar and GtkMenu aren't what you expect...

Please send us the code you've written and the errors you get when compiling (use [NOPARSE]```

```[/NOPARSE] when posting!).

--BTW, this is to you and pbrane immediately above.  i tried the first program that was complete.  of course it built and ran. the second program seemed several clicks over my head and i didn't even try.  but i just copied ite mfactory.c and, yup, got the "File" and "Options" on the menubar.  

the "harder" way seems reminiscent of ther athena toolkit that i used for several years.  i'll have to study the "easier[?]" way.  essentially, other than Quit, beneath "File" i'll want save-discussion {or whatever} which will save the user's text-to-speech conversation if he wants to.  the options will configure the slew of options to espeak.

i'm working on a GUI app for the speech impaired or mute who =are= able to type.  they will need to bring a netbook or tablet with builtin keyboard when they want to talk to folks.  

FWIW, the challenge is to make this thing intuitive... .

---

### Post by r-senior on 2012-02-02
The Zetcode tutorials are really good introductions, not just for GTK but lots of other things too. Here's the GTK menu part:

[http://zetcode.com/tutorials/gtktutorial/menusandtoolbars/](http://zetcode.com/tutorials/gtktutorial/menusandtoolbars/)

---

### Post by kline on 2012-02-02
> **r-senior said:**
> The Zetcode tutorials are really good introductions, not just for GTK but lots of other things too. Here's the GTK menu part:

[http://zetcode.com/tutorials/gtktutorial/menusandtoolbars/](http://zetcode.com/tutorials/gtktutorial/menusandtoolbars/)

well, i would have bet my mother's life that i had already tried this one and it had FAILED.  No; this works.  got to read this again. thanks.

---

