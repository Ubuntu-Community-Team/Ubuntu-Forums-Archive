---
title: "(GTK C)how can i fill an entire button with an image?"
date: 2008-03-13
forum: Programming Talk
---

### Post by pacofvf on 2008-03-13
i have this button:
[IMG]http://antares.dci.uia.mx/~ic06fvf/PM/button.jpg[/IMG]
```

gtk_button_set_image(GTK_BUTTON(examplebutton2),image);

```
how can i fill an entire button with an image?(gtk   c )

thanks.

---

### Post by dempl_dempl on 2008-03-13
I'm assuming you want to have a fancy icon instead of a plain button. In those situations ,  I've usually used an image component as a button. I really don't know GTK+ , but I'm sure there is such widget  in that framework.  All components have OnClick event / slot . Also,  I always use slots like  OnHover in order to highlight an image a little bit, when user hovers the mouse over a button

---

