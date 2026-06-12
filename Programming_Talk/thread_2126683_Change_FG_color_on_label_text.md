---
title: "Change FG color on label text"
date: 2013-03-17
forum: Programming Talk
---

### Post by codyj110 on 2013-03-17
Hi i'm new to GTK3 and have tried various methods of chaning the text on my label. If someone could please show me a sample text of how i could make this works.

        
self.entry1 = self.builder.get_object('entry1')
self.label1 = self.builder.get_object('label1')
    def on_entry1_activate(self,widget):
                  text = self.entry1.get_text()
                  self.label1.set_text(text)
       
On entry1 activate i would like to change label1 text color to red. How is this done?

Thank you in advance

---

### Post by StephenF on 2013-03-18
self.label1.set_markup('<span foreground="red">label text</span>')

All label text must be escaped html style e.g. < = &lt;

---

### Post by codyj110 on 2013-03-18
that does change the color of the FG, but also overwrites the entry widget text. is three a way to draw from the variable text using the markup code?

---

