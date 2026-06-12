---
title: "Could not open Synaptic package manager"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by movila on 2012-01-05
the ubuntu software center works fine, but I could not open the Synaptic Package Manager.
When I start the synaptic, it shows the following error:
```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
```

---

### Post by heyandy889 on 2012-01-05
Whoa. That is freaky. Well, I googled "synaptic terminate called after throwing an instance of 'std::out_of_range' what():  vector::_M_range_check" and came up with this page.

Looks like you might not be the only one . . . 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/879383](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/879383)

Does Synaptic ask you to give your user password? Should ask you something along the lines of "Please enter password: Synaptic lets you modify essential parts of your system." I ask because this grants super-user permission to Synaptic. It might crash if it didn't have super-user permission.

Welcome to the forums, dude!

---

### Post by oldrocker99 on 2012-05-09
Following a hint from the Launchpad link above, I fixed it by opening Universal Access, enabling the on-screen keyboard, the disabling it. Synaptic now opens normally.

---

