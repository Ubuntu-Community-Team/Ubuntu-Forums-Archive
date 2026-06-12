---
title: "html/php: creating tabs on webpage without navigating to new page"
date: 2009-02-13
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-13
Dear all,

I am a developing a webpage using html/php. I have a side bar created, with some buttons in the sidebar. I wish to make it such that when you click on each button, the main portion of the webpage displays different content (which dynamically comes from php code).

Is there a way to do this without making each button a link to a different webpage? Because this seems somewhat inefficient...

Thanks,

Tom

---

### Post by hessiess on 2009-02-13
> **qmqmqm said:**
> Dear all,

I am a developing a webpage using html/php. I have a side bar created, with some buttons in the sidebar. I wish to make it such that when you click on each button, the main portion of the webpage displays different content (which dynamically comes from php code).

Is there a way to do this without making each button a link to a different webpage? Because this seems somewhat inefficient...

Thanks,

Tom

1) use a URL vairiable i.e. ```
http://www.domain.whatever/index.php?page=number
```

2) use AJAX

3) Frames(not advised)

---

### Post by Tibuda on 2009-02-13
You better use AJAX with a traditional link if the browser has disabled javascript or xmlhttprequest.

---

