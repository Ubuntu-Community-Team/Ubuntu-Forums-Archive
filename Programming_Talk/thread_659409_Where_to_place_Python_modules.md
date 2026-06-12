---
title: "Where to place Python modules?"
date: 2008-01-05
forum: Programming Talk
---

### Post by Mr.popo on 2008-01-05
Ive got my own python modules which I need to place somewhere so python can read them. Ive got two questions.
1. Wheres the best place to put modules?
2. It wont let me add modules to /usr/lib/python2.5?

Thanks
Mr.popo

---

### Post by Wybiral on 2008-01-05
1. For your own projects (if you're writing a module used in another project) just add it to the project folder (you can make a folder for it using the module name, and name the main file __init__.py)

2. It should, but it will require root permission to move something there (and you should use the "site-packages" folder and use the module name as the folder with the "__init__.py" file described above)

---

### Post by Mr.popo on 2008-01-05
Ok thankyou very much :)

---

