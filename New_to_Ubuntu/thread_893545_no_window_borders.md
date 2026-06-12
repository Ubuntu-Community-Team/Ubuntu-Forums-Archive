---
title: "no window borders"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by shashank.ks on 2008-08-18
hi ,
    Some times when i which ever application i open does't contain any border. i am not abel to move the any window any where and to close i have to use alt + f4 combination. If i restart the computer the problem goes away.

I have included the screen shot of my desk top with vlc player having no border. I think it is the problem with the gtk. No idea where to start.

---

### Post by JillSwift on 2008-08-18
Something's crashing your window decorator.

You can start it again from a terminal or runline (ALT-F2):```
metacity --replace &
``` ... Unless you're running another decorator, like Emerald under Compiz. It would help to find a resolution if you'd let us know what you're running and on what. :) 

BTW, you can move undecorated windows by holding the ALT key and dragging, and access the window control menu by holding the ALT key and right-clicking on the window.

---

### Post by timcredible on 2008-08-18
i've seen that when going from emerald (compiz window decorator) to metacity (gnome standard window decorator).  are you using the 3d desktop effects?

---

### Post by shashank.ks on 2008-08-18
Yes i have 3d desktop. When i ran the compiz window manger  all borders came back. But i dont know why this is happening...? (sudden disapperance of borders) .jillswift talked about the somethings crashing my window decorator. Is there any logs i can look in to so that i can figure what is the cause problem? Thanks for the help.

---

