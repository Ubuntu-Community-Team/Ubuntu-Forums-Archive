---
title: "[SOLVED] vmware"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by jboy012000 on 2008-05-02
hi everyone,

i have just moved upto ubuntu 8.04lts from 7.10 and i want to use vmware, it worked fine with 7.10, but it will not work on 8.04lts, i had a go at starting vmware in the terminal but i got this message:

john@john-desktop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

john@john-desktop:~$ 

so i do as it says then i get this message,

john@john-desktop:~$ /usr/bin/vmware-config.pl.
bash: /usr/bin/vmware-config.pl.: No such file or directory
john@john-desktop:~$ 

can anyone help, i need vmware as i use it as a testing enviroment.

thanks

john

---

### Post by BbUiDgZ on 2008-05-02
not sure about this one i was searching for vmware in these forums as im about to install it for the first time in 8.04, but you could try ```
sudo /usr/bin/vmware-config.pl
``` as it looks as if it might be a permissions problem... but then again it could be a case of the blind tryin to lead the blind :lolflag:

---

### Post by jboy012000 on 2008-05-03
Thanks for your help, but after posting my thread i decided to try virtual box so far it seams ok and a lot less messin g around than vmware, let me know how you go with the install.

Cheers

---

### Post by Ducatiboy-stu on 2008-05-03
try this

[http://ubuntuforums.org/showthread.php?t=778389&page=2](http://ubuntuforums.org/showthread.php?t=778389&page=2)

I had major probs with vmware-server..

there are links to various pages that will assist


you may need to do the kernel upgrade..etc....

---

### Post by StOoZ on 2008-05-03
I wonder if a new version of vmware-server is on the horizon because of these issues.
Its one of the reason im not upgrading to 8.04

---

### Post by jboy012000 on 2008-05-04
I hope so i tried Virtual Box but it seems to be a no go. Just want to say thanks for everyone's replys we will see what happens, if I do figure it out I will post a thread.

---

### Post by BbUiDgZ on 2008-07-08
> **jboy012000 said:**
> Thanks for your help, but after posting my thread i decided to try virtual box so far it seams ok and a lot less messin g around than vmware, let me know how you go with the install.

Cheers

i followed the instructions in the README and the on screen instructions and all went well. Had to change the file permissions on the virtual machine folder in order to run vmware without sudo. 
Tis so good:)

---

