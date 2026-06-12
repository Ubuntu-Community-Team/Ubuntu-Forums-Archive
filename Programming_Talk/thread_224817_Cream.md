---
title: "Cream?"
date: 2006-07-28
forum: Programming Talk
---

### Post by Note360 on 2006-07-28
I just installed cream after using Gvim for a while and what happened? It comes up as GVim with this error message:
```

Error detected while processing function Cream..Cream_init_userdir..Cream_checkdir: 
line   23: 
E484: Can't open file /tmp/v141824/0 
 
 Error: Unable to find a location for user files. 


```

---

### Post by gunksta on 2008-07-28
This is an old, old post but I'm sure someone will have this problem again someday. I got the same error and it took me a few minutes to figure it out, but I figured I should post the answer.

You probably started gvim BEFORE starting cream, which isn't a good idea. You need to delete ~/.viminfo and then cream should work correctly.

---

### Post by KenJean on 2009-09-27
There is another possibility (This just happened to me).

If after installation of cream, the first time you invoke it is as a super-user (e.g. **sudo cream *some-file***) then the  .cream directory will be created with root as owner.

Thereafter, you will always have to invoke cream as a super-user, or you'll get the dreaded Unable-to-find-a-location-for-user-files error.

The solution, of course, is to open a file manager of some sort as root, delete the .cream directory and then invoke cream normally.

-KJ

---

