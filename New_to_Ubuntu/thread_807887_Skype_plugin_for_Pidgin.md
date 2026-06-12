---
title: "Skype plugin for Pidgin"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-05-26
I'm trying to add this plugin  skype4pidgin.deb from [http://myjobspace.co.nz/images/pidgin/](http://myjobspace.co.nz/images/pidgin/) it automaticly runs package installer and gives me a message that says: Error: Dependency is not satisfiable: pidgin "Requires Skype to be running."

Any help would be appreciated.

---

### Post by 505 on 2008-05-26
The skype plugin is just a plugin to control skype, not the have the skype protocol in Pidgin. That means that you still have to have Skype installed and running before you can use this plugin in Pidgin. Install Skype first, I believe it is available in the partner repros, or on Skypes own site.

---

### Post by niceguy123 on 2008-05-26
I've got skype runing.

---

### Post by 505 on 2008-05-26
Open a console and type
```

sudo dpkg -i skype4pidgin.deb

```
Make sure you cd to the directory where skype4pidgin.deb is located. If it fails to install it should tell you which dependencies are needed.

---

### Post by niceguy123 on 2008-05-27
> **505 said:**
> Open a console and type
```

sudo dpkg -i skype4pidgin.deb

```
Make sure you cd to the directory where skype4pidgin.deb is located. If it fails to install it should tell you which dependencies are needed.

Thanks, which directory should it be in?

---

### Post by 505 on 2008-05-27
I don't know, depends on where you downloaded the file. skype4pidgin.deb is just a file to install it. Once you run the above command it will install itself it the correct dorectory (if there are no errors).

So, if all downloads are saved on your desktop, open the terminal and do "cd Desktop" first, then run the command I posted above.

---

### Post by niceguy123 on 2008-05-27
> **505 said:**
> I don't know, depends on where you downloaded the file. skype4pidgin.deb is just a file to install it. Once you run the above command it will install itself it the correct dorectory (if there are no errors).

So, if all downloads are saved on your desktop, open the terminal and do "cd Desktop" first, then run the command I posted above.

My downloads show it and it should be in desktop, butI don't see it on the desktop. And I tried the code you gave here and got the following:

```
-desktop:~/Desktop$ sudo dpkg -i skype4pidgin.deb
dpkg: error processing skype4pidgin.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype4pidgin.deb

```

---

