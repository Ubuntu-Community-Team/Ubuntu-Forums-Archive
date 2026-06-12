---
title: "appending data after excutable's binrary"
date: 2010-09-29
forum: Programming Talk
---

### Post by SIGTERMer on 2010-09-29
I know I can append data at the end of a binary without effecting its normal behavior (probably because program size is mentioned in the ELF header somehow), but is it an acceptable practice? 

And how cross-platform-y is this technique?

---

### Post by worksofcraft on 2010-09-29
I think it is very acceptable practice. For instance follow this  very informative [vid on youtube]("http://www.youtube.com/watch?v=5-8h6eOwKwA") showing how to embed the gui definition into your executable so that the .glade file isn't exposed to the user.

---

### Post by SIGTERMer on 2010-09-30
> **worksofcraft said:**
> I think it is very acceptable practice. For instance follow this  very informative [vid on youtube]("http://www.youtube.com/watch?v=5-8h6eOwKwA") showing how to embed the gui definition into your executable so that the .glade file isn't exposed to the user.

Thanks worksofcraft for your reply. it seems this technique is indeed widely accepted (microsoft's exe format supports it). another question, will appending data make an executable conflict with the elf specification?

---

