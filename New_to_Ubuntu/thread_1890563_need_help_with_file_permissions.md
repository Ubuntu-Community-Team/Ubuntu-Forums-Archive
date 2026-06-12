---
title: "need help with file permissions"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by ixtok on 2011-12-03
Hi, I am using ubuntu 11.10. I am using the program Stellarium and I wish to add a folder into the usr/share/stellarium/skyculture directory. The owner of the directory is root. How do I accomplish this task?

---

### Post by matt_symes on 2011-12-03
Hi

> **ixtok said:**
> Hi, I am using ubuntu 11.10. I am using the program Stellarium and I wish to add a folder into the usr/share/stellarium/skyculture directory. The owner of the directory is root. How do I accomplish this task?

You need to create the folder with elevated privileges. 

Press ALT + F2 together and type
```

gksudo nautilus usr/share/stellarium/skyculture
```

Add the directory and the close nautilus. You can also copy and move file into that new directory this way. Be very careful with using nautilus this way though as you can delete any system file you want.

From the command line

```
sudo mkdir usr/share/stellarium/skyculture/<directory_name>
```

Can i ask why you need to create the folder ? Maybe there a config folder for it in your home directory .

Kind regards

---

### Post by ixtok on 2011-12-03
> **matt_symes said:**
> Hi

Can i ask why you need to create the folder ? Maybe there a config folder for it in your home directory .

Kind regards

Actually the folder is aready created and is in my home/Download directory. It was downloaded from the Stellarium Wiki site. The root owned skyculture directory contains multiple folders of different skycultures and this is just another one to use. I don't really want to create a new folder in the sky culture directory, I just want to drop in the already created new folder. Is this the correct way?

---

### Post by matt_symes on 2011-12-03
Hi

You can move the folder with ALT and F2 and gksudo nautilus as i highlighted.
> Is this the correct way?In this case, i think so.

Looks like a nice little program.

Kind regards

---

### Post by ixtok on 2011-12-03
Thanks it worked

---

### Post by daggerstab on 2011-12-04
**ixtok,**

If you need to make Stellarium load a custom sky culture, you'd better put it in ~/.stellarium/skycultures

Putting it in /usr/share/stellarium is somewhat wrong to do, because it requires dealing with permissions, as you have discovered. It also means that it will be deleted if you remove the Stellarium packages or overwritten if you update Stellarium.

---

### Post by matt_symes on 2011-12-04
Hi

> **daggerstab said:**
> **ixtok,**

If you need to make Stellarium load a custom sky culture, you'd better put it in **~/.stellarium/skycultures**

Putting it in /usr/share/stellarium is somewhat wrong to do, because it requires dealing with permissions, as you have discovered. It also means that it will be deleted if you remove the Stellarium packages or overwritten if you update Stellarium.

Thanks daggerstab!

@OP: That was what i was looking for when i asked about a config folder in your home directory.

Most programs - but not all - have them and, as has been stated, it means you do not need to play around with permissions; moving files and folders into system folders.

Kind regards

---

