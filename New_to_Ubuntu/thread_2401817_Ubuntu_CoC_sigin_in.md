---
title: "Ubuntu CoC sigin in"
date: 2018-09-23
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2018-09-23
Hey all,

I signed up for Ubuntu CoC with my administrator Account by mistake

I would like to handle Ubuntu CoC with my standard account? 

Do I have to entirely start the process for ubuntu CoC with my standard acocunt or sharing the keys from administrator accounts works good?

[B]Note: I am able to create a SSH key for Standard account, but I am pretty confused with GPG key process with my standard account,

[/B] Because when I generated gpg key from standard account it shown a different key?

How can I get started to complete the Ubuntu CoC with standard account?

---

### Post by deadflowr on 2018-09-23
Any account will do.
gpg does not matter who runs it (admin or no admin)
> Note: I am able to create a SSH key for Standard account, but I am pretty confused with GPG key process with my standard account,

Because when I generated gpg key from standard account it shown a different key?
All keys are independent to the user who generated them and from each other. No two newly generated keys should ever match. 
So be glad they differ.
It would be a huge problem if two or more users kept creating the same keys, wouldn't it?
You might forgo all that and use the coc signing tool assistant from here:
[https://wiki.ubuntu.com/Forums/CoCSA_Tutorial]("https://wiki.ubuntu.com/Forums/CoCSA_Tutorial")

---

