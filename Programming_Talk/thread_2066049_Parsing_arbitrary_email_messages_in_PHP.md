---
title: "Parsing arbitrary email messages in PHP"
date: 2012-10-03
forum: Programming Talk
---

### Post by pcman312 on 2012-10-03
Can anyone recommend any good mail parsing libraries in PHP? I need to be able to parse emails of various encoding types (everything from 8bit and quoted printable to mime multipart messages) so they can be processed and rendered.
I've tried using this one: [https://github.com/plancake/official-li](https://github.com/plancake/official-li) … ail-parser but it doesn't handle multipart messages.
I'm exploring the possibility of using the mailparse library, but I'm a bit hesitant since parts of it are described as experimental. Plus it appears that it needs the emails on the file system, which I don't currently have and would prefer not to do.

---

### Post by pcman312 on 2012-10-04
No one knows of a good email parsing library in PHP?

---

### Post by epicoder on 2012-10-05
All I've seen are recommendations for plancake. I've also seen some hints that Mail in PEAR might be able to do it. However, if you're up for it, you might consider writing your own using [RFC2822]("http://www.faqs.org/rfcs/rfc2822.html").

---

### Post by pcman312 on 2012-10-08
> **sh228 said:**
> All I've seen are recommendations for plancake. I've also seen some hints that Mail in PEAR might be able to do it. However, if you're up for it, you might consider writing your own using [RFC2822]("http://www.faqs.org/rfcs/rfc2822.html").
Thanks for the info. Unfortunately, I don't have the time to implement one from scratch :mad:

---

