---
title: "Javascript ternary operator: Multiple expressions possible?"
date: 2010-11-11
forum: Programming Talk
---

### Post by Krupski on 2010-11-11
**[COLOR="Red"]NOTE: This is not homework and I am not a student.[/COLOR]**

Hi all,

Simple question: Is it possible to put several expressions inside a single condition when using the ternary operator in Javascript?

Normally, it's done like this:

a=10 ? a=20 : a=10;

But, what I want to do is this:

a=10 ? (a=20; b='Twenty') : (a=10, b='Ten');

See? I want to do TWO (or more) things for each condition. Is this possible in Javascript? And if so, how to do it?

The actual use for this is:

```
/**
* Toggle WYSIWYG / textarea
**/
function toggle(a)
{
    var e = tinyMCE.get('message'); /* editor */

    e.isHidden() ? e.show() : e.hide(); /* toggle show/hide */
    e.isHidden() ? a.value = 'WYSIWYG' : a.value = 'Textarea'; /* toggle button label */
}
```

...which is called by this:

```

<input type="button" value="Textarea" class="button2" onclick="toggle(this);" />

```

What I hope to do is use only one ternary line and set BOTH "show/hide" AND "wysiwyg/textarea" at the same time.

Possible?

Thanks!

-- Roger

---

### Post by Reiger on 2010-11-12
Something to that effect is certainly possible, but why in the name of all that is good sense would you choose that rather than a simple easy-to-understand if statement?

```

if(e.isHidden()) {
  // do hidden branch
}
else {
  // do shown branch
}

```

---

### Post by Krupski on 2010-11-12
> **Reiger said:**
> Something to that effect is certainly possible, but why in the name of all that is good sense would you choose that rather than a simple easy-to-understand if statement?


Well, I originally had if{}else{} code and whenever I see that, I get the feeling that it would be simpler to use the ternary operator.

But then when I went to write it, I found I needed to do two operations per case and just wondered if it was possible.

It was 98% curiosity. :)

---

