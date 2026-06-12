---
title: "foreach entry { entry.text = &quot;&quot;; } - need help with this..)"
date: 2008-06-27
forum: Programming Talk
---

### Post by dinbrca on 2008-06-27
I have tried to use the foreach loop to make every entry in the window to "" here is the code:
```

foreach (Gtk.Entry f in this)
{
	f.Text = "";
}

```
what's wrong with it?

---

### Post by -grubby on 2008-06-27
Perhaps change ```
f.Text = "";
``` to ```
f.Text = " ";
```?

---

### Post by dinbrca on 2008-06-27
no it isn't the problem..

---

### Post by -grubby on 2008-06-27
> **dinbrca said:**
> no it isn't the problem..

Ok, I was just trying to help..

---

### Post by Can+~ on 2008-06-27
I think it is set_text(""), although I only use [pyGTK]("http://www.pygtk.org/pygtk2reference/class-gtkentry.html") (click for the reference)

---

### Post by dinbrca on 2008-06-27
nathangrubb i wasnt angry at you..
can+ I dont use Python

---

### Post by Can+~ on 2008-06-27
> **dinbrca said:**
> nathangrubb i wasnt angry at you..
can+ I dont use Python

I know you don't use it, but I thought it would be the same method :KS.

---

### Post by cdekter on 2008-06-27
What is the actual error/problem you are getting? Need more info...

---

### Post by slavik on 2008-06-28
> **dinbrca said:**
> I have tried to use the foreach loop to make every entry in the window to "" here is the code:
```

foreach (Gtk.Entry f in this)
{
	f.Text = "";
}

```
what's wrong with it?
what language are you using?

---

### Post by dinbrca on 2008-06-28
i am using C#

---

### Post by cdekter on 2008-06-28
I'm kinda guessing based on my experience with Windows Forms in C#... but I don't think you can iterate over the controls in a window like that. A Window is not a collection. You will need to set the Text property for each GtkEntry in your Window separately (unless of course you previously added all of them to some collection you are maintaining elsewhere).

---

