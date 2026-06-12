---
title: "which path does the trash have?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ben22 on 2008-04-25
Hi, 

I want to empty the trash, but don't have permissions to delete all files with my users. 

Thus I want to access it through the terminal

Which path does the Trash have?

Thx,
ben

---

### Post by sisco311 on 2008-04-25
in hardy heron (8.04) and xubuntu is:
> ~/.local/share/Trash/files/

in 7.10, 7.04, 6.10 ...:
> ~/.Trash
or
> ~/.Trash-XXXX
where XXXX is your user id.

---

### Post by Hieronymus on 2008-04-25
location is in you homedir:

/home/user/.local/share/Trash/files

Jeroen

---

### Post by ben22 on 2008-04-25
> **sisco311 said:**
> in hardy heron (8.04) and xubuntu is:


in 7.10, 7.04, 6.10 ...:

or

where XXXX is your user id.

thx, with which command can I delete all files in the trash folder?

---

### Post by sisco311 on 2008-04-25
```
**sudo rm -fr** ~/.local/share/Trash/files/*****
```
or
```
gksu nautilus
```
to open the file manager as super user and delete the files.(press Ctrl+H to see hidden folders)

---

### Post by Oldsoldier2003 on 2008-04-25
> **ben22 said:**
> thx, with which command can I delete all files in the trash folder?

since you mentioned before you had permissions issues you'll either need to 

```
cd <path/to/trash>
sudo rm -r *
```

be very very careful when you do this!

alternatively you can launch nautilus as root and use the gui

```
gksu nautilus
```

---

### Post by ben22 on 2008-04-25
I tried to find the Trash folder previously with gksu, but when I am in ~/ben there is no .Trash folder visible.

when using command line, [email]ben@ben-desktop:~/.Tras[/email]h$ ls

I see all the files.

**How can I see the .Trash folder using nautilus?**


> **Oldsoldier2003 said:**
> since you mentioned before you had permissions issues you'll either need to 

```
cd <path/to/trash>
sudo rm -r *
```

be very very careful when you do this!

alternatively you can launch nautilus as root and use the gui

```
gksu nautilus
```

---

### Post by sisco311 on 2008-04-25
> **ben22 said:**
> I tried to find the Trash folder previously with gksu, but when I am in ~/ben there is no .Trash folder visible.

when using command line, [EMAIL="ben@ben-desktop:%7E/.Tras"]ben@ben-desktop:~/.Tras[/EMAIL]h$ ls

I see all the files.

**How can I see the .Trash folder using nautilus?**

Ctrl+H or select the Show Hidden Files from the View menu.

---

### Post by ben22 on 2008-04-25
> **sisco311 said:**
> Ctrl+H or select the Show Hidden Files from the View menu.

sry, there is no Trash folder visible, using 7.10

I did:

1. gksu nautilus > file browser
2. CTRL H
3. File System > Home > ben : no folder Trash, however with:

```
ls ~/.Trash
``` - I can list all files.

**So: How could I see the content of this folder as root in Nautilus?**

---

### Post by sisco311 on 2008-04-25
> **ben22 said:**
> sry, there is no Trash folder visible, using 7.10

I did:

1. gksu nautilus > file browser
2. CTRL H
3. File System > Home > ben : no folder Trash, however with:

```
ls ~/.Trash
``` - I can list all files.

**So: How could I see the content of this folder as root in Nautilus?**

The name of the folder begins with a period: **.**Trash 
You can open nautilus in the .Trash folder:
```
gksu nautilus ~/.Trash
```

---

### Post by ben22 on 2008-04-25
> **sisco311 said:**
> The name of the folder begins with a period: **.**Trash 
You can open nautilus in the .Trash folder:
```
gksu nautilus ~/.Trash
```

Thx, that worked!

---

