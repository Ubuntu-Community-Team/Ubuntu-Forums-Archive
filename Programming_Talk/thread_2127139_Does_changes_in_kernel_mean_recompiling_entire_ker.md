---
title: "Does changes in kernel mean recompiling entire kernel?"
date: 2013-03-19
forum: Programming Talk
---

### Post by akshay.sulakhe on 2013-03-19
Hello Friends,
                     I am currently working on SELinux. I have to make some changes to the SELinux package and not the SELinux policy. I compiled the Ubuntu precise kernel, and now i am running it. If i make changes to the kernel, do i have to recompile the entire kernel again? That would be very tedious. I have used 'sudo make modules_install' while installing. Kindly let me know that if it's not necessary to compile the entire kernel, then how and what should i compile for the changes to take place. Thank you for your time.  :-)

---

### Post by Zugzwang on 2013-03-19
Hi akshay.sulakhe, 

recompiling the Kernel is not as bad as it seems. Typically, you will only touch very few source files and only these will be recompiled by the make system. All in all, the process should be *much* faster than the initial building of the kernel.

---

### Post by akshay.sulakhe on 2013-03-19
Good, I hope gedit wil register those timestamps and make can identify..If the make is successful and there are no errors, then i have to run make modules_install and make install. Do i need a restart after this???

---

