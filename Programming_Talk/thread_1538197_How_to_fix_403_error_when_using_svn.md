---
title: "How to fix 403 error when using svn?"
date: 2010-07-24
forum: Programming Talk
---

### Post by Murrquan on 2010-07-24
Hi, everyone! I'm trying to upload a plugin to the WordPress.org svn repository following these instructions: [http://wordpress.org/extend/plugins/about/svn/]("http://wordpress.org/extend/plugins/about/svn/")

Only the first shaded block of instructions, for "Task 1," is relevant to this. I imagine it's pretty basic stuff if you're used to version control!

Problem is, when I do the svn check-in here's what I get:

```
Authentication realm: <http://svn.wp-plugins.org:80> WordPress.org Subversion
Password for 'feathertail':
Adding         trunk/lightspeed-links.php
svn: Commit failed (details follow):
svn: Server sent unexpected return value (403 Forbidden) in response to CHECKOUT request for '/!svn/ver/252019/lightspeed-links/trunk'
```

Any idea what could cause this or how I could fix it? No one there seems to want to answer, so I thought I'd give the Ubuntu Forums a shot ... hey, I'm using svn to develop on Ubuntu, so it counts, right? >.>

---

### Post by jobix on 2010-07-25
> **Murrquan said:**
> 
No one there seems to want to answer, 

- Where is "there"?

- Did you try svn.haxx.se?

---

### Post by Murrquan on 2010-07-25
"There" is the WordPress Support forums: [LINK]("http://wordpress.org/support/topic/427700")

And no, I haven't tried that yet. Thanks!

---

