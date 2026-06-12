---
title: "Help!"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by anon6969 on 2008-05-09
I have Ubuntu installed as a duel boot on my Laptop from ages ago but I forgot the password!!!

What's more the DVD is broken so I can't re-install Ubuntu from CD.

What should I do?

Is there any way I can re-set the password or something?

---

### Post by subzero316 on 2008-05-09
> **anon6969 said:**
> I have Ubuntu installed as a duel boot on my Laptop from ages ago but I forgot the password!!!

What's more the DVD is broken so I can't re-install Ubuntu from CD.

What should I do?

Is there any way I can re-set the password or something?



Try Entering in the recovery mode

else


Press ESC at the grub prompt.
Tap e and get into  edit mode.
there`s a line that starts like>> kernel go there highlight and press e
Append this to the end of the line, ```
rw init=/bin/bash  
```<
press enter then press b to boot your system.
Youll get into the root she11 
Type in ```
passwd <username>
``` enter your new password.
reboot.

---

### Post by anon6969 on 2008-05-10
I should also have said I don't know what my username is...

---

### Post by Joeb454 on 2008-05-10
do ```
ls /home
``` first, it should list any users home directories :)

---

### Post by anon6969 on 2008-05-10
Great I did it. Now I can login to Ubuntu!

Thanks guys. 

Now I need to work out how to connect to the Internet in Ubuntu the same way I can in Windows....

I have a Username and Password for my ASDL connection, but where do I put them in Ubuntun...?

---

