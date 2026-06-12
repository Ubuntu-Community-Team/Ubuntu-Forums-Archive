---
title: "&quot;export&quot; part of an svn repository"
date: 2007-01-30
forum: Programming Talk
---

### Post by tomane on 2007-01-30
Hello,
"export" is not the correct word but that's the best I could come up with.
I have one repository with 2 top level directories, say, "foo" and "bar".
They are somewhat unrelated so want to take everything under "foo" and create a separate repository for "foo", preserving it's revision history. This would end up with a repository with revision history for "foo" and another one for "bar".
Can this be done?

cheers,
--to

---

### Post by stoffe on 2007-01-30
You should be able to find all info you need here: [http://svnbook.red-bean.com/en/1.0/ch05s03.html](http://svnbook.red-bean.com/en/1.0/ch05s03.html)

(Sorry, don't remember exactly how myself, maybe it had to do with "svnadmin dump").

---

### Post by tomane on 2007-01-31
Thanks, stoffe,
It's not done with one trivial step but the info that I needed is right there!

cheers,
--to

---

