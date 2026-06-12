---
title: "Gtk+ Understanding Multithread Application"
date: 2015-02-23
forum: Programming Talk
---

### Post by kr_Bahadr on 2015-02-23
[COLOR=#323D4F][FONT=Lucida Grande]Hello forum,[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]I want to understand multithreading process in gtk+. I searched on net and I learn that, gtk main is automatically lock global mutex. And at the and of main loop mutex become unlocked. So I can't analyze following condition : [/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]when I call g_timeout_add in the main loop, what is the program's behavior. [/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]I think when gtk_main unlocked the mutex, timeout function lock mutex and then timeout function is executed. When timeout function is finish, gtk main loop executed again. I want to ask that, I am wrong, or I am right ? [/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]and then I have another question : [/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]in this case, If I create a thread in g_timeout_add(), what is the program behavior ? I am no idea about this condition ? [/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]and the last question (if you still read, thanks a lot :) )[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]I learn that g_timeout_add lock global mutex automaticaly, when I create a tread in timeout func, and try to lock mutex with gdk_treads_enter in created task, what is the mutex condition ?[/FONT][/COLOR]


[COLOR=#323D4F][FONT=Lucida Grande]Please help me my friends :) [/FONT][/COLOR]


[COLOR=#323D4F][FONT=Lucida Grande]thanks a lot :)[/FONT][/COLOR]

---

