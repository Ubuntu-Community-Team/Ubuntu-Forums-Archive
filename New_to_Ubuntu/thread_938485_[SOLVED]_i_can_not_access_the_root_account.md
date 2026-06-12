---
title: "[SOLVED] i can not access the root account"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Dacker on 2008-10-04
i'm getting the same problem again but this time won't be solve, i chsh to zsh shell which is being saved into /etc/zsh and when i try to access the root account i get this error  ```
Cannot execute /bin/zsh: No such file or directory

``` 
i've tried to get back to the bash shell ```
chsh -s /etc/bash
```
but  ```
chsh: PAM authentication failed

```:confused:

Thanks in advance.......

---

### Post by dew5 on 2008-10-04
to access root 

sudo -i

Then enter password.

Just out of curiosity, what do you need root access for?

dew5

---

### Post by Dacker on 2008-10-04
i typed this command before and this what i got :
```
linux is not in the sudoers file.  This incident will be reported.
```

Actually i will have a course in NCLA and NCLP which is about SUSE and as newbie i need to practice more and more in the shell and its commands, therefore the choice has appointed on ubuntu....

---

### Post by dew5 on 2008-10-04
oh. 
what distro are you using?

---

### Post by iaculallad on 2008-10-04
Try booting on recovery mode and add your user name in the admin group:

```
adduser you_username admin
```

---

### Post by Sef on 2008-10-04
If you are using ubuntu, then you should use sudo:

```
sudo apt-get update && sudo apt-get upgrade
```.


That will give you temporary root access.

---

### Post by jemate18 on 2008-10-04
the above post is right the ubuntu way is by executing a command with sudo. 

Other distros preferred being su by typing su - or su

---

### Post by dew5 on 2008-10-04
Your user account isnt regestered as a sudoers account therefore no root access using the sudo -i command.
use the main account to regester your account as a sudoers account.

to do this the main account must go to System &#8658; Administration &#8658; Users and Groups from the top toolbar. 

hope this helps 

dew5

---

### Post by Dacker on 2008-10-05
the thing was being stuck into the wrong shell which is zsh shell and that cuz of chsh command that upside down the root account but i got availability to access through the recovery mode not to involve my account into the admin account but just to chsh. Thus, thank you iacuallad for this clue ..........  

Finally, thanks for everybody :).

---

### Post by Endolith on 2009-11-15
I have this problem now, too.  I tried to change my user's shell, but used "sudo chsh", and changed the root shell to "bash" instead of "/bin/bash".  Now when I try to change it I get "chsh: PAM authentication failed" and it seems like other things aren't working, either.

```
~$ sudo su
Cannot execute bash: No such file or directory

```

This happens with recovery mode, too.  What do I try next?

---

