---
title: "[C] Empty #include in examples"
date: 2010-08-06
forum: Programming Talk
---

### Post by SpinningAround on 2010-08-06
I have noticed that a few example in C lack any included libraries only #include is shown. Like the following example, is there some software that autoimport necessary libraries or something else?
[http://blog.sacaluta.com/2007/08/gtk-system-tray-icon-example.html](http://blog.sacaluta.com/2007/08/gtk-system-tray-icon-example.html)

---

### Post by Bachstelze on 2010-08-06
Not AFAIK.  The code snippet is probably just a "template", where you have to fill in the blank after [font=monospace]#include[/font] to suit your needs.

---

### Post by interval1066 on 2010-08-06
> **Bachstelze said:**
> Not AFAIK.  The code snippet is probably just a "template", where you have to fill in the blank after [font=monospace]#include[/font] to suit your needs.

I've seen some of those too. I guess you're supposed to fill in the appropriate header but it doesn't seem to make sense in some of the examples. Seems like it'd be easier to leave them in. I dunno, my 2 cents.

---

### Post by johnl on 2010-08-06
The problem is that the person who wrote the tutorial forgot that their webpage is not properly escaping the left and right carets in  ```
<something.h>
```, so it's interpreted as an HTML tag and not displayed by the browser.

If you check 'view source' in Firefox, you'll see that the author actually wrote:

```

#include <gtk/gtk.h>

```

---

### Post by interval1066 on 2010-08-06
Doh!

---

### Post by SpinningAround on 2010-08-07
> **johnl said:**
> The problem is that the person who wrote the tutorial forgot that their webpage is not properly escaping the left and right carets in  ```
<something.h>
```, so it's interpreted as an HTML tag and not displayed by the browser.

If you check 'view source' in Firefox, you'll see that the author actually wrote:

```

#include <gtk/gtk.h>

```

thanks :)

---

