---
title: "phrasing a website"
date: 2008-08-13
forum: Programming Talk
---

### Post by dtommy79 on 2008-08-13
Hi,

I'd like to store the most common phrases of my website in separate language files. how can I do that?

Thanks

---

### Post by Reiger on 2008-08-13
Right inside your website code if you want to!

[html]
<style type="text/css">
.show { display: visible; }
.hide { display: none; }
</style>
[omitted code]
<div lang="en" class="hide">
A hornet is a kind of wasp.
</div>
<div lang="nl" class="show">
Een hoornaar is een soort wesp.
</div>
[/html]

Include some JavaScript file which filters language based on preset preferences (Cookie!) by switching certain languages-sensitive tags to "hide" and others to "show" ...

---

