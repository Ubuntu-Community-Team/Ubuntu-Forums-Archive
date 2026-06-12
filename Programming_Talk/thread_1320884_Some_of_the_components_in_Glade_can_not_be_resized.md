---
title: "Some of the components in Glade can not be resized."
date: 2009-11-09
forum: Programming Talk
---

### Post by Somme on 2009-11-09
I'm using the default Glade version from Karmic repositories but something annoys me - I can't resize some of the designer components. For example, combo box - the only way to resize it is to go into properties and type it's size/location manually.

Is there a way to fix this ?

---

### Post by samjh on 2009-11-09
I don't understand what you mean by "resize some of the designer components".

GTK+ only uses layout managers, not absolute positioning.  Which means the size of individual components are dependent on the size of the components around it.

---

### Post by Somme on 2009-11-09
> **samjh said:**
> I don't understand what you mean by "resize some of the designer components".

GTK+ only uses layout managers, not absolute positioning.  Which means the size of individual components are dependent on the size of the components around it.

Not if you use *[COLOR=DimGray]fixed layout[/COLOR]*.

---

### Post by samjh on 2009-11-09
Oh, I see.  So you want to be able to graphically alter the size and position of a component within a Fixed container?  I'm afraid this is not the right place to ask for that feature.  Try the [glade-devel]("http://lists.ximian.com/mailman/listinfo/glade-devel") mailing list.

---

### Post by Somme on 2009-11-09
> **samjh said:**
> Oh, I see.  So you want to be able to graphically alter the size and position of a component within a Fixed container?  I'm afraid this is not the right place to ask for that feature.  Try the [glade-devel]("http://lists.ximian.com/mailman/listinfo/glade-devel") mailing list.

Yes, that's what I'm after for. Basically, it works for the most of components, except combo box ( there was another component which can not be resized, tough, I don't remember which one ). For now, thanks for the link - I'll definitely give them a shout :)

---

### Post by samjh on 2009-11-09
Hmmm... I can't graphically resize any objects within a Fixed container.  Obviously it can be done via typing the size and position in the Properties section, but that's not what you're after.

---

### Post by Somme on 2009-11-09
> **samjh said:**
> Hmmm... I can't graphically resize any objects within a Fixed container.  Obviously it can be done via typing the size and position in the Properties section, but that's not what you're after.

You need to hold down the Shift key ( which activates the ability to move or resize your components ).

---

### Post by samjh on 2009-11-09
Ah ha!  Thanks for that.  Being a Qt guy, I hardly use Glade and my ignorance shows. :)

Looks like just a peculiarity with Combobox then.

---

