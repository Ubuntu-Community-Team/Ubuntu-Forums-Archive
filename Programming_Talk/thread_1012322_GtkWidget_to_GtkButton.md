---
title: "GtkWidget to GtkButton"
date: 2008-12-15
forum: Programming Talk
---

### Post by DrPepper836 on 2008-12-15
In my code, I need to define a button. So I use the code
```
GtkWidget *button = gtk_button_new();
```

However, in the next line when I try to change the text of the button with this code 

```
gtk_button_set_label(button, "Fire!");
```

then it says that it can't convert from GtkWidget to GtkButton. And I can't just use gtk_button_new_with_label, because I also need to add a picture, which has the same issue.

---

### Post by Vadi on 2008-12-15
> gtk_button_set_label((GTK_BUTTON) button, "Fire!");

Will do it, if I'm not mistaken (haven't coded in gtk for a while).

I'd recommend reading the basics of gtk too, it'll help...

---

### Post by bruce89 on 2008-12-15
> **Vadi said:**
> 
```
gtk_button_set_label((GTK_BUTTON) button, "Fire!");[/CODE
Will do it, if I'm not mistaken (haven't coded in gtk for a while).

I'd recommend reading the basics of gtk too, it'll help...

Almost, it's actually:

[CODE]gtk_button_set_label ((GTK_BUTTON (button), "Fire!");
```

All the GTK+ classes have a casting macro with the same template as the one above.

---

### Post by DrPepper836 on 2008-12-15
Thanks Bruce, it worked perfectly.

---

### Post by Vadi on 2008-12-16
> **bruce89 said:**
> Almost, it's actually:

```
gtk_button_set_label ((GTK_BUTTON (button), "Fire!");
```

All the GTK+ classes have a casting macro with the same template as the one above.

Yep thanks for the correction.

---

