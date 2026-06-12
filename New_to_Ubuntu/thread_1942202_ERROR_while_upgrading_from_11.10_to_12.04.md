---
title: "ERROR: while upgrading from 11.10 to 12.04"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by likewinthomas on 2012-03-17
Hi,

My system got hanged while upgrading from 11.10 to 12.04 due to which i restarted my machine. Now when I am trying to upgrade it is not updating not only that it is showing some error like : partial upgrade due to some error in previous updating. Even I am getting error while opening the text editor, it is not at all opening.

Some body please help me how to overcome this problem.

Thank you

Likewin

---

### Post by TeoBigusGeekus on 2012-03-17
Open a terminal and post us the output of
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by anewguy on 2012-03-17
And remember 12.04 still is not production mode software.

---

### Post by tbhatia4 on 2012-03-17
> **likewinthomas said:**
> Hi,

My system got hanged while upgrading from 11.10 to 12.04 due to which i restarted my machine. Now when I am trying to upgrade it is not updating not only that it is showing some error like : partial upgrade due to some error in previous updating. Even I am getting error while opening the text editor, it is not at all opening.

Some body please help me how to overcome this problem.

Thank you

Likewin

you made a backup file before upgrading??

---

### Post by matt_symes on 2012-03-17
Hi

As an addendum to Teo's post

```
sudo apt-get install -f
```

may help as well.

As anewguy said, it's a pre-release version. 

If you are asking this question, are you sure 12.04 is right for you ?

Kind regards

---

### Post by anewguy on 2012-03-17
> **tbhatia4 said:**
> you made a backup file before upgrading??

I like this - after all the years - see my "dumb" post for what NOT to do to install 12.04!  ;)

Dave ;)

---

### Post by NikTh on 2012-03-17
Hi , 
you can also try ```
 sudo apt-get update && sudo apt-get dist-upgrade
```  then apt will try to install any dependencies probably missing.

---

### Post by philinux on 2012-03-17
> **likewinthomas said:**
> Hi,

My system got hanged while upgrading from 11.10 to 12.04 due to which i restarted my machine. Now when I am trying to upgrade it is not updating not only that it is showing some error like : partial upgrade due to some error in previous updating. Even I am getting error while opening the text editor, it is not at all opening.

Some body please help me how to overcome this problem.

Thank you

Likewin

Try this.

```
sudo dpkg --configure -a
```

---

