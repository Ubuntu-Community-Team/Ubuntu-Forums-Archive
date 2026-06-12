---
title: "Some CSS issues..."
date: 2009-12-11
forum: Programming Talk
---

### Post by gjoellee on 2009-12-11
Hi, I am currently creating a new theme for my website [www.stupidreality.org](www.stupidreality.org) 

I am having some issues especially with the top menu-bar. I want to move the links over to the left a certain amount of pixels, but I just can't get them to move. Any help plz?

---

### Post by joes7 on 2009-12-11
Use <align> and </align>. For example, if you wish them to be aligned to the right, write:

```

align : right

```

I think that should work, try by experimenting with HTML align tags and such.

---

### Post by gjoellee on 2009-12-11
> **joes7 said:**
> Use <align> and </align>. For example, if you wish them to be aligned to the right, write:

```

align : right

```

I think that should work, try by experimenting with HTML align tags and such.

Does not work. Here is the new CSS.

---

### Post by v8YKxgHe on 2009-12-11
What exactly are you trying to do? Fyi - posting the CSS is pointless, we can already see it and alter it here ;)

> I think that should work, try by experimenting with HTML align tags and such.

Styling is best done with CSS.

---

### Post by gjoellee on 2009-12-11
I want to move the links, over to where the main content of the website starts (I mean like move the links over to right above the main content area on the website).

See attachment:

---

### Post by v8YKxgHe on 2009-12-11
Ok, easy. On #page-bar add in 'margin: 0 auto; width: width_of_your_site'

---

### Post by gjoellee on 2009-12-11
> **AlexC_ said:**
> Ok, easy. On #page-bar add in 'margin: 0 auto; width: width_of_your_site'

Thanks! :D

---

### Post by Can+~ on 2009-12-11
> **joes7 said:**
> Use <align> and </align>.

Align is deprecated on HTML4.

---

