---
title: "Ubuntu default admin password for authentication ?"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by honey_bee on 2012-06-29
hi,
       I am using Ubuntu 10.10 in my system. Just after installing my fresh ubuntu  I configure my lan IP address and use "apply" it show me dial log box to enter password. I have not used root password during installation  but not know why is it asking. please guide me that what is the root password  by default for authentication ?

kindly see the attachment for more clarity.

thanks,
honey

---

### Post by papibe on 2012-06-29
Hi honey_bee.

It is asking for your own password, as you are by default on the admin group.

Regards.

---

### Post by honey_bee on 2012-06-29
thanks a lot for helping me. This means that the user bob which i had made during installation is my root user ? By the way there is a question in my mind that how can I access root user ?  What stands for Sudo  ?


thanks in advance;
honey

---

### Post by Cheesemill on 2012-06-29
Bob isn't your root user, they are a user in the admin group which means they are allowed to use the sudo command to temporarily run things with root privileges.

In Ubuntu the root user account is locked and can't be logged into normally.

For more information:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by honey_bee on 2012-06-29
Thanks for the reply. Well what Sudo stands for ....?

---

### Post by Cheesemill on 2012-06-29
**S**uper **U**ser **DO**

---

