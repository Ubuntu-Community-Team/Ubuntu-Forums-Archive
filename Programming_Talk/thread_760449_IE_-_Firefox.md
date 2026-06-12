---
title: "IE - Firefox"
date: 2008-04-20
forum: Programming Talk
---

### Post by Tux.Ice on 2008-04-20
Hey, i was wondering how you could make your index file check to see what browser you are using and forward to a page

for example if it was IE you would go to /ie/index.html
but if it was firefox it would go to /firefox/index.html


anyway to do this?

---

### Post by nvteighen on 2008-04-20
> **Tux.Ice said:**
> Hey, i was wondering how you could make your index file check to see what browser you are using and forward to a page

for example if it was IE you would go to /ie/index.html
but if it was firefox it would go to /firefox/index.html


anyway to do this?

Yes: with JavaScript's navigator object. This code will show what browser you're using, for example:

```

<script type="text/javascript">
<!--
var name = navigator.AppName;
document.write(browsername);
//-->
</script>

```

So to redirect, you must tell the script to compare browsername with the proper AppName and do a window.location.replace("http://<whatever>...")

---

### Post by Tux.Ice on 2008-04-20
HOw do i make javascript go to /ie

---

### Post by LaRoza on 2008-04-20
> **Tux.Ice said:**
> HOw do i make javascript go to /ie

```

window.location = "url";

```

---

### Post by nvteighen on 2008-04-20
> **LaRoza said:**
> ```

document.location = "url";

```
Isn't it window.location?

@OP: Anyway, you should first check how each browser identifies itself. All I know is that IE calls itself "Microsoft Internet Explorer". Firefox may be "Mozilla", but I'm not sure.

---

