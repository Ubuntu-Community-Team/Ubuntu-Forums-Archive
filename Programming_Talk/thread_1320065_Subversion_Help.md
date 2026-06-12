---
title: "Subversion Help"
date: 2009-11-08
forum: Programming Talk
---

### Post by mthalis on 2009-11-08
I installed subversion my Ubuntu 9.10 desktop referring this tutorial [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

But this tutorial not mention subversion folder structure. I also refer the Internet but couldn't get good idea about folder structure. Please help me.
I use this subversion for maintain my Java program(Netbeans), this subversion also use my friends. 

Please explain folder structure ?

---

### Post by mthalis on 2009-11-09
After reading Internet trunk, tags and branches are essential is it correct?

Hear how I created those folders

sudo svn mkdir file:///srv/svn/myproject/trunk -m "Created project directory"
sudo svn mkdir file:///srv/svn/myproject/tags -m "Created tags directory"
sudo svn mkdir file:///srv/svn/myproject/branches -m "Created branches directory"

After crating those folders, I can't see those folders inside myproject folder but if I go [http://192.168.1.3/svn/myproject](http://192.168.1.3/svn/myproject) then I can see those folders.

---

### Post by v8YKxgHe on 2009-11-09
You don't *have* to have any folders at all. It's just common to have 'trunk' 'branches' and 'tags' to keep your projects in. You'd add them via:

svn mkdir trunk branches tags

Then commit to your repository:

svn commit -m "Added initial structure"

[http://svnbook.red-bean.com/en/1.5/index.html](http://svnbook.red-bean.com/en/1.5/index.html) <- great guide for SVN.

---

