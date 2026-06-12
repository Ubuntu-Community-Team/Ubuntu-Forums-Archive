---
title: "versions?"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Yezinki on 2012-11-01
The present version is 12.04 LTS correct.....what are the differences between 12.04 & 12.10?

Thanks.

---

### Post by MG&amp;TL on 2012-11-01
12.10 is the current release.

12.04 is special in that it will get software updates for five years (LTS), whereas 12.10 will only get software updates for 18 months.

Obviously, 12.04 is more mature, whereas 12.10 will have some software that is only available on newer releases.

---

### Post by Yezinki on 2012-11-01
Thanks MG&TL for your detailed reply.

How can I stop 12.04 LTS to be upgraded to 12.10, as in update manager > setting have all checked?

Which option should be unchecked to stop it?

---

### Post by MG&amp;TL on 2012-11-01
In update manager, click "settings", then change the "Notify me of new Ubuntu releases" options to something more preferable.

See screenshot.

---

### Post by Yezinki on 2012-11-01
Thanks MG&TL, I have that set at never notify.

Lastly how can one know which version is running 12.04 or 12.10?

---

### Post by NM5TF on 2012-11-01
> **Yezinki said:**
> Thanks MG&TL, I have that set at never notify.

Lastly how can one know which version is running 12.04 or 12.10?

try this

```
lsb_release -rcd ; uname -r
```

Tommy

be advised that 12.10 is so new that it has lots of bugs...especially
if you have a Nvidia graphics card...

---

### Post by themartinlopez on 2012-11-01
Hey listen if you already have Ubuntu 12.04 installed I recommend you don't upgrade. The only new big difference in 12.10 is cloud integration.. Its not worth upgrading unless you want it.. It would probably only be a good idea to install if you are completely new to Linux.

---

### Post by MG&amp;TL on 2012-11-01
> **themartinlopez said:**
> Hey listen if you already have Ubuntu 12.04 installed I recommend you don't upgrade. The only new big difference in 12.10 is cloud integration.. Its not worth upgrading unless you want it.. It would probably only be a good idea to install if you are completely new to Linux.

Sorry to single this out amongst all the controversial* things on the internet, but do you seriously think the Ubuntu developer community spent six months on a release with the "only new big difference is cloud integration"? Even if all the rest of the differences were small, that's a lot of small improvements worth an upgrade.






*read: wrong/FUD/just controversial.

---

### Post by Yezinki on 2012-11-01
> **NM5TF said:**
> try this

```
lsb_release -rcd ; uname -r
```

Tommy

be advised that 12.10 is so new that it has lots of bugs...especially
if you have a Nvidia graphics card...


Thanks NM5TF these are the results for the command posted.

In Update manager> Settings have all checked & never check for a newer version, is that fine?


```
vaio@VGC-LS1:~$ lsb_release -rcd ; vaio -r
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
vaio: command not found
vaio@VGC-LS1:~$ 

```

---

### Post by Ryaniskira on 2012-11-01
12.04=
Year is 2012
It is released in April so that is where the .04 comes from

12.10=
Year is 2012
It is released in October so that is where the .10 comes from

LTS= 
long term support 
12.10 fixes bugs but the integrated Amazon in the unity shell is annoying. I believe it can be disabled though.

---

### Post by RedRat on 2012-11-01
Unless you are into the "latest and greatest" and truly enjoy debugging OSs, I would suggest that you stay with 12.04LTS. You have to be comfortable looking for solutions and debugging. Some find a challenge there and they should go for it. But if you are using an OS to be productive, i.e., email, write-create documents, view and surf the internet, stay with the various LTS versions that come down the pike in the next few years. 

As you will read here as the various releases of Ubuntu come out, there are going to be difficulties and challenges. If you enjoy the challenge of fiddling around with an OS and getting it to work on your system, go for the various intermediate releases. Otherwise, I suggest you stick with the LTS versions.

---

### Post by NM5TF on 2012-11-02
> **Yezinki said:**
> Thanks NM5TF these are the results for the command posted.

In Update manager> Settings have all checked & never check for a newer version, is that fine?


```
vaio@VGC-LS1:~$ lsb_release -rcd ; vaio -r
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
vaio: command not found
vaio@VGC-LS1:~$ 

```

very close...but you substituted YOUR user name at the end of the code
instead of copying & pasting it exactly....it would have shown what kernel
you are using....look at my example below...


tommy2@tommy-Inspiron-531s:~$ lsb_release -rcd ; uname -r
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
3.2.0-32-generic
tommy2@tommy-Inspiron-531s:~$ 


your Update Manager settings sound fine to me, but I would uncheck
the pre-release setting....like another person said above....I always
stick with the LTS kernels as they have time to be debugged & will be
supported for 5 years....


Tommy

---

