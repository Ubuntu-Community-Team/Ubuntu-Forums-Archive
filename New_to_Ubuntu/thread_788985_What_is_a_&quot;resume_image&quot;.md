---
title: "What is a &quot;resume image&quot;"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by DBrocks on 2008-05-10
Hey guys.

I am running Hardy SE, and whenever it boots, it displays the following message

kinit: no resume image found on /dev/sda5
kinit: doing normal boot.

What is a resume image? and what does it do?

Thanks

~Dan

---

### Post by brettg on 2008-05-10
When you hibernate a "resume image" is created (basically a snapshot of your RAM contents) 

At boot it checks for one, if one is there it resumes otherwise it does a normal boot

---

### Post by DBrocks on 2008-05-10
Okay thanks.

---

