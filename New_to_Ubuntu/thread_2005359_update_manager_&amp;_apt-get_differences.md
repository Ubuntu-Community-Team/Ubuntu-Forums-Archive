---
title: "update manager &amp; apt-get differences ?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by robertmf on 2012-06-17
:guitar: What is the functional difference between updating with [update manager] and using [apt-get] ?

I can update using apt-get.  Then checking Update Manager gives me more updates.  

Thanks in advance :p

---

### Post by drs305 on 2012-06-17
Update-manager is a bit more 'aggressive' than apt-get in that it will install kernel updates. Apt-get will also install these updates but requires an additional option in the command. Normally it just says the kernel package is held back. (There are reasons apt-get holds back non-kernel packages as well.)

There was a kernel update a few days ago in 12.04 and that may be what you are seeing.

Here is one link explaining it. Read both answers for a fuller understanding, as well as the 'man' page ( man apt-get ):
[http://askubuntu.com/questions/146260/is-updating-via-update-manager-equivalent-to-updating-with-apt-get]("http://askubuntu.com/questions/146260/is-updating-via-update-manager-equivalent-to-updating-with-apt-get")

---

### Post by blackbird34 on 2012-06-17
Update Manager is a front-end GUI for apt-get (especially for the apt-get update function). Both do the same thing, but sometimes when you do apt-get update, Update Manager realises its repository databases have been updated and gives you a message to that effect, before realizing you have done your apt-get upgrade by command line alrready. 
So:
>   Then checking Update Manager gives me more updates.  I think this is just that time lag i described.

Edit: beaten to it by an admin :D

---

