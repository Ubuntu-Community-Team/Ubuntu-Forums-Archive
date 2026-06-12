---
title: "Do I have to use chown?"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by kapi on 2012-10-10
I just used the command line to cp some font files to the font folder usr/shar/fonts.

But I read somewhere that I should also use chown. I'm really rusty on bash scripting and haven't really done any since college. The following input worked fine.

```
~/web development/fonts$ sudo cp fontface2 -R /usr/share/fonts

```

---

### Post by twipley on 2012-10-10
> **kapi said:**
> I just used the command line to cp some font files to the font folder usr/shar/fonts.

But I read somewhere that I should also use chown. I'm really rusty on bash scripting and haven't really done any since college. The following input worked fine.

```
~/web development/fonts$ sudo cp fontface2 -R /usr/share/fonts

```

Well, chowning is easy.

sudo chown -R 777 /usr/share/fonts

might be giving it a quick go;

tell us how it went!

---

### Post by kapi on 2012-10-10
Thanks for the reply,

The fonts are visible and working so I don't think I need to use chown as I am the only user on my laptop.

Cheers though

---

### Post by oldos2er on 2012-10-10
I wouldn't use chown on system files (anything outside your home folder) unless you know exactly what you're doing. Linux relies on root permissions on system files for much of its functioning.

Elevating your user privileges with sudo is the proper way to do what you want to do.

---

### Post by bab1 on 2012-10-10
> **twipley said:**
> Well, chowning is easy.

sudo chown -R 777 /usr/share/fonts

might be giving it a quick go;

tell us how it went!

This won't work as you expected. 

The command **chown** changes ownership and it is used like this on a file (or directory) owned by *user1* ```
sudo chown user2 somefile
```...if you wanted to change the group you would use this variation```
sudo chown user2:user2 somefile
```

The command **chmod** changes the users permissons (i.e 775) from your 777 like this```
sudo chmod 775 somefile
```

You can view the gory details here```
man chown

man chgrp

man chmod
```

---

### Post by shaktiman1234 on 2012-10-11
always be cautious before using chown, chmod, chgrp commands. If applied to a wrong file/directory you can screw up your whole installation.

---

