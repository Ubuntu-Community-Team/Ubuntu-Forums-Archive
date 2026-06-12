---
title: "Is Django available as a .deb install anywhere?"
date: 2006-10-02
forum: Programming Talk
---

### Post by saracen on 2006-10-02
Or should I just use the website install?  The reason i'm asking is because i'd like to have a good way to uninstall it.  Would python setup.py uninstall work?

---

### Post by pay on 2006-10-02
You might be able to install checkinstall ```
sudo aptitude install checkinstall
```which then makes a debian files and then run```
sudo checkinstall -D setup.py
```Might not work but then again it might aswell.

---

### Post by hyper7 on 2006-10-02
Installing alien to convert .rpm to deb packages is always a good idea.

```
sudo apt-get install alien
```

Then run alien on the RPM of your choice.

```
alien yourrpm.rpm
```

I found RPMs for Django, so you may want to give installing them a shot.

---

### Post by saracen on 2006-10-02
cool, i converted an rpm using alien.  Any ideas why the conversion alone has to be done as root?

---

### Post by hyper7 on 2006-10-02
No luck with Django and alien?

EDIT: Someone tried to answer your question about having to use 'sudo with alien on your thread in the Edgy Dev section.

You seem oddly paranoid.

---

### Post by saracen on 2006-10-02
Not oddly paranoid.  Anytime something asks me for sudo priveleges I question why.  I read the response on the other thread but it didn't really answer my question.  I just don't see the need for it if all it is doing is a file conversion.

---

### Post by Azmodan on 2006-10-15
You can also use fakeroot instead of sudo which will not require your root password.  Just apt-get it :

sudo apt-get install fakeroot

Then use fakeroot with alien :

fakeroot alien my_rpm_package.rpm

---

