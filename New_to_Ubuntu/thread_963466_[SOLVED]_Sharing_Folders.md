---
title: "[SOLVED] Sharing Folders"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by getitright on 2008-10-30
When I right click on my desktop folders I do not see Sharing Options in the drop down menu.

---

### Post by northern lights on 2008-10-30
Do you have either samba or nfs installed?

---

### Post by Sarmacid on 2008-10-30
Install samba

```
sudo apt-get install samba
```

---

### Post by getitright on 2008-10-30
I have Samba installed. It is the **designation** of folders as shared in linux that I am having the problem with surely this does not depend on samba or nfs? I should be able to designate a folder as shared without samba or nfs.

---

### Post by Sarmacid on 2008-10-30
Do you mean sharing folders with other ubuntu users?

---

### Post by biji on 2008-10-30
try istall this package: gnome-user-share
tis is cool sharing via webdav

---

### Post by getitright on 2008-10-30
I am not making myseself very clear on my problem.

When I go to System>Preferences>File Sharing I can enable file sharing. What I cannot do is to designate an individual folder/file for sharing in Nautilus. I can do this on my laptop simply by right clicking on a folder in Nautilus and selecting share in the drop down box. On my desktop the drop down box has no share option, this has somehow disappeared as it was there before.

---

### Post by plucky on 2008-10-30
> **getitright said:**
> I am not making myseself very clear on my problem.

When I go to System>Preferences>File Sharing I can enable file sharing. What I cannot do is to designate an individual folder/file for sharing in Nautilus. I can do this on my laptop simply by right clicking on a folder in Nautilus and selecting share in the drop down box. On my desktop the drop down box has no share option, this has somehow disappeared as it was there before.

What if you go right click on a folder and go to **Properties**.
Do you have a share tag there?

---

### Post by getitright on 2008-10-30
No share tag in **Properties**

---

### Post by plucky on 2008-10-30
Open Synaptic Package manager and see if you have **nautilus-share** and **gnome-system-tools** installed.

I think nautilus-share is the package you need installed to enable the sharing folder option


Good Luck

---

### Post by getitright on 2008-10-30
**gnome-system-tools** was already installed. Installed **nautilus-shaare** and my folder share option has been restored. Problem resolved.

---

