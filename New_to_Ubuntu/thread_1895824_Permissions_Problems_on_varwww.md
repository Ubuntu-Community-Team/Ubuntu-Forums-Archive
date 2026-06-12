---
title: "Permissions Problems on /var/www"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by redrings on 2011-12-15
I've read through the documentation and as many posts as I could find regarding file permissions in the forums, but I'm running into something strange I'm hoping someone can help explain to me what is going on.

I have some files in /var/www that I want to be able to have access to via samba.  At first, these files were in the root group owned by the root user, so I changed them to be owned by the www-data group using:

```
sudo chown -R www-data:www-data /var/www
```

using ```
ls -l
``` I can now see that the user and group are listed as www-data.

I then added myself to the www-data group using:

```
sudo usermod -g www-data
```

and then checked to make sure I was in the group using:

```
groups
```

Finally, I made sure that the group had rwx permissions to the files/folders using:

```
sudo chmod -R g+rwx /var/www
```

As far as I can tell, I should now be able to create and edit files as I am in the www-data group, the www-data group owns the files, and permissions for the group have been set; however, that is not the case.  When attempting to create a file in the /var/www folder using:

```
touch test
```

I get:

> touch: cannot touch 'test': Permission denied

Does anyone know what I'm doing wrong or not understanding correctly?  Thanks so much!

---

### Post by redrings on 2011-12-15
Well, touch still isn't working to create a file on the root - but I seem to be able to create files using samba now.

---

