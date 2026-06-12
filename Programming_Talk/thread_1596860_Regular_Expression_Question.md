---
title: "Regular Expression Question"
date: 2010-10-14
forum: Programming Talk
---

### Post by medic2000 on 2010-10-14
I have this regular expression:

preg_match("/^[A-Za-z&#305;&#304;ÜÖüö&#286;Ç&#350;&#287;ç&#351;\(\)\s]*$/", $word)

I want it to pass only letters, parentheses and one space between words. Space for words like "take heart".

But it allows more than one space(or whitespace) like "take \ \ \ heart".(this forum does not allow it so we can see only one whitespace now). What i need to change to make it correct?

---

### Post by spjackson on 2010-10-14
> **medic2000 said:**
> I have this regular expression:

preg_match("/^[A-Za-z&#305;&#304;ÜÖüö&#286;Ç&#350;&#287;ç&#351;\(\)\s]*$/", $word)

I want it to pass only letters, parentheses and one space between words. Space for words like "take heart".

But it allows limited spaces like "take      heart". What i need to change to make it correct?
Try
```

/^([A-Za-z&#305;&#304;ÜÖüö&#286;Ç&#350;&#287;ç&#351;\(\)]*\s?)+$/

```

---

### Post by medic2000 on 2010-10-17
> **spjackson said:**
> Try
```

/^([A-Za-z&#305;&#304;ÜÖüö&#286;Ç&#350;&#287;ç&#351;\(\)]*\s?)+$/

```

Unfortunately it doesn't work. It still allows more than one whitespace :(

---

### Post by spjackson on 2010-10-17
> **medic2000 said:**
> Unfortunately it doesn't work. It still allows more than one whitespace :(
Ah yes, sorry, so it would. Change the * after the ] to a + and that should solve it.

---

### Post by medic2000 on 2010-10-17
> **spjackson said:**
> Ah yes, sorry, so it would. Change the * after the ] to a + and that should solve it.

This works great! Thank you so much! :)

---

