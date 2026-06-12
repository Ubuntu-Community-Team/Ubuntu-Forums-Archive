---
title: "Urgent Help! Ubuntu 12.04 upgrade - Nautilus broken"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by ngubk on 2012-04-26
I've just upgrade to Ubuntu 12.04 a few hours ago. Now i can not even open a folder anymore. And i'm gonna have an important task to do with Ubuntu tomorrow.

```
 ngu@MyUbuntu:~$ nautilus
Initializing nautilus-dropbox 0.7.1
** Message: Initializing gksu extension...
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

(nautilus:10894): GLib-GObject-WARNING **: Two different plugins tried to register 'DejaDupNautilusExtension'.

(nautilus:10894): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed
Segmentation fault (core dumped)

```

---

### Post by ngubk on 2012-04-26
Anyone has any idea what "Two different plugins tried to register" is.
I've tried removing nautilus-open-terminal, nautilus dropbox but no luck so far.
Much appreciated for any reply.

---

### Post by kimda on 2012-04-26
```
sudo apt-get remove nautilus-gdu
```

Try this and remove this extension. I cannot find it in the repos so its probably not compatible.

---

### Post by ngubk on 2012-04-26
Thanks for your help. But i don't have nautilus-gdu in my repos either

---

### Post by grahammechanical on 2012-04-26
What if you removed this:

> 'DejaDupNautilusExtension'

That seems to be the extension that is being fought over.

regards.

---

### Post by vasa1 on 2012-04-26
> **ngubk said:**
> I've just upgrade to Ubuntu 12.04 a few hours ago. Now i can not even open a folder anymore. And i'm gonna have an important task to do with Ubuntu tomorrow.

```
 ...

** Message: Initializing gksu extension...
...
```
This also? I don't know what "gksu extension" is involved but hasn't nautilus-gksu been kicked to the kerb?

---

### Post by ngubk on 2012-04-26
Thanks. There is just a "Deja-dup" in the repos. But delete that will lead to even more error. Like there's no deja-dup so nautilus can not run

---

### Post by CLCressman on 2012-04-26
I would try another file manager, to get by until you get nautilus figured out.

---

### Post by kimda on 2012-04-27
Look at all the installed nautilus packages. 
```
dpkg -l | grep nautilus
```
Delete all the plugins (sudo apt-get remove pluginname). This should fix your problem since there are no plugins anymore (unless you build them from source / tarballs yourself). 
The only packages you should keep is nautilus, nautilus-data and libnautilus-extension1a.

---

### Post by ngubk on 2012-04-27
I've deleted all except for 3 packages you told me. Still doesn't work. For now, i'm using another file manager. Thanks for your help

---

### Post by kimda on 2012-04-27
You can try deleting your nautilus folder.
 
```
rm -rf .gconf/apps/nautilus/
``` 

and

```
rm -rf .config/nautilus/
```

Which will delete all your nautilus settings. And then reinstall nautilus

```
sudo apt-get install --reinstall nautilus nautilus-data
```

---

