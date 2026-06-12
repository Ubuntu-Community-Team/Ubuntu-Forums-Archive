---
title: "[SOLVED] Can't delete user"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by coldcoffee on 2008-11-12
I am using Intrepid. I want to delete a user. I go into users and groups and put in my sudo password. I delete the account and it dissappears until I open it again and there it is. Why can't I delete this account? It is my computer. I created the account and I am super-user on this computer.

This makes absolutely no sense to me. It is like I have no control over my own computer. I am sure there is a solution. I am thinking this should not be happening. Nonetheless it is frustrating that I can't undo something I created when I have highest privilege.

---

### Post by Nepherte on 2008-11-12
You can always try to delete it in the terminal:
```
sudo userdel <username>
```
replace <username> with the actual name. If there are any problems, the terminal will likely spit out the error.

---

### Post by coldcoffee on 2008-11-12
Thank you very much. Through the terminal it told me user was still logged in. So I realized this is why I could not delete it through System > Administration > Users and Groups.

Thanks again. I feel like such a noob!

---

