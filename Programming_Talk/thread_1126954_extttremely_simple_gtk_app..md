---
title: "extttremely simple gtk app."
date: 2009-04-15
forum: Programming Talk
---

### Post by sandyd on 2009-04-15
could someone teach me how to make a simple dialog bo with text and an "Ok" button with GTK, or some other language?

it has to be easeily executable becuase im using this as part of my KDE and Gnome Autostart.

Its just to display a warning to people that all the  stuff they leave on the desktop will go missing when they log out. (because the desktop is ALWAYS flooded with files and its kinda impossible to find anything.)

---

### Post by Can+~ on 2009-04-15
You can use Zenity for one-time easy dialogs.

```
zenity --warning --text="Everything on your desktop will be wiped out on logout." --title="Warning: Desktop cleanup"
```

And GTK+ is not a language, it's a toolkit for languages to use.

---

### Post by kknd on 2009-04-15
Forum search / google helps sometimes (don't be lazy, search first).

[http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)

---

### Post by sandyd on 2009-04-17
Thanks for the clarification!

---

