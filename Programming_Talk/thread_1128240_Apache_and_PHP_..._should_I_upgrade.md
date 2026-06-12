---
title: "Apache and PHP ... should I upgrade?"
date: 2009-04-17
forum: Programming Talk
---

### Post by skullmunky on 2009-04-17
I'm doing this little php project, and client's box is running Apache 1.3 and PHP 4.4.8.  My instinct is to advise them to upgrade, not least because I'm having to do more work digging up old releases of things that are compatible :)  Nothing else is on there, so no worries about breaking existing code.  

But are there other compelling reasons to upgrade, like security, future support and patches, etc., or is it fine if ain't broken?

---

### Post by Reiger on 2009-04-17
Well it's ancient. What more excuse do you need. ;)

---

### Post by sp0nge on 2009-04-17
From a security standpoint, this is a REQUIREMENT.. 

outdated PHP and Apache can be (read- ARE) extremely vulnerable if facing the world. There are vulnerabilities in both when not fully patched that can appear to be a juicy target for an attacker. These can be susceptible to buffer overflows, remote code execution, and data aggregation- and that's just off top of my head.

Upgrade..

---

### Post by skullmunky on 2009-05-04
Good, that's what I thought.  Just wanted to make sure I wasn't pushing unnecessary stuff on them.  

boy, trying to do all this over ssh into an osx server sure makes me appreciate how good we've got it... :)

---

