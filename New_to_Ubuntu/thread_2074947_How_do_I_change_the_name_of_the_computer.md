---
title: "How do I change the name of the computer?"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by zozza on 2012-10-22
My GNOME displays bobby@mycomputer.

How do I change the @mycomputer aspect?  

Is there a way to change the name of the computer?

Thanks!

---

### Post by aabed91 on 2012-10-22
You can review this post:
[http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/)

I think it will help you :)

---

### Post by bab1 on 2012-10-22
> **aabed91 said:**
> You can review this post:
[http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/)

I think it will help you :)

You also need to edit the /etc/hosts file or you will loose sudo rights.
```
gksudo gedit /etc/hosts
```

---

### Post by Karlchen on 2012-10-22
Hello, bab1.

There is no reference to the hostname in the default /etc/sudoers file.
So sudo privileges by default do not depend on the /etc/hosts file, nor on the content of /etc/hostname.
Yet, it will do no harm checking the /etc/sudoers file for references to the old hostname and add the new hostname, if any references are present.

Apart from that, it may be wise to make sure that /etc/hostname  and /etc/hosts specify the same hostname for the local machine anyway.

Kind regards,
Karl

---

### Post by bab1 on 2012-10-23
> **Karlchen said:**
> Hello, bab1.

There is no reference to the hostname in the default /etc/sudoers file.
So sudo privileges by default do not depend on the /etc/hosts file, nor on the content of /etc/hostname.
Yet, it will do no harm checking the /etc/sudoers file for references to the old hostname and add the new hostname, if any references are present.

Apart from that, it may be wise to make sure that /etc/hostname  and /etc/hosts specify the same hostname for the local machine anyway.

Kind regards,
Karl
If you don't match the hostname to the same in /etc/hosts you will get the following and not be able to use sudo```

sudo: unable to resolve host <old hostname>

```

---

### Post by critin on 2012-10-23
> **zozza said:**
> My GNOME displays bobby@mycomputer.

How do I change the @mycomputer aspect?  

Is there a way to change the name of the computer?

Thanks!

This is very easy to do.  Copy/paste the codes into the terminal, don't try to type them unless you are experienced with code.  Any typo will cause Drama!  Copy/paste...Follow instructions carefully and you'll find it easy.

Just be sure to read the whole page before doing anything--so you will understand what you're doing.
If there are warning messages, heed them.

[http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-change-your-computer-name/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-change-your-computer-name/)

[http://www.webupd8.org/2012/03/how-to-change-hostname-computer-name-in.html](http://www.webupd8.org/2012/03/how-to-change-hostname-computer-name-in.html)

---

