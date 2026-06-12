---
title: "[SOLVED] Nano Editor SpellCheck"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Tart on 2008-09-16
Hi All, 

I really like nano editor, it is simple and easy to use. However when I try to do spell check on it using CTRL+T I get the following error message:

 [ Spell checking failed: Error invoking "spell" ]


How to enable spell check in nano?

In past I tried vim and by default it didn't came with spell check. I had to install vim-full to enable spell check. Is this a similar situation with nano? I couldn't find any other extra packages for it. 
I have both ispell and aspell installed. 


Thank you!

---

### Post by Tart on 2008-09-16
Found solution

```
sudo gedit /etc/nanorc

```

find lines```

## Use this spelling checker instead of the internal one.  This option
## does not properly have a default value.
##
# set speller "aspell -x -c"
``` 

uncomment

---

### Post by gregphil on 2008-09-16
If you like nano you should look at "ne" (the Nice editor) which is available in the package manager.  It is a console (terminal) editor but has many more features than the normal 'small' editor.  And all the keys are mapped to the 'normal' meanings for someone who has been using a Windows computer for 10 years.  (like the arrow keys actually work, backspace and del keys work, etc)

Cheers!

---

### Post by Tart on 2008-09-17
Thank you for your recommendation. I'll check it out

---

