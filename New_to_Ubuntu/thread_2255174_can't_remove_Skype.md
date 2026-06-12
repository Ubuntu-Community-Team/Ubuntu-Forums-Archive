---
title: "can't remove Skype"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by samer226047-8 on 2014-12-02
Hi everyone , I have a problem each time I run skype and signin it told me that am already signed in on the same pc.
so I removed it from Software Center. but when I type in terminal Skype it run again.
I already tried : 
sudo apt-get remove skype => it gave me 0 removed packages , 27 unpdated packages 
sudo apt-get remove --purge skype => it removed packages with around 270mb but nothing changed same problem and am still able to run it by terminal 

please help 

and thanks in advance.

---

### Post by QIII on 2014-12-02
Hello!

Did you delete .skype from your /home directory when you purged it before reinstalling?

If you have uninstalled it but can still run it from the terminal, would you please post the results of

```
 which skype 
```

---

### Post by ian-weisser on 2014-12-02
> **samer226047-8 said:**
> sudo apt-get remove skype => it gave me 0 removed packages , 27 unpdated packages 

If you installed Skype from a package (like in the Software Center), then 0 removed packages indicates that your package manager is broken. You won't be able to remove the Skype package until the package manager is fixed.
'Purge' won't help. 'Purge' does not force removal.

Did you install Skype from Software Center? 
Or some other way? If so, please explain in detail what instructions you followed. A link to those instructions would be a great help.

---

