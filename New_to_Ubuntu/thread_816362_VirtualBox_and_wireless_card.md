---
title: "VirtualBox and wireless card"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by coubury on 2008-06-02
How can i get my wireless card recognized in VirtualBox?

In another forum someone said they had to do this but i dont undertsnad what they mean

**update
got my wireless working as well. pheww!!!
i had to choose the host interface name which needed to be mapped to the virtual adapter in the settings.

Gravatar #38. 

anyone help?

---

### Post by SpecialFred on 2008-06-02
If you are using Virtualbox, you shouldn't need it to recognize your wireless card. Instead, you can configure Virtualbox to make the guest OS think that it has a wired connection. 

Specifically, in Virtualbox, go to Settings -> Network -> Adapter 0. Check the 'Enable Network Adapter' box and the 'Cable Connected' box. That should let the guest OS use the internet connection.

Post back with how it goes.

---

### Post by SlappyPappy on 2008-06-03
The man is correct. No need to set it up. Just piggyback on the host's connection.

---

