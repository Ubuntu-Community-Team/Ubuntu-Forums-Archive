---
title: "[SOLVED] Can BASH do this???"
date: 2008-06-22
forum: Programming Talk
---

### Post by Barriehie on 2008-06-22
Hello Everyone,

My .sheep directory is getting huge!  Can BASH go through there and randomly delete some number of files?

Thank You,
Barrie

---

### Post by LaRoza on 2008-06-22
What do you mean by "random"?

It would be easy, I think, to just delete a set number. Deleting random files is possible, but I don't see why that would be more desirable.

---

### Post by Barriehie on 2008-06-22
> What do you mean by "random"?I mean to just pick some files.  Upon further thought deleting the oldest ones first would work.  Not sure if 'easy' for LaRoza will be easy for me but I'll take the borg's word for it and see what I can drum up code wise! :)

Barrie

---

### Post by stroyan on 2008-06-22
Here is a really short command to remove up to six files from ~/.sheep/ in
order from oldest to newest.  Whenever you are trying out a script like
this it is wise to try it with an 'echo' command instead of a real 'rm'
command so that surprises won't be painful ones.
```

cd ~/.sheep;while read file;do rm "$file";done <<< "$(ls -1tr | head -6)"

```

---

### Post by rye_ on 2008-06-23
> **Barriehie said:**
> I mean to just pick some files.  Upon further thought deleting the oldest ones first would work.  Not sure if 'easy' for LaRoza will be easy for me but I'll take the borg's word for it and see what I can drum up code wise! :)

Barrie

eeerrrrrrr. 
if your not that bothered about which files why not just delete them all periodically?

---

