---
title: "wireless problem"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by ayes on 2008-09-18
hi-i am ABSOLUTELY NEW to ubuntu-i am trying to install ndisgtk for installing my wireless adaptor.when i install from cd i get the message "dependancy is not satisfiable for".
i will need step by step help.
thanks in advance

---

### Post by northern lights on 2008-09-18
'ndisgtk' is in the repositories.

Either searching it in Synaptic (System > Administration > Synaptic Package Manager) or running ```
sudo apt-get update && sudo apt-get install ndisgtk
```should do the trick.

---

### Post by timjohn7 on 2008-09-18
What wireless adapter are you using?

I recommend installing wicd (follow the installation advice in the previous post) as it has solved numerous wireless issues for me and a number of others.

Welcome to the Community!

---

### Post by ayes on 2008-09-18
hi there-northen lights-i did that-thats when i got the error message.
thanks for the help-anyways what do i do next?

---

### Post by northern lights on 2008-09-18
Can you post the complete error message you are getting?

---

### Post by Crafty Kisses on 2008-09-18
I'd like to see the results of this command:
```
lshw -C network
```

---

### Post by ayes on 2008-09-18
northern lights-"error:dependancy is not satisfiable:ndiswrapper-utils-1.9

codename: i get "command not found"

---

### Post by ayes on 2008-09-18
hey guys i know i'm a bit slow-still getting used to the forum page

---

### Post by northern lights on 2008-09-18
> **ayes said:**
> northern lights-"error:dependancy is not satisfiable:ndiswrapper-utils-1.9

codename: i get "command not found"mkey. This is not very satisfiable. Was hoping for a more in-depth output.

Please post the output of ```
sudo lshw -C network
```
(capital C), as had been suggested by Codename.

---

### Post by ayes on 2008-09-18
codename-i still get "command not found"

i must be doing something wrong

let me read a bit tomorrow-see if i can figure something out or give you guys more to work with

thanks-see you guys tmrw-tired-goin to sleep-bye

---

### Post by ayes on 2008-09-18
hi guys-i'm back-thanks for all the help-used what you told me & played around-got that part working.thanks northern lights & codename!
but now for the new prob-i'm using a dlink dwa-142 usb wireless adaptor.
the netmw245.inf file does not work
i get the message "invalid driver"
any suggestions?

---

