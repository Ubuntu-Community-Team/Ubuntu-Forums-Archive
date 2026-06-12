---
title: "how do i log on- mouseless/ users order change"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by blesbok on 2008-09-03
two users are displayed on the logon screen: **childre**n and **parents**. to log on to parents, my only option is to use the mouse; tab with any other key only highlights the top menu item: **childre**n. up or down arrow has the same effect as enter.  one solution would be to change the display order to have **parents** on top; is this display alphabetical by default? (the children don't mind using the mouse :) Oh, i could type my user name, but that's a pain too; rather type password only if i can...

---

### Post by chrisN_uk on 2008-09-03
Hmm, you could try editing /etc/passwd

Near the bottom you should have two lines like:

parents:x:1000:1000:Parents,,,:/home/parents:/bin/bash
children:x:1000:1000:Children,,,:/home/children:/bin/bash

but  they will be slightly different. 
Changing their order may solve your problem i.e. change them to 

children:x:1000:1000:Children,,,:/home/children:/bin/bash
parents:x:1000:1000:Parents,,,:/home/parents:/bin/bash

instead, but don't change the lines themselves. Do back up though as I am no expert and this may do something strange! (though it probably wont)

---

