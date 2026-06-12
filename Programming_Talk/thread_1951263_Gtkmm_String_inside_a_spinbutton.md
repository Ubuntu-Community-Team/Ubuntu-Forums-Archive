---
title: "Gtkmm: String inside a spinbutton?"
date: 2012-04-02
forum: Programming Talk
---

### Post by fallenshadow on 2012-04-02
I just want to know is this possible with spinbuttons? It would be the perfect solution if I could do this.

As far as I know Spinbuttons support doubles but I don't think they can support other data types.

---

### Post by r-senior on 2012-04-02
You are correct, the methods of GtkSpinButton (and the associated GktAdjustment) only work with numbers.

Would GtkComboBox with the has-entry property set false do the job?

---

### Post by fallenshadow on 2012-04-08
Thanks, I think in the meantime I will stick with spinbuttons but have a label at the side of it. :)

---

