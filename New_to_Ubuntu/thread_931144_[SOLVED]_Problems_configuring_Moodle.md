---
title: "[SOLVED] Problems configuring Moodle"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by k3lt01 on 2008-09-27
Hi.

I have just gone and installed Moodle and when it comes to the configuration within firefox I come across a problem.

These are the steps I have taken:
1) Installed LAMP
2) Installed Moodle (Synaptic installed all the remaining dependencies).
3) Followed the Ubuntu Wiki pages and set up folders and permissions
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[https://help.ubuntu.com/community/MySQLMoodle](https://help.ubuntu.com/community/MySQLMoodle)
4) Open firefox and try to go to [http://localhost/moodle/admin](http://localhost/moodle/admin) and I get a download prompt asking what to do with the phtml file from [http://localhost](http://localhost).

Now [http://localhost](http://localhost) works ok but as soon as I try to go to localhost/moodle I get the download prompt.

Nothing like this happened in Gutsy or Feisty but I have a gut feeling the issue is firefox. I have checked the Applications in firefox's preferences but nothing matches it.

Anyone have any ideas what it could be?

I will add that I will use this for a job interview if I can get it working properly, otherwise I might have to revert back to Feisty or Gutsy to show it.

---

### Post by k3lt01 on 2008-09-27
Solved it, I went through the entire procedure again to check it each step of the way, I had already done this anyway. Anyway I go to clearing firefox's cache and it works. So for some reason my firefox cache wasn't clearing itself properly.

---

