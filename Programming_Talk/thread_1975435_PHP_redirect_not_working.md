---
title: "PHP redirect not working"
date: 2012-05-07
forum: Programming Talk
---

### Post by CrusaderAD on 2012-05-07
I need to do a PHP redirect at the bottom of the script after everything executes, so a redirect in the header doesn't work. I tried putting

```
<script type="text/javascript">
<!--
window.location = "http://www.google.com/"
//-->
</script>
```

At the bottom outside the php tags, but it doesn't redirect. Any ideas?

---

### Post by Barrucadu on 2012-05-07
You can redirect with a header, as long as nothing is output.

---

### Post by CrusaderAD on 2012-05-07
> **Barrucadu said:**
> You can redirect with a header, as long as nothing is output.

There is data being outputted that is in turn being printed. So I can't use a header.

---

### Post by v8YKxgHe on 2012-05-07
You should rework your logic ... having data being supplied to the user but then wanting to redirect straight away makes zero sense.

---

