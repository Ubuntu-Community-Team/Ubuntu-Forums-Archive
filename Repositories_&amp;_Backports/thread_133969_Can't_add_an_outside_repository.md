---
title: "Can't add an outside repository"
date: 2006-02-21
forum: Repositories &amp; Backports
---

### Post by yootje on 2006-02-21
When I'm in the Synaptic Manager, and click, settings>repositories, There isn't a "new" button. Just seven standard repos and some buttons like add, remove, settings, etc. How can I add an oustide repo?

---

### Post by hajk on 2006-02-21
Fire up your editor, like "sudo gedit /etc/apt/sources.list", and add a repository -- more likely -- uncomment some of the ones already there. Then, "sudo apt-get update" (or reload in Synaptic), and you're all set.

---

### Post by Marshall2day on 2006-02-21
Click Add and then click Custom in the box that pops up. Here you can add any repo you like.

---

### Post by yootje on 2006-02-21
[QUOTE=Marshall2day]Click Add and then click Custom in the box that pops up. Here you can add any repo you like.[/QUOTE]
It works, thanks for your help! :)

---

### Post by tomcat1965 on 2006-10-29
This doesn't work with 6.10,clicking add will not let you add any repositories,unlike 6.06 there is no custom button:(
Typing sudo gedit/etc/apt/sources.list will not let you view source lists as it's not a valid command.](*,)

---

