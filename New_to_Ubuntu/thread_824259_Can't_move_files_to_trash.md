---
title: "Can't move files to trash"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by KevNice on 2008-06-09
I asked this question on another thread addressing a related problem, which was solved.

While trying to solve that other problem (not being able to delete files from trash), I tried this code:

```
sudo rm -rf ~/.local/share/Trash/*
```

However, the first time I used this code, I think I accidentally did:

```
sudo rm -rf ~/.local/share/Trash
```

And ever since then, I can no longer move files to trash-- if I try to delete something, it prompts me to delete it permanently, immediately.

I think I messed up the paths to the Trash folder.

Can anyone help me fix this?

---

### Post by iaculallad on 2008-06-09
Open up your terminal:

> sudo mkdir ~/.local/share/Trash
sudo chown 777 ~/.local/share/Trash

---

### Post by Unix_Slayer on 2008-06-09
Ya gotta be careful with the trash bin. I moved stuff in there, and it had a symbolic link to the directory. I couldn't remove it from the trash, so I started to remove one file at a time. I had to re-install the lib that was linked to it.

---

### Post by KevNice on 2008-06-19
> **iaculallad said:**
> Open up your terminal:

I tried this, but no success.

Anyone got any other ideas?

---

### Post by iaculallad on 2008-06-19
Try this instead:

If you're using Hardy:

User Trash:

```
sudo mkdir /home/your_user_name_here/.local/share/Trash
sudo chown 777 /home/your_user_name_here/.local/share/Trash
```

Root Trash:

```
sudo mkdir ~/.local/share/Trash
sudo chown 777 ~/.local/share/Trash
sudo mkdir ~/.local/share/Trash/files
sudo chown 777 ~/.local/share/Trash/files

```
If you're on Gutsy:

```
sudo mkdir ~/.Trash
sudo chown 777 ~/.Trash
```

---

### Post by spimby on 2008-06-26
[QUOTE=iaculallad;5216450]Try this instead:

If you're using Hardy:

User Trash:

```
sudo mkdir /home/your_user_name_here/.local/share/Trash
sudo chown 777 /home/your_user_name_here/.local/share/Trash
```

I'm having a similar problem.  Couple of questions:

Doesn't chown 777 change the owner of the file to "777"?  Shouldn't that be "chmod 777" (I'm very new at this, so I could be *very *wrong).

Also, in my case giving everyone read, write, execute privileges to the directory did not help.  Should all the parent directories (up to and obviously including my home directory) allow me to have read, write, execute privileges? I think my current situation is not set up like that.

Thanks!

---

### Post by KevNice on 2008-07-01
> **iaculallad said:**
> Try this instead:

If you're using Hardy:

User Trash:

```
sudo mkdir /home/your_user_name_here/.local/share/Trash
sudo chown 777 /home/your_user_name_here/.local/share/Trash
```

Root Trash:

```
sudo mkdir ~/.local/share/Trash
sudo chown 777 ~/.local/share/Trash
sudo mkdir ~/.local/share/Trash/files
sudo chown 777 ~/.local/share/Trash/files

```


Tried all of this... no change in the result, though. Still cant move anything to Trash.

Strange thing is this... I have a /storage partition. When I delete things from the /storage partition, it does it with no problem and it appears in the Trash bin on my desktop. However when I delete anything out of the /home partition, thats when I get the errors.

---

### Post by iaculallad on 2008-07-01
Try using chmod with 666 as permission:

```
sudo mkdir ~/.local/share/Trash
sudo chmod 666 ~/.local/share/Trash
```

---

### Post by KevNice on 2008-07-01
> **iaculallad said:**
> Try using chmod with 666 as permission:

```
sudo mkdir ~/.local/share/Trash
sudo chmod 666 ~/.local/share/Trash
```

still no dice

---

### Post by sisco311 on 2008-07-01
Deleted

---

### Post by chrisccoulson on 2008-07-01
Your problem is that you're using sudo to re-create the Trash folder. The Freedesktop.org spec dictates that the trash folder must be owned by yourself, or it won't use it (which is exactly the behaviour you're seeing). Your trash will not work if the trash folder is owned by another user (even root).

There is no need to use sudo to create any file or folder in your home folder.

To recreate the trash folder, you just need to do:
```
mkdir ~/.local/share/Trash
```
No need to change permissions. It should be 755 by default and that should work.

If you've created a trash folder owned by root, then you'll have to chown it to yourself:
```
sudo chown <*user_name*>:<*user_name*> ~/.local/share/Trash
chmod 0755 ~/.local/share/Trash
```

Only trash folders *outside of the users home folder and on another partition* need the sticky bit set and 777 permissions. This is so the Freedesktop.org trash implementation can create a subdirectory owned by the user, in which their trash can be stored and will prevent other users from interfering with the permissions of this subfolder.

---

### Post by KevNice on 2008-07-02
Thanks a lot for that post, and the accompanying explanation for the problem. 

Got everything working just fine now

---

