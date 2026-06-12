---
title: "[SOLVED] re firewalls/firestarter"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-02
this relates to a recent solved query about firestarter.  i am using ubuntu 8:10.  this has both iptables and ufw as installed items listed in the repository.  am i right in believing that ufw is the firewall and iptables is a list of ip data that ufw uses and that they do not conflict.  i am also using firestarter, should i now use gufw as the gui instead or doesn't it matter that much.  i just want to use an effective firewall.  thanks everybody.
nigel
ps no great hurry on this one, i am going out for a while so...

---

### Post by Paqman on 2008-12-02
The firewall is iptables.

Ufw is a tool for making configuring iptables easier, but it's really intended for servers and hence is CLI-only. Gufw is a GUI that was made for ufw.

Firestarter, effectively, does pretty much the same as Gufw (ie: makes changes to iptables)

It's really down to personal preference between Gufw and Firestarter. On a desktop system, you shouldn't need to change the default firewall settings anyway, so unless you need to do something specific you don't need either of them.

---

### Post by collinp on 2008-12-02
iptables is the linux firewall. UFW is a frontend to iptables to make configuration easier, and firestarter is a graphical frontend.

---

### Post by capnthommo on 2008-12-02
okay thanks, so i don't need to actually do anything with any of them then?  i can just leave it all alone and the firewall will start when i boot up?  sorry if you have already answered, but i just want to make sure i have got it hammered hrough my skull.  thanks again
nigel

---

### Post by collinp on 2008-12-02
Yes, unless their is a specific reason that you need to edit your iptables configuration, you can leave it alone and it will do its job. And yes, it starts at boot.

---

