---
title: "UNIX-Running Editors in the Background&#8207;"
date: 2009-05-22
forum: Programming Talk
---

### Post by superdan006 on 2009-05-22
Hi,  
In UNIX, I want to alias gedit so that it will run in the background. Ie.,  

alias gedit='gedit *file* &'  

Do you have any ideas? I have had a lot of trouble with this one.  
Cheers, 
-Dan

---

### Post by unutbu on 2009-05-22
If file is a string which never changes, then you could do
```

alias ge='gedit file &'
```

If you want to allow file to change then you could define a function in your .bashrc like this:
```

ge() {
    gedit "$@" &
}
```

and use it like this:
```

ge filename
```

---

