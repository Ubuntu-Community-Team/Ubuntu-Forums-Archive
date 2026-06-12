---
title: "redrecting a page using php"
date: 2007-12-13
forum: Programming Talk
---

### Post by Nolander on 2007-12-13
hi all,

I want a page to display some text and then redirect the page when its finished. i tried using the header but u cant display the text.

ta,
nolander.

---

### Post by LaRoza on 2007-12-13
There are several ways of doing it, none involve php.

The first, is to use ECMAScript (JavaScript), the second is a meta redirect.

In JavaScript:

[php]
<script type="text/ecmascript">
setTimeOut("document.location = 'http://laroza.freehostia.com/home'",5000);
</script>
[/php]

If you use it in an external file:

[php]
window.onload = function()
{
    setTimeOut("document.location = 'http://laroza.freehostia.com/home'",5000);
}
[/php]

Put this in the head of the web page:
```

<script type="text/ecmascript" src="script/script.js"></script>

```

META redirects are not recommended. When using the script, post a link, in case it is disabled.

The PHP header() function will only work when nothing has been sent back, [http://laroza.freehostia.com](http://laroza.freehostia.com), redirects immediately to [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

---

