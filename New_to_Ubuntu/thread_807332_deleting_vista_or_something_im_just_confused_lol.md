---
title: "deleting vista? or something im just confused lol"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by roflatlife on 2008-05-25
i have wubi right now, which lets me use ubuntu and vista.
if i were to delete vista, wubi would also be gone because i saved it on vista, right?
also
let's say i am dual booting between vista and ubuntu. if i were to delete vista, would anything really drastic happen? or would i just have a lot of free space after that.
thanks for the help (if anyone responds)
sorry for sounding like a noob lol

---

### Post by sayakb on 2008-05-25
If you dual boot and then delete vista, you will just have a free partition with absolutely no effect on ubuntu. 
Though remember to remove the grub entry for Vista :lolflag:

---

### Post by roflatlife on 2008-05-25
uh what's a grub entry?
sorry im a total computer noob

---

### Post by sayakb on 2008-05-25
Grub is the bootloader for Linux. When you have vista+ubuntu, grub would provide an option for you to either boot into ubuntu for Vista. So if you remove vista, the grub option would remain there (though it shall be ineffective) and you have to manually remove it by editting the /boot/grub/menu.lst file

---

### Post by meierfra. on 2008-05-25
> if i were to delete vista, wubi would also be gone because i saved it on vista, right?

Yes. But there are ways to convert a wubi install  to a regular install. Asked about it in Wubi the forum, then  you  will  get responses  from the people who know wubi.

---

### Post by Vadi on 2008-05-25
"LinuxIsInnovation" is mistaken. Since you're using Wubi, which installs Ubuntu on the Windows harddrive space, erasing Windows would erase your Ubuntu.

What are you trying to accomplish though?

---

### Post by meierfra. on 2008-05-25
> "LinuxIsInnovation" is mistaken.

"LinuxIsInnovation" is talking about the regular  dual boot situation, which the OP asked about in the second paragraph:

> let's say i am dual booting between vista and ubuntu. if i were to delete vista, would anything really drastic happen? 

---

