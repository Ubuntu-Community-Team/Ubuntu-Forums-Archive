---
title: "I broke my Postfix install"
date: 2021-09-25
forum: New to Ubuntu
---

### Post by Gregory_Machin on 2021-09-25
Hi,

I installed Virtualmin on my server, that broke my configurations. I uninstalled Virtualmin, fixed Apache , but Postfix is not using the /etc/postfix. None of the changes I make to the configs are reflected in postfix -d. 

How can I find out what configuration the postfix binary is reading ?

G

---

### Post by ActionParsnip on 2021-09-26
Restore your configuration from your backups. You did make backups before you started changing the system... Right?

---

### Post by Gregory_Machin on 2021-09-27
Yes, have backups, that allowed me to fix all the other issue. But doesn't explain the /etc/postfix/main.cf not being processed

---

### Post by ActionParsnip on 2021-09-27
I'd start by checking the configuration file for the service to see which configuration file is specified to be used. Also make sure that the configuration file is readable by the user used to run the service

---

