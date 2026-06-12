---
title: "How to create central authentication system"
date: 2019-04-02
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-04-02
My current goal - To have the ability to log in to any user account in my home and have my settings and my /home/"$USER" available, regardless of location.

I'm thinking all /home/"$USER" on the server and shared via nfs, mounted on login at each client.

I know how to use Linux Terminal Server Project, already do for media centers in the home but I find it to slow to rely on for daily usage on my desktop machines even over gigabit (have gotten used to ssd speed).

Would LTSP be the better choice? Just centrally manage everything? Or is there a way to do just home folders and user accounts at any location? Best practices?

---

### Post by SeijiSensei on 2019-04-02
The simplest method is hoary old [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") which was designed as an authentication system by Sun Microsystems in conjunction with its development of NFS.  There's lots of documentation on using the two of them together to share home directories.

---

