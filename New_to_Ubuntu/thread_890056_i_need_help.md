---
title: "i need help"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by krimlon on 2008-08-14
E: Malformed line 54 in source list /etc/apt/sources.list (type)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

how do i fix this?

---

### Post by tamoneya on 2008-08-14
please post the result of running this command in terminal:```
cat /etc/apt/sources.list
```

Also next time you make a post try to make the thread topic more descriptive.  95% of the posts in this forum are asking for help.  Instead I would have recommended: "E: Malformed line 54 in source list /etc/apt/sources.list (type)" or "E: _cache->open() failed, please report."

---

### Post by Riffer on 2008-08-14
Basically its saying that on line 54 of your sources list is something wrong.

If you open a terminal ( found in Applications > Accessories) and paste in tamoneya's command, we can help you trouble shoot.

Also another fix is to paste this into your terminal 

sudo gedit /etc/apt/sources.list

you will be asked for your user password and after giving that your sources list will open up in a text editor.  On line 54 you can put a # in front of it which will stop that line from executing.  Save and close out.

Hope that helps

---

### Post by krimlon on 2008-08-14
Thanks i appreciate the help got it fixed

---

### Post by bodhi.zazen on 2008-08-14
> **tamoneya said:**
> please post the result of running this command in terminal:```
cat /etc/apt/sources.list
```Also next time you make a post try to make the thread topic more descriptive.  95% of the posts in this forum are asking for help.  Instead I would have recommended: "E: Malformed line 54 in source list /etc/apt/sources.list (type)" or "E: _cache->open() failed, please report."

Just as an aside, since we know the "bad" line, rather then listing the entire file we can :

```
cat -n /etc/apt/sources.list | grep ^54
```

This was we can then say change that line to .... 9without having to count out 54 lines or reading / scanning the entire file ...)

Just a thought, HTH

---

