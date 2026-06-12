---
title: "snapshot backup is using alot of storage"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by Samanrz on 2013-02-26
Recently I found out that there is a hidden folder .snapshot in \local that is keeping daily backup. Inside I see folders like 'AM.DAILY.01', 'PM.DAILY.01', ..... with almost the same content . when I try removing them it says that it's a read-only folder. It is using A LOT of storage and I don't know what to do. 
I am not a sudoer by the way.

Thanks in advance

---

### Post by cariboo on 2013-02-27
Where is /local located, as the standard install local is a hidden directory ~/.local? What backup program are you using. 

When you say you aren't a sudoer, does that mean your user isn't in the admin/sudo group?

---

### Post by Samanrz on 2013-02-27
I am sorry, I made a mistake. The snapshot folder is a hidden one as  home/username/.snapshot. I am not using any backup application! I don't know where these folders come from!
Inside each "AM/PM.DAILY.nb" I see all the contents of home/username.
Yes, I am not the administrator of my system. It's not my choice.

---

