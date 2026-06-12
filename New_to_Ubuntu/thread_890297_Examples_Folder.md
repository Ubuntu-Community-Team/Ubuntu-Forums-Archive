---
title: "Examples Folder"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by RealG187 on 2008-08-14
I want to clean up my home folder. Can I/should I delete the examples folder?
Or is it needed (for example does there need to be a blank open office document in there to make a new open office file, so if I delete that folder I cannot make any new files).

---

### Post by OutOfReach on 2008-08-14
Well I have deleted it some time ago and the world didn't end :)
So yeah it is perfectly safe to delete the folder.

---

### Post by iaculallad on 2008-08-14
> **RealG187 said:**
> I want to clean up my home folder. Can I/should I delete the examples folder?
Or is it needed (for example does there need to be a blank open office document in there to make a new open office file, so if I delete that folder I cannot make any new files).

It's safe to delete your ~/Examples folder. The templates are located under your ~/.Templates folder.

```
rm -rf ~/Examples
```

---

### Post by RealG187 on 2008-08-14
> **iaculallad said:**
> It's safe to delete your ~/Examples folder. The templates are located under your ~/.Templates folder.

```
rm -rf ~/Examples
```

Wierd, I didnt have to sudo that command even though the folder was locked and the permissions tab said I wasnt the owner!

---

### Post by iaculallad on 2008-08-14
> **RealG187 said:**
> Wierd, I didnt have to sudo that command even though the folder was locked and the permissions tab said I wasnt the owner!

You have all the privilege to delete it even without using sudo. It's you're home directory so even it was given the "Padlocked" icon, you can still remove it.

---

### Post by RealG187 on 2008-08-14
That's funny it said I wasn't the owner.

Could I have deleted it from a file manager (Nautilus) too?

---

### Post by iaculallad on 2008-08-14
> **RealG187 said:**
> That's funny it said I wasn't the owner.

Could I have deleted it from a file manager (Nautilus) too?

Yap, you could use nautilus too to delete the ~/Examples folder.

---

### Post by Rolcol on 2008-08-14
Isn't the examples folder a symlink?

Edit: Yup.  It points to /usr/share/example-content

---

### Post by iaculallad on 2008-08-14
> **Rolcol said:**
> Isn't the examples folder a symlink?

Edit: Yup.  It points to /usr/share/example-content

No. Actually when you create users, the Examples folder will automatically created on their Home directories. Original location for the Examples folder is in /etc/skel.

So when you want created users to have the same files on their Home folders, you could drop it in that folder too.

---

### Post by Rolcol on 2008-08-14
> **iaculallad said:**
> No. Actually when you create users, the Examples folder will automatically created on their Home directories. Original location for the Examples folder is in /etc/skel.

So when you want created users to have the same files on their Home folders, you could drop it in that folder too.

Are you sure?
```
roly@rolyslaptop:/etc/skel$ file Examples
Examples: symbolic link to `/usr/share/example-content'
roly@rolyslaptop:/etc/skel$ 
```

I mean "Examples" itself.

---

### Post by iaculallad on 2008-08-14
> **Rolcol said:**
> Are you sure?
```
roly@rolyslaptop:/etc/skel$ file Examples
Examples: symbolic link to `/usr/share/example-content'
roly@rolyslaptop:/etc/skel$ 
```

I mean "Examples" itself.

Yes, the Examples folder itself is a symlink of the /usr/share/example-content folder.

---

