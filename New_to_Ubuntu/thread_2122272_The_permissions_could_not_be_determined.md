---
title: "The permissions could not be determined ?"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by 825522 on 2013-03-04
Hi, everyone Im trying to unlock my drive for i can put themes in there  but everytime I try it says (The permissions of then my name and says  could not be determined.) Im I doing somthing wrong. oh and i cant find the theme folder. thanks

---

### Post by ajgreeny on 2013-03-04
More details please of exactly what you're trying to do, and what you mean by "I'm trying to unlock my drive"?

Where in the filesystem are you attempting to put the themes?

---

### Post by 825522 on 2013-03-04
Hi, sorry about that, Im trying to put them in the theme folder on my file system, I have tryed to put the themes in user, share ,theme and when I do that noting happens, and then I found another .theme folder in my file system, but it keeps telling me that im not the Admin, but it says on my user name that I am a Admin, so errrors keep coming up and it want let me put any files in that .theme folder, Iv been searching the net and I cant find the way how to unlock my file system. I hop that helps and sorry about not giveing you more info, thanks

---

### Post by Impavidus on 2013-03-04
You have to start your file manager, nautilus I presume, with root privileges. Open a terminal and type **gksudo nautilus**. Then you can copy your themes to the themes directory. You may be the admin, but you have to tell the systen explicitly you want to use your privileges.

Warning: using nautilus with root privileges makes it very easy to ruin your system.

---

### Post by ManamiVixen on 2013-03-04
But Impavidus, he also says "He cannot access his own folder" that is strange.

---

### Post by 825522 on 2013-03-04
Thanks everyone for your post i got evey thing working now thanks agine:)

---

